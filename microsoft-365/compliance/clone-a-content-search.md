---
title: コンテンツ検索をコピーする
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 4/26/2017
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 7b40eeaa-544c-4534-b89b-9f79998e374c
ms.custom:
- seo-marvel-apr2020
description: この記事の PowerShell スクリプトを使用して、Microsoft 365 のMicrosoft Purview コンプライアンス ポータルで既存のコンテンツ検索をすばやく複製します。
ms.openlocfilehash: 806705202865d97136713dba4afb263b605ef0f8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628817"
---
# <a name="clone-a-content-search"></a>コンテンツ検索をコピーする

Microsoft 365 のMicrosoft Purview コンプライアンス ポータルでコンテンツ検索を作成し、多くのメールボックスや SharePoint サイト、OneDrive for Business サイトを検索する場合は、しばらく時間がかかる場合があります。 URL を誤って入力すると、検索するサイトを指定すると、エラーが発生する可能性もあります。 これらの問題を回避するには、この記事のWindows PowerShell スクリプトを使用して、既存のコンテンツ検索をすばやく複製できます。 検索を複製すると、元の検索と同じプロパティ (コンテンツの場所や検索クエリなど) を含む新しい検索 (別の名前) が作成されます。 その後、キーワード クエリまたは日付範囲を変更して新しい検索を編集し、実行できます。

コンテンツ検索を複製する理由

- 異なるキーワード検索クエリの結果を比較するには、同じコンテンツの場所で実行されます。

- 新しい検索を作成するときに、多数のコンテンツの場所を再入力する必要がなくなったことを保存します。

- 検索結果のサイズを小さくします。 たとえば、返された検索結果が多すぎてエクスポートできない場合は、検索を複製してから、日付範囲に基づいて検索条件を追加し、検索結果の数を減らすことができます。

## <a name="script-information"></a>スクリプト情報

- Exchange Online V2 モジュールをインストールする必要があります。 詳細については、「[EXO V2 モジュールをインストールして管理する](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module)」を参照してください。

- このトピックで説明するスクリプトを実行するには、Microsoft Purview コンプライアンス ポータルの電子情報開示マネージャー役割グループのメンバーである必要があります。

- このスクリプトには、最小限のエラー処理が含まれています。 スクリプトの主な目的は、コンテンツ検索をすばやく複製することです。

- このスクリプトは新しいコンテンツ検索を作成しますが、起動しません。

- このスクリプトでは、複製するコンテンツ検索が電子情報開示ケースに関連付けられているかどうかを考慮します。 検索がケースに関連付けられている場合、新しい検索も同じケースに関連付けられます。 既存の検索がケースに関連付けられていない場合は、Microsoft Purview コンプライアンス ポータルの **[コンテンツ検索**] ページに新しい検索が一覧表示されます。

- このトピックで提供されているサンプル スクリプトは、Microsoft 標準サポート プログラムまたはサービスではサポートされていません。 サンプル スクリプトは現状のまま提供され、いかなる保証も伴いません。 さらに、Microsoft は、商品性、特定目的への適合性の黙示の保証を含む、一切の黙示の保証をいたしかねます。 本サンプル スクリプトおよびドキュメントの使用または性能に起因するすべてのリスクは、お客様が負うものとします。 サンプル スクリプトおよびドキュメントを使用したこと、または使用できなかったことに伴って生じるいかなる損害 (業務利益の損失、業務の中断、業務情報の損失、金銭上の損失、その他一切の損害) についても、Microsoft、Microsoft に帰属する作者、スクリプトの作成、製造、または納入に関与したその他のすべての人員は、いかなる場合も責めを負わないものとします。

## <a name="step-1-run-the-script-to-clone-a-search"></a>手順 1: スクリプトを実行して検索を複製する

この手順のスクリプトでは、既存のコンテンツ検索を複製して新しいコンテンツ検索を作成します。 このスクリプトを実行すると、次の情報を求めるメッセージが表示されます。

- **ユーザー資格情報** - このスクリプトでは、資格情報を使用して Security & Compliance PowerShell に接続します。 前に説明したように、スクリプトを実行するには、Microsoft Purview コンプライアンス ポータルの電子情報開示マネージャー役割グループのメンバーである必要があります。

- **既存の検索の名前** - 複製するコンテンツ検索です。

- **作成される新しい検索の名前** - この値を空白のままにすると、複製する検索の名前に基づく新しい検索の名前がスクリプトによって作成されます。

検索を複製するには:

1. 次のテキストをWindows PowerShell スクリプト ファイルに保存するには、.ps1 のファイル名サフィックスを使用します。たとえば、 `CloneSearch.ps1`.

   ```powershell
   # This PowerShell script clones an existing content search in Microsoft Purview compliance.

   # Ask for the name of the search you want to clone
   $searchName = Read-Host 'Enter the name of the search that you want to clone'
   # Ask for the name of the new search
   $newSearchName = Read-Host 'Enter a name for the new search [leave blank to automatically generate a name]'
   $originalSearch = Get-ComplianceSearch $searchName -EA SilentlyContinue
   # Make sure we have a valid search before continuing
   if(!$originalSearch)
   {
       Write-Error "Couldn't find search: $searchName"
       return
   }
   $searchNameCounter = 1
   # Find a suitable name for the new search
   while(!$newSearchName)
   {
       $newSearchName = $originalSearch.Name + "_" + $searchNameCounter
       $tempSearch = Get-ComplianceSearch $newSearchName -EA SilentlyContinue
       if ($tempSearch)
       {
           $newSearchName = $null
           $searchNameCounter++
       }
   }
   $caseName
   # Determine if the search is part of a case; if so get the case name
   if ($originalSearch.CaseId)
   {
       $searchCase = Get-ComplianceCase $originalSearch.CaseId
       $caseName = $searchCase.Name
   }
   # Need to cast this value as a Boolean the old fashion way
   $allowNotFoundExchangeLocationsEnabled = $false
   if ($originalSearch.AllowNotFoundExchangeLocationsEnabled)
   {
       $allowNotFoundExchangeLocationsEnabled = $true
   }
   $newSearch = New-ComplianceSearch -Name $newSearchName -AllowNotFoundExchangeLocationsEnabled $allowNotFoundExchangeLocationsEnabled -Case $caseName -ContentMatchQuery $originalSearch.ContentMatchQuery -Description $originalSearch.Description -ExchangeLocation $originalSearch.ExchangeLocation -ExchangeLocationExclusion $originalSearch.ExchangeLocationExclusion -Language $originalSearch.Language -SharePointLocation $originalSearch.SharePointLocation -SharePointLocationExclusion $originalSearch.SharePointLocationExclusion -PublicFolderLocation $originalSearch.PublicFolderLocation
   if ($newSearch)
   {
       Write-Host $newSearch.Name "was successfully created" -ForegroundColor Yellow
   }
   ```

2. [セキュリティ/コンプライアンス PowerShell に接続します](/powershell/exchange/connect-to-scc-powershell)。 同じ PowerShell ウィンドウで、スクリプトを保存したフォルダーに移動します。

3. スクリプトを実行します。例えば：

     ```powershell
     .\CloneSearch.ps1
     ```

4. スクリプトの入力を求められたら、次の情報を入力します。 各情報を入力し、Enter キーを押 **します**。

     - 既存の検索の名前。
     - 新しい検索の名前。

     このスクリプトは新しいコンテンツ検索を作成しますが、起動しません。 これにより、次の手順で検索を編集して実行できます。 新しい検索がケースに関連付けられているかどうかに応じて **、Get-ComplianceSearch** コマンドレットを実行するか、Microsoft Purview コンプライアンス ポータルの **[コンテンツ検索**] または [**電子情報開示**] ページに移動して、新しい検索のプロパティを表示できます。

## <a name="step-2-edit-and-run-the-cloned-search-in-the-microsoft-purview-compliance-portal"></a>手順 2: Microsoft Purview コンプライアンス ポータルで複製された検索を編集して実行する

既存のコンテンツ検索を複製するスクリプトを実行した後、次の手順では、Microsoft Purview コンプライアンス ポータルに移動して新しい検索を編集して実行します。 前述のように、キーワード検索クエリを変更し、検索条件を追加または削除することで、検索を編集できます。 詳しくは、次のトピックを参照してください。

- [Office 365 のコンテンツ検索](content-search.md)

- [コンテンツ検索のキーワード クエリと検索条件](keyword-queries-and-search-conditions.md)

- [電子情報開示のケース](./get-started-core-ediscovery.md)
