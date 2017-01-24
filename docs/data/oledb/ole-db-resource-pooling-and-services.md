---
title: "OLE DB 资源池和服务 | Microsoft Docs"
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
  - "OLE DB 服务 [OLE DB]"
  - "OLE DB 服务 [OLE DB], 提供程序要求"
  - "OLE DB, 资源池"
  - "资源池 [OLE DB], 提供程序要求"
  - "服务提供程序 [OLE DB]"
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 资源池和服务
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为了和 OLE DB 池或者任何 OLE DB 服务一起正常工作，提供程序必须支持所有对象的聚合。  这是任何 OLE DB 1.5 或更高版本的提供程序的要求。  它对于利用服务很关键。  不支持聚合的提供程序不能被集区，并且将不提供附加服务。  
  
 若要共用，提供程序必须支持自由线程模型。  资源池根据 **DBPROP\_THREADMODEL** 属性确定提供程序的线程模式。  
  
 如果提供程序具有在数据源为初始化状态时可能更改的全局连接状态，则它应该支持新的 **DBPROP\_RESETDATASOURCE** 属性。  该属性在连接被重用之前调用，并给予提供程序下次使用前清理状态的机会。  如果提供程序无法清理与连接关联的某些状态，它会为属性返回 **DBPROPSTATUS\_NOTSETTABLE**，连接将不被重用。  
  
 如果提供程序连接到远程数据库并且可以检测该连接是否可能丢失，则它应该支持 **DBPROP\_CONNECTIONSTATUS** 属性。  该属性给予 OLE DB 服务检测死连接并确保它们不返回到池中的能力。  
  
 最后，除非在池发生的同一级别实现，否则自动事务登记通常不工作。  如果提供程序本身支持自动事务登记，则它应该可以通过公开 **DBPROP\_INIT\_OLEDBSERVICES** 属性，并在 **DBPROPVAL\_OS\_TXNENLISTMENT** 被取消选定时禁用登记来支持禁用此登记。  
  
## 请参阅  
 [高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)