---
title: CDaoDatabase 类
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabase
- AFXDAO/CDaoDatabase
- AFXDAO/CDaoDatabase::CDaoDatabase
- AFXDAO/CDaoDatabase::CanTransact
- AFXDAO/CDaoDatabase::CanUpdate
- AFXDAO/CDaoDatabase::Close
- AFXDAO/CDaoDatabase::Create
- AFXDAO/CDaoDatabase::CreateRelation
- AFXDAO/CDaoDatabase::DeleteQueryDef
- AFXDAO/CDaoDatabase::DeleteRelation
- AFXDAO/CDaoDatabase::DeleteTableDef
- AFXDAO/CDaoDatabase::Execute
- AFXDAO/CDaoDatabase::GetConnect
- AFXDAO/CDaoDatabase::GetName
- AFXDAO/CDaoDatabase::GetQueryDefCount
- AFXDAO/CDaoDatabase::GetQueryDefInfo
- AFXDAO/CDaoDatabase::GetQueryTimeout
- AFXDAO/CDaoDatabase::GetRecordsAffected
- AFXDAO/CDaoDatabase::GetRelationCount
- AFXDAO/CDaoDatabase::GetRelationInfo
- AFXDAO/CDaoDatabase::GetTableDefCount
- AFXDAO/CDaoDatabase::GetTableDefInfo
- AFXDAO/CDaoDatabase::GetVersion
- AFXDAO/CDaoDatabase::IsOpen
- AFXDAO/CDaoDatabase::Open
- AFXDAO/CDaoDatabase::SetQueryTimeout
- AFXDAO/CDaoDatabase::m_pDAODatabase
- AFXDAO/CDaoDatabase::m_pWorkspace
helpviewer_keywords:
- CDaoDatabase [MFC], CDaoDatabase
- CDaoDatabase [MFC], CanTransact
- CDaoDatabase [MFC], CanUpdate
- CDaoDatabase [MFC], Close
- CDaoDatabase [MFC], Create
- CDaoDatabase [MFC], CreateRelation
- CDaoDatabase [MFC], DeleteQueryDef
- CDaoDatabase [MFC], DeleteRelation
- CDaoDatabase [MFC], DeleteTableDef
- CDaoDatabase [MFC], Execute
- CDaoDatabase [MFC], GetConnect
- CDaoDatabase [MFC], GetName
- CDaoDatabase [MFC], GetQueryDefCount
- CDaoDatabase [MFC], GetQueryDefInfo
- CDaoDatabase [MFC], GetQueryTimeout
- CDaoDatabase [MFC], GetRecordsAffected
- CDaoDatabase [MFC], GetRelationCount
- CDaoDatabase [MFC], GetRelationInfo
- CDaoDatabase [MFC], GetTableDefCount
- CDaoDatabase [MFC], GetTableDefInfo
- CDaoDatabase [MFC], GetVersion
- CDaoDatabase [MFC], IsOpen
- CDaoDatabase [MFC], Open
- CDaoDatabase [MFC], SetQueryTimeout
- CDaoDatabase [MFC], m_pDAODatabase
- CDaoDatabase [MFC], m_pWorkspace
ms.assetid: 8ff5b342-964d-449d-bef1-d0ff56aadf6d
ms.openlocfilehash: 683f3f9ebb09d69461e4f9026841363c452f4793
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096163"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase 类

表示使用数据访问对象（DAO）连接到 Access 数据库。 DAO 受 Office 2013 的支持。 DAO 3.6 是最终版本，被视为已过时。

## <a name="syntax"></a>语法

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|构造 `CDaoDatabase` 对象。 调用`Open`将对象连接到数据库。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDaoDatabase::CanTransact](#cantransact)|如果数据库支持事务，则返回非零值。|
|[CDaoDatabase::CanUpdate](#canupdate)|如果`CDaoDatabase`对象可更新（非只读），则返回非零值。|
|[CDaoDatabase::Close](#close)|关闭数据库连接。|
|[CDaoDatabase::Create](#create)|创建基础 DAO 数据库对象并初始化该`CDaoDatabase`对象。|
|[CDaoDatabase::CreateRelation](#createrelation)|定义数据库中的表之间的新关系。|
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|删除保存在数据库的 QueryDefs 集合中的 querydef 对象。|
|[CDaoDatabase::DeleteRelation](#deleterelation)|删除数据库中的表之间的现有关系。|
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|删除数据库中表的定义。 这会删除实际的表及其所有数据。|
|[CDaoDatabase::Execute](#execute)|执行操作查询。 为`Execute`返回结果的查询调用会引发异常。|
|[CDaoDatabase::GetConnect](#getconnect)|返回用于将`CDaoDatabase`对象连接到数据库的连接字符串。 用于 ODBC。|
|[CDaoDatabase::GetName](#getname)|返回当前正在使用的数据库的名称。|
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|返回为数据库定义的查询数。|
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|返回有关在数据库中定义的指定查询的信息。|
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|返回数据库查询操作超时之前的秒数。影响对 ODBC 数据源的所有后续打开、添加、更新和编辑操作以及其他操作（例如`Execute`调用）。|
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|返回受上次更新、编辑或添加操作或通过调用`Execute`影响的记录数。|
|[CDaoDatabase::GetRelationCount](#getrelationcount)|返回数据库中的表之间定义的关系数。|
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|返回有关在数据库中的表之间定义的指定关系的信息。|
|[CDaoDatabase::GetTableDefCount](#gettabledefcount)|返回数据库中定义的表的数目。|
|[CDaoDatabase::GetTableDefInfo](#gettabledefinfo)|返回有关数据库中的指定表的信息。|
|[CDaoDatabase::GetVersion](#getversion)|返回与数据库关联的数据库引擎的版本。|
|[CDaoDatabase::IsOpen](#isopen)|如果`CDaoDatabase`对象当前已连接到数据库，则返回非零值。|
|[CDaoDatabase::Open](#open)|建立与数据库的连接。|
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|设置在多晚时间之后数据库查询操作（仅限 ODBC 数据源）将超时。影响所有后续的已打开、添加、更新和删除操作。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|指向基础 DAO 数据库对象的指针。|
|[CDaoDatabase::m_pWorkspace](#m_pworkspace)|指向[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)对象的指针，该对象包含数据库并定义其事务空间。|

## <a name="remarks"></a>备注

有关支持的数据库格式的信息，请参阅[GetName](../../mfc/reference/cdaoworkspace-class.md#getname)成员函数。 在给定的 "工作区`CDaoDatabase` " 中，可以有一个或多个对象处于活动状态，由[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)对象表示。 工作区维护一组打开的数据库对象，称为数据库集合。

## <a name="usage"></a>用法

创建记录集对象时，可以隐式创建数据库对象。 但您也可以显式创建数据库对象。 若要使用显式`CDaoDatabase`使用现有数据库，请执行以下操作之一：

- 构造一个`CDaoDatabase`对象，并将指针传递到打开的[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)对象。

- 或构造`CDaoDatabase`对象而不指定工作区（MFC 创建一个临时工作区对象）。

若要创建新的 Microsoft Jet （。MDB）数据库中，构造`CDaoDatabase`一个对象并调用其[Create](#create)成员函数。 `Open`不要*在*之后`Create`调用。

若要打开现有数据库，请构造`CDaoDatabase`一个对象并调用其[open](#open)成员函数。

这些方法中的任何一种都将 DAO 数据库对象追加到工作区的数据库集合，并打开与该数据的连接。 然后，在连接的数据库上构造用于操作的[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)、 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)对象时，为这些`CDaoDatabase`对象传递构造函数，以指向对象的指针。 使用完连接后，调用[Close](#close)成员函数并销毁`CDaoDatabase`对象。 `Close`关闭之前未关闭的任何记录集。

## <a name="transactions"></a>事务

在工作区级别提供数据库事务处理-请参阅类`CDaoWorkspace`的[BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans)、 [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans)和[Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback)成员函数。

## <a name="odbc-connections"></a>ODBC 连接

使用 ODBC 数据源的建议方法是将外部表附加到 Microsoft Jet （。MDB）数据库。

## <a name="collections"></a>集合

每个数据库都维护自己的 tabledef、querydef、recordset 和 relation 对象的集合。 类`CDaoDatabase`提供用于处理这些对象的成员函数。

> [!NOTE]
>  这些对象存储在 DAO 中，而不是存储在 MFC 数据库对象中。 MFC 提供 tabledef、querydef 和 recordset 对象的类，而不是用于关系对象的类。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>要求

**标头：** afxdao

##  <a name="cantransact"></a>CDaoDatabase：： CanTransact

调用此成员函数以确定数据库是否允许事务。

```
BOOL CanTransact();
```

### <a name="return-value"></a>返回值

如果数据库支持事务，则为非零值;否则为0。

### <a name="remarks"></a>备注

在数据库的工作区中管理事务。

##  <a name="canupdate"></a>CDaoDatabase：： CanUpdate

调用此成员函数以确定`CDaoDatabase`对象是否允许更新。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>返回值

如果`CDaoDatabase`对象允许更新，则为非零; 否则为0，指示打开`CDaoDatabase`对象时在*bReadOnly*中传递了 TRUE，或者数据库本身是只读的。 请参见[开放式](#open)成员函数。

### <a name="remarks"></a>备注

有关数据库可更新性的信息，请参阅 DAO 帮助中的 "可更新属性" 主题。

##  <a name="cdaodatabase"></a>CDaoDatabase：： CDaoDatabase

构造 `CDaoDatabase` 对象。

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>参数

*pWorkspace*<br/>
指向`CDaoWorkspace`对象的指针，该对象将包含新的数据库对象。 如果接受默认值 NULL，则构造函数将创建一个使用默认`CDaoWorkspace` DAO 工作区的临时对象。 可以通过[m_pWorkspace](#m_pworkspace)数据成员获取指向工作区对象的指针。

### <a name="remarks"></a>备注

构造对象之后，如果要创建新的 Microsoft Jet （。MDB）数据库中，调用对象的[Create](#create)成员函数。 如果要打开现有数据库，请调用对象的[Open](#open)成员函数。

当你完成对象时，应调用其[Close](#close)成员函数，然后销毁`CDaoDatabase`对象。

你可能会发现，在文档类`CDaoDatabase`中嵌入对象会很方便。

> [!NOTE]
>  如果`CDaoDatabase`在不传递指向现有`CDaoDatabase`对象的指针的情况下打开[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象，也会隐式创建一个对象。 关闭 recordset 对象时，将关闭此数据库对象。

##  <a name="close"></a>CDaoDatabase：： Close

调用此成员函数以断开与数据库的连接，并关闭与数据库关联的任何打开的记录集、tabledefs 和 querydefs。

```
virtual void Close();
```

### <a name="remarks"></a>备注

在调用此成员函数之前，最好自行关闭这些对象。 关闭对象会将其从关联[工作区](../../mfc/reference/cdaoworkspace-class.md)中的数据库集合中删除。 `CDaoDatabase` 由于`Close`不会`CDaoDatabase`销毁对象，因此可以通过打开相同的数据库或不同的数据库重用该对象。

> [!CAUTION]
>  在关闭数据库之前，调用[更新](../../mfc/reference/cdaorecordset-class.md#update)成员函数（如果有挂起的`Close`编辑）和所有打开的记录集对象上的成员函数。 如果退出声明堆栈上的[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)或`CDaoDatabase`对象的函数，则数据库将关闭，所有未保存的更改将丢失，所有挂起的事务都将回滚，并且对数据的任何挂起的编辑都将丢失。

> [!CAUTION]
>  如果在任何记录集对象处于打开状态时尝试关闭某个数据库对象，或者如果在打开某个工作区对象的任何数据库对象处于打开状态时尝试关闭该对象，则这些记录集对象将关闭，任何挂起的更新或编辑都将已回滚。 如果尝试在工作区对象的任何数据库对象处于打开状态时将其关闭，则该操作将关闭属于该特定工作区对象的所有数据库对象，这可能会导致关闭的记录集对象处于关闭状态。 如果未关闭数据库对象，则 MFC 会在调试版本中报告断言失败。

如果在函数作用域外定义了数据库对象，并且在不关闭函数的情况下退出函数，则数据库对象将保持打开状态，直到显式关闭或定义它的模块超出范围为止。

##  <a name="create"></a>CDaoDatabase：： Create

若要创建新的 Microsoft Jet （。MDB）数据库，请在构造`CDaoDatabase`对象之后调用此成员函数。

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
字符串表达式，是要创建的数据库文件的名称。 它可以是完整路径和文件名，如 "C：\\\MYDB。MDB "。 必须提供名称。 如果未提供文件扩展名，则为。附加 MDB。 如果你的网络支持统一命名约定（UNC），则还可以指定网络路径，\\例如 "\\\\\\\MYSERVER\\\MYSHARE \MYDIR\\\MYDB"。 仅 Microsoft Jet （。MDB）可以使用此成员函数创建数据库文件。 （字符串文本中需要双反斜杠，因为\\"" 是C++转义符。）

*lpszLocale*<br/>
一个字符串表达式，用于指定用于创建数据库的排序顺序。 默认值为 `dbLangGeneral`。 可能的值有：

- `dbLangGeneral`英语、德语、法语、葡萄牙语、意大利语和新式西班牙语

- `dbLangArabic`阿拉伯语

- `dbLangCyrillic`俄语

- `dbLangCzech`捷克语

- `dbLangDutch`荷兰语

- `dbLangGreek`希腊语

- `dbLangHebrew`希伯来语

- `dbLangHungarian`匈牙利语

- `dbLangIcelandic`冰岛语

- `dbLangNordic`北欧语言（仅适用于 Microsoft Jet 数据库引擎版本1.0）

- `dbLangNorwdan`挪威语和丹麦语

- `dbLangPolish`波兰语

- `dbLangSpanish`传统西班牙语

- `dbLangSwedfin`瑞典语和芬兰语

- `dbLangTurkish`土耳其语

*dwOptions*<br/>
一个整数，指示一个或多个选项。 可能的值有：

- `dbEncrypt`创建加密数据库。

- `dbVersion10`使用 Microsoft Jet 数据库版本1.0 创建数据库。

- `dbVersion11`使用 Microsoft Jet 数据库版本1.1 创建数据库。

- `dbVersion20`使用 Microsoft Jet 数据库版本2.0 创建数据库。

- `dbVersion30`使用 Microsoft Jet 数据库版本3.0 创建数据库。

如果省略加密常量，则会创建未加密的数据库。 只能指定一个版本常量。 如果省略版本常量，则将创建一个使用 Microsoft Jet 数据库版本3.0 的数据库。

> [!CAUTION]
>  如果数据库未加密，即使您实现用户/密码安全，也可能会直接读取构成数据库的二进制磁盘文件。

### <a name="remarks"></a>备注

`Create`创建数据库文件和基础 DAO 数据库对象并初始化该C++对象。 对象将追加到关联的工作区的数据库集合。 数据库对象处于打开状态;不要在之后`Open*` `Create`调用。

> [!NOTE]
>  利用`Create`，你只可以创建 Microsoft Jet （。MDB）数据库。 不能创建 ISAM 数据库或 ODBC 数据库。

##  <a name="createrelation"></a>CDaoDatabase：： CreateRelation

调用此成员函数以建立数据库的主表中的一个或多个字段之间的关系，以及外表中的一个或多个字段（数据库中的另一个表）。

```
void CreateRelation(
    LPCTSTR lpszName,
    LPCTSTR lpszTable,
    LPCTSTR lpszForeignTable,
    long lAttributes,
    LPCTSTR lpszField,
    LPCTSTR lpszForeignField);

void CreateRelation(CDaoRelationInfo& relinfo);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
关系对象的唯一名称。 名称必须以字母开头，并且最多可以包含40个字符。 它可以包含数字和下划线字符，但不能包含标点或空格。

*lpszTable*<br/>
关系中的主表的名称。 如果该表不存在，则 MFC 将引发类型为[CDaoException](../../mfc/reference/cdaoexception-class.md)的异常。

*lpszForeignTable*<br/>
关系中外表的名称。 如果该表不存在，MFC 将引发类型`CDaoException`为的异常。

*lAttributes*<br/>
一个长整型值，该值包含关系类型的相关信息。 您可以使用此值来强制实施引用完整性。 您可以使用按位 "或" 运算符 **&#124;** （）来合并以下任意值（只要组合有意义）：

- `dbRelationUnique`关系为一对一关系。

- `dbRelationDontEnforce`不强制关系（无引用完整性）。

- `dbRelationInherited`关系存在于包含两个附加表的非当前数据库中。

- `dbRelationUpdateCascade`更新将级联（有关级联的详细信息，请参阅备注）。

- `dbRelationDeleteCascade`删除将级联。

*lpszField*<br/>
指向以 null 结尾的字符串的指针，该字符串包含主表（由*lpszTable*命名）中的字段的名称。

*lpszForeignField*<br/>
指向以 null 结尾的字符串的指针，该字符串包含外表（由*lpszForeignTable*命名）中的字段的名称。

*relinfo*<br/>
对[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)对象的引用，该对象包含有关您要创建的关系的信息。

### <a name="remarks"></a>备注

关系不能包含来自外部数据库的查询或附加表。

如果关系涉及两个表中每个表的一个字段，请使用函数的第一个版本。 如果关系涉及多个字段，请使用第二个版本。 关系中的最大字段数为14。

此操作创建基础 DAO 关系对象，但这是 MFC 实现的详细信息，因为关系对象的 MFC 封装包含在类`CDaoDatabase`中。 MFC 不提供关系的类。

如果将关系对象的属性设置为 "激活级联操作"，则在对相关的主键表进行更改时，数据库引擎会自动更新或删除一个或多个其他表中的记录。

例如，假设您在 Customers 表和 Orders 表之间建立了级联删除关系。 删除 Customers 表中的记录时，也会删除与该客户相关的 Orders 表中的记录。 此外，如果您在 Orders 表和其他表之间建立了级联删除关系，则当您从 Customers 表中删除记录时，将自动删除这些表中的记录。

有关相关信息，请参阅 DAO 帮助中的 "CreateRelation 方法" 主题。

##  <a name="deletequerydef"></a>CDaoDatabase：:D eleteQueryDef

调用此成员函数以从`CDaoDatabase`对象的 QueryDefs 集合中删除指定的 querydef （保存的查询）。

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
要删除的已保存查询的名称。

### <a name="remarks"></a>备注

之后，该查询将不再在数据库中定义。

有关创建 querydef 对象的信息，请参阅类[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 构造对象时，querydef 对象将与`CDaoDatabase`特定对象相关联，并向其传递指向数据库对象的指针。 `CDaoQueryDef`

##  <a name="deleterelation"></a>CDaoDatabase：:D eleteRelation

调用此成员函数可删除数据库对象的关系集合中的现有关系。

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
要删除的关系的名称。

### <a name="remarks"></a>备注

之后，关系将不再存在。

有关相关信息，请参阅 DAO 帮助中的 "删除方法" 主题。

##  <a name="deletetabledef"></a>CDaoDatabase：:D eleteTableDef

调用此成员函数可从`CDaoDatabase`对象的 TableDefs 集合中删除指定的表及其所有数据。

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
要删除的 tabledef 的名称。

### <a name="remarks"></a>备注

之后，该数据库中不再定义该表。

> [!NOTE]
>  不要删除系统表。

有关创建 tabledef 对象的信息，请参阅[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)类。 构造对象时，tabledef 对象将与`CDaoDatabase`特定对象相关联，并向其传递指向数据库对象的指针。 `CDaoTableDef`

有关相关信息，请参阅 DAO 帮助中的 "删除方法" 主题。

##  <a name="execute"></a>CDaoDatabase：： Execute

调用此成员函数以运行操作查询，或对数据库执行 SQL 语句。

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>参数

*lpszSQL*<br/>
指向以 null 结尾的字符串的指针，该字符串包含要执行的有效 SQL 命令。

*nOptions*<br/>
一个整数，指定与查询的完整性相关的选项。 您可以使用按位 "或" 运算符 **&#124;** （）来合并以下任何常量（假设组合有意义，例如，您不能将与结合`dbInconsistent`使用`dbConsistent`）：

- `dbDenyWrite`拒绝其他用户的写入权限。

- `dbInconsistent`缺省值不一致的更新。

- `dbConsistent`一致的更新。

- `dbSQLPassThrough`SQL 传递。 导致将 SQL 语句传递到 ODBC 数据源进行处理。

- `dbFailOnError`如果发生错误，则回滚更新。

- `dbSeeChanges`如果另一个用户正在更改您正在编辑的数据，则生成运行时错误。

> [!NOTE]
>  如果同时`dbInconsistent`包含`dbConsistent`和，或者两者都不包括，则结果为默认值。 有关这些常量的说明，请参阅 DAO 帮助中的 "执行方法" 主题。

### <a name="remarks"></a>备注

`Execute`仅适用于不返回结果的操作查询或 SQL 传递查询。 它不适用于返回记录的选择查询。

有关操作查询的定义和信息，请参阅 DAO 帮助中的主题 "操作查询" 和 "执行方法"。

> [!TIP]
>  给定语法正确的 SQL 语句和适当的权限， `Execute`即使不能修改或删除单个行，成员函数也不会失败。 因此， `dbFailOnError` `Execute`使用成员函数运行 update 或 delete 查询时，请始终使用选项。 此选项将导致 MFC 引发[CDaoException](../../mfc/reference/cdaoexception-class.md)类型的异常，并在受影响的任何记录被锁定且无法更新或删除时回滚所有成功的更改。 请注意，你始终可以`GetRecordsAffected`调用来查看受影响的记录数。

调用数据库对象的[GetRecordsAffected](#getrecordsaffected)成员函数，以确定受最近`Execute`调用影响的记录数。 例如， `GetRecordsAffected`返回有关执行操作查询时删除、更新或插入的记录数的信息。 当级联更新或删除有效时，返回的计数不会反映相关表中的更改。

`Execute`不返回记录集。 在`Execute`选择记录的查询上使用将导致 MFC 引发类型`CDaoException`为的异常。 （没有类似于`CDatabase::ExecuteSQL`的成员函数。）`ExecuteSQL`

##  <a name="getconnect"></a>CDaoDatabase：： GetConnect

调用此成员函数以检索用于将`CDaoDatabase`对象连接到 ODBC 或 ISAM 数据库的连接字符串。

```
CString GetConnect();
```

### <a name="return-value"></a>返回值

如果已在 ODBC 数据源上成功调用[Open](#open) ，则为连接字符串;否则为空字符串。 对于 Microsoft Jet （。MDB）数据库，除非您将其设置为与`dbSQLPassThrough`用于[Execute](#execute)成员函数的选项一起使用，或者用于打开记录集，否则字符串始终为空。

### <a name="remarks"></a>备注

该字符串提供有关在传递查询中使用的打开数据库或数据库的源的信息。 连接字符串由数据库类型说明符和零个或多个以分号分隔的参数组成。

> [!NOTE]
>  使用 MFC DAO 类通过 ODBC 连接到数据源比通过附加表进行连接效率更低。

> [!NOTE]
>  连接字符串用于根据需要将附加信息传递给 ODBC 和某些 ISAM 驱动程序。 它不用于。MDB 数据库。 对于 Microsoft Jet 数据库基表，连接字符串是一个空字符串（""），除非将其用于 SQL 传递查询，如以上返回值中所述。

有关如何创建连接字符串的说明，请参阅[Open](#open)成员函数。 在`Open`调用中设置连接字符串后，您可以在以后使用它来检查设置，以确定数据库的类型、路径、用户 ID、密码或 ODBC 数据源。

##  <a name="getname"></a>CDaoDatabase：： GetName

调用此成员函数以检索当前打开的数据库的名称，该名称是现有数据库文件或已注册 ODBC 数据源的名称。

```
CString GetName();
```

### <a name="return-value"></a>返回值

如果成功，则为数据库的完整路径和文件名;否则为空[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>备注

如果你的网络支持统一命名约定（UNC），则还可以指定网络路径，\\例如 "\\\\\\\MYSERVER\\\MYSHARE \MYDIR\\\MYDB。MDB "。 （字符串文本中需要双反斜杠，因为\\"" 是C++转义符。）

例如，您可能希望在标题中显示此名称。 如果在检索名称时出现错误，MFC 将引发类型为[CDaoException](../../mfc/reference/cdaoexception-class.md)的异常。

> [!NOTE]
>  为了在访问外部数据库时获得更好的性能，我们建议将外部数据库表附加到 Microsoft Jet 数据库（。MDB），而不是直接连接到数据源。

数据库类型由路径所指向的文件或目录指示，如下所示：

|路径名指向。|数据库类型|
|--------------------------|-------------------|
|.MDB 文件|Microsoft Jet 数据库（Microsoft Access）|
|包含的目录。DBF 文件|dBASE 数据库|
|包含的目录。XLS 文件|Microsoft Excel 数据库|
|包含的目录。PDX 文件|Paradox 数据库|
|包含格式正确的文本数据库文件的目录|文本格式数据库|

对于 SQL Server 和 Oracle 等 ODBC 数据库，数据库的连接字符串标识由 ODBC 注册的数据源名称（DSN）。

##  <a name="getquerydefcount"></a>CDaoDatabase：： GetQueryDefCount

调用此成员函数以检索在数据库的 QueryDefs 集合中定义的查询数。

```
short GetQueryDefCount();
```

### <a name="return-value"></a>返回值

数据库中定义的查询数。

### <a name="remarks"></a>备注

`GetQueryDefCount`如果需要遍历 QueryDefs 集合中的所有 querydefs，则会很有用。 若要获取集合中给定查询的相关信息，请参阅[GetQueryDefInfo](#getquerydefinfo)。

##  <a name="getquerydefinfo"></a>CDaoDatabase：： GetQueryDefInfo

调用此成员函数可获取有关在数据库中定义的查询的各种信息。

```
void GetQueryDefInfo(
    int nIndex,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetQueryDefInfo(
    LPCTSTR lpszName,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
用于按索引查找的数据库的 QueryDefs 集合中预定义查询的索引。

*querydefinfo*<br/>
对[CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md)对象的引用，该对象返回所请求的信息。

*dwInfoOptions*<br/>
用于指定要检索的记录集的哪些信息的选项。 此处列出了可用的选项，以及它们导致函数返回的有关记录集的内容：

- AFX_DAO_PRIMARY_INFO （默认值） Name，Type

- AFX_DAO_SECONDARY_INFO 主要信息和：创建日期，上次更新日期，返回记录，可更新

- AFX_DAO_ALL_INFO 主要和辅助信息以及：SQL、Connect、ODBCTimeout

*lpszName*<br/>
一个字符串，包含在数据库中定义的查询的名称，用于按名称进行查找。

### <a name="remarks"></a>备注

提供函数的两个版本，以便您可以按数据库的 QueryDefs 集合中的索引或查询的名称来选择查询。

有关*querydefinfo*中返回的信息的说明，请参阅[CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md)结构。 此结构中有与*dwInfoOptions*中的说明中列出的信息项对应的成员。 如果你请求一个级别的信息，也会获得任何以前的信息级别。

##  <a name="getquerytimeout"></a>CDaoDatabase：： GetQueryTimeout

调用此成员函数以检索连接数据库上的后续操作超时之前允许的当前秒数。

```
short GetQueryTimeout();
```

### <a name="return-value"></a>返回值

包含超时值（以秒为单位）的短整型。

### <a name="remarks"></a>备注

由于网络访问问题、过多的查询处理时间等，操作可能会超时。 设置生效时，它会影响对与此`CDaoDatabase`对象关联的任何记录集的所有打开、添加、更新和删除操作。 可以通过调用[SetQueryTimeout](#setquerytimeout)来更改当前超时设置。 在打开后更改记录集的查询超时值不会更改记录集的值。 例如，后续[移动](../../mfc/reference/cdaorecordset-class.md#move)操作不使用新值。 初始化数据库引擎时，最初设置默认值。

查询超时的默认值取自 Windows 注册表。 如果没有注册表设置，则默认值为60秒。 并非所有数据库都支持设置查询超时值的功能。 如果将查询超时值设置为0，则不会发生超时;与数据库的通信可能会停止响应。 在开发过程中，此行为可能会很有用。 如果调用失败，MFC 将引发类型为[CDaoException](../../mfc/reference/cdaoexception-class.md)的异常。

有关相关信息，请参阅 DAO 帮助中的主题 "QueryTimeout 属性"。

##  <a name="getrecordsaffected"></a>CDaoDatabase：： GetRecordsAffected

调用此成员函数来确定受[执行](#execute)成员函数的最近调用影响的记录数。

```
long GetRecordsAffected();
```

### <a name="return-value"></a>返回值

一个长整型，其中包含受影响的记录数。

### <a name="remarks"></a>备注

返回的值包括通过运行`Execute`操作查询所删除、更新或插入的记录数。 当级联更新或删除有效时，返回的计数不会反映相关表中的更改。

有关相关信息，请参阅 DAO 帮助中的主题 "RecordsAffected 属性"。

##  <a name="getrelationcount"></a>CDaoDatabase：： GetRelationCount

调用此成员函数以获取在数据库中的表之间定义的关系数。

```
short GetRelationCount();
```

### <a name="return-value"></a>返回值

数据库中的表之间定义的关系数。

### <a name="remarks"></a>备注

`GetRelationCount`如果需要遍历数据库的关系集合中的所有已定义关系，则此方法很有用。 若要获取有关集合中给定关系的信息，请参阅[GetRelationInfo](#getrelationinfo)。

为了说明关系的概念，请考虑使用 "供应商" 表和 "产品" 表，它可能具有一对多关系。 在此关系中，一个供应商可以提供多个产品。 其他关系是一对一和多对多关系。

##  <a name="getrelationinfo"></a>CDaoDatabase：： GetRelationInfo

调用此成员函数以获取有关数据库的关系集合中的指定关系的信息。

```
void GetRelationInfo(
    int nIndex,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetRelationInfo(
    LPCTSTR lpszName,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
用于按索引查找的数据库的关系集合中关系对象的索引。

*relinfo*<br/>
对[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)对象的引用，该对象返回所请求的信息。

*dwInfoOptions*<br/>
用于指定有关要检索的关系的信息的选项。 此处列出了可用的选项，以及它们导致函数返回的有关关系的内容：

- AFX_DAO_PRIMARY_INFO （默认值）名称、表、外部表

- AFX_DAO_SECONDARY_INFO 属性，字段信息

字段信息是一个[CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md)对象，它包含关系中涉及的主表中的字段。

*lpszName*<br/>
一个包含关系对象名称的字符串，用于按名称进行查找。

### <a name="remarks"></a>备注

此函数的两个版本通过索引或名称提供访问权限。 有关*relinfo*中返回的信息的说明，请参阅[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)结构。 此结构中有与*dwInfoOptions*中的说明中列出的信息项对应的成员。 如果在一个级别请求信息，还可以在任何之前的级别获取信息。

> [!NOTE]
>  如果将关系对象的属性设置为激活级联操作（`dbRelationUpdateCascades`或`dbRelationDeleteCascades`），则当对相关的主键进行更改时，Microsoft Jet 数据库引擎将自动更新或删除一个或多个其他表中的记录张. 例如，假设您在 Customers 表和 Orders 表之间建立了级联删除关系。 删除 Customers 表中的记录时，也会删除与该客户相关的 Orders 表中的记录。 此外，如果您在 Orders 表和其他表之间建立了级联删除关系，则当您从 Customers 表中删除记录时，将自动删除这些表中的记录。

##  <a name="gettabledefcount"></a>CDaoDatabase：： GetTableDefCount

调用此成员函数以检索数据库中定义的表的数目。

```
short GetTableDefCount();
```

### <a name="return-value"></a>返回值

在数据库中定义的 tabledefs 的数目。

### <a name="remarks"></a>备注

`GetTableDefCount`如果需要遍历数据库的 TableDefs 集合中的所有 tabledefs，则此方法很有用。 若要获取有关集合中某个给定表的信息，请参阅[GetTableDefInfo](#gettabledefinfo)。

##  <a name="gettabledefinfo"></a>CDaoDatabase：： GetTableDefInfo

调用此成员函数可获取有关在数据库中定义的表的各种信息。

```
void GetTableDefInfo(
    int nIndex,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetTableDefInfo(
    LPCTSTR lpszName,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
用于按索引查找的数据库的 TableDefs 集合中的 tabledef 对象的索引。

*tabledefinfo*<br/>
对[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)对象的引用，该对象返回所请求的信息。

*dwInfoOptions*<br/>
用于指定要检索的表的哪些信息的选项。 此处列出了可用的选项，以及它们导致函数返回的有关关系的内容：

- AFX_DAO_PRIMARY_INFO （默认值）名称，可更新，特性

- AFX_DAO_SECONDARY_INFO 主要信息和：创建日期，上次更新日期，源表名称，连接

- AFX_DAO_ALL_INFO 主要和辅助信息以及：验证规则，验证文本，记录计数

*lpszName*<br/>
用于按名称查找的 tabledef 对象的名称。

### <a name="remarks"></a>备注

提供函数的两个版本，以便您可以按数据库的 TableDefs 集合中的索引或表的名称选择表。

有关*tabledefinfo*中返回的信息的说明，请参阅[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)结构。 此结构中有与*dwInfoOptions*中的说明中列出的信息项对应的成员。 如果你在一个级别请求信息，则还会获取任何以前的级别的信息。

> [!NOTE]
>  AFX_DAO_ALL_INFO 选项提供了获取速度较慢的信息。 在这种情况下，如果有很多记录，则对表中的记录进行计数可能会非常耗时。

##  <a name="getversion"></a>CDaoDatabase：： GetVersion

调用此成员函数以确定 Microsoft Jet 数据库文件的版本。

```
CString GetVersion();
```

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，指示与对象关联的数据库文件的版本。

### <a name="remarks"></a>备注

返回的值以 "主要. 次要" 格式表示版本号;例如 "3.0"。 产品版本号（例如，3.0）由版本号（3）、句点和发布号（0）组成。 版本截止日期为1.0、1.1、2.0 和3.0。

相关信息，请参阅 DAO 帮助中的 "版本属性" 主题。

##  <a name="isopen"></a>CDaoDatabase：： IsOpen

调用此成员函数以确定`CDaoDatabase`对象当前是否在数据库上打开。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果`CDaoDatabase`对象当前已打开，则为非零; 否则为0。

### <a name="remarks"></a>备注

##  <a name="m_pdaodatabase"></a>CDaoDatabase：： m_pDAODatabase

包含一个指针，该指针指向`CDaoDatabase`对象基础的 DAO 数据库对象的 OLE 接口。

### <a name="remarks"></a>备注

如果需要直接访问 DAO 界面，请使用此指针。

有关直接调用 DAO 的信息，请参阅[技术说明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

##  <a name="m_pworkspace"></a>CDaoDatabase：： m_pWorkspace

包含指向[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)对象的指针，该对象包含数据库对象。

### <a name="remarks"></a>备注

如果需要直接访问工作区，请使用此指针，例如，获取指向工作区的数据库集合中的其他数据库对象的指针。

##  <a name="open"></a>CDaoDatabase：： Open

必须调用此成员函数来初始化表示现有数据库的`CDaoDatabase`新构造对象。

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>参数

*lpszName*<br/>
作为现有 Microsoft Jet （的名称）的名称的字符串表达式。MDB）数据库文件。 如果文件名有扩展名，则它是必需的。 如果你的网络支持统一命名约定（UNC），则还可以指定网络路径，\\例如 "\\\\\\\MYSERVER\\\MYSHARE \MYDIR\\\MYDB。MDB "。 （字符串文本中需要双反斜杠，因为\\"" 是C++转义符。）

使用*lpszName*时需要考虑一些注意事项。 如果是：

- 引用一个数据库，该数据库已由另一个用户打开以进行独占访问，MFC 引发了类型为[CDaoException](../../mfc/reference/cdaoexception-class.md)的异常。 捕获此异常以使用户了解数据库不可用。

- 为空字符串（""），并且*lpszConnect*为 "ODBC;"，则会显示一个对话框，其中列出了所有已注册的 ODBC 数据源名称，以便用户可以选择数据库。 应避免直接连接到 ODBC 数据源;请改用附加表。

- 否则，不引用现有数据库或有效的 ODBC 数据源名称，MFC 将引发类型`CDaoException`为的异常。

> [!NOTE]
>  有关 DAO 错误代码的详细信息，请参阅 DAOERR。H 文件。 有关相关信息，请参阅 DAO 帮助中的 "可捕获的数据访问错误" 主题。

*bExclusive*<br/>
一个布尔值，如果要为独占（非共享）访问打开数据库，则该值为 TRUE; 如果要为共享访问打开数据库，则为 FALSE。 如果省略此参数，则将为共享访问打开数据库。

*bReadOnly*<br/>
一个布尔值，如果要打开数据库以进行只读访问，则为 TRUE; 如果要打开数据库以进行读/写访问，则为 FALSE。 如果省略此参数，则会打开数据库以进行读/写访问。 所有依赖记录集均继承此属性。

*lpszConnect*<br/>
用于打开数据库的字符串表达式。 此字符串构成 ODBC 连接参数。 必须提供独占和只读参数以提供源字符串。 如果数据库是 Microsoft Jet 数据库（。MDB），则此字符串为空（""）。 默认值的语法（ **_T**（""））为 Unicode 以及应用程序的 ANSI 版本提供可移植性。

### <a name="remarks"></a>备注

`Open`将数据库与基础 DAO 对象相关联。 不能使用数据库对象来构造 recordset、tabledef 或 querydef 对象，直到它被初始化。 `Open`将数据库对象追加到关联的工作区的数据库集合。

按如下所示使用参数：

- 如果要打开 Microsoft Jet （。MDB）数据库中，使用*lpszName*参数并为*lpszConnect*参数传递空字符串或传递格式为 ";PWD = password "如果数据库受密码保护（。仅 MDB 数据库）。

- 如果要打开 ODBC 数据源，请在*lpszConnect*中传递有效的 ODBC 连接字符串，并在*lpszName*中传递一个空字符串。

有关相关信息，请参阅 DAO 帮助中的 "OpenDatabase 方法" 主题。

> [!NOTE]
>  为了获得更好的性能，以便在访问外部数据库（包括 ISAM 数据库和 ODBC 数据源）时获得更好的性能，建议将外部数据库表附加到 Microsoft Jet 引擎数据库（。MDB），而不是直接连接到数据源。

例如，如果 DBMS 主机不可用，则连接尝试可能会超时。 如果连接尝试失败， `Open`则会引发类型为[CDaoException](../../mfc/reference/cdaoexception-class.md)的异常。

其余备注仅适用于 ODBC 数据库：

如果数据库是 ODBC 数据库，而您`Open`的调用中的参数未包含足够的信息来建立连接，ODBC 驱动程序将打开一个对话框，以获取用户所需的信息。 当你调用`Open`时，你的连接字符串*lpszConnect*将私下存储，并通过调用[GetConnect](#getconnect)成员函数提供。

如果需要，您可以在调用`Open`以从用户那里获取信息（如密码）之前打开自己的对话框，然后将该信息添加到您传递到`Open`的连接字符串中。 或者，您可能希望保存传递的连接字符串（可能在 Windows 注册表中），以便您可以在下次应用程序调用`Open` `CDaoDatabase`对象时重复使用它。

你还可以将连接字符串用于多个级别的登录授权（每个都用于`CDaoDatabase`不同的对象）或传达其他特定于数据库的信息。

##  <a name="setquerytimeout"></a>CDaoDatabase：： SetQueryTimeout

调用此成员函数以替代连接数据库上的后续操作超时之前允许的默认秒数。

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>参数

*nSeconds*<br/>
查询尝试超时之前允许的秒数。

### <a name="remarks"></a>备注

由于网络访问问题、过多查询处理时间等，操作可能会超时。 如果`SetQueryTimeout`要更改查询超时值，请在打开记录集之前或在调用记录集的[AddNew](../../mfc/reference/cdaorecordset-class.md#addnew)、 [Update](../../mfc/reference/cdaorecordset-class.md#update)或[Delete](../../mfc/reference/cdaorecordset-class.md#delete)成员函数之前调用。 此设置会影响对与此 `CDaoDatabase` 对象关联的任何记录集的所有后续[Open](../../mfc/reference/cdaorecordset-class.md#open)`AddNew`、`Update`、和 `Delete` 和调用。 在打开后更改记录集的查询超时值不会更改记录集的值。 例如，后续[移动](../../mfc/reference/cdaorecordset-class.md#move)操作不使用新值。

查询超时的默认值为60秒。 并非所有数据库都支持设置查询超时值的功能。 如果将查询超时值设置为0，则不会发生超时;与数据库的通信可能会停止响应。 在开发过程中，此行为可能会很有用。

有关相关信息，请参阅 DAO 帮助中的主题 "QueryTimeout 属性"。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDaoWorkspace 类](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDatabase 类](../../mfc/reference/cdatabase-class.md)<br/>
[CDaoException 类](../../mfc/reference/cdaoexception-class.md)
