---
title: CDaoWorkspace 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoWorkspace
- AFXDAO/CDaoWorkspace
- AFXDAO/CDaoWorkspace::CDaoWorkspace
- AFXDAO/CDaoWorkspace::Append
- AFXDAO/CDaoWorkspace::BeginTrans
- AFXDAO/CDaoWorkspace::Close
- AFXDAO/CDaoWorkspace::CommitTrans
- AFXDAO/CDaoWorkspace::CompactDatabase
- AFXDAO/CDaoWorkspace::Create
- AFXDAO/CDaoWorkspace::GetDatabaseCount
- AFXDAO/CDaoWorkspace::GetDatabaseInfo
- AFXDAO/CDaoWorkspace::GetIniPath
- AFXDAO/CDaoWorkspace::GetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::GetLoginTimeout
- AFXDAO/CDaoWorkspace::GetName
- AFXDAO/CDaoWorkspace::GetUserName
- AFXDAO/CDaoWorkspace::GetVersion
- AFXDAO/CDaoWorkspace::GetWorkspaceCount
- AFXDAO/CDaoWorkspace::GetWorkspaceInfo
- AFXDAO/CDaoWorkspace::Idle
- AFXDAO/CDaoWorkspace::IsOpen
- AFXDAO/CDaoWorkspace::Open
- AFXDAO/CDaoWorkspace::RepairDatabase
- AFXDAO/CDaoWorkspace::Rollback
- AFXDAO/CDaoWorkspace::SetDefaultPassword
- AFXDAO/CDaoWorkspace::SetDefaultUser
- AFXDAO/CDaoWorkspace::SetIniPath
- AFXDAO/CDaoWorkspace::SetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::SetLoginTimeout
- AFXDAO/CDaoWorkspace::m_pDAOWorkspace
dev_langs:
- C++
helpviewer_keywords:
- CDaoWorkspace [MFC], CDaoWorkspace
- CDaoWorkspace [MFC], Append
- CDaoWorkspace [MFC], BeginTrans
- CDaoWorkspace [MFC], Close
- CDaoWorkspace [MFC], CommitTrans
- CDaoWorkspace [MFC], CompactDatabase
- CDaoWorkspace [MFC], Create
- CDaoWorkspace [MFC], GetDatabaseCount
- CDaoWorkspace [MFC], GetDatabaseInfo
- CDaoWorkspace [MFC], GetIniPath
- CDaoWorkspace [MFC], GetIsolateODBCTrans
- CDaoWorkspace [MFC], GetLoginTimeout
- CDaoWorkspace [MFC], GetName
- CDaoWorkspace [MFC], GetUserName
- CDaoWorkspace [MFC], GetVersion
- CDaoWorkspace [MFC], GetWorkspaceCount
- CDaoWorkspace [MFC], GetWorkspaceInfo
- CDaoWorkspace [MFC], Idle
- CDaoWorkspace [MFC], IsOpen
- CDaoWorkspace [MFC], Open
- CDaoWorkspace [MFC], RepairDatabase
- CDaoWorkspace [MFC], Rollback
- CDaoWorkspace [MFC], SetDefaultPassword
- CDaoWorkspace [MFC], SetDefaultUser
- CDaoWorkspace [MFC], SetIniPath
- CDaoWorkspace [MFC], SetIsolateODBCTrans
- CDaoWorkspace [MFC], SetLoginTimeout
- CDaoWorkspace [MFC], m_pDAOWorkspace
ms.assetid: 64f60de6-4df1-4d4a-a65b-c489b5257d52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a4a5b6936397728472bf0041735248157091db56
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054353"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace 类

管理单个用户从登录到注销的已命名并受密码保护的数据库会话。

## <a name="syntax"></a>语法

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|构造一个工作区对象。 然后，调用`Create`或`Open`。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDaoWorkspace::Append](#append)|将新创建的工作区追加到数据库引擎的工作区集合。|
|[CDaoWorkspace::BeginTrans](#begintrans)|开始一个新事务，应用于工作区中打开的所有数据库。|
|[CDaoWorkspace::Close](#close)|关闭工作区和所有其包含的对象。 挂起的事务将回滚。|
|[CDaoWorkspace::CommitTrans](#committrans)|完成当前的事务，并将保存所做的更改。|
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|压缩 （或重复项） 数据库。|
|[CDaoWorkspace::Create](#create)|创建新的 DAO 工作区对象。|
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|工作区的数据库集合中返回 DAO 数据库对象的数。|
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|返回指定工作区的数据库集合中定义的 DAO 数据库有关的信息。|
|[CDaoWorkspace::GetIniPath](#getinipath)|Windows 注册表中返回的位置的 Microsoft Jet 数据库引擎的初始化设置。|
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|返回一个值，该值指示是否涉及同一 ODBC 数据源的多个事务都通过隔离强制多个连接到数据源。|
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|返回当用户尝试登录到 ODBC 数据库时，会发生错误之前等待的秒数。|
|[CDaoWorkspace::GetName](#getname)|返回的工作区对象的用户定义名称。|
|[CDaoWorkspace::GetUserName](#getusername)|返回创建工作区时指定的用户名。 这是工作区所有者的名称。|
|[CDaoWorkspace::GetVersion](#getversion)|返回一个字符串，包含与工作区关联的数据库引擎的版本。|
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|数据库引擎的工作区集合中返回的 DAO 工作区对象的数量。|
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|返回有关指定数据库引擎的工作区集合中定义的 DAO 工作区的信息。|
|[CDaoWorkspace::Idle](#idle)|使数据库引擎可以执行的后台任务。|
|[CDaoWorkspace::IsOpen](#isopen)|返回非零的工作区是否打开。|
|[CDaoWorkspace::Open](#open)|显式打开与 DAO 的默认工作区相关联的工作区对象。|
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|尝试修复损坏的数据库。|
|[CDaoWorkspace::Rollback](#rollback)|结束当前事务并不会保存所做的更改。|
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|设置数据库引擎将使用特定密码的情况下创建工作区对象的密码。|
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|设置数据库引擎时没有特定的用户名称创建一个工作区对象使用的用户名。|
|[CDaoWorkspace::SetIniPath](#setinipath)|Windows 注册表中设置的位置的 Microsoft Jet 数据库引擎的初始化设置。|
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|指定是否涉及同一 ODBC 数据源的多个事务上隔离的强制多个连接到数据源。|
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|设置当用户尝试登录到 ODBC 数据源时，会发生错误之前等待的秒数。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|指向基础 DAO 工作区对象。|

## <a name="remarks"></a>备注

在大多数情况下，您不需要多个工作区，并不需要创建显式工作区的对象;当您打开数据库和记录集对象，它们使用 DAO 的默认工作区。 但是，如果需要您可以运行多个会话一次通过创建另一个工作区对象。 每个工作区对象可以包含在其自己的数据库集合中的多个打开的数据库对象。 在 MFC 中，工作区是主要事务管理器中，打开数据库的一组指定同一"事务空间。"

> [!NOTE]
>  DAO 数据库类是不同于基于开放式数据库连接 (ODBC) 的 MFC 数据库类。 所有 DAO 数据库类名称都具有"CDao"前缀。 一般情况下，基于 DAO 的 MFC 类是比基于 ODBC 的 MFC 类功能更强大。 基于 DAO 的类通过包括 ODBC 驱动程序的 Microsoft Jet 数据库引擎访问的数据。 它们还支持数据定义语言 (DDL) 操作，如创建数据库并添加表和字段通过类，而无需直接调用 DAO。

## <a name="capabilities"></a>功能

类`CDaoWorkspace`提供了以下：

- 显式访问权限，如有需要为创建初始化数据库引擎的默认工作区。 通常使用 DAO 的默认工作区隐式创建数据库和记录集对象。

- 在工作区中打开的事务应用于所有数据库的事务空间。 您可以创建额外的工作区来管理单独的事务空间。

- 基础 Microsoft Jet 数据库引擎的许多属性的接口 （请参阅静态成员函数）。 打开或创建工作区中，或调用静态成员函数之前打开或创建、 初始化数据库引擎。

- 对数据库引擎的工作区集合，可存储已追加到其所有活动的工作区的访问。 您还可以创建和使用工作区不会将它们附加到的集合。

## <a name="security"></a>安全性

MFC DAO，用于进行安全控制在不执行用户和组集合。 如果您需要的 DAO 这些方面，您必须自己进行编程它们通过直接调用 DAO 接口。 有关信息，请参阅[技术注意 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="usage"></a>用法

可以使用类`CDaoWorkspace`到：

- 显式打开默认工作区。

   通常使用默认工作区时，隐式 — 当您打开新的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象。 但可能需要显式访问 — 例如，到数据库引擎或访问工作区集合。 请参阅下面的"隐式使用的默认工作区"。

- 创建新的工作区。 调用[追加](#append)如果你想要将它们添加到工作区集合。

- 打开工作区集合中的现有工作区。

创建新的工作区已中不存在的工作区集合是下所述[创建](#create)成员函数。 不以任何方式数据库引擎会话之间保留工作区对象。 如果你的应用程序静态链接 MFC，结束应用程序取消初始化数据库引擎。 如果你的应用程序动态链接 mfc，则数据库引擎未初始化，MFC DLL 卸载时。

下所述显式打开默认工作区，或在工作区集合中，打开现有的工作区[打开](#open)成员函数。

结束通过关闭与工作区的工作区会话[关闭](#close)成员函数。 `Close` 关闭您未关闭之前，回滚任何未提交的事务的任何数据库。

## <a name="transactions"></a>事务

DAO 管理事务在工作区级别;因此，具有多个打开的数据库的工作区上的事务应用于所有数据库。 例如，如果两个数据库有未提交的更新，并调用[CommitTrans](#committrans)，所有更新都已提交。 如果你想要限制到单个数据库的事务，则它需要一个单独的工作区对象。

## <a name="implicit-use-of-the-default-workspace"></a>隐式使用默认工作区

MFC 使用在以下情况下隐式的 DAO 的默认工作区：

- 如果您创建一个新`CDaoDatabase`对象，但仍未通过现有`CDaoWorkspace`对象时，MFC 将创建一个临时工作区对象，对应于 DAO 的默认工作区。 如果这样做多个数据库，所有数据库对象都与默认工作区相关联。 您可以访问数据库的工作区通过`CDaoDatabase`数据成员。

- 同样，如果您创建`CDaoRecordset`无需提供一个指向对象`CDaoDatabase`对象时，MFC 创建一个临时数据库对象和扩展到临时工作区对象。 您可以通过访问记录集的数据库和其工作区中，间接`CDaoRecordset`数据成员。

## <a name="other-operations"></a>其他操作

此外提供了这其他数据库操作，例如修复数据库已损坏或压缩的数据库。

有关调用 DAO 直接和 DAO 安全信息，请参阅[技术注意 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>要求

**标头：** afxdao.h

##  <a name="append"></a>  CDaoWorkspace::Append

调用后调用此成员函数[创建](#create)。

```
virtual void Append();
```

### <a name="remarks"></a>备注

`Append` 将新创建的工作区对象追加到数据库引擎的工作区集合。 数据库引擎的会话; 之间将不再存在工作区它们存储在内存中，不在磁盘上。 不需要追加一个工作区;如果不这样做，您仍可以使用它。

追加的工作区保留在一个有效的工作区集合中，打开状态，直到你调用其[关闭](#close)成员函数。

有关相关信息，请参阅主题 DAO 帮助中的"追加方法"。

##  <a name="begintrans"></a>  CDaoWorkspace::BeginTrans

调用此成员函数以启动事务。

```
void BeginTrans();
```

### <a name="remarks"></a>备注

调用后`BeginTrans`，对数据或数据库结构进行的更新时提交事务才会生效。 由于工作区定义单个事务空间，事务将适用于工作区中所有打开的数据库。 有两种方法来完成该事务：

- 调用[CommitTrans](#committrans)成员函数以提交事务，然后将更改保存到数据源。

- 或拨打[回滚](#rollback)成员函数以取消该事务。

关闭工作区对象或数据库对象事务正在挂起时将回滚所有挂起的事务。

如果需要隔离的另一个 ODBC 数据源的一个 ODBC 数据源上的事务，请参阅[SetIsolateODBCTrans](#setisolateodbctrans)成员函数。

##  <a name="cdaoworkspace"></a>  CDaoWorkspace::CDaoWorkspace

构造 `CDaoWorkspace` 对象。

```
CDaoWorkspace();
```

### <a name="remarks"></a>备注

后构造 c + + 对象时，有两个选项：

- 调用对象的[打开](#open)成员函数将打开默认工作区，或者若要打开的工作区集合中的现有对象。

- 或调用对象的[创建](#create)成员函数来创建新的 DAO workspace 对象。 这会显式启动新的工作区会话，您可以通过参考`CDaoWorkspace`对象。 在调用`Create`，可以调用[追加](#append)如果你想要添加到数据库引擎的工作区集合工作区。

查看类概览[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)了解何时需要显式创建`CDaoWorkspace`对象。 通常情况下，使用打开时隐式创建的工作区[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象而无需指定一个工作区或当您打开[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)而无需指定数据库对象的对象。 在这种方式中创建的 MFC DAO 对象使用 DAO 的默认工作区，这是创建一次，重复使用。

若要释放工作区和其包含的对象，调用该工作区对象的[关闭](#close)成员函数。

##  <a name="close"></a>  CDaoWorkspace::Close

调用此成员函数以关闭工作区对象。

```
virtual void Close();
```

### <a name="remarks"></a>备注

关闭打开的工作区对象释放基础的 DAO 对象和工作区集合的成员的工作区是否从集合中移除它。 调用`Close`是好的编程做法。

> [!CAUTION]
>  关闭工作区对象会关闭任何打开的数据库工作区中。 这将打开，正在关闭数据库中的所有记录集和任何挂起的编辑或更新都将回滚。 有关相关信息，请参阅[CDaoDatabase::Close](../../mfc/reference/cdaodatabase-class.md#close)， [CDaoRecordset::Close](../../mfc/reference/cdaorecordset-class.md#close)， [CDaoTableDef::Close](../../mfc/reference/cdaotabledef-class.md#close)，和[CDaoQueryDef::Close](../../mfc/reference/cdaoquerydef-class.md#close)成员函数。

工作区中的对象不是永久的;它们仅存在时对其的引用存在。 这意味着，数据库引擎会话结束时，工作区和其数据库集合不会持久保留。 您必须重新创建它们的下一个会话通过重新打开工作区和数据库。

有关相关信息，请参阅主题 DAO 帮助中的"关闭方法"。

##  <a name="committrans"></a>  CDaoWorkspace::CommitTrans

调用此成员函数以提交事务，将一组编辑和更新保存到工作区中的一个或多个数据库。

```
void CommitTrans();
```

### <a name="remarks"></a>备注

事务数据库的数据或从通过调用其结构发生更改的一系列组成[BeginTrans](#begintrans)。 完成事务后，请提交或回滚 （取消所做的更改） 与[回滚](#rollback)。 默认情况下，如果事务，未记录的更新将被立即提交。 调用`BeginTrans`导致的更新的承诺，可延迟到调用`CommitTrans`。

> [!CAUTION]
>  在一个工作区中，事务始终是全局性的工作区并不限于只能有一个数据库或记录集。 如果你对多个数据库或在工作区事务中，记录集执行操作`CommitTrans`提交所有挂起的更新，和`Rollback`还原这些数据库和记录集上的所有操作。

关闭数据库或具有挂起的事务的工作区后，事务全部回滚。

> [!NOTE]
>  这不是两阶段提交机制。 如果无法提交一个更新，其他人仍将提交。

##  <a name="compactdatabase"></a>  CDaoWorkspace::CompactDatabase

调用此成员函数以压缩指定的 Microsoft Jet (。MDB) 数据库。

```
static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int nOptions = 0);

static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale,
    int nOptions,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>参数

*lpszSrcName*<br/>
对现有的名称已关闭数据库。 它可以完整路径和文件名，如"c:\\\MYDB。MDB"。 如果文件名的扩展名，则必须指定它。 如果网络支持的统一命名约定 (UNC)，您还可以指定网络路径，如"\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB。MDB"。 (双反斜杠需要在路径的字符串，因为"\\"c + + 转义符。)

*lpszDestName*<br/>
要创建压缩的数据库的完整路径。 此外可以指定与作为网络路径*lpszSrcName*。 不能使用*lpszDestName*参数，以指定相同数据库文件作为*lpszSrcName*。

*lpszPassword*<br/>
密码，在想要压缩受密码保护的数据库时使用。 请注意，如果您使用的版本`CompactDatabase`采用密码，则必须提供所有参数。 此外，由于这是连接参数，它需要特殊格式，按如下所示:;PWD = *lpszPassword*。 例如:;PWD ="满意"。 （前置分号是必需的。

*lpszLocale*<br/>
用来指定用于创建排序规则顺序的字符串表达式*lpszDestName*。 如果您省略此参数接受的默认值`dbLangGeneral`（见下文），新数据库的区域设置是相同的旧数据库。 可能的值有：

- `dbLangGeneral` 英语、 德语、 法语、 葡萄牙语、 意大利语、 和现代西班牙语

- `dbLangArabic` 阿拉伯语

- `dbLangCyrillic` 俄语

- `dbLangCzech` 捷克语

- `dbLangDutch` 荷兰语

- `dbLangGreek` 希腊语

- `dbLangHebrew` 希伯来语

- `dbLangHungarian` 匈牙利语

- `dbLangIcelandic` 冰岛语

- `dbLangNordic` 北欧语言 （Microsoft Jet 数据库引擎版本 1.0 仅）

- `dbLangNorwdan` 挪威语和丹麦语

- `dbLangPolish` 波兰语

- `dbLangSpanish` 传统西班牙语

- `dbLangSwedfin` 瑞典语和芬兰语

- `dbLangTurkish` 土耳其语

*nOptions*<br/>
指示用于目标数据库的一个或多个选项*lpszDestName*。 如果您省略此参数接受默认值*lpszDestName*将具有相同的加密和与相同的版本*lpszSrcName*。 你可以组合`dbEncrypt`或`dbDecrypt`选项与使用按位 OR 运算符的版本选项之一。 可能的值，指定数据库格式，而不是数据库引擎版本，包括：

- `dbEncrypt` 压缩时加密该数据库。

- `dbDecrypt` 压缩时对数据库进行解密。

- `dbVersion10` 创建压缩时使用 Microsoft Jet 数据库引擎版本 1.0 的数据库。

- `dbVersion11` 创建压缩时使用 Microsoft Jet 数据库引擎版本 1.1 的数据库。

- `dbVersion20` 创建压缩时使用 Microsoft Jet 数据库引擎版本 2.0 的数据库。

- `dbVersion30` 创建压缩时使用 Microsoft Jet 数据库引擎版本 3.0 的数据库。

可以使用`dbEncrypt`或`dbDecrypt`在 options 参数来指定是否加密或解密该数据库，因为它压缩。 如果省略加密常量或同时包含`dbDecrypt`并`dbEncrypt`， *lpszDestName*将具有相同加密作为*lpszSrcName*。 您可以使用版本常量之一选项参数中指定的压缩的数据库的数据格式版本。 此常量会影响仅的数据格式的版本*lpszDestName*。 您可以指定只有一个版本常量。 如果省略版本常数*lpszDestName*将具有与相同的版本*lpszSrcName*。 您可以压缩*lpszDestName*仅针对相同版本或更高版本比*lpszSrcName*。

> [!CAUTION]
>  如果未加密数据库，就可以，即使你实现用户/密码安全性，以直接读取构成数据库的二进制文件磁盘文件。

### <a name="remarks"></a>备注

更改数据库中的数据时，数据库文件将变成碎片，并使用比实际所需的更多磁盘空间。 我们会定期应压缩数据库进行碎片整理数据库文件。 压缩的数据库是通常较小。 您还可以选择在复制和压缩数据库时更改排序顺序、 加密或数据格式的版本。

> [!CAUTION]
>  `CompactDatabase`成员函数将不正确的完整的 Microsoft Access 数据库从一个版本转换为另一个。 转换仅数据格式。 Microsoft 访问权限定义对象，例如窗体和报表，不会转换。 但是，正确地转换数据。

> [!TIP]
>  此外可以使用`CompactDatabase`数据库文件复制。

有关数据库压缩的详细信息，请参阅主题 DAO 帮助中的"CompactDatabase 方法"。

##  <a name="create"></a>  CDaoWorkspace::Create

调用此成员函数以创建新的 DAO workspace 对象并将其与 MFC`CDaoWorkspace`对象。

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
唯一地命名新的工作区对象包含最多 14 个字符的字符串。 必须提供一个名称。 有关相关信息，请参阅主题 DAO 帮助中的"名称属性"。

*lpszUserName*<br/>
工作区的所有者的用户名。 有关要求，请参阅*lpszDefaultUser*参数[SetDefaultUser](#setdefaultuser)成员函数。 有关相关信息，请参阅主题 DAO 帮助中的"用户名属性"。

*lpszPassword*<br/>
新的工作区对象的密码。 密码可以是长度最多 14 个字符，并且可以包含除 ASCII 0 (null) 之外的任何字符。 密码是区分大小写。 有关相关信息，请参阅主题 DAO 帮助中的"密码属性"。

### <a name="remarks"></a>备注

整个创建过程是：

1. 构造[CDaoWorkspace](#cdaoworkspace)对象。

1. 调用对象的`Create`成员函数来创建基础 DAO 工作区。 必须指定一个工作区名称。

1. 另外也可以调用[追加](#append)如果你想要添加到数据库引擎的工作区集合工作区。 您可以使用工作区不会将附加它。

之后`Create`调用时，工作区对象是否处于打开状态，供使用。 不要调用`Open`后`Create`。 不要调用`Create`如果工作区集合中已存在工作区。 `Create` 如果它已被初始化，不能应用程序，初始化数据库引擎。

##  <a name="getdatabasecount"></a>  CDaoWorkspace::GetDatabaseCount

调用此成员函数可检索的工作区的数据库集合中的 DAO 数据库对象数，在工作区中打开数据库的数量。

```
short GetDatabaseCount();
```

### <a name="return-value"></a>返回值

在工作区中打开数据库的数量。

### <a name="remarks"></a>备注

`GetDatabaseCount` 如果您需要循环访问工作区的数据库集合中的所有已定义数据库，非常有用。 若要获取集合中给定的数据库有关的信息，请参阅[GetDatabaseInfo](#getdatabaseinfo)。 典型用法是调用`GetDatabaseCount`的几个打开的数据库，然后使用该数字作为循环索引重复调用`GetDatabaseInfo`。

##  <a name="getdatabaseinfo"></a>  CDaoWorkspace::GetDatabaseInfo

调用此成员函数以获取各种类型的工作区中打开的数据库有关的信息。

```
void GetDatabaseInfo(
    int nIndex,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetDatabaseInfo(
    LPCTSTR lpszName,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
在工作区的数据库集合中，为按索引进行查找的数据库对象的从零开始的索引。

*dbinfo*<br/>
对引用[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)对象，它返回请求的信息。

*dwInfoOptions*<br/>
指定要检索的数据库有关的信息的选项。 可用选项以及它们会导致函数返回此处列出：

- AFX_DAO_PRIMARY_INFO （默认值） 名称，可更新事务

- AFX_DAO_SECONDARY_INFO 主要信息加上： 版本中，排序规则顺序查询超时值

- AFX_DAO_ALL_INFO 主要和辅助数据库信息加上： 连接

*lpszName*<br/>
按名称查找数据库对象的名称。 名称是唯一命名新的工作区对象包含最多 14 个字符的字符串。

### <a name="remarks"></a>备注

函数的一个版本，可按索引查找数据库。 另一个版本，可以按名称查找数据库。

有关中返回的信息的说明*dbinfo*，请参阅[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)结构。 此结构具有对应于上面列出的说明中的信息的项目的成员*dwInfoOptions*。 当请求在某一级别的信息时，可以获取任何以前的级别的信息。

##  <a name="getinipath"></a>  CDaoWorkspace::GetIniPath

调用此成员函数以获取 Microsoft Jet 数据库的位置引擎的 Windows 注册表中的初始化设置。

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)包含注册表位置。

### <a name="remarks"></a>备注

可以使用位置以获取有关数据库引擎的设置的信息。 返回的信息是实际的注册表子项的名称。

有关相关信息，请参阅"IniPath 属性"和"自定义 Windows 注册表设置的数据访问"DAO 帮助中的主题。

##  <a name="getisolateodbctrans"></a>  CDaoWorkspace::GetIsolateODBCTrans

调用此成员函数可为工作区获取 DAO IsolateODBCTrans 属性的当前值。

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>返回值

如果 ODBC 事务之间隔离; 非零值否则为 0。

### <a name="remarks"></a>备注

在某些情况下，可能需要对相同的 ODBC 数据库具有挂起的多个同时进行的事务。 若要执行此操作，您需要打开单独的工作区为每个事务。 请记住，虽然每个工作区可以有其自己的 ODBC 连接到数据库，这会降低系统性能。 由于事务隔离不是通常所需的默认情况下共享来自多个工作区对象由同一个用户打开 ODBC 连接。

某些 ODBC 服务器，例如 Microsoft SQL Server 不允许在单个连接上同时进行的事务。 如果您需要有多个事务在针对此类数据库挂起的时间，IsolateODBCTrans 属性设置为 TRUE 上每个工作区就立即打开它。 这会强制每个工作区单独的 ODBC 连接。

有关相关信息，请参阅主题 DAO 帮助中的"IsolateODBCTrans 属性"。

##  <a name="getlogintimeout"></a>  CDaoWorkspace::GetLoginTimeout

调用此成员函数可为工作区获取 DAO LoginTimeout 属性的当前值。

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>返回值

当您尝试登录到 ODBC 数据库时，将发生错误之前等待的秒数。

### <a name="remarks"></a>备注

此值表示当您尝试登录到 ODBC 数据库时，将发生错误之前等待的秒数。 默认 LoginTimeout 设置为 20 秒的时间。 当 LoginTimeout 设置为 0 时，会发生任何超时和与数据源之间的通信可能会停止响应。

连接尝试登录到 ODBC 数据库，例如 Microsoft SQL Server 时可能会由于网络错误而失败或者因为服务器未运行。 而不是等待默认值为 20 秒的时间连接，可以指定数据库引擎等待多长时间才能生成错误。 在登录到服务器发生隐式作为多个不同的事件，如外部服务器数据库上运行查询的一部分。

有关相关信息，请参阅主题 DAO 帮助中的"LoginTimeout 属性"。

##  <a name="getname"></a>  CDaoWorkspace::GetName

调用此成员函数可获取 DAO 工作区对象基础的用户定义名称`CDaoWorkspace`对象。

```
CString GetName();
```

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)包含用户定义的名称的 DAO workspace 对象。

### <a name="remarks"></a>备注

名称可用于按名称访问数据库引擎的工作区集合中的 DAO 工作区对象。

有关相关信息，请参阅主题 DAO 帮助中的"名称属性"。

##  <a name="getusername"></a>  CDaoWorkspace::GetUserName

调用此成员函数以获取工作区的所有者的名称。

```
CString GetUserName();
```

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，表示工作区对象的所有者。

### <a name="remarks"></a>备注

若要获取或设置工作区所有者的权限，调用 DAO 直接以检查权限属性设置;这将确定哪些权限的用户拥有。 若要使用的权限，您需要一个系统。MDA 文件。

有关调用 DAO 直接，请参阅[技术注意 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。 有关相关信息，请参阅主题 DAO 帮助中的"用户名属性"。

##  <a name="getversion"></a>  CDaoWorkspace::GetVersion

调用此成员函数可确定在使用 Microsoft Jet 数据库引擎的版本。

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，该值指示与对象关联的数据库引擎的版本。

### <a name="remarks"></a>备注

返回的值表示窗体"major.minor;"中的版本号例如，"3.0。" 产品版本编号 (例如，3.0) 组成的版本号 (3)、 句点和发行版号 (0)。

有关相关信息，请参阅主题 DAO 帮助中的"版本属性"。

##  <a name="getworkspacecount"></a>  CDaoWorkspace::GetWorkspaceCount

调用此成员函数以检索 DAO 数据库引擎的工作区集合中的工作区对象的数目。

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>返回值

工作区集合中打开工作区数。

### <a name="remarks"></a>备注

此计数不包括任何打开的工作区，不会追加到集合。 `GetWorkspaceCount` 如果您需要循环访问工作区集合中的所有定义工作区，很有用。 若要获取有关给定的工作区集合中的信息，请参阅[GetWorkspaceInfo](#getworkspaceinfo)。 典型用法是调用`GetWorkspaceCount`的几个打开的工作区，然后使用该数字作为循环索引重复调用`GetWorkspaceInfo`。

##  <a name="getworkspaceinfo"></a>  CDaoWorkspace::GetWorkspaceInfo

调用此成员函数以获取各种类型的工作区打开的会话中的信息。

```
void GetWorkspaceInfo(
    int nIndex,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetWorkspaceInfo(
    LPCTSTR lpszName,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
在工作区集合中，为按索引进行查找的数据库对象的从零开始的索引。

*wkspcinfo*<br/>
对引用[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)对象，它返回请求的信息。

*dwInfoOptions*<br/>
指定有关要检索的工作区的信息的选项。 可用选项以及它们会导致函数返回此处列出：

- AFX_DAO_PRIMARY_INFO （默认值） 名称

- AFX_DAO_SECONDARY_INFO 主要信息加上： 用户名

- AFX_DAO_ALL_INFO 主要和辅助数据库信息加上： 隔离 ODBCTrans

*lpszName*<br/>
按名称查找工作区对象的名称。 名称是唯一命名新的工作区对象包含最多 14 个字符的字符串。

### <a name="remarks"></a>备注

有关中返回的信息的说明*wkspcinfo*，请参阅[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)结构。 此结构具有对应于上面列出的说明中的信息的项目的成员*dwInfoOptions*。 当请求在某一级别的信息时，可以获取的以前的级别的信息。

##  <a name="idle"></a>  CDaoWorkspace::Idle

调用`Idle`为数据库引擎提供将有机会执行后台任务，可能不是最新由于密集数据处理。

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>参数

*4%n 操作*<br/>
要在空闲处理期间执行的操作。 目前唯一有效的操作是`dbFreeLocks`。

### <a name="remarks"></a>备注

这通常是在多用户，在其中没有足够的背景处理时间，以保持最新记录集的所有记录的多任务处理环境中，则返回 true。

> [!NOTE]
>  调用`Idle`与使用 3.0 版 Microsoft Jet 数据库引擎创建的数据库不需要。 使用`Idle`仅对使用早期版本创建的数据库。

通常情况下，仅当没有其他操作 （包括鼠标移动） 发生时，才会取消的读取锁定，被更新本地动态集类型记录集对象中的数据。 如果定期调用`Idle`，提供有时间，以赶上上后台处理任务通过发布的数据库引擎不需要的读取锁定。 指定`dbFreeLocks`作为自变量的常量延迟处理直到所有读取的锁被释放。

在单用户环境中不需要此成员函数，除非正在运行的应用程序的多个实例。 `Idle`成员函数可提高在多用户环境中的性能，因为它会强制数据库引擎将数据刷新到磁盘，释放内存的锁定。 你可以通过将操作事务的一部分来释放读的锁。

有关相关信息，请参阅主题 DAO 帮助中的"空闲方法"。

##  <a name="isopen"></a>  CDaoWorkspace::IsOpen

调用此成员函数以确定是否`CDaoWorkspace`对象处于打开状态，即是否 MFC 对象已初始化通过调用[打开](#open)或调用[创建](#create)。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果工作区对象已打开，则非零值否则为 0。

### <a name="remarks"></a>备注

你可以调用任意成员函数是处于打开状态的工作区。

##  <a name="m_pdaoworkspace"></a>  CDaoWorkspace::m_pDAOWorkspace

指向基础 DAO 工作区对象的指针。

### <a name="remarks"></a>备注

如果需要直接访问基础的 DAO 对象，请使用此数据成员。 您可以调用通过此指针的 DAO 对象的接口。

直接访问 DAO 对象有关的信息，请参阅[技术注意 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

##  <a name="open"></a>  CDaoWorkspace::Open

显式打开与 DAO 的默认工作区相关联的工作区对象。

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
要打开的 DAO 工作区对象的名称 — 唯一的名称在工作区包含最多 14 个字符的字符串。 接受默认值为 NULL 以显式打开默认工作区。 有关命名要求，请参阅*lpszName*参数[创建](#create)。 有关相关信息，请参阅主题 DAO 帮助中的"名称属性"。

### <a name="remarks"></a>备注

构造后`CDaoWorkspace`对象，请调用此成员函数以执行下列操作之一：

- 显式打开默认工作区。 传递 NULL，否则*lpszName*。

- 打开现有`CDaoWorkspace`对象，按名称的工作区集合的成员。 传递的现有工作区对象的有效名称。

`Open` 将工作区对象放入打开状态，如果它已被初始化，不能应用程序还会初始化数据库引擎。

尽管许多`CDaoWorkspace`成员函数仅在工作区打开后调用，以下成员函数，对数据库引擎，可构造的 c + + 对象，但之前调用后`Open`:

||||
|-|-|-|
|[创建](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|
|[GetIniPath](#getinipath)|[空闲](#idle)|[SetIniPath](#setinipath)|
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|

##  <a name="repairdatabase"></a>  CDaoWorkspace::RepairDatabase

如果您需要以尝试修复损坏的数据库访问 Microsoft Jet 数据库引擎，调用此成员函数。

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
路径和文件名的现有 Microsoft Jet 引擎的数据库文件。 如果省略路径，搜索仅在当前目录。 如果您的系统支持的统一命名约定 (UNC)，您还可以指定网络路径，例如:"\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB。MDB"。 (因为中的路径字符串需要双反斜杠"\\"c + + 转义符。)

### <a name="remarks"></a>备注

您必须先关闭指定的数据库*lpszName*修复它之前。 在多用户环境中，其他用户不能有*lpszName*打开时将对其进行修复。 如果*lpszName*未关闭或不是可供独占使用，就会出错。

此成员函数尝试修复的不完整的写操作中被标记为可能已损坏的数据库。 如果使用 Microsoft Jet 数据库引擎的应用程序意外关闭由于电源故障或计算机硬件的问题，这可能发生。 如果您完成该操作并调用[关闭](../../mfc/reference/cdaodatabase-class.md#close)成员函数，或退出应用程序在通常的方式，数据库不会标记为可能已损坏。

> [!NOTE]
>  在修复后的数据库，它还是压缩它使用一个好办法[CompactDatabase](#compactdatabase)成员函数进行碎片整理文件和以恢复磁盘空间。

有关修复数据库的详细信息，请参阅主题 DAO 帮助中的"RepairDatabase 方法"。

##  <a name="rollback"></a>  CDaoWorkspace::Rollback

调用此成员函数以结束当前事务和工作区中的所有数据库都还原到其条件之前开始事务。

```
void Rollback();
```

### <a name="remarks"></a>备注

> [!CAUTION]
>  在一个工作区对象，事务始终是全局性的工作区并不限于只能有一个数据库或记录集。 如果你对多个数据库或在工作区事务中，记录集执行操作`Rollback`还原所有这些数据库和记录集上的所有操作。

如果在关闭工作区对象而不保存或回滚所有挂起的事务，事务是工作自动回滚。 如果您调用[CommitTrans](#committrans)或`Rollback`没有首先调用[BeginTrans](#begintrans)，出现错误。

> [!NOTE]
>  当开始事务时，数据库引擎保存在由 TEMP 环境变量在工作站上指定的目录中的文件中记录其操作。 如果事务日志文件耗尽 TEMP 驱动器上的可用存储，数据库引擎将使 MFC 引发`CDaoException`（DAO 错误 2004年）。 此时，如果您调用`CommitTrans`、 不确定数目的操作都将提交，但剩余未完成的操作都将丢失，和该操作必须重新启动。 调用`Rollback`释放事务日志，并将回滚该事务中的所有操作。

##  <a name="setdefaultpassword"></a>  CDaoWorkspace::SetDefaultPassword

调用此成员函数可设置数据库引擎将使用特定密码的情况下创建工作区对象的默认密码。

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>参数

*lpszPassword*<br/>
默认密码。 密码可以是长度最多 14 个字符，并且可以包含除 ASCII 0 (null) 之外的任何字符。 密码是区分大小写。

### <a name="remarks"></a>备注

默认密码设置适用于在调用后创建的新工作区。 在创建后续工作区时，不需要指定密码中的[创建](#create)调用。

若要使用此成员函数：

1. 构造`CDaoWorkspace`对象，但不是调用`Create`。

1. 调用`SetDefaultPassword`并且，如果你愿意， [SetDefaultUser](#setdefaultuser)。

1. 调用`Create`对于此工作区对象或后续条件，而不在指定的密码。

默认情况下，DefaultUser 属性设置为"admin"和 DefaultPassword 属性设置为空字符串 ("")。

有关安全性的详细信息，请参阅主题 DAO 帮助中的"权限属性"。 有关相关信息，请参阅"DefaultPassword 属性"和"DefaultUser Property"DAO 帮助中的主题。

##  <a name="setdefaultuser"></a>  CDaoWorkspace::SetDefaultUser

调用此成员函数可设置数据库引擎使用时没有特定的用户名称创建一个工作区对象的默认用户名称。

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>参数

*lpszDefaultUser*<br/>
默认用户名。 用户名称是 1 到 20 个字符，包括字母字符、 重音的字符、 数字、 空格和符号除外:"（引号） / （正斜杠），\ （反斜杠）， \[ \] （方括号）: （冒号）、 &#124; (管道）、 \< (更少的登录比)，> (更高版本-号)，+ （加号）、 = （等于登录），;（分号），（逗号）、 （问号） \* （星号），前导空格和控制字符 (ASCII 00 到 ASCII 31)。 有关相关信息，请参阅主题 DAO 帮助中的"用户名属性"。

### <a name="remarks"></a>备注

默认用户名设置应用于在调用后创建的新工作区。 在创建后续工作区时，不需要指定中的用户名[创建](#create)调用。

若要使用此成员函数：

1. 构造`CDaoWorkspace`对象，但不是调用`Create`。

1. 调用`SetDefaultUser`并且，如果你愿意， [SetDefaultPassword](#setdefaultpassword)。

1. 调用`Create`对于此工作区对象或后续条件，而不指定用户名。

默认情况下，DefaultUser 属性设置为"admin"和 DefaultPassword 属性设置为空字符串 ("")。

有关相关信息，请参阅"DefaultUser 属性"和"DefaultPassword Property"DAO 帮助中的主题。

##  <a name="setinipath"></a>  CDaoWorkspace::SetIniPath

调用此成员函数以指定的 Microsoft Jet 数据库引擎的 Windows 注册表设置位置。

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>参数

*lpszRegistrySubkey*<br/>
包含一个用于 Microsoft Jet 数据库引擎设置或可安装 ISAM 数据库所需的参数的位置的 Windows 注册表子项的名称的字符串。

### <a name="remarks"></a>备注

调用`SetIniPath`仅在需要指定特殊设置。 有关详细信息，请参阅主题 DAO 帮助中的"IniPath 属性"。

> [!NOTE]
>  调用`SetIniPath`应用程序在安装期间，不应用程序运行时。 `SetIniPath` 必须在调用之前打开任何工作区、 数据库或记录集;否则，MFC 将引发异常。

此机制可用于使用用户提供的注册表设置来配置数据库引擎。 此属性的作用域仅限于你的应用程序，并且无法更改无需重新启动你的应用程序。

##  <a name="setisolateodbctrans"></a>  CDaoWorkspace::SetIsolateODBCTrans

调用此成员函数可设置工作区的 DAO IsolateODBCTrans 属性的值。

```
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>参数

*bIsolateODBCTrans*<br/>
如果你想要开始隔离 ODBC 事务，传递了 TRUE。 如果你想要停止隔离 ODBC 事务，则传递 FALSE。

### <a name="remarks"></a>备注

在某些情况下，可能需要对相同的 ODBC 数据库具有挂起的多个同时进行的事务。 若要执行此操作，您需要打开单独的工作区为每个事务。 虽然每个工作区可以有其自己的 ODBC 连接到数据库，这会降低系统性能。 由于事务隔离不是通常所需的默认情况下共享来自多个工作区对象由同一个用户打开 ODBC 连接。

某些 ODBC 服务器，例如 Microsoft SQL Server 不允许在单个连接上同时进行的事务。 如果您需要有多个事务在针对此类数据库挂起的时间，IsolateODBCTrans 属性设置为 TRUE 上每个工作区就立即打开它。 这会强制每个工作区单独的 ODBC 连接。

##  <a name="setlogintimeout"></a>  CDaoWorkspace::SetLoginTimeout

调用此成员函数可设置工作区的 DAO LoginTimeout 属性的值。

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>参数

*nSeconds*<br/>
当您尝试登录到 ODBC 数据库时，将发生错误之前等待的秒数。

### <a name="remarks"></a>备注

此值表示当您尝试登录到 ODBC 数据库时，将发生错误之前等待的秒数。 默认 LoginTimeout 设置为 20 秒的时间。 当 LoginTimeout 设置为 0 时，会发生任何超时和与数据源之间的通信可能会停止响应。

连接尝试登录到 ODBC 数据库，例如 Microsoft SQL Server 时可能会由于网络错误而失败或者因为服务器未运行。 而不是等待默认值为 20 秒的时间连接，可以指定数据库引擎等待多长时间才能生成错误。 登录到服务器发生隐式作为多个不同的事件，如外部服务器数据库上运行查询的一部分。 超时值确定由 LoginTimeout 属性的当前设置。

有关相关信息，请参阅主题 DAO 帮助中的"LoginTimeout 属性"。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException 类](../../mfc/reference/cdaoexception-class.md)
