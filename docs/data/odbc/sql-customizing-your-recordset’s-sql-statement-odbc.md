---
title: "SQL：自定义记录集的 SQL 语句 (ODBC) | Microsoft Docs"
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
  - "自定义 SQL 语句"
  - "ODBC 记录集, SQL 语句"
  - "重写, SQL 语句"
  - "记录集, SQL 语句"
  - "SQL 语句, 自定义"
  - "SQL 语句, 记录集"
  - "SQL, 打开记录集"
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SQL：自定义记录集的 SQL 语句 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题说明：  
  
-   框架如何构造 SQL 语句  
  
-   如何重写 SQL 语句  
  
> [!NOTE]
>  此信息适用于 MFC ODBC 类。  如果使用的是 MFC DAO 类，请参见 DAO 帮助中的“Microsoft Jet 数据库引擎 SQL 和 ANSI SQL 比较”主题。  
  
## SQL 语句结构  
 记录集将记录选择主要建立在 SQL **SELECT** 语句的基础上。  当用向导声明类时，向导编写 `GetDefaultSQL` 成员函数的重写版本，类似于下面的语句（用于一个称为 `CAuthors` 的记录集）：  
  
```  
CString CAuthors::GetDefaultSQL()  
{  
    return "AUTHORS";  
}  
```  
  
 默认情况下，该重写返回用向导指定的表名。  此示例中，表名是“AUTHORS”。以后调用记录集的 **Open** 成员函数时，**Open** 构造的最终 **SELECT** 语句的形式如下：  
  
```  
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]   
       [ORDER BY m_strSort]  
```  
  
 在此语句中，通过调用 `GetDefaultSQL` 获取 `table-name`，从 `DoFieldExchange` 中的 RFX 函数调用获取 `rfx-field-list`。  虽然也可以用参数或筛选器修改默认语句，但这就是为 **SELECT** 语句所获取的内容，除非在运行时用重写版本替换它。  
  
> [!NOTE]
>  如果指定的列名包含（或可能包含）空格，则必须将名称括在方括号内。  例如，名称“First Name”应为“\[First Name\]”。  
  
 若要重写默认 **SELECT** 语句，请在调用 **Open** 时传递包含完整 **SELECT** 语句的字符串。  记录集并不构造它自己的默认字符串，而是使用您提供的字符串。  如果替换语句包含 **WHERE** 子句，则不要在 **m\_strFilter** 中指定筛选器，因为如果指定，则将有两个筛选语句。  同样，如果替换语句包含 **ORDER BY** 子句，则不要在 `m_strSort` 中指定排序，这样才不会有两个排序语句。  
  
> [!NOTE]
>  如果在筛选器（或 SQL 语句的其他部分）中使用字符串，则必须用 DBMS 特定的文本前缀和文本后缀字符（或多个字符）“括住”（包含在指定的分隔符之间）这些字符串。  
  
 根据所使用的 DBMS，对外部联接这样的操作可能还有特殊的语法要求。  使用 ODBC 函数从用于 DBMS 的驱动程序中获取该信息。  例如，为某一数据类型（如 **SQL\_VARCHAR**）调用 **::SQLGetTypeInfo** 来请求 **LITERAL\_PREFIX** 和 **LITERAL\_SUFFIX** 字符。  如果正在写与数据库无关的代码，请参见 MSDN Library 光盘上 ODBC SDK Programmer's Reference（ODBC SDK 程序员参考）中的附录 C 以了解详细的语法信息。  
  
 记录集对象构造用于选择记录的 SQL 语句，除非您传递自定义 SQL 语句。  该操作的完成方式主要取决于您在 **Open** 成员函数的 `lpszSQL` 参数中传递的值。  
  
 SQL **SELECT** 语句的一般形式为：  
  
```  
SELECT [ALL | DISTINCT] column-list FROM table-list  
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]  
```  
  
 将 **DISTINCT** 关键字添加到记录集的 SQL 语句的一种方法是将关键字嵌入 `DoFieldExchange` 的第一个 RFX 函数调用中。  例如：  
  
```  
...  
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);  
...  
```  
  
> [!NOTE]
>  只对以只读形式打开的记录集使用该方法。  
  
## 重写 SQL 语句  
 下表对要 **Open**（打开）的 `lpszSQL` 参数的几种可能情形进行了说明。  表后对表中的情况做了解释。  
  
 **lpszSQL 参数和结果 SQL 字符串**  
  
|Case|在 lpszSQL 中传递的内容|结果 SELECT 语句|  
|----------|----------------------|------------------|  
|1|**NULL**|**SELECT** *rfx\-field\-list* **FROM** *table\-name*<br /><br /> `CRecordset::Open` 调用 `GetDefaultSQL` 以获取表名。  结果字符串是情况 2 到情况 5 中的一种，具体取决于 `GetDefaultSQL` 的返回内容。|  
|2|表名|**SELECT** *rfx\-field\-list* **FROM** *table\-name*<br /><br /> 字段列表取自 `DoFieldExchange` 中的 RFX 语句。  如果 **m\_strFilter** 和 `m_strSort` 不为空，则添加 **WHERE** 和\/或 **ORDER BY** 子句。|  
|3 \*|完整的 **SELECT** 语句，但没有 **WHERE** 或 **ORDER BY** 子句|如所传递的内容。  如果 **m\_strFilter** 和 `m_strSort` 不为空，则添加 **WHERE** 和\/或 **ORDER BY** 子句。|  
|4 \*|完整的 **SELECT** 语句，具有 **WHERE** 和\/或 **ORDER BY** 子句|如所传递的内容。  **m\_strFilter** 和\/或 `m_strSort` 必须保持为空，否则将产生两个筛选器和\/或排序语句。|  
|5 \*|对存储过程的调用|如所传递的内容。|  
  
 \* `m_nFields` 必须少于或等于 **SELECT** 语句中指定的列数。  在 **SELECT** 语句中指定的每列的数据类型必须与相应的 RFX 输出列的数据类型相同。  
  
### 情况 1   lpszSQL \= NULL  
 记录集选择取决于当 `CRecordset::Open` 调用 `GetDefaultSQL` 时，后者返回的内容。  情况 2 到情况 5 描述了可能的字符串。  
  
### 情况 2   lpszSQL \= 表名  
 记录集使用记录字段交换 \(RFX\) 从列名生成列列表，列名是在记录集类的 `DoFieldExchange` 重写中的 RFX 函数调用中提供的。  如果使用了向导来声明记录集类，则该情况的结果与情况 1 相同（前提是传递的表名与在向导中指定的相同）。  如果不使用向导来编写类，则情况 2 是构造 SQL 语句的最简单方法。  
  
 下面的示例构造一个 SQL 语句，该语句从 MFC 数据库应用程序选择记录。  当框架调用 `GetDefaultSQL` 成员函数时，函数返回表名 `SECTION`。  
  
```  
CString CEnrollSet::GetDefaultSQL()  
{  
    return "SECTION";  
}  
```  
  
 为获取 SQL **SELECT** 语句的列名，框架调用 `DoFieldExchange` 成员函数。  
  
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
  
 完成后，SQL 语句类似于：  
  
```  
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo   
    FROM SECTION  
```  
  
### 情况 3   lpszSQL \= SELECT\/FROM 语句  
 手动指定列列表，而不是依赖 RFX 自动构造该列表。  可能要在以下时间执行该操作：  
  
-   想在 **SELECT** 后指定 **DISTINCT** 关键字。  
  
     列列表应按列名和类型在 `DoFieldExchange` 中列出的同一顺序来匹配列名和类型。  
  
-   有理由使用 ODBC 函数 **::SQLGetData** 手动检索列值，而不是依赖 RFX 为您绑定和检索列。  
  
     例如，您可能想要为新列提供空间，而这些新列是分发应用程序后您的应用程序客户添加到数据库表的。  您需要添加这些额外的字段数据成员，它们在使用向导声明类时是未知的。  
  
     列列表应按列名和类型在 `DoFieldExchange` 中列出的顺序来匹配列名和类型，后接手动绑定的列的名称。  有关详细信息，请参阅[记录集：动态绑定数据列 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
-   希望通过在 **FROM** 子句中指定多个表来联接表。  
  
     有关信息及示例，请参见 [记录集：执行联接 \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md)。  
  
### 情况 4   lpszSQL \= SELECT\/FROM 加 WHERE 和\/或 ORDER BY  
 指定全部内容：列列表（基于 `DoFieldExchange` 中的 RFX 调用）、表列表以及 **WHERE** 和\/或 **ORDER BY** 子句的内容。  如果用这种方法指定 **WHERE** 和\/或 **ORDER BY** 子句，则不使用 **m\_strFilter** 和\/或 `m_strSort`。  
  
### 情况 5   lpszSQL \= 存储过程调用  
 如果需要调用预定义查询（如 Microsoft SQL Server 数据库中的存储过程），必须在传递到 `lpszSQL` 的字符串中写 **CALL** 语句。  向导不支持为调用预定义查询声明记录集类。  并非所有的预定义查询都返回记录。  
  
 如果预定义查询不返回记录，则可以直接使用 `CDatabase` 成员函数 `ExecuteSQL`。  对于确实返回记录的预定义查询，还必须在 `DoFieldExchange` 中为过程返回的任何列手动写 RFX 调用。  RFX 调用的顺序和返回的类型都必须与预定义查询相同。  有关详细信息，请参阅[记录集：为预定义查询声明一个类 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)。  
  
## 请参阅  
 [SQL：SQL 和 C\+\+ 数据类型 \(ODBC\)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)   
 [SQL：进行直接 SQL 调用 \(ODBC\)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)