---
title: "记录集：批量获取记录 (ODBC) | Microsoft Docs"
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
  - "批量记录字段交换"
  - "批量 RFX 函数"
  - "批量取行"
  - "批量取行, 实现"
  - "DoBulkFieldExchange 方法"
  - "批量获取 ODBC 记录"
  - "ODBC 记录集, 批量取行"
  - "记录集, 批量取行"
  - "RFX (ODBC), 批量"
  - "RFX (ODBC), 批量取行"
  - "行集合, 批量取行"
ms.assetid: 20d10fe9-c58a-414a-b675-cdf9aa283e4f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集：批量获取记录 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 类 `CRecordset` 提供对批量取行的支持，这意味着在一次获取过程中可从数据源同时检索多个记录而不是一次检索一个记录。  只能在派生的 `CRecordset` 类中实现批量取行。  将数据从数据源传输到记录集对象的过程称作批量记录字段交换 \(Bulk RFX\)。  注意，如果在 `CRecordset` 派生类中不使用批量取行，则数据通过记录字段交换 \(RFX\) 进行传输。  有关更多信息，请参见[记录字段交换 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)。  
  
 本主题说明：  
  
-   [CRecordset 支持批量取行的方式](#_core_how_crecordset_supports_bulk_row_fetching)。  
  
-   [使用批量取行时的特殊注意事项](#_core_special_considerations)。  
  
-   [实现批量记录字段交换的方式](#_core_how_to_implement_bulk_record_field_exchange)。  
  
##  <a name="_core_how_crecordset_supports_bulk_row_fetching"></a> CRecordset 如何支持批量取行  
 打开记录集对象之前，可使用 `SetRowsetSize` 成员函数定义行集合大小。  行集合大小指定在一次获取过程中应检索的记录个数。  当批量取行实现时，默认的行集合大小为 25。  如果批量取行尚未实现，则行集合大小保持固定值 1。  
  
 初始化行集合大小之后，请调用 [Open](../Topic/CRecordset::Open.md) 成员函数。  此处必须指定 **dwOptions** 参数的 `CRecordset::useMultiRowFetch` 选项以便实现批量取行。  可附加设置 **CRecordset::userAllocMultiRowBuffers** 选项。  批量记录字段交换机制使用数组存储获取过程中检索到的多行数据。  这些存储缓冲区可由框架自动分配，也可手动分配。  指定 **CRecordset::userAllocMultiRowBuffers** 选项意味着您将执行分配。  
  
 下表列出了由 `CRecordset` 提供的用以支持批量取行的成员函数。  
  
|成员函数|说明|  
|----------|--------|  
|[CheckRowsetError](../Topic/CRecordset::CheckRowsetError.md)|处理获取过程中所发生错误的虚函数。|  
|[DoBulkFieldExchange](../Topic/CRecordset::DoBulkFieldExchange.md)|实现批量记录字段交换。  自动调用以便将多行数据从数据源传输到记录集对象。|  
|[GetRowsetSize](../Topic/CRecordset::GetRowsetSize.md)|检索行集合大小的当前设置。|  
|[GetRowsFetched](../Topic/CRecordset::GetRowsFetched.md)|在给定的获取之后通知实际检索到的行数。  多数情况下，该行数为行集合的大小，除非获取的是不完整的行集合。|  
|[GetRowStatus](../Topic/CRecordset::GetRowStatus.md)|返回行集合中特定行的获取状态。|  
|[RefreshRowset](../Topic/CRecordset::RefreshRowset.md)|刷新行集合中特定行的数据与状态。|  
|[SetRowsetCursorPosition](../Topic/CRecordset::SetRowsetCursorPosition.md)|将光标移动到行集合中的特定行。|  
|[SetRowsetSize](../Topic/CRecordset::SetRowsetSize.md)|将行集合大小的设置更改为指定值的虚函数。|  
  
##  <a name="_core_special_considerations"></a> 特殊的注意事项  
 虽然批量取行是性能增益，但某些功能的操作方式不同。  在决定实现批量取行之前，请注意以下事项：  
  
-   框架将自动调用 `DoBulkFieldExchange` 成员函数以将数据从数据源传输到记录集对象。  但数据不能从记录集传输回数据源。  调用 `AddNew`、**Edit**、**Delete** 或 **Update** 成员函数将导致断言失败。  虽然类 `CRecordset` 当前没有提供更新数据批量行的机制，但您仍然可以使用 ODBC API 函数 **SQLSetPos** 来编写您自己的函数。  有关 **SQLSetPos** 的更多信息，请参见 MSDN 文档中的 ODBC SDK Programmer's Reference（ODBC SDK 程序员参考）。  
  
-   成员函数 `IsDeleted`、`IsFieldDirty`、`IsFieldNull`、`IsFieldNullable`、`SetFieldDirty` 及 `SetFieldNull` 不能用于实现批量取行的记录集。  但可调用 `GetRowStatus` 替换 `IsDeleted`，调用 `GetODBCFieldInfo` 替换 `IsFieldNullable`。  
  
-   **Move** 操作将通过行集合重定位记录集。  例如，假设您打开一个包含 100 条记录，且初始行集合大小为 10 的记录集。  **Open** 将取第 1 至第 10 行，且当前记录位于第 1 行。  对 `MoveNext` 的调用将取下一个行集合而不是下一行。  下一个行集合包括第 11 至第 20 行，且当前记录位于第 11 行。  注意，当批量取行实现时，`MoveNext` 与 **Move\( 1 \)** 将不再等效。  **Move\( 1 \)** 将从当前记录的第 1 行开始取行集合。  在本例中，调用 **Open** 之后调用 **Move\( 1 \)** 将取包括第 2 至第 11 行的行集合，且当前记录位于第 2 行。  有关更多信息，请参见 [Move](../Topic/CRecordset::Move.md) 成员函数。  
  
-   与记录字段交换不同，向导不支持批量记录字段交换。  这意味着您必须将调用写到 Bulk RFX 函数，以便手动声明字段数据成员及手动重写 `DoBulkFieldExchange`。  有关更多信息，请参见《类库参考》中的[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。  
  
##  <a name="_core_how_to_implement_bulk_record_field_exchange"></a> 如何实现批量记录字段交换  
 批量记录字段交换将行集合数据从数据源传输到记录集对象。  Bulk RFX 函数使用数组存储该行集合中的数据以及每个数据项的长度。  在类定义中，必须将字段数据成员定义为指针以便访问数据数组。  此外，必须定义一组指针以访问长度数组。  不应将任何参数数据成员声明为指针；使用批量记录字段交换时声明参数数据成员与使用记录字段交换时声明参数数据成员作用相同。  下列代码显示了一个简单的示例：  
  
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
  
 既可手动分配存储缓冲区也可使用框架完成分配。  若要手动分配缓冲区，必须在 **Open** 成员函数中指定 **dwOptions** 参数的 **CRecordset::userAllocMultiRowBuffers** 选项。  请确保将数组大小至少设置为等于行集合大小。  如果希望框架完成分配，则应将指针初始化为 **NULL**。该操作通常在记录集对象的构造函数中完成：  
  
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
  
 最后，必须重写 `DoBulkFieldExchange` 成员函数。  为字段数据成员调用 Bulk RFX 函数；为任何参数数据成员调用 RFX 函数。  如果通过将 SQL 语句或存储过程传递给 **Open** 而打开记录集，则生成 Bulk RFX 调用的顺序必须与记录集中的列的顺序相对应；同样，参数的 RFX 调用顺序必须与 SQL 语句或存储过程中的参数顺序相对应。  
  
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
>  在派生的 `CRecordset` 类超出范围之前，必须调用 **Close** 成员函数。  这将确保框架分配的所有内存得以释放。  不论批量取行实现与否，都要始终显式调用 **Close**，这是一个良好的编程习惯。  
  
 有关记录字段交换 \(RFX\) 的更多信息，请参见[记录字段交换：RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  有关使用参数的更多信息，请参见 [CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md) 及[记录集：参数化记录集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::m\_nFields](../Topic/CRecordset::m_nFields.md)   
 [CRecordset::m\_nParams](../Topic/CRecordset::m_nParams.md)