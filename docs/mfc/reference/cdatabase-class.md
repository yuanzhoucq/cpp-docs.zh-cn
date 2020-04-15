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
ms.openlocfilehash: 260a4a38fcee8994d804267709c11279266d393c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376483"
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
|[C 数据库：C 数据库](#cdatabase)|构造 `CDatabase` 对象。 必须通过调用`OpenEx`或`Open`初始化对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C 数据库：：开始转换](#begintrans)|在连接的数据源上启动一个"事务"-对`AddNew`类`Edit`的`Delete`、`Update`和 成员函数`CRecordset`的一系列可逆调用。 数据源必须支持事务才能`BeginTrans`产生任何效果。|
|[C 数据库：：绑定参数](#bindparameters)|允许您在调用`CDatabase::ExecuteSQL`之前绑定参数。|
|[C 数据库：：取消](#cancel)|从第二个线程取消异步操作或进程。|
|[C 数据库：：可以](#cantransact)|如果数据源支持事务，则返回非零。|
|[C 数据库：：可以更新](#canupdate)|如果`CDatabase`对象是可向上的（不只读的），则返回非零。|
|[C 数据库：关闭](#close)|关闭数据源连接。|
|[C 数据库：：提交转换](#committrans)|完成 由`BeginTrans`启动的事务。 事务中更改数据源的命令将执行。|
|[C 数据库：：执行SQL](#executesql)|执行 SQL 语句。 不返回任何数据记录。|
|[C 数据库：：获取书签持久性](#getbookmarkpersistence)|标识书签在记录集对象上保留的操作。|
|[CDatabase::GetConnect](#getconnect)|返回用于将对象连接到数据源的`CDatabase`ODBC 连接字符串。|
|[C 数据库：：获取光标提交行为](#getcursorcommitbehavior)|标识在打开的记录集对象上提交事务的效果。|
|[C 数据库：：获取光标回滚行为](#getcursorrollbackbehavior)|标识回滚事务对打开的记录集对象的影响。|
|[C 数据库：：获取数据库名称](#getdatabasename)|返回当前正在使用的数据库的名称。|
|[C 数据库：：打开](#isopen)|如果对象当前连接到数据源`CDatabase`，则返回非零。|
|[C 数据库：：打开选项](#onsetoptions)|由框架调用以设置标准连接选项。 默认实现设置查询超时值。 您可以通过调用`SetQueryTimeout`来提前建立这些选项。|
|[C 数据库：：打开](#open)|建立与数据源的连接（通过 ODBC 驱动程序）。|
|[C 数据库：：打开Ex](#openex)|建立与数据源的连接（通过 ODBC 驱动程序）。|
|[C 数据库：：回滚](#rollback)|撤消在当前事务期间所做的更改。 数据源返回到其以前状态（如`BeginTrans`调用中定义的那样）保持不变。|
|[C 数据库：：设置登录超时](#setlogintimeout)|设置数据源连接尝试超时后的秒数。|
|[C 数据库：：设置查询超时](#setquerytimeout)|设置数据库查询操作超时后的秒数。影响所有后续记录集`Open` `AddNew`、`Edit`和`Delete`调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C 数据库：：m_hdbc](#m_hdbc)|打开数据库连接 （ODBC） 连接到数据源。 *HDBC*类型 。|

## <a name="remarks"></a>备注

数据源是由某些数据库管理系统 （DBMS） 托管的数据的特定实例。 示例包括微软 SQL 服务器、微软访问、博兰 dBASE 和 xBASE。 在应用程序中，一次可以`CDatabase`激活一个或多个对象。

> [!NOTE]
> 如果使用数据访问对象 （DAO） 类而不是开放数据库连接 （ODBC） 类，请使用类[CDao 数据库](../../mfc/reference/cdaodatabase-class.md)。 有关详细信息，请参阅文章[概述：数据库编程](../../data/data-access-programming-mfc-atl.md)。

要使用`CDatabase`，构造`CDatabase`对象并调用其成员`OpenEx`函数。 这将打开连接。 然后构造`CRecordset`对象以在连接的数据源上操作时，将记录集构造函数传递给对象的`CDatabase`指针。 使用完连接后，调用`Close`成员函数并销毁`CDatabase`对象。 `Close`关闭以前未关闭的任何记录集。

有关 的详细信息`CDatabase`，请参阅[数据源 （ODBC）](../../data/odbc/data-source-odbc.md)和[概述：数据库编程](../../data/data-access-programming-mfc-atl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="cdatabasebegintrans"></a><a name="begintrans"></a>C 数据库：：开始转换

调用此成员函数以开始具有连接的数据源的事务。

```
BOOL BeginTrans();
```

### <a name="return-value"></a>返回值

如果呼叫成功且仅手动提交更改，则非零;否则 0。

### <a name="remarks"></a>备注

事务由对`AddNew``Edit``Delete``Update``CRecordset`对象的 的 一个或多个调用组成，以及对象的成员函数。 在开始事务之前，`CDatabase`对象必须通过调用其`OpenEx`或`Open`成员函数连接到数据源。 要结束事务，请致电[CommitTrans](#committrans)接受对数据源的所有更改（并执行这些更改），或调用[回滚](#rollback)以中止整个事务。 打开`BeginTrans`事务中涉及的任何记录集并尽可能接近实际更新操作后调用。

> [!CAUTION]
> 根据您的 ODBC 驱动程序，在调用`BeginTrans`之前打开记录集可能会导致调用`Rollback`时出现问题。 您应该检查您正在使用的特定驱动程序。 例如，当使用 Microsoft ODBC 桌面驱动程序包 3.0 中包含的 Microsoft Access 驱动程序时，必须考虑 Jet 数据库引擎的要求，即不应在具有打开游标的任何数据库上开始事务。 在 MFC 数据库类中，打开的游标`CRecordset`表示打开的对象。 有关详细信息，请参阅[技术说明 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md)。

`BeginTrans`还可能锁定服务器上的数据记录，具体取决于请求的并发和数据源的功能。 有关锁定数据的信息，请参阅[文章"记录集：锁定记录"（ODBC）。](../../data/odbc/recordset-locking-records-odbc.md)

用户定义的事务在文章[事务 （ODBC） 中解释。](../../data/odbc/transaction-odbc.md)

`BeginTrans`建立可以回滚（反向）的事务序列的状态。 要为回滚建立新状态，请提交任何当前事务，然后再次调用`BeginTrans`。

> [!CAUTION]
> 再次`BeginTrans`调用而不调用`CommitTrans`或`Rollback`是一个错误。

调用[CanTransact](#cantransact)成员函数以确定驱动程序是否支持给定数据库的事务。 您还应调用[GetCursorCommitCommit行为](#getcursorcommitbehavior)和[GetCursorRollback行为，](#getcursorrollbackbehavior)以确定对游标保留的支持。

有关交易记录的详细信息，请参阅文章[事务 （ODBC）](../../data/odbc/transaction-odbc.md)。

### <a name="example"></a>示例

  请参阅文章["事务：在记录集 （ODBC） 中执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)"。

## <a name="cdatabasebindparameters"></a><a name="bindparameters"></a>C 数据库：：绑定参数

在`BindParameters`调用[CDatabase：：执行SQL](#executesql)之前需要绑定参数时，请覆盖。

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>参数

*hstmt*<br/>
要为其绑定参数的 ODBC 语句句柄。

### <a name="remarks"></a>备注

当您不需要存储过程的结果集时，此方法非常有用。

在重写中，调用`SQLBindParameters`和相关 ODBC 函数以绑定参数。 MFC 在`ExecuteSQL`调用 之前调用 重写。 你不需要打电话`SQLPrepare`。`ExecuteSQL`调用`SQLExecDirect`并销毁*hstmt，* 它只使用一次。

## <a name="cdatabasecancel"></a><a name="cancel"></a>C 数据库：：取消

调用此成员函数请求数据源取消正在进行的异步操作或从第二个线程取消进程。

```
void Cancel();
```

### <a name="remarks"></a>备注

请注意，MFC ODBC 类不再使用异步处理;要执行异步操作，必须直接调用 ODBC API 函数[SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function)。 有关详细信息，请参阅[异步执行](/sql/odbc/reference/develop-app/asynchronous-execution)。

## <a name="cdatabasecantransact"></a><a name="cantransact"></a>C 数据库：：可以

调用此成员函数以确定数据库是否允许事务。

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>返回值

如果使用此`CDatabase`对象的记录集允许事务，则非零;否则 0。

### <a name="remarks"></a>备注

有关交易记录的信息，请参阅文章事务[（ODBC）](../../data/odbc/transaction-odbc.md)。

## <a name="cdatabasecanupdate"></a><a name="canupdate"></a>C 数据库：：可以更新

调用此成员函数以确定`CDatabase`对象是否允许更新。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>返回值

如果对象允许更新`CDatabase`，则非零;否则 0，指示在打开`CDatabase`对象时在*bReadOnly*中传递 TRUE，或者数据源本身是只读的。 如果对 ODBC API 函数`SQLGetInfo`的调用返回 SQL_DATASOURCE_READ_ONLY 返回"y"，则数据源是只读的。

### <a name="remarks"></a>备注

并非所有驱动程序都支持更新。

## <a name="cdatabasecdatabase"></a><a name="cdatabase"></a>C 数据库：C 数据库

构造 `CDatabase` 对象。

```
CDatabase();
```

### <a name="remarks"></a>备注

构造对象后，必须调用其`OpenEx`或`Open`成员函数以建立与指定数据源的连接。

您可能会发现将`CDatabase`对象嵌入到文档类中很方便。

### <a name="example"></a>示例

此示例说明了在`CDocument`派生`CDatabase`类中的使用。

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

## <a name="cdatabaseclose"></a><a name="close"></a>C 数据库：关闭

如果要断开与数据源的连接，请调用此成员函数。

```
virtual void Close();
```

### <a name="remarks"></a>备注

在调用此成员函数之前，`CDatabase`必须关闭与对象关联的任何记录集。 因为`Close`不会破坏`CDatabase`对象，因此可以通过打开与同一数据源或其他数据源的新连接来重用该对象。

使用数据库`AddNew`的所有`Edit`挂起或记录集的语句都将被取消，并且所有挂起的事务都将回滚。 依赖于`CDatabase`对象的任何记录集都处于未定义状态。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

## <a name="cdatabasecommittrans"></a><a name="committrans"></a>C 数据库：：提交转换

完成事务时调用此成员函数。

```
BOOL CommitTrans();
```

### <a name="return-value"></a>返回值

如果已成功提交更新，则非零;否则 0。 如果`CommitTrans`失败，数据源的状态将未定义。 您必须检查数据以确定其状态。

### <a name="remarks"></a>备注

事务包括`AddNew`一系列对`Edit``Delete``Update``CRecordset`对象 的调用，以及以调用[BeginTrans](#begintrans)成员函数开头的对象的成员函数。 `CommitTrans`提交事务。 默认情况下，将立即提交更新;因此，更新将立即提交。调用`BeginTrans`会导致更新的承诺延迟到`CommitTrans`调用。

在调用`CommitTrans`结束事务之前，可以调用[回滚](#rollback)成员函数以中止事务并将数据源保留为其原始状态。 要开始新事务，请再次`BeginTrans`调用。

有关交易记录的详细信息，请参阅文章[事务 （ODBC）](../../data/odbc/transaction-odbc.md)。

### <a name="example"></a>示例

  请参阅文章["事务：在记录集 （ODBC） 中执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)"。

## <a name="cdatabaseexecutesql"></a><a name="executesql"></a>C 数据库：：执行SQL

当您需要直接执行 SQL 命令时，请调用此成员函数。

```
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>参数

*lpszSQL*<br/>
指向包含要执行的有效 SQL 命令的 null 端接字符串的指针。 你可以传递一个[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>备注

将命令创建为 null 终止字符串。 `ExecuteSQL`不返回数据记录。 如果要对记录操作，请使用记录集对象。

数据源的大多数命令都通过记录集对象发出，这些对象支持选择数据、插入新记录、删除记录和编辑记录的命令。 但是，并非所有 ODBC 功能都由数据库类直接支持，因此有时您可能需要使用 进行直接 SQL 调用`ExecuteSQL`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

## <a name="cdatabasegetbookmarkpersistence"></a><a name="getbookmarkpersistence"></a>C 数据库：：获取书签持久性

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
|SQL_BP_CLOSE|书签在`Requery`操作后有效。|
|SQL_BP_DELETE|行的书签在该行`Delete`的操作后有效。|
|SQL_BP_DROP|书签在`Close`操作后有效。|
|SQL_BP_SCROLL|书签在任何`Move`操作后都有效。 这只标识记录集上是否支持书签，正如 `CRecordset::CanBookmark` 返回的值一样。|
|SQL_BP_TRANSACTION|在提交或回滚事务后，书签将变为有效。|
|SQL_BP_UPDATE|行的书签在该行`Update`的操作后有效。|
|SQL_BP_OTHER_HSTMT|与某个记录集对象关联的书签在另一个记录集上有效。|

有关此返回值的详细信息，请参阅 Windows SDK 中的`SQLGetInfo`ODBC API 功能。 有关书签的详细信息，请参阅[文章"记录集：书签和绝对位置 "（ODBC）。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

## <a name="cdatabasegetconnect"></a><a name="getconnect"></a>C 数据库：：获取连接

调用此成员函数以检索调用 到`OpenEx`或`Open`将`CDatabase`对象连接到数据源期间使用的连接字符串。

```
const CString GetConnect() const;
```

### <a name="return-value"></a>返回值

在`OpenEx`调用或`Open`已调用连接字符串时包含连接字符串的**const**[CString;](../../atl-mfc-shared/reference/cstringt-class.md)否则，一个空字符串。

### <a name="remarks"></a>备注

有关如何创建连接字符串的说明，请参阅[CDatabase：：打开](#open)。

## <a name="cdatabasegetcursorcommitbehavior"></a><a name="getcursorcommitbehavior"></a>C 数据库：：获取光标提交行为

调用此成员函数以确定[CommitTrans](#committrans)操作如何影响打开的记录集对象上的游标。

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>返回值

指示事务对打开的记录集对象的影响的值。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

下表列出了 打开的记录集的可能`GetCursorCommitBehavior`返回值和相应的影响。

|返回值|对 CRecordset 对象的影响|
|------------------|----------------------------------|
|SQL_CB_CLOSE|在`CRecordset::Requery`事务提交后立即调用。|
|SQL_CB_DELETE|在`CRecordset::Close`事务提交后立即调用。|
|SQL_CB_PRESERVE|正常地执行`CRecordset`操作。|

有关此返回值的详细信息，请参阅 Windows SDK 中的`SQLGetInfo`ODBC API 功能。 有关交易记录的详细信息，请参阅文章[事务 （ODBC）](../../data/odbc/transaction-odbc.md)。

## <a name="cdatabasegetcursorrollbackbehavior"></a><a name="getcursorrollbackbehavior"></a>C 数据库：：获取光标回滚行为

调用此成员函数以确定[回滚](#rollback)操作如何影响打开的记录集对象上的游标。

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>返回值

指示事务对打开的记录集对象的影响的值。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

下表列出了 打开的记录集的可能`GetCursorRollbackBehavior`返回值和相应的影响。

|返回值|对 CRecordset 对象的影响|
|------------------|----------------------------------|
|SQL_CB_CLOSE|在`CRecordset::Requery`事务回滚后立即调用。|
|SQL_CB_DELETE|在`CRecordset::Close`事务回滚后立即调用。|
|SQL_CB_PRESERVE|正常地执行`CRecordset`操作。|

有关此返回值的详细信息，请参阅 Windows SDK 中的`SQLGetInfo`ODBC API 功能。 有关交易记录的详细信息，请参阅文章[事务 （ODBC）](../../data/odbc/transaction-odbc.md)。

## <a name="cdatabasegetdatabasename"></a><a name="getdatabasename"></a>C 数据库：：获取数据库名称

调用此成员函数以检索当前连接的数据库的名称（前提是数据源定义了名为"数据库"的命名对象）。

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>返回值

包含数据库名称的[CString（](../../atl-mfc-shared/reference/cstringt-class.md)如果成功）;否则，空`CString`。

### <a name="remarks"></a>备注

这与 或`OpenEx``Open`调用中指定的数据源名称 （DSN） 不同。 返回`GetDatabaseName`的内容取决于 ODBC。 通常，数据库是表的集合。 如果此实体具有名称，`GetDatabaseName`则返回它。

例如，您可能希望在标题中显示此名称。 如果从 ODBC 检索名称时发生错误，`GetDatabaseName`则返回空`CString`。

## <a name="cdatabaseisopen"></a><a name="isopen"></a>C 数据库：：打开

调用此成员函数以确定`CDatabase`对象当前是否连接到数据源。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果对象当前已`CDatabase`连接，则非零;否则 0。

## <a name="cdatabasem_hdbc"></a><a name="m_hdbc"></a>C 数据库：：m_hdbc

包含 ODBC 数据源连接的公共句柄 - "连接句柄"。

### <a name="remarks"></a>备注

通常，您无需直接访问此成员变量。 相反，框架在调用`OpenEx`或`Open`时分配句柄。 当您调用`CDatabase`对象上的**delete**运算符时，框架将解分配句柄。 请注意，`Close`成员函数不会解分配句柄。

但是，在某些情况下，您可能需要直接使用该句柄。 例如，如果需要直接调用 ODBC API 函数，而不是通过类`CDatabase`调用 ，则可能需要连接句柄作为参数传递。 请参阅下面的代码示例。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

## <a name="cdatabaseonsetoptions"></a><a name="onsetoptions"></a>C 数据库：：打开选项

当直接使用成员函数执行 SQL 语句时，`ExecuteSQL`框架将调用此成员函数。

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>参数

*hstmt*<br/>
正在为其设置选项的 ODBC 语句句柄。

### <a name="remarks"></a>备注

`CRecordset::OnSetOptions`也称为此成员函数。

`OnSetOptions`设置登录超时值。 如果以前对 和 成员函数`SetQueryTimeout`进行了调用，则`OnSetOptions`反映当前值;如果以前对 和 成员函数进行了调用，则反映当前值。否则，它将设置默认值。

> [!NOTE]
> 在 MFC 4.2`OnSetOptions`之前，还将处理模式设置为 snychronous 或异步。 从 MFC 4.2 开始，所有操作都是同步的。 要执行异步操作，必须直接调用 ODBC API 函数`SQLSetPos`。

不需要重写`OnSetOptions`来更改超时值。 相反，要自定义查询超时值，请在创建记录`SetQueryTimeout`集之前调用;但是，为了自定义查询超时值，请在创建记录集之前调用。`OnSetOptions`将使用新值。 设置的值适用于所有记录集或直接 SQL 调用的后续操作。

如果要`OnSetOptions`设置其他选项，则重写。 重写应在调用 ODBC `OnSetOptions` API 函数`SQLSetStmtOption`之前或之后调用基类。 按照 框架的默认实现中所示的方法`OnSetOptions`操作。

## <a name="cdatabaseopen"></a><a name="open"></a>C 数据库：：打开

调用此成员函数以初始化新构造`CDatabase`的对象。

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
指定数据源名称 – 通过 ODBC 管理员程序在 ODBC 注册的名称。 如果在*lpszConnect*中指定了 DSN 值（以"DSN+\<数据源>形式"），则不得在*lpszDSN*中再次指定它。 在这种情况下 *，lpszDSN*应为 NULL。 否则，如果要向用户显示数据源对话框，用户可以在该对话框中选择数据源，则可以传递 NULL。 有关详细信息，请参阅备注。

*b 独家*<br/>
此版本的类库不支持。 目前，如果此参数为 TRUE，断言将失败。 数据源始终以共享形式打开（非独占）。

*b 只读*<br/>
如果希望连接为只读，并且禁止对数据源的更新，则为 TRUE。 所有从属记录集都继承此属性。 默认值是 FALSE。

*lpszConnect*<br/>
指定连接字符串。 连接字符串串联信息，可能包括数据源名称、数据源上有效的用户 ID、用户身份验证字符串（如果数据源需要密码）和其他信息。 整个连接字符串必须由字符串"ODBC;"预定。（大写或小写）。 "ODBC;"字符串用于指示连接与 ODBC 数据源的连接;当类库的未来版本可能支持非 ODBC 数据源时，这是为了向上兼容。

*bUseCursorLib*<br/>
如果希望加载 ODBC 游标库 DLL，则为 TRUE。 光标库屏蔽了基础 ODBC 驱动程序的某些功能，从而有效地防止了动态集的使用（如果驱动程序支持它们）。 加载游标库时支持的唯一游标是静态快照和仅转发游标。 默认值为 TRUE。 如果计划直接从`CRecordset`创建记录集对象而不派生，则不应加载游标库。

### <a name="return-value"></a>返回值

如果连接成功，则非零;否则 0 如果用户在显示对话框时选择"取消"，请提供更多连接信息。 在所有其他情况下，框架将引发异常。

### <a name="remarks"></a>备注

必须先初始化数据库对象，然后才能使用它构造记录集对象。

> [!NOTE]
> 调用[OpenEx](#openex)成员函数是连接到数据源并初始化数据库对象的首选方法。

如果`Open`呼叫中的参数不包含足够的信息来建立连接，ODBC 驱动程序将打开一个对话框，从用户处获取必要的信息。 调用`Open`时，连接字符串*lpszConnect*会私下存储在对象中`CDatabase`，并且可以通过调用[GetConnect](#getconnect)成员函数来获取。

如果需要，可以在调用`Open`之前打开自己的对话框，以便从用户获取信息（如密码），然后将该信息添加到传递给 的连接字符串`Open`中。 或者，您可能希望保存传递的连接字符串，以便在应用程序下次调用`Open``CDatabase`对象时重用它。

您还可以将连接字符串用于多个级别的登录授权（每个级别用于其他`CDatabase`对象），或传输其他特定于数据源的信息。 有关连接字符串的详细信息，请参阅 Windows SDK 中的第 5 章。

例如，如果 DBMS 主机不可用，连接尝试可能会超时。 如果连接尝试失败，`Open`则引发`CDBException`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

## <a name="cdatabaseopenex"></a><a name="openex"></a>C 数据库：：打开Ex

调用此成员函数以初始化新构造`CDatabase`的对象。

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>参数

*lpszConnectString*<br/>
指定 ODBC 连接字符串。 这包括数据源名称以及其他可选信息，如用户 ID 和密码。 例如，"DSN=SQLServer_Source;UID_SA;PWD_abc123" 是一个可能的连接字符串。 请注意，如果通过 NULL 的*lpszConnectString*，数据源对话框将提示用户选择数据源。

*dwOptions*<br/>
指定以下值组合的位掩码。 默认值为 0，这意味着数据库将以写入访问共享方式打开，不会加载 ODBC 游标库 DLL，并且 ODBC 连接对话框仅在没有足够的信息进行连接时才会显示。

- `CDatabase::openExclusive`此版本的类库不支持。 数据源始终以共享形式打开（非独占）。 目前，如果指定此选项，断言将失败。

- `CDatabase::openReadOnly`将数据源打开为只读。

- `CDatabase::useCursorLib`加载 ODBC 光标库 DLL。 光标库屏蔽了基础 ODBC 驱动程序的某些功能，从而有效地防止了动态集的使用（如果驱动程序支持它们）。 加载游标库时支持的唯一游标是静态快照和仅转发游标。 如果计划直接从`CRecordset`创建记录集对象而不派生，则不应加载游标库。

- `CDatabase::noOdbcDialog`无论是否提供了足够的连接信息，请勿显示 ODBC 连接对话框。

- `CDatabase::forceOdbcDialog`始终显示 ODBC 连接对话框。

### <a name="return-value"></a>返回值

如果连接成功，则非零;否则 0 如果用户在显示对话框时选择"取消"，请提供更多连接信息。 在所有其他情况下，框架将引发异常。

### <a name="remarks"></a>备注

必须先初始化数据库对象，然后才能使用它构造记录集对象。

如果`OpenEx`呼叫中的*lpszConnectString*参数不包含足够的信息进行连接，则 ODBC 驱动程序将打开一个对话框，从用户处获取必要的信息，前提是您尚未设置`CDatabase::noOdbcDialog`或`CDatabase::forceOdbcDialog`位于*dwOptions*参数中。 调用`OpenEx`时，连接字符串*lpszConnectString*会私下存储在对象中`CDatabase`，并且可通过调用[GetConnect](#getconnect)成员函数获得。

如果需要，可以在调用`OpenEx`之前打开自己的对话框，以便从用户获取信息（如密码），然后将该信息添加到传递给`OpenEx`的连接字符串中。 或者，您可能希望保存传递的连接字符串，以便在应用程序下次调用`OpenEx``CDatabase`对象时重用它。

您还可以将连接字符串用于多个级别的登录授权（每个级别用于其他`CDatabase`对象），或传输其他特定于数据源的信息。 有关连接字符串的详细信息，请参阅*ODBC 程序员参考*章的第 6 章。

例如，如果 DBMS 主机不可用，连接尝试可能会超时。 如果连接尝试失败，`OpenEx`则引发`CDBException`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

## <a name="cdatabaserollback"></a><a name="rollback"></a>C 数据库：：回滚

调用此成员函数以撤消在事务期间所做的更改。

```
BOOL Rollback();
```

### <a name="return-value"></a>返回值

如果事务已成功冲销，则非零;否则 0。 如果`Rollback`调用失败，则数据源和事务状态未定义。 如果`Rollback`返回 0，则必须检查数据源以确定其状态。

### <a name="remarks"></a>备注

自上次`CRecordset``AddNew` `Edit` [BeginTrans](#begintrans) `Update`以来执行的所有 、`Delete`和调用都将回滚到该调用时的状态。

调用`Rollback`后，事务已结束，您必须再次调用`BeginTrans`另一个事务。 调用`BeginTrans`之前当前的记录在 之后`Rollback`再次成为当前记录。

回滚后，回滚之前当前的记录将保持最新状态。 有关回滚后记录集的状态和数据源的详细信息，请参阅文章[事务 （ODBC）。](../../data/odbc/transaction-odbc.md)

### <a name="example"></a>示例

  请参阅文章["事务：在记录集 （ODBC） 中执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)"。

## <a name="cdatabasesetlogintimeout"></a><a name="setlogintimeout"></a>C 数据库：：设置登录超时

调用此成员函数 （在调用`OpenEx`之前`Open`或 — 以覆盖数据源尝试连接超时之前允许的默认秒数）。

```
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>参数

*dw 秒*<br/>
连接尝试超时之前要允许的秒数。

### <a name="remarks"></a>备注

例如，如果 DBMS 不可用，则连接尝试可能会超时。 构造`SetLoginTimeout`未初始化`CDatabase`的对象后，但在调用 或`OpenEx``Open`之前调用 。

登录超时的默认值为 15 秒。 并非所有数据源都支持指定登录超时值的能力。 如果数据源不支持超时，您将获得跟踪输出，但不会提供异常。 值 0 表示"无限"。

## <a name="cdatabasesetquerytimeout"></a><a name="setquerytimeout"></a>C 数据库：：设置查询超时

调用此成员函数以覆盖默认秒数，以便在后续对连接的数据源超时的操作之前允许。

```
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>参数

*dw 秒*<br/>
查询尝试超时之前要允许的秒数。

### <a name="remarks"></a>备注

操作可能会由于网络访问问题、查询处理时间过长等原因而超时。 如果要`SetQueryTimeout`更改查询超时值，请先打开记录集之前或调用记录集`AddNew``Update`的`Delete`或 成员函数之前调用。 该设置影响所有后续`Open``AddNew`的`Update`、`Delete`和对与此`CDatabase`对象关联的任何记录集的调用。 打开后更改记录集的查询超时值不会更改记录集的值。 例如，后续`Move`操作不使用新值。

查询超时的默认值为 15 秒。 并非所有数据源都支持设置查询超时值的能力。 如果将查询超时值设置为 0，则不执行超时;如果将超时设置为 0，则不执行超时。与数据源的通信可能会停止响应。 此行为在开发期间可能很有用。 如果数据源不支持超时，您将获得跟踪输出，但不会提供异常。

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)
