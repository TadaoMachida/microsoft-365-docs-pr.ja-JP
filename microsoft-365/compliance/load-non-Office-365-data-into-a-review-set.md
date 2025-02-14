---
title: レビューセットにMicrosoft 365 以外のデータを読み込む
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: 電子情報開示 (Premium) ケースの分析用に Microsoft 365 以外のデータをレビュー セットにインポートする方法について説明します。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c1efdcb98c0d9ae5b0f47215997782a3b88c8683
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636009"
---
# <a name="load-non-microsoft-365-data-into-a-review-set"></a>レビューセットにMicrosoft 365 以外のデータを読み込む

Microsoft Purview eDiscovery (Premium) で分析する必要があるすべてのドキュメントが Microsoft 365 にあるわけではありません。 電子情報開示 (Premium) の Microsoft 365 以外のデータ インポート機能を使用すると、Microsoft 365 にないドキュメントをレビュー セットにアップロードできます。 この記事では、Microsoft 以外の 365 ドキュメントを電子情報開示 (Premium) に取り込んで分析する方法について説明します。

## <a name="requirements-to-upload-non-office-365-content"></a>Office 365以外のコンテンツをアップロードするための要件

この記事で説明する Microsoft 365 以外のアップロード機能を使用するには、次のものが必要です。

- Microsoft 365 以外のコンテンツを関連付けるすべてのカストディアンには、適切なライセンスを割り当てる必要があります。 詳細については、「 [電子情報開示の概要 (Premium)](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses)」を参照してください。

- 既存の電子情報開示 (Premium) ケース。

- Microsoft 365 以外のデータをアップロードして関連付ける前に、カストディアンをケースに追加する必要があります。

- Microsoft 以外の 365 データは、電子情報開示 (プレミアム) でサポートされているファイルの種類である必要があります。 詳細については、「[電子情報開示 (Premium) でサポートされているファイルの種類](supported-filetypes-ediscovery20.md)」を参照してください。

- レビュー セットにアップロードされたすべてのファイルは、フォルダーにある必要があります。各フォルダーは、特定のカストディアンに関連付けられています。 これらのフォルダーの名前には、*alias@domainname* のような名前付け形式を使用する必要があります。 alias@domainname は、ユーザーの Microsoft 365 エイリアスとドメインにする必要があります。 ルート フォルダー内のすべてのalias@domainname フォルダーを収集できます。 ルート フォルダーには、alias@domainname フォルダーのみを含めることができます。 ルート フォルダー内のルース ファイルはサポートされていません。

   アップロードする Microsoft 365 以外のデータのフォルダー構造は、次の例のようになります。

   - c:\nonO365\abraham.mcmahon@contoso.com
   - c:\nonO365\jewell.gordon@contoso.com
   - c:\nonO365\staci.gonzalez@contoso.com

   ここで、abraham.mcmahon@contoso.com、jewell.gordon@contoso.com、および staci.gonzalez@contoso.com は、ケース内のカストディアンの SMTP アドレスです。

   ![Microsoft 365 以外のデータ アップロード フォルダー構造。](../media/3f2dde84-294e-48ea-b44b-7437bd25284c.png)

- 電子情報開示マネージャーの役割グループに割り当てられている (電子情報開示管理者として追加された) アカウント。

- Microsoft 365 以外のコンテンツ フォルダー構造にアクセスできるコンピューターにインストールされた AzCopy v8.1 ツール。 AzCopy をインストールするには、 [Windows で AzCopy v8.1 でデータを転送する方法に関するページを](/previous-versions/azure/storage/storage-use-azcopy)参照してください。 既定の場所 ( **%ProgramFiles(x86)%\Microsoft SDK\Azure\AzCopy**) に AzCopy をインストールしてください。 AzCopy v8.1 を使用する必要があります。 他のバージョンの AzCopy は、電子情報開示 (Premium) で Microsoft 365 以外のデータを読み込むと機能しない場合があります。


## <a name="upload-non-microsoft-365-content-into-ediscovery-premium"></a>Microsoft 365 以外のコンテンツを電子情報開示 (Premium) にアップロードする

1. 電子情報開示マネージャーまたは電子情報開示管理者として、電子情報開示 (Premium) を開き、Microsoft 以外の 365 データがアップロードされるケースに移動します。  

2. [ **校閲セット**] をクリックし、レビュー セットを選択して Microsoft 365 以外のデータをアップロードします。  レビュー セットがない場合は、作成できます。 
 
3. レビュー セットをクリックするか、選択して [レビュー セットを開く] をクリックして **、レビュー セットを開きます**。

4. レビュー セットで、[**レビュー セットの管理**] (**[アクション]** オプションの直後の下向き矢印) をクリックし、[**非Office 365 データ**] オプションをクリックします。

5. **ファイルのアップロード** をクリックして、データ インポート ウィザードを開始します。

   ![ファイルをアップロードします。](../media/574f4059-4146-4058-9df3-ec97cf28d7c7.png)

   ウィザードの最初の手順で準備するセキュリティで保護された Microsoft 提供の Azure Storage に、ファイルをにアップロードします。  準備が完了したら、**次: ファイルのアップロード** ボタンがアクティブになります。

   ![Microsoft 365 以外のインポート: 準備します。](../media/0670a347-a578-454a-9b3d-e70ef47aec57.png)
 
5. **次: ファイルのアップロード** をクリックします。

6. [ **ファイルのアップロード** ] ページで、次の操作を行います。

   ![Microsoft 365 以外のインポート: ファイルをアップロードします。](../media/3ea53b5d-7f9b-4dfc-ba63-90a38c14d41a.png)

   a. [ **ファイルの場所へのパス** ] ボックスに、アップロードする Microsoft 365 以外のデータが格納されているルート フォルダーの場所を確認または入力します。 たとえば、「 **開始する前** に」セクションに示されているサンプル ファイルの場所については、「 **%USERPROFILE\Downloads\nonO365」と入力します**。 正しい場所を指定すると、パスの下のボックスに表示される AzCopy コマンドが適切に更新されます。

   b. [ **クリップボードにコピー** ] をクリックして、ボックスに表示されるコマンドをコピーします。

7. Windows コマンド プロンプトを起動し、前の手順でコピーしたコマンドを貼り付けてから **Enter キーを** 押して AzCopy コマンドを開始します。  コマンドを開始すると、Microsoft 以外の 365 ファイルが、手順 4 で準備された Azure Storage の場所にアップロードされます。

   ![Microsoft 365 以外のインポート: AzCopy。](../media/504e2dbe-f36f-4f36-9b08-04aea85d8250.png)

   > [!NOTE]
   > 前述のように、AzCopy v8.1 を使用して、[ **ファイルのアップロード** ] ページで提供されているコマンドを正常に使用する必要があります。 指定した AzCopy コマンドが失敗した場合は、「 [電子情報開示での AzCopy のトラブルシューティング (Premium)」](troubleshooting-azcopy.md)を参照してください。

8. Microsoft Purview コンプライアンス ポータルに戻るし、ウィザードで [**次へ: ファイルの処理**] をクリックします。  これにより、Azure Storage の場所にアップロードされた Microsoft 365 以外のファイルの処理、テキスト抽出、インデックス作成が開始されます。  

9. Microsoft **365 以外のデータをレビュー セットに追加** するという名前のジョブを表示して、[**ファイルの処理**] ページまたは [**ジョブ**] タブでファイルの処理の進行状況を追跡します。  ジョブが完了すると、新しいファイルがレビュー セットで使用できるようになります。

   ![Microsoft 365 以外のインポート: ファイルを処理します。](../media/218b1545-416a-4a9f-9b25-3b70e8508f67.png)

10. 処理が完了したら、ウィザードを閉じることができます。
