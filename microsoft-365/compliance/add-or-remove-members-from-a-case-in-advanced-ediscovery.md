---
title: ケースからメンバーを追加または削除する
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
description: 電子情報開示 (Premium) ケースを管理するときにケースにアクセスできるメンバーを追加または削除する方法について説明します。
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 0b3ed53ee897e88d70a7b1322999e5b81de8ed81
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627715"
---
# <a name="add-or-remove-members-from-a-case"></a>ケースからメンバーを追加または削除する

メンバーを追加または削除して、ケースにアクセスできるユーザーを管理できます。 ただし、メンバーが電子情報開示 (Premium) ケースにアクセスし、その場合はタスクを実行する前に、Microsoft Purview コンプライアンス ポータルの **[アクセス許可**] ページで電子情報開示マネージャーの役割グループにユーザーを追加する必要があります。 詳細については、「[電子情報開示のアクセス許可を割り当てる](./assign-ediscovery-permissions.md)」を参照してください。電子情報開示のアクセス許可を割り当てる」を参照してください。

1. **eDiscovery (Premium)** ページで、メンバーを追加するケースに移動します。

2. [**設定**] タブをクリックし、[**アクセス & アクセス許可**] タイルで [**選択**] をクリックします。

3. [**メンバーの管理**] で [**追加**] をクリックして、ケースにメンバーを追加します。 [役割グループの管理] で [追加] をクリックして、ケースに **役割グループ** を **追加** することもできます。

4. ケースのメンバーとして追加できるユーザーまたは役割グループのリストで、追加するユーザーまたは役割グループの名前の横にあるチェック ボックスをオンにします。

   > [!NOTE]
   > ケースに役割グループを追加する場合は、自分がメンバーである役割グループのみを追加できます。

5. ケースのメンバーとして追加するユーザーまたは役割グループを選択したら、[ **追加**] をクリックします。

6. [**このケースを管理**] で、[**保存**] をクリックして、ケース メンバーの新しいリストを保存します。

> [!IMPORTANT]
> ケースのメンバーとして追加した役割グループにロールが追加または削除された場合、ロール グループはケースのメンバー (またはロール グループがメンバーである場合) として自動的に削除されます。 その理由は、ケースのメンバーに追加のアクセス許可を誤って提供しないように組織を保護するためです。 同様に、役割グループが削除された場合は、そのロール グループがメンバーであったすべてのケースから削除されます。 詳細については、「[電子情報開示のアクセス許可を割り当てる](assign-ediscovery-permissions.md#adding-role-groups-as-members-of-ediscovery-cases)」を参照してください。電子情報開示のアクセス許可を割り当てる」を参照してください。

## <a name="removing-members-from-a-case"></a>ケースからメンバーを削除する

ケースからメンバーを削除できるのは [、電子情報開示管理者](assign-ediscovery-permissions.md) のみです。 電子情報開示マネージャーの役割グループに割り当てられている場合、またはケースを最初に作成した場合でも、電子情報開示管理者でない限り、自分または他のメンバーをケースから削除することはできません。 自分や他のメンバーをケースから削除するには、組織内の電子情報開示管理者に問い合わせてください。
