---
title: 记录集：创建和关闭记录集 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
ms.openlocfilehash: d98f7e59e52b86a1b9b1c3ffac5c3e7160e6c36d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581501"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>记录集：创建和关闭记录集 (ODBC)

本主题适用于 MFC ODBC 类。

若要使用记录集，构造一个记录集对象，然后调用其`Open`成员函数以运行记录集的查询，并选择记录。 完成与该记录集后，关闭并销毁对象。

本主题说明：

- [何时以及如何创建记录集对象](#_core_creating_recordsets_at_run_time)。

- [何时以及如何可以限定通过参数化、 筛选、 排序，或锁定的记录集的行为](#_core_setting_recordset_options)。

- [何时以及如何关闭记录集对象](#_core_closing_a_recordset)。

##  <a name="_core_creating_recordsets_at_run_time"></a> 在运行时创建记录集

您可以在程序中创建记录集对象之前，您通常会编写应用程序特定的记录集类。 有关此预备步骤的详细信息，请参阅[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。

当您需要从数据源选择记录时，请打开动态集或快照的对象。 要创建的对象类型取决于您需要在你的应用程序和哪些 ODBC 驱动程序支持的数据。 有关详细信息，请参阅[动态集](../../data/odbc/dynaset.md)并[快照](../../data/odbc/snapshot.md)。

#### <a name="to-open-a-recordset"></a>若要打开记录集

1. 构造的对象在`CRecordset`-派生的类。

   您可以构造在堆上或函数的堆栈帧上的对象。

1. （可选） 修改默认记录集行为。 有关可用选项，请参阅[设置记录集选项](#_core_setting_recordset_options)。

1. 调用对象的[打开](../../mfc/reference/crecordset-class.md#open)成员函数。

在构造函数中，传递一个指向`CDatabase`对象或传递 NULL 以使用该框架将构造一个临时数据库对象，然后打开基于返回的连接字符串[GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect)成员函数。 `CDatabase`对象可能已经连接到数据源。

对调用`Open`使用 SQL 来从数据源选择记录。 选择 （如果有） 的第一个记录是当前记录。 此记录的字段的值存储在记录集对象的字段数据成员。 如果选择了任何记录，同时`IsBOF`和`IsEOF`成员函数将返回 0。

在你[打开](../../mfc/reference/crecordset-class.md#open)调用时，你可以：

- 指定记录集是动态集或快照。 默认情况下，作为快照打开记录集。 或者，可以指定仅正向记录，这样仅向前滚动，一次一个记录集。

   默认情况下，记录集使用存储中的默认类型`CRecordset`数据成员`m_nDefaultType`。 向导编写代码以初始化`m_nDefaultType`到在向导中选择的记录集类型。 如果不接受此默认设置，您可以替换另一个记录集类型。

- 指定要替换默认的 sql 语句的字符串**选择**记录集构造的语句。

- 指定记录集是只读的还是仅限追加的。 记录集允许完全更新的默认值，但可以限制，仅添加新记录或可以禁止所有更新。

下面的示例演示如何打开类的只读快照对象`CStudentSet`，特定于应用程序的类：

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

调用后`Open`，使用成员函数和数据成员的对象来处理记录。 在某些情况下，你可能想要再次查询或刷新记录集以包括在数据源上发生的更改。 有关详细信息，请参阅[记录集： 再次查询记录集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)。

> [!TIP]
>  在开发期间使用的连接字符串可能不能最终用户所需的连接字符串不同。 有关通用化你的应用程序在这方面的建议，请参阅[数据源： 管理连接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)。

##  <a name="_core_setting_recordset_options"></a> 设置记录集选项

在构造记录集对象之后但在调用之前`Open`来选择记录，你可能想要设置某些选项来控制记录集的行为。 对于所有记录集，您可以：

- 指定[筛选器](../../data/odbc/recordset-filtering-records-odbc.md)来约束记录所选内容。

- 指定[排序](../../data/odbc/recordset-sorting-records-odbc.md)的记录的顺序。

- 指定[参数](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)让您可以选择使用获取，或在运行时计算的信息的记录。

如果条件正确，还可以设置以下选项：

- 如果记录集是可更新并支持锁定选项，指定[锁定](../../data/odbc/recordset-locking-records-odbc.md)方法用于更新。

> [!NOTE]
>  若要影响选择记录，必须设置这些选项，然后再调用`Open`成员函数。

##  <a name="_core_closing_a_recordset"></a> 关闭记录集

完成后使用记录集，必须释放它，然后释放其内存。

#### <a name="to-close-a-recordset"></a>若要关闭记录集

1. 调用其[关闭](../../mfc/reference/crecordset-class.md#close)成员函数。

1. 销毁记录集对象。

   如果函数的堆栈帧上进行声明，当对象超出作用域对象被自动销毁。 否则，请使用**删除**运算符。

`Close` 释放记录集的`HSTMT`处理。 它不会销毁 c + + 对象。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[记录集：添加、更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)