---
title: 複数地域環境の管理
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
localization_priority: Normal
description: 管理者は、複数地域の環境でSharePointサービスOneDrive管理する方法について学習できます。
ms.openlocfilehash: e1c608425c25c018eddebe14023537b2739694d110d3683829c861dd96a61c73
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/05/2021
ms.locfileid: "53795208"
---
# <a name="administering-a-multi-geo-environment"></a>複数地域環境の管理

ここでは、複数地域環境で Microsoft 365 のサービスが動作するしくみについて説明します。

## <a name="administrator-experience"></a>管理者エクスペリエンス

管理[センター SharePoint](https://admin.microsoft.com/sharepoint)左側のナビゲーションに[地域の場所] タブが表示され、地域の場所を表示および管理できる地理的位置マップが表示されます。 テナントの地理的な場所を追加または削除するには、このページを使用します。

## <a name="audit-log-search"></a>監査ログ検索

すべてのサテライト地域に対して統合された[監査ログ](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)は、Microsoft 365 監査ログの検索ページから利用できます。 すべての地域からの監査ログのエントリを参照できます。たとえば、NAM ユーザーと EUR ユーザーのアクティビティが、1 つの組織ビューに表示され、既存のフィルターを適用することで特定のユーザーのアクティビティを確認できます。

## <a name="bcs-secure-store-apps"></a>BCS、Secure Store、Apps

BCS、Secure Store、およびすべての App は、各サテライトの場所に個別のインスタンスがあります。そのため、SharePoint Online 管理者は、これらのサービスを各サテライトの場所とは別に管理および構成する必要があります。

## <a name="compliance-admin-center"></a>コンプライアンス管理センター

複数地域テナントには、コンプライアンス管理センターとコンプライアンス管理センターの 1[つのMicrosoft 365センターがあります](https://compliance.microsoft.com/)。

## <a name="ediscovery"></a>電子情報開示

デフォルトでは、複数地域のテナントの eDiscovery Manager またはeDiscovery Administrator が、そのテナントの中心地でのみ電子情報の開示ができるようになります。 Office 365 全体管理者は、別のユーザーが電子情報開示を実行できるように電子情報開示マネージャーのアクセス許可を割り当てる必要があります。また、サテライトの場所として電子情報開示を実施する地域を指定するために該当するコンプライアンス セキュリティ フィルターで "Region" パラメーターを割り当てる必要があります。それ以外の場合は、サテライトの場所で電子情報開示は実施されません。 地域のコンプライアンス セキュリティ フィルター を構成するには、[Office 365 Multi-Geo eDiscovery の構成](multi-geo-ediscovery-configuration.md)を参照してください。

## <a name="exchange-mailboxes"></a>Exchange メールボックス

ユーザーの PDL が変更された場合、Exchange メールボックスが自動的に移動します。 新しいメールボックスが作成されたとき、ユーザーの PDL の値が設定されていない場合は、ユーザーの PDL または中心地にメールボックスがプロビジョニングされます。

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>情報保護 (IP) データ損失防止 (DLP) ポリシー

必要に応じて、テナント全体または該当するユーザーにポリシーの範囲を指定するセキュリティ & コンプライアンス センターで、OneDrive for Business、SharePoint、Exchange の IP DLP ポリシーを設定できます。 例: サテライト地域にいるユーザーのポリシーを選択する場合は、そのポリシーを特定の OneDrive に適用し、ユーザーの OneDrive URL を入力するように選択します。 DLP ポリシーを作成する際の一般的なガイダンスについては、[データ損失防止ポリシーの概要](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)を参照してください。

DLP ポリシーは、そのポリシーの適用性に基づいて各地域の場所に自動的に同期されます。

地域の場所のすべてのユーザーに対する Information Protection ポリシーとデータ損失防止ポリシーの実装は、UI で使用可能なオプションではありません。その代わりに、ポリシーの適用が可能なアカウントを選択するか、すべてのアカウントにグローバルにポリシーを適用する必要があります。

## <a name="microsoft-powerapps"></a>Microsoft PowerApps

サテライト地域に作成された PowerApps は、テナントの中心地にあるエンドポイントを使用します。 Microsoft PowerApps は、Multi-Geo サービスではありません。 

## <a name="power-automate"></a>Power Automate

サテライト地域に作成された Flow は、テナントのデフォルトの地域にあるエンドポイントを使用します。  Power Automateは、複数地域サービスではありません。 

## <a name="sharepoint-storage-quota"></a>SharePoint のストレージ クォータ

デフォルトでは、複数地域環境のすべての地域では、使用できるテナントの ストレージ クォータを共有します。  特定の地域に固有のクォータを割り当てることで、ストレージ クォータを管理することもできます。 詳細については、[複数地域環境における SharePoint ストレージ クォータ](sharepoint-multi-geo-storage-quota.md)を参照してください。

## <a name="sharing"></a>共有

管理者は、各地域のポリシーの共有を設定し管理できます。 各地域OneDriveのSharePointサイトとサイトは、対応する地域固有の共有設定のみを受け入れる必要があります。 (たとえば、中心地への[外部共有](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)は許可できますが、サテライト地域またはその逆にはできません) 共有設定は地域間の共有制限を構成できませんので注意してください。

## <a name="stream"></a>Stream

1:1 チャットで Stream にアップロードされたビデオは、アップロードするユーザーのOneDriveに保存されます。 会議の記録は、会議を記録OneDrive出席者のグループに保存されます。

## <a name="taxonomy"></a>分類

エンタープライズで管理されるメタデータ[](/sharepoint/managed-metadata)の統合分類は、地理的な場所全体でサポートされ、マスターは会社の一元的な場所でホストされます。 中心地からグローバル分類を管理し、サテライト地域の分類に地域固有の用語を追加することをお勧めします。 グローバル分類の用語は、サテライト地域に同期されます。

詳細と開発者向けガイダンスについては、[複数地域テナントにおけるメタデータの管理](/sharepoint/dev/solution-guidance/multigeo-managedmetadata)を参照してください。

## <a name="user-profile-application"></a>ユーザー プロファイル アプリケーション

各地域に[ユーザー プロフィール アプリケーション](/sharepoint/manage-user-profiles)があります。 各ユーザーのプロフィール情報は、ユーザーの地域でホストされており、その地域の管理者が利用できます。

カスタムのプロフィール プロパティがある場合は、すべての地域で同じプロフィール スキーマを使用して、すべての地域の場所または必要な場所のどちらかにカスタムのプロフィール プロパティを設定します。 プログラムを使用したユーザー プロフィール データの設定方法に関するガイダンスは、[ユーザー プロフィールの一括更新 API](/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)を参照してください。

詳細と開発者向けガイダンスについては、[複数地域テナントのユーザー プロフィールの操作](/sharepoint/dev/solution-guidance/multigeo-userprofileexperience)を参照してください。

## <a name="yammer"></a>Yammer

Yammerは、複数地域のワークロードではありません。 Yammerに格納Yammerスレッドは、テナントの中央の場所に配置されます。 Yammerは、ファイルストレージの変更を展開しています。この変更により、Yammerファイルが格納SharePoint。 Yammerに保存SharePointファイルは、SharePointグループに関連付Yammerされます。 SharePointグループ サイトは、[サイトとグループ] で説明されている PDL[ロジックSharePoint基づいて作成されます](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md#sharepoint-sites-and-groups)。
