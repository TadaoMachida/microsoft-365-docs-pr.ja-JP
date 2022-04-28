---
title: Office 365 エンドポイントを管理する
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: エンタープライズ組織のネットワーク アーキテクチャで動作するように Office 365 エンドポイントを管理する方法について説明します。
ms.openlocfilehash: 6743ab1c3241b84b0eb1dd3e9f5e67e100e18b40
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090343"
---
# <a name="managing-office-365-endpoints"></a>Office 365 エンドポイントを管理する

複数の異なる場所にオフィスを構え、接続 WAN を使用しているエンタープライズ組織のほとんどで、Office 365 のネットワーク接続用の構成が必要です。信頼できるすべての Office 365 ネットワーク要求をファイアウォール経由で直接送信し、追加のパケット レベルの検査または処理はすべてバイパスすることで、ご使用のネットワークを最適化できます。これにより、待機時間と境界の容量要件が削減されます。Office 365 のネットワーク トラフィックを識別することが、ユーザーに最適なパフォーマンスを提供するための第一歩です。Office 365 のネットワーク接続の詳細については、「[Office 365 ネットワーク接続の原則](microsoft-365-network-connectivity-principles.md)」を参照してください。

Microsoft では、[Office 365 IP アドレスと URL の Web サービス](microsoft-365-ip-web-service.md) を使用して、Office 365 ネットワーク エンドポイントおよびそれらに対する進行中の変更にアクセスすることをお勧めします。

重要な Office 365 ネットワーク トラフィックの管理方法にかかわらず、Office 365 にはインターネット接続が必要です。接続が必要なその他のネットワーク エンドポイントは、「[Office 365 IP アドレスと URL Web サービスに含まれないその他のエンドポイント](additional-office365-ip-addresses-and-urls.md)」に記載されています。

Office 365 ネットワーク エンドポイントの使用方法は、エンタープライズ組織のネットワーク アーキテクチャによって決まります。この記事では、エンタープライズ ネットワーク アーキテクチャを Office 365 IP アドレスおよび URL と統合するためのいくつかの方法を概説しています。信頼できるネットワーク要求を選択するための最も簡単な方法は、各オフィスの所在地で Office 365 の自動構成をサポートする SD-WAN デバイスを使用することです。

## <a name="sd-wan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>重要な Office 365 ネットワーク トラフィックのローカル ブランチ送信用 SD-WAN

各ブランチ オフィスの所在地で、Office 365 の最適化カテゴリのエンドポイント、または最適化および許可カテゴリのエンドポイントへのトラフィックを直接 Microsoft のネットワークにルーティングするように構成されている SD-WAN デバイスを提供できます。その他のネットワーク トラフィック (オンプレミス データセンター トラフィック、一般的なインターネット Web サイトのトラフィック、および Office 365 の既定カテゴリのエンドポイントに対するトラフィックなど) は、より強固なネットワーク境界を持つ別の場所に送信されます。

Microsoft は SD-WAN のプロバイダーと協力し、自動構成を可能にしています。詳細については、「[Office 365 ネットワーク パートナー プログラム](microsoft-365-networking-partner-program.md)」を参照してください。

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>重要な Office 365 トラフィックの直接ルーティング用 PAC ファイルの使用

PAC または WPAD ファイルを使用して、Office 365 と関連付けられているが、IP アドレスを持たないネットワーク要求を管理します。プロキシまたは境界デバイスを介して送信される一般的なネットワーク要求は、待機時間を増大させます。SSL の中断と検査によって待機時間が最長になる一方、プロキシ認証や評価の検索などのその他のサービスは、パフォーマンスとユーザー エクスペリエンスを低下させます。また、これらの境界ネットワーク デバイスには、すべてのネットワーク接続要求を処理するために十分な容量が必要です。直接の Office 365 ネットワーク要求のために、プロキシまたは検査デバイスをバイパスすることをお勧めします。
  
[PowerShell Gallery の Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) は、Office 365 IP アドレスと URL Web サービスから最新のネットワーク エンドポイントを読み取り、サンプル PAC ファイルを作成する PowerShell スクリプトです。このスクリプトを変更して、既存の PAC ファイル管理と統合させることができます。

![ファイアウォールとプロキシ経由で Office 365 に接続する。](../media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**図 1 - 単純なエンタープライズ ネットワーク境界**

PAC ファイルは、図 1 のポイント 1 で Web ブラウザーに展開されます。重要な Office 365 ネットワーク トラフィックの直接送信に PAC ファイルを使用する場合は、ご使用のネットワーク境界ファイアウォールでこれらの URL の背後にある IP アドレスへの接続も許可する必要があります。これには、PAC ファイルで指定されているものと同じ Office 365 エンドポイント カテゴリの IP アドレスを取得し、これらのアドレスに基づくファイアウォール ACL を作成します。ファイアウォールは、図 1 のポイント 3 です。

それとは別に、最適化カテゴリのエンドポイントの直接ルーティングのみを行う場合は、それ以降の処理をバイパスするために、プロキシ サーバーに送信する必要なすべての許可カテゴリのエンドポイントをプロキシ サーバーにリストする必要があります。たとえば、SSL の中断と検査およびプロキシ認証は、最適化および許可いずれのカテゴリのエンドポイントとも互換性がありません。プロキシ サーバーは、図 1 のポイント 2 です。

一般的な構成は、プロキシ サーバーからの送信トラフィックをまったく処理せずに、プロキシ サーバーに到達する Office 365 ネットワーク トラフィックの宛先 IP アドレスを許可するというものです。SSL の中断と検査に関する問題の詳細については、「[Office 365 トラフィックに対するサード パーティ製のネットワーク デバイスまたはソリューションの使用](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)」を参照してください。

Get-PacFile スクリプトでは、次の 2 つの型のPAC ファイルが生成されます。

| 型 | 説明 |
|:-----|:-----|
|**1** <br/> |最適化エンドポイント トラフィックを直接送信し、その他すべてのトラフィックはプロキシ サーバーに送信します。 <br/> |
|**2** <br/> |最適化および許可エンドポイント トラフィックを直接送信し、その他すべてのトラフィックはプロキシ サーバーに送信します。この型のファイルは、サポートされているすべての ExpressRoute for Office 365 トラフィックを ExpressRoute ネットワーク セグメントに送信し、その他すべてのトラフィックをプロキシ サーバーに送信するためにも使用できます。 <br/> |

PowerShell スクリプトを呼び出す簡単な例を次に示します。

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

スクリプトに渡すことができるパラメーターは多数あります。

| パラメーター | 説明 |
|:-----|:-----|
|**ClientRequestId** <br/> |このパラメーターは必須です。呼び出しを行うクライアント マシンを表す GUID で、Web サービスに渡されます。 <br/> |
|**Instance** <br/> |既定で Worldwide に設定される Office 365 サービス インスタンスです。これも Web サービスに渡されます。 <br/> |
|**TenantName** <br/> |ご使用の Office 365 テナント名。Web サービスに渡され、一部の Office 365 URL で置換可能なパラメーターとして使用されます。 <br/> |
|**Type** <br/> |生成するプロキシ PAC ファイルの型。 <br/> |

追加のパラメーターを指定して PowerShell スクリプトを呼び出す別の例を、次に示します。

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>プロキシ サーバーによる Office 365 ネットワーク トラフィック処理のバイパス

PAC ファイルを直接送信トラフィックに使用しない場合でも、プロキシ サーバーを構成して、ネットワーク境界での処理をバイパスすることをお勧めします。一部のプロキシ サーバー ベンダーでは、[Office 365 ネットワーク パートナー プログラム](microsoft-365-networking-partner-program.md)で説明されているように、これが自動構成されています。

この構成を手動で行う場合は、Office 365 IP アドレスと URL の Web サービスから最適化および許可カテゴリのエンドポイント データを取得して、これらの処理をバイパスするようにプロキシ サーバーを構成する必要があります。最適化および許可カテゴリのエンドポイントに対しては、SSL 中断と検査およびプロキシ認証を行わないようにすることが重要です。
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Office 365 IP アドレスと URL の変更管理

ご使用のネットワーク境界に適切な構成を選択することに加え、Office 365 エンドポイントの変更管理プロセスを採用することも重要です。これらのエンドポイントは定期的に変更され、変更を管理しない場合、新しい IP アドレスや URL の追加後に、ユーザーのブロックやパフォーマンスの低下が引き起こされる可能性があります。

Office 365 IP アドレスと URL の変更は通常、各月の末日近くに公開されます。場合によっては、運用、サポート、またはセキュリティ上の必要により、このスケジュール外に変更が公開されることもあります。

IP アドレスまたは URL が追加されたために、ユーザーによる対応が必要な変更が公開された場合は、30 日前 (変更が公開された時点から、そのエンドポイントで Office 365 サービスが有効になるまでの期間) の通知がユーザーに送信されます。これが有効開始日として反映されます。Microsoft ではこの通知期間を確保するよう努めていますが、運用、サポート、またはセキュリティ上の必要性によって、常に確保できるとは限りません。接続を保持するために即時の対応が不要な変更 (IP アドレスまたは URL の削除や、重要度の低い変更など) の場合、事前通知はありません。このような場合、有効日はありません。指定されている通知の型にかかわらず、各変更がサービスで有効になる予定日を記載します。

### <a name="change-notification-using-the-web-service"></a>Web サービスを使用した変更通知

Office 365 IP アドレスと URL Web サービスを使用して、変更通知を取得できます。1 時間に 1 回 **/version** Web メソッドを呼び出して、Office 365 に接続するために使用しているエンドポイントのバージョンを確認することをお勧めします。使用中のバージョンと比べて、このバージョンが変更されている場合は、**/endpoints** Web メソッドから最新のエンドポイント データを取得する必要があります。また、必要に応じて、**/changes** Web メソッドから差分も取得します。検出されたバージョンに変更がない場合は、**/endpoints** および **/changes** Web メソッドを呼び出す必要はありません。

詳細については、「[Office 365 IP アドレスと URL の Web サービス](microsoft-365-ip-web-service.md)」を参照してください。

### <a name="change-notification-using-rss-feeds"></a>RSS フィードを使用した変更通知

Office 365 IP アドレスと URL の Web サービスでは、Outlook で登録できる RSS フィードが提供されます。Office 365 サービス インスタンス固有の各ページに、IP アドレスと URL の RSS URL へのリンクがあります。詳細については、「[Office 365 IP アドレスと URL の Web サービス](microsoft-365-ip-web-service.md)」を参照してください。

### <a name="change-notification-and-approval-review-using-power-automate"></a>Power Automate を使用した変更通知および承認確認

毎月行われるネットワーク エンドポイントの変更を手動で処理する必要がある方もいらっしゃるでしょう。Power Automate を使用すれば、Office 365 のネットワーク エンドポイントに変更があったときに、電子メールで通知し、必要に応じて、変更の承認プロセスを実行するフローを作成できます。確認が完了したら、ファイアウォールとプロキシ サーバーの管理チームに、自動的に電子メールで変更を通知するように設定できます。

Power Automate のサンプルおよびテンプレートの詳細については、「[Power Automate を使用して、Office 365 IP アドレスや URL への変更のメール通知を受け取る](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)」を参照してください。
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Office 365 のネットワーク エンドポイントについてよく寄せられる質問

Office 365 ネットワーク接続に関してよく寄せられるこれらの質問を参照してください。
  
### <a name="how-do-i-submit-a-question"></a>質問を送信するにはどうすればよいですか?

下部のリンクをクリックして、記事が役に立ったかどうかを示し、追加の質問を送信してください。Microsoft は皆様からのフィードバックを確認し、よく寄せられる質問でここの質問を更新しています。
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>テナントの場所を確認するにはどうすればよいですか?

 **テナントの場所** は、Microsoft の [データセンター マップ](./o365-data-locations.md)を使用して最適な場所が決定されます。
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>私は Microsoft と適切にピアリングされていますか?

 **ピアリング場所** の詳細については、[Microsoft とのピアリングのページ](https://www.microsoft.com/peering)を参照してください。
  
世界中に 2,500 を超える ISP ピアリング リレーションシップと 70 を超えるポイントがあるため、ユーザーのネットワークから Microsoft のネットワークへの接続はシームレスであるはずです。数分あれば、ISP のピアリング リレーションシップが最適であることを確認することができます。Microsoft ネットワークとのピアリング手順の[よい例と悪い例については、こちら](/archive/blogs/onthewire/__guidance)を参照してください。
  
<a name="bkmk_MissingIP"> </a>
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>公開済みの一覧に掲載されていない IP アドレスに対してネットワーク要求を受け取ります。それらの IP アドレスに対してアクセス権を付与する必要はありますか?

Microsoft では、直接ルーティングする必要がある Office 365 サーバーの IP アドレスのみを公開しています。公開されている一覧には、ネットワーク要求が示されるすべての IP アドレスが記載されているわけではありません。ユーザーは、Microsoft とサード パーティが所有している未公開の IP アドレスに対するネットワーク要求も受け取ります。このような IP アドレスは、動的に生成または管理されているため、変更されたときに適時の通知を行うことができません。ご使用のファイアウォールで、これらのネットワーク要求の FQDN に基づいてアクセスを許可できない場合は、PAC または WPAD ファイルを使用して要求を管理してください。
  
Office 365 と関連付けられた IP の詳細を確認するには、以下の手順を実行してください。
  
1. [IPv4](https://www.ipaddressguide.com/cidr) や [IPv6](https://www.ipaddressguide.com/ipv6-cidr) などの CIDR 計算ツールを使用して、より広く公開されている範囲に IP アドレスが含まれているかどうかを確認します。 たとえば、40.103.0.1 が含まれる IP アドレス 40.96.0.0/13 には、40.96 は一致しますが、40.103 は一致しません。
2. [whois クエリ](https://dnsquery.org/) を使用して、パートナーが IP を所有しているかどうかを確認します。 Microsoft 所有の場合は、内部パートナーの可能性があります。 多くのパートナーのネットワーク エンドポイントは、IP アドレスが公開されていない _既定_ のカテゴリに属しているものとして一覧表示されます。
3. IP アドレスは、Office 365 または依存関係の一部ではない可能性があります。 Office 365 ネットワーク エンドポイントの発行には、Microsoft のネットワーク エンドポイントすべては含まれません。
4. 証明書を確認します。ブラウザーで *HTTPS://\<IP_ADDRESS\>* を使用して IP アドレスに接続し、証明書に表示されるドメインを確認して、IP アドレスに関連付けられているドメインを把握します。Microsoft 所有の IP アドレスで、Office 365 の IP アドレス一覧に掲載されていない場合、その IP アドレスは、*MSOCDN.NET* や IP 情報が公開されていない他の Microsoft ドメインなど、Microsoft CDN に関連付けられている可能性があります。証明書のドメインが、Microsoft が IP アドレスの登録を主張しているドメインの場合は、お知らせください。

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>一部の Office 365 URL が、DNS 内の A レコードではなく CNAME レコードを指しています。CNAME レコードはどのように扱えばよいでしょうか?

クライアント コンピューターがクラウド サービスに接続するには、1 つ以上の IP アドレスが含まれる DNS A レコードまたは AAAA レコードが必要です。Office 365 に含まれる一部の URL は、A レコードまたは AAAA レコードではなく CNAME レコードを示します。こうした CNAME レコードは中間レコードで、一連の処理の途中であるものもあります。最終的には、特定の IP アドレスの A レコードまたは AAAA レコードに必ず解決されます。たとえば、最終的に IP アドレス _IP_1_ に解決される以下の一連の DNS レコードについて考慮してみましょう。

```console
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

これらの CNAME リダイレクトは DNS の通常の一部分であり、クライアント コンピューターとプロキシ サーバーに対して透過的です。負荷分散、コンテンツ配信ネットワーク、高可用性、サービス インシデントの軽減に使用されます。Microsoft はこうした中間 CNAME レコードを公開せず、任意の時点で変更する可能性があります。そのため、ご使用のプロキシ サーバーで許可されている方法で構成する必要はありません。

プロキシ サーバーは最初の URL (前述の例の場合、serviceA.office.com) を検証し、この URL が Office 365 の発行に含まれるようになります。プロキシ サーバーはこの URL の DNS を解決して特定の IP アドレスになるように要求し、IP_1 が戻されることになります。中間の CNAME リダイレクト レコードの検証は行いません。

ハードコーディングされた構成や、間接 Office 365 FQDN に基づく許可リストの使用は推奨されておらず、Microsoft もサポートしていません。さらに、ユーザー接続の問題が生じる原因となることが分かっています。CNAME リダイレクトをブロックしたり、Office 365 DNS エントリを不適切に解決したりする DNS ソリューションは、DNS 再帰が有効になっている DNS フォワーダーまたは DNS ルート ヒントを使用して解決することができます。多くのサード パーティのネットワーク境界製品では、[Office 365 IP アドレスと URL の Web サービス](microsoft-365-ip-web-service.md) を使用して、推奨されている Office 365 エンドポイントが許可リストに含まれるように自社の構成でネイティブに統合されています。

<a name="bkmk_akamai"> </a>
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Microsoft ドメイン名に nsatc.net や akadns.net などの名前が表示されるのはなぜですか?

Office 365 と他の Microsoft サービスは、Akamai や MarkMonitor などのいくつかのサードパーティ サービスを使用し、Office 365 の操作性を高めています。お客様の操作性を可能な限り高めるために、将来これらのサービスを変更する可能性があります。サード パーティ ドメインは、CDN などのコンテンツをホストする場合があります。また、地理的なトラフィック管理サービスなどのサービスをホストする場合があります。現在、次のようなサービスが使用されています:
  
*\*.nsatc.net* を含む要求が表示される場合、[MarkMonitor](https://www.markmonitor.com/) が使用されています。このサービスは、ドメイン名の保護と、悪意のある動作に対して保護するための監視サービスを提供しています。
  
*\*.exacttarget.com* に対する要求が表示される場合、[ExactTarget](https://www.marketingcloud.com/) が使用されています。このサービスは、メール リンク管理と悪意のある動作に対する監視サービスを提供しています。
  
次のいずれかの FQDN を含む要求が表示される場合、[Akamai](https://www.akamai.com/) が使用されています。このサービスは、geo-DNS サービスとコンテンツ配信ネットワーク サービスを提供しています。
  
```console
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

<a name="bkmk_thirdparty"> </a>
### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Office 365 への接続を最小限にする必要があります

Office 365 はインターネット上で機能するように構築された一連のサービスであり、信頼性と可用性の保証は、使用可能な多数の標準インターネット サービスに基づいています。最新のインターネット サービスを使用するには、DNS、CRL、CDN などの標準インターネット サービスに到達可能である必要がありますが、同様に、Office 365 を使用するためにも標準インターネット サービスに到達可能である必要があります。

Office 365 スイートは、複数の主なサービス分野から構成されています。これらのサービス分野への接続は、選択的に有効にすることができます。また、すべてのサービス分野が依存し、常に必須である共通分野があります。

| サービス分野 | 説明 |
|:-----|:-----|
|**Exchange** <br/> |Exchange Online および Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online と OneDrive for Business <br/> |
|**Skype for Business Online および Microsoft Teams** <br/> |Skype for Business および Microsoft Teams <br/> |
|**共通** <br/> |Office 365 Pro Plus、Office ブラウザー、Azure AD、およびその他の一般的なネットワーク エンドポイント <br/> |

基本的なインターネット サービスに加え、機能を統合するためにのみ使用されるサード パーティ サービスがあります。これらは統合のために必要ですが、Office 365 エンドポイントの記事ではオプションと示されています。オプションとは、エンドポイントにアクセスできなくても、サービスのコア機能は動作することを意味します。必須であるすべてのネットワーク エンドポイントでは、必須属性が true に設定されます。オプションのネットワーク エンドポイントでは、必須属性が false に設定され、通知属性によって、接続がブロックされた場合に失われる機能の詳細が示されます。
  
Office 365 を使用しようとして、サードパーティ サービスにアクセスできなかった場合、[この記事で必須またはオプションと記載されているすべての FQDN がプロキシとファイアウォールで許可されていることを確認します](urls-and-ip-address-ranges.md)。
  
<a name="bkmk_consumer"> </a>
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Microsoft のコンシューマー サービスへのアクセスをブロックするにはどうすればよいですか?

テナント制限機能では、OneDrive、Hotmail、Xbox.com など、すべての Microsoft コンシューマー アプリケーション (MSA アプリ) の使用のブロックがサポートされるようになりました。 これで、login.live.com エンドポイントに別のヘッダーが使用されます。 詳細については、「[テナント制限使用による SaaS クラウド アプリケーションへのアクセスの管理](/azure/active-directory/manage-apps/tenant-restrictions#blocking-consumer-applications)」を参照してください。

<a name="bkmk_IPOnlyFirewall"> </a>
### <a name="my-firewall-requires-ip-addresses-and-cannot-process-urls-how-do-i-configure-it-for-office-365"></a>ファイアウォールには IP アドレスが必要で、URL を処理することはできません。 Office 365 に合わせて構成する方法

Office 365 では、必要なすべてのネットワークエンド ポイント用 IP アドレスは提供されません。 一部は URL としてだけ提供され、既定に分類されます。 必要な既定のカテゴリの URL は、プロキシ サーバー経由で許可する必要があります。 プロキシ サーバーを所有していない場合は、ユーザーが Web ブラウザーのアドレス バーに入力する URL に対して Web 要求を構成している方法を確認してください。ユーザーが IP アドレスを提供することはありません。 Office 365 の既定のカテゴリ URL に IP アドレスがない場合でも、同じ方法で構成する必要があります。

## <a name="related-topics"></a>関連項目

[Office 365 IP アドレスと URL の Web サービス](microsoft-365-ip-web-service.md)

[Microsoft Azure データ センターの IP 範囲](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft パブリック IP スペース](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Microsoft Intune のネットワーク インフラストラクチャの要件](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute と Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365 の URL と IP アドレスの範囲](urls-and-ip-address-ranges.md)
  
[Office 365 向け ExpressRoute の管理](managing-expressroute-for-connectivity.md)
  
[Office 365 ネットワーク接続の原則](microsoft-365-network-connectivity-principles.md)
