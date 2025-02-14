---
title: Microsoft 365 で Slack 電子情報開示データをアーカイブするコネクタを設定する
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: 管理者は、Veritas Slack 電子情報開示から Microsoft 365 にデータをインポートおよびアーカイブするためのコネクタを設定できます。 このコネクタを使用すると、Microsoft 365 のサード パーティのデータ ソースからデータをアーカイブできます。 このデータをアーカイブした後、訴訟ホールド、コンテンツ検索、保持ポリシーなどのコンプライアンス機能を使用して、サード パーティのデータを管理できます。
ms.openlocfilehash: e48bd25b5f444ce17eba08677f5bd1c1171af1ff
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637751"
---
# <a name="set-up-a-connector-to-archive-slack-ediscovery-data"></a>Slack 電子情報開示データをアーカイブするコネクタを設定する

Microsoft Purview コンプライアンス ポータルの Veritas コネクタを使用して、ソーシャル メディア、インスタント メッセージング、ドキュメント コラボレーション プラットフォームから Microsoft 365 組織内のメールボックスにサード パーティのデータをインポートおよびアーカイブします。 Veritas には、サード パーティのデータ ソースからアイテムを (定期的に) キャプチャし、その項目を Microsoft 365 にインポートするように構成された [Slack](https://globanet.com/slack/) コネクタが用意されています。 Slack は、Slack API からメッセージとファイルをプルし、メール メッセージ形式に変換して、アイテムをユーザー メールボックスにインポートします。

Slack 電子情報開示データがユーザー メールボックスに格納された後、訴訟ホールド、電子情報開示、アイテム保持ポリシーと保持ラベル、通信コンプライアンスなどの Microsoft Purview 機能を適用できます。 Slack コネクタを使用して Microsoft 365 のデータをインポートおよびアーカイブすると、組織が政府および規制のポリシーに準拠し続けることができます。

## <a name="overview-of-archiving-slack-ediscovery-data"></a>Slack 電子情報開示データのアーカイブの概要

次の概要では、コネクタを使用して Microsoft 365 で Slack 情報をアーカイブするプロセスについて説明します。

![Slack アーカイブ ワークフロー。](../media/SlackConnectorWorkflow.png)

1. 組織は Slack と連携して Slack サイトを設定および構成します。

2. 24 時間に 1 回、Slack 電子情報開示からのチャット メッセージが Veritas Merge1 サイトにコピーされます。 また、コネクタはチャット メッセージの内容を電子メール メッセージ形式に変換します。

3. コンプライアンス ポータルで作成した Slack 電子情報開示コネクタは、毎日 Veritas Merge1 サイトに接続し、チャット メッセージを Microsoft クラウドの安全な Azure Storage の場所に転送します。

4. コネクタは、手順 3 で説明したように、 *電子メール* プロパティの値と自動ユーザー マッピングを使用して、変換されたチャット メッセージ アイテムを特定のユーザーのメールボックスにインポートします。 **Slack 電子情報開示** という名前の受信トレイ フォルダー内の新しいサブフォルダーがユーザー メールボックスに作成され、チャット メッセージアイテムがそのフォルダーにインポートされます。 コネクタは、 *Email* プロパティの値を使用して、アイテムをインポートするメールボックスを決定します。 すべてのチャット メッセージにはこのプロパティが含まれています。このプロパティには、チャット メッセージのすべての参加者の電子メール アドレスが入力されます。

## <a name="before-you-begin"></a>はじめに

- Microsoft コネクタの Veritas Merge1 アカウントを作成します。 アカウントを作成するには、 [Veritas カスタマー サポート](https://globanet.com/ms-connectors-contact)にお問い合わせください。 手順 1 でコネクタを作成するときに、このアカウントにサインインします。

- 組織の Slack エンタープライズ アカウントのユーザー名とパスワードを取得します。 Slack を構成するときは、手順 2. でこのアカウントにサインインする必要があります。

- 手順 1 で Slack 電子情報開示コネクタを作成し、手順 3 で完了したユーザーには、Data Connector 管理 ロールを割り当てる必要があります。 このロールは、コンプライアンス ポータルの **[データ コネクタ** ] ページでコネクタを追加するために必要です。 このロールは、既定で複数の役割グループに追加されます。 これらの役割グループの一覧については、「セキュリティ & コンプライアンス センターのアクセス許可」の「 [セキュリティとコンプライアンス センターの](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)ロール」セクションを参照してください。 または、組織内の管理者がカスタムロール グループを作成し、Data Connector 管理ロールを割り当ててから、適切なユーザーをメンバーとして追加することもできます。 手順については、[Microsoft Purview コンプライアンス ポータルのアクセス許可](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group)の「カスタム ロール グループの作成」セクションを参照してください。

- この Veritas データ コネクタは、Microsoft 365 US Government クラウドの GCC 環境でパブリック プレビュー段階にあります。 サード パーティのアプリケーションとサービスには、Microsoft 365 インフラストラクチャの外部にあり、Microsoft Purview およびデータ保護コミットメントの対象外であるサード パーティ システムに対する組織の顧客データの保存、送信、処理が含まれる場合があります。 Microsoft は、この製品を使用してサード パーティ製アプリケーションに接続することは、これらのサードパーティ アプリケーションが FEDRAMP に準拠していることを意味することを示しません。

## <a name="step-1-set-up-the-slack-ediscovery-connector"></a>手順 1: Slack 電子情報開示コネクタを設定する

最初の手順では、コンプライアンス ポータルの **[データ コネクタ** ] ページにアクセスし、Slack データ用のコネクタを作成します。

1. [https://compliance.microsoft.com](https://compliance.microsoft.com/) **[データ コネクタ** > **] の [Slack 電子情報開示**] に移動してクリックします。

2. **Slack 電子情報開示** 製品の説明ページで、[**コネクタの追加**] をクリックします。

3. [利用規約] ページ **で** 、[ **同意** する] をクリックします。

4. コネクタを識別する一意の名前を入力し、[ **次へ**] をクリックします。

5. Merge1 アカウントにサインインしてコネクタを構成します。

## <a name="step-2-configure-slack-ediscovery"></a>手順 2: Slack 電子情報開示を構成する

2 番目の手順では、Merge1 サイトで Slack 電子情報開示コネクタを構成します。 Veritas Merge1 サイトで Slack 電子情報開示コネクタを構成する方法の詳細については、「 [Merge1 サード パーティ コネクタ ユーザー ガイド」を](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Slack%20eDiscovery%20User%20Guide.pdf)参照してください。

[ **保存&完了**] をクリックすると、コンプライアンス ポータルのコネクタ ウィザードの **[ユーザー マッピング** ] ページが表示されます。

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>手順 3: ユーザーをマップし、コネクタのセットアップを完了する

1. [ **外部ユーザーを Microsoft 365 ユーザーにマップする** ] ページで、自動ユーザー マッピングを有効にします。

   Slack 電子情報開示アイテム *には、組織内* のユーザーの電子メール アドレスを含む Email というプロパティが含まれています。 コネクタがこのアドレスを Microsoft 365 ユーザーに関連付けることができる場合、アイテムはそのユーザーのメールボックスにインポートされます。

2. [ **次へ**] をクリックして設定を確認し、[ **データ コネクタ** ] ページに移動して、新しいコネクタのインポート プロセスの進行状況を確認します。

## <a name="step-4-monitor-the-slack-ediscovery-connector"></a>手順 4: Slack 電子情報開示コネクタを監視する

Slack 電子情報開示コネクタを作成した後、コンプライアンス ポータルでコネクタの状態を表示できます。

1. 左側の [https://compliance.microsoft.com](https://compliance.microsoft.com) ナビゲーションにある **[データ コネクタ** ] に移動してクリックします。

2. [ **コネクタ** ] タブをクリックし、 **Slack 電子情報開示** コネクタを選択してポップアップ ページを表示します。 このページには、コネクタに関するプロパティと情報が含まれています。

3. **[コネクタの状態とソース**] で、[**ログのダウンロード**] リンクをクリックして、コネクタの状態ログを開く (または保存) します。 このログには、Microsoft クラウドにインポートされたデータに関する情報が含まれています。 詳細については、「 [データ コネクタの管理者ログを表示する」を](data-connector-admin-logs.md)参照してください。

## <a name="known-issues"></a>既知の問題

- 現時点では、10 MB を超える添付ファイルやアイテムのインポートはサポートされていません。 より大きなアイテムのサポートは、後日提供される予定です。