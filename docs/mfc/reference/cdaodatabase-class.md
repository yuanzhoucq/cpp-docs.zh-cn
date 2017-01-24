---
title: "CDaoDatabase Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoDatabase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoDatabase class"
  - "CDaoDatabase class, and workspace"
  - "CDaoDatabase class, vs. CDatabase class"
  - "CDatabase 类, vs. CDaoDatabase class"
  - "数据库类 [C++], DAO"
ms.assetid: 8ff5b342-964d-449d-bef1-d0ff56aadf6d
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoDatabase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示与您可以对数据的数据库的连接。  
  
## 语法  
  
```  
class CDaoDatabase : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDaoDatabase::CDaoDatabase](../Topic/CDaoDatabase::CDaoDatabase.md)|构造 `CDaoDatabase` 对象。  调用 **Open** 连接到数据库中的对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDaoDatabase::CanTransact](../Topic/CDaoDatabase::CanTransact.md)|如果数据库支持事务，返回非零。|  
|[CDaoDatabase::CanUpdate](../Topic/CDaoDatabase::CanUpdate.md)|返回非零，则 `CDaoDatabase` 对象是可更新的\(不是只读的。）|  
|[CDaoDatabase::Close](../Topic/CDaoDatabase::Close.md)|关闭数据库连接。|  
|[CDaoDatabase::Create](../Topic/CDaoDatabase::Create.md)|创建基础DAO数据库对象和初始化 `CDaoDatabase` 对象。|  
|[CDaoDatabase::CreateRelation](../Topic/CDaoDatabase::CreateRelation.md)|定义在表中的新数据库中的关系。|  
|[CDaoDatabase::DeleteQueryDef](../Topic/CDaoDatabase::DeleteQueryDef.md)|移除数据库的QueryDefs集合保存的querydef对象。|  
|[CDaoDatabase::DeleteRelation](../Topic/CDaoDatabase::DeleteRelation.md)|删除表之间的现有关系在数据库中。|  
|[CDaoDatabase::DeleteTableDef](../Topic/CDaoDatabase::DeleteTableDef.md)|在数据库中删除一个表的定义。  这将删除与实际表及其所有数据。|  
|[CDaoDatabase::Execute](../Topic/CDaoDatabase::Execute.md)|执行事件查询。  调用返回结果引发异常的查询的 **Execute**。|  
|[CDaoDatabase::GetConnect](../Topic/CDaoDatabase::GetConnect.md)|返回用于的连接字符串连接到数据库的 `CDaoDatabase` 对象。  用于ODBC。|  
|[CDaoDatabase::GetName](../Topic/CDaoDatabase::GetName.md)|返回当前使用的数据库的名称。|  
|[CDaoDatabase::GetQueryDefCount](../Topic/CDaoDatabase::GetQueryDefCount.md)|返回为数据库定义查询的数目。|  
|[CDaoDatabase::GetQueryDefInfo](../Topic/CDaoDatabase::GetQueryDefInfo.md)|返回有关在数据库中定义的指定一次查询的信息。|  
|[CDaoDatabase::GetQueryTimeout](../Topic/CDaoDatabase::GetQueryTimeout.md)|返回秒数，在后数据库查询操作将超时。  影响后续打开，添加新，更新，并编辑操作，并在ODBC数据源中的其他操作\(仅限\)例如 **Execute** 调用。|  
|[CDaoDatabase::GetRecordsAffected](../Topic/CDaoDatabase::GetRecordsAffected.md)|返回次更新影响的记录数，通过调用编辑或添加操作或到 **Execute**。|  
|[CDaoDatabase::GetRelationCount](../Topic/CDaoDatabase::GetRelationCount.md)|在数据库中返回关系的数目中定义的表之间。|  
|[CDaoDatabase::GetRelationInfo](../Topic/CDaoDatabase::GetRelationInfo.md)|在数据库中返回有关指定关系的信息中定义的表之间。|  
|[CDaoDatabase::GetTableDefCount](../Topic/CDaoDatabase::GetTableDefCount.md)|返回在数据库中定义的表的数目。|  
|[CDaoDatabase::GetTableDefInfo](../Topic/CDaoDatabase::GetTableDefInfo.md)|返回有关指定表的信息在数据库中。|  
|[CDaoDatabase::GetVersion](../Topic/CDaoDatabase::GetVersion.md)|返回数据库引擎的版本与该数据库。|  
|[CDaoDatabase::IsOpen](../Topic/CDaoDatabase::IsOpen.md)|如果 `CDaoDatabase` 对象当前连接到数据库，返回非零。|  
|[CDaoDatabase::Open](../Topic/CDaoDatabase::Open.md)|生成与数据库的连接。|  
|[CDaoDatabase::SetQueryTimeout](../Topic/CDaoDatabase::SetQueryTimeout.md)|设置秒数，在后数据库查询操作\(仅在ODBC数据源\)将超时。  影响后续打开，添加新，更新和删除操作。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDaoDatabase::m\_pDAODatabase](../Topic/CDaoDatabase::m_pDAODatabase.md)|对基础DAO数据库对象的指针。|  
|[CDaoDatabase::m\_pWorkspace](../Topic/CDaoDatabase::m_pWorkspace.md)|对包含该数据库并定义其事务空间的 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 对象的指针。|  
  
## 备注  
 有关备份数据库格式的信息，请参见 [GetName](../Topic/CDaoWorkspace::GetName.md) 成员函数。  一次只能有一个或多 `CDaoDatabase` 对象激活在给定“工作区，”由 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 对象。  工作区维护打开数据库对象的集合，调用数据库集合。  
  
> [!NOTE]
>  MFC DAO数据库选件类从基于ODBC的MFC数据库选件类是不同的。  所有DAO数据库类名具有“CDao”前缀。  选件类 `CDaoDatabase` 提供一个接口类似于ODBC选件类 [CDatabase](../../mfc/reference/cdatabase-class.md)。  主要区别在于 `CDatabase` 访问DBMS通过开放式数据库连接\(odbc\)和该DBMS的ODBC驱动程序。  `CDaoDatabase` 访问数据。数据访问对象基于Microsoft Jet数据库引擎的\(DAO）。  通常，基于DAO的MFC选件类与基于ODBC的MFC选件类能够;基于DAO的选件类可以访问数据访问，包括通过ODBC驱动程序，将它们的数据库引擎。  基于DAO的选件类通过选件类还支持数据定义语言\(DDL\)操作，例如添加表，而不必直接调用DAO。  
  
## 用法  
 当您创建记录集对象时，可以隐式创建数据库对象。  但是，您可以显式创建数据库对象。  若要显式使用现有数据库与 `CDaoDatabase`，请执行下列任一操作:  
  
-   构造 `CDaoDatabase` 对象，将指针传递给打开 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 对象。  
  
-   或者 `CDaoDatabase` 构造对象，而无需指定工作区\(MFC创建一个临时工作区对象）。  
  
 若要创建新的Microsoft Jet \(.MDB\)数据库，请构造 `CDaoDatabase` 对象并调用其 [创建](../Topic/CDaoDatabase::Create.md) 成员函数。  不要在 **Create**之后调用 **Open**。  
  
 若要打开现有的数据库，请构造 `CDaoDatabase` 对象并调用其 [打开](../Topic/CDaoDatabase::Open.md) 成员函数。  
  
 这些技术中的任何一个追加到工作区的数据库集合的DAO数据库对象并打开一个数据连接。  在然后为操作的 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)、 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) 对象处于已连接的数据库时，通过这些对象的构造函数指针到您的 `CDaoDatabase` 对象。  使用完连接后，调用 [关闭](../Topic/CDaoDatabase::Close.md) 成员函数并销毁 `CDaoDatabase` 对象。  **Close** 关闭您以前未关闭的所有记录集。  
  
## 事务  
 数据库执行过程中提供在工作区级别—请参见 [BeginTrans](../Topic/CDaoWorkspace::BeginTrans.md)、 [CommitTrans](../Topic/CDaoWorkspace::CommitTrans.md)和 [回滚](../Topic/CDaoWorkspace::Rollback.md) 选件类 `CDaoWorkspace`的成员函数。  
  
## ODBC 连接  
 建议使用此方法的方式使用ODBC数据源。使用将将外部表与Microsoft Jet \(.MDB\)数据库。  
  
## 集合  
 每个数据库维护其tabledef、querydef、记录集和关系对象自己的集合。  选件类 `CDaoDatabase` 提供操作这些对象的成员函数。  
  
> [!NOTE]
>  对象存储DAO，而不是在MFC数据库对象。  MFC提供选件类tabledef、querydef和记录集对象，但不能参与关系的对象。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoDatabase`  
  
## 要求  
 **Header:** afxdao.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoWorkspace Class](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)   
 [CDaoException Class](../../mfc/reference/cdaoexception-class.md)