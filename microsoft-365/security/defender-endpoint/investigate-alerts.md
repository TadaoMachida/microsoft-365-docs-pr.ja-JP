---
title: Microsoft Defender for Endpoint アラートの調査
description: 調査オプションを使用して、ネットワークに影響を与えるアラートの詳細、その意味、解決方法を確認します。
keywords: 調査、調査、デバイス、デバイス、アラート キュー、ダッシュボード、IP アドレス、ファイル、提出、提出、詳細分析、タイムライン、検索、ドメイン、URL、IP
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
ms.openlocfilehash: e2ebdffa171266fdc0ec77047c9fecc5be9e56ba
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471167"
---
# <a name="investigate-alerts-in-microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint のアラートを調査する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Defender for Endpoint を試す場合は、 [無料試用版にサインアップしてください。](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatealerts-abovefoldlink)

ネットワークに影響を与えるアラートを調査し、その意味と解決方法を理解します。

アラート キューからアラートを選択して、アラート ページに移動します。 このビューには、アラート タイトル、影響を受けるアセット、詳細サイド ウィンドウ、およびアラート ストーリーが含まれる。

アラート ページから、影響を受けるアセットまたはアラート ストーリー ツリー ビューのエンティティを選択して調査を開始します。 詳細ウィンドウには、選択した内容に関する詳細情報が自動的に表示されます。 ここで表示できる情報の種類については、「 [Microsoft Defender for Endpoint でアラートを確認する」を参照してください](/microsoft-365/security/defender-endpoint/review-alerts)。

## <a name="investigate-using-the-alert-story"></a>アラート ストーリーを使用して調査する

アラート ストーリーは、アラートがトリガーされた理由、その前と後で発生した関連イベント、および他の関連エンティティの詳細を示します。

エンティティはクリック可能で、アラートではないすべてのエンティティは、そのエンティティのカードの右側にある展開アイコンを使用して展開できます。 フォーカスのエンティティは、そのエンティティのカードの左側に青いストライプで示され、最初はタイトルのアラートがフォーカスされます。

エンティティを展開して詳細を一目で確認します。 エンティティを選択すると、詳細ウィンドウのコンテキストがこのエンティティに切り替わるので、詳細情報を確認し、そのエンティティを管理できます。 エンティティ カード *の右側にある ...* を選択すると、そのエンティティで使用可能なすべてのアクションが表示されます。 これらの同じアクションは、エンティティにフォーカスがある場合に詳細ウィンドウに表示されます。

> [!NOTE]
> [アラート ストーリー] セクションには複数のアラートが含まれている場合があります。選択したアラートの前または後に、同じ実行ツリーに関連する追加のアラートが表示されます。

:::image type="content" source="images/alert-story-tree.png" alt-text="アラートにフォーカスが入ったアラート ストーリーと、いくつかの拡張カード" lightbox="images/alert-story-tree.png":::

## <a name="take-action-from-the-details-pane"></a>詳細ウィンドウからアクションを実行する

目的のエンティティを選択すると、詳細ウィンドウが変更され、選択したエンティティの種類に関する情報、利用可能な場合の歴史的な情報が表示され、アラート ページから直接このエンティティに対してアクションを実行するコントロールが提供されます。

調査が完了したら、開始したアラートに戻り、アラートの状態を **[** 解決済み] としてマークし、False アラートまたは True アラートとして **分類します**。 アラートを分類すると、この機能を調整して、より真のアラートと誤ったアラートを減らします。

真のアラートとして分類する場合は、下の図に示すように、決定を選択できます。

:::image type="content" source="images/alert-details-resolved-true.png" alt-text="解決済みアラートと決定ドロップダウンが展開された詳細ウィンドウ" lightbox="images/alert-details-resolved-true.png":::

業務用アプリケーションで誤ったアラートが発生している場合は、この種類のアラートを今後回避するために抑制ルールを作成します。

:::image type="content" source="images/alert-false-suppression-rule.png" alt-text="抑制ルールが強調表示された詳細ウィンドウのアクションと分類" lightbox="images/alert-false-suppression-rule.png":::

> [!TIP]
> 上記に記載されていない問題が 🙂 発生した場合は、ボタンを使用してフィードバックを提供するか、サポート チケットを開きます。


## <a name="related-topics"></a>関連項目
- [Microsoft Defender for Endpoint アラート キューを表示して整理する](alerts-queue.md)
- [エンドポイント通知の Microsoft Defender の管理](manage-alerts.md)
- [Defender for Endpoint アラートに関連付けられたファイルを調査する](investigate-files.md)
- [Defender for Endpoint Devices リストのデバイスを調査する](investigate-machines.md)
- [Defender for Endpoint アラートに関連付けられている IP アドレスを調査する](investigate-ip.md)
- [Defender for Endpoint アラートに関連付けられているドメインを調査する](investigate-domain.md)
- [Defender for Endpoint のユーザー アカウントを調査する](investigate-user.md)


