---
title: OLE DB 应用程序中的资源池
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
ms.openlocfilehash: 3604f6eaaf0f34a0ff7e54826923c2aa92eef4a2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209754"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>OLE DB 应用程序中的资源池

若要在应用程序中利用池，必须确保通过 `IDataInitialize` 或 `IDBPromptInitialize`获取数据源来调用 OLE DB 服务。 如果直接使用 `CoCreateInstance` 基于提供程序的 CLSID 来调用提供程序，则不会调用任何 OLE DB 服务。

OLE DB 服务可维护已连接数据源的池，只要已持有 `IDataInitialize` 或 `IDBPromptInitialize`，或者只要正在使用连接就可以。 池还会在 COM + 1.0 服务或 Internet Information Services （IIS）环境中自动维护。 如果你的应用程序利用 COM + 1.0 服务或 IIS 环境的外部池，则应保留对 `IDataInitialize` 或 `IDBPromptInitialize` 的引用或至少保留一个连接。 若要确保当应用程序释放最后一个连接时池不会被销毁，请在应用程序的生存期内保留该引用或保持到连接。

OLE DB 服务标识调用 `Initialize` 时从中绘制连接的池。 从池中提取连接后，不能将其移动到不同的池。 因此，请避免在应用程序中执行更改初始化信息的操作，例如，在调用 `Initialize`之前调用 `UnInitialize` 或调用特定于提供程序的接口 `QueryInterface`。 此外，使用 DBPROMPT_NOPROMPT 以外的提示值建立的连接不会被共用。 但是，从通过提示建立的连接中检索的初始化字符串可用于建立与同一数据源的其他共用连接。

某些提供程序必须为每个会话建立单独的连接。 这些附加连接必须单独登记在分布式事务中（如果存在）。 OLE DB 服务缓存并重用每个数据源一个会话，但如果应用程序每次从单个数据源请求多个会话，则该访问接口可能最终会进行附加连接并执行其他事务登记，未在池中。 在共用环境中为每个会话创建单独的数据源比从单个数据源创建多个会话更为有效。

最后，由于 ADO 自动使用 OLE DB 服务，因此您可以使用 ADO 建立连接，而池和登记会自动进行。

## <a name="see-also"></a>另请参阅

[OLE DB 资源池和服务](../../data/oledb/ole-db-resource-pooling-and-services.md)
