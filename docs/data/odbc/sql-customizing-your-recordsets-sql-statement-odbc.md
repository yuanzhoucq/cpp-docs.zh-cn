---
title: "SQL： 自定义记录集的 SQL 语句 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3099fbf6b97f3ad18a28c071fcd08ec8280fa24a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL：自定义记录集的 SQL 语句 (ODBC)
本主题说明：  
  
-   框架如何构造 SQL 语句  
  
-   如何重写的 SQL 语句  
  
> [!NOTE]
>  此信息适用于 MFC ODBC 类。 如果你正在使用 MFC DAO 类，请参阅主题"比较的 Microsoft Jet 数据库引擎 SQL 和 ANSI SQL"DAO 帮助中。  
  
## <a name="sql-statement-construction"></a>SQL 语句构造  
 记录集基均主要在 SQL 上的记录选择**选择**语句。 在你的类声明使用向导时，它写入的重写版本`GetDefaultSQL`如下所示的成员函数 (记录集类调用`CAuthors`)。  
  
```  
CString CAuthors::GetDefaultSQL()  
{  
    return "AUTHORS";  
}  
```  
  
 默认情况下，此重写返回时使用向导指定的表名称。 在示例中，表名为"作者"。 当您更高版本调用记录集的**打开**成员函数，**打开**构造最终**选择**窗体的语句：  
  
```  
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]   
       [ORDER BY m_strSort]  
```  
  
 其中`table-name`通过调用获取`GetDefaultSQL`和`rfx-field-list`从 RFX 函数调用中获取`DoFieldExchange`。 这是为所获取**选择**语句，除非它用替换重写版本在运行时，虽然你还可以修改默认语句又包含参数或筛选器。  
  
> [!NOTE]
>  如果指定的列名称包含 （或可能包含） 空间，必须将名称括在方括号中。 例如，名称"名字"应为"[名字]"。  
  
 重写默认**选择**语句，将包含一套完整的字符串传递**选择**语句在调用时**打开**。 而不是构造自己的默认字符串，该记录集使用您提供的字符串。 如果你替换语句包含**其中**子句，未指定中的筛选器**m_strFilter**因为然后会有两个筛选器语句。 同样，如果你替换语句包含**ORDER BY**子句，不指定中的排序`m_strSort`，以便不将具有两个排序语句。  
  
> [!NOTE]
>  如果你的筛选器 （或 SQL 语句的其他部分） 中使用文本字符串，你可能需要"quote"（包含在指定的分隔符） 此类字符串用特定于 DBMS 的文字前缀和文本后缀字符 （或多个字符）。  
  
 具体取决于所使用的 DBMS，你可能也会遇到特殊的语法要求，外部联接中，等操作。 使用 ODBC 函数为 DBMS 从您的驱动程序获取此信息。 例如，调用**:: SQLGetTypeInfo**对于特定数据类型，如**SQL_VARCHAR**、 请求**LITERAL_PREFIX**和**LITERAL_SUFFIX**字符。 如果你正在编写独立于数据库的代码，请参阅中的附录 C *ODBC SDK**程序员参考*详细的语法信息 MSDN 库 CD 上。  
  
 记录集对象构造它使用选择的记录，除非您传递自定义 SQL 语句的 SQL 语句。 如何做到这一点取决于主要中传递的值`lpszSQL`参数**打开**成员函数。  
  
 SQL 的一般形式**选择**语句是：  
  
```  
SELECT [ALL | DISTINCT] column-list FROM table-list  
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]  
```  
  
 一种方式添加**DISTINCT**到记录集的 SQL 语句的关键字是在中的第一个 RFX 函数调用中嵌入关键字`DoFieldExchange`。 例如:  
  
```  
...  
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);  
...  
```  
  
> [!NOTE]
>  此方法仅使用以只读方式打开的记录集。  
  
## <a name="overriding-the-sql-statement"></a>重写的 SQL 语句  
 下表显示了这样一些可能性：`lpszSQL`参数**打开**。 下表说明了表中的情况。  
  
 **LpszSQL 参数和生成的 SQL 字符串**  
  
|Case|你传递 lpszSQL|生成的 SELECT 语句|  
|----------|------------------------------|------------------------------------|  
|1|**NULL**|**选择** *rfx 字段列表* **FROM** *表名称*<br /><br /> `CRecordset::Open`调用`GetDefaultSQL`若要获取表名称。 生成的字符串是一个用例 2 至 5，具体取决于什么`GetDefaultSQL`返回。|  
|2|表名|**选择** *rfx 字段列表* **FROM** *表名称*<br /><br /> 字段列表则来自中的 RFX 语句`DoFieldExchange`。 如果**m_strFilter**和`m_strSort`都不为空，将添加**其中**和/或**ORDER BY**子句。|  
|3 *|完整**选择**语句但没有**其中**或**ORDER BY**子句|为通过。 如果**m_strFilter**和`m_strSort`都不为空，将添加**其中**和/或**ORDER BY**子句。|  
|4 *|完整**选择**语句**其中**和/或**ORDER BY**子句|为通过。 **m_strFilter**和/或`m_strSort`必须保持为空，要么是两个筛选器和/或排序语句生成。|  
|5 *|对存储过程的调用|为通过。|  
  
 \*`m_nFields`必须小于或等于的中指定的列数**选择**语句。 每个列中指定的数据类型**选择**语句必须是与对应的 RFX 输出列的数据类型相同。  
  
### <a name="case-1---lpszsql--null"></a>案例 1 lpszSQL = NULL  
 记录集选择取决于什么`GetDefaultSQL`时，后者返回`CRecordset::Open`调用它。 情况 2 到 5 情况描述了可能的字符串。  
  
### <a name="case-2---lpszsql--a-table-name"></a>情况 2 lpszSQL = 表名称  
 记录集使用记录字段交换 (RFX) 来生成从列名称的列列表中的 RFX 函数调用中的记录集类的重写提供`DoFieldExchange`。 如果向导用于声明记录集类，这种情况下将具有相同的结果作为情况 1 （前提是你传递的向导中指定的表名相同）。 如果不使用向导来编写类，则情况 2 是构造 SQL 语句的最简单方法。  
  
 下面的示例构造从 MFC 数据库应用程序中选择记录的 SQL 语句。 当框架调用`GetDefaultSQL`成员函数，该函数将返回表的名称， `SECTION`。  
  
```  
CString CEnrollSet::GetDefaultSQL()  
{  
    return "SECTION";  
}  
```  
  
 列的名称获取 SQL**选择**语句，框架调用`DoFieldExchange`成员函数。  
  
```  
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
  
```  
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo   
    FROM SECTION  
```  
  
### <a name="case-3---lpszsql--a-selectfrom-statement"></a>情况 3 lpszSQL = SELECT / 从语句  
 而不是依赖 RFX 自动构造的手动指定列列表。 你可能想要这样做：  
  
-   你想要指定**DISTINCT**关键字以下**选择**。  
  
     列列表应与匹配的列名称和类型的相同顺序如中列出`DoFieldExchange`。  
  
-   您有理由手动检索列的值使用 ODBC 函数**:: SQLGetData**而不是依赖 RFX 绑定以及为你检索列。  
  
     例如，可能会想以容纳新的列分发应用程序后，你的应用程序的客户添加到数据库表。 你需要添加已在类声明使用向导时不知道这些额外字段数据成员。  
  
     列列表应与匹配的列名称和类型的相同顺序如中列出`DoFieldExchange`后, 跟手动绑定的列的名称。 有关详细信息，请参阅[记录集： 动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
-   你想要通过指定多个表中的联接表**FROM**子句。  
  
     有关信息和示例，请参阅[记录集： 执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)。  
  
### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>用例 4 lpszSQL = 选择 / 从加上其中和/或 ORDER BY  
 指定的所有内容： 列列表 (根据中的 RFX 调用`DoFieldExchange`)，表列表中和内容**其中**和/或**ORDER BY**子句。 如果你指定你**其中**和/或**ORDER BY**子句这样一来，不要使用**m_strFilter**和/或`m_strSort`。  
  
### <a name="case-5---lpszsql--a-stored-procedure-call"></a>用例 5 lpszSQL = 存储过程调用  
 如果你需要调用预定义的查询 （如 Microsoft SQL Server 数据库中的存储过程），则必须编写**调用**语句中的字符串传递给`lpszSQL`。 向导不支持声明用于调用预定义的查询的记录集类。 并非所有预定义的查询返回的记录。  
  
 如果预定义的查询不返回记录，则可以使用`CDatabase`成员函数`ExecuteSQL`直接。 对于预定义的查询返回的记录，你必须手动编写 RFX 调用`DoFieldExchange`过程对于任何列返回。 RFX 调用必须处于相同的顺序，并返回相同的类型，作为预定义的查询。 有关详细信息，请参阅[记录集： 声明一个类的预定义的查询 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)。  
  
## <a name="see-also"></a>请参阅  
 [SQL: SQL 和 c + + 数据类型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)   
 [SQL：进行直接 SQL 调用 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
