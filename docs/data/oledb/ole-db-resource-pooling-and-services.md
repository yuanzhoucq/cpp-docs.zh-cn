---
title: "OLE DB 资源池和服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e2b3500c90455c7f180f16eae3c56433f57d0492
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ole-db-resource-pooling-and-services"></a>OLE DB 资源池和服务
若要很好地与 OLE DB 池，或使用任何 OLE DB 服务，你的提供程序必须支持的所有对象的聚合。 这是任何 OLE DB 1.5 或更高版本的提供程序的要求。 这非常重要利用服务。 不能共用提供程序不支持聚合并提供没有其他服务。  
  
 可存入池中，提供程序必须支持自由线程模型。 资源池确定根据提供程序的线程模型**DBPROP_THREADMODEL**属性。  
  
 如果该提供程序可能会更改数据源处于初始化状态时的全局连接状态，它应当支持新**DBPROP_RESETDATASOURCE**属性。 连接重复使用，并且为机会清理在其下一步使用之前的状态的提供程序之前调用此属性。 如果提供程序无法清除与连接关联的某些状态，它可以返回**DBPROPSTATUS_NOTSETTABLE**的属性和连接将不能重复使用。  
  
 提供程序连接到远程数据库，并可以检测是否应支持的连接可能会丢失**DBPROP_CONNECTIONSTATUS**属性。 此属性使 OLE DB 服务能够检测死连接并确保它们不会返回到池。  
  
 最后，除非它实现池发生级别自动事务登记通常无法运行。 提供程序本身支持自动事务登记应支持通过公开禁用此登记**DBPROP_INIT_OLEDBSERVICES**属性和禁用登记，如果**DBPROPVAL_OS_TXNENLISTMENT**取消选择。  
  
## <a name="see-also"></a>另请参阅  
 [高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)