---
title: "记录集：添加、更新和删除记录 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddNew 方法"
  - "记录集中的数据 [C++]"
  - "ODBC 记录集 [C++], 添加记录"
  - "ODBC 记录集 [C++], 删除记录"
  - "ODBC 记录集 [C++], 编辑记录"
  - "记录编辑 [C++]"
  - "记录编辑 [C++], 在记录集中"
  - "记录 [C++], 添加"
  - "记录 [C++], 删除"
  - "记录 [C++], 编辑"
  - "记录 [C++], 更新"
  - "记录集 [C++], 添加记录"
  - "记录集 [C++], 删除记录"
  - "记录集 [C++], 编辑记录"
  - "记录集 [C++], 更新"
ms.assetid: 760c8889-bec4-482b-a8f2-319792a6af98
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集：添加、更新和删除记录 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
> [!NOTE]
>  现在即可更有效地批量添加记录。  有关更多信息，请参见[记录集：批量添加记录 \(ODBC\)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md)。  
  
> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，这些对象中尚未实现批量取行。  如果正在使用批量取行，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 可更新的快照和动态集使您得以添加、编辑（更新）和删除记录。  本主题说明：  
  
-   [如何确定您的记录集是否可以更新](#_core_determining_whether_your_recordset_is_updatable)。  
  
-   [如何添加新记录](#_core_adding_a_record_to_a_recordset)。  
  
-   [如何编辑已有记录](#_core_editing_a_record_in_a_recordset)。  
  
-   [如何删除记录](#_core_deleting_a_record_from_a_recordset)。  
  
 有关如何执行更新和更新以何种方式显示给其他用户的更多信息，请参见[记录集：记录集如何更新记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  通常，添加、编辑或删除记录后，记录集立即更改数据源。  而您可以将相关更新组批处理为事务。  如果事务正在进行，则直到提交事务后更新才成为最终更新。  这使您得以取消或回滚更改。  有关事务的信息，请参见[事务 \(ODBC\)](../../data/odbc/transaction-odbc.md)。  
  
 下表总结了可用于具有不同更新特性的记录集的选项。  
  
### 记录集读取\/更新选项  
  
|类型|Read|编辑记录|删除记录|添加新记录（追加）|  
|--------|----------|----------|----------|---------------|  
|只读|Y|N|N|N|  
|仅追加|Y|N|N|Y|  
|可完整更新|Y|Y|Y|Y|  
  
##  <a name="_core_determining_whether_your_recordset_is_updatable"></a> 确定记录集是否是可更新的  
 如果数据源是可更新的，而且记录集已以可更新的方式打开，则记录集对象是可更新的。  记录集的更新能力还取决于所使用的 SQL 语句、ODBC 驱动程序的功能以及 ODBC 游标库是否在内存中。  无法更新只读记录集和数据源。  
  
#### 确定记录集是否是可更新的  
  
1.  调用记录集对象的 [CanUpdate](../Topic/CRecordset::CanUpdate.md) 成员函数。  
  
     如果记录集是可更新的，`CanUpdate` 返回一个非零值。  
  
 默认情况下，记录集是可完全更新的（可以执行 `AddNew`、**Edit** 和 **Delete** 操作）。  但您也可以使用 [appendOnly](../Topic/CRecordset::Open.md) 选项打开可更新的记录集。  以这种方式打开的记录集只允许用 `AddNew` 添加新记录。  无法编辑或删除现有记录。  通过调用 [CanAppend](../Topic/CRecordset::CanAppend.md) 成员函数，可以测试记录集是否以仅追加的方式打开。  如果记录集是完全可更新的或是以仅追加的方式打开，则 `CanAppend` 返回非零值。  
  
 下面的代码显示可以如何对一个称为 `rsStudentSet` 的记录集对象使用 `CanUpdate`：  
  
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
>  通过调用 **Update** 准备更新记录集时，请注意记录集要包括构成表主键的所有列（或表上所有唯一索引的所有列）。  某些情况下，框架只能使用记录集中选定用来标识表中要更新的记录的列。  如果没有全部必需的列，则可能会更新表中的多个记录，从而可能损坏表的引用完整性。  在此情况下，调用 **Update** 时框架将引发异常。  
  
##  <a name="_core_adding_a_record_to_a_recordset"></a> 将记录添加到记录集  
 记录集的 [CanAppend](../Topic/CRecordset::CanAppend.md) 成员函数返回非零值时，可以将新记录添加到记录集。  
  
#### 将新记录添加到记录集  
  
1.  确保记录集是可追加的。  
  
2.  调用记录集对象的 [AddNew](../Topic/CRecordset::AddNew.md) 成员函数。  
  
     `AddNew` 准备将记录集用作编辑缓冲区。  所有的字段数据成员都将设置为特殊值 Null，并标记为未更改的，因此调用 [Update](../Topic/CRecordset::Update.md) 时仅已更改（“更新”）的值被写入数据源。  
  
3.  设置新记录的字段数据成员的值。  
  
     给字段数据成员赋值。  未赋值的字段数据成员不写入数据源。  
  
4.  调用记录集对象的 **Update** 成员函数。  
  
     **Update** 通过将新记录写入数据源来完成添加。  有关调用 **Update** 失败时将发生什么情况的信息，请参见[记录集：记录集如何更新记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
 有关添加记录如何执行和记录集中添加的记录何时可见的信息，请参见[记录集：AddNew、Edit 和 Delete 的工作方式 \(ODBC\)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)。  
  
 下面的示例显示如何添加新记录：  
  
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
>  若要取消 `AddNew` 或 **Edit** 调用，只需再次调用 `AddNew` 或 **Edit**，或者使用 **AFX\_MOVE\_REFRESH** 参数调用 **Move**。  数据成员将重置为它们以前的值，而您仍将处于 **Edit** 或 **Add** 模式。  
  
##  <a name="_core_editing_a_record_in_a_recordset"></a> 编辑记录集中的记录  
 如果记录集的 [CanUpdate](../Topic/CRecordset::CanUpdate.md) 成员函数返回非零值，则可以编辑现有记录。  
  
#### 编辑记录集中的现有记录  
  
1.  确保记录集是可更新的。  
  
2.  滚动到要更新的记录。  
  
3.  调用记录集对象的 [Edit](../Topic/CRecordset::Edit.md) 成员函数。  
  
     **Edit** 准备将记录集用作编辑缓冲区。  所有的字段数据成员都有标记，以便记录集以后可以告知它们是否已更改。  当调用 [Update](../Topic/CRecordset::Update.md) 时，已更改的字段数据成员的新值将写入数据源。  
  
4.  设置新记录的字段数据成员的值。  
  
     给字段数据成员赋值。  没有赋值的字段保持不变。  
  
5.  调用记录集对象的 **Update** 成员函数。  
  
     **Update** 通过将已更改的记录写入数据源来完成编辑。  有关调用 **Update** 失败时将发生什么情况的信息，请参见[记录集：记录集如何更新记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
 编辑完记录后，已编辑过的记录保持为当前记录。  
  
 下面的示例显示 **Edit** 操作。  该示例假定用户已移动到他（或她）想要编辑的记录。  
  
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
>  若要取消 `AddNew` 或 **Edit** 调用，只需再次调用 `AddNew` 或 **Edit**，或者使用 **AFX\_MOVE\_REFRESH** 参数调用 **Move**。  数据成员将重置为它们以前的值，而您仍将处于 **Edit** 或 **Add** 模式。  
  
##  <a name="_core_deleting_a_record_from_a_recordset"></a> 从记录集中删除记录  
 如果记录集的 [CanUpdate](../Topic/CRecordset::CanUpdate.md) 成员函数返回非零值，则可以删除记录。  
  
#### 删除记录  
  
1.  确保记录集是可更新的。  
  
2.  滚动到要更新的记录。  
  
3.  调用记录集对象的 [Delete](../Topic/CRecordset::Delete.md) 成员函数。  
  
     **Delete** 立即在记录集和数据源中将记录都标记为已删除的。  
  
     与 `AddNew` 和 **Edit** 不同，**Delete** 没有相应的 **Update** 调用。  
  
4.  滚动到另一个记录。  
  
    > [!NOTE]
    >  在记录集中移动时，不能跳过已删除的记录。  有关更多信息，请参见 [IsDeleted](../Topic/CRecordset::IsDeleted.md) 成员函数。  
  
 下面的示例显示 **Delete** 操作。  该示例假定用户已移动到想要删除的记录。  调用 **Delete** 之后，移动到新记录很重要。  
  
```  
rsStudent.Delete( );  
rsStudent.MoveNext( );  
```  
  
 有关 `AddNew`、**Edit** 和 **Delete** 成员函数的作用的更多信息，请参见[记录集：记录集如何更新记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：锁定记录 \(ODBC\)](../../data/odbc/recordset-locking-records-odbc.md)