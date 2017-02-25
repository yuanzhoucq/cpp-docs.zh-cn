---
title: "CDaoQueryDef Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoQueryDef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoQueryDef class"
  - "查询 [Visual Studio], 定义"
  - "QueryDef objects"
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CDaoQueryDef Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示查询定义或“querydef，”在数据库中保存的通常是一个。  
  
## 语法  
  
```  
class CDaoQueryDef : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDaoQueryDef::CDaoQueryDef](../Topic/CDaoQueryDef::CDaoQueryDef.md)|构造 **CDaoQueryDef** 对象。  接下来根据需要调用 **Open** 或 **Create**。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDaoQueryDef::Append](../Topic/CDaoQueryDef::Append.md)|追加querydef对数据库的QueryDefs集合，已保存的查询。|  
|[CDaoQueryDef::CanUpdate](../Topic/CDaoQueryDef::CanUpdate.md)|如果查询可以更新数据库，返回非零。|  
|[CDaoQueryDef::Close](../Topic/CDaoQueryDef::Close.md)|关闭querydef对象。  当您完成使用协定时，请销毁C\+\+对象。|  
|[CDaoQueryDef::Create](../Topic/CDaoQueryDef::Create.md)|创建基础DAO querydef对象。  使用querydef作为一个临时查询或调用 **Append** 将其保存在数据库中。|  
|[CDaoQueryDef::Execute](../Topic/CDaoQueryDef::Execute.md)|执行querydef对象定义的查询。|  
|[CDaoQueryDef::GetConnect](../Topic/CDaoQueryDef::GetConnect.md)|返回连接字符串与querydef。  连接字符串标识数据源。  （对于SQL传递只查询;否则空字符串。）|  
|[CDaoQueryDef::GetDateCreated](../Topic/CDaoQueryDef::GetDateCreated.md)|返回已保存的查询创建日期。|  
|[CDaoQueryDef::GetDateLastUpdated](../Topic/CDaoQueryDef::GetDateLastUpdated.md)|返回次更新已保存的查询的日期。|  
|[CDaoQueryDef::GetFieldCount](../Topic/CDaoQueryDef::GetFieldCount.md)|返回querydef定义的字段数。|  
|[CDaoQueryDef::GetFieldInfo](../Topic/CDaoQueryDef::GetFieldInfo.md)|返回有关在查询定义中的指定字段的信息。|  
|[CDaoQueryDef::GetName](../Topic/CDaoQueryDef::GetName.md)|返回querydef的名称。|  
|[CDaoQueryDef::GetODBCTimeout](../Topic/CDaoQueryDef::GetODBCTimeout.md)|返回ODBC使用的超时值\(有关ODBC查询\)，而querydef执行时。  这多长时间确定允许查询的活动完成。|  
|[CDaoQueryDef::GetParameterCount](../Topic/CDaoQueryDef::GetParameterCount.md)|返回为查询定义参数的数目。|  
|[CDaoQueryDef::GetParameterInfo](../Topic/CDaoQueryDef::GetParameterInfo.md)|返回某个指定参数的信息对查询。|  
|[CDaoQueryDef::GetParamValue](../Topic/CDaoQueryDef::GetParamValue.md)|返回一个指定参数的值传递。|  
|[CDaoQueryDef::GetRecordsAffected](../Topic/CDaoQueryDef::GetRecordsAffected.md)|返回事件查询影响的记录数。|  
|[CDaoQueryDef::GetReturnsRecords](../Topic/CDaoQueryDef::GetReturnsRecords.md)|如果querydef定义的查询返回记录，返回非零。|  
|[CDaoQueryDef::GetSQL](../Topic/CDaoQueryDef::GetSQL.md)|返回指定querydef定义的查询的SQL字符串。|  
|[CDaoQueryDef::GetType](../Topic/CDaoQueryDef::GetType.md)|返回查询类型:删除，更新，追加，生成表，依此类推。|  
|[CDaoQueryDef::IsOpen](../Topic/CDaoQueryDef::IsOpen.md)|如果querydef已打开，并且可以执行，返回非零。|  
|[CDaoQueryDef::Open](../Topic/CDaoQueryDef::Open.md)|打开数据库中的QueryDefs集合存储的现有querydef。|  
|[CDaoQueryDef::SetConnect](../Topic/CDaoQueryDef::SetConnect.md)|设置一个SQL传递查询的连接字符串在ODBC数据源。|  
|[CDaoQueryDef::SetName](../Topic/CDaoQueryDef::SetName.md)|当querydef创建的，则设置已保存的查询的名称，替换在使用的名称。|  
|[CDaoQueryDef::SetODBCTimeout](../Topic/CDaoQueryDef::SetODBCTimeout.md)|设置ODBC使用的超时值\(有关ODBC查询\)，而querydef执行时。|  
|[CDaoQueryDef::SetParamValue](../Topic/CDaoQueryDef::SetParamValue.md)|一个指定参数的值传递。|  
|[CDaoQueryDef::SetReturnsRecords](../Topic/CDaoQueryDef::SetReturnsRecords.md)|指定querydef是否返回记录。  设置为 **TRUE** 的此属性可为SQL传递查询才有效。|  
|[CDaoQueryDef::SetSQL](../Topic/CDaoQueryDef::SetSQL.md)|设置指定querydef定义的查询的SQL字符串。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDaoQueryDef::m\_pDAOQueryDef](../Topic/CDaoQueryDef::m_pDAOQueryDef.md)|OLE接口的指针基础DAO querydef对象的。|  
|[CDaoQueryDef::m\_pDatabase](../Topic/CDaoQueryDef::m_pDatabase.md)|对querydef关联的 `CDaoDatabase` 对象的指针。  querydef可能会保存在数据库中。|  
  
## 备注  
 querydef是包含SQL语句描述一个查询及其属性，如“创建日期”和“ODBC超时的数据访问对象”。还可以创建临时querydef对象，而无需保存它们，但是，包括、、更高效—可以很方便地保存通常重用的查询数据库中。  [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 对象维护集合，调用QueryDefs集合，包含其保存的querydefs。  
  
> [!NOTE]
>  DAO数据库选件类根据了开放式数据库连接的MFC数据库选件类都一目了然\(odbc）。  所有DAO数据库类名具有“CDao”前缀。  您仍然可以访问使用DAO选件类的ODBC数据源。  通常，基于DAO的MFC选件类与基于ODBC的MFC选件类能够;基于DAO的选件类可以访问数据访问，包括通过ODBC驱动程序，将它们的数据库引擎。  基于DAO的选件类通过选件类还支持数据定义语言\(DDL\)操作，例如添加表，而不必直接调用DAO。  
  
## 用法  
 使用querydef对象都与现有的已保存查询使用或创建新的已保存查询或临时查询:  
  
1.  在所有情况下，请首先构造 `CDaoQueryDef` 对象，指向查询所属的 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 对象。  
  
2.  然后根据执行以下操作，您需要:  
  
    -   若要使用现有保存的查询，调用querydef对象的 [打开](../Topic/CDaoQueryDef::Open.md) 成员函数，提供已保存的查询的名称。  
  
    -   若要创建一个新的已保存的查询，请调用querydef对象的 [创建](../Topic/CDaoQueryDef::Create.md) 成员函数，提供查询的名称。  然后调用 [追加](../Topic/CDaoQueryDef::Append.md) 通过追加它以将该查询保存到数据库的QueryDefs集合。  **Create** 将querydef到一个打开状态，因此，在调用 **Create** 后不要调用 **Open**。  
  
    -   若要创建一个临时querydef，请调用 **Create**。  通过查询名称为空字符串。  不要调用 **Append**。  
  
 使用完querydef对象时，请调用 [关闭](../Topic/CDaoQueryDef::Close.md) 成员函数;然后销毁querydef对象。  
  
> [!TIP]
>  方便地创建已保存的查询将创建和存储在数据库中使用Microsoft Access。  然后可以将MFC代码可以打开并使用它们。  
  
## 用途  
 可以执行以下任何用途querydef对象:  
  
-   创建 `CDaoRecordset` 对象  
  
-   调用对象的 **Execute** 成员函数直接执行的查询或SQL传递查询  
  
 可以为任何类型的查询使用querydef对象，包括选择，事件、crosstab、删除、更新、追加，生成表、数据定义、SQL传递、联合和批量查询。  查询的类型取决于所提供SQL语句的内容。  有关查询类型的信息，请参见 **Execute** 和 [GetType](../Topic/CDaoQueryDef::GetType.md) 成员函数。  记录集为返回行的查询，通常这些通常用于使用 **选择…从** 关键字。  **Execute** 为批量操作是最常用的。  有关更多信息，请参见 [执行](../Topic/CDaoQueryDef::Execute.md) 和 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
## Querydefs和记录集  
 若要使用querydef对象创建 `CDaoRecordset` 对象，通常需要创建或上述打开一个querydef。  然后，在调用 [CDaoRecordset::Open](../Topic/CDaoRecordset::Open.md)时，构造记录集对象，通过指向您的querydef对象。  通过的querydef必须在打开状态。  有关更多信息，请参见选件类 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 不能使用querydef创建记录集\(最常见querydef的\)，除非它在打开状态。  将querydef到一个打开状态通过调用 **Open** 或 **Create**。  
  
## 外部数据库  
 Querydef对象是首选方法使用外部数据库引擎的本机SQL语言分支。  例如，可以在querydef对象中创建处理SQL查询\(如使用Microsoft SQL Server\)并将它存储。  当您需要使用基于Microsoft Jet数据库引擎时不的SQL查询，您必须提供指向一个外部数据源的连接字符串。  使用有效的连接的查询字符串跳过数据库引擎并将查询直接到进程中的外部数据库服务器。  
  
> [!TIP]
>  首选方式使用ODBC处理表将它们附加到Microsoft Jet \(.MDB\)数据库。  
  
 有关相关信息，请参见主题“QueryDef对象”，“QueryDefs集合”和“CdbDatabase对象” DAO SDK。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoQueryDef`  
  
## 要求  
 **Header:** afxdao.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoException Class](../../mfc/reference/cdaoexception-class.md)