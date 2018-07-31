---
title: OLE DB 应用程序中的资源池 |Microsoft Docs
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
ms.openlocfilehash: 4798b4bac8cc6f94e5199502a926eb084cc7534a
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340236"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>OLE DB 应用程序中的资源池
若要充分利用你的应用程序中的池，你必须确保通过获取数据源通过调用 OLE DB 服务`IDataInitialize`或`IDBPromptInitialize`。 如果直接使用`CoCreateInstance`调用提供程序基于提供程序的 CLSID，任何 OLE DB 服务进行调用。  
  
 OLE DB 服务维护池连接的数据源的引用，只要`IDataInitialize`或`IDBPromptInitialize`持有或只要正在使用的连接。 COM + 1.0 服务或 Internet Information Services (IIS) 环境中，池将还自动维护。 如果你的应用程序利用的 COM + 1.0 服务或 IIS 环境外部池，则应保留的引用`IDataInitialize`或`IDBPromptInitialize`或保存到至少一个连接上。 若要确保，池中不被损坏，最后一次连接发布的应用程序，保留引用，或将你的应用程序的生存期内连接保存。  
  
 OLE DB 服务标识时从中绘制连接池的`Initialize`调用。 从池中提取连接后，它不能移动到不同的池。 因此，避免执行更改初始化信息，例如，调用应用程序中的操作`UnInitialize`或调用`QueryInterface`特定于提供程序的接口，然后再调用`Initialize`。 此外，使用 DBPROMPT_NOPROMPT 以外的提示值已建立的连接不入池。 但是，从通过提示建立的连接检索的初始化字符串可用于建立其他连接池的连接相同的数据源。  
  
 某些提供程序必须进行单独为每个会话的连接。 如果存在，对这些额外的连接必须单独登记分布式事务。 OLE DB 服务缓存并重新使用每个数据源的单个会话，但如果应用程序请求单个数据源中的多个会话一次，则提供程序可能会最终建立其他连接和进行的其他事务登记不建立池连接。 它将在比单个数据源中创建多个会话共用的环境中创建的每个会话的单独的数据源实际上可以提供更有效。  
  
 最后，因为 ADO 自动将使用的 OLE DB services，则可以使用 ADO 建立的连接和池和登记会自动发生。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 资源池和服务](../../data/oledb/ole-db-resource-pooling-and-services.md)