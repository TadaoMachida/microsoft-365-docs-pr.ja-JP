---
title: 複数地域環境でのユーザー エクスペリエンス
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- SPO_Content
- Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
description: Microsoft 365の複数地域環境での SharePoint、OneDrive、および Exchange のユーザー エクスペリエンスについて説明します。
ms.openlocfilehash: 638aa7d65f9243bfd110eebac6473d641e1d0b61
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2022
ms.locfileid: "62806938"
---
# <a name="user-experience-in-a-multi-geo-environment"></a>複数地域環境でのユーザー エクスペリエンス

ここでは、OneDrive 複数地域構成でユーザーが確認できる内容について説明します。

## <a name="exchange-mailbox"></a>Exchange メールボックス

ユーザーの Exchange メールボックスは、優先されるデータの場所にプロビジョニングされ、PDLが変更されると自動的に移動されます。 ユーザーは、複数地域の環境でユーザー エクスペリエンスを変えることなく、Outlook および Web 上の Outlook を通常どおりに使用できます。

## <a name="hub-sites"></a>ハブ サイト

SharePoint Hub サイトは、従業員のコンテンツの検出とエンゲージメントを強化すると同時に、プロジェクト、部署、または地域の完全で一貫した表現を作成します。 複数地域の環境では、ハブ サイトの地理的な場所に関係なく、サテライトの場所のサイトをハブ サイトに簡単に関連付けることができます。 ユーザーは、サイトの地理的な場所に関係なく、単一の検索エクスペリエンスを通じてハブ全体で検索して結果を得ることができます。

## <a name="microsoft-365-app-launcher"></a>Microsoft 365 アプリ起動ツール

アプリ起動ツールは、Multi-Geo に対応していて、各タイルをワークロードの適切な地域の場所に差し向けます。 SharePoint と OneDrive のタイルは、ユーザーにプロビジョニングされた地理的な場所に対応する場所をポイントします。 つまり、ユーザーは中央の場所に OneDrive を持っており、その SharePoint タイルは中央の場所にある SP Home をポイントしますが、グループ サイトは PDL に対応する場所にプロビジョニングされます。 

## <a name="office-applications"></a>Office アプリケーション

Word、Excel、PowerPointなどのOffice アプリケーションは、ログイン時に各ユーザーの正しいOneDrive地理的位置を自動的に検出します。 ユーザーは、自分の OneDrive または SharePoint サイトの地域固有の URL を入力する必要がありません。

## <a name="onedrive-sync-app"></a>OneDrive 同期 アプリ

OneDrive 同期 アプリ (バージョン 17.3.6943.0625 以降) は、ユーザーの正しいOneDrive geo の場所を自動的に検出します。 同期アプリのサポートには、地理的な場所に関係なく、グループベースのサイトを同期する機能が含まれます。 Groove 同期クライアントは、複数地域ではサポートされていません。 

## <a name="onedrive-location"></a>OneDrive場所

ユーザーは、優先するデータの場所にOneDriveをプロビジョニングします。 ユーザーが、正しくない地域の場所 (以前の地域の場所からのブックマークなど) を含むOneDrive URL に移動すると、適切な地域の場所のOneDriveに自動的にリダイレクトされます。

## <a name="onedrive-ios-and-android"></a>OneDrive iOS および Android 

OneDrive iOS および Android モバイル アプリでは、地理的な場所に関係なく、共有されているOneDriveファイルとファイルが表示されます。 OneDrive モバイル アプリから検索すると、すべての地域の場所から関連する結果が表示されます。 これらのアプリの最新バージョンをダウンロードします。

詳細については、「[iOS でOneDriveを使用する](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247)」と「[Android のOneDriveを使用](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)する」を参照してください。

## <a name="onedrive-mobile-client"></a>OneDrive モバイル アプリ 

OneDriveモバイル クライアントは複数地域に対応し、すべての地理的位置から関連コンテンツと結果を表示します。

## <a name="search"></a>検索

各地域の場所には、独自の検索インデックスと検索センターがあります。 ユーザーが検索すると、クエリはすべての地域の場所に送信され、返された結果がマージされてランク付けされ、ユーザーが統合された結果を取得します。 ユーザーは、自分の地理的な場所に関係なく、すべての地域の場所から結果を取得します。 詳細については、「[OneDrive Multi-Geoの検索の構成](configure-search-for-multi-geo.md)」を参照してください。

サポートされている検索クライアントは、次のとおりです。

-   OneDrive

-   Delve

-   SharePoint Home

-   検索センター

-   SharePoint 検索 API を使用するカスタムの検索アプリケーション

## <a name="sharepoint-home"></a>SharePoint Home 

SharePoint Multi-Geoでは、SharePointホームは、ユーザーのOneDriveの場所によって決められた場所でホストされます。 たとえば、ユーザーのOneDriveがヨーロッパのサテライトの場所でホストされている場合、SharePoint Home はヨーロッパからレンダリングされます。 SharePoint ホームには、地理的な場所に関係なく、ユーザーに関連するすべてのコンテンツが含まれています。 

**フォローしているサイト、サイトからのニュース、最近のサイト、よく使うサイト、そしておすすめのサイト**

ユーザーが当該コンテンツに対する権限を持っている限り、コンテンツがホストされている地理的な場所に関係なく、これらすべてのコンポーネントが表示されます。 

**おすすめリンク**

管理者は、各地理的な場所に対応して、SharePoint ホームのおすすめリンクを構成できます。 これにより、管理者は各地域の SP ホームでその地域のユーザーに適したリンクをおすすめできます。 

## <a name="sharepoint-mobile-client"></a>SharePoint モバイル クライアント

SharePoint モバイル クライアントは複数地域に対応し、すべての地理的位置から関連コンテンツと結果を表示します。

## <a name="sharing"></a>共有

連絡先の選択のエクスペリエンスでは、地理的な場所に関係なくすべてのユーザーが表示されます。 これにより、ユーザーは、同じ地域または他のテナントの地域内の他のユーザーと共有できます。 さまざまな地域の場所のコンテンツは、ユーザーのOneDrive、Word、Excel、PowerPoint、Office.com の [**自分と共有**] ビューに表示され、ホストされている地域の場所に関係なく、シングル Sign-On エクスペリエンスでアクセスできます。

## <a name="teams-experience"></a>Teams のエクスペリエンス

Teamsは複数地域のサービスです。 OneDrive ファイルと最近表示したファイルは、ユーザーの地理的な場所に関係なく表示されます。 @メンションはすべての地理的な場所からのユーザーに機能します。

## <a name="user-profiles"></a>ユーザー プロファイル

ユーザー プロファイル情報は、ユーザーの地域の場所でマスター管理されます。ユーザーを選択すると、そのユーザーにとって適切な地域の場所に転送され、完全なプロファイルの詳細を確認できます。

Delve がオフの場合、SharePoint の従来の (複数地域に対応していない) プロファイル エクスペリエンスが表示されます。


