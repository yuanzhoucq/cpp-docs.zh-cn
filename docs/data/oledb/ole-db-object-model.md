---
title: "OLE DB 对象模型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB, 对象模型"
  - "行集合, OLE DB 对象模型"
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 对象模型
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 对象模型包含以下对象或组件。  所列的前四个对象或组件（数据源、会话、命令和行集合）使用户能够连接到数据源并查看该数据源。  从访问器开始的其余对象或组件用于当数据显示后处理数据。  
  
## 数据源  
 数据源对象使用户能够连接到数据源，例如一个文件或一个 DBMS。  数据源对象创建并管理该连接，并且包含权限和身份验证信息（例如登录名和密码）。  一个数据源对象可创建一个或多个会话。  
  
## 会话  
 会话管理与数据源进行的特定交互，以便查询和检索数据。  一个会话就是一个事务。  事务是由 ACID 测试定义的不可分工作单元。  有关 ACID 的定义，请参见[事务](#vcconoledbcomponents_transactions)。  
  
 会话执行一些重要的任务，例如打开行集合和返回创建会话的数据源对象。  会话也能返回元数据，或者关于数据源本身的信息（例如表信息）。  
  
 会话可创建一个或多个命令。  
  
## 命令  
 命令执行文本命令，例如 SQL 语句。  如果文本命令指定某一行集合，例如一个 SQL **SELECT** 语句，则该命令创建该行集合。  
  
 命令只是文本命令的容器，文本命令是自使用者传递至数据源对象用以由提供程序的基础数据存储所执行的字符串（例如 SQL 语句）。  通常，文本命令是一个 SQL **SELECT** 语句（在此情况下，因为 SQL **SELECT** 语句指定一个行集合，所以命令自动创建行集合）。  
  
## 行集合  
 行集合以表格格式公开数据。  索引是行集合的一种特例。  行集合可通过会话或命令创建。  
  
### 架构行集合  
 架构包含有数据库的元数据（结构信息）。  架构行集合是包含有架构信息的行集合。  一些用于 DBMS 的 OLE DB 提供程序支持架构行集合对象。  有关架构行集的更多信息，请参见[用架构行集合获取元数据](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)和[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)。  
  
### 查看对象  
 查看对象定义行集合中的行和列的子集。  它自己并不包含数据。  查看对象不能合并多个行集合中的数据。  
  
## 访问器  
 只有 OLE DB 使用访问器这一概念。  访问器描述数据在使用者中的存储方式。  它包含有行集合字段（列）和用户在使用者中声明的数据成员之间的一组绑定（称为列映射）。  
  
##  <a name="vcconoledbcomponents_transactions"></a> 事务  
 当从非最低级别提交或终止嵌套事务时，需要使用事务对象。  事务是由 ACID 测试定义的不可分工作单元。  ACID 代表：  
  
-   原子性：不能被分成更小的工作单元。  
  
-   并发：每次可以发生一个以上的事务。  
  
-   隔离：对于一个事务所作的更改，另一个事务只有有限的了解。  
  
-   持久性：事务可进行持久更改。  
  
## 枚举数  
 枚举数搜索可用数据源和其他枚举数。  不是为某一特定数据源自定义的使用者使用枚举数来搜索要使用的数据源。  
  
 Microsoft 数据访问 SDK 中提供的根枚举数遍历注册表查找数据源和其他枚举数。  其他枚举数遍历注册表，或者以提供程序特定的方式进行搜索。  
  
## 错误  
 任何 OLE DB 对象中的任何接口都可能会生成错误。  错误包含关于错误的附加信息，包括一个可选自定义错误对象。  该信息包含于 HRESULT 中。  
  
## 通知  
 通知由共享某一行集合的合作使用者组使用（“共享”此处意指使用者被假定在同一事务内工作）。  通知使得共享某一行集合的合作使用者能够知道对等方对行集合所执行的操作。  
  
## 请参阅  
 [OLE DB 编程](../../data/oledb/ole-db-programming.md)   
 [OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)