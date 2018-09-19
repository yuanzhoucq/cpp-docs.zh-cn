---
title: 数据源和会话 |Microsoft Docs
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
ms.openlocfilehash: 07c7a395f111d4473eed5f85a1329e85358f5d0c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037666"
---
# <a name="data-sources-and-sessions"></a>数据源和会话

下图显示了支持连接到和访问数据源的类。 每个类基于标准的 OLE DB 组件实现。  
  
![数据源和会话类](../../data/oledb/media/vcdatasourcesessionclasses.gif "vcdatasourcesessionclasses")  
数据源和会话类  
  
类是：  
  
- [CDataSource](../../data/oledb/cdatasource-class.md)此类实例化数据源对象，它用于创建和管理与通过 OLE DB 访问接口的数据源的连接。 数据源将连接字符串的窗体中的数据源地址和身份验证信息等信息。  
  
     它也是值得注意的是，帮助器类[CEnumerator](../../data/oledb/cenumerator-class.md)常用才能建立任何连接，以获取可用的系统上注册的提供程序的列表。 这可以作为数据源选择一个提供程序。 例如，**数据链接属性**对话框中使用此类上填充的提供程序列表**提供程序**选项卡。它等效于`SQLBrowseConnect`或`SQLDriverConnect`函数。  
  
- [CSession](../../data/oledb/csession-class.md)此类实例化到数据源表示单个访问会话的会话对象。 但是，可以在数据源上创建多个会话。 对于每个会话，可以创建行集、 命令和其他对象，若要从数据源访问数据。 该会话处理事务。  
  
## <a name="see-also"></a>请参阅  

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)