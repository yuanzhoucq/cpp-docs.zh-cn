---
title: 记录集：筛选记录 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
ms.openlocfilehash: 2e742ee02e142fd87df3f149379d9971c4acd166
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212898"
---
# <a name="recordset-filtering-records-odbc"></a>记录集：筛选记录 (ODBC)

本主题适用于 MFC ODBC 类。

本主题说明如何筛选记录集，以便只选择可用记录的特定子集。 例如，您可能希望仅选择特定课程的类节，如 MATH101。 筛选器是由 SQL **WHERE**子句的内容定义的搜索条件。 当框架将其追加到记录集的 SQL 语句时， **WHERE**子句会限制选择。

你必须在构造对象之后但在调用其 `Open` 成员函数之前建立记录集对象的筛选器（或在为之前调用了其 `Open` 成员函数的现有记录集对象调用 `Requery` 成员函数之前）。

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>为记录集对象指定筛选器

1. 构造新的记录集对象（或准备调用现有对象 `Requery`）。

1. 设置对象的[m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)数据成员的值。

   筛选器是一个以 null 结尾的字符串，其中包含 SQL **WHERE**子句的内容，而不是关键字**where**。 例如，使用：

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  文本字符串 "MATH101" 在上面用单引号引起来。 在 ODBC SQL 规范中，用单引号表示字符串文本。 在这种情况下，请查看 ODBC 驱动程序文档以了解 DBMS 的报价要求。 本主题末尾附近还进一步讨论了此语法。

1. 设置所需的任何其他选项，例如，排序顺序、锁定模式或参数。 指定参数特别有用。 有关参数化筛选器的信息，请参阅[记录集：参数化记录集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

1. 为新对象调用 `Open` （对于先前打开的对象，则为 `Requery`）。

> [!TIP]
>  在筛选器中使用参数可能是检索记录最有效的方法。

> [!TIP]
>  记录集筛选器对于[联接](../../data/odbc/recordset-performing-a-join-odbc.md)表和使用基于在运行时获取或计算的信息的[参数](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)非常有用。

记录集仅选择符合您指定的搜索条件的记录。 例如，若要指定上述课程筛选器（假设当前已设置了变量 `strCourseID` 例如，设置为 "MATH101"），请执行以下操作：

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

记录集包含 MATH101 的所有类节的记录。

请注意，在上面的示例中，使用字符串变量设置筛选器字符串的方式。 这是典型的用法。 但假设您希望为课程 ID 指定文本值100。 下面的代码演示如何使用文本值正确设置筛选器字符串：

```
m_strFilter = "StudentID = '100'";   // correct
```

请注意使用单引号字符;如果直接设置筛选器字符串，则筛选器字符串**不**是：

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

上面所示的引用符合 ODBC 规范，但某些 Dbms 可能需要其他引号字符。 有关详细信息，请参阅[sql：自定义记录集的 SQL 语句（ODBC）](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。

> [!NOTE]
>  如果选择通过将自己的 SQL 字符串传递到 `Open`来替代记录集的默认 SQL 字符串，则不应设置筛选器（如果自定义字符串具有**WHERE**子句）。 有关替代默认 SQL 的详细信息，请参阅[sql：自定义记录集的 SQL 语句（ODBC）](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：对记录进行排序 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[记录集：记录集如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[记录集：记录集如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
