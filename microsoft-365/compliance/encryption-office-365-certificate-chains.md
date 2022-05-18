---
title: Microsoft 365 暗号化チェーン
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 4/25/2022
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- Strat_O365_IP
description: Microsoft 365のルート証明書と証明機関 (CA) の完全な一覧を表示します。
ms.openlocfilehash: a15c22218d481f62e1363e3ef4d521bd59283f10
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468000"
---
# <a name="microsoft-365-encryption-chains"></a>Microsoft 365 暗号化チェーン

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft 365は、さまざまな証明書プロバイダーを利用します。 次に、お客様がMicrosoft 365にアクセスするときに発生する可能性がある既知のMicrosoft 365ルート証明書の完全な一覧について説明します。 独自のインフラストラクチャにインストールする必要がある証明書の詳細については、「[Microsoft 365のサード パーティの SSL 証明書を計画する」を](../enterprise/plan-for-third-party-ssl-certificates.md)参照してください。 次の証明書情報は、Microsoft 365のすべての世界中および国内のクラウド インスタンスに適用されます。

最終更新日: **2022 年 4 月 25 日**

> [!NOTE]
> **DOD および GCC High** のお客様に適用される証明書情報については、「[Microsoft 365暗号化チェーン - DOD と GCC High](encryption-office-365-certificate-chains-itar.md)」を参照してください。

| **証明書の種類** | **P7b ダウンロード** | **CRL エンドポイント** | **OCSP エンドポイント** | **AIA エンドポイント** |
| --- | --- | --- | --- | --- |
| パブリックに信頼されたルート証明書 | [Microsoft 365 ルート証明書バンドル (P7B)](https://download.microsoft.com/download/4/a/b/4ab1c940-826b-444b-b287-b7a902e68da0/m365_root_certs_20220331.p7b) | crl.globalsign.net<br>www.d-trust.net | 該当なし | 該当なし |
| パブリックに信頼された中間証明書 | [Microsoft 365中間証明書バンドル (P7B)](https://download.microsoft.com/download/1/4/7/14777f28-3fde-4958-aebf-bd192a4a7fac/m365_intermediate_certs_20201013.p7b) | cdp1.public-trust.com<br>crl.cnnic.cn<br>crl.entrust.net<br>crl.globalsign.com<br>crl.globalsign.net<br>crl.identrust.com<br>crl.thawte.com<br>crl3.digicert.com<br>crl4.digicert.com<br>s1.symcb.com<br>www.d-trust.net | isrg.trustid.ocsp.identrust.com<br>ocsp.digicert.com<br>ocsp.entrust.net<br>ocsp.globalsign.com<br>ocsp.omniroot.com<br>ocsp.startssl.com<br>ocsp.thawte.com<br>ocsp2.globalsign.com<br>ocspcnnicroot.cnnic.cn<br>root-c3-ca2-2009.ocsp.d-trust.net<br>root-c3-ca2-ev-2009.ocsp.d-trust.net<br>s2.symcb.com | aia.startssl.com<br>apps.identrust.com<br>cacert.omniroot.com<br>www.cnnic.cn |

以下のルートセクションと中間セクションを展開して、証明書プロバイダーに関する追加の詳細を確認します。

## <a name="microsoft-365-root-certificate-details"></a>**ルート証明書の詳細をMicrosoft 365する**

### <a name="baltimore-cybertrust-root"></a>**Baltimore CyberTrust Root**

| **件名** | CN=Baltimore CyberTrust Root<br>OU=CyberTrust<br>O=Baltimore<br>C=IE |
| --- | --- |
| **Serial Number\(シリアル番号\)** | 02:00:00:B9 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha1RSA |
| **有効期限が前にありません** | 2000 年 5 月 12 日 18:46:00 UTC |
| **有効期間が後でない** | 2025 年 5 月 12 日 23:59:00 UTC |
| **サブジェクト キー識別子** | e5:9d:59:30:82:47:58:cc:ac:08:54:36:86:7b:3a:b5:04:4d:f0 |
| **拇印 (SHA-1)** | D4DE20D05E66FC53FE1A50882C78DB2852CAE474 |
| **拇印 (SHA-256)** | 16AF57A9F676B0AB126095AA5EBADEF22AB31119D644AC95CD4B93DBF3F26AEB |
| **Pin (SHA-256)** | Y9mvm0exBk1JoQ57f9Vm28jKo5lFm/woKcVxrYxu80o= |

### <a name="cnnic-root"></a>**CNNIC ROOT**

| **件名** | CN=CNNIC ROOT<br>O=CNNIC<br>C=CN |
| --- | --- |
| **Serial Number\(シリアル番号\)** | 49:33:00:01 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha1RSA |
| **有効期限が前にありません** | 2007 年 4 月 16 日 07:09:14 UTC |
| **有効期間が後でない** | 2027 年 4 月 16 日 07:09:14 UTC |
| **サブジェクト キー識別子** | 65:f2:31:ad:2a:f7:f7:dd:52:96:0a:c7:02:c1:0e:ef:a6:d5:3b:11 |
| **機関キー識別子** | keyid:65:f2:31:ad:2a:f7:f7:dd:52:96:0a:c7:02:c1:0e:ef:a6:d5:3b:11 |
| **拇印 (SHA-1)** | 8BAF4C9B1DF02A92F7DA128EB91BACF498604B6F |
| **拇印 (SHA-256)** | E28393773DA845A679F2080CC7FB44A3B7A1C3792CB7EB7729FDCB6A8D99AEA7 |
| **Pin (SHA-256)** | H0IkzshPyZztiB/2/P0+IfjFGcVHqmpd094kcwLOUNE= |

### <a name="digicert-global-root-ca"></a>**DigiCert グローバル ルート CA**

| **件名** | CN=DigiCert グローバル ルート CA<br>OU=www.digicert.com<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **Serial Number\(シリアル番号\)** | 08:3B:E0:56:90:42:46:B1:A1:75:6A:C9:59:91:C7:4A |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha1RSA |
| **有効期限が前にありません** | 2006 年 11 月 10 日 00:00:00 UTC |
| **有効期間が後でない** | 2031 年 11 月 10 日 00:00:00 UTC |
| **サブジェクト キー識別子** | 03:de:50:35:56:d1:4c:bb:66:f0:a3:e2:1b:1b:c3:97:b2:3d:d1:55 |
| **機関キー識別子** | keyid:03:de:50:35:56:d1:4c:bb:66:f0:a3:e2:1b:1b:c3:97:b2:3d:d1:55 |
| **拇印 (SHA-1)** | A8985D3A65E5E5C4B2D7D66D40C6DD2FB19C5436 |
| **拇印 (SHA-256)** | 4348A0E9444C78CB265E058D5E8944B4D84F9662BD26DB257F8934A443C70161 |
| **Pin (SHA-256)** | r/mIkG3eEpVdm+u/ko/cwxzOMo1bk4TyHIlByibiA5E= |

### <a name="digicert-global-root-g2"></a>**DigiCert グローバル ルート G2**

| **件名** | CN=DigiCert Global Root G2<br>OU=www.digicert.com<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **発行者** | CN=DigiCert Global Root G2、OU=www.digicert.com、O=DigiCert Inc、C=US |
| **Serial Number\(シリアル番号\)** | 03:3A:F1:E6:A7:11:A9:A0:BB:28:64:B1:1D:09:FA:E5 |
| **公開キーの長さ** | RSA 2048 ビット |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2013 年 8 月 1 日 (木曜日) 5:00 AM |
| **有効期間は次の値までです** | 2038 年 1 月 15 日 (金曜日) 4:00 AM |
| **サブジェクト キー識別子** | 4E2254201895E6E36EE60FFAFAB912ED06178F39 |
| **機関キー識別子** | KeyID:4e:22:54:20:18:95:e6:e3:6e:e6:0f:fa:fa:b9:12:ed:06:17:8f:39 |
| **拇印 (SHA-1)** | DF3C24F9BFD666761B268073FE06D1CC8D4F82A4 |
| **拇印 (SHA-256)** | CB3CCBB76031E5E0138F8DD39A23F9DE47FFC35E43C1144CEA27D46A5AB1CB5F |

### <a name="digicert-high-assurance-ev-root-ca"></a>**DigiCert High Assurance EV ルート CA**

| **件名** | CN=DigiCert High Assurance EV ルート CA<br>OU=www.digicert.com<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **Serial Number\(シリアル番号\)** | 02:AC:5C:26:6A:0B:40:9B:8F:0B:79:F2:AE:46:25:77 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha1RSA |
| **有効期限が前にありません** | 2006 年 11 月 10 日 00:00:00 UTC |
| **有効期間が後でない** | 2031 年 11 月 10 日 00:00:00 UTC |
| **サブジェクト キー識別子** | b1:3e:c3:69:03:f8:bf:47:01:d4:98:26:1a:08:02:ef:63:64:2b:c3 |
| **機関キー識別子** | keyid:b1:3e:c3:69:03:f8:bf:47:01:d4:98:26:1a:08:02:ef:63:64:2b:c3 |
| **拇印 (SHA-1)** | 5FB7EE0633E259DBAD0C4C9AE6D38F1A61C7DC25 |
| **拇印 (SHA-256)** | 7431E5F4C3C1CE4690774F0B61E05440883BA9A01ED00BA6ABD7806ED3B118CF |
| **Pin (SHA-256)** | WoiWRyIOVNa9ihaBciRSC7X ZhliYS9VwUGOIud4PB18= |

### <a name="d-trust-root-class-3-ca-2-2009"></a>**D-TRUST ルート クラス 3 CA 2 2009**

| **件名** | CN=D-TRUST ルート クラス 3 CA 2 2009<br>O=D-Trust GmbH<br>C=DE |
| --- | --- |
| **Serial Number\(シリアル番号\)** | 09:83:F3 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2009 年 11 月 5 日 08:35:58 UTC |
| **有効期間が後でない** | 2029 年 11 月 5 日 08:35:58 UTC |
| **サブジェクト キー識別子** | fd:da:14:c4:9f:30:de:21:bd:1e:42:39:fc:ab:63:23:49:e0:f1:84 |
| **拇印 (SHA-1)** | 58E8ABB0361533FB80F79B1B6D29D3FF8D5F00F0 |
| **拇印 (SHA-256)** | 49E7A442ACF0EA628705054B52564B650E4F49E42E348D6AA38E039E957B1C1 |
| **Pin (SHA-256)** | 7KDxgUAs56hlKzG00DbfJH46MLf0GlDZHsT5CwBrQ6E= |
| **CRL URL** | ldap://directory.d-trust.net/CN=D-TRUST%20Root%20Class%203%20CA%202%202009,O=D-Trust%20GmbH,C=DE?certificaterevocationlist<br>http://www.d-trust.net/crl/d-trust\_root\_class\_3\_ca\_2\_2009.crl |

### <a name="d-trust-root-class-3-ca-2-ev-2009"></a>**D-TRUST ルート クラス 3 CA 2 EV 2009**

| **件名** | CN=D-TRUST ルート クラス 3 CA 2 EV 2009<br>O=D-Trust GmbH<br>C=DE |
| --- | --- |
| **Serial Number\(シリアル番号\)** | 09:83:F4 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2009 年 11 月 5 日 08:50:46 UTC |
| **有効期間が後でない** | 2029 年 11 月 5 日 08:50:46 UTC |
| **サブジェクト キー識別子** | d3:94:8a:4c:62:13:2a:19:2e:cc:72:8a:7d:36:d7:9a:1c:dc:67 |
| **拇印 (SHA-1)** | 96C91B0B95B4109842FAD0D82279FE60FAB91683 |
| **拇印 (SHA-256)** | EEC5496B988CE98625B934092EEC2908BED0B0F316C2D4730C84EAF1F3D34881 |
| **Pin (SHA-256)** | /zQvtsTIvTCkcG9zSJU58Z5uSMwF9GJUZU9mENvFQOk= |
| **CRL URL** | ldap://directory.d-trust.net/CN=D-TRUST%20Root%20Class%203%20CA%202%20EV%202009,O=D-Trust%20GmbH,C=DE?certificaterevocationlist<br>http://www.d-trust.net/crl/d-trust\_root\_class\_3\_ca\_2\_ev\_2009.crl |

### <a name="entrust-root-certification-authority---g2"></a>**ルート証明機関の委託 - G2**

| **件名** | CN=Entrust Root 証明機関 - G2<br>OU=&quot;(c) 2009 Entrust, Inc. - 承認された使用のみ&quot;<br>OU=www.entrust.net/legal-terms を参照してください<br>O=&quot;Entrust, Inc.&quot;<br>C=US |
| --- | --- |
| **Serial Number\(シリアル番号\)** | 4A:53:8C:28 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2009 年 7 月 7 日 17:25:54 UTC |
| **有効期間が後でない** | 2030 年 12 月 7 日 17:55:54 UTC |
| **サブジェクト キー識別子** | 6a:72:26:7a:d0:1e:ef:7d:e7:3b:69:51:d4:6c:8d:9f:90:12:66:ab |
| **拇印 (SHA-1)** | 8CF427FD790C3AD166068DE81E57EFBB932272D4 |
| **拇印 (SHA-256)** | 43DF5774B03E7FEF5FE40D931A7BEDF1BB2E6B42738C4E6D3841103D3AA7F339 |
| **Pin (SHA-256)** | du6FkDdMcVQ3u8prumAo6t3i3G27uMP2EOhR8R0at/U= |

### <a name="entrustnet-certification-authority-2048"></a>**Entrust.net Certification Authority (2048)**

| **件名** | CN=Entrust.net 証明機関 (2048)<br>OU=(c) 1999 Entrust.net Limited<br>OU=www.entrust.net/CPS2048\_ incorp. by ref. (liab を制限します。)<br>O=Entrust.net |
| --- | --- |
| **Serial Number\(シリアル番号\)** | 38:63:DE:F8 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha1RSA |
| **有効期限が前にありません** | 12 月 24 日 17:50:51 1999 UTC |
| **有効期間が後でない** | 2029 年 7 月 24 日 14:15:12 UTC |
| **サブジェクト キー識別子** | 55:e4:81:d1:11:80:be:d8:89:b9:08:a3:31:f9:a1:24:09:16:b9:70 |
| **拇印 (SHA-1)** | 503006091D97D4F5AE39F7CBE7927D7D652D3431 |
| **拇印 (SHA-256)** | 6DC47172E01CBCB0BF62580D895FE2B8AC9AD4F873801E0C10B9C837D21EB177 |
| **Pin (SHA-256)** | HqPF5D7WbC2imDpCpKebHpBnhs6fG1hiFBmgBGOofTg= |

### <a name="globalsign-root-ca---r1"></a>**GlobalSign Root CA - R1**

| **件名** | CN=GlobalSign ルート CA<br>OU=ルート CA<br>O=GlobalSign nv-sa<br>C=BE |
| --- | --- |
| **Serial Number\(シリアル番号\)** | 04:00:00:00:00:01:15:4B:5A:C3:94 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha1RSA |
| **有効期限が前にありません** | 1998 年 9 月 1 日 12:00:00 UTC |
| **有効期間が後でない** | 2028 年 1 月 28 日 12:00:00 UTC |
| **サブジェクト キー識別子** | 60:7b:66:1a:45:0d:97:ca:89:50:2f:7d:04:cd:34:a8:ff:fc:fd:4b |
| **拇印 (SHA-1)** | B1BC968BD4F49D622AA89A81F2150152A41D829C |
| **拇印 (SHA-256)** | EBD41040E4BB3EC742C9E381D31EF2A41A48B6685C96E7CEF3C1DF6CD4331C99 |
| **Pin (SHA-256)** | K87oWBWM9ULzyddvDfoxL+8lpNyoUB2ptGtn0fv6G2Q= |

### <a name="globalsign-root-ca---r3"></a>**GlobalSign Root CA - R3**

| **件名** | CN=GlobalSign<br>O=GlobalSign<br>OU=GlobalSign ルート CA - R3 |
| --- | --- |
| **発行者** | CN=GlobalSign、O=GlobalSign、OU=GlobalSign ルート CA - R3 |
| **Serial Number\(シリアル番号\)** | 04:00:00:00:00:01:21:58:53:08:A2 |
| **公開キーの長さ** | RSA 2048 ビット |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2009 年 3 月 18 日 (水曜日) 3:00 AM |
| **有効期間は次の値までです** | 2029 年 3 月 18 日 (日曜日) 3:00 AM |
| **サブジェクト キー識別子** | 8FF04B7FA82E4524AE4D50FA639A8BDEE2DD1BBC |
| **機関キー識別子** | KeyID:8f:f0:4b:7f:a8:2e:45:24:ae:4d:50:fa:63:9a:8b:de:e2:dd:1b:bc |
| **拇印 (SHA-1)** | D69B561148F01C77C54578C10926DF5B856976AD |
| **拇印 (SHA-256)** | CBB522D7B7F127AD6A0113865BDF1CD4102E7D0759AF635A7CF4720DC963C53B |

### <a name="isrg-root-x1"></a>**ISRG ルート X1**

| **件名** | C = US、O = Internet Security Research Group、CN = ISRG ルート X1 |
| --- | --- |
| **Serial Number\(シリアル番号\)** | 82:10:cf:b0:d2:40:e3:59:44:63:e0:bb:63:82:8b:00 |
| **公開キーの長さ** | RSA 4096 ビット |
| **署名アルゴリズム** | sha256WithRSAEncryption |
| **有効期限が前にありません** | 2015 年 6 月 4 日 11:04:38 UTC |
| **有効期間が後でない** | 2035 年 6 月 4 日 11:04:38 UTC |
| **サブジェクト キー識別子** | 79:B4:59:E6:7B:B6:E5:E4:01:73:80:08:C8:1A:58:F6:E9:9B:6E |
| **拇印 (SHA-1)** | CABD2A79A1076A31F21D253635CB039D4329A5E8 |
| **拇印 (SHA-256)** | 96BCEC06264976F37460779ACF28C5A7CFE8A3C0AAE11A8FFCEE05C0BDDF08C6 |
| **Pin (SHA-256)** | 0b9fa5a59eed715c26c1020c711b4f6ec42d58b0015e14337a39dad301c5afc3 |

### <a name="thawte-primary-root-ca---g3"></a>**thawte プライマリ ルート CA - G3**

| **件名** | CN=thawte プライマリ ルート CA - G3<br>OU=&quot;(c) 2008 Thawte, Inc. - 承認された使用のみ&quot;<br>OU=Certification Services Division<br>O=&quot;Thawte, Inc.&quot;<br>C=US |
| --- | --- |
| **Serial Number\(シリアル番号\)** | 60:01:97:B7:46:A7:EA:B4:B4:9A:D6:4B:2F:F7:90:FB |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2008 年 4 月 2 日 00:00:00 UTC |
| **有効期間が後でない** | 2037 年 12 月 1 日 23:59:59 UTC |
| **サブジェクト キー識別子** | ad:6c:aa:94:60:9c:ed:e4:ff:fa:3e:0a:74:2b:63:03:f7:b6:59:bf |
| **拇印 (SHA-1)** | F18B538D1BE903B6A6F056435B171589CAF36BF2 |
| **拇印 (SHA-256)** | 4B03F45807AD70F21BFC2CAE71C9FDE4604C064CF5FFB686BAE5DBAAD7FDD34C |
| **Pin (SHA-256)** | GQbGEk27Q4V40A4GbVBUxsN/D6YCjAVUXgmU7drshik= |

### <a name="verisign-class-3-public-primary-certification-authority---g5"></a>**VeriSign クラス 3 パブリック プライマリ証明機関 - G5**

| **件名** | CN=VeriSign クラス 3 パブリック プライマリ証明機関 - G5<br>OU=&quot;(c) 2006 VeriSign, Inc. - 承認された使用のみ&quot;<br>OU=VeriSign トラスト ネットワーク<br>O=&quot;VeriSign, Inc.&quot;<br>C=US |
| --- | --- |
| **Serial Number\(シリアル番号\)** | 18:DA:D1:9E:26:7D:E8:BB:4A:21:58:CD:CC:6B:3B:4A |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha1RSA |
| **有効期限が前にありません** | 2006 年 11 月 8 日 00:00:00 UTC |
| **有効期間が後でない** | 2036 年 7 月 16 日 23:59:59 UTC |
| **サブジェクト キー識別子** | 7f:d3:65:a7:c2:dd:ec:bb:f0:30:09:f3:43:39:fa:02:af:33:31:33 |
| **拇印 (SHA-1)** | 4EB6D578499B1CCF5F581EAD56BE3D9B6744A5E5 |
| **拇印 (SHA-256)** | 9ACFAB7E43C8D880D06B262A94DEEEE4B4659989C3D0CAF19BAF6405E41AB7DF |
| **Pin (SHA-256)** | JbQbUG5JJUoI6brnx0x3vZF6jilxsapbXGVfjhN8Fg= |

## <a name="microsoft-365-intermediate-certificate-details"></a>**中間証明書の詳細をMicrosoft 365する**

### <a name="cnnic-sha256-ssl"></a>**CNNIC SHA256 SSL**

| **件名** | CN=CNNIC SHA256 SSL <br>O=CNNIC SHA256 SSL <br>C=CN |
| --- | --- |
| **発行者** | CN=CNNIC ROOT <br>O=CNNIC <br>C=CN |
| **Serial Number\(シリアル番号\)** | 49:33:00:7C |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2014 年 12 月 18 日 12:32:18 UTC |
| **有効期間が後でない** | 2024 年 12 月 18 日 12:32:18 UTC |
| **サブジェクト キー識別子** | b7:d1:59:8b:8c:0d:06:28:47:23:00:3a:36:04:a5:ee:38:76:53:3c |
| **機関キー識別子** | keyid:65:f2:31:ad:2a:f7:f7:dd:52:96:0a:c7:02:c1:0e:ef:a6:d5:3b:11 |
| **拇印 (SHA-1)** | FC844648FC70843921BE88B18C48787A3E2813E |
| **拇印 (SHA-256)** | FA8B9F99DBB94E7B772AA9190846E777047C15C7A3BF4A1AF9C0CA984A689511 |
| **Pin (SHA-256)** | dKZRcLDh7hBNZTmTIHOGJ6C2Om/ITjUCPkOnLTnrZXk= |
| **AIA URL** | http://www.cnnic.cn/download/cert/CNNICROOT.cer |
| **CRL URL** | ldap:///CN=crl1,%20OU=crl,%20O=CNNIC,%20C=CN?certificateRevocationList;binary,authorityRevocationList;binary,deltaRevocationList;binary<br>http://crl.cnnic.cn/download/rootsha2crl/CRL1.crl |
| **OCSP URL** | <http://ocspcnnicroot.cnnic.cn> |

### <a name="d-trust-ssl-class-3-ca-1-2009"></a>**D-TRUST SSL クラス 3 CA 1 2009**

| **件名** | CN=D-TRUST SSL クラス 3 CA 1 2009<br>O=D-Trust GmbH<br>C=DE |
| --- | --- |
| **発行者** | CN=D-TRUST ルート クラス 3 CA 2 2009<br>O=D-Trust GmbH<br>C=DE |
| **サブジェクトの別名** | RFC822 Name=info@d-trust.net<br>URL=http://www.d-trust.net |
| **Serial Number\(シリアル番号\)** | 09:90:63 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2009 年 11 月 12 日 12:46:55 UTC |
| **有効期間が後でない** | 2029 年 11 月 5 日 08:35:58 UTC |
| **サブジェクト キー識別子** | 50:19:32:94:9a:c4:b5:04:4d:56:d0:83:21:d5:35:55:b0:b1:7a |
| **機関キー識別子** | keyid:fd:da:14:c4:9f:30:de:21:bd:1e:42:39:fc:ab:63:23:49:e0:f1:84 |
| **拇印 (SHA-1)** | 2FC5DE6528CDBE50A14C382FC1DE524FAABF95FC |
| **拇印 (SHA-256)** | 6AC159B4C2BC8E729F3B84642EF1286BCC80D775FE278C740ADA468D59439025 |
| **Pin (SHA-256)** | 9w0QP9HzLXkfs+4zENaUFq2XKcQON1oyksoJ+Gg2AZE= |
| **CRL URL** | ldap://directory.d-trust.net/CN=D-TRUST%20Root%20Class%203%20CA%202%202009,O=D-Trust%20GmbH,C=DE?certificaterevocationlist<br>http://www.d-trust.net/crl/d-trust\_root\_class\_3\_ca\_2\_2009.crl |
| **OCSP URL** | `http://root-c3-ca2-2009.ocsp.d-trust.net` |

### <a name="d-trust-ssl-class-3-ca-1-ev-2009"></a>**D-TRUST SSL クラス 3 CA 1 EV 2009**

| **件名** | CN=D-TRUST SSL クラス 3 CA 1 EV 2009<br>O=D-Trust GmbH<br>C=DE |
| --- | --- |
| **発行者** | CN=D-TRUST ルート クラス 3 CA 2 EV 2009<br>O=D-Trust GmbH<br>C=DE |
| **サブジェクトの別名** | RFC822 Name=info@d-trust.net<br>URL=http://www.d-trust.net |
| **Serial Number\(シリアル番号\)** | 09:90:64 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2009 年 11 月 12 日 12:52:43 UTC |
| **有効期間が後でない** | 2029 年 11 月 5 日 08:50:46 UTC |
| **サブジェクト キー識別子** | ac:ed:a5:9d:7a:a2:b6:43:f1:18:8a:25:6a:6c:b1:cc:a8:f2:5a:d4 |
| **機関キー識別子** | keyid:d3:94:8a:4c:62:13:2a:19:2e:cc:af:72:8a:7d:36:d7:9a:1c:dc:67 |
| **拇印 (SHA-1)** | 1069423D308D0FC54575059638560FC7556E32B3 |
| **拇印 (SHA-256)** | B0935DC04B4E60C0C42DEF7EC57A1B1D8F958D17988E71CC80A8CF5E635BA5B4 |
| **Pin (SHA-256)** | lv5BNZ5aWd27ooolUL-FTwIaaQwG4yyH3rss4X8= |
| **CRL URL** | ldap://directory.d-trust.net/CN=D-TRUST%20Root%20Class%203%20CA%202%20EV%202009,O=D-Trust%20GmbH,C=DE?certificaterevocationlist<br>http://www.d-trust.net/crl/d-trust\_root\_class\_3\_ca\_2\_ev\_2009.crl |
| **OCSP URL** | `http://root-c3-ca2-ev-2009.ocsp.d-trust.net` |

### <a name="digicert-basic-rsa-cn-ca-g2"></a>**DigiCert Basic RSA CN CA G2**

| **件名** | CN=DigiCert Basic RSA CN CA G2<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **発行者** | CN=DigiCert グローバル ルート CA、OU=www.digicert.com、O=DigiCert Inc、C=US |
| **Serial Number\(シリアル番号\)** | 02:F7:E1:F9:82:BA:D0:09:AF:F4:7D:C9:57:41:B2:F6 |
| **公開キーの長さ** | RSA 2048 ビット |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2020 年 3 月 4 日(水) 4:04 |
| **有効期間は次の値までです** | 2030 年 3 月 4 日 (月) 4:04 AM |
| **サブジェクト キー識別子** | 06BDA69B60795031BED5A9024AA0D095538B2F34 |
| **機関キー識別子** | KeyID:03:de:50:35:56:d1:4c:bb:66:f0:a3:e2:1b:1b:c3:97:b2:3d:d1:55 |
| **拇印 (SHA-1)** | 4D1FA5D1FB1AC3917C08E43F65015E6AEA571179 |
| **拇印 (SHA-256)** | CB57B3FF2040CB269497625BC90FA9D7B4ED4938C6F60F42F69AFDF508AC2993 |
| **CRL URL** | http://crl.digicert.cn/DigiCertGlobalRootCA.crl |
| **OCSP URL** | http://ocsp.digicert.cn |

### <a name="digicert-cloud-services-ca-1-older"></a>**DigiCert Cloud Services CA-1** (古い)

| **件名** | CN=DigiCert Cloud Services CA-1<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **発行者** | CN=DigiCert グローバル ルート CA<br>OU=www.digicert.com<br>O=DigiCert Inc<br>C=US |
| **Serial Number\(シリアル番号\)** | 01:9E:C1:C6:BD:3F:59:7B:B2:0C:33:38:E5:51:D8:77 |
| **公開キーの長さ** | RSA 2048 ビット |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2015 年 8 月 4 日 12:00 AM |
| **有効期間は次の値までです** | 2030 年 8 月 4 日 12:00 AM |
| **サブジェクト キー識別子** | dd:51:d0:a2:31:73:a9:73:ae:8f:b4:01:7e:5d:8c:57:cb:9f:f0:f7 |
| **機関キー識別子** | 03:de:50:35:56:d1:4c:bb:66:f0:a3:e2:1b:1b:c3:97:b2:3d:d1:55 |
| **拇印 (SHA-1)** | 81B68D6CD2f221F8F534E677523BB236BBA1DC56 |
| **拇印 (SHA-256)** | 2F6889961A7CA7067E8BA103C2CF9B9A924F8CA293F1178E23A1978D2F133D3 |
| **Pin (SHA-256)** | UgpUVparimk8QCjtWQaUQ7EGrtrykc/L8N66EhFY3VE= |
| **CRL URL** | http://crl3.digicert.com/DigiCertGlobalRootCA.crl<br>http://crl4.digicert.com/DigiCertGlobalRootCA.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="digicert-cloud-services-ca-1"></a>**DigiCert Cloud Services CA-1**

| **件名** | CN=DigiCert Cloud Services CA-1<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **発行者** | CN=DigiCert グローバル ルート CA<br>OU=www.digicert.com<br>O=DigiCert Inc<br>C=US |
| **Serial Number\(シリアル番号\)** | 0F:17:1A:48:C6:F2:23:80:92:18:CD:2E:D6:DD:C0:E8 |
| **公開キーの長さ** | RSA 2048 ビット |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2020 年 9 月 25 日 00:00 AM |
| **有効期間が後でない** | 2030 年 9 月 24 日 11:59 PM |
| **サブジェクト キー識別子** | dd:51:d0:a2:31:73:a9:73:ae:8f:b4:01:7e:5d:8c:57:cb:9f:f0:f7 |
| **機関キー識別子** | 03:de:50:35:56:d1:4c:bb:66:f0:a3:e2:1b:1b:c3:97:b2:3d:d1:55 |
| **拇印 (SHA-1)** | B3F6B64A07BB9611F47174407841F564FB991F29 |
| **拇印 (SHA-256)** | 5F88694615E4C61686E106B84C3338C6720C535F60D36F61282ED15E1977DD44 |
| **Pin (SHA-256)** | UgpUVparimk8QCjtWQaUQ7EGrtrykc/L8N66EhFY3VE= |
| **CRL URL** | http://crl3.digicert.com/DigiCertGlobalRootCA.crl<br>http://crl4.digicert.com/DigiCertGlobalRootCA.crl |
| **OCSP URL** | http://ocsp.digicert.com

### <a name="digicert-sha2-extended-validation-server-ca"></a>**DigiCert SHA2 拡張検証サーバー CA**

| **件名** | CN=DigiCert SHA2 拡張検証サーバー CA<br>OU=www.digicert.com<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **発行者** | CN=DigiCert High Assurance EV Root CA, OU=www.digicert.com, O=DigiCert Inc, C=US |
| **Serial Number\(シリアル番号\)** | 0C:79:A9:44:B0:8C:11:95:20:92:61:5F:E2:6B:1D:83 |
| **公開キーの長さ** | RSA 2048 ビット |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2013 年 10 月 22 日(火) 5:00 AM |
| **有効期間は次の値までです** | 2028 年 10 月 22 日 (日曜日) 5:00 AM |
| **サブジェクト キー識別子** | 3DD350A5D6A0ADEEF34A600A65D321D4F8F8D60F |
| **機関キー識別子** | KeyID:b1:3e:c3:69:03:f8:bf:47:01:d4:98:26:1a:08:02:ef:63:64:2b:c3 |
| **拇印 (SHA-1)** | 7E2F3A4F8FE8FA8A5730AECA029696637E986F3F |
| **拇印 (SHA-256)** | 403E062A2653059113285BAF80A0D4AE422C848C9F78FAD01FC94BC5B87FEF1A |
| **CRL URL** | http://crl4.digicert.com/DigiCertHighAssuranceEVRootCA.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="digicert-sha2-high-assurance-server-ca"></a>**DigiCert SHA2 High Assurance Server CA**

| **件名** | CN=DigiCert SHA2 High Assurance Server CA<br>OU=www.digicert.com<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **発行者** | CN=DigiCert High Assurance EV ルート CA<br>OU=www.digicert.com<br>O=DigiCert Inc<br>C=US |
| **Serial Number\(シリアル番号\)** | 04:E1:E7:A4:DC:5C:F2:F3:6D:C0:2B:42:B8:5D:15:9F |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2013 年 10 月 22 日 12:00:00 UTC |
| **有効期間が後でない** | 2028 年 10 月 22 日 12:00:00 UTC |
| **サブジェクト キー識別子** | 51:68:ff:90:af:02:07:75:3c:cc:d9:65:64:62:a2:12:b8:59:72:3b |
| **機関キー識別子** | keyid:b1:3e:c3:69:03:f8:bf:47:01:d4:98:26:1a:08:02:ef:63:64:2b:c3 |
| **拇印 (SHA-1)** | A031C46782E6E6C662C2C87C76DA9AA62CCABD8E |
| **拇印 (SHA-256)** | 19400BE5B7A31FB733917700789D2F0A2471C0C9D506C0E504C06C16D7CB17C0 |
| **Pin (SHA-256)** | k2v657xBsOVe1PQRwOsHsw3bsGT2VzIqz5K+59sNQws= |
| **CRL URL** | http://crl4.digicert.com/DigiCertHighAssuranceEVRootCA.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="digicert-sha2-secure-server-ca"></a>**DigiCert SHA2 Secure Server CA**

| **件名** | CN=DigiCert SHA2 Secure Server CA<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **発行者** | CN=DigiCert グローバル ルート CA<br>OU=www.digicert.com<br>O=DigiCert Inc<br>C=US |
| **Serial Number\(シリアル番号\)** | 01:FD:A3:EB:6E:CA:75:C8:88:43:8B:72:4B:CF:BC:91 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2013 年 3 月 8 日 12:00:00 UTC |
| **有効期間が後でない** | 2023 年 3 月 8 日 12:00:00 UTC |
| **サブジェクト キー識別子** | 0f:80:61:1c:82:31:61:d5:2f:28:e7:8d:46:38:b4:2c:e1:c6:d9:e2 |
| **機関キー識別子** | keyid:03:de:50:35:56:d1:4c:bb:66:f0:a3:e2:1b:1b:c3:97:b2:3d:d1:55 |
| **拇印 (SHA-1)** | 1FB86B1168EC743154062E8C9CC5B171A4B7CCB4 |
| **拇印 (SHA-256)** | 154C433C491929C5EF686E838E323664A00E6A0D822CCC958FB4DAB03E49A08F |
| **Pin (SHA-256)** | 5kJvNEMw0KjrCAu7eXY5HZdvyCS13BbA0VJG1RSP91w= |
| **CRL URL** | http://crl3.digicert.com/DigiCertGlobalRootCA.crl<br>http://crl4.digicert.com/DigiCertGlobalRootCA.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="digicert-sha2-secure-server-ca"></a>**DigiCert SHA2 Secure Server CA**

| **件名** | CN=DigiCert SHA2 Secure Server CA<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **発行者** | CN=DigiCert グローバル ルート CA、OU=www.digicert.com、O=DigiCert Inc、C=US |
| **Serial Number\(シリアル番号\)** | 02:74:2E:AA:17:CA:8E:21:C7:17:BB:1F:FC:FD:0C:A0 |
| **公開キーの長さ** | RSA 2048 ビット |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2020 年 9 月 22 日(火) 17:00 |
| **有効期間は次の値までです** | 2030 年 9 月 22 日(日) 16:59 |
| **サブジェクト キー識別子** | 0F80611C823161D52F28E78D4638B42CE1C6D9E2 |
| **機関キー識別子** | KeyID:03:de:50:35:56:d1:4c:bb:66:f0:a3:e2:1b:1b:c3:97:b2:3d:d1:55 |
| **拇印 (SHA-1)** | 626D44E704D1CEABE3BF0D53397464AC8080142C |
| **拇印 (SHA-256)** | C1AD7778796D20BCA65C889A2655021156528BB62FF5FA43E1B8E5A83E3D2EAA |
| **CRL URL** | http://crl3.digicert.com/DigiCertGlobalRootCA.crl http://crl4.digicert.com/DigiCertGlobalRootCA.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="digicert-tls-rsa-sha256-2020-ca1"></a>**DigiCert TLS RSA SHA256 2020 CA1**

| **件名** | CN=DigiCert TLS RSA SHA256 2020 CA1<br>O=DigiCert Inc<br>C=US |
| --- | --- |
| **発行者** | CN=DigiCert グローバル ルート CA、OU=www.digicert.com、O=DigiCert Inc、C=US |
| **Serial Number\(シリアル番号\)** | 0A:35:08:D5:5C:29:2B:01:7D:F8:AD:65:C0:0F:F7:E4 |
| **公開キーの長さ** | RSA 2048 ビット |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2020 年 9 月 23 日 (水曜日) 5:00 PM |
| **有効期間は次の値までです** | 2030 年 9 月 23 日 (月曜日) 16:59 |
| **サブジェクト キー識別子** | B76BA2EAA8AA848C79EAB4DA0F98B2C59576B9F4 |
| **機関キー識別子** | KeyID:03:de:50:35:56:d1:4c:bb:66:f0:a3:e2:1b:1b:c3:97:b2:3d:d1:55 |
| **拇印 (SHA-1)** | 6938FD4D98BAB03FAADB97B34396831E3780AEA1 |
| **拇印 (SHA-256)** | 25768713D3B459F9382D2A594F85F34709FD2A8930731542A4146FFB246BEC69 |
| **CRL URL** | http://crl3.digicert.com/DigiCertGlobalRootCA.crl http://crl4.digicert.com/DigiCertGlobalRootCA.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="entrust-certification-authority---l1c"></a>**証明機関の委託 - L1C**

| **件名** | CN=Entrust 証明機関 - L1C<br>OU=&quot;(c) 2009 Entrust, Inc.&quot;<br>OU=www.entrust.net/rpa は参照によって組み込まれています<br>O=&quot;Entrust, Inc.&quot;<br>C=US |
| --- | --- |
| **発行者** | CN=Entrust.net 証明機関 (2048)<br>OU=(c) 1999 Entrust.net Limited<br>OU=www.entrust.net/CPS2048\_ incorp. by ref. (liab を制限します。)<br>O=Entrust.net |
| **Serial Number\(シリアル番号\)** | 4C:0E:8C:39 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha1RSA |
| **有効期限が前にありません** | 2011 年 11 月 11 日 15:40:40 UTC |
| **有効期間が後でない** | 2021 年 11 月 12 日 02:51:17 UTC |
| **サブジェクト キー識別子** | 1e:f1:ab:89:06:f8:49:0f:01:33:77:ee:14:7a:ee:19:7c:93:28:4d |
| **機関キー識別子** | keyid:55:e4:81:d1:11:80:be:d8:89:b9:08:a3:31:f9:a1:24:09:16:b9:70 |
| **拇印 (SHA-1)** | C53E73073F93CE7895DE7484126BC303DAB9E657 |
| **拇印 (SHA-256)** | 0EE4DAF71A85D842D23F4910FD4C909B7271861931F1D5FEAC86825F52700E2 |
| **Pin (SHA-256)** | VFv5NemtodoRftw8KsvFb8AoCWwOJJ6bOJS+Ui0bQ94= |
| **CRL URL** | http://crl.entrust.net/2048ca.crl |
| **OCSP URL** | http://ocsp.entrust.net |

### <a name="entrust-certification-authority---l1k"></a>**証明機関の委託 - L1K**

| **件名** | CN=Entrust 証明機関 - L1K<br>OU=&quot;(c) 2012 Entrust, Inc. - 承認された使用のみ&quot;<br>OU=www.entrust.net/legal-terms を参照してください<br>O=&quot;Entrust, Inc.&quot;<br>C=US |
| --- | --- |
| **発行者** | CN=Entrust Root 証明機関 - G2<br>OU=&quot;(c) 2009 Entrust, Inc. - 承認された使用のみ&quot;<br>OU=www.entrust.net/legal-terms を参照してください<br>O=&quot;Entrust, Inc.&quot;<br>C=US |
| **Serial Number\(シリアル番号\)** | 0E:E9:4C:C3:00:00:00:00:51:D3:77:85 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2015 年 10 月 5 日 19:13:56 UTC |
| **有効期間が後でない** | 2030 年 12 月 5 日 19:43:56 UTC |
| **サブジェクト キー識別子** | 82:a2:70:74:dd:bc:53:3f:cf:7b:d4:f7:cd:7f:a7:60:c6:0a:4c:bf |
| **機関キー識別子** | keyid:6a:72:26:7a:d0:1e:ef:7d:e7:3b:69:51:d4:6c:8d:9f:90:12:66:ab |
| **拇印 (SHA-1)** | F21C12F46CDB6B2E16F09F9419CDFF328437B2D7 |
| **拇印 (SHA-256)** | 13EFB39A2F6654E8C67BD04F4C6D4C90CD6CAB5091BCEDC73787F6B77D3D3FE7 |
| **Pin (SHA-256)** | 980Ionqp3wkYtN9SZVgMzuWQzJta1nfxNPwTem1X0uc= |
| **CRL URL** | http://crl.entrust.net/g2ca.crl |
| **OCSP URL** | http://ocsp.entrust.net |

### <a name="globalsign-extended-validation-ca---sha256---g2"></a>**GlobalSign 拡張検証 CA - SHA256 - G2**

| **件名** | CN=GlobalSign 拡張検証 CA - SHA256 - G2<br>O=GlobalSign nv-sa<br>C=BE |
| --- | --- |
| **発行者** | CN=GlobalSign<br>O=GlobalSign<br>OU=GlobalSign ルート CA - R2 |
| **Serial Number\(シリアル番号\)** | 04:00:00:00:00:01:44:4E:F0:4A:55 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2014 年 2 月 20 日 10:00:00 UTC |
| **有効期間が後でない** | 2021 年 12 月 15 日 08:00:00 UTC |
| **サブジェクト キー識別子** | da:40:77:43:65:1c:f8:fe:a7:e3:f4:64:82:3e:4d:43:13:22:31:02 |
| **機関キー識別子** | keyid:9b:e2:07:57:67:1c:1e:c0:6a:06:de:59:b4:9a:2d:df:dc:19:86:2e |
| **拇印 (SHA-1)** | 65BE102BE26928650E0EF54DC8F4F15AF5F98E8B |
| **拇印 (SHA-256)** | 24F91C0705A0A5338641B365FB0D9D9709B56297CFF1857E73C02C1636D486AA |
| **Pin (SHA-256)** | LvRiGEjRqfzurezaWuj8Wie2gyHMrW5Q06LspMnox7A= |
| **CRL URL** | `http://crl.globalsign.net/root-r2.crl` |
| **OCSP URL** | `http://ocsp.globalsign.com/rootr2` |

### <a name="globalsign-extended-validation-ca---sha256---g3"></a>**GlobalSign 拡張検証 CA - SHA256 - G3**

| **件名** | CN=GlobalSign 拡張検証 CA - SHA256 - G3<br>O=GlobalSign nv-sa<br>C=BE |
| --- | --- |
| **発行者** | CN=GlobalSign<br>O=GlobalSign<br>OU=GlobalSign ルート CA - R3 |
| **Serial Number\(シリアル番号\)** | 48:A4:02:DD:27:92:0D:A2:08:34:9D:D1:99:7B |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2016 年 9 月 21 日 00:00:00 UTC |
| **有効期間が後でない** | 2026 年 9 月 21 日 00:00:00 UTC |
| **サブジェクト キー識別子** | dd:b3:e7:6d:a8:2e:e8:c5:4e:6e:cf:74:e6:75:3c:94:15:ce:e8:1d |
| **機関キー識別子** | keyid:8f:f0:4b:7f:a8:2e:45:24:ae:4d:50:fa:63:9a:8b:de:e2:dd:1b:bc |
| **拇印 (SHA-1)** | 6023192FE7B59D2789130A9FE4094F9B5570D4A2 |
| **拇印 (SHA-256)** | AED5DD9A5339685DFB029F6D89A14335A96512C3CACC52B2994AF8B6B37FA4D2 |
| **Pin (SHA-256)** | 86fLIetopQLDNxFZ0uMI66Xpl1pFgLlHHn9v6kT0i4I= |
| **CRL URL** | http://crl.globalsign.com/root-r3.crl |
| **OCSP URL** | http://ocsp2.globalsign.com/rootr3 |

### <a name="globalsign-organization-validation-ca---sha256---g2-older"></a>**GlobalSign Organization 検証 CA - SHA256 - G2** (古い)

| **件名** | CN=GlobalSign Organization 検証 CA - SHA256 - G2<br>O=GlobalSign nv-sa<br>C=BE |
| --- | --- |
| **発行者** | CN=GlobalSign<br>O=GlobalSign<br>OU=GlobalSign ルート CA - R3 |
| **Serial Number\(シリアル番号\)** | 04:00:00:00:00:01:31:89:C6:44:C9 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2011 年 8 月 2 日 10:00:00 UTC |
| **有効期間が後でない** | 2022 年 8 月 2 日 10:00:00 UTC |
| **サブジェクト キー識別子** | 96:de:61:f1:bd:1c:16:29:53:1c:c0:cc:7d:3b:83:00:40:e6:1a:7c |
| **機関キー識別子** | keyid:8f:f0:4b:7f:a8:2e:45:24:ae:4d:50:fa:63:9a:8b:de:e2:dd:1b:bc |
| **拇印 (SHA-1)** | EF90B2B86F4756EBE7D36FF3015D63523A0076E9 |
| **拇印 (SHA-256)** | 0B339212D7CFF17A2C59E35669B58E77350133750A78DA9404770EDD470DEF76 |
| **Pin (SHA-256)** | IQBnNBEiFuzh+8x6X8XLgh01V9Ic5/V3IRQLNFFc7v4= |
| **CRL URL** | http://crl.globalsign.net/root-r3.crl |
| **OCSP URL** | http://ocsp2.globalsign.com/rootr3 |

### <a name="globalsign-organization-validation-ca---sha256---g2"></a>**GlobalSign Organization 検証 CA - SHA256 - G2**

| **件名** | CN=GlobalSign Organization 検証 CA - SHA256 - G2<br>O=GlobalSign nv-sa<br>C=BE |
| --- | --- |
| **発行者** | CN=GlobalSign ルート CA<br>OU=ルート CA<br>O=GlobalSign nv-sa<br>C=BE |
| **Serial Number\(シリアル番号\)** | 04:00:00:00:00:01:44:4E:F0:42:47 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2014 年 2 月 20 日 10:00:00 UTC |
| **有効期間が後でない** | 2024 年 2 月 20 日 10:00:00 UTC |
| **サブジェクト キー識別子** | 96:de:61:f1:bd:1c:16:29:53:1c:c0:cc:7d:3b:83:00:40:e6:1a:7c |
| **機関キー識別子** | keyid:60:7b:66:1a:45:0d:97:ca:89:50:2f:7d:04:cd:34:a8:ff:fc:fd:4b |
| **拇印 (SHA-1)** | 902EF2DEEB3C5B13EA4C3D5193629309E231AE55 |
| **拇印 (SHA-256)** | 74EF335E5E18788307FB9D89CB704BEC112ABD23487DBFF41C4DED5070F241D9 |
| **Pin (SHA-256)** | IQBnNBEiFuzh+8x6X8XLgh01V9Ic5/V3IRQLNFFc7v4= |
| **CRL URL** | http://crl.globalsign.net/root.crl |
| **OCSP URL** | http://ocsp.globalsign.com/rootr1 |

### <a name="globalsign-organization-validation-ca---sha256---g3"></a>**GlobalSign Organization 検証 CA - SHA256 - G3**

| **件名** | CN=GlobalSign Organization 検証 CA - SHA256 - G3<br>O=GlobalSign nv-sa<br>C=BE |
| --- | --- |
| **発行者** | CN=GlobalSign ルート CA、OU=Root CA、O=GlobalSign nv-sa、C=BE |
| **Serial Number\(シリアル番号\)** | 47:07:B1:01:9A:0C:57:AD:39:B3:E1:7D:A9:F9 |
| **公開キーの長さ** | RSA 2048 ビット |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2015 年 9 月 3 日 (木曜日) 5:00 PM |
| **有効期間は次の値までです** | 2025 年 9 月 3 日 (水曜日) 5:00 PM |
| **サブジェクト キー識別子** | 6886B87D7AD96D496B872F188B15346CD7B47A0E |
| **機関キー識別子** | KeyID:60:7b:66:1a:45:0d:97:ca:89:50:2f:7d:04:cd:34:a8:ff:fc:fd:4b |
| **拇印 (SHA-1)** | 20D1EBAB5A71587B9116E4C74415D1A85B0DDDA5 |
| **拇印 (SHA-256)** | 699D54B7482A5D329331EA0415CC2EDCD60FDA01D19E71D054196BCE0677735C |
| **CRL URL** | http://crl.globalsign.com/root.crl |
| **OCSP URL** | http://ocsp.globalsign.com/rootr1 |

### <a name="globalsign-rsa-ov-ssl-ca-2018"></a>**GlobalSign RSA OV SSL CA 2018**

| **件名** | CN=GlobalSign RSA OV SSL CA 2018<br>O=GlobalSign nv-sa<br>C=BE |
| --- | --- |
| **発行者** | CN=GlobalSign、O=GlobalSign、OU=GlobalSign ルート CA - R3 |
| **Serial Number\(シリアル番号\)** | 01:Enterprise Edition:5F:22:1D:FC:62:3B:D4:33:3A:85:57 |
| **公開キーの長さ** | RSA 2048 ビット |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2018 年 11 月 20 日(火) 16:00 |
| **有効期間は次の値までです** | 2028 年 11 月 20 日 (月曜日) 16:00 |
| **サブジェクト キー識別子** | F8EF7FF2CD7867A8DE6F8F248D88F1870302B3EB |
| **機関キー識別子** | KeyID:8f:f0:4b:7f:a8:2e:45:24:ae:4d:50:fa:63:9a:8b:de:e2:dd:1b:bc |
| **拇印 (SHA-1)** | DFE83023062B997682708B4EAB8E819AFF5D9775 |
| **拇印 (SHA-256)** | B676FFA3179E8812093A1B5EAFEE876AE7A6AAF231078DAD1BFB21CD2893764A |
| **CRL URL** | http://crl.globalsign.com/root-r3.crl |
| **OCSP URL** | http://ocsp2.globalsign.com/rootr3 |

### <a name="lets-encrypt-authority-x3"></a>**Let's Encrypt Authority X3**

| **件名** | CN=Let's Encrypt Authority X3<br>O=Let's Encrypt<br>C=US |
| --- | --- |
| **発行者** | CN=DST ルート CA X3<br>O=Digital Signature Trust Co. |
| **Serial Number\(シリアル番号\)** | 0A:01:41:42:00:00:01:53:85:73:6A:0B:85:EC:A7:08 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2016 年 3 月 17 日 16:40:46 UTC |
| **有効期間が後でない** | 2021 年 3 月 17 日 16:40:46 UTC |
| **サブジェクト キー識別子** | a8:4a:6a:63:04:7d:dd:ba:e6:d1:39:b7:a6:45:65:ef:f3:a8:ec:a1 |
| **機関キー識別子** | keyid:c4:a7:b1:a4:7b:2c:71:fa:db:e1:4b:90:75:ff:c4:15:60:85:89:10 |
| **拇印 (SHA-1)** | E6A3B45B062D509B3382282D196EFE97D5956CCB |
| **拇印 (SHA-256)** | 25847D668EB4F04FDD40B12B6B0740C567DA7D024308EB6C2C96FE41D9DE218D |
| **Pin (SHA-256)** | YLh1dUR9y6Kja30RrAn7JKnbQG/uEtLMkBgFF2Fuihg= |
| **AIA URL** | http://apps.identrust.com/roots/dstrootcax3.p7c |
| **CRL URL** | http://crl.identrust.com/DSTROOTCAX3CRL.crl |
| **OCSP URL** | http://isrg.trustid.ocsp.identrust.com |

### <a name="microsoft-azure-tls-issuing-ca-01"></a>**MICROSOFT AZURE TLS 発行元 CA 01**

| **件名** | CN=Microsoft Azure TLS 発行元 CA 01<br>O=Microsoft Corporation<br>C=US |
| --- | --- |
| **発行者** | CN=DigiCert Global Root G2、OU=www.digicert.com、O=DigiCert Inc、C=US |
| **Serial Number\(シリアル番号\)** | 0A:AF:A6:C5:CA:63:C4:51:41:EA:3B:E1:F7:C7:53:17 |
| **公開キーの長さ** | RSA 4096 ビット |
| **署名アルゴリズム** | sha384RSA |
| **有効期限が前にありません** | 2020 年 7 月 29 日 (水曜日) 5:30 AM |
| **有効期間は次の値までです** | 2024 年 6 月 27 日(木曜日) 16:59 |
| **サブジェクト キー識別子** | 0F205DD7A15795DB92CF2BD0C7C27704CE728076 |
| **機関キー識別子** | KeyID:4e:22:54:20:18:95:e6:e3:6e:e6:0f:fa:fa:b9:12:ed:06:17:8f:39 |
| **拇印 (SHA-1)** | 2F2877C5D778C31E0F29C7E371DF5471BD673173 |
| **拇印 (SHA-256)** | 24C7299864E0A2A6964F551C0E8DF2461532FA8C48E4DBBB6080716691F190E5 |
| **CRL URL** | http://crl3.digicert.com/DigiCertGlobalRootG2.crl http://crl4.digicert.com/DigiCertGlobalRootG2.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="microsoft-azure-tls-issuing-ca-02"></a>**MICROSOFT AZURE TLS 発行元 CA 02**

| **件名** | CN=Microsoft Azure TLS 発行元 CA 02<br>O=Microsoft Corporation<br>C=US |
| --- | --- |
| **発行者** | CN=DigiCert Global Root G2、OU=www.digicert.com、O=DigiCert Inc、C=US |
| **Serial Number\(シリアル番号\)** | 0C:6A:E9:7C:CE:D5:99:83:86:90:A0:0A:9E:A5:32:14 |
| **公開キーの長さ** | RSA 4096 ビット |
| **署名アルゴリズム** | sha384RSA |
| **有効期限が前にありません** | 2020 年 7 月 29 日 (水曜日) 5:30 AM |
| **有効期間は次の値までです** | 2024 年 6 月 27 日(木曜日) 16:59 |
| **サブジェクト キー識別子** | 00AB91FC216226979AA8791B61419060A96267FD |
| **機関キー識別子** | KeyID:4e:22:54:20:18:95:e6:e3:6e:e6:0f:fa:fa:b9:12:ed:06:17:8f:39 |
| **拇印 (SHA-1)** | E7EEA674CA718E3BEFD90858E09F8372AD0AE2AA |
| **拇印 (SHA-256)** | 15A98761EBE011554DA3A46D206B0812CB2EB69AE87AAA11A6DD4CB84ED5142A |
| **CRL URL** | http://crl3.digicert.com/DigiCertGlobalRootG2.crl http://crl4.digicert.com/DigiCertGlobalRootG2.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="microsoft-azure-tls-issuing-ca-05"></a>**MICROSOFT AZURE TLS 発行元 CA 05**

| **件名** | CN=Microsoft Azure TLS 発行元 CA 05<br>O=Microsoft Corporation<br>C=US |
| --- | --- |
| **発行者** | CN=DigiCert Global Root G2、OU=www.digicert.com、O=DigiCert Inc、C=US |
| **Serial Number\(シリアル番号\)** | 0D:7B:ED:E9:7D:82:09:96:7A:52:63:1B:8B:DD:18:BD |
| **公開キーの長さ** | RSA 4096 ビット |
| **署名アルゴリズム** | sha384RSA |
| **有効期限が前にありません** | 2020 年 7 月 29 日 (水曜日) 5:30 AM |
| **有効期間は次の値までです** | 2024 年 6 月 27 日(木曜日) 16:59 |
| **サブジェクト キー識別子** | C7B29C7F1CE3B85AEFE9681AA85D94C126526A68 |
| **機関キー識別子** | KeyID:4e:22:54:20:18:95:e6:e3:6e:e6:0f:fa:fa:b9:12:ed:06:17:8f:39 |
| **拇印 (SHA-1)** | 6C3AF02E7F269AA73AFD0EFF2A88A4A1F04ED1E5 |
| **拇印 (SHA-256)** | D6831BA43607F5AC19778D627531562AF55145F191CAB5EFAFA0E0005442B302 |
| **CRL URL** | http://crl3.digicert.com/DigiCertGlobalRootG2.crl http://crl4.digicert.com/DigiCertGlobalRootG2.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="microsoft-azure-tls-issuing-ca-06"></a>**MICROSOFT AZURE TLS 発行元 CA 06**

| **件名** | CN=Microsoft Azure TLS 発行元 CA 06<br>O=Microsoft Corporation<br>C=US |
| --- | --- |
| **発行者** | CN=DigiCert Global Root G2、OU=www.digicert.com、O=DigiCert Inc、C=US |
| **Serial Number\(シリアル番号\)** | 02:E7:91:71:FB:80:21:E9:3F:E2:D9:83:83:4C:50:C0 |
| **公開キーの長さ** | RSA 4096 ビット |
| **署名アルゴリズム** | sha384RSA |
| **有効期限が前にありません** | 2020 年 7 月 29 日 (水曜日) 5:30 AM |
| **有効期間は次の値までです** | 2024 年 6 月 27 日(木曜日) 16:59 |
| **サブジェクト キー識別子** | D5C1673AC2A39DF477525B59123829E65568BBA5 |
| **機関キー識別子** | KeyID:4e:22:54:20:18:95:e6:e3:6e:e6:0f:fa:fa:b9:12:ed:06:17:8f:39 |
| **拇印 (SHA-1)** | 30E01761AB97E59A06B41EF20AF6F2DE7EF4F7B0 |
| **拇印 (SHA-256)** | 48FF8B49468C752304B48BFE818758987DEF6582E5F09B921F4B60BB3D6A8DD |
| **CRL URL** | http://crl3.digicert.com/DigiCertGlobalRootG2.crl http://crl4.digicert.com/DigiCertGlobalRootG2.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="microsoft-it-tls-ca-1"></a>**Microsoft IT TLS CA 1**

| **件名** | CN=Microsoft IT TLS CA 1<br>OU=Microsoft IT<br>O=Microsoft Corporation<br>L=Redmond<br>S=Washington<br>C=US |
| --- | --- |
| **発行者** | CN=Baltimore CyberTrust Root<br>OU=CyberTrust<br>O=Baltimore<br>C=IE |
| **Serial Number\(シリアル番号\)** | 08:B8:7A:50:1B:BE:9C:DA:2D:16:4D:3E:39:51:BF:55 |
| **公開キーの長さ** | RSA 4096 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2016 年 5 月 20 日 12:51:28 UTC |
| **有効期間が後でない** | 2024 年 5 月 20 日 12:51:28 UTC |
| **サブジェクト キー識別子** | 58:88:9f:d6:dc:9c:48:22:b7:14:3e:ff:84:88:e8:e6:85:ff:fa:7d |
| **機関キー識別子** | keyid:e5:9d:59:30:82:47:58:cc:ac:fa:08:54:36:86:7b:3a:b5:04:4d:f0 |
| **拇印 (SHA-1)** | 417E225037FBFAA4F95761D5AE729E1AEA7E3A42 |
| **拇印 (SHA-256)** | 4FF404F02E2CD00188F15D1C00F4B6D1E38B5A395CF85314EAEBA855B6A64B75 |
| **Pin (SHA-256)** | xjXxgkOYlag7jCtR5DreZm9b61iaIhd+J3+b2LiybIw= |
| **CRL URL** | http://crl3.digicert.com/Omniroot2025.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="microsoft-it-tls-ca-2"></a>**Microsoft IT TLS CA 2**

| **件名** | CN=Microsoft IT TLS CA 2<br>OU=Microsoft IT<br>O=Microsoft Corporation<br>L=Redmond<br>S=Washington<br>C=US |
| --- | --- |
| **発行者** | CN=Baltimore CyberTrust Root<br>OU=CyberTrust<br>O=Baltimore<br>C=IE |
| **Serial Number\(シリアル番号\)** | 0F:2C:10:C9:5B:06:C0:93:7F:B8:D4:49:F8:3E:85:69 |
| **公開キーの長さ** | RSA 4096 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2016 年 5 月 20 日 12:51:57 UTC |
| **有効期間が後でない** | 2024 年 5 月 20 日 12:51:57 UTC |
| **サブジェクト キー識別子** | 91:9e:3b:44:6c:3d:57:9c:42:77:2a:34:d7:4f:d1:cc:4a:97:2c:da |
| **機関キー識別子** | keyid:e5:9d:59:30:82:47:58:cc:ac:fa:08:54:36:86:7b:3a:b5:04:4d:f0 |
| **拇印 (SHA-1)** | 54D9D20239080C32316ED9FF980A48988F4ADF2D |
| **拇印 (SHA-256)** | 4E107C981B42ACBE41C01067E16D44DB64814D4193E572317EA04B87C79C475F |
| **Pin (SHA-256)** | wBdPad95AU7OgLRs0FU/E6ILO1MSCM84kJ9y0H+TT7s= |
| **CRL URL** | http://crl3.digicert.com/Omniroot2025.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="microsoft-it-tls-ca-4"></a>**Microsoft IT TLS CA 4**

| **件名** | CN=Microsoft IT TLS CA 4<br>OU=Microsoft IT<br>O=Microsoft Corporation<br>L=Redmond<br>S=Washington<br>C=US |
| --- | --- |
| **発行者** | CN=Baltimore CyberTrust Root<br>OU=CyberTrust<br>O=Baltimore<br>C=IE |
| **Serial Number\(シリアル番号\)** | 0B:6A:B3:B0:3E:B1:A9:F6:C4:60:92:6A:A8:CD:FE:B3 |
| **公開キーの長さ** | RSA 4096 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2016 年 5 月 20 日 12:52:38 UTC |
| **有効期間が後でない** | 2024 年 5 月 20 日 12:52:38 UTC |
| **サブジェクト キー識別子** | 7a:7b:8c:c1:cf:e7:a0:ca:1c:d4:6b:fa:fb:e1:33:c3:0f:1a:a2:9d |
| **機関キー識別子** | keyid:e5:9d:59:30:82:47:58:cc:ac:fa:08:54:36:86:7b:3a:b5:04:4d:f0 |
| **拇印 (SHA-1)** | 8A38755D0996823FE8FA3116A277CE446EAC4E99 |
| **拇印 (SHA-256)** | 5FFAC43E0DDC5B4AF2B696F6BC4DB7E91DF314BB8FE0D0713A0B1A7AD2A68FAC |
| **Pin (SHA-256)** | wUY9EOTJjS7Aj4fDVCu/KeE++mV7FgIcbn4WhMz1I2k= |
| **CRL URL** | http://crl3.digicert.com/Omniroot2025.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="microsoft-it-tls-ca-5"></a>**Microsoft IT TLS CA 5**

| **件名** | CN=Microsoft IT TLS CA 5<br>OU=Microsoft IT<br>O=Microsoft Corporation<br>L=Redmond<br>S=Washington<br>C=US |
| --- | --- |
| **発行者** | CN=Baltimore CyberTrust Root<br>OU=CyberTrust<br>O=Baltimore<br>C=IE |
| **Serial Number\(シリアル番号\)** | 08:88:CD:52:5F:19:24:44:4D:14:A5:82:91:DE:B9:52 |
| **公開キーの長さ** | RSA 4096 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2016 年 5 月 20 日 12:53:03 UTC |
| **有効期間が後でない** | 2024 年 5 月 20 日 12:53:03 UTC |
| **サブジェクト キー識別子** | 08:fe:25:9f:74:ea:87:04:c2:bc:bb:8e:a8:38:5f:33:c6:d1:6c:65 |
| **機関キー識別子** | keyid:e5:9d:59:30:82:47:58:cc:ac:fa:08:54:36:86:7b:3a:b5:04:4d:f0 |
| **拇印 (SHA-1)** | AD898AC73DF333EB60AC1F5FC6C4B2219DDB79B7 |
| **拇印 (SHA-256)** | F0EE5914ED94C7252D058B4E39808AEE6FA8F62CF0974FB7D6D2A9DF16E3A87F |
| **Pin (SHA-256)** | RCbqB+W8nctrlgzTeP4O6VjfqwdxIgI79eBpnBKRr32gc= |
| **CRL URL** | http://crl3.digicert.com/Omniroot2025.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="microsoft-rsa-tls-ca-01"></a>**Microsoft RSA TLS CA 01**

| **件名** | CN=Microsoft RSA TLS CA 01<br>O=Microsoft Corporation<br>C=US |
| --- | --- |
| **発行者** | CN=Baltimore CyberTrust Root、OU=CyberTrust、O=Baltimore、C=IE |
| **Serial Number\(シリアル番号\)** | 0F:14:96:5F:20:20:69:99:4F:D5:C7:AC:78:89:41:E2 |
| **公開キーの長さ** | RSA 4096 ビット |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2020 年 7 月 21 日(火) 16:00 |
| **有効期間は次の値までです** | 2024 年 10 月 8 日(火) 12:00 |
| **サブジェクト キー識別子** | B5760C3011CEC792424D4CC75C2CC8A90CE80B64 |
| **機関キー識別子** | KeyID:e5:9d:59:30:82:47:58:cc:ac:fa:08:54:36:86:7b:3a:b5:04:4d:f0 |
| **拇印 (SHA-1)** | 703D7A8F0EBF55AAA59F98EAF4A206004EB2516A |
| **拇印 (SHA-256)** | 04EEEA8E50B4775B3C24797262917EE5002EC4C75B56CDF3EE1C18CFCA5BA52 |
| **CRL URL** | http://crl3.digicert.com/Omniroot2025.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="microsoft-rsa-tls-ca-02"></a>**Microsoft RSA TLS CA 02**

| **件名** | CN=Microsoft RSA TLS CA 02<br>O=Microsoft Corporation<br>C=US |
| --- | --- |
| **発行者** | CN=Baltimore CyberTrust Root、OU=CyberTrust、O=Baltimore、C=IE |
| **Serial Number\(シリアル番号\)** | 0F:A7:47:22:C5:3D:88:C8:0F:58:9E:FB:1F:9D:4A:3A |
| **公開キーの長さ** | RSA 4096 ビット |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2020 年 7 月 21 日(火) 16:00 |
| **有効期間は次の値までです** | 2024 年 10 月 8 日(火) 12:00 |
| **サブジェクト キー識別子** | FF2F7FE106F438F32DED258D98C2FE0EF66CFCFA |
| **機関キー識別子** | KeyID:e5:9d:59:30:82:47:58:cc:ac:fa:08:54:36:86:7b:3a:b5:04:4d:f0 |
| **拇印 (SHA-1)** | B0C2D2D13CDD56CDAA6AB6E2C04440BE4A429C75 |
| **拇印 (SHA-256)** | 05E4005DB0C382F3BD66B47729E9011577601BF6F7B287E9A52CED710D258346 |
| **CRL URL** | http://crl3.digicert.com/Omniroot2025.crl |
| **OCSP URL** | http://ocsp.digicert.com |

### <a name="symantec-class-3-ev-ssl-ca---g3"></a>**Symantec Class 3 EV SSL CA - G3**

| **件名** | CN=Symantec クラス 3 EV SSL CA - G3<br>OU=Symantec Trust Network<br>O=Symantec Corporation<br>C=US |
| --- | --- |
| **発行者** | CN=VeriSign クラス 3 パブリック プライマリ証明機関 - G5<br>OU=&quot;(c) 2006 VeriSign, Inc. - 承認された使用のみ&quot;<br>OU=VeriSign トラスト ネットワーク<br>O=&quot;VeriSign, Inc.&quot;<br>C=US |
| **サブジェクトの別名** | ディレクトリ アドレス: CN=SymantecPKI-1-533 |
| **Serial Number\(シリアル番号\)** | 7E:E1:4A:6F:6F:EF:F2:D3:7F:3F:AD:65:4D:3A:DA:B4 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2013 年 10 月 31 日 00:00:00 UTC |
| **有効期間が後でない** | 2023 年 10 月 30 日 23:59:59 UTC |
| **サブジェクト キー識別子** | 01:59:ab:e7:dd:3a:0b:59:a6:64:63:d6:cf:20:07:57:d5:91:e7:6a |
| **機関キー識別子** | keyid:7f:d3:65:a7:c2:dd:ec:bb:f0:30:09:f3:43:39:fa:02:af:33:31:33 |
| **拇印 (SHA-1)** | E3FC0AD84F2F5A83ED6F86F567F8B14B40DCBF12 |
| **拇印 (SHA-256)** | 9E6BC5F9ECC52460E8EDC02C644D1BE1CB9F2316F41DAF3B616A0B2058294B31 |
| **Pin (SHA-256)** | gMxWOrX4PMQesK9qFNbYBxjBfjUvlkn/vN1n+L9lE5E= |
| **CRL URL** | http://s1.symcb.com/pca3-g5.crl |
| **OCSP URL** | http://s2.symcb.com |

### <a name="symantec-class-3-secure-server-ca---g4"></a>**Symantec Class 3 Secure Server CA - G4**

| **件名** | CN=Symantec クラス 3 Secure Server CA - G4<br>OU=Symantec Trust Network<br>O=Symantec Corporation<br>C=US |
| --- | --- |
| **発行者** | CN=VeriSign クラス 3 パブリック プライマリ証明機関 - G5<br>OU=&quot;(c) 2006 VeriSign, Inc. - 承認された使用のみ&quot;<br>OU=VeriSign トラスト ネットワーク<br>O=&quot;VeriSign, Inc.&quot;<br>C=US |
| **サブジェクトの別名** | ディレクトリ アドレス: CN=SymantecPKI-1-534 |
| **Serial Number\(シリアル番号\)** | 51:3F:B9:74:38:70:B7:34:40:41:8D:30:93:06:99:FF |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2013 年 10 月 31 日 00:00:00 UTC |
| **有効期間が後でない** | 2023 年 10 月 30 日 23:59:59 UTC |
| **サブジェクト キー識別子** | 5f:60:cf:61:90:55:df:84:43:14:8a:60:2a:b2:f5:7a:f4:43:18:ef |
| **機関キー識別子** | keyid:7f:d3:65:a7:c2:dd:ec:bb:f0:30:09:f3:43:39:fa:02:af:33:31:33 |
| **拇印 (SHA-1)** | FF67367C5CD4DE4AE18BCCE1D70FDABD7C866135 |
| **拇印 (SHA-256)** | EAE72EB454BF6C3977EBD289E970B2F5282949190093D0D0D26F98D0F0D6A9CF17 |
| **Pin (SHA-256)** | 9n0izTnSRF+ W4W4JTq51avSXkWhQB8duS2bxVLfzXsY= |
| **CRL URL** | http://s1.symcb.com/pca3-g5.crl |
| **OCSP URL** | http://s2.symcb.com |

### <a name="thawte-sha256-ssl-ca"></a>**thawte SHA256 SSL CA**

| **件名** | CN=thawte SHA256 SSL CA<br>O=&quot;Thawte, Inc.&quot;<br>C=US |
| --- | --- |
| **発行者** | CN=thawte プライマリ ルート CA - G3<br>OU=&quot;(c) 2008 Thawte, Inc. - 承認された使用のみ&quot;<br>OU=Certification Services Division<br>O=&quot;Thawte, Inc.&quot;<br>C=US |
| **サブジェクトの別名** | ディレクトリ アドレス: CN=VeriSignMPKI-2-415 |
| **Serial Number\(シリアル番号\)** | 36:34:9E:18:C9:9C:26:69:B6:56:2E:6C:E5:AD:71:32 |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2013 年 5 月 23 日 00:00:00 UTC |
| **有効期間が後でない** | 2023 年 5 月 22 日 23:59:59 UTC |
| **サブジェクト キー識別子** | 2b:9a:35:ae:01:18:38:30:e1:70:7a:05:e0:11:76:a3:ce:bd:90:14 |
| **機関キー識別子** | keyid:ad:6c:aa:94:60:9c:ed:e4:ff:fa:3e:0a:74:2b:63:03:f7:b6:59:bf |
| **拇印 (SHA-1)** | 67D147D5DAB7F28D663CA5B7A9568F087427B9F7 |
| **拇印 (SHA-256)** | 3F3AF9C9CC2C7599EF8F6DD7CA516CFC1797D7D12002254F3BFD0D4D0FE9DE86 |
| **Pin (SHA-256)** | /36ymPAVaUj3QDyB1lUkVf9GqJNug0R8JJPDN6348p8= |
| **CRL URL** | http://crl.thawte.com/ThawtePCA-G3.crl |
| **OCSP URL** | http://ocsp.thawte.com |

### <a name="verizon-akamai-sureserver-ca-g14-sha2"></a>**Verizon Akamai SureServer CA G14-SHA2**

| **件名** | CN=Verizon Akamai SureServer CA G14-SHA2<br>OU=Cybertrust<br>O=Verizon Enterprise ソリューション<br>L=アムステルダム<br>C=NL |
| --- | --- |
| **発行者** | CN=Baltimore CyberTrust Root<br>OU=CyberTrust<br>O=Baltimore<br>C=IE |
| **Serial Number\(シリアル番号\)** | 07:27:A4:6B |
| **公開キーの長さ** | RSA 2048 ビット (e 65537) |
| **署名アルゴリズム** | sha256RSA |
| **有効期限が前にありません** | 2014 年 4 月 2 日 14:36:10 UTC |
| **有効期間が後でない** | 2021 年 4 月 2 日 14:35:52 UTC |
| **サブジェクト キー識別子** | f8:bd:af:73:77:c6:c7:1b:f9:4b:4d:11:a7:d1:33:af:af:72:11 |
| **機関キー識別子** | keyid:e5:9d:59:30:82:47:58:cc:ac:fa:08:54:36:86:7b:3a:b5:04:4d:f0 |
| **拇印 (SHA-1)** | 6AD2B04E2196E48BF685752890E811CD2ED60606 |
| **拇印 (SHA-256)** | 7373D219B42547E41BCB752BCBE93F592FF6F99C340CE57B73D38C3EC0BA98 |
| **Pin (SHA-256)** | 8XFPrRr4VxmEIYKUu35QtR3oGbduX1AlrBzaBUHgp7c= |
| **AIA URL** | `https://cacert.omniroot.com/baltimoreroot.crt`<br>`https://cacert.omniroot.com/baltimoreroot.der` |
| **CRL URL** | http://cdp1.public-trust.com/CRL/Omniroot2025.crl |
| **OCSP URL** | http://ocsp.omniroot.com/baltimoreroot |

## <a name="additional-certificate-paths"></a>**追加の証明書パス**

次の一覧には、上記に含まれていないレガシ証明書が含まれており、時間の経過と共に上記の一覧とマージされます。

evsecure-aia.verisign.com<br>
sa.symcb.com<br>
sd.symcb.com<br>
\*.omniroot.com<br>
\*.verisign.com<br>
\*.symcb.com<br>
\*.symcd.com<br>
\*.verisign.net<br>
\*.geotrust.com<br>
\*.entrust.net<br>
\*.public-trust.com<br>
EVIntl-ocsp.verisign.com<br>
EVSecure-ocsp.verisign.com<br>
isrg.trustid.ocsp.identrust.com<br>
ocsp.digicert.com<br>
ocsp.entrust.net<br>
ocsp.globalsign.com/ExtendedSSLSHA256CACross<br>
ocsp.globalsign.com/rootr1<br>
ocsp.globalsign.com/rootr2<br>
ocsp2.globalsign.com/rootr3<br>
ocsp.int-x3.letsencrypt.org/<br>
ocsp.msocsp.com<br>
ocsp.omniroot.com/baltimoreroot<br>
ocsp2.globalsign.com/gsextendvalsha2g3r3<br>
ocsp2.globalsign.com/gsorganizationvalsha2g2<br>
ocsp2.globalsign.com/gsorganizationvalsha2g3<br>
ocsp2.globalsign.com/rootr3<br>
ocspx.digicert.com<br>
s2.symcb.com<br>
sr.symcd.com<br>
su.symcd.com<br>
vassg142.ocsp.omniroot.com<br>
cdp1.public-trust.com/CRL/Omniroot2025.crl<br>
crl.entrust.net/2048ca.crl<br>
crl.entrust.net/g2ca.crl<br>
crl.entrust.net/level1k.crl<br>
crl.entrust.net/rootca1.crl<br>
crl.globalsign.com/gs/gsextendvalsha2g3r3.crl<br>
crl.globalsign.com/gs/gsorganizationvalsha2g2.crl<br>
crl.globalsign.com/gsorganizationvalsha2g3.crl<br>
crl.globalsign.com/root.crl<br>
crl.globalsign.net/root-r2.crl<br>
crl.globalsign.com/root-r3.crl<br>
crl.globalsign.net/root.crl<br>
crl.identrust.com/DSTROOTCAX3CRL.crl<br>
crl.microsoft.com/pki/mscorp/crl/msitwww1.crl<br>
crl.microsoft.com/pki/mscorp/crl/msitwww2.crl<br>
crl3.digicert.com/DigiCertCloudServicesCA-1-g1.crl<br>
crl3.digicert.com/DigiCertGlobalRootCA.crl<br>
crl3.digicert.com/sha2-ev-server-g1.crl<br>
crl3.digicert.com/sha2-ha-server-g5.crl<br>
crl3.digicert.com/ssca-sha2-g5.crl<br>
crl4.digicert.com/DigiCertCloudServicesCA-1-g1.crl<br>
crl4.digicert.com/DigiCertGlobalRootCA.crl<br>
crl4.digicert.com/DigiCertHighAssuranceEVRootCA.crl<br>
crl4.digicert.com/sha2-ev-server-g1.crl<br>
crl4.digicert.com/sha2-ha-server-g5.crl<br>
crl4.digicert.com/ssca-sha2-g5.crl<br>
EVIntl-crl.verisign.com/EVIntl2006.crl<br>
EVSecure-crl.verisign.com/pca3-g5.crl<br>
mscrl.microsoft.com/pki/mscorp/crl/msitwww1.crl<br>
mscrl.microsoft.com/pki/mscorp/crl/msitwww2.crl<br>
s1.symcb.com/pca3-g5.crl<br>
sr.symcb.com/sr.crl<br>
su.symcb.com/su.crl<br>
vassg142.crl.omniroot.com/vassg142.crl<br>
aia.entrust.net/l1k-chain256.cer<br>
apps.identrust.com/roots/dstrootcax3.p7c<br>
<https://cacert.a.omniroot.com/vassg142.crt><br>
<https://cacert.a.omniroot.com/vassg142.der><br>
https://cacert.omniroot.com/baltimoreroot.crt<br>
https://cacert.omniroot.com/baltimoreroot.der<br>
cacerts.digicert.com/DigiCertCloudServicesCA-1.crt<br>
cacerts.digicert.com/DigiCertSHA2ExtendedValidationServerCA.crt<br>
cacerts.digicert.com/DigiCertSHA2HighAssuranceServerCA.crt<br>
cacerts.digicert.com/DigiCertSHA2SecureServerCA.crt<br>
cert.int-x3.letsencrypt.org/<br>
EVIntl-aia.verisign.com/EVIntl2006.cer<br>
secure.globalsign.com/cacert/gsextendvalsha2g2r2.crt<br>
secure.globalsign.com/cacert/gsextendvalsha2g3r3.crt<br>
secure.globalsign.com/cacert/gsorganizationvalsha2g2r1.crt<br>
secure.globalsign.com/cacert/gsorganizationvalsha2g3.crt<br>
sr.symcb.com/sr.crt<br>
su.symcb.com/su.crt<br>
<https://www.digicert.com/CACerts/DigiCertGlobalRootCA.crt><br>
<https://www.digicert.com/CACerts/DigiCertHighAssuranceEVRootCA.crt><br>
<https://www.microsoft.com/pki/mscorp/msitwww1.crt><br>
<https://www.microsoft.com/pki/mscorp/msitwww2.crt><br>
