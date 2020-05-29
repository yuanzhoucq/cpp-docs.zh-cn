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
ms.openlocfilehash: e2421e047d217fdc7a138509385399fa37d36a1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374503"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL：进行直接 SQL 调用 (ODBC)

本主题介绍：

- 何时使用直接 SQL 调用。

- [如何直接对数据源进行 SQL 调用](#_core_making_direct_sql_function_calls)。

> [!NOTE]
> 此信息适用于 MFC ODBC 类。 如果您正在使用 MFC DAO 类，请参阅 DAO 帮助中的主题"微软喷气数据库引擎 SQL 和 ANSI SQL 的比较"。

## <a name="when-to-call-sql-directly"></a><a name="_core_when_to_call_sql_directly"></a>何时直接调用 SQL

要创建新表、删除（删除）表、更改现有表、创建索引和执行更改[数据源 （ODBC）](../../data/odbc/data-source-odbc.md)架构的其他 SQL 函数，必须使用数据库定义语言 （DDL） 直接向数据源发出 SQL 语句。 使用向导为表创建记录集（在设计时）时，可以选择要在记录集中表示的表的列。 这不允许在编译程序后，稍后将数据源的其他用户添加到表中。 数据库类不直接支持 DDL，但您仍然可以编写代码，在运行时动态地将新列绑定到记录集。 有关如何执行此操作绑定的信息，请参阅[记录集：动态绑定数据列 （ODBC）。](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

您可以使用 DBMS 本身来更改架构或其他工具，以便执行 DDL 函数。 您还可以使用 ODBC 函数调用发送 SQL 语句，例如调用不返回记录的预定义查询（存储过程）。

## <a name="making-direct-sql-function-calls"></a><a name="_core_making_direct_sql_function_calls"></a>直接 SQL 函数调用

您可以使用[CDatabase 类](../../mfc/reference/cdatabase-class.md)对象直接执行 SQL 调用。 设置 SQL 语句字符串（通常在`CString`中），并将其传递给`CDatabase`对象的[CDatabase：：执行SQL](../../mfc/reference/cdatabase-class.md#executesql)成员函数。 如果使用 ODBC 函数调用发送通常返回记录的 SQL 语句，则忽略这些记录。

## <a name="see-also"></a>另请参阅

[SQL](../../data/odbc/sql.md)
