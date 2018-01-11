---
title: "OLE DB 提供程序模板 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f95b32d62d964c83853025ed4e4af9b90e7a630a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ole-db-provider-templates-c"></a>OLE DB 提供程序模板 (C++)
OLE DB 是 Microsoft 通用数据访问策略的一个重要部分。 OLE DB 设计允许来自任何数据源的高性能的数据访问。 任何表格数据将可查看通过 OLE DB 而不考虑它是否来自一个数据库。 此灵活性带给极大的方便。  
  
 中所述[OLE DB 使用者和提供程序](../../data/oledb/ole-db-consumers-and-providers.md)，OLE DB 使用使用者和提供程序的概念。 使用者发出请求的数据;该提供程序向使用者以表格格式返回数据。 从编程角度看，此模型最重要含意为提供程序必须实现任何使用者可以进行的调用。  
  
## <a name="what-is-a-provider"></a>一个提供程序是什么？  
 OLE DB 提供程序是为使用者对象的接口调用服务的 COM 对象的一组将以表格格式的数据从持久 （称为数据存储区） 的源传输到使用者。  
  
 提供程序可以简单或复杂。 提供程序可以通过实现更多的接口来支持最少的功能或全面的生产质量提供程序。 一个提供程序可以返回一个表，允许客户端确定该表的格式并对该数据执行操作。  
  
 每个提供程序实现一组标准的 COM 对象以处理来自客户端，与标准的含义的请求任何 OLE DB 使用者可以从任何提供程序，而不考虑 （例如 c + + 和基本） 的语言中访问数据。  
  
 每个 COM 对象包含多个接口，其中一些是必需的其中一些是可选的。 通过实现必需的接口，提供程序可保证最低任何的级别客户端应该能够使用的功能 （称为遵从性）。 一个提供程序可以实现可选的接口来提供其他功能。 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)描述这些接口的详细信息。 客户端应始终调用`QueryInterface`来判断提供程序是否支持给定的接口。  
  
## <a name="ole-db-specification-level-support"></a>OLE DB 规范级别支持  
 OLE DB 提供程序模板支持 OLE DB 版本 2.7 规范。 使用 OLE DB 提供程序模板，你可以实现级别 0 符合提供程序。 提供程序示例中，例如，使用模板来实现执行 DOS DIR 命令以在文件系统中查询的 non-MS-DOS 命令服务器。 提供程序示例在行集中，它是用于返回表格数据的标准 OLE DB 机制返回的目录信息。  
  
 最简单的提供程序支持的 OLE DB 模板类型是具有任何命令的只读提供程序。 此外支持通过命令使用提供程序，如是书签和读/写功能。 可以通过编写附加代码来实现读/写提供程序。 当前版本不支持动态行集和事务，但如果你希望可以将它们添加。  
  
## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>需要时创建的 OLE DB 提供程序？  
 你并不始终需要创建自己的提供程序;Microsoft 提供了多个中的预打包、 标准提供商**数据链接属性**Visual c + + 中的对话框。 若要创建的 OLE DB 提供程序的主要原因是利用通用数据访问策略。 因此是一些这样做的优点：  
  
-   通过 c + +、 Basic 和 Visual Basic Scripting Edition 如任何语言中访问数据。 它允许你的组织中的不同程序员可以访问相同的数据相同的方式，而不考虑它们使用哪种语言。  
  
-   公开你的数据与其他数据源，例如 SQL Server、 Excel 和访问。 这可能非常有用，如果你想要不同的格式之间传输数据。  
  
-   在参与跨数据源 （异类） 操作。 这可以是数据仓库的非常有效的方法。 通过使用 OLE DB 提供程序，可以将数据保留在其本机格式，并仍将能够访问在简单的操作。  
  
-   将其他功能添加到你的数据，例如查询处理。  
  
-   增加的访问数据时，控制如何操作的性能。  
  
-   提高可靠性。 如果你具有专有数据格式只能由一个程序员可以访问，您就处于风险。 使用 OLE DB 提供程序，你可以向所有程序员打开该专有格式。  
  
## <a name="read-only-and-updatable-providers"></a>只读的和可更新提供程序  
 提供程序可以大不相同复杂性和功能。 它可用于将提供程序分为只读提供程序和可更新提供程序：  
  
-   Visual c + + 6.0 支持仅只读提供程序。 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)讨论如何创建只读提供程序。  
  
-   Visual c + + 支持可更新提供程序，可以更新 （写入） 数据存储区。 有关可更新提供程序的信息，请参阅[创建可更新提供程序](../../data/oledb/creating-an-updatable-provider.md); [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)示例是一种可更新的提供程序。  
  
 有关详细信息，请参见:  
  
-   [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)  
  
-   [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)  
  
-   [OLE DB 编程](../../data/oledb/ole-db-programming.md)  
  
## <a name="see-also"></a>请参阅  
 [数据访问](../data-access-in-cpp.md)   
 [OLE DB SDK 文档](https://msdn.microsoft.com/en-us/library/ms722784.aspx)   
 [OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)