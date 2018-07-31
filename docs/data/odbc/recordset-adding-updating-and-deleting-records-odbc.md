---
title: 记录集： 添加、 更新和删除记录 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5a8844da684d8afa3fe4dd13d8323d2bb3138d6c
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337994"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>记录集：添加、更新和删除记录 (ODBC)
本主题适用于 MFC ODBC 类。  
  
> [!NOTE]
>  更有效地批量现在可以添加记录。 有关详细信息，请参阅[记录集： 添加记录 (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md)。  
  
> [!NOTE]
>  本主题适用于对象派生自`CRecordset`中的批量行提取尚未实现。 如果使用批量行提取，请参阅[记录集： 提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 可更新的快照和动态集允许您可以添加、 编辑 （更新） 和删除记录。 本主题说明：  
  
-   [如何确定记录集是否可以更新](#_core_determining_whether_your_recordset_is_updatable)。  
  
-   [如何添加新记录](#_core_adding_a_record_to_a_recordset)。  
  
-   [如何编辑现有记录](#_core_editing_a_record_in_a_recordset)。  
  
-   [如何删除一条记录](#_core_deleting_a_record_from_a_recordset)。  
  
 有关如何执行更新详细信息并方式更新显示给其他用户，请参阅[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。 通常情况下，当添加、 编辑或删除的记录，记录集的数据源立即更改。 而是可以为事务批处理相关的更新组。 如果事务正在进行时，更新不会成为最终直到提交事务。 这样即可取消或回滚所做的更改。 有关事务信息，请参阅[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
 下表总结了可用于具有不同更新特征的记录集的选项。  
  
### <a name="recordset-readupdate-options"></a>记录集读取/更新选项  
  
|类型|读取|编辑记录|删除记录|添加新 （追加）|  
|----------|----------|-----------------|-------------------|------------------------|  
|只读|Y|N|N|N|  
|仅限追加|Y|N|N|Y|  
|完全可更新|Y|Y|Y|Y|  
  
##  <a name="_core_determining_whether_your_recordset_is_updatable"></a> 确定记录集是否是可更新的  
 如果数据源是可更新并打开记录集持久化为可更新的记录集对象是可更新。 其可更新性还取决于您使用的 SQL 语句的 ODBC 驱动程序、 功能以及 ODBC 游标库是否在内存中。 无法更新只读的记录集或数据源。  
  
#### <a name="to-determine-whether-your-recordset-is-updatable"></a>若要确定是否可以更新记录集  
  
1.  调用记录集对象的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成员函数。  
  
     `CanUpdate` 如果是可更新的记录集，则返回非零值。  
  
 默认情况下，记录集都是完全可更新 (可以执行`AddNew`， `Edit`，和`Delete`操作)。 但也可以使用[appendOnly](../../mfc/reference/crecordset-class.md#open)选项来打开可更新的记录集。 打开这种方式的记录集允许仅添加新记录以及`AddNew`。 无法编辑或删除现有记录。 你可以测试是否记录集处于打开状态，仅通过调用追加[CanAppend](../../mfc/reference/crecordset-class.md#canappend)成员函数。 `CanAppend` 如果记录集是完全可更新或仅供追加，则返回非零值。  
  
 下面的代码演示如何使用`CanUpdate`对于记录集对象被称为`rsStudentSet`:  
  
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
>  当你准备更新记录集通过调用`Update`，负责记录集，包含所有列的主键的表 （或所有表上所有唯一索引的列） 组成。 在某些情况下，框架可以使用仅选定为记录集中的列来标识表中要更新的记录。 不包含所有必要的列，可能会在表中，从而可能损坏的引用完整性的表的更新多个记录。 在这种情况下，框架会引发异常时调用`Update`。  
  
##  <a name="_core_adding_a_record_to_a_recordset"></a> 将一条记录添加到记录集  
 可以向一个记录集添加新记录，如果其[CanAppend](../../mfc/reference/crecordset-class.md#canappend)成员函数返回一个非零值。  
  
#### <a name="to-add-a-new-record-to-a-recordset"></a>若要将新记录添加到记录集  
  
1.  请确保记录集是可附加。  
  
2.  调用记录集对象的[AddNew](../../mfc/reference/crecordset-class.md#addnew)成员函数。  
  
     `AddNew` 准备要充当编辑缓冲区的记录集。 所有字段数据成员是设置为特殊值为 Null，标记为不变，以便在调用时只会更改 （更新） 将值写入到数据源[更新](../../mfc/reference/crecordset-class.md#update)。  
  
3.  设置新记录的字段数据成员的值。  
  
     将值分配给字段数据成员。 这些不分配未写入到数据源。  
  
4.  调用记录集对象的`Update`成员函数。  
  
     `Update` 通过将新记录写入数据源来完成添加。 如果您不能调用，会发生情况有关的信息为`Update`，请参阅[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
 有关如何添加记录的工作原理以及时添加的记录中是可见的记录集的信息，请参阅[记录集： 如何 AddNew、 Edit 和删除工作 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)。  
  
 下面的示例演示如何添加新的记录：  
  
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
>  若要取消`AddNew`或`Edit`调用，只需进行再次调用`AddNew`或`Edit`或调用`Move`与*AFX_MOVE_REFRESH*参数。 数据成员将重置为其以前的值和仍处于`Edit`或`Add`模式。  
  
##  <a name="_core_editing_a_record_in_a_recordset"></a> 编辑记录集中的记录集  
 如果可以编辑现有记录记录集的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成员函数返回一个非零值。  
  
#### <a name="to-edit-an-existing-record-in-a-recordset"></a>若要编辑现有记录集中的记录  
  
1.  请确保记录集是可更新。  
  
2.  滚动到你想要更新的记录。  
  
3.  调用记录集对象的[编辑](../../mfc/reference/crecordset-class.md#edit)成员函数。  
  
     `Edit` 准备要充当编辑缓冲区的记录集。 所有字段数据成员被都标记，以便记录集更高版本可以判断它们是否已更改。 已更改的字段数据成员的新值将写入到数据源中，在调用时[更新](../../mfc/reference/crecordset-class.md#update)。  
  
4.  设置新记录的字段数据成员的值。  
  
     将值分配给字段数据成员。 未分配的值保持不变。  
  
5.  调用记录集对象的`Update`成员函数。  
  
     `Update` 完成编辑通过写入到数据源的更改的记录。 如果您不能调用，会发生情况有关的信息为`Update`，请参阅[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
 编辑记录后，已编辑的记录将保留当前记录。  
  
 下面的示例演示`Edit`操作。 它假定用户已移动到他或她想要编辑的记录。  
  
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
>  若要取消`AddNew`或`Edit`调用，只需进行再次调用`AddNew`或`Edit`或调用`Move`与*AFX_MOVE_REFRESH*参数。 数据成员将重置为其以前的值和仍处于`Edit`或`Add`模式。  
  
##  <a name="_core_deleting_a_record_from_a_recordset"></a> 从记录集删除记录  
 您可以删除记录，如果记录集的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成员函数返回一个非零值。  
  
#### <a name="to-delete-a-record"></a>若要删除的记录  
  
1.  请确保记录集是可更新。  
  
2.  滚动到你想要更新的记录。  
  
3.  调用记录集对象的[删除](../../mfc/reference/crecordset-class.md#delete)成员函数。  
  
     `Delete` 立即将记录标记为已删除的记录集和数据源上。  
  
     与不同`AddNew`并`Edit`，`Delete`没有相应的`Update`调用。  
  
4.  滚动到另一条记录。  
  
    > [!NOTE]
    >  移动时在记录集中，不能跳过已删除的记录。 有关详细信息，请参阅[IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted)成员函数。  
  
 下面的示例演示`Delete`操作。 它假定用户已移动到用户想要删除的记录。 之后`Delete`是调用，务必要将移动到新的记录。  
  
```  
rsStudent.Delete( );  
rsStudent.MoveNext( );  
```  
  
 有关效果的详细信息`AddNew`， `Edit`，并`Delete`成员函数，请参阅[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)