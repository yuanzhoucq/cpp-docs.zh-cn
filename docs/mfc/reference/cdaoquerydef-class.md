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
ms.openlocfilehash: fabb8e957ffaf8ab8d9d57bca8e7835d366ac390
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231814"
---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef 类

表示通常保存在数据库中的查询定义（即“querydef”）。

## <a name="syntax"></a>语法

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|构造 `CDaoQueryDef` 对象。 下一次调用 `Open` 或 `Create` ，具体取决于你的需求。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CDaoQueryDef：： Append](#append)|将 querydef 作为保存的查询追加到数据库的 QueryDefs 集合。|
|[CDaoQueryDef::CanUpdate](#canupdate)|如果查询可以更新数据库，则返回非零值。|
|[CDaoQueryDef：： Close](#close)|关闭 querydef 对象。 在完成 c + + 对象时对其进行销毁。|
|[CDaoQueryDef：： Create](#create)|创建基础 DAO querydef 对象。 使用 querydef 作为临时查询，或调用将 `Append` 其保存在数据库中。|
|[CDaoQueryDef：： Execute](#execute)|执行由 querydef 对象定义的查询。|
|[CDaoQueryDef：： GetConnect](#getconnect)|返回与 querydef 关联的连接字符串。 连接字符串标识数据源。 （仅适用于 SQL 传递查询; 否则为空字符串。）|
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|返回已保存的查询的创建日期。|
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|返回上次更新保存的查询的日期。|
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|返回由 querydef 定义的字段数。|
|[CDaoQueryDef：： Issomapper.getfieldinfo](#getfieldinfo)|返回有关在查询中定义的指定字段的信息。|
|[CDaoQueryDef：： GetName](#getname)|返回 querydef 的名称。|
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|返回在执行 querydef 时 ODBC 使用的超时值（针对 ODBC 查询）。 这将确定允许查询操作完成的时间长度。|
|[CDaoQueryDef：： GetParameterCount](#getparametercount)|返回为查询定义的参数的数目。|
|[CDaoQueryDef：： GetParameterInfo](#getparameterinfo)|返回有关指定参数的查询的信息。|
|[CDaoQueryDef::GetParamValue](#getparamvalue)|返回指定参数到查询的值。|
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|返回受操作查询影响的记录数。|
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|如果由 querydef 定义的查询返回记录，则返回非零值。|
|[CDaoQueryDef::GetSQL](#getsql)|返回指定由 querydef 定义的查询的 SQL 字符串。|
|[CDaoQueryDef：： GetType](#gettype)|返回查询类型：删除、更新、追加、生成表等。|
|[CDaoQueryDef：： IsOpen](#isopen)|如果 querydef 打开并可执行，则返回非零值。|
|[CDaoQueryDef：： Open](#open)|打开数据库的 QueryDefs 集合中存储的现有 querydef。|
|[CDaoQueryDef::SetConnect](#setconnect)|设置 ODBC 数据源上的 SQL 传递查询的连接字符串。|
|[CDaoQueryDef：： SetName](#setname)|设置已保存查询的名称，并替换创建 querydef 时使用的名称。|
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|设置在执行 querydef 时 ODBC 使用的超时值（针对 ODBC 查询）。|
|[CDaoQueryDef::SetParamValue](#setparamvalue)|将指定参数的值设置为查询。|
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|指定 querydef 是否返回记录。 将此特性设置为 TRUE 只对 SQL 传递查询有效。|
|[CDaoQueryDef::SetSQL](#setsql)|设置指定由 querydef 定义的查询的 SQL 字符串。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CDaoQueryDef：： m_pDAOQueryDef](#m_pdaoquerydef)|指向基础 DAO querydef 对象的 OLE 接口的指针。|
|[CDaoQueryDef：： m_pDatabase](#m_pdatabase)|指向 `CDaoDatabase` 与 querydef 关联的对象的指针。 Querydef 可能保存在数据库中。|

## <a name="remarks"></a>备注

Querydef 是一个数据访问对象，其中包含描述查询的 SQL 语句及其属性，如 "创建日期" 和 "ODBC Timeout"。 您还可以创建临时 querydef 对象，而无需保存这些对象，但在数据库中保存经常重复使用的查询非常方便，而且效率更高。 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象维护一个名为 QueryDefs 集合的集合，该集合包含其保存的 QueryDefs。

> [!NOTE]
> DAO 数据库类与基于开放式数据库连接（ODBC）的 MFC 数据库类不同。 所有 DAO 数据库类名称都具有 "CDao" 前缀。 你仍可以使用 DAO 类访问 ODBC 数据源。 通常，基于 DAO 的 MFC 类比基于 ODBC 的 MFC 类更强大;基于 DAO 的类可以通过其自己的数据库引擎来访问数据，包括通过 ODBC 驱动程序。 基于 DAO 的类还支持数据定义语言（DDL）操作，例如通过类添加表，而无需直接调用 DAO。

## <a name="usage"></a>使用情况

使用 querydef 对象可以处理现有的已保存查询，或创建新的已保存查询或临时查询：

1. 在所有情况下，首先构造 `CDaoQueryDef` 对象，并提供指向查询所属的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象的指针。

1. 然后根据需要执行以下操作：

   - 若要使用现有的已保存查询，请调用 querydef 对象的[Open](#open)成员函数，同时提供已保存查询的名称。

   - 若要创建新保存的查询，请调用 querydef 对象的[create](#create)成员函数，同时提供查询的名称。 然后调用[追加](#append)，通过将查询追加到数据库的 QueryDefs 集合来保存查询。 `Create`将 querydef 置于打开状态，因此在调用之后， `Create` 不会调用 `Open` 。

   - 若要创建临时 querydef，请调用 `Create` 。 为查询名称传递一个空字符串。 不要调用 `Append`。

使用 querydef 对象完成后，调用其[Close](#close)成员函数;然后销毁 querydef 对象。

> [!TIP]
> 创建保存的查询的最简单方法是使用 Microsoft Access 创建并将其存储在数据库中。 然后，你可以在 MFC 代码中打开和使用它们。

## <a name="purposes"></a>之

可以将 querydef 对象用于以下任意目的：

- 创建 `CDaoRecordset` 对象

- 调用对象的 `Execute` 成员函数以直接执行操作查询或 SQL 传递查询

您可以将 querydef 对象用于任何类型的查询，包括 select、action、交叉表、删除、更新、追加、生成表、数据定义、SQL 传递、联合和批量查询。 查询的类型取决于提供的 SQL 语句的内容。 有关查询类型的信息，请参阅 `Execute` 和[GetType](#gettype)成员函数。 记录集通常用于返回行的查询，通常是使用**SELECT .。。FROM**关键字。 `Execute`通常用于大容量操作。 有关详细信息，请参阅[Execute](#execute)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

## <a name="querydefs-and-recordsets"></a>Querydefs 和记录集

若要使用 querydef 对象创建 `CDaoRecordset` 对象，通常需要创建或打开一个 querydef，如上所述。 然后，在调用[CDaoRecordset：： Open](../../mfc/reference/cdaorecordset-class.md#open)时构造记录集对象，并将指针传递到 querydef 对象。 传递的 querydef 必须处于打开状态。 有关详细信息，请参阅类[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

不能使用 querydef 创建记录集（querydef 的最常见用途），除非它处于打开状态。 通过调用或，将 querydef 置于打开状态 `Open` `Create` 。

## <a name="external-databases"></a>外部数据库

Querydef 对象是使用外部数据库引擎的本机 SQL 方言的首选方法。 例如，可以创建一个 Transact-sql 查询（在 Microsoft SQL Server 上使用），并将其存储在 querydef 对象中。 如果需要使用不基于 Microsoft Jet 数据库引擎的 SQL 查询，则必须提供指向外部数据源的连接字符串。 使用有效连接字符串的查询将绕过数据库引擎，并将查询直接传递到外部数据库服务器进行处理。

> [!TIP]
> 使用 ODBC 表的首选方法是将它们附加到 Microsoft Jet （。MDB）数据库。

有关相关信息，请参阅 DAO SDK 中的主题 "QueryDef 对象"、"QueryDefs Collection" 和 "CdbDatabase 对象"。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>要求

**标头：** afxdao

## <a name="cdaoquerydefappend"></a><a name="append"></a>CDaoQueryDef：： Append

在调用[create](#create)创建新的 querydef 对象之后调用此成员函数。

```
virtual void Append();
```

### <a name="remarks"></a>备注

`Append`通过将对象追加到数据库的 QueryDefs 集合，将 querydef 保存在数据库中。 您可以使用 querydef 作为临时对象，而无需追加该对象，但如果您想要保留它，则必须调用 `Append` 。

如果尝试追加临时 querydef 对象，MFC 将引发类型为[CDaoException](../../mfc/reference/cdaoexception-class.md)的异常。

## <a name="cdaoquerydefcanupdate"></a><a name="canupdate"></a>CDaoQueryDef::CanUpdate

调用此成员函数以确定是否可以修改 querydef，如更改其名称或 SQL 字符串。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>返回值

如果允许修改 querydef，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果需要，可以修改 querydef：

- 它不基于处于只读状态的数据库。

- 您具有数据库的更新权限。

   这取决于是否已实现安全功能。 MFC 不提供对安全性的支持;您必须通过直接调用 DAO 或使用 Microsoft Access 来实现它。 请参阅 DAO 帮助中的主题 "权限属性"。

## <a name="cdaoquerydefcdaoquerydef"></a><a name="cdaoquerydef"></a>CDaoQueryDef::CDaoQueryDef

构造 `CDaoQueryDef` 对象。

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>参数

*pDatabase*<br/>
指向打开的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象的指针。

### <a name="remarks"></a>备注

对象可以表示存储在数据库的 QueryDefs 集合中的现有 querydef、要存储在集合中的新查询，或不存储的临时查询。 下一步取决于 querydef 的类型：

- 如果对象表示现有的 querydef，请调用对象的[Open](#open)成员函数对其进行初始化。

- 如果对象表示要保存的新 querydef，请调用对象的[Create](#create)成员函数。 这会将对象添加到数据库的 QueryDefs 集合。 然后调用 `CDaoQueryDef` 成员函数以设置该对象的属性。 最后，调用[Append](#append)。

- 如果对象表示临时 querydef （而不是保存在数据库中），请调用 `Create` ，传递查询名称的空字符串。 调用后 `Create` ，通过直接设置其特性来初始化 querydef。 不要调用 `Append`。

若要设置 querydef 的属性，可使用[SetName](#setname)、 [SetSQL](#setsql)、 [SetConnect](#setconnect)、 [SetODBCTimeout](#setodbctimeout)和[SetReturnsRecords](#setreturnsrecords)成员函数。

完成 querydef 对象后，调用其[Close](#close)成员函数。 如果有指向 querydef 的指针，请使用 **`delete`** 运算符销毁 c + + 对象。

## <a name="cdaoquerydefclose"></a><a name="close"></a>CDaoQueryDef：： Close

使用 querydef 对象完成后，调用此成员函数。

```
virtual void Close();
```

### <a name="remarks"></a>备注

关闭 querydef 会释放基础 DAO 对象，但不会销毁保存的 DAO querydef 对象或 c + + `CDaoQueryDef` 对象。 这不同于[CDaoDatabase：:D eletequerydef](../../mfc/reference/cdaodatabase-class.md#deletequerydef)，它将在 DAO （如果不是临时 querydef）中从数据库的 QueryDefs 集合中删除 querydef。

## <a name="cdaoquerydefcreate"></a><a name="create"></a>CDaoQueryDef：： Create

调用此成员函数以创建新保存的查询或新的临时查询。

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
保存在数据库中的查询的唯一名称。 有关字符串的详细信息，请参阅 DAO 帮助中的 "CreateQueryDef 方法" 主题。 如果接受默认值（空字符串），则会创建一个临时 querydef。 此类查询不会保存在 QueryDefs 集合中。

*lpszSQL*<br/>
定义查询的 SQL 字符串。 如果接受默认值 NULL，则以后必须调用[SetSQL](#setsql)来设置字符串。 在此之前，查询未定义。 不过，您可以使用未定义的查询打开记录集;有关详细信息，请参阅备注。 必须先定义 SQL 语句，然后才能将 querydef 追加到 QueryDefs 集合。

### <a name="remarks"></a>备注

如果传递*lpszName*中的名称，则可以调用[Append](#append)将 querydef 保存在数据库的 QueryDefs 集合中。 否则，该对象是临时的 querydef，不会保存。 在任一情况下，querydef 都处于打开状态，可以使用它来创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象，或调用 Querydef 的[Execute](#execute)成员函数。

如果未在*lpszSQL*中提供 SQL 语句，则不能使用运行该查询， `Execute` 但可以使用它来创建记录集。 在这种情况下，MFC 使用记录集的默认 SQL 语句。

## <a name="cdaoquerydefexecute"></a><a name="execute"></a>CDaoQueryDef：： Execute

调用此成员函数以运行由 querydef 对象定义的查询。

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>参数

*nOptions*<br/>
一个整数，它确定查询的特征。 有关相关信息，请参阅 DAO 帮助中的 "执行方法" 主题。 您可以使用按位 "或" 运算符（ **&#124;**）来合并此参数的以下常量：

- `dbDenyWrite`拒绝其他用户的写入权限。

- `dbInconsistent`不一致的更新。

- `dbConsistent`一致的更新。

- `dbSQLPassThrough`SQL 传递。 导致将 SQL 语句传递到 ODBC 数据库进行处理。

- `dbFailOnError`默认值。 如果发生错误，则回滚更新，并向用户报告错误。

- `dbSeeChanges`如果另一个用户正在更改您正在编辑的数据，则生成运行时错误。

> [!NOTE]
> 有关术语 "不一致" 和 "一致" 的说明，请参阅 DAO 帮助中的主题 "Execute 方法"。

### <a name="remarks"></a>备注

用这种方式执行的 Querydef 对象只能表示下列查询类型之一：

- 操作查询

- SQL 传递查询

`Execute`不适用于返回记录的查询，如 select 查询。 `Execute`通常用于大容量操作查询，如**UPDATE**、 **INSERT**或**SELECT INTO**，或用于数据定义语言（DDL）操作。

> [!TIP]
> 使用 ODBC 数据源的首选方法是将表附加到 Microsoft Jet （。MDB）数据库。 有关详细信息，请参阅 DAO 帮助中的 "用 DAO 访问外部数据库" 主题。

调用 querydef 对象的[GetRecordsAffected](#getrecordsaffected)成员函数，以确定受最近调用影响的记录数 `Execute` 。 例如， `GetRecordsAffected` 返回有关执行操作查询时删除、更新或插入的记录数的信息。 当级联更新或删除有效时，返回的计数不会反映相关表中的更改。

如果同时包含 `dbInconsistent` 和 `dbConsistent` ，或者如果不包含，则结果为默认值 `dbInconsistent` 。

`Execute`不返回记录集。 `Execute`在选择记录的查询上使用将导致 MFC 引发类型为[CDaoException](../../mfc/reference/cdaoexception-class.md)的异常。

## <a name="cdaoquerydefgetconnect"></a><a name="getconnect"></a>CDaoQueryDef：： GetConnect

调用此成员函数以获取与 querydef 的数据源关联的连接字符串。

```
CString GetConnect();
```

### <a name="return-value"></a>返回值

包含 querydef 连接字符串的[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="remarks"></a>备注

此函数仅与 ODBC 数据源和某些 ISAM 驱动程序一起使用。 它不用于 Microsoft Jet （。MDB）数据库;在这种情况下， `GetConnect` 将返回一个空字符串。 有关详细信息，请参阅[SetConnect](#setconnect)。

> [!TIP]
> 使用 ODBC 表的首选方法是将它们附加到。MDB 数据库。 有关详细信息，请参阅 DAO 帮助中的 "用 DAO 访问外部数据库" 主题。

有关连接字符串的信息，请参阅 DAO 帮助中的 "连接属性" 主题。

## <a name="cdaoquerydefgetdatecreated"></a><a name="getdatecreated"></a>CDaoQueryDef::GetDateCreated

调用此成员函数可获取 querydef 对象的创建日期。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>返回值

一个包含 querydef 创建日期和时间的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象。

### <a name="remarks"></a>备注

相关信息，请参阅 DAO 帮助中的主题 "DateCreated，LastUpdated Properties"。

## <a name="cdaoquerydefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoQueryDef::GetDateLastUpdated

调用此成员函数可获取 querydef 对象上一次更新的日期（当其任何属性发生更改时），例如其名称、其 SQL 字符串或它的连接字符串。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>返回值

一个[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，它包含 querydef 的上次更新日期和时间。

### <a name="remarks"></a>备注

相关信息，请参阅 DAO 帮助中的主题 "DateCreated，LastUpdated Properties"。

## <a name="cdaoquerydefgetfieldcount"></a><a name="getfieldcount"></a>CDaoQueryDef::GetFieldCount

调用此成员函数以检索查询中的字段数。

```
short GetFieldCount();
```

### <a name="return-value"></a>返回值

在查询中定义的字段数。

### <a name="remarks"></a>备注

`GetFieldCount`适用于遍历 querydef 中的所有字段。 为此，请将 `GetFieldCount` 与[issomapper.getfieldinfo](#getfieldinfo)结合使用。

## <a name="cdaoquerydefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoQueryDef：： Issomapper.getfieldinfo

调用此成员函数可获取有关在 querydef 中定义的字段的各种信息。

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
用于按索引查找的 querydef 字段集合中所需字段的从零开始的索引。

*fieldinfo*<br/>
对 `CDaoFieldInfo` 返回所请求信息的对象的引用。

*dwInfoOptions*<br/>
用于指定要检索的字段信息的选项。 此处列出了可用的选项，以及它们导致函数返回的内容：

- AFX_DAO_PRIMARY_INFO （默认值）名称、类型、大小、属性

- AFX_DAO_SECONDARY_INFO 主要信息加上：序号位置，必需，允许零长度、源字段、外名称、源表、排序顺序

- AFX_DAO_ALL_INFO 主要和辅助信息以及：默认值、验证文本和验证规则

*lpszName*<br/>
一个包含所需字段的名称的字符串，用于按名称进行查找。 可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>备注

有关在*fieldinfo*中返回的信息的说明，请参阅[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 此结构具有与上面*dwInfoOptions*下的描述性信息相对应的成员。 如果你请求一个级别的信息，也会获得任何以前的信息级别。

## <a name="cdaoquerydefgetname"></a><a name="getname"></a>CDaoQueryDef：： GetName

调用此成员函数以检索由 querydef 表示的查询的名称。

```
CString GetName();
```

### <a name="return-value"></a>返回值

查询的名称。

### <a name="remarks"></a>备注

Querydef 名称是用户定义的唯一名称。 有关 querydef 名称的详细信息，请参阅 DAO 帮助中的主题 "名称属性"。

## <a name="cdaoquerydefgetodbctimeout"></a><a name="getodbctimeout"></a>CDaoQueryDef::GetODBCTimeout

调用此成员函数以检索对 ODBC 数据源的查询超时前的当前时间限制。

```
short GetODBCTimeout();
```

### <a name="return-value"></a>返回值

查询超时前等待的秒数。

### <a name="remarks"></a>备注

有关此时间限制的详细信息，请参阅 DAO 帮助中的主题 "ODBCTimeout 属性"。

> [!TIP]
> 使用 ODBC 表的首选方法是将它们附加到 Microsoft Jet （。MDB）数据库。 有关详细信息，请参阅 DAO 帮助中的 "用 DAO 访问外部数据库" 主题。

## <a name="cdaoquerydefgetparametercount"></a><a name="getparametercount"></a>CDaoQueryDef：： GetParameterCount

调用此成员函数以检索已保存查询中的参数的数目。

```
short GetParameterCount();
```

### <a name="return-value"></a>返回值

在查询中定义的参数的数目。

### <a name="remarks"></a>备注

`GetParameterCount`适用于循环遍历 querydef 中的所有参数。 为此，请将 `GetParameterCount` 与[GetParameterInfo](#getparameterinfo)结合使用。

有关相关信息，请参阅 DAO 帮助中的主题 "参数对象"、"Parameters Collection" 和 "PARAMETERS 声明（SQL）"。

## <a name="cdaoquerydefgetparameterinfo"></a><a name="getparameterinfo"></a>CDaoQueryDef：： GetParameterInfo

调用此成员函数以获取关于 querydef 中定义的参数的信息。

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
Querydef 参数集合中所需参数的从零开始的索引，用于按索引查找。

*paraminfo*<br/>
对[CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)对象的引用，该对象返回所请求的信息。

*dwInfoOptions*<br/>
用于指定要检索的参数的哪些信息的选项。 此处列出了可用选项，以及它导致函数返回的内容：

- AFX_DAO_PRIMARY_INFO （默认值）名称、类型

*lpszName*<br/>
包含所需参数名称的字符串，用于按名称进行查找。 可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>备注

有关*paraminfo*中返回的信息的说明，请参阅[CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)结构。 此结构具有与上面*dwInfoOptions*下的描述性信息相对应的成员。

有关相关信息，请参阅 DAO 帮助中的主题 "PARAMETERS 声明（SQL）"。

## <a name="cdaoquerydefgetparamvalue"></a><a name="getparamvalue"></a>CDaoQueryDef::GetParamValue

调用此成员函数以检索存储在 querydef 参数集合中的指定参数的当前值。

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
你需要其值的参数的名称，用于按名称进行查找。

*nIndex*<br/>
用于按索引查找的 querydef 参数集合中的参数的从零开始的索引。 可以通过调用[GetParameterCount](#getparametercount)和[GetParameterInfo](#getparameterinfo)获取此值。

### <a name="return-value"></a>返回值

包含参数值的[COleVariant](../../mfc/reference/colevariant-class.md)类的对象。

### <a name="remarks"></a>备注

可以按名称或按其在集合中的序号位置访问参数。

有关相关信息，请参阅 DAO 帮助中的主题 "PARAMETERS 声明（SQL）"。

## <a name="cdaoquerydefgetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoQueryDef::GetRecordsAffected

调用此成员函数以确定上次[执行](#execute)调用所影响的记录数。

```
long GetRecordsAffected();
```

### <a name="return-value"></a>返回值

受影响的记录数。

### <a name="remarks"></a>备注

当级联更新或删除有效时，返回的计数不会反映相关表中的更改。

有关相关信息，请参阅 DAO 帮助中的主题 "RecordsAffected 属性"。

## <a name="cdaoquerydefgetreturnsrecords"></a><a name="getreturnsrecords"></a>CDaoQueryDef::GetReturnsRecords

调用此成员函数以确定 querydef 是否基于返回记录的查询。

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>返回值

如果 querydef 基于返回记录的查询，则为非零值;否则为0。

### <a name="remarks"></a>备注

此成员函数仅用于 SQL 传递查询。 有关 SQL 查询的详细信息，请参阅[执行](#execute)成员函数。 有关使用 SQL 传递查询的详细信息，请参阅[SetReturnsRecords](#setreturnsrecords)成员函数。

有关相关信息，请参阅 DAO 帮助中的主题 "ReturnsRecords 属性"。

## <a name="cdaoquerydefgetsql"></a><a name="getsql"></a>CDaoQueryDef::GetSQL

调用此成员函数以检索定义 querydef 所基于的查询的 SQL 语句。

```
CString GetSQL();
```

### <a name="return-value"></a>返回值

定义 querydef 所基于的查询的 SQL 语句。

### <a name="remarks"></a>备注

然后，您可能会分析字符串中的关键字、表名等。

有关相关信息，请参阅 DAO 帮助中的 "SQL 属性"、"Microsoft Jet 数据库引擎 SQL 和 ANSI SQL 的比较" 和 "在代码中查询数据库" 主题。

## <a name="cdaoquerydefgettype"></a><a name="gettype"></a>CDaoQueryDef：： GetType

调用此成员函数以确定 querydef 的查询类型。

```
short GetType();
```

### <a name="return-value"></a>返回值

由 querydef 定义的查询的类型。 有关值，请参阅 "备注"。

### <a name="remarks"></a>备注

查询类型是通过创建 querydef 或调用现有 querydef 的[SetSQL](#setsql)成员函数时在 QUERYDEF 的 SQL 字符串中指定的内容来设置的。 此函数返回的查询类型可以是以下值之一：

- `dbQSelect`单击

- `dbQAction` 操作

- `dbQCrosstab`交叉表

- `dbQDelete` 删除

- `dbQUpdate` Update

- `dbQAppend`附加

- `dbQMakeTable`生成表

- `dbQDDL`数据定义

- `dbQSQLPassThrough`传递

- `dbQSetOperation`交集

- `dbQSPTBulk`与结合使用 `dbQSQLPassThrough` 可指定不返回记录的查询。

> [!NOTE]
> 若要创建 SQL 传递查询，请不要设置 `dbSQLPassThrough` 常量。 当你创建 querydef 对象并设置连接字符串时，Microsoft Jet 数据库引擎会自动设置此设置。

有关 SQL 字符串的信息，请参阅[GetSQL](#getsql)。 有关查询类型的信息，请参阅[Execute](#execute)。

## <a name="cdaoquerydefisopen"></a><a name="isopen"></a>CDaoQueryDef：： IsOpen

调用此成员函数以确定 `CDaoQueryDef` 对象当前是否已打开。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果 `CDaoQueryDef` 对象当前已打开，则为非零; 否则为0。

### <a name="remarks"></a>备注

Querydef 必须处于打开状态，然后才能使用它来调用[Execute](#execute)或创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象。 若要将 querydef 置于打开状态呼叫，请[创建](#create)（用于新的 querydef）或[打开](#open)（适用于现有的 querydef）。

## <a name="cdaoquerydefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoQueryDef：： m_pDatabase

包含指向与 querydef 对象关联的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象的指针。

### <a name="remarks"></a>备注

如果需要直接访问数据库，请使用此指针，例如，获取指向数据库集合中其他 querydef 或 recordset 对象的指针。

## <a name="cdaoquerydefm_pdaoquerydef"></a><a name="m_pdaoquerydef"></a>CDaoQueryDef：： m_pDAOQueryDef

包含指向基础 DAO querydef 对象的 OLE 接口的指针。

### <a name="remarks"></a>备注

提供此指针是为了实现与其他类的完整性和一致性。 但是，因为 MFC 会完全封装 DAO querydefs，所以不太可能需要它。 如果使用此方法，则需要谨慎操作，尤其不要更改指针的值，除非您知道您正在执行的操作。

## <a name="cdaoquerydefopen"></a><a name="open"></a>CDaoQueryDef：： Open

调用此成员函数以打开以前保存在数据库的 QueryDefs 集合中的 querydef。

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
一个字符串，包含要打开的已保存的 querydef 的名称。 可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>备注

打开 querydef 后，可以调用其[Execute](#execute)成员函数或使用 Querydef 创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象。

## <a name="cdaoquerydefsetconnect"></a><a name="setconnect"></a>CDaoQueryDef::SetConnect

调用此成员函数以设置 querydef 对象的连接字符串。

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>参数

*lpszConnect*<br/>
一个字符串，其中包含关联的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象的连接字符串。

### <a name="remarks"></a>备注

连接字符串用于根据需要将附加信息传递给 ODBC 和某些 ISAM 驱动程序。 它不用于 Microsoft Jet （。MDB）数据库。

> [!TIP]
> 使用 ODBC 表的首选方法是将它们附加到。MDB 数据库。

在对 ODBC 数据源执行表示 SQL 传递查询的 querydef 之前，请使用设置连接字符串， `SetConnect` 并调用[SetReturnsRecords](#setreturnsrecords)以指定查询是否返回记录。

有关连接字符串的结构和连接字符串组件示例的详细信息，请参阅 DAO 帮助中的 "连接属性" 主题。

## <a name="cdaoquerydefsetname"></a><a name="setname"></a>CDaoQueryDef：： SetName

如果要更改不是临时的 querydef 的名称，请调用此成员函数。

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
一个字符串，其中包含关联的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象中 nontemporary 查询的新名称。

### <a name="remarks"></a>备注

Querydef 名称是用户定义的唯一名称。 在将 `SetName` querydef 对象追加到 QueryDefs 集合之前，可以调用。

## <a name="cdaoquerydefsetodbctimeout"></a><a name="setodbctimeout"></a>CDaoQueryDef::SetODBCTimeout

调用此成员函数可设置对 ODBC 数据源的查询超时前的时间限制。

```cpp
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>参数

*nODBCTimeout*<br/>
查询超时前等待的秒数。

### <a name="remarks"></a>备注

此成员函数可让你覆盖在连接的数据源上的后续操作之前的默认秒数 "超时"。 由于网络访问问题、过多的查询处理时间等，操作可能会超时。 `SetODBCTimeout`如果要更改查询超时值，请在使用此 querydef 执行查询前调用。 （由于 ODBC 重用连接，因此相同连接上的所有客户端的超时值都是相同的。）

查询超时的默认值为60秒。

## <a name="cdaoquerydefsetparamvalue"></a><a name="setparamvalue"></a>CDaoQueryDef::SetParamValue

调用此成员函数可在运行时设置 querydef 中参数的值。

```
virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
要设置其值的参数的名称。

*varValue*<br/>
要设置的值;请参阅 "备注"。

*nIndex*<br/>
Querydef 的 Parameters 集合中参数的序号位置。 可以通过调用[GetParameterCount](#getparametercount)和[GetParameterInfo](#getparameterinfo)获取此值。

### <a name="remarks"></a>备注

该参数必须已建立为 querydef 的 SQL 字符串的一部分。 可以按名称或按其在集合中的序号位置访问参数。

指定要设置为对象的值 `COleVariant` 。 有关在对象中设置所需值和类型的信息 `COleVariant` ，请参阅类[COleVariant](../../mfc/reference/colevariant-class.md)。

## <a name="cdaoquerydefsetreturnsrecords"></a><a name="setreturnsrecords"></a>CDaoQueryDef::SetReturnsRecords

在将 SQL 传递查询设置为外部数据库的过程中，调用此成员函数。

```cpp
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>参数

*bReturnsRecords*<br/>
如果对外部数据库的查询返回记录，则传递 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

在这种情况下，必须创建 querydef 并使用其他成员函数设置其属性 `CDaoQueryDef` 。 有关外部数据库的说明，请参阅[SetConnect](#setconnect)。

## <a name="cdaoquerydefsetsql"></a><a name="setsql"></a>CDaoQueryDef::SetSQL

调用此成员函数可设置 querydef 所执行的 SQL 语句。

```cpp
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>参数

*lpszSQL*<br/>
一个字符串，其中包含适用于执行的完整 SQL 语句。 此字符串的语法取决于查询所针对的 DBMS。 有关 Microsoft Jet 数据库引擎中使用的语法的讨论，请参阅 DAO 帮助中的 "在代码中生成 SQL 语句" 主题。

### <a name="remarks"></a>备注

的典型用法 `SetSQL` 是设置用于 SQL 传递查询的 querydef 对象。 （有关目标 DBMS 上的 SQL 传递查询的语法，请参阅 DBMS 的文档。）

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoException 类](../../mfc/reference/cdaoexception-class.md)
