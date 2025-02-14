---
title: 電子情報開示での AzCopy のトラブルシューティング (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: troubleshooting
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: 電子情報開示 (Premium) でエラー修復のためにOffice 365以外のデータを読み込む際の Azure AzCopy のエラーのトラブルシューティングを行います。
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 3a74dd5f2a341e9a99cbfc82cfb12900bae42491
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641144"
---
# <a name="troubleshoot-azcopy-in-ediscovery-premium"></a>電子情報開示での AzCopy のトラブルシューティング (Premium)

Microsoft Purview eDiscovery (Premium) でエラー修復のために Microsoft 365 以外のデータまたはドキュメントを読み込む場合、ユーザー インターフェイスには、アップロードするファイルの保存場所とファイルのアップロード先となる Azure ストレージの場所を含むパラメーターを含む Azure AzCopy コマンドが用意されています。 ドキュメントをアップロードするには、このコマンドをコピーし、ローカル コンピューターのコマンド プロンプトで実行します。  次のスクリーンショットは、AzCopy コマンドの例を示しています。

![Microsoft 365 以外のファイルをアップロードします。](../media/46ba68f6-af11-4e70-bb91-5fc7973516e3.png)

通常、指定されたコマンドは、実行時に機能します。 ただし、表示されるコマンドが正常に実行されない場合があります。 考えられる理由をいくつか次に示します。

## <a name="the-supported-version-of-azcopy-isnt-installed-on-the-local-computer"></a>サポートされているバージョンの AzCopy がローカル コンピューターにインストールされていない

現時点では、AzCopy v8.1 を使用して、Microsoft 以外の 365 データを電子情報開示 (Premium) に読み込む必要があります。 前のスクリーンショットに示した [ **ファイルのアップロード** ] ページに表示されている AzCopy コマンドは、AzCopy v8.1 を使用していない場合にエラーを返します。 このバージョンをインストールするには、 [Windows の AzCopy v8.1 でデータを転送する方法に関するページを](/previous-versions/azure/storage/storage-use-azcopy)参照してください。

## <a name="azcopy-isnt-installed-on-the-local-computer-or-its-not-installed-in-the-default-location"></a>AzCopy がローカル コンピューターにインストールされていないか、既定の場所にインストールされていません

AzCopy がインストールされていない場合、または既定のインストール場所 (つまり) 以外の場所にインストールされている場合は `%ProgramFiles(x86)%`、AzCopy コマンドを実行すると、次のエラーが発生する可能性があります。

> 指定されたパスがシステムで見つかりません。

AzCopy がローカル コンピューターにインストールされていない場合は、Windows 上の [AzCopy v8.1 を使用したデータの転送に関するページで](/previous-versions/azure/storage/storage-use-azcopy)インストール情報を確認できます。 必ず既定の場所にインストールしてください。

AzCopy がインストールされているが、既定の場所とは異なる場所にインストールされている場合は、コマンドをコピーし、テキスト ファイルに貼り付けてから、AzCopy がインストールされている場所にパスを変更できます。 たとえば、Azcopy が配置`%ProgramFiles%`されている場合は、コマンド`%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy.exe``%ProgramFiles%\Microsoft SDKs\Azure\AzCopy`の最初の部分を . この変更を行った後、テキスト ファイルからコピーし、コマンド プロンプトを実行します。

> [!TIP]
> AzCopy が別の場所にインストールされている場合は、既定のインストール場所をアンインストールしてから、既定の場所に再インストールすることを検討してください。 これは、将来的にこの問題を防ぐのに役立ちます。