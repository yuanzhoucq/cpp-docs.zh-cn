---
title: OLE DB 对象模型
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: 192195d02b034546e50b1cb860b1f11c47dc2b65
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210114"
---
# <a name="ole-db-object-model"></a>OLE DB 对象模型

OLE DB 对象模型由以下对象或组件组成。 列出的前四个对象或组件（数据源、会话、命令和行集）允许您连接到数据源并进行查看。 从访问器开始的其余部分与在显示数据时使用。

## <a name="data-sources"></a>“数据源”

数据源对象使您可以连接到数据源（例如文件或 DBMS）。 数据源对象创建并管理连接并且包含权限和身份验证信息（如登录名和密码）。 数据源对象可以创建一个或多个会话。

## <a name="sessions"></a>会话

会话管理与数据源的特定交互，以便查询和检索数据。 每个会话都是一个事务。 事务是由 ACID 测试定义的不可分工作单元。 有关 ACID 的定义，请参阅[事务](#vcconoledbcomponents_transactions)。

会话执行重要任务，如打开行集和返回创建行集的数据源对象。 会话还可以返回元数据，或者有关数据源本身的信息（例如表信息）。

会话可以创建一个或多个命令。

## <a name="commands"></a>命令

命令执行文本命令，如 SQL 语句。 如果 text 命令指定行集（例如 SQL **SELECT**语句），则该命令将创建行集。

命令只是文本命令的容器，它是从使用者传递到数据源对象的字符串（例如 SQL 语句），由提供程序的基础数据存储区执行。 通常，text 命令是一个 SQL **select**语句（在这种情况下，因为 sql **select**指定了行集，所以该命令会自动创建行集）。

## <a name="rowsets"></a>行集

行集以表格格式显示数据。 索引是行集的一种特殊情况。 可以从会话或命令创建行集。

### <a name="schema-rowsets"></a>架构行集

架构包含有关数据库的元数据（结构信息）。 架构行集是具有架构信息的行集。 一些用于 DBMS 的 OLE DB 提供程序支持架构行集对象。 有关架构行集的详细信息，请参阅[通过架构行集](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)和[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)获取元数据。

### <a name="view-objects"></a>查看对象

视图对象定义行集中的行和列的子集。 它不包含其自身的数据。 视图对象无法合并多个行集中的数据。

## <a name="accessors"></a>Remove

仅 OLE DB 使用访问器的概念。 访问器描述如何将数据存储在使用者中。 它在行集字段（列）与在使用者中声明的数据成员之间具有一组绑定（称为 "列映射"）。

##  <a name="transactions"></a><a name="vcconoledbcomponents_transactions"></a> 中的

当提交或中止非最低级别的嵌套事务时，将使用事务对象。 事务是由 ACID 测试定义的不可分工作单元。 ACID 代表：

- 原子性，不能划分为较小的工作单元

- 并发，一次可以发生多个事务

- 隔离，一个事务对其他

- 持久性，事务进行持久更改

## <a name="enumerators"></a>枚举器

枚举器搜索可用的数据源和其他枚举器。 不是针对特定数据源自定义的使用者使用枚举器搜索要使用的数据源。

在 Microsoft 数据访问 SDK 中随附的根枚举器遍历注册表，查找数据源和其他枚举器。 其他枚举器遍历注册表或以特定于提供程序的方式进行搜索。

## <a name="errors"></a>错误

任何 OLE DB 对象上的任何接口都可能会生成错误。 错误包含有关错误的其他信息，包括可选的自定义错误对象。 此信息存储在 HRESULT 中。

## <a name="notifications"></a>通知

通知由共享行集的协作使用者组使用（其中，共享意味着假设使用者在同一事务中运行）。 通知允许共享行集的协作使用者在其对等方执行的行集上通知相关操作。

## <a name="see-also"></a>另请参阅

[OLE DB 编程](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)
