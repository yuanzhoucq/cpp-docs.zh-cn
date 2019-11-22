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
ms.openlocfilehash: c1d235035cee9342c8c54c7aaa4e05a96d5a37e3
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303474"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace 类

管理单个用户从登录到注销的已命名并受密码保护的数据库会话。 DAO 受 Office 2013 的支持。 DAO 3.6 是最终版本，被视为已过时。

## <a name="syntax"></a>语法

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|构造工作区对象。 然后，调用 `Create` 或 `Open`。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDaoWorkspace::Append](#append)|将新创建的工作区追加到数据库引擎的工作区集合。|
|[CDaoWorkspace::BeginTrans](#begintrans)|开始一个新事务，该事务应用于工作区中打开的所有数据库。|
|[CDaoWorkspace::Close](#close)|关闭工作区及其包含的所有对象。 挂起的事务将回滚。|
|[CDaoWorkspace::CommitTrans](#committrans)|完成当前事务，并保存所做的更改。|
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|压缩（或复制）数据库。|
|[CDaoWorkspace::Create](#create)|创建新的 DAO 工作区对象。|
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|返回工作区的数据库集合中的 DAO 数据库对象数。|
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|返回有关工作区的数据库集合中定义的指定 DAO 数据库的信息。|
|[CDaoWorkspace::GetIniPath](#getinipath)|返回 Microsoft Jet 数据库引擎的初始化设置在 Windows 注册表中的位置。|
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|返回一个值，该值指示是否通过强制多个到数据源的连接隔离涉及同一 ODBC 数据源的多个事务。|
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|返回当用户尝试登录到 ODBC 数据库时发生错误之前等待的秒数。|
|[CDaoWorkspace::GetName](#getname)|返回工作区对象的用户定义名称。|
|[CDaoWorkspace::GetUserName](#getusername)|返回在创建工作区时指定的用户名。 这是工作区所有者的名称。|
|[CDaoWorkspace::GetVersion](#getversion)|返回一个字符串，该字符串包含与工作区关联的数据库引擎的版本。|
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|返回数据库引擎的工作区集合中 DAO 工作区对象的数量。|
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|返回有关在数据库引擎的工作区集合中定义的指定 DAO 工作区的信息。|
|[CDaoWorkspace::Idle](#idle)|允许数据库引擎执行后台任务。|
|[CDaoWorkspace::IsOpen](#isopen)|如果工作区打开，则返回非零值。|
|[CDaoWorkspace::Open](#open)|显式打开与 DAO 的默认工作区关联的工作区对象。|
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|尝试修复已损坏的数据库。|
|[CDaoWorkspace::Rollback](#rollback)|结束当前事务，不保存所做的更改。|
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|设置在创建工作区对象时，如果没有特定密码，数据库引擎所使用的密码。|
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|设置在创建工作区对象时，数据库引擎使用的用户名没有特定的用户名。|
|[CDaoWorkspace::SetIniPath](#setinipath)|设置 Microsoft Jet 数据库引擎的初始化设置在 Windows 注册表中的位置。|
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|指定是否隔离涉及同一 ODBC 数据源的多个事务，方法是强制执行到数据源的多个连接。|
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|设置当用户尝试登录到 ODBC 数据源时发生错误之前等待的秒数。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|指向基础 DAO 工作区对象。|

## <a name="remarks"></a>备注

在大多数情况下，你将不需要多个工作区，并且无需创建显式工作区对象;打开数据库和记录集对象时，它们使用 DAO 的默认工作区。 但是，如果需要，可以通过创建其他工作区对象一次运行多个会话。 每个工作区对象可以在其自身的数据库集合中包含多个打开的数据库对象。 在 MFC 中，工作区主要是一种事务管理器，它在同一 "事务空间" 中指定一组打开的数据库。

> [!NOTE]
>  DAO 数据库类与基于开放式数据库连接（ODBC）的 MFC 数据库类不同。 所有 DAO 数据库类名称都具有 "CDao" 前缀。 通常，基于 DAO 的 MFC 类比基于 ODBC 的 MFC 类更强大。 基于 DAO 的类通过 Microsoft Jet 数据库引擎（包括 ODBC 驱动程序）访问数据。 它们还支持数据定义语言（DDL）操作，例如创建数据库和通过类添加表和字段，而无需直接调用 DAO。

## <a name="capabilities"></a>功能

类 `CDaoWorkspace` 提供以下内容：

- 如果需要，可通过初始化数据库引擎创建的默认工作区进行显式访问。 通常，可以通过创建数据库和记录集对象隐式地使用 DAO 的默认工作区。

- 事务空间，其中事务应用于工作区中打开的所有数据库。 您可以创建其他工作区来管理单独的事务空间。

- 基础 Microsoft Jet 数据库引擎的多个属性的接口（请参见静态成员函数）。 打开或创建工作区，或在打开或创建之前调用静态成员函数，初始化数据库引擎。

- 访问数据库引擎的工作区集合，该集合存储追加到它的所有活动工作区。 你还可以创建和使用工作区，而无需将其追加到集合。

## <a name="security"></a>安全

MFC 不实现 DAO 中的用户和组集合，这些集合用于安全控制。 如果需要 DAO 的这些方面，则必须通过直接调用 DAO 接口自行进行编程。 有关信息，请参阅[技术说明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="usage"></a>用法

可以使用类 `CDaoWorkspace` 来执行以下操作：

- 显式打开默认工作区。

   通常，在打开新的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象时，默认工作区的使用是隐式的。 但您可能需要显式访问它，例如，访问数据库引擎属性或工作区集合。 请参阅下面的 "隐式使用默认工作区"。

- 创建新工作区。 如果要将其添加到工作区集合，请调用[Append](#append) 。

- 打开工作区集合中的现有工作区。

[创建](#create)成员函数下面介绍了如何创建工作区集合中尚不存在的新工作区。 工作区对象不会以任何方式在数据库 engine 会话之间保持。 如果你的应用程序静态链接 MFC，则结束取消数据库引擎的应用程序。 如果你的应用程序动态地与 MFC 链接，则在卸载 MFC DLL 时，数据库引擎将处于未初始化状态。

若要在工作区集合中显式打开默认工作区或打开现有的工作区，请参阅[打开](#open)成员函数。

通过[关闭包含 Close](#close)成员函数的工作区来结束工作区会话。 `Close` 关闭先前未关闭的任何数据库，回滚所有未提交的事务。

## <a name="transactions"></a>事务

DAO 在工作区级别管理事务;因此，具有多个打开数据库的工作区中的事务适用于所有数据库。 例如，如果两个数据库有未提交的更新，并且你调用[CommitTrans](#committrans)，则会提交所有更新。 如果要将事务限制为单个数据库，则需要为其提供单独的工作区对象。

## <a name="implicit-use-of-the-default-workspace"></a>隐式使用默认工作区

MFC 在下列情况下隐式使用 DAO 的默认工作区：

- 如果创建一个新的 `CDaoDatabase` 对象但未通过现有的 `CDaoWorkspace` 对象执行此操作，则 MFC 将为您创建一个临时工作区对象，这对应于 DAO 的默认工作区。 如果对多个数据库执行此操作，则所有数据库对象都与默认工作区关联。 可以通过 `CDaoDatabase` 数据成员访问数据库的工作区。

- 同样，如果在不提供指向 `CDaoDatabase` 对象的指针的情况下创建 `CDaoRecordset` 对象，MFC 会创建一个临时的数据库对象，并通过扩展来创建一个临时工作区对象。 您可以通过 `CDaoRecordset` 数据成员访问记录集的数据库，并间接地访问其工作区。

## <a name="other-operations"></a>其他操作

还提供了其他数据库操作，例如修复损坏的数据库或压缩数据库。

有关直接调用 DAO 和 DAO 安全性的信息，请参阅[技术说明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>要求

**标头：** afxdao.h

##  <a name="append"></a>CDaoWorkspace：： Append

调用[Create](#create)后调用此成员函数。

```
virtual void Append();
```

### <a name="remarks"></a>备注

`Append` 将新创建的工作区对象追加到数据库引擎的工作区集合。 工作区不会在数据库引擎会话之间保持不变;它们仅存储在内存中，而不是存储在磁盘上。 你不必追加工作区;否则，仍然可以使用它。

追加的工作区将保留在工作区集合中（处于活动的打开状态），直到调用其[Close](#close)成员函数。

有关相关信息，请参阅 DAO 帮助中的主题 "Append 方法"。

##  <a name="begintrans"></a>CDaoWorkspace：： BeginTrans

调用此成员函数以启动事务。

```
void BeginTrans();
```

### <a name="remarks"></a>备注

调用 `BeginTrans`后，在提交事务时，对数据或数据库结构所做的更新将会生效。 由于工作区定义了单个事务空间，因此该事务适用于工作区中的所有打开的数据库。 可以通过两种方法来完成事务：

- 调用[CommitTrans](#committrans)成员函数以提交事务，并将更改保存到数据源。

- 或调用[Rollback](#rollback)成员函数以取消事务。

当事务处于挂起状态时关闭工作区对象或数据库对象将回滚所有挂起的事务。

如果需要将一个 ODBC 数据源上的事务与另一个 ODBC 数据源上的事务隔离开来，请参阅[SetIsolateODBCTrans](#setisolateodbctrans)成员函数。

##  <a name="cdaoworkspace"></a>CDaoWorkspace::CDaoWorkspace

构造 `CDaoWorkspace` 对象。

```
CDaoWorkspace();
```

### <a name="remarks"></a>备注

构造C++对象后，可以使用两个选项：

- 调用对象的[open](#open) member 函数以打开默认工作区，或打开工作区集合中的现有对象。

- 或者调用对象的[create](#create)成员函数来创建新的 DAO 工作区对象。 这会显式启动新的工作区会话，你可以通过 `CDaoWorkspace` 对象对其进行引用。 调用 `Create`后，如果要将工作区添加到数据库引擎的工作区集合，可以调用[Append](#append) 。

有关何时需要显式创建 [ 对象的信息，请参阅 ](../../mfc/reference/cdaoworkspace-class.md)CDaoWorkspace`CDaoWorkspace` 的类概述。 通常情况下，如果在未指定工作区的情况下打开[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象，或在未指定数据库对象的情况下打开[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象，则会使用隐式创建的工作区。 以这种方式创建的 MFC DAO 对象使用 DAO 的默认工作区，该工作区将创建一次并重复使用。

若要释放工作区及其包含的对象，请调用工作区对象的[Close](#close)成员函数。

##  <a name="close"></a>CDaoWorkspace：： Close

调用此成员函数以关闭工作区对象。

```
virtual void Close();
```

### <a name="remarks"></a>备注

关闭打开的工作区对象会释放基础 DAO 对象，如果工作区是工作区集合的成员，则会将其从集合中移除。 调用 `Close` 是良好的编程做法。

> [!CAUTION]
>  关闭工作区对象会关闭工作区中所有打开的数据库。 这会导致在数据库中打开的任何记录集也会被关闭，并且将回滚所有挂起的编辑或更新。 有关相关信息，请参阅[CDaoDatabase：： close](../../mfc/reference/cdaodatabase-class.md#close)、 [CDaoRecordset：： close](../../mfc/reference/cdaorecordset-class.md#close)、 [CDaoTableDef：： Close](../../mfc/reference/cdaotabledef-class.md#close)和[CDaoQueryDef：： close](../../mfc/reference/cdaoquerydef-class.md#close)成员函数。

工作区对象不是永久的;它们仅在存在对它们的引用时存在。 这意味着，在数据库引擎会话结束时，工作区及其数据库集合不会持久保存。 必须再次打开工作区和数据库，为下一次会话重新创建它们。

有关相关信息，请参阅 DAO 帮助中的主题 "关闭方法"。

##  <a name="committrans"></a>CDaoWorkspace：： CommitTrans

调用此成员函数以提交事务-将一组编辑和更新保存到工作区中的一个或多个数据库。

```
void CommitTrans();
```

### <a name="remarks"></a>备注

事务由一系列对数据库数据或其结构的更改（从对[BeginTrans](#begintrans)的调用开始）组成。 完成事务时，请提交该事务，[或回滚（](#rollback)取消更改）。 默认情况下，如果没有事务，将立即提交记录更新。 调用 `BeginTrans` 会导致在调用 `CommitTrans`之前延迟更新的提交。

> [!CAUTION]
>  在一个工作区中，事务对工作区始终是全局性的，并不局限于一个数据库或记录集。 如果对一个工作区事务中的多个数据库或记录集执行操作，`CommitTrans` 会提交所有挂起的更新，并 `Rollback` 还原对这些数据库和记录集的所有操作。

当您关闭包含挂起的事务的数据库或工作区时，所有事务都将回滚。

> [!NOTE]
>  这不是一个两阶段的提交机制。 如果一个更新未能提交，则其他更新仍将提交。

##  <a name="compactdatabase"></a>CDaoWorkspace::CompactDatabase

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

*lpszSrcName*<br/>
现有的已关闭数据库的名称。 它可以是完整路径和文件名，如 "C：\\\MYDB。MDB "。 如果文件名有扩展名，则必须指定扩展名。 如果你的网络支持统一命名约定（UNC），则还可以指定网络路径，例如 "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB。MDB "。 （路径字符串中需要双反斜杠，因为 "\\" 是C++转义字符。）

*lpszDestName*<br/>
正在创建的压缩数据库的完整路径。 还可以指定与*lpszSrcName*的网络路径。 不能使用*lpszDestName*参数指定与*lpszSrcName*相同的数据库文件。

*lpszPassword*<br/>
一个密码，在你想要压缩受密码保护的数据库时使用。 请注意，如果使用采用密码的 `CompactDatabase` 版本，则必须提供所有参数。 此外，由于这是一个连接参数，它需要特殊格式，如下所示：;PWD = *lpszPassword*。 例如：;PWD = "满意"。 （要求前导分号。）

*lpszLocale*<br/>
用于指定创建*lpszDestName*的排序顺序的字符串表达式。 如果通过接受 `dbLangGeneral` 的默认值（见下文）来省略此参数，则新数据库的区域设置与旧数据库的区域设置相同。 可能的值包括：

- `dbLangGeneral` 英语、德语、法语、葡萄牙语、意大利语和新式西班牙语

- `dbLangArabic` 阿拉伯语

- `dbLangCyrillic` 俄语

- `dbLangCzech` 捷克语

- `dbLangDutch` 荷兰语

- `dbLangGreek` 希腊语

- `dbLangHebrew` 希伯来语

- `dbLangHungarian` 匈牙利语

- `dbLangIcelandic` 冰岛语

- `dbLangNordic` 北欧语言（仅限 Microsoft Jet 数据库引擎版本1.0）

- `dbLangNorwdan` 挪威语和丹麦语

- `dbLangPolish` 波兰语

- `dbLangSpanish` 传统西班牙语

- `dbLangSwedfin` 瑞典语和芬兰语

- `dbLangTurkish` 土耳其语

*nOptions*<br/>
指示目标数据库的一个或多个选项， *lpszDestName*。 如果通过接受默认值来省略此参数，则*lpszDestName*将具有与*lpszSrcName*相同的加密和版本。 您可以使用按位 "或" 运算符将 `dbEncrypt` 或 `dbDecrypt` 选项与其中一个版本选项组合在一起。 指定数据库格式的可能值（而不是数据库引擎版本）为：

- `dbEncrypt` 在压缩时加密数据库。

- `dbDecrypt` 在压缩时对数据库进行解密。

- `dbVersion10` 在压缩时创建使用 Microsoft Jet 数据库引擎版本1.0 的数据库。

- `dbVersion11` 在压缩时创建使用 Microsoft Jet 数据库引擎版本1.1 的数据库。

- `dbVersion20` 在压缩时创建使用 Microsoft Jet 数据库引擎版本2.0 的数据库。

- `dbVersion30` 在压缩时创建使用 Microsoft Jet 数据库引擎版本3.0 的数据库。

您可以使用 options 参数 `dbEncrypt` 或 `dbDecrypt` 来指定在压缩数据库时是否对其进行加密或解密。 如果省略了加密常量，或同时包括 `dbDecrypt` 和 `dbEncrypt`， *lpszDestName*将具有与*lpszSrcName*相同的加密。 您可以使用 options 参数中的一个版本常量来指定压缩数据库的数据格式版本。 此常量仅影响*lpszDestName*的数据格式版本。 只能指定一个版本常量。 如果省略版本常量， *lpszDestName*将具有与*lpszSrcName*相同的版本。 只能将*lpszDestName*压缩到与*lpszSrcName*的版本相同或更高的版本。

> [!CAUTION]
>  如果数据库未加密，即使您实现用户/密码安全，也可能会直接读取构成数据库的二进制磁盘文件。

### <a name="remarks"></a>备注

更改数据库中的数据时，数据库文件可能会成为碎片，并使用比所需的更多的磁盘空间。 应定期压缩数据库以对数据库文件进行碎片整理。 压缩的数据库通常较小。 您还可以选择在复制和压缩数据库时更改排序顺序、加密或数据格式的版本。

> [!CAUTION]
>  `CompactDatabase` 成员函数不会将完整的 Microsoft Access 数据库从一个版本正确转换为另一个版本。 只转换数据格式。 不会转换 Microsoft Access 定义的对象（如窗体和报表）。 但是，数据已正确转换。

> [!TIP]
>  你还可以使用 `CompactDatabase` 复制数据库文件。

有关压缩数据库的详细信息，请参阅 DAO 帮助中的 "CompactDatabase 方法" 主题。

##  <a name="create"></a>CDaoWorkspace：： Create

调用此成员函数以创建新的 DAO 工作区对象，并将其与 MFC `CDaoWorkspace` 对象相关联。

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
一个最多包含14个字符的字符串，用于唯一命名新的工作区对象。 必须提供名称。 有关相关信息，请参阅 DAO 帮助中的主题 "名称属性"。

*lpszUserName*<br/>
工作区所有者的用户名。 有关要求，请参阅[SetDefaultUser](#setdefaultuser)成员函数的*lpszDefaultUser*参数。 有关相关信息，请参阅 DAO 帮助中的主题 "UserName 属性"。

*lpszPassword*<br/>
新工作区对象的密码。 密码长度最多为14个字符，可以包含除 ASCII 0 （null）以外的任何字符。 密码区分大小写。 相关信息，请参阅 DAO 帮助中的 "Password 属性" 主题。

### <a name="remarks"></a>备注

总体创建过程如下：

1. 构造[CDaoWorkspace](#cdaoworkspace)对象。

1. 调用对象的 `Create` 成员函数以创建基础 DAO 工作区。 您必须指定工作区名称。

1. 如果要将工作区添加到数据库引擎的工作区集合，则可以选择调用[Append](#append) 。 您可以使用工作区，而无需附加它。

`Create` 调用后，工作区对象处于打开状态，可供使用。 不 `Create`之后调用 `Open`。 如果工作区已存在于工作区集合中，则不会调用 `Create`。 `Create` 初始化数据库引擎（如果尚未对应用程序进行初始化）。

##  <a name="getdatabasecount"></a>CDaoWorkspace::GetDatabaseCount

调用此成员函数以检索工作区的数据库集合中的 DAO 数据库对象（工作区中打开的数据库的数目）的数目。

```
short GetDatabaseCount();
```

### <a name="return-value"></a>返回值

工作区中打开的数据库的数目。

### <a name="remarks"></a>备注

如果需要循环遍历工作区的数据库集合中的所有已定义数据库，`GetDatabaseCount` 会很有用。 若要获取有关集合中某个给定数据库的信息，请参阅[oomads.getdatabaseinfo](#getdatabaseinfo)。 典型用法是对打开的数据库数调用 `GetDatabaseCount`，然后将该数字用作循环索引，以便对 `GetDatabaseInfo`进行重复调用。

##  <a name="getdatabaseinfo"></a>CDaoWorkspace：： Oomads.getdatabaseinfo

调用此成员函数可获取有关在工作区中打开的数据库的各种信息。

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
工作区的数据库集合中数据库对象的从零开始的索引，用于按索引查找。

*dbinfo*<br/>
对[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)对象的引用，该对象返回所请求的信息。

*dwInfoOptions*<br/>
用于指定要检索的数据库信息的选项。 此处列出了可用的选项，以及它们导致函数返回的内容：

- AFX_DAO_PRIMARY_INFO （默认值）名称，可更新，事务

- AFX_DAO_SECONDARY_INFO 主要信息和：版本、排序顺序、查询超时

- AFX_DAO_ALL_INFO 主要和辅助信息以及：连接

*lpszName*<br/>
用于按名称查找的数据库对象的名称。 该名称是一个字符串，最多包含14个字符来唯一命名新的工作区对象。

### <a name="remarks"></a>备注

函数的一个版本允许您按索引查找数据库。 其他版本允许您按名称查找数据库。

有关*dbinfo*中返回的信息的说明，请参阅[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)结构。 此结构中有与*dwInfoOptions*中的说明中列出的信息项对应的成员。 当你在一个级别请求信息时，还会获取任何以前的级别的信息。

##  <a name="getinipath"></a>CDaoWorkspace::GetIniPath

调用此成员函数以获取 Microsoft Jet 数据库引擎在 Windows 注册表中的初始化设置的位置。

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>返回值

包含注册表位置的[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="remarks"></a>备注

您可以使用该位置获取有关数据库引擎设置的信息。 返回的信息实际上是注册表子项的名称。

相关信息，请参阅 DAO 帮助中的主题 "IniPath 属性" 和 "自定义用于数据访问的 Windows 注册表设置"。

##  <a name="getisolateodbctrans"></a>CDaoWorkspace::GetIsolateODBCTrans

调用此成员函数可获取工作区 DAO IsolateODBCTrans 属性的当前值。

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>返回值

如果分离 ODBC 事务，则为非零值;否则为0。

### <a name="remarks"></a>备注

在某些情况下，您可能需要在同一个 ODBC 数据库上同时挂起多个事务。 为此，需要为每个事务打开一个单独的工作区。 请记住，尽管每个工作区都可以有自己的数据库的 ODBC 连接，但这会降低系统性能。 因为事务隔离通常不是必需的，所以，默认情况下共享来自同一用户打开的多个工作区对象的 ODBC 连接。

某些 ODBC 服务器（如 Microsoft SQL Server）不允许在单个连接上同时进行事务。 如果需要在针对此类数据库的时间挂起多个事务，请在打开每个工作区时，将 IsolateODBCTrans 属性设置为 TRUE。 这会为每个工作区强制执行单独的 ODBC 连接。

有关相关信息，请参阅 DAO 帮助中的主题 "IsolateODBCTrans 属性"。

##  <a name="getlogintimeout"></a>CDaoWorkspace：： GetLoginTimeout

调用此成员函数可获取工作区 DAO LoginTimeout 属性的当前值。

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>返回值

尝试登录到 ODBC 数据库时出现错误之前等待的秒数。

### <a name="remarks"></a>备注

此值表示在尝试登录到 ODBC 数据库时出现错误之前等待的秒数。 默认的 LoginTimeout 设置为20秒。 如果将 LoginTimeout 设置为0，则不会发生超时，并且与数据源的通信可能会停止响应。

尝试登录到 ODBC 数据库（如 Microsoft SQL Server）时，由于网络错误或服务器未运行，连接可能会失败。 您可以指定数据库引擎在生成错误之前等待的时间，而不是等待默认值为20秒。 登录到服务器时，会隐式地作为一些不同事件的一部分进行，如对外部服务器数据库运行查询。

有关相关信息，请参阅 DAO 帮助中的主题 "LoginTimeout 属性"。

##  <a name="getname"></a>CDaoWorkspace：： GetName

调用此成员函数以获取 `CDaoWorkspace` 对象基础上的 DAO 工作区对象的用户定义名称。

```
CString GetName();
```

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，其中包含 DAO 工作区对象的用户定义名称。

### <a name="remarks"></a>备注

该名称可用于按名称访问数据库引擎的工作区集合中的 DAO 工作区对象。

有关相关信息，请参阅 DAO 帮助中的主题 "名称属性"。

##  <a name="getusername"></a>CDaoWorkspace：： GetUserName

调用此成员函数以获取工作区所有者的名称。

```
CString GetUserName();
```

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，表示工作区对象的所有者。

### <a name="remarks"></a>备注

若要获取或设置工作区所有者的权限，请直接调用 DAO 来检查权限属性设置;这将确定用户拥有的权限。 若要处理权限，需要一个系统。MDA 文件。

有关直接调用 DAO 的信息，请参阅[技术说明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。 有关相关信息，请参阅 DAO 帮助中的主题 "UserName 属性"。

##  <a name="getversion"></a>CDaoWorkspace：： GetVersion

调用此成员函数以确定正在使用的 Microsoft Jet 数据库引擎的版本。

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，指示与对象关联的数据库引擎的版本。

### <a name="remarks"></a>备注

返回的值以 "主要. 次要" 格式表示版本号;例如 "3.0"。 产品版本号（例如，3.0）由版本号（3）、句点和发布号（0）组成。

相关信息，请参阅 DAO 帮助中的 "版本属性" 主题。

##  <a name="getworkspacecount"></a>CDaoWorkspace::GetWorkspaceCount

调用此成员函数以检索数据库引擎的工作区集合中 DAO 工作区对象的数量。

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>返回值

工作区集合中打开的工作区的数目。

### <a name="remarks"></a>备注

此计数不包括未追加到集合的任何打开的工作区。 如果需要遍历工作区集合中所有定义的工作区，`GetWorkspaceCount` 会很有用。 若要获取有关集合中给定工作区的信息，请参阅[GetWorkspaceInfo](#getworkspaceinfo)。 典型用法是对打开的工作区数调用 `GetWorkspaceCount`，然后将该数字用作循环索引，以便对 `GetWorkspaceInfo`进行重复调用。

##  <a name="getworkspaceinfo"></a>CDaoWorkspace::GetWorkspaceInfo

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
工作区集合中数据库对象的从零开始的索引，用于按索引查找。

*wkspcinfo*<br/>
对[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)对象的引用，该对象返回所请求的信息。

*dwInfoOptions*<br/>
用于指定要检索的工作区的哪些信息的选项。 此处列出了可用的选项，以及它们导致函数返回的内容：

- AFX_DAO_PRIMARY_INFO （默认值）名称

- AFX_DAO_SECONDARY_INFO 主要信息和：用户名

- AFX_DAO_ALL_INFO 主要和辅助信息以及：隔离 ODBCTrans

*lpszName*<br/>
用于按名称查找的工作区对象的名称。 该名称是一个字符串，最多包含14个字符来唯一命名新的工作区对象。

### <a name="remarks"></a>备注

有关*wkspcinfo*中返回的信息的说明，请参阅[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)结构。 此结构中有与*dwInfoOptions*中的说明中列出的信息项对应的成员。 当你在一个级别请求信息时，还会获取以前的级别的信息。

##  <a name="idle"></a>CDaoWorkspace：： Idle

调用 `Idle` 以便为数据库引擎提供执行可能不是最新的后台任务的机会，因为有大量的数据处理。

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>参数

*nAction*<br/>
在空闲处理期间要执行的操作。 目前 `dbFreeLocks`唯一有效的操作。

### <a name="remarks"></a>备注

在多用户的多任务环境中，如果后台处理时间不足以使记录集中的所有记录保持最新，则通常会出现这种情况。

> [!NOTE]
>  如果数据库是用 Microsoft Jet 数据库引擎3.0 版创建的，则不需要调用 `Idle`。 仅对使用早期版本创建的数据库使用 `Idle`。

通常，读取锁定会被删除，并且本地动态集类型的记录集对象中的数据仅在没有其他操作（包括鼠标移动）发生时才会更新。 如果你定期调用 `Idle`，则会通过释放不需要的读取锁定，为数据库引擎提供处理后台处理任务的时间。 将 `dbFreeLocks` 常数指定为参数会延迟处理，直到释放所有读取锁。

此成员函数在单用户环境中不是必需的，除非应用程序的多个实例正在运行。 在多用户环境中，`Idle` 成员函数可能会提高性能，因为这会强制数据库引擎将数据刷新到磁盘，释放内存锁。 您还可以通过使操作成为事务的一部分来释放读取锁定。

相关信息，请参阅 DAO 帮助中的 "空闲方法" 主题。

##  <a name="isopen"></a>CDaoWorkspace：： IsOpen

调用此成员函数以确定 `CDaoWorkspace` 对象是否处于打开状态，即，MFC 对象是否已通过调用[open](#open)或[Create](#create)调用进行了初始化。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果工作区对象处于打开状态，则为非零值;否则为0。

### <a name="remarks"></a>备注

可以调用处于打开状态的工作区的任何成员函数。

##  <a name="m_pdaoworkspace"></a>CDaoWorkspace：： m_pDAOWorkspace

指向基础 DAO 工作区对象的指针。

### <a name="remarks"></a>备注

如果需要直接访问基础 DAO 对象，请使用此数据成员。 可以通过此指针调用 DAO 对象的接口。

有关直接访问 DAO 对象的信息，请参阅[技术说明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

##  <a name="open"></a>CDaoWorkspace：： Open

显式打开与 DAO 的默认工作区关联的工作区对象。

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
要打开的 DAO 工作区对象的名称-最多包含14个字符的字符串，用于唯一命名工作区。 接受默认值 NULL，以显式打开默认工作区。 有关命名要求，请参阅[Create](#create)的*lpszName*参数。 有关相关信息，请参阅 DAO 帮助中的主题 "名称属性"。

### <a name="remarks"></a>备注

构造 `CDaoWorkspace` 对象后，调用此成员函数以执行下列操作之一：

- 显式打开默认工作区。 为*lpszName*传递 NULL。

- 按名称打开现有 `CDaoWorkspace` 对象，即工作区集合的成员。 传递现有工作区对象的有效名称。

`Open` 将工作区对象置于打开状态，还会初始化数据库引擎（如果尚未对应用程序进行初始化）。

尽管在打开工作区后，只能调用许多 `CDaoWorkspace` 成员函数，但以下在数据库引擎上操作的成员函数在构造C++对象之后、调用 `Open`之前可用：

||||
|-|-|-|
|[创建](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|
|[GetIniPath](#getinipath)|[时间](#idle)|[SetIniPath](#setinipath)|
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|

##  <a name="repairdatabase"></a>CDaoWorkspace::RepairDatabase

如果需要尝试修复访问 Microsoft Jet 数据库引擎的损坏数据库，请调用此成员函数。

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
现有 Microsoft Jet 引擎数据库文件的路径和文件名。 如果省略该路径，将仅搜索当前目录。 如果系统支持统一命名约定（UNC），则还可以指定网络路径，例如： "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB。MDB "。 （路径字符串中需要双反斜杠，因为 "\\" 是C++转义字符。）

### <a name="remarks"></a>备注

修复 LpszName 之前，必须先关闭由指定的数据库。 在多用户环境中，其他用户在修复它时无法打开*lpszName* 。 如果*lpszName*未关闭或不可供独占使用，则会出现错误。

此成员函数尝试修复通过不完整的写入操作被标记为可能损坏的数据库。 如果由于断电或计算机硬件问题而导致使用 Microsoft Jet 数据库引擎的应用程序意外关闭，则会发生这种情况。 如果完成操作并调用[Close](../../mfc/reference/cdaodatabase-class.md#close)成员函数或以常规方式退出应用程序，则数据库不会标记为可能已损坏。

> [!NOTE]
>  修复数据库后，最好使用[CompactDatabase](#compactdatabase)成员函数对文件进行碎片整理，并恢复磁盘空间。

有关修复数据库的详细信息，请参阅 DAO 帮助中的 "RepairDatabase 方法" 主题。

##  <a name="rollback"></a>CDaoWorkspace：： Rollback

调用此成员函数以结束当前事务，并将工作区中的所有数据库还原到事务开始之前的状态。

```
void Rollback();
```

### <a name="remarks"></a>备注

> [!CAUTION]
>  在一个工作区对象中，事务对工作区始终是全局性的，并不局限于一个数据库或记录集。 如果对一个工作区事务中的多个数据库或记录集执行操作，`Rollback` 会还原所有这些数据库和记录集上的所有操作。

如果在不保存或回滚任何挂起的事务的情况下关闭工作区对象，将自动回滚事务。 如果在不首先调用[BeginTrans](#begintrans)的情况下调用[CommitTrans](#committrans)或 `Rollback`，则会发生错误。

> [!NOTE]
>  开始事务时，数据库引擎会将其操作记录到保存在工作站上 TEMP 环境变量指定的目录中的文件中。 如果事务日志文件用完了 TEMP 驱动器上的可用存储空间，则数据库引擎将导致 MFC 引发 `CDaoException` （DAO 错误2004）。 此时，如果调用 `CommitTrans`，则会提交不确定的操作数量，但剩余未完成的操作将丢失，并且必须重新启动操作。 调用 `Rollback` 会释放事务日志，并回滚事务中的所有操作。

##  <a name="setdefaultpassword"></a>CDaoWorkspace::SetDefaultPassword

调用此成员函数可设置创建工作区对象时数据库引擎使用的默认密码，而无需指定密码。

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>参数

*lpszPassword*<br/>
默认密码。 密码长度最多为14个字符，可以包含除 ASCII 0 （null）以外的任何字符。 密码区分大小写。

### <a name="remarks"></a>备注

所设置的默认密码将应用于调用后创建的新工作区。 创建后续工作区时，无需在 "[创建](#create)调用" 中指定密码。

若要使用此成员函数：

1. 构造 `CDaoWorkspace` 对象，但不调用 `Create`。

1. 调用 `SetDefaultPassword`，如需要，请调用[SetDefaultUser](#setdefaultuser)。

1. 为此工作区对象或后续对象调用 `Create`，无需指定密码。

默认情况下，DefaultUser 属性设置为 "admin"，DefaultPassword 属性设置为空字符串（""）。

有关安全性的详细信息，请参阅 DAO 帮助中的主题 "权限属性"。 有关相关信息，请参阅 DAO 帮助中的主题 "DefaultPassword 属性" 和 "DefaultUser 属性"。

##  <a name="setdefaultuser"></a>CDaoWorkspace::SetDefaultUser

调用此成员函数可设置创建工作区对象时数据库引擎使用的默认用户名，但不使用特定用户名。

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>参数

*lpszDefaultUser*<br/>
默认用户名。 用户名长度为 1-20 个字符，并包含字母字符、重音字符、数字、空格和符号，除了： "（引号）、/（正斜杠）、\ （反斜杠）、\[ \] （方括号）、：（冒号）、 &#124; （管道）、\< （小于号）、> （大于号）、+ （正号）、= （等号）、（分号）、、（逗号）、（问号）、\* （星号）、前导空格和控制字符（ASCII 00 到 ASCII 31）。 有关相关信息，请参阅 DAO 帮助中的主题 "UserName 属性"。

### <a name="remarks"></a>备注

设置的默认用户名适用于在调用后创建的新工作区。 创建后续工作区时，无需在 "[创建](#create)调用" 中指定用户名。

若要使用此成员函数：

1. 构造 `CDaoWorkspace` 对象，但不调用 `Create`。

1. 调用 `SetDefaultUser`，如需要，请调用[SetDefaultPassword](#setdefaultpassword)。

1. 为此工作区对象或后续对象调用 `Create`，而不指定用户名。

默认情况下，DefaultUser 属性设置为 "admin"，DefaultPassword 属性设置为空字符串（""）。

有关相关信息，请参阅 DAO 帮助中的主题 "DefaultUser 属性" 和 "DefaultPassword 属性"。

##  <a name="setinipath"></a>CDaoWorkspace::SetIniPath

调用此成员函数以指定 Microsoft Jet 数据库引擎的 Windows 注册表设置的位置。

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>参数

*lpszRegistrySubkey*<br/>
一个字符串，其中包含用于 Microsoft Jet 数据库引擎设置的位置或可安装的 ISAM 数据库所需参数的 Windows 注册表子项的名称。

### <a name="remarks"></a>备注

仅当需要指定特殊设置时才调用 `SetIniPath`。 有关详细信息，请参阅 DAO 帮助中的主题 "IniPath 属性"。

> [!NOTE]
>  在应用程序安装期间（而不是在应用程序运行时）调用 `SetIniPath`。 打开任何工作区、数据库或记录集之前，必须先调用 `SetIniPath`;否则，MFC 会引发异常。

你可以使用此机制来配置具有用户提供的注册表设置的数据库引擎。 此属性的作用域仅限于应用程序，无法在不重新启动应用程序的情况下更改。

##  <a name="setisolateodbctrans"></a>CDaoWorkspace::SetIsolateODBCTrans

调用此成员函数可设置工作区 DAO IsolateODBCTrans 属性的值。

```
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>参数

*bIsolateODBCTrans*<br/>
如果要开始隔离 ODBC 事务，则传递 TRUE。 如果要停止隔离 ODBC 事务，则传递 FALSE。

### <a name="remarks"></a>备注

在某些情况下，您可能需要在同一个 ODBC 数据库上同时挂起多个事务。 为此，需要为每个事务打开一个单独的工作区。 尽管每个工作区都可以有自己的数据库的 ODBC 连接，但这会降低系统性能。 因为事务隔离通常不是必需的，所以，默认情况下共享来自同一用户打开的多个工作区对象的 ODBC 连接。

某些 ODBC 服务器（如 Microsoft SQL Server）不允许在单个连接上同时进行事务。 如果需要在针对此类数据库的时间挂起多个事务，请在打开每个工作区时，将 IsolateODBCTrans 属性设置为 TRUE。 这会为每个工作区强制执行单独的 ODBC 连接。

##  <a name="setlogintimeout"></a>CDaoWorkspace：： SetLoginTimeout

调用此成员函数可设置工作区 DAO LoginTimeout 属性的值。

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>参数

*nSeconds*<br/>
尝试登录到 ODBC 数据库时出现错误之前等待的秒数。

### <a name="remarks"></a>备注

此值表示在尝试登录到 ODBC 数据库时出现错误之前等待的秒数。 默认的 LoginTimeout 设置为20秒。 如果将 LoginTimeout 设置为0，则不会发生超时，并且与数据源的通信可能会停止响应。

尝试登录到 ODBC 数据库（如 Microsoft SQL Server）时，由于网络错误或服务器未运行，连接可能会失败。 您可以指定数据库引擎在生成错误之前等待的时间，而不是等待默认值为20秒。 登录到服务器时，会隐式地作为一些不同事件的一部分进行，如对外部服务器数据库运行查询。 超时值由 LoginTimeout 属性的当前设置确定。

有关相关信息，请参阅 DAO 帮助中的主题 "LoginTimeout 属性"。

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException 类](../../mfc/reference/cdaoexception-class.md)
