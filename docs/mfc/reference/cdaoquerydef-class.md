---
title: "CDaoQueryDef 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cbade1dc41b0e195606b10598e92f86195662bba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|构造**CDaoQueryDef**对象。 接下来调用**打开**或**创建**，取决于你的需求。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoQueryDef::Append](#append)|将此 querydef 追加到为已保存查询的数据库的 QueryDefs 集合。|  
|[CDaoQueryDef::CanUpdate](#canupdate)|返回非零，如果查询可以更新数据库。|  
|[CDaoQueryDef::Close](#close)|关闭 querydef 对象。 使用它完成后销毁 c + + 对象。|  
|[CDaoQueryDef::Create](#create)|创建基础的 DAO querydef 对象。 将用作临时查询或调用 querydef**追加**将其保存在数据库中。|  
|[CDaoQueryDef::Execute](#execute)|执行由 querydef 对象定义的查询。|  
|[CDaoQueryDef::GetConnect](#getconnect)|返回与此 querydef 关联的连接字符串。 连接字符串标识的数据源。 （有关 SQL 传递查询; 否则为空字符串。）|  
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|返回的已保存的查询的创建的日期。|  
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|返回上次更新的已保存的查询的日期。|  
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|返回由 querydef 定义字段的数目。|  
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|返回有关指定查询中定义的字段信息。|  
|[CDaoQueryDef::GetName](#getname)|返回此 querydef 的名称。|  
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|返回使用 ODBC （对于 ODBC 查询） 的超时值执行 querydef 时。 这将确定多长时间以允许查询的操作的完成。|  
|[CDaoQueryDef::GetParameterCount](#getparametercount)|返回为查询定义的参数的数目。|  
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|对查询返回有关指定参数的信息。|  
|[CDaoQueryDef::GetParamValue](#getparamvalue)|向查询中返回指定的参数的值。|  
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|返回由操作查询受影响的记录数。|  
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|返回非零，如果 querydef 所定义的查询返回的记录。|  
|[CDaoQueryDef::GetSQL](#getsql)|返回指定 querydef 所定义的查询的 SQL 字符串。|  
|[CDaoQueryDef::GetType](#gettype)|返回的查询类型： 删除、 更新、 追加、 生成表等等。|  
|[CDaoQueryDef::IsOpen](#isopen)|如果此 querydef 处于打开状态，并可执行，则返回非零值。|  
|[CDaoQueryDef::Open](#open)|打开现有 querydef 存储在数据库的 QueryDefs 集合中。|  
|[CDaoQueryDef::SetConnect](#setconnect)|在 ODBC 数据源上设置 SQL 传递查询的连接字符串。|  
|[CDaoQueryDef::SetName](#setname)|设置已保存的查询，并且替换中使用的名称，创建此 querydef 时的名称。|  
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|设置查询可使用由 ODBC （ODBC） 的超时值执行 querydef 时。|  
|[CDaoQueryDef::SetParamValue](#setparamvalue)|将指定的参数的值设置为查询。|  
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|指定此 querydef 是否返回的记录。 此属性设置为**TRUE**才有效的 SQL 传递查询。|  
|[CDaoQueryDef::SetSQL](#setsql)|设置指定 querydef 所定义的查询的 SQL 字符串。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|指向基础 DAO querydef 对象的 OLE 接口的指针。|  
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|指向的指针`CDaoDatabase`querydef 与之关联的对象。 可以将此 querydef 保存在数据库中，或不。|  
  
## <a name="remarks"></a>备注  
 Querydef 是一个包含描述一个查询，以及其属性，如"创建日期"和"ODBC 超时。"的 SQL 语句的数据访问对象 你还可以通过以下方式创建临时 querydef 对象而不进行保存，但会很方便-和高效得多-保存常用重复使用在数据库中的查询。 A [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象维护一个名为 QueryDefs 集合，包含其已保存的 querydefs 的集合。  
  
> [!NOTE]
>  DAO 数据库类有别于基于开放式数据库连接 (ODBC) 的 MFC 数据库类。 DAO 数据库类的所有名称都具有"CDao"前缀。 你仍可以访问 ODBC 数据源对于 DAO 类。 通常情况下，基于 DAO 的 MFC 类是更强于基于 ODBC; 的 MFC 类基于 DAO 的类可以访问数据，包括通过 ODBC 驱动程序，通过其自己的数据库引擎。 基于 DAO 的类还支持数据定义语言 (DDL) 操作，如添加表通过类，而无需直接调用 DAO。  
  
## <a name="usage"></a>用法  
 使用 querydef 对象这两个要使用现有的已保存查询，或创建新保存查询或临时查询：  
  
1.  在所有情况下，首先构造`CDaoQueryDef`对象，提供一个指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)查询所属对象。  
  
2.  然后执行以下操作，具体取决于希望：  
  
    -   若要使用现有的已保存查询，调用 querydef 对象[打开](#open)成员函数，提供已保存查询的名称。  
  
    -   若要创建新的已保存的查询时，调用 querydef 对象[创建](#create)成员函数，提供查询的名称。 然后调用[追加](#append)以将其追加到数据库的 QueryDefs 集合以保存查询。 **创建**将 querydef 放入打开状态，因此在调用**创建**不调用**打开**。  
  
    -   若要创建临时 querydef，调用**创建**。 传递的查询名称为空字符串。 不要调用**追加**。  
  
 当你完成使用 querydef 对象时，调用其[关闭](#close)成员函数; 然后销毁 querydef 对象。  
  
> [!TIP]
>  创建保存的查询的最简单方法是创建它们，并将其存储在使用 Microsoft Access 数据库。 然后可以打开，并在 MFC 代码中使用它们。  
  
## <a name="purposes"></a>目的  
 对于任何以下目的，可以使用 querydef 对象：  
  
-   若要创建`CDaoRecordset`对象  
  
-   若要调用对象的**执行**要直接执行操作查询或 SQL 传递查询的成员函数  
  
 你可以 querydef 对象用于任何类型的查询，其中包括 select、 操作、 交叉表、 删除、 更新、 追加、 生成表、 数据定义、 SQL 传递、 联合和大容量查询。 查询的类型是由你提供的 SQL 语句的内容确定的。 有关查询类型的信息，请参阅**执行**和[GetType](#gettype)成员函数。 记录集通常用于返回行的查询，通常使用的那些**选择...从**关键字。 **执行**最常用于大容量操作。 有关详细信息，请参阅[执行](#execute)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
## <a name="querydefs-and-recordsets"></a>Querydefs 和记录集  
 若要使用 querydef 对象创建`CDaoRecordset`对象，通常创建或打开 querydef 上文所述。 然后构造一个记录集对象，将指针传递给 querydef 对象中，当您调用[cdaorecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)。 你传递 querydef 必须处于打开状态。 有关详细信息，请参阅类[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 Querydef 不能用于创建记录集 （querydef 的最常见用途），除非它是处于打开状态。 将此 querydef 放入打开状态，通过调用**打开**或**创建**。  
  
## <a name="external-databases"></a>外部数据库  
 Querydef 对象是使用外部数据库引擎的本机 SQL 方言的首选的方法。 例如，可以创建 Transact SQL 查询 （如 Microsoft SQL Server 上使用），并将其存储在 querydef 对象。 当你需要使用不基于 Microsoft Jet 数据库引擎的 SQL 查询时，你必须提供指向外部数据源的连接字符串。 使用有效的连接字符串的查询绕过数据库引擎和查询将直接传递到外部数据库服务器处理。  
  
> [!TIP]
>  使用 ODBC 表的首选的方式是将它们附加到 Microsoft Jet (。MDB) 数据库。  
  
 有关相关信息，请参阅"QueryDef 对象"、"QueryDefs 集合"和"CdbDatabase 对象"DAO SDK 中的主题。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoQueryDef`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxdao.h  
  
##  <a name="append"></a>CDaoQueryDef::Append  
 调用此成员函数调用之后[创建](#create)以创建新的 querydef 对象。  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>备注  
 **追加**将 querydef 保存在数据库中，通过将对象追加到数据库的 QueryDefs 集合。 可以使用此 querydef 作为临时对象不会将附加它，但如果你希望保留，则必须调用**追加**。  
  
 如果你尝试将临时 querydef 对象追加，则 MFC 会引发类型的异常[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
##  <a name="canupdate"></a>CDaoQueryDef::CanUpdate  
 调用此成员函数可确定是否可以修改此 querydef — 例如，更改其名称或 SQL 字符串。  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>返回值  
 如果你有权修改此 querydef; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 如果，则可以修改此 querydef:  
  
-   它不基于是以只读方式打开的数据库。  
  
-   必须更新数据库的访问权限。  
  
     这取决于是否已实现安全功能。 MFC 为安全性，则不提供的支持你必须实现它自己通过调用 DAO 直接或通过使用 Microsoft Access。 请参阅主题 DAO 帮助中的"权限属性"。  
  
##  <a name="cdaoquerydef"></a>CDaoQueryDef::CDaoQueryDef  
 构造**CDaoQueryDef**对象。  
  
```  
CDaoQueryDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>参数  
 `pDatabase`  
 向打开的指针[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。  
  
### <a name="remarks"></a>备注  
 对象可以表示存储在数据库的 QueryDefs 集合、 新的查询存储在集合中或临时的查询，无法存储现有 querydef。 下一步取决于 querydef 的类型：  
  
-   如果该对象表示现有 querydef，调用对象的[打开](#open)成员函数，对其进行初始化。  
  
-   如果该对象表示要保存新 querydef，调用对象的[创建](#create)成员函数。 这将对象添加到数据库的 QueryDefs 集合。 然后调用`CDaoQueryDef`成员函数来设置对象的属性。 最后，调用[追加](#append)。  
  
-   如果该对象表示临时 querydef （不保存到数据库中），调用**创建**，传递查询的名称为空字符串。 在调用**创建**，初始化此 querydef 通过直接设置属性。 不要调用**追加**。  
  
 若要设置此 querydef 的特性，可以使用[SetName](#setname)， [SetSQL](#setsql)，[为表示](#setconnect)， [SetODBCTimeout](#setodbctimeout)，和[SetReturnsRecords](#setreturnsrecords)成员函数。  
  
 当你完成与 querydef 对象时，调用其[关闭](#close)成员函数。 如果你有一个指针指向此 querydef，使用**删除**运算符要销毁的 c + + 对象。  
  
##  <a name="close"></a>CDaoQueryDef::Close  
 当你完成使用 querydef 对象时，请调用此成员函数。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 关闭此 querydef 释放基础的 DAO 对象但不会销毁已保存的 DAO querydef 对象或 c + +`CDaoQueryDef`对象。 这是不与相同[CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef)，DAO （如果不是临时 querydef） 中的数据库的 QueryDefs 集合中删除此 querydef。  
  
##  <a name="create"></a>CDaoQueryDef::Create  
 调用此成员函数来创建新的已保存的查询或新的临时查询。  
  
```  
virtual void Create(
    LPCTSTR lpszName = NULL,  
    LPCTSTR lpszSQL = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 保存到数据库中查询的唯一名称。 有关字符串的详细信息，请参阅主题 DAO 帮助中的"CreateQueryDef 方法"。 如果你接受默认值为空字符串，将创建临时 querydef。 此类查询不会保存 QueryDefs 集合中。  
  
 `lpszSQL`  
 定义查询的 SQL 字符串。 如果你接受默认值的**NULL**，更高版本，必须调用[SetSQL](#setsql)设置字符串。 到那时，查询是不确定。 但是，可以使用未定义的查询以打开记录集;有关详细信息，请参阅备注。 可以将此 querydef 追加到 QueryDefs 集合之前，必须定义 SQL 语句。  
  
### <a name="remarks"></a>备注  
 如果通过中的名称`lpszName`，然后，你可以调用[追加](#append)querydef 保存数据库的 QueryDefs 集合中。 否则为对象是临时 querydef，并且不会保存。 在任一情况下，此 querydef 处于打开状态，并且你可以使用它来创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象或调用此 querydef[执行](#execute)成员函数。  
  
 如果未提供中的 SQL 语句`lpszSQL`，无法运行查询中的使用**执行**但可以使用它来创建一个记录集。 在这种情况下，MFC 使用记录集的默认 SQL 语句。  
  
##  <a name="execute"></a>CDaoQueryDef::Execute  
 调用此成员函数以运行由 querydef 对象定义的查询。  
  
```  
virtual void Execute(int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>参数  
 `nOptions`  
 一个整数，确定特性的查询。 有关相关信息，请参阅主题 DAO 帮助中的"执行方法"。 你可以使用按位 OR 运算符 ( **&#124;**) 组合为此参数的以下常量：  
  
- **dbDenyWrite**拒绝其他用户写入权限。  
  
- **dbInconsistent**不一致的更新。  
  
- **dbConsistent**一致的更新。  
  
- **dbSQLPassThrough** SQL 传递。 导致要传递到 ODBC 数据库以进行处理的 SQL 语句。  
  
- **dbFailOnError**默认值。 回滚更新出错时和报表错误到用户。  
  
- **dbSeeChanges**生成运行时错误，如果另一个用户正在更改正在编辑的数据。  
  
> [!NOTE]
>  有关的术语的解释"不一致"和"一致，"请参阅主题 DAO 帮助中的"执行方法"。  
  
### <a name="remarks"></a>备注  
 用于执行这种方式的 Querydef 对象只能表示以下的查询类型之一：  
  
-   操作查询  
  
-   SQL 传递查询  
  
 **执行**并不适用于返回记录，如 select 查询的查询。 **执行**通常用于大容量操作查询，如**更新**，**插入**，或**SELECT INTO**，或数据定义语言 (DDL)操作。  
  
> [!TIP]
>  若要使用 ODBC 数据源的首选的方式是将表附加到 Microsoft Jet (。MDB) 数据库。 有关详细信息，请参阅主题"访问外部数据库与"帮助中的 DAO DAO。  
  
 调用[GetRecordsAffected](#getrecordsaffected)要确定受最新的记录数的 querydef 对象的成员函数**执行**调用。 例如，`GetRecordsAffected`返回有关删除、 更新或插入时执行的操作查询的记录数的信息。 返回的计数将不会反映级联更新或删除时的相关表中的更改中都起作用。  
  
 如果你同时包含这两者**dbInconsistent**和**dbConsistent**或者如果都不包含，则结果为默认情况下， **dbInconsistent**。  
  
 **执行**不返回一个记录集。 使用**执行**在选择记录的查询会导致引发异常的类型的 MFC [CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
##  <a name="getconnect"></a>CDaoQueryDef::GetConnect  
 调用此成员函数可获取与此 querydef 数据源关联的连接字符串。  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>返回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)包含 querydef 的连接字符串。  
  
### <a name="remarks"></a>备注  
 此函数仅用于 ODBC 数据源和某些 ISAM 驱动程序的限制。 它不用于 Microsoft Jet (。MDB) 数据库;在这种情况下，`GetConnect`返回空字符串。 有关详细信息，请参阅[为表示](#setconnect)。  
  
> [!TIP]
>  使用 ODBC 表的首选的方式是将附加到它们。MDB 数据库。 有关详细信息，请参阅主题"访问外部数据库与"帮助中的 DAO DAO。  
  
 有关连接字符串的信息，请参阅主题 DAO 帮助中的"连接属性"。  
  
##  <a name="getdatecreated"></a>CDaoQueryDef::GetDateCreated  
 调用此成员函数可获取 querydef 对象的创建的日期。  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>返回值  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含的日期和时间 querydef 已创建。  
  
### <a name="remarks"></a>备注  
 有关相关信息，请参阅 DAO 帮助中的主题"时间，上次更新属性"。  
  
##  <a name="getdatelastupdated"></a>CDaoQueryDef::GetDateLastUpdated  
 上次更新该成员函数以获取日期 querydef 对象的调用-任何其属性已更改时，例如其名称、 其 SQL 字符串或其连接字符串。  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>返回值  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含的日期和 querydef 上次更新的时间。  
  
### <a name="remarks"></a>备注  
 有关相关信息，请参阅 DAO 帮助中的主题"时间，上次更新属性"。  
  
##  <a name="getfieldcount"></a>CDaoQueryDef::GetFieldCount  
 调用此成员函数可检索的查询中的字段的数目。  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>返回值  
 查询中定义的字段数。  
  
### <a name="remarks"></a>备注  
 `GetFieldCount`可用于遍历 querydef 中的所有字段。 出于这个目的，使用`GetFieldCount`结合[GetFieldInfo](#getfieldinfo)。  
  
##  <a name="getfieldinfo"></a>CDaoQueryDef::GetFieldInfo  
 调用此成员函数以获取有关此 querydef 中定义的字段的信息的各种类型。  
  
```  
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
 `nIndex`  
 所需域 querydef 的字段集合，按索引查找中的从零开始的索引。  
  
 `fieldinfo`  
 对引用`CDaoFieldInfo`返回请求的信息的对象。  
  
 `dwInfoOptions`  
 指定有关要检索的字段的信息的选项。 以及它们会导致要返回的函数，下面列出了可用的选项：  
  
- `AFX_DAO_PRIMARY_INFO`（默认值）名称、 类型、 大小属性  
  
- `AFX_DAO_SECONDARY_INFO`主要信息加号： 要求的序号位置、 允许长度为零、 源字段、 外的名称、 源表、 排序规则顺序  
  
- `AFX_DAO_ALL_INFO`主要和次要信息加号： 默认值，验证文本验证规则  
  
 `lpszName`  
 包含按名称查找所需字段的名称的字符串。 你可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>备注  
 有关在中返回的信息的说明`fieldinfo`，请参阅[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 此结构具有对应于下的描述性信息的成员`dwInfoOptions`上面。 如果请求的信息的一个级别，你将获取任何之前级别的信息以及。  
  
##  <a name="getname"></a>CDaoQueryDef::GetName  
 调用此成员函数可检索此 querydef 所表示的查询的名称。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>返回值  
 查询的名称。  
  
### <a name="remarks"></a>备注  
 Querydef 名称是唯一的用户定义的名称。 有关 querydef 名称的详细信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
##  <a name="getodbctimeout"></a>CDaoQueryDef::GetODBCTimeout  
 调用此成员函数可对 ODBC 数据源的查询超时之前检索当前时间限制。  
  
```  
short GetODBCTimeout();
```  
  
### <a name="return-value"></a>返回值  
 超时之前查询等待的秒数。  
  
### <a name="remarks"></a>备注  
 有关此时间限制的信息，请参阅主题 DAO 帮助中的"odbc 超时属性"。  
  
> [!TIP]
>  使用 ODBC 表的首选的方式是将它们附加到 Microsoft Jet (。MDB) 数据库。 有关详细信息，请参阅主题"访问外部数据库与"帮助中的 DAO DAO。  
  
##  <a name="getparametercount"></a>CDaoQueryDef::GetParameterCount  
 调用此成员函数可检索已保存的查询中的参数数目。  
  
```  
short GetParameterCount();
```  
  
### <a name="return-value"></a>返回值  
 查询中定义的参数的数目。  
  
### <a name="remarks"></a>备注  
 `GetParameterCount`可用于循环访问此 querydef 中的所有参数。 出于这个目的，使用`GetParameterCount`结合[GetParameterInfo](#getparameterinfo)。  
  
 有关相关信息，请参阅"参数对象"、"参数集合"和"参数声明 (SQL)"DAO 帮助中的主题。  
  
##  <a name="getparameterinfo"></a>CDaoQueryDef::GetParameterInfo  
 调用此成员函数以获取有关此 querydef 中定义的参数的信息。  
  
```  
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
 `nIndex`  
 在此 querydef 参数集合中，按索引查找所需参数的从零开始的索引。  
  
 `paraminfo`  
 对引用[CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)返回请求的信息的对象。  
  
 `dwInfoOptions`  
 指定要检索的参数有关的信息的选项。 可用的选项以及它会导致要返回的函数在此处列出：  
  
- `AFX_DAO_PRIMARY_INFO`（默认值）名称、 类型  
  
 `lpszName`  
 包含按名称查找所需的参数的名称的字符串。 你可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>备注  
 有关在中返回的信息的说明`paraminfo`，请参阅[CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)结构。 此结构具有对应于下的描述性信息的成员`dwInfoOptions`上面。  
  
 有关相关信息，请参阅"参数声明 (SQL)"DAO 帮助中的主题。  
  
##  <a name="getparamvalue"></a>CDaoQueryDef::GetParamValue  
 调用此成员函数可检索存储 querydef 的参数集合中的指定参数的当前值。  
  
```  
virtual COleVariant GetParamValue(LPCTSTR lpszName);  
virtual COleVariant GetParamValue(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 参数要按名称查找对其值的名称。  
  
 `nIndex`  
 Querydef 的参数集合，按索引查找中参数的从零开始索引。 你可以获取此值通过调用[GetParameterCount](#getparametercount)和[GetParameterInfo](#getparameterinfo)。  
  
### <a name="return-value"></a>返回值  
 类的对象[COleVariant](../../mfc/reference/colevariant-class.md) ，其中包含参数的值。  
  
### <a name="remarks"></a>备注  
 按名称或集合中其序号位置，你可以访问参数。  
  
 有关相关信息，请参阅"参数声明 (SQL)"DAO 帮助中的主题。  
  
##  <a name="getrecordsaffected"></a>CDaoQueryDef::GetRecordsAffected  
 调用此成员函数可确定的最后一次调用影响了多少条记录[执行](#execute)。  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>返回值  
 受影响的记录数。  
  
### <a name="remarks"></a>备注  
 返回的计数将不会反映级联更新或删除时的相关表中的更改中都起作用。  
  
 有关相关信息请参阅主题 DAO 帮助中的"RecordsAffected 属性"。  
  
##  <a name="getreturnsrecords"></a>CDaoQueryDef::GetReturnsRecords  
 调用此成员函数可确定是否将 querydef 基于返回记录的查询。  
  
```  
BOOL GetReturnsRecords();
```  
  
### <a name="return-value"></a>返回值  
 如果此 querydef 基于查询的非零返回记录;否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数仅用于 SQL 传递查询。 有关 SQL 查询的详细信息，请参阅[执行](#execute)成员函数。 有关使用 SQL 传递查询的详细信息，请参阅[SetReturnsRecords](#setreturnsrecords)成员函数。  
  
 有关相关信息，请参阅主题"属性"DAO 帮助中。  
  
##  <a name="getsql"></a>CDaoQueryDef::GetSQL  
 调用此成员函数可检索定义 querydef 所基于的查询的 SQL 语句。  
  
```  
CString GetSQL();
```  
  
### <a name="return-value"></a>返回值  
 定义此 querydef 所基于的查询的 SQL 语句。  
  
### <a name="remarks"></a>备注  
 然后，你将可能分析关键字、 表名称和等等的字符串。  
  
 有关相关信息，请参阅"SQL Property"、"比较的 Microsoft Jet 数据库引擎 SQL 和 ANSI SQL"和"查询数据库与 SQL 中的代码"DAO 帮助中的主题。  
  
##  <a name="gettype"></a>CDaoQueryDef::GetType  
 调用此成员函数可确定 querydef 的查询类型。  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>返回值  
 通过此 querydef 定义的查询的类型。 值，请参阅备注。  
  
### <a name="remarks"></a>备注  
 查询类型将由你指定的内容 querydef 的 SQL 字符串中时创建此 querydef 或调用现有 querydef [SetSQL](#setsql)成员函数。 此函数返回的查询类型可以是下列值之一：  
  
- **dbQSelect**选择  
  
- **dbQAction**操作  
  
- **dbQCrosstab**交叉表  
  
- **dbQDelete**删除  
  
- **dbQUpdate**更新  
  
- **dbQAppend**追加  
  
- **dbQMakeTable**生成表  
  
- **dbQDDL**数据定义  
  
- **dbQSQLPassThrough**传递  
  
- **dbQSetOperation**联合  
  
- **dbQSPTBulk**用于**dbQSQLPassThrough**若要指定不返回记录的查询。  
  
> [!NOTE]
>  若要创建 SQL 传递查询，未设置**dbSQLPassThrough**常量。 这将自动设置通过 Microsoft Jet 数据库引擎创建 querydef 对象和设置连接字符串时。  
  
 有关 SQL 字符串的信息，请参阅[GetSQL](#getsql)。 有关查询类型的信息，请参阅[执行](#execute)。  
  
##  <a name="isopen"></a>CDaoQueryDef::IsOpen  
 调用此成员函数可确定是否`CDaoQueryDef`对象当前处于打开状态。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零如果`CDaoQueryDef`对象是当前打开; 否则为 0。  
  
### <a name="remarks"></a>备注  
 Querydef 处于打开状态之前必须使用它来调用[执行](#execute)或创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象。 若要或者使 querydef 处于打开状态调用[创建](#create)（适用于新 querydef) 或[打开](#open)（适用于现有 querydef)。  
  
##  <a name="m_pdatabase"></a>CDaoQueryDef::m_pDatabase  
 包含指向的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)与 querydef 对象相关联的对象。  
  
### <a name="remarks"></a>备注  
 如果你需要直接访问数据库，请使用此指针 — 例如，若要获取指向其他 querydef 或记录集对象的数据库集合中。  
  
##  <a name="m_pdaoquerydef"></a>CDaoQueryDef::m_pDAOQueryDef  
 包含基础 DAO querydef 对象的 OLE 接口的指针。  
  
### <a name="remarks"></a>备注  
 此指针提供完整性和与其他类的一致性。 但是，因为 MFC 而是完全封装 DAO querydefs，你不可能需要它。 如果你使用它，这样慎重-除非你知道你正在特别是，不要更改指针的值。  
  
##  <a name="open"></a>CDaoQueryDef::Open  
 调用此成员函数以打开 querydef 以前保存的数据库的 QueryDefs 集合中。  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 包含已保存的 querydef，若要打开的名称的字符串。 你可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>备注  
 打开此 querydef 后，你可以调用其[执行](#execute)成员函数或使用 querydef 创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象。  
  
##  <a name="setconnect"></a>CDaoQueryDef::SetConnect  
 调用此成员函数以设置 querydef 对象的连接字符串。  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>参数  
 `lpszConnect`  
 包含关联的连接字符串的字符串[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。  
  
### <a name="remarks"></a>备注  
 连接字符串用于将其他信息传递到 ODBC 和根据需要某些 ISAM 驱动程序。 它不用于 Microsoft Jet (。MDB) 数据库。  
  
> [!TIP]
>  使用 ODBC 表的首选的方式是将附加到它们。MDB 数据库。  
  
 在执行之前 querydef 到 ODBC 数据源表示 SQL 传递查询，设置的连接字符串具有`SetConnect`并调用[SetReturnsRecords](#setreturnsrecords)来指定查询是否返回的记录。  
  
 有关连接字符串的结构和连接字符串组件的示例的详细信息，请参阅主题 DAO 帮助中的"连接属性"。  
  
##  <a name="setname"></a>CDaoQueryDef::SetName  
 如果你想要更改 querydef 不是临时的名称，请调用此成员函数。  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 包含一个非临时性查询中关联的新名称的字符串[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。  
  
### <a name="remarks"></a>备注  
 Querydef 名称是唯一的、 用户定义的名称。 你可以调用`SetName`之前 querydef 对象追加到 QueryDefs 集合。  
  
##  <a name="setodbctimeout"></a>CDaoQueryDef::SetODBCTimeout  
 调用此成员函数以设置对 ODBC 数据源的查询超时之前的时间限制。  
  
```  
void SetODBCTimeout(short nODBCTimeout);
```  
  
### <a name="parameters"></a>参数  
 *nODBCTimeout*  
 超时之前查询等待的秒数。  
  
### <a name="remarks"></a>备注  
 此成员函数，可以替代默认数秒，然后在已连接的数据源"超时。"上的后续操作 由于网络访问权限问题、 过多的查询处理时间等的操作可能会超时。 调用`SetODBCTimeout`之前执行具有此 querydef 的查询，如果你想要更改的查询超时值。 （如 ODBC 重用连接，超时值是相同的同一个连接上的所有客户端。）  
  
 查询超时的默认值为 60 秒。  
  
##  <a name="setparamvalue"></a>CDaoQueryDef::SetParamValue  
 调用此成员函数以在运行时在 querydef 中设置参数的值。  
  
```  
virtual void SetParamValue(
    LPCTSTR lpszName,  
    const COleVariant& varValue);

 
virtual void SetParamValue(
    int nIndex,  
    const COleVariant& varValue);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 参数要设置其值的名称。  
  
 `varValue`  
 要设置; 的值请参阅备注。  
  
 `nIndex`  
 Querydef 的参数集合中参数的序号位置。 你可以获取此值通过调用[GetParameterCount](#getparametercount)和[GetParameterInfo](#getparameterinfo)。  
  
### <a name="remarks"></a>备注  
 参数必须已建立作为 querydef 的 SQL 字符串的一部分。 按名称或集合中其序号位置，你可以访问参数。  
  
 指定的值将设置为`COleVariant`对象。 有关设置的所需的值和中的类型信息你`COleVariant`对象，请参阅类[COleVariant](../../mfc/reference/colevariant-class.md)。  
  
##  <a name="setreturnsrecords"></a>CDaoQueryDef::SetReturnsRecords  
 调用此成员函数设置到外部数据库的 SQL 传递查询的过程的一部分。  
  
```  
void SetReturnsRecords(BOOL bReturnsRecords);
```  
  
### <a name="parameters"></a>参数  
 *bReturnsRecords*  
 传递**TRUE**如果外部数据库中的查询返回的记录; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 在这种情况下，你必须创建此 querydef 并设置其属性使用其他`CDaoQueryDef`成员函数。 外部数据库的说明，请参阅[为表示](#setconnect)。  
  
##  <a name="setsql"></a>CDaoQueryDef::SetSQL  
 调用此成员函数可设置 querydef 执行的 SQL 语句。  
  
```  
void SetSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>参数  
 `lpszSQL`  
 包含一个完整的 SQL 语句，适用于执行的字符串。 此字符串的语法取决于 DBMS 的查询目标。 有关在 Microsoft Jet 数据库引擎中使用的语法的讨论，请参阅"生成 SQL 语句中的代码"DAO 帮助中的主题。  
  
### <a name="remarks"></a>备注  
 一个典型用途`SetSQL`是设置使用在 SQL 查询中传递的 querydef 对象。 （有关目标 DBMS SQL 传递查询的语法，请参阅所使用的 DBMS 的文档）。  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoException 类](../../mfc/reference/cdaoexception-class.md)
