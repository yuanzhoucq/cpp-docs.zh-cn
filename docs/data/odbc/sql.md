---
title: "SQL | Microsoft Docs"
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
  - "数据库类 [C++], SQL 语句"
  - "ODBC [C++], SQL 实现"
  - "SQL [C++]"
  - "SQL [C++], ODBC"
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SQL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

SQL \(结构化查询语言\) 是用于定义关系数据库进行通信，所以查询，修改和控制数据。  使用 SQL 语法，可以构造一条语句，根据指定的条件来提取记录。  
  
> [!NOTE]
>  此信息适用于 MFC ODBC 类。  如果使用的是 MFC DAO 类，请参见 DAO 帮助中的“Microsoft Jet 数据库引擎 SQL 和 ANSI SQL 比较”主题。  
  
 SQL 语句以 **CREATE** 或 **SELECT** 这样的关键字谓词开头。  SQL 是一种功能强大的语言，一个语句就可以影响整个表。  
  
 SQL 现有许多版本，每个版本都是使用特定的 DBMS 开发的。  MFC 数据库类识别一组 SQL 语句，该语句与 X\/Open 和 SQL Access Group 通用应用环境 \(Common Applications Environment, CAE\) SQL 规范草案 \(1991\) 相对应。  有关这些语句的语法的详细信息，请参见 MSDN Library 光盘上 ODBC SDK Programmer's Reference（ODBC SDK 程序员参考）中的附录 C。  
  
 本主题说明：  
  
-   [ODBC 和 SQL 的关系](#_core_open_database_connectivity_.28.odbc.29)。  
  
-   [数据库类使用的最常见的 SQL 关键字](#_core_the_database_classes)。  
  
-   [数据库类使用 SQL 的方式](#_core_how_the_database_classes_use_sql)。  
  
##  <a name="_core_open_database_connectivity_.28.odbc.29"></a> 开放式数据库连接 \(ODBC\)  
 数据库类由 ODBC 实现，ODBC 在调用级别接口中使用 SQL，而不是将 SQL 命令嵌入代码中。  ODBC 通过 ODBC 驱动程序，使用 SQL 与[数据源](../../data/odbc/data-source-odbc.md)通信。  这些驱动程序解释 SQL 并在必要时翻译它，以用于特定的数据库格式，如 Microsoft Access。  有关 ODBC 如何使用 SQL 的更多信息，请参见 [ODBC](../../data/odbc/odbc-basics.md) 和 MSDN Library 光盘上的 ODBC SDK Programmer's Reference（ODBC SDK 程序员参考）。  
  
##  <a name="_core_the_database_classes"></a> 数据库类  
 数据库类旨在使您可以在现有的[数据源](../../data/odbc/data-source-odbc.md)中操作并更新数据。  [MFC 应用程序向导](../../mfc/reference/database-support-mfc-application-wizard.md)、[MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)（通过“添加类”访问）和数据库类为您构造大部分 SQL 语句。  
  
 数据库类使用 SQL 中称作数据操作语言 \(Data Manipulation Language, DML\) 的那部分。  这些命令使您得以处理全部或部分数据源，添加新记录，编辑记录和删除记录。  下表列出了最常用的 SQL 关键字和数据库类使用它们的方式。  
  
### 一些常用的 SQL 关键字  
  
|SQL 关键字|向导和数据库类用它来|  
|-------------|----------------|  
|**SELECT**|标识数据源中要使用的表和列。|  
|**WHERE**|应用筛选器以缩小选定范围。|  
|**ORDER BY**|对记录集应用排序顺序。|  
|**Insert**|向记录集添加新记录。|  
|**DELETE**|从记录集中删除记录。|  
|**UPDATE**|修改记录的字段。|  
  
 另外，数据库类识别 ODBC **CALL** 语句，该语句可用来在某些数据源上调用预定义查询（或存储过程）。  ODBC 数据库驱动程序解释这些语句并代入适合于每个 DBMS 的命令。  
  
> [!NOTE]
>  并非所有的 DBMS 都支持 **CALL** 语句。  
  
 如果类无法识别用户在 `CRecordset::Open` 中提供的语句，则将该语句解释为表名。  
  
 有关框架如何构造 SQL 语句的解释，请参见[记录集：记录集如何选择记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) 和 [SQL：自定义记录集的 SQL 语句 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)。  
  
 SQL 数据库使用的数据类型与 C 和 C\+\+ 中所使用的相似。  有关这些相似性的讨论，请参见 [SQL：SQL 和 C\+\+ 数据类型 \(ODBC\)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)。  
  
 在 MSDN Library 光盘上的 ODBC SDK Programmer's Reference（ODBC SDK 程序员参考）中可以找到有关 SQL 的更多信息，包括受支持的 SQL 语句列表、数据类型、SQL 核心语法以及推荐的 SQL 出版物的阅读材料列表。  
  
##  <a name="_core_how_the_database_classes_use_sql"></a> 数据库类如何使用 SQL  
 从数据库类派生的记录集使用 ODBC 与数据源通信，而 ODBC 通过发送 SQL 语句检索数据源中的记录。  本主题说明数据库类与 SQL 之间的关系。  
  
 记录集通过将一个 SQL 语句的片断生成 `CString` 来构造 SQL 语句。  该字符串被构造为一个 **SELECT** 语句，该语句返回一组记录。  
  
 当记录集调用 ODBC 向数据源发送 SQL 语句时，ODBC 驱动程序管理器将语句传递到 ODBC 驱动程序，然后驱动程序将它发送到基础 DBMS。  DBMS 返回记录的结果集，并且 ODBC 驱动程序将记录返回给应用程序。  数据库类使您的程序得以访问从 `CRecordset` 派生的类型安全 C\+\+ 类中的结果集。  
  
 以下主题提供了有关数据库类如何使用 SQL 的更多信息：  
  
-   [SQL：自定义记录集的 SQL 语句 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)  
  
-   [SQL：SQL 和 C\+\+ 数据类型 \(ODBC\)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)  
  
-   [SQL：执行直接 SQL 调用 \(ODBC\)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)  
  
## 请参阅  
 [开放式数据库连接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)   
 [ODBC 基础](../../data/odbc/odbc-basics.md)