---
title: ロールベースのアクセス制御のカスタム ロール
description: Microsoft 365 Defender ポータルでカスタム ロールを管理する方法について説明します
keywords: アクセス、アクセス許可、Microsoft 365 Defender、M365、セキュリティ、MCAS、Cloud App Security、Microsoft Defender for Endpoint、スコープ、スコープ、RBAC、ロールベースのアクセス、カスタム ロールベースのアクセス、ロールベースの認証、MDO の RBAC、ロール、ロール グループ、アクセス許可継承、きめ細かなアクセス許可
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 94330e319eeb44618c1e11b27da7b3d63c08d203
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731353"
---
# <a name="custom-roles-in-role-based-access-control-for-microsoft-365-defender"></a>Microsoft 365 Defenderのロールベースのアクセス制御のカスタム ロール

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**適用対象:**

- Microsoft 365 Defender
 
Microsoft 365 Defenderへのアクセスに使用できるロールには、次の 2 種類があります。
- **グローバル Azure Active Directory (AD) ロール**
- **カスタムの役割**

Microsoft 365 Defenderへのアクセスは、[Azure Active Directoryのグローバル ロール (AAD) を](m365d-permissions.md)使用してまとめて管理できます。

特定の製品データへのアクセスをより柔軟に制御する必要がある場合は、各セキュリティ ポータルを使用してカスタム ロールを作成することで、Microsoft 365 Defenderアクセスを管理することもできます。  

たとえば、Microsoft Defender for Endpointによって作成されたカスタム ロールでは、Microsoft 365 Defender ポータル内のエンドポイント データを含む、関連する製品データへのアクセスが許可されます。 同様に、Microsoft Defender for Office 365によって作成されたカスタム ロールでは、Microsoft 365 Defender ポータル内の電子メール &コラボレーション データを含む、関連する製品データへのアクセスが許可されます。

既存のカスタム ロールを持つユーザーは、追加の構成を必要とせずに、既存のワークロードのアクセス許可に従って、Microsoft 365 Defender ポータルのデータにアクセスできます。

## <a name="create-and-manage-custom-roles"></a>カスタム ロールの作成と管理
カスタム ロールとアクセス許可は、次の各セキュリティ ポータルを使用して作成および個別に管理できます。 

- Microsoft Defender for Endpoint – [Microsoft Defender for Endpointでロールを編集する](../defender-endpoint/user-roles.md)
- Microsoft Defender for Office 365 – [セキュリティ & コンプライアンス センターのアクセス許可](../office-365-security/permissions-in-the-security-and-compliance-center.md?preserve-view=true&view=o365-worldwide)
- Microsoft Defender for Cloud Apps – [管理者アクセスを管理する](/cloud-app-security/manage-admins)

個々のポータルを通じて作成された各カスタム ロールでは、関連する製品ポータルのデータにアクセスできます。 たとえば、Microsoft Defender for Endpointによって作成されたカスタム ロールでは、Defender for Endpoint データへのアクセスのみが許可されます。

> [!TIP]
> アクセス許可とロールには、ナビゲーション ウィンドウで [アクセス許可] &ロールを選択して、Microsoft 365 Defender ポータルからアクセスすることもできます。 Microsoft Defender for Cloud Appsへのアクセスは、Defender for Cloud Apps ポータルを使用して管理され、Microsoft Defender for Identityへのアクセスも制御します。  [Microsoft Defender for Cloud Apps](/cloud-app-security/manage-admins)を参照してください

> [!NOTE]
> Microsoft Defender for Cloud Appsで作成されたカスタム ロールは、Microsoft Defender for Identity データにもアクセスできます。 ユーザー グループ管理者、または App/instance 管理者Microsoft Defender for Cloud Appsロールを持つユーザーは、Microsoft 365 Defender ポータルからMicrosoft Defender for Cloud Appsデータにアクセスできません。

## <a name="manage-permissions-and-roles-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender ポータルでアクセス許可とロールを管理する
アクセス許可とロールは、Microsoft 365 Defender ポータルで管理することもできます。

1. security.microsoft.com でMicrosoft 365 Defender ポータルにサインインします。
2. ナビゲーション ウィンドウで、**[アクセス許可と役割]** を選択します。
3. **[アクセス許可]** ヘッダーの下にある [ロール] を選択 **します**。

> [!NOTE]
> これは、Defender for Office 365および Defender for Endpoint にのみ適用されます。 他のワークロードのアクセスは、関連するポータルで行う必要があります。


## <a name="required-roles-and-permissions"></a>必要な役割と権限
次の表に、各ワークロードの各統合エクスペリエンスにアクセスするために必要なロールとアクセス許可の概要を示します。 次の表で定義されているロールは、個々のポータルのカスタム ロールを参照し、同様に名前が付けられている場合でも、Azure ADのグローバル ロールには接続されません。

> [!NOTE]
> インシデント管理には、インシデントの一部であるすべての製品の管理権限が必要です。
 
| **Microsoft 365 Defenderには、次のいずれかのロールが必要です。**  | **Defender for Endpoint には、次のいずれかのロールが必要です**  | **Defender for Office 365には、次のいずれかのロールが必要です。** | **Defender for Cloud アプリには、次のいずれかのロールが必要です** | 
|---------|---------|---------|---------|
| 調査データの表示: <ul><li>[アラート] ページ</li> <li>アラート キュー</li> <li>インシデント</li>  <li>インシデント キュー</li> <li>アクション センター</li></ul>| データの表示 - セキュリティ操作 | <ul><li>アラートを表示専用で管理する </li> <li>組織の構成</li><li>監査ログ</li> <li>表示専用の監査ログ</li> <li>セキュリティ閲覧者</li> <li>セキュリティ管理者</li><li>表示専用の受信者</li></ul>  | <ul><li>グローバル管理者</li> <li>セキュリティ管理者</li> <li>コンプライアンス管理者</li> <li>セキュリティ オペレーター</li> <li>セキュリティ閲覧者</li> <li>グローバルリーダー</li></ul> |
| ハンティング データの表示 | データの表示 - セキュリティ操作 | <ul><li>セキュリティ閲覧者</li> <li>セキュリティ管理者</li> <li>表示専用の受信者</li> | <ul><li>グローバル管理者</li> <li>セキュリティ管理者</li> <li>コンプライアンス管理者</li> <li>セキュリティ オペレーター</li> <li>セキュリティ閲覧者</li> <li>グローバルリーダー</li></ul> |
| アラートとインシデントの管理 | アラートの調査 | <ul><li>アラートの管理</li> <li>セキュリティ管理者</li> | <ul><li>グローバル管理者</li> <li>セキュリティ管理者</li> <li>コンプライアンス管理者</li> <li>セキュリティ オペレーター</li> <li>セキュリティ閲覧者</li></ul> |
| アクション センターの修復 | アクティブな修復アクション – セキュリティ操作 | 検索と消去 | |
| カスタム検出の設定 | セキュリティ設定の管理 |<ul><li>アラートの管理</li> <li>セキュリティ管理者</li></ul> | <ul><li>グローバル管理者</li> <li>セキュリティ管理者</li> <li>コンプライアンス管理者</li> <li>セキュリティ オペレーター</li> <li>セキュリティ閲覧者</li> <li>グローバルリーダー</li></ul> |
| 脅威の分析 | アラートとインシデント データ: <ul><li>データの表示 - セキュリティ操作</li></ul>TVM の軽減策:<ul><li>データの表示 - 脅威と脆弱性の管理</li></ul> | アラートとインシデント データ:<ul> <li>アラートを表示専用で管理する</li> <li>アラートの管理</li> <li>組織の構成</li><li>監査ログ</li> <li>表示専用の監査ログ</li><li>セキュリティ閲覧者</li> <li>セキュリティ管理者</li><li>表示専用の受信者</li> </ul> 禁止された電子メールの試行: <ul><li>セキュリティ閲覧者</li> <li>セキュリティ管理者</li><li>表示専用の受信者</li> | Defender for Cloud アプリまたは MDI ユーザーには使用できません |

たとえば、Microsoft Defender for Endpointからハンティング データを表示するには、データセキュリティ操作のアクセス許可を表示する必要があります。  

同様に、Microsoft Defender for Office 365からのハンティング データを表示するには、ユーザーは次のいずれかのロールを必要とします。  

- データ セキュリティ操作を表示する
- セキュリティ閲覧者
- セキュリティ管理者
- 表示専用の受信者

## <a name="related-topics"></a>関連項目
- [RBAC ロール](../office-365-security/migrate-to-defender-for-office-365-onboard.md#rbac-roles)
- [Microsoft 365 Defender へのアクセスを管理する](m365d-permissions.md)
- [Defender for Cloud アプリの管理者アクセスを管理する](/cloud-app-security/manage-admins)
