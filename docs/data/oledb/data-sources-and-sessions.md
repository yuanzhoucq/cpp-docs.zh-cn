---
title: 数据源和会话 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d93f6aba8e9fad27054c731d37e6df28b54eacda
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="data-sources-and-sessions"></a>数据源和会话
下图显示支持连接到和访问数据源的类。 每个类基于标准的 OLE DB 组件实现。  
  
 ![数据源和会话类](../../data/oledb/media/vcdatasourcesessionclasses.gif "vcdatasourcesessionclasses")  
数据源和会话类  
  
 类如下：  
  
-   [CDataSource](../../data/oledb/cdatasource-class.md)此类实例化的数据源对象，用于创建和管理与通过 OLE DB 访问接口的数据源的连接。 数据源采用如连接字符串的窗体中的数据源地址和身份验证信息的信息。  
  
     它也是值得注意的帮助器类[CEnumerator](../../data/oledb/cenumerator-class.md)常用之前建立任何连接以获取可用的系统上注册的提供程序的列表。 这可以作为数据源选择一个提供程序。 例如，**数据链接属性**对话框使用此类来填充的提供程序列表上**提供程序**选项卡。它相当于**SQLBrowseConnect**或**SQLDriverConnect**函数。  
  
-   [CSession](../../data/oledb/csession-class.md)此类实例化到数据源表示单个访问会话的会话对象。 但是，你可以在数据源上创建多个会话。 对于每个会话中，你可以创建行集、 命令和其他对象，若要从数据源访问数据。 会话处理事务。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)