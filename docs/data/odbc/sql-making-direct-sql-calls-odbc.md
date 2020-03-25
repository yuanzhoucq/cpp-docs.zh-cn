---
title: SQL：进行直接 SQL 调用 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
ms.openlocfilehash: 9240a227cdc4004d1e6e2b7ac26946ca233b71ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212623"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL：进行直接 SQL 调用 (ODBC)

本主题介绍：

- 何时使用直接 SQL 调用。

- [如何对数据源进行直接 SQL 调用](#_core_making_direct_sql_function_calls)。

> [!NOTE]
>  此信息适用于 MFC ODBC 类。 如果使用的是 MFC DAO 类，请参阅 DAO 帮助中的 "Microsoft Jet 数据库引擎 SQL 和 ANSI SQL 比较" 主题。

##  <a name="when-to-call-sql-directly"></a><a name="_core_when_to_call_sql_directly"></a>何时直接调用 SQL

若要创建新的表、删除（删除）表、更改现有表、创建索引和执行其他更改[数据源（ODBC）](../../data/odbc/data-source-odbc.md)架构的 sql 函数，必须使用数据库定义语言（DDL）直接向数据源发出 SQL 语句。 当您使用向导为表创建记录集（在设计时）时，您可以选择要在记录集中表示的表的列。 这不允许你或数据源的其他用户在稍后在编译程序后添加到表中的列。 数据库类不直接支持 DDL，但你仍可以编写代码以在运行时动态将新列绑定到记录集。 有关如何执行此绑定的信息，请参阅[记录集：动态绑定数据列（ODBC）](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

您可以使用 DBMS 本身来更改架构或允许您执行 DDL 函数的另一个工具。 你还可以使用 ODBC 函数调用来发送 SQL 语句，如调用不返回记录的预定义查询（存储过程）。

##  <a name="making-direct-sql-function-calls"></a><a name="_core_making_direct_sql_function_calls"></a>进行直接 SQL 函数调用

可以使用[CDatabase 类](../../mfc/reference/cdatabase-class.md)对象直接执行 SQL 调用。 设置 SQL 语句字符串（通常在 `CString`中），并将其传递到 `CDatabase` 对象的[CDatabase：： ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)成员函数。 如果使用 ODBC 函数调用来发送通常返回记录的 SQL 语句，则将忽略记录。

## <a name="see-also"></a>另请参阅

[SQL](../../data/odbc/sql.md)
