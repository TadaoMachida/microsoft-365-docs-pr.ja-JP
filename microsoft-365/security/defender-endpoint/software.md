---
title: ソフトウェア メソッドとプロパティ
description: 最近の上位のアラートを取得します。
keywords: apis, graph api, サポートされている API, get, alerts, recent
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 6b08b7c4ebb0a818dec5bdf799c3114d91764259
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2021
ms.locfileid: "61301788"
---
# <a name="software-resource-type"></a>ソフトウェア リソースの種類

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>メソッド

<br>

****

|メソッド|戻り値の型|説明|
|---|---|---|
|[ソフトウェアの一覧表示](get-software.md)|ソフトウェア コレクション|組織のソフトウェア インベントリを一覧表示する|
|[ID でソフトウェアを取得する](get-software-by-id.md)|ソフトウェア|特定のソフトウェアをそのソフトウェア ID で取得する|
|[ソフトウェア バージョンの配布を一覧表示する](get-software-ver-distribution.md)|ディストリビューション コレクション|ソフトウェア ID でソフトウェア バージョンの配布を一覧表示する|
|[ソフトウェアによるマシンの一覧表示](get-machines-by-software.md)|MachineRef コレクション|ソフトウェア ID に関連付けられているデバイスの一覧を取得する|
|[ソフトウェアによる脆弱性の一覧表示](get-vuln-by-software.md)|[脆弱性の](vulnerability.md) 収集|ソフトウェア ID に関連付けられている脆弱性の一覧を取得する|
|[不足している KB を取得する](get-missing-kbs-software.md)|KB コレクション|ソフトウェア ID に関連付けられている不足している KB の一覧を取得する|
|

## <a name="properties"></a>プロパティ

<br>

****

|プロパティ|種類|説明|
|---|---|---|
|id|String|ソフトウェア ID|
|名前|String|ソフトウェア名|
|ベンダー|String|ソフトウェア発行元名|
|弱点|Long|検出された脆弱性の数|
|publicExploit|ブール値|一部の脆弱性に対してパブリック エクスプロイトが存在する|
|activeAlert|ブール値|アクティブなアラートがこのソフトウェアに関連付けられている|
|exposedMachines|Long|公開されているデバイスの数|
|impactScore|倍精度浮動小数点数|このソフトウェアの露出スコアの影響|
|
