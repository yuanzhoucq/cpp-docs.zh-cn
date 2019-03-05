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
ms.openlocfilehash: 0e523b2a145254cd9b7adf2b066605a679349f6c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273437"
---
# <a name="cdatabase-class"></a>CDatabase 类

表示与数据源的连接，通过此连接可操作数据源。

## <a name="syntax"></a>语法

```
class CDatabase : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDatabase::CDatabase](#cdatabase)|构造 `CDatabase` 对象。 必须初始化该对象通过调用`OpenEx`或`Open`。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDatabase::BeginTrans](#begintrans)|启动"事务"— 可逆调用一系列`AddNew`， `Edit`， `Delete`，和`Update`类的成员函数`CRecordset`— 上连接的数据源。 数据源必须支持的事务`BeginTrans`产生任何影响。|
|[CDatabase::BindParameters](#bindparameters)|允许您将绑定参数之前，调用`CDatabase::ExecuteSQL`。|
|[CDatabase::Cancel](#cancel)|取消异步操作或从第二个线程的进程。|
|[CDatabase::CanTransact](#cantransact)|返回非零，如果数据源支持事务。|
|[CDatabase::CanUpdate](#canupdate)|返回非零值如果`CDatabase`对象是可更新 （非只读）。|
|[CDatabase::Close](#close)|关闭数据源连接。|
|[CDatabase::CommitTrans](#committrans)|完成开始的事务`BeginTrans`。 在事务中更改数据源的命令都将执行。|
|[CDatabase::ExecuteSQL](#executesql)|执行 SQL 语句。 返回没有数据记录。|
|[CDatabase::GetBookmarkPersistence](#getbookmarkpersistence)|标识通过该书签保存记录集对象的操作。|
|[CDatabase::GetConnect](#getconnect)|返回用于连接的 ODBC 连接字符串`CDatabase`到数据源的对象。|
|[CDatabase::GetCursorCommitBehavior](#getcursorcommitbehavior)|标识提交打开记录集对象上的事务的效果。|
|[CDatabase::GetCursorRollbackBehavior](#getcursorrollbackbehavior)|标识在打开记录集对象上回滚事务的效果。|
|[CDatabase::GetDatabaseName](#getdatabasename)|返回当前所用的数据库的名称。|
|[CDatabase::IsOpen](#isopen)|返回非零值如果`CDatabase`对象当前连接到数据源。|
|[CDatabase::OnSetOptions](#onsetoptions)|由框架调用以设置标准连接选项。 默认实现将设置查询超时值。 可以通过调用建立这些选项提前`SetQueryTimeout`。|
|[CDatabase::Open](#open)|建立与数据源 （通过 ODBC 驱动程序） 的连接。|
|[CDatabase::OpenEx](#openex)|建立与数据源 （通过 ODBC 驱动程序） 的连接。|
|[CDatabase::Rollback](#rollback)|反转当前事务期间所做的更改。 数据源返回到以前的状态，如中所定义`BeginTrans`调用时，不变。|
|[CDatabase::SetLoginTimeout](#setlogintimeout)|设置数据源连接尝试后将超时时间的秒数。|
|[CDatabase::SetQueryTimeout](#setquerytimeout)|集多少秒后的数据库查询操作将超时。影响所有后续的记录集`Open`， `AddNew`， `Edit`，和`Delete`调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CDatabase::m_hdbc](#m_hdbc)|打开数据库连接 (ODBC) 连接到数据源的句柄。 类型*HDBC*。|

## <a name="remarks"></a>备注

数据源是托管的某些数据库管理系统 (DBMS) 数据的特定实例。 示例包括 Microsoft SQL Server、 Microsoft Access、 Borland dBASE 和 xBASE。 可以有一个或多个`CDatabase`活动一次在应用程序中的对象。

> [!NOTE]
>  如果您正在使用的数据访问对象 (DAO) 类而不是开放式数据库连接 (ODBC) 类，使用类[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)相反。 有关详细信息，请参阅文章[概述：数据库编程](../../data/data-access-programming-mfc-atl.md)。

若要使用`CDatabase`，构造`CDatabase`对象，并调用其`OpenEx`成员函数。 这将打开一个连接。 然后构造时`CRecordset`在连接的数据源上的对象记录集构造函数将指针传递到你`CDatabase`对象。 当你完成使用的连接时，请调用`Close`成员函数，并销毁`CDatabase`对象。 `Close` 关闭以前关闭的任何记录集。

有关详细信息`CDatabase`，请参阅文章[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)和[概述：数据库编程](../../data/data-access-programming-mfc-atl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>要求

**标头：** afxdb.h

##  <a name="begintrans"></a>  CDatabase::BeginTrans

调用此成员函数以开始使用已连接的数据源的事务。

```
BOOL BeginTrans();
```

### <a name="return-value"></a>返回值

如果调用成功，并且在提交更改仅手动; 非零值否则为 0。

### <a name="remarks"></a>备注

交易都包含一个或多个调用`AddNew`， `Edit`， `Delete`，和`Update`的成员函数`CRecordset`对象。 开始一个事务之前,`CDatabase`对象必须已具有已连接到数据源通过调用其`OpenEx`或`Open`成员函数。 若要结束该事务，调用[CommitTrans](#committrans)以接受对数据源的所有更改 （并执行操作） 或调用[回滚](#rollback)中止整个事务。 调用`BeginTrans`后打开事务中涉及的任何记录集和为接近实际更新尽可能操作。

> [!CAUTION]
>  具体取决于 ODBC 驱动程序，打开之前调用的记录集`BeginTrans`调用时可能会导致问题`Rollback`。 应检查正在使用的特定驱动程序。 例如，当使用 Microsoft ODBC Desktop Driver Pack 3.0 中包含的 Microsoft Access 驱动程序，必须考虑应开始在已打开的游标的任何数据库上事务的 Jet 数据库引擎的要求。 在 MFC 数据库类中，打开的游标意味着打开`CRecordset`对象。 有关详细信息，请参阅[技术注意 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md)。

`BeginTrans` 在服务器上，具体取决于请求的并发性和数据源的功能也可能会锁定数据记录。 有关锁定的数据的信息，请参阅文章[记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)。

一文中介绍了用户定义的事务[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。

`BeginTrans` 建立的状态所属的事务序列的可回滚 （撤消）。 若要建立的新状态的回滚，提交任何当前的事务，然后调用`BeginTrans`试。

> [!CAUTION]
>  调用`BeginTrans`而无需调用再次`CommitTrans`或`Rollback`是错误。

调用[CanTransact](#cantransact)成员函数来确定您的驱动程序是否支持给定数据库的事务。 此外应调用[GetCursorCommitBehavior](#getcursorcommitbehavior)并[GetCursorRollbackBehavior](#getcursorrollbackbehavior)来确定游标实现保留的支持。

有关事务的详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。

### <a name="example"></a>示例

  请参阅文章[事务：在记录集 (ODBC) 执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。

##  <a name="bindparameters"></a>  CDatabase::BindParameters

重写`BindParameters`当你需要将绑定之前调用的参数[CDatabase::ExecuteSQL](#executesql)。

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>参数

*hstmt*<br/>
你想要将绑定参数 ODBC 语句句柄。

### <a name="remarks"></a>备注

此方法非常有用的不需要结果时设置从存储过程。

在替代中，调用`SQLBindParameters`和相关 ODBC 函数将参数绑定。 MFC 调用之前的调用重写`ExecuteSQL`。 不需要调用`SQLPrepare`;`ExecuteSQL`调用`SQLExecDirect`，并销毁*hstmt*，这仅使用一次。

##  <a name="cancel"></a>  CDatabase::Cancel

调用此成员函数以请求数据源取消异步操作正在进行中的或从第二个线程的进程。

```
void Cancel();
```

### <a name="remarks"></a>备注

请注意，MFC ODBC 类不能再使用异步处理;若要执行的异步操作，您必须直接调用 ODBC API 函数[SQLSetConnectOption](/previous-versions/windows/desktop/ms713564)。 有关详细信息，请参阅[异步执行](/previous-versions/windows/desktop/ms713563)Windows SDK 中。

##  <a name="cantransact"></a>  CDatabase::CanTransact

调用此成员函数以确定数据库是否允许事务。

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>返回值

非零值如果使用此记录集`CDatabase`对象允许事务; 否则为 0。

### <a name="remarks"></a>备注

有关事务信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。

##  <a name="canupdate"></a>  CDatabase::CanUpdate

调用此成员函数以确定是否`CDatabase`对象允许更新。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>返回值

如果非零`CDatabase`对象允许更新; 否则为 0，该值指示该你传入 TRUE *bReadOnly*当您打开`CDatabase`对象或数据源本身是只读的。 数据源是只读的如果 ODBC API 函数调用`SQLGetInfo`为 SQL_DATASOURCE_READ_ONLY 返回"y"。

### <a name="remarks"></a>备注

并非所有驱动程序支持的更新。

##  <a name="cdatabase"></a>  CDatabase::CDatabase

构造 `CDatabase` 对象。

```
CDatabase();
```

### <a name="remarks"></a>备注

构造对象之后, 必须调用其`OpenEx`或`Open`成员函数来建立与指定的数据源的连接。

您可能会发现可以方便地嵌入`CDatabase`中您的文档类对象。

### <a name="example"></a>示例

此示例演示如何使用`CDatabase`在`CDocument`-派生的类。

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

##  <a name="close"></a>  CDatabase::Close

如果你想要从数据源断开连接，请调用此成员函数。

```
virtual void Close();
```

### <a name="remarks"></a>备注

您必须关闭关联的任何记录集中`CDatabase`对象之前调用此成员函数。 因为`Close`不会销毁`CDatabase`对象，通过打开新的连接到同一数据源或不同的数据源，可以重用该对象。

所有挂起`AddNew`或`Edit`取消使用的数据库的记录集的语句，并且所有挂起的事务将回滚。 依赖于任何记录集`CDatabase`对象处于未定义的状态。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

##  <a name="committrans"></a>  CDatabase::CommitTrans

调用此成员函数在完成事务时。

```
BOOL CommitTrans();
```

### <a name="return-value"></a>返回值

如果更新已成功提交; 非零值否则为 0。 如果`CommitTrans`失败，数据源的状态为未定义。 必须检查以确定其状态的数据。

### <a name="remarks"></a>备注

事务的调用的一系列组成`AddNew`， `Edit`， `Delete`，和`Update`的成员函数`CRecordset`开始通过调用的对象[BeginTrans](#begintrans)成员函数。 `CommitTrans` 提交事务。 默认情况下，更新将被立即提交;调用`BeginTrans`导致的更新的承诺会延迟，直至`CommitTrans`调用。

直到您调用`CommitTrans`若要结束事务，可以调用[回滚](#rollback)成员函数来中止事务并使数据源保持其原始状态。 若要开始新的事务，调用`BeginTrans`试。

有关事务的详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。

### <a name="example"></a>示例

  请参阅文章[事务：在记录集 (ODBC) 执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。

##  <a name="executesql"></a>  CDatabase::ExecuteSQL

当您需要直接执行 SQL 命令时调用此成员函数。

```
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>参数

*lpszSQL*<br/>
指向包含要执行的有效 SQL 命令的以 null 结尾的字符串指针。 可以将传递[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>备注

创建该命令作为以 null 结尾的字符串。 `ExecuteSQL` 不返回数据记录。 如果你想要对记录进行操作，请改为使用记录集对象。

通过记录集对象，用于选择数据，插入新记录、 删除记录，并编辑记录支持命令颁发的大多数数据源将命令。 但是，并非所有 ODBC 功能直接都支持数据库类中，因此有时可能需要进行直接 SQL 调用与`ExecuteSQL`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

##  <a name="getbookmarkpersistence"></a>  CDatabase::GetBookmarkPersistence

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
|SQL_BP_CLOSE|书签将变为有效后`Requery`操作。|
|SQL_BP_DELETE|行的书签将变为无效后`Delete`该行上的操作。|
|SQL_BP_DROP|书签将变为有效后`Close`操作。|
|SQL_BP_SCROLL|之后，书签将有效`Move`操作。 这只标识记录集上是否支持书签，正如 `CRecordset::CanBookmark` 返回的值一样。|
|SQL_BP_TRANSACTION|在提交或回滚事务后，书签将变为有效。|
|SQL_BP_UPDATE|行的书签将变为无效后`Update`该行上的操作。|
|SQL_BP_OTHER_HSTMT|与某个记录集对象关联的书签在另一个记录集上有效。|

有关此返回值的详细信息，请参阅 ODBC API 函数`SQLGetInfo`Windows SDK 中。 有关书签的详细信息，请参阅文章[记录集：书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。

##  <a name="getconnect"></a>  CDatabase::GetConnect

调用此成员函数以检索到调用过程中使用的连接字符串`OpenEx`或`Open`连接`CDatabase`到数据源的对象。

```
const CString GetConnect() const;
```

### <a name="return-value"></a>返回值

一个**const**[CString](../../atl-mfc-shared/reference/cstringt-class.md)包含的连接字符串，如果`OpenEx`或`Open`已被调用; 否则为空字符串。

### <a name="remarks"></a>备注

请参阅[CDatabase::Open](#open)有关如何创建连接字符串的说明。

##  <a name="getcursorcommitbehavior"></a>  CDatabase::GetCursorCommitBehavior

调用此成员函数来确定如何[CommitTrans](#committrans)操作会影响上打开记录集对象的游标。

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>返回值

一个值，该值指示打开记录集对象上的事务的效果。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

下表列出了可能的返回值`GetCursorCommitBehavior`和打开记录集上相应的作用。

|返回值|CRecordset 对象上的效果|
|------------------|----------------------------------|
|SQL_CB_CLOSE|调用`CRecordset::Requery`紧跟的事务提交。|
|SQL_CB_DELETE|调用`CRecordset::Close`紧跟的事务提交。|
|SQL_CB_PRESERVE|通常情况下继续进行`CRecordset`操作。|

有关此返回值的详细信息，请参阅 ODBC API 函数`SQLGetInfo`Windows SDK 中。 有关事务的详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。

##  <a name="getcursorrollbackbehavior"></a>  CDatabase::GetCursorRollbackBehavior

调用此成员函数来确定如何[回滚](#rollback)操作会影响上打开记录集对象的游标。

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>返回值

一个值，该值指示打开记录集对象上的事务的效果。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

下表列出了可能的返回值`GetCursorRollbackBehavior`和打开记录集上相应的作用。

|返回值|CRecordset 对象上的效果|
|------------------|----------------------------------|
|SQL_CB_CLOSE|调用`CRecordset::Requery`紧跟在事务回滚。|
|SQL_CB_DELETE|调用`CRecordset::Close`紧跟在事务回滚。|
|SQL_CB_PRESERVE|通常情况下继续进行`CRecordset`操作。|

有关此返回值的详细信息，请参阅 ODBC API 函数`SQLGetInfo`Windows SDK 中。 有关事务的详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。

##  <a name="getdatabasename"></a>  CDatabase::GetDatabaseName

调用此成员函数以检索当前连接的数据库的名称 （前提是数据源定义一个命名的对象称为"数据库"）。

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)包含的数据库名称，如果成功; 否则为一个空`CString`。

### <a name="remarks"></a>备注

这是不与数据源名称 (DSN) 中指定相同`OpenEx`或`Open`调用。 什么`GetDatabaseName`返回依赖于 ODBC。 一般情况下，数据库是一系列表。 如果该实体具有一个名称，`GetDatabaseName`将其返回。

例如，可能想要在标题中显示此名称。 如果从 ODBC，检索的名称时出错`GetDatabaseName`返回一个空`CString`。

##  <a name="isopen"></a>  CDatabase::IsOpen

调用此成员函数以确定是否`CDatabase`对象当前连接到数据源。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果非零`CDatabase`当前连接对象; 否则为 0。

##  <a name="m_hdbc"></a>  CDatabase::m_hdbc

包含的公共句柄 ODBC 数据源连接，"连接句柄。"

### <a name="remarks"></a>备注

通常情况下，便无需直接访问此成员变量。 在调用时，该框架相反，分配句柄`OpenEx`或`Open`。 框架在调用时释放该句柄**删除**运算符`CDatabase`对象。 请注意，`Close`成员函数不释放句柄。

但是，某些情况下，可能需要直接使用的句柄。 例如，如果您需要直接而不是类通过调用 ODBC API 函数`CDatabase`，可能需要连接句柄将作为参数传递。 请参阅下面的代码示例。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

##  <a name="onsetoptions"></a>  CDatabase::OnSetOptions

框架调用此成员函数时直接执行 SQL 语句与`ExecuteSQL`成员函数。

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>参数

*hstmt*<br/>
ODBC 语句句柄设置选项。

### <a name="remarks"></a>备注

`CRecordset::OnSetOptions` 此外会调用此成员函数。

`OnSetOptions` 设置登录超时值。 如果以前调用`SetQueryTimeout`成员函数`OnSetOptions`反映当前的值; 否则，它会设置默认值。

> [!NOTE]
>  在 MFC 4.2 之前`OnSetOptions`还将处理模式设置为任一 snychronous 或异步。 从 MFC 4.2 开始，所有操作都是同步的。 若要执行异步操作，必须进行直接调用 ODBC API 函数`SQLSetPos`。

不需要重写`OnSetOptions`更改超时值。 相反，若要自定义的查询超时值，请调用`SetQueryTimeout`之前创建一个记录集;`OnSetOptions`将使用新值。 设置的值适用于所有记录集或直接 SQL 调用上的后续操作。

重写`OnSetOptions`如果你想要设置其他选项。 重写应调用基类`OnSetOptions`之前或之后调用 ODBC API 函数`SQLSetStmtOption`。 请按照说明中的框架的默认实现的方法`OnSetOptions`。

##  <a name="open"></a>  CDatabase::Open

调用此成员函数以初始化新构造`CDatabase`对象。

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
指定数据源名称，通过 ODBC 管理器计划通过 ODBC 注册的名称。 如果在指定的 DSN 值*lpszConnect* (在窗体"DSN =\<数据源 >")，它必须未中再次指定*lpszDSN*。 在这种情况下， *lpszDSN*应为 NULL。 如果你想要向用户显示数据源对话框中，用户可以在其中选择数据源，否则，可以将传递 NULL。 有关详细信息，请参阅备注。

*bExclusive*<br/>
不支持在此版本的类库。 目前，断言失败时，如果此参数为 TRUE。 总是打开数据源的共享 （非独占）。

*bReadOnly*<br/>
如果你想为只读的并禁止对数据源的更新的连接，则为 TRUE。 所有从属记录集中继承该属性。 默认值是 FALSE。

*lpszConnect*<br/>
指定连接字符串。 连接字符串连接信息，还可能包括数据源名称，在数据源、 用户身份验证字符串 （密码，如果数据源需要一个） 和其他信息有效的用户 ID。 整个连接字符串必须以字符串"ODBC;"为前缀（大写或小写）。 "ODBC"; 使用字符串来表示网络连接到 ODBC 数据源;这是为了向上兼容时类库的未来版本可能支持非 ODBC 数据源。

*bUseCursorLib*<br/>
如果你想要加载 ODBC 游标库 DLL，则为 TRUE。 游标库屏蔽基础 ODBC 驱动程序，有效地阻止动态集的使用 （如果该驱动程序支持它们） 的一些功能。 如果加载游标库支持的唯一游标是静态快照和只进游标。 默认值为 TRUE。 如果你打算创建记录集对象直接从`CRecordset`而无需从其派生，不应加载游标库。

### <a name="return-value"></a>返回值

已成功建立连接; 如果非零值否则为 0，如果用户选择取消时显示对话框，询问有关连接的详细信息。 在所有其他情况下，框架将引发异常。

### <a name="remarks"></a>备注

必须初始化数据库对象，然后才能使用它来构造一个记录集对象。

> [!NOTE]
>  调用[OpenEx](#openex)成员函数是连接到数据源并初始化您的数据库对象的首选的方法。

如果中的参数在`Open`调用不包含足够的信息来建立连接时，ODBC 驱动程序将打开一个对话框，以从用户获取所需的信息。 当您调用`Open`，你的连接字符串， *lpszConnect*，在私下存储`CDatabase`对象，并可通过调用[GetConnect](#getconnect)成员函数。

如果你想在调用之前，则可以打开您自己的对话框`Open`以获取信息从用户，如密码，然后将该信息到连接字符串传递给`Open`。 或者您可能想要节省你将传递，以便您可以重复使用它的下一步的连接字符串的时间应用程序应调用`Open`上`CDatabase`对象。

此外可以针对多个级别的登录名授权使用连接字符串 (每个不同`CDatabase`对象)，或者传递其他数据源特定的信息。 有关连接字符串的详细信息，请参阅 Windows SDK 中第 5 章。

如果 DBMS 主机不可用，，则可以对连接尝试超时。 如果连接尝试失败，`Open`引发`CDBException`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

##  <a name="openex"></a>  不同

调用此成员函数以初始化新构造`CDatabase`对象。

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>参数

*lpszConnectString*<br/>
指定的 ODBC 连接字符串。 这包括数据源名称，以及其他可选信息，例如用户 ID 和密码。 例如，"DSN = SQLServer_Source;UID = SA;PWD = abc123"是可能的连接字符串。 请注意，如果传递 NULL， *lpszConnectString*，数据源对话框会提示用户选择数据源。

*dwOptions*<br/>
一个位掩码，用于指定以下值的组合。 默认值为 0，这意味着，将打开该数据库作为共享具有写访问权限，将不加载 ODBC 游标库 DLL，和 ODBC 连接对话框将显示仅当没有足够的信息来建立连接。

- `CDatabase::openExclusive` 不支持在此版本的类库。 总是打开数据源的共享 （非独占）。 目前，断言失败时，如果指定此选项。

- `CDatabase::openReadOnly` 打开数据源为只读的。

- `CDatabase::useCursorLib` 加载 ODBC 游标库 DLL。 游标库屏蔽基础 ODBC 驱动程序，有效地阻止动态集的使用 （如果该驱动程序支持它们） 的一些功能。 如果加载游标库支持的唯一游标是静态快照和只进游标。 如果你打算创建记录集对象直接从`CRecordset`而无需从其派生，不应加载游标库。

- `CDatabase::noOdbcDialog` 不显示 ODBC 连接对话框中，而不考虑是否提供足够的连接信息。

- `CDatabase::forceOdbcDialog` 始终显示 ODBC 连接对话框。

### <a name="return-value"></a>返回值

已成功建立连接; 如果非零值否则为 0，如果用户选择取消时显示对话框，询问有关连接的详细信息。 在所有其他情况下，框架将引发异常。

### <a name="remarks"></a>备注

必须初始化数据库对象，然后才能使用它来构造一个记录集对象。

如果*lpszConnectString*中的参数在`OpenEx`调用不包含足够的信息来建立连接时，ODBC 驱动程序将打开一个对话框，以从用户获取所需的信息，前提是您不具有设置`CDatabase::noOdbcDialog`或`CDatabase::forceOdbcDialog`中*dwOptions*参数。 当您调用`OpenEx`，你的连接字符串， *lpszConnectString*，在私下存储`CDatabase`对象，并可通过调用[GetConnect](#getconnect)成员函数。

如果你想在调用之前，则可以打开您自己的对话框`OpenEx`从用户，密码，如获取信息并将该信息添加到连接字符串传递给`OpenEx`。 或者您可能想要节省你将传递，以便您可以重复使用它的下一步的连接字符串的时间应用程序应调用`OpenEx`上`CDatabase`对象。

此外可以针对多个级别的登录名授权使用连接字符串 (每个不同`CDatabase`对象)，或者传递其他数据源特定的信息。 有关连接字符串的详细信息，请参阅在第 6 章*ODBC 程序员参考*。

如果 DBMS 主机不可用，，则可以对连接尝试超时。 如果连接尝试失败，`OpenEx`引发`CDBException`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

##  <a name="rollback"></a>  CDatabase::Rollback

调用此成员函数要反转在事务期间所做的更改。

```
BOOL Rollback();
```

### <a name="return-value"></a>返回值

已成功撤消事务; 如果非零值否则为 0。 如果`Rollback`调用失败，数据源和事务状态为未定义。 如果`Rollback`返回 0，必须检查数据源，以确定其状态。

### <a name="remarks"></a>备注

所有`CRecordset` `AddNew`， `Edit`， `Delete`，并`Update`自上次执行的调用[BeginTrans](#begintrans)都会回滚到该调用时存在的状态。

在调用`Rollback`，该事务已结束，并且必须调用`BeginTrans`再次为另一个事务。 您在调用之前的当前记录`BeginTrans`将成为当前记录再次后的`Rollback`。

后回滚时，回滚之前的当前记录保持最新。 有关状态的记录集和回退后的数据源的详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。

### <a name="example"></a>示例

  请参阅文章[事务：在记录集 (ODBC) 执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。

##  <a name="setlogintimeout"></a>  CDatabase::SetLoginTimeout

调用此成员函数，在调用之前`OpenEx`或`Open`-重写的默认秒数之前尝试数据允许源连接将会超时。

```
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>参数

*dwSeconds*<br/>
超时的连接尝试之前允许的秒数。

### <a name="remarks"></a>备注

如果，例如，DBMS 不可用，则连接尝试可能会超时。 调用`SetLoginTimeout`构造未初始化之后`CDatabase`对象，但您拨打电话之前`OpenEx`或`Open`。

登录超时的默认值为 15 秒。 并非所有数据源都支持的功能来指定登录超时值。 如果数据源不支持超时，则会跟踪输出，但不是异常。 值为 0 表示"infinite。

##  <a name="setquerytimeout"></a>  CDatabase::SetQueryTimeout

调用此成员函数以重写默认连接的数据源时因超时的后续操作前允许的秒数。

```
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>参数

*dwSeconds*<br/>
超时之前查询尝试允许的秒数。

### <a name="remarks"></a>备注

由于网络访问权限问题、 过多的查询处理时间等的操作可能会超时。 调用`SetQueryTimeout`在打开记录集之前或在调用记录集的前`AddNew`，`Update`或`Delete`成员函数，如果你想要更改查询超时值。 设置会影响所有后续`Open`， `AddNew`， `Update`，和`Delete`对与此相关联的任何记录集的调用`CDatabase`对象。 打开后更改记录集的查询超时值不会更改该记录集的值。 例如，后续`Move`操作不使用新值。

查询超时的默认值为 15 秒。 并非所有数据源都支持的功能，若要设置查询超时值。 如果设置查询超时值为 0 时，会发生无超时;与数据源之间的通信可能会停止响应。 在开发过程中，此行为可能很有用。 如果数据源不支持超时，则会跟踪输出，但不是异常。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)
