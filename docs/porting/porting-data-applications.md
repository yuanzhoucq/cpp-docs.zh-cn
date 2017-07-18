---
title: "移植数据应用程序 | Microsoft Docs"
ms.custom: 
ms.date: 05/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 8d10c285-c13f-4e6e-a09e-5ee0f2666b44
caps.latest.revision: 0
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: 0fa935667ed1ec0410e8981758dce25b88324718
ms.openlocfilehash: b8599f7220554984453bfabe988b95209f5a82a0
ms.contentlocale: zh-cn
ms.lasthandoff: 05/24/2017

---

# <a name="porting-data-applications"></a>移植数据应用程序
多年来，Visual C ++ 提供了多种处理数据库的方法。 2011 年，Microsoft 宣布将 ODBC 作为从本机代码访问 SQL Server 产品的首选技术。 ODBC 是一个行业标准，通过它可在多个平台与数据源之间获取代码最佳的可移植性。 绝大多数 SQL 数据库和众多 NoSQL 产品都支持 ODBC。 可通过调用低级别 ODBC API、使用 MFC ODBC 包装器类或第三方 C++ 包装器库来直接使用 ODBC。 

OLE DB 是基于 COM 规范的低级别、高性能 API，仅在 Windows 上可用。 如果程序正在访问[链接服务器](https://msdn.microsoft.com/library/ms188279.aspx)，请使用 OLE DB。 ATL 提供的 OLE DB 模板可简化自定义 OLE DB 提供程序和使用者的创建。 最新版 OLE DB 随附 SQL Native Client 11 一起提供。  

如果旧版应用程序使用 OLE DB 或通过更高级别的 ADO 接口连接到 SQL Server，且你并未访问链接服务器，则应考虑在不久的将来迁移到 ODBC。 如果不需要跨平台可移植性或最新 SQL Server 功能，可使用用于 ODBC 的 Microsoft OLE DB 提供程序 (MSDASQL)。  MSDASQL 允许在 OLE DB 和 ADO（它在内部使用 OLEDB）上生成的应用程序通过 ODBC 驱动程序访问数据源。 与转换层一样，MSDASQL 也能影响数据库性能。 请通过测试来判断应用程序的受影响程度。 MSDASQL 附带 Windows 操作系统，而 Windows Server 2008 和 Windows Vista SP1 是首个包含此技术 64 位版本的 Windows 版本。

在单个 DLL 中打包 OLE DB 和 ODBC 驱动程序的 SQL Native Client 组件 (SNAC) 已被 ODBC 应用程序弃用。 SNAC 的 SQL Server 2012 版本 (SQLNCLI11.DLL) 随附 SQL Server 2016 一起提供，因为其他 SQL Server 组件都依赖于它。 但是，通过 ODBC 连接到 SQL Server 或 Azure SQL 数据库的新 C++ 应用程序应使用[最新版本的 ODBC 驱动程序](https://docs.microsoft.com/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server)。 有关详细信息，请参阅 [SQL Server Native Client Programming](https://msdn.microsoft.com/en-us/library/ms130892.aspx)（SQL Server Native Client 编程）

如果使用的是 C++/CLI，则可以一如既往地使用 ADO.NET。 有关详细信息，请参阅[使用 ADO.NET 进行数据访问 (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) 和[在 Visual Studio 中访问数据](/visualstudio/data-tools/accessing-data-in-visual-studio)。  
  
-   除 ODBC 包装器类之外，MFC 还提供数据访问对象 (DAO) 包装器类，用于连接到 Access 数据库。  但 DAO 已过时。 应升级任何基于 CDaoDatabase 或 CDaoRecordset 的代码。 

有关 Microsoft Windows 上数据访问技术历史记录的详细信息，请参阅 [Microsoft Data Access Components (Wikipedia)](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components)。（Microsoft 数据访问组件（维基百科））  

## <a name="see-also"></a>另请参阅  
 [Visual C++ 中的数据访问](../data/data-access-in-cpp.md)  
 [Microsoft Open Database Connectivity (ODBC)](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc)（Microsoft 开放式数据库连接 (ODBC)）  
 [数据访问技术路线图](https://msdn.microsoft.com/en-us/library/ms810810.aspx)  
