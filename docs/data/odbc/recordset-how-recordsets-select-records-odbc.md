---
title: 记录集：记录集如何选择记录 (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
ms.openlocfilehash: 4b446d69651cb3cf52bd6c15899d85ed76b319da
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079810"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>记录集：记录集如何选择记录 (ODBC)

> [!NOTE]
> MFC ODBC 使用者向导在 Visual Studio 2019 及更高版本中不可用。 你仍可以手动创建使用者。

本主题适用于 MFC ODBC 类。

本主题介绍：

- [选择记录时你的角色和选项](#_core_your_options_in_selecting_records)。

- [记录集如何构造其 SQL 语句并选择记录](#_core_how_a_recordset_constructs_its_sql_statement)。

- [可以如何自定义选择](#_core_customizing_the_selection)。

记录集通过将 SQL 语句发送给 ODBC 驱动程序来通过此驱动程序从数据源中选择记录。 发送的 SQL 取决于设计和打开记录集类的方式。

##  <a name="your-options-in-selecting-records"></a><a name="_core_your_options_in_selecting_records"></a> 选择记录时的选项

下表显示了选择记录时的选项。

### <a name="how-and-when-you-can-affect-a-recordset"></a>如何以及何时会影响记录集

|当你|你可以|
|--------------|-------------|
|使用“添加类”向导声明记录集类时|指定要从中进行选择的表。<br /><br /> 指定要包含的列。<br /><br /> 请参阅[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。|
|完成记录集类实现时|替代 `OnSetOptions`（高级）等成员函数以设置特定于应用程序的选项或更改默认设置。 如果需要参数化记录集，请指定参数数据成员。|
|构造记录集对象（在调用 `Open` 之前）|指定搜索条件（可能是复合条件），以便在筛选记录的 WHERE 子句中使用。 请参阅[记录集：筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。<br /><br /> 指定排序顺序，以便在对记录进行排序的 ORDER BY 子句中使用。 请参阅[记录集：对记录进行排序 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)。<br /><br /> 为添加到类中的任何参数指定参数值。 请参阅[记录集：参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。|

|通过调用 `Open` 运行记录集的查询|指定自定义 SQL 字符串以替换向导设置的默认 SQL 字符串。 请参阅类库参考中的 [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) 和 [SQL：自定义记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。|

|调用 `Requery` 以使用数据源上的最新值再次查询记录集|指定新参数、筛选器或排序。 请参阅[记录集：再次查询记录集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)。|

##  <a name="how-a-recordset-constructs-its-sql-statement"></a><a name="_core_how_a_recordset_constructs_its_sql_statement"></a> 记录集如何构造其 SQL 语句

调用记录集对象的 [Open](../../mfc/reference/crecordset-class.md#open) 成员函数时，`Open` 将使用以下部分或全部成分构造 SQL 语句：

- 传递给 `Open` 的 lpszSQL 参数。 如果不为 NULL，此参数将指定自定义 SQL 字符串或其中一部分。 框架将分析字符串。 如果字符串是 SQL SELECT 语句或 ODBC CALL 语句，框架则将此字符串用作记录集的 SQL 语句。 如果字符串不以“SELECT”或“{CALL”开头，框架则将使用提供的内容来构造 SQL FROM 子句。

- 由 [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) 返回的字符串。 默认情况下，这是你在向导中为记录集指定的表的名称，但可以更改函数返回的内容。 框架调用 `GetDefaultSQL` - 如果字符串不以“SELECT”或“{CALL”开头，则假定它是一个表名，用于构造 SQL 字符串。

- 记录集的字段数据成员，它们将被绑定到表的特定列。 框架将记录列绑定到这些成员的地址，将它们用作缓冲区。 框架将根据记录集的 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 或 [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 成员函数中的 [RFX](../../data/odbc/record-field-exchange-using-rfx.md) 或批量 RFX 函数调用来确定字段数据成员与表列的关联。

- [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) 数据成员中包含的记录集的[筛选器](../../data/odbc/recordset-filtering-records-odbc.md)（如果有）。 框架将使用此字符串来构造 SQL WHERE 子句。

- [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) 数据成员中包含的记录集的[排序](../../data/odbc/recordset-sorting-records-odbc.md)顺序（如果有）。 框架将使用此字符串来构造 SQL ORDER BY 子句。

   > [!TIP]
   > 若要使用 SQL GROUP BY 子句（可能是 HAVING 子句），请将子句追加到筛选器字符串的末尾。

- 为类指定的任何[参数数据成员](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)的值。 在调用 `Open` 或 `Requery` 之前设置参数值。 框架将参数值绑定到 SQL 字符串中的“?”占位符。 在编译时，使用占位符指定字符串。 在运行时，框架将根据传递的参数值填充详细信息。

`Open` 将从这些成分构造 SQL SELECT 语句。 有关框架如何使用成分的详细信息，请参阅[自定义选择](#_core_customizing_the_selection)。

在构造语句之后，`Open` 将 SQL 发送到 ODBC 驱动程序管理器（如果它在内存中，则发送到 ODBC 游标库），这会将它发送到特定 DBMS 的 ODBC 驱动程序。 此驱动程序将与 DBMS 通信以对数据源执行选择并提取第一条记录。 框架会将记录加载到记录集的字段数据成员中。

可以结合使用这些技术打开[表](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)，并根据多个表的[联接](../../data/odbc/recordset-performing-a-join-odbc.md)构造查询。 通过其他自定义，可以调用[预定义查询](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)（存储过程）、选择在设计时未知的表列，并将这些表列[绑定](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)到记录集字段，或者可以执行大多数其他数据访问任务。 通过[调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)或使用 [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) 直接执行 SQL 语句，仍然可以完成通过自定义记录集无法完成的任务。

##  <a name="customizing-the-selection"></a><a name="_core_customizing_the_selection"></a> 自定义选择

除了提供筛选器、排序顺序或参数之外，还可以执行以下操作来自定义记录集的选择：

- 为记录集调用 [Open](../../mfc/reference/crecordset-class.md#open) 时，在 lpszSQL 中传递自定义 SQL 字符串。 在 lpsqSQL 中传递的任何内容优先于 [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) 成员函数返回的内容。

   有关详细信息，请参阅 [SQL：自定义记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)，它介绍了可以传递到 `Open` 的 SQL 语句（或部分语句）的类型以及框架对它们的作用。

    > [!NOTE]
    >  如果传递的自定义字符串不以“SELECT”或“{CALL”开头，MFC 则假定它包含表名。 这同样适用于下一个项目符号项。

- 更改向导在记录集的 `GetDefaultSQL` 成员函数中写入的字符串。 编辑函数的代码以更改它返回的内容。 默认情况下，向导将编写一个 `GetDefaultSQL` 函数，此函数将返回单个表名。

   可以让 `GetDefaultSQL` 将可以传入到 lpszSQL 参数中的任何项返回到 `Open`。 如果未在 lpszSQL 中传递自定义 SQL 字符串，框架则将使用 `GetDefaultSQL` 返回的字符串。 至少，`GetDefaultSQL` 必须返回单个表名。 但是可以让它返回多个表名、一个完整的 SELECT 语句、一个 ODBC CALL 语句等。 有关可以传递给 lpszSQL 的内容的列表 - 或者让 `GetDefaultSQL` 返回的内容的列表 - 请参阅 [SQL：自定义记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。

   如果要执行两个或多个表的联接，请重写 `GetDefaultSQL` 以自定义 SQL FROM 子句中使用的表列表。 有关详细信息，请参阅[记录集：执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)。

- 手动绑定其他字段数据成员，可能基于在运行时获取的有关数据源架构的信息。 将字段数据成员添加到记录集类，[RFX](../../data/odbc/record-field-exchange-using-rfx.md) 或批量 RFX 函数调用它们到 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 或 [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) 成员函数，以及类构造函数中数据成员的初始化。 有关详细信息，请参阅[记录集：动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

- 替代 `OnSetOptions` 等记录集成员函数以设置特定于应用程序的选项或替代默认设置。

如果要将记录集基于复杂的 SQL 语句，则需要使用这些自定义技术的一些组合。 例如，可能想使用不受记录集直接支持的 SQL 子句和关键字，或者可能要联接多个表。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：记录集如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[ODBC 基础](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)