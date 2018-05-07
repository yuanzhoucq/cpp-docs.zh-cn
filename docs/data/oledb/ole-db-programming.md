---
title: OLE DB 编程 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB [C++]
- data access [C++], OLE DB programming
- OLE DB [C++], about OLE DB
ms.assetid: 52a80d66-17a9-43a1-9b90-392ae43cea2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fb77c5b7d7f6de91f74e83c395d0fcc13ebf70e0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="ole-db-programming"></a>OLE DB 编程
Microsoft OLE DB 是一项传统技术;对于新的应用程序是链接 SQL 服务器的所需的数据访问 API。 所有其他新的应用程序应使用 ODBC。 SQL Server 的当前 OLE DB 访问接口是 SQLNCLI11。DLL。 提供程序仍将在 SQL Server 2016 进行发布。 本文档适用于开发人员要保留已使用 OLE DB 的现有应用程序。
  
 OLE DB 模板是使高性能 OLE DB 数据库技术更易用的 C++ 模板，它提供了实现许多常用 OLE DB 接口的类。 此模板库划分为使用者模板和提供程序模板。  
  
 Visual C++ 还具有用于创建 OLE DB 初学者应用程序的向导支持。  
  
 此外，您可以使用属性来实现 OLE DB 使用者模板。  
  
|了解更多信息|请参阅|  
|-------------------------|---------|  
|使用 OLE DB 使用者模板（概念性主题）|[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)|  
|使用 OLE DB 提供程序模板（概念性主题）|[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)|  
|OLE DB 模板类和宏|[OLE DB 模板参考](../../data/oledb/ole-db-templates.md)（Visual c + +）|  
|OLE DB 使用者特性|[OLE DB 使用者特性](../../windows/ole-db-consumer-attributes.md)|  
|OLE DB 接口|[OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)（在 Windows SDK)|  
|OLE DB 模板示例|[OLE DB 模板示例](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c)| 
|数据访问编程概述 (Visual C++)|[数据访问编程](../../data/data-access-programming-mfc-atl.md)|  
|ODBC 概念主题|[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)|  

  
## <a name="see-also"></a>请参阅  
 [数据访问](../data-access-in-cpp.md)