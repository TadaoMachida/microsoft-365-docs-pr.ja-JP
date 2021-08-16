---
title: Azure に Microsoft 365 の高可用性フェデレーション認証を展開する
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: '概要: ユーザーサブスクリプションの高可用性フェデレーション認証を構成Microsoft 365でMicrosoft Azure。'
ms.openlocfilehash: 2bbd802a3ed3e7cc553d95e346d6b793b59f3533
ms.sourcegitcommit: e269371de759a1a747c9f292775463aa11415f25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2021
ms.locfileid: "58356818"
---
# <a name="deploy-high-availability-federated-authentication-for-microsoft-365-in-azure"></a>Azure に Microsoft 365 の高可用性フェデレーション認証を展開する

この記事では、次の仮想マシンを使用して Azure インフラストラクチャ サービスに Microsoft Microsoft 365の高可用性フェデレーション認証を展開する手順について説明します。
  
- 2 つの Web アプリケーション プロキシ サーバー
    
- 2 つの Active Directory フェデレーション サービス (AD FS) サーバー
    
- 2 つのレプリカ ドメイン コントローラー
    
- Azure AD Connect を実行する 1 つのディレクトリ同期サーバー
    
各サーバーのプレース ホルダー名を使用した構成がこちらです。
  
**Azure のインフラストラクチャの高可用性フェデレーションMicrosoft 365認証**

![Azure のフェデレーション認証インフラストラクチャMicrosoft 365の最終的な構成](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
すべての仮想マシンが単一のクロスプレミス Azure 仮想ネットワーク (VNet) に入っています。 
  
> [!NOTE]
> 個々のユーザーのフェデレーション認証は、オンプレミスのリソースには依存しません。ただし、クロスプレミス接続が使用できなくなると、オンプレミスの Active Directory Domain Services (AD DS) で加えられたユーザー アカウントとグループに対する更新が VNet 内のドメイン コントローラーで受信されなくなります。これを回避するために、クロスプレミス接続で高可用性を構成できます。詳細については、「[高可用性のクロスプレミス接続および VNet 間接続](/azure/vpn-gateway/vpn-gateway-highlyavailable)」を参照してください。
  
特定の役割を持つ仮想マシンの各ペアが独自のサブネットと可用性セットに入っています。
  
> [!NOTE]
> この VNet はオンプレミスのネットワークに接続されているため、この構成に管理サブネット上の jumpbox や仮想マシンの監視は含まれません。詳細については、「[N 層のアーキテクチャで Windows VM を実行する](/azure/guidance/guidance-compute-n-tier-vm)」を参照してください。 
  
この構成の結果、すべての Microsoft 365 ユーザーに対してフェデレーション認証が行え、AD DS 資格情報を使用して Microsoft 365 アカウントではなくサインインできます。 フェデレーション認証インフラストラクチャでは、オンプレミスの境界ネットワークよりも Azure インフラストラクチャ サービスでより簡単に展開できるサーバーの冗長セットが使用されます。
  
## <a name="bill-of-materials"></a>部品表

このベースライン構成には、Azure のサービスおよびコンポーネントの次のセットが必要です。
  
- 7 つの仮想マシン
    
- 4 つのサブネットを持つ 1 つのクロスプレミス仮想ネットワーク
    
- 4 つのリソース グループ
    
- 3 つの可用性セット
    
- 1 つの Azure サブスクリプション
    
仮想マシンと、この構成用の既定サイズを次に示します。
  
|**アイテム**|**仮想マシンの説明**|**Azure ギャラリー イメージ**|**既定のサイズ**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |1 つ目のドメイン コントローラー  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|2.  <br/> |2 つ目のドメイン コントローラー  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|3.  <br/> |Azure AD Connect サーバー  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|4.  <br/> |1 つ目の AD FS サーバー  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|5.  <br/> |2 つ目の AD FS サーバー  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|6.  <br/> |1 つ目の Web アプリケーション プロキシ サーバー  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|7.  <br/> |2 つ目の Web アプリケーション プロキシ サーバー  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
   
この構成の見積もりコストを計算するには、「[料金計算ツール](https://azure.microsoft.com/pricing/calculator/)」を参照してください
  
## <a name="phases-of-deployment"></a>展開のフェーズ

次のフェーズでは、このワークロードを展開します。
  
- [フェーズ 1: Azure を構成する](high-availability-federated-authentication-phase-1-configure-azure.md)。リソース グループ、ストレージ アカウント、可用性セット、およびクロスプレミスの仮想ネットワークを作成します。
    
- [フェーズ 2: ドメイン コントローラーを構成する](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)。 レプリカの AD DS ドメイン コントローラーとディレクトリ同期サーバーを作成して構成します。
    
- [フェーズ 3: AD FS サーバーを構成する](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)。2 つの AD FS サーバーを作成して構成します。
    
- [フェーズ 4: Web アプリケーション プロキシを構成する](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)。2 つの Web アプリケーション プロキシ サーバーを作成して構成します。
    
- [フェーズ 5: フェデレーション認証を構成Microsoft 365。](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) サブスクリプションのフェデレーション認証をMicrosoft 365します。
    
これらの記事では、Azure インフラストラクチャ サービスで機能する高可用性フェデレーション認証を作成する定義済みのアーキテクチャに関する、段階的な事前Microsoft 365ガイドを提供します。 以下の点にご注意ください。
  
- 経験豊富な AD FS の実行者である場合、フェーズ 3 と 4 の手順を自由に適応させて、自分のニーズに最適なサーバーのセットを構築できます。
    
- 既存のクロスプレミスの仮想ネットワークを使用した既存の Azure ハイブリッド クラウド展開がある場合は、フェーズ 1 と 2 の手順を自由に適応させるかスキップして、AD FS と Web アプリケーション プロキシ サーバーを適切なサブネットに配置できます。
    
開発/テスト環境またはこの構成の概念実証を構築するには、「フェデレーション id for your [Microsoft 365/テスト環境」を参照してください](federated-identity-for-your-microsoft-365-dev-test-environment.md)。
  
## <a name="next-step"></a>次の手順

このワークロードの構成を「[フェーズ 1: Azure を構成する](high-availability-federated-authentication-phase-1-configure-azure.md)」から開始します。  
