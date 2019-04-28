---
title: OLE DB 对象模型
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: 303ad4166f0f1126182956fae9c19f513be7cfb3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62283785"
---
# <a name="ole-db-object-model"></a>OLE DB 对象模型

OLE DB 对象模型由以下对象或组件。 第四个对象或列出的组件 （数据源、 会话、 命令和行集） 允许您连接到数据源并查看它。 在显示时使用的数据与其余部分中，从访问器中，开始。

## <a name="data-sources"></a>Data Sources

数据源对象允许您连接到数据源，如文件或 DBMS。 数据源对象创建和管理的连接并包含权限和身份验证信息 （如登录名和密码）。 数据源对象可以创建一个或多个会话。

## <a name="sessions"></a>会话

会话管理与数据源查询和检索数据的特定交互。 每个会话都在单个事务。 事务是 ACID 测试通过定义一个不可分的工作单元。 有关 ACID 的定义，请参阅[事务](#vcconoledbcomponents_transactions)。

会话执行重要任务，例如打开行集和返回数据源对象创建它。 元数据或有关数据源本身 （如表信息） 的信息，还可以返回会话。

会话可以创建一个或多个命令。

## <a name="commands"></a>命令

命令执行文本命令，例如 SQL 语句。 如果文本命令将指定的行集，如 SQL**选择**语句，该命令将创建行集。

命令是只是传递的字符串 （如 SQL 语句） 从使用者到数据源对象执行由提供程序的基础数据存储的文本命令的容器。 通常情况下，文本命令是一个 SQL**选择**语句 (在这种情况下，因为 SQL**选择**指定行集，该命令会自动创建行集)。

## <a name="rowsets"></a>行集

行集以表格格式显示数据。 索引是一种特殊情况的行集。 可以从会话或命令创建行集。

### <a name="schema-rowsets"></a>架构行集合

架构必须具有数据库的元数据 （结构化信息）。 架构行集是具有架构信息的行集。 DBMS 某些 OLE DB 访问接口支持架构行集对象。 有关架构行集的详细信息，请参阅[用架构行集获取元数据](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)并[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)。

### <a name="view-objects"></a>查看对象

视图对象定义的行和列集中的行的子集。 它没有自己的任何数据。 查看对象不能合并来自多个行集的数据。

## <a name="accessors"></a>访问器

仅 OLE DB 使用访问器的概念。 取值函数说明数据使用者中的存储方式。 行集字段 （列） 和数据成员声明中使用者之间，它具有一组绑定 （称为列映射）。

##  <a name="vcconoledbcomponents_transactions"></a> 事务

当提交或中止在非最低级别的嵌套的事务时，需要使用事务对象。 事务是 ACID 测试通过定义一个不可分的工作单元。 ACID 代表：

- 原子性，不能被分成较小的工作单元

- 并发，每次可以进行多个事务

- 隔离，一个事务具有有限的了解由另一个所做的更改

- 持续性，该事务可进行持久更改

## <a name="enumerators"></a>枚举数

枚举器搜索可用的数据源和其他枚举器。 为特定的数据源不自定义的使用者使用枚举器来搜索要使用的数据源。

根枚举器随附在 Microsoft 数据访问 SDK 中，将遍历注册表查找的数据源和其他枚举器。 其他枚举器遍历注册表或搜索提供程序特定的方式。

## <a name="errors"></a>错误

任何 OLE DB 对象上的任何接口可能会产生错误。 错误都有一个错误，包括一个可选的自定义错误对象有关的其他信息。 此信息存储在一个 HRESULT。

## <a name="notifications"></a>通知

通知将使用的共享行集的协同使用者组 （其中共享意味着假定使用者可以在同一事务中运行）。 通知使协同使用者共享行集，以了解有关行集执行其对等方上的操作。

## <a name="see-also"></a>请参阅

[OLE DB 编程](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)