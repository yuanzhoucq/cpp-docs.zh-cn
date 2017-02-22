---
title: "使用存储过程 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供程序模板, 存储过程"
  - "OLE DB, 存储过程"
  - "存储过程, 关于存储过程"
  - "存储过程, OLE DB"
  - "存储过程, Visual C++"
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# 使用存储过程
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

存储过程是存储在数据库中的可执行对象。  调用存储过程类似于调用 SQL 命令。  在数据源上使用存储过程（而不是在客户端应用程序中执行或准备语句）可以提供若干个优点，其中包括：更高的性能、较低的网络系统开销以及改善的一致性和准确性。  
  
 存储过程可以具有任意个（包括 0 个）输入或输出参数，并可以传递一个返回值。  您可以将参数值硬编码为特定数据值，也可以使用参数标记（问号“?”）。  
  
> [!NOTE]
>  使用 Visual C\+\+ 创建的 CLR SQL Server 存储过程必须用 **\/clr:safe** 编译器选项进行编译。  
  
 用于 SQL Server 的 OLE DB 提供程序 \(SQLOLEDB\) 支持以下由存储过程用来返回数据的机制：  
  
-   过程中的每一条 SELECT 语句都生成一个结果集。  
  
-   过程可以通过输出参数返回数据。  
  
-   过程可以具有整数返回代码。  
  
> [!NOTE]
>  不能将存储过程与 Jet 的 OLE DB 提供程序一起使用，因为该提供程序不支持存储过程；查询字符串中只允许使用常数。  
  
## 请参阅  
 [使用 OLE DB 使用者模板](../../data/oledb/working-with-ole-db-consumer-templates.md)