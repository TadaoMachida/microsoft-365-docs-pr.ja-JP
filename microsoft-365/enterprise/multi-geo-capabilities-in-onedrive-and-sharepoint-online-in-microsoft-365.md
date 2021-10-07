---
title: OneDrive および SharePoint Online の複数地域機能
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
- m365solution-scenario
- m365solution-spintranet
ms.localizationpriority: medium
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: OneDrive Online の複数地域機能を使用して、複数の地域に Microsoft 365 のプレゼンスを展開します。
ms.openlocfilehash: 52bdbeddec29879e5f985dd1dff64db0d04b8072
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/06/2021
ms.locfileid: "60189035"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>OneDrive および SharePoint Online の複数地域機能

OneDrive および SharePoint Online の複数地域機能を使用すると、SharePoint チーム サイトや Microsoft 365 グループ メールボックスなどの共有リソースを、指定した地域の場所に保存できます。

ユーザー、グループ メールボックス、SharePoint サイトごとに、関連データが格納される地域の場所を示す PDL (Preferred Data Location、優先されるデータの場所) があります。 ユーザーの個人データ (Exchange メールボックスと OneDrive) を、本人が作成した Microsoft 365 グループまたは SharePoint サイトと共に指定された地域の場所に格納して、データ所在地の要件を満たすことができます。 [地域の場所ごとに異なる管理者を指定する](add-a-sharepoint-geo-admin.md)ことができます。

ユーザーが Office アプリケーション、OneDrive、Search などの Microsoft 365 サービスを使用するとき、シームレスなエクスペリエンスが可能になります。 詳細については、「[複数地域環境でのユーザー エクスペリエンス](multi-geo-user-experience.md)」を参照してください。

## <a name="onedrive"></a>OneDrive

各ユーザーの OneDrive は、ユーザーの PDL に従ってサテライトの場所でプロビジョニングされるか、または[管理者が移動させる](move-onedrive-between-geo-locations.md)ことができます。 個人用ファイルはその地域の場所に保存されますが、他の地域の場所にいるユーザーと共有することも可能です。

## <a name="sharepoint-sites-and-groups"></a>SharePoint サイトとグループ

複数地域機能の管理は、SharePoint管理センターから利用できます。 詳細な情報は[対応するブログ記事](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)にあります。

ユーザーが複数地域環境で SharePoint グループに接続されたサイトを作成する場合は、PDL を使用して、サイトと関連付けられているグループ メールボックスが作成される地域の場所を決定します。 (ユーザーの PDL 値が設定されていない場合、またはサテライトの場所として構成されていない地域の場所に設定されている場合、サイトとメールボックスは中央の場所に作成されます)。

Microsoft 365、Exchange、OneDrive、SharePoint、Teams以外のサービスは複数地域ではありません。 ただし、Microsoft 365 によって作成されるグループは、作成者の PDL とその Exchange グループ メールボックスで構成され、SharePoint サイトは対応する geo にプロビジョニングされます。 

## <a name="managing-the-multi-geo-environment"></a>複数地域環境の管理

複数地域環境の設定と管理は、SharePoint 管理センターで行います。 

![管理センターの [地域の場所] ページSharePointスクリーンショット。](../media/sharepoint-multi-geo-admin-center.png)

(SharePoint サイトや OneDrive サイトを移動するなど、一部の操作では Microsoft PowerShell が必要です。)

## <a name="see-also"></a>関連項目

[SharePoint および Microsoft 365 グループでの複数地域機能](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[複数地域環境の管理](administering-a-multi-geo-environment.md)

[複数地域環境における SharePoint ストレージ クォータ](sharepoint-multi-geo-storage-quota.md)

[複数地域環境での Exchange Online メールボックスの管理](administering-exchange-online-multi-geo.md)
