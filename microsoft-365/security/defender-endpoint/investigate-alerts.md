---
title: Microsoft Defender for Endpointアラートを調査する
description: 調査オプションを使用して、ネットワークに影響を与えているアラート、その意味、およびそれらを解決する方法に関する詳細を取得します。
keywords: 調査, 調査, デバイス, デバイス, アラート キュー, ダッシュボード, IP アドレス, ファイル, 送信, 提出, 詳細分析, タイムライン, 検索, ドメイン, URL, IP
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: e4d379ee476276d24b683878bc4978addf220ced
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665802"
---
# <a name="investigate-alerts-in-microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpointのアラートを調査する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Defender for Endpoint を試す場合は、 [無料試用版にサインアップしてください。](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatealerts-abovefoldlink)

ネットワークに影響を与えているアラートを調査し、その意味と解決方法を理解します。

アラート キューからアラートを選択して、アラート ページに移動します。 このビューには、アラート タイトル、影響を受けるアセット、詳細サイド ウィンドウ、アラート ストーリーが含まれます。

アラート ページで、アラート ストーリー ツリー ビューで影響を受ける資産またはエンティティのいずれかを選択して、調査を開始します。 詳細ウィンドウには、選択した内容に関する詳細情報が自動的に入力されます。 ここで表示できる情報の種類については、[Microsoft Defender for Endpointのアラートの確認に](/microsoft-365/security/defender-endpoint/review-alerts)関する記事を参照してください。

## <a name="investigate-using-the-alert-story"></a>アラート ストーリーを使用して調査する

アラート ストーリーでは、アラートがトリガーされた理由、前後で発生した関連イベント、その他の関連エンティティが詳しく説明されています。

エンティティはクリック可能であり、アラートではないすべてのエンティティは、そのエンティティのカードの右側にある展開アイコンを使用して展開できます。 フォーカスのあるエンティティは、そのエンティティのカードの左側に青いストライプで示され、最初はタイトルのアラートがフォーカスされています。

エンティティを展開して、一目で詳細を表示します。 エンティティを選択すると、詳細ウィンドウのコンテキストがこのエンティティに切り替わります。さらに詳しい情報を確認したり、そのエンティティを管理したりできます。 エンティティ カードの右側にある *...* を選択すると、そのエンティティで使用可能なすべてのアクションが表示されます。 これらの同じアクションは、そのエンティティがフォーカスされているときに、詳細ウィンドウに表示されます。

> [!NOTE]
> アラート ストーリー セクションには複数のアラートが含まれている場合があり、選択したアラートの前後に同じ実行ツリーに関連する追加のアラートが表示されます。

:::image type="content" source="images/alert-story-tree.png" alt-text="アラートがフォーカスされ、一部の展開されたカードが含まれるアラート ストーリー" lightbox="images/alert-story-tree.png":::

## <a name="take-action-from-the-details-pane"></a>詳細ウィンドウからアクションを実行する

目的のエンティティを選択すると、詳細ウィンドウが変更され、選択したエンティティの種類に関する情報、使用可能な場合の履歴情報が表示され、アラート ページから直接このエンティティに **対してアクションを実行** するためのコントロールが提供されます。

調査が完了したら、開始したアラートに戻り、アラートの状態を **解決済み** としてマークし、 **False アラート** または **True アラート** として分類します。 アラートを分類すると、この機能を調整して、より真のアラートを提供し、誤ったアラートを減らすのに役立ちます。

このアラートを真のアラートとして分類する場合は、下の図に示すように、決定を選択することもできます。

:::image type="content" source="images/alert-details-resolved-true.png" alt-text="解決されたアラートと決定ドロップダウンが展開された詳細ウィンドウ" lightbox="images/alert-details-resolved-true.png":::

基幹業務アプリケーションで誤ったアラートが発生した場合は、今後この種類のアラートを回避する抑制ルールを作成します。

:::image type="content" source="images/alert-false-suppression-rule.png" alt-text="抑制ルールが強調表示された詳細ウィンドウのアクションと分類" lightbox="images/alert-false-suppression-rule.png":::

> [!TIP]
> 上記以外の問題が発生した場合は、ボタンを 🙂 使用してフィードバックを提供するか、サポート チケットを開きます。

## <a name="related-topics"></a>関連項目

- [Microsoft Defender for Endpoint アラート キューを表示して整理する](alerts-queue.md)
- [Microsoft Defender for Endpointアラートを管理する](manage-alerts.md)
- [Defender for Endpoint アラートに関連付けられているファイルを調査する](investigate-files.md)
- [Defender for Endpoint Devices の一覧のデバイスを調査する](investigate-machines.md)
- [Defender for Endpoint アラートに関連付けられている IP アドレスを調査する](investigate-ip.md)
- [Defender for Endpoint アラートに関連付けられているドメインを調査する](investigate-domain.md)
- [Defender for Endpoint のユーザー アカウントを調査する](investigate-user.md)
