---
title: "CDaoDatabase 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], DAO
- CDaoDatabase class, vs. CDatabase class
- CDaoDatabase class, and workspace
- CDaoDatabase class
- CDatabase class, vs. CDaoDatabase class
ms.assetid: 8ff5b342-964d-449d-bef1-d0ff56aadf6d
caps.latest.revision: 23
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
ms.openlocfilehash: c173ea0c0132752c08504053d9b00cdec8d3f69b
ms.lasthandoff: 02/24/2017

---
# <a name="cdaodatabase-class"></a>CDaoDatabase 类
表示与数据库的连接，通过此连接可操作数据。  
  
## <a name="syntax"></a>语法  
  
```  
class CDaoDatabase : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|构造 `CDaoDatabase` 对象。 调用**打开**对象连接到数据库。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoDatabase::CanTransact](#cantransact)|返回非零，如果数据库支持事务。|  
|[CDaoDatabase::CanUpdate](#canupdate)|返回非零如果`CDaoDatabase`是可更新的对象 （非只读）。|  
|[CDaoDatabase::Close](#close)|关闭数据库连接。|  
|[CDaoDatabase::Create](#create)|创建基础的 DAO 数据库对象并初始化`CDaoDatabase`对象。|  
|[CDaoDatabase::CreateRelation](#createrelation)|在数据库中定义各表之间新的关系。|  
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|删除 querydef 对象保存在数据库的 QueryDefs 集合中。|  
|[CDaoDatabase::DeleteRelation](#deleterelation)|删除现有关系数据库中表之间。|  
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|删除数据库中表的定义。 这将删除实际的表和其所有数据。|  
|[CDaoDatabase::Execute](#execute)|执行动作查询。 调用**Execute**为返回结果的查询将引发异常。|  
|[CDaoDatabase::GetConnect](#getconnect)|返回用于连接的连接字符串`CDaoDatabase`对象传递给数据库。 用于 ODBC。|  
|[CDaoDatabase::GetName](#getname)|返回当前所用的数据库的名称。|  
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|返回为数据库定义的查询数。|  
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|返回有关指定数据库中定义的查询信息。|  
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|返回多少秒后的数据库查询操作将超时。 影响所有后续打开、 添加新项、 更新和编辑操作和 ODBC 数据源上的其他操作 （仅限） 如**Execute**调用。|  
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|返回的记录数受上次更新编辑或添加操作或通过调用**Execute**。|  
|[CDaoDatabase::GetRelationCount](#getrelationcount)|返回数据库中的表之间定义关系的数量。|  
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|返回有关指定数据库中的表之间定义关系的信息。|  
|[Cdaodatabase:: Gettabledefcount](#gettabledefcount)|返回数据库中定义的表的数目。|  
|[Cdaodatabase:: Gettabledefinfo](#gettabledefinfo)|在数据库中返回有关指定表的信息。|  
|[CDaoDatabase::GetVersion](#getversion)|返回与数据库相关联的数据库引擎的版本。|  
|[CDaoDatabase::IsOpen](#isopen)|返回非零 if`CDaoDatabase`对象当前连接到数据库。|  
|[CDaoDatabase::Open](#open)|建立到数据库的连接。|  
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|集多少秒后的数据库查询 （在仅 ODBC 数据源） 的操作将超时。 影响所有后续打开、 添加新项、 更新和删除操作。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|指向基础 DAO 数据库对象的指针。|  
|[CDaoDatabase::m_pWorkspace](#m_pworkspace)|一个指向[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)对象，包含数据库，并定义自己的事务空间。|  
  
## <a name="remarks"></a>备注  
 有关支持的数据库格式的信息，请参阅[GetName](../../mfc/reference/cdaoworkspace-class.md#getname)成员函数。 您可以有一个或多个`CDaoDatabase`给定"工作区中，"所表示的活动一次对象[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)对象。 工作区保持打开的数据库对象，调用数据库集合的集合。  
  
> [!NOTE]
>  MFC DAO 数据库类均不同于基于 ODBC 的 MFC 数据库类中。 DAO 数据库类的所有名称都具有"CDao"前缀。 类`CDaoDatabase`提供类似于 ODBC 类的接口[CDatabase](../../mfc/reference/cdatabase-class.md)。 主要区别在于`CDatabase`为 DBMS 通过开放式数据库连接 (ODBC) 和 ODBC 驱动程序访问 DBMS。 `CDaoDatabase`通过数据访问对象 (DAO) 基于 Microsoft Jet 数据库引擎来访问数据。 通常情况下，基于 DAO MFC 类包括更强于基于 ODBC; 的 MFC 类基于 DAO 的类可以访问数据，包括通过 ODBC 驱动程序，通过其自己的数据库引擎。 基于 DAO 的类还支持数据定义语言 (DDL) 操作，如添加表通过类，而无需直接调用 DAO。  
  
## <a name="usage"></a>用法  
 在创建记录集对象时，您可以隐式地创建数据库对象。 但是，您还可以显式创建数据库对象。 若要使用现有数据库使用显式`CDaoDatabase`，请执行下列操作之一︰  
  
-   构造`CDaoDatabase`对象，将指针传递到已打开[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)对象。  
  
-   或构建`CDaoDatabase`而无需指定工作区 （MFC 创建的临时工作区对象） 的对象。  
  
 若要创建新的 Microsoft Jet (。MDB) 数据库构造`CDaoDatabase`对象，并调用其[创建](#create)成员函数。 不要*不*调用**打开**后**创建**。  
  
 若要打开现有的数据库，构造`CDaoDatabase`对象，并调用其[打开](#open)成员函数。  
  
 这些方法之一将 DAO 数据库对象追加到工作区中的数据库集合并打开与数据的连接。 当然后构造[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)， [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)，或[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)对象的操作系统上的连接的数据库，这些对象的构造函数将一个指针传递到您`CDaoDatabase`对象。 当您完成使用连接时，调用[关闭](#close)成员函数，并销毁`CDaoDatabase`对象。 **关闭**关闭还没有以前关闭的任何记录集。  
  
## <a name="transactions"></a>事务  
 在工作区级别提供数据库事务处理，请参阅[BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans)， [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans)，和[回滚](../../mfc/reference/cdaoworkspace-class.md#rollback)类的成员函数`CDaoWorkspace`。  
  
## <a name="odbc-connections"></a>ODBC 连接  
 若要使用 ODBC 数据源的推荐的方式是将外部表附加到 Microsoft Jet (。MDB) 数据库。  
  
## <a name="collections"></a>集合  
 每个数据库维护其自己 tabledef、 querydef、 记录和关系对象的集合。 类`CDaoDatabase`提供了用于处理这些对象的成员函数。  
  
> [!NOTE]
>  对象存储在 DAO 中，不在 MFC 数据库对象。 MFC 提供了有关 tabledef、 querydef 和记录集对象而不是关系对象的类。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoDatabase`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdao.h  
  
##  <a name="cantransact"></a>CDaoDatabase::CanTransact  
 调用此成员函数以确定数据库是否允许事务。  
  
```  
BOOL CanTransact();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果数据库支持事务。否则为 0。  
  
### <a name="remarks"></a>备注  
 事务在数据库的工作区中进行管理。  
  
##  <a name="canupdate"></a>CDaoDatabase::CanUpdate  
 调用此成员函数以确定是否`CDaoDatabase`对象允许更新。  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>返回值  
 如果非零`CDaoDatabase`对象允许更新; 否则为 0，该值指示该你传递**TRUE**中`bReadOnly`在您打开`CDaoDatabase`对象或数据库本身是只读的。 请参阅[打开](#open)成员函数。  
  
### <a name="remarks"></a>备注  
 数据库可更新性有关的信息，请参阅主题 DAO 帮助中的"可更新属性"。  
  
##  <a name="cdaodatabase"></a>CDaoDatabase::CDaoDatabase  
 构造 `CDaoDatabase` 对象。  
  
```  
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pWorkspace*  
 一个指向`CDaoWorkspace`将包含新的数据库对象的对象。 如果您接受默认值为**NULL**，构造函数创建一个临时`CDaoWorkspace`使用默认 DAO 工作区的对象。 您可以获取指向通过工作区对象的指针[m_pWorkspace](#m_pworkspace)数据成员。  
  
### <a name="remarks"></a>备注  
 后构造该对象，如果您正在创建新的 Microsoft Jet (。MDB) 数据库中，调用对象的[创建](#create)成员函数。 如果您是，相反，打开现有的数据库，调用对象的[打开](#open)成员函数。  
  
 当您完成与该对象时，应调用其[关闭](#close)成员函数，然后销毁`CDaoDatabase`对象。  
  
 您可能会发现方便嵌入`CDaoDatabase`中您的文档类对象。  
  
> [!NOTE]
>  一个`CDaoDatabase`如果打开，也会隐式创建对象[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象而无需将指针传递到一个现有`CDaoDatabase`对象。 当您关闭记录集对象时，此数据库对象已关闭。  
  
##  <a name="close"></a>CDaoDatabase::Close  
 调用该成员函数以从数据库断开连接，然后关闭任何打开的记录集、 tabledefs 和 querydefs 与数据库相关联。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 很好的做法这些对象自行关闭前调用此成员函数。 关闭`CDaoDatabase`对象将其从中关联的数据库集合删除[工作区](../../mfc/reference/cdaoworkspace-class.md)。 因为**关闭**不会销毁`CDaoDatabase`对象，通过打开同一个数据库或不同的数据库，可以重用该对象。  
  
> [!CAUTION]
>  调用[更新](../../mfc/reference/cdaorecordset-class.md#update)成员函数 （如果有挂起的编辑） 和**关闭**之前关闭的数据库的所有打开的记录集对象的成员函数。 如果您退出声明的函数[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)或`CDaoDatabase`对象在堆栈上，数据库已关闭、 未保存的任何更改都将丢失、 所有挂起的事务将回滚，和任何挂起的编辑您的数据都将丢失。  
  
> [!CAUTION]
>  如果您尝试关闭的数据库对象，而任何记录集对象处于打开状态，或者尝试关闭工作区对象，当属于该特定工作区的任何数据库对象打开时，将关闭这些记录集对象，并且任何挂起的更新或编辑将被回滚。 如果您尝试打开了属于该任何数据库对象时关闭工作区对象，该操作将关闭属于该特定工作区中的对象，它可能会导致正在关闭的不完整的记录集对象的所有数据库对象。 如果不关闭您的数据库对象，MFC 将报告在调试版本中的断言失败。  
  
 如果函数的范围之外定义的数据库对象，而不关闭它退出函数的数据库对象将保持打开，直到显式关闭或在其中定义该模块是超出范围。  
  
##  <a name="create"></a>CDaoDatabase::Create  
 若要创建新的 Microsoft Jet (。MDB) 数据库中，调用此成员函数之后您构造,`CDaoDatabase`对象。  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    LPCTSTR lpszLocale = dbLangGeneral,  
    int dwOptions = 0);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 字符串表达式，表示要创建的数据库文件的名称。 它可以完整路径和文件名，如"c:\\\MYDB。MDB"。 您必须提供一个名称。 如果不提供文件扩展名。追加 MDB。 如果您的网络支持的统一命名约定 (UNC)，您还可以指定网络路径，如"\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB"。 仅 Microsoft Jet (。可以使用此成员函数创建 MDB) 数据库文件。 (双反斜杠要求中的字符串文字，因为"\\"c + + 转义符。)  
  
 `lpszLocale`  
 用来指定用于创建数据库的排序规则顺序的字符串表达式。 默认值是**dbLangGeneral**。 可能的值有：  
  
- **dbLangGeneral**英语、 德语、 法语、 葡萄牙语、 意大利语和现代西班牙语  
  
- **dbLangArabic**阿拉伯语  
  
- **dbLangCyrillic**俄语  
  
- **dbLangCzech**捷克语  
  
- **dbLangDutch**荷兰语  
  
- **dbLangGreek**希腊语  
  
- **dbLangHebrew**希伯来语  
  
- **dbLangHungarian**匈牙利语  
  
- **dbLangIcelandic**冰岛语  
  
- **dbLangNordic**北欧语言 （Microsoft Jet 数据库引擎版本 1.0 仅）  
  
- **dbLangNorwdan**挪威语和丹麦语  
  
- **dbLangPolish**波兰语  
  
- **dbLangSpanish**传统西班牙语  
  
- **dbLangSwedfin**瑞典语和芬兰语  
  
- **dbLangTurkish**土耳其语  
  
 `dwOptions`  
 一个整数，指示一个或多个选项。 可能的值有：  
  
- **dbEncrypt**创建加密的数据库。  
  
- **dbVersion10**用于 Microsoft Jet 数据库版本 1.0 中创建数据库。  
  
- **dbVersion11**使用 Microsoft Jet 数据库 1.1 版创建的数据库。  
  
- **dbVersion20**使用 Microsoft Jet 数据库版本 2.0 创建的数据库。  
  
- **dbVersion30** 3.0 版 Microsoft Jet 数据库创建数据库。  
  
 如果省略加密常量，则创建未加密的数据库。 您可以指定只有一个版本常量。 如果省略版本常量，创建一个数据库，用 Microsoft Jet 数据库版本 3.0。  
  
> [!CAUTION]
>  如果数据库未加密，则有可能，即使您实现用户/密码安全性，以直接读取构成数据库的二进制文件磁盘文件。  
  
### <a name="remarks"></a>备注  
 **创建**创建数据库文件和基础 DAO 数据库对象并初始化 c + + 对象。 对象添加到相关的工作区数据库集合中。 数据库对象是处于打开状态;不要调用**打开**后**创建**。  
  
> [!NOTE]
>  与**创建**，您可以创建只有 Microsoft Jet (。MDB) 数据库。 无法创建 ISAM 数据库或 ODBC 数据库。  
  
##  <a name="createrelation"></a>CDaoDatabase::CreateRelation  
 调用该成员函数以建立在数据库中的主表中的一个或多个字段和外部表 （在数据库中的另一个表） 中的一个或多个字段之间的关系。  
  
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
 `lpszName`  
 关系对象的唯一名称。 名称必须以字母开头，并可以包含 40 个字符的最大值。 可以包含数字和下划线字符，但不能包括标点符号和空格。  
  
 `lpszTable`  
 该关系中的主表的名称。 如果表不存在，MFC 将引发类型的异常[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
 `lpszForeignTable`  
 外部表关系中的名称。 如果表不存在，MFC 将引发类型的异常`CDaoException`。  
  
 `lAttributes`  
 一个长值，包含关系类型有关的信息。 此值可用于强制实施引用完整性，等等。 您可以使用按位 OR 运算符 ( **|**) 将以下值中的任何组合 （前提是有意义的组合）︰  
  
- **dbRelationUnique**关系是一对一。  
  
- **dbRelationDontEnforce**关系不是强制执行 （无参照完整性）。  
  
- **dbRelationInherited**包含两个附加的表的非当前数据库中存在的关系。  
  
- **两**将级联更新 （级联的详细信息，请参阅备注）。  
  
- **dbRelationDeleteCascade**将级联删除。  
  
 *lpszField*  
 指向以 null 结尾的字符串，包含主表中的字段的名称 (通过名为`lpszTable`)。  
  
 *lpszForeignField*  
 指向以 null 结尾的字符串，包含外部表中的字段的名称 (通过名为`lpszForeignTable`)。  
  
 *relinfo*  
 对引用[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)对象，其中包含你想要创建的关系的信息。  
  
### <a name="remarks"></a>备注  
 关系不能包含查询或附加的表从外部数据库。  
  
 当该关系涉及每两个表中的一个字段时，请使用该函数的第一个版本。 当该关系涉及多个字段时，请使用第二个版本。 在关系中的字段的最大数为 14。  
  
 此操作将创建基本的 DAO 关系对象，但这是 MFC 实现的细节，因为类中包含的关系对象的 MFC 的封装`CDaoDatabase`。 MFC 不提供针对关系的类。  
  
 如果您将关系设置对象的属性，用于激活 cascade 操作，数据库引擎将自动更新或删除一个或多个其他表中相关主键表发生更改时。  
  
 例如，假设您建立客户表和 Orders 表之间的级联删除关系。 当从客户表中删除记录时，也将删除与该客户的 Orders 表中的记录。 此外，如果建立订单表和其他表之间的级联删除关系，则在从客户表中删除记录时，会自动删除这些表中的记录。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"CreateRelation 方法"。  
  
##  <a name="deletequerydef"></a>CDaoDatabase::DeleteQueryDef  
 调用此成员函数以删除指定的 querydef — 已保存的查询 — 从`CDaoDatabase`对象的 QueryDefs 集合。  
  
```  
void DeleteQueryDef(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 若要删除的已保存查询的名称。  
  
### <a name="remarks"></a>备注  
 之后，该查询不能再在数据库中定义。  
  
 有关创建 querydef 对象的信息，请参阅类[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 Querydef 对象将成为关联与特定`CDaoDatabase`对象在构造时`CDaoQueryDef`对象，它将指针传递给数据库对象。  
  
##  <a name="deleterelation"></a>CDaoDatabase::DeleteRelation  
 调用该成员函数以从数据库对象关系集合中删除现有关系。  
  
```  
void DeleteRelation(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 要删除的关系的名称。  
  
### <a name="remarks"></a>备注  
 之后，关系不再存在。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"删除方法"。  
  
##  <a name="deletetabledef"></a>CDaoDatabase::DeleteTableDef  
 调用此成员函数以删除指定的表及其所有从其数据`CDaoDatabase`对象的 TableDefs 集合。  
  
```  
void DeleteTableDef(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 若要删除 tabledef 的名称。  
  
### <a name="remarks"></a>备注  
 之后，该表不能再在数据库中定义。  
  
> [!NOTE]
>  要非常小心，以免删除系统表。  
  
 有关创建 tabledef 对象的信息，请参阅类[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)。 Tabledef 对象将成为关联与特定`CDaoDatabase`对象在构造时`CDaoTableDef`对象，它将指针传递给数据库对象。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"删除方法"。  
  
##  <a name="execute"></a>CDaoDatabase::Execute  
 调用该成员函数以执行动作查询或对数据库执行 SQL 语句。  
  
```  
void Execute(
    LPCTSTR lpszSQL,  
    int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>参数  
 `lpszSQL`  
 指向以 null 结尾的字符串，包含要执行的有效 SQL 命令。  
  
 `nOptions`  
 一个整数，指定与该查询的完整性相关的选项。 您可以使用按位 OR 运算符 ( **|**) 将组合任何以下常量 (提供组合有意义 — 例如，不会合并**dbInconsistent**与**dbConsistent**):  
  
- **dbDenyWrite**拒绝向其他用户授权写入权限。  
  
- **dbInconsistent** （默认值） 不一致的更新。  
  
- **dbConsistent**一致的更新。  
  
- **dbSQLPassThrough** SQL 传递。 使 SQL 语句，以传递到 ODBC 数据源以进行处理。  
  
- **dbFailOnError**出错时回滚更新。  
  
- **dbSeeChanges**生成运行时错误，如果另一个用户是正在更改您正在编辑的数据。  
  
> [!NOTE]
>  如果两个**dbInconsistent**和**dbConsistent**包括或者如果这都包括在内，则结果为默认值。 有关这些常量中的说明，请参阅主题 DAO 帮助中的"执行方法"。  
  
### <a name="remarks"></a>备注  
 **执行**仅适用于操作的查询或不返回结果的 SQL 传递查询。 不适用于 select 查询，返回的记录。  
  
 有关定义和有关操作查询的信息，请参阅"操作查询"和"执行方法"DAO 帮助中的主题。  
  
> [!TIP]
>  在给定语法正确的 SQL 语句和适当的权限， **Execute**成员函数不会发生故障甚至如果不是可以修改或删除单个行。 因此，始终使用**dbFailOnError**选项时使用**Execute**成员函数以进行更新或删除查询。 该选项将导致引发异常的类型的 MFC [CDaoException](../../mfc/reference/cdaoexception-class.md)并回滚所有成功的更改，如果任何受影响的记录将被锁定，无法更新或删除。 请注意，始终可以调用`GetRecordsAffected`以查看影响了多少条记录。  
  
 调用[GetRecordsAffected](#getrecordsaffected)成员函数的数据库对象，以确定受影响的最新的记录数**Execute**调用。 例如，`GetRecordsAffected`返回有关已删除、 更新或执行操作查询时插入的记录数的信息。 返回的计数不会反映在级联更新或删除时的相关表中的更改都生效。  
  
 **执行**不会返回一个记录集。 使用**Execute**上选择记录的查询将导致引发异常的类型的 MFC `CDaoException`。 (没有任何`ExecuteSQL`成员函数类似于`CDatabase::ExecuteSQL`。)  
  
##  <a name="getconnect"></a>CDaoDatabase::GetConnect  
 调用此成员函数来检索连接字符串用于连接`CDaoDatabase`到 ODBC 或 ISAM 数据库对象。  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>返回值  
 如果连接字符串[打开](#open)已成功打开 ODBC 数据源上调用; 否则为空字符串。 用于 Microsoft Jet (。MDB) 数据库，该字符串是始终是空除非将其设置为用于**dbSQLPassThrough**选项用于[Execute](#execute)成员函数或用于打开一个记录集。  
  
### <a name="remarks"></a>备注  
 该字符串提供了有关打开的数据库或传递查询中使用的数据库的源的信息。 连接字符串组成的数据库类型说明符和零个或多个参数之间用分号分隔。  
  
> [!NOTE]
>  使用 MFC DAO 类连接到通过 ODBC 数据源会降低效率比通过附加表进行连接。  
  
> [!NOTE]
>  连接字符串用于将附加信息传递到 ODBC 和根据需要某些 ISAM 驱动程序。 不被用于。MDB 的数据库。 对于 Microsoft Jet 数据库的基础表，连接字符串为空字符串 ("") 除外何时使用它对于 SQL 传递查询返回的值更高版本下所述。  
  
 请参阅[打开](#open)成员函数，创建连接字符串的方式的说明。 设置连接字符串后**打开**调用时，更高版本可用它来检查设置，以确定类型、 路径、 用户 ID、 密码或 ODBC 数据源的数据库。  
  
##  <a name="getname"></a>CDaoDatabase::GetName  
 调用此成员函数可检索当前打开的数据库，它是现有数据库文件的名称的名称或已注册的 ODBC 数据源的名称。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>返回值  
 完整路径和数据库，如果成功，则文件名称否则为空[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>备注  
 如果您的网络支持的统一命名约定 (UNC)，您还可以指定网络路径 — 例如，"\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB。MDB"。 (双反斜杠要求中的字符串文字，因为"\\"c + + 转义符。)  
  
 例如，可能会想要将该名称显示在标题中。 如果在检索名称时出错，MFC 将引发类型的异常[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
> [!NOTE]
>  为了更好的性能时要访问外部数据库，我们建议将外部数据库表附加到 Microsoft Jet 数据库 (。MDB) 而不是直接连接至数据源。  
  
 数据库类型的文件或目录的路径点，如下所示，由指示︰  
  
|路径名指向...|数据库类型|  
|--------------------------|-------------------|  
|.MDB 文件|Microsoft Jet 数据库 (Microsoft Access)|  
|包含目录。DBF 文件|dBASE 数据库|  
|包含目录。XLS 文件中|Microsoft Excel 数据库|  
|包含目录。PDX 文件|Paradox 数据库|  
|包含格式正确的文本数据库文件目录|文本格式数据库|  
  
 对于如 SQL Server 和 Oracle 的 ODBC 数据库，数据库的连接字符串标识注册由 ODBC 数据源名称 (DSN)。  
  
##  <a name="getquerydefcount"></a>CDaoDatabase::GetQueryDefCount  
 调用此成员函数以检索在数据库的 QueryDefs 集合中定义的查询数。  
  
```  
short GetQueryDefCount();
```  
  
### <a name="return-value"></a>返回值  
 数据库中定义的查询数。  
  
### <a name="remarks"></a>备注  
 `GetQueryDefCount`如果您需要循环遍历所有 querydefs QueryDefs 集合中，非常有用。 若要获取有关在集合中给定的查询的信息，请参阅[GetQueryDefInfo](#getquerydefinfo)。  
  
##  <a name="getquerydefinfo"></a>CDaoDatabase::GetQueryDefInfo  
 调用此成员函数来获取各种类型的数据库中定义的查询有关的信息。  
  
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
 `nIndex`  
 在数据库的 QueryDefs 集合中，对于通过索引查找预定义的查询的索引。  
  
 *querydefinfo*  
 对引用[CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md)返回所请求的信息的对象。  
  
 `dwInfoOptions`  
 指定要检索的记录集有关的信息的选项。 以及它们会导致该函数返回有关记录集，这里列出了可用的选项︰  
  
- `AFX_DAO_PRIMARY_INFO`（默认值）名称、 类型  
  
- `AFX_DAO_SECONDARY_INFO`加上的主要信息︰ 日期已创建、 上次更新日期、 返回的记录、 可更新  
  
- `AFX_DAO_ALL_INFO`主要和次要信息加上︰ SQL 中，连接中，odbc 超时  
  
 `lpszName`  
 包含按名称查找的数据库中定义的查询的名称的字符串。  
  
### <a name="remarks"></a>备注  
 提供两个版本的函数，让您可以选择一个查询数据库的 QueryDefs 集合中的索引或查询的名称。  
  
 有关在中返回的信息的说明*querydefinfo*，请参阅[CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md)结构。 这种结构有对应于上面的说明中列出的信息的项目的成员`dwInfoOptions`。 如果您请求的信息的一个级别，将获得信息以及任何前面级别。  
  
##  <a name="getquerytimeout"></a>CDaoDatabase::GetQueryTimeout  
 调用此成员函数可检索当前连接的数据库上的后续操作已超时前允许的秒数。  
  
```  
short GetQueryTimeout();
```  
  
### <a name="return-value"></a>返回值  
 包含以秒为单位的超时值的短整数。  
  
### <a name="remarks"></a>备注  
 由于网络访问权限问题、 过多的查询处理时间等的操作可能会超时。 该设置生效时，它会影响所有打开的、 添加新项、 更新和任何与此相关的记录集上的 delete 操作`CDaoDatabase`对象。 您可以通过调用来更改当前的超时设置[SetQueryTimeout](#setquerytimeout)。 在打开后更改记录集的查询超时值不会更改为记录集的值。 例如，后续[移动](../../mfc/reference/cdaorecordset-class.md#move)操作不使用新值。 初始化数据库引擎时，最初设置的默认值。  
  
 查询超时的默认值执行从 Windows 注册表中。 如果无注册表设置，默认值为 60 秒。 并非所有数据库都支持的功能，以设置查询超时值。 如果设置为 0 的查询超时值时，会发生无超时;并且，与数据库通信可能停止响应。 在开发过程中，此行为可能很有用。 如果调用失败，MFC 将引发类型的异常[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"QueryTimeout 属性"。  
  
##  <a name="getrecordsaffected"></a>CDaoDatabase::GetRecordsAffected  
 调用此成员函数以确定最近的调用的受影响的记录数[Execute](#execute)成员函数。  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>返回值  
 包含受影响的记录数的长整数。  
  
### <a name="remarks"></a>备注  
 返回的值包括删除、 更新或由操作查询进行插入的记录数**Execute**。 返回的计数不会反映在级联更新或删除时的相关表中的更改都生效。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"RecordsAffected 属性"。  
  
##  <a name="getrelationcount"></a>CDaoDatabase::GetRelationCount  
 调用该成员函数以获取在数据库中的表之间定义关系的数量。  
  
```  
short GetRelationCount();
```  
  
### <a name="return-value"></a>返回值  
 在数据库中的表之间定义关系的数量。  
  
### <a name="remarks"></a>备注  
 **GetRelationCount**如果您需要循环访问的数据库关系集合中的所有已定义关系会很有用。 若要获取有关给定关系在集合中的信息，请参阅[GetRelationInfo](#getrelationinfo)。  
  
 为了阐明关系的概念，请考虑 Suppliers 表和 Products 表，它可能没有一个对多关系。 在这种关系，一个供应商可以提供多个产品。 其他关系是一对一和多对多。  
  
##  <a name="getrelationinfo"></a>CDaoDatabase::GetRelationInfo  
 调用该成员函数以获取有关数据库的关系集合中的指定关系的信息。  
  
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
 `nIndex`  
 在数据库的关系集合中，对于通过索引的查找关系对象的索引。  
  
 *relinfo*  
 对引用[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)返回所请求的信息的对象。  
  
 `dwInfoOptions`  
 指定要检索的关系有关的信息的选项。 以及它们会导致该函数返回有关该关系，这里列出了可用的选项︰  
  
- `AFX_DAO_PRIMARY_INFO`（默认值）名称，表中，外部表  
  
- `AFX_DAO_SECONDARY_INFO`属性、 字段信息  
  
 字段信息是[CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md)对象，其中包含来自关系中所涉及的主表的字段。  
  
 `lpszName`  
 包含按名称查找关系对象的名称的字符串。  
  
### <a name="remarks"></a>备注  
 按索引或名称，则此函数的两个版本提供的访问。 有关在中返回的信息的说明*relinfo*，请参阅[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)结构。 这种结构有对应于上面的说明中列出的信息的项目的成员`dwInfoOptions`。 如果请求在某一级别的信息，您还在任何以前的级别上获取的信息。  
  
> [!NOTE]
>  如果您将关系设置对象的属性，用于激活级联操作 ( **dbRelationUpdateCascades**或**dbRelationDeleteCascades**)、 Microsoft Jet 数据库引擎会自动更新或删除记录在一个或多个其他表发生更改时对相关主键表。 例如，假设您建立客户表和 Orders 表之间的级联删除关系。 当从客户表中删除记录时，也将删除与该客户的 Orders 表中的记录。 此外，如果建立订单表和其他表之间的级联删除关系，则在从客户表中删除记录时，会自动删除这些表中的记录。  
  
##  <a name="gettabledefcount"></a>Cdaodatabase:: Gettabledefcount  
 调用此成员函数以检索数据库中定义的表的数目。  
  
```  
short GetTableDefCount();
```  
  
### <a name="return-value"></a>返回值  
 Tabledefs 数据库中定义的数量。  
  
### <a name="remarks"></a>备注  
 `GetTableDefCount`如果您需要循环访问该数据库的 TableDefs 集合中的所有 tabledefs，非常有用。 若要获取有关给定表集合中的信息，请参阅[GetTableDefInfo](#gettabledefinfo)。  
  
##  <a name="gettabledefinfo"></a>Cdaodatabase:: Gettabledefinfo  
 调用此成员函数来获取各种类型的数据库中定义的表有关的信息。  
  
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
 `nIndex`  
 在数据库的 TableDefs 集合中，对于通过索引查找 tabledef 对象的索引。  
  
 `tabledefinfo`  
 对引用[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)返回所请求的信息的对象。  
  
 `dwInfoOptions`  
 指定要检索的表有关的信息的选项。 以及它们会导致该函数返回有关该关系，这里列出了可用的选项︰  
  
- `AFX_DAO_PRIMARY_INFO`（默认值）可更新的、 名称、 属性  
  
- `AFX_DAO_SECONDARY_INFO`加上的主要信息︰ 日期创建，上次更新日期，源表名称，连接  
  
- `AFX_DAO_ALL_INFO`主要和次要信息加上︰ 验证规则，验证文本记录计数  
  
 `lpszName`  
 按名称查找 tabledef 对象名称。  
  
### <a name="remarks"></a>备注  
 提供两个版本的函数，这样您可以选择一个表的数据库 TableDefs 集合中的索引或表的名称。  
  
 有关在中返回的信息的说明`tabledefinfo`，请参阅[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)结构。 这种结构有对应于上面的说明中列出的信息的项目的成员`dwInfoOptions`。 如果您请求在某一级别的信息，您将获取任何以前的级别的信息。  
  
> [!NOTE]
>  `AFX_DAO_ALL_INFO`选项提供了可能会很慢，若要获取的信息。 在这种情况下，计算表中的记录的数量可能需要花大量时间在有多个记录。  
  
##  <a name="getversion"></a>CDaoDatabase::GetVersion  
 调用此成员函数来确定 Microsoft Jet 数据库文件的版本。  
  
```  
CString GetVersion();
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，该值指示与对象关联的数据库文件的版本。  
  
### <a name="remarks"></a>备注  
 返回的值表示窗体"major.minor;"中的版本号例如，"3.0 版"。 产品的版本号 (例如，3.0) 组成的版本号 (3)、 句点和发行版号 (0)。 结束日期的版本是 1.0、 1.1、 2.0 和 3.0。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"Version 属性"。  
  
##  <a name="isopen"></a>CDaoDatabase::IsOpen  
 调用此成员函数以确定是否`CDaoDatabase`对象是一个数据库上当前打开的。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果非零`CDaoDatabase`对象是当前打开; 否则为 0。  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_pdaodatabase"></a>CDaoDatabase::m_pDAODatabase  
 包含指向 DAO 数据库对象基础的 OLE 接口的指针`CDaoDatabase`对象。  
  
### <a name="remarks"></a>备注  
 如果您需要直接访问 DAO 接口，请使用此指针。  
  
 调用 DAO 有关的信息，请参阅[技术注意 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
##  <a name="m_pworkspace"></a>CDaoDatabase::m_pWorkspace  
 包含一个指向[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)对象，其中包含的数据库对象。  
  
### <a name="remarks"></a>备注  
 如果您需要直接访问工作区，请使用此指针 — 例如，若要获取指向工作区中的数据库集合中的其他数据库对象的指针。  
  
##  <a name="open"></a>CDaoDatabase::Open  
 必须调用该成员函数以初始化新构造`CDaoDatabase`表示现有数据库对象。  
  
```  
virtual void Open(
    LPCTSTR lpszName,  
    BOOL bExclusive = FALSE,  
    BOOL bReadOnly = FALSE,  
    LPCTSTR lpszConnect = _T(""));
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 是现有的 Microsoft Jet 的名称的字符串表达式 (。MDB) 数据库文件。 如果文件名扩展名，则需要。 如果您的网络支持的统一命名约定 (UNC)，您还可以指定网络路径，如"\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB。MDB"。 (双反斜杠要求中的字符串文字，因为"\\"c + + 转义符。)  
  
 使用时，需要注意一些事项适用`lpszName`。 如果它︰  
  
-   已由另一个用户，MFC 将引发异常的类型的独占访问打开的数据库是指[CDaoException](../../mfc/reference/cdaoexception-class.md)。 捕获该异常，让您的用户了解数据库将不可用。  
  
-   为空字符串 ("") 和*lpszConnect*是"ODBC;"，以便用户可以选择数据库，将显示一个对话框，列出所有已注册的 ODBC 数据源名称。 应避免直接连接到 ODBC 数据源;请改用附加的表。  
  
-   否则不引用现有数据库或有效的 ODBC 数据源名称，MFC 则引发一个类型的异常`CDaoException`。  
  
> [!NOTE]
>  有关 DAO 错误代码的详细信息，请参阅 DAOERR。H 文件。 有关相关信息，请参阅主题中的"可捕获的数据访问错误"DAO 帮助。  
  
 `bExclusive`  
 一个布尔值，则**TRUE**数据库是否要打开以进行独占 （非共享） 的访问权限和**FALSE**如果数据库位于要打开以进行共享访问。 如果省略此参数，则可共享访问打开数据库。  
  
 `bReadOnly`  
 一个布尔值，则**TRUE**数据库是否要打开以进行只读访问权限和**FALSE**如果数据库位于要打开以进行读/写访问。 如果省略此参数，则为读/写访问打开数据库。 所有从属记录集中继承该属性。  
  
 `lpszConnect`  
 字符串表达式，用于打开数据库。 此字符串构成 ODBC 连接参数。 必须提供要提供源字符串的排他锁和只读的参数。 如果该数据库是 Microsoft Jet 数据库 (。MDB)，该字符串为空 ("")。 默认值的语法 — **_T**("")-提供为 Unicode 和 ANSI 可移植性构建您的应用程序。  
  
### <a name="remarks"></a>备注  
 **打开**将数据库与基础的 DAO 对象相关联。 数据库对象不能用于构造记录集、 tabledef 或 querydef 对象初始化之前。 **打开**将数据库对象追加到相关的工作区数据库集合。  
  
 使用参数，如下所示︰  
  
-   若要打开 Microsoft Jet (。MDB) 数据库中，使用`lpszName`参数并传递一个空字符串为`lpszConnect`参数或传递窗体的密码字符串";PWD = 密码"如果数据库是受密码保护 (。MDB 仅限数据库）。  
  
-   如果同时打开 ODBC 数据源，将传递有效的 ODBC 连接字符串中`lpszConnect`中为空字符串`lpszName`。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"OpenDatabase 方法"。  
  
> [!NOTE]
>  为了提高性能时访问外部数据库，包括 ISAM 数据库和 ODBC 数据源中，建议将外部数据库表附加到 Microsoft Jet 引擎数据库 (。MDB) 而不是直接连接至数据源。  
  
 如果 DBMS 主机不可用，，则可以对连接尝试超时。 如果连接尝试失败，**打开**引发类型的异常[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
 剩余的备注仅适用于 ODBC 数据库︰  
  
 如果数据库是 ODBC 数据库和参数按您**打开**调用不包含足够的信息来建立连接时，ODBC 驱动程序打开一个对话框，从用户获取所需的信息。 当您调用**打开**，您的连接字符串， `lpszConnect`、 私下存储，可通过调用[GetConnect](#getconnect)成员函数。  
  
 如果您愿意，您可以打开对话框中，调用之前**打开**以获取信息从用户，如密码，然后将该信息对连接字符串传递给**打开**。 或者您可能想要节省以便您可以重复使用它的下一步 （可能是在 Windows 注册表中） 传递的连接字符串的时间应用程序调用**打开**上`CDaoDatabase`对象。  
  
 您还可以针对多个级别的登录授权使用连接字符串 (每个不同`CDaoDatabase`对象)，或者传递其他特定于数据库的信息。  
  
##  <a name="setquerytimeout"></a>CDaoDatabase::SetQueryTimeout  
 调用该成员函数以重写默认超时值已连接的数据库上的后续操作前允许的秒数。  
  
```  
void SetQueryTimeout(short nSeconds);
```  
  
### <a name="parameters"></a>参数  
 `nSeconds`  
 超时前的查询尝试允许的秒数。  
  
### <a name="remarks"></a>备注  
 由于网络访问权限问题、 过多的查询处理时间等的操作可能会超时。 调用`SetQueryTimeout`打开记录集之前或在调用记录集的前[AddNew](../../mfc/reference/cdaorecordset-class.md#addnew)，[更新](../../mfc/reference/cdaorecordset-class.md#update)，或[删除](../../mfc/reference/cdaorecordset-class.md#delete)成员函数，如果您想要更改查询超时值。 该设置将影响所有后续[打开](../../mfc/reference/cdaorecordset-class.md#open)， `AddNew`，**更新**，和**删除**到任何与此相关的记录集调用`CDaoDatabase`对象。 在打开后更改记录集的查询超时值不会更改为记录集的值。 例如，后续[移动](../../mfc/reference/cdaorecordset-class.md#move)操作不使用新值。  
  
 查询超时的默认值为 60 秒。 并非所有数据库都支持的功能，以设置查询超时值。 如果设置为 0 的查询超时值时，会发生无超时;与数据库通信可能会停止响应。 在开发过程中，此行为可能很有用。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"QueryTimeout 属性"。  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoWorkspace 类](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)   
 [CDatabase 类](../../mfc/reference/cdatabase-class.md)   
 [CDaoException 类](../../mfc/reference/cdaoexception-class.md)

