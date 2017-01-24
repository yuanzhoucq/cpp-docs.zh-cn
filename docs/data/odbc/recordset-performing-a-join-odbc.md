---
title: "记录集：执行联接 (ODBC) | Microsoft Docs"
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
  - "数据绑定 [C++], 记录集内的列"
  - "数据绑定 [C++], 记录集列"
  - "筛选器 [C++], 记录集的联接条件"
  - "联接 [C++], 在记录集中"
  - "ODBC 记录集 [C++], 联接"
  - "记录集 [C++], 绑定数据"
  - "记录集 [C++], 联接表"
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集：执行联接 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
## 什么是联接  
 联接操作（一个通用的数据访问任务）使您得以使用一个记录集对象处理来自多个表的数据。  联接两个或两个以上的表产生可以包含每个表中的列的记录集，但该记录集在应用程序中仍表现为单个表。  有时联接使用所有表的所有列，但有时联接中的 SQL **SELECT** 子句只使用每个表中的某些列。  数据库类支持只读联接，但不支持可更新的联接。  
  
 若要选择包含联接表中的列的记录，需要下列项：  
  
-   包含所有正在联接的表名的表列表。  
  
-   包含所有参与列名的列列表。  具有相同名称但来自不同表的列由表名限定。  
  
-   指定用于联接表的列的筛选器（SQL **WHERE** 子句）。  此筛选器采用“Table1.KeyCol \= Table2.KeyCol”的格式并实际完成联接。  
  
 可以以同样的方式联接两个以上的表，即通过将多个列对视为相等，每一对都由 SQL 关键字 **AND** 联接。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：为预定义查询声明一个类 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)   
 [记录集：声明表的类 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [记录集：再次查询记录集 \(ODBC\)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)