---
title: CDatabase 类
ms.date: 11/04/2016
f1_keywords:
- CDatabase
- AFXDB/CDatabase
- AFXDB/CDatabase::CDatabase
- AFXDB/CDatabase::BeginTrans
- AFXDB/CDatabase::BindParameters
- AFXDB/CDatabase::Cancel
- AFXDB/CDatabase::CanTransact
- AFXDB/CDatabase::CanUpdate
- AFXDB/CDatabase::Close
- AFXDB/CDatabase::CommitTrans
- AFXDB/CDatabase::ExecuteSQL
- AFXDB/CDatabase::GetBookmarkPersistence
- AFXDB/CDatabase::GetConnect
- AFXDB/CDatabase::GetCursorCommitBehavior
- AFXDB/CDatabase::GetCursorRollbackBehavior
- AFXDB/CDatabase::GetDatabaseName
- AFXDB/CDatabase::IsOpen
- AFXDB/CDatabase::OnSetOptions
- AFXDB/CDatabase::Open
- AFXDB/CDatabase::OpenEx
- AFXDB/CDatabase::Rollback
- AFXDB/CDatabase::SetLoginTimeout
- AFXDB/CDatabase::SetQueryTimeout
- AFXDB/CDatabase::m_hdbc
helpviewer_keywords:
- CDatabase [MFC], CDatabase
- CDatabase [MFC], BeginTrans
- CDatabase [MFC], BindParameters
- CDatabase [MFC], Cancel
- CDatabase [MFC], CanTransact
- CDatabase [MFC], CanUpdate
- CDatabase [MFC], Close
- CDatabase [MFC], CommitTrans
- CDatabase [MFC], ExecuteSQL
- CDatabase [MFC], GetBookmarkPersistence
- CDatabase [MFC], GetConnect
- CDatabase [MFC], GetCursorCommitBehavior
- CDatabase [MFC], GetCursorRollbackBehavior
- CDatabase [MFC], GetDatabaseName
- CDatabase [MFC], IsOpen
- CDatabase [MFC], OnSetOptions
- CDatabase [MFC], Open
- CDatabase [MFC], OpenEx
- CDatabase [MFC], Rollback
- CDatabase [MFC], SetLoginTimeout
- CDatabase [MFC], SetQueryTimeout
- CDatabase [MFC], m_hdbc
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
ms.openlocfilehash: ee1503f49f0e60b24e0ef3a9c9631f039ad9355e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223104"
---
# <a name="cdatabase-class"></a>CDatabase 类

表示与数据源的连接，通过此连接可操作数据源。

## <a name="syntax"></a>语法

```
class CDatabase : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDatabase：： CDatabase](#cdatabase)|构造 `CDatabase` 对象。 必须通过调用或初始化对象 `OpenEx` `Open` 。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CDatabase：： BeginTrans](#begintrans)|`AddNew` `Edit` `Delete` `Update` `CRecordset` 对连接的数据源启动一系列对类的、、和成员函数的可逆调用。 数据源必须支持的事务 `BeginTrans` 才能产生任何影响。|
|[CDatabase：： BindParameters](#bindparameters)|允许在调用之前绑定参数 `CDatabase::ExecuteSQL` 。|
|[CDatabase：： Cancel](#cancel)|取消异步操作或来自另一个线程的进程。|
|[CDatabase：： CanTransact](#cantransact)|如果数据源支持事务，则返回非零值。|
|[CDatabase：： CanUpdate](#canupdate)|如果 `CDatabase` 对象可更新（非只读），则返回非零值。|
|[CDatabase：： Close](#close)|关闭数据源连接。|
|[CDatabase：： CommitTrans](#committrans)|完成由开始的事务 `BeginTrans` 。 将执行更改数据源的事务中的命令。|
|[CDatabase：： ExecuteSQL](#executesql)|执行 SQL 语句。 不返回任何数据记录。|
|[CDatabase：： GetBookmarkPersistence](#getbookmarkpersistence)|标识用于在记录集对象上保留书签的操作。|
|[CDatabase::GetConnect](#getconnect)|返回用于将 `CDatabase` 对象连接到数据源的 ODBC 连接字符串。|
|[CDatabase：： GetCursorCommitBehavior](#getcursorcommitbehavior)|标识在打开的记录集对象上提交事务的效果。|
|[CDatabase：： GetCursorRollbackBehavior](#getcursorrollbackbehavior)|标识对打开的记录集对象回滚事务的影响。|
|[CDatabase：： GetDatabaseName](#getdatabasename)|返回当前正在使用的数据库的名称。|
|[CDatabase：： IsOpen](#isopen)|如果 `CDatabase` 对象当前已连接到数据源，则返回非零值。|
|[CDatabase：： OnSetOptions](#onsetoptions)|由框架调用以设置标准连接选项。 默认实现设置查询超时值。 可以通过调用来提前建立这些选项 `SetQueryTimeout` 。|
|[CDatabase：： Open](#open)|建立与数据源的连接（通过 ODBC 驱动程序）。|
|[CDatabase：： Microsoft.office.interop.visio.documents.open](#openex)|建立与数据源的连接（通过 ODBC 驱动程序）。|
|[CDatabase：： Rollback](#rollback)|撤消在当前事务中所做的更改。 数据源恢复为其以前的状态，如在调用时定义的，该状态 `BeginTrans` 未经更改。|
|[CDatabase：： SetLoginTimeout](#setlogintimeout)|设置秒数，在这段时间之后数据源连接尝试将超时。|
|[CDatabase：： SetQueryTimeout](#setquerytimeout)|设置在多少秒后数据库查询操作将超时。影响所有后续的记录集 `Open` 、 `AddNew` 、 `Edit` 和 `Delete` 调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CDatabase：： m_hdbc](#m_hdbc)|数据源的开放式数据库连接（ODBC）连接句柄。 键入*HDBC*。|

## <a name="remarks"></a>备注

数据源是由某些数据库管理系统（DBMS）承载的特定数据实例。 示例包括 Microsoft SQL Server、Microsoft Access、Borland dBASE 和 xBASE。 在应用程序中，一次可以有一个或多个 `CDatabase` 对象处于活动状态。

> [!NOTE]
> 如果使用的是数据访问对象（DAO）类而不是开放式数据库连接（ODBC）类，请改用类[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 。 有关详细信息，请参阅文章[概述：数据库编程](../../data/data-access-programming-mfc-atl.md)。

若要使用 `CDatabase` ，请构造一个 `CDatabase` 对象并调用其 `OpenEx` 成员函数。 这将打开一个连接。 然后 `CRecordset` ，在连接的数据源上构造用于操作的对象时，请向记录集构造函数传递一个指向对象的指针 `CDatabase` 。 使用完连接后，调用 `Close` 成员函数并销毁 `CDatabase` 对象。 `Close`关闭之前未关闭的任何记录集。

有关的详细信息 `CDatabase` ，请参阅文章[数据源（ODBC）](../../data/odbc/data-source-odbc.md)和[概述：数据库编程](../../data/data-access-programming-mfc-atl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>要求

**标头：** afxdb

## <a name="cdatabasebegintrans"></a><a name="begintrans"></a>CDatabase：： BeginTrans

调用此成员函数以使用连接的数据源开始事务。

```
BOOL BeginTrans();
```

### <a name="return-value"></a>返回值

如果调用成功，则为非零; 仅手动提交更改。否则为0。

### <a name="remarks"></a>备注

事务由一个或多个对 `AddNew` 对象的、 `Edit` 、 `Delete` 和 `Update` 成员函数 `CRecordset` 的调用组成。 开始事务之前， `CDatabase` 对象必须已通过调用其 `OpenEx` 或成员函数连接到数据源 `Open` 。 若要结束事务，请调用[CommitTrans](#committrans)以接受对数据源所做的所有更改（并执行这些更改）或调用[Rollback](#rollback)来中止整个事务。 `BeginTrans`打开事务中涉及的任何记录集并尽可能接近实际的更新操作后调用。

> [!CAUTION]
> 根据 ODBC 驱动程序的不同，在调用前打开记录集 `BeginTrans` 可能会在调用时导致问题 `Rollback` 。 你应检查正在使用的特定驱动程序。 例如，使用 Microsoft ODBC 桌面驱动程序包3.0 中包含的 Microsoft Access 驱动程序时，必须考虑 Jet 数据库引擎的要求，即不应在具有打开的游标的任何数据库上开始事务。 在 MFC 数据库类中，打开的游标表示打开的 `CRecordset` 对象。 有关详细信息，请参阅[技术说明 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md)。

`BeginTrans`还可能会锁定服务器上的数据记录，具体取决于所请求的并发和数据源的功能。 有关锁定数据的信息，请参阅[记录记录：锁定记录（ODBC）](../../data/odbc/recordset-locking-records-odbc.md)一文。

[事务（ODBC）](../../data/odbc/transaction-odbc.md)一文中介绍了用户定义的事务。

`BeginTrans`确定事务序列可以回滚到的状态。 若要为回滚建立新状态，请提交所有当前事务，然后 `BeginTrans` 再次调用。

> [!CAUTION]
> `BeginTrans`再次调用而不调用 `CommitTrans` 或 `Rollback` 为错误。

调用[CanTransact](#cantransact)成员函数，以确定驱动程序是否支持给定数据库的事务。 还应调用[GetCursorCommitBehavior](#getcursorcommitbehavior)和[GetCursorRollbackBehavior](#getcursorrollbackbehavior)来确定是否支持游标保存。

有关事务的详细信息，请参阅[事务（ODBC）](../../data/odbc/transaction-odbc.md)一文。

### <a name="example"></a>示例

  请参阅[事务：在记录集中执行事务（ODBC）](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)一文。

## <a name="cdatabasebindparameters"></a><a name="bindparameters"></a>CDatabase：： BindParameters

`BindParameters`需要在调用[CDatabase：： ExecuteSQL](#executesql)之前绑定参数时重写。

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>参数

*hstmt*<br/>
要将参数绑定到的 ODBC 语句句柄。

### <a name="remarks"></a>备注

当不需要来自存储过程的结果集时，此方法非常有用。

在重写中，调用 `SQLBindParameters` 和相关的 ODBC 函数以便绑定参数。 MFC 在调用之前调用你的重写 `ExecuteSQL` 。 无需调用，只需 `SQLPrepare` 调用 `ExecuteSQL` `SQLExecDirect` 并销毁*hstmt*。

## <a name="cdatabasecancel"></a><a name="cancel"></a>CDatabase：： Cancel

调用此成员函数以请求数据源取消正在进行的异步操作或从另一个线程中的进程。

```cpp
void Cancel();
```

### <a name="remarks"></a>备注

请注意，MFC ODBC 类不再使用异步处理;若要执行异步操作，必须直接调用 ODBC API 函数[SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function)。 有关详细信息，请参阅[异步执行](/sql/odbc/reference/develop-app/asynchronous-execution)。

## <a name="cdatabasecantransact"></a><a name="cantransact"></a>CDatabase：： CanTransact

调用此成员函数以确定数据库是否允许事务。

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>返回值

如果使用此对象的记录集允许事务，则为非零 `CDatabase` ; 否则为0。

### <a name="remarks"></a>备注

有关事务的信息，请参阅[事务（ODBC）](../../data/odbc/transaction-odbc.md)一文。

## <a name="cdatabasecanupdate"></a><a name="canupdate"></a>CDatabase：： CanUpdate

调用此成员函数以确定对象是否 `CDatabase` 允许更新。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>返回值

如果 `CDatabase` 对象允许更新，则为非零; 否则为0，指示打开对象时在*bReadOnly*中传递了 TRUE， `CDatabase` 或数据源本身是只读的。 如果调用 SQL_DATASOURCE_READ_ONLY 的 ODBC API 函数 `SQLGetInfo` 返回 "y"，则数据源为只读。

### <a name="remarks"></a>备注

并非所有驱动程序都支持更新。

## <a name="cdatabasecdatabase"></a><a name="cdatabase"></a>CDatabase：： CDatabase

构造 `CDatabase` 对象。

```
CDatabase();
```

### <a name="remarks"></a>备注

构造对象之后，必须调用其 `OpenEx` 或 `Open` 成员函数以建立与指定数据源的连接。

你可能会发现， `CDatabase` 在文档类中嵌入对象会很方便。

### <a name="example"></a>示例

此示例演示如何 `CDatabase` 在 `CDocument` 派生类中使用。

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

## <a name="cdatabaseclose"></a><a name="close"></a>CDatabase：： Close

如果要断开与数据源的连接，请调用此成员函数。

```
virtual void Close();
```

### <a name="remarks"></a>备注

在 `CDatabase` 调用此成员函数之前，必须先关闭与对象关联的任何记录集。 由于不 `Close` 会销毁 `CDatabase` 对象，因此可以通过打开与同一数据源或其他数据源的新连接来重复使用该对象。

所有挂起 `AddNew` `Edit` 的记录集或使用数据库的记录集都将被取消，并且将回滚所有挂起的事务。 依赖于该对象的任何记录集 `CDatabase` 都处于未定义状态。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

## <a name="cdatabasecommittrans"></a><a name="committrans"></a>CDatabase：： CommitTrans

完成事务时调用此成员函数。

```
BOOL CommitTrans();
```

### <a name="return-value"></a>返回值

如果更新已成功提交，则为非零值;否则为0。 如果 `CommitTrans` 失败，则数据源的状态为 undefined。 您必须检查数据以确定其状态。

### <a name="remarks"></a>备注

事务由一系列对 `AddNew` 对象的、、和成员函数的调用，以对 `Edit` `Delete` `Update` `CRecordset` [BeginTrans](#begintrans)成员函数的调用开始。 `CommitTrans`提交事务。 默认情况下，将立即提交更新;调用 `BeginTrans` 会导致在调用之前将更新提交到延迟 `CommitTrans` 。

在您调用 `CommitTrans` 以结束事务之前，您可以调用[Rollback](#rollback)成员函数来中止该事务，并使数据源保持其原始状态。 若要开始新的事务，请 `BeginTrans` 再次调用。

有关事务的详细信息，请参阅[事务（ODBC）](../../data/odbc/transaction-odbc.md)一文。

### <a name="example"></a>示例

  请参阅[事务：在记录集中执行事务（ODBC）](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)一文。

## <a name="cdatabaseexecutesql"></a><a name="executesql"></a>CDatabase：： ExecuteSQL

当需要直接执行 SQL 命令时，调用此成员函数。

```cpp
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>参数

*lpszSQL*<br/>
指向以 null 结尾的字符串的指针，该字符串包含要执行的有效 SQL 命令。 可以传递[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>备注

创建以 null 结尾的字符串形式的命令。 `ExecuteSQL`不返回数据记录。 如果要对记录进行操作，请改用记录集对象。

数据源的大多数命令都是通过记录集对象发出的，记录集对象支持用于选择数据、插入新记录、删除记录和编辑记录的命令。 但是，数据库类不会直接支持所有 ODBC 功能，因此，有时你可能需要使用进行直接 SQL 调用 `ExecuteSQL` 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

## <a name="cdatabasegetbookmarkpersistence"></a><a name="getbookmarkpersistence"></a>CDatabase：： GetBookmarkPersistence

在某些操作之后，通过调用此成员函数确定记录集对象上的书签的持久性。

```
DWORD GetBookmarkPersistence() const;
```

### <a name="return-value"></a>返回值

用于标识操作的位掩码，书签通过它来保存在记录集对象上。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

例如，如果调用 `CRecordset::GetBookmark`，然后调用 `CRecordset::Requery`，则从 `GetBookmark` 获取的书签可能不再有效。 在调用 `GetBookmarkPersistence` 之前应当先调用 `CRecordset::SetBookmark`。

下表列出了位掩码值，这些值可组合成 `GetBookmarkPersistence` 的返回值。

|位掩码值|书签的持久性|
|-------------------|--------------------------|
|SQL_BP_CLOSE|书签在操作后有效 `Requery` 。|
|SQL_BP_DELETE|行的书签在对该行执行操作后有效 `Delete` 。|
|SQL_BP_DROP|书签在操作后有效 `Close` 。|
|SQL_BP_SCROLL|书签在任何操作之后都有效 `Move` 。 这只标识记录集上是否支持书签，正如 `CRecordset::CanBookmark` 返回的值一样。|
|SQL_BP_TRANSACTION|在提交或回滚事务后，书签将变为有效。|
|SQL_BP_UPDATE|行的书签在 `Update` 对该行执行操作后有效。|
|SQL_BP_OTHER_HSTMT|与某个记录集对象关联的书签在另一个记录集上有效。|

有关此返回值的详细信息，请参阅 Windows SDK 中的 ODBC API 函数 `SQLGetInfo` 。 有关书签的详细信息，请参阅[记录记录集：书签和绝对位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)一文。

## <a name="cdatabasegetconnect"></a><a name="getconnect"></a>CDatabase：： GetConnect

调用此成员函数以检索在调用期间使用的连接字符串 `OpenEx` ，或将 `Open` 对象连接 `CDatabase` 到数据源的连接字符串。

```
const CString GetConnect() const;
```

### <a name="return-value"></a>返回值

**`const`** 如果调用了或，则为包含连接字符串的[CString](../../atl-mfc-shared/reference/cstringt-class.md) `OpenEx` `Open` ; 否则为空字符串。

### <a name="remarks"></a>备注

有关如何创建连接字符串的说明，请参阅[CDatabase：： Open](#open) 。

## <a name="cdatabasegetcursorcommitbehavior"></a><a name="getcursorcommitbehavior"></a>CDatabase：： GetCursorCommitBehavior

调用此成员函数来确定[CommitTrans](#committrans)操作如何影响打开的记录集对象上的游标。

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>返回值

指示事务对打开的记录集对象的影响的值。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

下表列出了可能的返回值 `GetCursorCommitBehavior` 以及打开的记录集的相应效果。

|返回值|对 CRecordset 对象的影响|
|------------------|----------------------------------|
|SQL_CB_CLOSE|`CRecordset::Requery`在事务提交之后立即调用。|
|SQL_CB_DELETE|`CRecordset::Close`在事务提交之后立即调用。|
|SQL_CB_PRESERVE|正常执行 `CRecordset` 操作。|

有关此返回值的详细信息，请参阅 Windows SDK 中的 ODBC API 函数 `SQLGetInfo` 。 有关事务的详细信息，请参阅[事务（ODBC）](../../data/odbc/transaction-odbc.md)一文。

## <a name="cdatabasegetcursorrollbackbehavior"></a><a name="getcursorrollbackbehavior"></a>CDatabase：： GetCursorRollbackBehavior

调用此成员函数以确定[回滚](#rollback)操作如何影响打开的记录集对象上的游标。

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>返回值

指示事务对打开的记录集对象的影响的值。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

下表列出了可能的返回值 `GetCursorRollbackBehavior` 以及打开的记录集的相应效果。

|返回值|对 CRecordset 对象的影响|
|------------------|----------------------------------|
|SQL_CB_CLOSE|`CRecordset::Requery`在事务回滚之后立即调用。|
|SQL_CB_DELETE|`CRecordset::Close`在事务回滚之后立即调用。|
|SQL_CB_PRESERVE|正常执行 `CRecordset` 操作。|

有关此返回值的详细信息，请参阅 Windows SDK 中的 ODBC API 函数 `SQLGetInfo` 。 有关事务的详细信息，请参阅[事务（ODBC）](../../data/odbc/transaction-odbc.md)一文。

## <a name="cdatabasegetdatabasename"></a><a name="getdatabasename"></a>CDatabase：： GetDatabaseName

调用此成员函数以检索当前连接的数据库的名称（前提是数据源定义了名为 "database" 的命名对象）。

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>返回值

如果成功，则为包含数据库名称的[CString](../../atl-mfc-shared/reference/cstringt-class.md) ;否则为空 `CString` 。

### <a name="remarks"></a>备注

这与或调用中指定的数据源名称（DSN）不相同 `OpenEx` `Open` 。 `GetDatabaseName`返回的内容取决于 ODBC。 通常，数据库是表的集合。 如果此实体具有名称， `GetDatabaseName` 则返回该名称。

例如，您可能希望在标题中显示此名称。 如果从 ODBC 检索名称时出现错误，则 `GetDatabaseName` 返回空 `CString` 。

## <a name="cdatabaseisopen"></a><a name="isopen"></a>CDatabase：： IsOpen

调用此成员函数以确定 `CDatabase` 对象当前是否已连接到数据源。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果 `CDatabase` 对象当前已连接，则为非零; 否则为0。

## <a name="cdatabasem_hdbc"></a><a name="m_hdbc"></a>CDatabase：： m_hdbc

包含 ODBC 数据源连接的公共句柄，即 "连接句柄"。

### <a name="remarks"></a>备注

通常，无需直接访问此成员变量。 相反，当调用或时，框架会分配句柄 `OpenEx` `Open` 。 在对对象调用运算符时，框架会释放句柄 **`delete`** `CDatabase` 。 请注意， `Close` 成员函数不会释放句柄。

但是，在某些情况下，可能需要直接使用该句柄。 例如，如果需要直接调用 ODBC API 函数而不是通过类调用 `CDatabase` ，则可能需要一个连接句柄作为参数传递。 请参阅下面的代码示例。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

## <a name="cdatabaseonsetoptions"></a><a name="onsetoptions"></a>CDatabase：： OnSetOptions

当使用成员函数直接执行 SQL 语句时，框架会调用此成员函数 `ExecuteSQL` 。

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>参数

*hstmt*<br/>
正在为其设置选项的 ODBC 语句句柄。

### <a name="remarks"></a>备注

`CRecordset::OnSetOptions`还将调用此成员函数。

`OnSetOptions`设置登录超时值。 如果以前对 `SetQueryTimeout` 和成员函数的调用，则 `OnSetOptions` 反映当前值; 否则，它将设置默认值。

> [!NOTE]
> 在 MFC 4.2 之前， `OnSetOptions` 还应将处理模式设置为 "snychronous" 或 "异步"。 从 MFC 4.2 开始，所有操作都是同步的。 若要执行异步操作，必须直接调用 ODBC API 函数 `SQLSetPos` 。

不需要重写 `OnSetOptions` 来更改超时值。 相反，若要自定义查询超时值，请 `SetQueryTimeout` 在创建记录集之前调用; `OnSetOptions` 将使用新值。 值设置适用于对所有记录集或直接 SQL 调用的后续操作。

`OnSetOptions`如果要设置其他选项，请重写。 重写应在 `OnSetOptions` 调用 ODBC API 函数之前或之后调用基类 `SQLSetStmtOption` 。 按照框架的默认实现中所示的方法进行操作 `OnSetOptions` 。

## <a name="cdatabaseopen"></a><a name="open"></a>CDatabase：： Open

调用此成员函数以初始化新构造的 `CDatabase` 对象。

```
virtual BOOL Open(
    LPCTSTR lpszDSN,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T("ODBC;"),
    BOOL bUseCursorLib = TRUE);
```

### <a name="parameters"></a>参数

*lpszDSN*<br/>
指定数据源名称-通过 ODBC 管理程序在 ODBC 中注册的名称。 如果在*lpszConnect*中指定了 dsn 值（格式为 "DSN = \<data-source> "），则不能在*lpszDSN*中再次指定它。 在这种情况下， *lpszDSN*应为 NULL。 否则，如果要向用户显示 "数据源" 对话框（用户可以在其中选择数据源），则可以传递 NULL。 有关详细信息，请参阅 "备注"。

*bExclusive*<br/>
在此版本的类库中不受支持。 目前，如果此参数为 TRUE，则断言失败。 数据源始终以共享方式打开（非独占）。

*bReadOnly*<br/>
如果希望连接为只读并且禁止更新数据源，则为 TRUE。 所有依赖记录集均继承此属性。 默认值是 FALSE。

*lpszConnect*<br/>
指定连接字符串。 连接字符串会连接信息，其中可能包括数据源名称、对数据源有效的用户 ID、用户身份验证字符串（如果数据源需要密码，则为密码）和其他信息。 整个连接字符串必须以字符串 "ODBC;" 作为前缀。（大写或小写）。 "ODBC;" 字符串用于指示连接到 ODBC 数据源;这是为了在将来版本的类库可能支持非 ODBC 数据源时实现向上兼容性。

*bUseCursorLib*<br/>
如果要加载 ODBC 游标库 DLL，则为 TRUE。 游标库屏蔽基础 ODBC 驱动程序的某些功能，有效阻止使用动态集（如果驱动程序支持）。 如果加载游标库，则仅支持静态快照和只进游标。 默认值为 TRUE。 如果您计划直接从中创建记录集对象 `CRecordset` ，则不应加载游标库。

### <a name="return-value"></a>返回值

如果成功建立连接，则为非零值;否则，如果用户选择 "取消"，则会出现一个对话框，要求提供更多连接信息。 在所有其他情况下，框架都会引发异常。

### <a name="remarks"></a>备注

必须先初始化数据库对象，然后才能使用它构造记录集对象。

> [!NOTE]
> 调用[microsoft.office.interop.visio.documents.open](#openex)成员函数是连接到数据源和初始化数据库对象的首选方式。

如果调用中的参数 `Open` 未包含足够的信息来建立连接，ODBC 驱动程序将打开一个对话框，以获取用户所需的信息。 当你调用时 `Open` ，你的连接字符串*lpszConnect*将私下存储在对象中， `CDatabase` 并通过调用[GetConnect](#getconnect)成员函数提供。

如果需要，您可以在调用 `Open` 以从用户那里获取信息（如密码）之前打开自己的对话框，然后将该信息添加到您传递到的连接字符串中 `Open` 。 或者你可能想要保存传递的连接字符串，以便在下次应用程序对对象调用时，可以重复使用它 `Open` `CDatabase` 。

你还可以使用连接字符串进行多个级别的登录授权（每个都针对不同的 `CDatabase` 对象）或传达其他特定于数据源的信息。 有关连接字符串的详细信息，请参阅 Windows SDK 中的第5章。

例如，如果 DBMS 主机不可用，则连接尝试可能会超时。 如果连接尝试失败， `Open` 则会引发 `CDBException` 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

## <a name="cdatabaseopenex"></a><a name="openex"></a>CDatabase：： Microsoft.office.interop.visio.documents.open

调用此成员函数以初始化新构造的 `CDatabase` 对象。

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>参数

*lpszConnectString*<br/>
指定 ODBC 连接字符串。 这包括数据源名称以及其他可选信息，如用户 ID 和密码。 例如，"DSN = SQLServer_Source;UID = SA;PWD = abc123 "是可能的连接字符串。 请注意，如果为*lpszConnectString*传递 NULL，"数据源" 对话框将提示用户选择一个数据源。

*dwOptions*<br/>
一个位掩码，指定以下值的组合。 默认值为0，表示数据库将以写访问权限打开，将不加载 ODBC 游标库 DLL，并且仅当没有足够的信息建立连接时，"ODBC 连接" 对话框才会显示。

- `CDatabase::openExclusive`在此版本的类库中不受支持。 数据源始终以共享方式打开（非独占）。 目前，如果指定此选项，则断言失败。

- `CDatabase::openReadOnly`以只读方式打开数据源。

- `CDatabase::useCursorLib`加载 ODBC 游标库 DLL。 游标库屏蔽基础 ODBC 驱动程序的某些功能，有效阻止使用动态集（如果驱动程序支持）。 如果加载游标库，则仅支持静态快照和只进游标。 如果您计划直接从中创建记录集对象 `CRecordset` ，则不应加载游标库。

- `CDatabase::noOdbcDialog`不管是否提供足够的连接信息，都不会显示 "ODBC 连接" 对话框。

- `CDatabase::forceOdbcDialog`始终显示 "ODBC 连接" 对话框。

### <a name="return-value"></a>返回值

如果成功建立连接，则为非零值;否则，如果用户选择 "取消"，则会出现一个对话框，要求提供更多连接信息。 在所有其他情况下，框架都会引发异常。

### <a name="remarks"></a>备注

必须先初始化数据库对象，然后才能使用它构造记录集对象。

如果调用中的*lpszConnectString*参数 `OpenEx` 包含的信息不足，无法建立连接，ODBC 驱动程序将打开一个对话框，以获取用户所需的信息，前提是未在 `CDatabase::noOdbcDialog` `CDatabase::forceOdbcDialog` *dwOptions*参数中设置或。 当你调用时 `OpenEx` ，你的连接字符串*lpszConnectString*将私下存储在对象中， `CDatabase` 并通过调用[GetConnect](#getconnect)成员函数提供。

如果需要，您可以在调用 `OpenEx` 以从用户那里获取信息（如密码）之前打开自己的对话框，然后将该信息添加到您传递到的连接字符串中 `OpenEx` 。 或者你可能想要保存传递的连接字符串，以便在下次应用程序对对象调用时，可以重复使用它 `OpenEx` `CDatabase` 。

你还可以使用连接字符串进行多个级别的登录授权（每个都针对不同的 `CDatabase` 对象）或传达其他特定于数据源的信息。 有关连接字符串的详细信息，请参阅*ODBC 程序员参考*中的第6章。

例如，如果 DBMS 主机不可用，则连接尝试可能会超时。 如果连接尝试失败， `OpenEx` 则会引发 `CDBException` 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

## <a name="cdatabaserollback"></a><a name="rollback"></a>CDatabase：： Rollback

调用此成员函数可以撤消在事务中所做的更改。

```
BOOL Rollback();
```

### <a name="return-value"></a>返回值

如果事务已成功撤消，则为非零值;否则为0。 如果 `Rollback` 调用失败，则不定义数据源和事务状态。 如果 `Rollback` 返回0，则必须检查数据源以确定其状态。

### <a name="remarks"></a>备注

`CRecordset` `AddNew` `Edit` `Delete` `Update` 自上个[BeginTrans](#begintrans)以来执行的所有、、和调用都将回滚到该调用时存在的状态。

调用后 `Rollback` ，该事务将会结束，并且必须 `BeginTrans` 再次调用另一个事务。 调用之前的当前记录 `BeginTrans` 将在之后再次成为当前记录 `Rollback` 。

回滚后，回滚之前的当前记录将保持为最新。 有关回滚后记录集的状态和数据源的详细信息，请参阅[事务（ODBC）](../../data/odbc/transaction-odbc.md)一文。

### <a name="example"></a>示例

  请参阅[事务：在记录集中执行事务（ODBC）](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)一文。

## <a name="cdatabasesetlogintimeout"></a><a name="setlogintimeout"></a>CDatabase：： SetLoginTimeout

调用或之前调用此成员函数， `OpenEx` `Open` 以重写尝试的数据源连接超时之前允许的默认秒数。

```cpp
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>参数

*dwSeconds*<br/>
连接尝试超时之前允许的秒数。

### <a name="remarks"></a>备注

例如，如果 DBMS 不可用，则连接尝试可能会超时。 在 `SetLoginTimeout` 构造未初始化的 `CDatabase` 对象之后、调用或之前 `OpenEx` 调用 `Open` 。

登录超时的默认值为15秒。 并非所有数据源都支持指定登录超时值的功能。 如果数据源不支持超时，则会获得跟踪输出，但不会出现异常。 值0表示 "无限大"。

## <a name="cdatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDatabase：： SetQueryTimeout

调用此成员函数以覆盖在连接的数据源上的后续操作超时之前允许的默认秒数。

```cpp
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>参数

*dwSeconds*<br/>
查询尝试超时之前允许的秒数。

### <a name="remarks"></a>备注

由于网络访问问题、过多的查询处理时间等，操作可能会超时。 `SetQueryTimeout`在打开您的记录集之前或在调用记录集之前调用 `AddNew` ， `Update` 或 `Delete` 在需要更改查询超时值之前调用成员函数。 此设置会影响 `Open` `AddNew` `Update` `Delete` 对与此对象关联的任何记录集的所有后续、、和调用 `CDatabase` 。 在打开后更改记录集的查询超时值不会更改记录集的值。 例如，后续 `Move` 操作不会使用新值。

查询超时的默认值为15秒。 并非所有数据源都支持设置查询超时值的功能。 如果将查询超时值设置为0，则不会发生超时;与数据源的通信可能会停止响应。 在开发过程中，此行为可能会很有用。 如果数据源不支持超时，则会获得跟踪输出，但不会出现异常。

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)
