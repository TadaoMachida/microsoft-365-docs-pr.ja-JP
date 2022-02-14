---
title: 複数地域の機能 (Microsoft Teams
ms.reviewer: daro
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
- m365solution-scenario
- m365solution-spintranet
ms.localizationpriority: medium
description: 複数地域でのTeamsのMicrosoft 365について説明します。
ms.openlocfilehash: 0315a9ff0429c5e00c662bd7345a3b6a39a591c3
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2022
ms.locfileid: "62805870"
---
# <a name="multi-geo-capabilities-in-microsoft-teams"></a>複数地域の機能 (Microsoft Teams

複数地域の機能を使用Teams、Teamsの場所に保存するチャット データの保存を有効にできます。 チャット データは、プライベート メッセージ、チャネル メッセージ、チャットで使用される画像などのチャット メッセージで構成されます。

Teamsユーザーとグループに優先データの場所 (PDL) を使用して、データを格納する場所を決定します。 PDL が設定されていないか無効な場合、データはテナントの中央の場所に格納されます。

> [!NOTE]
> 2021 年 7 月にTeamsの複数地域機能が展開されました。 チャットメッセージとチャネル メッセージは、今後数四半期で自動的に正しい地域の場所に移行されます。 テナントが最初の同期を完了した後、新しい PDL 変更が処理され、それ以降の新しい PDL 変更は受信順にキューに入れ、処理されます。

## <a name="user-chat"></a>ユーザー チャット

ユーザー チャットには、1 対 1、1 対多、プライベート会議メッセージが含まれます。

新しいユーザーが作成されると、Teamsの PDL を読み取り、すべてのチャット データをその地域の場所に保存します。

既存のユーザーの場合、管理者がユーザーの PDL を追加または変更すると、そのユーザーのチャット データが移行キューに追加され、指定した地域の場所に移動されます。

1 対 1 または 1 対多のチャットの保存場所は、チャットを作成したユーザーの PDL に基づいて行います。 そのユーザーの PDL が変更された場合、チャットは新しい地域の場所に移行されます。 会議チャットの保存場所は、会議開催者の PDL に基づいて行います。

ユーザーのデータの現在の場所をTeams、PowerShell に接続Teams[次の](/powershell/module/teams/connect-microsoftteams)コマンドを実行します。

```PowerShell
Get-MultiGeoRegion -EntityType User -EntityId <UPN>
```

## <a name="channel-messages"></a>チャネル メッセージ

各Microsoft 365グループには、関連するデータを格納する地域の場所を示す優先データの場所 (PDL) があります。 Teamsチームに関連付けられたグループの PDL を使用して、そのチームのチャネル メッセージング データを格納する場所を決定します。 これには、チャネル会議内で発生するプライベート チャネルとチャットが含まれます。

ユーザーが新しいチームを作成すると、そのユーザーの PDL によって、グループに割り当てられている PDL がMicrosoft 365されます。 グループ PDL は、そのチームのデータの格納場所を決定します。 そのユーザーの PDL が後で変更された場合、グループの PDL は変更されません。

既存のチームの場合、管理者がチームをバックアップする Microsoft 365 グループの PDL を追加または変更すると、そのチームのチャネル メッセージング データが移行キューに追加され、指定した地域の場所に移動されます。

グループグループの PDL をMicrosoft 365、選択Teamsに移行するデータをキューに入れられます。 ただし、グループに関連付けられているSharePointを自動的に移行するわけではありません。 「サイトを別の地域の場所に移動する」の手順に従って[、SharePointを個別に移動する必要があります](/microsoft-365/enterprise/move-sharepoint-between-geo-locations)。 異なる場所にある 1 つのグループのデータとTeamsデータSharePointしないように、両方の手順を実行してください。

チームのデータの現在の場所を見つけるには、[PowerShell Teamsに](/powershell/module/teams/connect-microsoftteams)接続し、次のコマンドを実行します。

```PowerShell
Get-MultiGeoRegion -EntityType Group -EntityId <GroupObjectId>
```

## <a name="user-experience"></a>ユーザー エクスペリエンス

Teamsジオはエンド ユーザーにシームレスに接続できます。 ユーザーまたはグループの PDL を変更すると、それぞれのデータが移行のためにキューに入れ、移行が自動的に行われます。移行の実行中にアクティブな場合でも、ユーザーまたは Teams クライアントに影響はありません。

## <a name="see-also"></a>関連項目

[Microsoft 365 Multi-Geo テナントの構成](/microsoft-365/enterprise/multi-geo-tenant-configuration)

[複数地域環境の管理](administering-a-multi-geo-environment.md)

[複数地域環境での Exchange Online メールボックスの管理](administering-exchange-online-multi-geo.md)
