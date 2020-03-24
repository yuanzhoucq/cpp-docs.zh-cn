---
title: Visual C++ 中的数据访问
ms.date: 03/28/2017
helpviewer_keywords:
- Visual C++, data access applications
- databases [C++]
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 95da6237-bbe2-480a-ae50-3a520051ceff
ms.openlocfilehash: a1645c1116daa66c578a6d6e697ab168e4006af9
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150948"
---
# <a name="data-access-in-visual-c"></a>Visual C++ 中的数据访问

几乎所有数据库产品（SQL 和 NoSQL）都提供用于本机 C++ 应用程序的接口。 行业标准接口是 ODBC，所有主要 SQL 数据库产品和多数 NoSQL 产品都支持该接口。 对于非 Microsoft 产品，请咨询供应商，了解详细信息。 此外，还提供具有各种许可条款的第三方库。

自 2011 年起，Microsoft 已将 ODBC 作为本机应用程序连接到本地和云中 Microsoft SQL Server 数据库的标准接口。 有关详细信息，请参阅[数据访问编程\( MFC ATL\)](data-access-programming-mfc-atl.md)。 C++/CLI 库可以使用本机 ODBC 驱动程序或 ADO.NET。 有关详细信息，请参阅[使用 ADO.NET 进行数据访问 (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) 和[在 Visual Studio 中访问数据](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio)。

## <a name="in-this-section"></a>本节内容

[数据访问编程 (MFC/ATL)](data-access-programming-mfc-atl.md)<br/>
介绍使用 Visual C++ 的旧版数据访问编程，其首选方法就是使用其中一个类库，例如活动模板库 (ATL) 或 Microsoft 基础类 (MFC) 库，这样可以简化数据库 API 的处理。

[开放式数据库连接 (ODBC)](odbc/open-database-connectivity-odbc.md)<br/>
Microsoft 基础类 (MFC) 库提供使用开放式数据库连接 (ODBC) 进行编程时所需的类。

[OLE DB 编程](oledb/ole-db-programming.md)<br/>
在某些情况下，尤其是在针对链接服务器进行编程时，仍然需要旧版接口。

## <a name="related-topics"></a>相关主题

[使用 C 和 C++连接到 SQL 数据库](/azure/sql-database/sql-database-develop-cplusplus-simple)<br/>
从 C 或 C++ 应用程序连接到 Azure SQL 数据库。

[用于 C++ 的 Microsoft Azure 存储客户端库](https://github.com/Azure/azure-storage-cpp)<br/>
[Azure 存储](/azure/storage/storage-introduction)是一种云存储解决方案，用于依赖于持久性、可用性和可扩展性来满足其客户需求的现代应用程序。 使用适用于 C++ 的 Azure 存储客户端库，从 C++ 连接到 Azure 存储。

[ODBC Driver for SQL Server](/sql/connect/odbc/microsoft-odbc-driver-for-sql-server)<br/>
最新的 ODBC 驱动程序为基于 C/C++ 的应用程序提供了对 Microsoft SQL Server 和 Microsoft Azure SQL 数据库的可靠数据访问。 提供对包括始终加密、Azure Active Directory 和 AlwaysOn 可用性组在内等功能的支持。 此外，还可用于 MacOS 和 Linux。

[适用于 SQL Server 的 OLE DB 驱动程序](/sql/connect/oledb/oledb-driver-for-sql-server)<br/>
最新的 OLE DB 驱动程序是一个独立的数据访问应用程序编程接口 (API)，支持 Microsoft SQL Server 和 Microsoft Azure SQL 数据库。

[Microsoft Azure C 和 C++ 开发人员中心](https://azure.microsoft.com/develop/cpp/)<br/>
通过 Azure，用户可以使用喜欢的工具轻松生成更具灵活性、可扩展性和可靠性的 C++ 应用程序。

[如何通过 C++ 使用 Blob 存储](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs)<br/>
Azure Blob 存储是一种将非结构化数据作为对象/Blob 存储在云中的服务。 Blob 存储可以存储任何类型的文本或二进制数据，例如文档、媒体文件或应用程序安装程序。 Blob 存储也称为对象存储。

[ODBC 程序员参考](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference)<br/>
ODBC 接口用于与 C 编程语言一起使用。 ODBC 接口的使用涉及三大块：SQL 语句、ODBC 函数调用，以及 C 编程。

## <a name="see-also"></a>另请参阅

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)
