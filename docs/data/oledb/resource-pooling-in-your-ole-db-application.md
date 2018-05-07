---
title: OLE DB 应用程序中的资源池 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ece7ce128251f66360566c9b1965466352c4e493
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="resource-pooling-in-your-ole-db-application"></a>OLE DB 应用程序中的资源池
若要充分利用你的应用程序中的池，你必须确保 OLE DB 服务都通过获取数据源通过调用**IDataInitialize**或**IDBPromptInitialize**。 如果直接使用`CoCreateInstance`调用提供程序基于提供程序的 CLSID，调用任何 OLE DB 服务。  
  
 OLE DB 服务维护的前提下尽可能的引用的已连接的数据源的池**IDataInitialize**或**IDBPromptInitialize**持有或只要没有中使用的连接。 在 COM + 1.0 服务或 Internet Information Services (IIS) 环境中，池将还自动维护。 如果你的应用程序充分利用环境外的 COM + 1.0 服务或 IIS 池，则应该保留对引用**IDataInitialize**或**IDBPromptInitialize**或保存到至少一个连接。 若要确保，池中不被销毁最后一次连接发布应用程序时，保留引用，或保存你的应用程序的生存期内连接。  
  
 OLE DB 服务标识在时间从其提取出连接池，`Initialize`调用。 从池中取出连接后，则它不能移动到不同的池。 因此，避免执行更改初始化信息，例如，调用应用程序中的内容`UnInitialize`或调用`QueryInterface`之前调用特定于提供程序接口`Initialize`。 此外，而不使用提示值建立的连接**DBPROMPT_NOPROMPT**未存入池中。 但是，从通过提示建立的连接检索的初始化字符串可以用于建立到同一数据源的其他已入池的连接。  
  
 某些提供程序必须进行单独为每个会话的连接。 如果存在，对这些额外的连接必须单独登记的分布式事务。 OLE DB 服务缓存和重用单个会话每个数据源，但如果应用程序请求从单个数据源的多个会话一次，则提供程序可能最终建立其他连接和进行其他事务登记的不建立池连接。 它会在比单个数据源中创建多个会话的共用环境中创建单独的数据源的每个会话实际上可以提供更高效。  
  
 最后，因为 ADO 自动将使用 OLE DB 服务，你可以使用 ADO 建立的连接和池和登记操作自动发生。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 资源池和服务](../../data/oledb/ole-db-resource-pooling-and-services.md)