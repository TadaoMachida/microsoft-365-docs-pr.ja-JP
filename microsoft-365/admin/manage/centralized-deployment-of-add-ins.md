---
title: 組織でアドインの集中展開が機能するかどうかを判断する
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b4527d49-4073-4b43-8274-31b7a3166f92
description: テナントとユーザーが要件を満たしていることを確認し、集中展開を使用してアドインを展開Officeします。
ms.openlocfilehash: 409a19f9e3579978eb3e3cf03d087820e494e181
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2022
ms.locfileid: "61933769"
---
# <a name="determine-if-centralized-deployment-of-add-ins-works-for-your-organization"></a>組織でアドインの集中展開が機能するかどうかを判断する

集中展開は、ほとんどのお客様が組織内のユーザーやグループに Officeアドインを展開するための、推奨される機能豊富な方法です。 管理者の場合は、このガイダンスを使用して、組織とユーザーが要件を満たしていることを確認し、集中展開を使用できます。

一元展開には、次のような利点があります。

- 管理者は、ユーザー、グループ経由で複数のユーザー、または組織内のすべてのユーザーにアドインを直接展開して割り当てできます (詳細については、「管理者要件」セクションを参照してください)。

- 関連するアプリケーションOfficeすると、アドインは自動的にダウンロードされます。 アドインがアドイン コマンドをサポートしている場合、アドインは自動的にアドイン アプリケーション内のリボンにOfficeされます。

- 管理者がアドインをオフまたは削除した場合、またはユーザーが Azure Active Directory またはアドインが割り当てられているグループから削除された場合、ユーザーのアドインは表示されなくなりました。

一元展開では、3 つのデスクトップ プラットフォームWindows Mac、および Online Officeできます。 一元展開では、iOS と Android もサポートしています (Outlook アドインのみ)。

すべてのユーザーのクライアントにアドインが表示されるには、最大 24 時間かかる場合があります。

## <a name="before-you-begin"></a>開始する前に

アドインの一元展開では、ユーザーが Microsoft 365 Business ライセンス (Business Basic、Business Standard、Business プレミアム)、Office 365 Enterprise ライセンス (E1/E3/E5/F3)、または Microsoft 365 Enterprise ライセンス (E3/E5/F3) を使用している必要があります (Office 組織 ID、Office 365 Education ライセンス (A1/A3/A5)、または Microsoft 365 Education ライセンス (A3/A5) を使用し、Exchange Online およびアクティブな Exchange Online メールボックスを持っています。 サブスクリプション ディレクトリは、サブスクリプション ディレクトリ内に存在するか、またはサブスクリプション ディレクトリにAzure Active Directory。
次の手順に従って、OfficeとExchange要件を確認したり、集中展開の互換性チェックを[使用できます](#centralized-deployment-compatibility-checker)。

一元展開は、次の機能をサポートしていません。

- MSI バージョンを対象とするOffice (ただし、Outlook 2016)
- オンプレミスのディレクトリ サービス
- On-Prem メールボックスへのアドインExchange展開
- SharePoint に展開するアドイン
- Teamsアプリ
- コンポーネント オブジェクト モデル (COM) または Visual Studio Tools for Office (VSTO) アドインの展開。
- SKU などのMicrosoft 365を含Exchange Onlineの展開: Microsoft 365 Apps for Business、Microsoft 365 Apps Enterprise。

### <a name="office-requirements"></a>Office要件

- Word、Excel、PowerPointアドインの場合、ユーザーは次のいずれかを使用している必要があります。
  - Windows デバイスのバージョン 1704 以降の Microsoft 365 Business ライセンス (Business Basic、Business Standard、Business プレミアム)、Office 365 Enterprise ライセンス (E1/E3/E5/F3)、または Microsoft 365 Enterprise ライセンス (E3/E5/F3)。
  - Mac のバージョン 15.34 以降。

- このOutlook、ユーザーは次のいずれかを使用している必要があります。
  - Microsoft 365 Business ライセンス (Business Basic、Business Standard、Business プレミアム)、Office 365 Enterprise ライセンス (E1/E3/E5/F3)、または Microsoft 365 Enterprise ライセンス (E3/E5/F3) のバージョン 1701 以降。
  - バージョン 1808 以降のバージョンOffice Professional Plus 2019 2019 Office Standard。
  - バージョン 16.0.4494.1000 以降の Office Professional Plus 2016 (MSI) または Office Standard 2016 (MSI)\*
  - バージョン 15.0.4937.1000 以降の Office Professional Plus 2013 (MSI) または Office Standard (MSI)\*
  - バージョン 16.0.9318.1000 以降のバージョンOffice 2016 for Mac
- iOS 用モバイルのバージョン 2.75.0 以降Outlookバージョン 2.75.0 以降
- Android 用モバイルのバージョン 2.2.145 Outlook以降

    *MSI バージョンの Outlookは、適切な Outlook リボンに管理者がインストールしたアドインを表示します。"My add-ins" セクションは表示されません。

### <a name="exchange-online-requirements"></a>Exchange Online要件

Microsoft Exchangeは、組織のテナント内にアドイン マニフェストを格納します。 アドインを展開する管理者と、それらのアドインを受け取るユーザーは、OAuth 認証をサポートする Exchange Online上にある必要があります。

組織の Exchange 管理者に、どの構成を使用できるのかを確認してください。ユーザーごとの OAuth 認証接続は、[Test-OAuthConnectivity](/powershell/module/exchange/test-oauthconnectivity) PowerShell コマンドレットを使用して、検証できます。

### <a name="admin-requirements"></a>管理者の要件

集中展開を介してアドインを展開するには、組織のグローバル管理者または管理者Exchange必要があります。

> [!NOTE]
> 次Exchangeに示すように、管理者がアドインを展開できるのは、Azure Active Directory 管理センターで App **Registrations** プロパティが true に設定されている場合のみです。
>
> ![image](https://user-images.githubusercontent.com/89943918/144516704-8874a10d-b540-41f3-ae9d-c07a8d7e143f.png)


### <a name="centralized-deployment-compatibility-checker"></a>集中展開の互換性チェック

集中展開互換性チェッカーを使用して、テナントのユーザーが Word、Excel、および PowerPoint の集中展開を使用するために設定されているかどうかを確認できます。 互換性チェックは、サポートをサポートするためにOutlookではありません。 互換性チェック [をダウンロードします](https://aka.ms/officeaddindeploymentorgcompatibilitychecker)。

#### <a name="run-the-compatibility-checker"></a>互換性チェックを実行する

1. 管理者特権のウィンドウPowerShell.exeします。

2. 次のコマンドを実行します。

   ```powershell
   Import-Module O365CompatibilityChecker
   ```

3. **Invoke-CompatabilityCheck コマンドを実行** します。

   ```powershell
   Invoke-CompatibilityCheck
   ```
   このコマンドは *_、TenantDomain_* *(TailspinToysIncorporated.onmicrosoft など) の入力を求めるプロンプトを表示します。 </span>com)**_および TenantAdmin_* 資格情報 (グローバル管理者資格情報を使用)、同意を要求します。

   > [!NOTE]
   > テナントのユーザー数によって、チェックが完了するのに数分または数時間かかる場合があります。 
  
ツールの実行が完了すると、コンマ区切り (.csv) 形式で出力ファイルが作成されます。 既定では、ファイル **は現在の作業ディレクトリ** に保存されます。 出力ファイルには、次の情報が含まれます。

- ユーザー名

- ユーザー ID (ユーザーのメール アドレス)

- 一元展開の準備完了 - 残りの項目が TRUE の場合

- Officeプラン - ライセンスOfficeのプラン

- ライセンス認証された Office - Office をライセンス認証している場合

- サポートされているメールボックス - OAuth 対応メールボックスを使用している場合

> [!NOTE]
> サーバーの全体展開 PowerShell モジュールを使用する場合、多要素認証はサポートされません。 モジュールは基本認証でのみ動作します。

## <a name="user-and-group-assignments"></a>ユーザーとグループの割り当て

集中展開機能は、現在、Azure Active Directory、配布リスト、セキュリティ グループなど、Microsoft 365でサポートされているグループの大部分をサポートしています。

> [!NOTE]
> メールが有効ではないセキュリティ グループは、現段階ではサポートされていません。

集中展開は、テナント内の個々のユーザー、グループ、およびすべてのユーザーへの割り当てをサポートします。 集中展開は、上位レベルのグループまたは親グループのないグループのユーザーをサポートしますが、ネストされたグループまたは親グループを持つグループのユーザーはサポートされません。

次の例では、Sandra、Sheila、「営業部門」のグループがアドインに割り当てられています。「西海岸営業部門」は入れ子のグループのため、Bert と Fred はアドインに割り当てられていません。

![MicrosoftTeams-image](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)


### <a name="find-out-if-a-group-contains-nested-groups"></a>グループにネストされたグループが含まれているかどうかを調べる

グループにネストされたグループが含まれているかどうかを調べる最も簡単な方法は、Outlook 内のグループの連絡先カードを確認することです。 電子メールの **[To]** フィールドにグループ名を入力し、解決時にグループ名を選択すると、グループ名にユーザーまたは入れ子になったグループが含まれているかが表示されます。 次の例では、「テスト グループ」での Outlook 情報先カードの [ **メンバー**] タブには、ユーザーはなく、2 つのサブ グループのみが表示されています。

![連絡先カードの [Outlook] タブ。](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)

反対のクエリを実行できます。グループを解決して、任意のグループのユーザーがいないかどうかを表示します。次の例では、「サブ グループ 1」が「テスト グループ」のメンバーである Outlook 情報先カードの [ **メンバーシップ**] タブの下に表示されます。

![連絡先カードの [Outlook] タブ。](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)

または、Azure Active Directory Graph API でクエリを実行して、グループ内でのグループ一覧を見つけます。詳細については、「[Operations on groups | Graph API reference (グループに対する操作 | Graph API リファレンス)](/previous-versions/azure/ad/graph/api/groups-operations)」を参照してください。

### <a name="contacting-microsoft-for-support"></a>Microsoft に連絡してサポートを受ける

web 用 Office アプリ (Word、Excel など) の使用中にアドインの読み込み中に問題が発生した場合は、Microsoft サポートに問い合わせが必要な場合があります[(方法](../../business-video/get-help-support.md)について説明します)。 サポート チケットに、ユーザーのMicrosoft 365情報を入力します。

| プラットフォーム | デバッグ情報 |
|:-----|:-----|
|Office | Charles/Fiddler ログ  <br/>  テナント ID ([方法の詳細](/onedrive/find-your-office-365-tenant-id))  <br/>  CorrelationID。 1 つの Office ページのソースを表示し、相関 ID の値を探してサポートに送信します。  <br/>`<input name=" **wdCorrelationId**" type="hidden" value=" **{BC17079E-505F-3000-C177-26A8E27EB623}**">`  <br/>  `<input name="user_id" type="hidden" value="1003bffd96933623"></form>` |
|リッチ クライアント (Windows、Mac) | Charles/Fiddler ログ  <br/>  クライアント アプリのビルド番号 (できれば **File/Account** のスクリーンショットとして) |

## <a name="related-content"></a>関連コンテンツ

[管理センターにアドインを展開](../manage/manage-deployment-of-add-ins.md) する (記事)\
[管理センターでアドインを管理](manage-addins-in-the-admin-center.md) する (記事)\
[集中展開に関する FAQ](../manage/centralized-deployment-faq.yml) (記事)\
[ビジネス ユーザー Microsoft 365最新の Officeクライアント](../setup/upgrade-users-to-latest-office-client.md)にアップグレードする (記事)
 
