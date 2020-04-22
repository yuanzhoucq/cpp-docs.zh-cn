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
ms.openlocfilehash: ab6cde9f478dc6f2e3cb0ba5bb338a3852f083fd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750501"
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
|[C记录集：CRecordset](#crecordset)|构造 `CRecordset` 对象。 派生类必须提供调用此构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CRecordset：：添加新](#addnew)|准备添加新记录。 调用`Update`以完成添加。|
|[C记录集：：可应用](#canappend)|如果可以通过成员函数将新记录添加到记录集，`AddNew`则返回非零。|
|[CRecordset：：CanBookmark](#canbookmark)|如果记录集支持书签，则返回非零。|
|[C 记录集：：取消](#cancel)|从第二个线程取消异步操作或进程。|
|[C记录集：：取消更新](#cancelupdate)|由于`AddNew`或`Edit`操作而取消任何挂起的更新。|
|[CRecordset：：可以重新启动](#canrestart)|如果`Requery`可以调用以再次运行记录集的查询，则返回非零。|
|[CRecordset：：CanScroll](#canscroll)|如果可以滚动浏览记录，则返回非零。|
|[CRecordset：：可以](#cantransact)|如果数据源支持事务，则返回非零。|
|[CRecordset：：可以更新](#canupdate)|如果可以更新记录集（可以添加、更新或删除记录），则返回非零。|
|[C记录集：：检查罗塞特错误](#checkrowseterror)|调用 以处理记录提取期间生成的错误。|
|[CRecordset：关闭](#close)|关闭记录集和与之关联的 ODBC HSTMT。|
|[C记录集：:Delete](#delete)|从记录集中删除当前记录。 删除后，必须显式滚动到其他记录。|
|[C记录集：:DoBulkFieldExchange](#dobulkfieldexchange)|调用以将数据从数据源到记录集的大量数据行交换。 实现批量记录字段交换（批量 RFX）。|
|[CRecordset：:DoFieldExchange](#dofieldexchange)|调用 以在记录集的字段数据成员和数据源上的相应记录之间交换数据（双向）。 实现记录字段交换 （RFX）。|
|[CRecordset：编辑](#edit)|准备对当前记录的更改。 调用`Update`以完成编辑。|
|[C 记录集：：刷新结果集](#flushresultset)|如果使用预定义的查询时，如果另一个要检索的结果集，则返回非零。|
|[CRecordset：获取书签](#getbookmark)|将记录的书签值分配给参数对象。|
|[C记录集：：获取默认连接](#getdefaultconnect)|已调用以获取默认连接字符串。|
|[C记录集：获取默认SQL](#getdefaultsql)|调用以获取要执行的默认 SQL 字符串。|
|[C记录集：：获取场值](#getfieldvalue)|返回记录集中的字段的值。|
|[C记录集：：获取ODBC字段计数](#getodbcfieldcount)|返回记录集中的字段数。|
|[CRecordset：：获取ODBC菲尔德信息](#getodbcfieldinfo)|返回有关记录集中字段的特定类型的信息。|
|[CRecordset：获取记录计数](#getrecordcount)|返回记录集中的记录数。|
|[C记录集：：获取罗数据集大小](#getrowsetsize)|返回您希望在单个提取期间检索的记录数。|
|[CRecordset：：获取行](#getrowsfetched)|返回在提取期间检索的实际行数。|
|[C记录集：获取罗维状态](#getrowstatus)|在提取后返回行的状态。|
|[C记录集：：获取SQL](#getsql)|获取用于选择记录集记录的 SQL 字符串。|
|[CRecordset：获取状态](#getstatus)|获取记录集的状态：当前记录的索引以及是否已获取记录的最终计数。|
|[C记录集：获取表名](#gettablename)|获取记录集所基于的表的名称。|
|[记录集：：IsBOF](#isbof)|如果记录集已定位在第一条记录之前，则返回非零。 没有最新记录。|
|[CRecordset：已删除](#isdeleted)|如果记录集位于已删除的记录上，则返回非零。|
|[记录集：：IsEOF](#iseof)|如果记录集位于最后一条记录之后，则返回非零。 没有最新记录。|
|[C记录集：：IsFieldDirty](#isfielddirty)|如果当前记录中的指定字段已更改，则返回非零。|
|[C记录集：：IsFieldNull](#isfieldnull)|如果当前记录中的指定字段为空（没有值），则返回非零。|
|[C 记录集：：可字段空](#isfieldnullable)|如果当前记录中的指定字段可以设置为 null（没有值），则返回非零。|
|[CRecordset：：是打开的](#isopen)|如果`Open`以前已调用，则返回非零。|
|[C 记录集：：移动](#move)|将记录集定位为从当前记录中的指定记录数，以任一方向。|
|[C 记录集：：先移动](#movefirst)|将当前记录定位到记录集中的第一条记录上。 首先进行测试`IsBOF`。|
|[C 记录集：：移动上次](#movelast)|将当前记录定位到最后一条记录或最后一个行集上。 首先进行测试`IsEOF`。|
|[C记录集：：移动下一个](#movenext)|将当前记录定位在下一条记录或下一个行集上。 首先进行测试`IsEOF`。|
|[C记录集：：MovePrev](#moveprev)|将当前记录定位到上一条记录或上一个行集上。 首先进行测试`IsBOF`。|
|[CRecordset：：打开选项](#onsetoptions)|调用以为指定的 ODBC 语句设置选项（在选择时使用）。|
|[CRecordset：：打开更新选项](#onsetupdateoptions)|调用以为指定的 ODBC 语句设置选项（在更新时使用）。|
|[CRecordset：：打开](#open)|通过检索表或执行记录集表示的查询来打开记录集。|
|[C记录集：：刷新罗塞特](#refreshrowset)|刷新指定行的数据和状态。|
|[C记录集：：重新查询](#requery)|再次运行记录集的查询以刷新所选记录。|
|[C记录集：：设置绝对位置](#setabsoluteposition)|将记录集放在与指定记录编号对应的记录上。|
|[CRecordset：：设置书签](#setbookmark)|将记录集放在书签指定的记录上。|
|[C记录集：：设置字段脏](#setfielddirty)|将当前记录中的指定字段标记为已更改。|
|[C记录集：：设置字段无效](#setfieldnull)|将当前记录中指定字段的值设置为 null（没有值）。|
|[C记录集：：设置锁定模式](#setlockingmode)|将锁定模式设置为"乐观"锁定（默认）或"悲观"锁定。 确定如何锁定记录以进行更新。|
|[C 记录集：：SetParamNull](#setparamnull)|将指定的参数设置为 null（没有值）。|
|[C 记录集：：设置罗塞特游标位置](#setrowsetcursorposition)|将光标定位在行集中的指定行上。|
|[C 记录集：：设置罗塞特大小](#setrowsetsize)|指定您希望在提取期间检索的记录数。|
|[CRecordset：：更新](#update)|通过在数据源上`AddNew`保存`Edit`新的或编辑的数据来完成 或 操作。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CRecordset：：m_hstmt](#m_hstmt)|包含记录集的 ODBC 语句句柄。 键入 `HSTMT`。|
|[CRecordset：m_nFields](#m_nfields)|包含记录集中的字段数据成员数。 键入 `UINT`。|
|[CRecordset：m_nParams](#m_nparams)|包含记录集中的参数数据成员数。 键入 `UINT`。|
|[CRecordset：m_pDatabase](#m_pdatabase)|包含指向记录集连接到数据源`CDatabase`的对象的指针。|
|[CRecordset：：m_strFilter](#m_strfilter)|包含 指定`CString`结构化查询语言 （SQL）`WHERE`子句的 。 用作筛选器，仅选择满足特定条件的记录。|
|[CRecordset：m_strSort](#m_strsort)|包含指定`CString`SQL`ORDER BY`子句的 。 用于控制记录的排序方式。|

## <a name="remarks"></a><a name="remarks"></a> 备注

对象称为"记录集"，`CRecordset`通常以两种形式使用：动态集和快照。 动态集与其他用户进行的数据更新保持同步。 快照是数据的静态视图。 每个窗体表示在打开记录集时修复的一组记录，但当您滚动到动态集中的记录时，它反映随后由其他用户或应用程序中的其他记录集对记录所做的更改。

> [!NOTE]
> 如果使用数据访问对象 （DAO） 类而不是开放数据库连接 （ODBC） 类，请使用类[CDaoRecordset。](../../mfc/reference/cdaorecordset-class.md) 有关详细信息，请参阅文章[概述：数据库编程](../../data/data-access-programming-mfc-atl.md)。

要使用任一类型的记录集，通常从`CRecordset`派生特定于应用程序的记录集类。 记录集从数据源中选择记录，然后您可以：

- 滚动记录。

- 更新记录并指定锁定模式。

- 筛选记录集以约束它从数据源上可用的记录中选择哪些记录。

- 对记录集进行排序。

- 参数化记录集，以自定义其选择与在运行时之前不知道的信息。

要使用类，请打开数据库并构造记录集对象，将构造函数传递指向对象的`CDatabase`指针。 然后调用记录集`Open`的成员函数，您可以在其中指定对象是动态集还是快照。 调用`Open`从数据源中选择数据。 打开记录集对象后，使用其成员函数和数据成员滚动记录并对其进行操作。 可用的操作取决于对象是动态集还是快照，它是可更新还是只读（这取决于开放数据库连接 （ODBC） 数据源的功能，以及您是否实现了批量行提取。 要刷新自`Open`调用以来可能已更改或添加的记录，请调用对象`Requery`的成员函数。 调用对象的`Close`成员函数，并在对象完成时销毁该函数。

在派生`CRecordset`类中，记录字段交换 （RFX） 或批量记录字段交换 （Bulk RFX） 用于支持记录字段的读取和更新。

有关记录集和记录字段交换的详细信息，请参阅文章[概述：数据库编程](../../data/data-access-programming-mfc-atl.md)、[记录集 （ODBC）、](../../data/odbc/recordset-odbc.md)[记录集：批量提取记录 （ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 （RFX）。](../../data/odbc/record-field-exchange-rfx.md) 有关动态集和快照的重点，请参阅[文章动态集](../../data/odbc/dynaset.md)和[快照](../../data/odbc/snapshot.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="crecordsetaddnew"></a><a name="addnew"></a>CRecordset：：添加新

准备向表添加新记录。

```
virtual void AddNew();
```

### <a name="remarks"></a>备注

您必须调用[重新查询](#requery)成员函数才能看到新添加的记录。 记录的字段最初为空。 （在数据库术语中，Null 表示"没有值"，并且与 C++ 中的 NULL 不同。要完成该操作，必须调用[Update](#update)成员函数。 `Update`将更改保存到数据源。

> [!NOTE]
> 如果已实现批量行提取，则无法调用`AddNew`。 这将导致断言失败。 尽管类`CRecordset`不提供更新批量数据行的机制，但您可以使用 ODBC API 函数编写自己的函数`SQLSetPos`。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

`AddNew`使用记录集的字段数据成员准备新的空记录。 调用`AddNew`后，在记录集的字段数据成员中设置所需的值。 （为此，您不必调用[Edit](#edit)成员函数;`Edit`仅用于现有记录。随后调用`Update`时，字段数据成员中更改的值将保存在数据源上。

> [!CAUTION]
> 如果在调用`Update`之前滚动到新记录，则新记录将丢失，并且不发出警告。

如果数据源支持事务，则可以将`AddNew`呼叫作为事务的一部分。 有关事务的详细信息，请参阅类[CDatabase](../../mfc/reference/cdatabase-class.md)。 请注意，在调用`AddNew`之前，应调用[CDatabase：：开始转换](../../mfc/reference/cdatabase-class.md#begintrans)。

> [!NOTE]
> 对于动态集，新记录将作为最后一条记录添加到记录集。 添加的记录不会添加到快照中;因此，这些记录不会添加到快照中。您必须调用`Requery`以刷新记录集。

调用`AddNew`其成员`Open`函数未调用的记录集是非法的。 如果`CDBException`调用`AddNew`无法追加到的记录集，则引发 。 您可以通过调用[CanAppend](#canappend)来确定记录集是否可更新。

有关详细信息，请参阅以下文章：[记录集：记录集如何更新记录 （ODBC）、](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)[记录集：添加、更新和删除记录 （ODBC）](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)和[事务 （ODBC）。](../../data/odbc/transaction-odbc.md)

### <a name="example"></a>示例

请参阅文章["事务：在记录集 （ODBC） 中执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)"。

## <a name="crecordsetcanappend"></a><a name="canappend"></a>C记录集：：可应用

确定以前打开的记录集是否允许您添加新记录。

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>返回值

如果记录集允许添加新记录，则非零;否则 0。 `CanAppend`如果以只读身份打开记录集，则返回 0。

## <a name="crecordsetcanbookmark"></a><a name="canbookmark"></a>CRecordset：：CanBookmark

确定记录集是否允许您使用书签标记记录。

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>返回值

如果记录集支持书签，则非零;否则 0。

### <a name="remarks"></a>备注

此函数独立于[Open](#open) `CRecordset::useBookmarks`成员函数的*dwOption*参数中的选项。 `CanBookmark`指示给定的 ODBC 驱动程序和光标类型是否支持书签。 `CRecordset::useBookmarks`指示书签是否可用，前提是书签受支持。

> [!NOTE]
> 仅转发记录集不支持书签。

有关书签和记录集导航的详细信息，请参阅[文章"记录集：书签和绝对位置 （ODBC）"](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和["记录集：滚动 （ODBC）"。](../../data/odbc/recordset-scrolling-odbc.md)

## <a name="crecordsetcancel"></a><a name="cancel"></a>C 记录集：：取消

请求数据源取消正在进行的异步操作或从第二个线程取消进程。

```cpp
void Cancel();
```

### <a name="remarks"></a>备注

请注意，MFC ODBC 类不再使用异步处理;要执行同色诺操作，必须直接调用 ODBC API 函数`SQLSetConnectOption`。 有关详细信息，请参阅*ODBC SDK 程序员指南*中的主题"异步执行函数"。

## <a name="crecordsetcancelupdate"></a><a name="cancelupdate"></a>C记录集：：取消更新

在调用[更新](#update)之前，取消由[编辑](#edit)或[AddNew](#addnew)操作引起的任何挂起更新。

```cpp
void CancelUpdate();
```

### <a name="remarks"></a>备注

> [!NOTE]
> 此成员函数不适用于使用批量行提取的记录集，因为此类记录集无法调用`Edit`或`AddNew`。 `Update` 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

如果启用了自动脏字段检查，`CancelUpdate`则成员变量将还原到以前`Edit`或`AddNew`已调用的值;否则，任何值更改都将保留。 默认情况下，在打开记录集时启用自动字段检查。 要禁用它，必须在[Open](#open) `CRecordset::noDirtyFieldCheck`成员函数的*dwOptions*参数中指定 。

有关更新数据的详细信息，请参阅[记录集：添加、更新和删除记录 （ODBC） 。](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

## <a name="crecordsetcanrestart"></a><a name="canrestart"></a>CRecordset：：可以重新启动

确定记录集是否允许通过调用`Requery`成员函数重新启动其查询（刷新其记录）。

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>返回值

允许重新查询时非零;否则 0。

## <a name="crecordsetcanscroll"></a><a name="canscroll"></a>CRecordset：：CanScroll

确定记录集是否允许滚动。

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>返回值

如果记录集允许滚动，则非零;否则 0。

### <a name="remarks"></a>备注

有关滚动的详细信息，请参阅[文章"记录集：滚动"（ODBC）。](../../data/odbc/recordset-scrolling-odbc.md)

## <a name="crecordsetcantransact"></a><a name="cantransact"></a>CRecordset：：可以

确定记录集是否允许事务。

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>返回值

如果记录集允许事务，则非零;否则 0。

### <a name="remarks"></a>备注

有关详细信息，请参阅文章[事务 （ODBC）](../../data/odbc/transaction-odbc.md)。

## <a name="crecordsetcanupdate"></a><a name="canupdate"></a>CRecordset：：可以更新

确定是否可以更新记录集。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>返回值

如果可以更新记录集，则非零;否则 0。

### <a name="remarks"></a>备注

如果基础数据源是只读的，或者在打开记录集时在*dwOptions*参数中`CRecordset::readOnly`指定，则记录集可能是只读的。

## <a name="crecordsetcheckrowseterror"></a><a name="checkrowseterror"></a>C记录集：：检查罗塞特错误

调用 以处理记录提取期间生成的错误。

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>参数

*nRetCode*<br/>
ODBC API 函数返回代码。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

此虚拟成员函数处理提取记录时发生的错误，并且在批量行提取期间非常有用。 您可能需要考虑重写`CheckRowsetError`来实现您自己的错误处理。

`CheckRowsetError`在游标导航操作（如`Open`、`Requery`或任何`Move`操作）中自动调用。 它传递了ODBC API函数`SQLExtendedFetch`的返回值。 下表列出了*nRetCode*参数的可能值。

|nRetCode|说明|
|--------------|-----------------|
|SQL_SUCCESS|功能成功完成;没有其他信息可用。|
|SQL_SUCCESS_WITH_INFO|功能成功完成，可能出现非致命错误。 可以通过调用`SQLError`获得其他信息。|
|SQL_NO_DATA_FOUND|已提取结果集中的所有行。|
|SQL_ERROR|功能失败。 可以通过调用`SQLError`获得其他信息。|
|SQL_INVALID_HANDLE|由于环境句柄、连接句柄或语句句柄无效，功能失败。 这表示编程错误。 没有来自`SQLError`的其他信息。|
|SQL_STILL_EXECUTING|以异步方式启动的函数仍在执行中。 请注意，默认情况下，MFC 永远不会将此值传递给`CheckRowsetError`。MFC 将继续调用`SQLExtendedFetch`，直到不再返回SQL_STILL_EXECUTING。|

有关 的详细信息`SQLError`，请参阅 Windows SDK。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

## <a name="crecordsetclose"></a><a name="close"></a>CRecordset：关闭

关闭记录集。

```
virtual void Close();
```

### <a name="remarks"></a>备注

处理为记录集分配的 ODBC HSTMT 和框架分配的所有内存。 通常在调用`Close`后，如果C++记录集对象是使用**new**分配的，则删除该对象。

通话后可以`Open`再次呼叫`Close`。 这允许您重用记录集对象。 另一种选择是调用`Requery`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

## <a name="crecordsetcrecordset"></a><a name="crecordset"></a>C记录集：CRecordset

构造 `CRecordset` 对象。

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>参数

*p数据库*<br/>
包含指向`CDatabase`对象的指针或值 NULL。 如果不是 NULL，并且`CDatabase`尚未调用对象`Open`的成员函数将其连接到数据源，则记录集会尝试在它自己的`Open`调用期间为您打开它。 如果传递 NULL，将使用`CDatabase`使用 ClassWizard 派生记录集类时指定的数据源信息构造和连接对象。

### <a name="remarks"></a>备注

可以直接使用`CRecordset`或派生应用程序`CRecordset`特定的类。 您可以使用 ClassWizard 派生记录集类。

> [!NOTE]
> 派生类*必须*提供其自己的构造函数。 在派生类的构造函数中，调用构造函数`CRecordset::CRecordset`，将适当的参数传递给它。

将 NULL 传递给记录集构造函数，以便`CDatabase`自动构造和连接对象。 这是一个有用的速记，不需要在构造记录集之前构造和连接`CDatabase`对象。

### <a name="example"></a>示例

有关详细信息，请参阅[记录集：为表 （ODBC） 声明类）的文章](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。

## <a name="crecordsetdelete"></a><a name="delete"></a>C记录集：:Delete

删除当前记录。

```
virtual void Delete();
```

### <a name="remarks"></a>备注

成功删除后，记录集的字段数据成员将设置为 Null 值，您必须显式调用其中一个`Move`函数才能移出已删除的记录。 一旦您移出已删除的记录，将无法返回到它。 如果数据源支持事务，则可以使`Delete`调用成为事务的一部分。 有关详细信息，请参阅文章[事务 （ODBC）](../../data/odbc/transaction-odbc.md)。

> [!NOTE]
> 如果已实现批量行提取，则无法调用`Delete`。 这将导致断言失败。 尽管类`CRecordset`不提供更新批量数据行的机制，但您可以使用 ODBC API 函数编写自己的函数`SQLSetPos`。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

> [!CAUTION]
> 记录集必须是可备份的，并且调用`Delete`记录集时必须有有效的记录电流。否则，将发生错误。 例如，如果删除记录，但在再次调用`Delete`之前不滚动到新记录，则`Delete`引发[CDBException](../../mfc/reference/cdbexception-class.md)。

与[AddNew](#addnew)和[Edit](#edit)`Delete`不同，调用 后不会调用[更新](#update)。 如果`Delete`调用失败，字段数据成员保持不变。

### <a name="example"></a>示例

此示例显示在函数的帧上创建的记录集。 该示例假定 存在`m_dbCust`，类型的成员`CDatabase`变量已连接到数据源。

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

## <a name="crecordsetdobulkfieldexchange"></a><a name="dobulkfieldexchange"></a>C记录集：:DoBulkFieldExchange

调用以将数据从数据源到记录集的大量数据行交换。 实现批量记录字段交换（批量 RFX）。

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象的指针。 框架已经设置了此对象，以指定字段交换操作的上下文。

### <a name="remarks"></a>备注

实现批量行提取时，框架将调用此成员函数以自动将数据从数据源传输到记录集对象。 `DoBulkFieldExchange`还将参数数据成员（如果有）绑定到 SQL 语句字符串中的参数占位符，以便记录集的选择。

如果未实现批量行提取，则框架将调用[DoFieldExchange](#dofieldexchange)。 要实现批量行提取，必须在[Open](#open)成员`CRecordset::useMultiRowFetch`函数中指定*dwOptions*参数的选项。

> [!NOTE]
> `DoBulkFieldExchange`仅当使用派生自 的`CRecordset`类时才可用。 如果直接从 中`CRecordset`创建了记录集对象，则必须调用[GetFieldValue](#getfieldvalue)成员函数来检索数据。

批量记录字段交换 （批量 RFX） 类似于记录字段交换 （RFX）。 数据会自动从数据源传输到记录集对象。 但是，`AddNew`您不能调用 、`Edit``Delete`或`Update`将更改传输回数据源。 类`CRecordset`当前不提供更新大量数据行的机制;因此，类不提供更新数据批量行的机制。但是，您可以使用 ODBC API 函数编写自己的函数`SQLSetPos`。

请注意，ClassWizard 不支持批量记录字段交换;因此，该类向导不支持批量记录字段交换。因此，您必须通过编写`DoBulkFieldExchange`对批量 RFX 函数的调用来手动覆盖。 有关这些函数的详细信息，请参阅主题[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。

有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。 有关相关信息，请参阅文章[记录字段交换 （RFX）](../../data/odbc/record-field-exchange-rfx.md)。

## <a name="crecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CRecordset：:DoFieldExchange

调用 以在记录集的字段数据成员和数据源上的相应记录之间交换数据（双向）。 实现记录字段交换 （RFX）。

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象的指针。 框架已经设置了此对象，以指定字段交换操作的上下文。

### <a name="remarks"></a>备注

未实现批量行提取时，框架将调用此成员函数，以在记录集对象的字段数据成员和数据源上的当前记录的相应列之间自动交换数据。 `DoFieldExchange`还将参数数据成员（如果有）绑定到 SQL 语句字符串中的参数占位符，以便记录集的选择。

如果实现了批量行提取，则框架将调用[DoBulkFieldExchange](#dobulkfieldexchange)。 要实现批量行提取，必须在[Open](#open)成员`CRecordset::useMultiRowFetch`函数中指定*dwOptions*参数的选项。

> [!NOTE]
> `DoFieldExchange`仅当使用派生自 的`CRecordset`类时才可用。 如果直接从 中`CRecordset`创建了记录集对象，则必须调用[GetFieldValue](#getfieldvalue)成员函数来检索数据。

字段数据交换（称为记录字段交换 （RFX） 在两个方向上工作：从记录集对象的字段数据成员到数据源上记录的字段，以及从数据源上的记录到记录集对象。

`DoFieldExchange`对于派生的记录集类，通常需要执行的唯一操作是使用 ClassWizard 创建类并指定字段数据成员的名称和数据类型。 您还可以向 ClassWizard 编写的代码添加代码，以指定参数数据成员或动态处理绑定的任何列。 有关详细信息，请参阅[文章记录集：动态绑定数据列 （ODBC）。](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

当您使用 ClassWizard 声明派生的记录集类时，向导`DoFieldExchange`会为您编写一个重写，类似于以下示例：

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

有关 RFX 函数的详细信息，请参阅主题[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。

有关 有关 的进一`DoFieldExchange`步示例和详细信息，请参阅[文章记录字段交换：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。 有关 RFX 的一般信息，请参阅记录[字段交换](../../data/odbc/record-field-exchange-rfx.md)的文章 。

## <a name="crecordsetedit"></a><a name="edit"></a>CRecordset：编辑

允许更改当前记录。

```
virtual void Edit();
```

### <a name="remarks"></a>备注

调用`Edit`后，可以通过直接重置字段数据成员的值来更改它们。 当您随后调用[Update](#update)成员函数以在数据源上保存更改时，操作将完成。

> [!NOTE]
> 如果已实现批量行提取，则无法调用`Edit`。 这将导致断言失败。 尽管类`CRecordset`不提供更新批量数据行的机制，但您可以使用 ODBC API 函数编写自己的函数`SQLSetPos`。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

`Edit`保存记录集的数据成员的值。 如果调用`Edit`，进行更改，然后再次调用`Edit`，记录的值将还原到第一次`Edit`调用之前的值。

在某些情况下，您可能希望通过使列为 Null（不包含任何数据）来更新列。 为此，请使用 TRUE 参数调用[SetFieldNull](#setfieldnull)以标记字段 Null;这还会导致更新列。 如果希望将字段写入数据源，即使其值未更改，请使用 TRUE 参数调用[SetFieldDirty。](#setfielddirty) 即使字段的值为 Null，这也能起作用。

如果数据源支持事务，则可以使`Edit`调用成为事务的一部分。 请注意，在调用`Edit`之前和打开记录集之后，应调用[CDatabase：：BeginTrans。](../../mfc/reference/cdatabase-class.md#begintrans) 另请注意，调用[CDatabase：：CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)不能替代调用`Update`来完成操作。 `Edit` 有关事务的详细信息，请参阅类[CDatabase](../../mfc/reference/cdatabase-class.md)。

根据当前锁定模式，更新的记录可能会锁定，`Edit`直到您调用`Update`或滚动到其他记录，或者它可能仅在`Edit`调用期间锁定。 您可以使用[SetLockingMode](#setlockingmode)更改锁定模式。

如果在调用`Update`之前滚动到新记录，则还原当前记录的上一个值。 如果`CDBException`调用`Edit`无法更新的记录集或没有当前记录，则引发 A。

有关详细信息，请参阅[文章事务 （ODBC）](../../data/odbc/transaction-odbc.md)和[记录集：锁定记录 （ODBC）。](../../data/odbc/recordset-locking-records-odbc.md)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

## <a name="crecordsetflushresultset"></a><a name="flushresultset"></a>C 记录集：：刷新结果集

如果有多个结果集，则检索预定义查询（存储过程）的下一个结果集。

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>返回值

如果要检索更多结果集，则非零;否则 0。

### <a name="remarks"></a>备注

仅当当前结果`FlushResultSet`集中的光标完全完成时，才应调用。 请注意，当您通过调用检索下一个结果集`FlushResultSet`时，光标在该结果集中无效;因此，当您通过调用检索下一个结果集时，光标对该结果集无效。调用 后应调用[MoveNext](#movenext)成员`FlushResultSet`函数。

如果预定义的查询使用输出参数或输入/输出参数，则必须调用`FlushResultSet`直到返回`FALSE`（值 0），才能获取这些参数值。

`FlushResultSet`调用 ODBC API`SQLMoreResults`函数 。 如果`SQLMoreResults`返回SQL_ERROR或SQL_INVALID_HANDLE，则`FlushResultSet`将引发异常。 有关 的详细信息`SQLMoreResults`，请参阅 Windows SDK。

如果要调用`FlushResultSet`，则存储过程需要具有绑定字段。

### <a name="example"></a>示例

以下代码假定该`COutParamRecordset`对象是基于`CRecordset`具有输入参数和输出参数的预定义查询且具有多个结果集的派生对象。 请注意[DoFieldExchange](#dofieldexchange)覆盖的结构。

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

## <a name="crecordsetgetbookmark"></a><a name="getbookmark"></a>CRecordset：获取书签

获取当前记录的书签值。

```cpp
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>参数

*瓦尔布克马克*<br/>
对表示当前记录上书签的[CDBVariant](../../mfc/reference/cdbvariant-class.md)对象的引用。

### <a name="remarks"></a>备注

要确定记录集是否支持书签，请调用[CanBookmark](#canbookmark)。 要使书签在受支持时可用，必须在[Open](#open)成员函数`CRecordset::useBookmarks`的*dwOptions*参数中设置该选项。

> [!NOTE]
> 如果书签不受支持或不可用，则调用`GetBookmark`将导致引发异常。 仅转发记录集不支持书签。

`GetBookmark`将当前记录的书签值分配给`CDBVariant`对象。 要在移动到其他记录后随时返回到该记录，请使用相应的`CDBVariant`对象调用[SetBookmark。](#setbookmark)

> [!NOTE]
> 某些记录集操作后，书签可能不再有效。 例如，如果调用`GetBookmark`后跟`Requery`，可能无法返回 使用`SetBookmark`的记录。 调用[CDatabase：获取书签持久性](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)，以检查是否可以安全地调用`SetBookmark`。

有关书签和记录集导航的详细信息，请参阅[文章"记录集：书签和绝对位置 （ODBC）"](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和["记录集：滚动 （ODBC）"。](../../data/odbc/recordset-scrolling-odbc.md)

## <a name="crecordsetgetdefaultconnect"></a><a name="getdefaultconnect"></a>C记录集：：获取默认连接

已调用以获取默认连接字符串。

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>返回值

包含`CString`默认连接字符串的 。

### <a name="remarks"></a>备注

框架调用此成员函数以获取记录集所基于的数据源的默认连接字符串。 ClassWizard 通过标识在 ClassWizard 中使用的相同数据源来获取有关表和列的信息，从而为您实现此函数。 在开发应用程序时，您可能会发现依赖此默认连接很方便。 但是，默认连接可能不适合应用程序的用户。 如果是这种情况，您应该重新实现此函数，放弃 ClassWizard 的版本。 有关连接字符串的详细信息，请参阅文章[数据源 （ODBC）](../../data/odbc/data-source-odbc.md)。

## <a name="crecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>C记录集：获取默认SQL

调用以获取要执行的默认 SQL 字符串。

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>返回值

包含`CString`默认 SQL 语句的 。

### <a name="remarks"></a>备注

框架调用此成员函数以获取记录集所基于的默认 SQL 语句。 这可能是表名称或 SQL **SELECT**语句。

通过使用 ClassWizard 声明记录集类来间接定义默认 SQL 语句，ClassWizard 会为您执行此任务。

如果需要 SQL 语句字符串供自己使用，请调用`GetSQL`，这将返回用于在打开记录集记录时使用的 SQL 语句。 您可以在类的重写中编辑默认 SQL 字符串`GetDefaultSQL`。 例如，可以使用**CALL**语句指定对预定义查询的调用。 （但是请注意，如果编辑`GetDefaultSQL`，还需要修改`m_nFields`以匹配数据源中的列数。

有关详细信息，请参阅[记录集：为表 （ODBC） 声明类）的文章](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。

> [!CAUTION]
> 如果框架无法标识表名称、提供了多个表名称或无法解释**CALL**语句，则表名称将为空。 请注意，使用**CALL**语句时，不得在大括号和**CALL**关键字之间插入空格，也不应在 curly 大括号之前或在**SELECT**语句中的**SELECT**关键字之前插入空白。

## <a name="crecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>C记录集：：获取场值

检索当前记录中的字段数据。

```cpp
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

*lpsz名称*<br/>
字段的名称。

*varValu*e 对将存储字段值的[CDBVariant](../../mfc/reference/cdbvariant-class.md)对象的引用。

*nFieldType*<br/>
字段的 ODBC C 数据类型。 使用默认值 DEFAULT_FIELD_TYPE 强制`GetFieldValue`根据下表从 SQL 数据类型确定 C 数据类型。 否则，您可以直接指定数据类型或选择兼容的数据类型;例如，您可以将任何数据类型存储在SQL_C_CHAR。

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

有关 ODBC 数据类型的详细信息，请参阅 Windows SDK 附录 D 中的"SQL 数据类型"和"C 数据类型"主题。

*nIndex*<br/>
字段的零基索引。

*strValue*<br/>
对[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的引用，该对象将存储转换为文本的字段值，而不考虑字段的数据类型。

### <a name="remarks"></a>备注

您可以按名称或索引查找字段。 可以将字段值存储在`CDBVariant`对象或`CString`对象中。

如果已实现批量行提取，则当前记录始终位于行集中的第一个记录上。 要对`GetFieldValue`给定行集中的记录使用，必须首先调用[SetRowsetCursorPosition](#setrowsetcursorposition)成员函数，以将光标移动到该行集中的所需行。 然后调用`GetFieldValue`该行。 要实现批量行提取，必须在[Open](#open)成员`CRecordset::useMultiRowFetch`函数中指定*dwOptions*参数的选项。

可用于`GetFieldValue`在运行时动态提取字段，而不是在设计时静态绑定字段。 例如，如果直接从 中`CRecordset`声明记录集对象，则必须使用`GetFieldValue`来检索字段数据;如果已直接从 中声明记录集对象。未实现记录字段交换 （RFX） 或批量记录字段交换 （Bulk RFX）。

> [!NOTE]
> 如果声明记录集对象而不派生于`CRecordset`，则不加载 ODBC 游标库。 游标库要求记录集至少有一个绑定列;因此，该库要求记录集至少具有一个绑定列。但是，当您直接使用`CRecordset`时，不会绑定任何列。 成员函数[CDatabase：：OpenEx](../../mfc/reference/cdatabase-class.md#openex)和[CDatabase：：打开](../../mfc/reference/cdatabase-class.md#open)控制是否将加载游标库。

`GetFieldValue`调用 ODBC API`SQLGetData`函数 。 如果驱动程序输出值SQL_NO_TOTAL字段值的实际长度，则`GetFieldValue`引发异常。 有关 的详细信息`SQLGetData`，请参阅 Windows SDK。

### <a name="example"></a>示例

以下示例代码说明了直接从`GetFieldValue`中声明的记录集对象的调用。 `CRecordset`

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
> 与 DAO`CDaoRecordset`类`CRecordset`不同，没有`SetFieldValue`成员函数。 如果直接从`CRecordset`创建对象，则该对象实际上是只读的。

有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

## <a name="crecordsetgetodbcfieldcount"></a><a name="getodbcfieldcount"></a>C记录集：：获取ODBC字段计数

检索记录集对象中的字段总数。

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>返回值

记录集中的字段数。

### <a name="remarks"></a>备注

有关创建记录集的详细信息，请参阅[文章"记录集：创建和关闭记录集 "（ODBC）。](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

## <a name="crecordsetgetodbcfieldinfo"></a><a name="getodbcfieldinfo"></a>CRecordset：：获取ODBC菲尔德信息

获取有关记录集中的字段的信息。

```cpp
void GetODBCFieldInfo(
    LPCTSTR lpszName,
    CODBCFieldInfo& fieldinfo);

void GetODBCFieldInfo(
    short nIndex,
    CODBCFieldInfo& fieldinfo);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
字段的名称。

*菲尔德信息*<br/>
对结构的`CODBCFieldInfo`引用。

*nIndex*<br/>
字段的零基索引。

### <a name="remarks"></a>备注

函数的一个版本允许您按名称查找字段。 另一个版本允许您按索引查找字段。

有关返回的信息的说明，请参阅[CODBCFieldInfo](../../mfc/reference/codbcfieldinfo-structure.md)结构。

有关创建记录集的详细信息，请参阅[文章"记录集：创建和关闭记录集 "（ODBC）。](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

## <a name="crecordsetgetrecordcount"></a><a name="getrecordcount"></a>CRecordset：获取记录计数

确定记录集的大小。

```
long GetRecordCount() const;
```

### <a name="return-value"></a>返回值

记录集中的记录数;如果记录集不包含任何记录，则为 0;或 -1，如果无法确定记录计数。

### <a name="remarks"></a>备注

> [!CAUTION]
> 记录计数被保留为"高水位线"，这是用户在记录中移动时记录数量最多的记录。 只有在用户超出最后一条记录后，才能知道记录总数。 出于性能原因，当您调用`MoveLast`时，计数不会更新。 要自己计算记录，请重复`MoveNext`调用，`IsEOF`直到返回非零。 通过`CRecordset:AddNew`添加记录并增加`Update`计数;通过`CRecordset::Delete`删除记录可减少计数。

## <a name="crecordsetgetrowsetsize"></a><a name="getrowsetsize"></a>C记录集：：获取罗数据集大小

获取要在给定提取期间检索的行数的当前设置。

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>返回值

给定提取期间要检索的行数。

### <a name="remarks"></a>备注

如果使用批量行提取，则打开记录集时的默认行集大小为 25;如果正在使用批量行提取，则打开记录集时的默认行集大小为 25;否则，它是 1。

要实现批量行提取，必须在[Open](#open)成员`CRecordset::useMultiRowFetch`函数的*dwOptions*参数中指定选项。 要更改行集大小的设置，请调用[SetRowsetSize](#setrowsetsize)。

有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

## <a name="crecordsetgetrowsfetched"></a><a name="getrowsfetched"></a>CRecordset：：获取行

确定提取后实际检索的记录数。

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>返回值

给定提取后从数据源检索的行数。

### <a name="remarks"></a>备注

当您已实现批量行提取时，这非常有用。 行集大小通常指示将从提取中检索多少行;因此，从提取中检索的行数。但是，记录集中的行总数也会影响将在行集中检索的行数。 例如，如果记录集有 10 条记录，行集大小设置为 4，则通过调用`MoveNext`遍历记录集将导致最终行集只有 2 条记录。

要实现批量行提取，必须在[Open](#open)成员`CRecordset::useMultiRowFetch`函数的*dwOptions*参数中指定选项。 要指定行集大小，请调用[SetRowsetSize](#setrowsetsize)。

有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

## <a name="crecordsetgetrowstatus"></a><a name="getrowstatus"></a>C记录集：获取罗维状态

获取当前行集中行的状态。

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>参数

*wRow*<br/>
当前行集中行的基于一个位置。 此值的范围可以从 1 到行集的大小。

### <a name="return-value"></a>返回值

行的状态值。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

`GetRowStatus`返回一个值，指示自上次从数据源检索行以来行状态的任何更改，或者未提取与*wRow*对应的行。 下表列出可能的返回值。

|状态值|说明|
|------------------|-----------------|
|SQL_ROW_SUCCESS|该行保持不变。|
|SQL_ROW_UPDATED|该行已更新。|
|SQL_ROW_DELETED|已删除该行。|
|SQL_ROW_ADDED|该行已添加。|
|SQL_ROW_ERROR|由于错误，该行无法检索。|
|SQL_ROW_NOROW|没有对应于*wRow*的行。|

有关详细信息，请参阅 Windows SDK 中的`SQLExtendedFetch`ODBC API 功能。

## <a name="crecordsetgetstatus"></a><a name="getstatus"></a>CRecordset：获取状态

确定记录集中当前记录的索引以及是否看到最后一条记录。

```cpp
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>参数

*rStatus*<br/>
对 `CRecordsetStatus` 对象的引用。 有关详细信息，请参阅“备注”部分。

### <a name="remarks"></a>备注

`CRecordset`尝试跟踪索引，但在某些情况下，这可能是不可能的。 有关说明，请参阅[GetRecordCount。](#getrecordcount)

结构`CRecordsetStatus`具有以下形式：

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

的`CRecordsetStatus`两个成员具有以下含义：

- `m_lCurrentRecord`包含记录集中当前记录的零基索引（如果已知）。 如果无法确定索引，则此成员包含AFX_CURRENT_RECORD_UNDEFINED （-2）。 如果`IsBOF`为 TRUE（空记录集或尝试在第一个记录之前滚动`m_lCurrentRecord`），则设置为AFX_CURRENT_RECORD_BOF （-1）。 如果在第一个记录上，则将其设置为 0，第二条记录 1，等等。

- `m_bRecordCountFinal`如果已确定记录集中的记录总数，则非零。 通常，这必须通过从记录集的开头开始和调用`MoveNext`直到`IsEOF`返回非零来实现。 如果此成员为零，则返回`GetRecordCount`的记录计数（如果不是 -1）只是记录的"高水位线"计数。

## <a name="crecordsetgetsql"></a><a name="getsql"></a>C记录集：：获取SQL

调用此成员函数获取用于在打开记录集时用于选择记录集记录的 SQL 语句。

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>返回值

对**const**包含 SQL`CString`语句的 的 引用。

### <a name="remarks"></a>备注

这通常是 SQL **SELECT**语句。 返回的`GetSQL`字符串是只读的。

返回`GetSQL`的字符串通常不同于您可能传递给*lpszSQL*参数中的记录集到`Open`成员函数的任何字符串。 这是因为记录集基于您传递给`Open`的内容、使用 ClassWizard 指定的内容、在`m_strFilter`和`m_strSort`数据成员中指定的内容以及您可能指定的任何参数构造了完整的 SQL 语句。 有关记录集如何构造此 SQL 语句的详细信息，请参阅[记录集：记录集如何选择记录 （ODBC）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。

> [!NOTE]
> 仅在调用[Open](#open)后调用此成员函数。

## <a name="crecordsetgettablename"></a><a name="gettablename"></a>C记录集：获取表名

获取记录集查询所基于的 SQL 表的名称。

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>返回值

如果**const**记录集基于表，`CString`则对 包含表名称的 引用;否则，一个空字符串。

### <a name="remarks"></a>备注

`GetTableName`仅当记录集基于表，而不是多个表的联接或预定义的查询（存储过程）时才有效。 该名称是只读的。

> [!NOTE]
> 仅在调用[Open](#open)后调用此成员函数。

## <a name="crecordsetisbof"></a><a name="isbof"></a>记录集：：IsBOF

如果记录集已定位在第一条记录之前，则返回非零。 没有最新记录。

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>返回值

如果记录集不包含任何记录，或者在第一个记录之前向后滚动，则非零;否则 0。

### <a name="remarks"></a>备注

在从记录滚动到记录之前，请调用此成员函数，以了解您是否在记录集的第一个记录之前。 您还可以使用 一`IsBOF`起`IsEOF`确定记录集是否包含任何记录或为空。 调用 后立即`Open`调用，如果记录集不包含任何记录，`IsBOF`则返回非零。当您打开至少具有一条记录的记录集时，第一个记录是当前记录，并`IsBOF`返回 0。

如果第一条记录是当前记录，而您调用`MovePrev``IsBOF`时，将随后返回非零。 如果`IsBOF`返回非零，并且调用`MovePrev`，则会发生错误。 如果`IsBOF`返回非零，则当前记录未定义，任何需要当前记录的操作都将导致错误。

### <a name="example"></a>示例

本示例使用`IsBOF``IsEOF`并检测记录集的限制，因为代码在两个方向上滚动通过记录集。

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

## <a name="crecordsetisdeleted"></a><a name="isdeleted"></a>CRecordset：已删除

确定当前记录是否已删除。

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>返回值

如果记录集位于已删除的记录上，则非零;否则 0。

### <a name="remarks"></a>备注

如果滚动到记录并`IsDeleted`返回 TRUE（非零），则必须滚动到其他记录，然后才能执行任何其他记录集操作。

的结果`IsDeleted`取决于许多因素，例如记录集类型、记录集是否可更新、打开记录集时是否指定`CRecordset::skipDeletedRecords`了选项、驱动程序是否打包已删除的记录以及是否有多个用户。

有关`CRecordset::skipDeletedRecords`和驱动程序打包的详细信息，请参阅[打开](#open)成员函数。

> [!NOTE]
> 如果已实现批量行提取，则不应调用`IsDeleted`。 而是调用[GetRow 状态](#getrowstatus)成员函数。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

## <a name="crecordsetiseof"></a><a name="iseof"></a>记录集：：IsEOF

如果记录集位于最后一条记录之后，则返回非零。 没有最新记录。

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>返回值

如果记录集不包含任何记录，或者您滚动超过最后一条记录，则为非零;否则 0。

### <a name="remarks"></a>备注

在从记录滚动到记录时调用此成员函数，以了解您是否超出了记录集的最后一条记录。 您还可以使用`IsEOF`来确定记录集是否包含任何记录或为空。 调用 后立即`Open`调用，如果记录集不包含任何记录，`IsEOF`则返回非零。 当您打开至少具有一条记录的记录集时，第一个记录是当前记录，并`IsEOF`返回 0。

如果最后一条记录是您调用`MoveNext`时的当前记录，`IsEOF`则随后将返回非零。 如果`IsEOF`返回非零，并且调用`MoveNext`，则会发生错误。 如果`IsEOF`返回非零，则当前记录未定义，任何需要当前记录的操作都将导致错误。

### <a name="example"></a>示例

请参阅[IsBOF](#isbof)的示例。

## <a name="crecordsetisfielddirty"></a><a name="isfielddirty"></a>C记录集：：IsFieldDirty

确定自调用[Edit](#edit)或[AddNew](#addnew)以来是否更改了指定的字段数据成员。

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>参数

*光伏*<br/>
指向要检查其状态的字段数据成员的指针，或 NULL 以确定任何字段是否脏。

### <a name="return-value"></a>返回值

如果指定的字段数据成员自调用`AddNew`或`Edit`后已更改，则非零。否则 0。

### <a name="remarks"></a>备注

当对[Update](#update)成员函数`CRecordset`的调用（在调用`Edit`或`AddNew`之后）更新当前记录时，所有脏字段数据成员中的数据都将传输到数据源上的记录。

> [!NOTE]
> 此成员函数不适用于使用批量行提取的记录集。 如果已实现批量行提取，则`IsFieldDirty`始终返回 FALSE 并将导致断言失败。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

调用`IsFieldDirty`将重置之前调用[SetFieldDirty](#setfielddirty)的影响，因为重新计算字段的脏状态。 `AddNew`在这种情况下，如果当前字段值与伪 null 值不同，则字段状态设置为脏。 `Edit`在这种情况下，如果字段值与缓存值不同，则字段状态设置为脏。

`IsFieldDirty`通过[多菲尔德交易所](#dofieldexchange)实施。

有关脏标志的详细信息，请参阅[记录集文章：记录集如何选择记录 （ODBC）。](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

## <a name="crecordsetisfieldnull"></a><a name="isfieldnull"></a>C记录集：：IsFieldNull

如果当前记录中的指定字段为 Null（没有值），则返回非零。

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>参数

*光伏*<br/>
指向要检查其状态的字段数据成员的指针，或 NULL 以确定是否有任何字段为 Null。

### <a name="return-value"></a>返回值

如果指定的字段数据成员标记为 Null，则非零;否则 0。

### <a name="remarks"></a>备注

调用此成员函数以确定记录集的指定字段数据成员是否已标记为 Null。 （在数据库术语中，Null 表示"没有值"，并且与 C++ 中的 NULL 不同。如果字段数据成员标记为 Null，则将其解释为当前记录的列，该列没有值。

> [!NOTE]
> 此成员函数不适用于使用批量行提取的记录集。 如果已实现批量行提取，则`IsFieldNull`始终返回 FALSE 并将导致断言失败。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

`IsFieldNull`通过[多菲尔德交易所](#dofieldexchange)实施。

## <a name="crecordsetisfieldnullable"></a><a name="isfieldnullable"></a>C 记录集：：可字段空

如果当前记录中的指定字段可以设置为 Null（没有值），则返回非零。

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>参数

*光伏*<br/>
指向要检查其状态的字段数据成员的指针，或 NULL 以确定是否可以将任何字段设置为 Null 值。

### <a name="remarks"></a>备注

调用此成员函数以确定指定的字段数据成员是否为"空"（可以设置为 Null 值;是否可以设置为 Null 值。"C++ NULL 与 Null 不同，在数据库术语中，Null 表示"没有值"）。

> [!NOTE]
> 如果已实现批量行提取，则无法调用`IsFieldNullable`。 相反，调用[GetODBCFieldInfo](#getodbcfieldinfo)成员函数以确定字段是否可以设置为 Null 值。 请注意，无论是否已实现批量`GetODBCFieldInfo`行提取，您始终都可以调用 。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

不能为空的字段必须具有值。 如果在添加或更新记录时尝试将此类字段设置为 Null，数据源将拒绝添加或更新，[更新](#update)将引发异常。 当您调用`Update`时，会出现异常，而不是调用[SetFieldNull](#setfieldnull)时。

对函数的第一个参数使用 NULL 将仅将函数应用于`outputColumn`字段，而不是`param`字段。 例如，呼叫

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

将仅`outputColumn`将字段设置为 NULL;`param`字段将不受影响。

要处理`param`字段，必须提供要处理的个人`param`的实际地址，例如：

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

这意味着您不能将所有`param`字段设置为 NULL，就像对字段一样`outputColumn`。

`IsFieldNullable`通过[多菲尔德交易所](#dofieldexchange)实施。

## <a name="crecordsetisopen"></a><a name="isopen"></a>CRecordset：：是打开的

确定记录集是否已打开。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果以前已调用记录集对象的[打开](#open)或[重新查询](#requery)成员函数，并且记录集尚未关闭，则非零;否则 0。

## <a name="crecordsetm_hstmt"></a><a name="m_hstmt"></a>CRecordset：：m_hstmt

包含与记录集关联的 HSTMT 类型的 ODBC 语句数据结构的句柄。

### <a name="remarks"></a>备注

对 ODBC 数据源的每个查询都与 HSTMT 相关联。

> [!CAUTION]
> 在调用`m_hstmt`[Open](#open)之前不要使用。

通常不需要直接访问 HSTMT，但可能需要它才能直接执行 SQL 语句。 类`ExecuteSQL``CDatabase`的成员函数提供了使用`m_hstmt`的示例。

## <a name="crecordsetm_nfields"></a><a name="m_nfields"></a>CRecordset：m_nFields

包含记录集类中的字段数据成员数;即记录集从数据源中选择的列数。

### <a name="remarks"></a>备注

记录集类的构造函数必须用正确的数字初始`m_nFields`化。 如果尚未实现批量行提取，ClassWizard 会当您使用它声明记录集类时为您编写此初始化。 您也可以手动编写。

框架使用此数字来管理字段数据成员与数据源上当前记录的相应列之间的交互。

> [!CAUTION]
> 此号码必须对应于在使用`DoFieldExchange`参数`DoBulkFieldExchange``CFieldExchange::outputColumn`调用[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)时或之后注册的"输出列"数。

您可以动态绑定列，如文章"记录集：动态绑定数据列"中所述。 如果这样做，则必须增加 中的`m_nFields`计数，以反映动态绑定列`DoFieldExchange`或`DoBulkFieldExchange`成员函数中的 RFX 或批量 RFX 函数调用数。

有关详细信息，请参阅[文章"记录集：动态绑定数据列 （ODBC）"](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)和["记录集：批量提取记录"（ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

### <a name="example"></a>示例

请参阅记录[字段交换的文章：使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。

## <a name="crecordsetm_nparams"></a><a name="m_nparams"></a>CRecordset：m_nParams

包含记录集类中的参数数据成员数;即，使用记录集的查询传递的参数数。

### <a name="remarks"></a>备注

如果记录集类具有任何参数数据成员，则类的构造函数必须用正确的数字初始`m_nParams`化。 默认值为`m_nParams`0 的值。 如果添加参数数据成员（必须手动添加），还必须在类构造函数中手动添加初始化，以反映参数数（参数数量必须至少与字符串中的`m_strFilter``m_strSort`''占位符数相同）。

框架在参数化记录集的查询时使用此数字。

> [!CAUTION]
> 此编号必须对应于在调用[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)中`DoFieldExchange`或`DoBulkFieldExchange`之后注册的参数值 为`CFieldExchange::param`、`CFieldExchange::outputParam`或`CFieldExchange::inoutParam`的 "参数"`CFieldExchange::inputParam`的"参数"数。

### <a name="example"></a>示例

  请参阅[文章记录集：参数化记录集 （ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)和[记录字段交换：使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。

## <a name="crecordsetm_pdatabase"></a><a name="m_pdatabase"></a>CRecordset：m_pDatabase

包含指向记录集连接到数据源`CDatabase`的对象的指针。

### <a name="remarks"></a>备注

此变量以两种方式设置。 通常，在构造记录集对象时，将`CDatabase`指针传递给已连接的对象。 如果改为传递 NULL，`CRecordset`则为您`CDatabase`创建一个对象并连接它。 在这两种情况下，`CRecordset`都在此变量中存储指针。

通常，您不需要直接使用存储在 中的`m_pDatabase`指针。 但是，如果将自己的扩展写入`CRecordset`，则可能需要使用指针。 例如，如果抛出自己的`CDBException`指针，则可能需要指针。 或者，如果需要使用同一`CDatabase`对象执行某些操作，例如运行事务、设置超时或调用类`ExecuteSQL``CDatabase`的成员函数直接执行 SQL 语句，则可能需要它。

## <a name="crecordsetm_strfilter"></a><a name="m_strfilter"></a>CRecordset：：m_strFilter

构造记录集对象后，但在调用其成员`Open`函数之前，使用此数据成员存储包含 SQL **WHERE**子`CString`句的 。

### <a name="remarks"></a>备注

记录集使用此字符串来约束（或筛选）它在`Open`或`Requery`调用期间选择的记录。 这对于选择记录子集非常有用，例如"位于加利福尼亚州的所有销售人员"（"州 + CA"）。 **WHERE**子句的 ODBC SQL 语法是

`WHERE search-condition`

请注意，您没有在字符串中包含**WHERE**关键字。 框架提供它。

还可以通过将''占位符放入筛选器字符串、在每个占位符的类中声明参数数据成员以及在运行时将参数传递给记录集来参数化。 这允许您在运行时构造筛选器。 有关详细信息，请参阅[记录集：参数化记录集 （ODBC）。](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

有关 SQL **WHERE**子句的详细信息，请参阅文章[SQL](../../data/odbc/sql.md)。 有关选择和筛选记录的详细信息，请参阅[文章"记录集：筛选记录"（ODBC）。](../../data/odbc/recordset-filtering-records-odbc.md)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

## <a name="crecordsetm_strsort"></a><a name="m_strsort"></a>CRecordset：m_strSort

构造记录集对象后，但在调用其成员`Open`函数之前，使用此数据成员存储包含 SQL ORDER `CString` **BY**子句的 。

### <a name="remarks"></a>备注

记录集使用此字符串对它在`Open`或`Requery`调用期间选择的记录进行排序。 可以使用此功能对一个或多个列的记录集进行排序。 **ORDER BY**子句的 ODBC SQL 语法是

`ORDER BY sort-specification [, sort-specification]...`

排序规范是整数或列名称。 您还可以通过将"ASC"或"DESC"追加到排序字符串中的列列表来指定升序或降序（默认情况下顺序是上升的）。 所选记录首先按列出的第一列排序，然后按第二列排序，等等。 例如，您可以按姓氏先订购"客户"记录集，然后按名字排序。 可以列出的列数取决于数据源。 有关详细信息，请参阅 Windows SDK。

请注意，您没有在字符串中包括**ORDER BY**关键字。 框架提供它。

有关 SQL 子句的详细信息，请参阅文章[SQL](../../data/odbc/sql.md)。 有关对记录进行排序的详细信息，请参阅[文章"记录集：排序记录"（ODBC）。](../../data/odbc/recordset-sorting-records-odbc.md)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

## <a name="crecordsetmove"></a><a name="move"></a>C 记录集：：移动

向前或向后移动记录集中的当前记录指针。

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>参数

nRows**<br/>
要向前或向后移动的行数。 正值向前移动，接近记录集的末尾。 负值向后移动，向起点移动。

*wFetchType*<br/>
确定将提取的`Move`行集。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

如果为*nRows*传递值 0，`Move`请刷新当前记录;如果为 nRows 传递值为 0，则刷新当前记录。`Move`将结束任何当前`AddNew`或`Edit`模式，并在调用`AddNew`之前`Edit`还原当前记录的值。

> [!NOTE]
> 当您浏览记录集时，不能跳过已删除的记录。 有关详细信息[，请参阅 CRecordset：已删除](#isdeleted)。 使用`skipDeletedRecords`选项集打开`CRecordset`打开 的`Move`时，断言*nRows*参数是否为 0。 此行为可防止刷新由使用相同数据的其他客户端应用程序删除的行。 有关`skipDeletedRecords`的说明，请参阅[Open](#open)中的*dwOption*参数。

`Move`按行集重新定位记录集。 基于*nRows*和*wFetchType*的值`Move`，获取相应的行集，然后使该行中的第一个记录集当前记录。 如果尚未实现批量行提取，则行集大小始终为 1。 提取行集时，`Move`直接调用[CheckRowsetError](#checkrowseterror)成员函数来处理从提取中产生的任何错误。

根据您传递的值，`Move`等效于其他成员`CRecordset`函数。 特别是 *，wFetchType*的值可能指示一个成员函数更直观，并且通常是移动当前记录的首选方法。

下表列出了*wFetchType*的可能值`Move`，该行集将基于*wFetchType*和*nRows*提取，以及任何对应于*wFetchType*的等效成员函数。

|wFetchType|提取的行集|等效成员函数|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE（默认值）|从当前行集中的第一行开始*nRows*行的行集。||
|SQL_FETCH_NEXT|下一个行集;*nRows*将被忽略。|[MoveNext](#movenext)|
|SQL_FETCH_PRIOR|上一个行集;*nRows*将被忽略。|[移动Prev](#moveprev)|
|SQL_FETCH_FIRST|记录集中的第一个行集;*nRows*将被忽略。|[首先移动](#movefirst)|
|SQL_FETCH_LAST|记录集中的最后一个完整行集;*nRows*将被忽略。|[移动上次](#movelast)|
|SQL_FETCH_ABSOLUTE|如果*nRows* > 0，则从记录集的开头开始*nRows*行的行集将从记录集开始。 如果*nRows* < 0，则从记录集末尾启动*nRows*行的行集。 如果*nRows* = 0，则返回文件开头 （BOF） 条件。|[设置绝对位置](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|从书签值对应于*nRows*的行开始的行集。|[设置书签](#setbookmark)|

> [!NOTE]
> 对于仅转发记录集，`Move`仅对*wFetchType*的值为 SQL_FETCH_NEXT有效。

> [!CAUTION]
> 如果`Move`记录集没有记录，则调用将引发异常。 要确定记录集是否有任何记录，请致电[IsBOF](#isbof)和[IsEOF](#iseof)。

> [!NOTE]
> 如果滚动过记录集的开头或结尾`IsBOF`（或`IsEOF`返回非零），则调用函数`Move`可能会引发 。 `CDBException` 例如，如果`IsEOF`返回非零，则`IsBOF`不返回，则`MoveNext`将引发异常，但不会`MovePrev`。

> [!NOTE]
> 如果在更新或`Move`添加当前记录时调用，更新将丢失，而不会发出警告。

有关记录集导航的详细信息，请参阅[文章"记录集：滚动（ODBC）"](../../data/odbc/recordset-scrolling-odbc.md)和["记录集：书签和绝对位置 （ODBC）"。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。 有关相关信息，请参阅 Windows SDK 中的`SQLExtendedFetch`ODBC API 功能。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

## <a name="crecordsetmovefirst"></a><a name="movefirst"></a>C 记录集：：先移动

使第一行中的第一个记录成为当前记录。

```cpp
void MoveFirst();
```

### <a name="remarks"></a>备注

无论是否实现了批量行提取，这始终是记录集中的第一个记录。

打开记录集后，不必`MoveFirst`立即调用。 此时，第一条记录（如果有）自动是当前记录。

> [!NOTE]
> 此成员函数对于仅转发记录集无效。

> [!NOTE]
> 当您浏览记录集时，不能跳过已删除的记录。 有关详细信息，请参阅[IsDelete 成员](#isdeleted)函数。

> [!CAUTION]
> 如果记录集没有`Move`记录，则调用任何函数都会引发异常。 要确定记录集是否有任何记录，请调用`IsBOF`和`IsEOF`。

> [!NOTE]
> 如果在更新或添加当前记录`Move`时调用任何函数，则更新将丢失，而不会发出警告。

有关记录集导航的详细信息，请参阅[文章"记录集：滚动（ODBC）"](../../data/odbc/recordset-scrolling-odbc.md)和["记录集：书签和绝对位置 （ODBC）"。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

  请参阅[IsBOF](#isbof)的示例。

## <a name="crecordsetmovelast"></a><a name="movelast"></a>C 记录集：：移动上次

使最后一个完整行中的第一个记录成为当前记录。

```cpp
void MoveLast();
```

### <a name="remarks"></a>备注

如果尚未实现批量行提取，则记录集的行集大小为 1，因此`MoveLast`只需移动到记录集中的最后一个记录。

> [!NOTE]
> 此成员函数对于仅转发记录集无效。

> [!NOTE]
> 当您浏览记录集时，不能跳过已删除的记录。 有关详细信息，请参阅[IsDelete 成员](#isdeleted)函数。

> [!CAUTION]
> 如果记录集没有`Move`记录，则调用任何函数都会引发异常。 要确定记录集是否有任何记录，请调用`IsBOF`和`IsEOF`。

> [!NOTE]
> 如果在更新或添加当前记录`Move`时调用任何函数，则更新将丢失，而不会发出警告。

有关记录集导航的详细信息，请参阅[文章"记录集：滚动（ODBC）"](../../data/odbc/recordset-scrolling-odbc.md)和["记录集：书签和绝对位置 （ODBC）"。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

  请参阅[IsBOF](#isbof)的示例。

## <a name="crecordsetmovenext"></a><a name="movenext"></a>C记录集：：移动下一个

使下一行中的第一个记录成为当前记录。

```cpp
void MoveNext();
```

### <a name="remarks"></a>备注

如果尚未实现批量行提取，则记录集的行集大小为 1，因此`MoveNext`只需移动到下一条记录即可。

> [!NOTE]
> 当您浏览记录集时，不能跳过已删除的记录。 有关详细信息，请参阅[IsDelete 成员](#isdeleted)函数。

> [!CAUTION]
> 如果记录集没有`Move`记录，则调用任何函数都会引发异常。 要确定记录集是否有任何记录，请调用`IsBOF`和`IsEOF`。

> [!NOTE]
> 还建议您在致电之前打电话`IsEOF``MoveNext`。 例如，如果滚动超过记录集的末尾，则返回非零;如果`IsEOF`已滚动过去记录集的末尾，则返回非零。后续调用`MoveNext`将引发异常。

> [!NOTE]
> 如果在更新或添加当前记录`Move`时调用任何函数，则更新将丢失，而不会发出警告。

有关记录集导航的详细信息，请参阅[文章"记录集：滚动（ODBC）"](../../data/odbc/recordset-scrolling-odbc.md)和["记录集：书签和绝对位置 （ODBC）"。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

  请参阅[IsBOF](#isbof)的示例。

## <a name="crecordsetmoveprev"></a><a name="moveprev"></a>C记录集：：MovePrev

使上一行中的第一个记录成为当前记录。

```cpp
void MovePrev();
```

### <a name="remarks"></a>备注

如果尚未实现批量行提取，则记录集的行集大小为 1，因此`MovePrev`只需移动到以前的记录即可。

> [!NOTE]
> 此成员函数对于仅转发记录集无效。

> [!NOTE]
> 当您浏览记录集时，不能跳过已删除的记录。 有关详细信息，请参阅[IsDelete 成员](#isdeleted)函数。

> [!CAUTION]
> 如果记录集没有`Move`记录，则调用任何函数都会引发异常。 要确定记录集是否有任何记录，请调用`IsBOF`和`IsEOF`。

> [!NOTE]
> 还建议您在致电之前打电话`IsBOF``MovePrev`。 例如，如果您在记录集的开头之前滚动过，`IsBOF`则返回非零;如果已滚动到记录集的开头，则返回非零。后续调用`MovePrev`将引发异常。

> [!NOTE]
> 如果在更新或添加当前记录`Move`时调用任何函数，则更新将丢失，而不会发出警告。

有关记录集导航的详细信息，请参阅[文章"记录集：滚动（ODBC）"](../../data/odbc/recordset-scrolling-odbc.md)和["记录集：书签和绝对位置 （ODBC）"。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

  请参阅[IsBOF](#isbof)的示例。

## <a name="crecordsetonsetoptions"></a><a name="onsetoptions"></a>CRecordset：：打开选项

调用以为指定的 ODBC 语句设置选项（在选择时使用）。

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>参数

*hstmt*<br/>
待设置选项的 ODBC 语句的 HSTMT。

### <a name="remarks"></a>备注

调用`OnSetOptions`为指定的 ODBC 语句设置选项（在选择时使用）。 框架调用此成员函数以设置记录集的初始选项。 `OnSetOptions`确定数据源对可滚动游标和游标并发的支持，并相应地设置记录集的选项。 （用于`OnSetOptions`选择操作的`OnSetUpdateOptions`，用于更新操作。

覆盖`OnSetOptions`以设置特定于驱动程序或数据源的选项。 例如，如果数据源支持打开独占访问，则可以重写`OnSetOptions`以利用该功能。

有关游标的详细信息，请参阅文章[ODBC](../../data/odbc/odbc-basics.md)。

## <a name="crecordsetonsetupdateoptions"></a><a name="onsetupdateoptions"></a>CRecordset：：打开更新选项

调用以为指定的 ODBC 语句设置选项（在更新时使用）。

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>参数

*hstmt*<br/>
待设置选项的 ODBC 语句的 HSTMT。

### <a name="remarks"></a>备注

调用`OnSetUpdateOptions`为指定的 ODBC 语句设置选项（在更新时使用）。 框架在创建 HSTMT 以更新记录集中的记录后调用此成员函数。 （用于`OnSetOptions`选择操作的`OnSetUpdateOptions`，用于更新操作。`OnSetUpdateOptions`确定数据源对可滚动游标和游标并发的支持，并相应地设置记录集的选项。

在`OnSetUpdateOptions`使用该语句访问数据库之前，重写以设置 ODBC 语句的选项。

有关游标的详细信息，请参阅文章[ODBC](../../data/odbc/odbc-basics.md)。

## <a name="crecordsetopen"></a><a name="open"></a>CRecordset：：打开

通过检索表或执行记录集表示的查询来打开记录集。

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>参数

*n 开放类型*<br/>
接受默认值，AFX_DB_USE_DEFAULT_TYPE或使用 中的以下值之一`enum OpenType`：

- `CRecordset::dynaset`具有双向滚动的记录集。 记录的成员身份和顺序在打开记录集时确定，但其他用户对数据值所做的更改在提取操作后可见。 动态集也称为键集驱动的记录集。

- `CRecordset::snapshot`具有双向滚动的静态记录集。 打开记录集时确定记录的成员身份和顺序;提取记录时确定数据值。 在关闭记录集然后重新打开之前，其他用户所做的更改不可见。

- `CRecordset::dynamic`具有双向滚动的记录集。 其他用户对成员资格、排序和数据值所做的更改在提取操作后可见。 请注意，许多 ODBC 驱动程序不支持这种类型的记录集。

- `CRecordset::forwardOnly`只具有前进滚动的只读记录集。

   对于`CRecordset`，默认值为`CRecordset::snapshot`。 默认值机制允许 VisualC++向导与具有不同默认值的 ODBC`CRecordset`和 DAO`CDaoRecordset`进行交互。

有关这些记录集类型的详细信息，请参阅文章[记录集 （ODBC）](../../data/odbc/recordset-odbc.md)。 有关相关信息，请参阅 Windows SDK 中的"使用块和可滚动光标"一文。

> [!CAUTION]
> 如果不支持请求的类型，则框架将引发异常。

*lpszSQL*<br/>
包含以下之一的字符串指针：

- NULL 指针。

- 表的名称。

- SQL **SELECT**语句（可选使用 SQL **WHERE**或**ORDER BY**子句）。

- 指定预定义查询名称的**CALL**语句（存储过程）。 请注意，不要在大括号和**CALL**关键字之间插入空格。

有关此字符串的详细信息，请参阅"[备注"](#remarks)部分下的表和 ClassWizard 角色的讨论。

> [!NOTE]
> 结果集中的列顺序必须与[DoFieldExchange](#dofieldexchange)或[DoBulkFieldExchange](#dobulkfieldexchange)函数覆盖中的 RFX 或批量 RFX 函数调用的顺序匹配。

*dwOptions*<br/>
可以指定下面列出的值组合的位掩码。 其中一些是相互排斥的。 默认值为**none**。

- `CRecordset::none`未设置选项。 此参数值与所有其他值是互斥的。 默认情况下，可以使用["编辑](#edit)"或["删除](#delete)"更新记录集，并允许使用[AddNew](#addnew)追加新记录。 高数据度取决于数据源以及您指定的*nOpenType*选项。 批量添加的优化不可用。 不会实现批量行提取。 在记录集导航期间，不会跳过已删除的记录。 书签不可用。 实现了自动脏场检查。

- `CRecordset::appendOnly`不允许`Edit`或`Delete`记录集上。 仅`AddNew`允许。 此选项与`CRecordset::readOnly`是互斥的。

- `CRecordset::readOnly`将记录集设置为只读。 此选项与`CRecordset::appendOnly`是互斥的。

- `CRecordset::optimizeBulkAdd`使用准备好的 SQL 语句一次优化添加许多记录。 仅当您不使用 ODBC API 函数`SQLSetPos`更新记录集时，才适用。 第一个更新确定哪些字段标记为脏。 此选项与`CRecordset::useMultiRowFetch`是互斥的。

- `CRecordset::useMultiRowFetch`实现批量行提取，以允许在单个提取操作中检索多行。 这是一个高级功能，旨在提高性能;但是，类向导不支持批量记录字段交换。 此选项与`CRecordset::optimizeBulkAdd`是互斥的。 请注意，如果指定`CRecordset::useMultiRowFetch`，则该选项`CRecordset::noDirtyFieldCheck`将自动打开（双缓冲将不可用）;在仅转发记录集上，该选项`CRecordset::useExtendedFetch`将自动打开。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

- `CRecordset::skipDeletedRecords`在浏览记录集时跳过所有已删除的记录。 这将降低某些相对获取的性能。 此选项在仅转发记录集上无效。 如果调用["移动"，](#move)将断言*nRows*参数设置为`CRecordset::skipDeletedRecords`0，并且`Move`选项集将断言。 请注意，`CRecordset::skipDeletedRecords`它类似于*驱动程序打包*，这意味着从记录集中删除已删除的行。 但是，如果驱动程序打包记录，则它将仅跳过您删除的记录;如果驱动程序包含记录，则仅跳过您删除的记录。在记录集打开时，它将不会跳过其他用户删除的记录。 `CRecordset::skipDeletedRecords`将跳过其他用户删除的行。

- `CRecordset::useBookmarks`如果支持，可在记录集中使用书签。 书签可减缓数据检索速度，但提高了数据导航的性能。 在仅转发记录集上无效。 有关详细信息，请参阅[文章记录集：书签和绝对位置 （ODBC）。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- `CRecordset::noDirtyFieldCheck`关闭自动脏场检查（双缓冲）。 这将提高性能;但是，必须通过调用`SetFieldDirty`和`SetFieldNull`成员函数手动将字段标记为脏。请注意，类`CRecordset`中的双缓冲类似于类`CDaoRecordset`中的双缓冲。 但是，在`CRecordset`中，不能对单个字段启用双重缓冲;在 中，无法对单个字段启用双重缓冲。您可以为所有字段启用它，或者禁用它对所有字段。 请注意，如果指定选项 ，`CRecordset::useMultiRowFetch`则将自动`CRecordset::noDirtyFieldCheck`打开;如果指定选项，则将自动打开。但是，`SetFieldDirty``SetFieldNull`并且不能用于实现批量行提取的记录集。

- `CRecordset::executeDirect`不要使用准备好的 SQL 语句。 为提高性能，如果永远不会调用成员函数，`Requery`请指定此选项。

- `CRecordset::useExtendedFetch`实现`SQLExtendedFetch`而不是`SQLFetch`。 这是为在仅转发记录集上实现批量行提取而设计的。 如果在仅转发记录集中`CRecordset::useMultiRowFetch`指定该选项，则`CRecordset::useExtendedFetch`将自动打开。

- `CRecordset::userAllocMultiRowBuffers`用户将为数据分配存储缓冲区。 如果要分配自己的存储，`CRecordset::useMultiRowFetch`请使用此选项;否则，框架将自动分配必要的存储。 有关详细信息，请参阅[记录集：批量获取记录 （ODBC） 的文章](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 请注意，不`CRecordset::userAllocMultiRowBuffers`指定`CRecordset::useMultiRowFetch`指定将导致断言失败。

### <a name="return-value"></a>返回值

如果对象已成功打开`CRecordset`，则非零;否则 0 如果[CDatabase：：打开](../../mfc/reference/cdatabase-class.md#open)（如果调用）返回 0。

### <a name="remarks"></a>备注

必须调用此成员函数才能运行由记录集定义的查询。 在调用`Open`之前，必须构造记录集对象。

此记录集与数据源的连接取决于在调用`Open`之前如何构造记录集。 如果将[CDatabase](../../mfc/reference/cdatabase-class.md)对象传递给尚未连接到数据源的记录集构造函数，则此成员函数使用[GetDefaultConnect](#getdefaultconnect)尝试打开数据库对象。 如果将 NULL 传递给记录集构造函数，则构造函数会为您构造一`CDatabase`个对象，并尝试`Open`连接数据库对象。 有关在这些不同情况下关闭记录集和连接的详细信息，请参阅[关闭](#close)。

> [!NOTE]
> 始终共享通过`CRecordset`对象访问数据源。 与`CDaoRecordset`类不同，`CRecordset`不能使用对象打开具有独占访问权限的数据源。

调用`Open`查询（通常是 SQL **SELECT**语句）时，会根据下表中显示的条件选择记录。

|lpszSQL 参数的值|所选记录由|示例|
|------------------------------------|----------------------------------------|-------------|
|Null|返回`GetDefaultSQL`的字符串。||
|SQL 表名称|表列表的所有列。 `DoFieldExchange` `DoBulkFieldExchange`|`"Customer"`|
|预定义查询（存储过程）名称|要返回的查询的列。|`"{call OverDueAccts}"`|
|**从**表列表中**选择**列列表|指定表中的指定列。|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
> 请注意，不要在 SQL 字符串中插入额外的空白。 例如，如果在大括号和**CALL**关键字之间插入空格，MFC 会将 SQL 字符串误解为表名并将其合并到**SELECT**语句中，这将导致引发异常。 同样，如果预定义的查询使用输出参数，请不要在大括号和''符号之间插入空格。 最后，不得在**CALL**语句中大括号之前或**SELECT**语句中的**SELECT**关键字之前插入空格。

通常的程序是将 NULL 传递给`Open`。在这种情况下，`Open`调用[GetDefaultSQL](#getdefaultsql)。 如果使用派生`CRecordset`类，则`GetDefaultSQL`提供在 ClassWizard 中指定的表名称。 您可以改为在`lpszSQL`参数中指定其他信息。

无论您通过什么，`Open`都会构造查询的最终 SQL 字符串（该字符串可能将 SQL **WHERE**和**ORDER BY**子`lpszSQL`句追加到您传递的字符串中），然后执行查询。 您可以通过调用[GetSQL](#getsql)在调用`Open`后检查构造的字符串。 有关记录集如何构造 SQL 语句和选择记录的其他详细信息，请参阅[记录集：记录集如何选择记录 （ODBC）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。

记录集类的字段数据成员绑定到所选数据的列。 如果返回任何记录，则第一条记录将成为当前记录。

如果要为记录集设置选项（如筛选器或排序），请在构造记录集对象后但在调用`Open`之前指定这些选项。 如果要在记录集打开后刷新记录集中的记录，请调用[重新查询](#requery)。

有关详细信息（包括其他示例），请参阅[文章记录集 （ODBC）](../../data/odbc/recordset-odbc.md)、[记录集：记录集如何选择记录 （ODBC）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)和[记录集：创建和关闭记录集 （ODBC）。](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

### <a name="example"></a>示例

以下代码示例显示了不同形式的`Open`调用。

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

## <a name="crecordsetrefreshrowset"></a><a name="refreshrowset"></a>C记录集：：刷新罗塞特

更新当前行集中行的数据和状态。

```cpp
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>参数

*wRow*<br/>
当前行集中行的基于一个位置。 此值的范围可以从零到行集的大小。

*wLock类型*<br/>
指示如何在刷新行后锁定行的值。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

如果为*wRow*传递值为零，则行集中的每一行都将刷新。

要使用`RefreshRowset`，必须通过在`CRecordset::useMulitRowFetch`[Open](#open)成员函数中指定选项来实现批量行提取。

`RefreshRowset`调用 ODBC API`SQLSetPos`函数 。 *wLockType*参数指定执行后`SQLSetPos`行的锁定状态。 下表描述了*wLockType*的可能值。

|wLock类型|说明|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE（默认值）|驱动程序或数据源可确保该行处于与调用之前`RefreshRowset`相同的锁定或解锁状态。|
|SQL_LOCK_EXCLUSIVE|驱动程序或数据源专门锁定行。 并非所有数据源都支持这种类型的锁。|
|SQL_LOCK_UNLOCK|驱动程序或数据源解锁该行。 并非所有数据源都支持这种类型的锁。|

有关 的详细信息`SQLSetPos`，请参阅 Windows SDK。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

## <a name="crecordsetrequery"></a><a name="requery"></a>C记录集：：重新查询

重建（刷新）记录集。

```
virtual BOOL Requery();
```

### <a name="return-value"></a>返回值

如果成功重建记录集，则非零;否则 0。

### <a name="remarks"></a>备注

如果返回任何记录，则第一条记录将成为当前记录。

为了使记录集反映您或其他用户对数据源进行的添加和删除，必须通过调用`Requery`来重新生成记录集。 如果记录集是动态集，它会自动反映您或其他用户对其现有记录（但不是添加）进行的更新。 如果记录集是快照，则必须调用`Requery`以反映其他用户的编辑以及添加和删除。

对于动态集或快照，在您希望使用新筛选器`Requery`或排序或新参数值重建记录集的任何时间调用。 通过将新值分配给`m_strFilter`和`m_strSort`之前调用`Requery`，设置新的筛选器或排序属性。 通过在调用`Requery`之前将新值分配给参数数据成员来设置新参数。 如果筛选器和排序字符串保持不变，则可以重用查询，从而提高性能。

如果重建记录集的尝试失败，记录集将关闭。 在调用`Requery`之前，可以通过调用`CanRestart`成员函数确定是否可以重新查询记录集。 `CanRestart`不能保证会`Requery`成功。

> [!CAUTION]
> 仅在`Requery`调用[Open](#open)后才能呼叫 。

### <a name="example"></a>示例

此示例重建记录集以应用其他排序顺序。

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

## <a name="crecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>C记录集：：设置绝对位置

将记录集放在与指定记录编号对应的记录上。

```cpp
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>参数

nRows**<br/>
记录集中当前记录的一个基于的盘位位置。

### <a name="remarks"></a>备注

`SetAbsolutePosition`基于此位形位置移动当前记录指针。

> [!NOTE]
> 此成员函数在仅转发记录集上无效。

对于 ODBC 记录集，绝对位置设置为 1 是指记录集中的第一个记录;设置为 0 是指文件开始 （BOF） 位置。

还可以将负值传递给`SetAbsolutePosition`。 在这种情况下，记录集的位置从记录集的末尾计算。 例如，`SetAbsolutePosition( -1 )`将当前记录指针移动到记录集中的最后一个记录。

> [!NOTE]
> 绝对位置不用作代理记录编号。 书签仍然是保留和返回到给定位置的推荐方式，因为删除之前的记录时记录的位置会发生变化。 此外，如果再次重新创建记录集，则无法保证给定记录集具有相同的绝对位置，因为除非使用**ORDER BY**子句使用 SQL 语句创建记录集中的单个记录的顺序不保证。

有关记录集导航和书签的详细信息，请参阅[文章"记录集：滚动 （ODBC）"](../../data/odbc/recordset-scrolling-odbc.md)和["记录集：书签和绝对位置 （ODBC）"。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

## <a name="crecordsetsetbookmark"></a><a name="setbookmark"></a>CRecordset：：设置书签

在包含指定书签的记录上定位记录集。

```cpp
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>参数

*瓦尔布克马克*<br/>
对包含特定记录的书签值的[CDBVariant](../../mfc/reference/cdbvariant-class.md)对象的引用。

### <a name="remarks"></a>备注

要确定记录集是否支持书签，请调用[CanBookmark](#canbookmark)。 要使书签在受支持时可用，必须在[Open](#open)成员函数`CRecordset::useBookmarks`的*dwOptions*参数中设置该选项。

> [!NOTE]
> 如果书签不受支持或不可用，则调用`SetBookmark`将导致引发异常。 仅转发记录集不支持书签。

若要首先检索当前记录的书签，请调用[GetBookmark，](#getbookmark)这将书签值保存到`CDBVariant`对象。 稍后，您可以使用保存的书签值调用`SetBookmark`该记录。

> [!NOTE]
> 在某些记录集操作后，应在调用`SetBookmark`之前检查书签持久性。 例如，如果检索书签，`GetBookmark`然后调用`Requery`，书签可能不再有效。 调用[CDatabase：获取书签持久性](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)，以检查是否可以安全地调用`SetBookmark`。

有关书签和记录集导航的详细信息，请参阅[文章"记录集：书签和绝对位置 （ODBC）"](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和["记录集：滚动 （ODBC）"。](../../data/odbc/recordset-scrolling-odbc.md)

## <a name="crecordsetsetfielddirty"></a><a name="setfielddirty"></a>C记录集：：设置字段脏

将记录集的字段数据成员标记为已更改或未更改。

```cpp
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>参数

*光伏*<br/>
在记录集或 NULL 中包含字段数据成员的地址。 如果为 NULL，则记录集中的所有字段数据成员将被标记。 （C++ NULL 与数据库术语中的 Null 不同，这意味着"没有值"。

*bDirty*<br/>
如果字段数据成员被标记为"脏"（已更改），则为 TRUE。 否则，如果字段数据成员被标记为"干净"（未更改），则 FALSE。

### <a name="remarks"></a>备注

将字段标记为未更改可确保字段不会更新，并减少 SQL 流量。

> [!NOTE]
> 此成员函数不适用于使用批量行提取的记录集。 如果已实现批量行提取，则`SetFieldDirty`将导致断言失败。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

框架标记已更改的字段数据成员，以确保它们将由记录字段交换 （RFX） 机制写入数据源上的记录。 更改字段的值通常会自动将字段设置脏，因此您很少需要调用`SetFieldDirty`自己，但有时您可能希望确保无论字段数据成员中的哪个值如何，都会显式更新或插入列。

> [!CAUTION]
> 仅在调用["编辑"](#edit)或["添加 New"](#addnew)后才能调用此成员函数。

对函数的第一个参数使用 NULL 将仅将函数应用于`outputColumn`字段，而不是`param`字段。 例如，呼叫

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

将仅`outputColumn`将字段设置为 NULL;`param`字段将不受影响。

要处理`param`字段，必须提供要处理的个人`param`的实际地址，例如：

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

这意味着您不能将所有`param`字段设置为 NULL，就像对字段一样`outputColumn`。

## <a name="crecordsetsetfieldnull"></a><a name="setfieldnull"></a>C记录集：：设置字段无效

将记录集的字段数据成员标记为 Null（具体没有值）或非 Null。

```cpp
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>参数

*光伏*<br/>
在记录集或 NULL 中包含字段数据成员的地址。 如果为 NULL，则记录集中的所有字段数据成员将被标记。 （C++ NULL 与数据库术语中的 Null 不同，这意味着"没有值"。

*bNull*<br/>
如果要将字段数据成员标记为无值（空），则非零。 否则 0 如果字段数据成员被标记为非 Null。

### <a name="remarks"></a>备注

将新记录添加到记录集时，所有字段数据成员最初都设置为 Null 值，并标记为"脏"（已更改）。 从数据源检索记录时，其列要么已有值，要么为 Null。

> [!NOTE]
> 不要在使用批量行提取的记录集中调用此成员函数。 如果已实现批量行提取，则调用`SetFieldNull`会导致断言失败。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

如果特别希望将当前记录的字段指定为没有值，则使用*bNull*设置为`SetFieldNull`TRUE 的调用将其标记为 Null。 如果字段以前标记为 Null，现在您希望为其提供值，只需设置其新值即可。 不必删除带有`SetFieldNull`的 Null 标志。 要确定是否允许该字段为 Null，请调用`IsFieldNullable`。

> [!CAUTION]
> 仅在调用["编辑"](#edit)或["添加 New"](#addnew)后才能调用此成员函数。

对函数的第一个参数使用 NULL 将仅将函数应用于`outputColumn`字段，而不是`param`字段。 例如，呼叫

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

将仅`outputColumn`将字段设置为 NULL;`param`字段将不受影响。

要处理`param`字段，必须提供要处理的个人`param`的实际地址，例如：

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

这意味着您不能将所有`param`字段设置为 NULL，就像对字段一样`outputColumn`。

> [!NOTE]
> 将参数设置为 Null 时，在打开`SetFieldNull`记录集之前调用 会导致断言。 在这种情况下，调用[SetParamNull](#setparamnull)。

`SetFieldNull`通过[多菲尔德交易所](#dofieldexchange)实施。

## <a name="crecordsetsetlockingmode"></a><a name="setlockingmode"></a>C记录集：：设置锁定模式

将锁定模式设置为"乐观"锁定（默认）或"悲观"锁定。 确定如何锁定记录以进行更新。

```cpp
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>参数

*nMode*<br/>
包含 以下值之一： `enum LockMode`

- `optimistic`乐观锁定仅在调用`Update`期间更新的记录锁定 。

- `pessimistic`悲观锁定在调用后立即`Edit`锁定记录，并将其锁定，`Update`直到呼叫完成或移动到新记录。

### <a name="remarks"></a>备注

如果需要指定记录集用于更新的两个记录锁定策略中的哪一个，请调用此成员函数。 默认情况下，记录集的锁定模式为`optimistic`。 您可以将其更改为更谨慎的`pessimistic`锁定策略。 在`SetLockingMode`构造并打开记录集对象后，但在调用 之前调用`Edit`调用 。

## <a name="crecordsetsetparamnull"></a><a name="setparamnull"></a>C 记录集：：SetParamNull

将参数标记为 Null（具体没有值）或非 Null。

```cpp
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
参数的从零开始的索引。

*bNull*<br/>
如果 TRUE（默认值），则参数将标记为 Null。 否则，参数将标记为非 Null。

### <a name="remarks"></a>备注

与[SetFieldNull](#setfieldnull)不同，`SetParamNull`您可以在打开记录集之前调用。

`SetParamNull`通常用于预定义的查询（存储过程）。

## <a name="crecordsetsetrowsetcursorposition"></a><a name="setrowsetcursorposition"></a>C 记录集：：设置罗塞特游标位置

将光标移动到当前行集中的行。

```cpp
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>参数

*wRow*<br/>
当前行集中行的基于一个位置。 此值的范围可以从 1 到行集的大小。

*wLock类型*<br/>
指示如何在刷新行后锁定行的值。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

实现批量行提取时，记录由行集检索，其中提取的行集中的第一条记录是当前记录。 为了在行集中对当前记录进行另一个记录，请调用`SetRowsetCursorPosition`。 例如，您可以与`SetRowsetCursorPosition`[GetFieldValue](#getfieldvalue)成员函数结合使用，从记录集的任何记录中动态检索数据。

要使用`SetRowsetCursorPosition`，必须通过在[Open](#open)成员函数中指定`CRecordset::useMultiRowFetch`*dwOptions*参数的选项来实现批量行提取。

`SetRowsetCursorPosition`调用 ODBC API`SQLSetPos`函数 。 *wLockType*参数指定执行后`SQLSetPos`行的锁定状态。 下表描述了*wLockType*的可能值。

|wLock类型|说明|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE（默认值）|驱动程序或数据源可确保该行处于与调用之前`SetRowsetCursorPosition`相同的锁定或解锁状态。|
|SQL_LOCK_EXCLUSIVE|驱动程序或数据源专门锁定行。 并非所有数据源都支持这种类型的锁。|
|SQL_LOCK_UNLOCK|驱动程序或数据源解锁该行。 并非所有数据源都支持这种类型的锁。|

有关 的详细信息`SQLSetPos`，请参阅 Windows SDK。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

## <a name="crecordsetsetrowsetsize"></a><a name="setrowsetsize"></a>C 记录集：：设置罗塞特大小

指定您希望在提取期间检索的记录数。

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>参数

*dwNewRowsetSize*<br/>
给定提取期间要检索的行数。

### <a name="remarks"></a>备注

此虚拟成员函数指定在使用批量行提取时希望在单个提取期间检索多少行。 要实现批量行提取，必须在[Open](#open)成员`CRecordset::useMultiRowFetch`函数的*dwOptions*参数中设置该选项。

> [!NOTE]
> 不`SetRowsetSize`实现批量行提取的调用将导致断言失败。

调用`SetRowsetSize``Open`之前调用以最初设置记录集的行集大小。 实现批量行提取时的默认行集大小为 25。

> [!NOTE]
> 调用`SetRowsetSize`时要小心。 如果要手动分配数据的存储（如 中的`CRecordset::userAllocMultiRowBuffers``Open`dwOptions 参数的选项指定），则应检查是否需要在调用`SetRowsetSize`后，但在执行任何游标导航操作之前重新分配这些存储缓冲区。

要获取行集大小的当前设置，请调用[GetRowsetSize](#getrowsetsize)。

有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

## <a name="crecordsetupdate"></a><a name="update"></a>CRecordset：：更新

通过在数据源上`AddNew`保存`Edit`新的或编辑的数据来完成 或 操作。

```
virtual BOOL Update();
```

### <a name="return-value"></a>返回值

如果成功更新一条记录，则非零;否则 0 如果没有列更改。 如果未更新任何记录，或者更新了多个记录，则引发异常。 对于数据源上的任何其他故障，也会引发异常。

### <a name="remarks"></a>备注

调用["新建](#addnew)"或["编辑](#edit)"成员函数后调用此成员函数。 完成`AddNew`或`Edit`操作需要此调用。

> [!NOTE]
> 如果已实现批量行提取，则无法调用`Update`。 这将导致断言失败。 尽管类`CRecordset`不提供更新批量数据行的机制，但您可以使用 ODBC API 函数编写自己的函数`SQLSetPos`。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

`AddNew`并`Edit`准备一个编辑缓冲区，其中添加或编辑的数据被放置到数据源中。 `Update`保存数据。 只会更新标记为或检测到已更改的字段。

如果数据源支持事务，则可以将`Update`调用（及其相应的`AddNew`或`Edit`调用）作为事务的一部分。 有关交易记录的详细信息，请参阅文章[事务 （ODBC）](../../data/odbc/transaction-odbc.md)。

> [!CAUTION]
> 如果在未首先`Update`调用 或`AddNew``Edit`的情况下调用`Update`，`CDBException`则引发 。 如果调用`AddNew`或`Edit`，必须在调用`Update``Move`操作之前或关闭记录集或数据源连接之前调用。 否则，您的更改将丢失，恕不另行通知。

有关处理`Update`失败的详细信息，请参阅[记录集：记录集如何更新记录 （ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

### <a name="example"></a>示例

请参阅文章["事务：在记录集 （ODBC） 中执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)"。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDatabase 类](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView 类](../../mfc/reference/crecordview-class.md)
