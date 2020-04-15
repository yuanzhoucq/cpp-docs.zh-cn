---
title: SQL：自定义记录集的 SQL 语句 (ODBC)
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
ms.openlocfilehash: 083d268d2b2f2eef072809b1afde9d6ea34f6996
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374518"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL：自定义记录集的 SQL 语句 (ODBC)

本主题介绍：

- 框架如何构造 SQL 语句

- 如何重写 SQL 语句

> [!NOTE]
> 此信息适用于 MFC ODBC 类。 如果您正在使用 MFC DAO 类，请参阅 DAO 帮助中的主题"微软喷气数据库引擎 SQL 和 ANSI SQL 的比较"。

## <a name="sql-statement-construction"></a>SQL 语句构造

记录集主要基于 SQL **SELECT**语句选择记录。 使用向导声明类时，它会编写一个类似于这样的`GetDefaultSQL`成员函数的重写版本（对于称为`CAuthors`的记录集类）。

```cpp
CString CAuthors::GetDefaultSQL()
{
    return "AUTHORS";
}
```

默认情况下，此覆盖返回使用向导指定的表名称。 在此示例中，表名称为"问题"。 稍后调用记录集`Open`的成员函数时，`Open`构造窗体的最终**SELECT**语句：

```
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]
       [ORDER BY m_strSort]
```

其中`table-name`通过调用`GetDefaultSQL`获得，并从`rfx-field-list`中的`DoFieldExchange`RFX 函数调用获得。 这是**选择**语句的启用，除非您在运行时将其替换为重写版本，尽管您也可以使用参数或筛选器修改默认语句。

> [!NOTE]
> 如果指定包含（或可能包含）空格的列名称，则必须将名称括在方括号中。 例如，"名字"的名称应为"[名字]。

要重写默认**SELECT**语句，请在调用`Open`时传递包含完整**SELECT**语句的字符串。 记录集使用您提供的字符串，而不是构造自己的默认字符串。 如果替换语句包含**WHERE**子句，请不要指定筛选器，`m_strFilter`因为您将有两个筛选器语句。 同样，如果替换语句包含 ORDER **BY**子句，则不要指定 排序`m_strSort`，这样您就不会有两个排序语句。

> [!NOTE]
> 如果在筛选器（或 SQL 语句的其他部分）中使用文本字符串，则可能需要使用特定于 DBMS 的文本前缀和文本后缀字符（或字符）来"报价"（在指定的分隔符中）引用此类字符串。

根据 DBMS，您可能还会遇到外部联接等操作的特殊语法要求。 使用 ODBC 函数从 DBMS 的驱动程序获取此信息。 例如，调用`::SQLGetTypeInfo`特定数据类型（如`SQL_VARCHAR`）以请求LITERAL_PREFIX和LITERAL_SUFFIX字符。 如果要编写与数据库无关的代码，请参阅[ODBC 程序员参考](/sql/odbc/reference/odbc-programmer-s-reference)中的[附录 C：SQL 语法](/sql/odbc/reference/appendixes/appendix-c-sql-grammar)，了解详细的语法信息。

记录集对象构造它用来选择记录的 SQL 语句，除非您传递自定义 SQL 语句。 如何做到这一点主要取决于您在`Open`成员函数的*lpszSQL*参数中传递的值。

SQL **SELECT**语句的一般形式是：

```
SELECT [ALL | DISTINCT] column-list FROM table-list
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]
```

将**DISTINCT**关键字添加到记录集的 SQL 语句的一种方法是在 中的第一个 RFX 函数调用`DoFieldExchange`中嵌入该关键字。 例如：

```
...
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);
...
```

> [!NOTE]
> 仅此技术将打开为只读的记录集使用。

## <a name="overriding-the-sql-statement"></a>重写 SQL 语句

下表显示了*lpszSQL*参数到`Open`的可能性。 下表中的案例在表之后进行说明。

**lpszSQL 参数和生成的 SQL 字符串**

|案例|您在 lpszSQL 中传递的内容|生成的 SELECT 语句|
|----------|------------------------------|------------------------------------|
|1|Null|**从***表名***中选择** *rfx 字段列表*<br /><br /> `CRecordset::Open`调用`GetDefaultSQL`以获取表名称。 生成的字符串是案例 2 到 5 之一，`GetDefaultSQL`具体取决于返回的内容。|
|2|表名称|**从***表名***中选择** *rfx 字段列表*<br /><br /> 字段列表取自 中的`DoFieldExchange`RFX 语句。 如果`m_strFilter``m_strSort`和 不是空，则添加**WHERE**和/或**ORDER BY**子句。|
|3\*|完整的**SELECT**语句，但没有**WHERE**或**ORDER BY**子句|通过。 如果`m_strFilter``m_strSort`和 不是空，则添加**WHERE**和/或**ORDER BY**子句。|
|4\*|带有**WHERE**和/或 ORDER **BY**子句的完整**SELECT**语句|通过。 `m_strFilter`和/或`m_strSort`必须保持空，或生成两个筛选器和/或排序语句。|
|5\*|对存储过程的调用|通过。|

\*`m_nFields`必须小于或等于**SELECT**语句中指定的列数。 **SELECT**语句中指定的每列的数据类型必须与相应 RFX 输出列的数据类型相同。

### <a name="case-1---lpszsql--null"></a>案例 1 lpszSQL = NULL

记录集选择取决于调用时`GetDefaultSQL``CRecordset::Open`返回的内容。 案例 2 到 5 描述可能的字符串。

### <a name="case-2---lpszsql--a-table-name"></a>案例 2 lpszSQL = 表名称

记录集使用记录字段交换 （RFX） 从记录集类重写 中的 RFX 函数调用中提供的列名称生成列列表`DoFieldExchange`。 如果使用向导声明记录集类，则此案例的结果与案例 1 相同（前提是传递您在向导中指定的表名）。 如果不使用向导编写类，则案例 2 是构造 SQL 语句的最简单方法。

下面的示例构造一个 SQL 语句，该语句从 MFC 数据库应用程序中选择记录。 当框架调用`GetDefaultSQL`成员函数时，该函数将返回表的名称`SECTION`。

```cpp
CString CEnrollSet::GetDefaultSQL()
{
    return "SECTION";
}
```

要获取 SQL **SELECT**语句的列名称，框架将调用`DoFieldExchange`成员函数。

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

完成后，SQL 语句如下所示：

```sql
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo
    FROM SECTION
```

### <a name="case-3---lpszsql--a-selectfrom-statement"></a>案例 3 lpszSQL = SELECT/FROM 语句

您可以手动指定列列表，而不是依靠 RFX 自动构造它。 您可能需要在：

- 您希望在**SELECT**之后指定 **"指定**"关键字。

   列列表应按与 在 中`DoFieldExchange`列出的列名称和类型的顺序匹配。

- 您有理由使用 ODBC 函数`::SQLGetData`手动检索列值，而不是依赖 RFX 为您绑定和检索列。

   例如，您可能希望容纳应用程序客户在应用程序分发后添加到数据库表的新列。 您需要添加这些额外的字段数据成员，这些成员在使用向导声明类时并不知道。

   列列表应按与 列`DoFieldExchange`名称和类型的顺序匹配，后跟手动绑定列的名称。 有关详细信息，请参阅[记录集：动态绑定数据列 （ODBC）。](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- 您希望通过在**FROM**子句中指定多个表来联接表。

   有关信息和示例，请参阅[记录集：执行联接 （ODBC）。](../../data/odbc/recordset-performing-a-join-odbc.md)

### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>案例 4 lpszSQL = 选择/从+WHERE 和/或 ORDER BY

指定所有内容：列列表（基于 中的`DoFieldExchange`RFX 调用），表列表以及**WHERE**和/或 ORDER **BY**子句的内容。 如果以这种方式指定**WHERE**和/或**ORDER BY**子句，请不要`m_strFilter`使用 和`m_strSort`/或 。

### <a name="case-5---lpszsql--a-stored-procedure-call"></a>案例 5 lpszSQL = 存储过程调用

如果需要调用预定义的查询（如 Microsoft SQL Server 数据库中的存储过程），则必须在传递给*lpszSQL*的字符串中编写**CALL**语句。 向导不支持声明用于调用预定义查询的记录集类。 并非所有预定义的查询都返回记录。

如果预定义的查询不返回记录，则可以直接使用`CDatabase`成员函数。 `ExecuteSQL` 对于返回记录的预定义查询，还必须手动`DoFieldExchange`为过程返回的任何列写入 RFX 调用。 RFX 调用必须按与预定义的查询相同的顺序返回相同的类型。 有关详细信息，请参阅[记录集：为预定义查询 （ODBC） 声明类](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)。

## <a name="see-also"></a>另请参阅

[SQL：SQL 和 C++ 数据类型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)<br/>
[SQL：进行直接 SQL 调用 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
