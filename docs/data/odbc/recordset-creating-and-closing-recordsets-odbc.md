---
title: 记录集：创建和关闭记录集 (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
ms.openlocfilehash: 155b51debfb6eacd3cbdd3293875274ca2dc4ab5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212974"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>记录集：创建和关闭记录集 (ODBC)

> [!NOTE]
> MFC ODBC 使用者向导在 Visual Studio 2019 及更高版本中不可用。 你仍可以手动创建使用者。

本主题适用于 MFC ODBC 类。

若要使用记录集，请构造记录集对象，然后调用其 `Open` 成员函数来运行记录集的查询并选择记录。 在结束使用记录集后，关闭并销毁对象。

本主题介绍：

- [何时以及如何创建记录集对象](#_core_creating_recordsets_at_run_time)。

- [何时以及如何通过参数化、筛选、排序或锁定记录集的行为来限定记录集的行为](#_core_setting_recordset_options)。

- [何时以及如何关闭记录集对象](#_core_closing_a_recordset)。

##  <a name="creating-recordsets-at-run-time"></a><a name="_core_creating_recordsets_at_run_time"></a> 在运行时创建记录集

在程序中创建记录集对象之前，通常需要首先编写特定于应用程序的记录集类。 有关此预备步骤的详细信息，请参阅[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。

需要从数据源中选择记录时，请打开动态集或快照对象。 要创建的对象类型取决于你需要对应用程序中的数据进行的操作以及 ODBC 驱动程序支持的内容。 有关详细信息，请参阅[动态集](../../data/odbc/dynaset.md)和[快照](../../data/odbc/snapshot.md)。

#### <a name="to-open-a-recordset"></a>打开记录集

1. 构造 `CRecordset` 派生的类的对象。

   可以在堆上或函数的堆栈帧上构造对象。

1. （可选）修改默认记录集行为。 有关可用选项，请参阅[设置记录集选项](#_core_setting_recordset_options)。

1. 调用对象的 [Open](../../mfc/reference/crecordset-class.md#open) 成员函数。

在构造函数中，传递指向 `CDatabase` 对象的指针或传递 NULL 以使用框架基于连接字符串构造和打开的临时数据库对象，此连接字符串由 [GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) 成员函数返回。 `CDatabase` 对象可能已经连接到数据源。

对 `Open` 的调用使用 SQL 来从数据源中选择记录。 选择的第一条记录（如果有）为当前记录。 此记录的字段的值存储在记录集对象的字段数据成员中。 如果选择了任何记录，`IsBOF` 和 `IsEOF` 成员函数则都返回 0。

在 [Open](../../mfc/reference/crecordset-class.md#open) 调用中，你可以：

- 指定记录集是动态集还是快照。 记录集默认作为快照打开。 或者，可以指定只进记录集，此记录集仅向前滚动，一次一条记录。

   默认情况下，记录集使用存储在 `CRecordset` 数据成员 `m_nDefaultType` 中的默认类型。 向导将编写代码以将 `m_nDefaultType` 初始化为你在向导中选择的记录集类型。 如果不接受此默认设置，可以替换另一个记录集类型。

- 指定字符串以替换记录集构造的默认 SQL SELECT 语句。

- 指定记录集是只读的还是仅追加的。 默认情况下，记录集允许完全更新，但可以将此限制为仅添加新记录，或者可以禁止所有更新。

以下示例演示了如何打开 `CStudentSet` 类的只读快照对象，此类是一个特定于应用程序的类：

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

调用 `Open` 后，使用对象的成员函数和数据成员来处理记录。 在某些情况下，你可能需要再次查询或刷新记录集来包含数据源上发生的更改。 有关详细信息，请参阅[记录集：重新查询记录集（ODBC）](../../data/odbc/recordset-requerying-a-recordset-odbc.md)。

> [!TIP]
>  你在开发期间使用的连接字符串可能与最终用户所需的连接字符串不同。 有关在这方面通用化应用程序的建议，请参阅[数据源：管理连接（ODBC）](../../data/odbc/data-source-managing-connections-odbc.md)。

##  <a name="setting-recordset-options"></a><a name="_core_setting_recordset_options"></a> 设置记录集选项

在你构造记录集对象之后但在调用 `Open` 来选择记录之前，你可能需要设置一些选项来控制记录集的行为。 对于所有记录集，你可以：

- 指定[筛选器](../../data/odbc/recordset-filtering-records-odbc.md)来约束记录选择。

- 为记录指定[排序](../../data/odbc/recordset-sorting-records-odbc.md)顺序。

- 指定[参数](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)，以便可以使用在运行时获取或计算的信息来选择记录。

如果满足条件，还可以设置以下选项：

- 如果记录集是可更新的并且支持锁定选项，则可以指定用于更新的[锁定](../../data/odbc/recordset-locking-records-odbc.md)方法。

> [!NOTE]
>  若要影响记录选择，必须在调用 `Open` 成员函数之前设置这些选项。

##  <a name="closing-a-recordset"></a><a name="_core_closing_a_recordset"></a> 关闭记录集

结束使用记录集后，必须对它进行处理，并解除它的内存分配。

#### <a name="to-close-a-recordset"></a>关闭记录集

1. 调用其 [Close](../../mfc/reference/crecordset-class.md#close) 成员函数。

1. 销毁记录集对象。

   如果在函数的堆栈帧上进行了声明，当对象超出作用域时，此对象将自动销毁。 否则，请使用 delete 运算符。

`Close` 释放记录集的 `HSTMT` 句柄。 它不会销毁 C++ 对象。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[记录集：添加、更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
