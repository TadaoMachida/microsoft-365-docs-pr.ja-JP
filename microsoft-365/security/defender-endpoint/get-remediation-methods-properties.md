---
title: 修復アクティビティのメソッドとプロパティ
description: API 応答には、テナントで作成された脅威&脆弱性管理修復アクティビティが含まれています。 選択した修復タスクに対して、すべての修復アクティビティ、1 つの修復アクティビティ、または公開されたデバイスに関する情報のみを要求できます。
keywords: apis, 修復, 修復 API, get, 修復タスク, 修復方法, 修復プロパティ,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 86218bb1dc3a30ab38e3df07496aa40a5775e88c
ms.sourcegitcommit: 6e570b79944862c86735db455349b685d5b903b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2022
ms.locfileid: "67020475"
---
# <a name="remediation-activity-methods-and-properties"></a>修復アクティビティのメソッドとプロパティ

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender 脆弱性の管理](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> Microsoft Defender 脆弱性の管理を体験しますか? [Microsoft Defender 脆弱性の管理パブリック プレビュー試用版](../defender-vulnerability-management/get-defender-vulnerability-management.md)にサインアップする方法の詳細については、こちらを参照してください。

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

API 応答には、テナントに作成された [脅威&脆弱性管理](next-gen-threat-and-vuln-mgt.md) 修復アクティビティが含まれています。

## <a name="methods"></a>メソッド

メソッド|データ型|説明
:---|:---|:---
[すべての修復作業を一覧表示する](get-remediation-all-activities.md)|調査コレクション|すべての修復アクティビティに関する情報を返します。
[1 つの修復アクティビティの暴露デバイスを一覧表示する](get-remediation-exposed-devices-activities.md)|調査エンティティ|指定した修復アクティビティの公開されたデバイスに関する情報を返します。
[ID による 1 つの修復アクティビティを取得する](get-remediation-one-activity.md)|調査エンティティ|指定した修復アクティビティの情報を返します。

[修復アクティビティ](tvm-remediation.md)の詳細については、こちらを参照してください。

## <a name="properties"></a>プロパティ

プロパティ ID|データ型|説明
:---|:---|:---
カテゴリ|文字列|修復アクティビティのカテゴリ (ソフトウェア/セキュリティ構成)
completerEmail|String|修復アクティビティが他のユーザーによって手動で完了した場合、この列には自分のメールが含まれます
completerId|String|修復アクティビティが他のユーザーによって手動で完了した場合、この列にはオブジェクト ID が含まれます。
completionMethod|String|修復アクティビティは、"自動的に" 完了 (すべてのデバイスにパッチが適用されている場合) または "完了済みとしてマーク" を選択したユーザーが "手動" で完了できます。
createdOn|DateTime|この修復アクティビティが作成された時刻
説明|String|この修復アクティビティの説明
dueOn|DateTime|この修復アクティビティに対して作成者が設定した期限
fixedDevices||修正されたデバイスの数
ID|String|この修復アクティビティの ID
Nameid|String|関連する製品名
優先度|String|この修復アクティビティの作成者セットの優先度 (高\中\低)
Productid|String|関連する製品 ID
productivityImpactRemediationType|String|いくつかの構成変更は、ユーザーに影響を与えないデバイスに対してのみ要求できます。 この値は、"すべての公開デバイス" または "ユーザーに影響のないデバイスのみ" の選択を示します。
rbacGroupNames|String|関連するデバイス グループ名
recommendedProgram|String|にアップグレードするための推奨プログラム
recommendedVendor|String|アップグレード先として推奨されるベンダー
recommendedVersion|String|更新/アップグレードに推奨されるバージョン
relatedComponent|String|この修復アクティビティの関連コンポーネント (セキュリティに関する推奨事項の関連コンポーネントと同様)
requesterEmail|String|作成者の電子メール アドレス
requesterId|String|Creator オブジェクト ID
requesterNotes|String|この修復アクティビティに対して作成者が追加したノート (フリー テキスト)
Scid|String|関連するセキュリティ推奨事項の SCID
状態|String|修復アクティビティの状態 (アクティブ/完了)
statusLastModifiedOn|DateTime|状態フィールドが更新された日付
targetDevices|Long|この修復が適用できる公開デバイスの数
Title|String|この修復アクティビティのタイトル
型|String|修復の種類
vendorId|String|関連するベンダー名

## <a name="see-also"></a>関連項目

- [ID による 1 つの修復アクティビティを取得する](get-remediation-one-activity.md)

- [すべての修復作業を一覧表示する](get-remediation-all-activities.md)

- [1 つの修復アクティビティの暴露デバイスを一覧表示する](get-remediation-exposed-devices-activities.md)

- [リスクベースの脅威&脆弱性管理](next-gen-threat-and-vuln-mgt.md)

- [組織の脆弱性](tvm-weaknesses.md)
