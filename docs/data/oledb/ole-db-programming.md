---
title: OLE DB 编程
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB [C++]
- data access [C++], OLE DB programming
- OLE DB [C++], about OLE DB
ms.assetid: 52a80d66-17a9-43a1-9b90-392ae43cea2b
ms.openlocfilehash: 59bee1c204d2f101d8175ff42c78ca4bbdcaeb4c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523138"
---
# <a name="ole-db-programming"></a>OLE DB 编程

Microsoft OLE DB 是一项传统技术;对于新的应用程序是链接 SQL 服务器的所需的数据访问 API。 所有其他新的应用程序应使用 ODBC。 SQL Server 的当前 OLE DB 访问接口是 SQLNCLI11。DLL。 提供程序仍将在 SQL Server 2016 发布。 本文档适用于开发人员要保留已在使用 OLE DB 的现有应用程序。

OLE DB 模板是使高性能 OLE DB 数据库技术更易用的 C++ 模板，它提供了实现许多常用 OLE DB 接口的类。 此模板库划分为使用者模板和提供程序模板。

Visual C++ 还具有用于创建 OLE DB 初学者应用程序的向导支持。

此外，可以使用属性来实现 OLE DB 使用者模板。

|了解更多信息|请参阅|
|-------------------------|---------|
|使用 OLE DB 使用者模板（概念性主题）|[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)|
|使用 OLE DB 提供程序模板（概念性主题）|[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)|
|OLE DB 模板类和宏|[OLE DB 模板参考](../../data/oledb/ole-db-templates.md)（Visual c + +）|
|OLE DB 使用者特性|[OLE DB 使用者特性](../../windows/ole-db-consumer-attributes.md)|
|OLE DB 接口|[OLE DB 程序员参考](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming(v%3dvs.85))（在 Windows SDK 中)|
|OLE DB 模板示例|[OLE DB 模板示例](https://github.com/Microsoft/VCSamples)|
|数据访问编程概述 (Visual C++)|[数据访问编程](../../data/data-access-programming-mfc-atl.md)|
|ODBC 概念主题|[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)|

## <a name="see-also"></a>请参阅

[数据访问](../data-access-in-cpp.md)