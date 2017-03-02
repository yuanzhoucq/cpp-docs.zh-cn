---
title: "CDaoQueryDef 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoQueryDef
dev_langs:
- C++
helpviewer_keywords:
- QueryDef objects
- CDaoQueryDef class
- queries [Visual Studio], defining
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
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
ms.openlocfilehash: 0bf06c68bb7072aa1907e4c730848cca9ff5e7d0
ms.lasthandoff: 02/24/2017

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
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|构造**CDaoQueryDef**对象。 接下来调用**打开**或**创建**，取决于您的需要。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CDaoQueryDef::Append](#append)|将此 querydef 追加到数据库的 QueryDefs 集合作为已保存的查询。|  
|[CDaoQueryDef::CanUpdate](#canupdate)|返回非零，如果查询可以更新数据库。|  
|[CDaoQueryDef::Close](#close)|关闭 querydef 对象。 与之完成后销毁 c + + 对象。|  
|[CDaoQueryDef::Create](#create)|创建基础的 DAO querydef 对象。 将用作临时查询或调用 querydef**追加**将其保存在数据库中。|  
|[CDaoQueryDef::Execute](#execute)|执行由 querydef 对象定义的查询。|  
|[CDaoQueryDef::GetConnect](#getconnect)|返回与此 querydef 关联的连接字符串。 连接字符串标识数据源。 （用于 SQL 传递查询; 否则为空字符串。）|  
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|返回已保存的查询的创建的日期。|  
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|返回上次更新已保存的查询的日期。|  
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|返回由 querydef 定义字段的数目。|  
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|返回有关在查询中定义的指定字段的信息。|  
|[CDaoQueryDef::GetName](#getname)|返回此 querydef 的名称。|  
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|返回查询可使用由 ODBC （ODBC） 的超时值执行 querydef 时。 这可确定多长时间以允许查询的操作才能完成。|  
|[CDaoQueryDef::GetParameterCount](#getparametercount)|返回为该查询定义的参数数目。|  
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|对查询返回有关指定参数的信息。|  
|[CDaoQueryDef::GetParamValue](#getparamvalue)|向查询中返回指定的参数的值。|  
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|返回由操作查询影响的记录数。|  
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|返回非零，如果 querydef 所定义的查询返回的记录。|  
|[CDaoQueryDef::GetSQL](#getsql)|返回指定 querydef 所定义的查询的 SQL 字符串。|  
|[CDaoQueryDef::GetType](#gettype)|返回的查询类型︰ 删除、 更新、 追加生成表等等。|  
|[CDaoQueryDef::IsOpen](#isopen)|如果此 querydef 处于打开状态，并且可以执行，则返回非零值。|  
|[CDaoQueryDef::Open](#open)|打开现有 querydef 存储在数据库的 QueryDefs 集合中。|  
|[CDaoQueryDef::SetConnect](#setconnect)|在 ODBC 数据源上设置 SQL 传递查询的连接字符串。|  
|[CDaoQueryDef::SetName](#setname)|设置已保存的查询，并且替换中使用的名称，创建此 querydef 时的名称。|  
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|设置查询可使用由 ODBC （ODBC） 的超时值执行 querydef 时。|  
|[CDaoQueryDef::SetParamValue](#setparamvalue)|将指定参数的值设置为该查询。|  
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|指定是否 querydef 返回的记录。 此属性设置为**TRUE**才有效的 SQL 传递查询。|  
|[CDaoQueryDef::SetSQL](#setsql)|设置指定 querydef 所定义的查询的 SQL 字符串。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|指向基础 DAO querydef 对象的 OLE 接口的指针。|  
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|一个指向`CDaoDatabase`querydef 与之关联的对象。 与否，querydef 可能保存在数据库中。|  
  
## <a name="remarks"></a>备注  
 Querydef 是包含描述一个查询，以及其属性，如"创建日期"和"ODBC Timeout。"的 SQL 语句的数据访问对象 您还可以创建临时 querydef 对象而不进行保存，但会很方便 — 和高效得多 — 以保存常用的重复使用数据库中的查询。 一个[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象会维护一个名为 QueryDefs 集合，包含其已保存的 querydefs 集合。  
  
> [!NOTE]
>  DAO 数据库类中是不同于基于开放式数据库连接 (ODBC) 的 MFC 数据库类。 DAO 数据库类的所有名称都具有"CDao"前缀。 您仍可以访问 ODBC 数据源对于 DAO 类。 通常情况下，基于 DAO MFC 类包括更强于基于 ODBC; 的 MFC 类基于 DAO 的类可以访问数据，包括通过 ODBC 驱动程序，通过其自己的数据库引擎。 基于 DAO 的类还支持数据定义语言 (DDL) 操作，如添加表通过类，而无需直接调用 DAO。  
  
## <a name="usage"></a>用法  
 使用 querydef 对象这两个要使用现有的已保存查询，也要创建一个新保存临时查询或查询︰  
  
1.  在所有情况下，首先构建了`CDaoQueryDef`对象，提供一个指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)查询所属对象。  
  
2.  然后执行以下操作，具体取决于您的想法︰  
  
    -   若要使用现有的已保存查询，调用 querydef 对象[打开](#open)成员函数，提供的已保存的查询的名称。  
  
    -   若要创建新的已保存的查询时，调用 querydef 对象[创建](#create)成员函数，提供的查询的名称。 然后，调用[追加](#append)以将其追加到该数据库的 QueryDefs 集合以保存查询。 **创建**将 querydef 放入打开的状态，因此在调用**创建**不调用**打开**。  
  
    -   若要创建临时 querydef，调用**创建**。 将传递查询名称为空字符串。 不要调用**追加**。  
  
 当您完成使用 querydef 对象时，调用其[关闭](#close)成员函数; 然后销毁 querydef 对象。  
  
> [!TIP]
>  若要创建已保存的查询的最简单方法是创建它们，并将其存储在使用 Microsoft Access 数据库中。 然后可以打开并在您的 MFC 代码中使用它们。  
  
## <a name="purposes"></a>目的  
 可以为任何以下目的使用 querydef 对象︰  
  
-   若要创建`CDaoRecordset`对象  
  
-   要调用的对象**Execute**成员函数来直接执行操作查询或 SQL 传递查询  
  
 可以使用任何类型的查询，包括选择、 操作、 交叉表、 删除、 更新 querydef 对象、 添加生成表、 数据定义、 SQL 传递、 union、 和大容量查询。 您提供的 SQL 语句的内容确定查询的类型。 有关查询类型的信息，请参阅**Execute**和[GetType](#gettype)成员函数。 记录集通常用于返回行的查询时，通常那些使用**选择...从**关键字。 **执行**最常用于大容量操作。 有关详细信息，请参阅[Execute](#execute)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
## <a name="querydefs-and-recordsets"></a>Querydefs 和记录集  
 若要使用 querydef 对象创建`CDaoRecordset`对象时，您通常创建或打开 querydef，上文所述。 然后，构建一个记录集对象，将指针传递给 querydef 对象，当您调用[cdaorecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)。 您传递的 querydef 必须处于打开状态。 有关详细信息，请参见类[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 Querydef 不能用于创建记录集 （最常见的 querydef 用途），除非它是处于打开状态。 将此 querydef 放入打开的状态，通过调用**打开**或**创建**。  
  
## <a name="external-databases"></a>外部数据库  
 Querydef 对象是使用外部数据库引擎的本机 SQL 方言的首选的方法。 例如，可以创建 Transact SQL 查询 （如 Microsoft SQL Server 上使用），并将其存储在 querydef 对象。 当您需要使用不基于 Microsoft Jet 数据库引擎的 SQL 查询时，必须提供指向外部数据源的连接字符串。 具有有效的连接字符串的查询跳过数据库引擎，该查询将直接传递到外部数据库服务器处理。  
  
> [!TIP]
>  使用 ODBC 表的首选的方法是将其附加到 Microsoft Jet (。MDB) 数据库。  
  
 有关相关信息，请参阅"QueryDef 对象"、"QueryDefs 集合"和"CdbDatabase 对象"DAO SDK 中的主题。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoQueryDef`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdao.h  
  
##  <a name="a-nameappenda--cdaoquerydefappend"></a><a name="append"></a>CDaoQueryDef::Append  
 在您调用后调用此成员函数[创建](#create)以创建新的 querydef 对象。  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>备注  
 **追加**将 querydef 保存到数据库的 QueryDefs 集合附加该对象的数据库。 可以使用此 querydef 作为临时对象不会将附加它，但如果您希望其持久保存，则必须调用**追加**。  
  
 如果您尝试将临时 querydef 对象追加，MFC 将引发类型的异常[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
##  <a name="a-namecanupdatea--cdaoquerydefcanupdate"></a><a name="canupdate"></a>CDaoQueryDef::CanUpdate  
 调用此成员函数来确定您是否可以修改此 querydef — 例如，更改其名称或 SQL 字符串。  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果您有权修改 querydef;否则为 0。  
  
### <a name="remarks"></a>备注  
 如果可以修改此 querydef:  
  
-   它不基于只读方式打开的数据库。  
  
-   您具有更新权限的数据库。  
  
     这取决于是否已实现的安全功能。 MFC 为安全性，则不提供的支持您必须实现它自己的调用 DAO 直接或通过使用 Microsoft Access。 请参阅主题 DAO 帮助中的"权限属性"。  
  
##  <a name="a-namecdaoquerydefa--cdaoquerydefcdaoquerydef"></a><a name="cdaoquerydef"></a>CDaoQueryDef::CDaoQueryDef  
 构造**CDaoQueryDef**对象。  
  
```  
CDaoQueryDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>参数  
 `pDatabase`  
 向打开的指针[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。  
  
### <a name="remarks"></a>备注  
 该对象可以表示存储在数据库的 QueryDefs 集合、 新的查询存储在集合中或临时查询，无法存储现有 querydef。 下一步取决于 querydef 的类型︰  
  
-   如果该对象表示现有 querydef，调用对象的[打开](#open)成员函数来对其进行初始化。  
  
-   如果该对象表示要保存新 querydef，调用对象的[创建](#create)成员函数。 将对象添加到数据库的 QueryDefs 集合。 然后，调用`CDaoQueryDef`成员函数来设置对象的属性。 最后，调用[追加](#append)。  
  
-   如果该对象表示临时 querydef （不保存到数据库中），则调用**创建**，传递空字符串作为查询的名称。 在调用**创建**，通过直接设置其属性初始化 querydef。 不要调用**追加**。  
  
 若要设置此 querydef 的属性，可以使用[SetName](#setname)， [SetSQL](#setsql)，[为表示](#setconnect)， [SetODBCTimeout](#setodbctimeout)，和[SetReturnsRecords](#setreturnsrecords)成员函数。  
  
 当完成 querydef 对象时，调用其[关闭](#close)成员函数。 如果您有一个指针指向此 querydef，使用**删除**运算符来销毁 c + + 对象。  
  
##  <a name="a-nameclosea--cdaoquerydefclose"></a><a name="close"></a>CDaoQueryDef::Close  
 当使用 querydef 对象完成时调用此成员函数。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 关闭此 querydef 释放基础的 DAO 对象但不会破坏已保存的 DAO querydef 对象或 c + +`CDaoQueryDef`对象。 这不是与相同[CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef)，此操作将删除此 querydef DAO （如果不是临时 querydef） 中的数据库的 QueryDefs 集合中。  
  
##  <a name="a-namecreatea--cdaoquerydefcreate"></a><a name="create"></a>CDaoQueryDef::Create  
 调用此成员函数以创建新的已保存的查询或新的临时查询。  
  
```  
virtual void Create(
    LPCTSTR lpszName = NULL,  
    LPCTSTR lpszSQL = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 保存到数据库中的查询的唯一名称。 有关字符串的详细信息，请参阅主题 DAO 帮助中的"CreateQueryDef 方法"。 如果您接受默认值为空字符串时，会创建临时 querydef。 此类查询不会保存 QueryDefs 集合中。  
  
 `lpszSQL`  
 用于定义查询的 SQL 字符串。 如果您接受默认值为**NULL**，稍后必须调用[SetSQL](#setsql)设置字符串。 到那时，该查询是不确定。 但是，可以使用未定义的查询打开记录集;有关详细信息，请参阅备注。 可以将此 querydef 追加到 QueryDefs 集合之前，必须定义 SQL 语句。  
  
### <a name="remarks"></a>备注  
 如果通过在名称`lpszName`，然后，可以调用[追加](#append)querydef 保存数据库的 QueryDefs 集合中。 否则为该对象是临时 querydef 并不会被保存。 在任一情况下，此 querydef 是处于打开状态，并且您也可以使用它来创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象或调用此 querydef [Execute](#execute)成员函数。  
  
 如果不提供 SQL 语句中的`lpszSQL`，不能运行与查询**Execute**但可以使用它来创建一个记录集。 在这种情况下，MFC 使用记录集的默认的 SQL 语句。  
  
##  <a name="a-nameexecutea--cdaoquerydefexecute"></a><a name="execute"></a>CDaoQueryDef::Execute  
 调用该成员函数以运行 querydef 对象所定义的查询。  
  
```  
virtual void Execute(int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>参数  
 `nOptions`  
 一个整数，用于确定查询的特征。 有关相关信息，请参阅主题 DAO 帮助中的"执行方法"。 您可以使用按位 OR 运算符 ( **|**) 组合为此参数的以下常量︰  
  
- **dbDenyWrite**拒绝向其他用户授权写入权限。  
  
- **dbInconsistent**不一致的更新。  
  
- **dbConsistent**一致的更新。  
  
- **dbSQLPassThrough** SQL 传递。 使 SQL 语句，以传递到 ODBC 数据库以进行处理。  
  
- **dbFailOnError**默认值。 回滚更新如果发生错误和错误报告给用户。  
  
- **dbSeeChanges**生成运行时错误，如果另一个用户是正在更改您正在编辑的数据。  
  
> [!NOTE]
>  有关的术语的解释ぃ璓"不一致"和"一致，"请参阅主题 DAO 帮助中的"执行方法"。  
  
### <a name="remarks"></a>备注  
 使用它来执行这种方式 Querydef 对象只能表示下列查询类型之一︰  
  
-   操作查询  
  
-   SQL 传递查询  
  
 **执行**查询返回的记录，如 select 查询中不工作。 **执行**通常用于大容量操作的查询，如**更新**，**插入**，或**SELECT INTO**，或数据定义语言 (DDL) 操作。  
  
> [!TIP]
>  若要使用 ODBC 数据源的首选的方式是将表附加到 Microsoft Jet (。MDB) 数据库。 有关详细信息，请参阅主题"访问外部数据库中的用 DAO"DAO 帮助。  
  
 调用[GetRecordsAffected](#getrecordsaffected) querydef 对象以确定受影响的最新的记录数的成员函数**Execute**调用。 例如，`GetRecordsAffected`返回有关已删除、 更新或执行操作查询时插入的记录数的信息。 返回的计数不会反映在级联更新或删除时的相关表中的更改都生效。  
  
 如果同时包括**dbInconsistent**和**dbConsistent**或者如果既不包含，则结果为默认情况下， **dbInconsistent**。  
  
 **执行**不会返回一个记录集。 使用**Execute**上选择记录的查询将导致引发异常的类型的 MFC [CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
##  <a name="a-namegetconnecta--cdaoquerydefgetconnect"></a><a name="getconnect"></a>CDaoQueryDef::GetConnect  
 调用此成员函数可获取与此 querydef 数据源关联的连接字符串。  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)包含 querydef 的连接字符串。  
  
### <a name="remarks"></a>备注  
 此函数只能用于 ODBC 数据源和某些 ISAM 驱动程序。 不用于 Microsoft Jet (。MDB) 的数据库。在这种情况下，`GetConnect`返回一个空字符串。 有关详细信息，请参阅[为表示](#setconnect)。  
  
> [!TIP]
>  若要使用 ODBC 表的首选的方法是将它们连接到。MDB 的数据库。 有关详细信息，请参阅主题"访问外部数据库中的用 DAO"DAO 帮助。  
  
 有关连接字符串的信息，请参阅主题 DAO 帮助中的"连接属性"。  
  
##  <a name="a-namegetdatecreateda--cdaoquerydefgetdatecreated"></a><a name="getdatecreated"></a>CDaoQueryDef::GetDateCreated  
 调用此成员函数可获取 querydef 对象的创建的日期。  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>返回值  
 一个[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含的日期和时间 querydef 已创建。  
  
### <a name="remarks"></a>备注  
 有关相关信息，请参阅 DAO 帮助中的主题"DateCreated，上次更新属性"。  
  
##  <a name="a-namegetdatelastupdateda--cdaoquerydefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoQueryDef::GetDateLastUpdated  
 调用此成员函数来获取日期 querydef 对象上次更新 — 当其任何属性已更改，例如其名称、 其 SQL 字符串或其连接字符串。  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>返回值  
 一个[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含的日期和 querydef 上次更新的时间。  
  
### <a name="remarks"></a>备注  
 有关相关信息，请参阅 DAO 帮助中的主题"DateCreated，上次更新属性"。  
  
##  <a name="a-namegetfieldcounta--cdaoquerydefgetfieldcount"></a><a name="getfieldcount"></a>CDaoQueryDef::GetFieldCount  
 调用此成员函数以检索查询中的字段数。  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>返回值  
 在查询中定义的字段数。  
  
### <a name="remarks"></a>备注  
 `GetFieldCount`可用于循环遍历此 querydef 中的所有字段。 实现此目的，使用`GetFieldCount`结合[GetFieldInfo](#getfieldinfo)。  
  
##  <a name="a-namegetfieldinfoa--cdaoquerydefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoQueryDef::GetFieldInfo  
 调用该成员函数以获取有关此 querydef 中定义的字段的信息的各种类型。  
  
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
 在此 querydef 字段集合中，对于通过索引查找所需字段的从零开始的索引。  
  
 `fieldinfo`  
 对引用`CDaoFieldInfo`返回所请求的信息的对象。  
  
 `dwInfoOptions`  
 指定有关要检索的字段的信息的选项。 以及它们会导致返回的函数，这里列出了可用的选项︰  
  
- `AFX_DAO_PRIMARY_INFO`（默认值）名称、 类型、 大小、 属性  
  
- `AFX_DAO_SECONDARY_INFO`加上的主要信息︰ 要求的序号位置、 允许长度为零、 源字段、 外名称、 源表、 排序规则顺序  
  
- `AFX_DAO_ALL_INFO`主要和次要信息加上︰ 默认值，验证文本验证规则  
  
 `lpszName`  
 包含按名称查找所需字段的名称的字符串。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>备注  
 有关在中返回的信息的说明`fieldinfo`，请参阅[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 这种结构有成员对应的描述性信息下`dwInfoOptions`上方。 如果您请求的信息的一个级别，将获得信息以及任何前面级别。  
  
##  <a name="a-namegetnamea--cdaoquerydefgetname"></a><a name="getname"></a>CDaoQueryDef::GetName  
 调用该成员函数以检索 querydef 所表示的查询的名称。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>返回值  
 查询的名称。  
  
### <a name="remarks"></a>备注  
 Querydef 名称是唯一的用户定义名称。 有关 querydef 名称的详细信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
##  <a name="a-namegetodbctimeouta--cdaoquerydefgetodbctimeout"></a><a name="getodbctimeout"></a>CDaoQueryDef::GetODBCTimeout  
 调用该成员函数以检索到 ODBC 数据源的查询超时之前的当前时间限制。  
  
```  
short GetODBCTimeout();
```  
  
### <a name="return-value"></a>返回值  
 超时之前查询等待的秒数。  
  
### <a name="remarks"></a>备注  
 有关此时间限制的信息，请参阅主题 DAO 帮助中的"odbc 超时属性"。  
  
> [!TIP]
>  使用 ODBC 表的首选的方法是将其附加到 Microsoft Jet (。MDB) 数据库。 有关详细信息，请参阅主题"访问外部数据库中的用 DAO"DAO 帮助。  
  
##  <a name="a-namegetparametercounta--cdaoquerydefgetparametercount"></a><a name="getparametercount"></a>CDaoQueryDef::GetParameterCount  
 调用此成员函数以检索保存的查询中的参数数目。  
  
```  
short GetParameterCount();
```  
  
### <a name="return-value"></a>返回值  
 在查询中定义的参数数目。  
  
### <a name="remarks"></a>备注  
 `GetParameterCount`可用于循环访问此 querydef 中的所有参数。 实现此目的，使用`GetParameterCount`结合[GetParameterInfo](#getparameterinfo)。  
  
 有关相关信息，请参阅"参数对象"、"参数集合"和"参数声明 (SQL)"DAO 帮助中的主题。  
  
##  <a name="a-namegetparameterinfoa--cdaoquerydefgetparameterinfo"></a><a name="getparameterinfo"></a>CDaoQueryDef::GetParameterInfo  
 调用该成员函数以获取有关此 querydef 中定义的参数的信息。  
  
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
 在此 querydef 参数集合中，对于通过索引查找所需参数的从零开始的索引。  
  
 `paraminfo`  
 对引用[CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)返回所请求的信息的对象。  
  
 `dwInfoOptions`  
 指定要检索的参数有关的信息的选项。 它会导致返回的函数以及此处列出的可用选项︰  
  
- `AFX_DAO_PRIMARY_INFO`（默认值）名称、 类型  
  
 `lpszName`  
 包含按名称查找所需参数的名称的字符串。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>备注  
 有关在中返回的信息的说明`paraminfo`，请参阅[CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)结构。 这种结构有成员对应的描述性信息下`dwInfoOptions`上方。  
  
 有关相关信息，请参阅"参数声明 (SQL)"DAO 帮助中的主题。  
  
##  <a name="a-namegetparamvaluea--cdaoquerydefgetparamvalue"></a><a name="getparamvalue"></a>CDaoQueryDef::GetParamValue  
 调用该成员函数以检索存储在 querydef 的参数集合中的指定参数的当前值。  
  
```  
virtual COleVariant GetParamValue(LPCTSTR lpszName);  
virtual COleVariant GetParamValue(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 要用于按名称查找其值的参数的名称。  
  
 `nIndex`  
 在此 querydef 参数集合中，对于通过索引查找参数的从零开始索引。 您可以获取此值对的调用与[GetParameterCount](#getparametercount)和[GetParameterInfo](#getparameterinfo)。  
  
### <a name="return-value"></a>返回值  
 类的对象[COleVariant](../../mfc/reference/colevariant-class.md) ，其中包含参数的值。  
  
### <a name="remarks"></a>备注  
 按名称或在集合中的序号位置，您可以访问该参数。  
  
 有关相关信息，请参阅"参数声明 (SQL)"DAO 帮助中的主题。  
  
##  <a name="a-namegetrecordsaffecteda--cdaoquerydefgetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoQueryDef::GetRecordsAffected  
 调用此成员函数以确定多少条记录受影响的最后一次调用[Execute](#execute)。  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>返回值  
 受影响的记录数。  
  
### <a name="remarks"></a>备注  
 返回的计数不会反映在级联更新或删除时的相关表中的更改都生效。  
  
 有关相关信息请参阅主题 DAO 帮助中的"RecordsAffected 属性"。  
  
##  <a name="a-namegetreturnsrecordsa--cdaoquerydefgetreturnsrecords"></a><a name="getreturnsrecords"></a>CDaoQueryDef::GetReturnsRecords  
 调用该成员函数以确定此 querydef 是否基于该查询将返回的记录。  
  
```  
BOOL GetReturnsRecords();
```  
  
### <a name="return-value"></a>返回值  
 如果此 querydef 基于查询的非零返回记录。否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数仅用于 SQL 传递查询。 有关 SQL 查询的详细信息，请参阅[Execute](#execute)成员函数。 有关使用 SQL 直接传递查询的详细信息，请参阅[SetReturnsRecords](#setreturnsrecords)成员函数。  
  
 有关相关信息，请参阅"属性"DAO 帮助中的主题。  
  
##  <a name="a-namegetsqla--cdaoquerydefgetsql"></a><a name="getsql"></a>CDaoQueryDef::GetSQL  
 调用该成员函数以检索定义 querydef 所基于的查询的 SQL 语句。  
  
```  
CString GetSQL();
```  
  
### <a name="return-value"></a>返回值  
 定义此 querydef 所基于的查询的 SQL 语句。  
  
### <a name="remarks"></a>备注  
 然后，您将可能分析关键字、 表名等的字符串。  
  
 有关相关信息，请参阅"SQL Property"、"比较的 Microsoft Jet 数据库引擎 SQL 和 ANSI SQL"和"查询数据库与 SQL 中的代码"DAO 帮助中的主题。  
  
##  <a name="a-namegettypea--cdaoquerydefgettype"></a><a name="gettype"></a>CDaoQueryDef::GetType  
 调用该成员函数以确定此 querydef 的查询类型。  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>返回值  
 由 querydef 定义查询的类型。 值，请参阅备注。  
  
### <a name="remarks"></a>备注  
 查询类型将由您指定的内容 querydef SQL 字符串中时创建此 querydef 或者调用现有 querydef [SetSQL](#setsql)成员函数。 此函数返回的查询类型可以是下列值之一︰  
  
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
>  若要创建的 SQL 传递查询，不设置**dbSQLPassThrough**常量。 这将自动由 Microsoft Jet 数据库引擎时创建 querydef 对象并设置连接字符串。  
  
 有关 SQL 字符串的信息，请参阅[GetSQL](#getsql)。 有关查询类型的信息，请参阅[Execute](#execute)。  
  
##  <a name="a-nameisopena--cdaoquerydefisopen"></a><a name="isopen"></a>CDaoQueryDef::IsOpen  
 调用此成员函数以确定是否`CDaoQueryDef`对象当前处于打开状态。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果非零`CDaoQueryDef`对象是当前打开; 否则为 0。  
  
### <a name="remarks"></a>备注  
 Querydef 处于打开状态之前必须使用它来调用[Execute](#execute)或创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象。 若要使 querydef 处于打开状态调用或者[创建](#create)（适用于新 querydef) 或[打开](#open)（适用于现有的 querydef)。  
  
##  <a name="a-namempdatabasea--cdaoquerydefmpdatabase"></a><a name="m_pdatabase"></a>CDaoQueryDef::m_pDatabase  
 包含一个指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)与 querydef 对象相关联的对象。  
  
### <a name="remarks"></a>备注  
 如果您需要直接访问数据库，请使用此指针 — 例如，若要获取指向其他 querydef 或记录集对象的数据库集合中。  
  
##  <a name="a-namempdaoquerydefa--cdaoquerydefmpdaoquerydef"></a><a name="m_pdaoquerydef"></a>CDaoQueryDef::m_pDAOQueryDef  
 包含指向基础 DAO querydef 对象的 OLE 接口的指针。  
  
### <a name="remarks"></a>备注  
 This 指针的完整性和一致性，与其他类提供。 但是，因为 MFC 而是完全封装 DAO querydefs，则可能需要它。 如果您使用它，这样做谨慎 — 特别是，请勿更改指针的值除非您知道自己在做什么。  
  
##  <a name="a-nameopena--cdaoquerydefopen"></a><a name="open"></a>CDaoQueryDef::Open  
 调用该成员函数以打开 querydef 以前保存的数据库的 QueryDefs 集合中。  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 一个字符串，包含已保存的 querydef，若要打开的名称。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>备注  
 一旦此 querydef 处于打开状态，就可以调用其[Execute](#execute)成员函数或使用 querydef 创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象。  
  
##  <a name="a-namesetconnecta--cdaoquerydefsetconnect"></a><a name="setconnect"></a>CDaoQueryDef::SetConnect  
 调用该成员函数以设置 querydef 对象的连接字符串。  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>参数  
 `lpszConnect`  
 一个字符串，包含关联的连接字符串[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。  
  
### <a name="remarks"></a>备注  
 连接字符串用于将附加信息传递到 ODBC 和根据需要某些 ISAM 驱动程序。 不用于 Microsoft Jet (。MDB) 数据库。  
  
> [!TIP]
>  若要使用 ODBC 表的首选的方法是将它们连接到。MDB 的数据库。  
  
 在执行之前 querydef 到 ODBC 数据源表示 SQL 传递查询，设置的连接字符串具有`SetConnect`并调用[SetReturnsRecords](#setreturnsrecords)来指定查询是否返回的记录。  
  
 有关连接字符串的结构和示例的连接字符串成分的详细信息，请参阅主题 DAO 帮助中的"连接属性"。  
  
##  <a name="a-namesetnamea--cdaoquerydefsetname"></a><a name="setname"></a>CDaoQueryDef::SetName  
 如果你想要更改 querydef 不是临时的名称，则调用此成员函数。  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 一个字符串，包含在关联的非临时性查询的新名称[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。  
  
### <a name="remarks"></a>备注  
 Querydef 名称是唯一的、 用户定义的名称。 您可以调用`SetName`之前 querydef 对象追加到 QueryDefs 集合。  
  
##  <a name="a-namesetodbctimeouta--cdaoquerydefsetodbctimeout"></a><a name="setodbctimeout"></a>CDaoQueryDef::SetODBCTimeout  
 调用该成员函数以设置对 ODBC 数据源的查询超时之前的时间限制。  
  
```  
void SetODBCTimeout(short nODBCTimeout);
```  
  
### <a name="parameters"></a>参数  
 *nODBCTimeout*  
 超时之前查询等待的秒数。  
  
### <a name="remarks"></a>备注  
 此成员函数，可以替代默认连接的数据源"超时值"上的后续操作前的秒数。 由于网络访问权限问题、 过多的查询处理时间等的操作可能会超时。 调用`SetODBCTimeout`之前执行与此 querydef 查询，如果您想要更改查询超时值。 （如 ODBC 重用连接，超时值是相同的同一个连接上的所有客户端。）  
  
 查询超时的默认值为 60 秒。  
  
##  <a name="a-namesetparamvaluea--cdaoquerydefsetparamvalue"></a><a name="setparamvalue"></a>CDaoQueryDef::SetParamValue  
 调用该成员函数以在运行时在 querydef 中设置参数的值。  
  
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
 你想要设置其值的参数的名称。  
  
 `varValue`  
 要设置; 的值请参阅备注。  
  
 `nIndex`  
 Querydef 的参数集合中参数的序号位置。 您可以获取此值对的调用与[GetParameterCount](#getparametercount)和[GetParameterInfo](#getparameterinfo)。  
  
### <a name="remarks"></a>备注  
 该参数必须已建立 querydef SQL 字符串的一部分。 按名称或在集合中的序号位置，您可以访问该参数。  
  
 指定的值将设置为`COleVariant`对象。 有关设置所需的值并键入的信息您`COleVariant`对象，请参阅类[COleVariant](../../mfc/reference/colevariant-class.md)。  
  
##  <a name="a-namesetreturnsrecordsa--cdaoquerydefsetreturnsrecords"></a><a name="setreturnsrecords"></a>CDaoQueryDef::SetReturnsRecords  
 调用此成员函数设置到外部数据库的 SQL 传递查询的过程的一部分。  
  
```  
void SetReturnsRecords(BOOL bReturnsRecords);
```  
  
### <a name="parameters"></a>参数  
 *bReturnsRecords*  
 传递**TRUE**如果外部数据库中的查询返回的记录; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 在这种情况下，您必须创建此 querydef 并设置其属性使用其他`CDaoQueryDef`成员函数。 外部数据库的说明，请参阅[为表示](#setconnect)。  
  
##  <a name="a-namesetsqla--cdaoquerydefsetsql"></a><a name="setsql"></a>CDaoQueryDef::SetSQL  
 调用该成员函数以设置 querydef 执行的 SQL 语句。  
  
```  
void SetSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>参数  
 `lpszSQL`  
 一个包含完整的 SQL 语句适用于执行字符串。 此字符串的语法取决于 DBMS，查询目标。 Microsoft Jet 数据库引擎中使用的语法的讨论，请参阅"生成 SQL 语句中的代码"DAO 帮助中的主题。  
  
### <a name="remarks"></a>备注  
 一个典型用途`SetSQL`是设置 querydef 对象以便在 SQL 传递查询中使用的设置。 （有关目标 DBMS 的 SQL 传递查询的语法，请参阅您的 DBMS 的文档。）  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoException 类](../../mfc/reference/cdaoexception-class.md)

