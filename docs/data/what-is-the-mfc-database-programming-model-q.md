---
title: "什么是 MFC 数据库编程模型？ | Microsoft Docs"
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
  - "DAO [C++], MFC"
  - "数据访问 [C++], 技术"
  - "数据库 [C++], MFC"
  - "MFC [C++], 数据库应用程序"
  - "ODBC [C++], MFC"
  - "ODBC 类 [C++], MFC 数据库类"
ms.assetid: f6f15bb8-4115-41f2-ad68-036e74a11bd9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 什么是 MFC 数据库编程模型？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

虽然 MFC 实现 DAO 和 ODBC 的底层方式非常不同，但它们具有类似的接口，使应用程序的移植变得相对容易，尤其是从 ODBC 移植到 DAO。  有关从 ODBC 移植到 DAO 的信息，请参见 [技术说明 55](../mfc/tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes.md)。  MFC 中的 DAO 和 ODBC 接口还与 Visual Basic 中的十分相似。  
  
 MFC 编程模型为每个开放式数据库提供数据库对象。  数据库对象表示数据库连接。  使用记录集对象进行查询和更新。  DAO 提供了附加的对象用于处理表结构、保存查询以便重用等目的（详见下文）。  MFC 为这些对象中的每一个都提供了类：一组类用于 DAO 的，另一组用于 ODBC。  
  
 使用 MFC 使数据访问更容易。  DAO 和 ODBC 数据库类提供高级别的抽象化，使您不用直接使用 DAO 或 ODBC。  写入它们的 API 比使用 MFC 类更复杂，  编写相对简单的小应用程序时尤其如此。  
  
 数据库类将下列组件添加到 MFC 类库：  
  
-   C\+\+ 数据库类，提供通过 DAO 或 ODBC 访问数据库的高级别 API  
  
-   应用程序向导和“添加类”的扩展，用于创建应用程序特定的数据库类  
  
-   示例程序，阐释类和向导的使用  
  
-   联机文档，包括概述、有关编程主题的文章和类参考资料  
  
 有关这些组件的信息，请参见 [ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)。  
  
 有关详细信息，请参阅：  
  
-   [在 DAO 和 ODBC 之间进行选择](../data/should-i-use-dao-or-odbc-q.md)。  
  
-   DAO 和 ODBC 中的 [数据库定义语言 \(DDL\) 和数据库操作语言 \(DML\) 的可用性](../data/are-ddl-and-dml-supported-q.md)。  
  
-   [安装 MFC 数据库支持](../data/installing-mfc-database-support.md)。  
  
-   MFC 中的 [ODBC](../data/odbc/odbc-and-mfc.md) 类。  
  
-   [MFC 数据访问编程文档](../data/mfc-database-documentation.md)。  
  
-   [MFC 如何实现 ODBC](../data/odbc/odbc-and-mfc.md)。  
  
## 请参阅  
 [关于数据访问的常见问题](../data/data-access-frequently-asked-questions-mfc-data-access.md)