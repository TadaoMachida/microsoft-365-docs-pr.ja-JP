---
title: 高度なハンティング スキーマの DeviceNetworkInfo テーブル
description: 高度なハンティング スキーマの DeviceNetworkInfo テーブルでネットワーク構成情報について説明します
keywords: 高度な捜索, 脅威の捜索, サイバー脅威の捜索, Microsoft 365 Defender, microsoft 365, m365, 検索, クエリ, テレメトリ, スキーマ参照, kusto, テーブル, 列, データ型, 説明, machinenetworkinfo, DeviceNetworkInfo, デバイス, マシン, mac, IP, アダプター, DNS, DHCP, ゲートウェイ, トンネル
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 86c087c8a8cdfa80904612625c08ec37ca6813ca
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2021
ms.locfileid: "61531125"
---
# <a name="devicenetworkinfo"></a>DeviceNetworkInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**適用対象:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint



`DeviceNetworkInfo` [高度なハンティング](advanced-hunting-overview.md) スキーマの表には、ネットワーク アダプター、IP と MAC アドレス、接続されたネットワークまたはドメインなど、コンピューターのネットワーク構成に関する情報が含まれています。 このテーブルの情報を返すクエリを作成するには、このリファレンスを使用します。

高度な捜索スキーマのその他のテーブルの詳細については、「[高度な捜索のリファレンス](advanced-hunting-schema-tables.md)」 を参照してください。

| 列名 | データ型 | 説明 |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | イベントが記録された日付と時刻 |
| `DeviceId` | `string` | コンピューターの一意識別子 |
| `DeviceName` | `string` | コンピューターの完全修飾ドメイン名 (FQDN) |
| `NetworkAdapterName` | `string` | ネットワーク アダプターの名前 |
| `MacAddress` | `string` | ネットワーク アダプターの MAC アドレス |
| `NetworkAdapterType` | `string` | ネットワーク アダプターの種類。 使用可能な値については、 [この列挙体を参照してください。](/dotnet/api/system.net.networkinformation.networkinterfacetype) |
| `NetworkAdapterStatus` | `string` | ネットワーク アダプターの運用状態。 使用可能な値については、 [この列挙体を参照してください。](/dotnet/api/system.net.networkinformation.operationalstatus) |
| `TunnelType` | `string` | トンネリング プロトコル(インターフェイスがこの目的で使用されている場合は、たとえば 6to4、Teredo、ISATAP、PPTP、SSTP、SSH など) |
| `ConnectedNetworks` | `string` | アダプターが接続されているネットワーク。 各 JSON 配列には、ネットワーク名、カテゴリ (パブリック、プライベート、ドメイン)、説明、およびインターネットにパブリックに接続されているかどうかを示すフラグが含まれています。 |
| `DnsAddresses` | `string` | JSON 配列形式の DNS サーバー アドレス |
| `IPv4Dhcp` | `string` | DHCP サーバーの IPv4 アドレス |
| `IPv6Dhcp` | `string` | DHCP サーバーの IPv6 アドレス |
| `DefaultGateways` | `string` | JSON 配列形式の既定のゲートウェイ アドレス |
| `IPAddresses` | `string` | アダプターに割り当てられたすべての IP アドレスと、それぞれのサブネット プレフィックスと IP アドレス空間 (パブリック、プライベート、リンクローカルなど) を含む JSON 配列 |
| `ReportId` | `long` | 繰り返しカウンターに基づくイベント識別子。 一意のイベントを識別するには、この列を DeviceName 列と Timestamp 列と組み合わせて使用する必要があります。 |

## <a name="related-topics"></a>関連項目
- [高度な追求の概要](advanced-hunting-overview.md)
- [クエリ言語の説明](advanced-hunting-query-language.md)
- [共有クエリを使用する](advanced-hunting-shared-queries.md)
- [デバイス、メール、アプリ、ID 全体で探す](advanced-hunting-query-emails-devices.md)
- [スキーマを理解する](advanced-hunting-schema-tables.md)
- [クエリのベスト プラクティスを適用する](advanced-hunting-best-practices.md)