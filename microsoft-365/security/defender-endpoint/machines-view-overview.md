---
title: デバイス一覧
description: デバイスの一覧で使用できる機能 (並べ替え、フィルター処理、調査を強化するためのリストのエクスポートなど) について説明します。
keywords: 並べ替え, フィルター, エクスポート, csv, デバイス名, ドメイン, 最後に見た, 内部 IP, 正常性状態, アクティブなアラート, アクティブなマルウェア検出, 脅威カテゴリ, レビュー アラート, ネットワーク, 接続, マルウェア, 種類, パスワード盗難, ランサムウェア, エクスプロイト, 脅威, 一般的なマルウェア, 不要なソフトウェア
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 232f27b9edb23e932d49cf33e026d22abfbe72dd
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617328"
---
# <a name="device-inventory"></a>デバイス一覧

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender 脆弱性の管理](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Defender for Endpoint を試す場合は、 [無料試用版にサインアップしてください。](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-machinesview-abovefoldlink)

**デバイス インベントリ** には、アラートが生成されたネットワーク内のデバイスの一覧が表示されます。 既定では、過去 30 日間に表示されたデバイスがキューに表示されます。

一目で、ドメイン、リスク レベル、OS プラットフォームなどの情報が表示され、最も危険なデバイスを簡単に識別できます。

> [!NOTE]
> デバイス インベントリは、さまざまなMicrosoft 365 Defender サービスで使用できます。 使用できる情報は、ライセンスによって異なります。 プラン 2 を使用すると、最も完全な機能[セットMicrosoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)取得できます。

デバイスリスト ビューをカスタマイズするには、いくつかのオプションを選択できます。 上部のナビゲーションでは、次の操作を行うことができます。

- 列を追加または削除する
- 一覧全体を CSV 形式でエクスポートする
- ページごとに表示するアイテムの数を選択する
- フィルターの適用

オンボード プロセス中に、センサー データの報告を開始すると、 **デバイスの一覧** にデバイスが徐々に設定されます。 このビューを使用して、オンボードされたエンドポイントがオンラインになった時点を追跡したり、オフライン分析用の CSV ファイルとして完全なエンドポイント 一覧をダウンロードしたりできます。

> [!NOTE]
> デバイスリストをエクスポートすると、組織内のすべてのデバイスが含まれます。 組織の規模によっては、ダウンロードにかなりの時間がかかる場合があります。 リストを CSV 形式でエクスポートすると、フィルター処理されていない方法でデータが表示されます。 CSV ファイルには、ビュー自体に適用されるフィルター処理に関係なく、組織内のすべてのデバイスが含まれます。

:::image type="content" source="images/device-inventory.png" alt-text="デバイスの一覧" lightbox="images/device-inventory.png":::

## <a name="sort-and-filter-the-device-list"></a>デバイスの一覧を並べ替え、フィルター処理する

次のフィルターを適用して、アラートの一覧を制限し、より焦点を絞ったビューを取得できます。

### <a name="device-name"></a>デバイス名

Microsoft Defender for Endpointオンボード プロセス中、MDE にオンボードされたデバイスは、センサー データの報告を開始すると、徐々にデバイス インベントリに入力されます。 この後、デバイス インベントリは、デバイス検出プロセスを通じてネットワーク内で検出されたデバイスによって設定されます。 デバイス インベントリには、次の 3 つのタブがあります。

- **コンピューターとモバイル**: エンタープライズ エンドポイント (ワークステーション、サーバー、モバイル デバイス)
- **ネットワーク デバイス**: ルーターやスイッチなどのデバイス
- **IoT デバイス**: プリンターやカメラなどのデバイス

## <a name="navigate-to-the-device-inventory-page"></a>[デバイス インベントリ] ページに移動する

[Microsoft 365 Defender ポータル](/microsoft-365/security/defender-business/mdb-get-started)の **[エンドポイント**] ナビゲーション メニューから **[デバイス インベントリ**] を選択して、デバイス インベントリ ページにアクセスします。

## <a name="device-inventory-overview"></a>デバイス インベントリの概要

デバイス インベントリが [ **コンピューターとモバイル** ] タブで開きます。デバイス名、ドメイン、リスク レベル、露出レベル、OS プラットフォーム、オンボード状態、センサーの正常性状態などの情報を一目で確認して、最も危険にさらされているデバイスを簡単に識別できます。

**[オンボード状態] 列を** 使用して、検出されたデバイスと、既にMicrosoft Defender for Endpointにオンボードされているデバイスで並べ替えとフィルター処理を行います。

![デバイスの一覧を含むデバイスの一覧の画像。](images/device-inventory.png)

[ **ネットワーク デバイス** ] タブと [ **IoT デバイス** ] タブには、ベンダー、モデル、デバイスの種類などの情報も表示されます。

![ネットワーク デバイスの一覧の画像。](images/device-inventory-networkdevices.png)

> [!NOTE]
> デバイス検出と [Microsoft Defender for IoT](/azure/defender-for-iot/organizations/) および [Corelight](https://corelight.com/integrations/iot-security) との統合は、完全な OT/IOT 資産インベントリの検索、識別、セキュリティ保護に役立ちます。 これらの統合で検出されたデバイスは、[ **IoT デバイス** ] タブに表示されます。詳細については、「 [デバイス検出の統合](device-discovery.md#device-discovery-integrations)」を参照してください。
>
> Defender for IoT が構成されている場合は、そこにデバイスを表示することもできます。 [組織のデバイス インベントリを使用して IoT デバイスを管理する方法に関するページを参照してください](/azure/defender-for-iot/organizations/how-to-manage-device-inventory-for-organizations)。

各デバイス インベントリ タブの上部には、デバイスの合計数、まだオンボードされていないデバイスの数、組織のリスクが高いと特定されたデバイスの数が表示されます。 この情報を使用すると、セキュリティ体制の改善のためにデバイスの優先順位を付けることができます。

[ネットワーク デバイスと IoT デバイスの **新しく検出された** デバイス数] タブには、検出された新しいデバイスの数 (過去 7 日間) が現在のビューに一覧表示されます。

![検出された新しいデバイス数の画像。](images/new-discovered-devices.png)

## <a name="explore-the-device-inventory"></a>デバイス インベントリを調べる

デバイス インベントリ ビューをカスタマイズするには、いくつかのオプションを選択できます。 各タブの上部のナビゲーションでは、次の操作を行うことができます。

- 名前でデバイスを検索する
- 最近使用した IP アドレスまたは IP アドレス プレフィックスでデバイスを検索する
- 列を追加または削除する
- オフライン分析のためにリスト全体を CSV 形式でエクスポートする
- 表示する日付範囲を選択する
- フィルターの適用

> [!NOTE]
> デバイスリストをエクスポートすると、組織内のすべてのデバイスが含まれます。 組織の規模によっては、ダウンロードにかなりの時間がかかる場合があります。 リストを CSV 形式でエクスポートすると、フィルター処理されていない方法でデータが表示されます。 CSV ファイルには、ビュー自体に適用されるフィルター処理に関係なく、組織内のすべてのデバイスが含まれます。

各デバイス インベントリ タブで使用できる並べ替え機能とフィルター機能を使用して、より焦点を絞ったビューを取得し、組織内のデバイスを評価および管理するのに役立ちます。

各タブの上部のカウントは、現在のビューに基づいて更新されます。

## <a name="use-filters-to-customize-the-device-inventory-views"></a>フィルターを使用してデバイス インベントリ ビューをカスタマイズする

フィルター | 説明
:---|:---
**リスク レベル** </br> | リスク レベルは、デバイス上のアクティブなアラートの種類や重大度など、要因の組み合わせに基づいて、デバイスの全体的なリスク評価を反映します。 アクティブなアラートを解決し、修復アクティビティを承認し、後続のアラートを抑制すると、リスク レベルが低下する可能性があります。
**露出レベル** </br> | 露出レベルは、保留中のセキュリティ推奨事項の累積的な影響に基づいて、デバイスの現在の露出を反映します。 可能なレベルは低、中、高です。 露出が低いということは、デバイスが悪用の影響を受けにくいという意味です。 </br> </br> 露出レベルに "データが利用できない" と表示される場合、次のような理由がいくつかあります。</br>- デバイスが 30 日間以上レポートを停止しました。 その場合は非アクティブと見なされ、露出は計算されません。</br>- デバイス OS がサポートされていません - [Microsoft Defender for Endpointの最小要件を](/microsoft-365/security/defender-endpoint/minimum-requirements)参照してください。</br>- 古いエージェントを持つデバイス (可能性は低い)。
**Tags** </br> | 個々のデバイスに追加したグループ化とタグ付けに基づいて、リストをフィルター処理します。 [デバイス タグの作成と管理に関するページを](machine-tags.md)参照してください。
**デバイスの値**</br> | デバイスが高い値と低い値のどちらとしてマークされているかに基づいて、リストをフィルター処理します。
**除外状態** </br> | デバイスが除外されたかどうかに基づいて、一覧をフィルター処理します。 詳細については、「デバイスを [除外する](exclude-devices.md)」を参照してください。
**OS プラットフォーム** </br>| 調査対象の OS プラットフォームでフィルター処理する </br></br>(_コンピューターとモバイルおよび IoT デバイスのみ_)
**最初に見た** </br> | デバイスがネットワークで初めて表示されたとき、またはデバイスがMicrosoft Defender for Endpoint センサーによって最初に報告されたタイミングに基づいてビューをフィルター処理します。</br></br>(_コンピューターとモバイルおよび IoT デバイスのみ_)
**Windows バージョン** </br> | 調査対象の Windows バージョンでフィルター処理します。</br></br> (_コンピューターとモバイルのみ_)
**センサーの正常性状態** </br> | Microsoft Defender for Endpointにオンボードされているデバイスの場合は、次のセンサーの正常性状態でフィルター処理します。</br> - **アクティブ**: センサー データをサービスにアクティブに報告しているデバイス。</br> - **非アクティブ**: 7 日以上シグナルの送信を停止したデバイス。 </br> - **構成が正しくない**: サービスとの通信が妨げているか、センサー データを送信できないデバイス。 </br> 構成が正しくないデバイスは、さらに次のように分類できます。 </br>  - センサー データなし </br>  - 通信の障害 </br>  正しく構成されていないデバイスの問題に対処する方法の詳細については、「 [異常なセンサーを修正](/microsoft-365/security/defender-endpoint/fix-unhealthy-sensors)する」を参照してください。</br></br> (_コンピューターとモバイルのみ_)
**オンボードの状態** </br> | オンボード状態は、デバイスが現在Microsoft Defender for Endpointにオンボードされているかどうかを示します。 次の状態でフィルター処理できます。 </br> - **オンボード済み**: エンドポイントはMicrosoft Defender for Endpointにオンボードされます。  </br> - **オンボード可能**: エンドポイントは、サポートされているデバイスとしてネットワーク内で検出されましたが、現在オンボードされていません。 Microsoft では、これらのデバイスのオンボードを非常に推奨しています。 </br> - **サポートされていません**:エンドポイントはネットワーク内で検出されましたが、Microsoft Defender for Endpointではサポートされていません。 </br> - **情報が不十分** です。システムはデバイスのサポート可能性を判断できませんでした。</br></br> (_コンピューターとモバイルのみ_)
**ウイルス対策の状態** </br> | ウイルス対策の状態が無効になっているか、更新されていないか不明かに基づいてビューをフィルター処理します。</br></br> (_コンピューターとモバイルのみ_)
**グループ** </br> | 調査対象のグループに基づいてリストをフィルター処理します。 </br></br> (_コンピューターとモバイルのみ_)
**Managed by** </br> | 管理対象は、デバイスの管理方法を示します。 次の条件でフィルター処理できます。</br> - Microsoft Defender for Endpoint</br> - Microsoft エンドポイント マネージャー (MEM)、テナント接続による Microsoft Configuration Managerとの共同管理を含む</br>- Microsoft Configuration Manager (ConfigMgr)</br> - 不明: 古い Windows バージョン、GPO 管理、または別のサード パーティ MDM が実行されている可能性があります。</br></br> (_コンピューターとモバイルのみ_) 
**デバイスの種類** </br> | 調査するデバイスの種類でフィルター処理します。</br></br> (_IoT デバイスのみ_)

## <a name="use-columns-to-customize-the-device-inventory-views"></a>列を使用してデバイス インベントリ ビューをカスタマイズする

表示から列を追加または削除し、使用可能な列ヘッダーをクリックしてエントリを並べ替えることができます。

[ **コンピューターとモバイル** ] タブで、[ **列のカスタマイズ** ] を選択して使用可能な列を表示します。 次の図では、既定値がチェックされます。

![コンピューターとモバイルの画像](images/computerandmobilescolumns.png)

[ **ネットワーク デバイス** ] タブで、[ **列のカスタマイズ** ] を選択して、使用可能な列を表示します。 次の図では、既定値がチェックされます。

![ネットワーク デバイス列の画像](images/networkdevicescolumns.png)

[ **IoT デバイス** ] タブで、[ **列のカスタマイズ** ] を選択して、使用可能な列を表示します。 次の図では、既定値がチェックされます。

![IoT デバイス列の画像](images/iotdevicescolumns.png)

## <a name="related-articles"></a>関連記事

[Microsoft Defender for Endpoint デバイスの一覧のデバイスを調査する](investigate-machines.md)
