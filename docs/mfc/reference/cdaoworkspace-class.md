---
title: CDaoWorkspace 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 52aaa4970ef483988194691eb6b870cbfe51f494
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377119"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace 类

管理单个用户从登录到注销的已命名并受密码保护的数据库会话。 通过 Office 2013 支持 DAO。 DAO 3.6 是最终版本，它被视为过时版本。

## <a name="syntax"></a>语法

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDao工作区：CDao工作区](#cdaoworkspace)|构造工作区对象。 之后，致电`Create`或`Open`。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDao工作：附加](#append)|将新创建的工作区追加到数据库引擎的工作区集合中。|
|[CDao工作：开始转换](#begintrans)|开始一个新事务，该事务适用于工作区中打开的所有数据库。|
|[CDao工作区：关闭](#close)|关闭工作区及其包含的所有对象。 挂起的事务将回滚。|
|[CDao工作区：提交转换](#committrans)|完成当前事务并保存更改。|
|[CDao工作区：压缩数据库](#compactdatabase)|压缩（或复制）数据库。|
|[CDao工作区：创建](#create)|创建新的 DAO 工作区对象。|
|[CDao工作区：获取数据库计数](#getdatabasecount)|返回工作区的数据库集合中的 DAO 数据库对象数。|
|[CDao工作区：获取数据库信息](#getdatabaseinfo)|返回有关工作区数据库集合中定义的指定 DAO 数据库的信息。|
|[CDao工作：获取IniPath](#getinipath)|在 Windows 注册表中返回 Microsoft Jet 数据库引擎的初始化设置的位置。|
|[CDao工作：获取隔离BCTrans](#getisolateodbctrans)|返回一个值，指示是否通过强制多个连接到数据源隔离涉及同一 ODBC 数据源的多个事务。|
|[CDao工作区：获取登录超时](#getlogintimeout)|返回用户尝试登录到 ODBC 数据库时发生错误的秒数。|
|[CDao工作区：获取名称](#getname)|返回工作区对象的用户定义的名称。|
|[CDao工作区：获取用户名](#getusername)|返回创建工作区时指定的用户名。 这是工作区所有者的名称。|
|[CDao工作：获取版本](#getversion)|返回包含与工作区关联的数据库引擎版本的字符串。|
|[CDao工作区：获取工作区计数](#getworkspacecount)|返回数据库引擎的工作区集合中的 DAO 工作区对象数。|
|[CDao工作空间：获取工作信息](#getworkspaceinfo)|返回有关数据库引擎工作区集合中定义的指定 DAO 工作区的信息。|
|[CDao工作区：空闲](#idle)|允许数据库引擎执行后台任务。|
|[CDao工作区：是开放的](#isopen)|如果工作区处于打开状态，则返回非零。|
|[CDao工作区：打开](#open)|显式打开与 DAO 的默认工作区关联的工作区对象。|
|[CDao工作区：修复数据库](#repairdatabase)|尝试修复损坏的数据库。|
|[CDao工作区：回滚](#rollback)|结束当前事务，不保存更改。|
|[CDao工作区：设置默认密码](#setdefaultpassword)|设置数据库引擎在没有特定密码的情况下创建工作区对象时使用的密码。|
|[CDao工作区：设置默认用户](#setdefaultuser)|设置创建没有特定用户名的工作区对象时数据库引擎使用的用户名。|
|[CDao工作区：SetIniPath](#setinipath)|在 Windows 注册表中设置 Microsoft Jet 数据库引擎的初始化设置的位置。|
|[CDao工作区：设置隔离BCTrans](#setisolateodbctrans)|指定是否通过强制多个连接到数据源来隔离涉及同一 ODBC 数据源的多个事务。|
|[CDao工作区：设置登录超时](#setlogintimeout)|设置用户尝试登录到 ODBC 数据源时发生错误的秒数。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CDao工作：m_pDAOWorkspace](#m_pdaoworkspace)|指向基础 DAO 工作区对象。|

## <a name="remarks"></a>备注

在大多数情况下，您将不需要多个工作区，并且不需要创建显式工作区对象;因此，您将不需要创建多个工作区对象。打开数据库和记录集对象时，它们将使用 DAO 的默认工作区。 但是，如果需要，可以通过创建其他工作区对象来一次运行多个会话。 每个工作区对象都可以在其自己的数据库集合中包含多个打开的数据库对象。 在 MFC 中，工作区主要是事务管理器，指定一组打开的数据库，所有这些数据库都位于相同的"事务空间"。

> [!NOTE]
> DAO 数据库类不同于基于开放数据库连接 （ODBC） 的 MFC 数据库类。 所有 DAO 数据库类名称都有"CDao"前缀。 通常，基于 DAO 的 MFC 类比基于 ODBC 的 MFC 类更有能力。 基于 DAO 的类通过 Microsoft Jet 数据库引擎访问数据，包括 ODBC 驱动程序。 它们还支持数据定义语言 （DDL） 操作，例如创建数据库并通过类添加表和字段，而无需直接调用 DAO。

## <a name="capabilities"></a>功能

类`CDaoWorkspace`提供以下内容：

- 如果需要，可以显式访问通过初始化数据库引擎创建的默认工作区。 通常，通过创建数据库和记录集对象来隐式使用 DAO 的默认工作区。

- 事务应用于工作区中打开的所有数据库的事务空间。 您可以创建其他工作区来管理单独的事务空间。

- 基础 Microsoft Jet 数据库引擎的许多属性的接口（请参阅静态成员函数）。 打开或创建工作区，或在打开或创建之前调用静态成员函数，将初始化数据库引擎。

- 访问数据库引擎的工作区集合，该集合存储已追加到它的所有活动工作区。 您还可以创建和使用工作区，而无需将它们追加到集合中。

## <a name="security"></a>安全性

MFC 不实现 DAO 中用于安全控制的用户和组集合。 如果您需要 DAO 的这些方面，则必须通过直接调用 DAO 接口自行编程。 有关详细信息，请参阅[技术说明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="usage"></a>使用情况

您可以使用类`CDaoWorkspace`：

- 显式打开默认工作区。

   通常，当您打开新的[CDao 数据库](../../mfc/reference/cdaodatabase-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象时，对默认工作区的使用是隐式的。 但是，您可能需要显式访问它 ， 例如，访问数据库引擎属性或工作区集合。 请参阅下面的"默认工作区的隐式使用"。

- 创建新工作区。 如果要将它们添加到工作区集合，请调用[附录](#append)。

- 在工作区集合中打开现有工作区。

创建工作区集合中不存在的新工作区将在["创建](#create)成员"函数下进行说明。 工作区对象不会在数据库引擎会话之间以任何方式保留。 如果应用程序以静态方式链接 MFC，则结束应用程序将取消初始化数据库引擎。 如果应用程序动态链接到 MFC，则在卸载 MFC DLL 时，数据库引擎将取消初始化。

显式打开默认工作区或在工作区集合中打开现有工作区，在["打开](#open)"成员函数下进行了说明。

通过[关闭成员函数](#close)关闭工作区，结束工作区会话。 `Close`关闭以前未关闭的任何数据库，回滚任何未提交的事务。

## <a name="transactions"></a>事务

DAO 在工作区级别管理事务;因此，具有多个打开数据库的工作区上的事务将应用于所有数据库。 例如，如果两个数据库具有未提交的更新，并且调用[CommitTrans，](#committrans)则所有更新都已提交。 如果要将事务限制为单个数据库，则需要单独的工作区对象。

## <a name="implicit-use-of-the-default-workspace"></a>隐式使用默认工作区

在以下情况下，MFC 隐式使用 DAO 的默认工作区：

- 如果创建新`CDaoDatabase`对象但不通过现有`CDaoWorkspace`对象创建，MFC 会为您创建一个临时工作区对象，该对象对应于 DAO 的默认工作区。 如果对多个数据库执行此操作，则所有数据库对象都与默认工作区相关联。 您可以通过`CDaoDatabase`数据成员访问数据库的工作区。

- 同样，如果创建`CDaoRecordset`对象而不提供指向`CDaoDatabase`对象的指针，MFC 将创建一个临时数据库对象，并通过扩展创建临时工作区对象。 您可以通过`CDaoRecordset`数据成员访问记录集的数据库，并间接访问其工作区。

## <a name="other-operations"></a>其他操作

还提供其他数据库操作，例如修复损坏的数据库或压缩数据库。

有关直接调用 DAO 的信息以及有关 DAO 安全性的信息，请参阅[技术说明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="cdaoworkspaceappend"></a><a name="append"></a>CDao工作：附加

调用[Create](#create)后调用此成员函数。

```
virtual void Append();
```

### <a name="remarks"></a>备注

`Append`将新创建的工作区对象追加到数据库引擎的工作区集合中。 工作区不会在数据库引擎会话之间保留;但是，在数据库引擎会话之间，工作区不会保留。它们只存储在内存中，而不是存储在磁盘上。 您不必追加工作区;因此，您不必追加工作区。如果没有，您仍然可以使用它。

附加工作区将保留在工作区集合中，处于活动打开状态，直到调用其[Close](#close)成员函数。

有关相关信息，请参阅 DAO 帮助中的主题"附加方法"。

## <a name="cdaoworkspacebegintrans"></a><a name="begintrans"></a>CDao工作：开始转换

调用此成员函数以启动事务。

```
void BeginTrans();
```

### <a name="remarks"></a>备注

调用`BeginTrans`后，对数据或数据库结构进行的更新在提交事务时生效。 由于工作区定义单个事务空间，因此事务将应用于工作区中的所有打开的数据库。 有两种方法可以完成事务：

- 调用[CommitTrans](#committrans)成员函数提交事务并将更改保存到数据源。

- 或者调用[回滚](#rollback)成员函数以取消事务。

在事务挂起时关闭工作区对象或数据库对象会回滚所有挂起的事务。

如果需要将一个 ODBC 数据源上的事务与另一个 ODBC 数据源上的事务隔离开来，请参阅[Set隔离ODBCTrans](#setisolateodbctrans)成员函数。

## <a name="cdaoworkspacecdaoworkspace"></a><a name="cdaoworkspace"></a>CDao工作区：CDao工作区

构造 `CDaoWorkspace` 对象。

```
CDaoWorkspace();
```

### <a name="remarks"></a>备注

构造C++对象后，有两个选项：

- 调用对象的[Open](#open)成员函数以打开默认工作区或打开工作区集合中的现有对象。

- 或者调用对象的["创建](#create)成员"函数以创建新的 DAO 工作区对象。 这将显式启动一个新的工作区会话，您可以通过对象引用该`CDaoWorkspace`会话。 调用`Create`后，如果要将工作区添加到数据库引擎的工作区集合，可以调用[附加程序](#append)。

有关何时需要显式创建 `CDaoWorkspace` 对象的信息，请参阅 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 的类概述。 通常，在打开[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象而不指定工作区时，或者在不指定数据库对象的情况下打开[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象时，可以使用隐式创建的工作区。 以这种方式创建的 MFC DAO 对象使用 DAO 的默认工作区，该工作区创建一次并重复使用。

要释放工作区及其包含的对象，请调用工作区对象的[Close](#close)成员函数。

## <a name="cdaoworkspaceclose"></a><a name="close"></a>CDao工作区：关闭

调用此成员函数以关闭工作区对象。

```
virtual void Close();
```

### <a name="remarks"></a>备注

关闭打开的工作区对象将释放基础 DAO 对象，如果工作区是工作区集合的成员，则将其从集合中删除。 调用`Close`是很好的编程实践。

> [!CAUTION]
> 关闭工作区对象将关闭工作区中的任何打开的数据库。 这将导致数据库中打开的任何记录集也关闭，并且任何挂起的编辑或更新都将回滚。 有关相关信息，请参阅[CDao 数据库：关闭](../../mfc/reference/cdaodatabase-class.md#close)[，CDaoRecordset：：关闭](../../mfc/reference/cdaorecordset-class.md#close)[，CDaoTableDef：：关闭](../../mfc/reference/cdaotabledef-class.md#close)，和[CDaoQueryDef：关闭](../../mfc/reference/cdaoquerydef-class.md#close)成员函数。

工作区对象不是永久性的;因此，工作区对象不是永久的。它们只存在于对它们的引用存在时。 这意味着当数据库引擎会话结束时，工作区及其数据库集合不会持久化。 您必须通过再次打开工作区和数据库来为下一个会话重新创建它们。

有关相关信息，请参阅 DAO 帮助中的主题"关闭方法"。

## <a name="cdaoworkspacecommittrans"></a><a name="committrans"></a>CDao工作区：提交转换

调用此成员函数以提交事务 — 保存一组编辑和更新到工作区中的一个或多个数据库。

```
void CommitTrans();
```

### <a name="remarks"></a>备注

事务包括对数据库数据或其结构的一系列更改，从调用[BeginTrans](#begintrans)开始。 完成事务后，要么提交它，要么回滚（取消更改），使用[回滚](#rollback)。 默认情况下，在没有事务的情况下，将立即提交对记录的更新。 调用`BeginTrans`会导致更新的承诺延迟到调用`CommitTrans`。

> [!CAUTION]
> 在一个工作区中，事务始终是工作区的全局事务，并且不仅限于一个数据库或记录集。 如果对工作区事务中的多个数据库或记录集执行操作，则`CommitTrans`提交所有挂起的更新，并`Rollback`还原这些数据库和记录集上的所有操作。

当您关闭具有挂起事务的数据库或工作区时，这些事务都将回滚。

> [!NOTE]
> 这不是两阶段提交机制。 如果一个更新无法提交，其他更新仍将提交。

## <a name="cdaoworkspacecompactdatabase"></a><a name="compactdatabase"></a>CDao工作区：压缩数据库

调用此成员函数以压缩指定的 Microsoft Jet （。MDB）数据库。

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

*lpszSrc名称*<br/>
现有已关闭数据库的名称。 它可以是完整的路径和文件名，如"C：\MYDB"。\\MDB"。 如果文件名具有扩展名，则必须指定它。 如果您的网络支持统一的命名约定 （UNC），您还可以指定网络路径，例如"_MYSERVER\\\\\\\\_MYSHARE\\\\\MYDIR _MYDB"。MDB"。 （路径字符串中需要双背斜杠，因为""\\是C++转义字符。

*lpszDest 名称*<br/>
要创建压缩数据库的完整路径。 您还可以指定网络路径与*lpszSrcName*一样。 不能使用*lpszDestName*参数指定与*lpszSrcName*相同的数据库文件。

*lpsz密码*<br/>
密码，用于压缩受密码保护的数据库。 请注意，如果使用的密码版本`CompactDatabase`，则必须提供所有参数。 此外，由于这是连接参数，它需要特殊的格式，如下所示：PWD= *lpsz密码*。 例如：PWD="快乐"。 （需要前导分号。

*lpszLocale*<br/>
用于指定用于创建*lpszDestName 的*排序的字符串表达式。 如果通过接受 的`dbLangGeneral`默认值（见下文）省略此参数，则新数据库的区位设置与旧数据库的区值相同。 可能的值包括：

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

*n选项*<br/>
指示目标数据库的一个或多个选项 *，lpszDestName*。 如果通过接受默认值省略此参数，*则 lpszDestName*将具有相同的加密和与*lpszSrcName*相同的版本。 您可以使用位`dbEncrypt`-OR`dbDecrypt`运算符将 或 选项与其中一个版本选项合并。 指定数据库格式（而不是数据库引擎版本）的可能值是：

- `dbEncrypt`压缩时加密数据库。

- `dbDecrypt`压缩时解密数据库。

- `dbVersion10`创建一个数据库，该数据库在压缩时使用 Microsoft Jet 数据库引擎版本 1.0。

- `dbVersion11`创建一个数据库，该数据库在压缩时使用 Microsoft Jet 数据库引擎版本 1.1。

- `dbVersion20`创建一个数据库，该数据库在压缩时使用 Microsoft Jet 数据库引擎版本 2.0。

- `dbVersion30`创建一个数据库，该数据库在压缩时使用 Microsoft Jet 数据库引擎版本 3.0。

您可以使用`dbEncrypt`或`dbDecrypt`在选项参数中指定是加密还是解密数据库。 如果省略`dbDecrypt`了加密常量，或者如果同时包含 和`dbEncrypt`，则*lpszDestName*将具有与*lpszSrcName*相同的加密。 可以使用选项参数中的一个版本常量来指定压缩数据库的数据格式版本。 此常量仅影响*lpszDestName*的数据格式的版本。 只能指定一个版本常量。 如果省略版本常量 *，lpszDestName*将具有与*lpszSrcName*相同的版本。 您只能将*lpszDestName*压缩到与*lpszSrcName*相同或更晚的版本。

> [!CAUTION]
> 如果数据库未加密，即使您实现了用户/密码安全性，也可以直接读取构成数据库的二进制磁盘文件。

### <a name="remarks"></a>备注

更改数据库中的数据时，数据库文件可能会变得碎片化，并且使用超过必要的磁盘空间。 应定期压缩数据库以碎片整理数据库文件。 压缩的数据库通常较小。 您还可以选择在复制和压缩数据库时更改整理顺序、加密或数据格式的版本。

> [!CAUTION]
> 成员`CompactDatabase`函数无法将完整的 Microsoft Access 数据库从一个版本正确转换为另一个版本。 仅转换数据格式。 不会转换 Microsoft 访问定义的对象（如窗体和报表）。 但是，数据将正确转换。

> [!TIP]
> 您还可以使用`CompactDatabase`复制数据库文件。

有关压缩数据库的详细信息，请参阅 DAO 帮助中的主题"压缩数据库方法"。

## <a name="cdaoworkspacecreate"></a><a name="create"></a>CDao工作区：创建

调用此成员函数以创建新的 DAO 工作区对象并将其与 MFC`CDaoWorkspace`对象关联。

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
具有最多 14 个字符的字符串，用于为新工作区对象唯一命名。 您必须提供名称。 有关相关信息，请参阅 DAO 帮助中的主题"名称属性"。

*lpszUser名称*<br/>
工作区所有者的用户名。 有关要求，请参阅["设置默认用户"](#setdefaultuser)成员函数的*lpszDefaultUser*参数。 有关相关信息，请参阅 DAO 帮助中的"用户名属性"主题。

*lpsz密码*<br/>
新工作区对象的密码。 密码最多只能长 14 个字符，并且可以包含除 ASCII 0（空）以外的任何字符。 密码是区分大小写的。 有关相关信息，请参阅 DAO 帮助中的主题"密码属性"。

### <a name="remarks"></a>备注

整个创建过程是：

1. 构造[CDao 工作区](#cdaoworkspace)对象。

1. 调用对象`Create`的成员函数以创建基础 DAO 工作区。 必须指定工作区名称。

1. 如果要将工作区添加到数据库引擎的工作区集合，则可以调用[附加程序](#append)。 您可以使用工作区，而无需附加它。

`Create`调用后，工作区对象处于打开状态，可供使用。 您不会在 之后`Open``Create`打电话。 如果工作区集合中`Create`已存在工作区，则不调用该工作区。 `Create`如果数据库引擎尚未为应用程序初始化，则初始化数据库引擎。

## <a name="cdaoworkspacegetdatabasecount"></a><a name="getdatabasecount"></a>CDao工作区：获取数据库计数

调用此成员函数以检索工作区的数据库集合中的 DAO 数据库对象数 - 工作区中的打开数据库数。

```
short GetDatabaseCount();
```

### <a name="return-value"></a>返回值

工作区中的打开数据库数。

### <a name="remarks"></a>备注

`GetDatabaseCount`如果需要循环访问工作区的数据库集合中的所有已定义的数据库，则非常有用。 要获取有关集合中给定数据库的信息，请参阅[GetDatabaseInfo](#getdatabaseinfo)。 典型用法是调用`GetDatabaseCount`打开的数据库数，然后将该数字用作重复调用`GetDatabaseInfo`的循环索引。

## <a name="cdaoworkspacegetdatabaseinfo"></a><a name="getdatabaseinfo"></a>CDao工作区：获取数据库信息

调用此成员函数以获取有关工作区中打开的数据库的各种信息。

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
工作区的"数据库"集合中数据库对象的零基索引，用于按索引查找。

*德布福*<br/>
对返回请求的信息的[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)对象的引用。

*dwInfoOptions*<br/>
指定要检索的数据库信息的选项。 此处列出了可用的选项以及它们导致函数返回的内容：

- AFX_DAO_PRIMARY_INFO（默认）名称、可上可交易、交易记录

- AFX_DAO_SECONDARY_INFO主要信息加上：版本、整理顺序、查询超时

- AFX_DAO_ALL_INFO主和辅助信息加上：连接

*lpsz名称*<br/>
数据库对象的名称，用于按名称查找。 该名称是一个字符串，最多包含 14 个字符，用于唯一命名新工作区对象。

### <a name="remarks"></a>备注

函数的一个版本允许您按索引查找数据库。 另一个版本允许您按名称查找数据库。

有关*dbinfo*中返回的信息的说明，请参阅[CDao 数据库信息](../../mfc/reference/cdaodatabaseinfo-structure.md)结构。 此结构的成员对应于*dwInfoOptions*描述中列出的信息项。 当您在一个级别请求信息时，您也获取任何先前级别的信息。

## <a name="cdaoworkspacegetinipath"></a><a name="getinipath"></a>CDao工作：获取IniPath

调用此成员函数以获取 Microsoft Jet 数据库引擎在 Windows 注册表中的初始化设置的位置。

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>返回值

包含注册表位置的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>备注

您可以使用该位置获取有关数据库引擎设置的信息。 返回的信息实际上是注册表子键的名称。

有关相关信息，请参阅 DAO 帮助中的"IniPath 属性"和"自定义数据访问的 Windows 注册表设置"的主题。

## <a name="cdaoworkspacegetisolateodbctrans"></a><a name="getisolateodbctrans"></a>CDao工作：获取隔离BCTrans

调用此成员函数获取工作区的 DAO 隔离ODBCTrans 属性的当前值。

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>返回值

如果 ODBC 事务是隔离的，则非零;否则 0。

### <a name="remarks"></a>备注

在某些情况下，您可能需要在同一 ODBC 数据库上同时挂起多个事务。 为此，您需要为每个事务打开单独的工作区。 请记住，尽管每个工作区都可以具有与数据库的 ODBC 连接，但这会降低系统性能。 由于通常不需要事务隔离，因此默认情况下共享同一用户打开的多个工作区对象的 ODBC 连接。

某些 ODBC 服务器（如 Microsoft SQL Server）不允许在单个连接上同时进行事务。 如果需要一次有多个事务针对此类数据库挂起，则在打开每个工作区时将隔离ODBCTrans属性设置为 TRUE。 这将强制为每个工作区建立单独的 ODBC 连接。

有关相关信息，请参阅 DAO 帮助中的主题"隔离ODBCTrans属性"。

## <a name="cdaoworkspacegetlogintimeout"></a><a name="getlogintimeout"></a>CDao工作区：获取登录超时

调用此成员函数获取工作区的 DAO 登录超时属性的当前值。

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>返回值

尝试登录到 ODBC 数据库时出错前的秒数。

### <a name="remarks"></a>备注

此值表示尝试登录到 ODBC 数据库时发生错误的秒数。 默认的登录超时设置为 20 秒。 当 LoginTimeout 设置为 0 时，不会发生超时，并且与数据源的通信可能会停止响应。

当您尝试登录到 ODBC 数据库（如 Microsoft SQL Server）时，连接可能会由于网络错误或服务器未运行而失败。 您可以指定数据库引擎在生成错误之前等待多长时间，而不是等待默认的 20 秒连接。 登录到服务器是许多不同事件的一部分，例如在外部服务器数据库上运行查询。

有关相关信息，请参阅 DAO 帮助中的"登录超时属性"主题。

## <a name="cdaoworkspacegetname"></a><a name="getname"></a>CDao工作区：获取名称

调用此成员函数以获取`CDaoWorkspace`对象基础的 DAO 工作区对象的用户定义的名称。

```
CString GetName();
```

### <a name="return-value"></a>返回值

包含 DAO 工作区对象的用户定义名称的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>备注

该名称可用于按名称访问数据库引擎的工作区集合中的 DAO 工作区对象。

有关相关信息，请参阅 DAO 帮助中的主题"名称属性"。

## <a name="cdaoworkspacegetusername"></a><a name="getusername"></a>CDao工作区：获取用户名

调用此成员函数以获取工作区所有者的名称。

```
CString GetUserName();
```

### <a name="return-value"></a>返回值

表示工作区对象所有者的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>备注

要获取或设置工作区所有者的权限，请直接调用 DAO 以检查"权限"属性设置;否则，请直接调用 DAO 以检查"权限"属性设置。这将确定用户具有的权限。 要使用权限，您需要一个 SYSTEM。MDA 文件。

有关直接调用 DAO 的信息，请参阅[技术说明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。 有关相关信息，请参阅 DAO 帮助中的"用户名属性"主题。

## <a name="cdaoworkspacegetversion"></a><a name="getversion"></a>CDao工作：获取版本

调用此成员函数以确定正在使用的 Microsoft Jet 数据库引擎的版本。

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>返回值

指示与对象关联的数据库引擎的版本的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>备注

返回的值表示窗体"主要.minor"中的版本号;例如，"3.0"。 产品版本号（例如 3.0）由版本号 （3）、句点和发行号 （0） 组成。

有关相关信息，请参阅 DAO 帮助中的主题"版本属性"。

## <a name="cdaoworkspacegetworkspacecount"></a><a name="getworkspacecount"></a>CDao工作区：获取工作区计数

调用此成员函数以检索数据库引擎工作区集合中的 DAO 工作区对象数。

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>返回值

工作区集合中的打开工作区数。

### <a name="remarks"></a>备注

此计数不包括未追加到集合中的任何打开工作区。 `GetWorkspaceCount`如果需要循环访问工作区集合中的所有已定义的工作区，则非常有用。 要获取有关集合中给定工作区的信息，请参阅[GetWorkspaceInfo](#getworkspaceinfo)。 典型用法是调用`GetWorkspaceCount`打开工作区的数量，然后将该数字用作重复调用`GetWorkspaceInfo`的循环索引。

## <a name="cdaoworkspacegetworkspaceinfo"></a><a name="getworkspaceinfo"></a>CDao工作空间：获取工作信息

调用此成员函数以获取有关会话中打开的工作区的各种信息。

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
工作区集合中数据库对象的零基索引，用于按索引查找。

*沃克斯普福*<br/>
对返回请求的信息的[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)对象的引用。

*dwInfoOptions*<br/>
指定要检索的工作区的信息的选项。 此处列出了可用的选项以及它们导致函数返回的内容：

- AFX_DAO_PRIMARY_INFO（默认）名称

- AFX_DAO_SECONDARY_INFO主要信息加：用户名

- AFX_DAO_ALL_INFO主要和次要信息加上：隔离 ODBCTrans

*lpsz名称*<br/>
工作区对象的名称，用于按名称查找。 该名称是一个字符串，最多包含 14 个字符，用于唯一命名新工作区对象。

### <a name="remarks"></a>备注

有关在*wkspcinfo 中*返回的信息的说明，请参阅[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)结构。 此结构的成员对应于*dwInfoOptions*描述中列出的信息项。 当您在一个级别请求信息时，您也会得到以前级别的信息。

## <a name="cdaoworkspaceidle"></a><a name="idle"></a>CDao工作区：空闲

调用`Idle`为数据库引擎提供执行由于数据处理密集而可能不是最新的后台任务的机会。

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>参数

*nAction*<br/>
在空闲处理期间执行的操作。 目前唯一有效的操作是`dbFreeLocks`。

### <a name="remarks"></a>备注

在多用户多任务处理环境中，通常如此，在这种环境中，没有足够的后台处理时间来保持记录集中的所有记录。

> [!NOTE]
> 使用`Idle`Microsoft Jet 数据库引擎的 3.0 版本创建的数据库不需要调用。 仅适用于`Idle`使用早期版本的数据库。

通常，读取锁被删除，并且仅当没有发生其他操作（包括鼠标移动）时，才会更新本地动态集类型记录集对象中的数据。 如果定期调用`Idle`，则通过释放不需要的读取锁，为数据库引擎提供时间来跟踪后台处理任务。 指定`dbFreeLocks`常量作为参数延迟处理，直到释放所有读取锁。

除非应用程序有多个实例正在运行，否则在单用户环境中不需要此成员函数。 成员`Idle`函数可能会提高多用户环境中的性能，因为它强制数据库引擎将数据刷新到磁盘，从而释放内存上的锁。 还可以通过使操作成为事务的一部分来释放读取锁。

有关相关信息，请参阅 DAO 帮助中的主题"空闲方法"。

## <a name="cdaoworkspaceisopen"></a><a name="isopen"></a>CDao工作区：是开放的

调用此成员函数以确定`CDaoWorkspace`对象是否打开，即 MFC 对象是否已通过调用[Open](#open)或对[Create](#create)进行初始化。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果工作区对象处于打开状态，则非零;否则 0。

### <a name="remarks"></a>备注

可以调用处于打开状态的工作区的任何成员函数。

## <a name="cdaoworkspacem_pdaoworkspace"></a><a name="m_pdaoworkspace"></a>CDao工作：m_pDAOWorkspace

指向基础 DAO 工作区对象的指针。

### <a name="remarks"></a>备注

如果需要直接访问基础 DAO 对象，请使用此数据成员。 可以通过此指针调用 DAO 对象的接口。

有关直接访问 DAO 对象的信息，请参阅[技术说明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="cdaoworkspaceopen"></a><a name="open"></a>CDao工作区：打开

显式打开与 DAO 的默认工作区关联的工作区对象。

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
要打开的 DAO 工作区对象的名称 - 具有最多 14 个字符的字符串，该字符串对工作区进行唯一命名。 接受默认值 NULL 以显式打开默认工作区。 有关命名要求，请参阅[创建](#create)的*lpszName*参数。 有关相关信息，请参阅 DAO 帮助中的主题"名称属性"。

### <a name="remarks"></a>备注

构造`CDaoWorkspace`对象后，调用此成员函数执行以下操作之一：

- 显式打开默认工作区。 通过 NULL 表示*lpszName*。

- 按名称打开`CDaoWorkspace`现有对象（工作区集合的成员）。 传递现有工作区对象的有效名称。

`Open`将工作区对象置于打开状态，如果尚未为应用程序初始化数据库引擎，则还会初始化数据库引擎。

尽管许多`CDaoWorkspace`成员函数只能在打开工作区后调用，但在构造C++对象后，但在调用`Open`：

||||
|-|-|-|
|[创建](#create)|[获取版本](#getversion)|[设置默认用户](#setdefaultuser)|
|[获取 Iinpath](#getinipath)|[Idle](#idle)|[设置IniPath](#setinipath)|
|[获取登录超时](#getlogintimeout)|[设置默认密码](#setdefaultpassword)|[设置登录超时](#setlogintimeout)|

## <a name="cdaoworkspacerepairdatabase"></a><a name="repairdatabase"></a>CDao工作区：修复数据库

如果需要尝试修复访问 Microsoft Jet 数据库引擎的损坏数据库，请调用此成员函数。

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
现有 Microsoft Jet 引擎数据库文件的路径和文件名。 如果省略路径，则仅搜索当前目录。 如果您的系统支持统一的命名约定 （UNC），您还可以\\\\\\指定网络路径，例如："\MYSERVER\\_MYSHARE\\\\\MYDIR \MYDB。MDB"。 （路径字符串中需要双背斜杠，因为""\\是C++转义字符。

### <a name="remarks"></a>备注

在修复数据库之前，必须关闭*lpszName*指定的数据库。 在多用户环境中，其他用户在修复 lpszName 时无法打开*lpszName。* 如果*lpszName*未关闭或不能独占使用，则会发生错误。

此成员函数尝试修复被不完整写入操作标记为可能损坏的数据库。 如果使用 Microsoft Jet 数据库引擎的应用程序由于停电或计算机硬件问题而意外关闭，则可能发生此情况。 如果完成该操作并调用[Close](../../mfc/reference/cdaodatabase-class.md#close)成员函数，或者以通常的方式退出应用程序，则数据库将不会标记为可能已损坏。

> [!NOTE]
> 修复数据库后，最好使用[CompactDatabase](#compactdatabase)成员函数压缩它，以碎片整理文件并恢复磁盘空间。

有关修复数据库的详细信息，请参阅 DAO 帮助中的主题"修复数据库方法"。

## <a name="cdaoworkspacerollback"></a><a name="rollback"></a>CDao工作区：回滚

调用此成员函数以结束当前事务，并在事务开始之前将工作区中的所有数据库还原到其条件。

```
void Rollback();
```

### <a name="remarks"></a>备注

> [!CAUTION]
> 在一个工作区对象中，事务始终是工作区的全局事务，并且不仅限于一个数据库或记录集。 如果对工作区事务中的多个数据库或记录集执行操作，则`Rollback`还原所有这些数据库和记录集上的所有操作。

如果关闭工作区对象而不保存或回滚任何挂起的事务，则事务将自动回滚。 如果您调用[CommitTrans](#committrans) `Rollback`或没有首先调用[BeginTrans，](#begintrans)则会发生错误。

> [!NOTE]
> 开始事务时，数据库引擎将其操作记录在工作站上的 TEMP 环境变量指定的目录中的文件中。 如果事务日志文件耗尽了 TEMP 驱动器上的可用存储，则数据库引擎将导致 MFC 引发 （DAO`CDaoException`错误 2004）。 此时，如果调用`CommitTrans`，将提交不确定数量的操作，但剩余的未完成的操作将丢失，并且必须重新启动该操作。 调用`Rollback`将释放事务日志并回滚事务中的所有操作。

## <a name="cdaoworkspacesetdefaultpassword"></a><a name="setdefaultpassword"></a>CDao工作区：设置默认密码

调用此成员函数以设置数据库引擎在没有特定密码的情况下创建工作区对象时使用的默认密码。

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>参数

*lpsz密码*<br/>
默认密码。 密码最多只能长 14 个字符，并且可以包含除 ASCII 0（空）以外的任何字符。 密码是区分大小写的。

### <a name="remarks"></a>备注

您设置的默认密码应用于调用后创建的新工作区。 创建后续工作区时，不需要在["创建](#create)"调用中指定密码。

要使用此成员函数：

1. 构造`CDaoWorkspace`对象但不调用`Create`。

1. 打电话`SetDefaultPassword`，如果您愿意，[请设置默认用户](#setdefaultuser)。

1. 调用`Create`此工作区对象或后续对象，而不指定密码。

默认情况下，默认用户属性设置为"管理员"，默认密码属性设置为空字符串 （""）。

有关安全性的详细信息，请参阅 DAO 帮助中的主题"权限属性"。 有关相关信息，请参阅 DAO 帮助中的"默认密码属性"和"默认用户属性"主题。

## <a name="cdaoworkspacesetdefaultuser"></a><a name="setdefaultuser"></a>CDao工作区：设置默认用户

调用此成员函数以设置数据库引擎在没有特定用户名的情况下创建工作区对象时使用的默认用户名。

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>参数

*lpszDefaultUser*<br/>
默认用户名。 用户名可以是 1 - 20 个字符长，包括字母字符、重音字符、数字、空格和符号，但："（引号）、/（前斜杠）、*（斜杠）、（括号\[\]）、：（冒号）、&#124;（管道）、（小于\<符号）、>（大于符号）、*（加号）、*（等号）;（分号）、、、（逗号）、（问号\*）、（星号）、前导空格和控制字符（ASCII 00 到 ASCII 31）。 有关相关信息，请参阅 DAO 帮助中的"用户名属性"主题。

### <a name="remarks"></a>备注

您设置的默认用户名将应用于调用后创建的新工作区。 创建后续工作区时，不需要在["创建](#create)"调用中指定用户名。

要使用此成员函数：

1. 构造`CDaoWorkspace`对象但不调用`Create`。

1. 打电话`SetDefaultUser`，如果您愿意，[请设置默认密码](#setdefaultpassword)。

1. 调用`Create`此工作区对象或后续对象，而不指定用户名。

默认情况下，默认用户属性设置为"管理员"，默认密码属性设置为空字符串 （""）。

有关相关信息，请参阅 DAO 帮助中的"默认用户属性"和"默认密码属性"主题。

## <a name="cdaoworkspacesetinipath"></a><a name="setinipath"></a>CDao工作区：SetIniPath

调用此成员函数以指定 Microsoft Jet 数据库引擎的 Windows 注册表设置的位置。

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>参数

*lpsz注册子键*<br/>
包含 Windows 注册表子键名称的字符串，用于 Microsoft Jet 数据库引擎设置的位置或可安装 ISAM 数据库所需的参数。

### <a name="remarks"></a>备注

仅当`SetIniPath`需要指定特殊设置时才调用。 有关详细信息，请参阅 DAO 帮助中的主题"IniPath 属性"。

> [!NOTE]
> 在`SetIniPath`应用程序安装期间调用，而不是在应用程序运行时调用。 `SetIniPath`在打开任何工作区、数据库或记录集之前，必须调用;否则，MFC 会引发异常。

您可以使用此机制使用用户提供的注册表设置配置数据库引擎。 此属性的范围仅限于您的应用程序，如果不重新启动应用程序，则无法更改。

## <a name="cdaoworkspacesetisolateodbctrans"></a><a name="setisolateodbctrans"></a>CDao工作区：设置隔离BCTrans

调用此成员函数以设置工作区的 DAO 隔离ODBCTrans 属性的值。

```
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>参数

*b 隔离ODBCTrans*<br/>
如果要开始隔离 ODBC 事务，则传递 TRUE。 如果要停止隔离 ODBC 事务，则传递 FALSE。

### <a name="remarks"></a>备注

在某些情况下，您可能需要在同一 ODBC 数据库上同时挂起多个事务。 为此，您需要为每个事务打开单独的工作区。 尽管每个工作区都可以有自己的 ODBC 连接到数据库，但这会降低系统性能。 由于通常不需要事务隔离，因此默认情况下共享同一用户打开的多个工作区对象的 ODBC 连接。

某些 ODBC 服务器（如 Microsoft SQL Server）不允许在单个连接上同时进行事务。 如果需要一次有多个事务针对此类数据库挂起，则在打开每个工作区时将隔离ODBCTrans属性设置为 TRUE。 这将强制为每个工作区建立单独的 ODBC 连接。

## <a name="cdaoworkspacesetlogintimeout"></a><a name="setlogintimeout"></a>CDao工作区：设置登录超时

调用此成员函数以设置工作区的 DAO 登录超时属性的值。

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>参数

*n 秒*<br/>
尝试登录到 ODBC 数据库时出错前的秒数。

### <a name="remarks"></a>备注

此值表示尝试登录到 ODBC 数据库时发生错误的秒数。 默认的登录超时设置为 20 秒。 当 LoginTimeout 设置为 0 时，不会发生超时，并且与数据源的通信可能会停止响应。

当您尝试登录到 ODBC 数据库（如 Microsoft SQL Server）时，连接可能会由于网络错误或服务器未运行而失败。 您可以指定数据库引擎在生成错误之前等待多长时间，而不是等待默认的 20 秒连接。 登录到服务器是许多不同事件的一部分，例如在外部服务器数据库上运行查询。 超时值由 LoginTimeout 属性的当前设置决定。

有关相关信息，请参阅 DAO 帮助中的"登录超时属性"主题。

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDao记录组类](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException 类](../../mfc/reference/cdaoexception-class.md)
