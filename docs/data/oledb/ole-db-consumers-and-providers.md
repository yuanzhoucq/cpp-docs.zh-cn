---
title: "OLE DB 使用者和提供程序 | Microsoft Docs"
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
  - "OLE DB 使用者"
  - "OLE DB 使用者, OLE DB 数据体系结构"
  - "OLE DB 提供程序"
  - "OLE DB 提供程序, OLE DB 数据体系结构"
  - "OLE DB, 数据模型"
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 使用者和提供程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 结构采用使用者和提供程序模型。  使用者请求数据。  提供程序响应这些请求，将数据放置于一个表格中并且将其返回到使用者。  使用者发出的任何调用都必须在提供程序中实现。  
  
 从技术定义而言，使用者是指任何通过 OLE DB 接口访问数据的系统或应用程序代码（不一定是 OLE DB 组件）。  这些接口在提供程序中实现。  因此，提供程序是指任何一个实现 OLE DB 接口来封装数据访问并将其向其他对象（即，使用者）公开的软件组件。  
  
 从其角色而言，使用者调用 OLE DB 接口方法；而 OLE DB 提供程序实现所需的 OLE DB 接口。  
  
 OLE DB 避免使用术语“客户端”和“服务器”，因为这些角色并不总是有意义，尤其具有 n 层的情况下。  因为使用者可能是一层中为另一组件服务的组件，所以称之为客户组件会引起混乱。  另外，提供程序有时更像一个数据库驱动程序，而不是服务器。  
  
## 请参阅  
 [OLE DB 编程](../../data/oledb/ole-db-programming.md)   
 [OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)