---
title: SQL:自定义记录集的 SQL 语句 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
ms.openlocfilehash: eabaab019ee94b0c5617573c534d920ec710e9b2
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036190"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL:自定义记录集的 SQL 语句 (ODBC)

本主题说明：

- 框架如何构造 SQL 语句

- 如何重写的 SQL 语句

> [!NOTE]
>  此信息适用于 MFC ODBC 类。 如果您正在使用 MFC DAO 类，请参阅"比较的 Microsoft Jet 数据库引擎 SQL 和 ANSI SQL"DAO 帮助中的主题。

## <a name="sql-statement-construction"></a>SQL 语句构造

记录集基主要在 SQL 上的选择记录**选择**语句。 当将您的类声明一个向导时，它将重写的版本`GetDefaultSQL`成员函数，如下所示 (记录集类名为`CAuthors`)。

```cpp
CString CAuthors::GetDefaultSQL()
{
    return "AUTHORS";
}
```

默认情况下，此重写返回使用向导指定的表名。 在示例中，表名称是"作者"。 当您更高版本调用记录集的`Open`成员函数`Open`构造最终**选择**窗体的语句：

```
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]
       [ORDER BY m_strSort]
```

其中`table-name`获取通过调用`GetDefaultSQL`并`rfx-field-list`与 RFX 函数调用中获取`DoFieldExchange`。 这是您获得**选择**语句，除非替换它重写版本与在运行时，虽然也可以修改默认的语句使用参数或筛选器。

> [!NOTE]
>  如果指定包含 （或可能包含） 空格的列名称，必须将名称括在方括号中。 例如，名称"名字"应为"[名字]"。

若要覆盖默认值**选择**语句，传递字符串，其中包含一个完整**选择**语句在调用时`Open`。 而不是构造自己的默认字符串，该记录集使用您提供的字符串。 如果替换语句包含**其中**子句中，未指定筛选器中的`m_strFilter`因为则可以使用两个筛选器语句。 同样，如果替换语句包含**ORDER BY**子句中，未指定排序中的`m_strSort`，以便不将具有两个排序语句。

> [!NOTE]
>  如果您的筛选器 （或 SQL 语句的其他部分） 中使用文本字符串，您可能需要"引用"（包含在指定的分隔符） 此类字符串与特定于 DBMS 的文字前缀和原义后缀字符 （或多个字符）。

具体取决于所使用的 DBMS，可能会遇到特殊的语法要求，对外部联接操作。 使用 ODBC 函数以从您的驱动程序为 DBMS 获取此信息。 例如，调用`::SQLGetTypeInfo`对于特定的数据类型，如`SQL_VARCHAR`、 请求的 LITERAL_PREFIX 和 LITERAL_SUFFIX 字符。 如果你正在编写独立于数据库的代码，请参阅[附录 c:SQL 语法](/sql/odbc/reference/appendixes/appendix-c-sql-grammar)中[ODBC 程序员参考](/sql/odbc/reference/odbc-programmer-s-reference)详细的语法的信息。

记录集对象构造它使用选择的记录，除非您传递自定义 SQL 语句的 SQL 语句。 如何做到这一点取决于主要中传递的值*lpszSQL*参数的`Open`成员函数。

SQL 的一般形式**选择**语句是：

```
SELECT [ALL | DISTINCT] column-list FROM table-list
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]
```

添加的一种方法**DISTINCT**记录集的 SQL 语句中的关键字是可以在中的第一个 RFX 函数调用中嵌入关键字`DoFieldExchange`。 例如：

```
...
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);
...
```

> [!NOTE]
>  此方法只能用于以只读方式打开的记录集。

## <a name="overriding-the-sql-statement"></a>重写的 SQL 语句

下表显示了这样一些可能性*lpszSQL*参数`Open`。 下表介绍了表中的情况。

**LpszSQL 参数和生成的 SQL 字符串**

|Case|您传递 lpszSQL|生成的 SELECT 语句|
|----------|------------------------------|------------------------------------|
|1|NULL|**SELECT** *rfx-field-list* **FROM** *table-name*<br /><br /> `CRecordset::Open` 调用`GetDefaultSQL`若要获取表名称。 生成的字符串是一个用例 2 到 5，具体取决于什么`GetDefaultSQL`返回。|
|2|表名称|**SELECT** *rfx-field-list* **FROM** *table-name*<br /><br /> 字段列表摘自中的 RFX 语句`DoFieldExchange`。 如果`m_strFilter`并`m_strSort`不为空，将添加**其中**和/或**ORDER BY**子句。|
|3 \*|完整**选择**语句但没有**其中**或**ORDER BY**子句|为通过。 如果`m_strFilter`并`m_strSort`不为空，将添加**其中**和/或**ORDER BY**子句。|
|4 \*|完整**选择**语句**其中**和/或**ORDER BY**子句|为通过。 `m_strFilter` 和/或`m_strSort`必须保留为空或两个筛选器和/或生成排序语句。|
|5 \*|对存储过程的调用|为通过。|

\* `m_nFields` 必须小于或等于在指定的列数**选择**语句。 每个列中指定的数据类型**选择**语句必须是相应的 RFX 输出列的数据类型相同。

### <a name="case-1---lpszsql--null"></a>Case 1   lpszSQL = NULL

记录集选择取决于什么`GetDefaultSQL`时，后者返回`CRecordset::Open`调用它。 用例 2 到 5 描述了可能的字符串。

### <a name="case-2---lpszsql--a-table-name"></a>案例 2 lpszSQL = 表名

记录集使用记录字段交换 (RFX) 生成的列名称的列列表中的 RFX 函数调用中的记录集类的重写提供`DoFieldExchange`。 如果向导用于声明您记录集的类，这种情况必须与用例 1 相同的结果 （前提是传递表名在向导中指定的相同）。 如果不使用向导来编写类，用例 2 是最简单的方法来构造 SQL 语句。

下面的示例构造从 MFC 数据库应用程序中选择记录的 SQL 语句。 当框架将调用`GetDefaultSQL`成员函数，该函数返回的表的名称`SECTION`。

```cpp
CString CEnrollSet::GetDefaultSQL()
{
    return "SECTION";
}
```

若要获取 SQL 的列的名称**选择**语句中，框架将调用`DoFieldExchange`成员函数。

```cpp
void CEnrollSet::DoFieldExchange(CFieldExchange* pFX)
{
    pFX->SetFieldType(CFieldExchange::outputColumn);
    RFX_Text(pFX, "CourseID", m_strCourseID);
    RFX_Text(pFX, "InstructorID", m_strInstructorID);
    RFX_Text(pFX, "RoomNo", m_strRoomNo);
    RFX_Text(pFX, "Schedule", m_strSchedule);
    RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

完成后，如下所示的 SQL 语句：

```sql
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo
    FROM SECTION
```

### <a name="case-3---lpszsql--a-selectfrom-statement"></a>Case 3   lpszSQL = a SELECT/FROM Statement

而不是依赖 RFX 自动构造的手动指定列列表。 您可能想要时采用此操作：

- 你想要指定**DISTINCT**关键字之后**选择**。

   列列表应与匹配的列名称和类型按相同顺序中所列`DoFieldExchange`。

- 您有理由手动检索列的值使用 ODBC 函数`::SQLGetData`而不是依赖 RFX 绑定并为你检索列。

   例如，可能想要适应分发应用程序后，你的应用程序的客户添加到数据库表的新列。 您需要添加已在类声明了一个向导时不知道这些额外字段数据成员。

   列列表应与匹配的列名称和类型按相同顺序中所列`DoFieldExchange`后, 跟手动绑定列的名称。 有关详细信息，请参阅[记录集：动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

- 你想要通过指定多个表中的联接表**FROM**子句。

   有关信息和示例，请参阅[记录集：执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)。

### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>用例 4 lpszSQL = SELECT / 从加上其中和/或 ORDER BY

指定的所有内容： 列的列表 (根据中的 RFX 调用`DoFieldExchange`)，表列表中和的内容**其中**和/或**ORDER BY**子句。 如果指定你**其中**和/或**ORDER BY**子句这样一来，不要使用`m_strFilter`和/或`m_strSort`。

### <a name="case-5---lpszsql--a-stored-procedure-call"></a>用例 5 lpszSQL = 存储过程调用

如果你需要调用预定义的查询 （如 Microsoft SQL Server 数据库中的存储过程），则必须编写**调用**中的字符串传递到语句*lpszSQL*。 向导不支持声明用于调用预定义的查询的记录集类。 并非所有预定义的查询返回的记录。

如果预定义的查询不返回记录，则可以使用`CDatabase`成员函数`ExecuteSQL`直接。 对于预定义查询返回的记录，手动必须编写调用 RFX`DoFieldExchange`该过程返回的任何列。 RFX 调用必须按相同顺序，并返回相同的类型，作为预定义的查询。 有关详细信息，请参阅[记录集：预定义的查询 (ODBC) 声明的类](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)。

## <a name="see-also"></a>请参阅

[SQL:SQL 和 c + + 数据类型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)<br/>
[SQL:进行直接 SQL 调用 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
