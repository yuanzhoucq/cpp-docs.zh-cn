---
title: 数据访问编程 (MFC-ATL)
ms.date: 11/16/2018
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: def97b2c-b5a6-445f-afeb-308050fd4852
ms.openlocfilehash: e71e16bef29239e0c6a391b2d5e2129042cd52fa
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221841"
---
# <a name="data-access-programming-mfcatl"></a>数据访问编程 (MFC/ATL)

多年来，Visual C ++ 提供了多种处理数据库的方法。 在 2011 年 Microsoft 公布了它作为从本机代码访问 SQL Server 产品的首选技术对齐开放式数据库连接 (ODBC)。 ODBC 是一个行业标准，通过它可在多个平台与数据源之间获取代码最佳的可移植性。 绝大多数 SQL 数据库和众多 NoSQL 产品都支持 ODBC。 可通过调用低级别 ODBC API、使用 MFC ODBC 包装器类或第三方 C++ 包装器库来直接使用 ODBC。

OLE DB 是基于 COM 规范的低级别、高性能 API，仅在 Windows 上可用。 如果程序正在访问[链接服务器](/sql/relational-databases/linked-servers/linked-servers-database-engine)，请使用 OLE DB。 ATL 提供的 OLE DB 模板可简化自定义 OLE DB 提供程序和使用者的创建。 Microsoft SQL Server 的最新提供程序可以找到有关的文档中[OLE DB 驱动程序适用于 SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)。

## <a name="porting-data-applications"></a>移植数据应用程序

如果旧版应用程序使用 OLE DB 或更高级别的 ADO 接口连接到 SQL Server，则应考虑迁移到最新[OLE DB 驱动程序适用于 SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)以便充分利用最新的 SQL Server 功能。 另一种方法，如果不需要跨平台可移植性或最新的 SQL Server 功能，您可以可能是使用 Microsoft OLE DB Provider for ODBC (MSDASQL)。  MSDASQL 允许在 OLE DB 和 ADO（它在内部使用 OLEDB）上生成的应用程序通过 ODBC 驱动程序访问数据源。 与任何转换层一样，MSDASQL 也能影响数据库性能。 请通过测试来判断应用程序的受影响程度。 MSDASQL 附带 Windows 操作系统，而 Windows Server 2008 和 Windows Vista SP1 是首个包含此技术 64 位版本的 Windows 版本。

如果在C++应用程序连接到 SQL Server 或 Azure SQL 数据库通过 ODBC，应使用[最新的 ODBC 驱动程序](/sql/connect/odbc/download-odbc-driver-for-sql-server)。

如果使用的是 C++/CLI，则可以一如既往地使用 ADO.NET。 有关详细信息，请参阅[使用 ADO.NET 进行数据访问 (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) 和[在 Visual Studio 中访问数据](/visualstudio/data-tools/accessing-data-in-visual-studio)。

- 除 ODBC 包装器类之外，MFC 还提供数据访问对象 (DAO) 包装器类，用于连接到 Access 数据库。  但 DAO 已过时。 应升级任何基于 CDaoDatabase 或 CDaoRecordset 的代码。

有关 Microsoft Windows 上数据访问技术历史记录的详细信息，请参阅 [Microsoft Data Access Components (Wikipedia)](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components)。（Microsoft 数据访问组件（维基百科））

## <a name="see-also"></a>请参阅

[数据访问](data-access-in-cpp.md)<br/>
[Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc)（Microsoft 开放式数据库连接 (ODBC)）<br/>
