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
ms.openlocfilehash: 56b8c4f52ec294f58a760e1309d32aa81286ddec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367017"
---
# <a name="recordset-filtering-records-odbc"></a>记录集：筛选记录 (ODBC)

本主题适用于 MFC ODBC 类。

本主题介绍如何筛选记录集，以便它仅选择可用记录的特定子集。 例如，您可能只想为特定课程（如 MATH101）选择类节。 筛选器是由 SQL **WHERE**子句的内容定义的搜索条件。 当框架将其追加到记录集的 SQL 语句时 **，WHERE**子句将约束选择。

在构造对象后，但在调用其成员`Open`函数之前（或在调用成员函数之前），必须建立记录集对象的筛选器（或在调用以前`Requery`调用其成员`Open`函数的现有记录集对象的成员函数之前）。

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>为记录集对象指定筛选器

1. 构造新的记录集对象（或准备调用`Requery`现有对象）。

1. 设置对象[m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)数据成员的值。

   筛选器是一个空端接字符串，其中包含 SQL **WHERE**子句的内容，但不包含关键字**WHERE**。 例如，使用：

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  文本字符串"MATH101"上面用单个引号显示。 在 ODBC SQL 规范中，单个引号用于表示字符串文本。 在这种情况下，请查看您的 ODBC 驱动程序文档以了解 DBMS 的报价要求。 此语法在本主题末尾也进一步讨论。

1. 设置所需的任何其他选项，如排序顺序、锁定模式或参数。 指定参数特别有用。 有关对筛选器进行参数化的信息，请参阅[记录集：参数化记录集 （ODBC）。](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

1. 调用`Open`新对象（或`Requery`以前打开的对象）。

> [!TIP]
> 在筛选器中使用参数可能是检索记录的最有效方法。

> [!TIP]
> 记录集筛选器可用于[联接](../../data/odbc/recordset-performing-a-join-odbc.md)表和使用基于在运行时获得或计算的信息的[参数](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

记录集仅选择满足您指定的搜索条件的记录。 例如，要指定上述课程筛选器（假设当前设置的变量`strCourseID`，例如设置为"MATH101"），请执行以下操作：

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

记录集包含 MATH101 的所有类部分的记录。

请注意，使用字符串变量在上面的示例中如何设置筛选器字符串。 这是典型的用法。 但是，假设您要为课程 ID 指定文本值 100。 以下代码演示如何使用文本值正确设置筛选器字符串：

```
m_strFilter = "StudentID = '100'";   // correct
```

请注意使用单引号字符;如果直接设置筛选器字符串，则筛选器字符串**不是**：

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

上面显示的报价符合 ODBC 规范，但某些 DBMS 可能需要其他报价字符。 有关详细信息，请参阅[SQL：自定义记录集的 SQL 语句 （ODBC）。](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

> [!NOTE]
> 如果选择通过将自己的 SQL 字符串传递给`Open`来覆盖记录集的默认 SQL 字符串，则如果自定义字符串具有**WHERE**子句，则不应设置筛选器。 有关重写默认 SQL 的详细信息，请参阅[SQL：自定义记录集的 SQL 语句 （ODBC）。](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：对记录进行排序 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[记录集：记录集如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[记录集：记录集如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
