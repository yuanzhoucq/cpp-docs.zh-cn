---
title: "CDatabase Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDatabase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDatabase 类"
  - "数据库类 [C++], ODBC"
  - "数据库连接 [C++], CDatabase 类"
  - "MFC [C++], ODBC"
  - "ODBC [C++], CDatabase 类"
  - "ODBC database class"
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CDatabase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示到数据源的连接，可以对数据源。  
  
## 语法  
  
```  
  
class CDatabase : public CObject  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDatabase::CDatabase](../Topic/CDatabase::CDatabase.md)|构造 `CDatabase` 对象。  必须通过调用 `OpenEx` 或 **Open**初始化对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDatabase::BeginTrans](../Topic/CDatabase::BeginTrans.md)|启动一个“事务” —一系列双面布料调用选件类 `CRecordset` 的 `AddNew`，**Edit**、 **Delete**和 **Update** 成员函数—在该连接的数据源。  数据源必须支持 **BeginTrans** 的事务可以起作用。|  
|[CDatabase::BindParameters](../Topic/CDatabase::BindParameters.md)|允许您为固定参数在调用 `CDatabase::ExecuteSQL`之前。|  
|[CDatabase::Cancel](../Topic/CDatabase::Cancel.md)|取消异步操作或处理从另一个线程。|  
|[CDatabase::CanTransact](../Topic/CDatabase::CanTransact.md)|如果数据源支持事务，返回非零。|  
|[CDatabase::CanUpdate](../Topic/CDatabase::CanUpdate.md)|返回非零，则 `CDatabase` 对象是可更新的\(不是只读的。）|  
|[CDatabase::Close](../Topic/CDatabase::Close.md)|关闭数据源连接。|  
|[CDatabase::CommitTrans](../Topic/CDatabase::CommitTrans.md)|完成 **BeginTrans**启动的事务。  修改数据源在事务的命令执行。|  
|[CDatabase::ExecuteSQL](../Topic/CDatabase::ExecuteSQL.md)|执行SQL语句。  数据记录不返回。|  
|[CDatabase::GetBookmarkPersistence](../Topic/CDatabase::GetBookmarkPersistence.md)|标识书签在记录集对象保持的操作。|  
|[CDatabase::GetConnect](../Topic/CDatabase::GetConnect.md)|返回使用的ODBC连接字符串连接到数据源的 `CDatabase` 对象。|  
|[CDatabase::GetCursorCommitBehavior](../Topic/CDatabase::GetCursorCommitBehavior.md)|标识对事务的影响传递给打开记录集对象。|  
|[CDatabase::GetCursorRollbackBehavior](../Topic/CDatabase::GetCursorRollbackBehavior.md)|标识回滚事务的影响在一个打开的记录集对象。|  
|[CDatabase::GetDatabaseName](../Topic/CDatabase::GetDatabaseName.md)|返回当前使用的数据库的名称。|  
|[CDatabase::IsOpen](../Topic/CDatabase::IsOpen.md)|如果 `CDatabase` 对象当前连接到数据源，返回非零。|  
|[CDatabase::OnSetOptions](../Topic/CDatabase::OnSetOptions.md)|调用由框架设置标准连接选项。  默认实现一组查询超时值。  通过调用 `SetQueryTimeout`提前建立这些选项。|  
|[CDatabase::Open](../Topic/CDatabase::Open.md)|建立到数据源的连接\(通过ODBC驱动程序）。|  
|[CDatabase::OpenEx](../Topic/CDatabase::OpenEx.md)|建立到数据源的连接\(通过ODBC驱动程序）。|  
|[CDatabase::Rollback](../Topic/CDatabase::Rollback.md)|在当前事务提交的撤消更改。  数据源返回到以前的状态，如定义在 **BeginTrans** 调用，不更改。|  
|[CDatabase::SetLoginTimeout](../Topic/CDatabase::SetLoginTimeout.md)|设置秒数，在后数据源连接尝试将超时。|  
|[CDatabase::SetQueryTimeout](../Topic/CDatabase::SetQueryTimeout.md)|设置秒数，在后数据库查询操作将超时。  影响所有后续记录集 **Open**，`AddNew`，**Edit**，并且，**Delete** 调用。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDatabase::m\_hdbc](../Topic/CDatabase::m_hdbc.md)|开放式数据库连接\(odbc\)数据源的连接处理。  键入 **HDBC**。|  
  
## 备注  
 数据源是某个数据库管理系统承载的数据特定实例\(dbms）。  示例包括Microsoft SQL Server、Microsoft Access，Borland dBASE和xBASE。  一次只能有一个或多 `CDatabase` 对象激活在您的应用程序。  
  
> [!NOTE]
>  如果您使用的是数据访问使用否决\(DAO\)选件类而不是开放式数据库连接\(odbc\)选件类，使用选件类 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)。  有关更多信息，请参见文章 [概述:数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
 若要使用 `CDatabase`，请构造 `CDatabase` 对象并调用其 `OpenEx` 成员函数。  这将打开连接。  在然后为操作的 `CRecordset` 对象处于已连接到的数据源时，请通过记录集构造函数指针到您的 `CDatabase` 对象。  使用完连接后，调用 **Close** 成员函数并销毁 `CDatabase` 对象。  **Close** 关闭您以前未关闭的所有记录集。  
  
 有关 `CDatabase`的更多信息，请参见位于 [数据源\(odbc\)](../../data/odbc/data-source-odbc.md) 和 [概述:数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDatabase`  
  
## 要求  
 **Header:** afxdb.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)