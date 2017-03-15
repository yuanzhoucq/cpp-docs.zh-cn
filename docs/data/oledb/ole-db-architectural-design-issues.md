---
title: "OLE DB 结构设计问题 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB, 应用程序设计注意事项"
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# OLE DB 结构设计问题
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

开始编写 OLE DB 应用程序之前应考虑以下问题：  
  
 **使用何种编程实现来编写 OLE DB 应用程序？**  
 Microsoft 提供多种库来解决该问题：OLE DB 模板库、OLE DB 特性以及 OLE DB SDK 中的原始 OLE DB 接口。  另外，Microsoft 还提供帮助您编写程序的向导。  有关这些实现的更详细的信息，请参见 [OLE DB 模板、特性和其他实现](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md)。  
  
 **是否需要编写自己的提供程序？**  
 大多数开发人员不需要编写自己的提供程序。  Microsoft 提供多种提供程序。  每次创建数据连接时（例如，当使用 ATL OLE DB 使用者向导向项目中添加使用者时），**“数据链接属性”**对话框都将列出系统中注册的所有可用提供程序。  如果其中一个提供程序适合于用户自己的数据存储和数据访问应用程序，最简单的办法就是使用该提供程序。  但是，如果数据存储区不适合所提供的某个类别，则必须创建自己的提供程序。  有关更多信息，请参见 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)。  
  
 **需要为自己的使用者提供何种级别的支持？**  
 一些使用者可能非常简单，另一些可能非常复杂。  OLE DB 对象的功能由属性指定。  使用 ATL OLE DB 使用者向导创建使用者或者使用数据库提供程序向导创建提供程序时，向导将为用户设置合适的对象属性来提供一组标准功能。  但是，如果向导生成的使用者类或提供程序类并不具有您需要的所有支持功能，那么您需要查阅这些类在 [OLE DB 模板库](../../data/oledb/ole-db-templates.md)中的接口。  这些接口包装原始 OLE DB 接口，提供附加实现以使其使用起来更加简单。  
  
 例如，如果您希望更新行集合中的数据，但在使用向导创建使用者时却忘记指定该功能，则可以在创建使用者之后通过对命令对象设置 **DBPROP\_IRowsetChange** 和 **DBPROP\_UPDATABILITY** 属性来指定该功能。  这样，创建行集合之后，它将具有 `IRowsetChange` 接口。  
  
 **您是否有使用其他数据访问技术（ADO、ODBC 或 DAO）的旧版代码？**  
 由于可能有各种各样的技术组合（例如 ADO 组件和 OLE DB 组件一起使用以及将 ODBC 代码迁移至 OLE DB），所以 Visual C\+\+ 文档不能涵盖所有的情形。  但是，用户可参阅以下 Microsoft 网站中众多关于各种情形的文章：  
  
-   [Microsoft 帮助和支持](http://go.microsoft.com/fwlink/?LinkId=148218)  
  
-   [Microsoft 数据访问技术文章概述](http://go.microsoft.com/fwlink/?LinkId=148217)  
  
-   [Visual Studio 解决方案中心](http://go.microsoft.com/fwlink/?LinkId=148215)  
  
-   [搜索 Microsoft.com](http://search.microsoft.com/)  
  
 进行搜索时，请输入最符合您的情况的关键字组合，例如，如果要使用 ADO 对象和 OLE DB 提供程序，可输入 **ADO AND "OLE DB"** 执行布尔搜索。  如需将旧版 DAO 代码迁移至 ODBC，可选择“所有词语”并指定字符串，例如“迁移 DAO”或“DAO 遗留”。  
  
## 请参阅  
 [OLE DB 编程](../../data/oledb/ole-db-programming.md)   
 [OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)