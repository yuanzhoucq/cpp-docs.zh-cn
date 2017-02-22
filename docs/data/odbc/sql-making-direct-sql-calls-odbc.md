---
title: "SQL：进行直接 SQL 调用 (ODBC) | Microsoft Docs"
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
  - "ODBC 中的直接 SQL 调用"
  - "ODBC, SQL 调用"
  - "SQL 调用"
  - "SQL, 从 ODBC 直接调用"
  - "SQL, 从 ODBC 进行的直接调用"
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# SQL：进行直接 SQL 调用 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题说明：  
  
-   何时使用直接 SQL 调用。  
  
-   [对数据源直接执行 SQL 调用的方法](#_core_making_direct_sql_function_calls)。  
  
> [!NOTE]
>  此信息适用于 MFC ODBC 类。  如果使用的是 MFC DAO 类，请参见 DAO 帮助中的“Microsoft Jet 数据库引擎 SQL 和 ANSI SQL 比较”主题。  
  
##  <a name="_core_when_to_call_sql_directly"></a> 何时直接调用 SQL  
 若要创建新表、除去（删除）表、改变现有表、创建索引和执行更改[数据源 \(ODBC\)](../../data/odbc/data-source-odbc.md) 架构的其他 SQL 函数，必须使用数据库定义语言 \(DDL\) 向数据源直接发出 SQL 语句。  当使用向导创建表的记录集时（设计时），可以选择要在记录集中出现的表列。  不允许选择编译完程序后您或数据源的其他用户后来向表中添加的列。  数据库类不直接支持 DDL，但您仍然可以在运行时写代码以将新列动态绑定到记录集。  有关如何进行此绑定的信息，请参见[记录集：动态绑定数据列 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
 可以使用 DBMS 本身或其他使您得以执行 DDL 函数的工具来改变架构。  也可以将 ODBC 函数调用用于发送 SQL 语句，如调用不返回记录的预定义查询（存储过程）。  
  
##  <a name="_core_making_direct_sql_function_calls"></a> 执行直接 SQL 函数调用  
 可以使用 [CDatabase Class](../../mfc/reference/cdatabase-class.md)对象直接执行 SQL 调用。  建立 SQL 语句字符串（通常在 `CString` 中）并将它传递到 `CDatabase` 对象的 [CDatabase::ExecuteSQL](../Topic/CDatabase::ExecuteSQL.md) 成员函数。  如果使用 ODBC 函数调用来发送通常返回记录的 SQL 语句，则将忽略这些记录。  
  
## 请参阅  
 [SQL](../../data/odbc/sql.md)