---
title: Microsoft 365 に送信されるメールのトラブルシューティング
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: troubleshooting
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: f4caa4e1-e414-4b21-8822-31c08064c059
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: この記事では、Microsoft 365のお客様への一括メール送信に関するベスト プラクティスMicrosoft 365 &、受信トレイに電子メールを送信する際の問題に関するトラブルシューティング情報を提供します。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 37703ccb0ffb37163033bb2fdca24566a33bb275
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128436"
---
# <a name="troubleshooting-mail-sent-to-microsoft-365"></a>Microsoft 365 に送信されるメールのトラブルシューティング

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**適用対象**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 プラン 1 およびプラン 2](defender-for-office-365.md)

この記事では、Microsoft 365の受信トレイに電子メールを送信しようとしたときに問題が発生している送信者のトラブルシューティング情報と、顧客への一括メール送信のベスト プラクティスについて説明します。

## <a name="are-you-managing-your-ip-and-domains-sending-reputation"></a>IP およびドメインの評価の管理者ですか

EOP フィルタリング テクノロジは、Microsoft 365やその他の Microsoft 製品 (Exchange Serverなど) にスパム対策保護を提供するように設計されています。 また、SPF、DKIM、DMARC も使用しています。電子メールを送信するドメインが許可されていることを確認することで、スプーフィングとフィッシングの問題に対処するのに役立つ電子メール認証テクノロジ。 EOP フィルター処理は、送信 IP、ドメイン、認証、リストの精度、苦情率、コンテンツなどに関連する多くの要因の影響を受けます。 そのうち、送信者の評判を下げる主な要因の 1 つであり、メールを配信する能力は迷惑メールの苦情率です。

## <a name="are-you-sending-email-from-new-ip-addresses"></a>新しい IP アドレスから電子メールを送信していますか

通常、電子メールを送信するために初めて使用する IP アドレスには、当社のシステムで構築された評価はありません。その結果、新しい IP アドレスからの電子メールでは、配信の問題が発生する可能性が高くなります。迷惑メールを送信しないための評価が IP で構築されると、通常 EOP の電子メール配信エクスペリエンスは向上します。

既存の SPF レコードで認証されているドメインに追加される新しい IP アドレスの場合、通常、そのドメインの送信評価の一部を継承できるという利点があります。ご使用のドメインの送信評価が優れていると、新しい IP の評価もすぐに向上します。新しい IP は、ボリューム、配布リストの正確さ、迷惑メールの苦情の割合に応じて、数週間またはすぐにでも、評価が向上することを期待できます。

## <a name="confirm-that-your-dns-is-set-up-correctly"></a>DNS が正しく設定されていることを確認する

メールのルーティングに必要な MX レコードなど、DNS レコードの作成と保守の手順については、DNS ホスティング プロバイダーに確認する必要があります。

## <a name="ensure-that-you-do-not-advertise-yourself-as-a-non-routable-ip"></a>ルーティング不能な IP で自分をアドバタイズしていないことを確認する

DNS 逆引き参照を行えない送信者からの電子メールは受け付けないことがあります。場合によっては、正当な送信者が、EOP に対して接続しようとするときに、インターネット ルーティング不能な IP で自身をアドバタイズすることがあります。プライベート (ルーティング不能な) ネットワーク用に予約されている IP アドレスは次のとおりです。

- 192.168.0.0/16 (または 192.168.0.0 ～ 192.168.255.255)
- 10.0.0.0/8 (または 10.0.0.0 ～ 10.255.255.255)
- 172.16.0.0/11 (または 172.16.0.0 ～ 172.31.255.255)

## <a name="you-received-a-non-delivery-report-ndr-when-sending-email-to-a-user-in-office-365"></a>Office 365 でユーザーに電子メールを送信すると、配信不能レポート (NDR) を受信する

一部の配信の問題の原因は、Microsoft によって送信者の IP アドレスがブロックされていることや、ユーザーのアカウントが以前の迷惑メール処理によって禁止された送信者として識別されていることにあります。エラーがあって NDR を受信したと分かっている場合には、まず、NDR メッセージに記載されている指示に従って問題を解決してください。

受信したエラーの詳細については、[Exchange Onlineの電子メール配信不能レポート](/exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online)のエラー コードの一覧を参照してください。

 たとえば、次の NDR を受け取った場合、送信 IP アドレスが Microsoft によってブロックされたことを示します。

 `550 5.7.606-649 Access denied, banned sending IP [x.x.x.x]; To request removal from this list please visit https://sender.office.com/ and follow the directions.`

この一覧からの削除を要求するには、 [リスト削除ポータルを使用して、ブロックされている送信者リストから自分を削除します](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md)。

## <a name="my-email-landed-in-the-recipients-junk-email-folder"></a>受信者の迷惑メール フォルダーにメールが届いた

EOP によってメッセージが誤ってスパムとして識別された場合は、受信者と協力して、メッセージを評価して分析する Microsoft Spam Analysis Team にこの誤検知メッセージを送信できます。 詳細については、「[メッセージとファイルを Microsoft に報告する](report-junk-email-messages-to-microsoft.md)」を参照してください。

## <a name="traffic-from-my-ip-address-is-throttled-by-eop"></a>自分の IP アドレスからのトラフィックが EOP によって調整される

IP アドレスが EOP によって調整されたことを示す NDR を EOP から受信することがあります。例:

 `host xxxx.outlook.com [x.x.x.x]: 451 4.7.550 Access denied, please try again later`

不審な動作が対象の IP アドレスで検出され、さらに詳しく評価される間、一時的に制限されているために NDR を受信しました。評価によって疑いが晴れると、この制限はすぐ解除されます。

## <a name="i-cant-receive-email-from-senders-in-microsoft-365"></a>Microsoft 365の送信者から電子メールを受信できない

 Microsoft ユーザーからのメッセージを受信するには、ご使用のネットワークが Microsoft データセンター内で EOP が使用している IP アドレスからの接続を許可していることを確認してください。 詳細については、「[Exchange Online Protection IP アドレス](../../enterprise/urls-and-ip-address-ranges.md)」を参照してください。

## <a name="best-practices-for-bulk-emailing-to-microsoft-365-users"></a>Microsoft 365 ユーザーへの一括メール送信のベスト プラクティス

多くの場合、ユーザーに Microsoft 365対して一括メール キャンペーンを行い、メールが安全かつタイムリーに届くようお考えの場合は、このセクションのヒントに従ってください。

### <a name="ensure-that-the-from-name-reflects-who-is-sending-the-message"></a>From 名にメッセージを送信するユーザーが反映されていることを確認する

[件名] はメッセージの内容に関する要約で、メッセージ本文には、オファリング、サービス、製品について明瞭かつ簡潔に記されている必要があります。 例：

正しい:

> From: marketing@shoppershandbag.com <br> 件名: クリスマスシーズンのカタログを更新しました。

正しくない:

> From: someone@outlook.com <br> 件名: カタログ

送信元について、また実行内容について分かりやすくすれば、ほとんどのスパム フィルターに引っかかることなく配信しやすくなります。

### <a name="always-include-an-unsubscribe-option-in-campaign-emails"></a>キャンペーン電子メールには必ず登録解除オプションを含める

マーケティング電子メール、特にニュースレターなどでは、その後の電子メールを登録解除する方法を必ず含める必要があります。例：

 `This email was sent to example@contoso.com by sender@fabrikam.com.`

 `Update Profile/Email Address | Instant removal with SafeUnsubscribe&trade; | Privacy Policy`

一部の送信者は、「登録解除」という件名で特定のエイリアスに電子メールを送信することを受信者に求めています。これよりも、上記の例の 1 回のクリックで完了する操作を推奨します。受信者に電子メールを送信することを要求する場合、ユーザーがリンクをクリックする際に、すべての必須フィールドにあらかじめデータが入っているようにしてください。

### <a name="use-the-double-opt-in-option-for-marketing-email-or-newsletter-registration"></a>マーケティング電子メールまたはニュースレターの登録にダブル オプトイン オプションを使用する

業界におけるこのベスト プラクティスは、会社の製品またはサービスを利用するためにユーザーによる連絡先情報の登録が必須である、または推奨される場合に適しています。一部の会社では、登録プロセスの際にマーケティング電子メールまたはニュースレターにユーザーを自動的にサインアップするようになっていますが、これは電子メールのフィルタリングにおいては問題のあるマーケティング手法であると見なされています。

登録プロセスで、「はい、ニュースレターを送信してください」、「はい、特別なオファーを送信してください」などのチェックボックスが既定で選択されていると、不注意なユーザーが、受信の必要のないマーケティング電子メールやニュースレターに意図せずにサインアップする可能性があります。

 代わりに、ダブル オプトイン オプションをお勧めします。つまり、マーケティングメールやニュースレターのチェック ボックスは既定でオフになっています。 さらに、登録フォームが送信されると、マーケティングメールを受け取る決定を確認できる URL を持つ確認メールがユーザーに送信されます。

 これにより、マーケティング電子メールを本当に受信する意志があるユーザーだけが電子メールにサインアップするようになり、以降は、問題のあるマーケティング電子メール手法を送信元の会社から排除できます。

### <a name="ensure-that-email-message-content-is-transparent-and-traceable"></a>電子メール メッセージの内容が透過的かつトレース可能であることを確認する

電子メールの送信方法と同様、その内容も重要になります。電子メール コンテンツを作成するときは、次のベスト プラクティスを使用して、電子メールがフィルタリング サービスによってフラグ設定されないようにする必要があります。

- 送信者をアドレス帳に追加するよう、電子メール・メッセージが受信者に要求する場合、そうした操作がメールの配信を保証するものではないことを明記する必要があります。

- メッセージ本文に含まれるリダイレクトは、類似性と一貫性があるべきで、多種多様であってはなりません。このコンテキストのリダイレクトとは、リンクやドキュメントなど、メッセージから離れた任意の対象のことです。広告や登録解除リンク、またはプロファイルの更新リンクがたくさんある場合には、すべてが同じドメインを指していなければなりません。例：

  正しい (すべてのドメインが同じ)。

  `unsubscribe.bulkmailer.com`

  `profile.bulkmailer.com`

  `options.bulkmailer.com`

  正しくありません (すべてのドメインが異なります)。

  `unsubscribe.bulkmailer.com`

  `profile.excite.com`

  `options.yahoo.com`

- サイズの大きな画像や添付ファイル、画像だけのメッセージは避けてください。

- パブリック プライバシーまたは P3P 設定では、トラッキング ピクセルが存在することを明記する必要があります (Web バグまたはビーコン)。

### <a name="remove-incorrect-email-aliases-from-your-databases"></a>データベースから不正な電子メール エイリアスを削除する

バウンス バックを作成するデータベース内のすべての電子メール エイリアスは不要であり、電子メールのフィルタリング サービスによってさらにセキュリティを確保するうえで送信メールを危険にさらすものです。電子メール データベースを最新の情報に保ってください。
