---
title: "CRecordset Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRecordset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRecordset class"
  - "database records [C++]"
  - "ODBC 记录集 [C++], CRecordset 对象"
  - "sets of records [C++]"
ms.assetid: dd89a21d-ef39-4aab-891b-1e373d67c855
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CRecordset Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示从数据源中选择的一组记录。  
  
## 语法  
  
```  
class CRecordset : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CRecordset::CRecordset](../Topic/CRecordset::CRecordset.md)|构造 `CRecordset` 对象。  您的派生类必须提供调用此站点的构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CRecordset::AddNew](../Topic/CRecordset::AddNew.md)|为添加新记录准备。  调用 `Update` 添加完。|  
|[CRecordset::CanAppend](../Topic/CRecordset::CanAppend.md)|如果新记录，可以添加到记录集通过 `AddNew` 成员函数，返回非零。|  
|[CRecordset::CanBookmark](../Topic/CRecordset::CanBookmark.md)|如果记录集支持书签，返回非零。|  
|[CRecordset::Cancel](../Topic/CRecordset::Cancel.md)|取消异步操作或处理从另一个线程。|  
|[CRecordset::CancelUpdate](../Topic/CRecordset::CancelUpdate.md)|取消任何挂起更新由于 `AddNew` 或 `Edit` 操作。|  
|[CRecordset::CanRestart](../Topic/CRecordset::CanRestart.md)|如果 `Requery` 可以调用同样，运行记录集的查询返回非零。|  
|[CRecordset::CanScroll](../Topic/CRecordset::CanScroll.md)|如果通过记录，将返回非零。|  
|[CRecordset::CanTransact](../Topic/CRecordset::CanTransact.md)|如果数据源支持事务，返回非零。|  
|[CRecordset::CanUpdate](../Topic/CRecordset::CanUpdate.md)|返回非零，如果记录集可更新\(可以添加，更新或删除记录）。|  
|[CRecordset::CheckRowsetError](../Topic/CRecordset::CheckRowsetError.md)|调用记录获取过程中发生的错误。|  
|[CRecordset::Close](../Topic/CRecordset::Close.md)|关闭记录集和ODBC **HSTMT** 与它。|  
|[CRecordset::Delete](../Topic/CRecordset::Delete.md)|从记录集中删除当前记录。  必须显式移动到另一个记录在该删除操作之后。|  
|[CRecordset::DoBulkFieldExchange](../Topic/CRecordset::DoBulkFieldExchange.md)|调用交换数据批量行从数据源到记录集。  实现批量记录字段交换\(bulk RFX）。|  
|[CRecordset::DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md)|调用交换数据\(在两个方向\)在记录集的字段数据成员和数据源中的相应的记录之间。  实现记录字段交换\(rfx）。|  
|[CRecordset::Edit](../Topic/CRecordset::Edit.md)|为当前记录的更改准备。  调用 `Update` 完成编辑。|  
|[CRecordset::FlushResultSet](../Topic/CRecordset::FlushResultSet.md)|返回非零，如果设置了另一个结果检索，那么，当使用预定义查询时。|  
|[CRecordset::GetBookmark](../Topic/CRecordset::GetBookmark.md)|进行记录的书签值给参数对象。|  
|[CRecordset::GetDefaultConnect](../Topic/CRecordset::GetDefaultConnect.md)|页中获取默认连接字符串。|  
|[CRecordset::GetDefaultSQL](../Topic/CRecordset::GetDefaultSQL.md)|页中获取执行的默认SQL字符串。|  
|[CRecordset::GetFieldValue](../Topic/CRecordset::GetFieldValue.md)|返回一个字段的值在记录集中。|  
|[CRecordset::GetODBCFieldCount](../Topic/CRecordset::GetODBCFieldCount.md)|返回的字段数在记录集中。|  
|[CRecordset::GetODBCFieldInfo](../Topic/CRecordset::GetODBCFieldInfo.md)|返回给定类型有关字段的信息在记录集。|  
|[CRecordset::GetRecordCount](../Topic/CRecordset::GetRecordCount.md)|返回记录的记录集中。|  
|[CRecordset::GetRowsetSize](../Topic/CRecordset::GetRowsetSize.md)|返回在一次获取过程中，您希望检索的记录数。|  
|[CRecordset::GetRowsFetched](../Topic/CRecordset::GetRowsFetched.md)|返回在获取过程中检索实际行数。|  
|[CRecordset::GetRowStatus](../Topic/CRecordset::GetRowStatus.md)|在获取后返回行的状态。|  
|[CRecordset::GetSQL](../Topic/CRecordset::GetSQL.md)|获取SQL字符串用于为记录集选择记录。|  
|[CRecordset::GetStatus](../Topic/CRecordset::GetStatus.md)|获取记录集的状态:当前记录的索引，并记录的最终计数是否已获得。|  
|[CRecordset::GetTableName](../Topic/CRecordset::GetTableName.md)|获取记录集表的名称。|  
|[CRecordset::IsBOF](../Topic/CRecordset::IsBOF.md)|如果将记录集定位，在第一条记录之前，返回非零。  没有当前记录。|  
|[CRecordset::IsDeleted](../Topic/CRecordset::IsDeleted.md)|如果记录集在已删除的记录，确定返回非零。|  
|[CRecordset::IsEOF](../Topic/CRecordset::IsEOF.md)|如果记录集在最后一条记录后，确定返回非零。  没有当前记录。|  
|[CRecordset::IsFieldDirty](../Topic/CRecordset::IsFieldDirty.md)|如果更改了，返回非零在当前记录的指定的字段。|  
|[CRecordset::IsFieldNull](../Topic/CRecordset::IsFieldNull.md)|返回非零，则在当前记录的指定字段为空\(没有值）。|  
|[CRecordset::IsFieldNullable](../Topic/CRecordset::IsFieldNullable.md)|返回非零，则在当前记录的指定字段可以设置为null \(具有值）。|  
|[CRecordset::IsOpen](../Topic/CRecordset::IsOpen.md)|如果 `Open` 之前，调用返回非零。|  
|[CRecordset::Move](../Topic/CRecordset::Move.md)|确定记录集到指定的记录数从当前记录的任一方向。|  
|[CRecordset::MoveFirst](../Topic/CRecordset::MoveFirst.md)|在记录集中的第一条记录确定当前记录。  首先测试 `IsBOF`。|  
|[CRecordset::MoveLast](../Topic/CRecordset::MoveLast.md)|确定当前记录在最后一条记录或在最后一个行集合。  首先测试 `IsEOF`。|  
|[CRecordset::MoveNext](../Topic/CRecordset::MoveNext.md)|确定当前记录在下一条记录或在下行集合。  首先测试 `IsEOF`。|  
|[CRecordset::MovePrev](../Topic/CRecordset::MovePrev.md)|确定当前记录在前一条记录或在前面的集合。  首先测试 `IsBOF`。|  
|[CRecordset::OnSetOptions](../Topic/CRecordset::OnSetOptions.md)|调用设置选项\(使用在选定的指定的ODBC语句。|  
|[CRecordset::OnSetUpdateOptions](../Topic/CRecordset::OnSetUpdateOptions.md)|调用设置选项\(使用在更新\)的指定ODBC语句。|  
|[CRecordset::Open](../Topic/CRecordset::Open.md)|通过检索表或执行记录集表示的查询打开记录集。|  
|[CRecordset::RefreshRowset](../Topic/CRecordset::RefreshRowset.md)|刷新指定的行的数据和状态。|  
|[CRecordset::Requery](../Topic/CRecordset::Requery.md)|再次运行记录集的查询刷新选定的记录。|  
|[CRecordset::SetAbsolutePosition](../Topic/CRecordset::SetAbsolutePosition.md)|在记录确定记录集使用指定的记录数量相对应。|  
|[CRecordset::SetBookmark](../Topic/CRecordset::SetBookmark.md)|在书签中指定的记录定位记录集。|  
|[CRecordset::SetFieldDirty](../Topic/CRecordset::SetFieldDirty.md)|标记在当前记录的指定字段为已更改。|  
|[CRecordset::SetFieldNull](../Topic/CRecordset::SetFieldNull.md)|设置指定字段的值在当前记录的null \(具有值）。|  
|[CRecordset::SetLockingMode](../Topic/CRecordset::SetLockingMode.md)|设置锁定模式“开放式锁定” \(默认值\)或“保守式锁定”。  确定记录如何为更新锁定。|  
|[CRecordset::SetParamNull](../Topic/CRecordset::SetParamNull.md)|将指定的参数设置为null \(具有值）。|  
|[CRecordset::SetRowsetCursorPosition](../Topic/CRecordset::SetRowsetCursorPosition.md)|在行集合中的指定在行光标。|  
|[CRecordset::SetRowsetSize](../Topic/CRecordset::SetRowsetSize.md)|指定在获取过程，您希望检索的记录数。|  
|[CRecordset::Update](../Topic/CRecordset::Update.md)|通过保存新记录或已编辑的数据完成 `AddNew` 或 `Edit` 操作在数据源。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CRecordset::m\_hstmt](../Topic/CRecordset::m_hstmt.md)|包含记录集的ODBC语句处理。  键入 `HSTMT`。|  
|[CRecordset::m\_nFields](../Topic/CRecordset::m_nFields.md)|在记录集包含字段数据成员的数目。  键入 `UINT`。|  
|[CRecordset::m\_nParams](../Topic/CRecordset::m_nParams.md)|在记录集包含参数数据成员的数目。  键入 `UINT`。|  
|[CRecordset::m\_pDatabase](../Topic/CRecordset::m_pDatabase.md)|包含指向记录集连接到数据源的 `CDatabase` 对象。|  
|[CRecordset::m\_strFilter](../Topic/CRecordset::m_strFilter.md)|包含指定结构化查询语言\(SQL\) `WHERE` 子句的 `CString`。  用于，筛选器选择满足特定条件的那些记录。|  
|[CRecordset::m\_strSort](../Topic/CRecordset::m_strSort.md)|包含指定SQL `ORDER BY` 子句的 `CString`。  用于控制日志排序。|  
  
## 备注  
 称为“记录集”，`CRecordset` 对象通常用于两种形式:动态集和快照。  动态集保持与其他用户所做的更新数据同步。  快照是数据的静态视图。  每个窗体表示已修复的一组记录，每次打开记录集，但，以便在移动到动态集时的记录，它反映其他记录集以后对该记录，由其他用户或更改在应用程序中。  
  
> [!NOTE]
>  如果您使用的是数据访问使用否决\(DAO\)选件类而不是开放式数据库连接\(odbc\)选件类，使用选件类 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  有关更多信息，请参见文章 [概述:数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
 若要使用branch使用类型的记录集，则从 `CRecordset`通常派生特定的记录集选件类。  从数据源的记录集选择记录和然后可以:  
  
-   滚动记录。  
  
-   更新记录并指定一个锁定模式。  
  
-   筛选记录它从这些选择可用在数据源的记录集约束。  
  
-   排序记录集。  
  
-   参数化记录集自定义该控件的信息选择未知直到运行时。  
  
 若要使用您的选件类，请打开数据库并构造记录集对象，通过构造函数指针到您的 `CDatabase` 对象。  然后调用记录集的 **Open** 成员函数，可以指定对象是否是动态集还是快照。  调用 **Open** 选择数据从数据源。  在打开后记录集对象，请使用其成员函数和数据成员滚动记录和对它们。  可用的操作取决于对象是否是动态集或快照，它是否可更新或只读\(这取决于开放式数据库连接\(odbc\)数据源\)的功能，因此，您是否实现批量取行。  若要刷新可能已更改或添加的记录，因为 **Open** 调用，调用对象的 **Requery** 成员函数。  当您完成使用协定时，调用对象的 **Close** 成员函数和销毁对象。  
  
 在派生的 `CRecordset` 选件类，记录字段交换\(rfx\)或批量记录字段交换\(bulk RFX\)用于支持读取和更新记录字段。  
  
 有关记录集和记录字段交换的更多信息，请参见位于 [概述:数据库编程](../../data/data-access-programming-mfc-atl.md)、 [记录集\(odbc\)](../../data/odbc/recordset-odbc.md)、 [记录集:获取记录\(odbc\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和 [记录字段交换\(rfx\)](../../data/odbc/record-field-exchange-rfx.md)。  有关动态集和快照中的一个焦点，请参见位于 [动态集](../../data/odbc/dynaset.md) 和 [快照](../../data/odbc/snapshot.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CRecordset`  
  
## 要求  
 **Header:** afxdb.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)   
 [CRecordView Class](../../mfc/reference/crecordview-class.md)