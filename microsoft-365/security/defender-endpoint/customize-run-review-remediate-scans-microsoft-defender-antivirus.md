---
title: スケジュールされたスキャンとオンデマンド スキャンを実行してカスタマイズします。
description: ネットワーク全体のエンドポイントでMicrosoft Defender ウイルス対策スキャンをカスタマイズして開始する
keywords: スキャン、スケジュール、カスタマイズ、除外、ファイルの除外、修復、スキャン結果、検疫、脅威の削除、クイック スキャン、フル スキャン、Microsoft Defender ウイルス対策
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 9acac2868b0bd2449338f4a61f663d8cfe8a8ee4
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/29/2021
ms.locfileid: "61218252"
---
# <a name="customize-initiate-and-review-the-results-of-microsoft-defender-antivirus-scans-and-remediation"></a>Microsoft Defender ウイルス対策スキャンと修復の結果をカスタマイズ、開始、および確認する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

グループ ポリシー、PowerShell、Windows Management Instrumentation (WMI) を使用して、Microsoft Defender ウイルス対策 スキャンを構成できます。 

## <a name="in-this-section"></a>このセクションの内容

トピック | 説明
---|---
[Microsoft Defender ウイルス対策 スキャンでファイル、フォルダー、およびプロセスで開かれたファイルの除外を構成して検証する](configure-exclusions-microsoft-defender-antivirus.md) | ファイル (指定されたプロセスによって変更されたファイルを含む) とフォルダーは、オンデマンド スキャン、スケジュールされたスキャン、および常時オンのリアルタイム保護の監視とスキャンから除外できます。
[Microsoft Defender ウイルス対策スキャン オプションを構成する](configure-advanced-scan-types-microsoft-defender-antivirus.md) | Microsoft Defender ウイルス対策を構成して、特定の種類の電子メール ストレージ ファイル、バックアップ ポイントまたは再解析ポイント、アーカイブされたファイル (.zip ファイルなど) をスキャンに含めることができます。 ネットワーク ファイルスキャンを有効にすることもできます
[スキャンの修復を構成する](configure-remediation-microsoft-defender-antivirus.md) | 脅威を検出したときに実行するMicrosoft Defender ウイルス対策と、検疫されたファイルを検疫フォルダーに保持する期間を構成する
[スケジュールされたスキャンを構成する](scheduled-catch-up-scans-microsoft-defender-antivirus.md) | 定期的な (スケジュールされた) スキャンをセットアップする (実行するタイミングや、フル スキャンとクイック スキャンのどちらで実行するかなど)
[スキャンを構成して実行する](run-scan-microsoft-defender-antivirus.md) | PowerShell、Windows Management Instrumentation を使用するか、Windows セキュリティ アプリを使用してエンドポイントで個別にオンデマンド スキャンを実行して構成する
[スキャン結果を確認する](review-scan-results-microsoft-defender-antivirus.md) | Microsoft Endpoint Configuration Manager、Microsoft Intune、またはWindows セキュリティ アプリを使用してスキャンの結果を確認する