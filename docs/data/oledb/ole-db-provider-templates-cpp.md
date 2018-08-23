---
title: OLE DB 提供程序模板 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4983234cdbc64f4ca8364c5afcc2d8e735ba2d01
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572132"
---
# <a name="ole-db-provider-templates-c"></a>OLE DB 提供程序模板 (C++)
OLE DB 是 Microsoft 通用数据访问策略的一个重要部分。 OLE DB 设计允许来自任何数据源的高性能的数据访问。 可通过 OLE DB 而不考虑它是否由数据库查看任何表格数据。 灵活地提供了极大的方便。  
  
 中所述[OLE DB 使用者和提供程序](../../data/oledb/ole-db-consumers-and-providers.md)，OLE DB 使用使用者和提供程序的概念。 使用者发出数据; 的请求提供程序向使用者以表格格式返回数据。 从编程的角度来看，此模型的最重要含义是提供程序必须实现任何使用者可以进行的调用。  
  
## <a name="what-is-a-provider"></a>一个提供程序是什么？  
 OLE DB 访问接口是为使用者对象的接口调用服务的 COM 对象的一组将以表格格式数据从持久性源 （称为数据存储区） 传输到使用者。  
  
 提供程序可以是简单或复杂。 提供程序可以通过实现更多的接口来支持最少量的功能或成熟的生产质量提供程序。 提供程序可以返回一个表，允许客户端确定该表的格式并对该数据执行操作。  
  
 每个提供程序实现一组标准的 COM 对象以处理来自客户端，与标准的含义的请求任何 OLE DB 使用者可以从任何提供程序，而不考虑语言 （如 c + + 和基本） 访问数据。  
  
 每个 COM 对象包含多个接口，其中一些是必需，其中一些是可选。 通过实现必需的接口，提供程序可保证最低任何的级别客户端应该能够使用的功能 （称为符合性）。 一个提供程序可以实现以提供其他功能的可选接口。 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)介绍这些接口的详细信息。 客户端应始终调用`QueryInterface`以确定提供程序是否支持给定的接口。  
  
## <a name="ole-db-specification-level-support"></a>OLE DB 规范级别支持  
 OLE DB 提供程序模板支持 OLE DB 版本 2.7 规范。 使用 OLE DB 提供程序模板，您可以实现兼容级别为 0 的访问接口。 提供程序示例中，例如，使用模板来实现执行 DOS DIR 命令来查询文件系统的 non-MS-DOS 命令服务器。 提供程序示例中的行集，它是用于返回表格数据的标准 OLE DB 机制返回目录信息。  
  
 最简单的提供程序支持的 OLE DB 模板类型是具有任何命令的只读提供程序。 此外支持使用命令的提供程序，以及书签和读/写功能。 可以通过编写额外代码来实现读/写提供程序。 动态行集和事务不支持的最新版本，但如果您希望可以将其添加。  
  
## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>你需要时创建的 OLE DB 访问接口？  
 您不始终需要创建自己的提供程序;Microsoft 提供了多个中的预打包、 标准提供商**数据链接属性**Visual c + + 中的对话框。 若要创建的 OLE DB 访问接口的主要原因是利用通用数据访问策略。 因此是一些这样做的优点：  
  
-   通过任何语言如 c + +、 Basic 和 Visual Basic Scripting Edition 访问数据。 它允许你的组织中不同程序员访问相同的数据相同的方式，而不考虑它们使用何种语言。  
  
-   例如，SQL Server、 Excel 和 Access 规避用户数据的其他数据源。 这可能非常有用，如果你想要在不同的格式中间传输数据。  
  
-   在参与跨数据源 （异类） 操作。 这可以是数据仓库的以非常高效的方式。 使用 OLE DB 访问接口，可以将数据保存在其本机格式，并仍将能够访问在一个简单的操作。  
  
-   将其他功能添加到你的数据，如查询处理。  
  
-   提高访问数据时，控制如何操作的性能。  
  
-   提高可靠性。 如果有一种专有数据格式可以访问只能由一个程序员，这是风险。 使用 OLE DB 访问接口，可以打开到所有的编程人员专用格式。  
  
## <a name="read-only-and-updatable-providers"></a>只读和可更新提供程序  
 提供程序可以在复杂程度和功能会有很大。 最好将提供程序分类为只读的提供程序和可更新的提供程序：  
  
-   Visual c + + 6.0 支持仅只读提供程序。 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)讨论如何创建只读提供程序。  
-   Visual c + + 支持可更新的提供程序，可以更新 （写入） 数据存储区。 有关可更新的提供程序的信息，请参阅[创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md); [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)示例是可更新的提供程序的一个示例。  
  
 有关详细信息，请参见:  
  
-   [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)  
  
-   [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)  
  
-   [OLE DB 编程](../../data/oledb/ole-db-programming.md)  
  
## <a name="see-also"></a>请参阅  
 [数据访问](../data-access-in-cpp.md)   
 [OLE DB SDK 文档](/previous-versions/windows/desktop/ms722784\(v=vs.85\))   
 [OLE DB 程序员参考](/previous-versions/windows/desktop/ms713643\(v=vs.85\))