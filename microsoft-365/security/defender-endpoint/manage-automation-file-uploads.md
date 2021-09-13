---
title: 自動化ファイルのアップロードを管理する
description: コンテンツ分析を有効にし、分析用に送信されるファイル拡張子とメール添付ファイル拡張機能を構成する
keywords: オートメーション、ファイル、アップロード、コンテンツ、分析、ファイル、拡張子、電子メール、添付ファイル
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c89b5b676e25b23e0e5fdfb925f6894647cb41e5
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2021
ms.locfileid: "59220445"
---
# <a name="manage-automation-file-uploads"></a>自動化ファイルのアップロードを管理する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Defender for Endpoint を試す場合は、 [無料試用版にサインアップしてください。](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automationefileuploads-abovefoldlink)

コンテンツ分析機能を有効にして、特定のファイルと電子メールの添付ファイルをクラウドに自動的にアップロードして、自動調査で追加の検査を行うことができます。

ファイル拡張子名とメール添付ファイル拡張子名を指定して、ファイルと電子メールの添付ファイルを識別します。

たとえば、ファイルまたは添付ファイルの拡張子名として *exe* と *bat* を追加すると、それらの拡張子を持つすべてのファイルまたは添付ファイルが自動的にクラウドに送信され、自動調査中に追加の検査が行われます。

## <a name="add-file-extension-names-and-attachment-extension-names"></a>ファイル拡張子名と添付ファイル拡張名を追加します。

1. ナビゲーション ウィンドウで、[エンドポイント **ルールの** \> **設定]** \>  \> **を選択します**。

2. コンテンツ分析の設定を [オン] と [オフ]**の間で切り****替えます**。

3. 次の内線番号を構成し、内線番号をコンマで区切ります。
   - **ファイル拡張子の名前** - 電子メールの添付ファイルを除く疑わしいファイルは、追加の検査のために提出されます

## <a name="related-topics"></a>関連項目

- [自動化フォルダーの除外を管理する](manage-automation-folder-exclusions.md)
