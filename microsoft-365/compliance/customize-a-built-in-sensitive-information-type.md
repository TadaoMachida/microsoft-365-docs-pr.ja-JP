---
title: 組み込みの機密情報の種類をカスタマイズする
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 07/08/2019
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: 組織のニーズを満たすルールを使用できるようにするカスタム機密情報タイプを作成する方法について説明します。
ms.openlocfilehash: 14fb645a4b7f58f609995bc71edae24090c83cc7
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630987"
---
# <a name="customize-a-built-in-sensitive-information-type"></a>組み込みの機密情報の種類をカスタマイズする

コンテンツ内の機密情報を探すときには、*ルール* と呼ばれるものの中にその情報を記述する必要があります。 Microsoft Purview データ損失防止 (DLP) には、すぐに利用できる最も一般的な機密情報の種類のルールが含まれています。 これらのルールを使用するには、それらをポリシーの中に組み込む必要があります。 これらの組み込みのルールを組織の特定のニーズに合わせて調整する必要がある場合は、カスタムの機密情報の種類を作成することができます。 このトピックでは、クレジット カード情報である可能性のある情報をより幅広い範囲で検出できるように、既存のルール コレクションが入っている XML ファイルをカスタマイズする方法について説明します。

この例は、これ以外の組み込みの機密情報の種類に適用することもできます。機密情報の既定の種類と XML 定義のリストについては、「[機密情報の種類のエンティティ定義](sensitive-information-type-entity-definitions.md)」のトピックを参照してください。

## <a name="export-the-xml-file-of-the-current-rules"></a>現在のルールの XML ファイルをエクスポートする

XML をエクスポートするには、[セキュリティ & コンプライアンス PowerShell に接続する](/powershell/exchange/connect-to-scc-powershell) が必要です。

1. PowerShell で次のように入力すると、組織のルールが画面上に表示されます。まだ独自のルールを作成していない場合は、"Microsoft Rule Package" というラベルの付いた既定の組み込みルールだけが表示されます。

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

2. 次のように入力して、組織のルールを変数に格納します。 変数に何かを格納すると、後ほどリモート PowerShell コマンドで使用するフォーマットの中で簡単に利用できます。

   ```powershell
   $ruleCollections = Get-DlpSensitiveInformationTypeRulePackage
   ```

3. 以下のように入力して、すべてのデータを含むフォーマットされた XML ファイルを作成します。

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\custompath\exportedRules.xml', $ruleCollections.SerializedClassificationRuleCollection)
   ```

   > [!IMPORTANT]
   > ルール パックが実際に格納されている場所を指定してください。`C:\custompath\` はプレースホルダーです。

## <a name="find-the-rule-that-you-want-to-modify-in-the-xml"></a>変更する必要のあるルールを XML の中から見つける

上記のコマンドレットによって、既定のルールを含む *ルール コレクション* 全体がエクスポートされます。この中から、修正しようとしているクレジット カード番号のルールを探す必要があります。

1. 前のセクションでエクスポートした XML ファイルをテキスト エディターで開きます。

2. 下へスクロールして `<Rules>` タグに移動します。ここが、DLP ルールを含むセクションの先頭です。(この XML ファイルにはルール コレクション全体の情報が含まれているため、ルールの部分を表示するには、先頭にある他の情報をスキップする必要があります。)

3. クレジット カード番号のルール定義を見つけるため、*Func_credit_card* を探します。XML ではルール名にスペースを含めることができないため、スペースは通常、アンダースコアで置き換えられます。また、ルール名が省略形になることもあります。たとえば、米国の (Social Security number) のルールは、"_SSN_" という省略形になります。クレジット カード番号のルールの XML は、次のコード サンプルのようなものです。

   ```xml
   <Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085"
          patternsProximity="300" recommendedConfidence="85">
         <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_credit_card" />
           <Any minMatches="1">
             <Match idRef="Keyword_cc_verification" />
             <Match idRef="Keyword_cc_name" />
             <Match idRef="Func_expiration_date" />
           </Any>
         </Pattern>
       </Entity>
   ```

XML 内でクレジット カード番号のルール定義が見つかったら、ニーズに合わせてルールの XML をカスタマイズします。(XML 定義の詳細については、このトピックの最後にある「[用語集](#term-glossary)」を参照してください。)

## <a name="modify-the-xml-and-create-a-new-sensitive-information-type"></a>XML を変更し、新しい機密情報の種類を作成する

最初に、既定のルールを直接変更できないため、新しい機密情報の種類を作成する必要があります。 カスタムの機密情報の種類を使用してさまざまな操作を行うことができます。詳細については、「[セキュリティ & コンプライアンス PowerShell でカスタムの機密情報の種類を作成する](create-a-custom-sensitive-information-type-in-scc-powershell.md)」を参照してください。 この例では、シンプルに保ち、裏付けとなる証拠を削除し、クレジット カード番号ルールにキーワードを追加します。

すべての XML ルール定義は、次のような一般的なテンプレートに基づいて作成されます。テンプレート内でクレジット カード番号定義 XML をコピーしてから貼り付け、いくつかの値を変更する必要があります (次の例の ".. ." プレースホルダーに注意してください)。続いて、変更された XML をポリシーで使用できる新しいルールとしてアップロードします。

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="https://schemas.microsoft.com/office/2011/mce">
  <RulePack id=". . .">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id=". . ." />
    <Details defaultLangCode=". . .">
      <LocalizedDetails langcode=" . . . ">
         <PublisherName>. . .</PublisherName>
         <Name>. . .</Name>
         <Description>. . .</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

 <Rules>
   <!-- Paste the Credit Card Number rule definition here.-->
      <LocalizedStrings>
         <Resource idRef=". . .">
           <Name default="true" langcode=" . . . ">. . .</Name>
           <Description default="true" langcode=". . ."> . . .</Description>
         </Resource>
      </LocalizedStrings>
   </Rules>
</RulePackage>
```

ここまでで、次の例のような XML ができあがります。ルール パッケージとルールは独自の GUID によって識別されるため、2 つの一意な GUID を生成する必要があります。1 つはルール パッケージのため、もう 1 つはクレジット カード番号ルールの GUID を置き換えるために使用します。(次のコード例のエンティティ ID に指定されている GUID は、組み込みルール定義の GUID であるため、新しい GUID で置き換える必要があります。)GUID を生成するにはいくつかの方法がありますが、PowerShell で「 **[guid]::NewGuid()** 」と入力すれば容易に生成できます。

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="https://schemas.microsoft.com/office/2011/mce">
  <RulePack id="8aac8390-e99f-4487-8d16-7f0cdee8defc">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id="8d34806e-cd65-4178-ba0e-5d7d712e5b66" />
    <Details defaultLangCode="en">
      <LocalizedDetails langcode="en">
        <PublisherName>Contoso Ltd.</PublisherName>
        <Name>Financial Information</Name>
        <Description>Modified versions of the Microsoft rule package</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

 <Rules>
    <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f"
       patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
      <LocalizedStrings>
         <Resource idRef="db80b3da-0056-436e-b0ca-1f4cf7080d1f">
<!-- This is the GUID for the preceding Credit Card Number entity because the following text is for that Entity. -->
           <Name default="true" langcode="en-us">Modified Credit Card Number</Name>
           <Description default="true" langcode="en-us">Credit Card Number that looks for additional keywords, and another version of Credit Card Number that doesn't require keywords (but has a lower confidence level)</Description>
         </Resource>
      </LocalizedStrings>
   </Rules>
</RulePackage>
```

## <a name="remove-the-corroborative-evidence-requirement-from-a-sensitive-information-type"></a>機密情報の種類から補強証拠の要件を削除する

Microsoft Purview コンプライアンス ポータルにアップロードできる新しい機密情報の種類が作成されたので、次の手順はルールをより具体的にすることです。 チェックサムの条件を満たす 16 桁の番号だけを検索し、たとえばキーワードのような、追加の (補強) 証拠 を必要としないように、ルールを変更します。 これを行うには、XML のうち補強証拠を探している部分を削除する必要があります。 補強証拠は、誤検知の削減に役立ちます。 この場合、通常、クレジットカード番号の近くに特定のキーワードまたは有効期限があります。 その証拠を削除する場合は、`confidenceLevel` (この例では 85) を下げることで、クレジット カード番号が見つかったかどうかの信頼性を調整する必要もあります。

```xml
<Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="300"
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
      </Pattern>
    </Entity>
```

## <a name="look-for-keywords-that-are-specific-to-your-organization"></a>組織に固有のキーワードを探す

補強証拠が必要であるものの、異なるキーワードまたは追加のキーワードを指定し、その証拠を探す場所を変更する必要がある場合について考えてみましょう。16 桁の番号の前後から補強証拠を探す範囲を拡大または縮小するため、`patternsProximity` を調整することができます。独自のキーワードを追加するには、キーワード リストを定義し、それをルールの中で参照する必要があります。次の XML では、キーワードとして "company card" と "Contoso card" を追加し、これらの語句がクレジット カード番号の前後 150 文字以内に含まれるメッセージをクレジット カード番号として識別します。

```xml
<Rules>
<! -- Modify the patternsProximity to be "150" rather than "300." -->
    <Entity id="db80b3da-0056-436e-b0ca-1f4cf7080d1f" patternsProximity="150" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
<!-- Add the following XML, which references the keywords at the end of the XML sample. -->
          <Match idRef="My_Additional_Keywords" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
<!-- Add the following XML, and update the information inside the <Term> tags with the keywords that you want to detect. -->
    <Keyword id="My_Additional_Keywords">
      <Group matchStyle="word">
        <Term caseSensitive="false">company card</Term>
        <Term caseSensitive="false">Contoso card</Term>
      </Group>
    </Keyword>
```

## <a name="upload-your-rule"></a>ルールをアップロードする

ルールをアップロードするには、次の手順を実行する必要があります。

1. ルールを Unicode エンコードの .xml ファイルとして保存します。これとは違うエンコードでファイルを保存すると、ルールが機能しないことに注意してください。

2. [セキュリティ/コンプライアンス PowerShell に接続します](/powershell/exchange/connect-to-scc-powershell)。

3. PowerShell で次のように入力します。

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\custompath\MyNewRulePack.xml'))
   ```

   > [!IMPORTANT]
   > ルール パックが実際に格納されている場所を指定してください。`C:\custompath\` はプレースホルダーです。

4. 確認のために「Y」と入力し、**ENTER** キーを押します。

5. 次のように入力して、新しいルールがアップロードされ、表示名が正しいことことを確認します。

   ```powershell
   Get-DlpSensitiveInformationType
   ```

機密情報の検出に新しいルールを使用するようにするには、ルールを DLP ポリシーに追加する必要があります。ルールをポリシーに追加する方法については、「[テンプレートから DLP ポリシーを作成する](create-a-dlp-policy-from-a-template.md)」を参照してください。

## <a name="term-glossary"></a>用語集

このトピックの手順に登場した用語の定義は次のとおりです。

<br>

****

|用語|定義|
|---|---|
|エンティティ|エンティティとは、機密情報の種類 (たとえば、クレジット カード番号) のことです。各エンティティには、その ID として一意の GUID があります。GUID をコピーして XML 内で検索すると、XML ルール定義と XML ルールをローカライズしたすべての翻訳版が見つかります。また、翻訳版の GUID を検索して定義を見つけ、その GUID を検索することもできます。|
|= (式) フィールドで使用できる関数|XML ファイルが参照する `Func_credit_card` は、コンパイル済みコードでは関数です。関数は、複雑な正規表現を実行し、チェックサムが組み込みルールと一致することを確認するために使用されます。これはコード内で実行されるため、一部の変数は XML ファイルに含まれていません。|
|IdMatch|一致が照合されるパターンの ID です (たとえば、クレジット カード番号)。|
|キーワード リスト|XML ファイルでは、 `keyword_cc_verification` および `keyword_cc_name` も参照します。これらは、エンティティの前後 `patternsProximity` 文字以内から一致を探すキーワードのリストです。現在のところ、これらは XML 内に表示されません。  |
|パターン|パターンには、機密タイプが探しているもののリストが含まれています。 これには、チェックサムの検証などのタスクを実行するキーワード、正規表現、および内部関数が含まれます。 機密情報タイプは、固有の信頼性を持つ複数のパターンを指定することができます。 これは、裏付けとなる証拠が見つかった場合に高い信頼度を返し、裏付けとなる証拠がほとんどまたはまったく見つからなかった場合に低い信頼度を返す機密情報タイプを作成するときに役立ちます。|
|パターンの confidenceLevel|DLP エンジンが一致を検索した内容の信頼性のレベルです。信頼性のレベルは、パターンの要件が満たされた場合のパターンへの一致に関連付けられます。これは、Exchange メール フロー ルール (トランスポート ルールとも呼ばれる) を使用するときに考慮する必要のある信頼性の尺度です。|
|patternsProximity|クレジット カード番号パターンらしき情報が見つかった場合、 `patternsProximity` はその番号からどの程度近接した範囲内で補強証拠の探索を行うかを指定します。|
|recommendedConfidence|このルールに対して推奨される信頼レベルです。推奨される信頼性は、エンティティとアフィニティに適用されます。エンティティの場合、この数値がパターンの `confidenceLevel` に対して評価されることはありません。この数値は、必要な場合に信頼レベルを選択するために役立つ提案にすぎません。アフィニティの場合、メール フロー ルール アクションが呼び出されるためには、パターンの `confidenceLevel` が `recommendedConfidence` の数値を上回っている必要があります。`recommendedConfidence` は、アクションを起動するメール フロー ルールで使用される既定の信頼レベルです。必要であれば、この代わりにパターンの信頼レベルに基づいてメール フロー ルールを起動するように手動で変更することもできます。|
|

## <a name="for-more-information"></a>詳細情報

- [機密情報の種類のエンティティ定義](sensitive-information-type-entity-definitions.md)
- [カスタムの機密情報の種類を作成する](create-a-custom-sensitive-information-type.md)
- [データ損失防止について](dlp-learn-about-dlp.md)
