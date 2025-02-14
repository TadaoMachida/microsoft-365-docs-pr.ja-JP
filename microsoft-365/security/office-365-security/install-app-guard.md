---
title: 管理者向け Application Guard for Office
keywords: application guard, 保護, 分離, 分離されたコンテナー, ハードウェアの分離
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
description: 最新のハードウェア ベースの分離を取得します。 悪用や悪意のあるリンクなどの現在および新しい攻撃が従業員の生産性とエンタープライズ セキュリティを中断するのを防ぎます。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9a7e820a4aedb4338111ef0fc76a35de480ea1f8
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530928"
---
# <a name="application-guard-for-office-for-admins"></a>管理者向け Application Guard for Office

**適用対象:** Word、Excel、PowerPoint for Microsoft 365 Apps、Windows 10 Enterprise、Windows 11 Enterprise

Office のMicrosoft Defender Application Guard (Application Guard for Office) は、信頼されていないファイルが信頼できるリソースにアクセスするのを防ぎ、新しい攻撃や新しい攻撃からエンタープライズを安全に保つのに役立ちます。 この記事では、Application Guard for Office のプレビュー用にデバイスを設定する手順について説明します。 デバイスで Application Guard for Office を有効にするシステム要件とインストール手順に関する情報を提供します。

## <a name="prerequisites"></a>前提条件

### <a name="minimum-hardware-requirements"></a>ハードウェアの最小要件

* **CPU**: 64 ビット、4 コア (物理または仮想)、仮想化拡張機能 (Intel VT-x OR AMD-V)、Core i5 相当以上を推奨
* **物理メモリ**: 8 GB RAM
* **ハード ディスク**: システム ドライブ上の 10 GB の空き領域 (SSD を推奨)

### <a name="minimum-software-requirements"></a>最小ソフトウェア要件

* **Windows**: Windows 10 Enterprise エディション、クライアント ビルド バージョン 2004 (20H1) ビルド 19041 以降。 すべてのバージョンのWindows 11がサポートされています。
* **Office**: ビルド 16.0.13530.10000 以降のMicrosoft 365 Apps。 現在のチャネルと月次エンタープライズ チャネルのインストールの場合、これはバージョン 2011 と等しくなります。 Semi-Annual エンタープライズ チャネルとSemi-Annual エンタープライズ チャネル (プレビュー) の場合、最小バージョンは 2108 以降です。 32 ビットバージョンと 64 ビット バージョンの両方がサポートされています。
* **更新プログラム パッケージ**: 累積的な毎月のセキュリティ更新プログラム [KB4571756](https://support.microsoft.com/help/4571756/windows-10-update-KB4571756) Windows 10

システム要件の詳細については、「[Microsoft Defender Application Guardのシステム要件」を](/windows/security/threat-protection/microsoft-defender-application-guard/reqs-md-app-guard)参照してください。 また、仮想化テクノロジを有効にする方法については、コンピューターの製造元のガイドを参照してください。
Microsoft 365 Apps更新チャネルの詳細については、「[Microsoft 365 Appsの更新チャネルの概要」を](/deployoffice/overview-update-channels)参照してください。

### <a name="licensing-requirements"></a>ライセンスの要件

* Microsoft 365 E5 Security
* 教職員向けのMicrosoft 365 A5
* 学生向けのMicrosoft 365 A5

> [!NOTE]
> 共有コンピューターのライセンス認証またはデバイス ベースのライセンスを持つMicrosoft 365 Apps for enterpriseは、Application Guard for Office にアクセスできません。
>
> Safe Documents ライセンス プランでは、Application Guard for Office へのアクセスが許可されます。 詳細については、「[Microsoft 365 E5/A5 の安全なドキュメント](/microsoft-365/security/office-365-security/safe-docs)」を参照してください。

## <a name="deploy-application-guard-for-office"></a>Office 用 Application Guard を展開する

### <a name="enable-application-guard-for-office"></a>Office 用 Application Guard を有効にする

1. **累積的な毎月のセキュリティ更新プログラム KB4571756 Windows 10ダウンロードして** インストールします。

2. [Windows 機能] **で [Microsoft Defender Application Guard**] を選択し、[OK] を選択 **します**。 Application Guard 機能を有効にすると、システムの再起動が求められます。 今すぐ再起動するか、手順 3 の後に再起動するかを選択できます。

   :::image type="content" source="../../media/ag03-deploy.png" alt-text="AG を示す [Windows 機能] ダイアログ ボックス" lightbox="../../media/ag03-deploy.png":::

   この機能は、次の PowerShell コマンドを管理者として実行して有効にすることもできます。

   ```powershell
   Enable-WindowsOptionalFeature -online -FeatureName Windows-Defender-ApplicationGuard
   ```

3. **コンピューター構成\\管理テンプレート\\Windows コンポーネント\\** のグループ ポリシーである **マネージド モード** でMicrosoft Defender Application Guardを検索しますMicrosoft Defender Application Guard。 [オプション] の値を **2** または **3** に設定し、[OK] または [**適用****] を** 選択して、このポリシーを有効にします。

   :::image type="content" source="../../media/ag04-deploy.png" alt-text="マネージド モードで AG を有効にするオプション" lightbox="../../media/ag04-deploy.png":::

   代わりに、対応する CSP ポリシーを設定できます。

   > OMA-URI: **./Device/Vendor/MSFT/WindowsDefenderApplicationGuard/Settings/AllowWindowsDefenderApplicationGuard** <br> データ型: **整数** <br> 値: **2**

4. システムを再起動します。

### <a name="set-diagnostics--feedback-to-send-full-data"></a>診断&フィードバックを設定して完全なデータを送信する

> [!NOTE]
> ただし、これは必須ではありませんが、省略可能な診断データを構成すると、報告された問題の診断に役立ちます。

この手順により、問題の特定と修正に必要なデータが Microsoft に届きます。 Windows デバイスで診断を有効にするには、次の手順に従います。

1. [スタート] メニューから **[設定] を** 開きます。

   :::image type="content" source="../../media/ag05-diagnostic.png" alt-text="[スタート] メニュー" lightbox="../../media/ag05-diagnostic.png":::

2. **Windows 設定** で、[**プライバシー**] を選択します。

   :::image type="content" source="../../media/ag06-diagnostic.png" alt-text="Windows の [設定] メニュー" lightbox="../../media/ag06-diagnostic.png":::

3. [プライバシー] で、[ **診断&フィードバック** ] を選択し、[ **オプションの診断データ**] を選択します。

   :::image type="content" source="../../media/ag07a-diagnostic.png" alt-text="[診断とフィードバック] メニュー" lightbox="../../media/ag07a-diagnostic.png":::

Windows 診断設定の構成の詳細については、「 [組織内の Windows 診断データの構成」](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management)を参照してください。

### <a name="confirm-that-application-guard-for-office-is-enabled-and-working"></a>Application Guard for Office が有効で動作していることを確認する

Application Guard for Office が有効になっていることを確認する前に、ポリシーが展開されているデバイスで Word、Excel、または PowerPoint を起動します。 Office がアクティブ化されていることを確認します。 最初に Office 製品をアクティブ化するために、仕事用 ID を使用することが必要になる場合があります。

Application Guard for Office が有効になっていることを確認するには、Word、Excel、または PowerPoint を起動し、信頼されていないドキュメントを開きます。 たとえば、インターネットからダウンロードされたドキュメントや、組織外のユーザーからの電子メールの添付ファイルを開くことができます。

信頼されていないファイルを初めて開くと、次の例のような Office スプラッシュ画面が表示されることがあります。 Application Guard for Office がアクティブ化され、ファイルが開かれている間、しばらくの間表示されることがあります。 信頼されていないファイルの後続の開き方は高速である必要があります。

:::image type="content" source="../../media/ag08-confirm.png" alt-text="Office アプリスプラッシュ ページ" lightbox="../../media/ag08-confirm.png":::

ファイルを開くと、ファイルが Application Guard for Office 内で開かれたことを示す視覚的なインジケーターがいくつか表示されます。

* リボンの吹き出し

  :::image type="content" source="../../media/ag09-confirm.png" alt-text="小さな App Guard ノートを示すドキュメント ファイル" lightbox="../../media/ag09-confirm.png":::

* タスク バーにシールドが表示されたアプリケーション アイコン

  ![タスク バーのアイコン。](../../media/ag12-limitations.png)

## <a name="configure-application-guard-for-office"></a>Office 用 Application Guard を構成する

Office では、Application Guard for Office の機能を構成できるように、次のポリシーがサポートされています。 これらのポリシーは、グループ ポリシーまたは [Office クラウド ポリシー サービス](/DeployOffice/overview-office-cloud-policy-service)を使用して構成できます。

> [!NOTE]
> これらのポリシーを構成すると、Application Guard for Office で開いたファイルの一部の機能を無効にすることができます。

|ポリシー|説明|
|---|---|
|Application Guard for Office を使用しない|このポリシーを有効にすると、Office 用 Application Guard の代わりに、Word、Excel、および PowerPoint で保護されたビュー分離コンテナーが強制的に使用されます。 このポリシーを使用すると、Microsoft Edge で Application Guard for Office を有効にしたままにしておく際に問題が発生した場合に、Application Guard for Office を一時的に無効にすることができます。|
|Office コンテナーの事前作成用の Application Guard を構成する|このポリシーは、信頼されていないファイルを分離するための Application Guard for Office コンテナーが、実行時のパフォーマンスを向上させるために事前に作成されているかどうかを決定します。 この設定を有効にした場合は、コンテナーの事前作成を続行する日数を指定するか、Office 組み込みのヒューリスティックでコンテナーを事前に作成することができます。
|Application Guard for Office で開いた Office ドキュメントのコピー/貼り付けを許可しない|このポリシーを有効にすると、Application Guard for Office で開かれたドキュメントから、その外部で開かれたドキュメントにコンテンツをコピーして貼り付けできなくなります。|
|Application Guard for Office でハードウェア アクセラレーションを無効にする|このポリシーは、Application Guard for Office でハードウェア アクセラレーションを使用してグラフィックスをレンダリングするかどうかを制御します。 この設定を有効にすると、Application Guard for Office はソフトウェア ベース (CPU) レンダリングを使用し、サードパーティのグラフィックス ドライバーを読み込んだり、接続されたグラフィックス ハードウェアと対話したりすることはありません。
|Application Guard for Office でサポートされていないファイルの種類の保護を無効にする|このポリシーは、Application Guard for Office でサポートされていないファイルの種類の開き方をブロックするかどうか、または保護されたビューへのリダイレクトを有効にするかどうかを制御します。
|Application Guard for Office で開いたドキュメントのカメラとマイクへのアクセスをオフにする|このポリシーを有効にすると、Application Guard for Office 内のカメラとマイクへの Office アクセスが削除されます。|
|Application Guard for Office で開いたドキュメントからの印刷を制限する|このポリシーを有効にすると、ユーザーが印刷できるプリンターが Application Guard for Office で開かれたファイルに制限されます。 たとえば、このポリシーを使用して、PDF への印刷のみをユーザーに制限できます。|
|ユーザーがファイルで Application Guard for Office 保護を削除できないようにする|このポリシーを有効にすると、(Office アプリケーション エクスペリエンス内で) Application Guard for Office 保護を無効にしたり、Application Guard for Office の外部でファイルを開いたりするためのオプションが削除されます。 <p> **メモ：** ユーザーは引き続き、このポリシーをバイパスするには、ファイルから手動で Web のマーク プロパティを削除するか、ドキュメントを信頼できる場所に移動します。|

> [!NOTE]
> 次のポリシーでは、ユーザーがサインアウトし、Windows にもう一度サインインして有効にする必要があります。
>
> * Application Guard for Office で開いたドキュメントのコピー/貼り付けを無効にする
> * Application Guard for Office で開いたドキュメントの印刷を制限する
> * Application Guard for Office で開いたドキュメントへのカメラとマイクのアクセスをオフにする

## <a name="submit-feedback"></a>フィードバックの送信

### <a name="submit-feedback-via-feedback-hub"></a>フィードバック ハブ経由でフィードバックを送信する

Application Guard for Office の起動時に問題が発生した場合は、フィードバック ハブからフィードバックを送信することをお勧めします。

1. **Feedback Hub アプリ** を開き、サインインします。

2. Application Guard の起動時にエラー ダイアログが表示される場合は、エラー ダイアログで **[Microsoft に報告** ] を選択して、新しいフィードバック送信を開始します。 それ以外の場合は<https://aka.ms/mdagoffice-fb>、Application Guard の適切なカテゴリを選択し、右上の [**新しいフィードバックの追加] を選択+&nbsp;** します。

3. **[フィードバックの集計**] ボックスに、まだ入力されていない場合は、概要を入力します。

4. 発生した問題の詳細な説明と、[ **詳細の説明** ] ボックスに実行した手順を入力し、[ **次へ**] を選択します。

5. **[問題**] の横にあるバブルを選択します。 選択したカテゴリが **セキュリティとプライバシー \> のMicrosoft Defender Application Guard – Office** であることを確認し、[**次へ**] を選択します。

6. [ **新しいフィードバック**]、[ **次へ**] の順に選択します。

7. 問題に関するトレースを収集します。

   1. [ **問題の再作成] タイルを** 展開します。

   2. Application Guard の実行中に発生している問題が発生した場合は、Application Guard インスタンスを開きます。 インスタンスを開くと、Application Guard コンテナー内から追加のトレースを収集できます。

   3. [ **記録の開始]** を選択し、タイルの回転が停止するのを待ち、[ *記録の停止]* と表示されます。

   4. Application Guard に関する問題を完全に再現します。 再現には、Application Guard インスタンスを起動して失敗するまで待つことや、実行中の Application Guard インスタンスで問題を再現することが含まれる場合があります。

   5. [ **記録の停止** ] タイルを選択します。

   6. 実行中の Application Guard インスタンスは、送信後数分間でも開いたままにしておき、コンテナー診断を収集することもできます。

8. 問題に関連するスクリーンショットまたはファイルを添付します。

9. **[送信]** を選択します。

### <a name="submit-feedback-via-office-customer-voice"></a>Office カスタマー ボイス経由でフィードバックを送信する

Office ドキュメントを Application Guard で開いたときに問題が発生した場合は、Office 内からフィードバックを送信することもできます。 フィードバックを送信するには、 [Office Insider の手引き](https://insider.office.com/handbook) を参照してください。

## <a name="integration-with-microsoft-defender-for-endpoint-and-microsoft-defender-for-office-365"></a>Microsoft Defender for EndpointとMicrosoft Defender for Office 365との統合

Application Guard for Office はMicrosoft Defender for Endpointと統合され、分離された環境で発生する悪意のあるアクティビティの監視とアラートを提供します。

[Microsoft E365 E5 の安全なドキュメント](/microsoft-365/security/office-365-security/safe-docs)は、Microsoft Defender for Endpointを使用して Application Guard for Office で開かれたドキュメントをスキャンする機能です。 追加の保護レイヤーでは、スキャンの結果が決定されるまで、ユーザーは Application Guard for Office から離れることはできません。

Microsoft Defender for Endpointは、エンタープライズ ネットワークが高度な脅威を防止、検出、調査、および対応できるように設計されたセキュリティ プラットフォームです。 このプラットフォームの詳細については、「[Microsoft Defender for Endpoint](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp)」を参照してください。 このプラットフォームへのデバイスのオンボードの詳細については、「デバイスを[Microsoft Defender for Endpoint サービスにオンボードする](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure)」を参照してください。

Defender for Endpoint を使用するようにMicrosoft Defender for Office 365を構成することもできます。 詳細については、「[Defender for Office 365とMicrosoft Defender for Endpointの統合](integrate-office-365-ti-with-mde.md)」を参照してください。

## <a name="limitations-and-considerations"></a>制限事項と考慮事項

* Application Guard for Office は、信頼できる企業リソース、イントラネット、ユーザーの ID、コンピューター上の任意のファイルにアクセスできないように、信頼されていないドキュメントを分離する保護モードです。 その結果、ユーザーがディスク上のローカル ファイルから画像を挿入するなど、そのようなアクセスに依存する機能にアクセスしようとすると、アクセスが失敗し、次の例のようなプロンプトが生成されます。 信頼されていないドキュメントが信頼できるリソースにアクセスできるようにするには、ユーザーはドキュメントから Application Guard 保護を削除する必要があります。

  :::image type="content" source="../../media/ag09-confirm.png" alt-text="安全メッセージと機能の状態を示すダイアログ ボックス" lightbox="../../media/ag09-confirm.png":::

  > [!NOTE]
  > ユーザーが保護を削除するのは、ファイルとそのソースを信頼している場合、またはどこから来たのかをユーザーに知らしてください。

* 信頼されていないドキュメントが信頼できる場所に格納されている場合、その場所からの信頼はドキュメントによって継承されます。 通常、組織のクラウド ストレージは信頼できる場所として識別されます。

* マクロや ActiveX コントロールなどのドキュメント内のアクティブなコンテンツは、Application Guard for Office では無効になっています。 ユーザーは、アクティブなコンテンツを有効にするために Application Guard 保護を削除する必要があります。

* ネットワーク共有からの信頼されていないファイル、または別の組織の OneDrive、OneDrive for Business、または SharePoint Online から共有されたファイルは、Application Guard で読み取り専用として開きます。 ユーザーは、このようなファイルのローカル コピーを保存してコンテナー内で作業を続けるか、元のファイルを直接操作するための保護を削除できます。

* Information Rights Management (IRM) によって保護されているファイルは、既定でブロックされます。 ユーザーがこのようなファイルを保護ビューで開く場合、管理者は組織のサポートされていないファイルの種類に対してポリシー設定を構成する必要があります。

* Application Guard for Office の Office アプリケーションに対するカスタマイズは、ユーザーがサインアウトして再びサインインした後、またはデバイスの再起動後も保持されません。

* UiA フレームワークを使用するアクセシビリティ ツールのみが、Application Guard for Office で開いたファイルに対してアクセス可能なエクスペリエンスを提供できます。

* インストール後に Application Guard を初めて起動するには、ネットワーク接続が必要です。 Application Guard がライセンスを検証するには、接続が必要です。

* ドキュメントの情報セクションで、[ *最終変更者* ] プロパティに **WDAGUtilityAccount** がユーザーとして表示される場合があります。 WDAGUtilityAccount は、Application Guard で構成された匿名ユーザーです。 デスクトップ ユーザーの ID は Application Guard コンテナー内で共有されません。

## <a name="performance-optimizations-for-application-guard-for-office"></a>Application Guard for Office のパフォーマンスの最適化

このセクションでは、Application Guard for Office で使用されるパフォーマンスの最適化の概要について説明します。 この情報は、管理者が Application Guard が有効になっている場合に、Office またはシステム全体のパフォーマンスに関連するユーザーからのレポートを診断するのに役立ちます。

Application Guard では、仮想化されたコンテナーを使用して、信頼されていないドキュメントをシステムから分離します。 コンテナーを作成し、Office ドキュメントを開くために Application Guard コンテナーを設定するプロセスには、ユーザーが信頼されていないドキュメントを開くときにユーザー エクスペリエンスに悪影響を与える可能性があるパフォーマンスオーバーヘッドがあります。

Application Guard では、予想されるファイルの開き方をユーザーに提供するために、システムで次のヒューリスティックが満たされたときに、ロジックを使用してコンテナーを事前に作成します。ユーザーは、過去 28 日間に Protected View または Application Guard でファイルを開いています。

このヒューリスティックが満たされると、Office は Windows にサインインした後、ユーザーの Application Guard コンテナーを事前に作成します。 この事前作成操作の進行中は、システムのパフォーマンスが低下することがありますが、操作が完了するとすぐに効果が解決します。

> [!NOTE]
> ヒューリスティックでコンテナーを事前に作成するために必要なヒントは、ユーザーがコンテナーを使用する際に Office アプリケーションによって生成されます。 ユーザーが Application Guard が有効になっている新しいシステムに Office をインストールした場合、ユーザーが初めて信頼されていないドキュメントをシステムで開くまで、Office はコンテナーを事前に作成しません。 ユーザーは、この最初のファイルが Application Guard で開くのに時間がかかることを確認します。

## <a name="known-issues"></a>既知の問題

* Web リンク (`http` または `https`Web リンク) を選択しても、ブラウザーは開きません。
* コピー貼り付け保護ポリシーの既定の設定は、テキストへのクリップボードアクセスのみを有効にすることです。
* サポートされていないファイルの種類の保護ポリシーの既定の設定は、暗号化されているか、Information Rights Management (IRM) が設定されている信頼されていないサポートされていないファイルの種類を開くのをブロックすることです。 これには、Microsoft Purview 情報保護の秘密度ラベルを使用して暗号化されるファイルが含まれます。
* 現時点では、CSV ファイルと HTML ファイルはサポートされていません。
* 現在、Office 用 Application Guard は NTFS 圧縮ボリュームでは機能しません。 "ERROR_VIRTUAL_DISK_LIMITATION" というエラーが表示される場合は、ボリュームの圧縮解除を試してください。
* .NET に更新すると、Application Guard でファイルを開けなくなります。 回避策として、ユーザーは、このエラーが発生したときにデバイスを再起動できます。 [Windows Defender Application GuardまたはWindows サンドボックスを開くときにエラー メッセージが表示される場合の](https://support.microsoft.com/help/4575917/receiving-an-error-message-when-attempting-to-open-windows-defender-ap)問題の詳細を確認します。
* 詳細については、「[よく寄せられる質問 - Microsoft Defender Application Guard」を参照してください。](/windows/security/threat-protection/microsoft-defender-application-guard/faq-md-app-guard)
