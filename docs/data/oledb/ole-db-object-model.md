---
title: OLE DB 对象模型 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ba9fd9b7ba5503f6ed5e1837147524f5abc7c31b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="ole-db-object-model"></a>OLE DB 对象模型
OLE DB 对象模型包含下列对象或组件。 第一个四个对象或列出的组件 （数据源、 会话、 命令和行集），可以连接到数据源并查看它。 与显示时使用的数据相关的其余部分，从访问器中，开始。  
  
## <a name="data-sources"></a>数据源  
 数据源对象，可以连接到数据源，如文件或 DBMS。 数据源对象创建和管理的连接并包含权限和身份验证信息 （如登录名和密码）。 数据源对象可以创建一个或多个会话。  
  
## <a name="sessions"></a>会话  
 会话管理与数据源以便查询和检索数据的特定交互。 每个会话就是一个事务。 事务是由 ACID 测试定义不可分的工作单元。 ACID 的定义，请参阅[事务](#vcconoledbcomponents_transactions)。  
  
 会话执行重要任务，例如打开行集合并返回创建它的数据源对象。 元数据或有关数据源本身 （例如表信息） 的信息，还可以返回会话。  
  
 会话可以创建一个或多个命令。  
  
## <a name="commands"></a>命令  
 命令执行文本命令，如 SQL 语句。 如果文本命令指定的行集，如 SQL**选择**语句，该命令将创建行集。  
  
 命令仅仅是一个容器，文本命令，这是自传递使用者至数据源对象执行由提供程序的基础数据存储区 （如 SQL 语句） 的字符串。 通常情况下，文本命令是一个 SQL**选择**语句 (在这种情况下，因为 SQL**选择**指定行集，该命令将自动创建一个行集)。  
  
## <a name="rowsets"></a>行集  
 行集公开表格格式的数据。 索引是一种特殊情况的行集。 你可以从会话或命令创建行集。  
  
### <a name="schema-rowsets"></a>架构行集合  
 架构包含数据库的元数据 （结构化信息）。 架构行集是包含架构信息的行集。 某些 OLE DB 提供程序 DBMS 支持架构行集对象。 有关架构行集的详细信息，请参阅[用架构行集合获取元数据](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)和[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)。  
  
### <a name="view-objects"></a>视图对象  
 视图对象定义的行和从行集中的列的子集。 它包含任何数据。 视图对象不能合并来自多个行集的数据。  
  
## <a name="accessors"></a>访问器  
 仅 OLE DB 使用访问器的概念。 访问器中描述如何将数据存储在使用者。 它包含行集字段 （列） 和您在使用者中声明的数据成员之间的一组 （称为列映射） 的绑定。  
  
##  <a name="vcconoledbcomponents_transactions"></a> 事务  
 当提交或中止在非最低级别的嵌套的事务时，需要使用事务对象。 事务是由 ACID 测试定义不可分的工作单元。 ACID 代表：  
  
-   原子性： 不能划分为较小工作单元。  
  
-   并发： 多个事务可一次。  
  
-   隔离： 一个事务具有有限的了解由另一个进行的更改。  
  
-   持续性： 事务进行永久更改。  
  
## <a name="enumerators"></a>枚举数  
 枚举器搜索可用数据源和其他枚举器。 没有为特定数据源的自定义的使用者使用枚举器来搜索要使用的数据源。  
  
 在 Microsoft 数据访问 SDK 中提供的根枚举器遍历注册表中查找数据源和其他枚举器。 其他枚举器遍历注册表或搜索以提供程序特定的方式。  
  
## <a name="errors"></a>错误  
 在任何 OLE DB 对象上的任何接口可以生成错误。 错误包含有关错误，包括可选的自定义错误对象的其他信息。 此信息包含在一个 HRESULT。  
  
## <a name="notifications"></a>通知  
 通知使用 （其中共享意味着，使用者都被认为在同一事务中工作） 的共享行集的协同使用者组。 通知使协同使用者共享行集，以了解有关行集执行其对等方上的操作。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 编程](../../data/oledb/ole-db-programming.md)   
 [OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)