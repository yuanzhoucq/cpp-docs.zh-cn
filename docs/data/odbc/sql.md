---
title: SQL |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: df1563d8bb3d53bb405fbb0d89b2b26cc964bd44
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093238"
---
# <a name="sql"></a>SQL
SQL （结构化查询语言） 是一种方法来定义查询、 修改和控制的数据与关系数据库，它允许通信。 使用 SQL 语法，你可以构造提取根据你指定的条件的记录的语句。  
  
> [!NOTE]
>  此信息适用于 MFC ODBC 类。 如果你正在使用 MFC DAO 类，请参阅本主题比较的 Microsoft Jet 数据库引擎 SQL 和 DAO 帮助中的 ANSI SQL。  
  
 SQL 语句以开头关键字谓词如**创建**或**选择**。 SQL 是一种非常强大语言;单个语句可能会影响整个表。  
  
 多个版本的 SQL 存在，使用特定 DBMS 记住每个开发。 MFC 数据库类识别一套对应到的 X / Open 的 SQL 语句和 SQL 访问组常见应用程序环境 (CAE) SQL 草案规范 （1991 年）。 有关这些语句的语法的信息，请参阅中的附录 C *ODBC SDK* *程序员参考*MSDN 库 CD 上。  
  
 本主题说明：  
  
-   [ODBC 和 SQL 之间的关系](#_core_open_database_connectivity_.28.odbc.29)。  
  
-   [数据库类使用的最常见 SQL 关键字](#_core_the_database_classes)。  
  
-   [数据库类如何使用 SQL](#_core_how_the_database_classes_use_sql)。  
  
##  <a name="_core_open_database_connectivity_.28.odbc.29"></a> 开放式数据库连接 (ODBC)  
 数据库类实现通过 ODBC，使用 SQL 调用级接口，而不是在代码中嵌入的 SQL 命令中。 ODBC 使用 SQL 与进行通信[数据源](../../data/odbc/data-source-odbc.md)通过 ODBC 驱动程序。 这些驱动程序解释 SQL，并将其，如有必要，用于为特定数据库格式，如 Microsoft Access。 有关 ODBC 如何使用 SQL 的详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)和 ODBC SDK*程序员参考*MSDN 库 CD 上。  
  
##  <a name="_core_the_database_classes"></a> 数据库类  
 数据库类旨在使您可以操作并更新中的现有数据[数据源](../../data/odbc/data-source-odbc.md)。 [MFC 应用程序向导](../../mfc/reference/database-support-mfc-application-wizard.md)、 [MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)(通过访问**添加类**)，并为你的数据库类构造大部分 SQL 语句。  
  
 数据库类使用已知数据操作语言 (DML) 作为 SQL 的一部分。 这些命令，可以使用数据源的全部或部分、 添加新的记录，编辑记录，和删除记录。 下表列出了最常见的 SQL 关键字和数据库类使用它们的方式。  
  
### <a name="some-common-sql-keywords"></a>一些常见的 SQL 关键字  
  
|SQL 关键字|向导和数据库类使用它|  
|-----------------|---------------------------------------------|  
|**SELECT**|若要确定哪些表和数据源中的列将被用于。|  
|**WHERE**|若要应用筛选器以缩小选择范围。|  
|**ORDER BY**|要应用于该记录集的排序顺序。|  
|**插入**|若要将新记录添加到记录集。|  
|**删除**|从记录集中删除记录。|  
|**更新**|若要修改的记录的字段。|  
  
 此外，数据库类识别 ODBC**调用**语句，可用于在某些数据源上调用预定义的查询 （或存储的过程）。 ODBC 数据库驱动程序解释这些语句，并替换该命令适用于每个 DBMS。  
  
> [!NOTE]
>  并非所有的 Dbms 支持**调用**语句。  
  
 如果类不能识别中的用户提供语句`CRecordset::Open`，它被解释为一个表名。  
  
 框架如何构造 SQL 语句的说明，请参阅[记录集： 如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)和[SQL： 自定义您记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
 SQL 数据库使用类似于 C 和 c + + 中使用的数据类型。 有关这些相似之处的讨论，请参阅[SQL: SQL 和 c + + 数据类型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)。  
  
 你可以找到详细信息，包括支持的 SQL 语句、 数据类型、 SQL 核心语法，和读取列表的 SQL，有关建议发布的列表中的 sql *ODBC SDK* *程序员参考* MSDN 库 CD 上。  
  
##  <a name="_core_how_the_database_classes_use_sql"></a> 数据库类如何使用 SQL  
 如果从数据库类派生的记录集使用 ODBC 与数据源，进行通信和 ODBC 通过发送 SQL 语句从数据源检索记录。 本主题说明数据库类与 SQL 之间的关系。  
  
 通过构建到 SQL 语句的各个部分的记录集构造 SQL 语句`CString`。 该字符串构造为**选择**语句语句，可返回一组记录。  
  
 当记录集调用 ODBC 将 SQL 语句发送到数据源时，ODBC 驱动程序管理器将语句传递给 ODBC 驱动程序和驱动程序将其发送到基础 DBMS。 DBMS 返回的记录的结果集和 ODBC 驱动程序返回的记录到应用程序。 数据库类使你程序的访问权限的类型安全的 c + + 类中的结果集源自`CRecordset`。  
  
 以下主题提供有关数据库类如何使用 SQL 的详细信息：  
  
-   [SQL： 自定义记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)  
  
-   [SQL：SQL 和 C++ 数据类型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)  
  
-   [SQL：进行直接 SQL 调用 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)  
  
## <a name="see-also"></a>请参阅  
 [开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [ODBC 基础](../../data/odbc/odbc-basics.md)