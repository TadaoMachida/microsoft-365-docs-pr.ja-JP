---
title: AutoPilot デバイスを作成し編集する
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.collection: ''
ms.custom:
- MiniMaven
- OKR_SMB_M365
search.appverid:
- BCS160
- MET150
- MOE150
description: Microsoft 365 Business Premium で AutoPilot を使用してデバイスをアップロードする方法について説明します。 プロファイルをデバイスまたはデバイスのグループに割り当てる
ms.openlocfilehash: 9e02b985e5742331426210d6d3824dfa120a21d3
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2022
ms.locfileid: "66894989"
---
# <a name="create-and-edit-autopilot-devices"></a>AutoPilot デバイスを作成し編集する

## <a name="upload-a-list-of-devices"></a>デバイスの一覧をアップロードする

[[ステップ バイ ステップ ガイド]](m365bp-add-Autopilot-devices-and-profile.md) を使ってデバイスをアップロードできますが、**[デバイス]** タブでアップロードすることもできます。 
  
デバイスは次の要件を満たしている必要があります。
  
- Windows 10 バージョン 1703 以降
    
- Windows out-of-box experience を行っていない新しいデバイス

1. Microsoft 365 管理センターで、[ **デバイス** \> **Autopilot** ] を選択します。
  
2. [ **Autopilot** ] ページで、[ **デバイス** ] タブ \> [ **デバイスの追加** ] を選択します。
    
    ![In the Devices tab, choose Add devices.](./../media/6ba81e22-c873-40ad-8a72-ce64d15ea6ba.png)
  
3. **[デバイスの追加]** パネルで準備した [[デバイス リスト CSV ファイル]](../admin/misc/device-list.md) を参照し、\> **[保存]** \> **[閉じる]** の順に選択します。
    
    この情報は、ハードウェアの製造元から、または CSV ファイルを生成する [Get-WindowsAutopilotInfo PowerShell スクリプト](https://www.powershellgallery.com/packages/Get-WindowsAutopilotInfo) を使って、入手できます。 
    
## <a name="assign-a-profile-to-a-device-or-a-group-of-devices"></a>プロファイルをデバイスまたはデバイスのグループに割り当てる

1. **[Windows の準備]** ページで **[デバイス]** タブを選択し、1 つまたは複数のデバイスの横にあるチェック ボックスをオンにします。 
    
2. [ **デバイス**] パネルで、[ **割り当てられたプロファイル**] ドロップダウンからプロファイルを選択します。 
    
    プロファイルがまだない場合は、「 [Autopilot プロファイルの作成と編集](../admin/devices/create-and-edit-Autopilot-profiles.md) 」で手順を参照してください。 

## <a name="see-also"></a>関連項目

[ビジネス プランの Microsoft 365 をセキュリティで保護するためのベスト プラクティス](../admin/security-and-compliance/secure-your-business-data.md)
