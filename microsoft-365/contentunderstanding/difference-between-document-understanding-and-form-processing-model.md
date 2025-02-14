---
title: Microsoft SharePoint Syntex のカスタム モデルの違い
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: ドキュメント理解モデルとフォーム処理モデルの主な違いについて説明します。
ms.openlocfilehash: 31f70983b90e758516f92081217010bb6a64acd4
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603794"
---
# <a name="differences-between-custom-models-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex のカスタム モデルの違い 

Microsoft SharePoint Syntexのコンテンツ理解では、SharePoint ドキュメント ライブラリにアップロードされたドキュメントを識別して分類し、各ファイルから関連情報を抽出できます。 たとえば、ファイルが SharePoint ドキュメントライブラリにアップロードされると、*発注書* として識別されたすべてのファイルがそのように分類され、カスタム ドキュメント ライブラリ ビューに表示されます。 さらに、各ファイルから特定の情報 (*PO番号* や *合計* など) を取得して、ドキュメントライブラリビューの列として表示できます。 

コンテンツの理解により、必要な情報を特定して抽出するための *モデル* を作成できます。 モデルは、検索、ビジネスプロセス、コンプライアンス、およびその他の多くのビジネス問題の解決を支援する上で価値があります。

使用できるカスタム モデルには、次の 2 種類があります。

- [ドキュメント理解モデル](document-understanding-overview.md)
- [フォーム処理モデル](form-processing-overview.md)

どちらのモデルも一般的に同じ目的で使用されますが、以下に示す主な違いは、どちらを使用できるかに影響します。

> [!NOTE]
> フォーム処理とドキュメントの理解シナリオの例の詳細については、[SharePoint Syntexの導入を開始](./adoption-getstarted.md)する方法に関するページを参照してください。

## <a name="structured-versus-unstructured-and-semi-structured-content"></a>構造化コンテンツと非構造化コンテンツおよび半構造化コンテンツ

ドキュメント理解モデルを使用して、文字や契約書などの非構造化ドキュメントからデータを識別して抽出します。抽出するテキスト エンティティは、ドキュメントの文または特定の領域にあります。 たとえば、非構造化ドキュメントは、さまざまな方法で記述できる契約更新レターである可能性があります。 ただし、情報は、テキスト文字列 `Service start date of` の後に実際の日付が続くなど、各契約更新ドキュメントの本文に一貫して存在します。

フォーム処理モデルを使用してファイルを識別し、フォームや請求書などの構造化または半構造化されたドキュメントからデータを抽出します。フォーム処理モデルは、サンプル ドキュメントからフォームのレイアウトを理解し、似ている場所から抽出する必要のあるデータを探すようにトレーニングされています。フォームは通常、エンティティが同じ場所に配置されている、より構造化されたレイアウトを持っています (たとえば、納税申告での社会保障番号など)。

> [!NOTE]
> ドキュメント理解モデルを作成したり、SharePoint ドキュメントライブラリに適用したりするには、コンテンツ センター サイトへのアクセスが必要です。 

## <a name="where-models-are-created"></a>モデルが作成された場所

ドキュメント理解モデルは、SharePoint コンテンツ センター サイトで作成および管理されます。 

> [!NOTE]
> 入力ドキュメントの詳細については、[フォーム処理モデルの要件と制限](/ai-builder/form-processing-model-requirements)を参照してください。 

フォーム処理モデルは PowerApps [AI ビルダー](/ai-builder/overview)で作成されますが、作成は SharePoint ドキュメント ライブラリから直接開始されます。 ドキュメント ライブラリでは、ユーザーがそのドキュメントのためにフォーム処理モデルを作成する前に、フォーム処理モデルの作成を有効にしておく必要があります。 管理者は、コンテンツの理解の管理設定でフォーム処理モデルの作成を有効にできます。 フォーム処理モデルでは、Power Automate フローを使用して、ドキュメント ライブラリにアップロードされたときにファイルを処理します。

ドキュメント理解モデルを作成するときは、SharePoint コンテンツタイプギャラリーに保存される新しい [SharePoint コンテンツ タイプ](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978)を作成します。 または、必要に応じて、既存のコンテンツタイプを使用してモデルを定義できます。

コンテンツ タイプが作成され、モデルに関連付けられたら、**[サイト コンテンツ タイプ]** プロパティ パネルからそのモデルを参照することもできます。

:::image type="content" source="../media/content-understanding/site-content-type-panel.png" alt-text="強調表示されたドキュメント理解モデルを示す [サイト コンテンツ タイプ] パネルのスクリーンショット。" lightbox="../media/content-understanding/site-content-type-panel.png":::

フォーム処理モデルは、新しい [SharePoint コンテンツ タイプ](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978)も作成し、SharePoint コンテンツ タイプ ギャラリーにも保存されます。

## <a name="where-they-can-be-applied"></a>適用可能な場所

アクセスできる SharePoint ドキュメント ライブラリにドキュメント理解モデルを適用できます。 コンテンツ センターを使用してドキュメント理解モデルを作成し、それをさまざまなドキュメント ライブラリに適用できます。 コンテンツ センターでは、ドキュメント理解モデルの使用方法と適用できる場所をより集中的に制御できます。 この情報はコンテンツセンターにもロールアップする必要があります。

現在、フォーム処理モデルは、モデルを作成した SharePoint ドキュメント ライブラリにのみ適用できます。 これにより、サイトにアクセスできるライセンス付与済みのユーザーは、フォーム処理モデルを作成できるようになります。 管理者は、SharePoint ドキュメントライブラリでフォーム処理を有効にして、ライセンス付与済みのユーザーが使用できるようにする必要があります。

## <a name="comparison-of-form-processing-and-document-understanding"></a>フォーム処理とドキュメントの理解の比較

次の表を使用して、フォーム処理を使用するタイミングとドキュメントの理解を使用するタイミングを理解します。

| 機能 | フォーム処理 | ドキュメント理解 |
| ------- | ------- | ------- |
| モデルの種類 - それぞれを使用する場合 | 構造化ファイル形式と半構造化ファイル形式 (請求書などのフォーム コンテンツの PDF や、レイアウトと書式設定が類似している発注書など)。  | 非構造化ファイル形式や半構造化ファイル形式 (レイアウトに違いはありますが、抽出される情報が類似している Office ドキュメントなど)。 |
| モデルの作成 | SharePoint ドキュメント ライブラリからシームレスにアクセスできる AI Builder で作成されたモデル。| SharePoint でコンテンツ センターという新しいサイトに作成されたモデル。 |
| 分類の種類| 抽出するデータに関する手がかりをシステムに与える設定可能な分類子。| 機械教育を使用して、抽出するデータのドキュメントの場所を割り当てる、オプションの抽出子を備えたトレーニング可能な分類子。|
| 場所 | 単一のドキュメント ライブラリ用にトレーニングされています。| 複数のライブラリに適用できます。|
| サポートされているファイルの種類| PDF、JPG、PNG 形式、合計 50 MB および 500 ページでトレーニングします。| 否定的な例を含め、5 - 10 個の PDF、Office、またはメール ファイルでトレーニングします。<br>Office ファイルは 64K 文字で切り捨てられます。 OCR でスキャンされるファイルは 20 ページに制限されています。 [サポートされているファイルの種類を](document-understanding-overview.md#supported-file-types)参照してください。|
| 管理されたメタデータと統合する | いいえ | はい。設定された管理対象メタデータ フィールドを参照するエンティティ抽出子のトレーニングを行います。|
| コンプライアンス機能とMicrosoft Purview 情報保護の統合 | 発行済みの保持ラベルを設定します。<br>秘密度ラベルを設定する予定です。 | 発行済みの保持ラベルを設定します。<br>公開された秘密度ラベルを設定します。 |
| サポートされる地域| フォーム処理は Power Platform に依存しています。 Power Platform と AI Builder のグローバルな可用性については、「[Power Platform の可用性](https://dynamics.microsoft.com/geographic-availability/)」を参照してください。 | すべての地域で利用可能です。|
| トランザクション コスト | AI Builder クレジットを使用します。<br>1 か月あたりのSharePoint Syntexライセンスごとに 3.5K クレジットが含まれています。<br>1 M のクレジットで 2,000 ファイル ページの処理が可能になります。<br>| 適用されません。 |
| 容量 | 既定の Power Platform 環境を使用します (Dataverse データベースをサポートするカスタム環境)。 | 容量制限はありません。|
| サポートされている言語| 73 を超える [言語の言語](/power-platform-release-plan/2021wave2/ai-builder/form-processing-new-language-support)サポート。 | モデルは、すべてのラテンアルファベット言語で動作します。 英語に加えて: ドイツ語、スウェーデン語、フランス語、スペイン語、イタリア語、およびポルトガル語。|


## <a name="see-also"></a>関連項目

[トレーニング: AI ビルダーを使用してビジネスの実績を高める](/learn/paths/improve-business-performance-ai-builder/?source=learn)

[ドキュメントの理解の概要](document-understanding-overview.md)

[フォーム処理の概要](form-processing-overview.md)

[SharePoint Syntex の概要](index.md)
