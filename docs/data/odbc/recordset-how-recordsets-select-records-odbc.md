---
title: 记录集：如何记录集选择记录 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
ms.openlocfilehash: 310481a6ea6637de817bf29d528cbdfe70ae70db
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041320"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>记录集：如何记录集选择记录 (ODBC)

本主题适用于 MFC ODBC 类。

本主题说明：

- [你的角色和您的选项中选择记录](#_core_your_options_in_selecting_records)。

- [记录集如何构造查询的 SQL 语句并选择记录](#_core_how_a_recordset_constructs_its_sql_statement)。

- [您可以如何自定义所选内容](#_core_customizing_the_selection)。

记录集从通过 ODBC 驱动程序的数据源中选择记录，通过将 SQL 语句发送到该驱动程序。 发送 SQL 取决于如何设计和打开记录集类。

##  <a name="_core_your_options_in_selecting_records"></a> 在选择记录的选项

下表中选择的记录显示你的选项。

### <a name="how-and-when-you-can-affect-a-recordset"></a>如何以及何时可能会影响记录集

|当你|你可以|
|--------------|-------------|
|声明在记录集类**添加类**向导|指定要从选择的表。<br /><br /> 指定要包含的列。<br /><br /> 请参阅[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。|
|完成您的记录集类实现|重写成员函数，如`OnSetOptions`（高级） 设置特定于应用程序的选项，或要更改默认值。 如果希望参数化记录集，则指定的参数数据成员。|
|构造一个记录集对象 (在调用之前`Open`)|指定在中使用的搜索条件 （可能是复合型）**其中**筛选记录的子句。 请参阅[记录集：筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。<br /><br /> 指定在中使用的排序顺序**ORDER BY**记录进行排序的子句。 请参阅[记录集：排序记录 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)。<br /><br /> 指定任何参数添加到类的参数值。 请参阅[记录集：参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。|

|通过调用运行记录集的查询`Open`|指定要替换由向导设置的默认 SQL 字符串的自定义 SQL 字符串。 请参阅[crecordset:: Open](../../mfc/reference/crecordset-class.md#open)中*类库参考*和[SQL:自定义记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。 |

|调用`Requery`再次查询记录集包含数据源中的最新值 |指定新的参数、 筛选或排序。 请参阅[记录集：再次查询记录集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)。 |

##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a> 记录集如何构造查询的 SQL 语句

当您调用记录集对象的[开放](../../mfc/reference/crecordset-class.md#open)成员函数`Open`构造 SQL 语句使用部分或全部以下要素：

- *LpszSQL*参数传递给`Open`。 如果不为 NULL，则此参数指定自定义 SQL 字符串或一个的一部分。 框架分析字符串。 如果字符串为 SQL**选择**语句或 ODBC**调用**语句，该框架使用字符串作为记录集的 SQL 语句。 如果字符串不以"SELECT"或"{CALL"开头，则框架将使用什么提供构造 SQL **FROM**子句。

- 返回的字符串[GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)。 默认情况下，这是在向导中，记录集指定的表的名称，但您可以更改该函数返回的内容。 框架将调用`GetDefaultSQL`-如果字符串不以"SELECT"或"{CALL"开头，则假定为表名，用来构造的 SQL 字符串。


- 字段数据成员的记录集，要绑定到表中的特定列。 该框架将记录列绑定到这些成员中，将它们用作缓冲区的地址。 框架到表中的列确定字段数据成员的相关[RFX](../../data/odbc/record-field-exchange-using-rfx.md)或批量 RFX 函数调用中的记录集[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)成员函数。

- [筛选器](../../data/odbc/recordset-filtering-records-odbc.md)记录集，如果有，将同时包含[m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)数据成员。 该框架使用此字符串来构造 SQL**其中**子句。

- [排序](../../data/odbc/recordset-sorting-records-odbc.md)排序记录集，如果任何，包含在[m_strSort](../../mfc/reference/crecordset-class.md#m_strsort)数据成员。 该框架使用此字符串来构造 SQL **ORDER BY**子句。

   > [!TIP]
   > 若要使用 SQL **GROUP BY**子句 (和可能**HAVING**子句)，将子句追加到筛选器字符串的末尾。

- 值的任何[的参数数据成员](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)指定类。 只需在调用之前设置参数值`Open`或`Requery`。 框架将绑定到的参数值"？"中的 SQL 字符串的占位符。 在编译时，指定与占位符的字符串。 在运行时，框架自动填入基于传递的参数值的详细信息。

`Open` 构造 SQL**选择**从这些因素的语句。 请参阅[自定义所选内容](#_core_customizing_the_selection)有关框架如何使用这些成分的详细信息。

构造语句之后,`Open`将 SQL 发送到 ODBC 驱动程序管理器 （和 ODBC 游标库是否在内存中），后者将其发送到的 ODBC 驱动程序为特定 DBMS。 驱动程序与 DBMS 就能执行的数据源中的选定内容进行通信，并获取第一条记录。 该框架将记录加载到记录集的字段数据成员。

可以使用这些方法的组合来打开[表](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)，并构造基于的查询[联接](../../data/odbc/recordset-performing-a-join-odbc.md)的多个表。 使用其他自定义，可以调用[预定义的查询](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)（存储的过程），选择表不在设计时已知的列和[绑定](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)到记录集字段或您可以执行大多数其他数据访问任务。 不能通过自定义记录集来完成的任务仍可以通过[调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)或直接执行 SQL 语句与[CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)。

##  <a name="_core_customizing_the_selection"></a> 自定义所选内容

除了提供筛选器、 排序顺序或参数，您可以执行以下操作以自定义记录集的选择：

- 将自定义 SQL 字符串中的传递*lpszSQL*当你调用[打开](../../mfc/reference/crecordset-class.md#open)记录集。 在传递的任何内容*lpsqSQL*优先于什么[GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)成员函数返回。

   有关详细信息，请参阅[SQL:自定义您的记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)，它描述了类型的 SQL 语句 （或部分语句） 可以传递给`Open`和框架与它们的用途。

    > [!NOTE]
    >  如果传递的自定义字符串不以"SELECT"或"{CALL"开头，MFC 将假定它包含表名称。 这同样适用于下一项目符号项。

- 更改字符串，该向导将在记录集中的写入`GetDefaultSQL`成员函数。 编辑函数的代码，以更改它返回的内容。 默认情况下，向导会将写入`GetDefaultSQL`返回单个表名称的函数。

   你可以`GetDefaultSQL`返回的任何项，可以传入*lpszSQL*参数`Open`。 如果不传递中的自定义 SQL 字符串*lpszSQL*，该框架使用的字符串的`GetDefaultSQL`返回。 至少，`GetDefaultSQL`必须返回单个表名称。 但您可以将该返回多个表名，完整**选择**语句，ODBC**调用**语句中，依次类推。 有关一系列可以传递给*lpszSQL* — 或具有`GetDefaultSQL`返回，请参阅[SQL:自定义记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。

   如果您正在执行的两个或多个表联接，重写`GetDefaultSQL`自定义在 SQL 中使用的表列表**FROM**子句。 有关详细信息，请参阅[记录集：执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)。


- 手动将其他字段数据成员，可能根据你获取有关架构的信息的数据源在运行时绑定。 将字段数据成员添加到记录集类中， [RFX](../../data/odbc/record-field-exchange-using-rfx.md)或批量 RFX 函数会调用由他们[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)成员函数和类构造函数中的数据成员的初始化。 有关详细信息，请参阅[记录集：动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

- 重写记录集成员函数，如`OnSetOptions`，可以设置特定于应用程序的选项或重写默认值。

如果你想要记录集的基础复杂的 SQL 语句，您需要使用这些自定义技术的某种组合。 例如，你可能想要使用 SQL 子句和关键字不直接支持的记录集或可能是您要联接多个表。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：如何记录集更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[ODBC 基础](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)