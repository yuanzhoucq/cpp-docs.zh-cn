---
title: "OLE DB 应用程序中的资源池 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供程序, 资源池"
  - "OLE DB 服务 [OLE DB], 资源池"
  - "OLE DB, 资源池"
  - "资源池 [OLE DB], 服务"
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 应用程序中的资源池
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要在应用程序中利用池，必须确保通过 **IDataInitialize** 或 **IDBPromptInitialize** 获得数据源来调用 OLE DB 服务。  如果直接使用 `CoCreateInstance` 基于提供程序的 CLSID 调用提供程序，将不调用任何 OLE DB 服务。  
  
 只要保持对 **IDataInitialize** 或 **IDBPromptInitialize** 的引用，或者只要有正在使用的连接，OLE DB 服务就会维护被连接数据源的池。  在 COM\+ 1.0 服务或 Internet 信息服务 \(IIS\) 环境中，同样自动维护池。  如果应用程序将在 COM\+ 1.0 服务或 IIS 环境的外部利用池，则应该保持对 **IDataInitialize** 或 **IDBPromptInitialize** 的引用，或者至少保持一个连接。  若要确保当上一连接被应用程序释放时池不被销毁，请在应用程序的生存期内保持引用或者保持连接。  
  
 OLE DB 服务标识将在调用 `Initialize` 时从中提取出连接的池。  从池中提取出连接后，该连接无法移到其他的池。  因此，在应用程序中避免将会更改初始化信息的操作，如在调用 `Initialize` 之前为提供程序特定的接口调用 `UnInitialize` 或调用 `QueryInterface`。  另外，用 **DBPROMPT\_NOPROMPT** 以外的提示值建立的连接不存储在池中。  不过，从通过提示建立的连接中检索的初始化字符串可用于建立与相同数据源的附加池连接。  
  
 一些提供程序必须为每个会话建立单独的连接。  如果存在分布式事务，这些附加连接必须在其中分开登记。  OLE DB 服务对每个数据源都缓存和重用一个会话，但是如果应用程序从单个数据源一次请求一个以上的会话，则提供程序可能最终建立附加连接和进行不存储在池中的附加事务登记。  实际上在池环境中为每个会话创建单独的数据源比从一个数据源创建多个会话更有效。  
  
 最后，因为 ADO 自动利用 OLE DB 服务，所以可以用 ADO 建立连接，而池与登记将自动发生。  
  
## 请参阅  
 [OLE DB 资源池和服务](../../data/oledb/ole-db-resource-pooling-and-services.md)