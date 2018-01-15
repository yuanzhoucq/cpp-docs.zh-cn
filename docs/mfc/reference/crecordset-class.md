---
title: "CRecordset 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CRecordset [MFC], CRecordset
- CRecordset [MFC], AddNew
- CRecordset [MFC], CanAppend
- CRecordset [MFC], CanBookmark
- CRecordset [MFC], Cancel
- CRecordset [MFC], CancelUpdate
- CRecordset [MFC], CanRestart
- CRecordset [MFC], CanScroll
- CRecordset [MFC], CanTransact
- CRecordset [MFC], CanUpdate
- CRecordset [MFC], CheckRowsetError
- CRecordset [MFC], Close
- CRecordset [MFC], Delete
- CRecordset [MFC], DoBulkFieldExchange
- CRecordset [MFC], DoFieldExchange
- CRecordset [MFC], Edit
- CRecordset [MFC], FlushResultSet
- CRecordset [MFC], GetBookmark
- CRecordset [MFC], GetDefaultConnect
- CRecordset [MFC], GetDefaultSQL
- CRecordset [MFC], GetFieldValue
- CRecordset [MFC], GetODBCFieldCount
- CRecordset [MFC], GetODBCFieldInfo
- CRecordset [MFC], GetRecordCount
- CRecordset [MFC], GetRowsetSize
- CRecordset [MFC], GetRowsFetched
- CRecordset [MFC], GetRowStatus
- CRecordset [MFC], GetSQL
- CRecordset [MFC], GetStatus
- CRecordset [MFC], GetTableName
- CRecordset [MFC], IsBOF
- CRecordset [MFC], IsDeleted
- CRecordset [MFC], IsEOF
- CRecordset [MFC], IsFieldDirty
- CRecordset [MFC], IsFieldNull
- CRecordset [MFC], IsFieldNullable
- CRecordset [MFC], IsOpen
- CRecordset [MFC], Move
- CRecordset [MFC], MoveFirst
- CRecordset [MFC], MoveLast
- CRecordset [MFC], MoveNext
- CRecordset [MFC], MovePrev
- CRecordset [MFC], OnSetOptions
- CRecordset [MFC], OnSetUpdateOptions
- CRecordset [MFC], Open
- CRecordset [MFC], RefreshRowset
- CRecordset [MFC], Requery
- CRecordset [MFC], SetAbsolutePosition
- CRecordset [MFC], SetBookmark
- CRecordset [MFC], SetFieldDirty
- CRecordset [MFC], SetFieldNull
- CRecordset [MFC], SetLockingMode
- CRecordset [MFC], SetParamNull
- CRecordset [MFC], SetRowsetCursorPosition
- CRecordset [MFC], SetRowsetSize
- CRecordset [MFC], Update
- CRecordset [MFC], m_hstmt
- CRecordset [MFC], m_nFields
- CRecordset [MFC], m_nParams
- CRecordset [MFC], m_pDatabase
- CRecordset [MFC], m_strFilter
- CRecordset [MFC], m_strSort
ms.assetid: dd89a21d-ef39-4aab-891b-1e373d67c855
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c2375739fe4d8442d4ecb7a1514641d45de4a8be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="crecordset-class"></a>CRecordset 类
表示从数据源选择的一组记录。  
  
## <a name="syntax"></a>语法  
  
```  
class CRecordset : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CRecordset::CRecordset](#crecordset)|构造 `CRecordset` 对象。 在派生的类必须提供调用此构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRecordset::AddNew](#addnew)|准备用于添加新记录。 调用`Update`完成添加。|  
|[CRecordset::CanAppend](#canappend)|返回非零，如果可以将新记录添加到记录集通过`AddNew`成员函数。|  
|[CRecordset::CanBookmark](#canbookmark)|返回非零，如果记录集支持书签。|  
|[CRecordset::Cancel](#cancel)|取消一个异步操作或从第二个线程的进程。|  
|[CRecordset::CancelUpdate](#cancelupdate)|取消任何挂起的更新，由于`AddNew`或`Edit`操作。|  
|[CRecordset::CanRestart](#canrestart)|返回非零如果`Requery`可以调用以进行重新运行记录集的查询。|  
|[CRecordset::CanScroll](#canscroll)|返回非零，如果可以滚动显示记录。|  
|[CRecordset::CanTransact](#cantransact)|返回非零，如果数据源支持事务。|  
|[CRecordset::CanUpdate](#canupdate)|返回非零，如果可以更新记录集 （你可以添加、 更新或删除记录）。|  
|[CRecordset::CheckRowsetError](#checkrowseterror)|调用以处理在记录提取过程中生成的错误。|  
|[CRecordset::Close](#close)|关闭记录集和 ODBC **HSTMT**与之关联。|  
|[CRecordset::Delete](#delete)|从记录集删除当前记录。 你必须显式滚动到另一条记录后删除。|  
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|调用以交换的数据源得到记录集的数据大容量行。 实现大容量记录字段交换 (Bulk RFX)。|  
|[CRecordset::DoFieldExchange](#dofieldexchange)|调用以 （在两个方向） 和之间交换数据的记录集的字段数据成员的数据源上相应的记录。 实现记录字段交换 (RFX)。|  
|[CRecordset::Edit](#edit)|准备对当前记录的更改。 调用`Update`来完成编辑。|  
|[CRecordset::FlushResultSet](#flushresultset)|返回非零，如果没有另一个结果设置要从中检索，使用预定义的查询时。|  
|[CRecordset::GetBookmark](#getbookmark)|将一条记录的书签值分配到参数对象。|  
|[CRecordset::GetDefaultConnect](#getdefaultconnect)|调用以获取默认连接字符串。|  
|[CRecordset::GetDefaultSQL](#getdefaultsql)|调用以获取要执行的默认 SQL 字符串。|  
|[CRecordset::GetFieldValue](#getfieldvalue)|在记录集中返回的字段的值。|  
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|在记录集中返回的字段的数目。|  
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|在记录集中返回特定类型的字段的信息。|  
|[CRecordset::GetRecordCount](#getrecordcount)|在记录集中返回记录的数。|  
|[CRecordset::GetRowsetSize](#getrowsetsize)|返回你想要在一次获取期间检索的记录数。|  
|[CRecordset::GetRowsFetched](#getrowsfetched)|返回的实际在提取过程中检索的行数。|  
|[CRecordset::GetRowStatus](#getrowstatus)|在提取后返回的行的状态。|  
|[CRecordset::GetSQL](#getsql)|获取用于选择记录的记录集的 SQL 字符串。|  
|[CRecordset::GetStatus](#getstatus)|获取记录集的状态： 当前记录和是否已获得最终的记录计数的索引。|  
|[CRecordset::GetTableName](#gettablename)|获取记录集所基于的表的名称。|  
|[CRecordset::IsBOF](#isbof)|返回非零，如果在第一条记录之前定位位置记录集。 没有最新记录。|  
|[CRecordset::IsDeleted](#isdeleted)|返回非零，如果记录集定位在已删除的记录上。|  
|[CRecordset::IsEOF](#iseof)|返回非零，如果在最后一条记录后定位位置记录集。 没有最新记录。|  
|[CRecordset::IsFieldDirty](#isfielddirty)|返回非零，如果已更改的当前记录中的指定的字段。|  
|[CRecordset::IsFieldNull](#isfieldnull)|返回非零，如果当前记录中的指定的字段为 null （具有任何值）。|  
|[CRecordset::IsFieldNullable](#isfieldnullable)|返回非零，如果当前记录中的指定的字段可以设置为 null （无任何值）。|  
|[CRecordset::IsOpen](#isopen)|返回非零如果`Open`已被调用过。|  
|[CRecordset::Move](#move)|将记录集到指定的记录数置于从中两个方向的当前记录。|  
|[CRecordset::MoveFirst](#movefirst)|在记录集中的第一个记录置于当前记录。 测试`IsBOF`第一个。|  
|[CRecordset::MoveLast](#movelast)|确定当前记录的位置上的最新记录或最后一个行集上。 测试`IsEOF`第一个。|  
|[CRecordset::MoveNext](#movenext)|确定当前记录的位置，在下一条记录或下一步的行集上。 测试`IsEOF`第一个。|  
|[CRecordset::MovePrev](#moveprev)|确定当前记录的位置，在上一记录或以前的行集上。 测试`IsBOF`第一个。|  
|[CRecordset::OnSetOptions](#onsetoptions)|设置选项 （在所选内容上使用） 为调用指定的 ODBC 语句。|  
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|调用以设置指定的 ODBC 语句 （在更新使用） 的选项。|  
|[CRecordset::Open](#open)|通过检索表或执行查询记录集表示打开记录集。|  
|[CRecordset::RefreshRowset](#refreshrowset)|刷新的数据和状态的指定的行。|  
|[CRecordset::Requery](#requery)|运行记录集的查询，再次以刷新选定的记录。|  
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|定位上与指定的记录号相对应的记录，记录集。|  
|[CRecordset::SetBookmark](#setbookmark)|在指定的书签记录定位记录集。|  
|[CRecordset::SetFieldDirty](#setfielddirty)|将当前记录中的指定的字段标记为已更改。|  
|[CRecordset::SetFieldNull](#setfieldnull)|设置为 null （无任何值） 的当前记录中的指定字段的值。|  
|[CRecordset::SetLockingMode](#setlockingmode)|设置为"开放式"锁定 （默认值） 或"保守式"锁定的锁定模式。 确定如何记录被锁定，无法更新。|  
|[CRecordset::SetParamNull](#setparamnull)|将指定的参数设置为 null （无任何值）。|  
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|将光标置于行集内指定的行。|  
|[CRecordset::SetRowsetSize](#setrowsetsize)|指定你想要在提取过程中检索的记录数。|  
|[CRecordset::Update](#update)|完成`AddNew`或`Edit`通过将新的或编辑数据保存在数据源上的操作。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CRecordset::m_hstmt](#m_hstmt)|包含记录集的 ODBC 语句句柄。 键入 `HSTMT`。|  
|[CRecordset::m_nFields](#m_nfields)|包含在记录集中的字段数据成员的数目。 键入 `UINT`。|  
|[CRecordset::m_nParams](#m_nparams)|包含在记录集中的参数数据成员的数目。 键入 `UINT`。|  
|[CRecordset::m_pDatabase](#m_pdatabase)|包含指向的`CDatabase`通过该记录集连接到数据源的对象。|  
|[CRecordset::m_strFilter](#m_strfilter)|包含`CString`，它指定结构化查询语言 (SQL)`WHERE`子句。 作为筛选器用于选择满足特定条件的那些记录。|  
|[CRecordset::m_strSort](#m_strsort)|包含`CString`，指定 SQL`ORDER BY`子句。 用于控制所记录的排序方式。|  
  
## <a name="remarks"></a>备注  
 名为"记录集，"`CRecordset`对象通常使用两种形式： 动态记录集和快照。 动态集与其他用户所做的数据更新中保持同步。 快照是数据的静态视图。 每个窗体表示一组固定的记录集打开时，记录但时滚动到中动态集的记录时，它反映随后所做的更改记录、 其他用户或其他应用程序中的记录集。  
  
> [!NOTE]
>  如果你正在使用的数据访问对象 (DAO) 类，而不是开放式数据库连接 (ODBC) 类，可以使用类[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)相反。 有关详细信息，请参阅文章[概述： 数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
 若要使用这两种记录集，你通常派生从一个应用程序特定的记录集类`CRecordset`。 记录集从数据源，选择记录，然后，你可以：  
  
-   滚动记录。  
  
-   更新的记录并指定锁定模式。  
  
-   筛选为约束从提供的那些数据源选择哪些记录的记录集。  
  
-   对记录集进行排序。  
  
-   参数化记录集使用直到运行时才知道的信息自定义的所选内容。  
  
 若要使用你的类，打开数据库，并构造记录集对象，向构造函数传递一个指向你`CDatabase`对象。 然后调用记录集的**打开**成员函数，你可以在其中指定的对象是否动态集或快照。 调用**打开**从数据源中选择数据。 打开记录集对象后，使用其成员函数和数据成员滚动显示记录并对它们进行操作。 可执行的操作取决于该对象是动态集或快照，它是可更新还是只读 （这取决于开放式数据库连接 (ODBC) 数据源的功能），并且是否已实现批量行提取。 若要刷新记录可能已更改或添加自**打开**调用，调用对象的**Requery**成员函数。 调用对象的**关闭**成员函数，并使用它完成后销毁对象。  
  
 在派生`CRecordset`类中，记录字段交换 (RFX) 或批量记录字段交换 (Bulk RFX) 用于支持读取和更新的记录字段。  
  
 有关记录集和记录字段交换的详细信息，请参阅文章[概述： 数据库编程](../../data/data-access-programming-mfc-atl.md)，[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)，[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)，和[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。 重点动态记录集和快照，请参阅文章[动态集](../../data/odbc/dynaset.md)和[快照](../../data/odbc/snapshot.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CRecordset`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxdb.h  
  
##  <a name="addnew"></a>CRecordset::AddNew  
 准备要向表中添加一条新记录。  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>备注  
 必须调用[Requery](#requery)成员函数，以查看新添加的记录。 记录的字段均最初为空。 (在数据库术语中，Null 表示"having 没有值"，并且不能与相同**NULL** c + + 中。)若要完成该操作，必须调用[更新](#update)成员函数。 **更新**将所做的更改保存到数据源。  
  
> [!NOTE]
>  如果你已实现批量行提取，则无法调用`AddNew`。 这将导致失败的断言。 尽管类`CRecordset`不提供一种机制，用于更新的数据大容量行，你可以通过使用 ODBC API 函数编写您自己的函数**SQLSetPos**。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
 `AddNew`准备新的空记录中使用的记录集的字段数据成员。 调用后`AddNew`，在记录集的字段数据成员中设置所需的值。 (无需调用[编辑](#edit)为此目的的成员函数; 请改用**编辑**仅为现有记录。)当你随后调用**更新**、 已更改的字段数据成员中的值将保存在数据源上。  
  
> [!CAUTION]
>  如果你向下滚动到一条新记录你在调用之前**更新**、 新的记录都将丢失，并且不提供任何警告。  
  
 如果数据源支持事务，则可以使你`AddNew`调用事务的一部分。 有关事务的详细信息，请参阅类[CDatabase](../../mfc/reference/cdatabase-class.md)。 请注意，应调用[CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans)之前调用`AddNew`。  
  
> [!NOTE]
>  动态集的新记录添加到记录集作为最后一条记录。 添加的记录不会添加到快照;必须调用**Requery**刷新记录集。  
  
 它是非法调用`AddNew`为记录集其**打开**不调用成员函数。 A`CDBException`如果调用引发`AddNew`无法附加到记录集。 你可以确定记录集是否可以更新通过调用[CanAppend](#canappend)。  
  
 有关详细信息，请参阅以下文章：[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)，[记录集： 添加、 更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)，和[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
### <a name="example"></a>示例  
 请参阅文章[事务： 在记录集 (ODBC) 执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。  
  
##  <a name="canappend"></a>CRecordset::CanAppend  
 确定是否以前已打开记录集可用于添加新记录。  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果是记录集允许添加新记录; 则为非 0否则为 0。 `CanAppend`如果你打开记录集持久化为只读的则将返回 0。  
  
##  <a name="canbookmark"></a>CRecordset::CanBookmark  
 确定是否记录集允许你将标记为使用书签的记录。  
  
```  
BOOL CanBookmark() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果记录集支持书签; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数是独立于**CRecordset::useBookmarks**选项`dwOptions`参数[打开](#open)成员函数。 `CanBookmark`指示给定的 ODBC 驱动程序及光标是否类型支持书签。 **CRecordset::useBookmarks**指示在提供它们支持是否可用，书签。  
  
> [!NOTE]
>  只进的记录集不支持书签。  
  
 有关书签和记录集导航的详细信息，请参阅文章[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
##  <a name="cancel"></a>CRecordset::Cancel  
 数据源取消正在进行的异步操作或从第二个线程的进程的请求。  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>备注  
 请注意，MFC ODBC 类不再使用异步处理;若要执行异步操作，必须直接调用 ODBC API 函数**SQLSetConnectOption**。 有关详细信息，请参阅 》 中的主题"异步执行函数" *ODBC SDK 程序员指南*。  
  
##  <a name="cancelupdate"></a>CRecordset::CancelUpdate  
 取消任何挂起的更新，引起[编辑](#edit)或[AddNew](#addnew)操作之前,[更新](#update)调用。  
  
```  
void CancelUpdate();
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  此成员函数不是适用于使用的批量行提取，因为不能调用此类记录集的记录集**编辑**， `AddNew`，或**更新**。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
 如果启用自动已更新的字段检查，`CancelUpdate`将还原到之前所具有的值的成员变量**编辑**或`AddNew`调用; 否则为值的任何更改将保留。 默认情况下，字段自动检查被启用打开记录集时。 若要禁用它，你必须指定**CRecordset::noDirtyFieldCheck**中`dwOptions`参数[打开](#open)成员函数。  
  
 有关更新数据的详细信息，请参阅文章[记录集： 添加、 更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)。  
  
##  <a name="canrestart"></a>CRecordset::CanRestart  
 确定记录集是否允许通过调用重启 （若要刷新其记录） 其查询**Requery**成员函数。  
  
```  
BOOL CanRestart() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果允许 requery; 则为非 0否则为 0。  
  
##  <a name="canscroll"></a>CRecordset::CanScroll  
 确定是否记录集允许滚动。  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果是记录集允许滚动，则为非零否则为 0。  
  
### <a name="remarks"></a>备注  
 有关滚动的详细信息，请参阅文章[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
##  <a name="cantransact"></a>CRecordset::CanTransact  
 确定记录集是否允许事务。  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果是记录集允许事务; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="canupdate"></a>CRecordset::CanUpdate  
 确定是否可以更新记录集。  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果可以更新记录集; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 记录集可能是只读的如果基础数据源是只读的或你指定**CRecordset::readOnly**中`dwOptions`参数打开记录集时。  
  
##  <a name="checkrowseterror"></a>CRecordset::CheckRowsetError  
 调用以处理在记录提取过程中生成的错误。  
  
```  
virtual void CheckRowsetError(RETCODE nRetCode);
```  
  
### <a name="parameters"></a>参数  
 `nRetCode`  
 ODBC API 函数返回代码。 有关详细信息，请参阅“备注”。  
  
### <a name="remarks"></a>备注  
 此虚拟成员函数处理时记录提取出来后，出现错误和批量行提取期间很有用。 你可能想要考虑重写`CheckRowsetError`来实现你自己的错误处理。  
  
 `CheckRowsetError`将自动调用在光标导航操作中，如**打开**， **Requery**，或任何**移动**操作。 它传递 ODBC API 函数的返回值**SQLExtendedFetch**。 下表列出的可能值`nRetCode`参数。  
  
|nRetCode|描述|  
|--------------|-----------------|  
|**SQL_SUCCESS**|已成功; 完成函数提供不了任何其他信息。|  
|**SQL_SUCCESS_WITH_INFO**|已成功完成，可能出现非致命错误的函数。 可以通过调用获取其他信息**SQLError**。|  
|**SQL_NO_DATA_FOUND**|已提取了从结果集中的所有行。|  
|**SQL_ERROR**|失败的函数。 可以通过调用获取其他信息**SQLError**。|  
|**SQL_INVALID_HANDLE**|由于无效的环境句柄、 连接句柄或语句句柄失败函数。 这指示编程错误。 无更多信息位于**SQLError**。|  
|`SQL_STILL_EXECUTING`|仍在执行已以异步方式启动的函数。 请注意，默认情况下，MFC 将永远不会将此值传递到`CheckRowsetError`;MFC 将继续调用**SQLExtendedFetch**直到不再返回`SQL_STILL_EXECUTING`。|  
  
 有关详细信息**SQLError**，请参阅 Windows SDK。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
##  <a name="close"></a>CRecordset::Close  
 关闭记录集。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 ODBC **HSTMT**和所有内存分配为记录集的框架后被释放。 通常在调用之后**关闭**，如果它已分配了与删除 c + + 记录集对象**新**。  
  
 你可以调用**打开**在调用后再次**关闭**。 这样就可以重复使用记录集对象。 替代项是调用**Requery**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]  
  
##  <a name="crecordset"></a>CRecordset::CRecordset  
 构造 `CRecordset` 对象。  
  
```  
CRecordset(CDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pDatabase`  
 包含指向的`CDatabase`对象或值**NULL**。 如果不是**NULL**和`CDatabase`对象的**打开**成员函数不调用以将其连接到数据源，记录集尝试自己期间为您打开它**打开**调用。 如果你通过**NULL**、`CDatabase`进行构造对象并将其连接为你使用你指定 ClassWizard 你记录集类的派生时的数据源信息。  
  
### <a name="remarks"></a>备注  
 你可以使用`CRecordset`直接派生从应用程序特定类或`CRecordset`。 可以使用 ClassWizard 派生记录集类。  
  
> [!NOTE]
>  派生的类*必须*提供其自己的构造函数。 在派生类的构造函数调用的构造函数`CRecordset::CRecordset`，将沿适当的参数传递给它。  
  
 传递**NULL**到记录集构造函数，以具有`CDatabase`对象构造并为你自动连接。 这是一种有用的简写形式，不需要你构造并连接`CDatabase`之前构造记录集对象。  
  
### <a name="example"></a>示例  
 有关详细信息，请参阅文章[记录集： 声明一个类用于表 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。  
  
##  <a name="delete"></a>CRecordset::Delete  
 删除当前记录。  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>备注  
 在成功删除之后, 记录集的字段数据成员设置为 Null 值，并且必须显式调用其中一个**移动**函数以便迁出已删除的记录。 一旦离开已删除的记录，不能返回到它。 如果数据源支持事务，则你可以**删除**调用事务的一部分。 有关详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
> [!NOTE]
>  如果你已实现批量行提取，则无法调用**删除**。 这将导致失败的断言。 尽管类`CRecordset`不提供一种机制，用于更新的数据大容量行，你可以通过使用 ODBC API 函数编写您自己的函数**SQLSetPos**。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
> [!CAUTION]
>  记录集必须是可更新，且必须具有有效记录的记录集当前在调用时**删除**; 否则为将会出错。 例如，如果你删除一条记录，但你在调用之前不将其滚动到一条新记录**删除**再次，**删除**引发[CDBException](../../mfc/reference/cdbexception-class.md)。  
  
 与不同[AddNew](#addnew)和[编辑](#edit)，调用**删除**对的调用后面不接[更新](#update)。 如果**删除**调用失败，字段数据成员将保留不变。  
  
### <a name="example"></a>示例  
 此示例演示在函数的帧上创建记录集。 该示例假定存在`m_dbCust`，类型的成员变量`CDatabase`已连接到数据源。  
  
 [!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]  
  
##  <a name="dobulkfieldexchange"></a>CRecordset::DoBulkFieldExchange  
 调用以交换的数据源得到记录集的数据大容量行。 实现大容量记录字段交换 (Bulk RFX)。  
  
```  
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向的指针[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象。 框架将已安装了此对象以便字段交换操作为指定上下文。  
  
### <a name="remarks"></a>备注  
 实现批量行提取时，框架将调用此成员函数以自动将数据从数据源传输到记录集对象。 `DoBulkFieldExchange`如果有的话，到记录集的选择的 SQL 语句字符串中的参数占位符，还将你的参数数据成员，绑定。  
  
 如果未实现批量行提取，框架将调用[DoFieldExchange](#dofieldexchange)。 若要实现批量行提取，必须指定`CRecordset::useMultiRowFetch`选项`dwOptions`中的参数[打开](#open)成员函数。  
  
> [!NOTE]
> `DoBulkFieldExchange`仅当使用派生自的类可用`CRecordset`。 如果你已创建记录集对象直接从`CRecordset`，必须调用[GetFieldValue](#getfieldvalue)成员函数来检索数据。  
  
 批量记录字段交换 (Bulk RFX) 是相似记录字段交换 (RFX)。 数据将自动传输从数据源到记录集对象。 但是，不能调用`AddNew`，**编辑**，**删除**，或**更新**传输回数据源的更改。 类`CRecordset`目前不提供一种机制用于更新大容量行的数据; 但是，可以通过使用 ODBC API 函数编写您自己的函数**SQLSetPos**。  
  
 请注意，ClassWizard 不支持批量记录字段交换;因此，你必须重写`DoBulkFieldExchange`手动通过编写对批量 RFX 函数的调用。 有关这些函数的详细信息，请参阅主题[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。  
  
 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。 有关相关信息，请参阅文章[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
##  <a name="dofieldexchange"></a>CRecordset::DoFieldExchange  
 调用以 （在两个方向） 和之间交换数据的记录集的字段数据成员的数据源上相应的记录。 实现记录字段交换 (RFX)。  
  
```  
virtual void DoFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向的指针[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象。 框架将已安装了此对象以便字段交换操作为指定上下文。  
  
### <a name="remarks"></a>备注  
 不实现批量行提取时，框架将调用此成员函数以自动交换字段数据成员的记录集对象和数据源上的当前记录的相应列之间的数据。 `DoFieldExchange`如果有的话，到记录集的选择的 SQL 语句字符串中的参数占位符，还将你的参数数据成员，绑定。  
  
 如果已实现批量行提取，框架将调用[DoBulkFieldExchange](#dobulkfieldexchange)。 若要实现批量行提取，必须指定`CRecordset::useMultiRowFetch`选项`dwOptions`中的参数[打开](#open)成员函数。  
  
> [!NOTE]
> `DoFieldExchange`仅当使用派生自的类可用`CRecordset`。 如果你已创建记录集对象直接从`CRecordset`，必须调用[GetFieldValue](#getfieldvalue)成员函数来检索数据。  
  
 字段数据，称为记录字段交换 (RFX) 的交换的工作方式在两个方向： 从数据源上的记录的字段的记录集对象的字段数据成员和记录集对象的数据源上的记录。  
  
 您通常必须执行以便实现的唯一操作`DoFieldExchange`为派生记录集类是与 ClassWizard 创建类并指定的字段数据成员的名称和数据类型。 此外可能将代码添加到 ClassWizard 写入指定的参数数据成员，或处理动态绑定任何列。 有关详细信息，请参阅文章[记录集： 动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
 在声明 ClassWizard 你派生的记录集类时，向导会将写入的重写`DoFieldExchange`，类似于下面的示例：  
  
 [!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]  
  
 有关 RFX 函数的详细信息，请参阅主题[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。  
  
 有关更多示例和有关的详细信息`DoFieldExchange`，请参阅文章[记录字段交换： RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。 有关 RFX 的常规信息，请参阅文章[记录字段交换](../../data/odbc/record-field-exchange-rfx.md)。  
  
##  <a name="edit"></a>CRecordset::Edit  
 允许对当前记录的更改。  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>备注  
 调用后**编辑**，你可以通过直接重置其值更改的字段数据成员。 在操作完成时随后调用[更新](#update)成员函数以将所做的更改保存在数据源上。  
  
> [!NOTE]
>  如果你已实现批量行提取，则无法调用**编辑**。 这将导致失败的断言。 尽管类`CRecordset`不提供一种机制，用于更新的数据大容量行，你可以通过使用 ODBC API 函数编写您自己的函数**SQLSetPos**。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
 **编辑**将保存记录集的数据成员的值。 如果调用**编辑**，进行更改，然后调用**编辑**再次，记录的值都将还原到它们早于第一个是**编辑**调用。  
  
 在某些情况下，你可能想要通过使 Null （不包含任何数据） 中更新列。 为此，请调用[SetFieldNull](#setfieldnull)其中参数**TRUE**标记字段为 Null。 这也会导致要更新的列。 如果你想要写入到数据源中，即使其值未更改，请调用的字段[SetFieldDirty](#setfielddirty)其中参数**TRUE**。 之所以即使字段具有 Null 值。  
  
 如果数据源支持事务，则你可以**编辑**调用事务的一部分。 请注意，应调用[CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans)之前调用**编辑**和之后打开记录集。 此外请注意，调用[CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)不能用于调用代替**更新**完成**编辑**操作。 有关事务的详细信息，请参阅类[CDatabase](../../mfc/reference/cdatabase-class.md)。  
  
 具体取决于当前的锁定模式下，要更新的记录可能被锁定**编辑**直到你调用**更新**或滚动到另一条记录，或它可能仅在被锁定**编辑**调用。 您可以更改与锁定模式[SetLockingMode](#setlockingmode)。  
  
 如果滚动到一条新记录之前调用还原以前的值的当前记录**更新**。 A`CDBException`如果调用引发**编辑**记录集不能更新或如果没有当前记录。  
  
 有关详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)和[记录集： 锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]  
  
##  <a name="flushresultset"></a>CRecordset::FlushResultSet  
 如果有多个结果集，检索预定义的查询 （存储过程），下一个结果集。  
  
```  
BOOL FlushResultSet();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果有多个结果集一个示例。否则为 0。  
  
### <a name="remarks"></a>备注  
 应调用`FlushResultSet`只有当您处于完全完成将光标放在当前结果集。 请注意，当你检索下一个结果集通过调用`FlushResultSet`，光标在该结果集上无效; 应调用[MoveNext](#movenext)之后调用的成员函数`FlushResultSet`。  
  
 如果预定义的查询使用输出参数或输入/输出参数，则必须调用`FlushResultSet`直到它返回`FALSE`（值 0），以获取这些参数值。  
  
 `FlushResultSet`调用 ODBC API 函数`SQLMoreResults`。 如果`SQLMoreResults`返回`SQL_ERROR`或`SQL_INVALID_HANDLE`，然后`FlushResultSet`将引发异常。 有关详细信息`SQLMoreResults`，请参阅 Windows SDK。  
  
 你的存储的过程需要具有绑定字段，如果你想要调用`FlushResultSet`。  
  
### <a name="example"></a>示例  
 下面的代码假定`COutParamRecordset`是`CRecordset`-派生的对象基于预定义的查询使用输入的参数和一个输出参数，并具有多个结果集。 请注意的结构[DoFieldExchange](#dofieldexchange)重写。  
  
 [!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]  
  
##  <a name="getbookmark"></a>CRecordset::GetBookmark  
 获取当前的记录的书签值。  
  
```  
void GetBookmark(CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>参数  
 `varBookmark`  
 对引用[CDBVariant](../../mfc/reference/cdbvariant-class.md)对象表示的当前记录的书签。  
  
### <a name="remarks"></a>备注  
 若要确定记录集是否支持书签，请调用[CanBookmark](#canbookmark)。 若要使书签可用，如果它们受支持，必须设置**CRecordset::useBookmarks**选项`dwOptions`参数[打开](#open)成员函数。  
  
> [!NOTE]
>  如果书签将变为不受支持或不可用，则调用`GetBookmark`将导致引发异常。 只进的记录集不支持书签。  
  
 `GetBookmark`将当前记录到的书签的值分配`CDBVariant`对象。 若要在将移动到另一条记录后随时返回到该记录，调用[SetBookmark](#setbookmark)具有相应`CDBVariant`对象。  
  
> [!NOTE]
>  某些记录集在操作后，书签可能不再有效。 例如，如果你调用`GetBookmark`跟**Requery**，你可能不能返回到的记录`SetBookmark`。 调用[CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)若要检查是否可以安全地调用`SetBookmark`。  
  
 有关书签和记录集导航的详细信息，请参阅文章[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
##  <a name="getdefaultconnect"></a>CRecordset::GetDefaultConnect  
 调用以获取默认连接字符串。  
  
```  
virtual CString GetDefaultConnect();
```  
  
### <a name="return-value"></a>返回值  
 A `CString` ，其中包含的默认连接字符串。  
  
### <a name="remarks"></a>备注  
 框架调用此成员函数以获取记录集所基于的数据源的默认连接字符串。 ClassWizard 通过标识用于在 ClassWizard 中获取有关表和列信息相同的数据源，为你实现此函数。 您可能会发现它方便地依赖于此开发你的应用程序时的默认连接。 但默认连接可能不适合于你的应用程序的用户。 如果是这种情况，应重新实现此函数，放弃 ClassWizard 的版本。 有关连接字符串的详细信息，请参阅文章[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)。  
  
##  <a name="getdefaultsql"></a>CRecordset::GetDefaultSQL  
 调用以获取要执行的默认 SQL 字符串。  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>返回值  
 A`CString`包含默认的 SQL 语句。  
  
### <a name="remarks"></a>备注  
 框架调用此成员函数可获取记录集所基于的默认 SQL 语句。 这可能是一个表名或 SQL**选择**语句。  
  
 间接通过声明与 ClassWizard，记录集类定义默认的 SQL 语句，ClassWizard 为你执行此任务。  
  
 如果你需要供自己使用的 SQL 语句字符串，调用`GetSQL`，它返回用于选择记录集的记录已打开状态时的 SQL 语句。 你可以编辑中的类的重写的默认 SQL 字符串`GetDefaultSQL`。 例如，可以指定对预定义的查询时使用的调用**调用**语句。 (请注意，但是，你编辑的如果`GetDefaultSQL`，还需要修改`m_nFields`以匹配的数据源中的列数。)  
  
 有关详细信息，请参阅文章[记录集： 声明一个类用于表 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。  
  
> [!CAUTION]
>  表名称将为空框架无法确定表名称，如果提供多个表名称，或者如果**调用**无法解释语句。 请注意，当使用**调用**语句，不能插入的大括号之间的空格和**调用**关键字，也应插入空格之前的大括号或之前不**选择**中的关键字**选择**语句。  
  
##  <a name="getfieldvalue"></a>CRecordset::GetFieldValue  
 检索对当前记录中的字段数据。  
  
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
 对引用[CDBVariant](../../mfc/reference/cdbvariant-class.md)将存储字段的值的对象。  
  
 `nFieldType`  
 字段的 ODBC C 数据类型。 使用默认值， **DEFAULT_FIELD_TYPE**，强制`GetFieldValue`根据下表来确定从 SQL 数据类型，C 数据类型。 否则，你可以在其中指定的数据直接键入或选择兼容的数据类型;例如，你可以存储任何数据类型属于**SQL_C_CHAR**。  
  
|C 数据类型|SQL 数据类型|  
|-----------------|-------------------|  
|**SQL_C_BIT**|**SQL_BIT**|  
|**SQL_C_UTINYINT**|**SQL_TINYINT**|  
|**SQL_C_SSHORT**|**SQL_SMALLINT**|  
|**SQL_C_SLONG**|**SQL_INTEGER**|  
|**SQL_C_FLOAT**|**SQL_REAL**|  
|**SQL_C_DOUBLE**|**SQL_FLOATSQL_DOUBLE**|  
|**SQL_C_TIMESTAMP**|**SQL_DATESQL_TIMESQL_TIMESTAMP**|  
|**SQL_C_CHAR**|**SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR**|  
|**SQL_C_BINARY**|**SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY**|  
  
 有关 ODBC 数据类型的详细信息，请参阅"SQL 数据类型"和"C 数据类型"的 Windows sdk 的附录 D 中的主题。  
  
 `nIndex`  
 字段的从零开始的索引。  
  
 `strValue`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)将存储字段的值的对象转换为文本，而不考虑该字段的数据类型。  
  
### <a name="remarks"></a>备注  
 你可以查找字段，按名称或索引。 你可以存储的字段值中任意一种`CDBVariant`对象或`CString`对象。  
  
 如果已实现批量行提取，当前记录始终位于在行集中的第一个记录。 若要使用`GetFieldValue`上给定的行集内的记录，你必须首先调用[SetRowsetCursorPosition](#setrowsetcursorposition)成员函数以将光标移到该行集内的所需行。 然后调用`GetFieldValue`该行。 若要实现批量行提取，必须指定`CRecordset::useMultiRowFetch`选项`dwOptions`中的参数[打开](#open)成员函数。  
  
 你可以使用`GetFieldValue`动态在运行的时，而不是在设计时静态绑定提取字段。 例如，如果您已声明直接从记录集对象`CRecordset`，必须使用`GetFieldValue`检索字段数据; 记录字段交换 (RFX) 或批量记录字段交换 (Bulk RFX)，未实现。  
  
> [!NOTE]
>  如果您声明一个记录集对象时不派生自`CRecordset`，没有 ODBC 游标库加载。 游标库要求记录集具有至少一个绑定的列;但是，当使用`CRecordset`直接，没有绑定任何列。 成员函数[CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex)和[CDatabase::Open](../../mfc/reference/cdatabase-class.md#open)控制是否将加载的是光标库。  
  
 `GetFieldValue`调用 ODBC API 函数**SQLGetData**。 如果您的驱动程序输出值**SQL_NO_TOTAL**字段值的实际长度`GetFieldValue`引发异常。 有关详细信息**SQLGetData**，请参阅 Windows SDK。  
  
### <a name="example"></a>示例  
 下面的示例代码演示如何调用`GetFieldValue`记录集对象声明直接从`CRecordset`。  
  
 [!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]  
  
> [!NOTE]
>  与 DAO 类不同`CDaoRecordset`，`CRecordset`没有`SetFieldValue`成员函数。 如果你从其创建对象直接`CRecordset`，它是有效地只读的。  
  
 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
##  <a name="getodbcfieldcount"></a>CRecordset::GetODBCFieldCount  
 检索的记录集对象中的字段的总数。  
  
```  
short GetODBCFieldCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 在记录集中的字段数。  
  
### <a name="remarks"></a>备注  
 有关创建记录集的详细信息，请参阅文章[记录集： 创建和关闭记录集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。  
  
##  <a name="getodbcfieldinfo"></a>CRecordset::GetODBCFieldInfo  
 获取有关在记录集中的字段的信息。  
  
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
 该函数的一个版本，可以按名称查找字段。 另一个版本中，可以按索引查找字段。  
  
 有关返回的信息的说明，请参阅[CODBCFieldInfo](../../mfc/reference/codbcfieldinfo-structure.md)结构。  
  
 有关创建记录集的详细信息，请参阅文章[记录集： 创建和关闭记录集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。  
  
##  <a name="getrecordcount"></a>CRecordset::GetRecordCount  
 确定记录集的大小。  
  
```  
long GetRecordCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 记录集; 中的记录数记录集不包含任何记录; 如果为 0如果无法确定的记录计数，-1。  
  
### <a name="remarks"></a>备注  
  
> [!CAUTION]
>  记录计数是保持为"高水位线，"最高编号记录，但出现在用户在记录间移动。 用户已经超过最后一条记录后，仅将已知的记录总数。 出于性能原因，将不更新计数在调用时`MoveLast`。 若要记录计数自己，调用`MoveNext`重复直到`IsEOF`返回非零值。 添加通过记录**CRecordset:AddNew**和**更新**的计数增加; 删除通过记录`CRecordset::Delete`减少计数。  
  
##  <a name="getrowsetsize"></a>CRecordset::GetRowsetSize  
 获取你想要在给定提取过程中检索的行数的当前设置。  
  
```  
DWORD GetRowsetSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 要在给定提取过程中检索的行数。  
  
### <a name="remarks"></a>备注  
 如果你将批量行提取，打开记录集时的默认行集大小为 25;否则，它为 1。  
  
 若要实现批量行提取，必须指定`CRecordset::useMultiRowFetch`选项`dwOptions`参数[打开](#open)成员函数。 若要更改的行集大小的设置，请调用[SetRowsetSize](#setrowsetsize)。  
  
 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
##  <a name="getrowsfetched"></a>CRecordset::GetRowsFetched  
 确定在提取后检索实际到多少条记录。  
  
```  
DWORD GetRowsFetched() const;  
```  
  
### <a name="return-value"></a>返回值  
 给定的获取之后从数据源检索的行数。  
  
### <a name="remarks"></a>备注  
 当你已实现批量行提取，这非常有用。 行集大小通常指示将从提取; 检索行数但是，在记录集中的行的总数也会影响将在行集中检索行数。 例如，如果你记录集具有行集大小设置为 4 的 10 个记录，然后遍历记录集通过调用`MoveNext`将导致具有仅 2 条记录的最后一个行集。  
  
 若要实现批量行提取，必须指定`CRecordset::useMultiRowFetch`选项`dwOptions`参数[打开](#open)成员函数。 若要指定行集大小，请调用[SetRowsetSize](#setrowsetsize)。  
  
 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]  
  
##  <a name="getrowstatus"></a>CRecordset::GetRowStatus  
 获取行集中的当前行的状态。  
  
```  
WORD GetRowStatus(WORD wRow) const;  
```  
  
### <a name="parameters"></a>参数  
 `wRow`  
 基于 1 中的位置的行的当前行集。 此值可以介于 1 到行集的大小。  
  
### <a name="return-value"></a>返回值  
 行状态值。 有关详细信息，请参阅“备注”。  
  
### <a name="remarks"></a>备注  
 `GetRowStatus`返回一个值，指示行的状态中的任一任何更改，自上次从数据源，或检索任何行对应于`wRow`提取了。 下表列出可能的返回值。  
  
|状态值|描述|  
|------------------|-----------------|  
|`SQL_ROW_SUCCESS`|行保持不变。|  
|`SQL_ROW_UPDATED`|行已被更新。|  
|`SQL_ROW_DELETED`|已删除该行。|  
|`SQL_ROW_ADDED`|已添加的行。|  
|`SQL_ROW_ERROR`|由于出错而检索行。|  
|`SQL_ROW_NOROW`|对应于没有行`wRow`。|  
  
 有关详细信息，请参阅 ODBC API 函数**SQLExtendedFetch** Windows SDK 中。  
  
##  <a name="getstatus"></a>CRecordset::GetStatus  
 确定记录集和是否已出现的最新记录中的当前记录的索引。  
  
```  
void GetStatus(CRecordsetStatus& rStatus) const;  
```  
  
### <a name="parameters"></a>参数  
 `rStatus`  
 对引用**CRecordsetStatus**对象。 有关详细信息，请参阅备注部分。  
  
### <a name="remarks"></a>备注  
 `CRecordset`尝试跟踪索引，但在某些情况下这可能不可行。 请参阅[GetRecordCount](#getrecordcount)有关说明。  
  
 **CRecordsetStatus**结构具有以下形式：  
  
 `struct CRecordsetStatus`  
  
 `{`  
  
 `long m_lCurrentRecord;`  
  
 `BOOL m_bRecordCountFinal;`  
  
 `};`  
  
 两个成员**CRecordsetStatus**具有以下含义：  
  
- **m_lCurrentRecord**如果已知包含记录集中的当前记录的从零开始索引。 如果无法确定索引，此成员包含**AFX_CURRENT_RECORD_UNDEFINED** (-2)。 如果`IsBOF`是**TRUE** （空记录集或尝试在第一条记录之前向下滚动），然后**m_lCurrentRecord**设置为**AFX_CURRENT_RECORD_BOF** (-1)。 如果在第一个记录，则它设置为 0，第二个记录 1，依次类推。  
  
- **m_bRecordCountFinal** Nonzero 如果已确定的记录集内的记录总数。 这通常必须实现通过记录集的开始处启动并调用`MoveNext`直到`IsEOF`返回非零值。 此成员为零，如果记录计数返回`GetRecordCount`，如果不为-1，是仅记录的"高水位线"计数。  
  
##  <a name="getsql"></a>CRecordset::GetSQL  
 调用此成员函数可获取用于选择记录集的记录已打开状态时的 SQL 语句。  
  
```  
const CString& GetSQL() const;  
```  
  
### <a name="return-value"></a>返回值  
 A **const**引用`CString`包含 SQL 语句。  
  
### <a name="remarks"></a>备注  
 通常，这将是 SQL**选择**语句。 返回的字符串`GetSQL`是只读的。  
  
 返回的字符串`GetSQL`通常不同于你可能会传递到记录集在任何字符串`lpszSQL`参数**打开**成员函数。 这是因为该记录集构造一个完整的 SQL 语句，基于传递给**打开**，ClassWizard，你可能具有指定的内容中与指定的内容**m_strFilter**和`m_strSort`数据成员，并且你可能已指定任何参数。 有关记录集如何构造此 SQL 语句中，有关详细信息，请参阅文章[记录集： 如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。  
  
> [!NOTE]
>  在调用后才调用此成员函数[打开](#open)。  
  
##  <a name="gettablename"></a>CRecordset::GetTableName  
 获取记录集的查询所基于的 SQL 表的名称。  
  
```  
const CString& GetTableName() const;  
```  
  
### <a name="return-value"></a>返回值  
 A **const**引用`CString`包含表的名称，如果记录集是根据一个表; 否则为空字符串。  
  
### <a name="remarks"></a>备注  
 `GetTableName`仅当才有效记录集基于表，不是联接的多个表或预定义的查询 （存储过程）。 名称是只读的。  
  
> [!NOTE]
>  在调用后才调用此成员函数[打开](#open)。  
  
##  <a name="isbof"></a>CRecordset::IsBOF  
 返回非零，如果在第一条记录之前定位位置记录集。 没有最新记录。  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果记录集不包含任何记录，或具有第一个记录; 之前向后滚动否则为 0。  
  
### <a name="remarks"></a>备注  
 从记录滚动到记录以了解是否你进入之前记录集的第一条记录之前，请调用此成员函数。 你还可以使用`IsBOF`连同`IsEOF`来确定记录集是否包含任何记录，或为空。 立即调用后**打开**，如果记录集不包含任何记录，`IsBOF`返回非零值。打开一个包含至少一个记录记录集时，第一条记录是当前记录和`IsBOF`返回 0。  
  
 如果第一条记录的当前记录，并且你调用`MovePrev`，`IsBOF`随后将返回非零值。 如果`IsBOF`返回非零，并且你调用`MovePrev`，发生错误。 如果`IsBOF`返回非零，当前记录是不确定，并需要当前记录的任何操作将导致错误。  
  
### <a name="example"></a>示例  
 此示例使用`IsBOF`和`IsEOF`来检测记录集的限制，如代码滚动中两个方向的记录集。  
  
 [!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]  
  
##  <a name="isdeleted"></a>CRecordset::IsDeleted  
 确定当前记录是否已被删除。  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>返回值  
 记录集放在已删除的记录; 如果非零否则为 0。  
  
### <a name="remarks"></a>备注  
 如果到一条记录滚动和`IsDeleted`返回**TRUE** （非零），然后你必须向下滚动到另一个记录才能执行记录集的任何其他操作。  
  
 结果`IsDeleted`取决于许多因素，如你记录集的类型，是否你指定是否可以更新，你的记录集**CRecordset::skipDeletedRecords**选项时是否打开记录集，你驱动程序包已删除的记录，以及是否有多个用户。  
  
 有关详细信息**CRecordset::skipDeletedRecords**和驱动程序封装，请参阅[打开](#open)成员函数。  
  
> [!NOTE]
>  如果已实现批量行提取，不应调用`IsDeleted`。 而应调用[GetRowStatus](#getrowstatus)成员函数。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
##  <a name="iseof"></a>CRecordset::IsEOF  
 返回非零，如果在最后一条记录后定位位置记录集。 没有最新记录。  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果记录集不包含任何记录，或已超出最后一条记录; 滚动否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此成员函数，如从记录滚动到记录以了解是否你已超出最后一个记录集的记录。 你还可以使用`IsEOF`来确定记录集是否包含任何记录，或为空。 立即调用后**打开**，如果记录集不包含任何记录，`IsEOF`返回非零值。 打开一个包含至少一个记录记录集时，第一条记录是当前记录和`IsEOF`返回 0。  
  
 在调用时如果最后一条记录是当前记录`MoveNext`，`IsEOF`随后将返回非零值。 如果`IsEOF`返回非零，并且你调用`MoveNext`，发生错误。 如果`IsEOF`返回非零，当前记录是不确定，并需要当前记录的任何操作将导致错误。  
  
### <a name="example"></a>示例  
 请参阅示例[IsBOF](#isbof)。  
  
##  <a name="isfielddirty"></a>CRecordset::IsFieldDirty  
 确定指定的字段数据成员是否已更改自[编辑](#edit)或[AddNew](#addnew)调用。  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 指向字段数据成员你想要检查，其状态的指针或**NULL**以确定其中任何一个字段是否已更新。  
  
### <a name="return-value"></a>返回值  
 非零，如果指定的字段数据成员自从调用`AddNew`或**编辑**; 否则为 0。  
  
### <a name="remarks"></a>备注  
 所有已更新字段数据成员中的数据将传输到记录在数据源上的当前记录更新通过调用时[更新](#update)成员函数`CRecordset`(到调用**编辑**或`AddNew`)。  
  
> [!NOTE]
>  此成员函数不是适用于使用的批量行提取的记录集。 如果已实现批量行提取，然后`IsFieldDirty`将始终返回**FALSE** ，将导致失败的断言。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
 调用`IsFieldDirty`将重置的以前调用的效果[SetFieldDirty](#setfielddirty)由于字段的更新状态会重新评估。 在`AddNew`情况下，如果当前的字段值的伪 null 值不同，字段状态设置已更新。 在**编辑**种情况下，如果字段值不同的缓存值，则字段状态设置已更新。  
  
 `IsFieldDirty`通过实现[DoFieldExchange](#dofieldexchange)。  
  
 已更新标志的详细信息，请参阅文章[记录集： 如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。  
  
##  <a name="isfieldnull"></a>CRecordset::IsFieldNull  
 返回非零，如果当前记录中的指定的字段为 Null （具有任何值）。  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 指向字段数据成员你想要检查，其状态的指针或**NULL**以确定其中任何一个字段是否为 Null。  
  
### <a name="return-value"></a>返回值  
 如果指定的字段数据成员标记为 Null; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此成员函数来确定记录集的指定的字段数据成员是否已标记为 Null。 (在数据库术语中，Null 表示"having 没有值"，并且不能与相同**NULL** c + + 中。)如果字段数据成员标记为 Null，则将它解释为没有值的当前记录的列。  
  
> [!NOTE]
>  此成员函数不是适用于使用的批量行提取的记录集。 如果已实现批量行提取，然后`IsFieldNull`将始终返回**FALSE** ，将导致失败的断言。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
 `IsFieldNull`通过实现[DoFieldExchange](#dofieldexchange)。  
  
##  <a name="isfieldnullable"></a>CRecordset::IsFieldNullable  
 返回非零，如果当前记录中的指定的字段可以设置为 Null （无任何值）。  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 指向字段数据成员你想要检查，其状态的指针或**NULL**以确定其中任何一个字段可以为 Null 值进行设置。  
  
### <a name="remarks"></a>备注  
 调用以确定是否可以指定的字段数据成员为"null"（可以是设置为一个 Null 值; 如果该成员函数C + + **NULL**不同时，则为 Null，这在数据库术语中，意味着"having 没有值")。  
  
> [!NOTE]
>  如果你已实现批量行提取，则无法调用`IsFieldNullable`。 而应调用[GetODBCFieldInfo](#getodbcfieldinfo)成员函数来确定是否可将字段设置为 Null 值。 请注意，始终可以调用`GetODBCFieldInfo`，不管是否已实现批量行提取。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
 不能为 Null 的字段必须具有一个值。 如果你尝试将此类字段设置为 Null 添加或更新记录时，数据源拒绝添加或更新，和[更新](#update)将引发异常。 在调用时，则会发生异常**更新**，在调用时不[SetFieldNull](#setfieldnull)。  
  
 使用**NULL**为函数的第一个参数将该函数仅适用于**outputColumn**字段，不**param**字段。 例如，调用  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 将仅设置**outputColumn**字段设置为**NULL**;**param**字段不会受到影响。  
  
 若要在**param**字段，你必须提供个人的实际地址**param**你想要使用，如：  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 这意味着您不能设置所有**param**字段设置为**NULL**，如可以按照与**outputColumn**字段。  
  
 `IsFieldNullable`通过实现[DoFieldExchange](#dofieldexchange)。  
  
##  <a name="isopen"></a>CRecordset::IsOpen  
 确定记录集是否已打开。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零如果记录集对象的[打开](#open)或[Requery](#requery)以前调用成员函数和记录集未被关闭; 否则为 0。  
  
##  <a name="m_hstmt"></a>CRecordset::m_hstmt  
 包含 ODBC 语句数据结构的类型的句柄**HSTMT**、 与记录集相关联。  
  
### <a name="remarks"></a>备注  
 与关联到 ODBC 数据源的每个查询**HSTMT**。  
  
> [!CAUTION]
>  不要使用**m_hstmt**之前[打开](#open)已调用。  
  
 通常不需要访问**HSTMT**直接，但你可能需要它，直接执行 SQL 语句。 `ExecuteSQL`类的成员函数`CDatabase`举例说明使用**m_hstmt**。  
  
##  <a name="m_nfields"></a>CRecordset::m_nFields  
 包含在记录集类; 中的字段数据成员的数目即，选定数据源的记录集的列数。  
  
### <a name="remarks"></a>备注  
 记录集类的构造函数必须初始化`m_nFields`与正确的数目。 如果不已实现批量行提取，ClassWizard 将写入此初始化时，当你使用它来声明你记录集的类。 你还可以编写它手动。  
  
 框架将使用此数字管理字段数据成员与数据源上的当前记录的相应列之间的交互。  
  
> [!CAUTION]
>  此数字必须与对应的"输出列"中注册数`DoFieldExchange`或`DoBulkFieldExchange`后调用[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)与参数**CFieldExchange::outputColumn**。  
  
 你可以在文章中所述动态绑定列"记录集： 动态绑定数据列。" 如果这样做，则必须增加中的计数`m_nFields`以反映调用 RFX 或批量 RFX 函数次数你`DoFieldExchange`或`DoBulkFieldExchange`对于动态绑定列的成员函数。  
  
 有关详细信息，请参阅文章[记录集： 动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)和[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>示例  
 请参阅文章[记录字段交换： 使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。  
  
##  <a name="m_nparams"></a>CRecordset::m_nParams  
 包含在记录集类; 中的参数数据成员的数目即与记录集的查询一起传递的参数数目。  
  
### <a name="remarks"></a>备注  
 如果你记录集的类具有任何参数数据成员，必须初始化类的构造函数`m_nParams`与正确的数目。 值`m_nParams`默认值为 0。 如果添加参数数据成员 （这必须手动执行） 必须在类构造函数，以反映参数的数目也手动添加初始化 (它必须是至少一样大的数字的形式 ' 中的占位符你**m_strFilter**或`m_strSort`字符串)。  
  
 它对参数化记录集的查询时，框架将使用此数字。  
  
> [!CAUTION]
>  此数字必须与对应"params"中注册的数`DoFieldExchange`或`DoBulkFieldExchange`后调用[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)参数值为**CFieldExchange::inputParam**， **CFieldExchange::param**， **CFieldExchange::outputParam**，或**CFieldExchange::inoutParam**。  
  
### <a name="example"></a>示例  
  请参阅文章[记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)和[记录字段交换： 使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。  
  
##  <a name="m_pdatabase"></a>CRecordset::m_pDatabase  
 包含指向的`CDatabase`通过该记录集连接到数据源的对象。  
  
### <a name="remarks"></a>备注  
 两种方式设置此变量。 通常情况下，将指针传递到已连接`CDatabase`对象构造记录集对象时。 如果你通过**NULL**相反，`CRecordset`创建`CDatabase`你对象并将其连接。 在任一情况下，`CRecordset`将指针存储在此变量。  
  
 通常不直接需要使用存储在指针**m_pDatabase**。 如果你编写自己的扩展到`CRecordset`，但是，你可能需要使用该指针。 例如，你可能需要指针如果引发了自己`CDBException`s。 你可能需要它，如果你需要做些什么使用相同或者`CDatabase`对象，如运行的事务，设置超时，或调用`ExecuteSQL`类的成员函数`CDatabase`直接执行 SQL 语句。  
  
##  <a name="m_strfilter"></a>CRecordset::m_strFilter  
 在构造的记录集对象之后，但你在调用之前其**打开**成员函数，使用此数据成员来存储`CString`包含 SQL**其中**子句。  
  
### <a name="remarks"></a>备注  
 记录集使用此字符串来约束 （或筛选器） 期间它选择的记录**打开**或**Requery**调用。 这可用于选择记录，如"加利福尼亚州基于所有销售人员"的子集 ("状态 = CA")。 ODBC SQL 语法**其中**子句  
  
 `WHERE search-condition`  
  
 请注意，不包括**其中**在字符串中的关键字。 框架提供了它。  
  
 此外可以参数筛选器字符串化放置 ' 中，为每个占位符，声明你的类中的参数数据成员并将参数传递给在记录集的占位符运行时间。 这使你在运行时构造筛选器。 有关详细信息，请参阅文章[记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
 有关 SQL**其中**子句，请参阅文章[SQL](../../data/odbc/sql.md)。 有关选择和筛选的记录的详细信息，请参阅文章[记录集： 筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]  
  
##  <a name="m_strsort"></a>CRecordset::m_strSort  
 在构造的记录集对象之后，但你在调用之前其**打开**成员函数，使用此数据成员来存储`CString`包含 SQL **ORDER BY**子句。  
  
### <a name="remarks"></a>备注  
 记录集使用此字符串排序期间它选择的记录**打开**或**Requery**调用。 此功能可用于对一个或多个列上的记录集进行排序。 ODBC SQL 语法**ORDER BY**子句  
  
 `ORDER BY sort-specification [, sort-specification]...`  
  
 其中排序规范是一个整数或列名称。 你还可以通过将"ASC"或"DESC"追加到排序字符串中的列列表中指定 （默认情况下，顺序为升序） 的升序或降序顺序。 选择的记录排在前面通过第一列列出，然后通过第二个，依次类推。 例如，你可能订购"客户"记录集的最后一个名称，则第一个名称。 你可以列出的列数取决于数据源。 有关详细信息，请参阅 Windows SDK。  
  
 请注意，不包括**ORDER BY**在字符串中的关键字。 框架提供了它。  
  
 有关 SQL 子句的详细信息，请参阅文章[SQL](../../data/odbc/sql.md)。 有关对记录进行排序的详细信息，请参阅文章[记录集： 排序记录 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]  
  
##  <a name="move"></a>CRecordset::Move  
 将当前记录指针集中的记录，向前或向后移动。  
  
```  
virtual void Move(
    long nRows,  
    WORD wFetchType = SQL_FETCH_RELATIVE);
```  
  
### <a name="parameters"></a>参数  
 `nRows`  
 要向前或向后移动的行数。 正值表示向前，移动记录集的一端。 值为负时，开始向后移动。  
  
 `wFetchType`  
 确定行集的**移动**将提取。 有关详细信息，请参阅“备注”。  
  
### <a name="remarks"></a>备注  
 如果传递的值为 0 `nRows`，**移动**刷新当前记录;**移动**将结束任何当前`AddNew`或**编辑**模式，并且将还原之前的当前记录的值`AddNew`或**编辑**调用。  
  
> [!NOTE]
>  记录集中移动时，不能跳过已删除的记录。 请参阅[CRecordset::IsDeleted](#isdeleted)有关详细信息。 当你打开`CRecordset`与**skipDeletedRecords**选项集，**移动**断言如果`nRows`参数为 0。 此行为会阻止其他客户端使用的应用程序相同的数据删除的行的刷新。 请参阅`dwOption`中的参数[打开](#open)有关的说明**skipDeletedRecords**。  
  
 **移动**按行集重新定位记录集。 基于值的`nRows`和`wFetchType`，**移动**提取相应的行集，然后将第一条记录在该行集的当前记录。 如果你不具有实现批量行提取，然后行集大小始终为 1。 在提取行集时**移动**直接调用[CheckRowsetError](#checkrowseterror)成员函数以处理导致提取任何错误。  
  
 具体取决于您传递的值**移动**等效于其他`CRecordset`成员函数。 具体而言，值`wFetchType`可能表示一个成员函数，则更直观，通常用于移动当前记录的首选的方法。  
  
 下表列出的可能值`wFetchType`，行集的**移动**将提取基于`wFetchType`和`nRows`，对应于任何等效成员函数`wFetchType`。  
  
|wFetchType|提取行集|等效成员函数|  
|----------------|--------------------|--------------------------------|  
|`SQL_FETCH_RELATIVE`（默认值）|行集起始`nRows`从当前行集中的第一行的行。||  
|`SQL_FETCH_NEXT`|下一步的行集;`nRows`将被忽略。|[MoveNext](#movenext)|  
|`SQL_FETCH_PRIOR`|以前的行集;`nRows`将被忽略。|[MovePrev](#moveprev)|  
|`SQL_FETCH_FIRST`|在记录集中; 第一个行集`nRows`将被忽略。|[MoveFirst](#movefirst)|  
|`SQL_FETCH_LAST`|在记录集中; 最后一个的整个行集`nRows`将被忽略。|[MoveLast](#movelast)|  
|`SQL_FETCH_ABSOLUTE`|如果`nRows`> 0，开始的行集`nRows`从开始处的记录集的行。 如果`nRows`< 0，开始的行集`nRows`从记录集的结尾的行。 如果`nRows`= 0，则返回一个开头的文件 (BOF) 条件。|[SetAbsolutePosition](#setabsoluteposition)|  
|`SQL_FETCH_BOOKMARK`|从其书签值对应于行开始的行集`nRows`。|[SetBookmark](#setbookmark)|  
  
> [!NOTE]
>  对于只进记录集**移动**才有效，且值为`SQL_FETCH_NEXT`为`wFetchType`。  
  
> [!CAUTION]
>  调用**移动**记录集是否没有记录，将引发异常。 若要确定记录集是否具有任何记录，请调用[IsBOF](#isbof)和[IsEOF](#iseof)。  
  
> [!NOTE]
>  如果你使用滚动条滚动过去的开头或末尾的记录集 (`IsBOF`或`IsEOF`返回非零)，则调用**移动**函数将可能引发`CDBException`。 例如，如果`IsEOF`返回非零和`IsBOF`不存在，然后`MoveNext`将引发异常，但`MovePrev`将不会。  
  
> [!NOTE]
>  如果调用**移动**时的当前记录正在更新或添加，更新都将丢失而不发出警告。  
  
 有关记录集导航的详细信息，请参阅文章[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。 有关相关信息，请参阅 ODBC API 函数**SQLExtendedFetch** Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]  
  
##  <a name="movefirst"></a>CRecordset::MoveFirst  
 使当前记录第一个行集的第一个记录。  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>备注  
 无论是否已实现批量行提取，这将始终为记录集中的第一条记录。  
  
 无需调用**MoveFirst**后立即打开记录集。 此时，第一条记录 （如果有） 将自动当前记录。  
  
> [!NOTE]
>  此成员函数仅向前的记录集无效。  
  
> [!NOTE]
>  记录集中移动时，不能跳过已删除的记录。 请参阅[IsDeleted](#isdeleted)有关详细信息的成员函数。  
  
> [!CAUTION]
>  调用的任何**移动**函数将引发异常，如果记录集不具有任何记录。 若要确定记录集是否具有任何记录，请调用`IsBOF`和`IsEOF`。  
  
> [!NOTE]
>  如果你调用任意**移动**函数时的当前记录正在更新或添加，更新都将丢失而不发出警告。  
  
 有关记录集导航的详细信息，请参阅文章[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
### <a name="example"></a>示例  
  请参阅示例[IsBOF](#isbof)。  
  
##  <a name="movelast"></a>CRecordset::MoveLast  
 使第一条记录中最后一个的整个行集的当前记录。  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>备注  
 如果不已实现批量行提取，记录集具有行集大小为 1，因此`MoveLast`只需移动到的最后记录的记录集。  
  
> [!NOTE]
>  此成员函数仅向前的记录集无效。  
  
> [!NOTE]
>  记录集中移动时，不能跳过已删除的记录。 请参阅[IsDeleted](#isdeleted)有关详细信息的成员函数。  
  
> [!CAUTION]
>  调用的任何**移动**函数将引发异常，如果记录集不具有任何记录。 若要确定记录集是否具有任何记录，请调用`IsBOF`和`IsEOF`。  
  
> [!NOTE]
>  如果你调用任意**移动**函数时的当前记录正在更新或添加，更新都将丢失而不发出警告。  
  
 有关记录集导航的详细信息，请参阅文章[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
### <a name="example"></a>示例  
  请参阅示例[IsBOF](#isbof)。  
  
##  <a name="movenext"></a>CRecordset::MoveNext  
 使第一条记录中的下一步的行集的当前记录。  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>备注  
 如果不已实现批量行提取，记录集具有行集大小为 1，因此`MoveNext`只需将其移到下一条记录。  
  
> [!NOTE]
>  记录集中移动时，不能跳过已删除的记录。 请参阅[IsDeleted](#isdeleted)有关详细信息的成员函数。  
  
> [!CAUTION]
>  调用的任何**移动**函数将引发异常，如果记录集不具有任何记录。 若要确定记录集是否具有任何记录，请调用`IsBOF`和`IsEOF`。  
  
> [!NOTE]
>  此外建议您调用`IsEOF`之前调用`MoveNext`。 例如，如果记录集，末尾具有滚动`IsEOF`将返回非零值; 的后续调用`MoveNext`会引发异常。  
  
> [!NOTE]
>  如果你调用任意**移动**函数时的当前记录正在更新或添加，更新都将丢失而不发出警告。  
  
 有关记录集导航的详细信息，请参阅文章[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
### <a name="example"></a>示例  
  请参阅示例[IsBOF](#isbof)。  
  
##  <a name="moveprev"></a>CRecordset::MovePrev  
 使第一条记录中以前的行集的当前记录。  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>备注  
 如果不已实现批量行提取，记录集具有行集大小为 1，因此`MovePrev`只需将其移到上一记录。  
  
> [!NOTE]
>  此成员函数仅向前的记录集无效。  
  
> [!NOTE]
>  记录集中移动时，不能跳过已删除的记录。 请参阅[IsDeleted](#isdeleted)有关详细信息的成员函数。  
  
> [!CAUTION]
>  调用的任何**移动**函数将引发异常，如果记录集不具有任何记录。 若要确定记录集是否具有任何记录，请调用`IsBOF`和`IsEOF`。  
  
> [!NOTE]
>  此外建议您调用`IsBOF`之前调用`MovePrev`。 例如，如果具有滚动记录集，开头`IsBOF`将返回非零值; 的后续调用`MovePrev`会引发异常。  
  
> [!NOTE]
>  如果你调用任意**移动**函数时的当前记录正在更新或添加，更新都将丢失而不发出警告。  
  
 有关记录集导航的详细信息，请参阅文章[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
### <a name="example"></a>示例  
  请参阅示例[IsBOF](#isbof)。  
  
##  <a name="onsetoptions"></a>CRecordset::OnSetOptions  
 设置选项 （在所选内容上使用） 为调用指定的 ODBC 语句。  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>参数  
 `hstmt`  
 **HSTMT**其选项，则设置的 ODBC 语句。  
  
### <a name="remarks"></a>备注  
 调用`OnSetOptions`对于指定的 ODBC 语句设置选项 （使用所选内容上）。 框架调用此成员函数可设置为记录集的初始选项。 `OnSetOptions`确定数据源的支持可滚动游标和游标并发并相应地设置记录集的选项。 (而`OnSetOptions`用于选择操作，`OnSetUpdateOptions`用于更新操作。)  
  
 重写`OnSetOptions`设置特定于驱动程序或数据源的选项。 例如，如果你的数据源支持打开要执行的独占访问权，你可能会替代`OnSetOptions`即可利用该功能。  
  
 有关游标的详细信息，请参阅文章[ODBC](../../data/odbc/odbc-basics.md)。  
  
##  <a name="onsetupdateoptions"></a>CRecordset::OnSetUpdateOptions  
 调用以设置指定的 ODBC 语句 （在更新使用） 的选项。  
  
```  
virtual void OnSetUpdateOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>参数  
 `hstmt`  
 **HSTMT**其选项，则设置的 ODBC 语句。  
  
### <a name="remarks"></a>备注  
 调用`OnSetUpdateOptions`对于指定的 ODBC 语句设置选项 （使用更新）。 创建 HSTMT 以更新在记录集中的记录后，框架将调用此成员函数。 (而`OnSetOptions`用于选择操作，`OnSetUpdateOptions`用于更新操作。)`OnSetUpdateOptions`确定数据源的支持可滚动游标和游标并发并相应地设置记录集的选项。  
  
 重写`OnSetUpdateOptions`该语句用于访问数据库之前设置的 ODBC 语句的选项。  
  
 有关游标的详细信息，请参阅文章[ODBC](../../data/odbc/odbc-basics.md)。  
  
##  <a name="open"></a>CRecordset::Open  
 通过检索表或执行查询记录集表示打开记录集。  
  
```  
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,  
    LPCTSTR lpszSQL = NULL,  
    DWORD dwOptions = none);
```  
  
### <a name="parameters"></a>参数  
 `nOpenType`  
 接受默认值， **AFX_DB_USE_DEFAULT_TYPE**，或使用以下项之一中的值**枚举 OpenType**:  
  
- **CRecordset::dynaset**具有双向滚动的记录集。 打开记录集，但由其他用户对数据值进行的更改处于可见提取操作之后确定的成员身份以及排序的记录。 动态集也被称为键集驱动的记录集。  
  
- **CRecordset::snapshot**具有双向滚动的静态记录集。 打开记录集; 时确定的成员身份以及记录的排序提取记录时确定的数据值。 后，关闭，然后重新打开记录集，其他用户所做的更改不可见。  
  
- **CRecordset::dynamic**具有双向滚动的记录集。 由其他用户对成员资格、 排序和数据值进行的更改都可见下列提取操作。 请注意，许多 ODBC 驱动程序不支持这种类型的记录集。  
  
- **CRecordset::forwardOnly**的只读的记录集包含仅向前滚动。  
  
     有关`CRecordset`，默认值是**CRecordset::snapshot**。 默认值机制允许 Visual c + + 向导与这两个 ODBC 进行交互`CRecordset`和 DAO `CDaoRecordset`，它具有不同的默认值。  
  
 有关这些记录集类型的详细信息，请参阅文章[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)。 有关相关信息，请参阅文章"使用块和可滚动游标"在 Windows SDK 中。  
  
> [!CAUTION]
>  如果不支持所请求的类型，则框架将引发异常。  
  
 `lpszSQL`  
 字符串指针，包含以下项之一：  
  
-   A **NULL**指针。  
  
-   表的名称。  
  
-   SQL**选择**语句 (根据需要使用 SQL**其中**或**ORDER BY**子句)。  
  
-   A**调用**语句并指定预定义的查询 （存储过程） 的名称。 请注意不要插入的大括号之间的空格和**调用**关键字。  
  
 有关此字符串的详细信息，请参阅表和讨论的备注 ClassWizard 的角色。  
  
> [!NOTE]
>  结果集中的列的顺序必须匹配 RFX 的顺序或批量 RFX 函数调用你[DoFieldExchange](#dofieldexchange)或[DoBulkFieldExchange](#dobulkfieldexchange)函数重写。  
  
 `dwOptions`  
 一个位屏蔽，可以指定下面列出的值的组合。 其中的某些类是互斥的。 默认值是**无**。  
  
- **CRecordset::none**无需选项进行设置。 此参数值是与所有其他值互斥。 默认情况下，可以使用更新记录集[编辑](#edit)或[删除](#delete)，并允许追加新记录与[AddNew](#addnew)。 可更新性取决于数据源以及上`nOpenType`选项，你指定。 批量添加适用于优化不可用。 不会实现批量行提取。 已删除的记录不能跳过在记录集导航过程。 书签将不可用。 检查自动已更新的字段被实现。  
  
- **CRecordset::appendOnly**不允许**编辑**或**删除**对记录集。 允许`AddNew`仅。 此选项是与互斥**CRecordset::readOnly**。  
  
- **CRecordset::readOnly**打开记录集持久化为只读的。 此选项是与互斥**CRecordset::appendOnly**。  
  
- **CRecordset::optimizeBulkAdd**已准备的 SQL 语句用于优化一次添加多个记录。 仅适用于未使用 ODBC API 函数**SQLSetPos**更新记录集。 第一个更新确定哪些字段标记为已更新。 此选项是与互斥`CRecordset::useMultiRowFetch`。  
  
- `CRecordset::useMultiRowFetch`实现批量行提取，若要允许多个要在单个提取操作中检索的行。 这是一项高级的功能能够提高性能;但是，ClassWizard 不支持批量记录字段交换。 此选项是与互斥**CRecordset::optimizeBulkAdd**。 请注意，如果你指定`CRecordset::useMultiRowFetch`，然后选项**CRecordset::noDirtyFieldCheck**将自动开启 （双缓冲将不可用）; 在只进记录集中，选项**CRecordset::useExtendedFetch**将自动打开。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
- **CRecordset::skipDeletedRecords**浏览记录集时跳过所有已删除的记录。 这将会在某些相对提取中的性能变慢。 此选项仅向前的记录集上无效。 如果调用[移动](#move)与`nRows`参数设置为 0，和**CRecordset::skipDeletedRecords**选项集，**移动**将断言。 请注意， **CRecordset::skipDeletedRecords**类似于*驱动程序封装*，这意味着，已删除的行已从记录集。 但是，如果您的驱动程序包记录，然后它将跳过删除; 的那些记录它不会跳过该记录集处于打开状态时，由其他用户删除的记录。 **CRecordset::skipDeletedRecords**将跳过由其他用户删除的行。  
  
- **CRecordset::useBookmarks**记录集，如果支持，可以对其使用书签。 书签降低数据检索，但提高数据导航的性能。 在只进的记录集上无效。 有关详细信息，请参阅文章[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。  
  
- **CRecordset::noDirtyFieldCheck**关闭自动已更新的字段检查 （双缓冲）。 这将提高性能;但是，你必须手动将标记字段为脏通过调用`SetFieldDirty`和`SetFieldNull`成员函数。请注意类中该双缓冲`CRecordset`类似于类中的双缓冲`CDaoRecordset`。 但是，在`CRecordset`，你不能启用针对单个字段的双缓冲; 所有字段都启用或禁用的所有字段。 请注意，如果指定了选项`CRecordset::useMultiRowFetch`，然后**CRecordset::noDirtyFieldCheck**自动; 但是，将开启`SetFieldDirty`和`SetFieldNull`不能用于实现批量行提取的记录集。  
  
- **CRecordset::executeDirect**不使用已准备的 SQL 语句。 为提高性能，将此选项指定如果**Requery**绝不会调用成员函数。  
  
- **CRecordset::useExtendedFetch**实现**SQLExtendedFetch**而不是**SQLFetch**。 这旨在用于实现批量行提取的只进的记录集。 如果指定了选项`CRecordset::useMultiRowFetch`上只进记录集，然后**CRecordset::useExtendedFetch**将自动打开。  
  
- **CRecordset::userAllocMultiRowBuffers**用户将为数据分配存储缓冲区。 使用此选项结合`CRecordset::useMultiRowFetch`如果你想要分配你自己的存储; 否则，框架将自动分配必要的存储区。 有关详细信息，请参阅文章[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 请注意该指定**CRecordset::userAllocMultiRowBuffers**而无需指定`CRecordset::useMultiRowFetch`将导致失败的断言。  
  
### <a name="return-value"></a>返回值  
 非零如果`CRecordset`对象已成功打开; 否则为 0 如果[CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) （如果称为），则返回 0。  
  
### <a name="remarks"></a>备注  
 必须调用该成员函数以运行由记录集定义的查询。 之前调用**打开**，您必须先构造的记录集对象。  
  
 该记录集连接到数据源取决于如何构造之前调用的记录集**打开**。 如果你通过[CDatabase](../../mfc/reference/cdatabase-class.md)对象尚未连接到数据源的记录集构造函数使用此成员函数[GetDefaultConnect](#getdefaultconnect)尝试打开的数据库对象。 如果你通过**NULL**到记录集构造函数中，构造函数将构造`CDatabase`为你的对象和**打开**尝试连接的数据库对象。 有关关闭记录集并在这些不同的情况下连接的详细信息，请参阅[关闭](#close)。  
  
> [!NOTE]
>  对通过数据源的访问`CRecordset`始终共享对象。 与不同`CDaoRecordset`类，不能用于`CRecordset`要使用的独占访问权打开数据源对象。  
  
 当调用**打开**，一个查询，通常 SQL**选择**语句中，选择根据下表中所示的条件的记录。  
  
|LpszSQL 参数值|由确定所选记录|示例|  
|------------------------------------|----------------------------------------|-------------|  
|**NULL**|返回的字符串`GetDefaultSQL`。||  
|SQL 表名称|中的表列表中的所有列`DoFieldExchange`或`DoBulkFieldExchange`。|`"Customer"`|  
|预定义的查询 （存储过程） 名称|查询定义要返回的列。|`"{call OverDueAccts}"`|  
|**选择**列列表**FROM**表列表|指定表中的指定的列。|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|  
  
> [!CAUTION]
>  请注意，执行 SQL 字符串中插入额外的空白。 例如，如果插入的大括号之间的空格和**调用**关键字，MFC 将错误解释为的表名的 SQL 字符串并将其到合并**选择**语句，这将导致所引发的异常。 同样，如果你预定义的查询使用输出参数，不能插入的大括号之间的空格和 ' 符号。 最后，你不能插入之前的大括号中的空白**调用**语句或之前**选择**中的关键字**选择**语句。  
  
 常规步骤是将传递**NULL**到**打开**; 在这种情况下，**打开**调用[GetDefaultSQL](#getdefaultsql)。 如果你使用派生`CRecordset`类， **GetDefaultSQL**提供你在 ClassWizard 中指定的表名称。 您可以指定中的其他信息`lpszSQL`参数。  
  
 你传递的任何**打开**构造查询的最终 SQL 字符串 (字符串可能具有 SQL**其中**和**ORDER BY**子句追加到`lpszSQL`字符串传入） 和执行该查询。 你可以通过调用检查构造的字符串[GetSQL](#getsql)之后调用**打开**。 有关如何记录集构造 SQL 语句，并选择记录，有关其他详细信息，请参阅文章[记录集： 如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。  
  
 记录集类的字段数据成员将绑定到所选的数据的列。 如果返回任何记录，第一条记录成为当前记录。  
  
 如果你想要设置为记录集，筛选器或排序，如选项指定这些属性构造记录集对象之后但在调用之前**打开**。 如果你想要刷新的记录后记录集中的记录集已打开，请调用[Requery](#requery)。  
  
 有关详细信息，包括其他示例，请参阅文章[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)，[记录集： 如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)，和[记录集： 创建和关闭记录集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。  
  
### <a name="example"></a>示例  
 下面的代码示例演示不同形式的**打开**调用。  
  
 [!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]  
  
##  <a name="refreshrowset"></a>CRecordset::RefreshRowset  
 更新数据和行集中的当前行的状态。  
  
```  
void RefreshRowset(
    WORD wRow,  
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>参数  
 `wRow`  
 基于 1 中的位置的行的当前行集。 此值可介于 0 到行集的大小。  
  
 `wLockType`  
 一个值，该值指示如何刷新它之后锁定该行。 有关详细信息，请参阅“备注”。  
  
### <a name="remarks"></a>备注  
 如果通过值为零`wRow`，然后将刷新每个行集中的行。  
  
 若要使用`RefreshRowset`，你必须已实现批量行提取，通过指定**CRecordset::useMulitRowFetch**选项[打开](#open)成员函数。  
  
 `RefreshRowset`调用 ODBC API 函数**SQLSetPos**。 `wLockType`参数指定后的行的锁定状态**SQLSetPos**已执行。 下表描述的可能值`wLockType`。  
  
|wLockType|描述|  
|---------------|-----------------|  
|`SQL_LOCK_NO_CHANGE`（默认值）|驱动程序或数据源可确保之前行处于相同的锁定或解锁状态`RefreshRowset`调用。|  
|`SQL_LOCK_EXCLUSIVE`|驱动程序或数据源以独占方式锁定行。 并非所有数据源都支持这种类型的锁定。|  
|`SQL_LOCK_UNLOCK`|驱动程序或数据源解除锁定行。 并非所有数据源都支持这种类型的锁定。|  
  
 有关详细信息**SQLSetPos**，请参阅 Windows SDK。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
##  <a name="requery"></a>CRecordset::Requery  
 重新生成 （刷新） 记录集。  
  
```  
virtual BOOL Requery();
```  
  
### <a name="return-value"></a>返回值  
 如果已成功重建记录集; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 如果返回任何记录，第一条记录成为当前记录。  
  
 为了使为反映的添加和删除您或其他用户对数据源的记录集，必须重新记录集生成通过调用**Requery**。 如果记录集是动态集，它会自动反映你或其他用户对其现有记录 （但不是添加件） 进行的更新。 如果记录集是快照，则必须调用**Requery**以反映编辑由其他用户，以及添加和删除。  
  
 对于动态集或快照中，调用**Requery**任何你想要重新生成使用新的筛选器或排序或新的参数值的记录集的时间。 通过将新值赋给将新的筛选器或排序属性设置**m_strFilter**和`m_strSort`之前调用**Requery**。 通过将新值分配给之前调用的参数数据成员设置新的参数**Requery**。 如果筛选器和排序字符串未更改，你可以重用查询，这将提高性能。  
  
 如果重新生成该记录集的尝试失败，已关闭记录集。 在调用之前**Requery**，你可以确定是否可以通过调用重新记录集的查询`CanRestart`成员函数。 `CanRestart`不能保证**Requery**将会成功。  
  
> [!CAUTION]
>  调用**Requery**仅具有调用后[打开](#open)。  
  
### <a name="example"></a>示例  
 此示例重新生成一个记录集应用不同的排序顺序。  
  
 [!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]  
  
##  <a name="setabsoluteposition"></a>CRecordset::SetAbsolutePosition  
 定位上与指定的记录号相对应的记录，记录集。  
  
```  
void SetAbsolutePosition(long nRows);
```  
  
### <a name="parameters"></a>参数  
 `nRows`  
 基于 1 的序号位置的当前记录的记录集。  
  
### <a name="remarks"></a>备注  
 `SetAbsolutePosition`将当前记录指针基于此序号位置。  
  
> [!NOTE]
>  此成员函数上仅向前的记录集无效。  
  
 对于 ODBC 记录集的绝对位置设置为 1 是指记录集; 中的第一个记录设置为 0 是指开头的文件 (BOF) 位置。  
  
 你还可以传递到负值`SetAbsolutePosition`。 在这种情况下记录集的位置计算从记录集的末尾。 例如，`SetAbsolutePosition( -1 )`将当前记录指针移到记录集的最后一个记录。  
  
> [!NOTE]
>  绝对位置不应作为代理项记录编号。 书签仍将保留并返回到给定的位置，因为记录的位置更改时将删除前面记录的推荐的方法。 此外，则不能确保给定的记录将具有相同的绝对位置，如果重新因为不能保证在记录集内的单个记录的顺序，除非创建与 SQL 语句使用再次创建记录集**ORDER BY**子句。  
  
 有关记录集导航和书签的详细信息，请参阅文章[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。  
  
##  <a name="setbookmark"></a>CRecordset::SetBookmark  
 在包含指定的书签记录定位记录集。  
  
```  
void SetBookmark(const CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>参数  
 `varBookmark`  
 对引用[CDBVariant](../../mfc/reference/cdbvariant-class.md)包含特定记录的书签值对象。  
  
### <a name="remarks"></a>备注  
 若要确定记录集是否支持书签，请调用[CanBookmark](#canbookmark)。 若要使书签可用，如果它们受支持，必须设置**CRecordset::useBookmarks**选项`dwOptions`参数[打开](#open)成员函数。  
  
> [!NOTE]
>  如果书签将变为不受支持或不可用，则调用`SetBookmark`将导致引发异常。 只进的记录集不支持书签。  
  
 若要首先检索当前记录的书签，请调用[GetBookmark](#getbookmark)，这将保存到的书签值`CDBVariant`对象。 更高版本，你可以返回到该记录通过调用`SetBookmark`使用已保存的书签值。  
  
> [!NOTE]
>  某些记录集在操作后，应检查之前调用的书签持久性`SetBookmark`。 例如，如果检索具有书签`GetBookmark`，然后调用**Requery**，书签可能不再有效。 调用[CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)若要检查是否可以安全地调用`SetBookmark`。  
  
 有关书签和记录集导航的详细信息，请参阅文章[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
##  <a name="setfielddirty"></a>CRecordset::SetFieldDirty  
 将其标记为已更改的记录集或为未更改的字段数据成员。  
  
```  
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 包含在记录集中的字段数据成员的地址或**NULL**。 如果**NULL**，标记在记录集中的所有字段数据成员。 (C + + **NULL**不同时，为 Null，在数据库术语中，这意味着"having 没有值。")  
  
 `bDirty`  
 **TRUE**字段数据成员是否会被标记为"脏"（更改）。 否则为**FALSE**字段数据成员是否会被标记为"清理"（未更改）。  
  
### <a name="remarks"></a>备注  
 将标记为未更改的字段可确保该字段将不会更新，并导致更少的 SQL 流量。  
  
> [!NOTE]
>  此成员函数不是适用于使用的批量行提取的记录集。 如果已实现批量行提取，然后`SetFieldDirty`将导致失败的断言。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
 Framework 标记更改字段数据成员，以确保它们将数据源上的记录写入，通过记录字段交换 (RFX) 机制。 更改字段的值通常设置为字段脏自动，因此你将很少需要调用`SetFieldDirty`你自己，但你有时可能想要确保，列将显式更新或插入而不考虑哪些值处于字段数据成员。  
  
> [!CAUTION]
>  只有具有调用之后才调用此成员函数[编辑](#edit)或[AddNew](#addnew)。  
  
 使用**NULL**为函数的第一个参数将该函数仅适用于**outputColumn**字段，不**param**字段。 例如，调用  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 将仅设置**outputColumn**字段设置为**NULL**;**param**字段不会受到影响。  
  
 若要在**param**字段，你必须提供个人的实际地址**param**你想要使用，如：  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 这意味着您不能设置所有**param**字段设置为**NULL**，如可以按照与**outputColumn**字段。  
  
##  <a name="setfieldnull"></a>CRecordset::SetFieldNull  
 为 Null （专门具有任何值） 或为非 Null 标志记录集字段数据的成员。  
  
```  
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 包含在记录集中的字段数据成员的地址或**NULL**。 如果**NULL**，标记在记录集中的所有字段数据成员。 (C + + **NULL**不同时，为 Null，在数据库术语中，这意味着"having 没有值。")  
  
 `bNull`  
 如果字段数据成员均被标记为不具有任何值 (Null)，则为非 0。 如果字段数据成员是被标记为非 Null 则否则为 0。  
  
### <a name="remarks"></a>备注  
 当你将一条新记录添加到记录集时，所有字段数据成员最初设置为 Null 值的并标记为"脏"（更改）。 当从数据源检索一条记录时，其列已具有值，或者为 Null。  
  
> [!NOTE]
>  请勿在使用批量行提取的记录集上调用此成员函数。 如果你已实现批量行提取，则调用`SetFieldNull`导致失败的断言。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
 如果你明确想要将当前记录的字段指定为不具有一个值，调用`SetFieldNull`与`bNull`设置为**TRUE**标记为 Null。 如果字段以前已标记为 Null，并且现在想要为其提供一个值，只需将其新值设置。 不需要删除与 Null 标志`SetFieldNull`。 若要确定是否允许该字段为 Null，调用`IsFieldNullable`。  
  
> [!CAUTION]
>  只有具有调用之后才调用此成员函数[编辑](#edit)或[AddNew](#addnew)。  
  
 使用**NULL**为函数的第一个参数将该函数仅适用于**outputColumn**字段，不**param**字段。 例如，调用  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 将仅设置**outputColumn**字段设置为**NULL**;**param**字段不会受到影响。  
  
 若要在**param**字段，你必须提供个人的实际地址**param**你想要使用，如：  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 这意味着您不能设置所有**param**字段设置为**NULL**，如可以按照与**outputColumn**字段。  
  
> [!NOTE]
>  当将参数设置为 Null，调用`SetFieldNull`记录集是打开的导致断言之前。 在这种情况下，调用[SetParamNull](#setparamnull)。  
  
 `SetFieldNull`通过实现[DoFieldExchange](#dofieldexchange)。  
  
##  <a name="setlockingmode"></a>CRecordset::SetLockingMode  
 设置为"开放式"锁定 （默认值） 或"保守式"锁定的锁定模式。 确定如何记录被锁定，无法更新。  
  
```  
void SetLockingMode(UINT nMode);
```  
  
### <a name="parameters"></a>参数  
 `nMode`  
 包含中的以下值之一**枚举 LockMode**:  
  
- **开放式**乐观锁定锁定正在更新仅在调用期间记录**更新**。  
  
- **保守式**保守式锁定锁定记录就会立即**编辑**称为并阻止对其锁定直到**更新**调用完成或移动到新的记录。  
  
### <a name="remarks"></a>备注  
 如果你需要指定的记录集使用更新的两种记录锁定的策略，请调用此成员函数。 默认情况下，记录集的锁定模式是**开放式**。 您可以更改，为更加小心**保守式**锁定策略。 调用`SetLockingMode`构造并打开记录集对象之后但在调用之前**编辑**。  
  
##  <a name="setparamnull"></a>CRecordset::SetParamNull  
 为 Null （专门具有任何值） 或为非 Null 标志参数。  
  
```  
void SetParamNull(
    int nIndex,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 参数的从零开始的索引。  
  
 `bNull`  
 如果**TRUE** （默认值），参数标记为 Null。 否则，该参数被标记为非 Null。  
  
### <a name="remarks"></a>备注  
 与不同[SetFieldNull](#setfieldnull)，可以调用`SetParamNull`已打开记录集之前。  
  
 `SetParamNull`通常用于预定义查询 （存储过程）。  
  
##  <a name="setrowsetcursorposition"></a>CRecordset::SetRowsetCursorPosition  
 将光标移到中当前行集的行。  
  
```  
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>参数  
 `wRow`  
 基于 1 中的位置的行的当前行集。 此值可以介于 1 到行集的大小。  
  
 `wLockType`  
 值，该值指示如何刷新它之后锁定行。 有关详细信息，请参阅“备注”。  
  
### <a name="remarks"></a>备注  
 当实现批量行提取，记录将检索的行集，其中读取的行集的第一个记录是当前记录。 若要使行集内的另一条记录成为当前记录，调用`SetRowsetCursorPosition`。 例如，你可以组合`SetRowsetCursorPosition`与[GetFieldValue](#getfieldvalue)成员函数以动态地从记录集中的任何记录中检索数据。  
  
 若要使用`SetRowsetCursorPosition`，你必须已实现批量行提取，通过指定`CRecordset::useMultiRowFetch`选项`dwOptions`中的参数[打开](#open)成员函数。  
  
 `SetRowsetCursorPosition`调用 ODBC API 函数**SQLSetPos**。 `wLockType`参数指定后的行的锁定状态**SQLSetPos**已执行。 下表描述的可能值`wLockType`。  
  
|wLockType|描述|  
|---------------|-----------------|  
|`SQL_LOCK_NO_CHANGE`（默认值）|驱动程序或数据源可确保之前行处于相同的锁定或解锁状态`SetRowsetCursorPosition`调用。|  
|`SQL_LOCK_EXCLUSIVE`|驱动程序或数据源以独占方式锁定行。 并非所有数据源都支持这种类型的锁定。|  
|`SQL_LOCK_UNLOCK`|驱动程序或数据源解除锁定行。 并非所有数据源都支持这种类型的锁定。|  
  
 有关详细信息**SQLSetPos**，请参阅 Windows SDK。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
##  <a name="setrowsetsize"></a>CRecordset::SetRowsetSize  
 指定你想要在提取过程中检索的记录数。  
  
```  
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```  
  
### <a name="parameters"></a>参数  
 *dwNewRowsetSize*  
 要在给定提取过程中检索的行数。  
  
### <a name="remarks"></a>备注  
 此虚拟成员函数可指定你想要使用批量行提取时在一次获取期间检索的行数。 若要实现批量行提取，必须设置`CRecordset::useMultiRowFetch`选项`dwOptions`参数[打开](#open)成员函数。  
  
> [!NOTE]
>  调用`SetRowsetSize`而无需实现批量行提取将导致失败的断言。  
  
 调用`SetRowsetSize`之前调用**打开**最初设置为记录集的行集大小。 在实现批量行提取时的默认行集大小为 25。  
  
> [!NOTE]
>  在调用时要格外小心`SetRowsetSize`。 如果你手动分配存储大小的数据 (所指定的**CRecordset::userAllocMultiRowBuffers**选项中的 dwOptions 参数**打开**)，应检查是否需要重新分配这些存储缓冲区后调用`SetRowsetSize`，但在执行任何游标导航操作之前。  
  
 若要获取的行集大小的当前设置，请调用[GetRowsetSize](#getrowsetsize)。  
  
 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
##  <a name="update"></a>CRecordset::Update  
 完成`AddNew`或**编辑**通过将新的或编辑数据保存在数据源上的操作。  
  
```  
virtual BOOL Update();
```  
  
### <a name="return-value"></a>返回值  
 如果已成功更新一个记录; 则为非 0如果没有列发生了更改则否则为 0。 如果没有更新任何记录，或如果多个已更新一个记录，则引发异常。 也会引发异常的任何其他故障对数据源。  
  
### <a name="remarks"></a>备注  
 在调用后调用此成员函数[AddNew](#addnew)或[编辑](#edit)成员函数。 完成所需的此调用`AddNew`或**编辑**操作。  
  
> [!NOTE]
>  如果你已实现批量行提取，则无法调用**更新**。 这将导致失败的断言。 尽管类`CRecordset`不提供一种机制，用于更新的数据大容量行，你可以通过使用 ODBC API 函数编写您自己的函数**SQLSetPos**。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。  
  
 同时`AddNew`和**编辑**准备保存到数据源在其中放置添加或编辑的数据的编辑缓冲区。 **更新**将数据保存。 更新仅这些字段标记或检测到为已更改。  
  
 如果数据源支持事务，则你可以**更新**调用 (和其对应`AddNew`或**编辑**调用) 事务的一部分。 有关事务的详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
> [!CAUTION]
>  如果调用**更新**但未事先调用`AddNew`或**编辑**，**更新**引发`CDBException`。 如果调用`AddNew`或**编辑**，必须调用**更新**之前调用**移动**操作或之前关闭记录集或数据源连接。 否则，所做的更改都将丢失而不另行通知。  
  
 有关处理的详细信息**更新**失败，请参阅文章[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
### <a name="example"></a>示例  
 请参阅文章[事务： 在记录集 (ODBC) 执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDatabase 类](../../mfc/reference/cdatabase-class.md)   
 [CRecordView 类](../../mfc/reference/crecordview-class.md)
