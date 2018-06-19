---
title: Visual c + + 中的数据访问 |Microsoft 文档
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, data access applications
- databases [C++]
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 95da6237-bbe2-480a-ae50-3a520051ceff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bb74d27af485f765e1330bc83ab196e1d9ba6b5c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090639"
---
# <a name="data-access-in-visual-c"></a>Visual C++ 中的数据访问

几乎所有数据库产品（SQL 和 NoSQL）都提供用于本机 C++ 应用程序的接口。 行业标准接口是 ODBC，所有主要 SQL 数据库产品和多数 NoSQL 产品都支持该接口。 对于非 Microsoft 产品，请咨询供应商，了解详细信息。 此外，还提供具有各种许可条款的第三方库。

自 2011 年起，Microsoft 已将 ODBC 作为本机应用程序连接到本地和云中 Microsoft SQL Server 数据库的标准接口。 有关详细信息，请参阅[数据访问编程\( MFC ATL\)](data-access-programming-mfc-atl.md)。 C++/CLI 库可以使用本机 ODBC 驱动程序或 ADO.NET。 有关详细信息，请参阅[使用 ADO.NET 进行数据访问 (C++/CLI)](/dotnet/data-access-using-adonet-cpp-cli.md) 和[在 Visual Studio 中访问数据](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio)。

## <a name="in-this-section"></a>本节内容
[数据访问编程 (MFC/ATL)](data-access-programming-mfc-atl.md)介绍旧版数据访问使用 Visual c + +，其中的首选的方式是使用其中一个类库，例如活动模板库 (ATL) 或 Microsoft 基础类 (MFC) 库，编程这简化数据库 Api 的处理。

[打开数据库连接 (ODBC)](odbc/open-database-connectivity-odbc.md) Microsoft 基础类 (MFC) 库提供编程开放式数据库连接 (ODBC) 的类。

[OLE DB 编程](oledb/ole-db-programming.md)一个主要旧接口，特别是，当您对编程在某些情况下，仍需要链接服务器。

## <a name="related-topics"></a>相关主题
[连接到 SQL 数据库使用 C 和 c + +](/azure/sql-database/sql-database-develop-cplusplus-simple)来自 C 或 c + + 应用程序连接到 Azure SQL 数据库。

[用于 c + + 的 Microsoft Azure 存储客户端库](https://github.com/Azure/azure-storage-cpp)
[Azure 存储空间](/azure/storage/storage-introduction)是依赖于持续性、 可用性和可伸缩性，以满足的需求的现代应用程序的云存储解决方案其客户。 使用适用于 C++ 的 Azure 存储客户端库，从 C++ 连接到 Azure 存储。

[ODBC Driver 13.1 for SQL Server-Windows 发布](https://blogs.msdn.microsoft.com/sqlnativeclient/2016/08/01/announcing-the-odbc-driver-13-1-for-sql-server)的最新的 ODBC 驱动程序到 Microsoft SQL Server 2016 Microsoft Azure SQL 数据库提供可靠的数据的访问，对于 C/c + + 基于应用程序。 提供始终加密功能包括支持、 Azure Active Directory 和 AlwaysOn 可用性组。 此外，还可用于 MacOS 和 Linux。     
 
[SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client-programming) SQL Server Native Client 是独立的数据访问应用程序编程接口 (API)，用于 OLE DB 和 ODBC，支持通过 SQL Server 2014 的 SQL Server 2005。 新的应用程序应使用适用于 SQL Server 的 ODBC 驱动程序 13.1。

[Microsoft Azure C 和 c + + 开发人员中心](https://azure.microsoft.com/develop/cpp/)Azure 可以轻松地使用较高的灵活性、 可伸缩性和可靠性使用你喜欢的工具生成 c + + 应用程序。    

[如何通过 c + + 使用 Blob 存储](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs)Azure Blob 存储是一种服务中将非结构化的数据存储在云中作为对象/blob。 Blob 存储可以存储任何类型的文本或二进制数据（如文档、媒体文件或应用程序安装程序）。 Blob 存储也称为对象存储。

[ ODBC 程序员参考](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference)ODBC 接口设计用于 C 编程语言。 ODBC 接口的使用涉及三大块：SQL 语句、ODBC 函数调用，以及 C 编程。

## <a name="see-also"></a>请参阅
[Visual C++](../visual-cpp-in-visual-studio.md)
