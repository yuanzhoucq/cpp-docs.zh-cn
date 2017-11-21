---
title: "SQL： 进行直接 SQL 调用 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cac2844c64bf2157a9984a29b8885434eb07b811
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL：进行直接 SQL 调用 (ODBC)
本主题说明：  
  
-   何时使用直接 SQL 调用。  
  
-   [到数据源如何建立直接 SQL 调用](#_core_making_direct_sql_function_calls)。  
  
> [!NOTE]
>  此信息适用于 MFC ODBC 类。 如果你正在使用 MFC DAO 类，请参阅主题"比较的 Microsoft Jet 数据库引擎 SQL 和 ANSI SQL"DAO 帮助中。  
  
##  <a name="_core_when_to_call_sql_directly"></a>当直接调用 SQL  
 若要创建新表，删除 (delete) 表、 更改现有的表、 创建索引，和执行更改其他 SQL 功能[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)架构，你必须直接向使用数据库的数据源发出 SQL 语句定义语言 (DDL)。 当使用向导来创建表的记录集 （在设计时） 时，你可以选择要表示的记录集的表中的哪些列。 这不允许您或其他用户的数据源向表中添加更高版本，在已编译你的程序之后的列。 数据库类不支持 DDL 直接，但你仍可以编写代码以动态，运行时绑定到记录集的新列。 有关如何执行此绑定的信息，请参阅[记录集： 动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
 可以使用 DBMS 本身更改架构或另一个工具，可用于执行 DDL 功能。 你还可以用于发送 SQL 语句，例如在调用不返回记录的预定义的查询 （存储过程） 中使用 ODBC 函数调用。  
  
##  <a name="_core_making_direct_sql_function_calls"></a>进行直接 SQL 函数调用  
 你可以直接执行 SQL 调用使用[CDatabase 类](../../mfc/reference/cdatabase-class.md)对象。 设置你的 SQL 语句字符串 (通常在`CString`) 并将其传递到[CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)成员函数你`CDatabase`对象。 如果你使用 ODBC 函数调用发送一条 SQL 语句通常返回的记录，记录将被忽略。  
  
## <a name="see-also"></a>另请参阅  
 [SQL](../../data/odbc/sql.md)