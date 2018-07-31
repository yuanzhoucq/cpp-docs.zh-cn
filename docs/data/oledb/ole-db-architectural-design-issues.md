---
title: OLE DB 结构设计问题 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5b080945309732bec06c63eb665bbf6dd5f4acb5
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340558"
---
# <a name="ole-db-architectural-design-issues"></a>OLE DB 结构设计问题
启动 OLE DB 应用程序之前，应考虑以下问题：  
  
 **您将使用哪些编程实现来编写 OLE DB 应用程序？**  
 Microsoft 还提供了几个库来实现此目的： OLE DB 模板库、 OLE DB 属性和 OLE DB SDK 中的原始 OLE DB 接口。 此外，还有向导，可帮助您编写您的程序。 这些实现中所述[OLE DB 模板、 特性和其他实现](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md)。  
  
 **若要编写自己的提供程序需要吗？**  
 大多数开发人员不需要编写自己的提供程序。 Microsoft 提供了多个提供商。 创建数据连接 （例如，使用者添加到使用 ATL OLE DB 使用者向导的项目时），每当**数据链接属性**对话框会列出系统中注册的所有可用提供程序。 如果这些提供程序之一适用于你自己的数据存储和数据访问应用程序，最简单的办法就是使用其中一种。 但是，如果数据存储区不适合以下类别之一，您必须创建自己的提供程序。 有关创建提供程序的信息，请参阅[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)。  
  
 **您需要为使用者的支持级别？**  
 某些使用者可以是非常基本;而其他人可能非常复杂。 由属性指定的 OLE DB 对象的功能。 当使用 ATL OLE DB 使用者向导来创建使用者或数据库提供程序向导创建提供程序时，它设置合适的对象属性，以便为您提供一组标准的功能。 但是，如果向导生成的使用者或提供程序类不支持所需其执行的操作的一切，您需要引用这些类在接口[OLE DB 模板库](../../data/oledb/ole-db-templates.md)。 这些接口将包装原始提供额外的实现来使用它们更轻松地进行您的 OLE DB 接口。  
  
 例如，如果您想要更新行集中的数据，但忘记指定这使用向导创建使用者时，您可以指定的功能在事后通过设置`DBPROP_IRowsetChange`和`DBPROP_UPDATABILITY`命令对象上的属性。 然后，创建行集时，它具有`IRowsetChange`接口。  
  
 **你是否使用另一种数据访问技术 （ADO、 ODBC 或 DAO） 的较旧代码？**  
 给定技术 （如 ADO 组件使用 OLE DB 组件并将 ODBC 代码迁移到 OLE DB） 的可能组合，涵盖所有情况下已超出 Visual c + + 文档的讨论范围。 但是，涉及各种方案的许多文章有以下 Microsoft 网站上：  
  
-   [Microsoft 帮助和支持](http://go.microsoft.com/fwlink/p/?linkid=148218)  
  
-   [Microsoft 数据访问技术文章概述](http://go.microsoft.com/fwlink/p/?linkid=148217)  
  
-   [Visual Studio 解决方案中心](http://go.microsoft.com/fwlink/p/?linkid=148215)  
  
-   [搜索 Microsoft.com](http://search.microsoft.com/)  
  
 在执行搜索时，输入关键字的组合，用于最适合自己方案;例如： 如果已通过 OLE DB 访问接口使用 ADO 对象，请尝试布尔搜索与**ADO 和"OLE DB"**。 如果你想要将较早的 DAO 代码迁移到 ODBC，选择"所有词语"并指定字符串，如**迁移 DAO**。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 编程](../../data/oledb/ole-db-programming.md)   
 [OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)