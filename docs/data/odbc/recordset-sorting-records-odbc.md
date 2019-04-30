---
title: 记录集：排序记录 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: 831f21901186ed0ae010b0f332327eefcba94b51
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368625"
---
# <a name="recordset-sorting-records-odbc"></a>记录集：排序记录 (ODBC)

本主题适用于 MFC ODBC 类。

本主题说明如何对记录集进行排序。 可以指定要作为排序依据的一个或多个列，并可以指定按升序或降序 (**ASC**或**DESC**;**ASC**是默认值) 为每个指定的列。 例如，如果指定两个列，记录进行排序首先名为的第一列，然后单击名为的第二个列。 SQL **ORDER BY**子句定义一种。 当框架将追加**ORDER BY**到记录集的 SQL 子句的查询，所选内容的排序子句控制。

构造对象后，但在调用之前，必须建立记录集的排序顺序及其`Open`成员函数 (或在调用之前`Requery`现有记录集的成员函数对象，其`Open`已被成员函数以前调用过）。

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>若要指定记录集对象的排序顺序

1. 构造一个新的记录集对象 (或准备调用`Requery`一个现有的)。

1. 将对象的值设置[m_strSort](../../mfc/reference/crecordset-class.md#m_strsort)数据成员。

   排序是以 null 结尾的字符串。 它包含的内容**ORDER BY**子句，但不是关键字**ORDER BY**。 例如，使用：

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. 设置任何其他所需的选项，如筛选器、 锁定模式或参数。

1. 调用`Open`为新的对象 (或`Requery`现有对象)。

所选的记录进行排序所指定。 例如，要对一组学生记录由最后一个名称，则名字的降序进行排序，执行以下操作：

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

记录集包含的所有学生记录，以降序 (从 Z 到 A) 按姓氏排序，然后按名字。

> [!NOTE]
>  如果你选择覆盖通过将传递到你自己的 SQL 字符串的记录集的默认 SQL 字符串`Open`，如果自定义的字符串具有未设置一种**ORDER BY**子句。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[记录集：筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)