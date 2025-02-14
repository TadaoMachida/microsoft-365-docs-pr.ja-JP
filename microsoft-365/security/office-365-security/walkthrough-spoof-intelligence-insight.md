---
title: スプーフィング インテリジェンス ポリシーとスプーフィング インテリジェンス 分析情報を使用してスプーフィングされた送信者を管理する
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 59a3ecaf-15ed-483b-b824-d98961d88bdd
ms.collection:
- M365-security-compliance
description: 管理者は、スプーフィング インテリジェンス ポリシーとスプーフィング インテリジェンス分析情報を使用して、検出されたスプーフィングされた送信者を許可またはブロックする方法を学習できます。
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 66253ed6deab0f41cac3a4ff732201e20d100e98
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2022
ms.locfileid: "65771999"
---
# <a name="manage-spoofed-senders-using-the-spoof-intelligence-policy-and-spoof-intelligence-insight-in-eop"></a>EOP でスプーフィング インテリジェンス ポリシーとスプーフィング インテリジェンス 分析情報を使用してスプーフィングされた送信者を管理する

**適用対象**
- [Microsoft Defender for Office 365 プラン 1 およびプラン 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Microsoft 365 Defender ポータルのスプーフィング送信者管理は、テナント許可/ブロックリストの **[スプーフィング**] タブでのみ使用できるようになりました。 Microsoft 365 Defender ポータルの現在の手順については、「[EOP でのスプーフィング インテリジェンス分析情報](learn-about-spoof-intelligence.md)」を参照してください。
>
> Exchange Online PowerShell またはスタンドアロン EOP PowerShell のスプーフィングされた送信者管理は、関連する **\*-TenantAllowBlockListSpoofItems**、**Get-SpoofIntelligenceInsight**、**Get-SpoofMailReport** コマンドレットにのみ移行中です。 これらのコマンドレットを使用する手順については、次の記事を参照してください。
>
> - [PowerShell を使用してスプーフィングされた送信者エントリを表示する](tenant-allow-block-list.md#view-spoofed-sender-entries)
> - [PowerShell を使用してスプーフィングされた送信者許可エントリを追加する](manage-tenant-allows.md#add-spoofed-sender-allow-entries-using-powershell)
> - [PowerShell を使用してスプーフィングされた送信者ブロック エントリを追加する](manage-tenant-blocks.md#add-spoofed-sender-block-entries)
> - [PowerShell を使用してスプーフィングされた送信者エントリを変更する](modify-remove-entries-tenant-allow-block.md#modify-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list)
> - [PowerShell を使用してスプーフィングされた送信者エントリを削除する](modify-remove-entries-tenant-allow-block.md#remove-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list)
>
> **Get-PhishFilterPolicy** コマンドレットと **Set-PhishFilterPolicy** コマンドレットを使用した古いスプーフィングされた送信者管理エクスペリエンスは非推奨のプロセスにありますが、コマンドレットがすべての場所で削除されるまで、この記事では完全さを示しています。

## <a name="what-do-you-need-to-know-before-you-begin"></a>始める前に把握しておくべき情報

- Exchange Online PowerShell へ接続するには、「[Exchange Online PowerShell に接続する](/powershell/exchange/connect-to-exchange-online-powershell)」を参照してください。 スタンドアロンの EOP PowerShell に接続するには、「[Exchange Online Protection PowerShell への接続](/powershell/exchange/connect-to-exchange-online-protection-powershell)」を参照してください。

- この記事の手順を実行する際には、あらかじめ **Exchange Online** でアクセス許可を割り当てる必要があります。
  - スプーフィング インテリジェンス ポリシーを変更したり、スプーフィング インテリジェンスを有効または無効にするには、次のメンバーである必要があります。
    - **組織の管理**
    - **セキュリティ管理者**<u>と</u>**表示専用構成** または **表示専用組織管理**。
  - スプーフィング インテリジェンス ポリシーへの読み取り専用アクセスの場合は、 **グローバル リーダー** または **セキュリティ 閲覧者** ロール グループのメンバーである必要があります。

  詳細については、「[Exchange Online のアクセス許可](/exchange/permissions-exo/permissions-exo)」を参照してください。

  **注**:

  - Microsoft 365 管理センターで、対応する Azure Active Directory のロールにユーザーを追加すると、ユーザーには、必要なアクセス許可 _および_ Microsoft 365 のその他の機能に必要なアクセス許可が付与されます。詳しくは、「[管理者のロールについて](../../admin/add-users/about-admin-roles.md)」を参照してください。
  - [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) の **閲覧専用の組織管理** の役割グループが この機能への読み取り専用アクセス権も付与します。

- スプーフィング インテリジェンスのオプションについては、「 [フィッシング対策ポリシーのスプーフィング設定」を参照してください](set-up-anti-phishing-policies.md#spoof-settings)。

- フィッシング対策ポリシーでは、スプーフィング インテリジェンス設定を有効、無効、および構成できます。 サブスクリプションに基づく手順については、次のいずれかのトピックを参照してください。

  - [EOP でフィッシング対策ポリシーを構成します](configure-anti-phishing-policies-eop.md)。
  - [Microsoft Defender for Office 365でフィッシング対策ポリシーを構成](configure-mdo-anti-phishing-policies.md)します。

- スプーフィング インテリジェンスの推奨設定については、「 [EOP フィッシング対策ポリシーの設定](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings)」を参照してください。

## <a name="use-powershell-to-manage-spoofed-senders"></a>PowerShell を使用してスプーフィングされた送信者を管理する

許可された送信者とブロックされた送信者をスプーフィング インテリジェンスで表示するには、次の構文を使用します。

```powershell
Get-PhishFilterPolicy [-AllowedToSpoof <Yes | No | Partial>] [-ConfidenceLevel <Low | High>] [-DecisionBy <Admin | SpoofProtection>] [-Detailed] [-SpoofType <Internal | External>]
```

この例では、ドメイン内のユーザーのスプーフィングが許可されているすべての送信者に関する詳細情報を返します。

```powershell
Get-PhishFilterPolicy -AllowedToSpoof Yes -Detailed -SpoofType Internal
```

構文とパラメーターの詳細については、「 [Get-PhishFilterPolicy](/powershell/module/exchange/get-phishfilterpolicy)」を参照してください。

スプーフィング インテリジェンスで許可およびブロックされた送信者を構成するには、次の手順に従います。

1. **Get-PhishFilterPolicy** コマンドレットの出力を CSV ファイルに書き込み、次のコマンドを実行して、検出されたスプーフィングされた送信者の現在の一覧をキャプチャします。

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

2. CSV ファイルを編集して、次の値を追加または変更します。
   - **送信者** (ソース サーバーの PTR レコードのドメイン、IP/24 アドレス、または検証済みの DKIM ドメイン)
   - **スプーフィングユーザー**: 次のいずれかの値。
     - 内部ユーザーの電子メール アドレス。
     - 外部ユーザーの電子メール ドメイン。
     - スプーフィングされた電子メール アドレスに関係なく、指定した **送信者** からのスプーフィングされたメッセージをブロックまたは許可することを示す空白の値。
   - **AllowedToSpoof** (はいまたはいいえ)
   - **SpoofType** (内部または外部)

   次のコマンドを実行して、ファイルを保存し、ファイルを読み取り、内容を名前付きの `$UpdateSpoofedSenders` 変数として格納します。

   ```powershell
   $UpdateSpoofedSenders = Get-Content -Raw "C:\My Documents\Spoofed Senders.csv"
   ```

3. 次のコマンドを `$UpdateSpoofedSenders` 実行して、変数を使用してスプーフィング インテリジェンス ポリシーを構成します。

   ```powershell
   Set-PhishFilterPolicy -Identity Default -SpoofAllowBlockList $UpdateSpoofedSenders
   ```

構文とパラメーターの詳細については、「 [Set-PhishFilterPolicy](/powershell/module/exchange/set-phishfilterpolicy)」を参照してください。

## <a name="how-do-you-know-these-procedures-worked"></a>正常な動作を確認する方法

スプーフィングが許可され、スプーフィングが許可されていない送信者でスプーフィング インテリジェンスを構成したことを確認するには、PowerShell で次のコマンドを実行して、スプーフィングが許可され、スプーフィングが許可されていない送信者を表示します。

  ```powershell
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType External
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType External
  ```

- PowerShell で、次のコマンドを実行して、スプーフィングされたすべての送信者の一覧を CSV ファイルにエクスポートします。

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```
