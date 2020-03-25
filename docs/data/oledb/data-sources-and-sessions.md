---
title: 数据源和会话
ms.date: 11/19/2018
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
ms.openlocfilehash: 0514f6a9285936c85608f08774c1d377fd72d6ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211050"
---
# <a name="data-sources-and-sessions"></a>数据源和会话

下图显示了支持连接到数据源和访问数据源的类。 每个类都基于标准 OLE DB 组件实现。

![数据源和会话类](../../data/oledb/media/vcdatasourcesessionclasses.gif "数据源和会话类") <br/>
数据源和会话类

类包括：

- [CDataSource](../../data/oledb/cdatasource-class.md)此类实例化数据源对象，该对象通过 OLE DB 提供程序创建和管理到数据源的连接。 数据源以连接字符串的形式获取信息，如数据源地址和身份验证信息。

   还值得注意的是，在建立连接之前经常使用 helper 类[CEnumerator](../../data/oledb/cenumerator-class.md)来获取系统上注册的可用提供程序列表。 这允许您选择作为数据源的提供程序。 例如，"**数据链接属性**" 对话框使用此类在 "**提供程序**" 选项卡上填充提供程序列表。它等同于 `SQLBrowseConnect` 或 `SQLDriverConnect` 函数。

- [CSession](../../data/oledb/csession-class.md)此类实例化 session 对象，该对象表示到数据源的单个访问会话。 但是，可以在一个数据源上创建多个会话。 对于每个会话，可以创建行集、命令和其他对象来访问数据源中的数据。 会话处理事务。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)
