---
title: アプリの脅威を修復する
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
description: アプリの脅威を修復する。
ms.openlocfilehash: 05106b9aaf790f92e8b69bfe14b393c45c934862
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/06/2021
ms.locfileid: "60193365"
---
# <a name="remediate-app-threats"></a>アプリの脅威を修復する

>*[セキュリティとコンプライアンスのための Microsoft 365 ライセンス ガイダンス](https://aka.ms/ComplianceSD)。*

Microsoft 365 コンプライアンス センターの [Microsoft アプリ ガバナンス] セクションの [**アラート**] ページを使用して、Microsoft 365 テナントに対するアプリの脅威を修復します。

![Microsoft 365 コンプライアンス センターの [アプリ ガバナンス アラートの概要] ページ。](..\media\manage-app-protection-governance\mapg-cc-alerts.png)

[**アラート**] ページには、既定で、アプリ ガバナンスによって生成された新しい脅威アラートと、アクティブなアプリ ポリシーによって生成されたポリシー ベースのアラートが一覧表示されます。 特定のアラートの詳細を表示するには、特定のアラートを選択します。これにより、追加のアラート情報と状態を変更する機能を含むアラート ウィンドウが開きます。

![Microsoft 365 コンプライアンス センターの [アプリ ガバナンス アラートの詳細] ページ。](..\media\manage-app-protection-governance\mapg-cc-alerts-alert.png)

このウィンドウから、次の追加情報を取得できます:

- [**説明**] フィールドのアラートに関する追加詳細。
- **ポリシー名** フィールドからアラートを生成したアプリ ポリシーの名前。 [**ポリシー表示**] を選択して、アラートを生成したアプリ ポリシーに移動することもできます。

**アクション** から自動修復用に構成したアプリ ポリシーの状態は **解決済み** になります。

次の手順を使用して、アプリ アラートを修復できます:

1. 調査: アラートの情報を調べ、その状態を **マーク進行中** に変更します。
2. 解決策: 調査後、必要に応じて、テナントでアプリ ポリシーの決定が変更されるか、アプリのサポートが続行されたら、その状態を [**解決済み**]に変更します。

アプリのアラート パターンに基づいて、適切なアプリ ポリシーを更新し、その **アクション** 設定を変更して、自動修復を実行できます。 これにより、アプリ ポリシーによって生成される今後のアラートを調査して手動で解決する必要がなくなります。 詳細については、「[アプリ ポリシーを管理する](app-governance-app-policies-manage.md)」を参照してください。
