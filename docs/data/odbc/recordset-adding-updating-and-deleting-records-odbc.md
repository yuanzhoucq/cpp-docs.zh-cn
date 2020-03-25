---
title: 记录集：添加、更新和删除记录 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- records [C++], deleting
- AddNew method
- ODBC recordsets [C++], deleting records
- data in recordsets [C++]
- record editing [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: 760c8889-bec4-482b-a8f2-319792a6af98
ms.openlocfilehash: 14fc26709541135e80a2e0fe4de872cc75221874
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213000"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>记录集：添加、更新和删除记录 (ODBC)

本主题适用于 MFC ODBC 类。

> [!NOTE]
>  你现在可以更有效地批量添加记录。 有关详细信息，请参阅[记录集：批量添加记录（ODBC）](../../data/odbc/recordset-adding-records-in-bulk-odbc.md)。

> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，其中尚未实现批量提取行。 如果使用批量取行，请参阅[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

可更新的快照和动态集允许添加、编辑（更新）和删除记录。 本主题介绍：

- [如何确定您的记录集是否可更新](#_core_determining_whether_your_recordset_is_updatable)。

- [如何添加新记录](#_core_adding_a_record_to_a_recordset)。

- [如何编辑现有记录](#_core_editing_a_record_in_a_recordset)。

- [如何删除记录](#_core_deleting_a_record_from_a_recordset)。

有关如何执行更新以及更新对其他用户的显示方式的详细信息，请参阅[记录集：记录集如何更新记录（ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。 通常，在添加、编辑或删除记录时，记录集会立即更改数据源。 您可以改为将相关更新组合到事务中。 如果事务正在进行，则在提交事务之前，更新不会成为最终版本。 这允许您恢复或回滚更改。 有关事务的信息，请参阅[Transaction （ODBC）](../../data/odbc/transaction-odbc.md)。

下表总结了可用于具有不同更新特征的记录集的选项。

### <a name="recordset-readupdate-options"></a>记录集读取/更新选项

|类型|读取|编辑记录|删除记录|添加新的（追加）|
|----------|----------|-----------------|-------------------|------------------------|
|只读|Y|N|N|N|
|仅追加|Y|N|N|Y|
|完全可更新|Y|Y|Y|Y|

##  <a name="determining-whether-your-recordset-is-updateable"></a><a name="_core_determining_whether_your_recordset_is_updatable"></a>确定您的记录集是否可更新

如果数据源是可更新的并且您将记录集作为可更新的打开，则记录集对象是可更新的。 它还取决于所使用的 SQL 语句、ODBC 驱动程序的功能以及 ODBC 游标库是否在内存中。 您无法更新只读记录集或数据源。

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>确定您的记录集是否可更新

1. 调用 recordset 对象的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成员函数。

   如果记录集是可更新的，`CanUpdate` 将返回一个非零值。

默认情况下，记录集是完全可更新的（可以执行 `AddNew`、`Edit`和 `Delete` 操作）。 但你也可以使用[appendOnly](../../mfc/reference/crecordset-class.md#open)选项来打开可更新的记录集。 以这种方式打开的记录集只允许将新记录添加到 `AddNew`中。 您无法编辑或删除现有记录。 您可以通过调用[CanAppend](../../mfc/reference/crecordset-class.md#canappend)成员函数来测试是否只为追加而打开记录集。 如果记录集是完全可更新的，或者只是为了追加，则 `CanAppend` 返回一个非零值。

下面的代码演示如何对名为 `rsStudentSet`的记录集对象使用 `CanUpdate`：

```cpp
if( !rsStudentSet.Open( ) )
    return FALSE;
if( !rsStudentSet.CanUpdate( ) )
{
    AfxMessageBox( "Unable to update the Student recordset." );
    return;
}
```

> [!CAUTION]
>  当您准备通过调用 `Update`来更新记录集时，请注意您的记录集包括构成表的主键的所有列（或表中的所有唯一索引的所有列）。 在某些情况下，框架只能使用记录集中所选的列来标识要更新的表中的记录。 如果没有所有必需的列，表中的多个记录可能会更新，这可能会破坏表的引用完整性。 在这种情况下，在调用 `Update`时，框架会引发异常。

##  <a name="adding-a-record-to-a-recordset"></a><a name="_core_adding_a_record_to_a_recordset"></a>将记录添加到记录集

如果记录集的[CanAppend](../../mfc/reference/crecordset-class.md#canappend)成员函数返回一个非零值，则可以向记录集添加新记录。

#### <a name="to-add-a-new-record-to-a-recordset"></a>向记录集添加新记录

1. 请确保记录集是可追加的。

1. 调用记录集对象的[AddNew](../../mfc/reference/crecordset-class.md#addnew)成员函数。

   `AddNew` 准备要用作编辑缓冲区的记录集。 所有字段数据成员均设置为特殊值 Null 并标记为 "未更改"，以便在调用[Update](../../mfc/reference/crecordset-class.md#update)时，仅将更改的（脏）值写入数据源。

1. 设置新记录的字段数据成员的值。

   为字段数据成员赋值。 未分配的将不会写入数据源。

1. 调用记录集对象的 `Update` 成员函数。

   `Update` 通过向数据源写入新记录来完成添加。 有关未能调用 `Update`的情况的信息，请参阅[记录集：记录集如何更新记录（ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

有关如何添加记录以及添加记录在记录集中可见的方式的信息，请参阅[记录集： AddNew、Edit 和 Delete 工作（ODBC）](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)。

下面的示例演示如何添加新记录：

```cpp
if( !rsStudent.Open( ) )
    return FALSE;
if( !rsStudent.CanAppend( ) )
    return FALSE;                      // no field values were set
rsStudent.AddNew( );
rsStudent.m_strName = strName;
rsStudent.m_strCity = strCity;
rsStudent.m_strStreet = strStreet;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not added; no field values were set." );
    return FALSE;
}
```

> [!TIP]
>  若要取消 `AddNew` 或 `Edit` 调用，只需对 `AddNew` 或 `Edit` 调用，或使用 *`Move`* 参数调用 AFX_MOVE_REFRESH 即可。 数据成员将重置为以前的值，并且仍处于 `Edit` 或 `Add` 模式。

##  <a name="editing-a-record-in-a-recordset"></a><a name="_core_editing_a_record_in_a_recordset"></a>编辑记录集中的记录

如果记录集的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成员函数返回一个非零值，则可以编辑现有记录。

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>编辑记录集中的现有记录

1. 请确保记录集是可更新的。

1. 滚动到要更新的记录。

1. 调用记录集对象的[编辑](../../mfc/reference/crecordset-class.md#edit)成员函数。

   `Edit` 准备要用作编辑缓冲区的记录集。 所有字段数据成员都将被标记，以便记录集以后可以告诉您它们是否已更改。 调用[Update](../../mfc/reference/crecordset-class.md#update)时，已更改字段数据成员的新值将写入数据源。

1. 设置新记录的字段数据成员的值。

   为字段数据成员赋值。 未赋值的值将保持不变。

1. 调用记录集对象的 `Update` 成员函数。

   `Update` 通过将更改的记录写入数据源来完成编辑。 有关未能调用 `Update`的情况的信息，请参阅[记录集：记录集如何更新记录（ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

编辑记录后，编辑的记录将保留当前记录。

下面的示例演示 `Edit` 操作。 它假定用户已移动到他（或她）想要编辑的记录。

```cpp
rsStudent.Edit( );
rsStudent.m_strStreet = strNewStreet;
rsStudent.m_strCity = strNewCity;
rsStudent.m_strState = strNewState;
rsStudent.m_strPostalCode = strNewPostalCode;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not updated; no field values were set." );
    return FALSE;
}
```

> [!TIP]
> 若要取消 `AddNew` 或 `Edit` 调用，只需对 `AddNew` 或 `Edit` 调用，或使用 *`Move`* 参数调用 AFX_MOVE_REFRESH 即可。 数据成员将重置为以前的值，并且仍处于 `Edit` 或 `Add` 模式。

##  <a name="deleting-a-record-from-a-recordset"></a><a name="_core_deleting_a_record_from_a_recordset"></a>从记录集中删除记录

如果记录集的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成员函数返回一个非零值，则可以删除记录。

#### <a name="to-delete-a-record"></a>删除记录

1. 请确保记录集是可更新的。

1. 滚动到要更新的记录。

1. 调用 recordset 对象的[Delete](../../mfc/reference/crecordset-class.md#delete)成员函数。

   `Delete` 立即在记录集和数据源上将记录标记为已删除。

   与 `AddNew` 和 `Edit`不同，`Delete` 没有对应的 `Update` 调用。

1. 滚动到其他记录。

   > [!NOTE]
   >  在记录集时，可能不会跳过已删除的记录。 有关详细信息，请参阅[IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted)成员函数。

下面的示例演示 `Delete` 操作。 它假定用户已移动到用户要删除的记录。 调用 `Delete` 后，移动到新记录很重要。

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

有关 `AddNew`、`Edit`和 `Delete` 成员函数的影响的详细信息，请参阅[记录集：记录集如何更新记录（ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
