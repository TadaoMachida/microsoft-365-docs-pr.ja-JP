---
title: 監査のオンとオフを切り替える
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: e893b19a-660c-41f2-9074-d3631c95a014
ms.custom: seo-marvel-apr2020
description: 管理者が監査ログを検索する機能を有効または無効にするには、Microsoft 365 コンプライアンス センターの監査ログ検索機能を有効または無効にする方法を示します。
ms.openlocfilehash: 793c76d45f2cd7aed43a959dfcb94edeb9869310
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/26/2021
ms.locfileid: "58575326"
---
# <a name="turn-auditing-on-or-off"></a>監査のオンとオフを切り替える

監査ログは、エンタープライズ組織と組織のMicrosoft 365既定Office 365オンになります。 ただし、新しい組織または組織Microsoft 365をOffice 365、組織の監査状態を確認する必要があります。 手順については、この記事の [「組織の](#verify-the-auditing-status-for-your-organization) 監査状態を確認する」セクションを参照してください。 

Microsoft 365 コンプライアンス センター で監査を有効にすると、組織のユーザーと管理者のアクティビティが監査ログに記録され、ユーザーに割り当てられたライセンスに応じて 90 日間、最大 1 年間保持されます。 ただし、監査ログ データを記録および保持しない理由が組織にある場合があります。 このような場合、グローバル管理者は、管理者が監査をオフにMicrosoft 365。

> [!IMPORTANT]
> Microsoft 365 で監査をオフにした場合、Office 365 管理アクティビティ API または Azure Sentinel を使用して組織の監査データにアクセスすることはできません。 この記事の手順に従って監査をオフにした場合、Microsoft 365 コンプライアンス センター を使用して監査ログを検索したり、Exchange Online PowerShell で **Search-UnifiedAuditLog** コマンドレットを実行したりすると、結果は返されません。 つまり、監査ログは、管理アクティビティ API または Azure Sentinel Office 365使用できません。
  
## <a name="before-you-turn-auditing-on-or-off"></a>監査を有効またはオフにする前に

- 組織で監査を有効またはExchange Onlineするには、監査ログの役割を割りMicrosoft 365があります。 既定では、この役割は、管理センターの [アクセス許可] ページの[コンプライアンス管理] および [組織の管理Exchange割り当てられます。 グループ内のグローバルMicrosoft 365は、組織の管理役割グループのメンバー Exchange Online。

    > [!NOTE]
    > 監査を有効またはオフに切り替Exchange Onlineユーザーにアクセス許可を割り当てる必要があります。 ユーザーに[アクセス許可] ページの[監査ログ] 役割を割り当てるMicrosoft 365 コンプライアンス センター、監査を有効またはオフにすることはできません。 これは、基になるコマンドレットが PowerShell コマンドレットExchange Onlineです。

- 監査ログの検索に関する詳細な手順については、「監査ログの検索 [」を参照してください](search-the-audit-log-in-security-and-compliance.md)。 管理アクティビティ API の詳細Microsoft 365、「管理 API の概要」を参照Microsoft 365[してください](/office/office-365-management-api/get-started-with-office-365-management-apis)。

## <a name="verify-the-auditing-status-for-your-organization"></a>組織の監査状態を確認する

組織の監査が有効になっていることを確認するには、PowerShell で次のコマンド[Exchange Onlineできます](/powershell/exchange/connect-to-exchange-online-powershell)。

```powershell
Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
```

`True` _UnifiedAuditLogIngestionEnabled_ プロパティの値は、監査が有効になっていることを示します。 値は `False` 、監査が有効になっていることを示します。

## <a name="turn-on-auditing"></a>監査を有効にする

組織で監査を有効にしていない場合は、組織で有効にするか、PowerShell Microsoft 365 コンプライアンス センターを使用Exchange Onlineできます。 監査ログを検索するときに結果を返す前に、監査を有効にしてから数時間かかる場合があります。
  
### <a name="use-the-compliance-center-to-turn-on-auditing"></a>コンプライアンス センターを使用して監査を有効にする

1. <https://compliance.microsoft.com> に移動し、サインインします。

2. 左側のナビゲーション ウィンドウで、[監査] をMicrosoft 365 コンプライアンス センターを **クリックします**。

   組織の監査が有効ではない場合は、ユーザーと管理アクティビティの記録を開始するように求めるバナーが表示されます。

   ![[監査] ページのバナー。](../media/AuditingBanner.png)

3. [ユーザーと **管理アクティビティの記録を開始する] バナーをクリック** します。

   変更を有効にするには、最大 60 分かかる場合があります。

### <a name="use-powershell-to-turn-on-auditing"></a>PowerShell を使用して監査を有効にする

1. [Exchange Online PowerShell に接続します](/powershell/exchange/connect-to-exchange-online-powershell)。

2. 次の PowerShell コマンドを実行して監査を有効にする。

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
    ```

    変更を有効にするには、最大 60 分かかる可能性があるというメッセージが表示されます。
  
## <a name="turn-off-auditing"></a>監査をオフにする

監査をオフExchange Online PowerShell を使用する必要があります。
  
1. [Exchange Online PowerShell に接続します](/powershell/exchange/connect-to-exchange-online-powershell)。

2. 次の PowerShell コマンドを実行して監査をオフにします。

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
    ```

3. しばらくすると、監査が無効 (無効) になっていることを確認します。 このようにするには、次の 2 つの方法があります。

    - PowerShell Exchange Onlineで、次のコマンドを実行します。

      ```powershell
      Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
      ```

      `False` _UnifiedAuditLogIngestionEnabled_ プロパティの値は、監査がオフになっていることを示します。

    - [監査]**ページの**[監査] Microsoft 365 コンプライアンス センター。

      組織の監査が有効ではない場合は、ユーザーと管理アクティビティの記録を開始するように求めるバナーが表示されます。
