---
title: OLE DB 对象模型
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: b37205eb91317c602010a4b568057845b2345ef0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369797"
---
# <a name="ole-db-object-model"></a>OLE DB 对象模型

OLE DB 对象模型由以下对象或组件组成。 列出的前四个对象或组件（数据源、会话、命令和行集）允许您连接到数据源并查看它。 其余的，从访问器开始，与在显示数据时处理数据有关。

## <a name="data-sources"></a>“数据源”

数据源对象允许您连接到数据源（如文件或 DBMS）。 数据源对象创建和管理连接，并包含权限和身份验证信息（如登录名和密码）。 数据源对象可以创建一个或多个会话。

## <a name="sessions"></a>会话

会话管理与数据源的特定交互以查询和检索数据。 每个会话都是单个事务。 事务是由 ACID 测试定义的不可分割的工作单元。 有关 ACID 的定义，请参阅[事务](#vcconoledbcomponents_transactions)。

会话执行重要任务，如打开行集并返回创建它的数据源对象。 会话还可以返回元数据或有关数据源本身的信息（如表信息）。

会话可以创建一个或多个命令。

## <a name="commands"></a>命令

命令执行文本命令（如 SQL 语句）。 如果文本命令指定行集（如 SQL **SELECT**语句），则该命令将创建行集。

命令只是文本命令的容器，它是从使用者传递到数据源对象的字符串（如 SQL 语句），供提供程序的基础数据存储执行。 通常，文本命令是 SQL **SELECT**语句（在这种情况下，由于 SQL **SELECT**指定了行集，命令会自动创建一个行集）。

## <a name="rowsets"></a>行集

行集以表格格式显示数据。 索引是行集的特殊情况。 可以从会话或命令创建行集。

### <a name="schema-rowsets"></a>架构行集

架构具有有关数据库的元数据（结构信息）。 架构行集是具有架构信息的行集。 DBMS 的某些 OLE DB 提供程序支持架构排组对象。 有关架构行集的详细信息，请参阅[使用架构行集](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)和[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)获取元数据。

### <a name="view-objects"></a>查看对象

视图对象定义行集中的行和列的子集。 它没有自己的数据。 视图对象无法合并来自多个行集的数据。

## <a name="accessors"></a>访问器

只有 OLE DB 使用访问器的概念。 访问器描述数据在使用者中的存储方式。 它在行集字段（列）和在使用者中声明的数据成员之间具有一组绑定（称为列映射）。

## <a name="transactions"></a><a name="vcconoledbcomponents_transactions"></a>交易

在以最低级别以外的其他级别提交或中止嵌套事务时，将使用事务对象。 事务是由 ACID 测试定义的不可分割的工作单元。 ACID 代表：

- 原子性，不能分为较小的工作单元

- 并发，一次可以发生多个事务

- 隔离，一个事务对另一个事务所做的更改了解有限

- 持久性，事务进行持续更改

## <a name="enumerators"></a>枚举器

枚举器搜索可用的数据源和其他枚举器。 未为特定数据源自定义的使用者使用枚举器搜索要使用的数据源。

在 Microsoft 数据访问 SDK 中附带的根枚举器将遍历注册表，查找数据源和其他枚举器。 其他枚举者遍历注册表或以特定于提供程序的方式进行搜索。

## <a name="errors"></a>错误

任何 OLE DB 对象上的任何接口都可能产生错误。 错误包含有关错误的其他信息，包括可选的自定义错误对象。 此信息存储在 HRESULT 中。

## <a name="notifications"></a>通知

共享行集的合作使用者组使用通知（其中共享意味着假定使用者在同一事务中工作）。 通知使共享行集的协作使用者能够了解其对等方执行的行集上的操作。

## <a name="see-also"></a>另请参阅

[OLE DB 编程](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)
