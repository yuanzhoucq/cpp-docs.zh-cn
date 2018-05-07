---
title: 记录集： 如何记录集选择记录 (ODBC) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9ff2f1e9946eb32356eb09fa2ee216aa636a351
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>记录集：记录集如何选择记录 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 本主题说明：  
  
-   [你的角色和你的选项中选择记录](#_core_your_options_in_selecting_records)。  
  
-   [记录集如何构造查询的 SQL 语句并选择记录](#_core_how_a_recordset_constructs_its_sql_statement)。  
  
-   [你可以进行哪些自定义所选内容](#_core_customizing_the_selection)。  
  
 记录集从数据源通过 ODBC 驱动程序中选择的记录，通过将 SQL 语句发送到该驱动程序。 发送 SQL 取决于你如何在设计和打开记录集类。  
  
##  <a name="_core_your_options_in_selecting_records"></a> 选择记录中的选项  
 下表中选择记录显示你的选项。  
  
### <a name="how-and-when-you-can-affect-a-recordset"></a>如何以及何时可能会影响记录集  
  
|当你|你可以|  
|--------------|-------------|  
|声明记录集类与**添加类**向导|指定要从选择的表。<br /><br /> 指定要包含的列。<br /><br /> 请参阅[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。|  
|完成记录集类实现|重写成员函数，如`OnSetOptions`（高级） 设置应用程序特定的选项或更改默认值。 如果你希望参数化记录集，请指定参数数据成员。|  
|构造一个记录集对象 (在调用之前**打开**)|指定搜索条件 （可能为复合） 用于**其中**记录进行筛选的子句。 请参阅[记录集： 筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。<br /><br /> 指定在中使用的排序顺序**ORDER BY**记录进行排序的子句。 请参阅[记录集： 对记录 (ODBC) 进行排序](../../data/odbc/recordset-sorting-records-odbc.md)。<br /><br /> 指定任何参数添加到类的参数值。 请参阅[记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。|  

|通过调用运行记录集的查询**打开**|指定要替换设置向导的默认 SQL 字符串的自定义 SQL 字符串。 请参阅[CRecordset::Open](../../mfc/reference/crecordset-class.md#open)中*类库参考*和[SQL： 自定义记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。 |  

|调用**Requery**对数据源的最新值的记录集的类型重新查询 |指定新的参数、 筛选或排序。 请参阅[记录集： 再次查询记录集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)。 |  
  
##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a> 记录集如何构造查询的 SQL 语句  
 当调用的记录集对象[打开](../../mfc/reference/crecordset-class.md#open)成员函数，**打开**构造使用的部分或全部以下成分的 SQL 语句：  
  
-   **LpszSQL**参数传递给**打开**。 如果不是**NULL**，此参数指定的自定义 SQL 字符串或其中一个的一部分。 框架分析字符串。 如果字符串为 SQL**选择**语句或 ODBC**调用**语句，框架会将字符串用作记录集的 SQL 语句。 如果字符串不以"SELECT"或"{调用"开头，框架将使用什么提供来构造 SQL **FROM**子句。  
  
-   返回的字符串[GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)。 默认情况下，这是为在向导中，记录集指定的表的名称，但你可以更改该函数返回。 框架调用`GetDefaultSQL`— 如果字符串不以"SELECT"或"{调用"开头，则假定要用于构造 SQL 字符串的表名称。  
  

-   字段数据成员的记录集，这将会绑定到特定列的表。 框架将记录列绑定到这些成员中，将它们用作缓冲区的地址。 框架到表中的列确定的字段数据成员的相关性[RFX](../../data/odbc/record-field-exchange-using-rfx.md)或批量 RFX 函数调用中记录集的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)成员函数。  
  
-   [筛选器](../../data/odbc/recordset-filtering-records-odbc.md)为记录集，如果有的话，将同时包含[m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)数据成员。 框架将使用此字符串构造 SQL**其中**子句。  
  
-   [排序](../../data/odbc/recordset-sorting-records-odbc.md)顺序记录集，如果任何，包含在[m_strSort](../../mfc/reference/crecordset-class.md#m_strsort)数据成员。 框架将使用此字符串构造 SQL **ORDER BY**子句。  

  
    > [!TIP]
    >  若要使用 SQL **GROUP BY**子句 (和可能**HAVING**子句)，将子句附加到你的筛选器字符串的末尾。  
  
-   值的任何[参数数据成员](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)指定类。 只需在调用之前设置参数值**打开**或**Requery**。 框架将绑定到的参数值"？"中的 SQL 字符串的占位符。 在编译时，你用占位符中指定的字符串。 在运行时，框架自动填写基于传递的参数值的详细信息。  
  
 **打开**构造 SQL**选择**从这些成分的语句。 请参阅[自定义所选内容](#_core_customizing_the_selection)有关框架如何使用这些成分的详细信息。  
  
 在构造此语句之后,**打开**将 SQL 发送到 ODBC 驱动程序管理器 （和 ODBC 游标库中，如果它是内存中），这将其发送到 ODBC 驱动程序的特定 DBMS。 驱动程序与 DBMS 数据源中的选定内容执行通信，并获取第一条记录。 框架将记录加载到记录集的字段数据成员。  
  
 你可以使用这些技术的组合以打开[表](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)并来构造该查询基于[联接](../../data/odbc/recordset-performing-a-join-odbc.md)的多个表。 使用其他自定义，可以调用[预定义查询](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)（存储的过程），选择表不在设计时已知的列和[绑定](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)它们到记录集字段或者让你可以执行大多数其他数据访问任务。 不能通过自定义记录集来完成的任务仍可通过[调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)或直接执行 SQL 语句与[CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)。  
  
##  <a name="_core_customizing_the_selection"></a> 自定义所选内容  
 除了提供筛选器、 排序顺序或参数，你可以执行以下操作以自定义记录集的选择：  
  
-   将自定义 SQL 字符串中的传递**lpszSQL**当调用[打开](../../mfc/reference/crecordset-class.md#open)为记录集。 任何内容中传递**lpsqSQL**优先于什么[GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)成员函数返回。  
  
     有关详细信息，请参阅[SQL： 自定义您记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)，其描述的类型的 SQL 语句 （或部分语句） 你可以将传递到**打开**和框架所执行的操作使用它们。  
  
    > [!NOTE]
    >  如果传递的自定义字符串不以"SELECT"或"{调用"开头，MFC 将假定它包含表名称。 这也适用于下一步的项目符号项。  
  
-   Alter 向导会将写入在你的记录集的字符串`GetDefaultSQL`成员函数。 编辑来更改它返回的函数的代码。 默认情况下，向导会将写入`GetDefaultSQL`返回单个表名称的函数。  
  
     你可以`GetDefaultSQL`返回任何项，可以传入**lpszSQL**参数**打开**。 如果不传递中的自定义 SQL 字符串**lpszSQL**，框架将使用该字符串，`GetDefaultSQL`返回。 至少，`GetDefaultSQL`必须返回一个表名。 但你可以使其返回多个表名称，完整**选择**语句，ODBC**调用**语句中，依次类推。 有关可以传递给列表**lpszSQL** — 或具有`GetDefaultSQL`返回 — 请参阅[SQL： 自定义您记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
     如果您正在执行两个或多个表的联接，重写`GetDefaultSQL`以自定义使用在 SQL 中的表列表**FROM**子句。 有关详细信息，请参阅[记录集： 执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)。  
  

-   手动将绑定可能根据你获取有关架构的信息的数据源在运行时的其他字段数据成员。 将字段数据成员添加到记录集类， [RFX](../../data/odbc/record-field-exchange-using-rfx.md)或批量 RFX 函数调用由他们[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)成员函数和类构造函数中的数据成员的初始化。 有关详细信息，请参阅[记录集： 动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
-   重写记录集成员函数，如`OnSetOptions`、 设置应用程序特定选项也可以重写默认值。  
  
 如果你想要使基于复杂的 SQL 语句的记录集，你需要使用这些自定义项技术的某种组合。 例如，你可能想要使用 SQL 子句和关键字不直接支持的记录集或可能是你要加入多个表。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 如何记录集更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [ODBC 基础知识](../../data/odbc/odbc-basics.md)   
 [SQL](../../data/odbc/sql.md)   
 [记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)