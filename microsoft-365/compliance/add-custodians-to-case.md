---
title: 電子情報開示 (Premium) ケースにカストディアンを追加する
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Microsoft Purview eDiscovery (Premium) の組み込みのカストディアン管理ツールを使用して、ワークフローを調整し、ケース内の関連データ ソースを特定する方法について説明します。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4e7734e886651cb0169d5823a23790761791eb4e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640988"
---
# <a name="add-custodians-to-an-ediscovery-premium-case"></a>電子情報開示 (Premium) ケースにカストディアンを追加する

Microsoft Purview eDiscovery (Premium) の組み込みのカストディアン管理ツールを使用して、カストディアンの管理とケースに関連する保管データ ソースの特定に関するワークフローを調整します。 カストディアンを追加すると、システムは Exchange メールボックスとOneDrive for Business アカウントを自動的に識別して保留にすることができます。 調査の検出プロセス中に、カストディアンがアクセスまたは貢献した他のデータ ソース (メールボックス、サイト、Teams など) を特定することもできます。 このような場合は、カストディアン管理ツールを使用して、これらのデータ ソースを特定のカストディアンに関連付けることができます。 ケースにカストディアンを追加し、他のデータ ソースをケースに関連付けた後は、データをすばやく保持し、保管データを検索できます。

電子情報開示 (Premium) ケースでは、次の 4 つの手順でカストディアンを追加および管理できます。

1. カストディアンを識別します。

2. カストディアン データの場所を選択します。

3. 保留設定を構成します。

4. カストディアンを確認し、プロセスを完了します。

## <a name="make-sure-you-have-the-necessary-permissions"></a>必要なアクセス許可があることを確認する

ケースにカストディアンを追加するには、電子情報開示マネージャーの役割グループのメンバーである必要があります。 これにより、ケースにカストディアンを追加し、保管データ ソースを保留するために必要なアクセス許可が提供されます。 詳細については、「[電子情報開示のアクセス許可を割り当てる](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions)」を参照してください。電子情報開示のアクセス許可を割り当てる」を参照してください。

## <a name="step-1-identify-custodians"></a>手順 1: カストディアンを特定する

1. [https://compliance.microsoft.com](https://compliance.microsoft.com)適切な電子情報開示アクセス許可が割り当てられているユーザー アカウントに移動してサインインします。

2. Microsoft Purview コンプライアンス ポータルの左側のナビゲーション ウィンドウで、**電子情報開示****電子情報開示** >  (Premium) を選択し、[[**ケース**](https://go.microsoft.com/fwlink/p/?linkid=2173764)] タブを選択します。

3. カストディアンを追加するケースを選択します。

4. [**データ ソース**] タブを選択し、[**データ ソース** > の追加] を選択して **新しいカストディアンを追加** します。

5. ユーザーの名前またはエイリアスの最初の部分を入力して、組織内の 1 人以上のユーザーをカストディアンとしてケースに追加します。 アクティブユーザーと非アクティブユーザーの両方が検索されます。 正しいユーザーを見つけたら、そのユーザーの名前を選択してリストに追加します。 

## <a name="step-2-choose-custodian-data-locations"></a>手順 2: カストディアン データの場所を選択する

カストディアンを選択すると、これらのユーザーとそのデータ ソースの識別と検証が自動的に試行されます。 リストにカストディアンを追加すると、ツールには、カストディアンとして追加されたアクティブな各ユーザーのプライマリ メールボックスと OneDrive アカウントが自動的に含まれます。 ユーザーが非アクティブの場合、ツールはプライマリ メールボックスのみを識別します。 ケースにカストディアンを追加するときに、これらのデータ ソースを含めないように選択できます。

カストディアンのメールボックスと OneDrive アカウントに加えて、他のデータの場所を、SharePoint サイトやカストディアンがメンバーである Microsoft Team などのカストディアンに関連付けることもできます。 これにより、ケースのカストディアンに関連付けられている他のデータ ソースのコンテンツを保持、収集、分析、および確認できます。

カストディアンのプライマリ メールボックスと OneDrive アカウントの選択を解除するには:

1. カストディアンを展開して、各カストディアンに自動的に関連付けられているプライマリ データの場所を表示します。

2. **[メールボックス**] または **[OneDrive**] の横にある **[クリア**] を選択して、カストディアンのメールボックスまたは OneDrive アカウントをこの保管担当者のデータの場所として関連付けから削除します。

   ![保管担当者に関連付ける場所を構成します。](../media/ConfigureCustodianLocations.png)

他のメールボックス、サイト、Teams、または Yammer グループを特定のカストディアンに関連付けるには、

1. カストディアンを展開して、次のサービスを表示して、データの場所をカストディアンに関連付けます。 サービスの横にある **[編集]** をクリックして、データの場所を追加します。

   - **Exchange**: 他のメールボックスをカストディアンに関連付けるために使用します。 検索ボックスに、ユーザー メールボックスまたは配布グループの名前またはエイリアス (3 文字以上) を入力します。 保管担当者に割り当てるメールボックスを選択し、[ **追加**] をクリックします。

   - **SharePoint: SharePoint** サイトをカストディアンに関連付けるために使用します。 一覧でサイトを選択するか、検索ボックスに URL を入力してサイトを検索します。 カストディアンに割り当てるサイトを選択し、[ **追加**] をクリックします。 ユーザーが非アクティブな場合は、OneDrive サイトを SharePoint の場所として追加する必要があります。 

   - **Teams**: カストディアンが現在メンバーになっている Microsoft Teams を割り当てる場合に使用します。 カストディアンに割り当てるチームを選択し、[ **追加**] をクリックします。 チームを追加すると、そのチームに関連付けられている SharePoint サイトとグループ メールボックスが自動的に識別されて検索され、管理者に割り当てられます。

   - **Yammer**: カストディアンが現在メンバーになっている Yammer グループを割り当てる場合に使用します。 カストディアンに割り当てるグループを選択し、[ **追加**] をクリックします。 チームを追加すると、そのグループに関連付けられている SharePoint サイトとグループ メールボックスが自動的に識別されて検索され、管理者に割り当てられます。

   > [!NOTE]
   > **Exchange** と **SharePoint** の場所ピッカーを使用して、組織内のメールボックスまたはサイトをカストディアンに関連付けることができます。 には、カストディアンがメンバーではない Microsoft Team または Yammer グループのメールボックスとサイトの関連付けも含まれます。 これを行うには、各チームまたは Yammer グループに関連付けられているメールボックスとサイトの両方を追加する必要があります。

2. 各カストディアンに割り当てられているメールボックス、サイト、Teams、Yammer グループの合計数を表示するには、テーブル内の各カストディアンを展開します。 各カストディアンに割り当てられたデータの場所を確定すると、これらの関連付けが保持され、電子情報開示 (Premium) ワークフローの収集、処理、および確認の段階で使用されます。

3. カストディアンを追加してデータの場所を構成したら、[ **次へ** ] をクリックして **[保留設定]** ページに移動します。  

## <a name="step-3-configure-hold-settings"></a>手順 3: 保留設定を構成する

 カストディアンとそのデータの場所を確定したら、一部またはすべてのカストディアンを保留にすることができます。 保管担当者を保留にすると、保留リストを削除するか、保管担当者を保留から解放するまで、保管担当者に関連付けられているすべてのコンテンツの場所のすべてのコンテンツが保持されます。 場合によっては、保管担当者を保留にせずにケースに追加することもできます。

カストディアンとデータ ソースを保留にするには、

1. **[保留設定]** ページで、[保留] 列の下にあるチェック ボックスをオンにすると、個々のカストディアンに **保留** を適用できます。

   または、列の上部にある **[保留** ] チェック ボックスをオンにして、すべてのカストディアンを保留にすることもできます。

2. カストディアンホールドの選択を確認し、[ **次へ**] をクリックします。

   > [!NOTE]
   > 保管担当者を保留にしない場合、カストディアンとその関連データ ソースはケースに追加されますが、それらのデータ ソース内のコンテンツはケースに関連付けられたホールドによって保持されません。

## <a name="step-4-review-the-custodians-and-complete-the-process"></a>手順 4: カストディアンを確認し、プロセスを完了する

実際にケースにカストディアンを追加する前に、カストディアンの一覧、それらに割り当てられているデータの場所、および保留設定を確認できます。

1. テーブル内の各カストディアンに関連付けられているすべてのデータ ソース数と保留設定を確認して確認します。 必要に応じて、[管理者の **特定** ] ページまたは **[保留設定]** ページに戻り、変更を加えます。

2. [ **送信]** をクリックして、カストディアンとそのデータの場所をケースに追加し、すべての保管ホールド設定を適用します。

   新しいカストディアンがケースに追加され、[ **データ ソース** ] タブに表示されます。

   [![[データ ソース] タブに一覧表示されるカストディアン。](../media/DataSourcesTab.png) ](../media/DataSourcesTab.png#lightbox)
