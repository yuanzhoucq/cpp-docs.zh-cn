---
title: "CRecordset 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRecordset
- AFXDB/CRecordset
- AFXDB/CRecordset::CRecordset
- AFXDB/CRecordset::AddNew
- AFXDB/CRecordset::CanAppend
- AFXDB/CRecordset::CanBookmark
- AFXDB/CRecordset::Cancel
- AFXDB/CRecordset::CancelUpdate
- AFXDB/CRecordset::CanRestart
- AFXDB/CRecordset::CanScroll
- AFXDB/CRecordset::CanTransact
- AFXDB/CRecordset::CanUpdate
- AFXDB/CRecordset::CheckRowsetError
- AFXDB/CRecordset::Close
- AFXDB/CRecordset::Delete
- AFXDB/CRecordset::DoBulkFieldExchange
- AFXDB/CRecordset::DoFieldExchange
- AFXDB/CRecordset::Edit
- AFXDB/CRecordset::FlushResultSet
- AFXDB/CRecordset::GetBookmark
- AFXDB/CRecordset::GetDefaultConnect
- AFXDB/CRecordset::GetDefaultSQL
- AFXDB/CRecordset::GetFieldValue
- AFXDB/CRecordset::GetODBCFieldCount
- AFXDB/CRecordset::GetODBCFieldInfo
- AFXDB/CRecordset::GetRecordCount
- AFXDB/CRecordset::GetRowsetSize
- AFXDB/CRecordset::GetRowsFetched
- AFXDB/CRecordset::GetRowStatus
- AFXDB/CRecordset::GetSQL
- AFXDB/CRecordset::GetStatus
- AFXDB/CRecordset::GetTableName
- AFXDB/CRecordset::IsBOF
- AFXDB/CRecordset::IsDeleted
- AFXDB/CRecordset::IsEOF
- AFXDB/CRecordset::IsFieldDirty
- AFXDB/CRecordset::IsFieldNull
- AFXDB/CRecordset::IsFieldNullable
- AFXDB/CRecordset::IsOpen
- AFXDB/CRecordset::Move
- AFXDB/CRecordset::MoveFirst
- AFXDB/CRecordset::MoveLast
- AFXDB/CRecordset::MoveNext
- AFXDB/CRecordset::MovePrev
- AFXDB/CRecordset::OnSetOptions
- AFXDB/CRecordset::OnSetUpdateOptions
- AFXDB/CRecordset::Open
- AFXDB/CRecordset::RefreshRowset
- AFXDB/CRecordset::Requery
- AFXDB/CRecordset::SetAbsolutePosition
- AFXDB/CRecordset::SetBookmark
- AFXDB/CRecordset::SetFieldDirty
- AFXDB/CRecordset::SetFieldNull
- AFXDB/CRecordset::SetLockingMode
- AFXDB/CRecordset::SetParamNull
- AFXDB/CRecordset::SetRowsetCursorPosition
- AFXDB/CRecordset::SetRowsetSize
- AFXDB/CRecordset::Update
- AFXDB/CRecordset::m_hstmt
- AFXDB/CRecordset::m_nFields
- AFXDB/CRecordset::m_nParams
- AFXDB/CRecordset::m_pDatabase
- AFXDB/CRecordset::m_strFilter
- AFXDB/CRecordset::m_strSort
dev_langs:
- C++
helpviewer_keywords:
- database records [C++]
- CRecordset class
- ODBC recordsets [C++], CRecordset objects
- sets of records [C++]
ms.assetid: dd89a21d-ef39-4aab-891b-1e373d67c855
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: f7a05a5eefd6f55a68c6e9f1726dfb7c29f399f2
ms.lasthandoff: 02/24/2017

---
# <a name="crecordset-class"></a>CRecordset 类
表示从数据源选择的一组记录。  
  
## <a name="syntax"></a>语法  
  
```  
class CRecordset : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CRecordset::CRecordset](#crecordset)|构造 `CRecordset` 对象。 在派生的类必须提供可调用此构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CRecordset::AddNew](#addnew)|准备用于添加新记录。 调用`Update`完成添加。|  
|[CRecordset::CanAppend](#canappend)|返回非零，如果可以将新记录添加到通过记录集`AddNew`成员函数。|  
|[CRecordset::CanBookmark](#canbookmark)|返回非零，如果该记录集支持书签。|  
|[CRecordset::Cancel](#cancel)|取消一个异步操作或从第二个线程的进程。|  
|[CRecordset::CancelUpdate](#cancelupdate)|取消任何挂起的更新，由于`AddNew`或`Edit`操作。|  
|[CRecordset::CanRestart](#canrestart)|返回非零 if`Requery`可以调用以再次运行记录集的查询。|  
|[CRecordset::CanScroll](#canscroll)|返回非零，如果您可以滚动浏览记录。|  
|[CRecordset::CanTransact](#cantransact)|返回非零，如果数据源支持事务。|  
|[CRecordset::CanUpdate](#canupdate)|返回非零，如果可以更新记录集 （您可以添加、 更新或删除记录）。|  
|[CRecordset::CheckRowsetError](#checkrowseterror)|调用处理记录读取期间生成的错误。|  
|[CRecordset::Close](#close)|关闭记录集和 ODBC **HSTMT**与其相关联。|  
|[CRecordset::Delete](#delete)|从记录集中删除当前记录。 您必须显式滚动到另一条记录后删除。|  
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|调用来交换大容量数据行的数据源得到记录集。 实现批量记录字段交换 (Bulk RFX)。|  
|[CRecordset::DoFieldExchange](#dofieldexchange)|调用之间交换数据 （在两个方向） 记录集的字段数据成员和数据源上相应的记录。 实现记录字段交换 (RFX)。|  
|[CRecordset::Edit](#edit)|准备要对当前记录的更改。 调用`Update`来完成编辑。|  
|[CRecordset::FlushResultSet](#flushresultset)|返回非零，如果没有其他结果设置为在使用预定义的查询时进行检索。|  
|[CRecordset::GetBookmark](#getbookmark)|将一条记录的书签值分配给参数对象。|  
|[CRecordset::GetDefaultConnect](#getdefaultconnect)|调用以获取默认连接字符串。|  
|[CRecordset::GetDefaultSQL](#getdefaultsql)|调用以获取要执行的默认 SQL 字符串。|  
|[CRecordset::GetFieldValue](#getfieldvalue)|在记录集中返回的字段的值。|  
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|在记录集中返回的字段的数目。|  
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|在记录集中返回特定类型的字段的信息。|  
|[CRecordset::GetRecordCount](#getrecordcount)|在记录集中返回记录的数。|  
|[CRecordset::GetRowsetSize](#getrowsetsize)|返回要在一次获取期间检索的记录数。|  
|[CRecordset::GetRowsFetched](#getrowsfetched)|返回在提取过程中检索实际的行数。|  
|[CRecordset::GetRowStatus](#getrowstatus)|后一次提取返回的行的状态。|  
|[CRecordset::GetSQL](#getsql)|获取用于选择记录的记录集的 SQL 字符串。|  
|[CRecordset::GetStatus](#getstatus)|获取记录集的状态︰ 当前记录和记录的最终计数是否已获取的索引。|  
|[CRecordset::GetTableName](#gettablename)|获取记录集所基于的表的名称。|  
|[CRecordset::IsBOF](#isbof)|返回记录集已放在第一条记录之前，非零值。 没有当前记录。|  
|[CRecordset::IsDeleted](#isdeleted)|返回非零，如果记录集中定位在已删除的记录。|  
|[CRecordset::IsEOF](#iseof)|返回非零，如果在最后一条记录后定位完记录集。 没有当前记录。|  
|[CRecordset::IsFieldDirty](#isfielddirty)|返回非零，如果已更改为当前记录中指定的字段。|  
|[CRecordset::IsFieldNull](#isfieldnull)|返回为当前记录中指定的字段为 null 时，非零值 （不具有任何值）。|  
|[CRecordset::IsFieldNullable](#isfieldnullable)|返回非零，如果可以设置为当前记录中指定的字段为 null （具有任何值）。|  
|[CRecordset::IsOpen](#isopen)|返回非零 if`Open`已被调用过。|  
|[CRecordset::Move](#move)|定位记录集到指定的记录数从两个方向中的当前记录。|  
|[CRecordset::MoveFirst](#movefirst)|将当前记录定位在记录集中的第一个记录。 测试`IsBOF`第一个。|  
|[CRecordset::MoveLast](#movelast)|将当前记录定位或最后一个行集合上最后一条记录。 测试`IsEOF`第一个。|  
|[CRecordset::MoveNext](#movenext)|在下一条记录或下一个行集上，将定位当前记录。 测试`IsEOF`第一个。|  
|[CRecordset::MovePrev](#moveprev)|在上一条记录或上一个行集上，将定位当前记录。 测试`IsBOF`第一个。|  
|[CRecordset::OnSetOptions](#onsetoptions)|若要设置 （用于所选内容上） 的选项为调用指定的 ODBC 语句。|  
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|调用以设置指定的 ODBC 语句 （update 上使用） 的选项。|  
|[CRecordset::Open](#open)|通过检索表或执行查询来表示该记录集打开记录集。|  
|[CRecordset::RefreshRowset](#refreshrowset)|刷新的数据和状态的指定的行。|  
|[CRecordset::Requery](#requery)|将运行再次以刷新所选的记录的记录集的查询。|  
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|将记录集中定位到指定的记录号相对应的记录。|  
|[CRecordset::SetBookmark](#setbookmark)|将记录集中定位指定的书签的记录。|  
|[CRecordset::SetFieldDirty](#setfielddirty)|将当前记录中指定的字段标记为已更改。|  
|[CRecordset::SetFieldNull](#setfieldnull)|设置为 null （具有任何值） 为当前记录中指定的字段的值。|  
|[CRecordset::SetLockingMode](#setlockingmode)|设置为"开放式"锁定 （默认值） 或"保守式"锁定的锁定模式。 确定如何记录被锁定，无法更新。|  
|[CRecordset::SetParamNull](#setparamnull)|将指定的参数设置为 null （具有任何值）。|  
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|将光标置于该行集内指定的行。|  
|[CRecordset::SetRowsetSize](#setrowsetsize)|指定你想要在提取过程中检索的记录数。|  
|[CRecordset::Update](#update)|完成`AddNew`或`Edit`通过将新的或编辑数据保存在数据源上的操作。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CRecordset::m_hstmt](#m_hstmt)|包含记录集的 ODBC 语句句柄。 键入 `HSTMT`。|  
|[CRecordset::m_nFields](#m_nfields)|包含在记录集中的字段数据成员的数目。 键入 `UINT`。|  
|[CRecordset::m_nParams](#m_nparams)|包含在记录集中的参数数据成员的数目。 键入 `UINT`。|  
|[CRecordset::m_pDatabase](#m_pdatabase)|包含一个指向`CDatabase`通过该记录集连接到数据源对象。|  
|[CRecordset::m_strFilter](#m_strfilter)|包含`CString`，用于指定结构化查询语言 (SQL)`WHERE`子句。 用作筛选器以选择满足特定条件的那些记录。|  
|[CRecordset::m_strSort](#m_strsort)|包含`CString`，它指定一个 SQL`ORDER BY`子句。 用于控制所记录的排序方式。|  
  
## <a name="remarks"></a>备注  
 称为"记录集，"`CRecordset`对象通常使用两种形式︰ 动态集和快照。 动态集与其他用户所做的数据更新中保持同步。 快照是数据的静态视图。 每个窗体表示一组固定的记录集打开时，记录但时滚动到中动态集的记录时，它反映随后所做的更改记录，其他用户或应用程序中的其他记录集。  
  
> [!NOTE]
>  如果您正在使用的数据访问对象 (DAO) 类，而不是开放式数据库连接 (ODBC) 类，可以使用类[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)相反。 有关详细信息，请参阅文章[概述︰ 数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
 若要使用这两种记录集，则通常派生从一个应用程序特定的记录集类`CRecordset`。 记录集选择数据源中的记录，然后，你可以︰  
  
-   滚动记录。  
  
-   更新的记录，并指定锁定模式。  
  
-   筛选记录集来限制从可用的那些数据源选择哪些记录。  
  
-   对记录集进行排序。  
  
-   参数化记录集进行自定义信息直到运行时才知道的所选内容。  
  
 若要使用您的类，打开数据库，然后构造一个记录集对象，将构造函数传递一个指向您`CDatabase`对象。 然后，调用记录集的**打开**成员函数，您可以在其中指定对象是否是动态集或快照。 调用**打开**从数据源选择数据。 打开记录集对象后，使用其成员函数和数据成员滚动查看记录和对它们进行操作。 可用的操作取决于该对象是动态集还是快照，它是否可更新或只读模式 （这取决于开放式数据库连接 (ODBC) 数据源的功能），和批量取行实现。 若要刷新记录可能已更改或添加自**打开**调用，调用对象的**Requery**成员函数。 调用对象的**关闭**成员函数，并与之完成后销毁对象。  
  
 在派生`CRecordset`类中，记录字段交换 (RFX) 或批量记录字段交换 (Bulk RFX) 用来支持读取和更新的记录字段。  
  
 有关记录集和记录字段交换的详细信息，请参阅文章[概述︰ 数据库编程](../../data/data-access-programming-mfc-atl.md)，[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)，[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)，和[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。 专注于动态集与快照，请参阅文章[动态集](../../data/odbc/dynaset.md)和[快照](../../data/odbc/snapshot.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CRecordset`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdb.h  
  
##  <a name="addnew"></a>CRecordset::AddNew  
 准备要向表添加一条新记录。  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>备注  
 必须调用[Requery](#requery)成员函数，以查看新添加的记录。 记录的字段是最初为 Null。 (在数据库术语中，Null 意味着您"没有值"，并且不与相同**NULL** c + + 中。)若要完成该操作，必须调用[更新](#update)成员函数。 **更新**将所做的更改保存到数据源。  
  
> [!NOTE]
>  如果已实现批量取行，则无法调用`AddNew`。 这将导致失败的断言。 尽管类`CRecordset`不提供一种机制进行更新的数据大容量行，您可以通过使用 ODBC API 函数中编写您自己的函数**SQLSetPos**。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 `AddNew`准备新的空记录中使用的记录集的字段数据成员。 在您调用之后`AddNew`，在记录集的字段数据成员中设置所需的值。 (无需调用[编辑](#edit)实现此目的的成员函数; 请改用**编辑**仅为现有记录。)当您随后调用**更新**、 已更改的字段数据成员中的值保存在数据源上。  
  
> [!CAUTION]
>  如果您向下滚动到一条新记录然后才能调用**更新**、 新的记录将会丢失，并给出任何警告。  
  
 如果数据源支持事务，则可以使您`AddNew`调用事务的一部分。 有关事务的详细信息，请参阅类[CDatabase](../../mfc/reference/cdatabase-class.md)。 请注意，应调用[CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans)之前调用`AddNew`。  
  
> [!NOTE]
>  对于动态集，新记录添加到记录集中作为最后一条记录。 添加的记录不会添加到快照;必须调用**Requery**来刷新记录集。  
  
 您不能调用`AddNew`为记录集其**打开**尚未调用成员函数。 一个`CDBException`您调用将引发`AddNew`为不能追加到记录集。 您可以确定记录集是否可以更新通过调用[CanAppend](#canappend)。  
  
 有关详细信息，请参阅以下文章︰[记录集︰ 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)，[记录集︰ 添加、 更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)，和[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
### <a name="example"></a>示例  
 请参阅文章[事务︰ 在记录集 (ODBC) 执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。  
  
##  <a name="canappend"></a>CRecordset::CanAppend  
 确定是否先前已打开记录集允许您添加新记录。  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果是记录集允许添加新记录;否则为 0。 `CanAppend`如果您打开记录集为只读，则将返回 0。  
  
##  <a name="canbookmark"></a>CRecordset::CanBookmark  
 确定是否记录集，可以将记录使用书签标记。  
  
```  
BOOL CanBookmark() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果该记录集支持书签;否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数是独立于**CRecordset::useBookmarks**选项`dwOptions`参数[打开](#open)成员函数。 `CanBookmark`指示给定的 ODBC 驱动程序和游标类型是否支持书签。 **CRecordset::useBookmarks**指示是否对书签可用，提供支持它们。  
  
> [!NOTE]
>  只能向前的记录集不支持书签。  
  
 有关书签和记录集导航的详细信息，请参阅文章[记录集︰ 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[记录集︰ 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
##  <a name="cancel"></a>CRecordset::Cancel  
 数据源取消正在进行的异步操作或从第二个线程的进程的请求。  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>备注  
 请注意，MFC ODBC 类不能再使用异步处理;若要执行异步操作，必须直接调用 ODBC API 函数**SQLSetConnectOption**。 详细信息，请参阅"异步执行函数"主题中*ODBC SDK 程序员指南*。  
  
##  <a name="cancelupdate"></a>CRecordset::CancelUpdate  
 取消任何挂起的更新、 引起[编辑](#edit)或[AddNew](#addnew)操作时之前,[更新](#update)调用。  
  
```  
void CancelUpdate();
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  此成员函数不是适用于正在使用批量取行，因为不能调用此类记录集的记录集**编辑**， `AddNew`，或**更新**。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 如果启用了自动已更新的字段检查，`CancelUpdate`将还原到之前所具有的值的成员变量**编辑**或`AddNew`调用; 否则为值的任何更改将保留。 默认情况下，自动字段启用检查时打开记录集。 若要禁用它，必须指定**CRecordset::noDirtyFieldCheck**中`dwOptions`参数[打开](#open)成员函数。  
  
 有关更新数据的详细信息，请参阅文章[记录集︰ 添加、 更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)。  
  
##  <a name="canrestart"></a>CRecordset::CanRestart  
 确定记录集是否允许重新查询 （若要刷新其记录） 启动通过调用**Requery**成员函数。  
  
```  
BOOL CanRestart() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果允许重新查询; 非零值否则为 0。  
  
##  <a name="canscroll"></a>CRecordset::CanScroll  
 确定记录集是否允许滚动。  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果是记录集允许滚动，则为非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 有关滚动的详细信息，请参阅文章[记录集︰ 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
##  <a name="cantransact"></a>CRecordset::CanTransact  
 确定记录集是否允许事务。  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果是记录集允许事务;否则为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="canupdate"></a>CRecordset::CanUpdate  
 确定是否可以更新记录集。  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果可以更新记录集，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 记录集可能是只读的如果基础数据源是只读的或者如果您指定**CRecordset::readOnly**中`dwOptions`参数时打开记录集。  
  
##  <a name="checkrowseterror"></a>CRecordset::CheckRowsetError  
 调用处理记录读取期间生成的错误。  
  
```  
virtual void CheckRowsetError(RETCODE nRetCode);
```  
  
### <a name="parameters"></a>参数  
 `nRetCode`  
 ODBC API 函数的返回代码。 有关详细信息，请参阅“备注”。  
  
### <a name="remarks"></a>备注  
 此虚拟成员函数处理时提取的记录，可能发生的错误，在批量取行期间很有用。 您可能会考虑重写`CheckRowsetError`来实现您自己的错误处理。  
  
 `CheckRowsetError`会自动调用在光标导航操作中，如**打开**， **Requery**，或其任意**移动**操作。 它传递的 ODBC API 函数的返回值**SQLExtendedFetch**。 下表列出的可能值`nRetCode`参数。  
  
|nRetCode|描述|  
|--------------|-----------------|  
|**SQL_SUCCESS**|函数成功地完成。提供不了任何其他信息。|  
|**SQL_SUCCESS_WITH_INFO**|已成功完成，可能出现非致命错误的函数。 可以通过调用获取其他信息**SQLError**。|  
|**SQL_NO_DATA_FOUND**|已提取从结果集中的所有行。|  
|**SQL_ERROR**|失败的函数。 可以通过调用获取其他信息**SQLError**。|  
|**SQL_INVALID_HANDLE**|函数失败由于无效的环境句柄、 连接句柄或语句句柄。 这指示编程错误。 无附加信息可从**SQLError**。|  
|`SQL_STILL_EXECUTING`|以异步方式启动函数仍在执行。 请注意，默认情况下，MFC 将永远不会将此值传递到`CheckRowsetError`;MFC 将继续调用**SQLExtendedFetch** ，直到不再返回`SQL_STILL_EXECUTING`。|  
  
 有关详细信息**SQLError**，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="close"></a>CRecordset::Close  
 关闭记录集。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 ODBC **HSTMT**和释放分配给记录集的框架的所有内存。 通常在调用之后**关闭**，如果它已分配与删除 c + + recordset 对象**新**。  
  
 您可以调用**打开**在调用后再次**关闭**。 这样就可以重用该记录集对象。 替代方法是调用**Requery**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase #&17;](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]  
  
##  <a name="crecordset"></a>CRecordset::CRecordset  
 构造 `CRecordset` 对象。  
  
```  
CRecordset(CDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pDatabase`  
 包含一个指向`CDatabase`对象或值**NULL**。 如果不是**NULL**和`CDatabase`对象的**打开**成员函数不调用才能将其连接到数据源时，记录集尝试打开它为您自己在**打开**调用。 如果您通过**NULL**、`CDatabase`构造并为您使用您指定当派生类向导使用记录集类的数据源信息而连接对象。  
  
### <a name="remarks"></a>备注  
 您既可以使用`CRecordset`直接或应用程序特定的类从其派生`CRecordset`。 类向导可用于派生的记录集类。  
  
> [!NOTE]
>  派生的类*必须*提供其自己的构造函数。 在派生类的构造函数调用的构造函数`CRecordset::CRecordset`，将沿着适当的参数传递给它。  
  
 传递**NULL**给记录集构造函数，可具有`CDatabase`对象构造，并为您自动连接。 这是一种有用的简写形式，不需要您来构造和连接`CDatabase`之前构建您的记录集对象。  
  
### <a name="example"></a>示例  
 有关详细信息，请参阅文章[记录集︰ 声明一个类用于表 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。  
  
##  <a name="delete"></a>CRecordset::Delete  
 删除当前记录。  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>备注  
 成功删除操作之后，记录集的字段数据成员设置为一个 Null 值，并且必须显式调用其中一个**移动**若要离开已删除的记录的函数。 一旦离开已删除的记录，它不是无法返回到它。 如果数据源支持事务，则可以使**删除**调用事务的一部分。 有关详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
> [!NOTE]
>  如果已实现批量取行，则无法调用**删除**。 这将导致失败的断言。 尽管类`CRecordset`不提供一种机制进行更新的数据大容量行，您可以通过使用 ODBC API 函数中编写您自己的函数**SQLSetPos**。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
> [!CAUTION]
>  记录集必须可更新，并且必须有有效的记录中记录集的当前调用时**删除**; 否则为就会出错。 例如，如果您删除一条记录，但在调用之前不会发生滚动到一条新记录**删除**再次重申，**删除**引发[CDBException](../../mfc/reference/cdbexception-class.md)。  
  
 与不同[AddNew](#addnew)和[编辑](#edit)，调用**删除**对的调用后面不接[更新](#update)。 如果**删除**调用失败，则字段数据成员将保留不变。  
  
### <a name="example"></a>示例  
 此示例演示在函数的帧上创建一个记录集。 该示例假定存在`m_dbCust`，类型的成员变量`CDatabase`已连接到数据源。  
  
 [!code-cpp[NVC_MFCDatabase #&18;](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]  
  
##  <a name="dobulkfieldexchange"></a>CRecordset::DoBulkFieldExchange  
 调用来交换大容量数据行的数据源得到记录集。 实现批量记录字段交换 (Bulk RFX)。  
  
```  
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 一个指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象。 框架将已设置该对象指定字段的 exchange 操作上下文。  
  
### <a name="remarks"></a>备注  
 批量取行是在实现时，框架将调用该成员函数以自动将数据从数据源传输到记录集对象。 `DoBulkFieldExchange`如果有的话，到记录集的所选内容的 SQL 语句字符串中的参数占位符，还将您的参数数据成员绑定。  
  
 如果未实现批量取行，框架将调用[DoFieldExchange](#dofieldexchange)。 若要实现批量取行，您必须指定`CRecordset::useMultiRowFetch`选项`dwOptions`中的参数[打开](#open)成员函数。  
  
> [!NOTE]
> `DoBulkFieldExchange`仅当使用派生类可用`CRecordset`。 如果已创建直接从记录集对象`CRecordset`，必须调用[GetFieldValue](#getfieldvalue)成员函数以检索数据。  
  
 批量记录字段交换 (Bulk RFX) 等同于记录字段交换 (RFX)。 数据是自动从数据源传输到记录集对象。 但是，无法调用`AddNew`，**编辑**，**删除**，或**更新**传输回数据源的更改。 类`CRecordset`目前不提供机制更新大容量行的数据; 但是，可以通过使用 ODBC API 函数编写您自己的函数**SQLSetPos**。  
  
 请注意，ClassWizard 不支持批量记录字段交换;因此，您必须重写`DoBulkFieldExchange`手动通过编写对批量 RFX 函数的调用。 有关这些函数的详细信息，请参阅主题[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。  
  
 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 有关相关信息，请参阅文章[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
##  <a name="dofieldexchange"></a>CRecordset::DoFieldExchange  
 调用之间交换数据 （在两个方向） 记录集的字段数据成员和数据源上相应的记录。 实现记录字段交换 (RFX)。  
  
```  
virtual void DoFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 一个指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象。 框架将已设置该对象指定字段的 exchange 操作上下文。  
  
### <a name="remarks"></a>备注  
 批量取行是不在实现时，框架将调用该成员函数以自动交换字段数据成员的记录集对象和数据源上的当前记录的相应列之间的数据。 `DoFieldExchange`如果有的话，到记录集的所选内容的 SQL 语句字符串中的参数占位符，还将您的参数数据成员绑定。  
  
 如果实现批量取行，框架将调用[DoBulkFieldExchange](#dobulkfieldexchange)。 若要实现批量取行，您必须指定`CRecordset::useMultiRowFetch`选项`dwOptions`中的参数[打开](#open)成员函数。  
  
> [!NOTE]
> `DoFieldExchange`仅当使用派生类可用`CRecordset`。 如果已创建直接从记录集对象`CRecordset`，必须调用[GetFieldValue](#getfieldvalue)成员函数以检索数据。  
  
 交换字段数据，调用记录字段交换 (RFX)，可以在这两个方向︰ 从数据源上记录的字段记录集对象的字段数据成员和记录集对象的数据源上的记录。  
  
 您通常必须执行以便实现的唯一操作`DoFieldExchange`对于派生的记录集类是用类向导创建类并指定的字段数据成员的名称和数据类型。 您可以向 ClassWizard 写入指定的参数数据成员或处理动态绑定的任何列中添加代码。 有关详细信息，请参阅文章[记录集︰ 动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
 在声明派生的记录集类与类向导时，向导会将写入的重写`DoFieldExchange`，类似于下面的示例︰  
  
 [!code-cpp[NVC_MFCDatabase #&19;](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]  
  
 有关 RFX 函数的详细信息，请参阅主题[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。  
  
 有关详细信息的其他示例以及`DoFieldExchange`，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。 有关 RFX 的一般信息，请参阅文章[记录字段交换](../../data/odbc/record-field-exchange-rfx.md)。  
  
##  <a name="edit"></a>CRecordset::Edit  
 允许对当前记录的更改。  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>备注  
 在您调用之后**编辑**，您可以通过直接重新设置其值更改的字段数据成员。 在操作完成时您随后调用[更新](#update)成员函数，以保存到数据源所做的更改。  
  
> [!NOTE]
>  如果已实现批量取行，则无法调用**编辑**。 这将导致失败的断言。 尽管类`CRecordset`不提供一种机制进行更新的数据大容量行，您可以通过使用 ODBC API 函数中编写您自己的函数**SQLSetPos**。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 **编辑**保存记录集的数据成员的值。 如果调用**编辑**，进行更改，然后调用**编辑**同样，将记录的值还原为它们早于第一个是**编辑**调用。  
  
 在某些情况下，您可能想要通过它，则为 Null （不包含任何数据） 进行更新的列。 若要这样做，请调用[SetFieldNull](#setfieldnull)参数为**TRUE**来标记该字段为 Null。 这也导致要更新的列。 如果您希望将字段来写入数据源，即使其值未更改，请调用[SetFieldDirty](#setfielddirty)参数为**TRUE**。 这样即使该字段具有值为 Null。  
  
 如果数据源支持事务，则可以使**编辑**调用事务的一部分。 请注意，应调用[CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans)之前调用**编辑**和之后打开记录集。 此外请注意，调用[CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)不能用于调用代替**更新**完成**编辑**操作。 有关事务的详细信息，请参阅类[CDatabase](../../mfc/reference/cdatabase-class.md)。  
  
 根据当前的锁定模式，所更新的记录可能被锁定**编辑**直到您调用**更新**或者滚动到另一个记录，则可能仅在被锁定或**编辑**调用。 您可以更改与锁定模式[SetLockingMode](#setlockingmode)。  
  
 如果滚动到一条新记录之前，先调用，则会还原以前的值的当前记录**更新**。 一个`CDBException`您调用将引发**编辑**不能更新的记录集或如果没有当前记录。  
  
 有关详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)和[记录集︰ 锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase #&20;](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]  
  
##  <a name="flushresultset"></a>CRecordset::FlushResultSet  
 如果有多个结果集，检索预定义查询 （存储过程） 的下一个结果集。  
  
```  
BOOL FlushResultSet();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果有多个结果集一个示例。否则为 0。  
  
### <a name="remarks"></a>备注  
 应调用`FlushResultSet`只有当您处于完全完成将光标放在当前结果集。 请注意，当您检索下一个结果集通过调用`FlushResultSet`，光标在该结果集上无效; 应调用[MoveNext](#movenext)之后调用的成员函数`FlushResultSet`。  
  
 如果预定义的查询使用输出参数或输入/输出参数，则必须调用`FlushResultSet`直到它返回`FALSE`（值 0），以获取这些参数值。  
  
 `FlushResultSet`调用 ODBC API 函数`SQLMoreResults`。 如果`SQLMoreResults`返回`SQL_ERROR`或`SQL_INVALID_HANDLE`，然后`FlushResultSet`将引发异常。 有关详细信息`SQLMoreResults`，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 你的存储的过程需要具有绑定字段，如果你想要调用`FlushResultSet`。  
  
### <a name="example"></a>示例  
 下面的代码假定`COutParamRecordset`是`CRecordset`-基于预定义查询的输入的参数和输出参数，并让多个结果集派生的对象。 请注意的结构[DoFieldExchange](#dofieldexchange)重写。  
  
 [!code-cpp[NVC_MFCDatabase #&21;](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDatabase #&22;](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]  
  
##  <a name="getbookmark"></a>CRecordset::GetBookmark  
 获取当前记录的书签值。  
  
```  
void GetBookmark(CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>参数  
 `varBookmark`  
 对引用[CDBVariant](../../mfc/reference/cdbvariant-class.md)对象，表示对当前记录的书签。  
  
### <a name="remarks"></a>备注  
 若要确定记录集上是否支持了书签，请调用[CanBookmark](#canbookmark)。 若要使书签可用，如果受支持，必须设置**CRecordset::useBookmarks**选项`dwOptions`参数[打开](#open)成员函数。  
  
> [!NOTE]
>  如果书签不受支持或不可用，则调用`GetBookmark`将导致引发异常。 只能向前的记录集不支持书签。  
  
 `GetBookmark`将当前记录到的书签的值分配`CDBVariant`对象。 若要在将移动到另一条记录后随时返回到该记录，请调用[SetBookmark](#setbookmark)与相应`CDBVariant`对象。  
  
> [!NOTE]
>  某些记录集在操作之后，书签可能不再有效。 例如，如果您调用`GetBookmark`跟**Requery**，您可能不能返回到该记录`SetBookmark`。 调用[CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)若要检查是否可以安全地调用`SetBookmark`。  
  
 有关书签和记录集导航的详细信息，请参阅文章[记录集︰ 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[记录集︰ 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
##  <a name="getdefaultconnect"></a>CRecordset::GetDefaultConnect  
 调用以获取默认连接字符串。  
  
```  
virtual CString GetDefaultConnect();
```  
  
### <a name="return-value"></a>返回值  
 一个`CString`，其中包含的默认连接字符串。  
  
### <a name="remarks"></a>备注  
 框架调用此成员函数以获取记录集所基于的数据源的默认连接字符串。 类向导通过识别您使用在 ClassWizard 来获取有关表和列信息相同的数据源，为你实现此函数。 您可能会发现它方便地依赖于开发您的应用程序时该默认连接。 但默认连接可能不适合于应用程序的用户。 如果是这种情况，应重新实现此函数中，放弃 ClassWizard 的版本。 有关连接字符串的详细信息，请参阅文章[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)。  
  
##  <a name="getdefaultsql"></a>CRecordset::GetDefaultSQL  
 调用以获取要执行的默认 SQL 字符串。  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>返回值  
 一个`CString`，其中包含默认的 SQL 语句。  
  
### <a name="remarks"></a>备注  
 框架调用此成员函数可获取该记录集所基于的默认 SQL 语句。 这可能是表名或 SQL**选择**语句。  
  
 间接通过声明与 ClassWizard，记录集类定义默认的 SQL 语句和类向导为您执行此任务。  
  
 如果您需要为自己使用的 SQL 语句字符串，调用`GetSQL`，表示将返回用来打开时选择记录集的记录的 SQL 语句。 您可以编辑您的类的重写中的默认 SQL 字符串`GetDefaultSQL`。 例如，可以指定对预定义的查询时使用的调用**调用**语句。 (请注意，但是，如果您编辑`GetDefaultSQL`，还需要修改`m_nFields`相匹配的数据源中的列数。)  
  
 有关详细信息，请参阅文章[记录集︰ 声明一个类用于表 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。  
  
> [!CAUTION]
>  表名称将为空，如果框架不能标识的表名，如果提供多个表名，或者如果**调用**无法解释语句。 请注意，当使用**调用**语句中，不能插入在大括号之间的空白和**调用**关键字，也不应将大括号之前或在之前的空白插入**选择**中的关键字**选择**语句。  
  
##  <a name="getfieldvalue"></a>CRecordset::GetFieldValue  
 检索当前记录中的字段数据。  
  
```  
void GetFieldValue(
    LPCTSTR lpszName,  
    CDBVariant& varValue,  
    short nFieldType = DEFAULT_FIELD_TYPE);

 
void GetFieldValue(
    short nIndex,  
    CDBVariant& varValue,  
    short nFieldType = DEFAULT_FIELD_TYPE);

 
void GetFieldValue(
    short nIndex,  
    CStringA& strValue);

 
void GetFieldValue(
    short nIndex,  
    CStringW& strValue);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 字段的名称。  
  
 *varValu*e  
 对引用[CDBVariant](../../mfc/reference/cdbvariant-class.md)将存储在字段的值的对象。  
  
 `nFieldType`  
 ODBC C 数据类型的字段。 使用默认值**DEFAULT_FIELD_TYPE**，强制`GetFieldValue`根据下表确定从 SQL 数据类型的 C 数据类型。 否则，您可以在其中指定的数据直接键入或选择兼容的数据类型;例如，可以存储任何数据类型读入**SQL_C_CHAR**。  
  
|C 数据类型|SQL 数据类型|  
|-----------------|-------------------|  
|**SQL_C_BIT**|**SQL_BIT**|  
|**为 SQL_C_UTINYINT**|**SQL_TINYINT**|  
|**SQL_C_SSHORT**|**SQL_SMALLINT**|  
|**SQL_C_SLONG**|**SQL_INTEGER**|  
|**SQL_C_FLOAT**|**SQL_REAL**|  
|**SQL_C_DOUBLE**|**SQL_FLOATSQL_DOUBLE**|  
|**SQL_C_TIMESTAMP**|**SQL_DATESQL_TIMESQL_TIMESTAMP**|  
|**SQL_C_CHAR**|**SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR**|  
|**SQL_C_BINARY**|**SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY**|  
  
 有关 ODBC 数据类型的详细信息，请参阅主题"SQL 数据类型"和"C 数据类型"中的附录 D [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `nIndex`  
 字段的从零开始的索引。  
  
 `strValue`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，它将存储在字段的值转换为文本，而不考虑该字段的数据类型。  
  
### <a name="remarks"></a>备注  
 您可以查找字段，按名称或索引。 您可以存储字段值中任意一种`CDBVariant`对象或`CString`对象。  
  
 如果已实现批量取行，当前记录始终位于行集中的第一条记录。 若要使用`GetFieldValue`上中给定的行集的记录，您必须首先调用[SetRowsetCursorPosition](#setrowsetcursorposition)成员函数以将光标移到所需的行，该行集内。 然后，调用`GetFieldValue`为该行。 若要实现批量取行，您必须指定`CRecordset::useMultiRowFetch`选项`dwOptions`中的参数[打开](#open)成员函数。  
  
 您可以使用`GetFieldValue`若要在运行的时而不是以静态方式将它们绑定在设计时动态获取字段。 例如，如果您已声明直接从记录集对象`CRecordset`，必须使用`GetFieldValue`检索字段数据; 记录字段交换 (RFX) 或批量记录字段交换 (Bulk RFX) 未实现。  
  
> [!NOTE]
>  如果您声明一个记录集对象而无需派生自`CRecordset`，而没有加载 ODBC 游标库。 游标库要求记录集具有至少一个绑定的列;但是，当使用`CRecordset`直接，没有绑定任何列。 成员函数[CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex)和[CDatabase::Open](../../mfc/reference/cdatabase-class.md#open)控制是否将加载游标库。  
  
 `GetFieldValue`调用 ODBC API 函数**SQLGetData**。 如果您的驱动程序输出值**SQL_NO_TOTAL**字段值的实际长度为`GetFieldValue`将引发异常。 有关详细信息**SQLGetData**，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的示例代码演示如何调用`GetFieldValue`直接从记录集对象声明为`CRecordset`。  
  
 [!code-cpp[NVC_MFCDatabase 第&23;](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]  
  
> [!NOTE]
>  与 DAO 类不同`CDaoRecordset`，`CRecordset`没有`SetFieldValue`成员函数。 如果您创建直接从一个对象`CRecordset`，它是有效地只读的。  
  
 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="getodbcfieldcount"></a>CRecordset::GetODBCFieldCount  
 检索的记录集对象中的字段的总数。  
  
```  
short GetODBCFieldCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 在记录集中的字段数。  
  
### <a name="remarks"></a>备注  
 有关创建记录集的详细信息，请参阅文章[记录集︰ 创建和关闭记录集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。  
  
##  <a name="getodbcfieldinfo"></a>CRecordset::GetODBCFieldInfo  
 获取有关在记录集中的字段信息。  
  
```  
void GetODBCFieldInfo(
    LPCTSTR lpszName,  
    CODBCFieldInfo& fieldinfo);

 
void GetODBCFieldInfo(
    short nIndex,  
    CODBCFieldInfo& fieldinfo);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 字段的名称。  
  
 `fieldinfo`  
 对引用`CODBCFieldInfo`结构。  
  
 `nIndex`  
 字段的从零开始的索引。  
  
### <a name="remarks"></a>备注  
 该函数的一个版本允许您按名称查找字段。 另一个版本中，可以按索引查找字段。  
  
 有关返回的信息的说明，请参阅[CODBCFieldInfo](../../mfc/reference/codbcfieldinfo-structure.md)结构。  
  
 有关创建记录集的详细信息，请参阅文章[记录集︰ 创建和关闭记录集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。  
  
##  <a name="getrecordcount"></a>CRecordset::GetRecordCount  
 确定记录集的大小。  
  
```  
long GetRecordCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 记录集; 中的记录数记录集不包含任何记录; 如果为 0或-1，如果不确定的记录数。  
  
### <a name="remarks"></a>备注  
  
> [!CAUTION]
>  保持为"高水位线，"最高编号记录尚可视为用户遍历记录的记录数。 用户已超出最后一条记录移动后，只有知道总记录数。 出于性能原因，将更新的计数不在调用时`MoveLast`。 若要记录计数自己，调用`MoveNext`重复直至`IsEOF`返回非零值。 添加一条记录通过**CRecordset:AddNew**和**更新**增加的计数; 删除通过记录`CRecordset::Delete`减少计数。  
  
##  <a name="getrowsetsize"></a>CRecordset::GetRowsetSize  
 获取你想要在给定提取过程中检索的行数的当前设置。  
  
```  
DWORD GetRowsetSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 要在给定提取过程中检索的行数。  
  
### <a name="remarks"></a>备注  
 如果使用批量取行，打开记录集时的默认行集大小为 25;否则，它为 1。  
  
 若要实现批量取行，您必须指定`CRecordset::useMultiRowFetch`选项`dwOptions`参数[打开](#open)成员函数。 若要更改的行集大小的设置，请调用[SetRowsetSize](#setrowsetsize)。  
  
 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="getrowsfetched"></a>CRecordset::GetRowsFetched  
 确定后提取实际检索多少条记录。  
  
```  
DWORD GetRowsFetched() const;  
```  
  
### <a name="return-value"></a>返回值  
 给定的获取之后从数据源检索的行数。  
  
### <a name="remarks"></a>备注  
 如果已实现批量取行，这非常有用。 行集大小通常指示将从读取; 检索行的数目但是，在记录集中的行总数也会影响将行集中检索行的数目。 例如，如果您的记录集中有 10 条记录，行集大小设置为 4，然后遍历记录集通过调用`MoveNext`会导致具有仅 2 条记录的最后一个行集。  
  
 若要实现批量取行，您必须指定`CRecordset::useMultiRowFetch`选项`dwOptions`参数[打开](#open)成员函数。 若要指定行集大小，请调用[SetRowsetSize](#setrowsetsize)。  
  
 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase #&24;](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]  
  
##  <a name="getrowstatus"></a>CRecordset::GetRowStatus  
 获取当前行集中的行的状态。  
  
```  
WORD GetRowStatus(WORD wRow) const;  
```  
  
### <a name="parameters"></a>参数  
 `wRow`  
 基于&1; 的行位置的当前行集中。 此值可介于 1 到行集大小。  
  
### <a name="return-value"></a>返回值  
 行状态值。 有关详细信息，请参阅“备注”。  
  
### <a name="remarks"></a>备注  
 `GetRowStatus`返回一个值，指示状态设置为行中的任一任何更改，自上次检索从数据源，或返回任何行对应于`wRow`提取了。 下表列出可能的返回值。  
  
|状态值|描述|  
|------------------|-----------------|  
|`SQL_ROW_SUCCESS`|该行是不变。|  
|`SQL_ROW_UPDATED`|更新了该行。|  
|`SQL_ROW_DELETED`|行已被删除。|  
|`SQL_ROW_ADDED`|已添加的行。|  
|`SQL_ROW_ERROR`|该行是检索由于出现错误。|  
|`SQL_ROW_NOROW`|对应于没有行`wRow`。|  
  
 有关详细信息，请参阅 ODBC API 函数**SQLExtendedFetch**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getstatus"></a>CRecordset::GetStatus  
 确定记录集并是否曾出现最后一条记录中的当前记录的索引。  
  
```  
void GetStatus(CRecordsetStatus& rStatus) const;  
```  
  
### <a name="parameters"></a>参数  
 `rStatus`  
 对引用**CRecordsetStatus**对象。 有关详细信息，请参阅备注部分。  
  
### <a name="remarks"></a>备注  
 `CRecordset`尝试跟踪索引，但在某些情况下这不可能。 请参阅[GetRecordCount](#getrecordcount)的说明。  
  
 **CRecordsetStatus**结构具有以下形式︰  
  
 `struct CRecordsetStatus`  
  
 `{`  
  
 `long m_lCurrentRecord;`  
  
 `BOOL m_bRecordCountFinal;`  
  
 `};`  
  
 两个成员**CRecordsetStatus**具有以下含义︰  
  
- **m_lCurrentRecord**如果已知包含在记录集中，当前记录的从零开始的索引。 如果无法确定索引，此成员将包含**AFX_CURRENT_RECORD_UNDEFINED** (-2)。 如果`IsBOF`是**TRUE** （空记录集或尝试在第一条记录之前向下滚动），然后**m_lCurrentRecord**设置为**AFX_CURRENT_RECORD_BOF** (-1)。 如果在第一条记录，然后它设置为 0，第二个记录 1，依此类推。  
  
- **m_bRecordCountFinal** Nonzero 如果已确定记录集内的记录总数。 通常这必须通过从记录集的开头，并调用完成`MoveNext`直到`IsEOF`返回非零值。 如果此成员为零，该记录进行计数以返回`GetRecordCount`，如果不为 –&1;，仅记录的"高水位线"计数。  
  
##  <a name="getsql"></a>CRecordset::GetSQL  
 调用此成员函数可获取用于选择记录集的记录时已打开的 SQL 语句。  
  
```  
const CString& GetSQL() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**const**引用`CString`，其中包含 SQL 语句。  
  
### <a name="remarks"></a>备注  
 这通常是一个 SQL**选择**语句。 返回的字符串`GetSQL`是只读的。  
  
 返回的字符串`GetSQL`通常不同于您可能已传递到中的记录集的任何字符串`lpszSQL`参数**打开**成员函数。 这是因为该记录集构造一个完整的 SQL 语句根据传递给**打开**，与类向导，您可以指定在指定的内容**m_strFilter**和`m_strSort`数据成员，并且你可能已指定任何参数。 有关记录集如何构造该 SQL 语句，有关详细信息，请参阅文章[记录集︰ 如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。  
  
> [!NOTE]
>  只有在调用后调用此成员函数[打开](#open)。  
  
##  <a name="gettablename"></a>CRecordset::GetTableName  
 获取记录集的查询所基于的 SQL 表的名称。  
  
```  
const CString& GetTableName() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**const**引用`CString`包含表的名称，如果记录集是根据一个表; 否则为空字符串。  
  
### <a name="remarks"></a>备注  
 `GetTableName`才有效，如果该记录集基于一个表，而不是联接的多个表或预定义的查询 （存储过程）。 该名称是只读的。  
  
> [!NOTE]
>  只有在调用后调用此成员函数[打开](#open)。  
  
##  <a name="isbof"></a>CRecordset::IsBOF  
 返回记录集已放在第一条记录之前，非零值。 没有当前记录。  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果该记录集不包含任何记录，或者具有在第一条记录; 之前向后滚动，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 从记录滚动到记录以了解是否仔细之前记录集的第一个记录之前，请调用此成员函数。 您还可以使用`IsBOF`连同`IsEOF`来确定记录集是否包含任何记录，或为空。 立即调用后**打开**，如果该记录集不包含任何记录`IsBOF`返回非零值。第一条记录都有至少一个记录的记录集打开时，是当前记录和`IsBOF`，则返回 0。  
  
 如果第一条记录是当前记录，并且调用`MovePrev`，`IsBOF`随后返回非零值。 如果`IsBOF`返回非零，并且您调用`MovePrev`，就会出错。 如果`IsBOF`返回非零值时，当前记录是未定义的并需要当前记录的任何操作将导致错误。  
  
### <a name="example"></a>示例  
 此示例使用`IsBOF`和`IsEOF`以检测代码将滚动到两个方向中的记录集的记录集限制。  
  
 [!code-cpp[NVC_MFCDatabase #&25;](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]  
  
##  <a name="isdeleted"></a>CRecordset::IsDeleted  
 确定当前记录是否已被删除。  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>返回值  
 记录集放在已删除的记录; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果您滚动到一条记录和`IsDeleted`返回**TRUE** （非零），则你必须滚动到另一条记录之前可以执行记录集的任何其他操作。  
  
 结果`IsDeleted`取决于许多因素，如您的记录集类型，您的记录集是否可以更新，无论您是否指定**CRecordset::skipDeletedRecords**选项何时是否你驱动程序的包删除记录、 打开记录集，以及是否有多个用户。  
  
 有关详细信息**CRecordset::skipDeletedRecords**和驱动程序装箱，请参阅[打开](#open)成员函数。  
  
> [!NOTE]
>  如果已实现批量取行，则不应调用`IsDeleted`。 而应调用[GetRowStatus](#getrowstatus)成员函数。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="iseof"></a>CRecordset::IsEOF  
 返回非零，如果在最后一条记录后定位完记录集。 没有当前记录。  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果该记录集不包含任何记录，或者已超出最后一条记录; 滚动否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此成员函数，如从记录滚动到记录以了解是否您已超出最后一个记录集的记录。 您还可以使用`IsEOF`来确定记录集是否包含任何记录，或为空。 立即调用后**打开**，如果该记录集不包含任何记录`IsEOF`返回非零值。 第一条记录都有至少一个记录的记录集打开时，是当前记录和`IsEOF`，则返回 0。  
  
 如果最后一条记录时的当前记录调用`MoveNext`，`IsEOF`随后返回非零值。 如果`IsEOF`返回非零，并且您调用`MoveNext`，就会出错。 如果`IsEOF`返回非零值时，当前记录是未定义的并需要当前记录的任何操作将导致错误。  
  
### <a name="example"></a>示例  
 请参阅示例[IsBOF](#isbof)。  
  
##  <a name="isfielddirty"></a>CRecordset::IsFieldDirty  
 确定指定的字段数据成员以来已被更改[编辑](#edit)或[AddNew](#addnew)调用。  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 字段数据成员你想要检查，其状态的指针或**NULL**以确定是否已更新的任何字段。  
  
### <a name="return-value"></a>返回值  
 如果指定的字段数据成员已更改后调用，则为非`AddNew`或**编辑**; 否则为 0。  
  
### <a name="remarks"></a>备注  
 所有已更新字段数据成员中的数据将传输到该记录在数据源上的当前记录更新通过调用时[更新](#update)成员函数`CRecordset`(在调用**编辑**或`AddNew`)。  
  
> [!NOTE]
>  此成员函数不是适用于正在使用批量取行的记录集。 如果已实现批量取行，然后`IsFieldDirty`将始终返回**FALSE** ，将导致失败的断言。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 调用`IsFieldDirty`将重置以前调用的效果[SetFieldDirty](#setfielddirty)由于重新计算该字段的更新状态。 在`AddNew`的情况下，如果当前的字段值不同于伪 null 值，将字段状态设置已更新。 在**编辑**种情况下，如果字段值与缓存的值，则字段状态设置已更新。  
  
 `IsFieldDirty`通过实现[DoFieldExchange](#dofieldexchange)。  
  
 已更新标志的详细信息，请参阅文章[记录集︰ 如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。  
  
##  <a name="isfieldnull"></a>CRecordset::IsFieldNull  
 返回为当前记录中指定的字段为 Null 时，非零值 （不具有任何值）。  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 字段数据成员你想要检查，其状态的指针或**NULL**来确定是否其中任何一个字段将为 Null。  
  
### <a name="return-value"></a>返回值  
 如果指定的字段数据成员标记为 Null; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此成员函数确定记录集的指定的字段数据成员是否已标记为 Null。 (在数据库术语中，Null 意味着您"没有值"，并且不与相同**NULL** c + + 中。)如果字段数据成员标记为 Null，它被解释为当前记录没有值的列。  
  
> [!NOTE]
>  此成员函数不是适用于正在使用批量取行的记录集。 如果已实现批量取行，然后`IsFieldNull`将始终返回**FALSE** ，将导致失败的断言。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 `IsFieldNull`通过实现[DoFieldExchange](#dofieldexchange)。  
  
##  <a name="isfieldnullable"></a>CRecordset::IsFieldNullable  
 返回非零，如果为当前记录中指定的字段可以设置为 Null （具有任何值）。  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 字段数据成员你想要检查，其状态的指针或**NULL**以确定其中任何一个字段可以为 Null 值将设置。  
  
### <a name="remarks"></a>备注  
 调用以确定是否可为"null"指定的字段数据成员 （可以是设置为一个 Null 值; 如果该成员函数C + + **NULL**不同时，则为 Null 时，这在数据库术语中，意味着"having 没有值")。  
  
> [!NOTE]
>  如果已实现批量取行，则无法调用`IsFieldNullable`。 而应调用[GetODBCFieldInfo](#getodbcfieldinfo)成员函数以确定是否可以将字段设置为 Null 值。 请注意，始终可以调用`GetODBCFieldInfo`，而不考虑批量取行实现。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 不能为 Null 的字段必须具有值。 添加或更新时，如果尝试将此类字段设置为 Null，在添加或更新记录时，拒绝数据源和[更新](#update)将引发异常。 当您调用，则会发生异常**更新**、 不是在您调用时[SetFieldNull](#setfieldnull)。  
  
 使用**NULL**为该函数的第一个参数将该函数仅适用于**outputColumn**字段，不**param**字段。 例如，调用  
  
 [!code-cpp[NVC_MFCDatabase #&26;](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 将仅设置**outputColumn**字段设置为**NULL**;**param**字段不会受到影响。  
  
 从事**param**字段中，你必须提供个人的实际地址**param**你想要使用，如︰  
  
 [!code-cpp[NVC_MFCDatabase #&27;](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 这意味着您不能设置所有**param**字段设置为**NULL**，如可以与**outputColumn**字段。  
  
 `IsFieldNullable`通过实现[DoFieldExchange](#dofieldexchange)。  
  
##  <a name="isopen"></a>CRecordset::IsOpen  
 确定记录集是否已打开。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果非零记录集对象的[打开](#open)或[Requery](#requery)以前调用成员函数，但尚未关闭记录集; 否则为 0。  
  
##  <a name="m_hstmt"></a>CRecordset::m_hstmt  
 包含 ODBC 语句数据结构的类型的句柄**HSTMT**，则会使用该记录关联。  
  
### <a name="remarks"></a>备注  
 与关联到 ODBC 数据源的每个查询**HSTMT**。  
  
> [!CAUTION]
>  请不要使用**m_hstmt**之前[打开](#open)已调用。  
  
 通常不需要访问**HSTMT**直接，但您可能需要它，直接执行 SQL 语句。 `ExecuteSQL`类的成员函数`CDatabase`举例说明使用**m_hstmt**。  
  
##  <a name="m_nfields"></a>CRecordset::m_nFields  
 包含记录集类中; 中的字段数据成员的数目即，选定数据源中的记录集的列数。  
  
### <a name="remarks"></a>备注  
 记录集类的构造函数必须初始化`m_nFields`与正确的号码。 如果尚未实现批量取行，ClassWizard 将写入此初始化时，当用于声明记录集类。 您还可以编写它手动。  
  
 框架将使用此数字来管理的字段数据成员与数据源上的当前记录的相应列之间的交互。  
  
> [!CAUTION]
>  此数字必须对应于"输出列"中注册数`DoFieldExchange`或`DoBulkFieldExchange`调用后[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)与参数**CFieldExchange::outputColumn**。  
  
 您可以在文章中所述动态绑定列"记录集︰ 动态绑定数据列。" 如果您这样做，则必须增加中的计数`m_nFields`以反映 RFX 或批量 RFX 函数的调用您`DoFieldExchange`或`DoBulkFieldExchange`动态绑定列的成员函数。  
  
 有关详细信息，请参阅文章[记录集︰ 动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)和[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>示例  
 请参阅文章[记录字段交换︰ 使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。  
  
##  <a name="m_nparams"></a>CRecordset::m_nParams  
 包含记录集类中; 中的参数数据成员的数目也就是说，参数的数目与记录集的查询一起传递。  
  
### <a name="remarks"></a>备注  
 如果您的记录集类具有任何参数数据成员，必须初始化类的构造函数`m_nParams`与正确的号码。 值`m_nParams`默认值为 0。 如果添加参数数据成员 （这必须执行手动操作） 必须在类构造函数，以反映参数的数目也手动添加初始化 (其范围必须至少与的数目一样大 ' 中的占位符您**m_strFilter**或`m_strSort`字符串)。  
  
 当参数化记录集的查询时，框架将使用此数字。  
  
> [!CAUTION]
>  此数字必须对应于"params"中注册的数`DoFieldExchange`或`DoBulkFieldExchange`调用后[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)参数值为**CFieldExchange::inputParam**， **CFieldExchange::param**， **CFieldExchange::outputParam**，或**CFieldExchange::inoutParam**。  
  
### <a name="example"></a>示例  
  请参阅文章[记录集︰ 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)和[记录字段交换︰ 使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。  
  
##  <a name="m_pdatabase"></a>CRecordset::m_pDatabase  
 包含一个指向`CDatabase`通过该记录集连接到数据源对象。  
  
### <a name="remarks"></a>备注  
 两种方式设置此变量。 通常情况下，将指针传递到已连接`CDatabase`对象构造记录集对象时。 如果您通过**NULL**相反，`CRecordset`创建`CDatabase`为您的对象并将其连接。 在任一情况下，`CRecordset`将指针存储在此变量。  
  
 通常不直接需要使用存储在指针**m_pDatabase**。 如果您编写您自己的扩展`CRecordset`，但是，您可能需要使用该指针。 例如，您可能需要将指针仅当您引发自己`CDBException`s。 您可能需要它，如果您需要执行一些使用同一个操作或者`CDatabase`对象，例如，运行设置超时的事务或调用`ExecuteSQL`类的成员函数`CDatabase`直接执行 SQL 语句。  
  
##  <a name="m_strfilter"></a>CRecordset::m_strFilter  
 在构造记录集对象之后但在调用之前其**打开**成员函数，请使用此数据成员来存储`CString`包含 SQL**其中**子句。  
  
### <a name="remarks"></a>备注  
 记录集使用此字符串将约束 （或筛选器） 期间它选择的记录**打开**或**Requery**调用。 这可用于选择记录，例如"加利福尼亚州基于所有销售人员"的一个子集 ("状态 = CA")。 ODBC SQL 语法**其中**子句  
  
 `WHERE search-condition`  
  
 请注意，不包括**其中**在字符串中的关键字。 框架提供了它。  
  
 您可以将筛选器字符串参数通过将在该类中的占位符为每个占位符，声明您的类中的参数数据成员并将参数传递给记录集在运行时。 这样就可以在运行时构造筛选器。 有关详细信息，请参阅文章[记录集︰ 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
 有关 SQL**其中**子句，请参阅文章[SQL](../../data/odbc/sql.md)。 有关选择和筛选记录的详细信息，请参阅文章[记录集︰ 筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase #&30;](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]  
  
##  <a name="m_strsort"></a>CRecordset::m_strSort  
 在构造记录集对象之后但在调用之前其**打开**成员函数，请使用此数据成员来存储`CString`包含 SQL **ORDER BY**子句。  
  
### <a name="remarks"></a>备注  
 记录集使用此字符串来对它在选择这些记录排序**打开**或**Requery**调用。 此功能可用于对一个或多个列上的记录集进行排序。 ODBC SQL 语法**ORDER BY**子句  
  
 `ORDER BY sort-specification [, sort-specification]...`  
  
 其中排序规范是一个整数或列名称。 此外可以通过将"ASC"或"DESC"追加到排序字符串中的列列表中指定升序或降序顺序 （默认情况下，顺序为升序）。 所选的记录排在前面的第一列列出，然后依据的第二个，依次类推。 例如，您可能订购最后一个名称，然后按名字的"客户"记录的集。 您可以列出的列数取决于数据源。 有关详细信息，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 请注意，不包括**ORDER BY**在字符串中的关键字。 框架提供了它。  
  
 有关 SQL 子句的详细信息，请参阅文章[SQL](../../data/odbc/sql.md)。 有关对记录进行排序的详细信息，请参阅文章[记录集︰ 排序记录 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase #&31;](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]  
  
##  <a name="move"></a>CRecordset::Move  
 将当前记录集中的记录，向前或向后指针。  
  
```  
virtual void Move(
    long nRows,  
    WORD wFetchType = SQL_FETCH_RELATIVE);
```  
  
### <a name="parameters"></a>参数  
 `nRows`  
 要向前或向后移动的行数。 正值表示向前移动，移向记录集的结尾。 值为负开始向后移动。  
  
 `wFetchType`  
 确定行集，**移动**将提取。 有关详细信息，请参阅“备注”。  
  
### <a name="remarks"></a>备注  
 如果传递的值为 0， `nRows`，**移动**刷新当前记录;**移动**将结束所有当前`AddNew`或**编辑**模式下，将还原之前的当前记录的值和`AddNew`或**编辑**调用。  
  
> [!NOTE]
>  当遍历一个记录集时，则不能跳过已删除的记录。 请参阅[CRecordset::IsDeleted](#isdeleted)有关详细信息。 当您打开`CRecordset`与**skipDeletedRecords**选项集，**移动**断言如果`nRows`参数为 0。 此行为可防止其他使用相同的数据的客户端应用程序被删除的行的刷新。 请参阅`dwOption`中的参数[打开](#open)有关的说明**skipDeletedRecords**。  
  
 **移动**按行集重新定位该记录集。 基于值的`nRows`和`wFetchType`，**移动**提取适当的行集，并将第一条记录中的行集的当前记录。 如果你尚未实现批量取行，然后行集大小始终为 1。 在提取行集时**移动**直接调用[CheckRowsetError](#checkrowseterror)成员函数来处理所导致的提取任何错误。  
  
 根据您传递的值**移动**等效于其他`CRecordset`成员函数。 具体而言，值`wFetchType`就说明更直观的成员函数，并且通常用于移动当前记录的首选的方法。  
  
 下表列出的可能值`wFetchType`，行集，**移动**将提取基于`wFetchType`和`nRows`，并对应于任何等效成员函数`wFetchType`。  
  
|wFetchType|提取行集|等效成员函数|  
|----------------|--------------------|--------------------------------|  
|`SQL_FETCH_RELATIVE`（默认值）|行集起始`nRows`到当前行集中的第一行的行。||  
|`SQL_FETCH_NEXT`|下一个行集;`nRows`将被忽略。|[MoveNext](#movenext)|  
|`SQL_FETCH_PRIOR`|上一个行集;`nRows`将被忽略。|[MovePrev](#moveprev)|  
|`SQL_FETCH_FIRST`|在记录集中; 第一个行集`nRows`将被忽略。|[MoveFirst](#movefirst)|  
|`SQL_FETCH_LAST`|在记录集中; 最后一个完整的行集`nRows`将被忽略。|[MoveLast](#movelast)|  
|`SQL_FETCH_ABSOLUTE`|如果`nRows`1> 0，开始的行集`nRows`从开始处的记录集的行。 如果`nRows` < 0,="" the="" rowset="" starting=""> `nRows`从记录集的结尾的行。 如果`nRows`= 0，则返回一个开头的文件 (BOF) 条件。|[SetAbsolutePosition](#setabsoluteposition)|  
|`SQL_FETCH_BOOKMARK`|从其书签值对应于行开始的行集`nRows`。|[SetBookmark](#setbookmark)|  
  
> [!NOTE]
>  对于只进记录集**移动**才具有值的有效`SQL_FETCH_NEXT`为`wFetchType`。  
  
> [!CAUTION]
>  调用**移动**记录集含有没有记录的情况下将引发异常。 若要确定记录集是否具有任何记录，请调用[IsBOF](#isbof)和[IsEOF](#iseof)。  
  
> [!NOTE]
>  如果您使用滚动条滚动过去的开头或结尾的记录集 (`IsBOF`或`IsEOF`返回非零值)，则调用**移动**函数将可能引发`CDBException`。 例如，如果`IsEOF`返回非零值和`IsBOF`不存在，然后`MoveNext`将引发异常，但`MovePrev`将不会。  
  
> [!NOTE]
>  如果调用**移动**时的当前记录更新或添加，更新都将丢失而不发出警告。  
  
 有关记录集导航的详细信息，请参阅文章[记录集︰ 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[记录集︰ 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 有关相关信息，请参阅 ODBC API 函数**SQLExtendedFetch**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase #&28;](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]  
  
##  <a name="movefirst"></a>CRecordset::MoveFirst  
 使第一条记录中第一个行集的当前记录。  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>备注  
 无论是否批量取行实现了，这将始终为记录集中的第一个记录。  
  
 无需调用**MoveFirst**立即打开记录集之后。 在那时，第一条记录 （如果有） 将自动当前记录。  
  
> [!NOTE]
>  此成员函数无效，不能用于仅向前的记录集。  
  
> [!NOTE]
>  当遍历一个记录集时，则不能跳过已删除的记录。 请参阅[IsDeleted](#isdeleted)成员函数的详细信息。  
  
> [!CAUTION]
>  调用的任何**移动**函数将引发异常，如果记录集不含有任何记录。 若要确定记录集是否具有任何记录，请调用`IsBOF`和`IsEOF`。  
  
> [!NOTE]
>  如果在调用的任何**移动**函数时的当前记录更新或添加，更新都将丢失而不发出警告。  
  
 有关记录集导航的详细信息，请参阅文章[记录集︰ 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[记录集︰ 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>示例  
  请参阅示例[IsBOF](#isbof)。  
  
##  <a name="movelast"></a>CRecordset::MoveLast  
 使第一条记录中的最后一个完整行集的当前记录。  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>备注  
 如果你尚未实现批量取行，您的记录集具有的行集大小为 1，因此`MoveLast`只需移动到最后一个记录中的记录集中。  
  
> [!NOTE]
>  此成员函数无效，不能用于仅向前的记录集。  
  
> [!NOTE]
>  当遍历一个记录集时，则不能跳过已删除的记录。 请参阅[IsDeleted](#isdeleted)成员函数的详细信息。  
  
> [!CAUTION]
>  调用的任何**移动**函数将引发异常，如果记录集不含有任何记录。 若要确定记录集是否具有任何记录，请调用`IsBOF`和`IsEOF`。  
  
> [!NOTE]
>  如果在调用的任何**移动**函数时的当前记录更新或添加，更新都将丢失而不发出警告。  
  
 有关记录集导航的详细信息，请参阅文章[记录集︰ 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[记录集︰ 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>示例  
  请参阅示例[IsBOF](#isbof)。  
  
##  <a name="movenext"></a>CRecordset::MoveNext  
 使第一条记录中的下一个行集的当前记录。  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>备注  
 如果你尚未实现批量取行，您的记录集具有的行集大小为 1，因此`MoveNext`只需将其移到下一条记录。  
  
> [!NOTE]
>  当遍历一个记录集时，则不能跳过已删除的记录。 请参阅[IsDeleted](#isdeleted)成员函数的详细信息。  
  
> [!CAUTION]
>  调用的任何**移动**函数将引发异常，如果记录集不含有任何记录。 若要确定记录集是否具有任何记录，请调用`IsBOF`和`IsEOF`。  
  
> [!NOTE]
>  此外建议您调用`IsEOF`之前调用`MoveNext`。 例如，如果您使用滚动条滚动该记录集的末尾，`IsEOF`将返回非零值; 的后续调用`MoveNext`会引发异常。  
  
> [!NOTE]
>  如果在调用的任何**移动**函数时的当前记录更新或添加，更新都将丢失而不发出警告。  
  
 有关记录集导航的详细信息，请参阅文章[记录集︰ 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[记录集︰ 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>示例  
  请参阅示例[IsBOF](#isbof)。  
  
##  <a name="moveprev"></a>CRecordset::MovePrev  
 使第一条记录中的上一个行集的当前记录。  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>备注  
 如果你尚未实现批量取行，您的记录集具有的行集大小为 1，因此`MovePrev`只需将其移到上一条记录。  
  
> [!NOTE]
>  此成员函数无效，不能用于仅向前的记录集。  
  
> [!NOTE]
>  当遍历一个记录集时，则不能跳过已删除的记录。 请参阅[IsDeleted](#isdeleted)成员函数的详细信息。  
  
> [!CAUTION]
>  调用的任何**移动**函数将引发异常，如果记录集不含有任何记录。 若要确定记录集是否具有任何记录，请调用`IsBOF`和`IsEOF`。  
  
> [!NOTE]
>  此外建议您调用`IsBOF`之前调用`MovePrev`。 例如，如果滚记录集，开头`IsBOF`将返回非零值; 的后续调用`MovePrev`会引发异常。  
  
> [!NOTE]
>  如果在调用的任何**移动**函数时的当前记录更新或添加，更新都将丢失而不发出警告。  
  
 有关记录集导航的详细信息，请参阅文章[记录集︰ 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[记录集︰ 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>示例  
  请参阅示例[IsBOF](#isbof)。  
  
##  <a name="onsetoptions"></a>CRecordset::OnSetOptions  
 若要设置 （用于所选内容上） 的选项为调用指定的 ODBC 语句。  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>参数  
 `hstmt`  
 **HSTMT** ODBC 语句的选项，则设置。  
  
### <a name="remarks"></a>备注  
 调用`OnSetOptions`设置为指定的 ODBC 语句 （用于所选内容上） 的选项。 框架调用此成员函数可设置为记录集的初始选项。 `OnSetOptions`确定数据源的支持可滚动游标和游标并发，并相应地设置记录集的选项。 (而`OnSetOptions`用于选择操作，`OnSetUpdateOptions`用于更新操作。)  
  
 重写`OnSetOptions`来设置特定于驱动程序或数据源选项。 例如，如果您的数据源打开要执行的独占访问权的支持，您可能会替代`OnSetOptions`以利用该功能。  
  
 有关游标的详细信息，请参阅文章[ODBC](../../data/odbc/odbc-basics.md)。  
  
##  <a name="onsetupdateoptions"></a>CRecordset::OnSetUpdateOptions  
 调用以设置指定的 ODBC 语句 （update 上使用） 的选项。  
  
```  
virtual void OnSetUpdateOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>参数  
 `hstmt`  
 **HSTMT** ODBC 语句的选项，则设置。  
  
### <a name="remarks"></a>备注  
 调用`OnSetUpdateOptions`设置为指定的 ODBC 语句 （用于更新上） 的选项。 创建 HSTMT 更新记录集中的记录后，框架将调用此成员函数。 (而`OnSetOptions`用于选择操作，`OnSetUpdateOptions`用于更新操作。)`OnSetUpdateOptions`确定数据源的支持可滚动游标和游标并发，并相应地设置记录集的选项。  
  
 重写`OnSetUpdateOptions`设置 ODBC 语句的选项，然后该语句用于访问数据库。  
  
 有关游标的详细信息，请参阅文章[ODBC](../../data/odbc/odbc-basics.md)。  
  
##  <a name="open"></a>CRecordset::Open  
 通过检索表或执行查询来表示该记录集打开记录集。  
  
```  
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,  
    LPCTSTR lpszSQL = NULL,  
    DWORD dwOptions = none);
```  
  
### <a name="parameters"></a>参数  
 `nOpenType`  
 接受默认值**AFX_DB_USE_DEFAULT_TYPE**，或使用下列任一值，从**枚举 OpenType**:  
  
- **CRecordset::dynaset**具有双向滚动的记录集。 已打开记录集，但都可以看到 fetch 操作后的数据值的其他用户所做的更改时确定的成员身份和顺序的记录。 动态集实参也称为键集驱动的记录集。  
  
- **CRecordset::snapshot**具有双向滚动的静态记录集。 打开记录集; 时确定的成员身份和顺序的记录提取记录时确定的数据值。 关闭然后再重新打开记录集之前，将不可见的其他用户所做的更改。  
  
- **CRecordset::dynamic**具有双向滚动的记录集。 为由其他用户对成员身份、 排序和数据值所做的更改都可见后提取操作。 请注意，很多 ODBC 驱动程序不支持这种类型的记录集。  
  
- **CRecordset::forwardOnly**的只读的记录集包含仅向前滚动。  
  
     有关`CRecordset`，默认值是**CRecordset::snapshot**。 默认值机制允许这两个 ODBC 与之交互的 Visual c + + 向导`CRecordset`和 DAO `CDaoRecordset`，具有不同的默认值。  
  
 有关这些记录集类型的详细信息，请参阅文章[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)。 相关信息，请参阅文章"使用块游标和可滚动游标"中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
> [!CAUTION]
>  如果不支持所请求的类型，该框架将引发异常。  
  
 `lpszSQL`  
 比字符串指针，其中包含以下项之一︰  
  
-   一个**NULL**指针。  
  
-   表的名称。  
  
-   SQL**选择**语句 (并且可选择带有 SQL**其中**或**ORDER BY**子句)。  
  
-   一个**调用**语句并指定预定义查询 （存储过程） 的名称。 请注意，您不会插入在大括号之间的空白和**调用**关键字。  
  
 有关此字符串的详细信息，请参阅表和类向导的备注中的角色的讨论。  
  
> [!NOTE]
>  在结果集中列的顺序必须匹配 RFX 的顺序，否则 Bulk RFX 函数调用中您[DoFieldExchange](#dofieldexchange)或[DoBulkFieldExchange](#dobulkfieldexchange)函数重写。  
  
 `dwOptions`  
 位掩码，可以指定下面列出的值的组合。 其中一些是相互排斥的。 默认值是**无**。  
  
- **CRecordset::none**未设置选项。 此参数值是与所有其他值互相排斥的。 默认情况下，可以使用更新记录集[编辑](#edit)或[删除](#delete)，并允许追加新记录与[AddNew](#addnew)。 可更新性取决于数据源以及`nOpenType`您指定的选项。 批量添加的优化将不可用。 批量取行都不会实现。 已删除的记录不能跳过在记录集中导航。 书签将不可用。 实现自动已更新的字段检查。  
  
- **CRecordset::appendOnly**不允许**编辑**或**删除**对记录集。 允许`AddNew`仅。 此选项是互相排斥与**CRecordset::readOnly**。  
  
- **CRecordset::readOnly**打开以只读方式记录集。 此选项是互相排斥与**CRecordset::appendOnly**。  
  
- **CRecordset::optimizeBulkAdd**使用预定义的 SQL 语句来优化一次添加多个记录。 仅适用于未使用的 ODBC API 函数**SQLSetPos**要更新的记录集。 第一次更新确定哪些字段标记为已更新。 此选项是互相排斥与`CRecordset::useMultiRowFetch`。  
  
- `CRecordset::useMultiRowFetch`实现批量取行以允许在单个的提取操作中检索多个行。 这是设计用于提高性能; 一项高级的功能但是，ClassWizard 不支持批量记录字段交换。 此选项是互相排斥与**CRecordset::optimizeBulkAdd**。 请注意，如果您指定`CRecordset::useMultiRowFetch`，然后选择**CRecordset::noDirtyFieldCheck**将自动打开 （双缓冲将不可用）; 在只进记录集中，该选项**CRecordset::useExtendedFetch**将自动打开。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
- **CRecordset::skipDeletedRecords**在记录集中定位时跳过所有已删除的记录。 这将降低性能在某些相对提取操作中。 此选项仅向前的记录集上无效。 如果调用[移动](#move)与`nRows`参数设置为 0，并且**CRecordset::skipDeletedRecords**选项集，**移动**将断言。 请注意， **CRecordset::skipDeletedRecords**类似于*驱动程序装箱*，这意味着，已删除的行已从记录集。 但是，如果您的驱动程序包记录，然后它将跳过删除; 这些记录它不会跳过该记录集处于打开状态时，由其他用户删除的记录。 **CRecordset::skipDeletedRecords**将跳过的其他用户删除的行。  
  
- **CRecordset::useBookmarks**记录集，如果支持，可能会对其使用书签。 书签降低数据检索，但提高数据导航的性能。 在仅向前的记录集上无效。 有关详细信息，请参阅文章[记录集︰ 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。  
  
- **CRecordset::noDirtyFieldCheck**关闭自动已更新的字段检查 （双缓冲）。 这将提高性能;但是，您必须手动将标记字段为脏通过调用`SetFieldDirty`和`SetFieldNull`成员函数。请注意在类中的双缓冲`CRecordset`类似于类中的双缓冲`CDaoRecordset`。 但是，在`CRecordset`，则不能启用双缓冲的各个字段; 对于所有字段启用或禁用对所有字段。 请注意，如果指定了选项`CRecordset::useMultiRowFetch`，然后**CRecordset::noDirtyFieldCheck**自动; 但是，将打开`SetFieldDirty`和`SetFieldNull`不能用于实现批量取行的记录集。  
  
- **CRecordset::executeDirect**不使用预定义的 SQL 语句。 为提高性能，此选项指定如果**Requery**绝不会调用成员函数。  
  
- **CRecordset::useExtendedFetch**实现**SQLExtendedFetch**而不是**SQLFetch**。 这样设计是用于实现批量的只进的记录集取的行。 如果指定了选项`CRecordset::useMultiRowFetch`只进记录集，然后**CRecordset::useExtendedFetch**将自动打开。  
  
- **CRecordset::userAllocMultiRowBuffers**用户将为数据分配存储缓冲区。 将此选项中结合使用`CRecordset::useMultiRowFetch`如果您想要分配您自己的存储; 否则，该框架将自动分配必要的存储区。 有关详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 请注意该指定**CRecordset::userAllocMultiRowBuffers**而无需指定`CRecordset::useMultiRowFetch`将导致失败的断言。  
  
### <a name="return-value"></a>返回值  
 如果非零`CRecordset`对象已成功打开; 否则为 0 [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) （如果称为），则返回 0。  
  
### <a name="remarks"></a>备注  
 必须调用该成员函数以运行定义记录集的查询。 之前，先调用**打开**，您必须先构造记录集对象。  
  
 此记录集的连接到数据源取决于如何构造之前，先调用记录集**打开**。 如果您通过[CDatabase](../../mfc/reference/cdatabase-class.md)对象传递给尚未连接到数据源的记录集构造函数使用此成员函数[GetDefaultConnect](#getdefaultconnect)来尝试打开的数据库对象。 如果您通过**NULL**到记录集构造函数中，构造函数将构造`CDatabase`，为您的对象和**打开**尝试连接的数据库对象。 有关关闭记录集并在这些不同的情况下连接的详细信息，请参阅[关闭](#close)。  
  
> [!NOTE]
>  通过数据源访问的`CRecordset`始终共享对象。 与不同`CDaoRecordset`类，则不能使用`CRecordset`对象具有独占访问权打开数据源。  
  
 当您调用**打开**，一个查询，通常是 SQL**选择**语句中，选择根据下表中所示的条件的记录。  
  
|LpszSQL 参数的值|取决于所选记录|示例|  
|------------------------------------|----------------------------------------|-------------|  
|**NULL**|返回的字符串`GetDefaultSQL`。||  
|SQL 表名|中的表列表中的所有列`DoFieldExchange`或`DoBulkFieldExchange`。|`"Customer"`|  
|预定义的查询 （存储过程） 名称|查询定义要返回的列。|`"{call OverDueAccts}"`|  
|**选择**列列表**FROM**表列表|来自指定表的指定的列。|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|  
  
> [!CAUTION]
>  请注意执行 SQL 字符串中插入额外的空白。 例如，如果插入的大括号之间的空白和**调用**关键字，MFC 将错误解释为的表名的 SQL 字符串并将其插入合并**选择**语句中，这将导致引发异常。 同样，如果预定义的查询使用输出参数，不会插入在大括号之间的空白和 ' 符号。 最后，不能插入之前在大括号中的空白**调用**语句或之前**选择**中的关键字**选择**语句。  
  
 常规步骤是将传递**NULL**到**打开**; 在这种情况下，**打开**调用[GetDefaultSQL](#getdefaultsql)。 如果您使用派生`CRecordset`类， **GetDefaultSQL**提供类向导中指定的表名称。 您可以指定中的其他信息`lpszSQL`参数。  
  
 您传递的任何内容，**打开**构造查询的最终 SQL 字符串 (字符串可能具有 SQL**其中**和**ORDER BY**子句附加到`lpszSQL`您传递的字符串)，然后执行查询。 您可以通过调用检查构造的字符串[GetSQL](#getsql)之后调用**打开**。 有关记录集如何构造 SQL 语句并选择记录，有关其他详细信息，请参阅文章[记录集︰ 如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。  
  
 记录集类的字段数据成员被绑定到所选的数据的列。 如果返回任何记录，第一条记录成为当前记录。  
  
 如果您想要设置为记录集，如筛选或排序，选项指定这些属性构造记录集对象之后但在调用之前**打开**。 如果您想要刷新后记录集中记录的记录集已打开，请调用[Requery](#requery)。  
  
 有关详细信息，包括其他示例，请参阅文章[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)，[记录集︰ 如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)，和[记录集︰ 创建和关闭记录集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。  
  
### <a name="example"></a>示例  
 下面的代码示例演示不同形式的**打开**调用。  
  
 [!code-cpp[NVC_MFCDatabase #&16;](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]  
  
##  <a name="refreshrowset"></a>CRecordset::RefreshRowset  
 更新数据和当前行集中的行的状态。  
  
```  
void RefreshRowset(
    WORD wRow,  
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>参数  
 `wRow`  
 基于&1; 的行位置的当前行集中。 此值可介于&0; 到行集大小。  
  
 `wLockType`  
 一个值，该值刷新它后锁定行的方式。 有关详细信息，请参阅“备注”。  
  
### <a name="remarks"></a>备注  
 如果传递的值为零`wRow`，然后在行集中的每一行，则会刷新。  
  
 若要使用`RefreshRowset`，您必须已实现通过指定的大容量行取**CRecordset::useMulitRowFetch**选项[打开](#open)成员函数。  
  
 `RefreshRowset`调用 ODBC API 函数**SQLSetPos**。 `wLockType`参数指定后的行的锁状态**SQLSetPos**已执行。 下表描述了可能的值为`wLockTyp`e。  
  
|wLockType|描述|  
|---------------|-----------------|  
|`SQL_LOCK_NO_CHANGE`（默认值）|驱动程序或数据源可确保之前的一行是相同的锁定还是未锁定状态`RefreshRowset`调用。|  
|`SQL_LOCK_EXCLUSIVE`|驱动程序或数据源以独占方式锁定行。 并非所有数据源都支持这种类型的锁。|  
|`SQL_LOCK_UNLOCK`|驱动程序或数据源对行进行解锁。 并非所有数据源都支持这种类型的锁。|  
  
 有关详细信息**SQLSetPos**，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="requery"></a>CRecordset::Requery  
 重新生成 （刷新） 记录集。  
  
```  
virtual BOOL Requery();
```  
  
### <a name="return-value"></a>返回值  
 如果已成功重新生成该记录集; 则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 如果返回任何记录，第一条记录成为当前记录。  
  
 为了使记录集，以反映的添加和删除您或其他用户对数据源，你必须通过调用重建记录集**Requery**。 记录集是否动态集，它会自动反映您或其他用户对其现有记录 （但不是添加件） 进行的更新。 如果该记录集是一个快照，则必须调用**Requery**以反映由其他用户，以及添加和删除操作的编辑。  
  
 对于动态集还是快照中，调用**Requery**随时要重新生成使用新的筛选器或排序或新的参数值的记录集。 通过将新值赋给设置新的筛选或排序属性**m_strFilter**和`m_strSort`之前调用**Requery**。 通过将新值分配给之前调用的参数数据成员设置新的参数**Requery**。 如果筛选器和排序字符串未更改，您可以重复使用查询中，从而提高了性能。  
  
 如果重新生成该记录集的尝试失败，则关闭记录集。 在调用之前**Requery**，您可以确定是否可以通过调用重新记录集的查询`CanRestart`成员函数。 `CanRestart`不能保证**Requery**将会成功。  
  
> [!CAUTION]
>  调用**Requery**仅具有调用后[打开](#open)。  
  
### <a name="example"></a>示例  
 此示例重新生成一个记录集应用不同的排序顺序。  
  
 [!code-cpp[NVC_MFCDatabase #&29;](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]  
  
##  <a name="setabsoluteposition"></a>CRecordset::SetAbsolutePosition  
 将记录集中定位到指定的记录号相对应的记录。  
  
```  
void SetAbsolutePosition(long nRows);
```  
  
### <a name="parameters"></a>参数  
 `nRows`  
 基于&1; 的序号位置的当前记录在记录集中。  
  
### <a name="remarks"></a>备注  
 `SetAbsolutePosition`将当前记录指针根据此序号位置。  
  
> [!NOTE]
>  此成员函数无效，不能在仅向前的记录集中。  
  
 对于 ODBC 记录集的绝对位置设置为 1 是指在记录集中; 第一条记录设置为 0 是指开头的文件 (BOF) 位置。  
  
 您还可以传递到负值`SetAbsolutePosition`。 在这种情况下由记录集的结尾计算记录集的位置。 例如，`SetAbsolutePosition( -1 )`将当前记录指针移动到记录集内的最后一个记录。  
  
> [!NOTE]
>  绝对位置不是要用作代理记录编号。 书签仍然是保留和返回到给定位置在前面的记录都被删除时记录的位置更改以来的推荐的方法。 此外，则不能确保给定的记录将具有相同的绝对位置，如果重新因为不能保证在记录集内的单个记录的顺序，除非创建 SQL 语句使用重新创建该记录集**ORDER BY**子句。  
  
 有关记录集导航和书签的详细信息，请参阅文章[记录集︰ 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[记录集︰ 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。  
  
##  <a name="setbookmark"></a>CRecordset::SetBookmark  
 将记录集中定位包含指定的书签的记录。  
  
```  
void SetBookmark(const CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>参数  
 `varBookmark`  
 对引用[CDBVariant](../../mfc/reference/cdbvariant-class.md)对象，其中包含特定记录的书签值。  
  
### <a name="remarks"></a>备注  
 若要确定记录集上是否支持了书签，请调用[CanBookmark](#canbookmark)。 若要使书签可用，如果受支持，必须设置**CRecordset::useBookmarks**选项`dwOptions`参数[打开](#open)成员函数。  
  
> [!NOTE]
>  如果书签不受支持或不可用，则调用`SetBookmark`将导致引发异常。 只能向前的记录集不支持书签。  
  
 若要首先检索当前记录的书签，请调用[GetBookmark](#getbookmark)，该命令可保存到的书签值`CDBVariant`对象。 更高版本，你可以返回到该记录通过调用`SetBookmark`使用已保存的书签值。  
  
> [!NOTE]
>  某些记录集在操作后，您应该检查之前调用的书签持久性`SetBookmark`。 例如，如果检索具有书签`GetBookmark`，然后调用**Requery**，书签可能不再有效。 调用[CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)若要检查是否可以安全地调用`SetBookmark`。  
  
 有关书签和记录集导航的详细信息，请参阅文章[记录集︰ 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[记录集︰ 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
##  <a name="setfielddirty"></a>CRecordset::SetFieldDirty  
 标记为已更改的记录集或为未更改的字段数据成员。  
  
```  
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 包含在记录集中的字段数据成员的地址或**NULL**。 如果**NULL**，在记录集中的所有字段数据成员均未都标记。 (C + + **NULL**不是 Null 相同数据库术语中，这意味着"having 没有值。")  
  
 `bDirty`  
 **TRUE**字段数据成员是否被标记为"更新"（更改）。 否则为**FALSE**字段数据成员是否会被标记为"干净"（未更改）。  
  
### <a name="remarks"></a>备注  
 将标记为未更改的字段可确保该字段不更新，并减少 SQL 流量。  
  
> [!NOTE]
>  此成员函数不是适用于正在使用批量取行的记录集。 如果已实现批量取行，然后`SetFieldDirty`将导致失败的断言。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 Framework 线更改字段数据成员，以确保它们将被写入与数据源上记录的记录字段交换 (RFX) 机制。 更改字段的值通常设置的字段脏自动，因此您将很少需要调用`SetFieldDirty`，但您有时可能想要确保，列将显式更新或插入不管哪些值是字段数据成员中。  
  
> [!CAUTION]
>  只有具有调用之后才调用此成员函数[编辑](#edit)或[AddNew](#addnew)。  
  
 使用**NULL**为该函数的第一个参数将该函数仅适用于**outputColumn**字段，不**param**字段。 例如，调用  
  
 [!code-cpp[NVC_MFCDatabase #&26;](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 将仅设置**outputColumn**字段设置为**NULL**;**param**字段不会受到影响。  
  
 从事**param**字段中，你必须提供个人的实际地址**param**你想要使用，如︰  
  
 [!code-cpp[NVC_MFCDatabase #&27;](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 这意味着您不能设置所有**param**字段设置为**NULL**，如可以与**outputColumn**字段。  
  
##  <a name="setfieldnull"></a>CRecordset::SetFieldNull  
 为 Null （特别具有任何值） 或非空标记的记录集的字段数据成员。  
  
```  
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 包含在记录集中的字段数据成员的地址或**NULL**。 如果**NULL**，在记录集中的所有字段数据成员均未都标记。 (C + + **NULL**不是 Null 相同数据库术语中，这意味着"having 没有值。")  
  
 `bNull`  
 字段数据成员是否被标记为具有空值 (Null)，非零值。 否则为 0 的字段数据成员是否被标记为非 Null。  
  
### <a name="remarks"></a>备注  
 当将一条新记录添加到记录集时，所有字段数据成员最初设置为 Null 值并标记为"脏"（更改）。 当从数据源检索一条记录时，其列已具有值，或者都为 Null。  
  
> [!NOTE]
>  请勿在使用批量取行的记录集上调用该成员函数。 如果已实现批量取行，则调用`SetFieldNull`导致失败的断言。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 如果您特别希望将当前记录的字段指定为不具有值，调用`SetFieldNull`与`bNull`设置为**TRUE**标记为 Null。 如果字段以前标记为 Null，并且你现在想要为其提供一个值，只需设置它的新值。 不需要删除带有 Null 标志`SetFieldNull`。 若要确定是否允许该字段为 Null，请调用`IsFieldNullable`。  
  
> [!CAUTION]
>  只有具有调用之后才调用此成员函数[编辑](#edit)或[AddNew](#addnew)。  
  
 使用**NULL**为该函数的第一个参数将该函数仅适用于**outputColumn**字段，不**param**字段。 例如，调用  
  
 [!code-cpp[NVC_MFCDatabase #&26;](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 将仅设置**outputColumn**字段设置为**NULL**;**param**字段不会受到影响。  
  
 从事**param**字段中，你必须提供个人的实际地址**param**你想要使用，如︰  
  
 [!code-cpp[NVC_MFCDatabase #&27;](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 这意味着您不能设置所有**param**字段设置为**NULL**，如可以与**outputColumn**字段。  
  
> [!NOTE]
>  参数设置为 Null 时，调用时`SetFieldNull`记录集是打开的导致断言之前。 在这种情况下，调用[SetParamNull](#setparamnull)。  
  
 `SetFieldNull`通过实现[DoFieldExchange](#dofieldexchange)。  
  
##  <a name="setlockingmode"></a>CRecordset::SetLockingMode  
 设置为"开放式"锁定 （默认值） 或"保守式"锁定的锁定模式。 确定如何记录被锁定，无法更新。  
  
```  
void SetLockingMode(UINT nMode);
```  
  
### <a name="parameters"></a>参数  
 `nMode`  
 包含中的以下值之一**枚举 LockMode**:  
  
- **开放式**乐观锁定锁定仅在调用期间所更新的记录**更新**。  
  
- **保守式**保守式锁定锁定记录就立即**编辑**调用并将其锁定之前保留**更新**调用完成或移动到一条新记录。  
  
### <a name="remarks"></a>备注  
 如果您需要指定这两个记录集使用更新的记录锁定的策略，则调用此成员函数。 默认情况下，记录集的锁定模式是**开放式**。 您可以更改，为更加小心**保守式**锁定策略。 调用`SetLockingMode`构造并打开记录集对象之后但在调用之前**编辑**。  
  
##  <a name="setparamnull"></a>CRecordset::SetParamNull  
 标志参数为 Null （特别具有任何值） 或非 Null。  
  
```  
void SetParamNull(
    int nIndex,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 参数的从零开始的索引。  
  
 `bNull`  
 如果**TRUE** （默认值），该参数标记为 Null。 否则，该参数被标记为非 Null。  
  
### <a name="remarks"></a>备注  
 与不同[SetFieldNull](#setfieldnull)，您可以调用`SetParamNull`已打开记录集之前。  
  
 `SetParamNull`通常与预定义的查询 （存储过程） 一起使用。  
  
##  <a name="setrowsetcursorposition"></a>CRecordset::SetRowsetCursorPosition  
 将光标移到当前行集内的行。  
  
```  
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>参数  
 `wRow`  
 基于&1; 的行位置的当前行集中。 此值可介于 1 到行集大小。  
  
 `wLockType`  
 值，该值指示如何刷新它后锁定该行。 有关详细信息，请参阅“备注”。  
  
### <a name="remarks"></a>备注  
 当实现批量取行时，记录将检索的行集，其中第一个记录中提取行集是当前记录。 为了使该行集内的另一条记录成为当前记录，调用`SetRowsetCursorPosition`。 例如，可以合并`SetRowsetCursorPosition`与[GetFieldValue](#getfieldvalue)成员函数以动态地从记录集中的任何记录中检索数据。  
  
 若要使用`SetRowsetCursorPosition`，您必须已实现通过指定的大容量行取`CRecordset::useMultiRowFetch`选项`dwOptions`中的参数[打开](#open)成员函数。  
  
 `SetRowsetCursorPosition`调用 ODBC API 函数**SQLSetPos**。 `wLockType`参数指定后的行的锁状态**SQLSetPos**已执行。 下表描述了可能的值为`wLockTyp`e。  
  
|wLockType|描述|  
|---------------|-----------------|  
|`SQL_LOCK_NO_CHANGE`（默认值）|驱动程序或数据源可确保之前的一行是相同的锁定还是未锁定状态`SetRowsetCursorPosition`调用。|  
|`SQL_LOCK_EXCLUSIVE`|驱动程序或数据源以独占方式锁定行。 并非所有数据源都支持这种类型的锁。|  
|`SQL_LOCK_UNLOCK`|驱动程序或数据源对行进行解锁。 并非所有数据源都支持这种类型的锁。|  
  
 有关详细信息**SQLSetPos**，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="setrowsetsize"></a>CRecordset::SetRowsetSize  
 指定你想要在提取过程中检索的记录数。  
  
```  
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```  
  
### <a name="parameters"></a>参数  
 *dwNewRowsetSize*  
 要在给定提取过程中检索的行数。  
  
### <a name="remarks"></a>备注  
 此虚拟成员函数可指定您想要使用批量取行时，在一次获取期间检索的行数。 若要实现批量取行，必须设置`CRecordset::useMultiRowFetch`选项`dwOptions`参数[打开](#open)成员函数。  
  
> [!NOTE]
>  调用`SetRowsetSize`而无需实现批量取行，则会失败的断言。  
  
 调用`SetRowsetSize`之前调用**打开**最初设置为记录集的行集大小。 实现批量取行时的默认行集大小为 25。  
  
> [!NOTE]
>  在调用时要格外小心`SetRowsetSize`。 如果手动分配存储的数据 (所指定的**CRecordset::userAllocMultiRowBuffers**选项中的 dwOptions 参数**打开**)，您应该检查您是否需要重新分配存储缓冲区之后调用`SetRowsetSize`，但在执行任何游标导航操作之前。  
  
 若要获取行集大小的当前设置，请调用[GetRowsetSize](#getrowsetsize)。  
  
 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="update"></a>CRecordset::Update  
 完成`AddNew`或**编辑**通过将新的或编辑数据保存在数据源上的操作。  
  
```  
virtual BOOL Update();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果一条记录已成功更新;如果没有列已更改为否则为 0。 如果没有更新任何记录，或者如果有多个记录已更新，则将引发异常。 也会引发异常的任何其他失败对数据源。  
  
### <a name="remarks"></a>备注  
 在调用后调用此成员函数[AddNew](#addnew)或[编辑](#edit)成员函数。 完成所需的此调用`AddNew`或**编辑**操作。  
  
> [!NOTE]
>  如果已实现批量取行，则无法调用**更新**。 这将导致失败的断言。 尽管类`CRecordset`不提供一种机制进行更新的数据大容量行，您可以通过使用 ODBC API 函数中编写您自己的函数**SQLSetPos**。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 同时`AddNew`和**编辑**添加或编辑过的数据放置在其中编辑缓冲区准备保存到数据源。 **更新**将数据保存。 更新只有这些字段标记，或者检测到为已更改。  
  
 如果数据源支持事务，则可以使**更新**调用 (及其相应`AddNew`或**编辑**调用) 事务的一部分。 有关事务的详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
> [!CAUTION]
>  如果调用**更新**而不必首先调用`AddNew`或**编辑**，**更新**引发`CDBException`。 如果调用`AddNew`或**编辑**，必须调用**更新**之前调用**移动**操作或关闭记录集或数据源连接之前。 否则，所做的更改都将丢失而不另行通知。  
  
 有关处理的详细信息**更新**失败，请参阅文章[记录集︰ 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
### <a name="example"></a>示例  
 请参阅文章[事务︰ 在记录集 (ODBC) 执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDatabase 类](../../mfc/reference/cdatabase-class.md)   
 [CRecordView 类](../../mfc/reference/crecordview-class.md)

