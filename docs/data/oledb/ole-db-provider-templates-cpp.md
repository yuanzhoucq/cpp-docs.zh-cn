---
title: "OLE DB 提供程序模板 (C++) | Microsoft Docs"
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
  - "数据库 [C++], OLE DB 模板"
  - "OLE DB 提供程序模板 [C++], 关于 OLE DB 提供程序模板"
  - "OLE DB 提供程序 [C++], 关于提供程序"
  - "模板 [C++], OLE DB"
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 提供程序模板 (C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 是 Microsoft 的通用数据访问策略的重要组成部分。  OLE DB 设计允许来自任何数据源的高性能数据访问。  不论是否来自数据库，任何表格数据都可以通过 OLE DB 查看。  此灵活性带给您极大的方便。  
  
 正如 [OLE DB 使用者和提供程序](../../data/oledb/ole-db-consumers-and-providers.md)中的解释，OLE DB 使用使用者和提供程序的概念。  使用者发出数据请求；提供程序将数据以表格格式返回给使用者。  从编程角度讲，此模型最重要的含义是提供程序必须实现使用者可以进行的任何调用。  
  
## 什么是提供程序？  
 OLE DB 提供程序是一组为来自使用者对象的接口调用服务的 COM 对象，它将数据以表格格式从持久的源（称为数据存储区）传输给使用者。  
  
 提供程序可以是简单的，也可以是复杂的。  提供程序可以支持最小数量的功能，也可以通过实现更多的接口来支持全面的生产品质提供程序。  提供程序可以返回一个表，它允许客户端确定该表的格式，并对那些数据执行操作。  
  
 每个提供程序均实现一组标准的 COM 对象以处理来自客户端的请求，具有任何 OLE DB 使用者都可以访问来自任何提供程序的数据的标准含义，与语言（例如 C\+\+ 和 Basic）无关。  
  
 每个 COM 对象都包含若干接口，这些接口有些是必选的，有些是可选的。  通过实现强制接口，提供程序保证任何客户端都应该能够使用的最低功能级别（称为遵从性）。  提供程序可以实现可选接口来提供附加功能。  [OLE DB 提供程序模板结构](../../data/oledb/ole-db-provider-template-architecture.md)详细描述了这些接口。  客户端应始终调用 `QueryInterface` 来确定提供程序是否支持给定的接口。  
  
## OLE DB 规范级别支持  
 OLE DB 提供程序模板支持 OLE DB 2.7 版规范。  使用 OLE DB 提供程序模板，可以实现符合级别 0 的提供程序。  例如，提供程序示例使用模板实现一个非 SQL \(MS\-DOS\) 命令服务器，该服务器执行 DOS DIR 命令来查询文件系统。  提供程序示例在行集合中返回目录信息，而行集合是返回表格数据的标准 OLE DB 机制。  
  
 OLE DB 模板支持的最简单提供程序类型是不带命令的只读提供程序。  带命令的提供程序也受支持，书签和读\/写功能同样受支持。  可以通过编写附加的代码来实现读\/写提供程序。  动态行集合和事务不受当前版本的支持，但如果需要可以添加它们。  
  
## 何时需要创建 OLE DB 提供程序？  
 并不是始终需要创建自己的提供程序；在 Visual C\+\+ 中，Microsoft 在**“数据链接属性”**对话框中提供了若干预封装的标准提供程序。  创建 OLE DB 提供程序的主要原因是利用通用数据访问策略。  这样做的一些优点是：  
  
-   通过任何语言（如 C\+\+、Basic、Visual Basic Scripting Edition）访问数据。  这使组织中的不同程序员得以用相同的方法访问相同的数据，不论他们使用的语言是什么。  
  
-   向其他数据源（如 SQL Server、Excel、Access）公开数据。  如果要在不同的格式间传输数据，这会很有用。  
  
-   参与跨数据源（异类）操作。  这可以成为将数据送入库的非常有效的方法。  通过使用 OLE DB 提供程序，可以将数据保持为本机格式并在简单操作中仍然能够访问它。  
  
-   向数据添加附加功能，如查询处理。  
  
-   通过控制如何操作数据，提高数据访问性能。  
  
-   提高可靠性。  如果您的专用数据格式只能由一个程序员访问，这是危险的。  使用 OLE DB 提供程序，可以向所有程序员公开此专用格式。  
  
## 只读和可更新的提供程序  
 不同的提供程序之间复杂性和功能可能会相差很大。  将提供程序分为只读提供程序和可更新的提供程序很有用：  
  
-   Visual C\+\+ 6.0 只支持只读提供程序。  [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)讨论如何创建只读提供程序。  
  
-   Visual C\+\+ .NET 支持可更新的提供程序，这些提供程序可以更新（写入）数据存储区。  有关可更新的提供程序的信息，请参见 [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)；[UpdatePV](http://msdn.microsoft.com/zh-cn/c8bed873-223c-4a7d-af55-f90138c6f38f) 示例是可更新的提供程序的一个示例。  
  
 有关详细信息，请参阅：  
  
-   [OLE DB 提供程序模板结构](../../data/oledb/ole-db-provider-template-architecture.md)  
  
-   [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)  
  
-   [OLE DB 编程](../../data/oledb/ole-db-programming.md)  
  
## 请参阅  
 [数据访问](../Topic/Data%20Access%20in%20Visual%20C++.md)   
 [OLE DB SDK 文档](https://msdn.microsoft.com/en-us/library/ms722784.aspx)   
 [OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)