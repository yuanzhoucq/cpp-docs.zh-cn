---
title: "OLE DB 结构设计问题 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b894ec1cbd227663d46e98e523ffe8c1c5d84475
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="ole-db-architectural-design-issues"></a>OLE DB 结构设计问题
启动 OLE DB 应用程序之前，应考虑以下问题：  
  
 **你将使用哪些编程实现编写 OLE DB 应用程序？**  
 Microsoft 提供了几个库来实现此目的： OLE DB 模板库、 OLE DB 属性和 OLE DB SDK 中的原始 OLE DB 接口。 此外，提供了向导，可帮助你编写你的程序。 这些实现中所述[OLE DB 模板、 特性和其他实现](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md)。  
  
 **你是否需要编写自己的提供程序？**  
 大多数开发人员不需要编写自己的提供程序。 Microsoft 提供了多个提供商。 每当创建数据连接 （例如，向使用 ATL OLE DB 使用者向导为项目添加使用者时），**数据链接属性**对话框将列出你系统上注册的所有可用提供程序。 如果这些提供程序之一是适合于你自己数据存储和数据访问应用程序，最简单办法就是使用以下方法之一。 但是，如果数据存储区不适合其中一个类别，你必须创建自己的提供程序。 有关创建提供程序的信息，请参阅[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)。  
  
 **您需要为自己的使用者何种级别的支持？**  
 某些使用者可以是很基本;虽然其他人可非常复杂。 属性指定的 OLE DB 对象的功能。 当你使用 ATL OLE DB 使用者向导创建使用者或数据库提供程序向导创建提供程序时，它设置为你要为你提供一组标准的功能的适当的对象属性。 但是，如果向导生成的使用者或提供程序类不支持所需的一切其执行的操作，你需要在这些类的接口，请参阅[OLE DB 模板库](../../data/oledb/ole-db-templates.md)。 这些接口包装原始的 OLE DB 接口，提供额外的实现以使用它们更轻松地进行你。  
  
 例如，如果你想要更新在行集中的数据，但忘记在使用向导创建使用者时指定此，你可以指定功能事后通过设置**DBPROP_IRowsetChange**和**DBPROP_UPDATABILITY**命令对象上的属性。 然后，当创建行集合，它具有`IRowsetChange`接口。  
  
 **你是否使用另一种数据访问技术 （ADO、 ODBC 或 DAO） 更早代码？**  
 给定的技术 （如 ADO 组件使用 OLE DB 组件并将 ODBC 代码迁移到 OLE DB） 的可能组合，涵盖所有情况下不的 Visual c + + 文档的范围。 但是，涉及各种方案的许多文章有以下 Microsoft 网站上：  
  
-   [Microsoft 帮助和支持](http://go.microsoft.com/fwlink/p/?linkid=148218)  
  
-   [Microsoft 数据访问技术文章概述](http://go.microsoft.com/fwlink/p/?linkid=148217)  
  
-   [Visual Studio 解决方案中心](http://go.microsoft.com/fwlink/p/?linkid=148215)  
  
-   [搜索 Microsoft.com](http://search.microsoft.com/)  
  
 在执行搜索时，输入最适合你的方案; 的关键字组合例如： 如果你使用的 ADO 对象具有的 OLE DB 提供程序，请尝试布尔搜索与**ADO 和"OLE DB"**。 如果你想要将较早的 DAO 代码迁移至 ODBC，选择"所有词语"并指定字符串，如**迁移 DAO**。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 编程](../../data/oledb/ole-db-programming.md)   
 [OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)