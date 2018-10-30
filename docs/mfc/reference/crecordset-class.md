---
title: CRecordset 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 086aaebcdc44439c45a219c7292da4aff9e13b06
ms.sourcegitcommit: a88d228480d4bb5834e985d7b3ead2760be95572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2018
ms.locfileid: "50203087"
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
|[CRecordset::CanAppend](#canappend)|返回非零，如果可以将新记录添加到通过记录集`AddNew`成员函数。|
|[CRecordset::CanBookmark](#canbookmark)|返回非零，如果记录集支持书签。|
|[CRecordset::Cancel](#cancel)|取消异步操作或从第二个线程的进程。|
|[CRecordset::CancelUpdate](#cancelupdate)|取消所有挂起的更新，由于`AddNew`或`Edit`操作。|
|[CRecordset::CanRestart](#canrestart)|返回非零值如果`Requery`可以调用以再次运行记录集的查询。|
|[CRecordset::CanScroll](#canscroll)|返回非零，如果可以滚动浏览记录。|
|[CRecordset::CanTransact](#cantransact)|返回非零，如果数据源支持事务。|
|[CRecordset::CanUpdate](#canupdate)|返回非零，如果可以更新该记录集 （你可以添加、 更新或删除记录）。|
|[CRecordset::CheckRowsetError](#checkrowseterror)|调用以处理记录提取期间生成的错误。|
|[CRecordset::Close](#close)|关闭记录集和与之关联 ODBC HSTMT。|
|[CRecordset::Delete](#delete)|从记录集中删除当前记录。 您必须显式滚动到另一条记录后删除。|
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|调用以交换的数据从数据源的记录集的大容量行。 实现批量记录字段交换 (Bulk RFX)。|
|[CRecordset::DoFieldExchange](#dofieldexchange)|调用以交换 （在这两个方向上） 之间的记录集的字段数据成员和数据源上的相应记录的数据。 实现记录字段交换 (RFX)。|
|[CRecordset::Edit](#edit)|准备对当前记录的更改。 调用`Update`以完成编辑。|
|[CRecordset::FlushResultSet](#flushresultset)|返回非零，如果存在另一个结果设置为在使用预定义的查询时进行检索。|
|[CRecordset::GetBookmark](#getbookmark)|将一条记录的书签值分配给参数对象。|
|[Crecordset:: Getdefaultconnect](#getdefaultconnect)|调用以获取默认连接字符串。|
|[CRecordset::GetDefaultSQL](#getdefaultsql)|调用以获取要执行的默认 SQL 字符串。|
|[CRecordset::GetFieldValue](#getfieldvalue)|在记录集中返回的字段值。|
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|在记录集中返回字段的数。|
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|在记录集中返回特定类型的字段的信息。|
|[CRecordset::GetRecordCount](#getrecordcount)|在记录集中返回记录的数。|
|[CRecordset::GetRowsetSize](#getrowsetsize)|返回要在单个提取过程中检索的记录数。|
|[CRecordset::GetRowsFetched](#getrowsfetched)|返回实际提取过程中检索的行数。|
|[CRecordset::GetRowStatus](#getrowstatus)|后一次提取返回的行的状态。|
|[CRecordset::GetSQL](#getsql)|获取用于选择记录集的记录的 SQL 字符串。|
|[CRecordset::GetStatus](#getstatus)|获取记录集的状态： 当前记录和是否已获得最终的记录数的索引。|
|[CRecordset::GetTableName](#gettablename)|获取记录集所基于的表的名称。|
|[CRecordset::IsBOF](#isbof)|返回非零，如果在第一条记录之前定位完记录集。 没有当前记录。|
|[CRecordset::IsDeleted](#isdeleted)|返回非零，如果记录集定位在已删除的记录上。|
|[CRecordset::IsEOF](#iseof)|返回非零，如果在最后一条记录后定位完记录集。 没有当前记录。|
|[CRecordset::IsFieldDirty](#isfielddirty)|返回非零，如果已更改的当前记录中的指定的字段。|
|[CRecordset::IsFieldNull](#isfieldnull)|返回当前记录中的指定的字段为 null 时，非零值 （不具有任何值）。|
|[CRecordset::IsFieldNullable](#isfieldnullable)|返回非零，如果可以设置的当前记录中的指定的字段为 null （具有任何值）。|
|[CRecordset::IsOpen](#isopen)|返回非零值如果`Open`已被调用过。|
|[CRecordset::Move](#move)|从两个方向中的当前记录到指定数目的记录定位记录集。|
|[CRecordset::MoveFirst](#movefirst)|定位在记录集中的第一个记录的当前记录。 用于测试`IsBOF`第一个。|
|[CRecordset::MoveLast](#movelast)|定位当前记录的最后一个记录或最后一个行集。 用于测试`IsEOF`第一个。|
|[CRecordset::MoveNext](#movenext)|在下一条记录或下一个行集上定位的当前记录。 用于测试`IsEOF`第一个。|
|[CRecordset::MovePrev](#moveprev)|在上一条记录或上一个行集上定位的当前记录。 用于测试`IsBOF`第一个。|
|[CRecordset::OnSetOptions](#onsetoptions)|调用以设置 （使用所选内容上） 的选项为指定的 ODBC 语句。|
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|调用以设置指定的 ODBC 语句 （适用于更新） 的选项。|
|[Crecordset:: Open](#open)|通过检索表或执行的查询的记录集表示打开记录集。|
|[CRecordset::RefreshRowset](#refreshrowset)|刷新的数据和指定的行的状态。|
|[CRecordset::Requery](#requery)|运行以刷新所选的记录的记录集的查询。|
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|定位到指定的记录号相对应的记录的记录集。|
|[CRecordset::SetBookmark](#setbookmark)|定位指定的书签记录的记录集。|
|[CRecordset::SetFieldDirty](#setfielddirty)|将当前记录中指定的字段标记为已更改。|
|[CRecordset::SetFieldNull](#setfieldnull)|为 null （具有任何值） 的当前记录中设置指定字段的值。|
|[CRecordset::SetLockingMode](#setlockingmode)|设置为"开放式"锁定 （默认值） 或"保守式"锁定的锁定模式。 确定如何更新锁定的记录。|
|[CRecordset::SetParamNull](#setparamnull)|将指定的参数设置为 null （具有任何值）。|
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|将光标置于该行集内的指定行上。|
|[CRecordset::SetRowsetSize](#setrowsetsize)|指定你想要在提取过程中检索的记录数。|
|[CRecordset::Update](#update)|完成`AddNew`或`Edit`通过将新的或编辑数据保存在数据源上的操作。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CRecordset::m_hstmt](#m_hstmt)|包含记录集的 ODBC 语句句柄。 键入 `HSTMT`。|
|[CRecordset::m_nFields](#m_nfields)|包含在记录集中的字段数据成员的数目。 键入 `UINT`。|
|[CRecordset::m_nParams](#m_nparams)|包含在记录集中的参数数据成员的数目。 键入 `UINT`。|
|[CRecordset::m_pDatabase](#m_pdatabase)|包含一个指向`CDatabase`对象通过该记录集与连接到数据源。|
|[CRecordset::m_strFilter](#m_strfilter)|包含`CString`指定结构化查询语言 (SQL)`WHERE`子句。 作为筛选器用于选择满足特定条件的那些记录。|
|[CRecordset::m_strSort](#m_strsort)|包含`CString`，它指定 SQL`ORDER BY`子句。 用于控制如何记录进行排序。|

## <a name="remarks"></a>备注

名为"记录集，"`CRecordset`对象通常使用两种形式： 动态集和快照。 动态集与其他用户所做的数据更新中保持同步。 快照是数据的静态视图。 每个窗体表示一组固定的打开记录集时，记录但时滚动中动态集的记录时，它反映随后所做的更改记录、 其他用户或应用程序中的其他记录集。

> [!NOTE]
>  如果您正在使用的数据访问对象 (DAO) 类而不是开放式数据库连接 (ODBC) 类，使用类[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)相反。 有关详细信息，请参阅文章[概述： 数据库编程](../../data/data-access-programming-mfc-atl.md)。

若要使用这两种记录集，您通常派生应用程序特定的记录集类从`CRecordset`。 记录集从数据源选择的记录，然后，可以：

- 滚动浏览记录。

- 更新的记录，并指定锁定模式。

- 要将限制从提供的那些数据源选择的记录的记录集的筛选器。

- 对记录集进行排序。

- 参数化记录集进行自定义信息直到运行时才知道其所选内容。

若要使用您的类，打开数据库，然后构造一个记录集对象，将构造函数传递一个指向你`CDatabase`对象。 然后，调用记录集的`Open`成员函数，您可以在其中指定的对象是否动态集或快照。 调用`Open`从数据源选择数据。 打开记录集对象后，使用其成员函数和数据成员来滚动浏览记录并进行这些操作。 可使用的操作取决于该对象是动态集或快照，是否可更新或只读的 （这取决于开放式数据库连接 (ODBC) 数据源的功能），并且是否已实现批量行提取。 若要刷新记录可能已更改或添加以来`Open`调用，调用对象的`Requery`成员函数。 调用对象的`Close`成员函数，并使用它完成后销毁对象。

在派生`CRecordset`类中，记录字段交换 (RFX) 或大容量记录字段交换 (Bulk RFX) 用于支持读取和更新记录的字段。

记录集和记录字段交换有关的详细信息，请参阅文章[概述： 数据库编程](../../data/data-access-programming-mfc-atl.md)，[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)，[记录集： 提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)，并[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。 致力于动态集和快照，请参阅文章[动态集](../../data/odbc/dynaset.md)并[快照](../../data/odbc/snapshot.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>要求

**标头：** afxdb.h

##  <a name="addnew"></a>  CRecordset::AddNew

准备向表添加一条新记录。

```
virtual void AddNew();
```

### <a name="remarks"></a>备注

必须调用[再次查询](#requery)成员函数，以查看新添加的记录。 记录的字段是最初为 Null。 （在数据库术语中，Null 意味着"无值"，并且不为 NULL，c + + 中相同。）若要完成该操作，必须调用[更新](#update)成员函数。 `Update` 将所做的更改保存到数据源。

> [!NOTE]
>  如果已实现批量行提取，则不能调用`AddNew`。 这将导致失败的断言。 尽管类`CRecordset`不提供一种机制，用于更新的数据大容量行，可以编写您自己的函数，通过使用 ODBC API 函数`SQLSetPos`。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

`AddNew` 准备新的空记录中使用记录集的字段数据成员。 调用后`AddNew`，在记录集的字段数据成员中设置所需的值。 (无需调用[编辑](#edit)成员函数实现此目的; 请改用`Edit`仅为现有记录。)当您随后调用`Update`、 已更改的字段数据成员中的值保存在数据源上。

> [!CAUTION]
>  如果滚动到新的记录然后再调用`Update`、 新的记录将丢失，和给出任何警告。

如果数据源支持事务，可以使您`AddNew`调用事务的一部分。 有关事务的详细信息，请参阅类[CDatabase](../../mfc/reference/cdatabase-class.md)。 请注意，应调用[CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans)然后才能调用`AddNew`。

> [!NOTE]
>  程序需求，新记录添加到记录集中作为最后一条记录。 添加的记录不会添加到快照;必须调用`Requery`刷新记录集。

您不能调用`AddNew`记录集的`Open`尚未调用成员函数。 一个`CDBException`如果您调用，将引发`AddNew`无法附加到记录集。 您可以确定记录集是否可更新通过调用[CanAppend](#canappend)。

有关详细信息，请参阅以下文章：[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)，[记录集： 添加、 更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)，和[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。

### <a name="example"></a>示例

请参阅文章[事务： 在记录集 (ODBC) 执行的事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。

##  <a name="canappend"></a>  CRecordset::CanAppend

确定是否以前打开的记录集，可添加新记录。

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>返回值

非零，如果记录集允许添加新记录;否则为 0。 `CanAppend` 如果打开记录集持久化为只读的则将返回 0。

##  <a name="canbookmark"></a>  CRecordset::CanBookmark

确定是否记录集，可将记录使用书签标记。

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>返回值

如果记录集支持书签; 非零值否则为 0。

### <a name="remarks"></a>备注

此函数是独立于`CRecordset::useBookmarks`选项*dwOptions*参数[打开](#open)成员函数。 `CanBookmark` 指示给定的 ODBC 驱动程序和游标类型是否支持书签。 `CRecordset::useBookmarks` 指示是否书签将可用，提供它们受支持。

> [!NOTE]
>  只进的记录集不支持书签。

有关书签和记录集导航的详细信息，请参阅文章[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)并[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。

##  <a name="cancel"></a>  CRecordset::Cancel

数据源取消异步操作正在进行中的或从第二个线程的进程的请求。

```
void Cancel();
```

### <a name="remarks"></a>备注

请注意，MFC ODBC 类不能再使用异步处理;若要执行的异步操作，您必须直接调用 ODBC API 函数`SQLSetConnectOption`。 详细信息，请参阅"异步执行函数"的主题中*ODBC SDK 程序员指南*。

##  <a name="cancelupdate"></a>  CRecordset::CancelUpdate

取消任何挂起的更新、 引起[编辑](#edit)或[AddNew](#addnew)操作之前,[更新](#update)调用。

```
void CancelUpdate();
```

### <a name="remarks"></a>备注

> [!NOTE]
>  此成员函数不是适用于使用的批量行提取，因为不能调用此类记录集的记录集`Edit`， `AddNew`，或`Update`。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

如果启用自动脏字段检查，则`CancelUpdate`将还原到之前所具有的值的成员变量`Edit`或`AddNew`已被调用; 否则为值的任何更改将保留。 默认情况下，自动字段检查被启用时打开记录集。 若要禁用它，必须指定`CRecordset::noDirtyFieldCheck`中*dwOptions*参数[打开](#open)成员函数。

有关更新数据的详细信息，请参阅文章[记录集： 添加、 更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)。

##  <a name="canrestart"></a>  CRecordset::CanRestart

确定记录集是否允许通过调用重启 （若要刷新其记录） 其查询`Requery`成员函数。

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>返回值

如果允许重新查询; 非零值否则为 0。

##  <a name="canscroll"></a>  CRecordset::CanScroll

确定记录集是否允许滚动。

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>返回值

如果记录集允许滚动，则为非零值否则为 0。

### <a name="remarks"></a>备注

有关滚动的详细信息，请参阅文章[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。

##  <a name="cantransact"></a>  CRecordset::CanTransact

确定记录集是否允许事务。

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>返回值

如果记录集允许事务; 非零值否则为 0。

### <a name="remarks"></a>备注

有关详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。

##  <a name="canupdate"></a>  CRecordset::CanUpdate

确定是否可以更新该记录集。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>返回值

如果可以更新该记录集; 非零值否则为 0。

### <a name="remarks"></a>备注

记录集可能是只读的如果基础数据源是只读的或者指定`CRecordset::readOnly`中*dwOptions*参数打开记录集时。

##  <a name="checkrowseterror"></a>  CRecordset::CheckRowsetError

调用以处理记录提取期间生成的错误。

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>参数

*nRetCode*<br/>
ODBC API 函数的返回代码。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

此虚拟成员函数处理时提取的记录，发生错误和批量行提取期间很有用。 要考虑重写`CheckRowsetError`来实现您自己的错误处理。

`CheckRowsetError` 将自动调用在游标导航操作中，如`Open`， `Requery`，或任何`Move`操作。 它传递的 ODBC API 函数的返回值`SQLExtendedFetch`。 下表列出了可能的值为*nRetCode*参数。

|nRetCode|描述|
|--------------|-----------------|
|SQL_SUCCESS|函数成功地完成。提供不了任何其他信息。|
|SQL_SUCCESS_WITH_INFO|已成功完成，可能出现非致命错误的函数。 可以通过调用获取其他信息`SQLError`。|
|SQL_NO_DATA_FOUND|已提取的结果集中的所有行。|
|SQL_ERROR|失败的函数。 可以通过调用获取其他信息`SQLError`。|
|SQL_INVALID_HANDLE|由于无效的环境句柄、 连接句柄或语句句柄失败的函数。 这指示编程错误。 无其他信息是可从`SQLError`。|
|SQL_STILL_EXECUTING|以异步方式启动的函数仍在执行。 请注意，默认情况下，MFC 将永远不会将此值传递到`CheckRowsetError`;MFC 将继续调用`SQLExtendedFetch`直到其不再返回 SQL_STILL_EXECUTING。|

有关详细信息`SQLError`，请参阅 Windows SDK。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

##  <a name="close"></a>  CRecordset::Close

关闭记录集。

```
virtual void Close();
```

### <a name="remarks"></a>备注

取消分配 ODBC HSTMT 和所有内存分配的记录集的框架。 通常在调用之后`Close`，如果它已分配与删除 c + + 记录集对象**新**。

您可以调用`Open`后调用`Close`。 这样可以重复使用记录集对象。 替代方法是调用`Requery`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

##  <a name="crecordset"></a>  CRecordset::CRecordset

构造 `CRecordset` 对象。

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>参数

*pDatabase*<br/>
包含一个指向`CDatabase`对象或值为 NULL。 如果不为 NULL，`CDatabase`对象的`Open`成员函数不调用以将其连接到数据源，该记录集尝试打开为你自己期间`Open`调用。 如果传递 NULL，`CDatabase`构造对象并将其连接的适用于您使用您指定当派生类向导在记录集类的数据源信息。

### <a name="remarks"></a>备注

您可以使用`CRecordset`直接或派生特定于应用程序的类从`CRecordset`。 类向导用于派生您的记录集类。

> [!NOTE]
>  在派生的类*必须*提供自己的构造函数。 在派生类的构造函数中调用构造函数`CRecordset::CRecordset`，将沿适当的参数传递给它。

将 NULL 传递给您的记录集构造函数具有`CDatabase`对象构造，并自动为您进行连接。 这是一种有用的简写形式，不需要可构造并连接`CDatabase`之前构造记录集对象。

### <a name="example"></a>示例

有关详细信息，请参阅文章[记录集： 声明一个类用于表 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。

##  <a name="delete"></a>  CRecordset::Delete

删除当前记录。

```
virtual void Delete();
```

### <a name="remarks"></a>备注

在成功删除之后, 记录集的字段数据成员将设置为一个 Null 值，并且必须显式调用的一个`Move`才能移出已删除记录的函数。 一旦您移出已删除的记录，不能返回到它。 如果数据源支持事务，则可以进行`Delete`调用事务的一部分。 有关详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。

> [!NOTE]
>  如果已实现批量行提取，则不能调用`Delete`。 这将导致失败的断言。 尽管类`CRecordset`不提供一种机制，用于更新的数据大容量行，可以编写您自己的函数，通过使用 ODBC API 函数`SQLSetPos`。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

> [!CAUTION]
>  记录集必须可更新，并且必须有有效记录当前记录集内调用时`Delete`; 否则为就会出错。 例如，如果您删除的记录，但在调用之前不将其滚动到新的记录`Delete`再次`Delete`将引发[CDBException](../../mfc/reference/cdbexception-class.md)。

与不同[AddNew](#addnew)并[编辑](#edit)，调用`Delete`通过调用后面不接[更新](#update)。 如果`Delete`调用失败，字段数据成员将保留不变。

### <a name="example"></a>示例

此示例演示一个函数在框架上创建一个记录集。 该示例假定存在`m_dbCust`，类型的成员变量`CDatabase`已连接到数据源。

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

##  <a name="dobulkfieldexchange"></a>  CRecordset::DoBulkFieldExchange

调用以交换的数据从数据源的记录集的大容量行。 实现批量记录字段交换 (Bulk RFX)。

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>参数

*pFX*<br/>
一个指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象。 框架已具有将设置此对象指定为字段 exchange 操作上下文。

### <a name="remarks"></a>备注

实现批量行提取时，框架将调用此成员函数以自动将数据从数据源传输到记录集对象。 `DoBulkFieldExchange` 如果有，到记录集的所选内容的 SQL 语句字符串中的参数占位符，还将您参数的数据成员，绑定。

如果未实现批量行提取，框架将调用[DoFieldExchange](#dofieldexchange)。 若要实现批量行提取，必须指定`CRecordset::useMultiRowFetch`的选项*dwOptions*中的参数[打开](#open)成员函数。

> [!NOTE]
> `DoBulkFieldExchange` 仅当使用派生自的类可用`CRecordset`。 如果已创建记录集对象直接从`CRecordset`，必须调用[GetFieldValue](#getfieldvalue)成员函数以检索数据。

批量记录字段交换 (Bulk RFX) 是类似于记录字段交换 (RFX)。 数据是自动从数据源传输到记录集对象。 但是，不能调用`AddNew`， `Edit`， `Delete`，或`Update`传输回数据源的更改。 类`CRecordset`目前不提供机制更新大容量行的数据; 但是，使用 ODBC API 函数可以编写您自己的函数`SQLSetPos`。

请注意，ClassWizard 不支持批量记录字段交换;因此，您必须重写`DoBulkFieldExchange`手动通过编写对批量 RFX 函数的调用。 有关这些函数的详细信息，请参阅主题[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。

有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。 有关相关信息，请参阅文章[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。

##  <a name="dofieldexchange"></a>  CRecordset::DoFieldExchange

调用以交换 （在这两个方向上） 之间的记录集的字段数据成员和数据源上的相应记录的数据。 实现记录字段交换 (RFX)。

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>参数

*pFX*<br/>
一个指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象。 框架已具有将设置此对象指定为字段 exchange 操作上下文。

### <a name="remarks"></a>备注

当未实现批量行提取时，框架将调用此成员函数以自动和之间交换数据的记录集对象的字段数据成员的对应列的数据源上的当前记录。 `DoFieldExchange` 如果有，到记录集的所选内容的 SQL 语句字符串中的参数占位符，还将您参数的数据成员，绑定。

如果实现批量行提取，框架将调用[DoBulkFieldExchange](#dobulkfieldexchange)。 若要实现批量行提取，必须指定`CRecordset::useMultiRowFetch`的选项*dwOptions*中的参数[打开](#open)成员函数。

> [!NOTE]
> `DoFieldExchange` 仅当使用派生自的类可用`CRecordset`。 如果已创建记录集对象直接从`CRecordset`，必须调用[GetFieldValue](#getfieldvalue)成员函数以检索数据。

字段数据，称为记录字段交换 (RFX) 的交换中两个方向上的工作： 从数据源上的记录的字段的记录集对象的字段数据成员并从上至记录集对象的数据源的记录。

唯一的操作时通常必须执行实现`DoFieldExchange`派生记录集的类是使用类向导创建类并指定字段数据成员的名称和数据类型。 您还可能会将代码添加到 ClassWizard 写入指定的参数数据成员或处理动态绑定的任何列。 有关详细信息，请参阅文章[记录集： 动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

声明类向导在派生的记录集类时，向导会将写入的重写`DoFieldExchange`，类似于下面的示例：

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

有关 RFX 函数的详细信息，请参阅主题[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。

有关更多示例和详细信息`DoFieldExchange`，请参阅文章[记录字段交换： RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。 有关 RFX 的常规信息，请参阅文章[记录字段交换](../../data/odbc/record-field-exchange-rfx.md)。

##  <a name="edit"></a>  CRecordset::Edit

允许对当前记录更改。

```
virtual void Edit();
```

### <a name="remarks"></a>备注

调用后`Edit`，可以通过直接重置其值更改的字段数据成员。 在操作完成时您随后调用[更新](#update)成员函数上的数据源保存所做的更改。

> [!NOTE]
>  如果已实现批量行提取，则不能调用`Edit`。 这将导致失败的断言。 尽管类`CRecordset`不提供一种机制，用于更新的数据大容量行，可以编写您自己的函数，通过使用 ODBC API 函数`SQLSetPos`。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

`Edit` 保存记录集的数据成员的值。 如果您调用`Edit`，进行更改，然后调用`Edit`同样，记录的值会还原到之前第一个`Edit`调用。

在某些情况下，你可能想要更新的 （不包含任何数据），则为 Null 的列。 若要执行此操作，调用[SetFieldNull](#setfieldnull)其中参数为 true，则标记字段为 Null; 这也会导致要更新的列。 如果你想要写入的数据源，即使其值已更改，请调用的字段[SetFieldDirty](#setfielddirty)参数为 TRUE。 这样即使字段具有值为 Null。

如果数据源支持事务，则可以进行`Edit`调用事务的一部分。 请注意，应调用[CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans)然后才能调用`Edit`和之后打开记录集。 此外请注意，调用[CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)不是调用的替代`Update`完成`Edit`操作。 有关事务的详细信息，请参阅类[CDatabase](../../mfc/reference/cdatabase-class.md)。

具体取决于当前的锁定模式下，可能会被锁定要更新的记录`Edit`直到您调用`Update`或滚动到另一条记录，或者它可能仅在锁定`Edit`调用。 你可以用在锁定模式下[SetLockingMode](#setlockingmode)。

如果滚动到新的记录，然后才能调用还原以前的值的当前记录`Update`。 一个`CDBException`如果您调用，将引发`Edit`不能更新的记录集或如果没有当前记录。

有关详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)并[记录集： 锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

##  <a name="flushresultset"></a>  CRecordset::FlushResultSet

如果有多个结果集，检索预定义的查询 （存储过程） 下, 一步的结果的集。

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>返回值

如果有多个结果集来检索; 非零值否则为 0。

### <a name="remarks"></a>备注

应调用`FlushResultSet`只有当您处于完全结束当前结果集游标。 请注意，当检索下一个结果集通过调用`FlushResultSet`，将光标在该结果集上无效; 应调用[MoveNext](#movenext)成员函数之后，调用`FlushResultSet`。

如果预定义的查询使用输出参数或输入/输出参数，则必须调用`FlushResultSet`直到其返回`FALSE`（值 0），以获取这些参数值。

`FlushResultSet` 调用 ODBC API 函数`SQLMoreResults`。 如果`SQLMoreResults`然后返回 SQL_ERROR 或 SQL_INVALID_HANDLE，`FlushResultSet`将引发异常。 有关详细信息`SQLMoreResults`，请参阅 Windows SDK。

你的存储的过程需要具有绑定字段，如果你想要调用`FlushResultSet`。

### <a name="example"></a>示例

以下代码假定`COutParamRecordset`是`CRecordset`-基于预定义的查询使用输入的参数和输出参数，并让多个结果集派生的对象。 请注意的结构[DoFieldExchange](#dofieldexchange)重写。

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

##  <a name="getbookmark"></a>  CRecordset::GetBookmark

获取当前记录的书签值。

```
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>参数

*varBookmark*<br/>
对引用[CDBVariant](../../mfc/reference/cdbvariant-class.md)对象，表示当前记录上的书签。

### <a name="remarks"></a>备注

若要确定是否记录集上支持书签，请调用[CanBookmark](#canbookmark)。 若要使书签可用，如果它们受支持，必须设置`CRecordset::useBookmarks`选项*dwOptions*参数[打开](#open)成员函数。

> [!NOTE]
>  如果书签不受支持或不可用，则调用`GetBookmark`将导致引发异常。 只进的记录集不支持书签。

`GetBookmark` 将当前记录到的书签值分配`CDBVariant`对象。 若要移动到另一个记录后随时返回到该记录，请调用[SetBookmark](#setbookmark)相对应的`CDBVariant`对象。

> [!NOTE]
>  某些记录集在操作之后，书签可能不再有效。 例如，如果您调用`GetBookmark`跟`Requery`，你可能不能返回到的记录`SetBookmark`。 调用[CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)若要检查是否可以安全地调用`SetBookmark`。

有关书签和记录集导航的详细信息，请参阅文章[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)并[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。

##  <a name="getdefaultconnect"></a>  Crecordset:: Getdefaultconnect

调用以获取默认连接字符串。

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>返回值

一个`CString`，其中包含默认连接字符串。

### <a name="remarks"></a>备注

框架调用此成员函数以获取记录集所基于的数据源的默认连接字符串。 类向导通过标识用于在 ClassWizard 中获取有关表和列的信息相同的数据源为您实现此函数。 您可能会发现它可以方便地依赖于开发您的应用程序时此默认连接。 但默认的连接可能适用于应用程序的用户。 如果是这种情况，应重新实现此函数中，放弃 ClassWizard 的版本。 有关连接字符串的详细信息，请参阅文章[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)。

##  <a name="getdefaultsql"></a>  CRecordset::GetDefaultSQL

调用以获取要执行的默认 SQL 字符串。

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>返回值

一个`CString`，其中包含默认的 SQL 语句。

### <a name="remarks"></a>备注

框架调用此成员函数可获取记录集所基于的默认 SQL 语句。 这可能是表名称或 SQL**选择**语句。

间接通过声明类向导，在记录集类定义默认的 SQL 语句和类向导会为您执行此任务。

如果需要为自己使用的 SQL 语句字符串，调用`GetSQL`，它返回用于选择记录集的记录时已打开的 SQL 语句。 您可以编辑中的类的重写的默认 SQL 字符串`GetDefaultSQL`。 例如，可以指定预定义的查询使用调用**调用**语句。 (请注意，不过，您编辑的如果`GetDefaultSQL`，还需要修改`m_nFields`以匹配的数据源中的列数。)

有关详细信息，请参阅文章[记录集： 声明一个类用于表 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。

> [!CAUTION]
>  表名称将为空，如果框架无法识别的表名称，如果提供了多个表名称，或者如果**调用**无法解释语句。 请注意，当使用**调用**语句，不能插入大括号之间的空白并**调用**关键字，也应插入空格前的大括号或之前不**选择**中的关键字**选择**语句。

##  <a name="getfieldvalue"></a>  CRecordset::GetFieldValue

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

*lpszName*<br/>
字段的名称。

*varValu*e A 引用[CDBVariant](../../mfc/reference/cdbvariant-class.md)将存储在字段的值的对象。

*nFieldType*<br/>
字段的 ODBC C 数据类型。 使用默认值，DEFAULT_FIELD_TYPE，强制`GetFieldValue`来确定将 C 数据类型从 SQL 数据类型，根据下表。 否则，您可以在其中指定的数据直接键入或选择兼容的数据类型;例如，可以存储任何数据类型属于 SQL_C_CHAR。

|C 数据类型|SQL 数据类型|
|-----------------|-------------------|
|SQL_C_BIT|SQL_BIT|
|为 SQL_C_UTINYINT|SQL_TINYINT|
|SQL_C_SSHORT|SQL_SMALLINT|
|SQL_C_SLONG|SQL_INTEGER|
|SQL_C_FLOAT|SQL_REAL|
|SQL_C_DOUBLE|SQL_FLOATSQL_DOUBLE|
|SQL_C_TIMESTAMP|SQL_DATESQL_TIMESQL_TIMESTAMP|
|SQL_C_CHAR|SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR|
|SQL_C_BINARY|SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY|

有关 ODBC 数据类型的详细信息，请参阅"SQL 数据类型"和"C 数据类型"的 Windows SDK 的附录 D 中的主题。

*nIndex*<br/>
字段的从零开始的索引。

*strValue*<br/>
对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)将存储在字段的值的对象转换为文本，而不考虑字段的数据类型。

### <a name="remarks"></a>备注

您可以查看字段按名称或索引。 可以将字段值存储在`CDBVariant`对象或`CString`对象。

如果已实现批量行提取，在行集中的第一个记录上始终位于当前记录。 若要使用`GetFieldValue`上给定行集内的记录，你必须首先调用[SetRowsetCursorPosition](#setrowsetcursorposition)成员函数以将光标移到所需的行中的行集。 然后，调用`GetFieldValue`该行。 若要实现批量行提取，必须指定`CRecordset::useMultiRowFetch`的选项*dwOptions*中的参数[打开](#open)成员函数。

可以使用`GetFieldValue`动态地在运行的时，而不是以静态方式将其绑定在设计时提取的字段。 例如，如果您已声明直接从记录集对象`CRecordset`，则必须使用`GetFieldValue`检索字段数据; 记录字段交换 (RFX) 或大容量记录字段交换 (Bulk RFX)，未实现。

> [!NOTE]
>  如果你声明而不派生自的记录集对象`CRecordset`，而没有加载 ODBC 游标库。 游标库要求记录集具有至少一个绑定的列;但是，如果使用`CRecordset`直接绑定的列都。 成员函数[不同](../../mfc/reference/cdatabase-class.md#openex)并[CDatabase::Open](../../mfc/reference/cdatabase-class.md#open)控制是否将加载游标库。

`GetFieldValue` 调用 ODBC API 函数`SQLGetData`。 如果您的驱动程序输出的字段值的实际长度值 SQL_NO_TOTAL`GetFieldValue`将引发异常。 有关详细信息`SQLGetData`，请参阅 Windows SDK。

### <a name="example"></a>示例

下面的示例代码演示如何调用`GetFieldValue`直接从记录集对象声明为`CRecordset`。

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
>  与 DAO 类不同`CDaoRecordset`，`CRecordset`没有`SetFieldValue`成员函数。 如果您创建的对象直接从`CRecordset`，它是实际上它是只读的。

有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

##  <a name="getodbcfieldcount"></a>  CRecordset::GetODBCFieldCount

检索记录集对象中的字段的总数。

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>返回值

在记录集中的字段数。

### <a name="remarks"></a>备注

有关创建记录集的详细信息，请参阅文章[记录集： 创建和关闭记录集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。

##  <a name="getodbcfieldinfo"></a>  CRecordset::GetODBCFieldInfo

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

*lpszName*<br/>
字段的名称。

*fieldinfo*<br/>
对引用`CODBCFieldInfo`结构。

*nIndex*<br/>
字段的从零开始的索引。

### <a name="remarks"></a>备注

该函数的一个版本，可以按名称查找字段。 其他版本，可按索引查找字段。

有关返回的信息的说明，请参阅[CODBCFieldInfo](../../mfc/reference/codbcfieldinfo-structure.md)结构。

有关创建记录集的详细信息，请参阅文章[记录集： 创建和关闭记录集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。

##  <a name="getrecordcount"></a>  CRecordset::GetRecordCount

确定记录集的大小。

```
long GetRecordCount() const;
```

### <a name="return-value"></a>返回值

记录集; 中的记录数如果记录集不包含任何记录; 则为 0或如果无法确定记录计数为-1。

### <a name="remarks"></a>备注

> [!CAUTION]
>  保持为"高使用标记，"编号最高的记录但视为用户遍历记录的记录数。 用户已经超过最后一条记录后，仅已知的记录总数。 出于性能原因，将不更新计数在调用时`MoveLast`。 若要对记录进行计数自己，调用`MoveNext`反复直到`IsEOF`返回非零值。 添加通过记录`CRecordset:AddNew`并`Update`增加计数; 删除通过记录`CRecordset::Delete`减少计数。

##  <a name="getrowsetsize"></a>  CRecordset::GetRowsetSize

获取你想要在给定提取过程中检索的行数的当前设置。

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>返回值

要在给定提取过程中检索的行数。

### <a name="remarks"></a>备注

如果使用批量行提取，打开记录集时的默认行集大小为 25;否则，它是 1。

若要实现批量行提取，必须指定`CRecordset::useMultiRowFetch`选项*dwOptions*参数[打开](#open)成员函数。 若要更改的行集大小的设置，请调用[SetRowsetSize](#setrowsetsize)。

有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

##  <a name="getrowsfetched"></a>  CRecordset::GetRowsFetched

确定后提取实际检索多少条记录。

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>返回值

给定提取后从数据源检索的行数。

### <a name="remarks"></a>备注

在实现批量行提取，这很有用。 行集大小通常指示将从提取; 中检索行数但是，在记录集中的总行数也会影响将行集中检索行数。 例如，如果记录集，行集大小设置为 4 的 10 条记录，然后遍历记录集通过调用`MoveNext`将导致具有只有 2 个记录的最后一个行集。

若要实现批量行提取，必须指定`CRecordset::useMultiRowFetch`选项*dwOptions*参数[打开](#open)成员函数。 若要指定行集大小，请调用[SetRowsetSize](#setrowsetsize)。

有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

##  <a name="getrowstatus"></a>  CRecordset::GetRowStatus

获取当前行集中的行的状态。

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>参数

*wRow*<br/>
基于 1 的行位置的当前行集中。 此值的范围是从 1 到行集的大小。

### <a name="return-value"></a>返回值

行状态值。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

`GetRowStatus` 返回一个值，指示状态设置为行中的任一任何更改，因为上一次检索从数据源，或返回任何行对应于*wRow*提取。 下表列出可能的返回值。

|状态值|描述|
|------------------|-----------------|
|SQL_ROW_SUCCESS|该行未更改。|
|SQL_ROW_UPDATED|已更新行。|
|SQL_ROW_DELETED|已删除该行。|
|SQL_ROW_ADDED|已添加的行。|
|SQL_ROW_ERROR|因出错而检索行。|
|SQL_ROW_NOROW|没有对应的行*wRow*。|

有关详细信息，请参阅 ODBC API 函数`SQLExtendedFetch`Windows SDK 中。

##  <a name="getstatus"></a>  CRecordset::GetStatus

确定记录集和是否达到过最后一条记录中的当前记录的索引。

```
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>参数

*rStatus*<br/>
对 `CRecordsetStatus` 对象的引用。 有关详细信息，请参阅备注部分。

### <a name="remarks"></a>备注

`CRecordset` 尝试跟踪索引，但在某些情况下这不可能。 请参阅[GetRecordCount](#getrecordcount)的说明。

`CRecordsetStatus`结构具有以下形式：

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

两个成员`CRecordsetStatus`具有以下含义：

- `m_lCurrentRecord` 如果已知，包含记录集中的当前记录的从零开始索引。 如果索引不能确定，此成员包含 AFX_CURRENT_RECORD_UNDEFINED (-2)。 如果`IsBOF`为 TRUE （空记录集或尝试在第一条记录之前向下滚动），则`m_lCurrentRecord`设置为 AFX_CURRENT_RECORD_BOF (-1)。 在第一条记录，则它设置为 0，第二个记录 1，依次类推。

- `m_bRecordCountFinal` 如果已确定的记录集中的记录总数，非零值。 通常必须通过开始处的记录集和调用来完成这`MoveNext`直到`IsEOF`返回非零值。 如果此成员为零，则记录计数所返回的`GetRecordCount`，如果不为-1，是仅记录的"高使用标记"计数。

##  <a name="getsql"></a>  CRecordset::GetSQL

调用此成员函数可获取用于选择记录集的记录时已打开的 SQL 语句。

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>返回值

一个**const**引用`CString`，其中包含 SQL 语句。

### <a name="remarks"></a>备注

这通常是 SQL**选择**语句。 返回的字符串`GetSQL`是只读的。

返回的字符串`GetSQL`通常不同于你可能会传递到记录集在任何字符串*lpszSQL*参数`Open`成员函数。 这是因为该记录集构造基于传递给一个完整的 SQL 语句`Open`，使用类向导，您可以指定在指定的内容`m_strFilter`和`m_strSort`数据成员，并且可能具有的任何参数指定。 有关记录集如何构造此 SQL 语句，有关详细信息，请参阅文章[记录集： 如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。

> [!NOTE]
>  仅在调用后调用此成员函数[打开](#open)。

##  <a name="gettablename"></a>  CRecordset::GetTableName

获取记录集的查询所基于的 SQL 表的名称。

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>返回值

一个**const**引用`CString`包含表的名称，如果记录集是根据一个表; 否则为空字符串。

### <a name="remarks"></a>备注

`GetTableName` 是仅记录集基于某一表，而不是联接的多个表或预定义的查询 （存储过程） 时才有效。 名称是只读的。

> [!NOTE]
>  仅在调用后调用此成员函数[打开](#open)。

##  <a name="isbof"></a>  CRecordset::IsBOF

返回非零，如果在第一条记录之前定位完记录集。 没有当前记录。

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>返回值

如果记录集不包含任何记录，或如果已在第一条记录; 之前向后滚动，则非零值否则为 0。

### <a name="remarks"></a>备注

之前从记录滚动到记录以了解是否已在第一个记录的记录集之前调用此成员函数。 此外可以使用`IsBOF`连同`IsEOF`来确定记录集是否包含任何记录，或为空。 立即调用后`Open`，如果记录集不包含任何记录，`IsBOF`返回非零值。打开具有至少一个记录的记录集，第一条记录时的当前记录和`IsBOF`返回 0。

如果第一条记录的当前记录，并且你调用`MovePrev`，`IsBOF`随后将返回非零值。 如果`IsBOF`返回非零值，并且您调用`MovePrev`，出现错误。 如果`IsBOF`返回非零值时，当前记录是不确定，并需要当前记录任何操作将导致错误。

### <a name="example"></a>示例

此示例使用`IsBOF`和`IsEOF`来检测记录集的限制，如代码滚动浏览中两个方向上的记录集。

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

##  <a name="isdeleted"></a>  CRecordset::IsDeleted

确定当前记录是否已被删除。

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>返回值

如果记录集定位在已删除的记录; 上的非零否则为 0。

### <a name="remarks"></a>备注

如果滚动到一条记录和`IsDeleted`返回 TRUE （非零），则您必须向下滚动到另一个记录之前可以执行任何其他记录集操作。

结果`IsDeleted`取决于许多因素，如你的记录集类型，记录集是可更新，无论您指定`CRecordset::skipDeletedRecords`选项时是否驱动程序包删除记录，打开记录集，以及是否有多个用户。

有关详细信息`CRecordset::skipDeletedRecords`和驱动程序打包，请参阅[打开](#open)成员函数。

> [!NOTE]
>  如果已实现批量行提取，不应调用`IsDeleted`。 改为调用[GetRowStatus](#getrowstatus)成员函数。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

##  <a name="iseof"></a>  CRecordset::IsEOF

返回非零，如果在最后一条记录后定位完记录集。 没有当前记录。

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>返回值

如果记录集不包含任何记录，或如果已超出最后一条记录; 滚动，则非零值否则为 0。

### <a name="remarks"></a>备注

调用此成员函数，如从记录滚动到记录以了解是否已超出最后一个记录的记录集。 此外可以使用`IsEOF`来确定记录集是否包含任何记录，或为空。 立即调用后`Open`，如果记录集不包含任何记录，`IsEOF`返回非零值。 打开具有至少一个记录的记录集，第一条记录时的当前记录和`IsEOF`返回 0。

最后一条记录的当前记录时是否调用`MoveNext`，`IsEOF`随后将返回非零值。 如果`IsEOF`返回非零值，并且您调用`MoveNext`，出现错误。 如果`IsEOF`返回非零值时，当前记录是不确定，并需要当前记录任何操作将导致错误。

### <a name="example"></a>示例

有关示例，请参阅[IsBOF](#isbof)。

##  <a name="isfielddirty"></a>  CRecordset::IsFieldDirty

确定指定的字段数据成员是否已更改以来[编辑](#edit)或[AddNew](#addnew)调用。

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>参数

*pv*<br/>
指向字段数据成员你想要检查，则为 NULL 以确定的任何字段是否已更新其状态的指针。

### <a name="return-value"></a>返回值

如果指定的字段数据成员已更改自调用非零`AddNew`或`Edit`; 否则为 0。

### <a name="remarks"></a>备注

所有已更新字段数据成员中的数据将传输到记录上的数据源时的当前记录更新通过调用[更新](#update)成员函数`CRecordset`(到调用`Edit`或`AddNew`).

> [!NOTE]
>  此成员函数不是适用于使用的批量行提取的记录集。 如果已实现批量行提取，然后`IsFieldDirty`将始终返回 FALSE，将导致失败的断言。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

调用`IsFieldDirty`将重置以前调用的效果[SetFieldDirty](#setfielddirty)因为字段的已更新的状态是重新计算。 在`AddNew`的情况下，如果当前字段值不同于伪 null 值，将字段状态设置已更新。 在`Edit`用例中，如果字段值与不同的缓存值，则字段状态将设置已更新。

`IsFieldDirty` 通过实现[DoFieldExchange](#dofieldexchange)。

已更新标志的详细信息，请参阅文章[记录集： 如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。

##  <a name="isfieldnull"></a>  CRecordset::IsFieldNull

返回非零，如果当前记录中的指定的字段为 Null （不具有任何值）。

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>参数

*pv*<br/>
指向字段数据成员的状态，你想要进行检查，或者以确定的任何字段是否为 Null，则为 NULL 指针。

### <a name="return-value"></a>返回值

如果指定的字段数据成员标记为 Null; 非零值否则为 0。

### <a name="remarks"></a>备注

调用此成员函数可确定记录集的指定的字段数据成员是否已标记为 Null。 （在数据库术语中，Null 意味着"无值"，并且不为 NULL，c + + 中相同。）如果字段数据成员标记为 Null，它被解释为当前记录没有值的列。

> [!NOTE]
>  此成员函数不是适用于使用的批量行提取的记录集。 如果已实现批量行提取，然后`IsFieldNull`将始终返回 FALSE，将导致失败的断言。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

`IsFieldNull` 通过实现[DoFieldExchange](#dofieldexchange)。

##  <a name="isfieldnullable"></a>  CRecordset::IsFieldNullable

返回非零，如果当前记录中指定的字段可以设置为 Null （具有任何值）。

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>参数

*pv*<br/>
指向字段数据成员的状态，你想要检查，或空值，以确定是否可以进行的任何字段设置为 Null 值的指针。

### <a name="remarks"></a>备注

调用以确定是否可为"null"指定的字段数据成员 （可以是设置为一个 Null 值; 如果此成员函数C + + NULL 不是 Null，这意味着，在数据库术语中，相同"having 没有值")。

> [!NOTE]
>  如果已实现批量行提取，则不能调用`IsFieldNullable`。 改为调用[GetODBCFieldInfo](#getodbcfieldinfo)成员函数以确定是否可以将字段设置为 Null 值。 请注意，您可以始终调用`GetODBCFieldInfo`，无论是否已实现批量行提取。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

不能为 Null 的字段必须具有值。 如果您尝试将此类字段设置为 Null 添加或更新记录时，数据源会拒绝添加或更新，并[更新](#update)将引发异常。 在调用时，会发生异常`Update`，在调用时不[SetFieldNull](#setfieldnull)。

该函数的第一个参数将该函数仅适用于使用 NULL`outputColumn`字段，不`param`字段。 例如，调用

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

将仅设置`outputColumn`字段为 NULL;`param`字段不会受影响。

若要在运行`param`字段，必须提供个人的实际地址`param`你想要如：

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

这意味着您不能设置所有`param`字段为 NULL，如处理`outputColumn`字段。

`IsFieldNullable` 通过实现[DoFieldExchange](#dofieldexchange)。

##  <a name="isopen"></a>  CRecordset::IsOpen

确定记录集是否已打开。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果非零值的记录集对象[开放](#open)或[再次查询](#requery)以前调用成员函数和记录集未关闭; 否则为 0。

##  <a name="m_hstmt"></a>  CRecordset::m_hstmt

包含 ODBC 语句的数据结构，类型 HSTMT，与该记录集相关联的句柄。

### <a name="remarks"></a>备注

每个查询到 ODBC 数据源是与 HSTMT 相关联。

> [!CAUTION]
>  不要使用`m_hstmt`之前[打开](#open)已调用。

通常情况下不需要 HSTMT 直接访问，但可能需要它的直接执行 SQL 语句。 `ExecuteSQL`类的成员函数`CDatabase`提供的使用示例`m_hstmt`。

##  <a name="m_nfields"></a>  CRecordset::m_nFields

包含记录集类中; 中的字段数据成员的数目它是选定数据源的记录集的列数。

### <a name="remarks"></a>备注

记录集类的构造函数必须初始化`m_nFields`与正确的数字。 如果尚未实现批量行提取，ClassWizard 将用于声明您记录集的类时写入此初始化时。 您还可以编写它手动。

该框架使用此数字来管理的对应列的数据源上的当前记录的字段数据成员之间的交互。

> [!CAUTION]
>  此数字必须与对应的"输出列"中注册数`DoFieldExchange`或`DoBulkFieldExchange`后调用[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)与参数`CFieldExchange::outputColumn`。

可以将列绑定动态，本文中所述"记录集： 动态绑定数据列。" 如果这样做，则必须增加中的计数`m_nFields`以反映调用 RFX 或批量 RFX 函数数你`DoFieldExchange`或`DoBulkFieldExchange`动态绑定列的成员函数。

有关详细信息，请参阅文章[记录集： 动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)并[记录集： 提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

### <a name="example"></a>示例

请参阅文章[记录字段交换： 使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。

##  <a name="m_nparams"></a>  CRecordset::m_nParams

包含记录集类中; 中的参数数据成员的数目也就是说，使用记录集的查询传递的参数个数。

### <a name="remarks"></a>备注

如果记录集类具有任何参数的数据成员，类的构造函数必须初始化`m_nParams`与正确的数字。 值`m_nParams`默认值为 0。 如果添加参数的数据成员 （它们必须执行手动操作） 必须在类构造函数，以反映参数的数目也手动添加一个初始化 (它必须是至少达数 ' 中的占位符你`m_strFilter`或`m_strSort`字符串)。

参数化记录集的查询时，框架将使用此数字。

> [!CAUTION]
>  此数字必须与对应的"参数"中注册`DoFieldExchange`或`DoBulkFieldExchange`后调用[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)使用的参数值`CFieldExchange::inputParam`， `CFieldExchange::param`， `CFieldExchange::outputParam`，或`CFieldExchange::inoutParam`.

### <a name="example"></a>示例

  请参阅文章[记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)并[记录字段交换： 使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。

##  <a name="m_pdatabase"></a>  CRecordset::m_pDatabase

包含一个指向`CDatabase`对象通过该记录集与连接到数据源。

### <a name="remarks"></a>备注

两种方式设置此变量。 通常情况下，将指针传递到已连接`CDatabase`对象构造的记录集对象时。 如果传递 NULL 而`CRecordset`创建`CDatabase`对象，并将其连接。 在任一情况下，`CRecordset`将指针存储在此变量。

通常情况下不直接需要使用存储在指针`m_pDatabase`。 如果您编写自己的扩展到`CRecordset`，但是，您可能需要使用该指针。 例如，您可能需要将指针如果引发自己`CDBException`s。 或如果您需要执行一些使用的相同操作可能需要它`CDatabase`对象，如运行的事务，设置超时，或调用`ExecuteSQL`类的成员函数`CDatabase`直接执行 SQL 语句。

##  <a name="m_strfilter"></a>  CRecordset::m_strFilter

在构造记录集对象之后但在调用之前其`Open`成员函数中，使用此数据成员来存储`CString`包含 SQL**其中**子句。

### <a name="remarks"></a>备注

记录集使用此字符串来约束 （或筛选器） 期间它将选择的记录`Open`或`Requery`调用。 这可用于选择记录，例如"所有销售人员均基于加利福尼亚州"的一个子集 ("状态 = CA")。 ODBC SQL 语法**其中**子句

`WHERE search-condition`

请注意，不包括**其中**在字符串中的关键字。 框架提供了它。

您可以还通过参数化筛选器字符串放置 ' 占位符，在类中的参数数据成员声明为每个占位符，并将参数传递给记录集在运行时。 这允许您在运行时构造筛选器。 有关详细信息，请参阅文章[记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

详细了解 SQL**其中**子句，请参阅文章[SQL](../../data/odbc/sql.md)。 有关选择和筛选记录的详细信息，请参阅文章[记录集： 筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

##  <a name="m_strsort"></a>  CRecordset::m_strSort

在构造记录集对象之后但在调用之前其`Open`成员函数中，使用此数据成员来存储`CString`包含 SQL **ORDER BY**子句。

### <a name="remarks"></a>备注

记录集使用此字符串将期间选择的记录进行排序`Open`或`Requery`调用。 此功能可用于对一个或多个列上的记录集进行排序。 ODBC SQL 语法**ORDER BY**子句

`ORDER BY sort-specification [, sort-specification]...`

其中排序规范是一个整数或列名称。 此外可以通过将"ASC"或"DESC"追加到排序字符串中的列列表中指定升序或降序顺序 （默认情况下，顺序为升序）。 所选的记录排在前面的第一列列出，然后通过第二个，依次类推。 例如，您可能订购"客户"记录集的最后一个名称，则第一个名称。 可以列出的列数取决于数据源。 有关详细信息，请参阅 Windows SDK。

请注意，不包括**ORDER BY**在字符串中的关键字。 框架提供了它。

有关 SQL 子句的详细信息，请参阅文章[SQL](../../data/odbc/sql.md)。 有关对记录进行排序的详细信息，请参阅文章[记录集： 排序记录 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

##  <a name="move"></a>  CRecordset::Move

将当前记录指针集中的记录，向前或向后移动。

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>参数

*nRows*<br/>
要向前或向后移动的行数。 值为正，移动到记录集结束。 值为负向后移动的开头。

*wFetchType*<br/>
确定行集的`Move`将提取。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

如果为 0 的值传递*nRows*，`Move`刷新当前记录;`Move`将结束所有当前`AddNew`或`Edit`模式下，并且将还原之前的当前记录的值`AddNew`或`Edit`调用。

> [!NOTE]
>  当遍历一个记录集时，则不能跳过已删除的记录。 请参阅[CRecordset::IsDeleted](#isdeleted)有关详细信息。 当打开`CRecordset`与`skipDeletedRecords`选项设置，`Move`断言如果*nRows*参数为 0。 此行为可防止其他使用相同的数据的客户端应用程序被删除的行的刷新。 请参阅*dwOption*中的参数[打开](#open)有关的说明`skipDeletedRecords`。

`Move` 按行集重新定位该记录集。 根据为值*nRows*并*wFetchType*，`Move`提取相应的行集，并将第一条记录中的行集的当前记录。 如果不具有实现批量行提取，则行集大小始终为 1。 提取行集时`Move`直接调用[CheckRowsetError](#checkrowseterror)成员函数以处理导致提取的任何错误。

具体取决于您传递的值`Move`等效于其他`CRecordset`成员函数。 具体而言，值*wFetchType*可能表示一个成员函数，则更直观，并通常用于移动当前记录的首选的方法。

下表列出了可能的值为*wFetchType*，行集的`Move`将提取基于*wFetchType*并*nRows*，任何等效项成员函数将对应于*wFetchType*。

|wFetchType|提取行集|等效的成员函数|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE （默认值）|行集起始*nRows*从当前行集中的第一行的行。||
|SQL_FETCH_NEXT|下一步的行;*nRows*将被忽略。|[MoveNext](#movenext)|
|SQL_FETCH_PRIOR|上一个行集;*nRows*将被忽略。|[MovePrev](#moveprev)|
|SQL_FETCH_FIRST|记录集; 中第一个行集*nRows*将被忽略。|[MoveFirst](#movefirst)|
|SQL_FETCH_LAST|记录集; 最后一个完整行集*nRows*将被忽略。|[MoveLast](#movelast)|
|SQL_FETCH_ABSOLUTE|如果*nRows* > 0，开始的行集*nRows*从开始处的记录集的行。 如果*nRows* < 0，开始的行集*nRows*从记录集的末尾的行。 如果*nRows* = 0，则返回开头的文件 (BOF) 条件。|[SetAbsolutePosition](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|从其书签值对应的行处开始的行集*nRows*。|[SetBookmark](#setbookmark)|

> [!NOTE]
>  对于只进记录集`Move`才有效，且值为 SQL_FETCH_NEXT *wFetchType*。

> [!CAUTION]
>  调用`Move`将引发异常，如果记录集不具有任何记录。 若要确定记录集是否具有任何记录，请调用[IsBOF](#isbof)并[IsEOF](#iseof)。

> [!NOTE]
>  如果您使用滚动条滚动过去的开头或结尾，记录集的 (`IsBOF`或`IsEOF`返回非零值)，则调用`Move`函数将可能引发`CDBException`。 例如，如果`IsEOF`返回非零值和`IsBOF`却没有，然后`MoveNext`将引发异常，但`MovePrev`将不会。

> [!NOTE]
>  如果调用`Move`时的当前记录更新或添加，更新都将丢失而不发出警告。

有关记录集导航的详细信息，请参阅文章[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)并[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。 有关相关信息，请参阅 ODBC API 函数`SQLExtendedFetch`Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

##  <a name="movefirst"></a>  CRecordset::MoveFirst

使第一条记录中第一个行集的当前记录。

```
void MoveFirst();
```

### <a name="remarks"></a>备注

无论是否已实现批量行提取，此属性始终为记录集中的第一个记录。

无需调用`MoveFirst`立即打开记录集后。 此时，第一条记录 （如果有） 将自动当前记录。

> [!NOTE]
>  此成员函数不是有效的只进的记录集。

> [!NOTE]
>  当遍历一个记录集时，则不能跳过已删除的记录。 请参阅[IsDeleted](#isdeleted)成员函数的详细信息。

> [!CAUTION]
>  调用的任何`Move`函数将引发异常，如果记录集不具有任何记录。 若要确定记录集是否具有任何记录，请调用`IsBOF`和`IsEOF`。

> [!NOTE]
>  如果你调用任意`Move`函数时当前记录更新或添加，更新都将丢失而不发出警告。

有关记录集导航的详细信息，请参阅文章[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)并[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

  有关示例，请参阅[IsBOF](#isbof)。

##  <a name="movelast"></a>  CRecordset::MoveLast

使第一条记录中的最后一个完整行集的当前记录。

```
void MoveLast();
```

### <a name="remarks"></a>备注

如果你尚未实现批量行提取，记录集具有的行集大小为 1，因此`MoveLast`只需将移到最后一个记录中记录集。

> [!NOTE]
>  此成员函数不是有效的只进的记录集。

> [!NOTE]
>  当遍历一个记录集时，则不能跳过已删除的记录。 请参阅[IsDeleted](#isdeleted)成员函数的详细信息。

> [!CAUTION]
>  调用的任何`Move`函数将引发异常，如果记录集不具有任何记录。 若要确定记录集是否具有任何记录，请调用`IsBOF`和`IsEOF`。

> [!NOTE]
>  如果你调用任意`Move`函数时当前记录更新或添加，更新都将丢失而不发出警告。

有关记录集导航的详细信息，请参阅文章[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)并[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

  有关示例，请参阅[IsBOF](#isbof)。

##  <a name="movenext"></a>  CRecordset::MoveNext

使第一条记录中的下一步的行集的当前记录。

```
void MoveNext();
```

### <a name="remarks"></a>备注

如果你尚未实现批量行提取，记录集具有的行集大小为 1，因此`MoveNext`只需将其移动到下一条记录。

> [!NOTE]
>  当遍历一个记录集时，则不能跳过已删除的记录。 请参阅[IsDeleted](#isdeleted)成员函数的详细信息。

> [!CAUTION]
>  调用的任何`Move`函数将引发异常，如果记录集不具有任何记录。 若要确定记录集是否具有任何记录，请调用`IsBOF`和`IsEOF`。

> [!NOTE]
>  此外建议您调用`IsEOF`之前调用`MoveNext`。 例如，如果您使用滚动条滚动的记录集，或结尾`IsEOF`将返回非零值; 的后续调用`MoveNext`会引发异常。

> [!NOTE]
>  如果你调用任意`Move`函数时当前记录更新或添加，更新都将丢失而不发出警告。

有关记录集导航的详细信息，请参阅文章[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)并[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

  有关示例，请参阅[IsBOF](#isbof)。

##  <a name="moveprev"></a>  CRecordset::MovePrev

使当前记录的上一个行集的第一个记录。

```
void MovePrev();
```

### <a name="remarks"></a>备注

如果你尚未实现批量行提取，记录集具有的行集大小为 1，因此`MovePrev`只需将其移动到上一条记录。

> [!NOTE]
>  此成员函数不是有效的只进的记录集。

> [!NOTE]
>  当遍历一个记录集时，则不能跳过已删除的记录。 请参阅[IsDeleted](#isdeleted)成员函数的详细信息。

> [!CAUTION]
>  调用的任何`Move`函数将引发异常，如果记录集不具有任何记录。 若要确定记录集是否具有任何记录，请调用`IsBOF`和`IsEOF`。

> [!NOTE]
>  此外建议您调用`IsBOF`之前调用`MovePrev`。 例如，如果滚，记录集的开头`IsBOF`将返回非零值; 的后续调用`MovePrev`会引发异常。

> [!NOTE]
>  如果你调用任意`Move`函数时当前记录更新或添加，更新都将丢失而不发出警告。

有关记录集导航的详细信息，请参阅文章[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)并[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

  有关示例，请参阅[IsBOF](#isbof)。

##  <a name="onsetoptions"></a>  CRecordset::OnSetOptions

调用以设置 （使用所选内容上） 的选项为指定的 ODBC 语句。

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>参数

*hstmt*<br/>
ODBC 语句的选项，可设置的 HSTMT。

### <a name="remarks"></a>备注

调用`OnSetOptions`为指定的 ODBC 语句设置选项 （使用所选内容上）。 框架调用此成员函数以设置记录集的初始选项。 `OnSetOptions` 确定对于可滚动游标和游标并发的数据源的支持，并相应地设置记录集的选项。 (而`OnSetOptions`用于选择操作`OnSetUpdateOptions`用于更新操作。)

重写`OnSetOptions`来设置特定于驱动程序或数据源选项。 例如，如果你的数据源进行独占访问打开的支持，您可能会替代`OnSetOptions`以充分利用该功能。

有关游标的详细信息，请参阅文章[ODBC](../../data/odbc/odbc-basics.md)。

##  <a name="onsetupdateoptions"></a>  CRecordset::OnSetUpdateOptions

调用以设置指定的 ODBC 语句 （适用于更新） 的选项。

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>参数

*hstmt*<br/>
ODBC 语句的选项，可设置的 HSTMT。

### <a name="remarks"></a>备注

调用`OnSetUpdateOptions`为指定的 ODBC 语句设置选项 （适用于更新）。 创建 HSTMT 更新记录集中的记录后，框架将调用此成员函数。 (而`OnSetOptions`用于选择操作`OnSetUpdateOptions`用于更新操作。)`OnSetUpdateOptions`确定对于可滚动游标和游标并发的数据源的支持，并相应地设置记录集的选项。

重写`OnSetUpdateOptions`设置 ODBC 语句的选项，然后该语句用于访问数据库。

有关游标的详细信息，请参阅文章[ODBC](../../data/odbc/odbc-basics.md)。

##  <a name="open"></a>  Crecordset:: Open

通过检索表或执行的查询的记录集表示打开记录集。

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>参数

*nOpenType*<br/>
接受默认值、 AFX_DB_USE_DEFAULT_TYPE 或使用以下值之一从`enum OpenType`:

- `CRecordset::dynaset` 与双向滚动记录集。 打开记录集，但由其他用户对数据值所做的更改会显示以下提取操作时确定成员身份和顺序的记录。 动态集也称为是由键集驱动的记录集。

- `CRecordset::snapshot` 静态记录集包含的双向滚动。 打开记录集; 时确定成员身份和顺序的记录提取记录时确定的数据值。 后，关闭，然后重新打开记录集，由其他用户所做的更改不可见。

- `CRecordset::dynamic` 与双向滚动记录集。 会显示以下提取操作的成员身份、 排序和数据值的其他用户所做的更改。 请注意，很多 ODBC 驱动程序不支持这种类型的记录集。

- `CRecordset::forwardOnly` 而只向前滚动只读的记录集。

   有关`CRecordset`，默认值是`CRecordset::snapshot`。 默认值机制允许 Visual c + + 向导以便与这两个 ODBC`CRecordset`和 DAO `CDaoRecordset`，它具有不同的默认值。

有关这些记录集类型的详细信息，请参阅文章[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)。 有关相关信息，请参阅文章"使用块游标和可滚动游标"Windows SDK 中。

> [!CAUTION]
>  如果不支持所请求的类型，该框架将引发异常。

*lpszSQL*<br/>
字符串指针，其中包含以下项之一：

- NULL 指针。

- 表的名称。

- SQL**选择**语句 (根据需要使用 SQL**其中**或**ORDER BY**子句)。

- 一个**调用**语句并指定预定义查询 （存储过程） 的名称。 请注意没有插入大括号之间空格和**调用**关键字。

有关此字符串的详细信息，请参阅表和备注 ClassWizard 的角色的讨论。

> [!NOTE]
>  在结果集中列的顺序必须与 RFX 的顺序匹配或批量 RFX 函数调用中您[DoFieldExchange](#dofieldexchange)或[DoBulkFieldExchange](#dobulkfieldexchange)函数重写。

*dwOptions*<br/>
一个位掩码，可以指定下面列出的值的组合。 其中一些是相互排斥的。 默认值是**none**。

- `CRecordset::none` 未设置选项。 此参数值是与所有其他值相互排斥。 默认情况下，可以使用更新记录集[编辑](#edit)或[删除](#delete)，并允许追加新记录以及[AddNew](#addnew)。 可更新性取决于数据源以及*nOpenType*您指定的选项。 优化大容量补充内容不可用。 不会实现批量行提取。 已删除的记录不能跳过在记录集中导航。 书签将不可用。 实现自动脏字段检查。

- `CRecordset::appendOnly` 不允许`Edit`或`Delete`上该记录集。 允许`AddNew`仅。 此选项是互斥的与`CRecordset::readOnly`。

- `CRecordset::readOnly` 打开记录集持久化为只读的。 此选项是互斥的与`CRecordset::appendOnly`。

- `CRecordset::optimizeBulkAdd` 已准备的 SQL 语句用于优化一次添加多个记录。 不使用 ODBC API 函数时才应用`SQLSetPos`来更新该记录集。 第一次更新确定哪些字段标记为已更新。 此选项是互斥的与`CRecordset::useMultiRowFetch`。

- `CRecordset::useMultiRowFetch` 实现批量行提取，以允许多个要在单个提取操作中检索的行。 这是一项高级的功能设计用于提高性能;但是，ClassWizard 不支持批量记录字段交换。 此选项是互斥的与`CRecordset::optimizeBulkAdd`。 请注意，如果您指定`CRecordset::useMultiRowFetch`，然后选择`CRecordset::noDirtyFieldCheck`将自动开启 （双缓冲将不可用）; 在仅正向记录集中，该选项`CRecordset::useExtendedFetch`将自动打开。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

- `CRecordset::skipDeletedRecords` 在记录集中导航时，请跳过所有已删除的记录。 这会降低某些相对提取操作中的性能。 此选项只进的记录集上无效。 如果在调用[移动](#move)与*nRows*参数设置为 0，并且`CRecordset::skipDeletedRecords`选项集，`Move`将断言。 请注意，`CRecordset::skipDeletedRecords`类似于*驱动程序封装*，这意味着，已删除的行已从记录集。 但是，如果您的驱动程序包记录，然后它将跳过删除; 这些记录它将跳过该记录集处于打开状态时删除其他用户的记录。 `CRecordset::skipDeletedRecords` 将跳过的其他用户删除的行。

- `CRecordset::useBookmarks` 可以使用记录集上的书签，如果受支持。 书签降低数据检索，但提高性能的数据导航。 对只进的记录集不有效。 有关详细信息，请参阅文章[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。

- `CRecordset::noDirtyFieldCheck` 关闭自动脏字段检查 （双缓冲）。 这将提高性能;但是，您必须手动标记的字段为脏通过调用`SetFieldDirty`和`SetFieldNull`成员函数。请注意在类中的双缓冲`CRecordset`类似于类中的双缓冲`CDaoRecordset`。 但是，在`CRecordset`，你不能启用对各个字段的双缓冲; 对于所有字段启用或禁用的所有字段。 请注意，如果指定了选项`CRecordset::useMultiRowFetch`，然后`CRecordset::noDirtyFieldCheck`自动; 但是，将开启`SetFieldDirty`和`SetFieldNull`不能实现批量行提取的记录集上使用。

- `CRecordset::executeDirect` 不要使用预定义的 SQL 语句。 如果，则为改进性能，指定此选项`Requery`永远不会调用成员函数。

- `CRecordset::useExtendedFetch` 实现`SQLExtendedFetch`而不是`SQLFetch`。 这被设计用于实现批量行提取的只进的记录集。 如果指定了选项`CRecordset::useMultiRowFetch`只进记录集，然后`CRecordset::useExtendedFetch`将自动打开。

- `CRecordset::userAllocMultiRowBuffers` 用户将数据分配存储缓冲区。 使用此选项结合`CRecordset::useMultiRowFetch`如果你想要分配你自己的存储; 否则，该框架将自动分配必要的存储。 有关详细信息，请参阅文章[记录集： 提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 请注意该指定`CRecordset::userAllocMultiRowBuffers`而无需指定`CRecordset::useMultiRowFetch`将导致失败的断言。

### <a name="return-value"></a>返回值

如果非零`CRecordset`对象已成功打开; 否则为 0 [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) （如果调用），则返回 0。

### <a name="remarks"></a>备注

必须调用此成员函数以运行查询定义的记录集。 然后再调用`Open`，必须构造记录集对象。

此记录集的数据源连接取决于如何构造之前，调用记录集`Open`。 如果传递[CDatabase](../../mfc/reference/cdatabase-class.md)对象复制到尚未连接到数据源的记录集构造函数使用此成员函数[GetDefaultConnect](#getdefaultconnect)尝试打开的数据库对象。 如果将 NULL 传递给记录集构造函数中，构造函数将构造`CDatabase`对象，和`Open`尝试连接的数据库对象。 关闭记录集和这些不同情况下的连接的详细信息，请参阅[关闭](#close)。

> [!NOTE]
>  通过数据源访问的`CRecordset`始终共享对象。 与不同`CDaoRecordset`类，不能使用`CRecordset`对象以获得独占访问权限打开数据源。

当您调用`Open`，一个查询，通常 SQL**选择**语句中，选择以下表中所示的条件的记录。

|LpszSQL 参数的值|取决于选择的记录|示例|
|------------------------------------|----------------------------------------|-------------|
|NULL|返回的字符串`GetDefaultSQL`。||
|SQL 表名称|中的表列表中的所有列`DoFieldExchange`或`DoBulkFieldExchange`。|`"Customer"`|
|预定义的查询 （存储过程） 名称|查询定义要返回的列。|`"{call OverDueAccts}"`|
|**选择**列列表**FROM**表列表|指定表中的指定的列。|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
>  请谨慎执行 SQL 字符串中插入额外的空格。 例如，如果插入大括号之间空格和**调用**关键字，MFC 将解释为表名的 SQL 字符串和融入**选择**语句，这将导致所引发的异常。 同样，如果预定义的查询使用输出参数，不能插入大括号之间的空白和 ' 符号。 最后，不能插入之前的大括号中的空格**调用**语句或之前**选择**中的关键字**选择**语句。

常规步骤是将传递到 NULL `Open`; 在这种情况下，`Open`调用[GetDefaultSQL](#getdefaultsql)。 如果您使用的派生`CRecordset`类，`GetDefaultSQL`提供类向导中指定的表名称。 您可以指定中的其他信息`lpszSQL`参数。

您传递的任何`Open`构造查询的最终 SQL 字符串 (字符串可能具有 SQL**其中**和**ORDER BY**子句追加到`lpszSQL`您传递的字符串)，然后再执行该查询。 可以通过调用检查构造的字符串[GetSQL](#getsql)之后调用`Open`。 有关如何记录集构造 SQL 语句，并选择记录，有关其他详细信息，请参阅文章[记录集： 如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。

记录集类的字段数据成员绑定到所选的数据的列。 如果未返回任何记录，第一条记录将成为当前记录。

如果你想要设置的记录集，如筛选或排序，选项指定这些属性构造记录集对象之后但在调用之前`Open`。 如果你想要刷新后记录集中记录的记录集已打开，请调用[再次查询](#requery)。

有关详细信息，包括其他示例，请参阅文章[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)，[记录集： 如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)，和[记录集： 创建和关闭记录集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。

### <a name="example"></a>示例

下面的代码示例演示不同形式的`Open`调用。

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

##  <a name="refreshrowset"></a>  CRecordset::RefreshRowset

更新数据和当前行集中的行的状态。

```
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>参数

*wRow*<br/>
基于 1 的行位置的当前行集中。 此值可以介于 0 到行集的大小。

*wLockType*<br/>
一个值，该值指示如何将该行锁定后已刷新。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

如果为零的值传递*wRow*，然后将刷新行集中的每个行。

若要使用`RefreshRowset`，你必须具有实现批量行提取通过指定`CRecordset::useMulitRowFetch`选项[打开](#open)成员函数。

`RefreshRowset` 调用 ODBC API 函数`SQLSetPos`。 *WLockType*参数指定的行后的锁定状态`SQLSetPos`已执行。 下表描述了可能的值为*wLockType*。

|wLockType|描述|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE （默认值）|驱动程序或数据源可确保之前的一行是相同的锁定或解锁状态`RefreshRowset`调用。|
|SQL_LOCK_EXCLUSIVE|驱动程序或数据源以独占方式锁定行。 并非所有数据源都支持这种类型的锁。|
|SQL_LOCK_UNLOCK|驱动程序或数据源对行进行解锁。 并非所有数据源都支持这种类型的锁。|

有关详细信息`SQLSetPos`，请参阅 Windows SDK。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

##  <a name="requery"></a>  CRecordset::Requery

重新生成 （刷新） 记录集。

```
virtual BOOL Requery();
```

### <a name="return-value"></a>返回值

记录集已成功重新生成; 如果非零值否则为 0。

### <a name="remarks"></a>备注

如果未返回任何记录，第一条记录将成为当前记录。

为了使该记录集，以反映添加和删除操作，您或其他用户对数据源，必须重新记录集生成通过调用`Requery`。 如果记录集是动态集，它会自动反映您或其他用户对其现有的记录 （但不是添加件） 进行的更新。 如果记录集是快照，则必须调用`Requery`以反映由其他用户，以及添加和删除操作的编辑。

对于动态集或快照中，调用`Requery`任何时候你想要重新生成使用新的筛选器或排序或新的参数值的记录集。 分配到的新值来设置新的筛选或排序属性`m_strFilter`并`m_strSort`然后才能调用`Requery`。 通过将新值分配给之前调用的参数数据成员设置新的参数`Requery`。 如果筛选器和排序字符串未发生更改，可以重复使用查询，这将提高性能。

如果重新生成该记录集的尝试失败，则关闭记录集。 在调用之前`Requery`，可以确定记录集是否可以通过调用重新查询`CanRestart`成员函数。 `CanRestart` 并不保证`Requery`将会成功。

> [!CAUTION]
>  调用`Requery`之后调用仅[打开](#open)。

### <a name="example"></a>示例

此示例重新生成一个记录集应用不同的排序顺序。

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

##  <a name="setabsoluteposition"></a>  CRecordset::SetAbsolutePosition

定位到指定的记录号相对应的记录的记录集。

```
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>参数

*nRows*<br/>
基于 1 的序号位置的当前记录中记录集。

### <a name="remarks"></a>备注

`SetAbsolutePosition` 将当前记录指针根据此序号位置。

> [!NOTE]
>  此成员函数上只进的记录集无效。

对于 ODBC 记录集的绝对位置设置为 1 是指在记录集; 中的第一个记录设置为 0 是指开头的文件 (BOF) 位置。

你还可以传递到负值`SetAbsolutePosition`。 在这种情况下，记录集的末尾都被计算记录集的位置。 例如，`SetAbsolutePosition( -1 )`将当前记录指针移动到记录集中的最后一个记录。

> [!NOTE]
>  绝对位置不是要用作代理记录编号。 书签仍是保留和返回到给定位置，因为记录的位置发生更改时将删除前面记录的推荐的方法。 此外，则不能确保如果重新因为除非创建和使用SQL语句，否则不能保证在记录集内的单个记录的顺序重新创建记录集，给定的记录将具有相同的绝对位置**ORDER BY**子句。

有关记录集导航和书签的详细信息，请参阅文章[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)并[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。

##  <a name="setbookmark"></a>  CRecordset::SetBookmark

定位记录集包含指定的书签的记录。

```
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>参数

*varBookmark*<br/>
对引用[CDBVariant](../../mfc/reference/cdbvariant-class.md)对象，其中包含特定记录的书签值。

### <a name="remarks"></a>备注

若要确定是否记录集上支持书签，请调用[CanBookmark](#canbookmark)。 若要使书签可用，如果它们受支持，必须设置`CRecordset::useBookmarks`选项*dwOptions*参数[打开](#open)成员函数。

> [!NOTE]
>  如果书签不受支持或不可用，则调用`SetBookmark`将导致引发异常。 只进的记录集不支持书签。

若要首先检索当前记录的书签，请调用[GetBookmark](#getbookmark)，这将保存到的书签值`CDBVariant`对象。 更高版本，你可以通过返回到该记录调用`SetBookmark`使用已保存的书签值。

> [!NOTE]
>  某些记录集在操作之后，应检查之前，调用书签暂留`SetBookmark`。 例如，如果检索具有书签`GetBookmark`，然后调用`Requery`，书签可能不再有效。 调用[CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)若要检查是否可以安全地调用`SetBookmark`。

有关书签和记录集导航的详细信息，请参阅文章[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)并[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。

##  <a name="setfielddirty"></a>  CRecordset::SetFieldDirty

标记为已更改的记录集或为未更改的字段数据成员。

```
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>参数

*pv*<br/>
包含中的记录集或为 NULL 的字段数据成员的地址。 如果为 NULL，将标记为记录集中的所有字段数据成员。 (C + + NULL 不是 Null 相同数据库术语中，这意味着"无任何值。")

*bDirty*<br/>
如果字段数据成员是被标记为"更新"（更改），则为 TRUE。 如果字段数据成员将会被标记为"清理"（未更改）; 否则为 FALSE。

### <a name="remarks"></a>备注

将标记为未更改的字段可确保该字段不更新，并且会导致较少 SQL 流量。

> [!NOTE]
>  此成员函数不是适用于使用的批量行提取的记录集。 如果已实现批量行提取，然后`SetFieldDirty`将导致失败的断言。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

Framework 标记更改字段数据成员，以确保它们将写入到数据源上的记录的记录字段交换 (RFX) 机制。 将更改字段的值通常字段已更新会自动设置，因此很少需要调用`SetFieldDirty`自己，但您有时可能想要确保，列将显式更新或插入而不考虑哪些值是字段数据成员。

> [!CAUTION]
>  调用此成员函数才具有名为[编辑](#edit)或[AddNew](#addnew)。

该函数的第一个参数将该函数仅适用于使用 NULL`outputColumn`字段，不`param`字段。 例如，调用

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

将仅设置`outputColumn`字段为 NULL;`param`字段不会受影响。

若要在运行`param`字段，必须提供个人的实际地址`param`你想要如：

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

这意味着您不能设置所有`param`字段为 NULL，如处理`outputColumn`字段。

##  <a name="setfieldnull"></a>  CRecordset::SetFieldNull

为 Null （特别具有任何值） 或为非 Null 标志记录集字段数据的成员。

```
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>参数

*pv*<br/>
包含中的记录集或为 NULL 的字段数据成员的地址。 如果为 NULL，将标记为记录集中的所有字段数据成员。 (C + + NULL 不是 Null 相同数据库术语中，这意味着"无任何值。")

*bNull*<br/>
如果字段数据成员是被标记为不具有任何值 (Null)，非零值。 否则为 0 的字段数据成员是否被标记为非 Null。

### <a name="remarks"></a>备注

当你将一条新记录添加到记录集时，所有字段数据成员是最初设置为 Null 值和标记为"更新"（更改）。 当从数据源检索一条记录时，其列已具有的值或均为 Null。

> [!NOTE]
>  请勿在使用批量行提取的记录集上调用此成员函数。 如果已实现批量行提取，则调用`SetFieldNull`导致失败的断言。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

如果您特别希望将当前记录的字段指定为不具有一个值，调用`SetFieldNull`与*bNull*设置为 TRUE 以标记为 Null。 如果以前标记的字段为 Null，并且现在想要为其提供一个值，只需设置它的新值。 无需删除具有 Null 标志`SetFieldNull`。 若要确定是否允许该字段为 Null，请调用`IsFieldNullable`。

> [!CAUTION]
>  调用此成员函数才具有名为[编辑](#edit)或[AddNew](#addnew)。

该函数的第一个参数将该函数仅适用于使用 NULL`outputColumn`字段，不`param`字段。 例如，调用

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

将仅设置`outputColumn`字段为 NULL;`param`字段不会受影响。

若要在运行`param`字段，必须提供个人的实际地址`param`你想要如：

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

这意味着您不能设置所有`param`字段为 NULL，如处理`outputColumn`字段。

> [!NOTE]
>  将参数设置为 Null，调用时`SetFieldNull`记录集是在断言中的打开的结果之前。 在这种情况下，调用[SetParamNull](#setparamnull)。

`SetFieldNull` 通过实现[DoFieldExchange](#dofieldexchange)。

##  <a name="setlockingmode"></a>  CRecordset::SetLockingMode

设置为"开放式"锁定 （默认值） 或"保守式"锁定的锁定模式。 确定如何更新锁定的记录。

```
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>参数

*nMode*<br/>
包含中的以下值之一`enum LockMode`:

- `optimistic` 仅在调用过程正在更新的记录进行乐观锁定锁定`Update`。

- `pessimistic` 保守式锁定的记录进行锁定就立即`Edit`调用，并将其锁定之前保留`Update`调用完成或移动到新的记录。

### <a name="remarks"></a>备注

如果你需要指定这两个记录集使用更新的记录锁定的策略，请调用此成员函数。 默认情况下，记录集的锁定模式是`optimistic`。 您可以更改为更加小心`pessimistic`锁定策略。 调用`SetLockingMode`构造并打开记录集对象之后但在调用之前`Edit`。

##  <a name="setparamnull"></a>  CRecordset::SetParamNull

标记参数为 Null （特别具有任何值） 或为非 Null。

```
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
参数的从零开始的索引。

*bNull*<br/>
如果 TRUE （默认值），则该参数标记为 Null。 否则，该参数将标记为非 Null。

### <a name="remarks"></a>备注

与不同[SetFieldNull](#setfieldnull)，可以调用`SetParamNull`之前已打开记录集。

`SetParamNull` 通常与预定义的查询 （存储过程） 一起使用。

##  <a name="setrowsetcursorposition"></a>  CRecordset::SetRowsetCursorPosition

将光标移到当前行集内的行。

```
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>参数

*wRow*<br/>
基于 1 的行位置的当前行集中。 此值的范围是从 1 到行集的大小。

*wLockType*<br/>
值，该值指示如何将该行锁定后已刷新。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

在实现批量取行时，通过行集，其中第一个记录中提取行集是当前记录检索记录。 若要使该行集内的另一条记录的当前记录，调用`SetRowsetCursorPosition`。 例如，您可以将结合`SetRowsetCursorPosition`与[GetFieldValue](#getfieldvalue)成员函数以动态地从记录集的任何记录中检索数据。

若要使用`SetRowsetCursorPosition`，你必须具有实现批量行提取通过指定`CRecordset::useMultiRowFetch`的选项*dwOptions*中的参数[打开](#open)成员函数。

`SetRowsetCursorPosition` 调用 ODBC API 函数`SQLSetPos`。 *WLockType*参数指定的行后的锁定状态`SQLSetPos`已执行。 下表描述了可能的值为*wLockType*。

|wLockType|描述|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE （默认值）|驱动程序或数据源可确保之前的一行是相同的锁定或解锁状态`SetRowsetCursorPosition`调用。|
|SQL_LOCK_EXCLUSIVE|驱动程序或数据源以独占方式锁定行。 并非所有数据源都支持这种类型的锁。|
|SQL_LOCK_UNLOCK|驱动程序或数据源对行进行解锁。 并非所有数据源都支持这种类型的锁。|

有关详细信息`SQLSetPos`，请参阅 Windows SDK。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

##  <a name="setrowsetsize"></a>  CRecordset::SetRowsetSize

指定你想要在提取过程中检索的记录数。

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>参数

*dwNewRowsetSize*<br/>
要在给定提取过程中检索的行数。

### <a name="remarks"></a>备注

此虚拟成员函数可指定你想要在单个提取过程中使用批量行提取时检索的行数。 若要实现批量行提取，必须设置`CRecordset::useMultiRowFetch`选项*dwOptions*参数[打开](#open)成员函数。

> [!NOTE]
>  调用`SetRowsetSize`而无需实现批量行提取将导致失败的断言。

调用`SetRowsetSize`之前调用`Open`最初设置记录集的行集大小。 实现批量行提取时的默认行集大小为 25。

> [!NOTE]
>  调用时要格外小心`SetRowsetSize`。 如果手动分配存储的数据 (所指定的`CRecordset::userAllocMultiRowBuffers`dwOptions 参数中的选项`Open`)，应检查是否需要调用后重新分配这些存储缓冲区`SetRowsetSize`，但在之前执行任何游标导航操作。

若要获取的行集大小的当前设置，请调用[GetRowsetSize](#getrowsetsize)。

有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

##  <a name="update"></a>  CRecordset::Update

完成`AddNew`或`Edit`通过将新的或编辑数据保存在数据源上的操作。

```
virtual BOOL Update();
```

### <a name="return-value"></a>返回值

已成功更新一条记录; 如果非零值否则为 0，如果没有列已发生更改。 如果没有更新任何记录，或者如果有多个已更新一个记录，将引发异常。 也会引发异常的任何其他故障对数据源。

### <a name="remarks"></a>备注

在调用后调用此成员函数[AddNew](#addnew)或[编辑](#edit)成员函数。 完成所需的此调用`AddNew`或`Edit`操作。

> [!NOTE]
>  如果已实现批量行提取，则不能调用`Update`。 这将导致失败的断言。 尽管类`CRecordset`不提供一种机制，用于更新的数据大容量行，可以编写您自己的函数，通过使用 ODBC API 函数`SQLSetPos`。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

这两`AddNew`和`Edit`准备对保存到数据源添加或编辑过的数据放置在该域中的编辑缓冲区。 `Update` 保存数据。 只有这些字段标记为或检测到因为更改会更新。

如果数据源支持事务，则可以进行`Update`调用 (和其对应`AddNew`或`Edit`调用) 事务的一部分。 有关事务的详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。

> [!CAUTION]
>  如果您调用`Update`而不必首先调用`AddNew`或`Edit`，`Update`引发`CDBException`。 如果您调用`AddNew`或`Edit`，必须调用`Update`之前调用`Move`操作或之前关闭记录集或数据源连接。 否则，所做的更改都将丢失而不另行通知。

有关处理的详细信息`Update`失败，请参阅文章[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

### <a name="example"></a>示例

请参阅文章[事务： 在记录集 (ODBC) 执行的事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDatabase 类](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView 类](../../mfc/reference/crecordview-class.md)
