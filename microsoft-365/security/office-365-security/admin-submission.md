---
title: 提出を管理する
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: seo-marvel-apr2020
description: 管理者は、Microsoft 365 Defender ポータルで申請ポータルを使用して、ブロックされた正当なメール、疑わしい電子メール、疑わしいフィッシングメール、スパム、その他の潜在的に有害なメッセージ、URL、電子メールの添付ファイルを再スキャン用に Microsoft に送信する方法について説明します。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2502e86f0400e0d803399c0e32a359e907375410
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944001"
---
# <a name="use-the-submissions-portal-to-submit-suspected-spam-phish-urls-legitimate-email-getting-blocked-and-email-attachments-to-microsoft"></a>送信ポータルを使用して、疑わしいスパム、フィッシング、URL、ブロックされる正当なメール、および電子メールの添付ファイルを Microsoft に送信する

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**適用対象**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 プラン 1 およびプラン 2](defender-for-office-365.md)

Exchange Online メールボックスを持つ Microsoft 365 組織では、管理者は、Microsoft 365 Defender ポータルの申請ポータルを使用して、電子メール メッセージ、URL、添付ファイルを Microsoft に送信してスキャンできます。

分析のために電子メール メッセージを送信すると、次の情報が表示されます。

- **Email認証チェック**: 電子メール認証が配信されたときに成功したか失敗したかの詳細。
- **ポリシー ヒット**: テナントへの受信メールを許可またはブロックした可能性があるポリシーに関する情報。サービス フィルターの判定をオーバーライドします。
- **ペイロードの評価/起爆**: メッセージ内の URL と添付ファイルを最新の状態で確認します。
- **グレーデラー分析**: メッセージが悪意のあるかどうかを確認するために、人間の採点者によって行われたレビュー。

> [!IMPORTANT]
> ペイロードの評価/デトネーションとグレーデラーの分析は、すべてのテナントで行われるわけではありません。 データがコンプライアンスのためにテナント境界から離れることが想定されていない場合、情報が組織外に出ないようにブロックされます。

電子メール メッセージ、URL、添付ファイルを Microsoft に送信するその他の方法については、「 [メッセージとファイルを Microsoft に報告する」を参照してください](report-junk-email-messages-to-microsoft.md)。

この短いビデオでは、Microsoft Defender for Office 365で管理者の提出を使用して評価のために Microsoft にメッセージを送信する方法について説明します。
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBLPn]

## <a name="what-do-you-need-to-know-before-you-begin"></a>はじめに把握しておくべき情報

- <https://security.microsoft.com/> で Microsoft 365 Defender ポータルを開きます。 **[申請]** ページに直接移動するには、 <https://security.microsoft.com/reportsubmission>.

- Microsoft にメッセージとファイルを送信するには、次のいずれかのロールが必要です。
  - [Microsoft 365 Defender ポータル](permissions-microsoft-365-security-center.md)の **セキュリティ管理者** または **セキュリティ 閲覧者**。

    この記事の後半で説明するように [、カスタム メールボックスへのユーザー提出を表示するには、](#view-user-submissions-to-microsoft) これらのロールの 1 つが必要であることに注意してください。

- 管理者は、メールボックスで引き続き使用でき、ユーザーまたは別の管理者によって削除されない場合、30 日の古いメッセージを送信できます。

- 管理送信は、次のレートで調整されます。
  - 15 分間の最大送信数: 150 件
  - 24 時間の同じ申請: 3 件の提出
  - 15 分間の同じ申請: 1 件の提出

- ユーザーが Microsoft にメッセージとファイルを送信する方法の詳細については、「メッセージ [とファイルを Microsoft に報告する」を参照してください](report-junk-email-messages-to-microsoft.md)。

## <a name="report-questionable-email-to-microsoft"></a>問題のあるメールを Microsoft に報告する

1. Microsoft 365 Defender ポータルの <https://security.microsoft.com>[アクション] & **[申請**] の [**申請]** ページ **に**\>移動します。 **[申請]** ページに直接移動するには、 <https://security.microsoft.com/reportsubmission>.

2. [ **送信]** ページで、レポートするコンテンツの種類に基づいて [ **電子メール** ] タブが選択されていることを確認し、[分析用に Microsoft に送信] アイコンをクリックします ![。](../../media/m365-cc-sc-create-icon.png) **分析のために Microsoft に送信します**。

3. [ **ネットワーク メッセージ ID の追加または電子メール ファイルのアップロード** ] セクションで、次のいずれかのオプションを使用します。
     - **電子メール ネットワーク メッセージ ID を追加します**。これは、メッセージの **X-MS-Exchange-Organization-Network-Message-Id** ヘッダー、または検疫済みメッセージの **X-MS-Office365-Filtering-Correlation-Id** ヘッダーで使用できる GUID 値です。
     - **電子メール ファイル (.msg または .eml) をアップロード** する: [ **ファイルの参照**] をクリックします。 開いたダイアログで、.eml または .msg ファイルを見つけて選択し、[ **開く**] をクリックします。

4. [ **問題のある受信者を選択** する] ボックスで、ポリシー チェックを実行する受信者を指定します。 ポリシー チェックでは、ユーザーまたは組織のポリシーが原因で、電子メールがスキャンをバイパスしたかどうかが決定されます。

5. [ **Microsoft に送信する理由の選択]** セクションで、次のいずれかのオプションを選択します。
   - **ブロックされていない必要があります (False positive)**
   - **ブロックされている必要があります (False negative)**: 電子 **メールが表示されるセクションとして分類されている必要があります** 。次のいずれかの値を選択します (不明な場合は、最善の判断をしてください)。
     - **フィッシング**
     - **Malware**
     - **スパム**

6. 完了したら、**[送信]** をクリックします。

   > :::image type="content" source="../../media/submission-flyout-email.png" alt-text="新しい URL 送信プロセス" lightbox="../../media/submission-flyout-email.png":::

## <a name="report-questionable-urls-to-microsoft"></a>問題のある URL を Microsoft に報告する

1. Microsoft 365 Defender ポータルの <https://security.microsoft.com>[アクション] & **[申請**] の [**申請]** ページ **に**\>移動します。 **[申請]** ページに直接移動するには、 <https://security.microsoft.com/reportsubmission>.

2. [ **申請]** ページで、レポートするコンテンツの種類に基づいて [ **URL** ] タブが選択されていることを確認し、[分析用に Microsoft に送信] アイコンをクリックします ![。](../../media/m365-cc-sc-create-icon.png) **分析のために Microsoft に送信します**。

3. 表示される **[URL** ] ボックスに、完全な URL (たとえば) `https://www.fabrikam.com/marketing.html`を入力します。

4. [ **Microsoft に送信する理由の選択]** セクションで、次のいずれかのオプションを選択します。
   - **ブロックされていない必要があります (False positive)**
   - **ブロックされている必要があります (False negative)**: **[この URL は表示されるセクションとして分類されている必要があります** ] で、次のいずれかの値を選択します (わからない場合は、最善の判断をしてください)。
     - **フィッシング**
     - **Malware**

5. 完了したら、**[送信]** をクリックします。

    > :::image type="content" source="../../media/submission-url-flyout.png" alt-text="新しいEmail申請プロセス" lightbox="../../media/submission-url-flyout.png":::

 > [!NOTE]
 > URL の送信は、データが環境から離れることを許可しないクラウドでは使用できません。 URL を選択する機能は淡色表示されます。

## <a name="report-questionable-email-attachment-to-microsoft"></a>Microsoft に質問のある電子メールの添付ファイルを報告する

1. Microsoft 365 Defender ポータルの <https://security.microsoft.com>[アクション] & **[申請**] の [**申請]** ページ **に**\>移動します。 **[申請]** ページに直接移動するには、 <https://security.microsoft.com/reportsubmission>.

2. [**申請]** ページで、レポートするコンテンツの種類に基づいて **[Email添付ファイル**] タブが選択されていることを確認し、[分析用に Microsoft に送信] アイコンをクリックします![。](../../media/m365-cc-sc-create-icon.png) **分析のために Microsoft に送信します**。

3. 表示される [ **ファイル** ] セクションで、[ **ファイルの参照**] をクリックします。 開いたダイアログで、ファイルを見つけて選択し、[ **開く**] をクリックします。

3. [ **Microsoft に送信する理由の選択]** セクションで、次のいずれかのオプションを選択します。
   - **ブロックされていない必要があります (False positive)**
   - **ブロックされている必要があります (False negative)**: **[このファイルは表示されるセクションとして分類されている必要があります** ] で、次のいずれかの値を選択します (不明な場合は、最善の判断をしてください)。
     - **フィッシング**
     - **Malware**

4. 完了したら、**[送信]** をクリックします。

    > :::image type="content" source="../../media/submission-file-flyout.png" alt-text="新しい添付ファイルの送信プロセス" lightbox="../../media/submission-file-flyout.png":::

> [!NOTE]
> マルウェア フィルターによってメッセージの添付ファイルがマルウェア アラート Text.txt ファイルに置き換えられた場合は、元の添付ファイルを含む検疫から元のメッセージを送信する必要があります。 検疫の詳細と、マルウェアの誤検知を含むメッセージを解放する方法については、「 [管理者としての検疫済みメッセージとファイルの管理](manage-quarantined-messages-and-files.md)」を参照してください。ファイルの送信は、データが環境から離れることを許可しないクラウドでは使用できません。 [ファイル] を選択する機能は淡色表示されます。

## <a name="view-email-admin-submissions-to-microsoft"></a>Microsoft へのメール管理者の提出を表示する

1. Microsoft 365 Defender ポータルの <https://security.microsoft.com>[アクション] & **[申請**] の [**申請]** ページ **に**\>移動します。 **[申請]** ページに直接移動するには、 <https://security.microsoft.com/reportsubmission>.

2. [ **送信] ページで** 、[ **電子メール** ] タブが選択されていることを確認します。

   - 使用可能な列ヘッダーをクリックすると、エントリを並べ替えることができます。 [ **列のカスタマイズ** ] をクリックして、必要な列を選択します。 すべての列を選択し、送信グリッドに表示できます。 既定値にはアスタリスク (*)が付いています。
     - **申請名**<sup>\*</sup>
     - **[送信者]**<sup>\*</sup>
     - **[受信者]**
     - **送信日**<sup>\*</sup>
     - **送信の理由**<sup>\*</sup>
     - **ステータス**<sup>\*</sup>
     - **結果**<sup>\*</sup>
     - **フィルターの判定**
     - **配信/ブロックの理由**
     - **申請 ID**
     - **ネットワーク メッセージ ID/オブジェクト ID**
     - **方向**
     - [**Sender IP (送信者の IP)**]
     - **一括準拠レベル (BCL)**
     - **宛先**
     - **ポリシー アクション**
     - **提出者**
     - **フィッシング シミュレーション**
     - **タグ**<sup>\*</sup>
     - **許可**

     完了したら、**[適用]** をクリックします。

     :::image type="content" source="../../media/email-admin-submission-customize-columns.png" alt-text="電子メール管理者の提出の列オプションをカスタマイズします。" lightbox="../../media/email-admin-submission-customize-columns.png":::

   - エントリをフィルター処理するには、[フィルター] をクリック **します**。 使用できるフィルターは次のとおりです。
     - **送信日**: **開始日** と **終了日**。
     - **申請 ID**: すべての申請に割り当てられる GUID 値。
     - **ネットワーク メッセージ ID**
     - **Sender**
     - **[受信者]**
     - **[名前]**
     - **提出者**
     - **送信の理由**
     - **状態**
     - **Tags**

     完了したら、**[適用]** をクリックします。

     :::image type="content" source="../../media/email-admin-submission-filters.png" alt-text="電子メール管理者の提出のフィルター オプション。" lightbox="../../media/email-admin-submission-filters.png":::

   - エントリをグループ化するには、[ **グループ化** ] をクリックし、ドロップダウン リストから次のいずれかの値を選択します。
     - **なし**
     - **理由**
     - **状態**
     - **結果**
     - **Tags**

   - エントリをエクスポートするには、[ **エクスポート**] をクリックします。 表示されるダイアログで、.csv ファイルを保存します。

## <a name="view-email-attachment-admin-submissions-to-microsoft"></a>Microsoft へのメール添付ファイル管理者の提出を表示する

1. Microsoft 365 Defender ポータルの <https://security.microsoft.com>[アクション] & **[申請**] の [**申請]** ページ **に**\>移動します。 **[申請]** ページに直接移動するには、 <https://security.microsoft.com/reportsubmission>.

2. [**申請]** ページで、[**Email添付ファイル**] タブが選択されていることを確認します。

   - 使用可能な列ヘッダーをクリックすると、エントリを並べ替えることができます。 [ **列のカスタマイズ** ] をクリックして、必要な列を選択します。 すべての列を選択し、送信グリッドに表示できます。 既定値にはアスタリスク (*)が付いています。
     - **添付ファイル名**<sup>\*</sup>
     - **送信日**<sup>\*</sup>
     - **送信の理由**<sup>\*</sup>
     - **ステータス**<sup>\*</sup>
     - **結果**<sup>\*</sup>
     - **フィルターの判定**
     - **配信/ブロックの理由**
     - **申請 ID**
     - **オブジェクト ID**
     - **ポリシー アクション**
     - **提出者**
     - **タグ**<sup>\*</sup>
     - **許可**

     完了したら、**[適用]** をクリックします。

     :::image type="content" source="../../media/email-attachment-admin-submission-customize-columns.png" alt-text="電子メール添付ファイル管理者の送信の列オプションをカスタマイズします。":::

   - エントリをフィルター処理するには、[フィルター] をクリック **します**。 使用できるフィルターは次のとおりです。
     - **送信日**: **開始日** と **終了日**。
     - **申請 ID**: すべての申請に割り当てられる GUID 値。
     - **添付ファイルの名前**
     - **提出者**
     - **送信の理由**
     - **状態**
     - **Tags**

     完了したら、**[適用]** をクリックします。

     :::image type="content" source="../../media/email-attachment-admin-submission-filters.png" alt-text="電子メール添付ファイル管理者の送信のフィルター オプション。":::

   - エントリをグループ化するには、[ **グループ化** ] をクリックし、ドロップダウン リストから次のいずれかの値を選択します。
     - **なし**
     - **理由**
     - **状態**
     - **結果**
     - **Tags**

   - エントリをエクスポートするには、[ **エクスポート**] をクリックします。 表示されるダイアログで、.csv ファイルを保存します。

## <a name="view-urls-admin-submissions-to-microsoft"></a>Microsoft に対する URL 管理者の提出を表示する

1. Microsoft 365 Defender ポータルの <https://security.microsoft.com>[アクション] & **[申請**] の [**申請]** ページ **に**\>移動します。 **[申請]** ページに直接移動するには、 <https://security.microsoft.com/reportsubmission>.

2. [ **申請] ページで** 、[ **URL** ] タブが選択されていることを確認します。

   - 使用可能な列ヘッダーをクリックすると、エントリを並べ替えることができます。 [ **列のカスタマイズ** ] をクリックして、必要な列を選択します。 すべての列を選択し、送信グリッドに表示できます。 既定値にはアスタリスク (*)が付いています。
     - [**URL**<sup>\*</sup>]
     - **送信日**<sup>\*</sup>
     - **送信の理由**<sup>\*</sup>
     - **ステータス**<sup>\*</sup>
     - **結果**<sup>\*</sup>
     - **フィルターの判定**
     - **配信/ブロックの理由**
     - **申請 ID**
     - **オブジェクト ID**
     - **ポリシー アクション**
     - **提出者**
     - **タグ**<sup>\*</sup>
     - **許可**

     完了したら、**[適用]** をクリックします。

     :::image type="content" source="../../media/url-admin-submission-customize-columns.png" alt-text="URL 管理者申請の列オプションをカスタマイズします。":::

   - エントリをフィルター処理するには、[フィルター] をクリック **します**。 使用できるフィルターは次のとおりです。
     - **送信日**: **開始日** と **終了日**。
     - **申請 ID**: すべての申請に割り当てられる GUID 値。
     - **URL**
     - **提出者**
     - **送信の理由**
     - **状態**
     - **Tags**

     完了したら、**[適用]** をクリックします。

     :::image type="content" source="../../media/url-admin-submission-customize-columns.png" alt-text="URL 管理者申請のフィルター オプション。":::

   - エントリをグループ化するには、[ **グループ化** ] をクリックし、ドロップダウン リストから次のいずれかの値を選択します。
     - **なし**
     - **理由**
     - **状態**
     - **結果**
     - **Tags**

   - エントリをエクスポートするには、[ **エクスポート**] をクリックします。 表示されるダイアログで、.csv ファイルを保存します。

### <a name="admin-submission-result-details"></a>提出結果の詳細を管理する

管理者の提出で送信されたメッセージが確認され、申請の詳細ポップアップに結果が表示されます。

- 配信時に送信者のメール認証に失敗した場合。
- メッセージのセキュリティ判定に影響を与える、または上書きされる可能性があるポリシー ヒットに関する情報。
- 現在の爆発的な結果により、メッセージに含まれる URL またはファイルが悪意のあるものかが確認されます。
- 採点者からのフィードバック。

オーバーライドが見つかった場合、結果は数分で使用可能になります。 電子メール認証に問題がない場合、または配信がオーバーライドの影響を受けなかった場合、採点者からのフィードバックには最大 1 日かかる可能性があります。

## <a name="view-user-submissions-to-microsoft"></a>Microsoft へのユーザー申請を表示する

[レポート メッセージ アドイン](enable-the-report-message-add-in.md)、[レポート フィッシング アドイン](enable-the-report-phish-add-in.md)、またはユーザーが組 [み込みのレポートをOutlook on the webで使用している](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md)場合は、[**ユーザー報告メッセージ**] タブでレポートしているユーザーを確認できます。

1. Microsoft 365 Defender ポータルの <https://security.microsoft.com>[アクション] & **[申請**] の [**申請]** ページ **に**\>移動します。 **[申請]** ページに直接移動するには、 <https://security.microsoft.com/reportsubmission>.

2. [ **申請] ページで** 、[ **ユーザーが報告したメッセージ** ] タブを選択します。

   - 使用可能な列ヘッダーをクリックすると、エントリを並べ替えることができます。 [ **列のカスタマイズ** ] をクリックしてオプションを表示します。 既定値にはアスタリスク (*)が付いています。

     - **件名Email**<sup>\*</sup>
     - **報告者**<sup>\*</sup>
     - **報告日**<sup>\*</sup>
     - **[送信者]**<sup>\*</sup>
     - **報告された理由**<sup>\*</sup>
     - **結果**<sup>\*</sup>
     - **メッセージ報告 ID**
     - **ネットワーク メッセージ ID**
     - [**Sender IP (送信者の IP)**]
     - **レポート元**
     - **フィッシング シミュレーション**
     - **管理者申請に変換済み**
     - **タグ**<sup>\*</sup>
     - **マーク済み**<sup>\*</sup>
     - **マーク付き**
     - **マークされた日付**

     完了したら、**[適用]** をクリックします。

   - エントリをフィルター処理するには、[フィルター] をクリック **します**。 使用できるフィルターは次のとおりです。
     - **報告日**: **開始日** と **終了日**。
     - [**レポート作成者**]
     - **メールの件名**
     - **メッセージ報告 ID**
     - **ネットワーク メッセージ ID**
     - **Sender**
     - **報告された理由**: **迷惑メール**、**フィッシング**、**スパム** ではない
     - **報告元**: **Microsoft アドイン** または **サード パーティアドイン**
     - **フィッシング シミュレーション**: **はい** または **いいえ**
     - **管理者申請に変換**: **はい** または **いいえ**
     - **Tags**

     完了したら、**[適用]** をクリックします。

     > :::image type="content" source="../../media/admin-submission-reported-messages.png" alt-text="ユーザー申請の [新しいフィルター] オプション" lightbox="../../media/admin-submission-reported-messages.png":::

   - エントリをグループ化するには、[ **グループ化** ] をクリックし、ドロップダウン リストから次のいずれかの値を選択します。
     - **なし**
     - **理由**
     - **Sender**
     - [**レポート作成者**]
     - **結果**
     - **レポート元**
     - **フィッシング シミュレーション**
     - **管理者申請に変換済み**
     - **Tags**

   - エントリをエクスポートするには、[ **エクスポート**] をクリックします。 表示されるダイアログで、.csv ファイルを保存します。
   - レポート [メッセージの確認管理](admin-review-reported-message.md)表示されるユーザーに通知するには
 
> [!NOTE]
> 組織がユーザーから報告されたメッセージをカスタム メールボックスにのみ送信するように構成されている場合、報告されたメッセージは **ユーザー報告メッセージ** に表示されますが、結果は常に空になります (再スキャンされなかったため)。

## <a name="undo-user-submissions"></a>ユーザーの申請を元に戻す

ユーザーがカスタム メールボックスに不審な電子メールを送信すると、ユーザーと管理者は送信を元に戻すオプションを持っていません。 ユーザーが電子メールを回復する場合は、[削除済みアイテム] フォルダーまたは [迷惑Email フォルダーで回復できます。

## <a name="convert-user-reported-messages-from-the-custom-mailbox-into-an-admin-submission"></a>ユーザーが報告したメッセージをカスタム メールボックスから管理者の提出に変換する

Microsoft にメッセージを送信せずにユーザーから報告されたメッセージをインターセプトするようにカスタム メールボックスを構成した場合は、分析のために特定のメッセージを見つけて Microsoft に送信できます。

[ **ユーザーから報告されたメッセージ** ] タブで、一覧でメッセージを選択し、[ **分析のために Microsoft に送信**] をクリックし、ドロップダウン リストから次のいずれかの値を選択します。

- **クリーンなレポート**
- **フィッシングを報告する**
- **マルウェアを報告する**
- **スパムを報告する**
- **トリガー調査**

  :::image type="content" source="../../media/admin-submission-main-action-button.png" alt-text="[アクション] ボタンの [新規] オプション" lightbox="../../media/admin-submission-main-action-button.png":::

メッセージが Microsoft に報告された場合、[ **管理者に変換] の送信** 値が **[いいえ]** から **[はい**] に変わります。 管理者申請に直接アクセスするには、それぞれのユーザーが報告したメッセージの送信ポップアップ内のオーバーフロー メニューから **[変換された管理者** 申請の表示] をクリックします。

:::image type="content" source="../../media/view-converted-admin-submission.png" alt-text="ユーザーから報告されたメッセージから作成された管理者の提出を表示するオプション。":::

## <a name="view-associated-alert-for-user-and-admin-email-submissions"></a>ユーザーと管理者のメール送信に関連するアラートを表示する

> [!IMPORTANT]
> このセクションの情報は、Defender for Office 365プラン 2 以降にのみ適用されます。
>
> 現在、ユーザー申請では、フィッシングとして報告されたメッセージに対してのみアラートが生成されます。

ユーザーが報告したフィッシング メッセージと管理者のメール送信ごとに、対応するアラートが生成されます。

ユーザーが報告したフィッシング メッセージに対応するアラートを表示するには、[ **ユーザーが報告したメッセージ** ] タブを選択し、メッセージをダブルクリックして送信ポップアップを開きます。 [その他のオプション] アイコンをクリック ![します。](../../media/m365-cc-sc-more-actions-icon.png) **その他のオプション** を選択し、[  **アラートの表示**] を選択します。

:::image type="content" source="../../media/alert-from-user-submission.png" alt-text="ユーザーから報告されたフィッシング メッセージから関連するアラートを表示するオプション。":::

管理者のメール送信に対応するアラートを表示するには、[ **電子メール** ] タブを選択し、メッセージをダブルクリックして申請ポップアップを開きます。 [**電子メール エンティティを開く**] オプションで [**アラートの表示**] を選択します。

:::image type="content" source="../../media/alert-from-admin-submission.png" alt-text="管理者の申請から関連するアラートを表示するオプション。":::
