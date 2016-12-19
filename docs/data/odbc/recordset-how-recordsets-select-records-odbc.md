---
title: "记录集：记录集如何选择记录 (ODBC) | Microsoft Docs"
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
  - "ODBC 记录集, 选择记录"
  - "记录选择, ODBC 记录集"
  - "记录, 选择"
  - "记录集, 构造 SQL 语句"
  - "记录集, 选择记录"
  - "SQL 语句, 记录集"
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集：记录集如何选择记录 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 本主题说明：  
  
-   [您在选择记录时的角色和选项](#_core_your_options_in_selecting_records)。  
  
-   [记录集构造其 SQL 语句和选择记录的方式](#_core_how_a_recordset_constructs_its_sql_statement)。  
  
-   [可以对选择进行哪些自定义](#_core_customizing_the_selection)。  
  
 记录集通过 ODBC 驱动程序从数据源中选择记录的方法是将 SQL 语句发送到该驱动程序。  发送的 SQL 取决于设计与打开记录集类的方式。  
  
##  <a name="_core_your_options_in_selecting_records"></a> 选择记录中的选项  
 下表显示了选择记录中的选项。  
  
### 您可以影响记录集的方式与时间  
  
|当您|您可以：|  
|--------|----------|  
|用“添加类”向导声明记录集类|指定从哪个表选择。<br /><br /> 指定包含哪些列。<br /><br /> 请参见[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。|  
|完成记录集类的实现|重写成员函数，如 `OnSetOptions`（高级），以设置应用程序特定的选项或更改默认值。  如果需要一个参数化记录集，则指定参数数据成员。|  
|构造一个记录集对象（调用 **Open** 之前）|指定筛选记录的 **WHERE** 子句中使用的搜索条件（可为复合型）。  请参见[记录集：筛选记录 \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)。<br /><br /> 指定排序记录的 **ORDER BY** 子句中使用的排列顺序。  请参见[记录集：对记录排序 \(ODBC\)](../../data/odbc/recordset-sorting-records-odbc.md)。<br /><br /> 指定已添加到类的所有参数的参数值。  请参见[记录集：参数化记录集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。|  
|调用 **Open** 以运行记录集的查询|指定一个自定义 SQL 字符串，替换由向导设置的默认 SQL 字符串。  请参见“类库引用”中的 [CRecordset::Open](../Topic/CRecordset::Open.md) 和 [SQL：自定义记录集的 SQL 语句 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)。|  
|调用 **Requery** 用数据源中的最新值再次查询记录集|指定新参数、筛选器或排序。  请参见[记录集：再次查询记录集 \(ODBC\)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)。|  
  
##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a> 记录集如何构造其 SQL 语句  
 调用记录集对象的 [Open](../Topic/CRecordset::Open.md) 成员函数时，**Open** 将用某些或所有下列成分构造 SQL 语句：  
  
-   传递到 **Open** 的 **lpszSQL** 参数。  如果不为 **NULL**，则该参数指定一个自定义 SQL 字符串或该字符串的一部分。  框架将分析该字符串。  如果该字符串为 SQL **SELECT** 语句或 ODBC **CALL** 语句，则框架将该字符串作为记录集的 SQL 语句使用。  如果该字符串不以“SELECT”或“{CALL”开头，则框架使用所提供的字符串构造一个 SQL **FROM** 子句。  
  
-   由 [GetDefaultSQL](../Topic/CRecordset::GetDefaultSQL.md) 返回的字符串。  默认情况下，这是您在向导中为记录集指定的表名，但您可更改函数的返回值。  框架将调用 `GetDefaultSQL`，如果该字符串不以“SELECT”或“{CALL”开头，则将其假定为表名（用于构造 SQL 字符串）。  
  
-   记录集的字段数据成员，这些字段数据成员将绑定到表的特定列。  框架将记录列绑定到这些成员的地址，并将其地址作为缓冲区。  框架从记录集的 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 或 [DoBulkFieldExchange](../Topic/CRecordset::DoBulkFieldExchange.md) 成员函数中的 [RFX](../../data/odbc/record-field-exchange-using-rfx.md) 或“批量 RFX”函数调用中，确定字段数据成员与表列的相互关系。  
  
-   包含在 [m\_strFilter](../Topic/CRecordset::m_strFilter.md) 数据成员中的记录集的[筛选器](../../data/odbc/recordset-filtering-records-odbc.md)（如果有的话）。  框架使用该字符串构造 SQL **WHERE** 子句。  
  
-   包含在 [m\_strSort](../Topic/CRecordset::m_strSort.md) 数据成员中的记录集的[排序](../../data/odbc/recordset-sorting-records-odbc.md)顺序（如果有的话）。  框架使用该字符串构造 SQL **ORDER BY** 子句。  
  
    > [!TIP]
    >  若要使用 SQL **GROUP BY** 子句（也可能包括 **HAVING** 子句），请将该（这些）子句追加到筛选器字符串的末尾。  
  
-   为类指定的任何[参数数据成员](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)的值。  即将调用 **Open** 或 **Requery** 之前设置参数值。  框架将这些参数值绑定到 SQL 字符串中的“?”占位符。  编译时，指定带有占位符的字符串。  运行时，框架根据传递的参数值填写详细信息。  
  
 **Open** 从这些成分中构造 SQL **SELECT** 语句。  有关框架如何使用这些成分的详细信息，请参见[自定义选定内容](#_core_customizing_the_selection)。  
  
 构造了该语句后，**Open** 将 SQL 发送到 ODBC 驱动程序管理器（及 ODBC 游标库，前提是如果它存在于内存中），ODBC 驱动程序管理器将 SQL 发送到特定 DBMS 的 ODBC 驱动程序。  该驱动程序与 DBMS 进行通信以执行数据源中的选项并获取第一个记录。  框架将记录加载到记录集的字段数据成员中。  
  
 可以利用这些技术组合打开[表](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)并基于多个表的[联接](../../data/odbc/recordset-performing-a-join-odbc.md)来构造查询。  使用额外的自定义，可调用[预定义查询](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)（存储过程）、选择设计时未知的表列并将它们[绑定](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)到记录集字段，或执行大多数其他数据访问任务。  通过自定义记录集无法完成的任务仍然可通过[调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)或直接执行具有 [CDatabase::ExecuteSQL](../Topic/CDatabase::ExecuteSQL.md) 的 SQL 语句来完成。  
  
##  <a name="_core_customizing_the_selection"></a> 自定义选定内容  
 除提供筛选器、排序顺序或参数以外，还可以执行下列操作来自定义记录集的选定内容：  
  
-   调用记录集的 [Open](../Topic/CRecordset::Open.md) 时，传递 **lpszSQL** 中的自定义 SQL 字符串。  **lpsqSQL** 中传递的任何内容均优先于 [GetDefaultSQL](../Topic/CRecordset::GetDefaultSQL.md) 成员函数返回的内容。  
  
     有关更多信息，请参见 [SQL：自定义记录集的 SQL 语句 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)，它描述了可以传递到 **Open** 的 SQL 语句（或部分语句）的类型和框架对它们的处理。  
  
    > [!NOTE]
    >  如果传递的自定义字符串不是以“SELECT”或“{CALL”开头，则 MFC 假定该字符串包含表名。  这同样适用于下一个项目符号项。  
  
-   改变向导写入记录集的 `GetDefaultSQL` 成员函数的字符串。  编辑该函数的代码以更改其返回的内容。  默认情况下，向导编写返回单一表名的 `GetDefaultSQL` 函数。  
  
     可让 `GetDefaultSQL` 返回 **lpszSQL** 参数中可传递到 **Open** 的任何项。  如果不传递 **lpszSQL** 中的自定义 SQL 字符串，则框架使用 `GetDefaultSQL` 返回的字符串。  `GetDefaultSQL` 必须最少返回一个表名。  但也可让它返回多个表名、一个完整的 **SELECT** 语句、一个 ODBC **CALL** 语句等。  有关可传递到 **lpszSQL** 的内容列表（或让 `GetDefaultSQL` 返回的内容列表），请参见 [SQL：自定义记录集的 SQL 语句 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)。  
  
     如果正执行两个或更多个表的联接，则重写 `GetDefaultSQL` 以自定义 SQL **FROM** 子句中使用的表列表。  有关更多信息，请参见[记录集：执行联接 \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md)。  
  
-   可能要基于运行时获得的有关数据源架构的信息来手动绑定其他的字段数据成员。  将字段数据成员添加到记录集类，将它们的 [RFX](../../data/odbc/record-field-exchange-using-rfx.md) 或“批量 RFX”函数调用添加到 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 或 [DoBulkFieldExchange](../Topic/CRecordset::DoBulkFieldExchange.md) 成员函数中，并在类构造函数中添加数据成员的初始化。  有关更多信息，请参见[记录集：动态绑定数据列 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
-   重写记录集成员函数（如 `OnSetOptions`）以设置应用程序特定的选项或重写默认值。  
  
 如果要使记录集基于复杂的 SQL 语句，需要使用这些自定义技术的组合。  例如，您也许要使用记录集并不直接支持的 SQL 子句及关键字，或者您也许正在联接多个表。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：记录集如何更新记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [ODBC 基础](../../data/odbc/odbc-basics.md)   
 [SQL](../../data/odbc/sql.md)   
 [记录集：锁定记录 \(ODBC\)](../../data/odbc/recordset-locking-records-odbc.md)