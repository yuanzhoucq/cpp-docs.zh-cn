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
ms.openlocfilehash: 0fbc4ee3f2033f7507a1ed68493fa7e48bc62c51
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754737"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase 类

表示使用数据访问对象 （DAO） 访问数据库的连接。 通过 Office 2013 支持 DAO。 DAO 3.6 是最终版本，它被视为过时版本。

## <a name="syntax"></a>语法

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[道数据库：：CDao数据库](#cdaodatabase)|构造 `CDaoDatabase` 对象。 调用`Open`以将对象连接到数据库。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDao数据库：：可以](#cantransact)|如果数据库支持事务，则返回非零。|
|[CDao 数据库：：可以更新](#canupdate)|如果`CDaoDatabase`对象是可向上的（不只读的），则返回非零。|
|[CDao 数据库：关闭](#close)|关闭数据库连接。|
|[CDao 数据库：：创建](#create)|创建基础 DAO 数据库对象并初始化该`CDaoDatabase`对象。|
|[CDao 数据库：：创建关系](#createrelation)|在数据库中的表之间定义一个新关系。|
|[CDao数据库：:DeleteQueryDef](#deletequerydef)|删除保存在数据库的 QueryDefs 集合中的查询def对象。|
|[CDao数据库：:Delete关系](#deleterelation)|删除数据库中表之间的现有关系。|
|[CDao数据库：:DeleteTableDef](#deletetabledef)|删除数据库中表的定义。 这将删除实际表及其所有数据。|
|[CDao 数据库：执行](#execute)|执行操作查询。 调用`Execute`返回结果的查询将引发异常。|
|[CDao 数据库：获取连接](#getconnect)|返回用于将`CDaoDatabase`对象连接到数据库的连接字符串。 用于 ODBC。|
|[CDaoDatabase::GetName](#getname)|返回当前正在使用的数据库的名称。|
|[CDao 数据库：：获取查询定义](#getquerydefcount)|返回为数据库定义的查询数。|
|[CDao数据库：：获取查询信息](#getquerydefinfo)|返回有关数据库中定义的指定查询的信息。|
|[CDao 数据库：获取查询超时](#getquerytimeout)|返回数据库查询操作超时后的秒数。影响对 ODBC 数据源（仅）的所有后续打开、添加新、更新和编辑操作以及其他操作，如`Execute`调用。|
|[CDao 数据库：获取受影响的记录](#getrecordsaffected)|返回受上次更新、编辑或添加操作或调用`Execute`的影响的记录数。|
|[CDao 数据库：获取关系计数](#getrelationcount)|返回数据库中表之间定义的关系数。|
|[CDao数据库：获取关系信息](#getrelationinfo)|返回有关数据库中表之间定义的指定关系的信息。|
|[CDao 数据库：获取TableDefCount](#gettabledefcount)|返回数据库中定义的表数。|
|[CDao 数据库：获取桌面信息](#gettabledefinfo)|返回有关数据库中指定表的信息。|
|[CDao 数据库：获取版本](#getversion)|返回与数据库关联的数据库引擎的版本。|
|[CDao 数据库：：是打开的](#isopen)|如果对象当前连接到数据库`CDaoDatabase`，则返回非零。|
|[CDao 数据库：：打开](#open)|建立与数据库的连接。|
|[CDao 数据库：：设置查询超时](#setquerytimeout)|设置数据库查询操作（仅在 ODBC 数据源上）超时后的秒数。影响所有后续打开、添加新操作、更新和删除操作。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CDao数据库：：m_pDAODatabase](#m_pdaodatabase)|指向基础 DAO 数据库对象的指针。|
|[CDao数据库：m_pWorkspace](#m_pworkspace)|指向包含数据库并定义其事务空间的[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)对象的指针。|

## <a name="remarks"></a>备注

有关支持的数据库格式的信息，请参阅[GetName](../../mfc/reference/cdaoworkspace-class.md#getname)成员函数。 您可以在给定的"工作区"`CDaoDatabase`中同时激活一个或多个对象，该对象由[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)对象表示。 工作区维护打开的数据库对象的集合，称为数据库集合。

## <a name="usage"></a>使用情况

在创建记录集对象时，可以隐式创建数据库对象。 但是，您也可以显式创建数据库对象。 要将现有数据库显式使用，`CDaoDatabase`请执行以下任一操作：

- 构造`CDaoDatabase`对象，将指针传递给打开的[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)对象。

- 或者在不指定`CDaoDatabase`工作区的情况下构造对象（MFC 创建临时工作区对象）。

创建新的 Microsoft Jet （.MDB） 数据库，构造`CDaoDatabase`对象并调用其[创建](#create)成员函数。 *不要*在`Open`之后`Create`打电话。

要打开现有数据库，请构造对象`CDaoDatabase`并调用其[Open](#open)成员函数。

这些技术中的任何一种都将 DAO 数据库对象追加到工作区的数据库集合，并打开与数据的连接。 然后构造用于在连接的数据库上操作的[CDaoRecordsetset、CDaoTableDef](../../mfc/reference/cdaorecordset-class.md)或[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)对象时，将这些对象的构造函数传递给对象`CDaoDatabase`。 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) 使用完连接后，调用[Close](#close)成员函数并销毁`CDaoDatabase`对象。 `Close`关闭以前未关闭的任何记录集。

## <a name="transactions"></a>事务

数据库事务`CDaoWorkspace`处理在工作区级别提供 - 请参阅类的[BeginTrans、CommitTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans)和[回滚](../../mfc/reference/cdaoworkspace-class.md#rollback)成员函数。 [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans)

## <a name="odbc-connections"></a>ODBC 连接

使用 ODBC 数据源的建议方法是将外部表附加到 Microsoft Jet （。MDB）数据库。

## <a name="collections"></a>集合

每个数据库都维护自己的表def、查询def、记录集和关系对象的集合。 类`CDaoDatabase`提供用于操作这些对象的成员函数。

> [!NOTE]
> 对象存储在 DAO 中，而不是存储在 MFC 数据库对象中。 MFC 为表def、查询def和记录集对象提供类，但不为关系对象提供类。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="cdaodatabasecantransact"></a><a name="cantransact"></a>CDao数据库：：可以

调用此成员函数以确定数据库是否允许事务。

```
BOOL CanTransact();
```

### <a name="return-value"></a>返回值

如果数据库支持事务，则非零;否则 0。

### <a name="remarks"></a>备注

事务在数据库的工作区中管理。

## <a name="cdaodatabasecanupdate"></a><a name="canupdate"></a>CDao 数据库：：可以更新

调用此成员函数以确定`CDaoDatabase`对象是否允许更新。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>返回值

如果对象允许更新`CDaoDatabase`，则非零;否则 0，指示在打开`CDaoDatabase`对象时在*bReadOnly*中传递 TRUE，或者数据库本身是只读的。 请参阅[打开](#open)成员函数。

### <a name="remarks"></a>备注

有关数据库可备份性的信息，请参阅 DAO 帮助中的主题"可建立属性"。

## <a name="cdaodatabasecdaodatabase"></a><a name="cdaodatabase"></a>道数据库：：CDao数据库

构造 `CDaoDatabase` 对象。

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>参数

*p工作空间*<br/>
指向将包含新`CDaoWorkspace`数据库对象的对象的指针。 如果接受 NULL 的默认值，构造函数将创建一个使用`CDaoWorkspace`默认 DAO 工作区的临时对象。 您可以通过[m_pWorkspace](#m_pworkspace)数据成员获取指向工作区对象的指针。

### <a name="remarks"></a>备注

构造对象后，如果要创建新的 Microsoft Jet （。MDB） 数据库，调用对象的["创建](#create)成员"函数。 相反，如果您正在打开现有数据库，请调用对象的[Open](#open)成员函数。

完成该对象后，应调用其[Close](#close)成员函数，然后销毁该`CDaoDatabase`对象。

您可能会发现将`CDaoDatabase`对象嵌入到文档类中很方便。

> [!NOTE]
> 如果`CDaoDatabase`打开[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象而不将指针传递到现有`CDaoDatabase`对象，则也会隐式创建对象。 关闭记录集对象时，此数据库对象将关闭。

## <a name="cdaodatabaseclose"></a><a name="close"></a>CDao 数据库：关闭

调用此成员函数以断开与数据库的连接，并关闭与数据库关联的任何打开的记录集、表def和查询def。

```
virtual void Close();
```

### <a name="remarks"></a>备注

最好在调用此成员函数之前自行关闭这些对象。 关闭`CDaoDatabase`对象会将其从关联的[工作区](../../mfc/reference/cdaoworkspace-class.md)中的"数据库"集合中删除。 因为`Close`不会破坏`CDaoDatabase`对象，因此可以通过打开同一数据库或其他数据库来重用该对象。

> [!CAUTION]
> 在关闭数据库之前，调用[Update](../../mfc/reference/cdaorecordset-class.md#update)成员函数（如果有挂起的`Close`编辑）和所有打开的记录集对象上的成员函数。 如果退出声明[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)或`CDaoDatabase`堆栈上的对象的函数，数据库将关闭，任何未保存的更改都将丢失，所有挂起的事务都将回滚，并且对数据的任何挂起编辑都将丢失。

> [!CAUTION]
> 如果在打开任何记录集对象时尝试关闭数据库对象，或者尝试关闭工作区对象，而属于该特定工作区的任何数据库对象处于打开状态，则这些记录集对象将关闭，任何挂起的更新或编辑都将回滚。 如果尝试在属于工作区对象的任何数据库对象打开时关闭工作区对象，则操作将关闭属于该特定工作区对象的所有数据库对象，这可能会导致关闭未关闭的记录集对象。 如果不关闭数据库对象，MFC 将报告调试生成中的断言失败。

如果数据库对象是在函数范围之外定义的，并且在不关闭该函数的情况下退出该函数，则数据库对象将保持打开状态，直到显式关闭或定义该对象的模块超出范围。

## <a name="cdaodatabasecreate"></a><a name="create"></a>CDao 数据库：：创建

创建新的 Microsoft Jet （.MDB） 数据库，在构造`CDaoDatabase`对象后调用此成员函数。

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
字符串表达式，它是要创建的数据库文件的名称。 它可以是完整的路径和文件名，如"C：\MYDB"。\\MDB"。 您必须提供名称。 如果不提供文件名扩展名， .MDB 被追加。 如果您的网络支持统一的命名约定 （UNC），您还可以指定网络路径，例如"_MYSERVER\\\\\\\\_MYSHARE _MYDIR\\\\_MYDB"。 只有微软喷气机 （.可以使用此成员函数创建 MDB）数据库文件。 （字符串文本中需要双背斜杠，因为""\\是C++转义字符。

*lpszLocale*<br/>
用于指定用于创建数据库的整理顺序的字符串表达式。 默认值为 `dbLangGeneral`。 可能的值包括：

- `dbLangGeneral`英语、德语、法语、葡萄牙语、意大利语和现代西班牙语

- `dbLangArabic`阿拉伯语

- `dbLangCyrillic`俄语

- `dbLangCzech`捷克语

- `dbLangDutch`荷兰语

- `dbLangGreek`希腊语

- `dbLangHebrew`希伯来语

- `dbLangHungarian`匈牙利语

- `dbLangIcelandic`冰岛语

- `dbLangNordic`北欧语言（仅限 Microsoft Jet 数据库引擎版本 1.0）

- `dbLangNorwdan`挪威语和丹麦语

- `dbLangPolish`波兰语

- `dbLangSpanish`传统西班牙语

- `dbLangSwedfin`瑞典语和芬兰语

- `dbLangTurkish`土耳其语

*dwOptions*<br/>
指示一个或多个选项的整数。 可能的值包括：

- `dbEncrypt`创建加密数据库。

- `dbVersion10`使用 Microsoft Jet 数据库版本 1.0 创建数据库。

- `dbVersion11`使用 Microsoft Jet 数据库版本 1.1 创建数据库。

- `dbVersion20`使用 Microsoft Jet 数据库版本 2.0 创建数据库。

- `dbVersion30`使用 Microsoft Jet 数据库版本 3.0 创建数据库。

如果省略加密常量，将创建未加密的数据库。 只能指定一个版本常量。 如果省略版本常量，将创建使用 Microsoft Jet 数据库版本 3.0 的数据库。

> [!CAUTION]
> 如果数据库未加密，即使您实现了用户/密码安全性，也可以直接读取构成数据库的二进制磁盘文件。

### <a name="remarks"></a>备注

`Create`创建数据库文件和基础 DAO 数据库对象并初始化C++对象。 该对象将追加到关联的工作区的"数据库"集合中。 数据库对象处于打开状态;不要在`Open*`之后`Create`调用 。

> [!NOTE]
> 使用`Create`时，只能创建 Microsoft Jet （。MDB）数据库。 您不能创建 ISAM 数据库或 ODBC 数据库。

## <a name="cdaodatabasecreaterelation"></a><a name="createrelation"></a>CDao 数据库：：创建关系

调用此成员函数以建立数据库中主表中的一个或多个字段与外表中的一个或多个字段（数据库中的另一个表）之间的关系。

```cpp
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

*lpsz名称*<br/>
关系对象的唯一名称。 名称必须以字母开头，最多只能包含 40 个字符。 它可以包括数字和下划线字符，但不能包括标点符号或空格。

*lpszTable*<br/>
关系中主表的名称。 如果表不存在，MFC 将引发[CDaoException](../../mfc/reference/cdaoexception-class.md)类型的异常。

*lpsz 外表*<br/>
关系中的外表的名称。 如果表不存在，MFC 将引发类型`CDaoException`异常。

*l 属性*<br/>
包含有关关系类型的信息的长值。 除其他事项外，可以使用此值强制实施引用完整性。 您可以使用位-OR 运算符 **（&#124;**） 组合以下任一值（只要组合有意义）：

- `dbRelationUnique`关系是一对一的。

- `dbRelationDontEnforce`不强制执行关系（没有引用完整性）。

- `dbRelationInherited`关系存在于包含两个附加表的非当前数据库中。

- `dbRelationUpdateCascade`更新将级联（有关级联的详细信息，请参阅备注）。

- `dbRelationDeleteCascade`删除将级联。

*lpszField*<br/>
指向 null 端接字符串的指针，其中包含主表中字段的名称（由*lpszTable*命名）。

*lpsz外国场*<br/>
指向空端结束的字符串的指针，其中包含外表中字段的名称（由*lpsz外表*命名）。

*雷利福*<br/>
对包含要创建关系的信息的[CDao 关系信息](../../mfc/reference/cdaorelationinfo-structure.md)对象的引用。

### <a name="remarks"></a>备注

关系不能涉及来自外部数据库的查询或附加表。

当关系涉及两个表中每个表中的一个字段时，请使用函数的第一个版本。 当关系涉及多个字段时，请使用第二个版本。 关系中的最大字段数为 14。

此操作创建一个基础 DAO 关系对象，但这是 MFC 实现的详细信息，因为 MFC 对关系对象的封装包含在类`CDaoDatabase`中。 MFC 不为关系提供类。

如果将关系对象的属性设置为激活级联操作，则数据库引擎在更改相关主键表时会自动更新或删除一个或多个其他表中的记录。

例如，假设您在客户表和订单表之间建立级联删除关系。 从"客户"表中删除记录时，"订单"表中与该客户相关的记录也会被删除。 此外，如果在"订单"表和其他表之间建立级联删除关系，则当您从"客户"表中删除记录时，将自动删除这些表中的记录。

有关相关信息，请参阅 DAO 帮助中的主题"创建关系方法"。

## <a name="cdaodatabasedeletequerydef"></a><a name="deletequerydef"></a>CDao数据库：:DeleteQueryDef

调用此成员函数从`CDaoDatabase`对象的 QueryDefs 集合中删除指定的查询def - 保存的查询。

```cpp
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
要删除的已保存查询的名称。

### <a name="remarks"></a>备注

之后，不再在数据库中定义该查询。

有关创建查询定义对象的信息，请参阅类[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 构造对象时，查询def对象将变为`CDaoDatabase`与特定对象关联，`CDaoQueryDef`将该对象传递给数据库对象的指针。

## <a name="cdaodatabasedeleterelation"></a><a name="deleterelation"></a>CDao数据库：:Delete关系

调用此成员函数从数据库对象的"关系"集合中删除现有关系。

```cpp
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
要删除的关系的名称。

### <a name="remarks"></a>备注

之后，关系不再存在。

有关相关信息，请参阅 DAO 帮助中的主题"删除方法"。

## <a name="cdaodatabasedeletetabledef"></a><a name="deletetabledef"></a>CDao数据库：:DeleteTableDef

调用此成员函数从`CDaoDatabase`对象的 TableDefs 集合中删除指定的表及其所有数据。

```cpp
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
要删除的表def的名称。

### <a name="remarks"></a>备注

之后，该表不再在数据库中定义。

> [!NOTE]
> 非常小心不要删除系统表。

有关创建表def对象的信息，请参阅类[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)。 当您构造对象，将指向数据库对象的指针`CDaoDatabase`传递给该对象时，`CDaoTableDef`表def对象将变为与特定对象关联。

有关相关信息，请参阅 DAO 帮助中的主题"删除方法"。

## <a name="cdaodatabaseexecute"></a><a name="execute"></a>CDao 数据库：执行

调用此成员函数以在数据库上运行操作查询或执行 SQL 语句。

```cpp
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>参数

*lpszSQL*<br/>
指向包含要执行的有效 SQL 命令的 null 端接字符串的指针。

*n选项*<br/>
指定与查询完整性相关的选项的整数。 您可以使用位OR运算符 **（&#124;**） 组合以下任一常量（前提是组合有意义 - 例如，您不会与`dbInconsistent``dbConsistent`组合使用 。

- `dbDenyWrite`拒绝其他用户的写入权限。

- `dbInconsistent`（默认）更新不一致。

- `dbConsistent`一致的更新。

- `dbSQLPassThrough`SQL 传递。 使 SQL 语句传递到 ODBC 数据源进行处理。

- `dbFailOnError`如果发生错误，回滚更新。

- `dbSeeChanges`如果其他用户正在更改正在编辑的数据，则生成运行时错误。

> [!NOTE]
> 如果两`dbInconsistent`者`dbConsistent`都包括在内，或者两者都包括在内，则结果为默认值。 有关这些常量的说明，请参阅 DAO 帮助中的主题"执行方法"。

### <a name="remarks"></a>备注

`Execute`仅适用于不返回结果的操作查询或 SQL 传递查询。 它不适用于返回记录的选定查询。

有关操作查询的定义和信息，请参阅 DAO 帮助中的"操作查询"和"执行方法"主题。

> [!TIP]
> 给定语法上正确的 SQL 语句和适当的权限，即使`Execute`无法修改或删除单个行，成员函数也不会失败。 因此，在使用成员`dbFailOnError`函数运行更新或删除`Execute`查询时，始终使用 选项。 此选项会导致 MFC 引发[CDaoException](../../mfc/reference/cdaoexception-class.md)类型的异常，并在任何受影响的记录被锁定且无法更新或删除时回滚所有成功更改。 请注意，您可以随时调用`GetRecordsAffected`以查看受影响的记录数。

调用数据库对象的[GetRecords 受影响的](#getrecordsaffected)成员函数，以确定受最近`Execute`调用影响的记录数。 例如，`GetRecordsAffected`返回有关在执行操作查询时删除、更新或插入的记录数的信息。 当级联更新或删除生效时，返回的计数不会反映相关表中的更改。

`Execute`不返回记录集。 在`Execute`选择记录的查询上使用会导致 MFC 引发类型`CDaoException`异常。 （没有`ExecuteSQL`类似于`CDatabase::ExecuteSQL`的成员函数。

## <a name="cdaodatabasegetconnect"></a><a name="getconnect"></a>CDao 数据库：获取连接

调用此成员函数以检索用于将`CDaoDatabase`对象连接到 ODBC 或 ISAM 数据库的连接字符串。

```
CString GetConnect();
```

### <a name="return-value"></a>返回值

如果在 ODBC 数据源上成功调用 Open 的连接字符串;如果已在 ODBC 数据源上成功调用[Open，](#open)则连接字符串。否则，一个空字符串。 对于微软喷气式飞机 （.MDB） 数据库，字符串始终为空，除非您将其设置为与[执行](#execute)成员函数`dbSQLPassThrough`一起使用或用于打开记录集的选项。

### <a name="remarks"></a>备注

该字符串提供有关在传递查询中使用的开放数据库或数据库的来源的信息。 连接字符串由数据库类型指定器和零个或多个参数组成，这些参数由分号分隔。

> [!NOTE]
> 使用 MFC DAO 类通过 ODBC 连接到数据源的效率低于通过附加表进行连接的效率。

> [!NOTE]
> 连接字符串用于根据需要将其他信息传递给 ODBC 和某些 ISAM 驱动程序。 它不用于 。MDB 数据库。 对于 Microsoft Jet 数据库基表，连接字符串是一个空字符串 （""），除非将其用于 SQL 传递查询，如上面的返回值所述。

有关如何创建连接字符串的说明，请参阅[Open](#open)成员函数。 在`Open`调用中设置连接字符串后，以后可以使用它检查设置以确定数据库的类型、路径、用户 ID、密码或 ODBC 数据源。

## <a name="cdaodatabasegetname"></a><a name="getname"></a>CDao 数据库：获取名称

调用此成员函数以检索当前打开的数据库的名称，该数据库是现有数据库文件的名称或已注册的 ODBC 数据源的名称。

```
CString GetName();
```

### <a name="return-value"></a>返回值

数据库的完整路径和文件名（如果成功）;否则，空[的 CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>备注

如果您的网络支持统一的命名约定 （UNC），您还可以\\\\\\指定网络路径，例如，"[MYSERVER\\]MYSHARE \MYDIR\\\\_MYDB。MDB"。 （字符串文本中需要双背斜杠，因为""\\是C++转义字符。

例如，您可能希望在标题中显示此名称。 如果在检索名称时发生错误，MFC 将引发[CDaoException](../../mfc/reference/cdaoexception-class.md)类型的异常。

> [!NOTE]
> 为了在访问外部数据库时获得更好的性能，我们建议您将外部数据库表附加到 Microsoft Jet 数据库 （。MDB），而不是直接连接到数据源。

数据库类型由路径指向的文件或目录指示，如下所示：

|路径名称指向.|数据库类型|
|--------------------------|-------------------|
|.MDB 文件|微软喷气数据库（微软访问）|
|包含 的目录。DBF 文件|dBASE 数据库|
|包含 的目录。XLS 文件|微软Excel数据库|
|包含 的目录。PDX 文件|悖论数据库|
|包含适当格式的文本数据库文件的目录|文本格式数据库|

对于 ODBC 数据库（如 SQL Server 和 Oracle），数据库的连接字符串标识由 ODBC 注册的数据源名称 （DSN）。

## <a name="cdaodatabasegetquerydefcount"></a><a name="getquerydefcount"></a>CDao 数据库：：获取查询定义

调用此成员函数以检索数据库的 QueryDefs 集合中定义的查询数。

```
short GetQueryDefCount();
```

### <a name="return-value"></a>返回值

数据库中定义的查询数。

### <a name="remarks"></a>备注

`GetQueryDefCount`如果需要循环浏览查询Defs 集合中的所有查询def，则非常有用。 要获取有关集合中给定查询的信息，请参阅[GetQueryDefInfo](#getquerydefinfo)。

## <a name="cdaodatabasegetquerydefinfo"></a><a name="getquerydefinfo"></a>CDao数据库：：获取查询信息

调用此成员函数以获取有关数据库中定义的查询的各种信息。

```cpp
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
数据库的 QueryDefs 集合中预定义查询的索引，用于按索引查找。

*查询definfo*<br/>
对返回请求的信息的[CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md)对象的引用。

*dwInfoOptions*<br/>
指定有关要检索的记录集的信息的选项。 此处列出了可用选项以及它们导致函数返回记录集的原因：

- AFX_DAO_PRIMARY_INFO（默认）名称、类型

- AFX_DAO_SECONDARY_INFO主要信息加上：创建日期、上次更新日期、返回记录、可升级

- AFX_DAO_ALL_INFO主要和辅助信息加上：SQL、连接、ODBCTimeout

*lpsz名称*<br/>
包含数据库中定义的查询名称的字符串，用于按名称查找。

### <a name="remarks"></a>备注

提供了函数的两个版本，以便可以通过数据库的 QueryDefs 集合中的索引或查询的名称来选择查询。

有关*查询中*返回的信息的说明，请参阅[CDaoQueryDefinfo](../../mfc/reference/cdaoquerydefinfo-structure.md)结构。 此结构的成员对应于*dwInfoOptions*描述中列出的信息项。 如果您请求一级信息，您也会得到任何以前的信息级别。

## <a name="cdaodatabasegetquerytimeout"></a><a name="getquerytimeout"></a>CDao 数据库：获取查询超时

调用此成员函数以检索当前秒数，以便在连接的数据库上的后续操作超时之前允许。

```
short GetQueryTimeout();
```

### <a name="return-value"></a>返回值

包含超时值（以秒为单位）的短整数。

### <a name="remarks"></a>备注

操作可能会由于网络访问问题、查询处理时间过长等原因而超时。 当该设置生效时，它会影响与此`CDaoDatabase`对象关联的任何记录集上的所有打开、添加新、更新和删除操作。 您可以通过调用[SetQueryTimeout](#setquerytimeout)来更改当前超时设置。 打开后更改记录集的查询超时值不会更改记录集的值。 例如，后续[移动](../../mfc/reference/cdaorecordset-class.md#move)操作不使用新值。 初始化数据库引擎时，最初会设置默认值。

查询超时的默认值取自 Windows 注册表。 如果没有注册表设置，则默认值为 60 秒。 并非所有数据库都支持设置查询超时值的能力。 如果将查询超时值设置为 0，则不执行超时;如果将超时设置为 0，则不执行超时。与数据库的通信可能会停止响应。 此行为在开发期间可能很有用。 如果调用失败，MFC 将引发[CDaoException](../../mfc/reference/cdaoexception-class.md)类型的异常。

有关相关信息，请参阅 DAO 帮助中的"查询超时属性"主题。

## <a name="cdaodatabasegetrecordsaffected"></a><a name="getrecordsaffected"></a>CDao 数据库：获取受影响的记录

调用此成员函数以确定受[Execute](#execute)成员函数最近调用影响的记录数。

```
long GetRecordsAffected();
```

### <a name="return-value"></a>返回值

包含受影响的记录数的长整数。

### <a name="remarks"></a>备注

返回的值包括使用`Execute`运行的操作查询删除、更新或插入的记录数。 当级联更新或删除生效时，返回的计数不会反映相关表中的更改。

有关相关信息，请参阅 DAO 帮助中的主题"记录受影响的属性"。

## <a name="cdaodatabasegetrelationcount"></a><a name="getrelationcount"></a>CDao 数据库：获取关系计数

调用此成员函数以获取数据库中表之间定义的关系数。

```
short GetRelationCount();
```

### <a name="return-value"></a>返回值

数据库中表之间定义的关系数。

### <a name="remarks"></a>备注

`GetRelationCount`如果需要循环访问数据库关系集合中的所有已定义关系，则非常有用。 要获取有关集合中给定关系的信息，请参阅[GetRelationInfo](#getrelationinfo)。

为了说明关系的概念，请考虑供应商表和产品表，它们可能具有一对多关系。 在此关系中，一个供应商可以提供多个产品。 其他关系是一对一和多对多。

## <a name="cdaodatabasegetrelationinfo"></a><a name="getrelationinfo"></a>CDao数据库：获取关系信息

调用此成员函数以获取有关数据库关系集合中指定关系的信息。

```cpp
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
关系对象在数据库的关系集合中的索引，用于按索引查找。

*雷利福*<br/>
对返回请求的信息的[CDao 关系信息](../../mfc/reference/cdaorelationinfo-structure.md)对象的引用。

*dwInfoOptions*<br/>
指定有关要检索的关系的信息的选项。 此处列出了可用选项以及它们导致函数返回的关系的原因：

- AFX_DAO_PRIMARY_INFO（默认）名称、表、外表

- AFX_DAO_SECONDARY_INFO 属性、字段信息

字段信息是包含关系中涉及的主表中的字段的[CDao 关系FieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md)对象。

*lpsz名称*<br/>
包含关系对象名称的字符串，用于按名称查找。

### <a name="remarks"></a>备注

此函数的两个版本提供索引或名称的访问。 有关*在 relinfo*中返回的信息的说明，请参阅[CDao 关系信息](../../mfc/reference/cdaorelationinfo-structure.md)结构。 此结构的成员对应于*dwInfoOptions*描述中列出的信息项。 如果您在一个级别请求信息，您还会在任何以前的级别上获取信息。

> [!NOTE]
> 如果将关系对象的属性设置为激活级联操作 （`dbRelationUpdateCascades`或`dbRelationDeleteCascades`），则当对相关主键表进行更改时，Microsoft Jet 数据库引擎会自动更新或删除一个或多个其他表中的记录。 例如，假设您在客户表和订单表之间建立级联删除关系。 从"客户"表中删除记录时，"订单"表中与该客户相关的记录也会被删除。 此外，如果在"订单"表和其他表之间建立级联删除关系，则当您从"客户"表中删除记录时，将自动删除这些表中的记录。

## <a name="cdaodatabasegettabledefcount"></a><a name="gettabledefcount"></a>CDao 数据库：获取TableDefCount

调用此成员函数以检索数据库中定义的表数。

```
short GetTableDefCount();
```

### <a name="return-value"></a>返回值

数据库中定义的表defs数。

### <a name="remarks"></a>备注

`GetTableDefCount`如果需要循环访问数据库的 TableDefs 集合中的所有表def，则非常有用。 要获取有关集合中给定表的信息，请参阅[GetTableDefInfo](#gettabledefinfo)。

## <a name="cdaodatabasegettabledefinfo"></a><a name="gettabledefinfo"></a>CDao 数据库：获取桌面信息

调用此成员函数以获取有关数据库中定义的表的各种信息。

```cpp
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
数据库的 TableDefs 集合中的表def对象的索引，用于按索引查找。

*表德福*<br/>
对返回请求的信息的[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)对象的引用。

*dwInfoOptions*<br/>
指定要检索的表的信息的选项。 此处列出了可用选项以及它们导致函数返回的关系的原因：

- AFX_DAO_PRIMARY_INFO（默认）名称、可上可、属性

- AFX_DAO_SECONDARY_INFO主要信息加上：创建日期、上次更新日期、源表名称、连接

- AFX_DAO_ALL_INFO主要和辅助信息加上：验证规则、验证文本、记录计数

*lpsz名称*<br/>
表def对象的名称，用于按名称查找。

### <a name="remarks"></a>备注

提供了函数的两个版本，以便您可以通过数据库的 TableDefs 集合中的索引或表的名称来选择表。

有关*表中*返回的信息的说明，请参阅[CDaoTableDefinfo](../../mfc/reference/cdaotabledefinfo-structure.md)结构。 此结构的成员对应于*dwInfoOptions*描述中列出的信息项。 如果您在一个级别请求信息，则也获取任何以前级别的信息。

> [!NOTE]
> AFX_DAO_ALL_INFO选项提供的信息可能获取速度很慢。 在这种情况下，如果有许多记录，计算表中的记录可能非常耗时。

## <a name="cdaodatabasegetversion"></a><a name="getversion"></a>CDao 数据库：获取版本

调用此成员函数以确定 Microsoft Jet 数据库文件的版本。

```
CString GetVersion();
```

### <a name="return-value"></a>返回值

指示与对象关联的数据库文件的版本的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>备注

返回的值表示窗体"主要.minor"中的版本号;例如，"3.0"。 产品版本号（例如 3.0）由版本号 （3）、句点和发行号 （0） 组成。 到目前为止的版本是 1.0、1.1、2.0 和 3.0。

有关相关信息，请参阅 DAO 帮助中的主题"版本属性"。

## <a name="cdaodatabaseisopen"></a><a name="isopen"></a>CDao 数据库：：是打开的

调用此成员函数以确定对象`CDaoDatabase`当前是否在数据库上打开。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果对象当前处于`CDaoDatabase`打开状态，则非零;否则 0。

### <a name="remarks"></a>备注

## <a name="cdaodatabasem_pdaodatabase"></a><a name="m_pdaodatabase"></a>CDao数据库：：m_pDAODatabase

包含指向对象基础的 DAO 数据库对象的 OLE 接口的`CDaoDatabase`指针。

### <a name="remarks"></a>备注

如果需要直接访问 DAO 接口，请使用此指针。

有关直接调用 DAO 的信息，请参阅[技术说明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="cdaodatabasem_pworkspace"></a><a name="m_pworkspace"></a>CDao数据库：m_pWorkspace

包含指向包含数据库对象的[CDao 工作区](../../mfc/reference/cdaoworkspace-class.md)对象的指针。

### <a name="remarks"></a>备注

如果需要直接访问工作区，请使用此指针 ，例如，获取指向工作区数据库集合中其他数据库对象的指针。

## <a name="cdaodatabaseopen"></a><a name="open"></a>CDao 数据库：：打开

必须调用此成员函数来初始化表示现有数据库的新`CDaoDatabase`构造对象。

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
作为现有 Microsoft Jet （） 名称的字符串表达式 。MDB）数据库文件。 如果文件名具有扩展名，则需要它。 如果您的网络支持统一的命名约定 （UNC），您还可以指定网络路径，例如"_MYSERVER\\\\\\\\_MYSHARE\\\\\MYDIR _MYDB"。MDB"。 （字符串文本中需要双背斜杠，因为""\\是C++转义字符。

使用*lpszName*时，需要考虑一些注意事项。 如果是：

- 指已开放供其他用户独占访问的数据库，MFC 将引发[CDaoException](../../mfc/reference/cdaoexception-class.md)类型的异常。 捕获该异常，让用户知道数据库不可用。

- 是空字符串 （""）和*lpszConnect*是"ODBC;;"，显示一个对话框，列出所有已注册的 ODBC 数据源名称，以便用户可以选择数据库。 应避免直接连接到 ODBC 数据源;改用附加的表。

- 否则不引用现有数据库或有效的 ODBC 数据源名称，MFC 将引发类型`CDaoException`异常。

> [!NOTE]
> 有关 DAO 错误代码的详细信息，请参阅 DAOERR。H 文件。 有关相关信息，请参阅 DAO 帮助中的主题"可捕获的数据访问错误"。

*b 独家*<br/>
如果数据库要打开以进行独占（非共享）访问，则为 TRUE 的布尔值，如果要打开数据库以进行共享访问，则为 FALSE。 如果省略此参数，数据库将打开以进行共享访问。

*b 只读*<br/>
如果数据库要打开以进行只读访问，则为 TRUE 的布尔值，如果要打开数据库以进行读/写访问，则为 FALSE。 如果省略此参数，数据库将打开以进行读取/写入访问。 所有从属记录集都继承此属性。

*lpszConnect*<br/>
用于打开数据库的字符串表达式。 此字符串构成 ODBC 连接参数。 您必须提供独占和只读参数才能提供源字符串。 如果数据库是 Microsoft Jet 数据库 （。MDB），此字符串为空（"）。 默认值的语法 [ **_T**（"） " - 为 Unicode 以及应用程序的 ANSI 生成提供了可移植性。

### <a name="remarks"></a>备注

`Open`将数据库与基础 DAO 对象关联。 在初始化记录对象之前，不能使用数据库对象构造记录集、表def 或 querydef 对象。 `Open`将数据库对象追加到关联的工作区的数据库集合。

使用参数如下：

- 如果您要打开微软喷气机 （。MDB） 数据库，使用*lpszName*参数并传递*lpszConnect*参数的空字符串或传递窗体的密码字符串";如果数据库受密码保护（，则 PWD_密码）。仅限 MDB 数据库）。

- 如果要打开 ODBC 数据源，请传递*lpszConnect*中的有效 ODBC 连接字符串和*lpszName*中的空字符串。

有关相关信息，请参阅 DAO 帮助中的主题"打开数据库方法"。

> [!NOTE]
> 为了在访问外部数据库（包括 ISAM 数据库和 ODBC 数据源）时性能更好，建议您将外部数据库表附加到 Microsoft Jet 引擎数据库 （）。MDB），而不是直接连接到数据源。

例如，如果 DBMS 主机不可用，连接尝试可能会超时。 如果连接尝试失败，`Open`将引发[CDaoException](../../mfc/reference/cdaoexception-class.md)类型的异常。

其余注释仅适用于 ODBC 数据库：

如果数据库是 ODBC 数据库，并且`Open`呼叫中的参数不包含足够的信息来建立连接，则 ODBC 驱动程序将打开一个对话框，从用户处获取必要的信息。 调用 时`Open`，连接字符串*lpszConnect*将私下存储，可通过调用[GetConnect](#getconnect)成员函数获得。

如果需要，可以在调用`Open`之前打开自己的对话框，以便从用户获取信息（如密码），然后将该信息添加到传递给 的连接字符串`Open`中。 或者，您可能希望保存传递的连接字符串（可能位于 Windows 注册表中），以便在应用程序下次调用`Open``CDaoDatabase`对象时重用它。

您还可以使用连接字符串进行多个级别的登录授权（每个级别用于其他`CDaoDatabase`对象），或传输其他特定于数据库的信息。

## <a name="cdaodatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDao 数据库：：设置查询超时

调用此成员函数以覆盖默认秒数，以便在后续对连接的数据库超时执行操作之前允许。

```cpp
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>参数

*n 秒*<br/>
查询尝试超时之前要允许的秒数。

### <a name="remarks"></a>备注

操作可能会由于网络访问问题、查询处理时间过长等而超时。 如果要`SetQueryTimeout`更改查询超时值，请先打开记录集之前或调用记录集的[AddNew、Update](../../mfc/reference/cdaorecordset-class.md#addnew)或[删除](../../mfc/reference/cdaorecordset-class.md#delete)成员函数。 [Update](../../mfc/reference/cdaorecordset-class.md#update) 该设置影响所有后续[的](../../mfc/reference/cdaorecordset-class.md#open) `AddNew`Open `Update`、`Delete`和对与此`CDaoDatabase`对象关联的任何记录集的调用。 打开后更改记录集的查询超时值不会更改记录集的值。 例如，后续[移动](../../mfc/reference/cdaorecordset-class.md#move)操作不使用新值。

查询超时的默认值为 60 秒。 并非所有数据库都支持设置查询超时值的能力。 如果将查询超时值设置为 0，则不执行超时;如果将超时设置为 0，则不执行超时。与数据库的通信可能会停止响应。 此行为在开发期间可能很有用。

有关相关信息，请参阅 DAO 帮助中的"查询超时属性"主题。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDaoWorkspace 类](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDao记录组类](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDatabase 类](../../mfc/reference/cdatabase-class.md)<br/>
[CDaoException 类](../../mfc/reference/cdaoexception-class.md)
