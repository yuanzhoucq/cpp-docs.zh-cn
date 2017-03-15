---
title: "CDaoWorkspace 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoWorkspace
dev_langs:
- C++
helpviewer_keywords:
- DAO workspaces [C++]
- transaction spaces [C++], DAO workspace
- ODBC classes [C++], vs. DAO classes
- default workspaces [C++], DAO
- workspaces [C++], DAO
- sessions [C++], DAO workspace
- Workspace class
- CDaoWorkspace class
- workspaces [C++], interface to database engine
- Workspaces collection
- persistence [C++], DAO workspace
- workspaces [C++], default
- defaults [C++], workspaces
- DAO workspaces [C++], CDaoWorkspace class
- security [MFC], DAO workspaces
- security [MFC]
- database engine [C++], accessing via workspace
- transaction spaces [C++]
- DDLs [C++]
- workspaces [C++], persistence
- default workspaces [C++]
ms.assetid: 64f60de6-4df1-4d4a-a65b-c489b5257d52
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5d7f9aea6fa4913641bc92662b3cf5dfeaddb9d8
ms.lasthandoff: 02/24/2017

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
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|构造工作区对象。 然后，调用**创建**或**打开**。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CDaoWorkspace::Append](#append)|将新创建的工作区追加到数据库引擎的工作区集合。|  
|[CDaoWorkspace::BeginTrans](#begintrans)|开始一个新事务，这适用于所有数据库打开工作区中。|  
|[CDaoWorkspace::Close](#close)|关闭工作区和所有包含的对象。 挂起的事务将回滚。|  
|[CDaoWorkspace::CommitTrans](#committrans)|完成当前的事务并保存所做的更改。|  
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|压缩 （或重复项） 数据库。|  
|[CDaoWorkspace::Create](#create)|创建新的 DAO 工作区对象。|  
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|返回工作区中的数据库集合中的 DAO 数据库对象的数目。|  
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|返回有关指定在工作区中的数据库集合中定义的 DAO 数据库信息。|  
|[CDaoWorkspace::GetIniPath](#getinipath)|Windows 注册表中返回的位置 Microsoft Jet 数据库引擎的初始化设置。|  
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|返回一个值，该值指示是否涉及同一个 ODBC 数据源的多个事务之间隔离通过强制与数据源的多个连接。|  
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|返回用户尝试登录到 ODBC 数据库时出现错误之前等待的秒数。|  
|[CDaoWorkspace::GetName](#getname)|返回工作区中对象的用户定义名称。|  
|[CDaoWorkspace::GetUserName](#getusername)|返回工作区创建时指定的用户名。 这是工作区所有者的名称。|  
|[CDaoWorkspace::GetVersion](#getversion)|返回一个字符串，包含与工作区关联的数据库引擎的版本。|  
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|数据库引擎的工作区集合中返回 DAO 工作区中对象的数目。|  
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|返回有关指定 DAO 工作区数据库引擎的工作区集合中定义的信息。|  
|[CDaoWorkspace::Idle](#idle)|允许数据库引擎将执行的后台任务。|  
|[CDaoWorkspace::IsOpen](#isopen)|返回非零的工作区是否打开。|  
|[CDaoWorkspace::Open](#open)|显式打开与 DAO 的默认工作区关联的工作区对象。|  
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|尝试修复损坏的数据库。|  
|[CDaoWorkspace::Rollback](#rollback)|结束当前事务，且不保存所做的更改。|  
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|设置数据库引擎时不使用特定密码创建一个工作区中对象所使用的密码。|  
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|设置数据库引擎时没有特定的用户名称创建一个工作区中对象所使用的用户名。|  
|[CDaoWorkspace::SetIniPath](#setinipath)|Windows 注册表中设置的位置 Microsoft Jet 数据库引擎的初始化设置。|  
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|指定是否由强制为数据源的多个连接隔离，则涉及相同的 ODBC 数据源的多个事务。|  
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|设置当用户尝试登录到 ODBC 数据源中发生错误之前等待的秒数。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|指向基础 DAO 工作区对象。|  
  
## <a name="remarks"></a>备注  
 在大多数情况下，不需要使用多个工作区，并不需要创建显式工作区对象;当您打开数据库和记录集对象时，它们使用 DAO 的默认工作区。 但是，如果需要您可以运行多个会话一次通过创建额外的工作区对象。 工作区中的每个对象可以包含在其自己的数据库集合中的多个打开的数据库对象。 在 MFC 中，工作区是主要的事务管理器，指定一组打开数据库都在同一个"事务 space。  
  
> [!NOTE]
>  DAO 数据库类中是不同于基于开放式数据库连接 (ODBC) 的 MFC 数据库类。 DAO 数据库类的所有名称都有"CDao"前缀。 一般情况下，基于 DAO MFC 类是更强于基于 ODBC 的 MFC 类。 基于 DAO 的类通过 Microsoft Jet 数据库引擎，其中包括 ODBC 驱动程序访问数据。 它们还支持数据定义语言 (DDL) 操作，如创建数据库并添加表和字段通过类，而无需直接调用 DAO。  
  
## <a name="capabilities"></a>功能  
 类`CDaoWorkspace`提供了以下︰  
  
-   显式访问权限，如有必要，到默认工作区，创建的初始化数据库引擎。 通常使用 DAO 的默认工作区隐式创建数据库和记录集对象。  
  
-   在工作区中打开的事务应用于所有数据库的事务空间。 您可以创建其他工作区，以管理单独的事务空间。  
  
-   一个指向基础 Microsoft Jet 数据库引擎的很多属性的接口 （请参阅静态成员函数）。 打开或创建一个工作区，或调用静态成员函数之前打开或创建，初始化数据库引擎。  
  
-   对数据库引擎的工作区集合，其中存储所有已追加到它的活动工作区的访问。 您还可以创建和使用工作区不会将它们附加到的集合。  
  
## <a name="security"></a>安全性  
 MFC DAO，用于安全控制在未实现的用户和组的集合。 如果您需要 DAO 的那些方面，您必须自己进行编程它们通过直接调用 DAO 接口。 有关信息，请参阅[技术注意 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
## <a name="usage"></a>用法  
 您可以使用类`CDaoWorkspace`到︰  
  
-   显式打开默认工作区。  
  
     通常使用默认工作区，则隐式 — 当您打开新[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象。 但您可能需要显式访问 — 例如，与数据库引擎或访问工作区集合。 请参阅下文的"隐式使用的默认工作区"。  
  
-   创建新的工作区。 调用[追加](#append)如果想要将它们添加到工作区集合。  
  
-   在工作区集合中打开现有的工作区。  
  
 创建新的工作区中尚不存在集合进行了描述在工作区中[创建](#create)成员函数。 不以任何方式数据库引擎会话之间保留工作区中的对象。 如果您的应用程序以静态方式链接 MFC，结束应用程序取消初始化数据库引擎。 如果您的应用程序动态地与 MFC 链接，则数据库引擎是未初始化，MFC DLL 将在卸载时。  
  
 在下所述显式打开默认工作区，或在工作区集合中，打开现有的工作区[打开](#open)成员函数。  
  
 通过关闭与工作区来结束工作区中的会话[关闭](#close)成员函数。 **关闭**关闭还没有关闭以前，回滚任何未提交的事务的任何数据库。  
  
## <a name="transactions"></a>事务  
 DAO 管理事务级别的工作区中;因此，具有多个打开的数据库的工作区上的事务应用于所有数据库。 例如，如果两个数据库有未提交的更新，并调用[CommitTrans](#committrans)，所有更新都已提交。 如果你想要限制到单个数据库的事务，则为其需要单独的工作区对象。  
  
## <a name="implicit-use-of-the-default-workspace"></a>隐式使用的默认工作区  
 MFC 使用 DAO 的隐式在以下情况下的默认工作区︰  
  
-   如果您创建一个新`CDaoDatabase`对象，但不是这样做通过现有`CDaoWorkspace`对象时，MFC 将创建一个临时工作区对象，它对应于 DAO 的默认工作区。 如果这样做多个数据库，所有数据库对象均与默认工作区相关联。 您可以访问数据库的工作区通过`CDaoDatabase`数据成员。  
  
-   同样，如果您创建`CDaoRecordset`对象而无需提供一个指向`CDaoDatabase`对象时，MFC 将创建一个临时数据库对象并且通过扩展，临时工作区对象。 您可以通过访问记录集的数据库和间接的其工作区中，`CDaoRecordset`数据成员。  
  
## <a name="other-operations"></a>其他操作  
 此外提供了这其他数据库操作，如修复数据库已损坏或压缩的数据库。  
  
 调用 DAO 直接以及 DAO 安全性有关的信息，请参阅[技术注意 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoWorkspace`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdao.h  
  
##  <a name="a-nameappenda--cdaoworkspaceappend"></a><a name="append"></a>CDaoWorkspace::Append  
 在您调用后调用此成员函数[创建](#create)。  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>备注  
 **追加**将新创建的工作区对象追加到数据库引擎的工作区集合。 数据库引擎会话; 期间不会保留工作区这些存储在内存中，不是磁盘上。 无需附加工作区中;如果不这样做，您仍可以使用它。  
  
 附加工作区保留在活动的工作区集合中，打开状态，直到您调用其[关闭](#close)成员函数。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"追加方法"。  
  
##  <a name="a-namebegintransa--cdaoworkspacebegintrans"></a><a name="begintrans"></a>CDaoWorkspace::BeginTrans  
 调用该成员函数以启动事务。  
  
```  
void BeginTrans();
```  
  
### <a name="remarks"></a>备注  
 在您调用之后**BeginTrans**，当提交事务时，对您的数据或数据库结构所做的更新将立即生效。 由于工作区定义单个事务空间，因此事务应用于工作区中的所有打开数据库。 有两种方法可以完成该事务︰  
  
-   调用[CommitTrans](#committrans)成员函数以提交该事务并将更改保存到数据源。  
  
-   或致电[回滚](#rollback)成员函数来取消该事务。  
  
 关闭工作区对象或数据库对象时挂起事务将回滚所有挂起的事务。  
  
 如果您需要找出那些在另一个 ODBC 数据源中的一个 ODBC 数据源上的事务，请参阅[SetIsolateODBCTrans](#setisolateodbctrans)成员函数。  
  
##  <a name="a-namecdaoworkspacea--cdaoworkspacecdaoworkspace"></a><a name="cdaoworkspace"></a>CDaoWorkspace::CDaoWorkspace  
 构造 `CDaoWorkspace` 对象。  
  
```  
CDaoWorkspace();
```  
  
### <a name="remarks"></a>备注  
 构建 c + + 对象时后, 您将具有两个选项︰  
  
-   调用对象的[打开](#open)成员函数以打开默认工作区或打开工作区集合中的某个现有对象。  
  
-   或调用对象的[创建](#create)成员函数来创建新的 DAO 工作区对象。 这将显式启动新的工作区中会话，您可以通过参考`CDaoWorkspace`对象。 在调用**创建**，您可以调用[追加](#append)如果想要将工作区添加到数据库引擎的工作区集合。  
  
 请参阅类概述[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)有关信息时您需要显式创建`CDaoWorkspace`对象。 通常情况下，你使用打开时将隐式创建的工作区[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象而无需指定一个工作区或当您打开[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)而无需指定数据库对象的对象。 在这种方式中创建的 MFC DAO 对象使用的 DAO 的默认工作区中，这是创建一次并且重复使用。  
  
 若要释放工作区和其所含的对象，调用该工作区中对象的[关闭](#close)成员函数。  
  
##  <a name="a-nameclosea--cdaoworkspaceclose"></a><a name="close"></a>CDaoWorkspace::Close  
 调用该成员函数以关闭该工作区对象。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 关闭打开的工作区对象释放基础的 DAO 对象并在工作区集合的成员的工作区是否从集合中移除它。 调用**关闭**是好的编程做法。  
  
> [!CAUTION]
>  关闭工作区对象关闭任何打开的数据库工作区中。 这将打开，正在关闭数据库中的所有记录集和任何挂起的编辑或更新都将回滚。 有关相关信息，请参阅[CDaoDatabase::Close](../../mfc/reference/cdaodatabase-class.md#close)， [CDaoRecordset::Close](../../mfc/reference/cdaorecordset-class.md#close)， [CDaoTableDef::Close](../../mfc/reference/cdaotabledef-class.md#close)，和[CDaoQueryDef::Close](../../mfc/reference/cdaoquerydef-class.md#close)成员函数。  
  
 工作区中的对象不是永久的;它们只对它们的引用存在时存在。 这意味着，数据库引擎会话结束时，工作区和其数据库集合不会保留。 您必须通过重新创建它们的下一个会话重新打开工作区和数据库。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"Close 方法"。  
  
##  <a name="a-namecommittransa--cdaoworkspacecommittrans"></a><a name="committrans"></a>CDaoWorkspace::CommitTrans  
 调用此成员函数以提交事务 — 将一组编辑和更新保存到工作区中的一个或多个数据库。  
  
```  
void CommitTrans();
```  
  
### <a name="remarks"></a>备注  
 事务由一系列更改对数据库的数据或其结构，以调用开头的[BeginTrans](#begintrans)。 在完成事务后，可以提交或回滚它 （取消所做的更改） 与[回滚](#rollback)。 默认情况下，如果事务，未对记录的更新将被立即提交。 调用**BeginTrans**会导致在您调用之前延迟的更新承诺**CommitTrans**。  
  
> [!CAUTION]
>  在一个工作区中，事务始终是全局到工作区并不限于只能有一个数据库或记录集。 如果你执行在多个数据库或在工作区事务中，记录集上的操作**CommitTrans**提交所有挂起的更新，并**回滚**还原这些数据库和记录集上的所有操作。  
  
 当您关闭数据库或具有挂起的事务的工作区时，所有回滚事务。  
  
> [!NOTE]
>  这不是一种两阶段提交机制。 如果无法提交一个更新，其他人仍将提交。  
  
##  <a name="a-namecompactdatabasea--cdaoworkspacecompactdatabase"></a><a name="compactdatabase"></a>CDaoWorkspace::CompactDatabase  
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
 `lpszSrcName`  
 数据库已关闭的一个现有的名称。 它可以完整路径和文件名，如"c:\\\MYDB。MDB"。 如果文件名扩展名，则必须指定它。 如果您的网络支持的统一命名约定 (UNC)，您还可以指定网络路径，如"\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB。MDB"。 (双反斜杠需要在路径的字符串，因为"\\"c + + 转义符。)  
  
 `lpszDestName`  
 要创建压缩的数据库的完整路径。 您还可以指定网络路径作为与`lpszSrcName`。 不能使用`lpszDestName`参数以指定的同一个数据库文件`lpszSrcName`。  
  
 `lpszPassword`  
 一个密码，在您希望压缩受密码保护的数据库时使用。 请注意，如果您使用的版本`CompactDatabase`，它接受一个密码，则必须提供所有参数。 此外，由于这是一个连接参数，因此它要求特殊格式设置，如下所示:;PWD= `lpszPassword`. 例如:;PWD ="快乐"。 （前面的分号是必需的。  
  
 `lpszLocale`  
 用来指定用于创建排序规则顺序的字符串表达式`lpszDestName`。 如果忽略此参数接受默认值为**dbLangGeneral** （见下文），新数据库的区域设置是与旧的数据库中的相同。 可能的值有：  
  
- **dbLangGeneral**英语、 德语、 法语、 葡萄牙语、 意大利语和现代西班牙语  
  
- **dbLangArabic**阿拉伯语  
  
- **dbLangCyrillic**俄语  
  
- **dbLangCzech**捷克语  
  
- **dbLangDutch**荷兰语  
  
- **dbLangGreek**希腊语  
  
- **dbLangHebrew**希伯来语  
  
- **dbLangHungarian**匈牙利语  
  
- **dbLangIcelandic**冰岛语  
  
- **dbLangNordic**北欧语言 （Microsoft Jet 数据库引擎版本 1.0 只）  
  
- **dbLangNorwdan**挪威语和丹麦语  
  
- **dbLangPolish**波兰语  
  
- **dbLangSpanish**传统西班牙语  
  
- **dbLangSwedfin**瑞典语和芬兰语  
  
- **dbLangTurkish**土耳其语  
  
 `nOptions`  
 指示目标数据库的一个或多个选项`lpszDestName`。 如果您省略此参数接受默认值为`lpszDestName`将具有相同的加密和与相同的版本`lpszSrcName`。 您可以组合使用**dbEncrypt**或**dbDecrypt**选项与使用按位或运算符版本选项之一。 可能的值，指定数据库格式，没有数据库引擎版本是︰  
  
- **dbEncrypt**压缩时加密的数据库。  
  
- **dbDecrypt**压缩时解密该数据库。  
  
- **dbVersion10**创建压缩时使用 Microsoft Jet 数据库引擎版本 1.0 数据库。  
  
- **dbVersion11**创建压缩时使用 Microsoft Jet 数据库引擎版本 1.1 的数据库。  
  
- **dbVersion20**创建压缩时使用 Microsoft Jet 数据库引擎版本 2.0 的数据库。  
  
- **dbVersion30**创建压缩时使用 Microsoft Jet 数据库引擎版本 3.0 的数据库。  
  
 您可以使用**dbEncrypt**或**dbDecrypt**在 options 参数来指定是否加密或解密该数据库，因为它进行压缩。 如果省略加密常量或同时包括**dbDecrypt**和**dbEncrypt**，`lpszDestName`将具有相同的加密作为`lpszSrcName`。 您可以使用版本常量中的一个选项参数中指定压缩的数据库的数据格式的版本。 此常量会影响的数据格式的版本仅`lpszDestName`。 您可以指定只有一个版本常量。 如果省略版本常量`lpszDestName`将具有相同的版本`lpszSrcName`。 您可以压缩`lpszDestName`仅对相同的版本或更高版本比`lpszSrcName`。  
  
> [!CAUTION]
>  如果数据库未加密，则有可能，即使您实现用户/密码安全性，以直接读取构成数据库的二进制文件磁盘文件。  
  
### <a name="remarks"></a>备注  
 更改数据库中的数据时，数据库文件将变成碎片，并使用比实际所需的更多磁盘空间。 我们会定期应该压缩数据库，使之对数据库文件进行碎片整理。 压缩的数据库是通常较小。 您还可以选择在复制和压缩数据库时更改的排列顺序、 加密或数据格式的版本。  
  
> [!CAUTION]
>  `CompactDatabase`成员函数会不正确地转换完整的 Microsoft Access 数据库从一个版本到另一个。 仅数据格式将转换。 Microsoft 访问权限定义对象，如窗体和报表，不会转换。 但是，正确地转换数据。  
  
> [!TIP]
>  您还可以使用`CompactDatabase`数据库文件复制。  
  
 有关压缩的数据库的详细信息，请参阅主题 DAO 帮助中的"CompactDatabase 方法"。  
  
##  <a name="a-namecreatea--cdaoworkspacecreate"></a><a name="create"></a>CDaoWorkspace::Create  
 调用此成员函数以创建新的 DAO workspace 对象并将其与 MFC`CDaoWorkspace`对象。  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    LPCTSTR lpszUserName,  
    LPCTSTR lpszPassword);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 唯一地命名新的 workspace 对象最多 14 个字符的字符串。 您必须提供一个名称。 有关相关信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
 *lpszUserName*  
 工作区的所有者的用户名。 有关要求，请参阅`lpszDefaultUser`参数[SetDefaultUser](#setdefaultuser)成员函数。 有关相关信息，请参阅主题 DAO 帮助中的"用户名属性"。  
  
 `lpszPassword`  
 新的工作区中对象的密码。 密码长度最多为 14 个字符，并且可以包含除 ASCII 0 (null) 之外的任何字符。 密码是区分大小写。 有关相关信息，请参阅主题 DAO 帮助中的"密码属性"。  
  
### <a name="remarks"></a>备注  
 整个创建过程是︰  
  
1.  构造[CDaoWorkspace](#cdaoworkspace)对象。  
  
2.  调用对象的**创建**成员函数来创建基础 DAO 工作区。 您必须指定工作区名称。  
  
3.  （可选） 调用[追加](#append)如果想要将工作区添加到数据库引擎的工作区集合。 您可以使用工作区而无需将其追加。  
  
 之后**创建**调用时，工作区对象是否处于打开状态，可供使用。 您不调用**打开**后**创建**。 您不调用**创建**在工作区集合中已存在工作区。 **创建**初始化数据库引擎，如果它已尚未初始化您的应用程序。  
  
##  <a name="a-namegetdatabasecounta--cdaoworkspacegetdatabasecount"></a><a name="getdatabasecount"></a>CDaoWorkspace::GetDatabaseCount  
 调用此成员函数以检索在工作区中的数据库集合中的 DAO 数据库对象数 — 工作区中打开数据库的数目。  
  
```  
short GetDatabaseCount();
```  
  
### <a name="return-value"></a>返回值  
 工作区中打开数据库的数目。  
  
### <a name="remarks"></a>备注  
 `GetDatabaseCount`如果您需要循环访问工作区中的数据库集合中的所有已定义数据库，很有用。 若要获取集合中的给定数据库有关的信息，请参阅[GetDatabaseInfo](#getdatabaseinfo)。 典型用法就是调用`GetDatabaseCount`的几个打开的数据库，然后使用该数字作为循环索引重复调用`GetDatabaseInfo`。  
  
##  <a name="a-namegetdatabaseinfoa--cdaoworkspacegetdatabaseinfo"></a><a name="getdatabaseinfo"></a>CDaoWorkspace::GetDatabaseInfo  
 调用此成员函数来获取各种类型的工作区中打开的数据库有关的信息。  
  
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
 `nIndex`  
 在工作区中的数据库集合中，对于通过索引查找的数据库对象的从零开始的索引。  
  
 `dbinfo`  
 对引用[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)返回所请求的信息的对象。  
  
 `dwInfoOptions`  
 指定要检索的数据库有关的信息的选项。 以及它们会导致返回的函数，这里列出了可用的选项︰  
  
- `AFX_DAO_PRIMARY_INFO`（默认值）可更新的、 名称、 事务  
  
- `AFX_DAO_SECONDARY_INFO`加上的主要信息︰ 版本中，排序规则顺序查询超时值  
  
- `AFX_DAO_ALL_INFO`主要和次要信息加上︰ 连接  
  
 `lpszName`  
 按名称查找数据库对象的名称。 名称是唯一命名新的 workspace 对象最多 14 个字符的字符串。  
  
### <a name="remarks"></a>备注  
 该函数的一个版本，可以按索引查找数据库。 另一个版本中，可以按名称查找数据库。  
  
 有关在中返回的信息的说明`dbinfo`，请参阅[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)结构。 这种结构有对应于上面的说明中列出的信息的项目的成员`dwInfoOptions`。 当请求在某一级别的信息时，可以为任何以前的级别的信息。  
  
##  <a name="a-namegetinipatha--cdaoworkspacegetinipath"></a><a name="getinipath"></a>CDaoWorkspace::GetIniPath  
 调用该成员函数以获取引擎的初始化设置 Windows 注册表中的 Microsoft Jet 数据库的位置。  
  
```  
static CString PASCAL GetIniPath();
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)包含注册表位置。  
  
### <a name="remarks"></a>备注  
 该位置可用于获取有关数据库引擎的设置的信息。 返回的信息是实际的注册表子项的名称。  
  
 有关相关信息，请参阅"IniPath 属性"和"自定义 Windows 注册表设置为数据访问"DAO 帮助中的主题。  
  
##  <a name="a-namegetisolateodbctransa--cdaoworkspacegetisolateodbctrans"></a><a name="getisolateodbctrans"></a>CDaoWorkspace::GetIsolateODBCTrans  
 调用此成员函数，可为工作区获取 DAO IsolateODBCTrans 属性的当前值。  
  
```  
BOOL GetIsolateODBCTrans();
```  
  
### <a name="return-value"></a>返回值  
 ODBC 事务之间隔离; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 在某些情况下，可能需要对同一个 ODBC 数据库有挂起的多个同时进行的事务。 若要执行此操作，您需要打开单独的工作区为每个事务。 请记住，虽然每个工作区可以有其自己的 ODBC 连接到数据库，这会降低系统性能。 由于事务隔离不是正常情况下必需的默认情况下共享来自多个工作区对象由同一个用户打开的 ODBC 连接。  
  
 某些 ODBC 服务器，例如 Microsoft SQL Server 不允许在单个连接上的同步事务。 如果您需要一次挂起对此类数据库的多个事务，IsolateODBCTrans 属性设置为**TRUE**上每个工作区，就立即打开它。 这将强制一个单独的 ODBC 连接每个工作区。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"IsolateODBCTrans 属性"。  
  
##  <a name="a-namegetlogintimeouta--cdaoworkspacegetlogintimeout"></a><a name="getlogintimeout"></a>CDaoWorkspace::GetLoginTimeout  
 调用此成员函数，可为工作区获取 DAO LoginTimeout 属性的当前值。  
  
```  
static short PASCAL GetLoginTimeout();
```  
  
### <a name="return-value"></a>返回值  
 在您尝试登录到 ODBC 数据库时，将发生错误之前等待的秒数。  
  
### <a name="remarks"></a>备注  
 此值表示在您尝试登录到 ODBC 数据库时，将发生错误之前等待的秒数。 默认 LoginTimeout 设置为 20 秒。 当 LoginTimeout 设置为 0 时，无超时会发生，并且与数据源之间的通信可能会停止响应。  
  
 当您尝试登录到 ODBC 数据库，如 Microsoft SQL Server 连接可能失败发生网络错误或者因为服务器未运行。 而不是等待默认值为 20 秒连接，您可以指定数据库引擎，它将生成错误之前的等待多长时间。 登录到服务器的大量不同的事件，如在外部服务器数据库上运行查询的一部分隐式发生。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"LoginTimeout 属性"。  
  
##  <a name="a-namegetnamea--cdaoworkspacegetname"></a><a name="getname"></a>CDaoWorkspace::GetName  
 调用此成员函数以获取 DAO 工作区对象基础的用户定义名称`CDaoWorkspace`对象。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)包含 DAO 工作区对象的用户定义名称。  
  
### <a name="remarks"></a>备注  
 该名称可用于按名称访问该数据库引擎的工作区集合中的 DAO 工作区对象。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
##  <a name="a-namegetusernamea--cdaoworkspacegetusername"></a><a name="getusername"></a>CDaoWorkspace::GetUserName  
 调用该成员函数以获取工作区的所有者的名称。  
  
```  
CString GetUserName();
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)表示工作区对象的所有者。  
  
### <a name="remarks"></a>备注  
 若要获取或设置工作区所有者的权限，请调用 DAO 直接以检查权限属性设置;这可确定哪些权限的用户拥有。 若要使用的权限，您需要一个系统。MDA 文件。  
  
 调用 DAO 有关的信息，请参阅[技术注意 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。 有关相关信息，请参阅主题 DAO 帮助中的"用户名属性"。  
  
##  <a name="a-namegetversiona--cdaoworkspacegetversion"></a><a name="getversion"></a>CDaoWorkspace::GetVersion  
 调用该成员函数以确定正在使用 Microsoft Jet 数据库引擎的版本。  
  
```  
static CString PASCAL GetVersion();
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，该值指示与对象关联的数据库引擎的版本。  
  
### <a name="remarks"></a>备注  
 返回的值表示窗体"major.minor;"中的版本号例如，"3.0 版"。 产品的版本号 (例如，3.0) 组成的版本号 (3)、 句点和发行版号 (0)。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"Version 属性"。  
  
##  <a name="a-namegetworkspacecounta--cdaoworkspacegetworkspacecount"></a><a name="getworkspacecount"></a>CDaoWorkspace::GetWorkspaceCount  
 调用此成员函数以检索 DAO 数据库引擎的工作区集合中的工作区中对象的数目。  
  
```  
short GetWorkspaceCount();
```  
  
### <a name="return-value"></a>返回值  
 打开工作区中工作区集合数。  
  
### <a name="remarks"></a>备注  
 此计数不包括任何打开的工作区，不会追加到集合。 `GetWorkspaceCount`如果您需要循环访问工作区集合中的所有已定义工作区，很有用。 若要获取有关在集合中给定的工作区的信息，请参阅[GetWorkspaceInfo](#getworkspaceinfo)。 典型用法就是调用`GetWorkspaceCount`的几个打开的工作区，然后使用该数字作为循环索引重复调用`GetWorkspaceInfo`。  
  
##  <a name="a-namegetworkspaceinfoa--cdaoworkspacegetworkspaceinfo"></a><a name="getworkspaceinfo"></a>CDaoWorkspace::GetWorkspaceInfo  
 调用此成员函数来获取各种类型的有关工作区中打开的会话中的信息。  
  
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
 `nIndex`  
 在工作区集合中，对于通过索引查找的数据库对象的从零开始的索引。  
  
 `wkspcinfo`  
 对引用[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)返回所请求的信息的对象。  
  
 `dwInfoOptions`  
 指定要检索的工作区的信息的选项。 以及它们会导致返回的函数，这里列出了可用的选项︰  
  
- `AFX_DAO_PRIMARY_INFO`（默认值）名称  
  
- `AFX_DAO_SECONDARY_INFO`加上的主要信息︰ 用户名称  
  
- `AFX_DAO_ALL_INFO`主要和次要信息加上︰ 隔离 ODBCTrans  
  
 `lpszName`  
 按名称查找 workspace 对象名称。 名称是唯一命名新的 workspace 对象最多 14 个字符的字符串。  
  
### <a name="remarks"></a>备注  
 有关在中返回的信息的说明`wkspcinfo`，请参阅[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)结构。 这种结构有对应于上面的说明中列出的信息的项目的成员`dwInfoOptions`。 当请求在某一级别的信息时，您会获得以及前面级别的信息。  
  
##  <a name="a-nameidlea--cdaoworkspaceidle"></a><a name="idle"></a>CDaoWorkspace::Idle  
 调用**空闲**，为数据库引擎提供了执行的后台任务，可能不是最新由于密集数据处理机会。  
  
```  
static void PASCAL Idle(int nAction = dbFreeLocks);
```  
  
### <a name="parameters"></a>参数  
 `nAction`  
 要在空闲处理期间执行的操作。 目前，唯一有效的操作**dbFreeLocks**。  
  
### <a name="remarks"></a>备注  
 这通常是在多用户，在其中没有足够的背景处理时间来保留在记录集中的所有记录当前的多任务处理环境，则返回 true。  
  
> [!NOTE]
>  调用**空闲**与使用 Microsoft Jet 数据库引擎的 3.0 版本创建的数据库没有必要。 使用**空闲**仅用于使用早期版本创建的数据库。  
  
 通常情况下，仅当没有其他操作 （包括鼠标移动） 发生时，才会取消的读取锁定，被更新本地动态集类型记录集对象中的数据。 如果定期调用**空闲**，提供有时间，以便释放来处理任务的背景上保持同步的数据库引擎不需要的读锁。 指定**dbFreeLocks**常量作为参数延迟处理直到所有的读的锁被释放。  
  
 除非正在运行的应用程序的多个实例，该成员函数不需要在单用户环境中。 **空闲**成员函数可提高多用户环境中的性能，因为它会强制数据库引擎将数据刷新到磁盘，释放内存的锁定。 你可以通过将操作的事务的一部分来释放读的锁。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"空闲方法"。  
  
##  <a name="a-nameisopena--cdaoworkspaceisopen"></a><a name="isopen"></a>CDaoWorkspace::IsOpen  
 调用此成员函数以确定是否`CDaoWorkspace`对象处于打开状态 — 即，是否 MFC 对象已初始化通过调用[打开](#open)或调用[创建](#create)。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果工作区对象已打开，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 您可以调用任何成员函数是处于打开状态的工作区。  
  
##  <a name="a-namempdaoworkspacea--cdaoworkspacempdaoworkspace"></a><a name="m_pdaoworkspace"></a>CDaoWorkspace::m_pDAOWorkspace  
 指向基础 DAO 工作区对象的指针。  
  
### <a name="remarks"></a>备注  
 如果您需要直接访问基础的 DAO 对象，请使用此数据成员。 您可以调用通过此指针的 DAO 对象的接口。  
  
 直接访问 DAO 对象有关的信息，请参阅[技术注意 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
##  <a name="a-nameopena--cdaoworkspaceopen"></a><a name="open"></a>CDaoWorkspace::Open  
 显式打开与 DAO 的默认工作区关联的工作区对象。  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 要打开的 DAO 工作区中对象的名称 — 唯一地命名工作区最多 14 个字符的字符串。 接受默认值**NULL**来显式打开默认工作区。 有关命名要求，请参阅`lpszName`参数[创建](#create)。 有关相关信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
### <a name="remarks"></a>备注  
 在构造之后`CDaoWorkspace`对象，请调用该成员函数以执行下列操作之一︰  
  
-   显式打开默认工作区。 Pass **NULL** for `lpszName`.  
  
-   打开一个现有的`CDaoWorkspace`对象、 按名称的工作区集合的成员。 通过现有的工作区中对象的有效名称。  
  
 **打开**将工作区对象置于打开状态，并还初始化数据库引擎，如果它已尚未初始化您的应用程序。  
  
 尽管许多`CDaoWorkspace`函数仅在打开工作区后调用的成员，下面的成员函数，它们对数据库引擎的操作，在后可以获得构造的 c + + 对象，但在调用之前**打开**:  
  
||||  
|-|-|-|  
|[创建](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|  
|[GetIniPath](#getinipath)|[空闲](#idle)|[SetIniPath](#setinipath)|  
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|  
  
##  <a name="a-namerepairdatabasea--cdaoworkspacerepairdatabase"></a><a name="repairdatabase"></a>CDaoWorkspace::RepairDatabase  
 如果您需要以尝试修复访问 Microsoft Jet 数据库引擎的数据库已损坏，则调用此成员函数。  
  
```  
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 路径和文件名将现有的 Microsoft Jet 引擎数据库文件。 如果省略路径，搜索当前的目录。 如果您的系统支持的统一命名约定 (UNC)，您还可以指定网络路径，如:"\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB。MDB"。 (双反斜杠需要路径字符串中，因为"\\"c + + 转义符。)  
  
### <a name="remarks"></a>备注  
 您必须关闭由指定的数据库`lpszName`修复它之前。 在多用户环境中，其他用户不能有`lpszName`打开时将对其进行修复。 如果`lpszName`未关闭或不可用供独占使用，则会出错。  
  
 此成员函数尝试修复的不完整的写操作中被标记为可能已损坏的数据库。 如果使用 Microsoft Jet 数据库引擎的应用程序由于电源故障或计算机硬件的问题而意外关闭，也可能发生。 如果您完成该操作并调用[关闭](../../mfc/reference/cdaodatabase-class.md#close)成员函数，或退出该应用程序在通常的方式，数据库将不能标记为可能已损坏。  
  
> [!NOTE]
>  在修复数据库之后, 它还是压缩它使用一个好主意[CompactDatabase](#compactdatabase)成员函数可对该文件进行碎片整理以恢复磁盘空间。  
  
 有关修复数据库的详细信息，请参阅主题 DAO 帮助中的"RepairDatabase 方法"。  
  
##  <a name="a-namerollbacka--cdaoworkspacerollback"></a><a name="rollback"></a>CDaoWorkspace::Rollback  
 调用该成员函数以结束当前事务并将工作区中的所有数据库都还原为其状态，该事务已开始之前。  
  
```  
void Rollback();
```  
  
### <a name="remarks"></a>备注  
  
> [!CAUTION]
>  一个工作区对象中，事务始终是全局到工作区，并不局限于只有一个数据库或记录集。 如果你执行在多个数据库或在工作区事务中，记录集上的操作**回滚**还原上对所有这些数据库和记录集的所有操作。  
  
 如果在关闭工作区对象而不保存或回滚任何挂起的事务，将自动回滚事务。 如果调用[CommitTrans](#committrans)或**回滚**没有首先调用[BeginTrans](#begintrans)，就会出错。  
  
> [!NOTE]
>  当开始一个事务时，数据库引擎在由 TEMP 环境变量在工作站上指定的目录中保留的文件中记录其操作。 如果事务日志文件耗尽 TEMP 驱动器上的可用存储空间，数据库引擎将使 MFC 引发`CDaoException`（DAO 错误 2004年）。 此时，如果调用**CommitTrans**、 不确定数目的操作被提交，但剩余未完成的操作都将丢失，和该操作必须重新启动。 调用**回滚**释放事务日志，并回滚在事务中的所有操作。  
  
##  <a name="a-namesetdefaultpassworda--cdaoworkspacesetdefaultpassword"></a><a name="setdefaultpassword"></a>CDaoWorkspace::SetDefaultPassword  
 调用该成员函数以将数据库引擎使用 workspace 对象创建不使用特定密码时的默认密码设置。  
  
```  
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```  
  
### <a name="parameters"></a>参数  
 `lpszPassword`  
 默认的密码。 密码长度最多为 14 个字符，并且可以包含除 ASCII 0 (null) 之外的任何字符。 密码是区分大小写。  
  
### <a name="remarks"></a>备注  
 默认密码设置适用于在调用后创建的新工作区。 当创建后续工作区时，不需要指定密码中的[创建](#create)调用。  
  
 若要使用此成员函数︰  
  
1.  构造`CDaoWorkspace`对象但不是调用**创建**。  
  
2.  调用`SetDefaultPassword`并且，如果您愿意， [SetDefaultUser](#setdefaultuser)。  
  
3.  调用**创建**对于此工作区中对象或其他条件，而不在指定的密码。  
  
 默认情况下，DefaultUser 属性设置为"admin"并且 DefaultPassword 属性设置为空字符串 ("")。  
  
 有关安全性的详细信息，请参阅主题 DAO 帮助中的"权限属性"。 有关相关信息，请参阅"DefaultPassword 属性"和"DefaultUser Property"DAO 帮助中的主题。  
  
##  <a name="a-namesetdefaultusera--cdaoworkspacesetdefaultuser"></a><a name="setdefaultuser"></a>CDaoWorkspace::SetDefaultUser  
 调用此成员函数可设置数据库引擎时没有特定的用户名称创建一个工作区中对象所使用的默认用户名称。  
  
```  
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```  
  
### <a name="parameters"></a>参数  
 `lpszDefaultUser`  
 默认用户名。 用户名可以是 1-20 个字符并将包括字母字符、 重音的字符、 数字、 空格和符号除外:"（引号） / （正斜杠）、 \ （反斜杠）、 \[ \] （方括号）: （冒号）、 |（管道） \< (较少-号)，1> (更高版本-号)，+ （加号） = （等于登录），;（分号），（逗号）、 （问号） * （星号），前导空格和控制字符 (ASCII 00 到 ASCII 31)。 有关相关信息，请参阅主题 DAO 帮助中的"用户名属性"。  
  
### <a name="remarks"></a>备注  
 您设置的默认用户名称适用于在调用后创建的新工作区。 当创建后续工作区时，不需要指定用户名，[创建](#create)调用。  
  
 若要使用此成员函数︰  
  
1.  构造`CDaoWorkspace`对象但不是调用**创建**。  
  
2.  调用`SetDefaultUser`并且，如果您愿意， [SetDefaultPassword](#setdefaultpassword)。  
  
3.  调用**创建**对于此工作区中对象或其他条件，而不指定用户名。  
  
 默认情况下，DefaultUser 属性设置为"admin"并且 DefaultPassword 属性设置为空字符串 ("")。  
  
 有关相关信息，请参阅"DefaultUser 属性"和"DefaultPassword Property"DAO 帮助中的主题。  
  
##  <a name="a-namesetinipatha--cdaoworkspacesetinipath"></a><a name="setinipath"></a>CDaoWorkspace::SetIniPath  
 调用该成员函数以指定 Microsoft Jet 数据库引擎的 Windows 注册表设置的位置。  
  
```  
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```  
  
### <a name="parameters"></a>参数  
 *lpszRegistrySubkey*  
 包含一个用于 Microsoft Jet 数据库引擎的设置或所需的可安装 ISAM 数据库参数的位置的 Windows 注册表子项的名称的字符串。  
  
### <a name="remarks"></a>备注  
 调用`SetIniPath`仅当您需要指定特殊设置。 有关详细信息，请参阅主题 DAO 帮助中的"IniPath 属性"。  
  
> [!NOTE]
>  调用`SetIniPath`应用程序在安装期间，不应用程序运行时。 `SetIniPath`必须在调用之前打开任何工作区、 数据库或记录集;否则，MFC 将引发异常。  
  
 可以使用此机制使用用户提供的注册表设置配置数据库引擎。 此属性的作用域仅限于您的应用程序，无需重新启动您的应用程序不能更改。  
  
##  <a name="a-namesetisolateodbctransa--cdaoworkspacesetisolateodbctrans"></a><a name="setisolateodbctrans"></a>CDaoWorkspace::SetIsolateODBCTrans  
 调用此成员函数可设置为工作区的 DAO IsolateODBCTrans 属性的值。  
  
```  
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```  
  
### <a name="parameters"></a>参数  
 *bIsolateODBCTrans*  
 传递**TRUE**如果您想要开始隔离 ODBC 事务。 传递**FALSE**如果你想要停止隔离 ODBC 事务。  
  
### <a name="remarks"></a>备注  
 在某些情况下，可能需要对同一个 ODBC 数据库有挂起的多个同时进行的事务。 若要执行此操作，您需要打开单独的工作区为每个事务。 虽然每个工作区可以有其自己的 ODBC 连接到数据库，这会降低系统性能。 由于事务隔离不是正常情况下必需的默认情况下共享来自多个工作区对象由同一个用户打开的 ODBC 连接。  
  
 某些 ODBC 服务器，例如 Microsoft SQL Server 不允许在单个连接上的同步事务。 如果您需要一次挂起对此类数据库的多个事务，IsolateODBCTrans 属性设置为**TRUE**上每个工作区，就立即打开它。 这将强制一个单独的 ODBC 连接每个工作区。  
  
##  <a name="a-namesetlogintimeouta--cdaoworkspacesetlogintimeout"></a><a name="setlogintimeout"></a>CDaoWorkspace::SetLoginTimeout  
 调用此成员函数可设置为工作区的 DAO LoginTimeout 属性的值。  
  
```  
static void PASCAL SetLoginTimeout(short nSeconds);
```  
  
### <a name="parameters"></a>参数  
 `nSeconds`  
 在您尝试登录到 ODBC 数据库时，将发生错误之前等待的秒数。  
  
### <a name="remarks"></a>备注  
 此值表示在您尝试登录到 ODBC 数据库时，将发生错误之前等待的秒数。 默认 LoginTimeout 设置为 20 秒。 当 LoginTimeout 设置为 0 时，无超时会发生，并且与数据源之间的通信可能会停止响应。  
  
 当您尝试登录到 ODBC 数据库，如 Microsoft SQL Server 连接可能失败发生网络错误或者因为服务器未运行。 而不是等待默认值为 20 秒连接，您可以指定数据库引擎，它将生成错误之前的等待多长时间。 登录到服务器上的大量不同的事件，如在外部服务器数据库上运行查询的一部分隐式发生。 超时值确定由 LoginTimeout 属性的当前设置。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"LoginTimeout 属性"。  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoException 类](../../mfc/reference/cdaoexception-class.md)

