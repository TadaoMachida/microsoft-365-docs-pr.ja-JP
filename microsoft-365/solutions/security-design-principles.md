---
title: Microsoft 365 Enterpriseリソース計画 - サイバーセキュリティ アーキテクチャ
description: Microsoft のサイバーセキュリティ アーキテクトである Kozeta Garrett の Microsoft Enterprise アーキテクチャにおけるセキュリティ上の課題を克服する方法について説明します。
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- M365solutions
ms.custom: seo-marvel-jun2020
f1.keywords: NOCSH
ms.openlocfilehash: c580b6529a3467a08befdb07c1b0b8d516208183
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2021
ms.locfileid: "61106205"
---
# <a name="security-hurdles-you-can-sail-overone-architects-viewpoint"></a>出航できるセキュリティ上のハードル -1 人のアーキテクトの視点

この記事では、Microsoft の Cybersecurity Architect [である Kozeta Garrett](https://www.linkedin.com/in/kozeta-garrett-53013a6/) 氏が、企業組織で直面する主なセキュリティ上の課題について説明し、これらの困難を乗り越える方法を推奨しています。

## <a name="about-the-author"></a>筆者について

![Kozeta Garrett 写真。](../media/solutions-architecture-center/kozeta-garrett-security.jpg)

クラウド セキュリティ アーキテクトとしての私の役割では、複数の組織と協力して、Microsoft 365と Azure に移行し、エンタープライズ セキュリティ ソリューションを開発し、ビジネス回復性のためのセキュリティ アーキテクチャと文化の変革を支援する顧客向けのセキュリティ アーキテクチャの設計と実装に重点を置いた戦略的および技術的なガイダンスを提供してきました。 私の経験には、インシデントの検出と対応、マルウェア分析、侵入テスト、IT セキュリティと防御体制の改善の推奨などがあります。 最新化の取り組みを含め、ビジネスの実現に向けたセキュリティにつながる変革を主導することに非常に情熱を注いでいます。

ここ数年でセキュリティの近代化の考え方を採用した組織が、COVID-19 の最近の状況にもかかわらず、リモートで安全な方法でリモート操作を継続できる優れた立場にあることを確認することは、最も満足のいくものです。 残念ながら、これらの状況は、この即時のニーズに対応できなかった一部の顧客のウェイクアップ 呼び出しとしても役立っています。 多くの組織は、このような非常に異常な状況で運用できるように、迅速に最新化し、蓄積された IT セキュリティ負債を廃止し、セキュリティ体制を一晩で改善する必要があることを認識しています。

良いニュースは、Microsoft が組織のセキュリティ体制を迅速に強化するのに役立つ優れたリソースをキュレーションしたことです。 これらのリソースに加えて、これらのハードルを乗り越えていけることを期待して、私が毎日お客様と遭遇した最大の課題を共有したいと思います。

現在、バージニア北部に住んでいます。この国の首都ワシントン DC の近くにいます。 ランニング、サイクリング、ウォーキング、水泳など、あらゆる形式の屋外アクティビティやエクササイズが大好きです。 これらに対抗するために、私は料理、料理、旅行と同じくらい楽しまれます。

## <a name="partner-with-the-security-team-from-the-start-of-cloud-adoption"></a>クラウド導入の開始からセキュリティ チームとパートナーを組む

まず、組織内のチームが最初から調整することがいかに重要であるかを強調できません。 セキュリティ チームは、クラウドの導入と設計の初期段階で重要なパートナーとして取り組む必要があります。 つまり、セキュリティ チームをクラウド導入に取り込み、ビジネスに追加された機能 (セキュリティで保護されたモバイル デバイス、フル機能アプリケーションからの優れたユーザー エクスペリエンス、限られた機能の電子メールや生産性アプリケーションを超えた企業データの価値の創出など) だけでなく、新旧のセキュリティ課題の解決に役立つストレージ、AI、コンピューティング分析機能を活用することを意味します。 セキュリティ チームは、人 (カルチャ)、プロセス (トレーニング)、成功するためのテクノロジなど、このシフトのすべての側面の管理に含める必要があります。 また、セキュリティ オペレーション センター (SOC) の近代化と継続的な改善に投資することを意味します。 セキュリティ戦略とビジネス戦略と環境の傾向を一致させて、デジタル変革が安全に行われるように協力します。 これが適切に行われると、組織は、ビジネス、IT、セキュリティの変更など、変更に迅速に適応する機能を開発します。

お客様が最もハードルを乗り越えているのは、運用チームと SOC チームの間に実際のパートナーシップがない場合です。 運用チームは、クラウドを採用するための厳しい期限を迫られ、義務付けられていますが、セキュリティ チームは、包括的なセキュリティ戦略を見直して計画するプロセスの早い段階に必ずしも含まれているわけではありません。 これには、さまざまなクラウド コンポーネントとコンポーネントをオンプレミスで統合する必要があります。 このパートナーシップの欠如は、サイロ内で機能し、特定のコンポーネントのコントロールを実装するように見えるさまざまなチームにさらに複雑さを与え、実装、トラブルシューティング、統合の複雑さが増します。

これらのハードルを乗り越えるお客様は、運用とガバナンスとセキュリティとリスク管理チームの間で良好なパートナーシップを築き、ハイブリッド クラウド ワークロードを保護するためのセキュリティ戦略と要件を見直します。 サイバーセキュリティ ガバナンス、リスク、コンプライアンスの要件に従って、データ保護とシステムとサービスの可用性という、最終的なセキュリティの目標と成果に焦点を当てています。 これらの組織は、運用とガバナンス チームと SOC の間で早期のパートナーシップを構築します。これは、セキュリティ設計アプローチに不可欠であり、投資の価値を最大限に高めます。

## <a name="build-a-modern-identity-based-security-perimeter"></a>最新の (ID ベースの) セキュリティ境界を構築する

次に、ゼロ トラスト アーキテクチャ アプローチを採用します。 これは、ID ベースの最新のセキュリティ境界の構築から始まります。 オンプレミスでもクラウドでも、すべてのアクセス試行が検証されるまで信頼されていないものとして扱われるセキュリティ アーキテクチャを設計します。"信頼せず、常に確認してください。 この設計アプローチにより、セキュリティと生産性が向上するだけでなく、ユーザーはあらゆる種類のデバイスでどこからでも作業できます。 Microsoft 365に含まれる高度なクラウド コントロールは、ユーザーのリスク レベルに基づいて貴重なリソースへのアクセスを制御しながら、ユーザーの ID を保護するのに役立ちます。

推奨される構成については、「 [ID とデバイスのアクセス構成」を](../security/office-365-security/microsoft-365-policies-configurations.md)参照してください。

## <a name="transition-security-controls-to-the-cloud"></a>セキュリティ制御をクラウドに移行する

多くのセキュリティ チームは、"ネットワーク境界セキュリティ" を維持し、オンプレミスのセキュリティ ツールと制御をクラウド ソリューションに "強制" しようとするなど、すべてのオンプレミスの世界向けに構築された従来のセキュリティのベスト プラクティスを引き続き使用しています。 このようなコントロールはクラウド向けに設計されておらず、効果がなく、最新のクラウド機能の導入を妨げている。 ネットワーク境界セキュリティ アプローチで機能するプロセスとツールは、非効率的で、クラウド機能を妨げるものであり、最新の自動化されたセキュリティ機能を利用することはできません。

このハードルを乗り越えるには、防御戦略をクラウドマネージド保護、自動調査と修復、自動ペンテスト、Defender for Office 365、インシデント分析に移行します。 最新のデバイス管理ソリューションを使用しているお客様は、すべてのデバイス (スマートフォン、パーソナル コンピューター、ノート PC、タブレットなど) 全体で自動化された管理、標準化された修正プログラム、ウイルス対策、ポリシーの適用、およびアプリケーション保護を実装しています。 これにより、VPN、Microsoft System Center Configuration Manager (SCCM)、Active Directory グループ ポリシーが不要になります。 条件付きアクセス ポリシーと組み合わせることで、強力な制御と可視性が提供され、ユーザーの操作元に関係なくリソースへのアクセスが効率化されます。

## <a name="strive-for-best-together-security-tools"></a>"ベスト な一緒に" セキュリティ ツールを目指す

お客様がつまずくもう 1 つのハードルは、セキュリティ ツールに対して "最高の種類" アプローチを取ることです。 新しいセキュリティ ニーズに対処するために "最適な" ポイント ソリューションを継続的に重ね合わせて、エンタープライズ セキュリティを分解します。 最善の意図を持っていても、ほとんどの環境のツールは、コストがかかりすぎて複雑になるため、統合されません。 これにより、チームが処理できるアラートよりもトリアージするアラートが多くなるので、可視性のギャップが生じます。 新しいツールで SecOps チームを再トレーニングすることも、絶え間ない課題になります。

"単純な方が優れています" アプローチは、セキュリティにも適しています。 "ベスト オブ ブリード" ツールを使う代わりに、既定で連携するツールと共に "ベスト な一緒に" 戦略を採用することで、このハードルを乗り越えて進みます。 Microsoft セキュリティ機能は、アプリケーション、ユーザー、クラウドにまたがる統合された脅威保護を使用して組織全体を保護します。 統合により、組織は侵入時に攻撃者を封じ込め、攻撃を迅速に修復することで、より回復性を高め、リスクを軽減できます。

## <a name="balance-security-with-functionality"></a>セキュリティと機能のバランスを取る

私は長いサイバーセキュリティの背景と経験から生まれるので、最初は最も安全な構成から始め、組織が運用とセキュリティのニーズに基づいてセキュリティ構成を緩和できるようにする傾向があります。 ただし、これは、機能の喪失とユーザー エクスペリエンスの低下という大きな代償を伴う可能性があります。 多くの組織が学習したように、セキュリティがユーザーにとって困難すぎる場合は、アンマネージド クラウド サービスの使用を含め、ユーザーを回避する方法が見つかります。 受け入れるのが難しいのと同じように、微妙な機能とセキュリティのバランスを実現する必要があることに気付きました。

ユーザーが仕事を遂行するために必要な操作を行うことを認識している組織は、"シャドウ IT の戦い" は戦う価値がないことを認識します。 シャドウ IT と、承認されていない SaaS アプリケーションを仕事に使用する場合、IT 従業員が最大の違反者であることを認識しています。 彼らは戦略をシフトし、(抑制ではなく) 使用を奨励し、それが生み出すリスクの軽減に焦点を当てています。 これらの組織のセキュリティ チームは、すべてがブロックされ、ログに記録され、リバース プロキシまたは VPN を介して送信されることを主張しません。 代わりに、これらのセキュリティ チームは、貴重な機密データが間違った関係者や悪意のあるアプリに公開されないようにするための取り組みを 2 倍に減らしています。 データの整合性を保護するために機能します。 暗号化、セキュリティで保護された多要素認証、自動リスクとコンプライアンス、クラウド アクセス セキュリティ ブローカー (CASB) 機能など、より高度なクラウド情報保護機能を最大限に活用しながら、複数のプラットフォーム間で保護された共有を許可し、奨励しています。 彼らは影の IT を刺激的な創造性、生産性、コラボレーションに変えています。これにより、ビジネスは競争力を維持できます。

## <a name="adopt-a-methodical-approach"></a>方法的なアプローチを採用する

業界に関係なく、さまざまな組織でクラウド セキュリティを実装する際に経験した課題のほとんどは、よく似ています。 まず、特定の機能と機能に関する優れたドキュメントは多数ありますが、組織レベルでは、それらに適用されるもの、セキュリティ機能が重複する場所、および機能を統合する方法に関する混乱のレベルがあります。 また、どのセキュリティ機能が事前に構成され、組織による構成が必要であるかについても、ある程度の不確かさがあります。 さらに、SOC チームは残念ながら、組織が既に行っている急速なクラウド導入とデジタル変革に備えるために必要な、完全な露出、トレーニング、予算割り当てを行っていません。

これらのハードルをクリアするために、Microsoft では、セキュリティ戦略と実装に対する方法論的なアプローチを取るために設計されたいくつかのリソースをキュレーションしました。

|関連情報   |詳細情報  |
|---------|---------|
|[自宅での作業をサポートするセキュリティ チームの主なタスク](../security/top-security-tasks-for-remote-work.md)      | ほとんどの在宅勤務者を突然サポートしている場合、この記事はセキュリティを迅速に強化するのに役立ちます。 これには、ライセンス プランに基づいて推奨される最も重要なタスクが含まれます。    |
|[ビジネス意思決定者向けのセキュリティのMicrosoft 365](../security/Microsoft-365-security-for-bdm.md)    | より包括的な計画を立てる時間がある場合、この記事には、攻撃面によって優先順位付けされたMicrosoft 365にまたがる推奨事項が含まれています。 ライセンスと領域 (ID、脅威保護、監視など) の並べ替えに使用できるスプレッドシートも付属しています。  |
|[Microsoft セキュリティ アーキテクチャに関する推奨事項](/security/compass/compass)    | セキュリティ アーキテクトの場合は、ID、ネットワーク、セキュリティ操作など、規範別に整理されたセキュリティに関する推奨事項を確認してください。   |
|[Microsoft Security Operations の推奨事項](/security/compass/security-operations-videos-and-decks)|Security Operations Center (SOC) のセットアップと実行に関する Microsoft の推奨事項について説明します |
|[最高情報セキュリティ責任者 (CISO) ワークショップ トレーニング](/security/ciso-workshop/ciso-workshop)   | クラウド セキュリティを初めて使用する場合は、この一連のビデオをお見逃しなく。        |
|[docs.security.com/security](/security/)    | セキュリティ戦略とアーキテクチャに関する Microsoft 全体の技術ガイダンス。        |
| | |

これらのリソースはすべて、出発点として使用され、組織のニーズに合わせて調整されるように設計されています。
