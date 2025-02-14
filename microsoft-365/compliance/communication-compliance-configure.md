---
title: コミュニケーション コンプライアンスの使用を開始する
description: コミュニケーション コンプライアンス ポリシーを設定して、レビュー用にユーザー コミュニケーションを構成します。
keywords: Microsoft 365、Microsoft Purview、コンプライアンス、通信コンプライアンス
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: c641a8699f59454bcc756cb0910f18a125d953e6
ms.sourcegitcommit: 221212fff9737e0ea386755deb8fed62ae9c254b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2022
ms.locfileid: "66787674"
---
# <a name="get-started-with-communication-compliance"></a>コミュニケーション コンプライアンスの使用を開始する

コミュニケーション コンプライアンス ポリシーを使用して、内部または外部のレビュー担当者による調査用のユーザー コミュニケーションを識別します。 コミュニケーション コンプライアンス ポリシーを使用して組織内の通信を検出する方法の詳細については、「 [コミュニケーション コンプライアンス ポリシー](/microsoft-365/compliance/communication-compliance-policies)」を参照してください。 Microsoft Teams、Exchange Online、Yammer の通信で不適切なコンテンツを検出するために Contoso が通信コンプライアンス ポリシーをすばやく構成した方法を確認する場合は、この[ケース スタディ](/microsoft-365/compliance/communication-compliance-case-study)を参照してください。

## <a name="subscriptions-and-licensing"></a>サブスクリプションとライセンス

コミュニケーション コンプライアンスを開始する前に、[Microsoft 365 サブスクリプション](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans)とアドオンを確認する必要があります。 コミュニケーション コンプライアンスにアクセスして使用するには、組織に次のいずれかのサブスクリプションまたはアドオンが必要です。

- Microsoft 365 E5/A5/F5/G5 サブスクリプション (有料または試用版)
- Microsoft 365 E3/A3/F3/G5 サブスクリプション + Microsoft 365 E5/A5/F5/G5 コンプライアンス アドオン
- Microsoft 365 E3/A3/F3/G5 サブスクリプション + Microsoft 365 E5/A5/F5/G5 Insider Risk Management アドオン
- Office 365 Enterprise E5 サブスクリプション (有料または試用版)
- Office 365 A5 サブスクリプション (有料または試用版)
- Office 365 Enterprise E3 サブスクリプション + Office 365 Advanced Compliance アドオン (新しいサブスクリプションでは使用できなくなりました。注を参照)

コミュニケーション コンプライアンス ポリシーに含まれるユーザーには、上記のいずれかのライセンスを割り当てる必要があります。 サブスクリプションとライセンスの詳細については、 [セキュリティ&コンプライアンスに関する Microsoft 365 のガイダンスを](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance)参照してください。

> [!IMPORTANT]
> 現在、通信コンプライアンスは、Azure サービスの依存関係でサポートされている地理的リージョンと国でホストされているテナントで利用できます。 組織で通信コンプライアンスがサポートされていることを確認するには、 [国/地域ごとの Azure 依存関係の可用性](/troubleshoot/azure/general/dependency-availability-by-country)に関するページを参照してください。

既存の Office 365 Enterprise E5 プランがなく、コミュニケーション コンプライアンスをお試しになりたい場合は、[Microsoft 365](/office365/admin/try-or-buy-microsoft-365) を既存のサブスクリプションに追加するか、Office 365 Enterprise E5 の[試用版にサインアップ](https://www.microsoft.com/microsoft-365/enterprise)することができます。

> [!NOTE]
> Office 365 Advanced Compliance はスタンドアロン サブスクリプションとして販売されなくなりました。 現在のサブスクリプションの有効期限が切れると、お客様は、同じまたは追加のコンプライアンス機能を含む上記のいずれかのサブスクリプションに移行する必要があります。

## <a name="recommended-actions"></a>推奨処理

推奨されるアクションは、組織がコミュニケーション コンプライアンス機能を使い始め、既存のポリシーを最大限に活用するのに役立ちます。 **[ポリシー]** ページに含まれる推奨アクションは、組織内の通信における機密情報の種類と不適切なコンテンツ アクティビティを分析情報として提供し、要約します。 分析情報は、 [データ分類](/microsoft-365/compliance/data-classification-overview) と機密ラベル、保持ラベル、および機密情報の種類の分類の適用によってサポートされます。 これらの分析情報には、組織内のユーザーの個人を特定できる情報 (PII) は含まれません。

![通信コンプライアンスの推奨アクション。](../media/communication-compliance-recommended-actions.png)

不適切なコンテンツを含むメッセージ内のアクティビティは、不適切なコンテンツ テンプレートを使用する既存のポリシーまたは不適切なコンテンツに分類子を使用するカスタム ポリシーから分類子 [の種類](/microsoft-365/compliance/communication-compliance-policies#classifiers) によって集計されます。 ポリシーのアラート ダッシュボードで、これらのメッセージのアラートを調査します。

[機密情報の種類](/microsoft-365/compliance/communication-compliance-policies#sensitive-information-types)に関連するアクティビティは、既存のポリシーで説明されているメッセージと、既存のポリシーでカバーされていないメッセージで検出されます。 分析情報は、組織が既存の通信コンプライアンス ポリシーで以前に定義していないものも含め、すべての機密情報の種類に対して集計されます。 これらの分析情報を使用して、新しい通信コンプライアンス ポリシーを作成するか、既存のポリシーを更新します。

## <a name="step-1-required-enable-permissions-for-communication-compliance"></a>手順 1 (必須): コミュニケーション コンプライアンスのアクセス許可を有効にする

> [!IMPORTANT]
> ロール グループを構成した後、ロール グループのアクセス許可が組織全体の割り当てられたユーザーに適用されるまでに最大 30 分かかる場合があります。

通信コンプライアンス機能を管理するための初期アクセス許可を構成するために使用される 6 つの役割グループがあります。 Microsoft Purview コンプライアンス ポータルのメニュー オプションとして **通信コンプライアンス** を使用できるようにし、これらの構成手順を続行するには、次のいずれかのロールまたは役割グループに割り当てる必要があります。

- Azure Active Directory [*グローバル管理者*](/azure/active-directory/roles/permissions-reference#global-administrator) ロール
- Azure Active Directory [*コンプライアンス管理者*](/azure/active-directory/roles/permissions-reference#compliance-administrator) ロール
- Microsoft Purview コンプライアンス ポータル [*組織管理*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)役割グループ
- Microsoft Purview コンプライアンス ポータル [*コンプライアンス管理者*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)の役割グループ
- *コミュニケーション コンプライアンス* の役割グループ
- *コミュニケーション コンプライアンス管理* 役割グループ

次のロールのメンバーには、*Communication Compliance 管理* ロール グループに含まれるのと同じソリューションアクセス許可があります。

- Azure Active Directory *グローバル管理者*
- Azure Active Directory *コンプライアンス管理者*
- Microsoft Purview コンプライアンス ポータル *組織管理*
- Microsoft Purview コンプライアンス ポータル *コンプライアンス管理者*

> [!IMPORTANT]
> コミュニケーション コンプライアンスまたは *コミュニケーション コンプライアンス 管理* ロール グループに少なくとも 1  人のユーザーが含まれていることを確認します (選択したオプションに応じて)。 特定のユーザーが組織を離れた場合、コミュニケーション コンプライアンス構成が "ゼロ管理者" シナリオに入らないようにします。

通信コンプライアンス ポリシーとアラートを管理する方法に応じて、ユーザーを特定の役割グループに割り当てて、さまざまな通信コンプライアンス機能のセットを管理する必要があります。 コンプライアンスの責任が異なるユーザーに特定のロール グループを割り当てて、コミュニケーション コンプライアンス機能のさまざまな領域を管理するオプションがあります。 または、指定された管理者、アナリスト、調査担当者、および閲覧者のすべてのユーザー アカウントを、*コミュニケーション コンプライアンス* ロール グループに割り当ててもよいでしょう。 コンプライアンス管理の要件に最適な 1 つのロール グループまたは複数のロール グループを使用します。

通信コンプライアンスを構成および管理する場合は、次のソリューション役割グループオプションから選択します。

| 役割 | ロール権限 |
|:-----|:-----------------|
| **コミュニケーション コンプライアンス** | このロール グループを使用して、1 つのグループ内の組織のコミュニケーション コンプライアンスを管理します。 指定された管理者、アナリスト、調査担当者、閲覧者のすべてのユーザー アカウントを追加することで、コミュニケーション コンプライアンスのアクセス許可を 1 つのグループに構成できます。 このロール グループには、すべてのコミュニケーション コンプライアンスのアクセス許可ロールが含まれます。 この構成は、通信コンプライアンスを迅速に開始する最も簡単な方法であり、個別のユーザー グループに対して個別のアクセス許可を定義する必要がない組織に適しています。 通信コンプライアンス管理者としてポリシーを作成するユーザーは、Exchange Onlineでメールボックスをホストしている必要があります。|
| **コミュニケーション コンプライアンス管理者** | このロール グループを使用して、最初にコミュニケーション コンプラいアナスを構成し、後でコミュニケーション コンプライアンス管理者を定義されたグループに分離します。 このロール グループに割り当てられたユーザーは、コミュニケーション コンプライアンス ポリシー、グローバル設定、およびロール グループの割り当てを作成、読み取り、更新、および削除できます。 この役割グループに割り当てられたユーザーは、メッセージ アラートを表示できません。 通信コンプライアンス管理者としてポリシーを作成するユーザーは、Exchange Onlineでメールボックスをホストしている必要があります。|
| **コミュニケーション コンプライアンス アナリスト** | このグループを使用して、コミュニケーション コンプライアンス アナリストとして機能するユーザーにアクセス許可を割り当てます。 この役割グループに割り当てられているユーザーは、レビュー担当者として割り当てられているポリシーを表示したり、メッセージ メタデータ (メッセージ コンテンツではなく) を表示したり、追加の校閲者にエスカレーションしたり、ユーザーに通知を送信したりできます。 アナリストは保留中のアラートを解決できません。 |
| **コミュニケーション コンプライアンス調査担当者** | このグループを使用して、コミュニケーション コンプライアンス調査担当者として機能するユーザーにアクセス許可を割り当てます。 この役割グループに割り当てられているユーザーは、メッセージ のメタデータとコンテンツを表示し、追加のレビュー担当者にエスカレーションし、電子情報開示 (Premium) ケースにエスカレートし、ユーザーに通知を送信し、アラートを解決できます。 |
| **コミュニケーション コンプライアンス閲覧者** | このグループを使用して、コミュニケーション レポートを管理するユーザーにアクセス許可を割り当てます。 このロール グループに割り当てられたユーザーは、コミュニケーション コンプライアンス ホーム ページのすべてのレポート ウィジェットにアクセスでき、すべてのコミュニケーション コンプライアンス レポートを表示できます。 |

### <a name="option-1-assign-all-compliance-users-to-the-communication-compliance-role-group"></a>オプション 1: すべてのコンプライアンス ユーザーをコミュニケーション コンプライアンス ロール グループに割り当てる

1. Microsoft 365 組織の管理者アカウントの資格情報を使って、[https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) にサインインします。

2. セキュリティ &amp; コンプライアンス センターで、**[アクセス許可]** に移動します。 Office 365 でロールの表示と管理へのリンクを選択します。

3. *[コミュニケーション コンプライアンス]* ロール グループを選択し、**[ロール グループの編集]** を選択します。

4. 左側のナビゲーション ウィンドウから **[メンバーの選択]** を選択し、**[編集]** を選択します。

5. **[追加]** を選択し、*コミュニケーション コンプライアンス* ロール グループに追加するすべてのユーザーのチェック ボックスをオンにします。

6. **[追加]** を選択し、**[完了]** を選択します。

7. **[保存]** を選択して、ユーザーをロール グループに追加します。 **[閉じる]** を選択して手順を完了します

### <a name="option-2-assign-users-to-specific-communication-compliance-role-groups"></a>オプション 2: 特定のコミュニケーション コンプライアンス ロール グループにユーザーを割り当てる

このオプションを使用して、ユーザーを特定のロール グループに割り当てて、組織内のさまざまなユーザー間のコミュニケーション コンプライアンス アクセスと責任をセグメント化します。

1. Microsoft 365 組織内の管理者アカウントの資格情報を使用して [Microsoft Purview コンプライアンス ポータル](https://compliance.microsoft.com)にサインインし、**アクセス許可**</a>に移動します。

2. Office 365 でロールの表示と管理へのリンクを選択します。

3. いずれかのコミュニケーション コンプライアンス ロール グループを選択し、**[ロール グループの編集]** を選択します。

4. 左側のナビゲーション ウィンドウから **[メンバーの選択]** を選択し、**[編集]** を選択します。

5. **[追加]** を選択し、ロール グループに追加するすべてのユーザーのチェック ボックスをオンにします。

6. **[追加]** を選択し、**[完了]** を選択します。

7. **[保存]** を選択して、ユーザーをロール グループに追加します。

8. 次のコミュニケーション コンプライアンス ロール グループを選択し、必要なロール グループごとに手順 4 - 7 を繰り返します。

9. **[閉じる]** を選択して手順を完了します。

ロール グループとアクセス許可の詳細については、「[コンプライアンス センターのアクセス許可](../security/office-365-security/protect-against-threats.md)」を参照してください。

## <a name="step-2-required-enable-the-audit-log"></a>手順 2 (必須): 監査ログを有効にする

コミュニケーション コンプライアンスでは、監査ログを使用してアラートを表示し、レビュー担当者が実行した修復アクションを追跡する必要があります。 監査ログは、定義済みの組織ポリシーに関連付けられているすべてのアクティビティの概要です。また、コミュニケーション コンプライアンス ポリシーに変更があった場合はいつでもその概要を示します。

Microsoft 365 の組織では、監査が既定で有効になっています。 組織によっては、特定の理由で監査を無効にしている場合があります。 組織の監査が無効になっている場合は、別の管理者が無効にしている可能性があります。 この手順を完了する場合は、監査を再びオンにしても問題ないか確認することをお勧めします。

監査を有効にする詳しい手順については、「[監査ログ検索を有効または無効する](/microsoft-365/compliance/turn-audit-log-search-on-or-off)」を参照してください。 監査を有効にすると、監査ログの準備中で、準備が完了してから数時間で検索を実行できるというメッセージが表示されます。 このアクションを行う必要があるのは 1 回だけです。 監査ログの使用の詳細については、「[監査ログを検索する](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance)」を参照してください。

## <a name="step-3-optional-set-up-groups-for-communication-compliance"></a>手順 3 (省略可能): コミュニケーション コンプライアンスのグループを設定する

 コミュニケーション コンプライアンス ポリシーを作成するときは、コミュニケーションをレビューされたユーザーとレビューを実行するユーザーを定義します。 ポリシーでは、メール アドレスを使って、個々のユーザーまたはユーザーのグループを指定します。 セットアップを簡略化するために、コミュニケーションをレビューされたユーザーのグループと、それらのコミュニケーションをレビューするユーザーのグループを作成できます。 グループを使用している場合は、複数必要になる場合があります。 たとえば、2 つの異なるユーザー グループ間の通信を検出する場合や、監視対象ではないグループを指定する場合などです。

次のグラフを使用して、組織内にコミュニケーション コンプライアンス ポリシー用のグループを構成することができます:

| **ポリシー メンバー** | **サポートされているグループ** | **サポートされていないグループ** |
|:-----|:-----|:-----|
|監督対象ユーザー <br> 除外されたユーザー | 配布グループ <br> Microsoft 365 グループ | 動的配布グループ <br> 入れ子になった配布グループ <br> メールが有効なセキュリティ グループ <br> 動的メンバーシップを持つ Microsoft 365 グループ |
| レビュー担当者 | なし | 配布グループ <br> 動的配布グループ <br> 入れ子になった配布グループ <br> メールが有効なセキュリティ グループ |

ポリシーで *配布グループ* を割り当てると、ポリシーは *配布グループ* 内の各ユーザーからのすべての電子メールと Teams チャットを検出します。 ポリシーで *Microsoft 365 グループ* を割り当てると、ポリシーは、各グループ メンバーが受信した個々のメールやチャットではなく *、Microsoft 365 グループ* に送信されたすべてのメールと Teams チャットを検出します。 各ユーザーからの個々のメールと Teams チャットが自動的に検出されるように、通信コンプライアンス ポリシーで配布グループを使用することをお勧めします。

Exchange オンプレミス展開または外部メール プロバイダーを使用している組織で、ユーザーの Microsoft Teams チャットを検出する場合は、オンプレミスまたは外部メールボックスを持つユーザーの配布グループを作成する必要があります。 これらの手順の後半では、ポリシー ウィザードで **監視対象ユーザーおよびグループ** の選択としてこの配布グループを割り当てます。 クラウドベースのストレージを有効にするための要件と制限事項、およびオンプレミス ユーザーに対する Teams のサポートの詳細については、「[オンプレミス ユーザーの Teams チャット データを検索する](/microsoft-365/compliance/search-cloud-based-mailboxes-for-on-premises-users)」を参照してください。

大企業組織で監視対象ユーザーを管理するには、大規模なグループ全体のすべてのユーザーに対するメッセージを検出することが必要な場合があります。 PowerShell を使用して、割り当てられたグループのグローバル コミュニケーション コンプライアンス ポリシーの配布グループを構成できます。 これにより、1 つのポリシーを持つ何千人ものユーザーのメッセージを検出し、新入社員が組織に参加するときに通信コンプライアンス ポリシーを更新し続けることができます。

1. 次のプロパティを使用して、グローバル コミュニケーション コンプライアンス ポリシー専用の[配布グループ](/powershell/module/exchange/new-distributiongroup)を作成します: この配布グループが他の目的や他の Office 365 サービスに使用されていないことを確認します。

    - **MemberDepartRestriction = Closed**。 ユーザーが配布グループから自分を削除できないようにします。
    - **MemberJoinRestriction = Closed**。 ユーザーが配布グループに自分自身を追加できないようにします。
    - **ModerationEnabled = True**。 このグループに送信されるすべてのメッセージが承認の対象であること、およびグループが通信コンプライアンス ポリシー構成の外部で通信するために使用されていないことを確認します。

    ```PowerShell
    New-DistributionGroup -Name <your group name> -Alias <your group alias> -MemberDepartRestriction 'Closed' -MemberJoinRestriction 'Closed' -ModerationEnabled $true
    ```

2. 使用されていない [Exchange カスタム属性](/Exchange/recipients/mailbox-custom-attributes)を選択して、組織のコミュニケーション コンプライアンス ポリシーに追加されたユーザーを追跡します。

3. 定期的なスケジュールで次の PowerShell スクリプトを実行して、ユーザーをコミュニケーション コンプライアンス ポリシーに追加します。

    ```PowerShell
    $Mbx = (Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited -Filter {CustomAttribute9 -eq $Null})
    $i = 0
    ForEach ($M in $Mbx)
    {
      Write-Host "Adding" $M.DisplayName
      Add-DistributionGroupMember -Identity <your group name> -Member $M.DistinguishedName -ErrorAction SilentlyContinue
      Set-Mailbox -Identity $M.Alias -<your custom attribute name> SRAdded
      $i++
    }
    Write-Host $i "Mailboxes added to supervisory review distribution group."
    ```

グループの設定の詳細については、次の記事を参照してください。

- [配布グループを作成して管理する](/Exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups)
- [Microsoft 365 Graph の概要](/office365/admin/create-groups/office-365-groups)

## <a name="step-4-optional-verify-your-yammer-tenant-is-in-native-mode"></a>手順 4 (省略可能): Yammer テナントがネイティブ モードであることを確認する

ネイティブ モードでは、すべての Yammer ユーザーは Azure Active Directory (Azure AD) にあり、すべてのグループは Office 365 グループであり、すべてのファイルは SharePoint Online に保存されます。 コミュニケーション コンプライアンス ポリシーを有効にして、プライベート メッセージ内の危険な会話や Yammer 内のコミュニティ会話をスキャンして識別するためには、Yammer テナントがネイティブ モードである必要があります。

ネイティブ モードでの Yammer 構成の詳細については、以下を参照してください。

- [Microsoft 365 での Yammer ネイティブ モードの概要](/yammer/configure-your-yammer-network/overview-native-mode)
- [Microsoft 365 ネイティブ モードで Yammer ネットワークを構成する](/yammer/configure-your-yammer-network/native-mode)

## <a name="step-5-required-create-a-communication-compliance-policy"></a>手順 5 (必須): コミュニケーション コンプライアンス ポリシーを作成する

>[!IMPORTANT]
>PowerShell を使用した通信コンプライアンス ポリシーの作成と管理はサポートされていません。 これらのポリシーを作成および管理するには、 [通信コンプライアンス ソリューション](https://compliance.microsoft.com/supervisoryreview)でポリシー管理コントロールを使用する必要があります。

>[!TIP]  
>新しい通信コンプライアンス ポリシーを設定し、アラートを修復する詳細なチュートリアルをご覧ください。 [この 15 分間のビデオ](/microsoft-365/compliance/communication-compliance-plan#creating-a-communication-compliance-policy-walkthrough)では、コミュニケーション コンプライアンス ポリシーが不適切なメッセージを検出し、潜在的な違反を調査し、コンプライアンスの問題を修復するのに役立つ方法のデモンストレーションを確認してください。

1. Microsoft 365 組織内の管理者アカウントの資格情報を使用して、[Microsoft Purview コンプライアンス ポータル](https://compliance.microsoft.com)にサインインします。

2. Microsoft Purview コンプライアンス ポータルで、[**通信コンプライアンス**] を選択します。

3. **[ポリシー]** タブを選択します。

4. **[ポリシーの作成]** を選択して、テンプレートから新しいポリシーを作成して構成するか、カスタム ポリシーを作成して構成します。

    ポリシー テンプレートを選択してポリシーを作成する場合は、次の手順を実行します。

    - ポリシー名を確認または更新します。 ポリシーを作成したら、ポリシー名は変更できません。

    - 監督の対象外とするユーザーやグループの選択を含めて、監督するユーザーまたはグループを選択します。 競合するテンプレートを使用する場合は、2 つのグループまたは 2 人のユーザーを選択して内部通信を検出します。

    - ポリシーのレビュー担当者を選択します。 レビュー担当者は個々のユーザーであり、すべてのレビュー担当者は Exchange Online でホストされているメールボックスを持っている必要があります。 ここに追加されたレビュー担当者は、調査と修復ワークフローでアラートをエスカレートするときに選択できるレビュー担当者です。 レビュー担当者は、ポリシーに追加されると、ポリシーへの割り当てを通知し、レビュー プロセスに関する情報へのリンクを提供するメール メッセージを自動的に受信します。

    - 限定された条件フィールドを選択します。通常は、ポリシーに適用する機密情報の種類またはキーワード辞書です。

    > [!NOTE]
    > [光学式文字認識 (OCR)](/microsoft-365/compliance/communication-compliance-policies#optical-character-recognition-ocr)を有効にして、メッセージ内の埋め込み画像または添付画像をスキャンして、ポリシー条件に一致する印刷されたテキストまたは手書きテキストをスキャンしたい場合は、**[ポリシーのカスタマイズ]**  >  **[条件と割合]** を選択し、**[画像から印刷または手書きのテキストを抽出して評価する]** を有効にします。

    ポリシー ウィザードを使用してカスタム ポリシーを作成する場合は、次の操作を行います:

    - ポリシーに名前と説明を付けます。 ポリシー作成後にポリシー名は変更できません。

    - 監視対象のユーザーまたはグループを選択します。これには、組織内のすべてのユーザー、特定のユーザーとグループ、または対象外とする他のユーザーとグループの選択が含まれます。

    - ポリシーのレビュー担当者を選択します。 レビュー担当者は個々のユーザーであり、すべてのレビュー担当者は Exchange Online でホストされているメールボックスを持っている必要があります。 ここに追加されたレビュー担当者は、調査と修復ワークフローでアラートをエスカレートするときに選択できるレビュー担当者です。 レビュー担当者は、ポリシーに追加されると、ポリシーへの割り当てを通知し、レビュー プロセスに関する情報へのリンクを提供するメール メッセージを自動的に受信します。

    - Exchange、Microsoft Teams、Yammer など、スキャンする通信チャネルを選択します。 Microsoft 365 でコネクタを構成した場合は、サードパーティのソースをスキャンすることも選択します。

    - 受信、送信、内部通信など、検出する通信方向を選択します。

    - コミュニケーション コンプライアンス ポリシーの[条件](/microsoft-365/compliance/communication-compliance-policies#conditional-settings)を定義します。 [メッセージ アドレス]、[キーワード]、[ファイルの種類]、および [サイズの一致条件] の中から選ぶことができます。

    - 機密情報の種類を含めるかどうかを選択します。 この手順で、既定およびカスタムの機密情報の種類を選択できます。 既存のカスタムの機密情報の種類から選択するか、コミュニケーション コンプライアンス ウィザードで、カスタムのキーワード辞書を使用します。 必要に応じて、ウィザードを実行する前にこれらの項目を作成できます。 コミュニケーション コンプライアンス ポリシー ウィザード内から新しい機密情報の種類を作成することもできます。

    - 分類子を有効にするかどうかを選択します。 分類子は、メール メッセージまたはその他の種類のテキストの本文で送受信された不適切な言語や画像を検出できます。 次の組み込みの分類子を選択できます: *脅迫*、*冒とく*、*標的を絞った嫌がらせ*、*アダルト画像*、*淫らな画像*、*残虐な画像*。

    - [光学式文字認識 (OCR)](/microsoft-365/compliance/communication-compliance-policies#optical-character-recognition-ocr) を有効にして、メッセージ内の埋め込み画像または添付画像をスキャンして、ポリシー条件に一致する印刷テキストまたは手書きテキストをスキャンします。 カスタム ポリシーの場合、OCR スキャンの選択を有効にするには、テキスト、キーワード、分類子、または機密情報の種類に関連付けられている 1 つ以上の条件付き設定をポリシーで構成する必要があります。

    - レビューする通コミュニケーションの割合を定義します。

    - ポリシーの選択を確認し、ポリシーを作成します。

5. テンプレートを使用する場合は **[ポリシーの作成]** を選択し、カスタム ポリシー ウィザードを使用する場合は **[送信]** を選択します。

6. **[ポリシーが作成されました]** のページには、ポリシーがアクティブ化されるタイミングとキャプチャされるコミュニケーションに関するガイドラインが表示されます。

## <a name="step-6-optional-update-compliance-boundaries-for-communication-compliance-policies"></a>手順 6 (省略可能): 通信コンプライアンス ポリシーのコンプライアンス境界を更新する

[コンプライアンス境界は](/microsoft-365/compliance/set-up-compliance-boundaries) 、電子情報開示マネージャーが検索できるユーザー コンテンツの場所 (メールボックス、OneDrive アカウント、SharePoint サイトなど) を制御する組織内に論理境界を作成します。

組織内でコンプライアンス境界を構成した場合は、特定のユーザーが通信コンプライアンス ポリシーをサポートするメールボックスにアクセスできるように、コンプライアンスの境界を更新する必要があります。 ポリシー管理と調査と修復アクションが正常に機能するためには、コミュニケーション コンプライアンス管理者とコミュニケーション コンプライアンス レビュー担当者へのアクセスを許可する必要があります。

通信コンプライアンス管理者と校閲者のアクセスを許可するには、次の PowerShell コマンドを実行します。 今後新しい通信コンプライアンス ポリシーを追加する場合でも、これらのコマンドを 1 回だけ実行する必要があります。

```powershell
Import-Module ExchangeOnlineManagement
$UserCredential = Get-Credential
Connect-IPPSSession -Credential $UserCredential
New-ComplianceSecurityFilter -FilterName "CC_mailbox" -Users <list your communication compliance admins and reviewers user alias or email address> -Filters "Mailbox_Name -like 'SupervisoryReview{*'" -Action All
```

コマンドレット構文の詳細については、「 [New-ComplianceSecurityFilter」を](/powershell/module/exchange/new-compliancesecurityfilter)参照してください。

## <a name="step-7-optional-create-notice-templates-and-configure-user-anonymization"></a>手順 7 (省略可能): 通知テンプレートを作成し、ユーザーの匿名化を構成する

ポリシー アラートに応答して、関連付けられたユーザーにリマインダー通知を送信するオプションが必要な場合は、少なくとも 1 つの通知テンプレートを組織内に作成する必要があります。 通知テンプレート フィールドは、アラート修復プロセスの一環として送信される前に編集できます。また、コミュニケーション コンプライアンス ポリシーごとにカスタマイズされた通知テンプレートを作成することをお勧めします。

ポリシーの一致を調査し、メッセージに対してアクションを実行するときに、表示されるユーザー名の匿名化を有効にすることもできます。

1. Microsoft 365 組織内の管理者アカウントの資格情報を使用して、[Microsoft Purview コンプライアンス ポータル](https://compliance.microsoft.com)にサインインします。

2. Microsoft Purview コンプライアンス ポータルで、**コミュニケーション コンプライアンス** に移動します。

3. ユーザー名の匿名化を構成するには、**[プライバシー]** タブを選択します。

4. 匿名化を有効にするには **[匿名化されたバージョンのユーザー名を表示する]** を選択します。

5. **[保存]** を選択します。

6. **[通知テンプレート]** タブに移動し、**[通知テンプレート 作成]** を選択します。

7. **[通知テンプレートの変更]** ページで、次のフィールドを入力します:

    - テンプレート名 (必須)
    - 送信元 (必須)
    - CC と BCC (省略可能)
    - 件名 (必須)
    - メッセージ本文 (必須)

8. **[保存]** を選択して、通知テンプレートを作成して保存します。

## <a name="step-8-optional-test-your-communication-compliance-policy"></a>手順 8 (省略可能): 通信コンプライアンス ポリシーをテストする

コミュニケーション コンプライアンス ポリシーを作成したら、定義した条件がポリシーによって適切に実施されていることを確認するためのテストの実施をお勧めします。 通信コンプライアンス ポリシーに機密情報の種類が含まれている場合は[、Microsoft Purview データ損失防止 (DLP)](/microsoft-365/compliance/create-test-tune-dlp-policy) ポリシーをテストすることもできます。 テストするコミュニケーションがキャプチャされるように、ポリシーをアクティブ化する時間をかならず指定します。

以下の手順に従って、コミュニケーション コンプライアンス ポリシーをテストします。

1. テストするポリシーで定義されている監督対象ユーザーとしてサインインしているときに、メール クライアント、Microsoft Teams、または Yammer を開きます。

2. コミュニケーション コンプライアンス ポリシーで定義した基準を満たすメール、Microsoft Teams チャット、または Yammer メッセージを送信します。 このテストは、キーワード、添付ファイルのサイズ、ドメインなどです。ポリシーで構成された条件設定が厳しすぎないか、または緩すぎないかを必ず確認してください。

    > [!NOTE]
    > Email メッセージは、ポリシーの完全な処理に約 24 時間かかる場合があります。 Microsoft Teams、Yammer、およびサード パーティのプラットフォームでの通信は、ポリシーの完全な処理に約 48 時間かかる場合があります。

3. コミュニケーション コンプライアンス ポリシーで指定されたレビュー担当者として Microsoft 365 にサインインします。 **[コミュニケーション コンプライアンス]**  >  **[アラート]** の順に移動して、ポリシーのアラートを表示します。

4. 修復コントロールを使用してアラートを修復し、アラートが正しく解決されていることを確認します。

## <a name="next-steps"></a>次の手順

最初のコミュニケーション コンプライアンス ポリシーを作成する手順を完了すると、24 時間から 48 時間後にアクティビティ インジケーターからアラートを受け取り始めます。 この記事の手順 5 のガイダンスを使用して、必要に応じて追加のポリシーを構成します。

コミュニケーション コンプライアンス アラートについての詳細は、「[コミュニケーション コンプライアンスのアラートを調査し修復する](/microsoft-365/compliance/communication-compliance-investigate-remediate)」を参照してください。

最新の通信コンプライアンス更新プログラムに対応するには、組織の [コミュニケーション コンプライアンス](https://compliance.microsoft.com/)**の新機能** を選択します。
