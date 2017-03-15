---
title: "架构（MFC 数据访问） | Microsoft Docs"
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
  - "数据库架构 [C++]"
  - "数据库架构 [C++], 关于数据库架构"
  - "数据库 [C++], 架构"
  - "架构 [C++], 数据库"
  - "结构 [C++]"
  - "结构 [C++], 数据库"
ms.assetid: 7d17e35f-1ccf-4853-b915-5b8c7a45b9ee
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 架构（MFC 数据访问）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

数据库架构描述了表格的当前结构和数据库中的数据库视图。  一般情况下，向导生成的代码假定数据集所访问的表格的架构不会改变，但数据库类可以处理部分架构更改，如添加、重新排序或删除未绑定的列。  如果表格更改，则必须手动更新表格的记录集，然后重新编译应用程序。  
  
 你还可以补充由向导生成的代码来处理在编译时并非完全清楚架构的数据库。  有关详细信息，请参阅[记录集：动态绑定数据列 \(ODBC\)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
## 请参阅  
 [数据访问编程 \(MFC\/ATL\)](../data/data-access-programming-mfc-atl.md)   
 [SQL](../data/odbc/sql.md)   
 [记录集 \(ODBC\)](../data/odbc/recordset-odbc.md)