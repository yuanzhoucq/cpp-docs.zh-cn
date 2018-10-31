---
title: SQL： 进行直接 SQL 调用 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2201a8936c1f28221bfcb628139a979e042715b9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079215"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL：进行直接 SQL 调用 (ODBC)

本主题说明：

- 何时使用直接 SQL 调用。

- [对数据源如何进行直接 SQL 调用](#_core_making_direct_sql_function_calls)。

> [!NOTE]
>  此信息适用于 MFC ODBC 类。 如果您正在使用 MFC DAO 类，请参阅"比较的 Microsoft Jet 数据库引擎 SQL 和 ANSI SQL"DAO 帮助中的主题。

##  <a name="_core_when_to_call_sql_directly"></a> 当直接调用 SQL

若要创建新表，删除 (delete) 表、 更改现有表、 创建索引，以及执行更改其他 SQL 功能[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)架构中，你必须直接向使用数据库的数据源发出 SQL 语句定义语言 (DDL)。 当使用向导来创建表的记录集 （在设计时） 时，可以选择要表示为记录集中的表的哪些列。 这不允许你或其他数据源的用户向表中添加更高版本，你编译程序后的列。 数据库类不支持 DDL 直接，但您仍然可以编写代码以动态地在运行时绑定到记录集的新列。 有关如何执行此绑定操作的信息，请参阅[记录集： 动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

可以使用 DBMS 本身更改架构或另一个工具，使你能够执行 DDL 函数。 此外可以用于将 SQL 语句，例如调用不返回记录的预定义的查询 （存储过程） 发送使用 ODBC 函数调用。

##  <a name="_core_making_direct_sql_function_calls"></a> 执行直接 SQL 函数调用

您可以直接执行 SQL 调用使用[CDatabase 类](../../mfc/reference/cdatabase-class.md)对象。 设置你的 SQL 语句字符串 (通常在`CString`) 并将其传递给[CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)成员函数在`CDatabase`对象。 如果使用 ODBC 函数调用来发送一条 SQL 语句通常返回的记录，记录将被忽略。

## <a name="see-also"></a>请参阅

[SQL](../../data/odbc/sql.md)