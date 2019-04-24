---
title: SQL
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
ms.openlocfilehash: 8f93d97530068695359273b523e7d2ae46de01cb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037852"
---
# <a name="sql"></a>SQL

SQL （结构化查询语言） 是一种方法来定义查询、 修改和控制的数据与关系数据库，它允许进行通信。 使用 SQL 语法，可以构造根据你指定的条件的记录中提取的语句。

> [!NOTE]
>  此信息适用于 MFC ODBC 类。 如果使用 MFC DAO 类时，请参阅本主题比较的 Microsoft Jet 数据库引擎 SQL 和 DAO 帮助中的 ANSI SQL。

SQL 语句如开头关键字谓词**创建**或**选择**。 SQL 是非常强大的语言;单个语句可能会影响整个表。

存在多个版本的 SQL，使用特定 DBMS 记住每个开发。 MFC 数据库类识别到的 X / Open 相对应的 SQL 语句和 SQL 访问组常见的应用程序环境 (CAE) SQL 草案规范 （1991 年） 的一组。 这些语句的语法的信息，请参阅中的附录 C *ODBC SDK* *程序员参考*MSDN 库 CD 上。

本主题说明：

- [ODBC 和 SQL 之间的关系](#_core_open_database_connectivity_.28.odbc.29)。

- [使用数据库类的最常见 SQL 关键字](#_core_the_database_classes)。

- [数据库类如何使用 SQL](#_core_how_the_database_classes_use_sql)。

##  <a name="_core_open_database_connectivity_.28.odbc.29"></a> 开放式数据库连接 (ODBC)

使用 ODBC，使用调用级别接口，而无需在代码中嵌入 SQL 命令中的 SQL 实现数据库类。 ODBC 使用 SQL 与通信[数据源](../../data/odbc/data-source-odbc.md)通过 ODBC 驱动程序。 这些驱动程序解释 SQL 和翻译，如有必要，以用于特殊数据库格式，如 Microsoft Access。 有关 ODBC 如何使用 SQL 的详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)和 ODBC SDK*程序员参考*MSDN 库 CD 上。

##  <a name="_core_the_database_classes"></a> 数据库类

数据库类旨在使你能够处理和更新数据中的现有[数据源](../../data/odbc/data-source-odbc.md)。 [MFC 应用程序向导](../../mfc/reference/database-support-mfc-application-wizard.md)，则[MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)(通过访问**添加类**)，和数据库类为您构造的大多数 SQL 语句。

数据库类使用 SQL 作为数据操作语言 (DML) 的已知的一部分。 这些命令，您可以使用全部或部分数据源、 添加新记录、 编辑记录，和删除记录。 下表列出了最常见的 SQL 关键字和数据库类使用它们的方式。

### <a name="some-common-sql-keywords"></a>一些常见的 SQL 关键字

|SQL 关键字|向导和数据库类使用它|
|-----------------|---------------------------------------------|
|**SELECT**|若要确定哪些表和数据源中的列将被用于。|
|**WHERE**|若要应用筛选器，用于限制所选内容。|
|**ORDER BY**|要应用于该记录集的排序顺序。|
|**INSERT**|若要将新记录添加到记录集。|
|**DELETE**|若要从记录集删除记录。|
|**UPDATE**|若要修改记录的字段。|

此外，数据库类识别 ODBC**调用**语句，可用于在某些数据源上调用预定义的查询 （或存储的过程）。 ODBC 数据库驱动程序解释这些语句，并将替换为适用于每个 DBMS 命令。

> [!NOTE]
>  并非所有 Dbms 支持**调用**语句。

如果类不能识别中的用户提供语句`CRecordset::Open`，它被解释为表名。

框架如何构造 SQL 语句的说明，请参阅[记录集：如何记录集选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)和[SQL:自定义记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。

SQL 数据库使用类似于在 C 中使用的数据类型和C++。 有关这些相似之处的讨论，请参阅[SQL:SQL 和C++数据类型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)。

你可以找到包括一系列支持的 SQL 语句、 数据类型、 SQL core 语法，以及建议发布的 sql，读取列表中的 sql 的详细信息*ODBC SDK* *程序员参考* MSDN 库 CD 上。

##  <a name="_core_how_the_database_classes_use_sql"></a> 数据库类如何使用 SQL

从数据库类派生的记录集使用 ODBC 与数据源进行通信和 ODBC 通过发送的 SQL 语句从数据源检索的记录。 本主题介绍数据库类和 SQL 之间的关系。

记录集构造 SQL 语句，方法是建立到 SQL 语句的组成部分`CString`。 该字符串构造为**选择**语句，返回一组记录。

当该记录集调用 ODBC 将 SQL 语句发送到数据源时，ODBC 驱动程序管理器将该语句传递到 ODBC 驱动程序和驱动程序将其发送到基础 DBMS。 DBMS 返回结果集的记录，并向应用程序的 ODBC 驱动程序返回的记录。 数据库类让您访问的结果集在类型安全的程序C++类派生自`CRecordset`。

以下主题提供有关数据库类如何使用 SQL 的详细信息：

- [SQL:自定义记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

- [SQL:SQL 和C++数据类型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

- [SQL:进行直接 SQL 调用 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

## <a name="see-also"></a>请参阅

[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[ODBC 基础](../../data/odbc/odbc-basics.md)