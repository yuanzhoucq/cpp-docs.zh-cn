---
title: "CDaoWorkspace Class | Microsoft Docs"
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
  - "CDaoWorkspace"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoWorkspace class"
  - "DAO workspaces [C++]"
  - "DAO workspaces [C++], CDaoWorkspace class"
  - "database engine [C++], accessing via workspace"
  - "DDLs [C++]"
  - "default workspaces [C++]"
  - "default workspaces [C++], DAO"
  - "默认值 [C++], 工作区"
  - "ODBC 类 [C++], vs. DAO classes"
  - "persistence [C++], DAO workspace"
  - "security [MFC]"
  - "security [MFC], DAO workspaces"
  - "sessions [C++], DAO workspace"
  - "transaction spaces [C++]"
  - "transaction spaces [C++], DAO workspace"
  - "Workspace class"
  - "workspaces [C++], DAO"
  - "workspaces [C++], default"
  - "workspaces [C++], interface to database engine"
  - "workspaces [C++], 持久性"
  - "Workspaces collection"
ms.assetid: 64f60de6-4df1-4d4a-a65b-c489b5257d52
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoWorkspace Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理从登录的命名，密码保护的数据库会话注销，由单个用户。  
  
## 语法  
  
```  
class CDaoWorkspace : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDaoWorkspace::CDaoWorkspace](../Topic/CDaoWorkspace::CDaoWorkspace.md)|构造工作区对象。  之后，调用 **Create** 或 **Open**。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDaoWorkspace::Append](../Topic/CDaoWorkspace::Append.md)|追加新创建的工作区到数据库引擎的工作区集合。|  
|[CDaoWorkspace::BeginTrans](../Topic/CDaoWorkspace::BeginTrans.md)|开始新事务，适用于所有数据库中打开的工作区。|  
|[CDaoWorkspace::Close](../Topic/CDaoWorkspace::Close.md)|关闭它包含的工作区和所有对象。  等待事务回滚。|  
|[CDaoWorkspace::CommitTrans](../Topic/CDaoWorkspace::CommitTrans.md)|完成当前事务并保存更改。|  
|[CDaoWorkspace::CompactDatabase](../Topic/CDaoWorkspace::CompactDatabase.md)|压缩\(或重复\)数据库。|  
|[CDaoWorkspace::Create](../Topic/CDaoWorkspace::Create.md)|创建新的DAO工作区对象。|  
|[CDaoWorkspace::GetDatabaseCount](../Topic/CDaoWorkspace::GetDatabaseCount.md)|返回DAO在工作区中的数据库集合的数据库对象数目。|  
|[CDaoWorkspace::GetDatabaseInfo](../Topic/CDaoWorkspace::GetDatabaseInfo.md)|返回有关在工作区中的数据库集合定义的指定DAO数据库的信息。|  
|[CDaoWorkspace::GetIniPath](../Topic/CDaoWorkspace::GetIniPath.md)|返回Microsoft Jet数据库引擎的初始化设置的位置在Windows注册表中。|  
|[CDaoWorkspace::GetIsolateODBCTrans](../Topic/CDaoWorkspace::GetIsolateODBCTrans.md)|返回一个值是否涉及同一ODBC数据源通过与数据源的强制的多个连接独立多个事务。|  
|[CDaoWorkspace::GetLoginTimeout](../Topic/CDaoWorkspace::GetLoginTimeout.md)|返回秒数，在错误之前，当用户尝试登录到ODBC数据库时。|  
|[CDaoWorkspace::GetName](../Topic/CDaoWorkspace::GetName.md)|返回用户定义名称工作区对象。|  
|[CDaoWorkspace::GetUserName](../Topic/CDaoWorkspace::GetUserName.md)|在工作区中创建的，返回指定的用户名。  这是工作区的所有者名称。|  
|[CDaoWorkspace::GetVersion](../Topic/CDaoWorkspace::GetVersion.md)|返回包含数据库引擎的版本与工作区的字符串。|  
|[CDaoWorkspace::GetWorkspaceCount](../Topic/CDaoWorkspace::GetWorkspaceCount.md)|返回DAO在数据库引擎的工作区集合的工作区的对象的数目。|  
|[CDaoWorkspace::GetWorkspaceInfo](../Topic/CDaoWorkspace::GetWorkspaceInfo.md)|返回有关数据库引擎的工作区集合定义的指定DAO工作区的信息。|  
|[CDaoWorkspace::Idle](../Topic/CDaoWorkspace::Idle.md)|授予数据库引擎执行后台任务。|  
|[CDaoWorkspace::IsOpen](../Topic/CDaoWorkspace::IsOpen.md)|如果工作区处于打开状态，返回非零。|  
|[CDaoWorkspace::Open](../Topic/CDaoWorkspace::Open.md)|显式打开工作区对象与DAO的默认工作区。|  
|[CDaoWorkspace::RepairDatabase](../Topic/CDaoWorkspace::RepairDatabase.md)|尝试修复一个损坏的数据库。|  
|[CDaoWorkspace::Rollback](../Topic/CDaoWorkspace::Rollback.md)|关闭当前事务，不保存更改。|  
|[CDaoWorkspace::SetDefaultPassword](../Topic/CDaoWorkspace::SetDefaultPassword.md)|为数据库引擎使用的密码工作区对象时创建的，而不用特定密码。|  
|[CDaoWorkspace::SetDefaultUser](../Topic/CDaoWorkspace::SetDefaultUser.md)|为数据库引擎使用的用户名工作区对象时创建的，而不用特定用户名。|  
|[CDaoWorkspace::SetIniPath](../Topic/CDaoWorkspace::SetIniPath.md)|设置Microsoft Jet数据库引擎的初始化设置的位置在Windows注册表中。|  
|[CDaoWorkspace::SetIsolateODBCTrans](../Topic/CDaoWorkspace::SetIsolateODBCTrans.md)|指定涉及同一ODBC数据源的多个事务是否通过强制与数据源的多个连接隔离。|  
|[CDaoWorkspace::SetLoginTimeout](../Topic/CDaoWorkspace::SetLoginTimeout.md)|设置秒数，在错误之前，当用户尝试登录到ODBC数据源时。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDaoWorkspace::m\_pDAOWorkspace](../Topic/CDaoWorkspace::m_pDAOWorkspace.md)|指向基础DAO工作区对象。|  
  
## 备注  
 在大多数情况下，不需要多个工作区，因此，您不需要显式创建工作区对象;在打开数据库和记录集对象时，它们使用DAO的默认工作区。  但是，如果需要，可以同时对多个会话由创建的其他工作区对象来运行。  每个工作区对象可以在自己的数据库集合包含多个打开的数据库对象。  在MFC中，工作区是主事务管理器，指定设置打开数据库都在同一个“事务空间”。  
  
> [!NOTE]
>  DAO数据库选件类根据了开放式数据库连接的MFC数据库选件类都一目了然\(odbc）。  所有DAO数据库类名具有“CDao”前缀。  通常，基于DAO的MFC选件类与基于ODBC的MFC选件类能够。  基于DAO的选件类访问数据。Microsoft Jet数据库引擎，包括ODBC驱动程序。  通过选件类还支持数据定义语言\(DDL\)操作，例如创建数据库并添加表和字段，而不必直接调用DAO。  
  
## 功能  
 选件类 `CDaoWorkspace` 提供以下内容:  
  
-   显式访问，如果需要，对默认工作区，创建通过初始化数据库引擎。  通常使用DAO的默认工作区隐式通过创建数据库和记录集对象。  
  
-   事务适用于所有数据库已经在工作区的事务空间。  可以创建其他的工作区管理单独的事务空间。  
  
-   对于基础Microsoft Jet数据库引擎的许多属性的接口\(请参见静态成员函数）。  打开或创建工作区或调用静态成员函数，开始之前或创建，初始化数据库引擎。  
  
-   对数据库引擎的工作区集合的访问，存储所有活动工作区追加到它。  也可以创建和使用工作区时，不会将它们追加到集合。  
  
## 安全性  
 MFC不实现DAO的用户和组集合，为安全控件。  如果需要DAO的某些方面，必须自行通过直接调用DAO接口的程序。  有关信息，请参见 [技术说明54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
## 用法  
 可以使用选件类 `CDaoWorkspace` :  
  
-   请显式打开默认工作区。  
  
     —通常，当您打开一个新的 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 对象时，对默认工作区的使用是隐式的。  例如，但您可能需要显式地需要访问它\)，访问数据库引擎属性或工作区集合。  请参见的“对默认工作区的隐式使用” cookie。  
  
-   创建新工作区。  如果要添加到工作区集合，请调用 [追加](../Topic/CDaoWorkspace::Append.md)。  
  
-   打开工作区集合的现有工作区。  
  
 创建已不存在工作区集合的新工作区中介绍 [创建](../Topic/CDaoWorkspace::Create.md) 成员函数下。  工作区对象无论如何不会在datababase引擎的会话之间保持。  如果您的应用程序链接MFC静态，关闭应用程序uninitializes数据库引擎。  如果您的MFC的应用程序动态链接，数据库引擎未初始化，虽然MFC DLL卸载。  
  
 显式打开默认工作区或打开现有工作区在工作区集合，描述在 [打开](../Topic/CDaoWorkspace::Open.md) 成员函数下。  
  
 通过关闭已 [关闭](../Topic/CDaoWorkspace::Close.md) 成员函数的工作区关闭工作区会话。  **Close** 关闭您以前未关闭的所有数据库，回滚任何未提交的事务。  
  
## 事务  
 DAO管理事务在工作区级别;因此，在工作区的事务有多个打开的数据库的应用于所有数据库。  例如，因此，如果两个数据库允许未提交更新和您调用 [CommitTrans](../Topic/CDaoWorkspace::CommitTrans.md)，所有更新。  如果希望限制事务到一个数据库，不需要单独的工作区对象。  
  
## 为默认工作区的隐式使用  
 MFC使用DAO的默认工作区隐式在以下情况下:  
  
-   如果创建新 `CDaoDatabase` 对象，但通过现有 `CDaoWorkspace` 对象不这样做，MFC创建自己的临时工作区对象，对应于DAO的默认工作区。  如果有多个数据库这样做，所有数据库对象与默认工作区。  通过 `CDaoDatabase` 数据成员可以访问数据库的工作区。  
  
-   同样，因此，如果创建一 `CDaoRecordset` 对象，而无需提供指向 `CDaoDatabase` 对象，MFC通过扩展创建一个临时数据库对象，然后，在中，临时工作区对象。  通过 `CDaoRecordset` 数据成员可以访问记录集的数据库和间接其工作区。  
  
## 其他操作  
 其他数据库操作还提供，如修复一个损坏的数据库或压缩数据库。  
  
 有关直接调用DAO的信息以及有关DAO安全，请参见 [技术说明54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoWorkspace`  
  
## 要求  
 **Header:** afxdao.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoException Class](../../mfc/reference/cdaoexception-class.md)