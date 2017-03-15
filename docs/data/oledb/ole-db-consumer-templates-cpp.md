---
title: "OLE DB 使用者模板 (C++) | Microsoft Docs"
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
  - "数据库 [C++]，OLE DB 模板"
  - "OLE DB 使用者 [C++]，数据访问"
  - "OLE DB 使用者模板 [C++]"
  - "数据库 [C++]，使用者"
ms.assetid: d3e42612-0bc0-4d65-9c32-0e8a7b219e82
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 使用者模板 (C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 使用者模板支持 OLE DB 2.6 版规范。 （OLE DB 使用者模板针对 OLE DB 2.6 进行测试，但该模板并非支持规范中的每个接口。） 使用者模板最小化实现 OLE DB 使用者所必须编写的代码的量。 该模板提供：  
  
-   对 OLE DB 功能的轻松访问以及与 ATL 和 MFC 的轻松集成。  
  
-   用于数据库参数和列的简单绑定模型。  
  
-   用于 OLE DB 编程的本机 C\/C\+\+ 数据类型。  
  
 要使用 OLE DB 模板，应熟悉 C\+\+ 模板、COM 和 OLE DB 接口。 如果不熟悉 OLE DB，请参阅 [OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms718124.aspx)。  
  
 OLE DB 模板支持现有 OLE DB 对象模型而不是添加新的对象模型。 OLE DB 使用者模板中的顶层类并行于 OLE DB 规范中定义的组件。 OLE DB 使用者模板的设计包括高级功能，如行集上的多个访问器。 模板和多重继承的使用可缩小库的规模并让库变得灵活。  
  
## OLE DB 使用者访问数据的方式  
 使用者使用多种类型的对象，以下主题对这些对象进行了介绍：  
  
-   [数据源和会话](../../data/oledb/data-sources-and-sessions.md)  
  
-   [访问器和行集合](../../data/oledb/accessors-and-rowsets.md)  
  
-   [命令和表](../../data/oledb/commands-and-tables.md)  
  
-   [用户记录](../../data/oledb/user-records.md)  
  
 使用者执行任何操作之前，应首先选择一个适合需要访问的数据库的类型的 OLE DB 提供程序（例如，SQL、Oracle、ODBC 和 MSDS）。 要执行此操作，通常要使用一个枚举器（请参阅[数据源和会话](../../data/oledb/data-sources-and-sessions.md)中所提到的 [CEnumerator](../../data/oledb/cenumerator-class.md)）。  
  
 [数据源对象](../../data/oledb/data-sources-and-sessions.md)提供连接到所选数据源所必需的连接信息。 数据源对象还包含身份验证信息（如登录名和密码），该信息用于向用户提供访问数据源的权限。 数据源对象建立到数据库的连接，然后创建一个或多个会话对象。 每个[会话对象](../../data/oledb/data-sources-and-sessions.md)管理自身与数据库的交互（也即查询和检索数据），并独立于其他现有会话而执行这些事务。  
  
 会话创建行集和命令对象。[命令对象](../../data/oledb/commands-and-tables.md)允许用户与数据库进行交互，例如，通过使用 SQL 命令来实现。[行集对象](../../data/oledb/accessors-and-rowsets.md)是一组数据，可在其中进行导航和[更新、删除和插入行](../../data/oledb/updating-rowsets.md)。  
  
 OLE DB 使用者将数据库表中的列与局部变量绑定；它使用[访问器](../../data/oledb/accessors-and-rowsets.md)来实现这一操作，访问器包含一个有关数据在使用者内存储的方式的映射。 该映射由表列和使用者应用程序中的本地缓冲区（变量）之间的一组绑定构成。  
  
 使用使用者的一个重要概念是声明使用者中的两个类：[命令（或表）类](../../data/oledb/commands-and-tables.md)和[用户记录类](../../data/oledb/user-records.md)。 通过命令（或表）类访问行集，该类继承自访问器类和行集类。 用户记录类包含之前介绍的行集绑定映射。  
  
 有关详细信息，请参阅下列主题：  
  
-   [创建 OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer.md)  
  
-   [常见的 OLE DB 使用者方案（示例）](../../data/oledb/working-with-ole-db-consumer-templates.md)  
  
## 请参阅  
 [OLE DB 编程](../../data/oledb/ole-db-programming.md)   
 [数据访问](../Topic/Data%20Access%20in%20Visual%20C++.md)   
 [OLE DB SDK 文档](https://msdn.microsoft.com/en-us/library/ms722784.aspx)   
 [OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)