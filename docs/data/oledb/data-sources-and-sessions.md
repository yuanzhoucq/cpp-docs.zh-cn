---
title: "数据源和会话 | Microsoft Docs"
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
  - "连接 [C++], 数据源"
  - "数据源 [C++], OLE DB"
  - "OLE DB 使用者模板 [C++], 数据源"
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 数据源和会话
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下图显示支持连接和访问数据源的类。  每个类都基于标准 OLE DB 组件实现。  
  
 ![数据源和会话类](../../data/oledb/media/vcdatasourcesessionclasses.png "vcDataSourceSessionClasses")  
数据源和会话类  
  
 这些类包括：  
  
-   [CDataSource](../../data/oledb/cdatasource-class.md) 此类实例化数据源对象，该对象通过 OLE DB 提供程序创建和管理与数据源的连接。  数据源以连接字符串的形式保持数据源地址和身份验证信息等信息。  
  
     另外值得注意的是，在建立任何连接之前通常使用 Helper 类 [CEnumerator](../../data/oledb/cenumerator-class.md) 来获取系统中注册的可用提供程序列表。  这使您可以选择一个提供程序作为数据源。  例如，**“数据链接属性”**对话框使用此类填充**“提供程序”**选项卡中的提供程序列表。  它等效于 **SQLBrowseConnect** 或 **SQLDriverConnect** 函数。  
  
-   [CSession](../../data/oledb/csession-class.md) 此类实例化会话对象，该对象表示与数据源的单个访问会话。  但也可以在一个数据源上创建多个会话。  对于每个会话，可以创建行集合、命令和其他对象以访问数据源中的数据。  会话负责处理事务。  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)