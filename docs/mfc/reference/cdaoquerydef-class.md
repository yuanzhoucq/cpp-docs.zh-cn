---
title: CDaoQueryDef 类
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDef
- AFXDAO/CDaoQueryDef
- AFXDAO/CDaoQueryDef::CDaoQueryDef
- AFXDAO/CDaoQueryDef::Append
- AFXDAO/CDaoQueryDef::CanUpdate
- AFXDAO/CDaoQueryDef::Close
- AFXDAO/CDaoQueryDef::Create
- AFXDAO/CDaoQueryDef::Execute
- AFXDAO/CDaoQueryDef::GetConnect
- AFXDAO/CDaoQueryDef::GetDateCreated
- AFXDAO/CDaoQueryDef::GetDateLastUpdated
- AFXDAO/CDaoQueryDef::GetFieldCount
- AFXDAO/CDaoQueryDef::GetFieldInfo
- AFXDAO/CDaoQueryDef::GetName
- AFXDAO/CDaoQueryDef::GetODBCTimeout
- AFXDAO/CDaoQueryDef::GetParameterCount
- AFXDAO/CDaoQueryDef::GetParameterInfo
- AFXDAO/CDaoQueryDef::GetParamValue
- AFXDAO/CDaoQueryDef::GetRecordsAffected
- AFXDAO/CDaoQueryDef::GetReturnsRecords
- AFXDAO/CDaoQueryDef::GetSQL
- AFXDAO/CDaoQueryDef::GetType
- AFXDAO/CDaoQueryDef::IsOpen
- AFXDAO/CDaoQueryDef::Open
- AFXDAO/CDaoQueryDef::SetConnect
- AFXDAO/CDaoQueryDef::SetName
- AFXDAO/CDaoQueryDef::SetODBCTimeout
- AFXDAO/CDaoQueryDef::SetParamValue
- AFXDAO/CDaoQueryDef::SetReturnsRecords
- AFXDAO/CDaoQueryDef::SetSQL
- AFXDAO/CDaoQueryDef::m_pDAOQueryDef
- AFXDAO/CDaoQueryDef::m_pDatabase
helpviewer_keywords:
- CDaoQueryDef [MFC], CDaoQueryDef
- CDaoQueryDef [MFC], Append
- CDaoQueryDef [MFC], CanUpdate
- CDaoQueryDef [MFC], Close
- CDaoQueryDef [MFC], Create
- CDaoQueryDef [MFC], Execute
- CDaoQueryDef [MFC], GetConnect
- CDaoQueryDef [MFC], GetDateCreated
- CDaoQueryDef [MFC], GetDateLastUpdated
- CDaoQueryDef [MFC], GetFieldCount
- CDaoQueryDef [MFC], GetFieldInfo
- CDaoQueryDef [MFC], GetName
- CDaoQueryDef [MFC], GetODBCTimeout
- CDaoQueryDef [MFC], GetParameterCount
- CDaoQueryDef [MFC], GetParameterInfo
- CDaoQueryDef [MFC], GetParamValue
- CDaoQueryDef [MFC], GetRecordsAffected
- CDaoQueryDef [MFC], GetReturnsRecords
- CDaoQueryDef [MFC], GetSQL
- CDaoQueryDef [MFC], GetType
- CDaoQueryDef [MFC], IsOpen
- CDaoQueryDef [MFC], Open
- CDaoQueryDef [MFC], SetConnect
- CDaoQueryDef [MFC], SetName
- CDaoQueryDef [MFC], SetODBCTimeout
- CDaoQueryDef [MFC], SetParamValue
- CDaoQueryDef [MFC], SetReturnsRecords
- CDaoQueryDef [MFC], SetSQL
- CDaoQueryDef [MFC], m_pDAOQueryDef
- CDaoQueryDef [MFC], m_pDatabase
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
ms.openlocfilehash: ed298c40daa9485683d0b989e47b97fdce9f6562
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754710"
---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef 类

表示通常保存在数据库中的查询定义（即“querydef”）。

## <a name="syntax"></a>语法

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[道查询Def：：CDaoQueryDef](#cdaoquerydef)|构造 `CDaoQueryDef` 对象。 下一`Open`个电话`Create`或 ，具体取决于您的需要。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDaoQueryDef：附加](#append)|将查询def追加到数据库的 QueryDefs 集合作为保存的查询。|
|[CDaoQueryDef：可以更新](#canupdate)|如果查询可以更新数据库，则返回非零。|
|[CDaoQueryDef：关闭](#close)|关闭查询def对象。 完成后，销毁C++对象。|
|[CDaoQueryDef：创建](#create)|创建基础 DAO 查询def 对象。 将查询def用作临时查询，或调用`Append`将其保存在数据库中。|
|[CDaoQueryDef：执行](#execute)|执行查询def对象定义的查询。|
|[CDaoQueryDef：获取连接](#getconnect)|返回与查询def关联的连接字符串。 连接字符串标识数据源。 （仅适用于 SQL 传递查询;否则为空字符串。|
|[CDaoQueryDef：获取日期创建](#getdatecreated)|返回创建保存的查询的日期。|
|[CDaoQueryDef：获取更新日期](#getdatelastupdated)|返回上次更新保存的查询的日期。|
|[CDaoQueryDef：获取现场计数](#getfieldcount)|返回查询def定义的字段数。|
|[CDaoQueryDef：获取菲尔德信息](#getfieldinfo)|返回有关在查询中定义的指定字段的信息。|
|[CDaoQueryDef：获取名称](#getname)|返回查询def的名称。|
|[CDaoQueryDef：获取ODBC时间](#getodbctimeout)|在执行查询def时返回 ODBC（用于 ODBC 查询）使用的超时值。 这将确定允许查询操作完成的时间。|
|[CDao查询Def：获取参数计数](#getparametercount)|返回为查询定义的参数数。|
|[CDaoQueryDef：获取参数信息](#getparameterinfo)|将有关指定参数的信息返回给查询。|
|[CDaoQueryDef：获取帕拉姆价值](#getparamvalue)|将指定参数的值返回给查询。|
|[CDaoQueryDef：获取受影响的记录](#getrecordsaffected)|返回受操作查询影响的记录数。|
|[CDaoQueryDef：获取退货记录](#getreturnsrecords)|如果查询def 定义的查询返回记录，则返回非零。|
|[CDaoQueryDef：获取SQL](#getsql)|返回指定查询 def 定义的查询的 SQL 字符串。|
|[CDaoQueryDef：获取类型](#gettype)|返回查询类型：删除、更新、追加、制作表等。|
|[CDaoQueryDef：是开放的](#isopen)|如果查询def处于打开状态，则可以执行，则返回非零。|
|[CDaoQueryDef：打开](#open)|打开存储在数据库的 QueryDefs 集合中的现有查询def。|
|[CDaoQueryDef：设置连接](#setconnect)|设置 ODBC 数据源上的 SQL 传递查询的连接字符串。|
|[CDaoQueryDef：set 名称](#setname)|设置保存的查询的名称，在创建查询def时替换正在使用的名称。|
|[CDaoQueryDef：设置ODBC时间](#setodbctimeout)|设置执行查询def时 ODBC（用于 ODBC 查询）使用的超时值。|
|[CDaoQueryDef：setParam值](#setparamvalue)|将指定参数的值设置到查询。|
|[CDao查询Def：设置返回记录](#setreturnsrecords)|指定查询def 是否返回记录。 将此属性设置为 TRUE 仅适用于 SQL 传递查询。|
|[CDao查询Def：SetSQL](#setsql)|设置指定查询 def 定义的查询的 SQL 字符串。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CDaoQueryDef：m_pDAOQueryDef](#m_pdaoquerydef)|指向基础 DAO 查询def 对象的 OLE 接口的指针。|
|[CDaoQueryDef：m_pDatabase](#m_pdatabase)|指向与查询def`CDaoDatabase`关联的对象的指针。 查询def 可能保存在数据库中，也可能不保存在数据库中。|

## <a name="remarks"></a>备注

查询def是一个数据访问对象，它包含描述查询的 SQL 语句及其属性，如"创建日期"和"ODBC 超时"。 您还可以创建临时查询def对象而不保存它们，但将数据库中常用重用的查询保存起来很方便，而且效率更高。 [CDao数据库](../../mfc/reference/cdaodatabase-class.md)对象维护一个集合，称为 QueryDefs 集合，其中包含其保存的查询defs。

> [!NOTE]
> DAO 数据库类不同于基于开放数据库连接 （ODBC） 的 MFC 数据库类。 所有 DAO 数据库类名称都有"CDao"前缀。 您仍可以使用 DAO 类访问 ODBC 数据源。 一般来说，基于 DAO 的 MFC 类比基于 ODBC 的 MFC 类更有能力;基于 DAO 的类可以通过自己的数据库引擎访问数据，包括通过 ODBC 驱动程序。 基于 DAO 的类还支持数据定义语言 （DDL） 操作，例如通过类添加表，而无需直接调用 DAO。

## <a name="usage"></a>使用情况

使用查询def对象处理现有保存的查询或创建新的保存查询或临时查询：

1. 在所有情况下，首先构造一个`CDaoQueryDef`对象，提供指向查询所属的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象的指针。

1. 然后执行以下操作，具体取决于所需内容：

   - 要使用现有的保存查询，请调用查询def对象的[Open](#open)成员函数，提供保存的查询的名称。

   - 要创建新的保存查询，请调用查询def对象的["创建](#create)成员"函数，提供查询的名称。 然后调用[附加程序](#append)，通过将查询追加到数据库的 QueryDefs 集合来保存查询。 `Create`将查询def置于打开状态，因此在调用`Create`后不调用`Open`。

   - 要创建临时查询def，请调用`Create`。 传递查询名称的空字符串。 不要调用 `Append`。

使用查询def对象完成后，调用其 Close 成员函数;当使用查询def对象完成时，调用其[Close](#close)成员函数。然后销毁查询def对象。

> [!TIP]
> 创建保存的查询的最简单方法是使用 Microsoft Access 创建这些查询并将其存储在数据库中。 然后，您可以在 MFC 代码中打开并使用它们。

## <a name="purposes"></a>目的

您可以将查询def对象用于以下任何目的：

- 创建`CDaoRecordset`对象

- 调用对象`Execute`的成员函数直接执行操作查询或 SQL 传递查询

您可以将 querydef 对象用于任何类型的查询，包括选择、操作、交叉表、删除、更新、追加、制作表、数据定义、SQL 传递、联合和批量查询。 查询的类型由您提供的 SQL 语句的内容决定。 有关查询类型的信息，请参阅`Execute`和[GetType](#gettype)成员函数。 记录集通常用于返回行的查询，通常是使用**SELECT 的查询。从**关键字。 `Execute`最常用于批量操作。 有关详细信息，请参阅[执行](#execute)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

## <a name="querydefs-and-recordsets"></a>查询def和记录集

要使用 querydef 对象创建`CDaoRecordset`对象，通常创建或打开查询def，如上文所述。 然后构造一个记录集对象，在调用[CDaoRecordset：：：：打开](../../mfc/reference/cdaorecordset-class.md#open)时，将指针传递给查询def对象。 您传递的查询def必须处于打开状态。 有关详细信息，请参阅类[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

除非记录def 处于打开状态，否则不能使用 querydef 创建记录集（查询def 的最常用用途）。 通过调用 或`Open``Create`将查询def置于打开状态。

## <a name="external-databases"></a>外部数据库

查询def对象是使用外部数据库引擎的本机 SQL 方言的首选方法。 例如，您可以创建 Transact SQL 查询（如在 Microsoft SQL Server 上使用），并将其存储在查询def 对象中。 当您需要不使用不基于 Microsoft Jet 数据库引擎的 SQL 查询时，必须提供指向外部数据源的连接字符串。 具有有效连接字符串的查询绕过数据库引擎，并将查询直接传递到外部数据库服务器进行处理。

> [!TIP]
> 使用 ODBC 表的首选方法是将它们附加到 Microsoft Jet （。MDB）数据库。

有关相关信息，请参阅 DAO SDK 中的"查询Def对象"、"查询Defs集合"和"Cdb数据库对象"的主题。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="cdaoquerydefappend"></a><a name="append"></a>CDaoQueryDef：附加

调用[Create](#create)后调用此成员函数以创建新的查询def对象。

```
virtual void Append();
```

### <a name="remarks"></a>备注

`Append`通过将对象追加到数据库的 QueryDefs 集合，将查询def保存在数据库中。 可以将 querydef 用作临时对象而不附加它，但如果希望它持久化，则必须调用`Append`。

如果尝试追加临时查询def对象，MFC 将引发[CDaoException](../../mfc/reference/cdaoexception-class.md)类型的异常。

## <a name="cdaoquerydefcanupdate"></a><a name="canupdate"></a>CDaoQueryDef：可以更新

调用此成员函数以确定是否可以修改查询def，例如更改其名称或 SQL 字符串。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>返回值

如果允许修改查询def，则非零;否则 0。

### <a name="remarks"></a>备注

您可以修改查询def，如果：

- 它不基于打开只读的数据库。

- 您具有数据库的更新权限。

   这取决于您是否实现了安全功能。 MFC 不提供安全性支持;因此，MFC 不提供安全性支持。您必须通过直接调用 DAO 或使用 Microsoft Access 来实现它。 请参阅 DAO 帮助中的主题"权限属性"。

## <a name="cdaoquerydefcdaoquerydef"></a><a name="cdaoquerydef"></a>道查询Def：：CDaoQueryDef

构造 `CDaoQueryDef` 对象。

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>参数

*p数据库*<br/>
指向打开的[CDao 数据库](../../mfc/reference/cdaodatabase-class.md)对象的指针。

### <a name="remarks"></a>备注

该对象可以表示存储在数据库的 QueryDefs 集合中的现有查询def、要存储在集合中的新查询或不存储的临时查询。 下一步取决于查询def的类型：

- 如果对象表示现有查询def，请调用对象的[Open](#open)成员函数进行初始化。

- 如果对象表示要保存的新查询def，请调用对象的["创建](#create)成员"函数。 这会将对象添加到数据库的 QueryDefs 集合中。 然后调用`CDaoQueryDef`成员函数来设置对象的属性。 最后，调用[附录](#append)。

- 如果对象表示临时查询def（不保存在数据库中），则调用`Create`，传递查询名称的空字符串。 调用`Create`后，通过直接设置查询属性来初始化查询def。 不要调用 `Append`。

要设置查询def的属性，可以使用 SetName、SetSQL、SetConnect、SetODBCTimeout[SetODBCTimeout](#setodbctimeout)和[SetReturn记录](#setreturnsrecords)成员函数。 [SetName](#setname) [SetSQL](#setsql) [SetConnect](#setconnect)

完成查询def对象后，调用其[Close](#close)成员函数。 如果有指向查询def的指针，请使用**delete**运算符销毁C++对象。

## <a name="cdaoquerydefclose"></a><a name="close"></a>CDaoQueryDef：关闭

使用查询def对象完成后，调用此成员函数。

```
virtual void Close();
```

### <a name="remarks"></a>备注

关闭查询def将释放基础 DAO 对象，但不会销毁保存的 DAO 查询def 对象`CDaoQueryDef`或C++对象。 这与[CDaoDatabase：:DeleteQueryDef ）](../../mfc/reference/cdaodatabase-class.md#deletequerydef)不同，后者从 DAO 中的数据库的 QueryDefs 集合中删除查询def（如果不是临时查询def）。

## <a name="cdaoquerydefcreate"></a><a name="create"></a>CDaoQueryDef：创建

调用此成员函数以创建新的保存查询或新的临时查询。

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
保存在数据库中的查询的唯一名称。 有关字符串的详细信息，请参阅 DAO 帮助中的主题"创建查询Def方法"。 如果接受默认值，则为空字符串，将创建临时查询def。 此类查询不会保存在查询 Defs 集合中。

*lpszSQL*<br/>
定义查询的 SQL 字符串。 如果接受默认值 NULL，则必须稍后调用[SetSQL](#setsql)来设置字符串。 在此之前，查询未定义。 但是，您可以使用未定义的查询打开记录集;但是，您可以使用未定义的查询打开记录集。有关详细信息，请参阅备注。 必须先定义 SQL 语句，然后才能将查询def追加到 QueryDefs 集合。

### <a name="remarks"></a>备注

如果在*lpszName*中传递名称，则可以调用[附加程序](#append)以将查询def保存在数据库的 QueryDefs 集合中。 否则，该对象是临时查询def，并且不保存。 在这两种情况下，查询def处于打开状态，您可以使用它创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象或调用查询def的["执行成员"](#execute)函数。

如果不在*lpszSQL*中提供 SQL 语句 ，则无法运行查询，`Execute`但可以使用它创建记录集。 在这种情况下，MFC 使用记录集的默认 SQL 语句。

## <a name="cdaoquerydefexecute"></a><a name="execute"></a>CDaoQueryDef：执行

调用此成员函数以运行由查询def对象定义的查询。

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>参数

*n选项*<br/>
确定查询特征的整数。 有关相关信息，请参阅 DAO 帮助中的主题"执行方法"。 您可以使用位OR运算符 **（&#124;**） 来组合以下参数的常量：

- `dbDenyWrite`拒绝其他用户的写入权限。

- `dbInconsistent`更新不一致。

- `dbConsistent`一致的更新。

- `dbSQLPassThrough`SQL 传递。 使 SQL 语句传递到 ODBC 数据库进行处理。

- `dbFailOnError`默认值。 如果发生错误，回滚更新，并将错误报告给用户。

- `dbSeeChanges`如果其他用户正在更改正在编辑的数据，则生成运行时错误。

> [!NOTE]
> 有关术语"不一致"和"一致"的说明，请参阅 DAO 帮助中的主题"执行方法"。

### <a name="remarks"></a>备注

以这种方式用于执行的 Querydef 对象只能表示以下查询类型之一：

- 操作查询

- SQL 传递查询

`Execute`不适用于返回记录的查询，例如选择查询。 `Execute`通常用于批量操作查询，如**更新**、**插入**、或**SELECT 输入**，或用于数据定义语言 （DDL） 操作。

> [!TIP]
> 使用 ODBC 数据源的首选方法是将表附加到 Microsoft Jet （。MDB）数据库。 有关详细信息，请参阅 DAO 帮助中的主题"使用 DAO 访问外部数据库"。

调用查询def对象的[GetRecords 受影响的](#getrecordsaffected)成员函数，以确定受最近`Execute`调用影响的记录数。 例如，`GetRecordsAffected`返回有关在执行操作查询时删除、更新或插入的记录数的信息。 当级联更新或删除生效时，返回的计数不会反映相关表中的更改。

如果同时`dbInconsistent`包含 和`dbConsistent`，或者如果同时包含两者，则结果为默认值`dbInconsistent`。

`Execute`不返回记录集。 在`Execute`选择记录的查询上使用会导致 MFC 引发[CDaoException](../../mfc/reference/cdaoexception-class.md)类型的异常。

## <a name="cdaoquerydefgetconnect"></a><a name="getconnect"></a>CDaoQueryDef：获取连接

调用此成员函数获取与查询def的数据源关联的连接字符串。

```
CString GetConnect();
```

### <a name="return-value"></a>返回值

包含查询def的连接字符串的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>备注

此功能仅与 ODBC 数据源和某些 ISAM 驱动程序一起使用。 它不与微软 Jet （.MDB）数据库;在这种情况下，`GetConnect`返回一个空字符串。 有关详细信息，请参阅[设置连接](#setconnect)。

> [!TIP]
> 使用 ODBC 表的首选方法是将它们附加到 。MDB 数据库。 有关详细信息，请参阅 DAO 帮助中的主题"使用 DAO 访问外部数据库"。

有关连接字符串的信息，请参阅 DAO 帮助中的主题"连接属性"。

## <a name="cdaoquerydefgetdatecreated"></a><a name="getdatecreated"></a>CDaoQueryDef：获取日期创建

调用此成员函数以获取创建查询def对象的日期。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>返回值

包含创建查询def的日期和时间的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象。

### <a name="remarks"></a>备注

有关相关信息，请参阅 DAO 帮助中的主题"创建日期，上次更新的属性"。

## <a name="cdaoquerydefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoQueryDef：获取更新日期

调用此成员函数以获取查询def对象上次更新的日期 - 更改其任何属性（如其名称、SQL 字符串或连接字符串）的日期。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>返回值

包含查询def上次更新的日期和时间的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象。

### <a name="remarks"></a>备注

有关相关信息，请参阅 DAO 帮助中的主题"创建日期，上次更新的属性"。

## <a name="cdaoquerydefgetfieldcount"></a><a name="getfieldcount"></a>CDaoQueryDef：获取现场计数

调用此成员函数以检索查询中的字段数。

```
short GetFieldCount();
```

### <a name="return-value"></a>返回值

查询中定义的字段数。

### <a name="remarks"></a>备注

`GetFieldCount`可用于循环浏览查询def中的所有字段。 为此，请与`GetFieldCount`[GetFieldInfo](#getfieldinfo)结合使用。

## <a name="cdaoquerydefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoQueryDef：获取菲尔德信息

调用此成员函数以获取有关查询def中定义的字段的各种信息。

```cpp
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
查询def的字段集合中所需字段的零基索引，用于按索引进行查找。

*菲尔德信息*<br/>
对返回请求的信息`CDaoFieldInfo`的对象的引用。

*dwInfoOptions*<br/>
指定要检索的字段的信息的选项。 此处列出了可用的选项以及它们导致函数返回的内容：

- AFX_DAO_PRIMARY_INFO（默认）名称、类型、大小、属性

- AFX_DAO_SECONDARY_INFO主要信息加：序号位置、必需位置、允许零长度、源字段、外名、源表、分门顺序

- AFX_DAO_ALL_INFO主和辅助信息加上：默认值、验证文本、验证规则

*lpsz名称*<br/>
包含所需字段名称的字符串，用于按名称查找。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>备注

有关*在字段信息*中返回的信息的说明，请参阅[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 此结构的成员对应于上面*的 dwInfoOptions*下的描述性信息。 如果您请求一级信息，您也会得到任何以前的信息级别。

## <a name="cdaoquerydefgetname"></a><a name="getname"></a>CDaoQueryDef：获取名称

调用此成员函数以检索查询def 表示的查询的名称。

```
CString GetName();
```

### <a name="return-value"></a>返回值

查询的名称。

### <a name="remarks"></a>备注

查询def名称是唯一的用户定义名称。 有关查询定义名称的详细信息，请参阅 DAO 帮助中的主题"名称属性"。

## <a name="cdaoquerydefgetodbctimeout"></a><a name="getodbctimeout"></a>CDaoQueryDef：获取ODBC时间

调用此成员函数，在对 ODBC 数据源的查询超时之前检索当前时间限制。

```
short GetODBCTimeout();
```

### <a name="return-value"></a>返回值

查询超时前的秒数。

### <a name="remarks"></a>备注

有关此时间限制的信息，请参阅 DAO 帮助中的主题"ODBCTime 属性"。

> [!TIP]
> 使用 ODBC 表的首选方法是将它们附加到 Microsoft Jet （。MDB）数据库。 有关详细信息，请参阅 DAO 帮助中的主题"使用 DAO 访问外部数据库"。

## <a name="cdaoquerydefgetparametercount"></a><a name="getparametercount"></a>CDao查询Def：获取参数计数

调用此成员函数以检索保存的查询中的参数数。

```
short GetParameterCount();
```

### <a name="return-value"></a>返回值

查询中定义的参数数。

### <a name="remarks"></a>备注

`GetParameterCount`可用于循环浏览查询def中的所有参数。 为此，请与`GetParameterCount`[GetparameterInfo](#getparameterinfo)结合使用。

有关相关信息，请参阅 DAO 帮助中的"参数对象"、"参数集合"和"参数声明 （SQL）"主题。

## <a name="cdaoquerydefgetparameterinfo"></a><a name="getparameterinfo"></a>CDaoQueryDef：获取参数信息

调用此成员函数以获取有关查询def中定义的参数的信息。

```cpp
void GetParameterInfo(
    int nIndex,
    CDaoParameterInfo& paraminfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetParameterInfo(
    LPCTSTR lpszName,
    CDaoParameterInfo& paraminfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
查询def参数集合中所需参数的零基索引，用于按索引查找。

*帕拉姆福*<br/>
对返回请求的信息的[CDao 参数Info](../../mfc/reference/cdaoparameterinfo-structure.md)对象的引用。

*dwInfoOptions*<br/>
指定要检索的参数的信息的选项。 此处列出了可用选项以及导致函数返回的内容：

- AFX_DAO_PRIMARY_INFO（默认）名称、类型

*lpsz名称*<br/>
包含所需参数名称的字符串，用于按名称查找。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>备注

有关*在参数信息*中返回的信息的说明，请参阅[CDao 参数信息](../../mfc/reference/cdaoparameterinfo-structure.md)结构。 此结构的成员对应于上面*的 dwInfoOptions*下的描述性信息。

有关相关信息，请参阅 DAO 帮助中的"参数声明 （SQL）"主题。

## <a name="cdaoquerydefgetparamvalue"></a><a name="getparamvalue"></a>CDaoQueryDef：获取帕拉姆价值

调用此成员函数以检索存储在查询def 参数集合中的指定参数的当前值。

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
需要其值的参数的名称，用于按名称查找。

*nIndex*<br/>
查询def参数集合中参数的零基索引，用于按索引查找。 可以通过调用[GetparameterCount](#getparametercount)和[GetparameterInfo](#getparameterinfo)获取此值。

### <a name="return-value"></a>返回值

包含参数值的类[COleVariant](../../mfc/reference/colevariant-class.md)的对象。

### <a name="remarks"></a>备注

您可以按名称或其在集合中的任位位置访问参数。

有关相关信息，请参阅 DAO 帮助中的"参数声明 （SQL）"主题。

## <a name="cdaoquerydefgetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoQueryDef：获取受影响的记录

调用此成员函数以确定受上次调用[执行](#execute)的影响的记录数。

```
long GetRecordsAffected();
```

### <a name="return-value"></a>返回值

受影响的记录数。

### <a name="remarks"></a>备注

当级联更新或删除生效时，返回的计数不会反映相关表中的更改。

有关相关信息，请参阅 DAO 帮助中的主题"记录受影响的属性"。

## <a name="cdaoquerydefgetreturnsrecords"></a><a name="getreturnsrecords"></a>CDaoQueryDef：获取退货记录

调用此成员函数以确定查询def是否基于返回记录的查询。

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>返回值

如果查询def基于返回记录的查询，则非零;否则 0。

### <a name="remarks"></a>备注

此成员函数仅用于 SQL 传递查询。 有关 SQL 查询的详细信息，请参阅[执行](#execute)成员函数。 有关使用 SQL 直通查询的详细信息，请参阅[SetReturnRecords](#setreturnsrecords)成员函数。

有关相关信息，请参阅 DAO 帮助中的主题"返回记录属性"。

## <a name="cdaoquerydefgetsql"></a><a name="getsql"></a>CDaoQueryDef：获取SQL

调用此成员函数以检索定义查询def所基于的查询的 SQL 语句。

```
CString GetSQL();
```

### <a name="return-value"></a>返回值

定义查询def所基于的查询的 SQL 语句。

### <a name="remarks"></a>备注

然后，您可能会解析关键字、表名等的字符串。

有关相关信息，请参阅 DAO 帮助中的"SQL 属性"、"Microsoft Jet 数据库引擎 SQL 和 ANSI SQL 的比较"和"使用代码中的 SQL 查询数据库"的主题。

## <a name="cdaoquerydefgettype"></a><a name="gettype"></a>CDaoQueryDef：获取类型

调用此成员函数以确定查询def的查询类型。

```
short GetType();
```

### <a name="return-value"></a>返回值

查询定义中的查询类型。 有关值，请参阅备注。

### <a name="remarks"></a>备注

查询类型由创建查询def或调用现有查询def的[SetSQL](#setsql)成员函数时在查询def的 SQL 字符串中指定的内容设置。 此函数返回的查询类型可以是以下值之一：

- `dbQSelect`选择

- `dbQAction` 操作

- `dbQCrosstab`交叉选项卡

- `dbQDelete`删除

- `dbQUpdate` Update

- `dbQAppend`附加

- `dbQMakeTable`制作台

- `dbQDDL`数据定义

- `dbQSQLPassThrough`直通

- `dbQSetOperation`联盟

- `dbQSPTBulk``dbQSQLPassThrough`用于指定不返回记录的查询。

> [!NOTE]
> 要创建 SQL 传递查询，请不要设置`dbSQLPassThrough`常量。 当您创建查询def对象并设置连接字符串时，Microsoft Jet 数据库引擎会自动设置此设置。

有关 SQL 字符串的信息，请参阅[GetSQL](#getsql)。 有关查询类型的信息，请参阅[执行](#execute)。

## <a name="cdaoquerydefisopen"></a><a name="isopen"></a>CDaoQueryDef：是开放的

调用此成员函数以确定`CDaoQueryDef`对象当前是否打开。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果对象当前处于`CDaoQueryDef`打开状态，则非零;否则 0。

### <a name="remarks"></a>备注

在使用 querydef 调用[Execute](#execute)或创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象之前，查询def必须处于打开状态。 将查询def放入打开状态调用["创建](#create)"（对于新查询def）或[Open（](#open)对于现有查询def）。

## <a name="cdaoquerydefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoQueryDef：m_pDatabase

包含指向与查询def对象关联的[CDao 数据库](../../mfc/reference/cdaodatabase-class.md)对象的指针。

### <a name="remarks"></a>备注

如果需要直接访问数据库，请使用此指针 ，例如，获取指向数据库集合中其他查询def或记录集对象的指针。

## <a name="cdaoquerydefm_pdaoquerydef"></a><a name="m_pdaoquerydef"></a>CDaoQueryDef：m_pDAOQueryDef

包含指向基础 DAO 查询def 对象的 OLE 接口的指针。

### <a name="remarks"></a>备注

此指针提供是为了与其他类保持完整和一致。 但是，由于 MFC 相当完全封装 DAO 查询defs，因此不太可能需要它。 如果确实使用它，请谨慎操作，特别是，除非您知道自己在做什么，否则不要更改指针的值。

## <a name="cdaoquerydefopen"></a><a name="open"></a>CDaoQueryDef：打开

调用此成员函数以打开以前保存在数据库的 QueryDefs 集合中的查询def。

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
包含要打开的已保存查询def的名称的字符串。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>备注

查询def打开后，可以调用其[执行](#execute)成员函数或使用查询def创建[CDaoRecordset 对象](../../mfc/reference/cdaorecordset-class.md)。

## <a name="cdaoquerydefsetconnect"></a><a name="setconnect"></a>CDaoQueryDef：设置连接

调用此成员函数以设置查询def对象的连接字符串。

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>参数

*lpszConnect*<br/>
包含关联[CDao 数据库](../../mfc/reference/cdaodatabase-class.md)对象的连接字符串的字符串。

### <a name="remarks"></a>备注

连接字符串用于根据需要将其他信息传递给 ODBC 和某些 ISAM 驱动程序。 它不用于微软喷气式飞机 （。MDB）数据库。

> [!TIP]
> 使用 ODBC 表的首选方法是将它们附加到 。MDB 数据库。

在执行表示对 ODBC 数据源的 SQL 传递查询的查询def之前，请设置连接字符串并`SetConnect`调用[SetReturnRecords](#setreturnsrecords)以指定查询是否返回记录。

有关连接字符串结构和连接字符串组件示例的详细信息，请参阅 DAO 帮助中的主题"连接属性"。

## <a name="cdaoquerydefsetname"></a><a name="setname"></a>CDaoQueryDef：set 名称

如果要更改不临时的查询def的名称，请调用此成员函数。

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
包含关联[CDao 数据库](../../mfc/reference/cdaodatabase-class.md)对象中非临时查询的新名称的字符串。

### <a name="remarks"></a>备注

查询def名称是唯一的、用户定义的名称。 您可以在将查询`SetName`def对象追加到查询Defs集合之前进行调用。

## <a name="cdaoquerydefsetodbctimeout"></a><a name="setodbctimeout"></a>CDaoQueryDef：设置ODBC时间

调用此成员函数以在对 ODBC 数据源的查询超时之前设置时间限制。

```cpp
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>参数

*nODBC超时*<br/>
查询超时前的秒数。

### <a name="remarks"></a>备注

此成员函数允许您在连接的数据源"超时"的后续操作之前覆盖默认秒数。 操作可能会由于网络访问问题、查询处理时间过长等原因而超时。 如果要`SetODBCTimeout`更改查询超时值，请在此查询def执行查询之前调用。 （当 ODBC 重用连接时，同一连接上的所有客户端的超时值都相同。

查询超时的默认值为 60 秒。

## <a name="cdaoquerydefsetparamvalue"></a><a name="setparamvalue"></a>CDaoQueryDef：setParam值

调用此成员函数以在运行时在查询def中设置参数的值。

```
virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
要设置其值的参数的名称。

*varValue*<br/>
要设置的值;请参阅备注。

*nIndex*<br/>
参数在查询def的参数集合中的设置位置。 可以通过调用[GetparameterCount](#getparametercount)和[GetparameterInfo](#getparameterinfo)获取此值。

### <a name="remarks"></a>备注

参数必须已作为查询def SQL 字符串的一部分建立。 您可以按名称或其在集合中的任位位置访问参数。

指定要设置为`COleVariant`对象的值。 有关在`COleVariant`对象中设置所需值和类型的信息，请参阅类[COleVariant](../../mfc/reference/colevariant-class.md)。

## <a name="cdaoquerydefsetreturnsrecords"></a><a name="setreturnsrecords"></a>CDao查询Def：设置返回记录

调用此成员函数，作为将 SQL 传递查询设置为外部数据库的过程的一部分。

```cpp
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>参数

*b返回记录*<br/>
如果外部数据库上的查询返回记录，则传递 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

在这种情况下，必须创建查询def并使用其他成员`CDaoQueryDef`函数设置其属性。 有关外部数据库的说明，请参阅[SetConnect](#setconnect)。

## <a name="cdaoquerydefsetsql"></a><a name="setsql"></a>CDao查询Def：SetSQL

调用此成员函数以设置查询def执行的 SQL 语句。

```cpp
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>参数

*lpszSQL*<br/>
包含完整 SQL 语句的字符串，适合执行。 此字符串的语法取决于查询所针对的 DBMS。 有关 Microsoft Jet 数据库引擎中使用的语法的讨论，请参阅 DAO 帮助中的主题"在代码中构建 SQL 语句"。

### <a name="remarks"></a>备注

的典型用途`SetSQL`是设置查询def对象以用于 SQL 传递查询。 （有关目标 DBMS 上的 SQL 传递查询的语法，请参阅 DBMS 的文档。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDao记录组类](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoException 类](../../mfc/reference/cdaoexception-class.md)
