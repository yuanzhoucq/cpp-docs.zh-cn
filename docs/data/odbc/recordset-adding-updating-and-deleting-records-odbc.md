---
title: "记录集： 添加、 更新和删除记录 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cad50d25f6b9e2cc619fb19e21c2b6575ababa47
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>记录集：添加、更新和删除记录 (ODBC)
本主题适用于 MFC ODBC 类。  
  
> [!NOTE]
>  更有效地批量现在可以添加记录。 有关详细信息，请参阅[记录集： 添加记录 (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md)。  
  
> [!NOTE]
>  本主题适用于派生自`CRecordset`中哪些批量行提取尚未实现。 如果你将批量行提取，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 可更新的快照和动态集允许您可以添加、 编辑 （更新） 和删除记录。 本主题说明：  
  
-   [如何确定是否可以更新记录集](#_core_determining_whether_your_recordset_is_updatable)。  
  
-   [如何添加新的记录](#_core_adding_a_record_to_a_recordset)。  
  
-   [如何编辑现有记录](#_core_editing_a_record_in_a_recordset)。  
  
-   [如何删除一条记录](#_core_deleting_a_record_from_a_recordset)。  
  
 有关如何执行更新的详细信息 out 以及如何向其他用户显示你的更新，请参阅[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。 通常情况下，当添加、 编辑或删除一条记录，记录集数据源立即更改。 相反，你可以为事务批处理的相关的更新的组。 如果一个事务正在进行，此更新不会成为最终直到提交事务。 这样，你可以将带回或回滚所做的更改。 有关事务的信息，请参阅[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
 下表总结了可用于具有不同更新特征的记录集的选项。  
  
### <a name="recordset-readupdate-options"></a>记录集读取/更新选项  
  
|类型|读取|编辑记录|删除记录|添加新 （追加）|  
|----------|----------|-----------------|-------------------|------------------------|  
|只读|Y|N|N|N|  
|仅限追加|Y|N|N|Y|  
|完全可更新|Y|Y|Y|Y|  
  
##  <a name="_core_determining_whether_your_recordset_is_updatable"></a>确定记录集是否是可更新  
 如果数据源是可更新并且打开记录集持久化为可更新，是可更新记录集对象。 其 updateability 还取决于你使用的 SQL 语句的 ODBC 驱动程序，功能以及 ODBC 游标库是否在内存中。 无法更新只读的记录集或数据源。  
  
#### <a name="to-determine-whether-your-recordset-is-updatable"></a>若要确定是否可以更新记录集  
  
1.  调用记录集对象的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成员函数。  
  
     `CanUpdate`如果记录集是可更新，则返回非零值。  
  
 默认情况下，记录集都是完全可更新 (你可以执行`AddNew`，**编辑**，和**删除**操作)。 但你也可以使用[仅附加](../../mfc/reference/crecordset-class.md#open)选项来打开可更新的记录集。 这种方式打开记录集允许仅添加新记录与`AddNew`。 你无法编辑或删除现有记录。 你可以测试是否记录集处于打开状态仅通过调用追加[CanAppend](../../mfc/reference/crecordset-class.md#canappend)成员函数。 `CanAppend`如果记录集是完全可更新或仅供追加，则返回非零值。  
  
 下面的代码演示如何使用`CanUpdate`对于记录集对象被称为`rsStudentSet`:  
  
```  
if( !rsStudentSet.Open( ) )  
    return FALSE;  
if( !rsStudentSet.CanUpdate( ) )  
{  
    AfxMessageBox( "Unable to update the Student recordset." );  
    return;  
}  
```  
  
> [!CAUTION]
>  当你准备更新记录集通过调用**更新**，请注意你记录集包括所有列组成的主键的表 （或所有表上任何唯一索引的列）。 在某些情况下，该框架还可以使用仅选定记录集中的列来标识表中要更新的记录。 不包含所有必要的列，则可能在表中，可能损坏的表的引用完整性更新多个记录。 在这种情况下，框架会引发异常时调用**更新**。  
  
##  <a name="_core_adding_a_record_to_a_recordset"></a>将记录添加到记录集  
 你可以将新记录添加到记录集，如果其[CanAppend](../../mfc/reference/crecordset-class.md#canappend)成员函数将返回一个非零值。  
  
#### <a name="to-add-a-new-record-to-a-recordset"></a>将一条新记录添加到记录集  
  
1.  请确保记录集是可附加。  
  
2.  调用记录集对象的[AddNew](../../mfc/reference/crecordset-class.md#addnew)成员函数。  
  
     `AddNew`准备为充当编辑缓冲区的记录集。 设置为特殊值 Null 的并标记为不变，以便在调用时只会更改 （脏） 将值写入到数据源所有字段数据成员[更新](../../mfc/reference/crecordset-class.md#update)。  
  
3.  设置新记录的字段数据成员的值。  
  
     将值分配给字段数据成员。 未分配的那些不写入数据源。  
  
4.  调用记录集对象的**更新**成员函数。  
  
     **更新**通过将新记录写入数据源来完成添加。 如果您不能调用，会发生情况有关的信息为**更新**，请参阅[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
 有关如何添加记录的工作机制和添加的记录何时可见记录集中的信息，请参阅[记录集： 如何 AddNew、 Edit 和删除工作 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)。  
  
 下面的示例演示如何添加新的记录：  
  
```  
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
>  若要取消`AddNew`或**编辑**调用，只需进行另一个调用`AddNew`或**编辑**或调用**移动**与**AFX_MOVE_REFRESH**参数。 数据成员被重置为其以前的值和仍位于**编辑**或**添加**模式。  
  
##  <a name="_core_editing_a_record_in_a_recordset"></a>编辑记录集中的记录集  
 如果满足以下条件，则可以编辑现有记录记录集的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成员函数将返回一个非零值。  
  
#### <a name="to-edit-an-existing-record-in-a-recordset"></a>若要编辑现有记录在记录集中  
  
1.  请确保记录集是可更新。  
  
2.  滚动到想要更新的记录。  
  
3.  调用记录集对象的[编辑](../../mfc/reference/crecordset-class.md#edit)成员函数。  
  
     **编辑**准备为充当编辑缓冲区的记录集。 所有字段数据成员被标记都为，以便记录集以后可以告知它们是否已更改。 已更改的字段数据成员的新值写入到数据源，当您调用[更新](../../mfc/reference/crecordset-class.md#update)。  
  
4.  设置新记录的字段数据成员的值。  
  
     将值分配给字段数据成员。 这些不分配值保持不变。  
  
5.  调用记录集对象的**更新**成员函数。  
  
     **更新**通过所更改的记录写入数据源完成编辑。 如果您不能调用，会发生情况有关的信息为**更新**，请参阅[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
 编辑记录后，已编辑的记录将保持为当前记录。  
  
 下面的示例演示**编辑**操作。 它假定用户已移动到他或她想要编辑的记录。  
  
```  
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
>  若要取消`AddNew`或**编辑**调用，只需进行另一个调用`AddNew`或**编辑**或调用**移动**与**AFX_MOVE_REFRESH**参数。 数据成员被重置为其以前的值和仍位于**编辑**或**添加**模式。  
  
##  <a name="_core_deleting_a_record_from_a_recordset"></a>从记录集中删除一条记录  
 可删除的记录，如果记录集的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成员函数将返回一个非零值。  
  
#### <a name="to-delete-a-record"></a>若要删除一条记录  
  
1.  请确保记录集是可更新。  
  
2.  滚动到想要更新的记录。  
  
3.  调用记录集对象的[删除](../../mfc/reference/crecordset-class.md#delete)成员函数。  
  
     **删除**立即将记录标记为删除，在记录集和数据源。  
  
     与不同`AddNew`和**编辑**，**删除**没有对应**更新**调用。  
  
4.  滚动到另一条记录。  
  
    > [!NOTE]
    >  将移动时在记录集中，不能跳过已删除的记录。 有关详细信息，请参阅[IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted)成员函数。  
  
 下面的示例演示**删除**操作。 它假定用户已移动到用户想要删除的记录。 后**删除**是调用，务必要移动到新的记录。  
  
```  
rsStudent.Delete( );  
rsStudent.MoveNext( );  
```  
  
 有关详细信息的效果`AddNew`，**编辑**，和**删除**成员函数，请参阅[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)