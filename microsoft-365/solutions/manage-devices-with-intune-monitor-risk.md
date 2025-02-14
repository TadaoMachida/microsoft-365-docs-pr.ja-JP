---
title: 手順 6.デバイスのリスクとセキュリティ ベースラインへのコンプライアンスを監視する
ms.author: bcarter
author: brendacarter
f1.keywords:
- connect Intune to Defender
- monitor device risk
- monitor device compliance
- deploy security baselines
manager: dougeby
audience: ITPro
description: Microsoft Intune を Defender for Endpoint に接続し、アクセスの条件としてデバイスのリスクを監視する方法について説明します。
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- deploy security baselines
- m365solution-managedevices
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
keywords: ''
ms.openlocfilehash: eab30a8a0801dcbdf95bee3c33f54a920850a6db
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2022
ms.locfileid: "66749245"
---
# <a name="step-6-monitor-device-risk-and-compliance-to-security-baselines"></a>手順 6.デバイスのリスクとセキュリティ ベースラインへのコンプライアンスを監視する

組織が Microsoft Defender for Endpoint を展開した後、MicrosoftI ntune を Defender for Endpoint と統合することで、デバイスの分析情報と保護を強化できます。 モバイル デバイスの場合、これにはアクセスの条件としてデバイスのリスクを監視する機能が含まれます。 Windows デバイスの場合、これらのデバイスのセキュリティ ベースラインへの準拠を監視できます。 

Microsoft Defender for Endpoint の展開には、エンドポイントのオンボーディングが含まれます。 Intune を使用してエンドポイントをオンボードした場合 (推奨)、Microsoft Intune を Defender for Endpoint に既に接続しています。 別の方法を使用してエンドポイントを Defender for Endpoint にオンボードした場合は、「[Intune で Microsoft Defender for Endpoint を構成する](/mem/intune/protect/advanced-threat-protection-configure)」を参照し、Intune と Microsoft Defender for Endpoint の間にサービス間接続が設定されていることを確認してください。 


![エンドポイントとMicrosoft Intuneの統合図のディフェンダー](../media/devices/devices-defender-for-endpoint-steps.png#lightbox)

この図について:
- Microsoft Defender for Endpoint は、デバイスの脅威保護の洗練度を大幅に向上させます。 
- Microsoft Intune ではアプリ保護ポリシーの設定とデバイスの管理 (構成の変更を含む) が可能ですが、Defender for Endpoint はデバイスの脅威を継続的に監視し、自動化されたアクションを実行して攻撃を修正できます。 
- Intune を使用して、デバイスを Defender for Endpoint にオンボードできます。 これを行う場合は、これらのデバイスも Microsoft Purview エンドポイントのデータ損失防止 (エンドポイント DLP) 機能とともに動作する様に有効化します。

この記事には、次の手順が含まれています。
- デバイスのリスクを監視する
- セキュリティ ベースラインへのコンプライアンスを監視する

Defender for Endpoint がまだ設定されていない場合は、脅威保護管理者と協力して、[評価環境とパイロット環境を設定します](../security/defender/eval-defender-endpoint-overview.md)。 パイロット グループと協力して、この記事の機能を試すことができます。

## <a name="monitor-device-risk-as-a-condition-for-access"></a>アクセスの条件としてデバイスのリスクを監視する

Microsoft Defender for Endpoint を展開すると、脅威のリスク信号を利用できます。 これにより、リスク スコアに基づいてデバイスへのアクセスをブロックできます。 マイクロソフトでは、リスク スコアが中以下のデバイスへのアクセスを許可することをお勧めします。

Android および iOS / iPadOS の場合、脅威信号はアプリ保護ポリシー (APP) 内で使用できます。 これを構成する方法については、「[アプリ保護ポリシーを作成して割り当て、デバイスのリスク レベルを設定する](/mem/intune/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level)」を参照してください。

すべてのプラットフォームで、既存のデバイス コンプライアンス ポリシーにリスク レベルを設定できます。「[条件付きアクセス ポリシーを作成する](/mem/intune/protect/advanced-threat-protection-configure#create-a-conditional-access-policy)」を参照してください。

## <a name="deploy-security-baselines-and-monitor-compliance-to-these-settings"></a>セキュリティ ベースラインを展開し、これらの設定へのコンプライアンスを監視する

適用対象: Windows 10、Windows 11

記事「[手順 5. 構成プロファイルの展開](manage-devices-with-intune-configuration-profiles.md)」では、Windows 10 および Windows 11 で使用可能なセキュリティ ベースラインを使用して構成プロファイルを開始することを推奨しています。 Microsoft Defender for Endpoint には、エンドポイント検出および応答 (EDR) の設定など、Defender for Endpoint スタックのすべてのセキュリティ制御を最適化する設定を提供するセキュリティ ベースラインも含まれています。 これらは、Microsoft Intune を使用して展開されます。

理想的には、Defender for Endpoint にオンボーディングされたデバイスは、両方のベースラインで展開されます。最初に Windows を保護するための Windows Intune セキュリティ ベースラインと、次に Defender for Endpoint セキュリティ コントロールを最適に構成するために上に階層化された Defender for Endpoint セキュリティベースラインです。

リスクと脅威に関する最新のデータを活用し、ベースラインの進化に伴う競合を最小限に抑えるために、ベースラインの最新バージョンは、リリースされたらすぐにすべての製品に適用してください。 

Defender for Endpoint を使用すると、これらのベースラインへのコンプライアンスを監視できます。 

![セキュリティ ベースラインへのコンプライアンスを監視するためのカード](../media/devices/secconmgmt-baseline-card.png#lightbox)

セキュリティ ベースラインを展開し、これらの設定へのコンプライアンスを監視するには、この表の手順を使用します。


|手順  |説明  |
|---------|---------|
|1     |重要な概念を確認し、Microsoft Defender for Endpoint と Windows Intune のセキュリティ ベースラインを比較します。 <br><br>推奨事項については、「[Microsoft Defender for Endpoint セキュリティ ベースラインへのコンプライアンスの向上](../security/defender-endpoint/configure-machines-security-baseline.md)」を参照してください。<br><br>使用可能なセキュリティ ベースラインのリストと競合を回避する方法を確認するには、「[セキュリティ ベースラインを使用して Intune で Windows デバイスを構成する](/mem/intune/protect/security-baselines)」を参照してください。         |
|2     |  Intune の Windows セキュリティ ベースライン設定を展開します。「[手順 5. 構成プロファイルを展開する](manage-devices-with-intune-configuration-profiles.md)」のガイダンスに従った場合、すでにこれを達成している可能性があります。        |
|3    |  Intune のDefender for Endpoint ベースライン設定を展開します。 プロファイルを作成してベースライン バージョンを選択するには、「[Microsoft Intune でのセキュリティ ベースライン プロファイルの管理](/mem/intune/protect/security-baselines-configure)」を参照してください。<br><br>こちらの手順に従うこともできます: 「[エンドポイント セキュリティ ベースライン用の Microsoft Defender を確認して割り当てる](../security/defender-endpoint/configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline)」     |
|4     | Defender for Endpoint で、[デバイス構成管理のセキュリティ ベースラインカードを確認](../security/defender-endpoint/configure-machines.md)します。          |


## <a name="next-steps"></a>次の手順
[手順 7. エンドポイントに情報保護機能を使用して DLP を実装する](manage-devices-with-intune-dlp-mip.md)に移動します。