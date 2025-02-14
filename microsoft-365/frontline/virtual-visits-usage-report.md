---
title: Microsoft Teams 仮想訪問の使用状況レポート
author: LanaChin
ms.author: v-lanachin
manager: samanro
audience: Admin
ms.topic: article
ms.service: microsoft-365-frontline
ms.reviewer: ''
f1.keywords:
- NOCSH
ms.localizationpriority: high
search.appverid: MET150
ms.collection:
- M365-collaboration
- m365-frontline
description: Microsoft Teams 管理センターの仮想訪問の使用状況レポートを使用して、組織内の仮想予定アクティビティの概要を取得する方法について説明します。
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5f609ebb1d48e1e7c9b55d2998c793403dec8fa0
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2022
ms.locfileid: "66995108"
---
# <a name="microsoft-teams-virtual-visits-usage-report"></a>Microsoft Teams 仮想訪問の使用状況レポート

Microsoft Teams 管理センターの仮想訪問使用状況レポートでは、組織内の Teams 仮想予定アクティビティの概要が管理者に表示されます。 [Bookings アプリ](bookings-virtual-visits.md)と [Microsoft Teams 電子カルテ (EHR) コネクタ](teams-in-hc.md#virtual-appointments-and-electronic-healthcare-record-ehr-integration)を使用して、スケジュールされた仮想予定の詳細なアクティビティを表示できます。

レポートを表示するには、グローバル管理者または Teams 管理者である必要があります。

サンプル レポートには以下のタブがあります。 レポートに表示される情報は、Bookings アプリ、Teams EHR コネクタ、またはその両方のライセンスがあるかどうかによって異なります。

|タブ |説明  |
|---------|---------|
|**[仮想訪問](#virtual-visits)**     |仮想予定の合計数と、EHR システムから実施された Bookings アプリと Teams EHR 統合会議を使用してスケジュールされた予定の数の内訳を示します。         |
|**[期間](#duration)**     |予定の平均期間と参加者のロ平均ロビー待機時間を示します。         |
|**[Bookings](#bookings)**     |Bookings アプリを通じてスケジュールされた予定の数を示します。         |
|**[EHR](#ehr)**     |EHR システムから実施された Teams EHR 統合予定の数を示します。         |  

このレポートを使用して、組織内の仮想予定アクティビティと傾向に関する分析情報を取得します。 この情報は、仮想予定を最適化して、より良いビジネス成果を提供するのに役立ちます。

## <a name="view-the-virtual-visits-usage-report"></a>仮想訪問使用状況レポートを表示する

1. Microsoft Teams 管理センターの左側のナビゲーションで、[**分析およびレポート**]  >  [**使用状況レポート**] に移動します。 [**レポートの表示**] タブの [**レポート**] で、[**仮想訪問の使用状況**] を選択します。
2. [**日付範囲**] で、7 日間、30 日、または 90 日間の日付範囲を選択します。 次に、[**レポートの実行**] を選択します。

> [!NOTE]
> 既定では、仮想訪問の分析はオンになっており、レポートが使用可能です。 このレポートの使用により、組織内の仮想予定に関するデータを収集するアクセス許可を Microsoft に付与することになります。 データ保持の詳細については、「[Microsoft 365 のデータの保持、削除、および破棄](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview)」を参照してください。
>
>組織のレポートをオフにする場合は、ページの右上隅にある [**設定**] で行うことができます。 この設定を変更後、設定が有効になるまでに 0 (ゼロ) から 2 時間かかる場合があります。

## <a name="interpret-the-report"></a>レポートを解釈する

### <a name="virtual-visits"></a>仮想訪問

ここに表示されるグラフは、Bookings アプリ、Teams EHR コネクタ、またはその両方のライセンスがあるかどうかによって異なります。 詳細については、「[Bookings アプリの管理](/microsoftteams/bookings-app-admin?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)」と 「[Cerner EHR への統合](ehr-admin-cerner.md)」または「[エピック EHR への統合](ehr-admin-epic.md)」に関するページを参照してください。

:::image type="content" source="media/virtual-visits-usage-report-virtual-visits.png" alt-text="番号付き吹き出しを示す仮想訪問の使用状況レポートの [仮想アクセス] タブのスクリーンショット。" lightbox="media/virtual-visits-usage-report-virtual-visits.png":::

|吹き出し |説明  |
|--------|-------------|
|**1**   |各レポートには、このレポートが生成された日付が表示されます。 通常、レポートにはアクティビティの時刻から 24 から 48 時間の遅延が反映されます。 |
|**2**   |X 軸は、レポートで選択された日付範囲です。 縦軸は予定の数です。<br>特定の日付のドットにカーソルを合わせると、その日付の予定の数が表示されます。|
|**3**   |凡例の項目を選択して、グラフに表示する系列をフィルターできます。 たとえば、[**Bookings の合計仮想訪問数**] または [**合計 EHR 仮想訪問数**] を選択して、それぞれに関連する情報のみを表示します。 この選択を変更しても、表内の情報は変わりません。 |
|**4**   |この表には、選択した日付範囲で行われた各予定に関する詳細情報が表示されます。 <ul><li>**開始時刻 (UTC)** は、スタッフ メンバーと参加者の両方が会議に参加している日時、または会議で最初のアクティビティが発生した日時です。  </li> <li>**会議 ID** は、会議の一意の ID です。</li> <li>**ロビー待機時間** は、参加者が最初にロビーに参加してから、同じ参加者または別の参加者がスタッフメンバーによって会議に参加できるようになるまでの時間です。</li><li>**期間** は、開始時刻と最後のユーザーが会議を離れる時刻の時間差です。 スタッフ メンバーと参加者の両方が会議に参加しなかった場合、期間は 0 (ゼロ) と表示されます。</li> <li>**状態** には、会議の状態が表示されます。 <ul><li>**完了**: 1 人以上のスタッフ メンバーと参加者が会議に参加し、会議が終了した場合。 または、1 人以上の参加者が会議に参加し、会議が終了した場合。</li> <li> **出席なし**: 1 人のスタッフが会議に参加し、他のユーザーが参加せず、会議が終了した場合。 </li></ul> </li> <li>**会議の種類** は、仮想予定が Bookings アプリまたは Teams EHR コネクタを介してスケジュールされたかどうかを示します。</li> <li>**出席者** は、会議のスタッフ メンバーと参加者の合計数です。</li> <li>**SMS 送信** は、SMS 通知が出席者に送信されたかどうかを示します。 </li> </li> </ul> |
|**5**   |[**設定**] を選択して [**仮想訪問の分析**] ウィンドウを開きます。 ここから、組織の仮想訪問レポートを無効または有効にし、表内の列を追加または削除できます。 テーブルに希望する情報を表示するには、表に列を追加する必要があります。|
|**6**   |レポートを CSV ファイルにエクスポートすると、オフラインで分析できます。 [**Excel にエクスポート**] を選択してから、[**ダウンロード**] タブの [**ダウンロード**] を選択して、準備のできたレポートをダウンロードします。|

### <a name="duration"></a>期間

:::image type="content" source="media/virtual-visits-usage-report-duration.png" alt-text="番号付き吹き出しを示す仮想訪問の使用状況レポートの [期間] タブのスクリーンショット。" lightbox="media/virtual-visits-usage-report-duration.png":::

|吹き出し |説明  |
|--------|-------------|
|**1**   |各レポートには、このレポートが生成された日付が表示されます。 通常、レポートにはアクティビティの時刻から 24 から 48 時間の遅延が反映されます。 |
|**2**   |X 軸は、レポートで選択された日付範囲です。 縦軸は分数です。<br>特定の日付のドットにポインターを合わせると、特定の日付の平均予定期間または平均ロビー待機時間が表示されます。  |
|**3**   |凡例の項目を選択して、グラフに表示する系列をフィルターできます。 たとえば、[**平均仮想訪問時間**] または [**平均ロビー待機時間**] を選択して、それぞれに関連する情報のみを表示します。 この選択を変更しても、表内の情報は変わりません。 |
|**4**   |この表には、選択した日付範囲で行われた各予定に関する詳細情報が表示されます。 <ul><li>**開始時刻 (UTC)** は、スタッフ メンバーと参加者の両方が会議に参加している日時、または会議で最初のアクティビティが発生した日時です。  </li> <li>**会議 ID** は、会議の一意の ID です。</li> <li>**ロビー待機時間** は、参加者が最初にロビーに参加してから、同じ参加者または別の参加者がスタッフメンバーによって会議に参加できるようになるまでの時間です。</li><li>**期間** は、開始時刻と最後のユーザーが会議を離れる時刻の時間差です。 スタッフ メンバーと参加者の両方が会議に参加しなかった場合、期間は 0 (ゼロ) と表示されます。</li> <li>**状態** には、会議の状態が表示されます。 <ul><li>**完了**: 1 人以上のスタッフ メンバーと参加者が会議に参加し、会議が終了した場合。 または、1 人以上の参加者が会議に参加し、会議が終了した場合。</li> <li> **出席なし**: 1 人のスタッフが会議に参加し、他のユーザーが参加せず、会議が終了した場合。 </li></ul> </li> <li>**会議の種類** は、仮想予定が Bookings アプリまたは Teams EHR コネクタを介してスケジュールされたかどうかを示します。</li> <li>**出席者** は、会議のスタッフ メンバーと参加者の合計数です。</li> <li>**SMS 送信** は、SMS 通知が出席者に送信されたかどうかを示します。 </li> </li> </ul>|
|**5**   |[**設定**] を選択して [**仮想訪問の分析**] ウィンドウを開きます。 ここから、組織の仮想訪問レポートを無効または有効にし、表内の列を追加または削除できます。 テーブルに希望する情報を表示するには、表に列を追加する必要があります。|
|**6**   |レポートを CSV ファイルにエクスポートすると、オフラインで分析できます。 [**Excel にエクスポート**] を選択してから、[**ダウンロード**] タブの [**ダウンロード**] を選択して、準備のできたレポートをダウンロードします。|
### <a name="bookings"></a>Bookings

Bookings アプリを含むライセンスがある場合は、このタブが表示されます。 詳細については、「[Bookings アプリの管理](/microsoftteams/bookings-app-admin?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)」を参照してください。

:::image type="content" source="media/virtual-visits-usage-report-bookings.png" alt-text="番号付き吹き出しを示す仮想訪問の使用状況レポートの [Bookings] タブのスクリーンショット。" lightbox="media/virtual-visits-usage-report-bookings.png":::

|吹き出し |説明  |
|--------|-------------|
|**1**   |各レポートには、このレポートが生成された日付が表示されます。 通常、レポートにはアクティビティの時刻から 24 から 48 時間の遅延が反映されます。 |
|**2**   |X 軸は、レポートで選択された日付範囲です。 縦軸は、Bookings 予定の数です。<br>特定の日付のドットにマウス ポインターを合わせると、その日付に発生した Bookings の予定の数が表示されます。|
|**3**   |この表には、選択した日付範囲で行われた各予定に関する詳細情報が表示されます。 <ul><li>**開始時刻 (UTC)** は、スタッフ メンバーと参加者の両方が会議に参加している日時、または会議で最初のアクティビティが発生した日時です。  </li> <li>**会議 ID** は、会議の一意の ID です。</li> <li>**ロビー待機時間** は、参加者が最初にロビーに参加してから、同じ参加者または別の参加者がスタッフメンバーによって会議に参加できるようになるまでの時間です。</li><li>**期間** は、開始時刻と最後のユーザーが会議を離れる時刻の時間差です。 スタッフ メンバーと参加者の両方が会議に参加しなかった場合、期間は 0 (ゼロ) と表示されます。</li> <li>**状態** には、会議の状態が表示されます。 <ul><li>**完了**: 1 人以上のスタッフ メンバーと参加者が会議に参加し、会議が終了した場合。 または、1 人以上の参加者が会議に参加し、会議が終了した場合。</li> <li> **出席なし**: 1 人のスタッフが会議に参加し、他のユーザーが参加せず、会議が終了した場合。 </li></ul> </li> <li>**会議の種類** は、仮想予定が Bookings アプリまたは Teams EHR コネクタを介してスケジュールされたかどうかを示します。</li> <li>**出席者** は、会議のスタッフ メンバーと参加者の合計数です。</li> <li>**SMS 送信** は、SMS 通知が出席者に送信されたかどうかを示します。 </li> </li> </ul>|
|**4**   |[**設定**] を選択して [**仮想訪問の分析**] ウィンドウを開きます。 ここから、組織の仮想訪問レポートを無効または有効にし、表内の列を追加または削除できます。 テーブルに希望する情報を表示するには、表に列を追加する必要があります。|
|**5**   |レポートを CSV ファイルにエクスポートすると、オフラインで分析できます。 [**Excel にエクスポート**] を選択してから、[**ダウンロード**] タブの [**ダウンロード**] を選択して、準備のできたレポートをダウンロードします。|
### <a name="ehr"></a>EHR

Teams EHR コネクタを含むライセンスがある場合は、このタブが表示されます。 詳細については、「[Cerner EHR への統合](ehr-admin-cerner.md)」または「[エピック EHR への統合](ehr-admin-epic.md)」を参照してください。

:::image type="content" source="media/virtual-visits-usage-report-ehr.png" alt-text="番号付き吹き出しを示す仮想訪問の使用状況レポートの [EHR] タブのスクリーンショット。" lightbox="media/virtual-visits-usage-report-ehr.png":::

|吹き出し |説明  |
|--------|-------------|
|**1**   |各レポートには、このレポートが生成された日付が表示されます。 通常、レポートにはアクティビティの時刻から 24 から 48 時間の遅延が反映されます。 |
|**2**   |X 軸は、レポートで選択された日付範囲です。 縦軸は、EHR 予定の数です。<br>特定の日付のドットにマウス ポインターを合わせると、その日付の EHR 予定の数が表示されます。|
|**3**   |この表には、選択した日付範囲で行われた各予定に関する詳細情報が表示されます。 <ul><li>**開始時刻 (UTC)** は、スタッフ メンバーと参加者の両方が会議に参加している日時、または会議で最初のアクティビティが発生した日時です。  </li> <li>**会議 ID** は、会議の一意の ID です。</li> <li>**ロビー待機時間** は、参加者が最初にロビーに参加してから、同じ参加者または別の参加者がスタッフメンバーによって会議に参加できるようになるまでの時間です。</li><li>**期間** は、開始時刻と最後のユーザーが会議を離れる時刻の時間差です。 スタッフ メンバーと参加者の両方が会議に参加しなかった場合、期間は 0 (ゼロ) と表示されます。</li> <li>**状態** には、会議の状態が表示されます。 <ul><li>**完了**: 1 人以上のスタッフ メンバーと参加者が会議に参加し、会議が終了した場合。 または、1 人以上の参加者が会議に参加し、会議が終了した場合。</li> <li> **出席なし**: 1 人のスタッフが会議に参加し、他のユーザーが参加せず、会議が終了した場合。 </li></ul> </li> <li>**会議の種類** は、仮想予定が Bookings アプリまたは Teams EHR コネクタを介してスケジュールされたかどうかを示します。</li> <li>**出席者** は、会議のスタッフ メンバーと参加者の合計数です。</li> <li>**SMS 送信** は、SMS 通知が出席者に送信されたかどうかを示します。 </li> </li> </ul>|
|**4**   |[**設定**] を選択して [**仮想訪問の分析**] ウィンドウを開きます。 ここから、組織の仮想訪問レポートを無効または有効にし、表内の列を追加または削除できます。 テーブルに希望する情報を表示するには、表に列を追加する必要があります。|
|**5**   |レポートを CSV ファイルにエクスポートすると、オフラインで分析できます。 [**Excel にエクスポート**] を選択してから、[**ダウンロード**] タブの [**ダウンロード**] を選択して、準備のできたレポートをダウンロードします。|

> [!NOTE]
> ビジネス意思決定者などの管理者以外のユーザーがこのレポートにアクセスして表示するためのプライベート プレビューに組織が参加する場合は、[Microsoft にお問い合わせください](mailto:tapmwtanalytics@microsoft.com)。

## <a name="related-articles"></a>関連記事

- [Teams と Bookings アプリを使用した仮想予定](bookings-virtual-visits.md)
- [Teams での仮想アクセス - Epic EHR への統合](ehr-admin-epic.md)
- [Teams での仮想予定 - Cerner EHR への統合](ehr-admin-cerner.md)
