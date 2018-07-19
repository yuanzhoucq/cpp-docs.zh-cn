---
title: CDaoQueryDef 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 24aeac6c19a481f3be8d6555862c9631cb1672b1
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339437"
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
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|构造 `CDaoQueryDef` 对象。 接下来调用`Open`或`Create`，取决于你的需求。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoQueryDef::Append](#append)|将此 querydef 追加到数据库的 QueryDefs 集合作为保存的查询。|  
|[CDaoQueryDef::CanUpdate](#canupdate)|返回非零，如果查询可以更新数据库。|  
|[CDaoQueryDef::Close](#close)|关闭 querydef 对象。 使用它完成后销毁 c + + 对象。|  
|[CDaoQueryDef::Create](#create)|创建基础的 DAO querydef 对象。 将用作临时查询或调用 querydef`Append`将其保存在数据库中。|  
|[CDaoQueryDef::Execute](#execute)|执行由 querydef 对象定义的查询。|  
|[CDaoQueryDef::GetConnect](#getconnect)|返回与此 querydef 关联的连接字符串。 连接字符串标识数据源。 （有关 SQL 传递查询; 否则为空字符串。）|  
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|返回已保存的查询的创建的日期。|  
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|返回上次更新的已保存的查询的日期。|  
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|返回由 querydef 定义字段数。|  
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|返回有关在查询中定义的指定字段的信息。|  
|[CDaoQueryDef::GetName](#getname)|返回此 querydef 的名称。|  
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|返回使用 ODBC （适用于 ODBC 查询） 的超时值执行 querydef 时。 这将确定多长时间以允许查询的操作的完成。|  
|[CDaoQueryDef::GetParameterCount](#getparametercount)|返回为该查询定义的参数数目。|  
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|对查询返回有关指定参数的信息。|  
|[CDaoQueryDef::GetParamValue](#getparamvalue)|向查询中返回指定参数的值。|  
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|返回受影响的操作查询的记录数。|  
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|返回非零，如果 querydef 所定义的查询返回的记录。|  
|[CDaoQueryDef::GetSQL](#getsql)|返回指定 querydef 所定义的查询的 SQL 字符串。|  
|[CDaoQueryDef::GetType](#gettype)|返回的查询类型： 删除、 更新、 追加，生成表和其他操作。|  
|[CDaoQueryDef::IsOpen](#isopen)|如果 querydef 处于打开状态，并且可以执行，则返回非零值。|  
|[CDaoQueryDef::Open](#open)|打开存储在数据库的 QueryDefs 集合中现有 querydef。|  
|[CDaoQueryDef::SetConnect](#setconnect)|在 ODBC 数据源上设置 SQL 传递查询的连接字符串。|  
|[CDaoQueryDef::SetName](#setname)|设置已保存的查询，创建 querydef 时替换中使用的名称的名称。|  
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|设置超时值 （适用于 ODBC 查询） 使用 ODBC 执行 querydef 时。|  
|[CDaoQueryDef::SetParamValue](#setparamvalue)|将指定参数的值设置为该查询。|  
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|指定是否 querydef 返回的记录。 将此属性设置为 TRUE 时才有效 SQL 传递查询。|  
|[CDaoQueryDef::SetSQL](#setsql)|设置指定 querydef 所定义的查询的 SQL 字符串。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|指向基础 DAO querydef 对象的 OLE 接口的指针。|  
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|一个指向`CDaoDatabase`querydef 与之关联的对象。 Querydef 可能保存在数据库中，或不。|  
  
## <a name="remarks"></a>备注  
 Querydef 是包含介绍查询和其属性，如"创建日期"和"ODBC 超时。"的 SQL 语句的数据访问对象 此外可以创建临时 querydef 对象，而不进行保存，但会很方便 — 和高效得多 — 保存常用重复使用数据库中的查询。 一个[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象维护一个名为 QueryDefs 集合，包含其已保存的 querydefs 集合。  
  
> [!NOTE]
>  DAO 数据库类是不同于基于开放式数据库连接 (ODBC) 的 MFC 数据库类。 所有 DAO 数据库类名称都具有"CDao"前缀。 您仍然可以访问 ODBC 数据源对于 DAO 类。 一般情况下，基于 DAO 的 MFC 类是更强于基于 ODBC; 的 MFC 类基于 DAO 的类可以访问数据，包括通过 ODBC 驱动程序，通过其自己的数据库引擎。 基于 DAO 的类还支持数据定义语言 (DDL) 操作，例如添加表通过类，而无需直接调用 DAO。  
  
## <a name="usage"></a>用法  
 使用 querydef 对象或者能够使用现有的已保存查询，或创建新保存的查询或临时查询：  
  
1.  在所有情况下，首先构建`CDaoQueryDef`对象，提供指向的指针[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)为查询所属对象。  
  
2.  然后执行以下操作，具体取决于所需操作：  
  
    -   若要使用现有的已保存查询，调用 querydef 对象的[打开](#open)成员函数，提供的已保存的查询的名称。  
  
    -   若要创建一个新的已保存的查询，请调用 querydef 对象[创建](#create)成员函数，提供的查询的名称。 然后调用[追加](#append)以将它追加到数据库的 QueryDefs 集合保存查询。 `Create` 将此 querydef 放到打开状态，因此在调用`Create`不调用`Open`。  
  
    -   若要创建临时 querydef，调用`Create`。 传递的查询名称为空字符串。 不要调用 `Append`。  
  
 完成使用 querydef 对象后，调用其[关闭](#close)成员函数; 然后销毁 querydef 对象。  
  
> [!TIP]
>  若要创建已保存的查询的最简单方法是创建它们，并将其存储在使用 Microsoft Access 数据库中。 然后可以打开并在 MFC 代码中使用它们。  
  
## <a name="purposes"></a>目的  
 您可以将 querydef 对象用于任何实现以下目的：  
  
-   若要创建`CDaoRecordset`对象  
  
-   若要调用对象的`Execute`成员函数来直接执行动作查询或 SQL 传递查询  
  
 可以使用任何类型的查询，包括 select、 操作、 交叉表、 删除、 更新 querydef 对象、 追加，生成表、 数据定义、 SQL 直通、 union、 和大容量查询。 你提供的 SQL 语句的内容确定查询的类型。 有关查询类型的信息，请参阅`Execute`并[GetType](#gettype)成员函数。 记录集通常用于返回行的查询时，通常使用**选择...从**关键字。 `Execute` 通常用于大容量操作。 有关详细信息，请参阅[Execute](#execute)并[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
## <a name="querydefs-and-recordsets"></a>Querydefs 和记录集  
 若要使用 querydef 对象来创建`CDaoRecordset`对象，通常创建或打开 querydef 上文所述。 然后，构建记录集对象，在调用时，将指针传递给 querydef 对象[cdaorecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)。 传递的 querydef 必须处于打开状态。 有关详细信息，请参阅类[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 Querydef 不能用于创建记录集 （querydef 的最常见用途），除非它是处于打开状态。 将此 querydef 放入打开状态，通过调用`Open`或`Create`。  
  
## <a name="external-databases"></a>外部数据库  
 Querydef 对象是使用外部数据库引擎的本机 SQL 方言的首选的方法。 例如，可以创建 Transact SQL 查询 （如 Microsoft SQL Server 上使用），并将其存储在 querydef 对象。 当您需要使用不基于 Microsoft Jet 数据库引擎的 SQL 查询时，必须提供指向外部数据源的连接字符串。 具有有效的连接字符串的查询跳过数据库引擎，该查询将直接传递到外部数据库服务器处理。  
  
> [!TIP]
>  若要使用的 ODBC 表的首选的方法是将它们附加到 Microsoft Jet (。MDB) 数据库。  
  
 有关相关信息，请参阅"QueryDef 对象"、"QueryDefs 集合"和"CdbDatabase 对象"DAO SDK 中的主题。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoQueryDef`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdao.h  
  
##  <a name="append"></a>  CDaoQueryDef::Append  
 调用后调用此成员函数[创建](#create)以创建新的 querydef 对象。  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>备注  
 `Append` 通过将对象附加到数据库的 QueryDefs 集合数据库中保存 querydef。 可以使用此 querydef 作为临时对象不会将附加它，但如果您希望其持久保存，则必须调用`Append`。  
  
 如果您尝试追加临时 querydef 对象，则 MFC 会引发类型的异常[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
##  <a name="canupdate"></a>  CDaoQueryDef::CanUpdate  
 调用此成员函数以确定是否可以修改此 querydef — 例如，更改其名称或 SQL 字符串。  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>返回值  
 如果你有权修改 querydef; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果可以修改此 querydef:  
  
-   它不基于只读方式打开的数据库。  
  
-   具有更新权限的数据库。  
  
     这取决于是否已实现的安全功能。 MFC 不提供安全; 支持您必须实现它自己通过调用 DAO 直接或通过使用 Microsoft Access。 请参阅主题 DAO 帮助中的"权限属性"。  
  
##  <a name="cdaoquerydef"></a>  CDaoQueryDef::CDaoQueryDef  
 构造 `CDaoQueryDef` 对象。  
  
```  
CDaoQueryDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>参数  
 *pDatabase*  
 向打开的指针[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。  
  
### <a name="remarks"></a>备注  
 该对象可以表示存储在数据库的 QueryDefs 集合、 要存储在集合中的新查询或临时查询，无法存储现有 querydef。 下一步取决于 querydef 的类型：  
  
-   如果该对象表示现有 querydef，调用对象的[打开](#open)成员函数对其进行初始化。  
  
-   如果该对象表示要保存新 querydef，调用对象的[创建](#create)成员函数。 这将对象添加到数据库的 QueryDefs 集合。 然后，调用`CDaoQueryDef`成员函数来设置对象的属性。 最后，调用[追加](#append)。  
  
-   如果该对象表示临时 querydef （不保存到数据库中），则调用`Create`，传递空字符串作为查询的名称。 在调用`Create`，通过直接设置其属性初始化 querydef。 不要调用 `Append`。  
  
 若要设置的 querydef 属性，可以使用[SetName](#setname)， [SetSQL](#setsql)，[为表示](#setconnect)， [SetODBCTimeout](#setodbctimeout)，和[SetReturnsRecords](#setreturnsrecords)成员函数。  
  
 完成与 querydef 对象后，调用其[关闭](#close)成员函数。 如果您有一个指针指向 querydef，使用**删除**运算符要销毁的 c + + 对象。  
  
##  <a name="close"></a>  CDaoQueryDef::Close  
 当你完成使用 querydef 对象时调用此成员函数。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 关闭 querydef 释放基础的 DAO 对象，但不会销毁已保存的 DAO querydef 对象或 c + +`CDaoQueryDef`对象。 这是不与相同[CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef)，其中删除 querydef DAO （如果不是临时 querydef） 中的数据库的 QueryDefs 集合中。  
  
##  <a name="create"></a>  CDaoQueryDef::Create  
 调用此成员函数以创建新保存的查询或新的临时查询。  
  
```  
virtual void Create(
    LPCTSTR lpszName = NULL,  
    LPCTSTR lpszSQL = NULL);
```  
  
### <a name="parameters"></a>参数  
 *lpszName*  
 保存到数据库中查询的唯一名称。 有关字符串的详细信息，请参阅主题 DAO 帮助中的"CreateQueryDef 方法"。 如果你接受默认值为空字符串，将创建临时 querydef。 此类查询不会保存 QueryDefs 集合中。  
  
 *lpszSQL*  
 定义查询的 SQL 字符串。 如果你接受默认值为 NULL，则必须更高版本调用[SetSQL](#setsql)设置字符串。 在此之前，该查询是未定义。 但是，可以使用未定义的查询打开记录集;有关详细信息，请参阅备注。 可以将此 querydef 追加到 QueryDefs 集合之前，必须定义 SQL 语句。  
  
### <a name="remarks"></a>备注  
 如果通过中的名称*lpszName*，然后，可以调用[追加](#append)querydef 保存数据库的 QueryDefs 集合中。 否则为该对象是临时 querydef 的不保存。 在任一情况下，此 querydef 是处于打开状态，以及您也可以使用它来创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象或调用 querydef [Execute](#execute)成员函数。  
  
 如果不提供中的 SQL 语句*lpszSQL*，不能运行在查询中的使用`Execute`但可以使用它来创建记录集。 在这种情况下，MFC 使用记录集的默认的 SQL 语句。  
  
##  <a name="execute"></a>  CDaoQueryDef::Execute  
 调用此成员函数以运行 querydef 对象所定义的查询。  
  
```  
virtual void Execute(int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>参数  
 *nOptions*  
 一个整数，用于确定查询的特征。 有关相关信息，请参阅主题 DAO 帮助中的"执行方法"。 可以使用按位 OR 运算符 ( **&#124;**) 组合为此参数的以下常量：  
  
- `dbDenyWrite` 向其他用户拒绝写入权限。  
  
- `dbInconsistent` 不一致的更新。  
  
- `dbConsistent` 一致的更新。  
  
- `dbSQLPassThrough` SQL 传递。 导致要传递到 ODBC 数据库以进行处理的 SQL 语句。  
  
- `dbFailOnError` 默认值。 回滚更新如果发生错误和错误报告给用户。  
  
- `dbSeeChanges` 如果另一个用户正在更改正在编辑的数据，则生成运行时错误。  
  
> [!NOTE]
>  有关这些术语的说明"不一致"和"一致，"请参阅主题 DAO 帮助中的"执行方法"。  
  
### <a name="remarks"></a>备注  
 在这种方式中执行所用的 Querydef 对象只能表示下列查询类型之一：  
  
-   操作查询  
  
-   SQL 传递查询  
  
 `Execute` 不适用于返回记录，如 select 查询的查询。 `Execute` 通常用于进行大容量操作的查询，如**更新**，**插入**，或**SELECT INTO**，或数据定义语言 (DDL) 操作。  
  
> [!TIP]
>  若要使用 ODBC 数据源的首选的方法是将表附加到 Microsoft Jet (。MDB) 数据库。 有关详细信息，请参阅主题"访问外部数据库中的用 DAO"DAO 帮助。  
  
 调用[GetRecordsAffected](#getrecordsaffected) querydef 对象确定影响的最新的记录数的成员函数`Execute`调用。 例如，`GetRecordsAffected`返回有关已删除、 更新或插入时执行操作查询的记录数的信息。 返回的计数将不会反映在级联更新或删除时的相关表中的更改都生效。  
  
 如果同时包含`dbInconsistent`并`dbConsistent`或者如果都不包含，则结果为默认情况下， `dbInconsistent`。  
  
 `Execute` 不会返回一个记录集。 使用`Execute`上选择记录的查询会导致引发异常的类型的 MFC [CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
##  <a name="getconnect"></a>  CDaoQueryDef::GetConnect  
 调用此成员函数以获取与 querydef 的数据源相关联的连接字符串。  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)包含 querydef 的连接字符串。  
  
### <a name="remarks"></a>备注  
 此函数只能用于 ODBC 数据源和某些 ISAM 驱动程序。 不用于 Microsoft Jet (。MDB) 的数据库。在这种情况下，`GetConnect`返回空字符串。 有关详细信息，请参阅[为表示](#setconnect)。  
  
> [!TIP]
>  若要使用的 ODBC 表的首选的方法是将它们连接到。MDB 的数据库。 有关详细信息，请参阅主题"访问外部数据库中的用 DAO"DAO 帮助。  
  
 有关连接字符串的信息，请参阅主题 DAO 帮助中的"连接属性"。  
  
##  <a name="getdatecreated"></a>  CDaoQueryDef::GetDateCreated  
 调用此成员函数可获取 querydef 对象的创建的日期。  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>返回值  
 一个[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含的日期和 querydef 的创建的时间。  
  
### <a name="remarks"></a>备注  
 相关信息，请参阅 DAO 帮助中的主题"DateCreated，上次更新属性"。  
  
##  <a name="getdatelastupdated"></a>  CDaoQueryDef::GetDateLastUpdated  
 上次更新此成员函数来获取日期 querydef 对象的调用，当其任何属性发生更改，如其名称、 其 SQL 字符串或其连接字符串。  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>返回值  
 一个[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含的日期和 querydef 上次更新的时间。  
  
### <a name="remarks"></a>备注  
 相关信息，请参阅 DAO 帮助中的主题"DateCreated，上次更新属性"。  
  
##  <a name="getfieldcount"></a>  CDaoQueryDef::GetFieldCount  
 调用此成员函数以检索查询中的字段数。  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>返回值  
 在查询中定义的字段数。  
  
### <a name="remarks"></a>备注  
 `GetFieldCount` 可用于循环遍历 querydef 中的所有字段。 为此，使用`GetFieldCount`结合[GetFieldInfo](#getfieldinfo)。  
  
##  <a name="getfieldinfo"></a>  CDaoQueryDef::GetFieldInfo  
 调用此成员函数以获取各种类型的有关 querydef 中定义的字段的信息。  
  
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
 *nIndex*  
 Querydef 的字段集合，用于查找索引中将所需字段的从零开始的索引。  
  
 *fieldinfo*  
 对引用`CDaoFieldInfo`对象，它返回请求的信息。  
  
 *dwInfoOptions*  
 指定有关要检索的字段的信息的选项。 可用选项以及它们会导致函数返回此处列出：  
  
- AFX_DAO_PRIMARY_INFO （默认值） 名称、 类型、 大小、 属性  
  
- AFX_DAO_SECONDARY_INFO 主要信息加上： 要求的序号位置、 允许长度为零、 源字段、 外名称、 源表、 排序规则顺序  
  
- AFX_DAO_ALL_INFO 主要和辅助数据库信息加上： 默认值，验证文本验证规则  
  
 *lpszName*  
 包含按名称查找将所需字段的名称的字符串。 可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>备注  
 有关中返回的信息的说明*fieldinfo*，请参阅[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 此结构具有对应的描述性信息下的成员*dwInfoOptions*上面。 如果请求一个级别的信息，您将获取信息以及任何前的级别。  
  
##  <a name="getname"></a>  CDaoQueryDef::GetName  
 调用此成员函数以检索 querydef 所表示的查询的名称。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>返回值  
 查询的名称。  
  
### <a name="remarks"></a>备注  
 Querydef 名称是用户定义的唯一名称。 有关 querydef 名称的详细信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
##  <a name="getodbctimeout"></a>  CDaoQueryDef::GetODBCTimeout  
 调用此成员函数以检索 ODBC 数据源的查询超时之前的当前时间限制。  
  
```  
short GetODBCTimeout();
```  
  
### <a name="return-value"></a>返回值  
 超时之前查询等待的秒数。  
  
### <a name="remarks"></a>备注  
 有关此时间限制的信息，请参阅主题 DAO 帮助中的"odbc 超时属性"。  
  
> [!TIP]
>  若要使用的 ODBC 表的首选的方法是将它们附加到 Microsoft Jet (。MDB) 数据库。 有关详细信息，请参阅主题"访问外部数据库中的用 DAO"DAO 帮助。  
  
##  <a name="getparametercount"></a>  CDaoQueryDef::GetParameterCount  
 调用此成员函数以检索已保存的查询中的参数数量。  
  
```  
short GetParameterCount();
```  
  
### <a name="return-value"></a>返回值  
 在查询中定义的参数数目。  
  
### <a name="remarks"></a>备注  
 `GetParameterCount` 可用于循环访问 querydef 中的所有参数。 为此，使用`GetParameterCount`结合[GetParameterInfo](#getparameterinfo)。  
  
 有关相关信息，请参阅"参数对象"、"参数集合"和"参数声明 (SQL)"DAO 帮助中的主题。  
  
##  <a name="getparameterinfo"></a>  CDaoQueryDef::GetParameterInfo  
 调用此成员函数以获取有关 querydef 中定义的参数的信息。  
  
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
 *nIndex*  
 按索引进行查找的 querydef 的参数集合中的所需参数的从零开始的索引。  
  
 *paraminfo*  
 对引用[CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)对象，它返回请求的信息。  
  
 *dwInfoOptions*  
 指定要检索的参数有关的信息的选项。 以及它会导致要返回的函数，此处列出了可用的选项：  
  
- AFX_DAO_PRIMARY_INFO （默认值） 的名称、 类型  
  
 *lpszName*  
 包含按名称查找所需参数的名称的字符串。 可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>备注  
 有关中返回的信息的说明*paraminfo*，请参阅[CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)结构。 此结构具有对应的描述性信息下的成员*dwInfoOptions*上面。  
  
 有关相关信息，请参阅"参数声明 (SQL)"DAO 帮助中的主题。  
  
##  <a name="getparamvalue"></a>  CDaoQueryDef::GetParamValue  
 调用此成员函数以检索存储在 querydef 的参数集合中的指定参数的当前值。  
  
```  
virtual COleVariant GetParamValue(LPCTSTR lpszName);  
virtual COleVariant GetParamValue(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 *lpszName*  
 要对按名称查找其值的参数的名称。  
  
 *nIndex*  
 按索引进行查找的 querydef 的参数集合中的参数的从零开始的索引。 您可以获取此值通过调用[GetParameterCount](#getparametercount)并[GetParameterInfo](#getparameterinfo)。  
  
### <a name="return-value"></a>返回值  
 类的对象[COleVariant](../../mfc/reference/colevariant-class.md) ，其中包含参数的值。  
  
### <a name="remarks"></a>备注  
 按名称或集合中其序号位置，可以访问该参数。  
  
 有关相关信息，请参阅"参数声明 (SQL)"DAO 帮助中的主题。  
  
##  <a name="getrecordsaffected"></a>  CDaoQueryDef::GetRecordsAffected  
 调用此成员函数可确定多少条记录受影响的最后一次调用[Execute](#execute)。  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>返回值  
 受影响的记录数。  
  
### <a name="remarks"></a>备注  
 返回的计数将不会反映在级联更新或删除时的相关表中的更改都生效。  
  
 有关相关信息请参阅主题 DAO 帮助中的"RecordsAffected 属性"。  
  
##  <a name="getreturnsrecords"></a>  CDaoQueryDef::GetReturnsRecords  
 调用此成员函数可确定 querydef 是否基于查询返回的记录。  
  
```  
BOOL GetReturnsRecords();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果 querydef 基于一个查询返回的记录;否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数仅用于 SQL 传递查询。 有关 SQL 查询的详细信息，请参阅[Execute](#execute)成员函数。 有关使用 SQL 直接传递查询的详细信息，请参阅[SetReturnsRecords](#setreturnsrecords)成员函数。  
  
 有关相关信息，请参阅"属性"DAO 帮助中的主题。  
  
##  <a name="getsql"></a>  CDaoQueryDef::GetSQL  
 调用此成员函数以检索定义 querydef 所基于的查询的 SQL 语句。  
  
```  
CString GetSQL();
```  
  
### <a name="return-value"></a>返回值  
 定义 querydef 所基于的查询的 SQL 语句。  
  
### <a name="remarks"></a>备注  
 然后将可能分析的字符串关键字、 表名等。  
  
 有关相关信息，请参阅"SQL Property"、"比较的 Microsoft Jet 数据库引擎 SQL 和 ANSI SQL"和"查询数据库与 SQL 中的代码"DAO 帮助中的主题。  
  
##  <a name="gettype"></a>  CDaoQueryDef::GetType  
 调用此成员函数来确定此 querydef 的查询类型。  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>返回值  
 Querydef 所定义的查询的类型。 值，请参阅备注。  
  
### <a name="remarks"></a>备注  
 查询类型设置由什么 querydef 的 SQL 字符串中时指定创建 querydef 或调用现有 querydef [SetSQL](#setsql)成员函数。 此函数返回的查询类型可以是下列值之一：  
  
- `dbQSelect` 选择  
  
- `dbQAction` 操作  
  
- `dbQCrosstab` 交叉表  
  
- `dbQDelete` 删除  
  
- `dbQUpdate` 更新  
  
- `dbQAppend` 追加  
  
- `dbQMakeTable` 生成表  
  
- `dbQDDL` 数据定义  
  
- `dbQSQLPassThrough` 直通  
  
- `dbQSetOperation` 联合  
  
- `dbQSPTBulk` 用于`dbQSQLPassThrough`若要指定不返回记录的查询。  
  
> [!NOTE]
>  若要创建 SQL 传递查询，不设置`dbSQLPassThrough`常量。 这是由自动设置 Microsoft Jet 数据库引擎时创建 querydef 对象并设置连接字符串。  
  
 有关 SQL 字符串的信息，请参阅[GetSQL](#getsql)。 有关查询类型的信息，请参阅[Execute](#execute)。  
  
##  <a name="isopen"></a>  CDaoQueryDef::IsOpen  
 调用此成员函数以确定是否`CDaoQueryDef`对象当前处于打开状态。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果非零`CDaoQueryDef`对象是当前打开; 否则为 0。  
  
### <a name="remarks"></a>备注  
 Querydef 必须是处于打开状态，然后使用它来调用[Execute](#execute)或创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象。 若要使 querydef 处于打开状态调用要么[创建](#create)（适用于新 querydef) 或[打开](#open)（适用于现有的 querydef)。  
  
##  <a name="m_pdatabase"></a>  CDaoQueryDef::m_pDatabase  
 包含一个指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)与 querydef 对象相关联的对象。  
  
### <a name="remarks"></a>备注  
 如果您需要直接访问数据库，请使用此指针 — 例如，若要获取指向其他 querydef 或记录集对象的数据库集合中。  
  
##  <a name="m_pdaoquerydef"></a>  CDaoQueryDef::m_pDAOQueryDef  
 包含基础 DAO querydef 对象的 OLE 接口的指针。  
  
### <a name="remarks"></a>备注  
 This 指针的完整性和一致性与其他类提供。 但是，因为 MFC 而不是完全封装 DAO querydefs，您不太可能需要它。 如果您使用它，请谨慎 — 除非您知道您做什么特别是，不要更改指针的值。  
  
##  <a name="open"></a>  CDaoQueryDef::Open  
 调用此成员函数以打开 querydef 以前保存的数据库的 QueryDefs 集合中。  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>参数  
 *lpszName*  
 一个字符串，包含已保存的 querydef，若要打开的名称。 可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>备注  
 打开 querydef 后，可以调用其[Execute](#execute)成员函数或使用创建 querydef [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象。  
  
##  <a name="setconnect"></a>  CDaoQueryDef::SetConnect  
 调用此成员函数以设置 querydef 对象的连接字符串。  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>参数  
 *lpszConnect*  
 一个字符串，包含关联的连接字符串[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。  
  
### <a name="remarks"></a>备注  
 连接字符串用于将附加信息传递到 ODBC 和根据需要某些 ISAM 驱动程序。 它不用于 Microsoft Jet (。MDB) 数据库。  
  
> [!TIP]
>  若要使用的 ODBC 表的首选的方法是将它们连接到。MDB 的数据库。  
  
 在执行到 ODBC 数据源表示 SQL 传递查询 querydef 之前, 设置的连接字符串具有`SetConnect`，并调用[SetReturnsRecords](#setreturnsrecords)来指定查询是否返回的记录。  
  
 有关连接字符串的结构和示例的连接字符串组成部分的详细信息，请参阅主题 DAO 帮助中的"连接属性"。  
  
##  <a name="setname"></a>  CDaoQueryDef::SetName  
 如果你想要更改 querydef 不是临时的名称，请调用此成员函数。  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 *lpszName*  
 包含关联的非临时性查询的新名称的字符串[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。  
  
### <a name="remarks"></a>备注  
 Querydef 名称是唯一的、 用户定义的名称。 您可以调用`SetName`之前 querydef 对象追加到 QueryDefs 集合。  
  
##  <a name="setodbctimeout"></a>  CDaoQueryDef::SetODBCTimeout  
 调用此成员函数以设置 ODBC 数据源的查询超时之前的时间限制。  
  
```  
void SetODBCTimeout(short nODBCTimeout);
```  
  
### <a name="parameters"></a>参数  
 *nODBCTimeout*  
 超时之前查询等待的秒数。  
  
### <a name="remarks"></a>备注  
 此成员函数允许您重写的默认连接的数据源"超时时间。"上的后续操作之前等待的秒数 由于网络访问权限问题、 过多的查询处理时间等的操作可能会超时。 调用`SetODBCTimeout`之前执行具有此 querydef 的查询，如果你想要更改查询超时值。 （如 ODBC 重用连接，超时值是相同的同一连接上的所有客户端。）  
  
 查询超时的默认值为 60 秒。  
  
##  <a name="setparamvalue"></a>  CDaoQueryDef::SetParamValue  
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
 *lpszName*  
 参数要设置其值的名称。  
  
 *varValue*  
 要设置; 的值请参阅备注。  
  
 *nIndex*  
 Querydef 的参数集合中参数的序号位置。 您可以获取此值通过调用[GetParameterCount](#getparametercount)并[GetParameterInfo](#getparameterinfo)。  
  
### <a name="remarks"></a>备注  
 该参数必须已建立 querydef 的 SQL 字符串的一部分。 按名称或集合中其序号位置，可以访问该参数。  
  
 指定要设置为值`COleVariant`对象。 了解如何设置所需的值并键入你`COleVariant`对象，请参阅类[COleVariant](../../mfc/reference/colevariant-class.md)。  
  
##  <a name="setreturnsrecords"></a>  CDaoQueryDef::SetReturnsRecords  
 调用此成员函数设置到外部数据库的 SQL 传递查询的过程的一部分。  
  
```  
void SetReturnsRecords(BOOL bReturnsRecords);
```  
  
### <a name="parameters"></a>参数  
 *bReturnsRecords*  
 在外部数据库查询返回的记录; 如果传递了 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 在这种情况下，必须创建 querydef 并设置其属性使用其他`CDaoQueryDef`成员函数。 外部数据库的说明，请参阅[为表示](#setconnect)。  
  
##  <a name="setsql"></a>  CDaoQueryDef::SetSQL  
 调用此成员函数可设置 querydef 执行的 SQL 语句。  
  
```  
void SetSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>参数  
 *lpszSQL*  
 一个包含一个完整的 SQL 语句，适用于执行字符串。 此字符串的语法取决于 DBMS 的查询目标。 Microsoft Jet 数据库引擎中使用的语法的讨论，请参阅本主题中的"生成 SQL 语句中代码"DAO 帮助。  
  
### <a name="remarks"></a>备注  
 一个典型用途`SetSQL`是在 SQL 传递查询中使用一个 querydef 对象的设置。 （有关 SQL 目标 DBMS 上的传递查询的语法，请参阅所使用的 DBMS 的文档）。  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoException 类](../../mfc/reference/cdaoexception-class.md)
