---
title: 记录集：对记录进行排序 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: 8b4deea1d8cbd4abe01ccc7a4114131378abe463
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366928"
---
# <a name="recordset-sorting-records-odbc"></a>记录集：对记录进行排序 (ODBC)

本主题适用于 MFC ODBC 类。

本主题介绍如何对记录集进行排序。 您可以指定一个或多个列，以这些列为基础排序，也可以指定升序或降序 **（ASC**或**DESC;****ASC**是每个指定列的默认值。 例如，如果指定两列，则记录首先在命名的第一列上排序，然后对命名的第二列进行排序。 SQL **ORDER BY**子句定义排序。 当框架将 ORDER **BY**子句追加到记录集的 SQL 查询时，子句将控制所选内容的顺序。

在构造对象后，但在调用对象`Open`成员函数之前（或在调用`Requery``Open`成员函数之前），必须建立记录集的排序顺序。

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>为记录集对象指定排序顺序

1. 构造新的记录集对象（或准备调用`Requery`现有记录集对象）。

1. 设置对象[m_strSort](../../mfc/reference/crecordset-class.md#m_strsort)数据成员的值。

   排序是 null 终止的字符串。 它包含**ORDER BY**子句的内容，但不包含关键字**ORDER BY**。 例如，使用：

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. 设置所需的任何其他选项，如筛选器、锁定模式或参数。

1. 调用`Open`新对象（或`Requery`现有对象）。

所选记录按指定顺序排序。 例如，要按姓氏（名字）降序排序一组学生记录，然后按名字排序，可以执行以下操作：

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

记录集包含所有学生记录，按姓氏按降序排序 （Z 到 A），然后按名字排序。

> [!NOTE]
> 如果选择通过将自己的 SQL 字符串传递给`Open`来覆盖记录集的默认 SQL 字符串，则如果自定义字符串具有 ORDER **BY**子句，请不要设置排序。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[记录集：筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
