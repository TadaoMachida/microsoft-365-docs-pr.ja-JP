---
title: 電子情報開示 (Premium) ケースにカストディアンをインポートする
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: 一括インポート ツールを使用して、Microsoft Purview eDiscovery (Premium) のケースに複数のカストディアンとその関連データ ソースをすばやく追加します。
ms.openlocfilehash: f50304711b12cbcf0b42f0cb185d29d085924108
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626867"
---
# <a name="import-custodians-to-an-ediscovery-premium-case"></a>電子情報開示 (Premium) ケースにカストディアンをインポートする

多くのカストディアンを含むMicrosoft Purview eDiscovery (Premium) ケースの場合は、ケースに追加するために必要な情報を含む CSV ファイルを使用して、一度に複数のカストディアンをインポートできます。 インポート カストディアン ツールでは、インポート ジョブが作成される前に CSV ファイルも検証されます。 つまり、インポート ジョブが完了するまで待たなくても、カストディアンがケースに追加されないようにするエラーがあることを学習する前に、CSV ファイル内のエラーを修正できます。

## <a name="before-you-import-custodians"></a>カストディアンをインポートする前に

- CSV ファイルあたり最大 1,000 個のカストディアン (行) をインポートできます。 同時に 1,000 人のカストディアンをインポートすると、タイムアウト エラーが発生し、一部のカストディアンがインポートに失敗する可能性があることに注意してください。 これを修復するには、インポートを繰り返し、失敗したカストディアンをインポートする必要があります。 タイムアウトを回避するには、一度に 200 人のカストディアンをインポートすることをお勧めします。

- 各カストディアンに最大 500 個のデータ ソースを関連付けることができます。  

- 組織の Azure Active Directory の一部であるカストディアンのみをインポートできます。

- 各カストディアンには一意の電子メール アドレスが必要です。

- 非アクティブなメールボックスをカストディアンとしてインポートしたり、非アクティブなメールボックスを別の管理者に関連付けるには、非アクティブなメールボックスの電子メール アドレス (.sarad@contoso.onmmicrosoft.com など) に "." プレフィックスを追加します。

## <a name="import-custodians"></a>カストディアンをインポートする

1. 電子情報開示 (Premium) ケースを開き、[ **データ ソース** ] タブを選択します。

2. [**データ ソースのインポート****カストディアン** の追加] をクリックします > 。

3. **[テンプレートの取得**] ウィザード ページで、[**CSV テンプレートのダウンロード**] をクリックして、カストディアン テンプレートの CSV ファイルをダウンロードします。

   ![[Import custodians]\(カストディアンのインポート\) ポップアップ ページから CSV テンプレートをダウンロードします。](../media/ImportCustodians1.png)

4. 保管情報を CSV ファイルに追加し、ローカル コンピューターに保存します。 CSV ファイルで必要なプロパティの詳細については、「 [カストディアン CSV ファイル](#custodian-csv-file) 」セクションを参照してください。

5. 保管担当者情報を含む CSV ファイルを準備したら、[**データ ソース**] タブに戻り、[**データ ソース** > の **インポートカストディアン** の追加] をもう一度クリックします。

6. [ **CSV ファイルのアップロード** ] ウィザード ページで、[ **Csv ファイルのアップロード** ] をクリックし、保管担当者情報を含む CSV ファイルをアップロードします。

   CSV ファイルをアップロードすると、インポート ウィザードによって CSV ファイルが検証されます。 検証エラーが存在する場合は、エラーを表示するためのリンクを含むエラー バナーがウィザードに表示されます。

   ![詳細へのリンクを含む検証エラー バナー。](../media/ImportCustodians2.png)

   エラー情報は、エラーを含むセルの行と列を識別し、修復アクションを提案します。 検証エラーを修正し、固定 CSV ファイルを再アップロードする必要があります。 インポートカストディアン ジョブを作成する前に、CSV ファイルを正常に検証する必要があります。

7. CSV ファイルが正常に検証されたら、[ **次へ** ] をクリックし、[ **インポート** ] をクリックしてインポート ジョブを開始します。

インポート ジョブを開始すると、電子情報開示 (Premium) によって次の処理が実行されます。

- ケースの [ジョブ] タブに **BulkAddCustodian** という名前の **ジョブ** を作成します。

- 各カストディアンのすべてのデータ ソースの高度なインデックス作成を実行します。

- すべてのカストディアン データ ソースを保留にします (CSV ファイルの **Is OnHold** プロパティが TRUE に設定されている場合)

インポートカストディアン ジョブが完了すると、カストディアンとその関連データ ソースがケースの **[データ ソース]** ページに追加されます。

## <a name="custodian-csv-file"></a>カストディアン CSV ファイル

CSV カストディアン テンプレートをダウンロードしたら、各行にカストディアンとそのデータ ソースを追加できます。 ヘッダー行の列名は変更しないでください。 ワークロードの種類とワークロードの場所の列を使用して、他のデータ ソースをカストディアンに関連付けます。

| 列名|説明|
|:------- |:------------------------------------------------------------|
|**カストディアン contactEmail**     |カストディアンの UPN 電子メール アドレス。 たとえば、sarad@contoso.onmicrosoft.com。           |
|**Exchange が有効になっている** | 保管担当者のメールボックスを含めるか含まない場合は TRUE/FALSE 値。      |
|**OneDrive が有効になっている** | 保管担当者のOneDrive for Businessアカウントを含めるか含まない場合は TRUE/FALSE 値。 |
|**Is OnHold**        | 保管担当者データ ソースを保留にするかどうかを示す TRUE/FALSE 値。 <sup>1</sup>     |
|**Workload1 の種類**         |カストディアンに関連付けるデータ ソースの種類を示す文字列値。 次の値を指定できます。 <br/>- ExchangeMailbox<br/> - SharePointSite<br/>- TeamsMailbox<sup>2</sup><br/>- YammerMailbox<sup>2</sup>. これらのワークロードの種類の前の値では、大文字と小文字が区別されます。 CSV ファイルには、3 つのワークロードの種類とその対応するワークロードの場所の列が含まれています。 合計で 500 個のワークロードの種類と場所を追加できます。|
|**Workload1 の場所**     | ワークロードの種類に応じて、これはデータ ソースの場所になります。 たとえば、Exchange メールボックスの電子メール アドレスや SharePoint サイトの URL などです。 |
|||

> [!NOTE]
> <sup>1</sup> ケースで 1,000 を超えるメールボックスまたは 100 個のサイトを保留にすると、必要に応じて電子情報開示ホールドが自動的にスケーリングされます。 つまり、1 つのポリシーにデータを追加する代わりに、データの場所が複数の保留ポリシーに自動的に追加されます。 ただし、1 組織あたり 10,000 件のケース ホールド ポリシーの制限は引き続き適用されます。 ホールド制限の詳細については、「 [電子情報開示の制限 (Premium)](limits-ediscovery20.md#hold-limits)」を参照してください。
<br>
> <sup>2</sup> TEAMSMailbox と YammerMailbox ワークロードを CSV ファイルに含めると、グループ サイト (TeamSite と YammerSite) が既定で自動的に追加されます。 CSV ファイルで TeamsSite と YammerSite を個別に指定する必要はありません。

カストディアン情報を含む CSV ファイルの例を次に示します。<br/><br/>

|カストディアン contactEmail      | Exchange が有効になっている | OneDrive が有効になっている | Is OnHold | Workload1 の種類 | Workload1 の場所             |
| ----------------- | ---------------- | ---------------- | --------- | -------------- | ------------------------------ |
|robinc@contoso.onmicrosoft.com | TRUE             | TRUE             | TRUE      | SharePointSite | https://contoso.sharepoint.com |
|pillarp@contoso.onmicrosoft.com | TRUE             | TRUE             | TRUE      | |  |
|.johnj@contoso.onmicrosoft.com|TRUE|TRUE|TRUE||
|sarad@contoso.onmicrosoft.com|TRUE|TRUE|TRUE|ExchangeMailbox|.saradavis@contoso.onmicrosoft.com
||||||

> [!NOTE]
> 前述のように、非アクティブなメールボックスをカストディアンとしてインポートしたり、非アクティブなメールボックスを別のカストディアンに関連付けるために、非アクティブなメールボックスの UPN アドレスに "." プレフィックスを追加します。
