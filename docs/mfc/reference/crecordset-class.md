---
title: CRecordset 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 1ebdb18254171d28b5d5e02367596b79142df284
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626191"
---
# <a name="crecordset-class"></a>CRecordset 类

表示从数据源选择的一组记录。

## <a name="syntax"></a>语法

```
class CRecordset : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CRecordset：： CRecordset](#crecordset)|构造 `CRecordset` 对象。 派生类必须提供调用此类的构造函数。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CRecordset：： AddNew](#addnew)|准备添加新记录。 调用 `Update` 以完成加法。|
|[CRecordset：： CanAppend](#canappend)|如果可以通过 `AddNew` 成员函数将新记录添加到记录集中，则返回非零值。|
|[CRecordset：： CanBookmark](#canbookmark)|如果记录集支持书签，则返回非零值。|
|[CRecordset：： Cancel](#cancel)|取消异步操作或来自另一个线程的进程。|
|[CRecordset：： CancelUpdate](#cancelupdate)|取消任何挂起的更新，因为 `AddNew` 或 `Edit` 操作。|
|[CRecordset：： CanRestart](#canrestart)|如果可以调用 `Requery` 以重新运行记录集的查询，则返回非零值。|
|[CRecordset：： CanScroll](#canscroll)|如果可以滚动记录，则返回非零值。|
|[CRecordset：： CanTransact](#cantransact)|如果数据源支持事务，则返回非零值。|
|[CRecordset：： CanUpdate](#canupdate)|如果可以更新记录集（您可以添加、更新或删除记录），则返回非零值。|
|[CRecordset：： CheckRowsetError](#checkrowseterror)|调用以处理在记录提取过程中生成的错误。|
|[CRecordset：： Close](#close)|关闭记录集和与其关联的 ODBC HSTMT。|
|[CRecordset：:D e)](#delete)|从记录集中删除当前记录。 删除后，必须显式滚动到其他记录。|
|[CRecordset：:D oBulkFieldExchange](#dobulkfieldexchange)|调用以将数据源中的批量数据行交换到记录集。 实现批量记录字段交换（Bulk RFX）。|
|[CRecordset：:D oFieldExchange](#dofieldexchange)|调用以在记录集的字段数据成员和数据源的相应记录之间交换数据（双向）。 实现记录字段交换（RFX）。|
|[CRecordset：： Edit](#edit)|准备当前记录的更改。 调用 `Update` 以完成编辑。|
|[CRecordset：： FlushResultSet](#flushresultset)|当使用预定义的查询时，如果要检索另一个结果集，则返回非零值。|
|[CRecordset：： GetBookmark](#getbookmark)|将记录的书签值分配给 parameter 对象。|
|[CRecordset：： GetDefaultConnect](#getdefaultconnect)|调用以获取默认的连接字符串。|
|[CRecordset：： GetDefaultSQL](#getdefaultsql)|调用以获取要执行的默认 SQL 字符串。|
|[CRecordset：： GetFieldValue](#getfieldvalue)|返回记录集中某个字段的值。|
|[CRecordset：： GetODBCFieldCount](#getodbcfieldcount)|返回记录集中的字段数。|
|[CRecordset：： GetODBCFieldInfo](#getodbcfieldinfo)|返回有关记录集中字段的特定类型的信息。|
|[CRecordset：： GetRecordCount](#getrecordcount)|返回记录集中的记录数。|
|[CRecordset：： GetRowsetSize](#getrowsetsize)|返回一次提取时要检索的记录数。|
|[CRecordset：： GetRowsFetched](#getrowsfetched)|返回在提取过程中检索到的实际行数。|
|[CRecordset：： GetRowStatus](#getrowstatus)|返回提取后行的状态。|
|[CRecordset：： GetSQL](#getsql)|获取用于为记录集选择记录的 SQL 字符串。|
|[CRecordset：： GetStatus](#getstatus)|获取记录集的状态：当前记录的索引和是否已获取记录的最终计数。|
|[CRecordset：： GetTableName](#gettablename)|获取记录集所基于的表的名称。|
|[CRecordset：： IsBOF](#isbof)|如果记录集已定位在第一条记录之前，则返回非零值。 没有当前记录。|
|[CRecordset：： IsDeleted](#isdeleted)|如果记录集位于已删除记录上，则返回非零值。|
|[CRecordset：： IsEOF](#iseof)|如果记录集位于最后一条记录之后，则返回非零值。 没有当前记录。|
|[CRecordset：： IsFieldDirty](#isfielddirty)|如果当前记录中的指定字段已更改，则返回非零值。|
|[CRecordset：： IsFieldNull](#isfieldnull)|如果当前记录中的指定字段为空（没有值），则返回非零值。|
|[CRecordset：： IsFieldNullable](#isfieldnullable)|如果可以将当前记录中的指定字段设置为 null （没有值），则返回非零值。|
|[CRecordset：： IsOpen](#isopen)|如果以前调用了 `Open`，则返回非零值。|
|[CRecordset：： Move](#move)|将记录集定位到任一方向的当前记录中的指定数量的记录。|
|[CRecordset：： MoveFirst](#movefirst)|定位记录集中第一条记录上的当前记录。 首先测试 `IsBOF`。|
|[CRecordset：： MoveLast](#movelast)|定位最后一条记录或最后一个行集的当前记录。 首先测试 `IsEOF`。|
|[CRecordset：： MoveNext](#movenext)|将当前记录定位到下一条记录或下一个行集。 首先测试 `IsEOF`。|
|[CRecordset：： MovePrev](#moveprev)|定位上一条记录或上一个行集的当前记录。 首先测试 `IsBOF`。|
|[CRecordset：： OnSetOptions](#onsetoptions)|调用以设置指定 ODBC 语句的选项（在选择时使用）。|
|[CRecordset：： OnSetUpdateOptions](#onsetupdateoptions)|调用以设置指定 ODBC 语句的选项（在更新时使用）。|
|[CRecordset：： Open](#open)|通过检索表或执行记录集表示的查询打开记录集。|
|[CRecordset：： RefreshRowset](#refreshrowset)|刷新指定行的数据和状态。|
|[CRecordset：： Requery](#requery)|再次运行记录集的查询以刷新所选记录。|
|[CRecordset：： SetAbsolutePosition](#setabsoluteposition)|定位与指定记录号对应的记录上的记录集。|
|[CRecordset：： SetBookmark](#setbookmark)|将记录集定位于书签指定的记录上。|
|[CRecordset：： SetFieldDirty](#setfielddirty)|将当前记录中的指定字段标记为已更改。|
|[CRecordset：： SetFieldNull](#setfieldnull)|将当前记录中指定字段的值设置为 null （没有值）。|
|[CRecordset：： SetLockingMode](#setlockingmode)|将锁定模式设置为 "乐观" 锁定（默认值）或 "悲观" 锁定。 确定如何锁定记录以获取更新。|
|[CRecordset：： SetParamNull](#setparamnull)|将指定参数设置为 null （没有值）。|
|[CRecordset：： SetRowsetCursorPosition](#setrowsetcursorposition)|将光标置于行集中指定的行上。|
|[CRecordset：： SetRowsetSize](#setrowsetsize)|指定在提取过程中要检索的记录数。|
|[CRecordset：： Update](#update)|通过保存数据源上的新数据或编辑的数据来完成 `AddNew` 或 `Edit` 操作。|

### <a name="public-data-members"></a>公共数据成员

|“属性”|描述|
|----------|-----------------|
|[CRecordset：： m_hstmt](#m_hstmt)|包含记录集的 ODBC 语句句柄。 键入 `HSTMT`。|
|[CRecordset：： m_nFields](#m_nfields)|包含记录集中的字段数据成员数。 键入 `UINT`。|
|[CRecordset：： m_nParams](#m_nparams)|包含记录集中的参数数据成员数。 键入 `UINT`。|
|[CRecordset：： m_pDatabase](#m_pdatabase)|包含一个指向 `CDatabase` 对象的指针，该对象通过该对象将记录集连接到数据源。|
|[CRecordset：： m_strFilter](#m_strfilter)|包含指定结构化查询语言（SQL） `WHERE` 子句的 `CString`。 用作筛选器，以仅选择符合特定条件的那些记录。|
|[CRecordset：： m_strSort](#m_strsort)|包含指定 SQL `ORDER BY` 子句的 `CString`。 用于控制记录的排序方式。|

## <a name="remarks"></a>备注

通常在两种形式下使用 "记录集" `CRecordset` 对象：动态集和快照。 动态集中与其他用户所做的数据更新保持同步。 快照是数据的静态视图。 每个窗体都表示一组在记录集打开时已修复的记录，但当滚动到动态集中的某条记录时，它将反映其他用户或应用程序中的其他记录集对记录所做的更改。

> [!NOTE]
>  如果使用的是数据访问对象（DAO）类而不是开放式数据库连接（ODBC）类，请改用类[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 。 有关详细信息，请参阅文章[概述：数据库编程](../../data/data-access-programming-mfc-atl.md)。

若要使用任一类型的记录集，通常从 `CRecordset`派生特定于应用程序的记录集类。 记录集从数据源中选择记录，然后您可以：

- 滚动记录。

- 更新记录并指定锁定模式。

- 筛选记录集，以限制从数据源中的可用记录选择的记录。

- 对记录集排序。

- 参数化记录集，以通过在运行时之前不知道的信息自定义其选择。

若要使用类，请打开数据库并构造 recordset 对象，并向构造函数传递一个指向 `CDatabase` 对象的指针。 然后调用记录集的 `Open` 成员函数，您可以在其中指定对象是动态集还是快照。 调用 `Open` 从数据源中选择数据。 打开 recordset 对象之后，使用其成员函数和数据成员滚动记录并对其进行操作。 可用的操作取决于对象是动态集还是快照，它是可更新还是只读（这取决于开放式数据库连接（ODBC）数据源的功能）以及是否已实现批量取行。 若要刷新 `Open` 调用后可能已更改或添加的记录，请调用对象的 `Requery` 成员函数。 调用对象的 `Close` 成员函数并在完成后销毁对象。

在派生 `CRecordset` 类中，记录字段交换（RFX）或批量记录字段交换（Bulk RFX）用于支持读取和更新记录字段。

有关记录集和记录字段交换的详细信息，请参阅文章[概述：数据库编程](../../data/data-access-programming-mfc-atl.md)、[记录集（odbc）](../../data/odbc/recordset-odbc.md)、[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换（RFX）](../../data/odbc/record-field-exchange-rfx.md)。 若要专注于动态集和快照，请参阅文章[动态集](../../data/odbc/dynaset.md)和[快照](../../data/odbc/snapshot.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>要求

**标头：** afxdb

##  <a name="addnew"></a>CRecordset：： AddNew

准备将新记录添加到表中。

```
virtual void AddNew();
```

### <a name="remarks"></a>备注

若要查看新添加的记录，必须调用[Requery](#requery)成员函数。 该记录的字段最初为空。 （在数据库术语中，Null 表示 "无值"，而不是中C++的 null。）若要完成该操作，必须调用[更新](#update)成员函数。 `Update` 保存对数据源所做的更改。

> [!NOTE]
>  如果已实现批量行提取，则无法调用 `AddNew`。 这将导致断言失败。 尽管类 `CRecordset` 不提供更新批量数据行的机制，但你可以使用 ODBC API 函数 `SQLSetPos`来编写你自己的函数。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

`AddNew` 使用记录集的字段数据成员准备新的空记录。 调用 `AddNew`后，在记录集的字段数据成员中设置所需的值。 （无需出于此目的调用[Edit](#edit)成员函数; 仅对现有记录使用 `Edit`。）以后调用 `Update`时，字段数据成员中更改的值将保存在数据源中。

> [!CAUTION]
>  如果在调用 `Update`之前滚动到新记录，则新记录将丢失，并且不会发出任何警告。

如果数据源支持事务，则可以将 `AddNew` 调用部分事务。 有关事务的详细信息，请参阅类[CDatabase](../../mfc/reference/cdatabase-class.md)。 请注意，在调用 `AddNew`之前，应调用[CDatabase：： BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) 。

> [!NOTE]
>  对于动态集，新记录作为最后一条记录添加到记录集。 添加的记录不会添加到快照;您必须调用 `Requery` 来刷新记录集。

对于 `Open` 成员函数未调用的记录集，调用 `AddNew` 是非法的。 如果为无法追加到的记录集调用 `AddNew`，则会引发 `CDBException`。 可以通过调用[CanAppend](#canappend)来确定是否可以更新记录集。

有关详细信息，请参阅以下文章：[记录集：记录集如何更新记录（odbc）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)、[记录集：添加、更新和删除记录（Odbc）](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)和[事务（odbc）](../../data/odbc/transaction-odbc.md)。

### <a name="example"></a>示例

请参阅[事务：在记录集中执行事务（ODBC）](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)一文。

##  <a name="canappend"></a>CRecordset：： CanAppend

确定先前打开的记录集是否允许添加新记录。

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>返回值

如果记录集允许添加新记录，则为非零值;否则为0。 如果以只读方式打开了记录集，`CanAppend` 将返回0。

##  <a name="canbookmark"></a>CRecordset：： CanBookmark

确定记录集是否允许使用书签标记记录。

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>返回值

如果记录集支持书签，则为非零值;否则为0。

### <a name="remarks"></a>备注

此函数独立于[Open](#open)成员函数的*dwOptions*参数中的 `CRecordset::useBookmarks` 选项。 `CanBookmark` 指示给定的 ODBC 驱动程序和游标类型是否支持书签。 `CRecordset::useBookmarks` 指示书签是否可用（如果支持）。

> [!NOTE]
>  在只进记录集上不支持书签。

有关书签和记录集导航的详细信息，请参阅文章[记录集：书签和绝对位置（odbc）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[记录集：滚动（odbc）](../../data/odbc/recordset-scrolling-odbc.md)。

##  <a name="cancel"></a>CRecordset：： Cancel

请求数据源取消正在进行的异步操作或来自另一个线程的进程。

```
void Cancel();
```

### <a name="remarks"></a>备注

请注意，MFC ODBC 类不再使用异步处理;若要执行异步操作，必须 `SQLSetConnectOption`中直接调用 ODBC API 函数。 有关详细信息，请参阅《 *ODBC SDK 程序员指南》* 中的 "异步执行函数" 主题。

##  <a name="cancelupdate"></a>CRecordset：： CancelUpdate

在调用[Update](#update)之前，取消任何挂起的更新，这些更新是由[编辑](#edit)或[AddNew](#addnew)操作引起的。

```
void CancelUpdate();
```

### <a name="remarks"></a>备注

> [!NOTE]
>  此成员函数不适用于使用批量行提取的记录集，因为此类记录集无法调用 `Edit`、`AddNew`或 `Update`。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

如果启用了自动脏字段检查，`CancelUpdate` 会将成员变量还原到 `Edit` 或调用 `AddNew` 之前的值;否则，任何值更改都将保留。 默认情况下，在打开记录集时，自动字段检查将处于启用状态。 若要禁用此功能，必须在[Open](#open)成员函数的*dwOptions*参数中指定 `CRecordset::noDirtyFieldCheck`。

有关更新数据的详细信息，请参阅[记录记录集：添加、更新和删除记录（ODBC）](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)一文。

##  <a name="canrestart"></a>CRecordset：： CanRestart

确定记录集是否允许通过调用 `Requery` 成员函数来重新启动其查询（刷新其记录）。

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>返回值

如果允许 requery，则为非零值;否则为0。

##  <a name="canscroll"></a>CRecordset：： CanScroll

确定记录集是否允许滚动。

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>返回值

如果记录集允许滚动，则为非零值;否则为0。

### <a name="remarks"></a>备注

有关滚动的详细信息，请参阅[记录记录：滚动（ODBC）](../../data/odbc/recordset-scrolling-odbc.md)一文。

##  <a name="cantransact"></a>CRecordset：： CanTransact

确定记录集是否允许事务。

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>返回值

如果记录集允许事务，则为非零值;否则为0。

### <a name="remarks"></a>备注

有关详细信息，请参阅[事务（ODBC）](../../data/odbc/transaction-odbc.md)一文。

##  <a name="canupdate"></a>CRecordset：： CanUpdate

确定是否可以更新记录集。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>返回值

如果可以更新记录集，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果基础数据源为只读，或者当打开记录集时在*dwOptions*参数中指定了 `CRecordset::readOnly`，则记录集可能为只读。

##  <a name="checkrowseterror"></a>CRecordset：： CheckRowsetError

调用以处理在记录提取过程中生成的错误。

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>参数

*nRetCode*<br/>
ODBC API 函数返回代码。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

此虚拟成员函数处理提取记录时出现的错误，在批量提取行期间很有用。 你可能需要考虑重写 `CheckRowsetError` 以实现你自己的错误处理。

`CheckRowsetError` 在游标导航操作中自动调用，如 `Open`、`Requery`或任何 `Move` 操作。 它传递了 ODBC API 函数 `SQLExtendedFetch`的返回值。 下表列出了*nRetCode*参数的可能值。

|nRetCode|描述|
|--------------|-----------------|
|SQL_SUCCESS|函数已成功完成;无其他信息可用。|
|SQL_SUCCESS_WITH_INFO|函数已成功完成，可能出现非致命错误。 可以通过调用 `SQLError`获取其他信息。|
|SQL_NO_DATA_FOUND|已提取结果集中的所有行。|
|SQL_ERROR|函数失败。 可以通过调用 `SQLError`获取其他信息。|
|SQL_INVALID_HANDLE|由于环境句柄、连接句柄或语句句柄无效，函数失败。 这表明编程错误。 `SQLError`中不提供任何其他信息。|
|SQL_STILL_EXECUTING|异步启动的函数仍在执行。 请注意，默认情况下，MFC 永远不会将此值传递给 `CheckRowsetError`;MFC 将继续调用 `SQLExtendedFetch`，直到不再返回 SQL_STILL_EXECUTING。|

有关 `SQLError`的详细信息，请参阅 Windows SDK。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

##  <a name="close"></a>CRecordset：： Close

关闭记录集。

```
virtual void Close();
```

### <a name="remarks"></a>备注

ODBC HSTMT 以及为记录集分配的所有内存都将释放。 通常在调用 `Close`后，如果记录C++集对象是用**new**分配的，则将其删除。

调用 `Close`后，可以再次调用 `Open`。 这使您可以重复使用 recordset 对象。 替代方法是调用 `Requery`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

##  <a name="crecordset"></a>CRecordset：： CRecordset

构造 `CRecordset` 对象。

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>参数

*pDatabase*<br/>
包含指向 `CDatabase` 对象的指针或值为 NULL 的值。 如果不为 NULL，并且尚未调用 `CDatabase` 对象的 `Open` 成员函数以将其连接到数据源，则记录集会在其自己的 `Open` 调用期间尝试打开它。 如果传递 NULL，则使用在使用 ClassWizard 派生记录集类时指定的数据源信息构造并连接 `CDatabase` 对象。

### <a name="remarks"></a>备注

您可以直接使用 `CRecordset`，也可以从 `CRecordset`派生特定于应用程序的类。 可以使用 ClassWizard 来派生记录集类。

> [!NOTE]
>  派生类*必须*提供其自己的构造函数。 在派生类的构造函数中，调用构造函数 `CRecordset::CRecordset`，并将适当的参数传递给它。

将 NULL 传递给记录集构造函数以自动构造和连接 `CDatabase` 对象。 这是一个有用的速记，无需在构造记录集之前构建并连接 `CDatabase` 对象。

### <a name="example"></a>示例

有关详细信息，请参阅文章[记录集：声明表的类（ODBC）](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。

##  <a name="delete"></a>CRecordset：:D e)

删除当前记录。

```
virtual void Delete();
```

### <a name="remarks"></a>备注

成功删除后，记录集的字段数据成员被设置为 Null 值，并且必须显式调用 `Move` 函数之一，以便移出已删除的记录。 移出已删除的记录后，不能返回到该记录。 如果数据源支持事务，则可以将 `Delete` 调用部分事务。 有关详细信息，请参阅[事务（ODBC）](../../data/odbc/transaction-odbc.md)一文。

> [!NOTE]
>  如果已实现批量行提取，则无法调用 `Delete`。 这将导致断言失败。 尽管类 `CRecordset` 不提供更新批量数据行的机制，但你可以使用 ODBC API 函数 `SQLSetPos`来编写你自己的函数。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

> [!CAUTION]
>  记录集必须是可更新的，在调用 `Delete`时，记录集中必须有有效的记录;否则，将发生错误。 例如，如果您删除一个记录，但在再次调用 `Delete` 之前不滚动到新记录，`Delete` 将引发[CDBException](../../mfc/reference/cdbexception-class.md)。

与[AddNew](#addnew)和[Edit](#edit)不同，对 `Delete` 的调用后跟对[Update](#update)的调用。 如果 `Delete` 调用失败，字段数据成员将保持不变。

### <a name="example"></a>示例

此示例显示在函数框架上创建的记录集。 该示例假设存在 `m_dbCust`，`CDatabase` 已连接到数据源的类型的成员变量。

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

##  <a name="dobulkfieldexchange"></a>CRecordset：:D oBulkFieldExchange

调用以将数据源中的批量数据行交换到记录集。 实现批量记录字段交换（Bulk RFX）。

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象的指针。 框架将已设置此对象，以指定字段交换操作的上下文。

### <a name="remarks"></a>备注

实现批量行提取后，框架将调用此成员函数以自动将数据从数据源传输到记录集对象。 `DoBulkFieldExchange` 还将参数数据成员（如果有）绑定到记录集选定内容的 SQL 语句字符串中的参数占位符。

如果未实现批量行提取，则框架将调用[DoFieldExchange](#dofieldexchange)。 若要实现批量行提取，必须在[Open](#open)成员函数中指定*dwOptions*参数的 `CRecordset::useMultiRowFetch` 选项。

> [!NOTE]
> 仅当使用从 `CRecordset`派生的类时，`DoBulkFieldExchange` 才可用。 如果已直接从 `CRecordset`创建了 recordset 对象，则必须调用[GetFieldValue](#getfieldvalue)成员函数以检索数据。

批量记录字段交换（Bulk RFX）类似于记录字段交换（RFX）。 数据自动从数据源传输到 recordset 对象。 但是，您不能调用 `AddNew`、`Edit`、`Delete`或 `Update` 将更改传输回数据源。 类 `CRecordset` 当前不提供更新批量数据行的机制;不过，您可以使用 ODBC API 函数 `SQLSetPos`编写您自己的函数。

请注意，ClassWizard 不支持批量记录字段交换;因此，您必须通过编写对大容量 RFX 函数的调用来手动重写 `DoBulkFieldExchange`。 有关这些函数的详细信息，请参阅主题[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。

有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。 有关相关信息，请参阅[记录字段交换（RFX）](../../data/odbc/record-field-exchange-rfx.md)一文。

##  <a name="dofieldexchange"></a>CRecordset：:D oFieldExchange

调用以在记录集的字段数据成员和数据源的相应记录之间交换数据（双向）。 实现记录字段交换（RFX）。

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象的指针。 框架将已设置此对象，以指定字段交换操作的上下文。

### <a name="remarks"></a>备注

如果未实现批量行提取，则框架将调用此成员函数以自动在记录集对象的字段数据成员与数据源中的当前记录的对应列之间交换数据。 `DoFieldExchange` 还将参数数据成员（如果有）绑定到记录集选定内容的 SQL 语句字符串中的参数占位符。

如果已实现批量行提取，则框架将调用[DoBulkFieldExchange](#dobulkfieldexchange)。 若要实现批量行提取，必须在[Open](#open)成员函数中指定*dwOptions*参数的 `CRecordset::useMultiRowFetch` 选项。

> [!NOTE]
> 仅当使用从 `CRecordset`派生的类时，`DoFieldExchange` 才可用。 如果已直接从 `CRecordset`创建了 recordset 对象，则必须调用[GetFieldValue](#getfieldvalue)成员函数以检索数据。

字段数据的交换（称为记录字段交换（RFX））在两个方向上都适用：从记录集对象的字段数据成员到数据源中记录的字段，以及从数据源中的记录到记录集对象。

通常，为派生的记录集类实现 `DoFieldExchange` 必须执行的唯一操作是创建具有 ClassWizard 的类，并指定字段数据成员的名称和数据类型。 你还可以将代码添加到 ClassWizard 写入的内容，以指定参数数据成员或处理动态绑定的任何列。 有关详细信息，请参阅[记录记录集：动态绑定数据列（ODBC）](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)一文。

使用 ClassWizard 声明派生的记录集类时，向导会为你编写 `DoFieldExchange` 的替代，这类似于以下示例：

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

有关 RFX 函数的详细信息，请参阅主题[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。

有关 `DoFieldExchange`的更多示例和详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。 有关 RFX 的一般信息，请参阅[记录字段交换](../../data/odbc/record-field-exchange-rfx.md)一文。

##  <a name="edit"></a>CRecordset：： Edit

允许对当前记录进行更改。

```
virtual void Edit();
```

### <a name="remarks"></a>备注

调用 `Edit`后，可以通过直接重置字段数据成员的值来更改字段数据成员。 当您随后调用[Update](#update)成员函数以保存对数据源所做的更改时，操作完成。

> [!NOTE]
>  如果已实现批量行提取，则无法调用 `Edit`。 这将导致断言失败。 尽管类 `CRecordset` 不提供更新批量数据行的机制，但你可以使用 ODBC API 函数 `SQLSetPos`来编写你自己的函数。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

`Edit` 保存记录集的数据成员的值。 如果调用 `Edit`，进行更改，然后再次调用 `Edit`，则会将记录的值还原为第一次 `Edit` 调用前的值。

在某些情况下，您可能希望通过将列设为 Null （不包含数据）来更新该列。 为此，请使用参数 TRUE 调用[SetFieldNull](#setfieldnull) ，以将字段标记为 Null;这也会导致列更新。 如果希望将字段写入数据源（即使其值未更改），请使用参数 TRUE 调用[SetFieldDirty](#setfielddirty) 。 即使该字段的值为 Null，也是如此。

如果数据源支持事务，则可以将 `Edit` 调用部分事务。 请注意，在调用 `Edit` 之前和打开记录集之后，应调用[CDatabase：： BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) 。 另请注意，调用[CDatabase：： CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)不能代替调用 `Update` 来完成 `Edit` 操作。 有关事务的详细信息，请参阅类[CDatabase](../../mfc/reference/cdatabase-class.md)。

根据当前的锁定模式，要更新的记录可能会被 `Edit` 锁定，直到您调用 `Update` 或滚动到其他记录，或者仅在 `Edit` 调用期间锁定。 可以通过[SetLockingMode](#setlockingmode)更改锁定模式。

如果在调用 `Update`之前滚动到新记录，则会还原当前记录的以前值。 如果为无法更新的记录集调用 `Edit` 或当前没有记录，则会引发 `CDBException`。

有关详细信息，请参阅文章[Transaction （odbc）](../../data/odbc/transaction-odbc.md)和[Recordset：锁定记录（odbc）](../../data/odbc/recordset-locking-records-odbc.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

##  <a name="flushresultset"></a>CRecordset：： FlushResultSet

如果有多个结果集，则检索预定义查询的下一个结果集（存储过程）。

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>返回值

如果要检索多个结果集，则为非零值;否则为0。

### <a name="remarks"></a>备注

仅当在当前结果集上完全完成游标时，才应调用 `FlushResultSet`。 请注意，在通过调用 `FlushResultSet`检索下一个结果集时，游标在该结果集上无效;调用 `FlushResultSet`后，应调用[MoveNext](#movenext)成员函数。

如果预定义的查询使用输出参数或输入/输出参数，则必须调用 `FlushResultSet`，直到返回 `FALSE` （值为0），才能获得这些参数值。

`FlushResultSet` 调用 ODBC API 函数 `SQLMoreResults`。 如果 `SQLMoreResults` 返回 SQL_ERROR 或 SQL_INVALID_HANDLE，则 `FlushResultSet` 会引发异常。 有关 `SQLMoreResults`的详细信息，请参阅 Windows SDK。

如果要调用 `FlushResultSet`，则存储过程需要具有绑定字段。

### <a name="example"></a>示例

下面的代码假定 `COutParamRecordset` 是一个基于预定义查询的 `CRecordset`派生对象，其中包含一个输入参数和一个输出参数，并具有多个结果集。 请注意[DoFieldExchange](#dofieldexchange)重写的结构。

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

##  <a name="getbookmark"></a>CRecordset：： GetBookmark

获取当前记录的书签值。

```
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>参数

*varBookmark*<br/>
对[CDBVariant](../../mfc/reference/cdbvariant-class.md)对象的引用，该对象表示当前记录上的书签。

### <a name="remarks"></a>备注

若要确定记录集是否支持书签，请调用[CanBookmark](#canbookmark)。 若要使书签可用（如果支持），则必须在[Open](#open)成员函数的*dwOptions*参数中设置 `CRecordset::useBookmarks` 选项。

> [!NOTE]
>  如果书签不受支持或不可用，则调用 `GetBookmark` 将导致引发异常。 在只进记录集上不支持书签。

`GetBookmark` 将当前记录的书签的值分配给 `CDBVariant` 的对象。 若要在移动到不同记录后随时返回到该记录，请使用相应的 `CDBVariant` 对象调用[SetBookmark](#setbookmark) 。

> [!NOTE]
>  某些记录集操作完成后，书签可能不再有效。 例如，如果调用 `GetBookmark` 后跟 `Requery`，则可能无法使用 `SetBookmark`返回到该记录。 调用[CDatabase：： GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)以检查是否可以安全调用 `SetBookmark`。

有关书签和记录集导航的详细信息，请参阅文章[记录集：书签和绝对位置（odbc）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[记录集：滚动（odbc）](../../data/odbc/recordset-scrolling-odbc.md)。

##  <a name="getdefaultconnect"></a>CRecordset：： GetDefaultConnect

调用以获取默认的连接字符串。

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>返回值

一个包含默认连接字符串的 `CString`。

### <a name="remarks"></a>备注

框架调用此成员函数以获取记录集所基于的数据源的默认连接字符串。 ClassWizard 通过标识在 ClassWizard 中使用的数据源来获取有关表和列的信息，从而实现此功能。 你可能会发现，在开发应用程序时，依赖于此默认连接会很方便。 但默认连接可能不适用于您的应用程序的用户。 如果是这种情况，则应重新实现此功能，放弃 ClassWizard 的版本。 有关连接字符串的详细信息，请参阅[数据源（ODBC）](../../data/odbc/data-source-odbc.md)一文。

##  <a name="getdefaultsql"></a>CRecordset：： GetDefaultSQL

调用以获取要执行的默认 SQL 字符串。

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>返回值

包含默认 SQL 语句的 `CString`。

### <a name="remarks"></a>备注

框架调用此成员函数以获取记录集所基于的默认 SQL 语句。 这可能是表名或 SQL **SELECT**语句。

您可以通过使用 ClassWizard 声明记录集类来间接定义默认的 SQL 语句，ClassWizard 为您执行此任务。

如果你需要用于自己的 SQL 语句字符串，请调用 `GetSQL`，它将返回在打开时用于选择记录集的记录的 SQL 语句。 您可以在类的 `GetDefaultSQL`重写中编辑默认 SQL 字符串。 例如，您可以使用**call**语句指定对预定义查询的调用。 （但请注意，如果您编辑 `GetDefaultSQL`，则还需要修改 `m_nFields` 以匹配数据源中的列数。）

有关详细信息，请参阅文章[记录集：声明表的类（ODBC）](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。

> [!CAUTION]
>  如果框架无法标识表名称，则表名称将为空; 如果提供了多个表名称，则为; 如果**调用**语句无法解释，则为。 请注意，在使用**CALL**语句时，不能在大括号和**CALL**关键字之间插入空格，也不应在**select**语句中的大括号或**select**关键字之前插入空格。

##  <a name="getfieldvalue"></a>CRecordset：： GetFieldValue

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

*varValu*e 对将存储字段值的[CDBVariant](../../mfc/reference/cdbvariant-class.md)对象的引用。

*nFieldType*<br/>
字段的 ODBC C 数据类型。 使用默认值 DEFAULT_FIELD_TYPE，将强制 `GetFieldValue` 根据下表强制从 SQL 数据类型确定 C 数据类型。 否则，可以直接指定数据类型或选择兼容的数据类型;例如，可以在 SQL_C_CHAR 中存储任何数据类型。

|C 数据类型|SQL 数据类型|
|-----------------|-------------------|
|SQL_C_BIT|SQL_BIT|
|SQL_C_UTINYINT|SQL_TINYINT|
|SQL_C_SSHORT|SQL_SMALLINT|
|SQL_C_SLONG|SQL_INTEGER|
|SQL_C_FLOAT|SQL_REAL|
|SQL_C_DOUBLE|SQL_FLOATSQL_DOUBLE|
|SQL_C_TIMESTAMP|SQL_DATESQL_TIMESQL_TIMESTAMP|
|SQL_C_CHAR|SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR|
|SQL_C_BINARY|SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY|

有关 ODBC 数据类型的详细信息，请参阅 Windows SDK 附录 D 中的 "SQL 数据类型" 和 "C 数据类型" 主题。

*nIndex*<br/>
字段的从零开始的索引。

*strValue*<br/>
对[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的引用，该对象将存储转换为文本的字段值，而不考虑字段的数据类型。

### <a name="remarks"></a>备注

可以按名称或索引查找字段。 可以将字段值存储在 `CDBVariant` 对象或 `CString` 对象中。

如果已实现批量行提取，则当前记录始终位于行集的第一条记录上。 若要对给定行集中的记录使用 `GetFieldValue`，必须先调用[SetRowsetCursorPosition](#setrowsetcursorposition)成员函数，将光标移到该行集中的所需行。 然后对该行调用 `GetFieldValue`。 若要实现批量行提取，必须在[Open](#open)成员函数中指定*dwOptions*参数的 `CRecordset::useMultiRowFetch` 选项。

您可以使用 `GetFieldValue` 在运行时动态提取字段，而不是在设计时进行静态绑定。 例如，如果您已直接从 `CRecordset`中声明了 recordset 对象，则必须使用 `GetFieldValue` 检索字段数据;未实现记录字段交换（RFX）或批量记录字段交换（Bulk RFX）。

> [!NOTE]
>  如果在不从 `CRecordset`派生的情况下声明记录集对象，则不会加载 ODBC 游标库。 游标库要求记录集至少有一个绑定列;但是，如果直接使用 `CRecordset`，则不会绑定任何列。 成员函数[CDatabase：： microsoft.office.interop.visio.documents.open](../../mfc/reference/cdatabase-class.md#openex)和[CDatabase：： Open](../../mfc/reference/cdatabase-class.md#open)控件是否将加载光标库。

`GetFieldValue` 调用 ODBC API 函数 `SQLGetData`。 如果驱动程序输出字段值的实际长度值 SQL_NO_TOTAL，`GetFieldValue` 会引发异常。 有关 `SQLGetData`的详细信息，请参阅 Windows SDK。

### <a name="example"></a>示例

下面的示例代码演示了如何调用直接从 `CRecordset`中声明的记录集对象的 `GetFieldValue`。

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
>  与 DAO 类 `CDaoRecordset`不同，`CRecordset` 没有 `SetFieldValue` 成员函数。 如果直接从 `CRecordset`创建对象，则该对象实际上是只读的。

有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

##  <a name="getodbcfieldcount"></a>CRecordset：： GetODBCFieldCount

检索记录集对象中的字段总数。

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>返回值

记录集中的字段数。

### <a name="remarks"></a>备注

有关创建记录集的详细信息，请参阅[记录记录集：创建和关闭记录集（ODBC）](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)一文。

##  <a name="getodbcfieldinfo"></a>CRecordset：： GetODBCFieldInfo

获取有关记录集中的字段的信息。

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
对 `CODBCFieldInfo` 结构的引用。

*nIndex*<br/>
字段的从零开始的索引。

### <a name="remarks"></a>备注

函数的一个版本可让你按名称查找字段。 其他版本允许您按索引查找字段。

有关返回的信息的说明，请参阅[CODBCFieldInfo](../../mfc/reference/codbcfieldinfo-structure.md)结构。

有关创建记录集的详细信息，请参阅[记录记录集：创建和关闭记录集（ODBC）](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)一文。

##  <a name="getrecordcount"></a>CRecordset：： GetRecordCount

确定记录集的大小。

```
long GetRecordCount() const;
```

### <a name="return-value"></a>返回值

记录集中的记录数;如果记录集不包含任何记录，则为 0;如果无法确定记录计数，则为-1。

### <a name="remarks"></a>备注

> [!CAUTION]
>  记录计数以 "高水位线" 的形式进行维护，该记录在用户浏览记录时仍会显示。 仅在用户超过最后一条记录后知道记录总数。 出于性能原因，在调用 `MoveLast`时不会更新计数。 若要自行统计记录，请重复调用 `MoveNext`，直到 `IsEOF` 返回非零值。 通过 `CRecordset:AddNew` 添加记录并 `Update` 增加计数;通过 `CRecordset::Delete` 删除记录会减少计数。

##  <a name="getrowsetsize"></a>CRecordset：： GetRowsetSize

获取给定提取过程中要检索的行数的当前设置。

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>返回值

给定提取过程中要检索的行数。

### <a name="remarks"></a>备注

如果使用批量取行，则打开记录集时默认行集大小为 25;否则为1。

若要实现批量行提取，必须在[Open](#open)成员函数的*dwOptions*参数中指定 `CRecordset::useMultiRowFetch` 选项。 若要更改行集大小的设置，请调用[SetRowsetSize](#setrowsetsize)。

有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

##  <a name="getrowsfetched"></a>CRecordset：： GetRowsFetched

确定提取后实际检索的记录数。

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>返回值

给定提取后从数据源中检索的行数。

### <a name="remarks"></a>备注

如果已实现批量行提取，这会很有用。 行集大小通常指示将从提取中检索的行数;不过，记录集中的总行数还会影响将在行集中检索多少行。 例如，如果您的记录集包含10条记录，行集大小设置为4，则通过调用 `MoveNext` 遍历记录集将导致最终行集只有2个记录。

若要实现批量行提取，必须在[Open](#open)成员函数的*dwOptions*参数中指定 `CRecordset::useMultiRowFetch` 选项。 若要指定行集大小，请调用[SetRowsetSize](#setrowsetsize)。

有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

##  <a name="getrowstatus"></a>CRecordset：： GetRowStatus

获取当前行集中某行的状态。

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>参数

*wRow*<br/>
当前行集中某一行的位置（从1开始）。 此值的范围为1到行集的大小。

### <a name="return-value"></a>返回值

行的状态值。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

`GetRowStatus` 返回一个值，该值指示自上次从数据源检索到的行的状态变化，或未获取与*wRow*相对应的行。 下表列出可能的返回值。

|状态值|描述|
|------------------|-----------------|
|SQL_ROW_SUCCESS|该行不变。|
|SQL_ROW_UPDATED|已更新行。|
|SQL_ROW_DELETED|已删除该行。|
|SQL_ROW_ADDED|已添加行。|
|SQL_ROW_ERROR|由于出现错误，该行是 unretrievable 的。|
|SQL_ROW_NOROW|没有对应于*wRow*的行。|

有关详细信息，请参阅 Windows SDK 中的 ODBC API 函数 `SQLExtendedFetch`。

##  <a name="getstatus"></a>CRecordset：： GetStatus

确定记录集中当前记录的索引以及是否已查看最后一条记录。

```
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>参数

*rStatus*<br/>
对 `CRecordsetStatus` 对象的引用。 有关详细信息，请参阅备注部分。

### <a name="remarks"></a>备注

`CRecordset` 尝试跟踪索引，但在某些情况下，这可能是不可能的。 有关说明，请参阅[GetRecordCount](#getrecordcount) 。

`CRecordsetStatus` 结构的格式如下：

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

`CRecordsetStatus` 的两个成员具有以下含义：

- `m_lCurrentRecord` 包含记录集中当前记录的从零开始的索引，如果已知，则为。 如果无法确定索引，则此成员包含 AFX_CURRENT_RECORD_UNDEFINED （-2）。 如果 `IsBOF` 为 TRUE （空记录集或尝试在第一条记录前滚动），则 `m_lCurrentRecord` 设置为 AFX_CURRENT_RECORD_BOF （-1）。 如果在第一条记录上，则将其设置为0，第二记录为1，依此类推。

- 如果确定了记录集中的记录总数，则 `m_bRecordCountFinal` 非零值。 通常，必须通过从记录集的开头开始，然后调用 `MoveNext` 直到 `IsEOF` 返回非零值才能完成此操作。 如果此成员为零，则 `GetRecordCount`返回的记录计数（如果不为-1）仅为记录的 "高水位线" 计数。

##  <a name="getsql"></a>CRecordset：： GetSQL

调用此成员函数以获取在打开时用于选择记录集的记录的 SQL 语句。

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>返回值

对包含 SQL 语句的 `CString` 的**常量**引用。

### <a name="remarks"></a>备注

这通常是一个 SQL **SELECT**语句。 `GetSQL` 返回的字符串是只读的。

`GetSQL` 返回的字符串通常不同于你可能已传递到 `Open` 成员函数的*lpszSQL*参数中的记录集的任何字符串。 这是因为记录集基于您传递到 `Open`的内容、您使用 ClassWizard 指定的内容、您在 `m_strFilter` 中指定的内容和 `m_strSort` 的数据成员，以及您可能指定的任何参数来构造完整的 SQL 语句。 有关记录集如何构造此 SQL 语句的详细信息，请参阅文章[记录集：记录集如何选择记录（ODBC）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。

> [!NOTE]
>  仅在调用[Open](#open)后调用此成员函数。

##  <a name="gettablename"></a>CRecordset：： GetTableName

获取记录集的查询所基于的 SQL 表的名称。

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>返回值

如果记录集基于表，则为对包含表名称的 `CString` 的**常量**引用;否则为空字符串。

### <a name="remarks"></a>备注

仅当记录集基于表，而不是多个表的联接或预定义的查询（存储过程）时，`GetTableName` 才有效。 该名称是只读的。

> [!NOTE]
>  仅在调用[Open](#open)后调用此成员函数。

##  <a name="isbof"></a>CRecordset：： IsBOF

如果记录集已定位在第一条记录之前，则返回非零值。 没有当前记录。

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>返回值

如果记录集不包含任何记录，或者在第一条记录前向后滚动，则为非零值;否则为0。

### <a name="remarks"></a>备注

在从记录滚动到记录之前调用此成员函数，以了解您是否已离开记录集的第一条记录。 您还可以将 `IsBOF` 与 `IsEOF` 一起使用，以确定记录集是否包含任何记录或是否为空。 调用 `Open`后，如果记录集不包含任何记录，则 `IsBOF` 返回非零值。打开至少包含一条记录的记录集时，第一条记录为当前记录并且 `IsBOF` 返回0。

如果第一条记录是当前记录并且您调用 `MovePrev`，`IsBOF` 随后将返回非零值。 如果 `IsBOF` 返回非零值并且您调用 `MovePrev`，则会发生错误。 如果 `IsBOF` 返回非零值，则不定义当前记录，并且任何需要当前记录的操作都将导致错误。

### <a name="example"></a>示例

此示例使用 `IsBOF` 和 `IsEOF` 来检测记录集的限制，因为代码将在两个方向的记录集中滚动。

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

##  <a name="isdeleted"></a>CRecordset：： IsDeleted

确定当前记录是否已被删除。

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>返回值

如果记录集位于已删除记录上，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果滚动到某一记录并且 `IsDeleted` 返回 TRUE （非零），则必须滚动到其他记录，然后才能执行任何其他记录集操作。

`IsDeleted` 的结果取决于许多因素，例如记录集类型、记录集是否可更新、打开记录集时是否指定了 "`CRecordset::skipDeletedRecords`" 选项、驱动程序是否打包删除的记录，以及是否有多个那些.

有关 `CRecordset::skipDeletedRecords` 和驱动程序打包的详细信息，请参阅[开放](#open)成员函数。

> [!NOTE]
>  如果已实现批量行提取，则不应调用 `IsDeleted`。 请改为调用[GetRowStatus](#getrowstatus)成员函数。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

##  <a name="iseof"></a>CRecordset：： IsEOF

如果记录集位于最后一条记录之后，则返回非零值。 没有当前记录。

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>返回值

如果记录集不包含任何记录，或者滚动到最后一条记录之外，则为非零值;否则为0。

### <a name="remarks"></a>备注

在从记录滚动到记录时调用此成员函数，以了解您是否超出了记录集的最后一条记录。 您还可以使用 `IsEOF` 来确定记录集是否包含任何记录或是否为空。 调用 `Open`后，如果记录集不包含任何记录，则 `IsEOF` 返回非零值。 打开至少包含一条记录的记录集时，第一条记录为当前记录并且 `IsEOF` 返回0。

如果在调用 `MoveNext`时，最后一条记录是当前记录，`IsEOF` 随后将返回非零值。 如果 `IsEOF` 返回非零值并且您调用 `MoveNext`，则会发生错误。 如果 `IsEOF` 返回非零值，则不定义当前记录，并且任何需要当前记录的操作都将导致错误。

### <a name="example"></a>示例

请参阅[IsBOF](#isbof)的示例。

##  <a name="isfielddirty"></a>CRecordset：： IsFieldDirty

确定指定的字段数据成员是否已在调用[编辑](#edit)或[AddNew](#addnew)后发生了更改。

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>参数

*函数*<br/>
指向要检查其状态的字段数据成员的指针，或为 NULL 以确定是否有任何字段处于脏状态。

### <a name="return-value"></a>返回值

如果自调用 `AddNew` 或 `Edit`后，指定的字段数据成员发生了更改，则为非零值;否则为0。

### <a name="remarks"></a>备注

当通过调用 `CRecordset` 的[Update](#update)成员函数（在调用 `Edit` 或 `AddNew`）更新当前记录时，所有更新的字段数据成员中的数据都将传输到数据源上的记录。

> [!NOTE]
>  此成员函数不适用于使用批量取行的记录集。 如果已实现批量行提取，则 `IsFieldDirty` 将始终返回 FALSE，并将导致断言失败。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

调用 `IsFieldDirty` 将重置之前调用[SetFieldDirty](#setfielddirty)的效果，因为重新计算字段的已更新状态。 在 `AddNew` 情况下，如果当前字段值不同于伪 null 值，则字段状态设置为 "已更新"。 在 `Edit` 情况下，如果字段值不同于缓存值，则字段状态设置为 "已更新"。

`IsFieldDirty` 通过[DoFieldExchange](#dofieldexchange)实现。

有关脏标志的详细信息，请参阅[记录记录集：记录集如何选择记录（ODBC）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)一文。

##  <a name="isfieldnull"></a>CRecordset：： IsFieldNull

如果当前记录中的指定字段为空（没有值），则返回非零值。

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>参数

*函数*<br/>
指向要检查其状态的字段数据成员的指针，或为 NULL 以确定是否有任何字段为 Null。

### <a name="return-value"></a>返回值

如果将指定字段数据成员标记为 Null，则为非零值;否则为0。

### <a name="remarks"></a>备注

调用此成员函数以确定是否已将记录集的指定字段数据成员标记为 Null。 （在数据库术语中，Null 表示 "无值"，而不是中C++的 null。）如果将字段数据成员标记为 Null，则将其解释为当前记录中没有值的列。

> [!NOTE]
>  此成员函数不适用于使用批量取行的记录集。 如果已实现批量行提取，则 `IsFieldNull` 将始终返回 FALSE，并将导致断言失败。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

`IsFieldNull` 通过[DoFieldExchange](#dofieldexchange)实现。

##  <a name="isfieldnullable"></a>CRecordset：： IsFieldNullable

如果可以将当前记录中的指定字段设置为 Null （没有值），则返回非零值。

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>参数

*函数*<br/>
指向要检查其状态的字段数据成员的指针，或为 NULL 以确定是否可以将任何字段设置为 Null 值。

### <a name="remarks"></a>备注

调用此成员函数以确定指定的字段数据成员是否为 "nullable" （可以设置为 Null 值;C++ Null 与 null 不同，后者在数据库术语中意味着 "无值"）。

> [!NOTE]
>  如果已实现批量行提取，则无法调用 `IsFieldNullable`。 改为调用[GetODBCFieldInfo](#getodbcfieldinfo)成员函数，以确定字段是否可以设置为 Null 值。 请注意，无论是否已实现批量行提取，都可以始终调用 `GetODBCFieldInfo`。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

不能为 Null 的字段必须具有值。 如果在添加或更新记录时尝试将此类字段设置为 Null，则数据源拒绝添加或更新，[更新](#update)将引发异常。 调用 `Update`时（而不是在调用[SetFieldNull](#setfieldnull)时），将发生异常。

将函数的第一个参数用于函数将仅应用于 `outputColumn` 字段，而不是 `param` 字段。 例如，调用

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

仅将 `outputColumn` 字段设置为 NULL;`param` 字段将不受影响。

若要处理 `param` 字段，必须提供要处理的单个 `param` 的实际地址，例如：

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

这意味着，你不能将所有 `param` 字段设置为 NULL，因为你可以在 `outputColumn` 字段。

`IsFieldNullable` 通过[DoFieldExchange](#dofieldexchange)实现。

##  <a name="isopen"></a>CRecordset：： IsOpen

确定记录集是否已打开。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果以前调用了 recordset 对象的[Open](#open)或[Requery](#requery)成员函数并且记录集尚未关闭，则为非零值;否则为0。

##  <a name="m_hstmt"></a>CRecordset：： m_hstmt

包含与记录集相关联的、类型为 HSTMT 的 ODBC 语句数据结构的句柄。

### <a name="remarks"></a>备注

ODBC 数据源的每个查询都与 HSTMT 关联。

> [!CAUTION]
>  在调用[Open](#open)之前，不要使用 `m_hstmt`。

通常不需要直接访问 HSTMT，但你可能需要它来直接执行 SQL 语句。 类 `CDatabase` 的 `ExecuteSQL` 成员函数提供了使用 `m_hstmt`的示例。

##  <a name="m_nfields"></a>CRecordset：： m_nFields

包含 recordset 类中的字段数据成员数;也就是说，记录集从数据源中选择的列数。

### <a name="remarks"></a>备注

Recordset 类的构造函数必须用正确的数字初始化 `m_nFields`。 如果你尚未实现批量行提取，则当你使用它声明记录集类时，ClassWizard 会为你编写此初始化。 你还可以手动编写。

框架使用此数字来管理字段数据成员与数据源中当前记录的对应列之间的交互。

> [!CAUTION]
>  此数字必须与在使用参数 `CFieldExchange::outputColumn`调用[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)后，在 `DoFieldExchange` 或 `DoBulkFieldExchange` 中注册的 "输出列" 的数目对应。

可以动态绑定列，如 "记录集：动态绑定数据列" 一文中所述。 如果这样做，则必须增加 `m_nFields` 中的计数，以反映 `DoFieldExchange` 或 `DoBulkFieldExchange` 成员函数中用于动态绑定列的 RFX 或 Bulk RFX 函数调用的数目。

有关详细信息，请参阅文章[记录集：动态绑定数据列（odbc）](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)和[记录集：批量提取记录（odbc）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

### <a name="example"></a>示例

请参阅[记录字段交换：使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。

##  <a name="m_nparams"></a>CRecordset：： m_nParams

包含 recordset 类中的参数数据成员数;这就是记录集查询传递的参数的数目。

### <a name="remarks"></a>备注

如果记录集类有任何参数数据成员，则该类的构造函数必须用正确的数字初始化 `m_nParams`。 `m_nParams` 的值默认为0。 如果添加参数数据成员（必须手动执行此操作），则还必须在类构造函数中手动添加初始化，以反映参数的数目（至少必须与 `m_strFilter` 中的 "" 占位符的数目相同或 `m_strSort`string）。

参数化记录集的查询时，框架使用此数字。

> [!CAUTION]
>  此数字必须与在对参数值为 `CFieldExchange::inputParam`、`CFieldExchange::param`、`CFieldExchange::outputParam`或 `CFieldExchange::inoutParam`的[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)调用后 `DoFieldExchange` 或 `DoBulkFieldExchange` 中注册的 "params" 的数量相对应。

### <a name="example"></a>示例

  请参阅文章[记录集：参数化记录集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)和[记录字段交换：使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。

##  <a name="m_pdatabase"></a>CRecordset：： m_pDatabase

包含一个指向 `CDatabase` 对象的指针，该对象通过该对象将记录集连接到数据源。

### <a name="remarks"></a>备注

此变量通过两种方式进行设置。 通常，当构造 recordset 对象时，会将指针传递到已连接的 `CDatabase` 对象。 如果改为传递 NULL，`CRecordset` 将为您创建一个 `CDatabase` 对象并将其连接起来。 在任一情况下，`CRecordset` 都将指针存储在此变量中。

通常不会直接使用存储在 `m_pDatabase`中的指针。 但是，如果你将自己的扩展写入 `CRecordset`，则可能需要使用指针。 例如，如果引发自己的 `CDBException`，则可能需要指针。 如果需要使用同一个 `CDatabase` 对象（例如运行事务、设置超时，或调用类 `CDatabase` 的 `ExecuteSQL` 成员函数来直接执行 SQL 语句）执行某些操作，则可能需要使用此方法。

##  <a name="m_strfilter"></a>CRecordset：： m_strFilter

构造 recordset 对象之后但在调用其 `Open` 成员函数之前，请使用此数据成员存储包含 SQL **WHERE**子句的 `CString`。

### <a name="remarks"></a>备注

记录集使用此字符串来约束（或筛选）它在 `Open` 或 `Requery` 调用期间选择的记录。 这适用于选择部分记录，如 "所有基于加利福尼亚的销售人员" （"状态 = CA"）。 **WHERE**子句的 ODBC SQL 语法是

`WHERE search-condition`

请注意，在字符串中不包含**WHERE**关键字。 框架提供此方法。

您还可以通过在筛选器字符串中放置占位符，为每个占位符声明类中的参数数据成员，并在运行时将参数传递给记录集来对筛选器字符串进行参数化。 这使您可以在运行时构造筛选器。 有关详细信息，请参阅[记录记录集：参数化记录集（ODBC）一](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)文。

有关 SQL **WHERE**子句的详细信息，请参阅[sql](../../data/odbc/sql.md)。 有关选择和筛选记录的详细信息，请参阅文章[记录集：筛选记录（ODBC）](../../data/odbc/recordset-filtering-records-odbc.md)一文。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

##  <a name="m_strsort"></a>CRecordset：： m_strSort

构造 recordset 对象之后但在调用其 `Open` 成员函数之前，请使用此数据成员存储包含 SQL **ORDER by**子句的 `CString`。

### <a name="remarks"></a>备注

记录集使用此字符串对它在 `Open` 或 `Requery` 调用期间选择的记录进行排序。 您可以使用此功能对一个或多个列的记录集进行排序。 **ORDER by**子句的 ODBC SQL 语法是

`ORDER BY sort-specification [, sort-specification]...`

其中，排序规范是一个整数或列的名称。 还可以通过将 "ASC" 或 "DESC" 追加到排序字符串中的列列表，指定升序或降序（默认情况下顺序为升序）。 所选记录首先按列出的第一列进行排序，然后按第二列排序，依此类推。 例如，您可以按姓氏和名字对 "Customers" 记录集进行排序。 您可以列出的列数取决于数据源。 有关详细信息，请参阅 Windows SDK。

请注意，在字符串中不包含**ORDER BY**关键字。 框架提供此方法。

有关 SQL 子句的详细信息，请参阅[sql](../../data/odbc/sql.md)。 有关对记录进行排序的详细信息，请参阅[记录记录：排序记录（ODBC）](../../data/odbc/recordset-sorting-records-odbc.md)一文。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

##  <a name="move"></a>CRecordset：： Move

在记录集中向前或向后移动当前记录指针。

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>参数

*nRows*<br/>
向前或向后移动的行数。 正值表示向前移动，直到记录集的末尾。 负值将向后移动。

*wFetchType*<br/>
确定 `Move` 将提取的行集。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

如果为*nRows*传递值0，则 `Move` 刷新当前记录;`Move` 将结束任何当前 `AddNew` 或 `Edit` 模式，并且将在调用 `AddNew` 或 `Edit` 之前还原当前记录的值。

> [!NOTE]
>  当您在记录集中移动时，无法跳过已删除的记录。 有关详细信息，请参阅[CRecordset：： IsDeleted](#isdeleted) 。 使用 `skipDeletedRecords` 选项集打开 `CRecordset` 时，如果*nRows*参数为0，则 `Move` 断言。 此行为可防止刷新其他客户端应用程序使用相同数据删除的行。 有关 `skipDeletedRecords`说明，请参阅[打开](#open)中的*dwOption*参数。

`Move` 按行集重新定位记录集。 基于*nRows*和*wFetchType*的值，`Move` 获取适当的行集，然后使该行集中的第一条记录成为当前记录。 如果尚未实现批量行提取，则行集大小始终为1。 提取行集时，`Move` 直接调用[CheckRowsetError](#checkrowseterror)成员函数来处理提取后产生的任何错误。

根据您传递的值，`Move` 与其他 `CRecordset` 成员函数等效。 特别是， *wFetchType*的值可能表示一个成员函数，该函数比较直观，并且通常是移动当前记录的首选方法。

下表列出了*wFetchType*的可能值、`Move` 将基于*wFetchType*和*nRows*提取的行集，以及与*wFetchType*相对应的任何等效成员函数。

|wFetchType|提取的行集|等效成员函数|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE （默认值）|行集从当前行集中的第一行开始*nRows*行。||
|SQL_FETCH_NEXT|下一个行集;将忽略*nRows* 。|[MoveNext](#movenext)|
|SQL_FETCH_PRIOR|之前的行集;将忽略*nRows* 。|[MovePrev](#moveprev)|
|SQL_FETCH_FIRST|记录集中的第一个行集;将忽略*nRows* 。|[MoveFirst](#movefirst)|
|SQL_FETCH_LAST|记录集中的最后一个完整行集;将忽略*nRows* 。|[MoveLast](#movelast)|
|SQL_FETCH_ABSOLUTE|如果*nRows* > 0，则从记录集开头开始*nRows*行的行集。 如果*nRows* < 0，则从记录集末尾开始*nRows*行的行集。 如果*nRows* = 0，则返回文件开头（BOF）条件。|[SetAbsolutePosition](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|从其书签值对应于*nRows*的行开始的行集。|[SetBookmark](#setbookmark)|

> [!NOTE]
>  对于只进记录集，`Move` 仅对*wFetchType*的值有效。

> [!CAUTION]
>  如果记录集没有记录，则调用 `Move` 会引发异常。 若要确定记录集是否有任何记录，请调用[IsBOF](#isbof)和[IsEOF](#iseof)。

> [!NOTE]
>  如果滚动了记录集的开头或结尾（`IsBOF` 或 `IsEOF` 返回非零值），则调用 `Move` 函数可能会引发 `CDBException`。 例如，如果 `IsEOF` 返回非零值并且 `IsBOF` 未返回，则 `MoveNext` 将引发异常，但 `MovePrev` 将不会引发异常。

> [!NOTE]
>  如果在更新或添加当前记录时调用 `Move`，则更新将丢失，且不发出警告。

有关记录集导航的详细信息，请参阅文章[记录集：滚动（odbc）](../../data/odbc/recordset-scrolling-odbc.md)和[记录集：书签和绝对位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。 有关相关信息，请参阅 Windows SDK 中的 ODBC API 函数 `SQLExtendedFetch`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

##  <a name="movefirst"></a>CRecordset：： MoveFirst

使第一个行集中的第一条记录成为当前记录。

```
void MoveFirst();
```

### <a name="remarks"></a>备注

不管是否已实现批量提取，这始终是记录集中的第一条记录。

打开记录集之后，无需立即调用 `MoveFirst`。 此时，第一条记录（如果有）将自动成为当前记录。

> [!NOTE]
>  此成员函数对于只进记录集无效。

> [!NOTE]
>  当您在记录集中移动时，无法跳过已删除的记录。 有关详细信息，请参阅[IsDeleted](#isdeleted)成员函数。

> [!CAUTION]
>  如果记录集没有记录，则调用任何 `Move` 函数将引发异常。 若要确定记录集是否有任何记录，请调用 `IsBOF` 和 `IsEOF`。

> [!NOTE]
>  如果在更新或添加当前记录时调用任何 `Move` 函数，则更新将丢失且不发出警告。

有关记录集导航的详细信息，请参阅文章[记录集：滚动（odbc）](../../data/odbc/recordset-scrolling-odbc.md)和[记录集：书签和绝对位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

  请参阅[IsBOF](#isbof)的示例。

##  <a name="movelast"></a>CRecordset：： MoveLast

使最后一个完成的行集中的第一条记录成为当前记录。

```
void MoveLast();
```

### <a name="remarks"></a>备注

如果尚未实现批量取行，则记录集的行集大小为1，因此 `MoveLast` 只需移动到记录集中的最后一条记录。

> [!NOTE]
>  此成员函数对于只进记录集无效。

> [!NOTE]
>  当您在记录集中移动时，无法跳过已删除的记录。 有关详细信息，请参阅[IsDeleted](#isdeleted)成员函数。

> [!CAUTION]
>  如果记录集没有记录，则调用任何 `Move` 函数将引发异常。 若要确定记录集是否有任何记录，请调用 `IsBOF` 和 `IsEOF`。

> [!NOTE]
>  如果在更新或添加当前记录时调用任何 `Move` 函数，则更新将丢失且不发出警告。

有关记录集导航的详细信息，请参阅文章[记录集：滚动（odbc）](../../data/odbc/recordset-scrolling-odbc.md)和[记录集：书签和绝对位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

  请参阅[IsBOF](#isbof)的示例。

##  <a name="movenext"></a>CRecordset：： MoveNext

使下一行集中的第一条记录成为当前记录。

```
void MoveNext();
```

### <a name="remarks"></a>备注

如果尚未实现批量取行，则记录集的行集大小为1，因此 `MoveNext` 只需移动到下一条记录。

> [!NOTE]
>  当您在记录集中移动时，无法跳过已删除的记录。 有关详细信息，请参阅[IsDeleted](#isdeleted)成员函数。

> [!CAUTION]
>  如果记录集没有记录，则调用任何 `Move` 函数将引发异常。 若要确定记录集是否有任何记录，请调用 `IsBOF` 和 `IsEOF`。

> [!NOTE]
>  还建议在调用 `MoveNext`之前调用 `IsEOF`。 例如，如果滚动到了记录集的末尾，`IsEOF` 将返回非零值;对 `MoveNext` 的后续调用将引发异常。

> [!NOTE]
>  如果在更新或添加当前记录时调用任何 `Move` 函数，则更新将丢失且不发出警告。

有关记录集导航的详细信息，请参阅文章[记录集：滚动（odbc）](../../data/odbc/recordset-scrolling-odbc.md)和[记录集：书签和绝对位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

  请参阅[IsBOF](#isbof)的示例。

##  <a name="moveprev"></a>CRecordset：： MovePrev

使上一个行集中的第一条记录成为当前记录。

```
void MovePrev();
```

### <a name="remarks"></a>备注

如果尚未实现批量取行，则记录集的行集大小为1，因此 `MovePrev` 只需移动到上一条记录。

> [!NOTE]
>  此成员函数对于只进记录集无效。

> [!NOTE]
>  当您在记录集中移动时，无法跳过已删除的记录。 有关详细信息，请参阅[IsDeleted](#isdeleted)成员函数。

> [!CAUTION]
>  如果记录集没有记录，则调用任何 `Move` 函数将引发异常。 若要确定记录集是否有任何记录，请调用 `IsBOF` 和 `IsEOF`。

> [!NOTE]
>  还建议在调用 `MovePrev`之前调用 `IsBOF`。 例如，如果您向前滚动记录集的开头，`IsBOF` 将返回非零值;对 `MovePrev` 的后续调用将引发异常。

> [!NOTE]
>  如果在更新或添加当前记录时调用任何 `Move` 函数，则更新将丢失且不发出警告。

有关记录集导航的详细信息，请参阅文章[记录集：滚动（odbc）](../../data/odbc/recordset-scrolling-odbc.md)和[记录集：书签和绝对位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

  请参阅[IsBOF](#isbof)的示例。

##  <a name="onsetoptions"></a>CRecordset：： OnSetOptions

调用以设置指定 ODBC 语句的选项（在选择时使用）。

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>参数

*hstmt*<br/>
要设置其选项的 ODBC 语句的 HSTMT。

### <a name="remarks"></a>备注

调用 `OnSetOptions` 为指定的 ODBC 语句设置选项（在选择时使用）。 框架调用此成员函数来设置记录集的初始选项。 `OnSetOptions` 确定数据源对可滚动游标的支持和游标并发性，并相应地设置记录集的选项。 （而 `OnSetOptions` 用于选择操作，`OnSetUpdateOptions` 用于更新操作。）

重写 `OnSetOptions` 以设置特定于该驱动程序或数据源的选项。 例如，如果数据源支持打开以进行独占访问，则可以重写 `OnSetOptions` 以利用此功能。

有关游标的详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)。

##  <a name="onsetupdateoptions"></a>CRecordset：： OnSetUpdateOptions

调用以设置指定 ODBC 语句的选项（在更新时使用）。

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>参数

*hstmt*<br/>
要设置其选项的 ODBC 语句的 HSTMT。

### <a name="remarks"></a>备注

调用 `OnSetUpdateOptions` 为指定的 ODBC 语句设置选项（在 update 中使用）。 框架在创建 HSTMT 以更新记录集中的记录后，调用此成员函数。 （而 `OnSetOptions` 用于选择操作，`OnSetUpdateOptions` 用于更新操作。）`OnSetUpdateOptions` 确定数据源对可滚动游标的支持和游标并发性，并相应地设置记录集的选项。

重写 `OnSetUpdateOptions` 以设置 ODBC 语句的选项，然后将该语句用于访问数据库。

有关游标的详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)。

##  <a name="open"></a>CRecordset：： Open

通过检索表或执行记录集表示的查询打开记录集。

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>参数

*nOpenType*<br/>
接受默认值 AFX_DB_USE_DEFAULT_TYPE，或使用 `enum OpenType`中的以下值之一：

- `CRecordset::dynaset` 使用双向滚动的记录集。 记录的成员资格和排序是在记录集打开时确定的，而其他用户对数据值所做的更改在提取操作后可见。 动态集也称为键集驱动的记录集。

- `CRecordset::snapshot` 使用双向滚动的静态记录集。 记录的成员资格和排序是在打开记录集时确定的;数据值是在提取记录时确定的。 在关闭并重新打开该记录集之前，其他用户所做的更改将不可见。

- `CRecordset::dynamic` 使用双向滚动的记录集。 其他用户对成员身份、排序和数据值所做的更改将在提取操作后可见。 请注意，许多 ODBC 驱动程序不支持此类型的记录集。

- `CRecordset::forwardOnly` 只有向前滚动的只读记录集。

   对于 `CRecordset`，默认值为 "`CRecordset::snapshot`"。 默认值机制允许视觉对象C++向导与 ODBC `CRecordset` 和 DAO `CDaoRecordset`交互，它们具有不同的默认值。

有关这些记录集类型的详细信息，请参阅[记录记录集（ODBC）](../../data/odbc/recordset-odbc.md)一文。 相关信息，请参阅 "Windows SDK 中的" 使用块和可滚动游标 "一文。

> [!CAUTION]
>  如果不支持请求的类型，则框架将引发异常。

*lpszSQL*<br/>
包含以下项之一的字符串指针：

- NULL 指针。

- 表的名称。

- SQL **SELECT**语句（可以选择使用 sql **WHERE**或**ORDER BY**子句）。

- 指定预定义查询的名称的**CALL**语句（存储过程）。 请注意，不要在大括号和**CALL**关键字之间插入空格。

有关此字符串的详细信息，请参阅 "[备注](#remarks)" 部分下的表和 ClassWizard 角色的讨论。

> [!NOTE]
>  结果集中列的顺序必须与[DoFieldExchange](#dofieldexchange)或[DoBulkFieldExchange](#dobulkfieldexchange)函数重写中 rfx 或 Bulk rfx 函数调用的顺序相匹配。

*dwOptions*<br/>
一个位掩码，可以指定下列值的组合。 其中一些是互斥的。 默认值为 "**无**"。

- `CRecordset::none` 未设置任何选项。 此参数值与所有其他值互相排斥。 默认情况下，可以使用 "[编辑](#edit)" 或 "[删除](#delete)" 更新记录集，并允许使用[AddNew](#addnew)追加新记录。 可更新性取决于数据源以及指定的*nOpenType*选项。 大容量添加的优化不可用。 不会实现批量提取行。 记录集导航过程中将不会跳过已删除的记录。 书签不可用。 自动脏字段检查已实现。

- `CRecordset::appendOnly` 不允许记录集上 `Edit` 或 `Delete`。 仅允许 `AddNew`。 此选项与 `CRecordset::readOnly`互相排斥。

- `CRecordset::readOnly` 将记录集作为只读打开。 此选项与 `CRecordset::appendOnly`互相排斥。

- `CRecordset::optimizeBulkAdd` 使用已准备好的 SQL 语句一次优化添加多个记录。 仅当未使用 ODBC API 函数 `SQLSetPos` 来更新记录集时才适用。 第一个更新确定哪些字段被标记为 "已更新"。 此选项与 `CRecordset::useMultiRowFetch`互相排斥。

- `CRecordset::useMultiRowFetch` 实现批量行提取，以允许在单个提取操作中检索多个行。 这是一项高级功能，旨在提高性能;但是，ClassWizard 不支持批量记录字段交换。 此选项与 `CRecordset::optimizeBulkAdd`互相排斥。 请注意，如果指定 `CRecordset::useMultiRowFetch`，则选项 `CRecordset::noDirtyFieldCheck` 将自动打开（两个缓冲将不可用）;在只进记录集上，选项 `CRecordset::useExtendedFetch` 将自动打开。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

- `CRecordset::skipDeletedRecords` 在整个记录集中导航时，跳过所有已删除的记录。 这会降低某些相对提取的性能。 此选项在只进记录集上无效。 如果调用*nRows*参数设置为0的[Move](#move) ，并设置 `CRecordset::skipDeletedRecords` 选项，`Move` 将断言。 请注意，`CRecordset::skipDeletedRecords` 类似于*驱动程序打包*，这意味着从记录集中删除删除的行。 但是，如果你的驱动程序将记录打包，则它将仅跳过你删除的记录;当记录集处于打开状态时，它不会跳过其他用户删除的记录。 `CRecordset::skipDeletedRecords` 将跳过其他用户删除的行。

- `CRecordset::useBookmarks` 可能会在记录集中使用书签（如果支持）。 书签会减缓数据检索，但会提高数据导航的性能。 在只进记录集上无效。 有关详细信息，请参阅[记录记录集：书签和绝对位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)一文。

- `CRecordset::noDirtyFieldCheck` 关闭自动脏字段检查（双缓冲）。 这将提高性能;但是，必须通过调用 `SetFieldDirty` 和 `SetFieldNull` 成员函数，手动将字段标记为已更新。请注意，类 `CRecordset` 中的双缓冲类似于类 `CDaoRecordset`中的双缓冲。 但是，在 `CRecordset`中，不能对各个字段启用双缓冲;您可以为所有字段启用它或对所有字段禁用该字段。 请注意，如果指定选项 `CRecordset::useMultiRowFetch`，则 `CRecordset::noDirtyFieldCheck` 将自动打开;但是，不能对实现批量取行的记录集使用 `SetFieldDirty` 和 `SetFieldNull`。

- `CRecordset::executeDirect` 不使用准备好的 SQL 语句。 为了提高性能，如果永远不会调用 `Requery` 成员函数，请指定此选项。

- `CRecordset::useExtendedFetch` 实现 `SQLExtendedFetch` 而不是 `SQLFetch`。 这适用于在只进记录集上实现批量行提取。 如果对只进记录集指定选项 `CRecordset::useMultiRowFetch`，则 `CRecordset::useExtendedFetch` 将自动打开。

- `CRecordset::userAllocMultiRowBuffers` 用户将为数据分配存储缓冲区。 如果要分配自己的存储，请将此选项与 `CRecordset::useMultiRowFetch` 结合使用;否则，框架将自动分配所需的存储。 有关详细信息，请参阅[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。 请注意，指定 `CRecordset::userAllocMultiRowBuffers` 而不指定 `CRecordset::useMultiRowFetch` 将导致断言失败。

### <a name="return-value"></a>返回值

如果 `CRecordset` 对象已成功打开，则为非零值;否则为0，如果[CDatabase：： Open](../../mfc/reference/cdatabase-class.md#open) （如果调用）返回0。

### <a name="remarks"></a>备注

您必须调用此成员函数以运行由记录集定义的查询。 在调用 `Open`之前，必须构造 recordset 对象。

此记录集与数据源的连接取决于在调用 `Open`之前如何构造记录集。 如果将[CDatabase](../../mfc/reference/cdatabase-class.md)对象传递到尚未连接到数据源的记录集构造函数，则此成员函数将使用[GetDefaultConnect](#getdefaultconnect)尝试打开该数据库对象。 如果将 NULL 传递到 recordset 构造函数，则构造函数将为你构造 `CDatabase` 对象，并 `Open` 尝试连接数据库对象。 有关在这些不同环境下关闭记录集和连接的详细信息，请参阅[Close](#close)。

> [!NOTE]
>  始终共享通过 `CRecordset` 对象访问数据源的权限。 与 `CDaoRecordset` 类不同的是，您不能使用 `CRecordset` 对象打开具有独占访问权限的数据源。

调用 `Open`时，通常是一个 SQL **SELECT**语句，它根据下表中所示的条件来选择记录。

|LpszSQL 参数的值|选择的记录由|示例|
|------------------------------------|----------------------------------------|-------------|
|NULL|`GetDefaultSQL`返回的字符串。||
|SQL 表名称|`DoFieldExchange` 或 `DoBulkFieldExchange`中的表列表的所有列。|`"Customer"`|
|预定义的查询（存储过程）名称|定义查询以返回的列。|`"{call OverDueAccts}"`|
|从表列表**中** **选择**列列表|指定的表中指定的列。|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
>  请注意，不要在 SQL 字符串中插入额外的空格。 例如，如果在大括号和**CALL**关键字之间插入空格，MFC 会将 SQL 字符串误认为为表名，并将其合并到**SELECT**语句中，这将导致引发异常。 同样，如果预定义的查询使用 output 参数，则不要在大括号和 "" 符号之间插入空格。 最后，在**CALL** **语句或 select 语句中**的**select**关键字之前，不能在大括号前插入空格。

一般的过程是将 NULL 传递到 `Open`;在这种情况下，`Open` 调用[GetDefaultSQL](#getdefaultsql)。 如果使用派生的 `CRecordset` 类，`GetDefaultSQL` 将给出在 ClassWizard 中指定的表名。 您可以改为在 `lpszSQL` 参数中指定其他信息。

无论通过哪种方式，`Open` 都可以为查询构造最终 SQL 字符串（该字符串可能会将 SQL WHERE 和**ORDER BY**子句追加到你传递的 `lpszSQL` 字符串**上**），然后执行查询。 调用 `Open`后，可以通过调用[GetSQL](#getsql)来检查构造的字符串。 有关记录集如何构造 SQL 语句和选择记录的其他详细信息，请参阅记录记录集[：记录集如何选择记录（ODBC）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)一文。

记录集类的字段数据成员绑定到所选数据的列。 如果返回任何记录，则第一个记录将成为当前记录。

如果要设置记录集的选项，例如筛选器或排序，请在构造 recordset 对象之后但在调用 `Open`之前指定这些选项。 如果要在记录集已打开后刷新记录集中的记录，请调用[Requery](#requery)。

有关详细信息（包括其他示例），请参阅文章[记录集（odbc）](../../data/odbc/recordset-odbc.md)、[记录集：记录集如何选择记录（Odbc）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)和[记录集：创建和关闭记录集（odbc）](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。

### <a name="example"></a>示例

下面的代码示例演示了 `Open` 调用的不同形式。

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

##  <a name="refreshrowset"></a>CRecordset：： RefreshRowset

更新当前行集中的行的数据和状态。

```
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>参数

*wRow*<br/>
当前行集中某一行的位置（从1开始）。 此值的范围为从零到行集的大小。

*wLockType*<br/>
一个值，该值指示在刷新行后如何锁定该行。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

如果为*wRow*传递的值为零，则将刷新行集中的每一行。

若要使用 `RefreshRowset`，必须通过在[Open](#open)成员函数中指定 `CRecordset::useMulitRowFetch` 选项来实现批量行提取。

`RefreshRowset` 调用 ODBC API 函数 `SQLSetPos`。 *WLockType*参数指定执行 `SQLSetPos` 后的行锁定状态。 下表描述了*wLockType*的可能值。

|wLockType|描述|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE （默认值）|驱动程序或数据源确保行处于调用 `RefreshRowset` 之前的锁定或解锁状态。|
|SQL_LOCK_EXCLUSIVE|驱动程序或数据源只锁定行。 并非所有数据源都支持这种类型的锁。|
|SQL_LOCK_UNLOCK|驱动程序或数据源将锁定该行。 并非所有数据源都支持这种类型的锁。|

有关 `SQLSetPos`的详细信息，请参阅 Windows SDK。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

##  <a name="requery"></a>CRecordset：： Requery

重新生成（刷新）记录集。

```
virtual BOOL Requery();
```

### <a name="return-value"></a>返回值

如果成功重新生成记录集，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果返回任何记录，则第一个记录将成为当前记录。

为了使记录集反映您或其他用户对数据源所做的添加和删除操作，您必须通过调用 `Requery`重新生成记录集。 如果记录集是动态集，则它会自动反映您或其他用户对其现有记录所做的更新（但不是添加）。 如果记录集是快照，则必须调用 `Requery` 来反映其他用户的编辑以及添加和删除操作。

对于动态集或快照，请使用新的筛选器或排序或新参数值，调用 `Requery` 任何时候要重新生成记录集。 设置新的筛选器或排序属性，方法是在调用 `Requery`之前将新值分配给 `m_strFilter` 和 `m_strSort`。 在调用 `Requery`之前，通过将新值分配给参数数据成员来设置新参数。 如果筛选器和排序字符串未更改，则可以重复使用查询，从而提高性能。

如果重新生成记录集的尝试失败，则关闭该记录集。 调用 `Requery`之前，可以通过调用 `CanRestart` 成员函数来确定是否可以重新查询记录集。 `CanRestart` 不保证 `Requery` 会成功。

> [!CAUTION]
>  仅在调用[Open](#open)后调用 `Requery`。

### <a name="example"></a>示例

此示例重新生成一个记录集以应用不同的排序顺序。

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

##  <a name="setabsoluteposition"></a>CRecordset：： SetAbsolutePosition

定位与指定记录号对应的记录上的记录集。

```
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>参数

*nRows*<br/>
记录集中当前记录的从1开始的序号位置。

### <a name="remarks"></a>备注

`SetAbsolutePosition` 根据此序号位置移动当前记录指针。

> [!NOTE]
>  此成员函数在只进记录集上无效。

对于 ODBC 记录集，绝对位置设置1指的是记录集中的第一条记录;如果设置为0，则表示文件的起始位置。

还可以将负值传递到 `SetAbsolutePosition`。 在这种情况下，将从记录集的末尾计算记录集的位置。 例如，`SetAbsolutePosition( -1 )` 将当前记录指针移动到记录集中的最后一条记录。

> [!NOTE]
>  绝对位置不应用作代理项记录号。 书签仍是保留并返回到给定位置的建议方法，因为在删除前面的记录后，记录的位置会发生变化。 此外，如果重新创建记录集，则不能确保给定的记录将具有相同的绝对位置，因为记录集中单个记录的顺序不能保证，除非是使用 Order BY 的 SQL 语句创建的。子句。

有关记录集导航和书签的详细信息，请参阅文章[记录集：滚动（odbc）](../../data/odbc/recordset-scrolling-odbc.md)和[记录集：书签和绝对位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。

##  <a name="setbookmark"></a>CRecordset：： SetBookmark

将记录集定位在包含指定书签的记录上。

```
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>参数

*varBookmark*<br/>
对包含特定记录书签值的[CDBVariant](../../mfc/reference/cdbvariant-class.md)对象的引用。

### <a name="remarks"></a>备注

若要确定记录集是否支持书签，请调用[CanBookmark](#canbookmark)。 若要使书签可用（如果支持），则必须在[Open](#open)成员函数的*dwOptions*参数中设置 `CRecordset::useBookmarks` 选项。

> [!NOTE]
>  如果书签不受支持或不可用，则调用 `SetBookmark` 将导致引发异常。 在只进记录集上不支持书签。

若要首先检索当前记录的书签，请调用[GetBookmark](#getbookmark)，这会将书签值保存到 `CDBVariant` 的对象。 稍后，可以通过使用保存的书签值调用 `SetBookmark`，返回到该记录。

> [!NOTE]
>  某些记录集操作完成后，应在调用 `SetBookmark`之前检查书签的持久性。 例如，如果使用 `GetBookmark` 检索书签，然后调用 `Requery`，则书签可能不再有效。 调用[CDatabase：： GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)以检查是否可以安全调用 `SetBookmark`。

有关书签和记录集导航的详细信息，请参阅文章[记录集：书签和绝对位置（odbc）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[记录集：滚动（odbc）](../../data/odbc/recordset-scrolling-odbc.md)。

##  <a name="setfielddirty"></a>CRecordset：： SetFieldDirty

将记录集的字段数据成员标记为已更改或保持不变。

```
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>参数

*函数*<br/>
包含记录集的字段数据成员的地址，或为 NULL。 如果为 NULL，则对记录集中的所有字段数据成员进行标记。 （C++ Null 与数据库术语中的 null 不相同，这意味着 "无值"。）

*bDirty*<br/>
如果要将字段数据成员标记为 "已更新" （已更改），则为 TRUE。 否则，如果将字段数据成员标记为 "清理" （未更改），则为 FALSE。

### <a name="remarks"></a>备注

将字段标记为 "未更改" 可确保字段不会更新，导致 SQL 流量更少。

> [!NOTE]
>  此成员函数不适用于使用批量取行的记录集。 如果已实现批量行提取，则 `SetFieldDirty` 将导致断言失败。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

框架标记已更改的字段数据成员，以确保通过记录字段交换（RFX）机制将它们写入数据源上的记录。 更改字段的值通常会自动对字段进行更新，因此，你很少需要自行调用 `SetFieldDirty`，但有时你可能需要确保列将被显式更新或插入，而不考虑字段数据中的值职员.

> [!CAUTION]
>  只有在调用 "[编辑](#edit)" 或 " [AddNew](#addnew)" 后才调用此成员函数。

将函数的第一个参数用于函数将仅应用于 `outputColumn` 字段，而不是 `param` 字段。 例如，调用

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

仅将 `outputColumn` 字段设置为 NULL;`param` 字段将不受影响。

若要处理 `param` 字段，必须提供要处理的单个 `param` 的实际地址，例如：

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

这意味着，你不能将所有 `param` 字段设置为 NULL，因为你可以在 `outputColumn` 字段。

##  <a name="setfieldnull"></a>CRecordset：： SetFieldNull

将记录集的字段数据成员标记为 Null （具体没有值）或非 Null。

```
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>参数

*函数*<br/>
包含记录集的字段数据成员的地址，或为 NULL。 如果为 NULL，则对记录集中的所有字段数据成员进行标记。 （C++ Null 与数据库术语中的 null 不相同，这意味着 "无值"。）

*bNull*<br/>
如果要将字段数据成员标记为没有值（Null），则为非零值。 否则，如果将字段数据成员标记为非 Null，则为0。

### <a name="remarks"></a>备注

向记录集添加新记录时，所有字段数据成员最初均设置为 Null 值并标记为 "已更新" （已更改）。 在从数据源中检索记录时，其列要么已包含值，要么是 Null。

> [!NOTE]
>  不要对使用批量取行的记录集调用此成员函数。 如果已实现批量行提取，则调用 `SetFieldNull` 将导致断言失败。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

如果要将当前记录的字段指定为不具有值，请调用 `SetFieldNull` 将*bNull*设置为 TRUE，以将其标记为 Null。 如果字段以前标记为 Null，并且你现在要为其指定值，只需设置其新值。 无需删除 `SetFieldNull`的 Null 标志。 若要确定是否允许字段为 Null，请调用 `IsFieldNullable`。

> [!CAUTION]
>  只有在调用 "[编辑](#edit)" 或 " [AddNew](#addnew)" 后才调用此成员函数。

将函数的第一个参数用于函数将仅应用于 `outputColumn` 字段，而不是 `param` 字段。 例如，调用

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

仅将 `outputColumn` 字段设置为 NULL;`param` 字段将不受影响。

若要处理 `param` 字段，必须提供要处理的单个 `param` 的实际地址，例如：

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

这意味着，你不能将所有 `param` 字段设置为 NULL，因为你可以在 `outputColumn` 字段。

> [!NOTE]
>  将参数设置为 Null 时，在打开记录集之前对 `SetFieldNull` 的调用会导致断言。 在这种情况下，请调用[SetParamNull](#setparamnull)。

`SetFieldNull` 通过[DoFieldExchange](#dofieldexchange)实现。

##  <a name="setlockingmode"></a>CRecordset：： SetLockingMode

将锁定模式设置为 "乐观" 锁定（默认值）或 "悲观" 锁定。 确定如何锁定记录以获取更新。

```
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>参数

*nMode*<br/>
包含 `enum LockMode`中的以下值之一：

- `optimistic` 乐观锁定将在调用 `Update`时锁定正在更新的记录。

- `pessimistic` 悲观锁定将在调用 `Edit` 时立即锁定记录，并使其保持锁定状态，直到完成 `Update` 调用或移动到新记录为止。

### <a name="remarks"></a>备注

如果需要指定记录集用于更新的两个记录锁定策略中的哪一个，请调用此成员函数。 默认情况下，将 `optimistic`记录集的锁定模式。 你可以将其更改为更小心 `pessimistic` 锁定策略。 在构造并打开 recordset 对象之后但在调用 `Edit`之前，请调用 `SetLockingMode`。

##  <a name="setparamnull"></a>CRecordset：： SetParamNull

将参数标记为 Null （具体没有值）或非 Null。

```
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
参数的从零开始的索引。

*bNull*<br/>
如果为 TRUE （默认值），则将参数标记为 Null。 否则，该参数将标记为非 Null。

### <a name="remarks"></a>备注

与[SetFieldNull](#setfieldnull)不同，您可以在打开记录集之前调用 `SetParamNull`。

`SetParamNull` 通常用于预定义的查询（存储过程）。

##  <a name="setrowsetcursorposition"></a>CRecordset：： SetRowsetCursorPosition

将光标移动到当前行集中的一行。

```
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>参数

*wRow*<br/>
当前行集中某一行的位置（从1开始）。 此值的范围为1到行集的大小。

*wLockType*<br/>
一个值，该值指示在刷新行后如何锁定该行。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

实现批量行提取时，记录由行集检索，其中提取的行集中的第一条记录为当前记录。 为了使行集中的另一记录成为当前记录，请调用 `SetRowsetCursorPosition`。 例如，可以将 `SetRowsetCursorPosition` 与[GetFieldValue](#getfieldvalue)成员函数结合，以便从记录集的任何记录中动态检索数据。

若要使用 `SetRowsetCursorPosition`，必须通过在[Open](#open)成员函数中指定*dwOptions*参数的 `CRecordset::useMultiRowFetch` 选项来实现批量行提取。

`SetRowsetCursorPosition` 调用 ODBC API 函数 `SQLSetPos`。 *WLockType*参数指定执行 `SQLSetPos` 后的行锁定状态。 下表描述了*wLockType*的可能值。

|wLockType|描述|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE （默认值）|驱动程序或数据源确保行处于调用 `SetRowsetCursorPosition` 之前的锁定或解锁状态。|
|SQL_LOCK_EXCLUSIVE|驱动程序或数据源只锁定行。 并非所有数据源都支持这种类型的锁。|
|SQL_LOCK_UNLOCK|驱动程序或数据源将锁定该行。 并非所有数据源都支持这种类型的锁。|

有关 `SQLSetPos`的详细信息，请参阅 Windows SDK。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

##  <a name="setrowsetsize"></a>CRecordset：： SetRowsetSize

指定在提取过程中要检索的记录数。

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>参数

*dwNewRowsetSize*<br/>
给定提取过程中要检索的行数。

### <a name="remarks"></a>备注

此虚拟成员函数指定使用批量行提取时要在单个提取过程中检索的行数。 若要实现批量行提取，必须在[Open](#open)成员函数的*dwOptions*参数中设置 `CRecordset::useMultiRowFetch` 选项。

> [!NOTE]
>  在未实现批量取行的情况下调用 `SetRowsetSize` 将导致断言失败。

在调用之前调用 `SetRowsetSize` `Open` 最初设置记录集的行集大小。 实现批量行提取时默认行集大小为25。

> [!NOTE]
>  调用 `SetRowsetSize`时请务必小心。 如果手动为数据分配存储（由 `Open`中 dwOptions 参数的 `CRecordset::userAllocMultiRowBuffers` 选项指定），则应检查是否需要在调用 `SetRowsetSize`之后但在执行任何游标之前重新分配这些存储缓冲区导航操作。

若要获取行集大小的当前设置，请调用[GetRowsetSize](#getrowsetsize)。

有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

##  <a name="update"></a>CRecordset：： Update

通过保存数据源上的新数据或编辑的数据来完成 `AddNew` 或 `Edit` 操作。

```
virtual BOOL Update();
```

### <a name="return-value"></a>返回值

如果成功更新一个记录，则为非零值;否则，如果没有列发生更改，则返回0。 如果未更新任何记录，或者更新了多个记录，则会引发异常。 对于数据源中的任何其他失败，也会引发异常。

### <a name="remarks"></a>备注

调用[AddNew](#addnew)或[Edit](#edit)成员函数后调用此成员函数。 完成 `AddNew` 或 `Edit` 操作需要执行此调用。

> [!NOTE]
>  如果已实现批量行提取，则无法调用 `Update`。 这将导致断言失败。 尽管类 `CRecordset` 不提供更新批量数据行的机制，但你可以使用 ODBC API 函数 `SQLSetPos`来编写你自己的函数。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

`AddNew` 和 `Edit` 准备一个编辑缓冲区，在此缓冲区中添加或编辑的数据用于保存到数据源。 `Update` 保存数据。 仅更新标记或检测为已更改的字段。

如果数据源支持事务，则可以对事务进行 `Update` 调用（及其相应的 `AddNew` 或 `Edit` 调用）部分。 有关事务的详细信息，请参阅[事务（ODBC）](../../data/odbc/transaction-odbc.md)一文。

> [!CAUTION]
>  如果在调用 `Update` 时未首先调用 `AddNew` 或 `Edit`，则 `Update` 将引发 `CDBException`。 如果调用 `AddNew` 或 `Edit`，则必须先调用 `Update`，然后才能调用 `Move` 操作或关闭记录集或数据源连接。 否则，你所做的更改将丢失，但不通知。

有关处理 `Update` 故障的详细信息，请参阅[记录记录集：记录集如何更新记录（ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)一文。

### <a name="example"></a>示例

请参阅[事务：在记录集中执行事务（ODBC）](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)一文。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDatabase 类](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView 类](../../mfc/reference/crecordview-class.md)
