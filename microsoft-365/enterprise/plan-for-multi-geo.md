---
title: Microsoft 365 Multi-Geo の計画
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Microsoft 365 Multi-Geo 複数地域、複数地域のしくみ、およびデータ ストレージに使用できる地理的な場所について説明します。
ms.openlocfilehash: bda48f14b14840eed03d456ef66e7d86df890619
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2022
ms.locfileid: "64822796"
---
# <a name="plan-for-microsoft-365-multi-geo"></a>Microsoft 365 Multi-Geo の計画

このガイダンスは、データ常駐の要件を満たすために、会社のプレゼンスに従って、Microsoft 365 テナントを追加の地域に拡張する準備をしている多国籍企業 (MNC) の管理者向けに設計されています。

複数地域構成では、Microsoft 365 テナントは中央の場所と、1 つ以上のサテライトの場所から構成されます。 これは、複数の地域にまたがる単一のテナントです。 地理的な場所を含むテナント情報は、Azure Active Directory (Azure AD) 内で管理されます。

この構成の基本的な概念についての理解を助けるために、複数地域に関するいくつかの主要な用語を示します。

- **テナント** - Microsoft 365 における組織の表現。通常、1 つ以上のドメインが関連付けられています (例: https://contoso.sharepoint.com))。

- **地理的な場所** – Microsoft 365 テナントのデータをホストできる地理的な場所。

- **サテライトの場所** – Office 365 テナントのデータをホストするように構成した追加の地理的な場所。 複数地域テナントは、複数の地域の場所 (たとえば、北米とヨーロッパ) に展開します。

- **優先するデータの場所 (PDL)** – 個別のユーザーの Exchange および OneDrive データが保存される地域の場所。 この場所は、テナントに対して構成されている地理的位置のいずれかに管理者が設定できます。 既に OneDrive サイトを所有しているユーザーの PDL を変更しても、そのユーザーの OneDrive データは新しい地域の場所に自動的には移動されない点に注意してください。 詳細については、「[別の地域の場所に OneDrive ライブラリを移動する](move-onedrive-between-geo-locations.md)」を参照してください。 Exchange メールボックスがある場合、メールボックスは自動的に新しい優先するデータの場所に移動されます。

複数地域の有効化に必要になる主な 4 つの手順は次のとおりです。

1. アカウント チームと協力して、_Microsoft 365 の複数地域機能_ をサービス プランに追加します。

2. サテライトの場所を選択して、その場所をテナントに追加します。

3. ユーザーの優先するデータの場所を適切なサテライトの場所に設定します。 ユーザーに新しい OneDrive サイトまたは Exchange メールボックスがプロビジョニングされると、そのサイトがユーザーの PDL にプロビジョニングされます。

4. ユーザーの既存の OneDrive サイトを中央の場所から、そのユーザーの優先するデータの場所に移行します (必要な場合)。 (ユーザーの PDL を設定すると、Exchange メールボックスは自動的に移行されます。)

それぞれの手順の詳細については、「[Microsoft 365 Multi-Geo の構成](multi-geo-tenant-configuration.md)」を参照してください。

> [!IMPORTANT]
> Microsoft 365 Multi-Geo は、パフォーマンスの最適化を目的とした設計ではなく、データ所在地に関する要件を満たすように設計されていることにご注意ください。 Microsoft 365 のパフォーマンスを最適化する方法については、「[Microsoft 365 のネットワーク計画とパフォーマンス チューニング](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)」を参照するか、サポート グループにお問い合わせください。

次に示す場所は、OneDrive、SharePoint サイト、Exchange のメールボックスをホストできるサテライトの場所として構成できます。 Multi-Geo の計画をするときには、Microsoft 365 テナントに追加する場所のリストを作成します。 1 つまたは 2 つのサテライトの場所から初めて、必要に応じて段階的に別の地域の場所に拡張することをお勧めします。

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

複数地域を構成するときは、Microsoft 365 への移行と同時にオンプレミスのインフラストラクチャを統合する機会だと考えてください。たとえば、シンガポールとマレーシアにオンプレミス ファームがある場合、データ所在地の要件で許可されているときには、それらのファームを APC サテライトの場所に統合できます。

## <a name="best-practices"></a>ベスト プラクティス

いくつかの初期テストのために、Microsoft 365 にテスト用ユーザーを作成することをお勧めします。 運用ユーザーを複数地域にオンボードする前に、このユーザーとのテストと検証の手順について説明Microsoft 365。

テスト ユーザーによるテストが完了したら、パイロット グループ (IT 部門から) を選択して、新しい地理的な場所でOneDriveとExchangeを最初に使用します。 この最初のグループには、OneDrive をまだ所有していないユーザーを選択します。 この初期グループのユーザーは 5 人未満にして、バッチ ロールアウトのアプローチに従って段階的に増員していきます。

各ユーザーには *優先するデータの場所* (PDL) を設定しておく必要があります。これにより、それぞれのユーザーの OneDrive をプロビジョニングする地域の場所を Microsoft 365 が判断できるようになります。ユーザーの優先するデータの場所は、選択したサテライトの場所のいずれか、または中央の場所と一致する必要があります。PDL フィールドは必須ではありませんが、すべてのユーザーの PDL を設定することをお勧めします。PDL のないユーザーのワークロードは中央の場所にプロビジョニングされます。

ユーザーのリストを作成して、ユーザー プリンシパル名 (UPN) と適切な優先するデータの場所の地域コードを含めます。テスト用ユーザーと初期パイロット グループを含めて開始します。このリストは、構成の手順で必要になります。

ユーザーがオンプレミスの Active Directory システムから Azure Active Directory に同期される場合、同期されるユーザーの優先されるデータの場所を Active Directory 属性にして、Azure Active Directory Connect を使用して設定する必要があります。 同期されるユーザーの優先されるデータの場所は、Azure AD PowerShell を使用して直接構成することはできません。 Active Directory で PDL を設定して同期する手順については、「[Azure Active Directory Connect 同期: Microsoft 365 リソースの優先されるデータの場所を構成する](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)」を参照してください。

複数地域テナントの管理は、複数地域ではないテナントの管理と異なることがあり、SharePoint および OneDrive の設定と機能の多くが複数地域に対応しています。構成を進める前に、「[複数地域環境の管理](administering-a-multi-geo-environment.md)」を確認することをお勧めします。

[複数地域環境でのエンド ユーザーのエクスペリエンス](multi-geo-user-experience.md)の詳細については、複数地域環境のユーザー エクスペリエンスに関するページを参照してください。

Microsoft 365 Multi-Geo 複数地域の構成を開始する場合は、「[Microsoft 365 Multi-Geo の構成](multi-geo-tenant-configuration.md)」を参照してください。

構成の完了後は、ユーザーが優先するデータの場所から作業するために必要になる、[ユーザーの OneDrive ライブラリの移行](move-onedrive-between-geo-locations.md)を必ず実行してください。

## <a name="related-topics"></a>関連項目

[Microsoft 365 Multi-Geo 電子情報開示の構成](./multi-geo-ediscovery-configuration.md)
