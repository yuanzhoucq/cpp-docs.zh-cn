---
title: "记录集： 批量提取记录 (ODBC) |Microsoft 文档"
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
- bulk row fetching, implementing
- ODBC recordsets, bulk row fetching
- bulk record field exchange
- bulk row fetching
- bulk RFX functions
- recordsets, bulk row fetching
- DoBulkFieldExchange method
- fetching ODBC records in bulk
- RFX (ODBC), bulk
- rowsets, bulk row fetching
- RFX (ODBC), bulk row fetching
ms.assetid: 20d10fe9-c58a-414a-b675-cdf9aa283e4f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8d9738af557cb8d4dd26b792851f8be276e91380
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>记录集：批量提取记录 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 类`CRecordset`提供有关批量行提取，这意味着，多个记录可以来检索一次在一次获取，而不是检索一个记录一次从数据源的支持。 你可以实现批量行提取仅在派生`CRecordset`类。 将数据从数据源传输到记录集对象的过程称为批量记录字段交换 (Bulk RFX)。 请注意，如果你未使用中的批量行提取`CRecordset`-派生的类中，数据通过记录字段交换 (RFX) 传输。 有关详细信息，请参阅[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
 本主题说明：  
  
-   [CRecordset 如何支持批量行提取](#_core_how_crecordset_supports_bulk_row_fetching)。  
  
-   [注意一些特殊事项时使用批量取行](#_core_special_considerations)。  
  
-   [如何实现批量记录字段交换](#_core_how_to_implement_bulk_record_field_exchange)。  
  
##  <a name="_core_how_crecordset_supports_bulk_row_fetching"></a>CRecordset 如何支持批量行提取  
 在打开之前记录集对象，你可以定义与行集大小`SetRowsetSize`成员函数。 行集大小指定应在一次获取检索多少条记录。 实现批量行提取时，默认行集大小为 25。 如果未实现批量行提取，在 1 保持固定的行集大小。  
  
 在初始化的行集大小后，调用[打开](../../mfc/reference/crecordset-class.md#open)成员函数。 在这里，你必须指定`CRecordset::useMultiRowFetch`选项**dwOptions**实现批量行提取的参数。 此外，你可以设置**CRecordset::userAllocMultiRowBuffers**选项。 批量记录字段交换机制使用数组存储在提取过程中检索的数据的多个行。 由框架可以自动分配这些存储缓冲区或你可以手动将他们分配。 指定**CRecordset::userAllocMultiRowBuffers**选项意味着，你将执行操作分配。  
  
 下表列出了由提供的成员函数`CRecordset`以支持批量行提取。  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|处理在提取过程中发生任何错误的虚拟函数。|  
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|实现大容量记录字段交换。 将自动调用到传输的数据的多个行从数据源到记录集对象。|  
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|检索行集大小的当前设置。|  
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|指示给定的获取之后实际检索到行数。 在大多数情况下，这是行集大小，除非提取了不完整行集。|  
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|返回行集合中的特定行的 fetch 状态。|  
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|刷新的数据和行集合中的特定行的状态。|  
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|将光标移到行集合中的特定行。|  
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|为指定的值可更改的行集大小的设置的虚拟函数。|  
  
##  <a name="_core_special_considerations"></a>特殊的注意事项  
 尽管批量行提取是性能提升，但某些功能的操作方式不同。 你决定实现批量行提取之前，请考虑以下各项：  
  
-   框架将自动调用`DoBulkFieldExchange`成员函数以将数据从数据源传输到记录集对象。 但是，数据将不传输从记录集到数据源。 调用`AddNew`，**编辑**，**删除**，或**更新**成员函数导致失败的断言。 尽管`CRecordset`目前不提供一种机制，用于更新的数据大容量行，你可以通过使用 ODBC API 函数编写您自己的函数**SQLSetPos**。 有关详细信息**SQLSetPos**，请参阅*ODBC SDK 程序员参考*MSDN 文档中。  
  
-   成员函数`IsDeleted`， `IsFieldDirty`， `IsFieldNull`， `IsFieldNullable`， `SetFieldDirty`，和`SetFieldNull`不能用于实现批量行提取的记录集。 但是，你可以调用`GetRowStatus`代替了`IsDeleted`，和`GetODBCFieldInfo`代替了`IsFieldNullable`。  
  
-   **移动**操作按行集重新定位记录集。 例如，假设你打开一个包含初始行集大小为 10 的 100 条记录的记录集。 **打开**提取行 1 到 10，与位于第 1 行的当前记录。 调用`MoveNext`提取下一步的行集，不是下一步的行。 一个行集合包括位于第 11 行的 11 至第 20，与当前记录的行。 请注意，`MoveNext`和**Move (1)**实现批量行提取时就不等效。 **Move (1)**提取当前记录的第 1 行开始的行集。 在此示例中，调用**Move (1)**之后调用**打开**提取与位于第 2 行的当前记录包含 2 至第 11 行的行集。 有关详细信息，请参阅[移动](../../mfc/reference/crecordset-class.md#move)成员函数。  
  
-   与记录字段交换不同向导不支持批量记录字段交换。 这意味着你必须手动声明将字段数据成员并手动重写`DoBulkFieldExchange`通过编写对批量 RFX 函数的调用。 有关详细信息，请参阅[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)中*类库参考*。  
  
##  <a name="_core_how_to_implement_bulk_record_field_exchange"></a>如何实现批量记录字段交换  
 批量记录字段交换将行集的数据从数据源传输到记录集对象。 批量 RFX 函数使用数组来存储此数据，以及数组存储在行集中的每个数据项的长度。 在类定义中，你必须定义将字段数据成员为指针来访问数据的数组。 此外，你必须定义一组的指针访问数组的长度。 不应声明为指针; 为任何参数数据成员声明的参数数据成员时使用批量记录字段交换等同于使用记录字段交换时声明它们。 下面的代码演示一个简单的示例：  
  
```  
class MultiRowSet : public CRecordset  
{  
public:  
   // Field/Param Data  
      // field data members  
      long* m_rgID;  
      LPSTR m_rgName;  
  
      // pointers for the lengths  
      // of the field data  
      long* m_rgIDLengths;  
      long* m_rgNameLengths;  
  
      // input parameter data member  
      CString m_strNameParam;  
  
   .  
   .  
   .  
}  
```  
  
 你可以手动分配这些存储缓冲区或框架完成分配。 若要自己分配缓冲区，必须指定**CRecordset::userAllocMultiRowBuffers**选项**dwOptions**中的参数**打开**成员函数。 请务必将数组的大小设置为至少等于行集大小。 如果你想要完成分配的框架，你应将指针初始化为**NULL。** 这通常是记录集对象的构造函数中：  
  
```  
MultiRowSet::MultiRowSet( CDatabase* pDB )  
   : CRecordset( pDB )  
{  
   m_rgID = NULL;  
   m_rgName = NULL;  
   m_rgIDLengths = NULL;  
   m_rgNameLengths = NULL;  
   m_strNameParam = "";  
  
   m_nFields = 2;  
   m_nParams = 1;  
  
   .  
   .  
   .  
}  
```  
  
 最后，您必须重写`DoBulkFieldExchange`成员函数。 对于字段数据成员调用批量 RFX 函数;对于任何的参数数据成员调用 RFX 函数。 如果打开记录集通过将 SQL 语句或存储的过程传递**打开**，在进行批量 RFX 调用的顺序必须对应于求值的记录集的列; 同样，RFX 的顺序调用参数必须对应于求值的 SQL 语句中的参数或存储过程。  
  
```  
void MultiRowSet::DoBulkFieldExchange( CFieldExchange* pFX )  
{  
   // call the Bulk RFX functions  
   // for field data members  
   pFX->SetFieldType( CFieldExchange::outputColumn );  
   RFX_Long_Bulk( pFX, _T( "[colRecID]" ),  
                  &m_rgID, &m_rgIDLengths );  
   RFX_Text_Bulk( pFX, _T( "[colName]" ),  
                  &m_rgName, &m_rgNameLengths, 30 );  
  
   // call the RFX functions for  
   // for parameter data members  
   pFX->SetFieldType( CFieldExchange::inputParam );  
   RFX_Text( pFX, "NameParam", m_strNameParam );  
}  
```  
  
> [!NOTE]
>  必须调用**关闭**之前你派生的成员函数`CRecordset`类号超出范围。 这可确保释放由框架分配任何内存。 是一个很好的编程做法始终显式调用**关闭**，不管是否已实现批量行提取。  
  
 记录字段交换 (RFX) 有关的详细信息，请参阅[记录字段交换： RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。 有关使用参数的详细信息，请参阅[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)和[记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)   
 [CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)

