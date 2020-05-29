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
ms.openlocfilehash: 628ffb2feee385a4114b0dbea074f81678c529d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367108"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>记录集：添加、更新和删除记录 (ODBC)

本主题适用于 MFC ODBC 类。

> [!NOTE]
> 现在，您可以更高效地批量添加记录。 有关详细信息，请参阅[记录集：批量添加记录 （ODBC）。](../../data/odbc/recordset-adding-records-in-bulk-odbc.md)

> [!NOTE]
> 本主题适用于从 `CRecordset` 派生的对象，其中尚未实现批量提取行。 如果使用批量行提取，请参阅[记录集：批量提取记录 （ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

可更新的快照和动态集允许您添加、编辑（更新）和删除记录。 本主题介绍：

- [如何确定您的记录集是否可更新](#_core_determining_whether_your_recordset_is_updatable)。

- [如何添加新记录](#_core_adding_a_record_to_a_recordset)。

- [如何编辑现有记录](#_core_editing_a_record_in_a_recordset)。

- [如何删除记录](#_core_deleting_a_record_from_a_recordset)。

有关如何执行更新以及更新如何向其他用户显示的详细信息，请参阅[记录集：记录集如何更新记录 （ODBC）。](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) 通常，当您添加、编辑或删除记录时，记录集会立即更改数据源。 您可以将相关更新组批处理到事务中。 如果事务正在进行，则在提交事务之前，更新不会成为最终更新。 这允许您收回或回滚更改。 有关交易记录的信息，请参阅[事务 （ODBC）](../../data/odbc/transaction-odbc.md)。

下表总结了具有不同更新特征的记录集可用的选项。

### <a name="recordset-readupdate-options"></a>记录集读取/更新选项

|类型|读取|编辑记录|删除记录|添加新（追加）|
|----------|----------|-----------------|-------------------|------------------------|
|只读|Y|N|N|N|
|仅追加|Y|N|N|Y|
|完全可上|Y|Y|Y|Y|

## <a name="determining-whether-your-recordset-is-updateable"></a><a name="_core_determining_whether_your_recordset_is_updatable"></a>确定记录集是否可更新

如果数据源是可更新的，并且将记录集打开为可更新的，则记录集对象是可更新的。 其可更新性还取决于您使用的 SQL 语句、ODBC 驱动程序的功能以及 ODBC 光标库是否位于内存中。 不能更新只读记录集或数据源。

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>确定记录集是否可更新

1. 调用记录集对象的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成员函数。

   `CanUpdate`如果记录集是可更新的，则返回非零值。

默认情况下，记录集是完全可更新的（您可以执行`AddNew`和`Edit``Delete`操作）。 但是，您也可以使用["仅追加"](../../mfc/reference/crecordset-class.md#open)选项打开可更新的记录集。 以这种方式打开的记录集只允许使用`AddNew`添加新记录。 您不能编辑或删除现有记录。 您可以通过调用[CanAppend](../../mfc/reference/crecordset-class.md#canappend)成员函数来测试记录集是否仅打开以进行追加。 `CanAppend`如果记录集是完全可更新的，或者仅打开以追加，则返回非零值。

以下代码显示了如何使用`CanUpdate`名为 的记录集对象： `rsStudentSet`

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
> 当您准备通过调用`Update`更新记录集时，请注意，记录集包含组成表主键的所有列（或表上任何唯一索引的所有列）。 在某些情况下，框架只能使用记录集中选择的列来标识要更新的表中的记录。 如果没有所有必要的列，则表中可能会更新多个记录，从而可能损坏表的引用完整性。 在这种情况下，框架在调用`Update`时会引发异常。

## <a name="adding-a-record-to-a-recordset"></a><a name="_core_adding_a_record_to_a_recordset"></a>将记录添加到记录集

如果记录集[的 CanAppend](../../mfc/reference/crecordset-class.md#canappend)成员函数返回非零值，则可以向记录集添加新记录集。

#### <a name="to-add-a-new-record-to-a-recordset"></a>将新记录添加到记录集

1. 确保记录集是可追加的。

1. 调用记录集对象的[AddNew](../../mfc/reference/crecordset-class.md#addnew)成员函数。

   `AddNew`准备记录集以充当编辑缓冲区。 所有字段数据成员都设置为特殊值 Null，并标记为"无"，因此仅在调用[Update](../../mfc/reference/crecordset-class.md#update)时将更改（脏）值写入数据源。

1. 设置新记录的字段数据成员的值。

   将值分配给字段数据成员。 您未分配的那些不会写入数据源。

1. 调用记录集对象`Update`的成员函数。

   `Update`通过将新记录写入数据源来完成添加。 有关未能调用`Update`时发生的情况的信息，请参阅[记录集：记录集如何更新记录 （ODBC）。](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

有关添加记录的工作原理以及添加记录在记录集中何时可见的信息，请参阅[记录集：如何添加新、编辑和删除工作 （ODBC）。](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)

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
> 要取消`AddNew`或`Edit`呼叫，只需使用*AFX_MOVE_REFRESH*参数`AddNew`拨打`Edit`或呼叫`Move`即可。 数据成员将重置为其以前的值，您仍处于`Edit`或`Add`模式下。

## <a name="editing-a-record-in-a-recordset"></a><a name="_core_editing_a_record_in_a_recordset"></a>在记录集中编辑记录

如果记录集的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成员函数返回非零值，则可以编辑现有记录。

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>编辑记录集中的现有记录

1. 确保记录集是可更新的。

1. 滚动到要更新的记录。

1. 调用记录集对象的["编辑](../../mfc/reference/crecordset-class.md#edit)"成员函数。

   `Edit`准备记录集以充当编辑缓冲区。 标记所有字段数据成员，以便记录集可以稍后判断它们是否已更改。 当您调用[Update](../../mfc/reference/crecordset-class.md#update)时，更改字段数据成员的新值将写入数据源。

1. 设置新记录的字段数据成员的值。

   将值分配给字段数据成员。 不分配值的值保持不变。

1. 调用记录集对象`Update`的成员函数。

   `Update`通过将更改的记录写入数据源来完成编辑。 有关未能调用`Update`时发生的情况的信息，请参阅[记录集：记录集如何更新记录 （ODBC）。](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

编辑记录后，编辑的记录将保留当前记录。

下面的示例显示一个`Edit`操作。 它假定用户已移动到他或她要编辑的记录。

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
> 要取消`AddNew`或`Edit`呼叫，只需使用*AFX_MOVE_REFRESH*参数`AddNew`拨打`Edit`或呼叫`Move`即可。 数据成员将重置为其以前的值，您仍处于`Edit`或`Add`模式下。

## <a name="deleting-a-record-from-a-recordset"></a><a name="_core_deleting_a_record_from_a_recordset"></a>从记录集中删除记录

如果记录集的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成员函数返回非零值，则可以删除记录。

#### <a name="to-delete-a-record"></a>删除记录

1. 确保记录集是可更新的。

1. 滚动到要更新的记录。

1. 调用记录集对象的["删除](../../mfc/reference/crecordset-class.md#delete)"成员函数。

   `Delete`立即将记录标记为已删除，无论是在记录集中还是在数据源上。

   与`AddNew``Edit`和`Delete`不同`Update`，没有相应的呼叫。

1. 滚动到另一条记录。

   > [!NOTE]
   >  在记录集中移动时，可能不会跳过已删除的记录。 有关详细信息，请参阅[IsDelete 成员](../../mfc/reference/crecordset-class.md#isdeleted)函数。

下面的示例显示一个`Delete`操作。 它假定用户已移动到用户要删除的记录。 调用`Delete`后，请务必移动到新记录。

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

`AddNew`有关 和`Edit``Delete`成员函数的效果的详细信息，请参阅[记录集：记录集如何更新记录 （ODBC）。](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
