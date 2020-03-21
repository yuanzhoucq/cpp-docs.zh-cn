---
title: SQL
ms.date: 05/09/2019
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
ms.openlocfilehash: 5e31105e682e8acecbdc0da461614fc46e4ae227
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079776"
---
# <a name="sql"></a>SQL

SQL（结构化查询语言）是一种与关系数据库通信的方法，使你能够定义、查询、修改和控制数据。 通过使用 SQL 语法，可以构造一个根据所指定的条件提取记录的语句。

> [!NOTE]
>  此信息适用于 MFC ODBC 类。 如果使用的是 MFC DAO 类，请参阅 DAO 帮助中的主题“Microsoft Jet 数据库引擎 SQL 和 ANSI SQL 的比较”。

SQL 语句以关键字谓词开头，例如“CREATE”或“SELECT”。 SQL 是一种功能非常强大的语言；单个语句可以影响整个表。

存在许多版本的 SQL，每个版本的开发都考虑到特定的 DBMS。 MFC 数据库类识别一组对应于 X/Open 和 SQL 访问组公用应用程序环境 (CAE) SQL 草案规范 (1991) 的 SQL 语句。 有关这些语句的语法的信息，请参阅 MSDN 库 CD 上的*ODBC SDK* *程序员参考*中的附录 C。

本主题介绍：

- [ODBC 和 SQL 之间的关系](#_core_open_database_connectivity_.28.odbc.29).

- [数据库类使用的最常见的 SQL 关键字](#_core_the_database_classes)。

- [数据库类如何使用 SQL](#_core_how_the_database_classes_use_sql)。

##  <a name="open-database-connectivity-odbc"></a><a name="_core_open_database_connectivity_.28.odbc.29"></a> 开放式数据库连接 (ODBC)

数据库类是使用 ODBC 实现的，ODBC 在调用级接口中使用 SQL，而不是在代码中嵌入 SQL 命令。 ODBC 使用 SQL 通过 ODBC 驱动程序与[数据源](../../data/odbc/data-source-odbc.md)进行通信。 这些驱动程序将解释 SQL 并在必要时对其进行转换，以便与特定数据库格式（例如 Microsoft Access）一起使用。 有关 ODBC 如何使用 SQL 的详细信息，请参阅 MSDN 库 CD 上的 [ODBC](../../data/odbc/odbc-basics.md) 和 ODBC SDK 程序员参考。

##  <a name="database-classes"></a><a name="_core_the_database_classes"></a> 数据库类

> [!NOTE]
> MFC ODBC 使用者向导在 Visual Studio 2019 及更高版本中不可用。 你仍可以手动创建使用者。

数据库类旨在使你能够操作和更新现有[数据源](../../data/odbc/data-source-odbc.md)中的数据。 [MFC 应用程序向导](../../mfc/reference/database-support-mfc-application-wizard.md)、[MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)（通过“添加类”访问）以及数据库类将为你构造大多数 SQL 语句。

数据库类将使用 SQL 的一部分，这部分称为数据操作语言 (DML)。 这些命令使你可以处理所有或部分数据源、添加新记录、编辑记录和删除记录。 下表列出了最常见的 SQL 关键字以及数据库类使用它们的方式。

### <a name="some-common-sql-keywords"></a>一些常见的 SQL 关键字

|SQL 关键字|向导和数据库类将此关键字用于|
|-----------------|---------------------------------------------|
|**SELECT**|确定要使用数据源中的哪些表和列。|
|**WHERE**|应用缩小选择范围的筛选器。|
|**ORDER BY**|将排序顺序应用于记录集。|
|**INSERT**|将新记录添加到记录集。|
|**DELETE**|从记录集中删除记录。|
|**UPDATE**|修改记录的字段。|

此外，数据库类将识别 ODBC“CALL”语句，你可以使用这些语句在某些数据源上调用预定义查询（或存储过程）。 ODBC 数据库驱动程序将解释这些语句并替换适用于每个 DBMS 的命令。

> [!NOTE]
>  并非所有的 DBMS 都支持“CALL”语句。

如果类无法识别 `CRecordset::Open` 中用户提供的语句，此语句则被解释为表名。

有关框架如何构造 SQL 语句的说明，请参阅[记录集：记录集如何选择记录（odbc）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)和[SQL：自定义记录集的 SQL 语句（odbc）](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。

SQL 数据库使用的数据类型类似于 C 和 C++ 中使用的数据类型。 有关这些相似性的讨论，请参阅[sql： sql 和C++数据类型（ODBC）](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)。

可在 MSDN Library CD 上的*ODBC SDK* *程序员参考*中找到有关 sql 的详细信息，包括受支持的 sql 语句、数据类型、sql core 语法和建议发布的阅读列表。

##  <a name="how-the-database-classes-use-sql"></a><a name="_core_how_the_database_classes_use_sql"></a> 数据库类如何使用 SQL

从数据库类派生的记录集使用 ODBC 与数据源通信，ODBC 通过发送 SQL 语句从数据源检索记录。 本主题介绍了数据库类和 SQL 之间的关系。

记录集通过将 SQL 语句的各个片段构建为一个 `CString` 来构造一个 SQL 语句。 此字符串构造为“SELECT”语句，它将返回一组记录。

当记录集调用 ODBC 将 SQL 语句发送到数据源时，ODBC 驱动程序管理器将此语句传递给 ODBC 驱动程序，驱动程序会将它发送到基础 DBMS。 DBMS 返回记录的结果集，ODBC 驱动程序将记录返回给应用程序。 数据库类使程序能够在派生自 `CRecordset` 的类型安全 C++ 类中访问结果集。

以下主题提供了有关数据库类如何使用 SQL 的详细信息：

- [SQL：自定义记录集的 SQL 语句（ODBC）](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

- [SQL：SQL 和 C++ 数据类型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

- [SQL：进行直接 SQL 调用 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

## <a name="see-also"></a>另请参阅

[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[ODBC 基础](../../data/odbc/odbc-basics.md)