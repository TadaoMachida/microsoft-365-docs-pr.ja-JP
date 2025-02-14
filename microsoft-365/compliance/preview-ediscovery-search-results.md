---
title: 電子情報開示検索の結果をプレビューする
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Microsoft Purview コンプライアンス ポータルで、コンテンツ検索または電子情報開示 (標準) 検索によって返される結果のサンプルをプレビューします。
ms.openlocfilehash: f369148c6f898c4150d0c86f898640f71ab367a0
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628597"
---
# <a name="preview-ediscovery-search-results"></a>電子情報開示検索結果をプレビューする

コンテンツ検索、またはMicrosoft Purview 電子情報開示 (標準) ケースに関連付けられている検索を実行すると、検索によって返される結果サンプルをプレビューできます。 検索クエリによって返されたアイテムをプレビューすると、検索が所望の結果を返しているかどうか、検索クエリを変更して検索を再実行する必要があるのかどうかを把握することができます。

検索によって返される結果サンプルをプレビューするには、次の方法があります。

1. Microsoft Purview コンプライアンス ポータルで、コンテンツ検索ページまたは電子情報開示 (標準) ケースに移動します。

2. 検索を選択して、ポップアップ ページを表示します。

3. ポップアップ ページの下部で、**[サンプルのレビュー]** をクリックします。

   ![ポップアップ ページで [サンプルのレビュー] をクリックして結果をプレビューする。](../media/PreviewSearchResults1.png)

   検索結果のサンプルを含むページが表示されます。

4. 閲覧ウィンドウでアイテムを選んで内容を表示します。

   ![閲覧ウィンドウでアイテムをプレビュー。](../media/PreviewSearchResults2.png)

   前述のスクリーンショットでは、アイテムをプレビューする場合に、検索クエリのキーワードが強調表示されていることがわかります。

## <a name="how-the-search-result-samples-are-selected"></a>検索結果のサンプルを選択する方法

最大 1,000 個のランダムに選ばれたアイテムをプレビューすることができます。 プレビューで利用可能なアイテムは、無作為に選ばれたものに加えて、以下の条件を満たすものです。

- 単一のコンテンツの場所 (メールボックスまたはサイト) で最大 100 個のアイテムをプレビューすることができます。 つまり、1,000 個未満のアイテムをプレビューできる可能性があるということです。 たとえば、4 つのメールボックスを検索して 1,500 件の推定値が返ってきた場合、各メール ボックスから 100 件しかプレビューできないため、400 件のみプレビュー可能になります。

- メールボックス アイテムの場合、プレビューできるのはメールのメッセージのみです。 タスク、予定表のアイテム、連絡先などのアイテムは、プレビューできません。

- サイト アイテムの場合は、ドキュメントのみプレビューできます。 フォルダー、リスト、リストの添付ファイルなどのアイテムはプレビューできません。

## <a name="file-types-supported-when-previewing-search-results"></a>検索結果をプレビューする場合にサポートされるファイルの種類

サポートされているファイルの種類は、プレビュー ウィンドウでプレビューできます。 サポートされていないファイルの種類の場合は、ファイルのコピーをローカル コンピューターにダウンロードする必要があります(**元のアイテムをダウンロード** をクリックします)。 .aspx Web ページの場合、ページの URL が含まれていても、ページへのアクセス許可を持っていないことがあります。 インデックスのないアイテムはプレビュー表示できません。

次のファイルの種類はサポートされており、検索結果ウィンドウでプレビューできます。
  
- .txt、.html、.mhtml

- .eml

- .doc、.docx、.docm

- .pptm、.pptx

- .pdf

また、次のファイル コンテナーの種類もサポートされています。プレビュー ウィンドウでは、コンテナー内のファイルの一覧を表示できます。
  
- .zip

- .gzip