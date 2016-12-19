---
title: "使用 DAO 和 ODBC 可以访问哪些数据源？ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO [C++], 数据源类型"
  - "数据 [C++], DAO"
  - "数据 [C++], ODBC"
  - "数据访问 [C++], DAO"
  - "数据源 [C++], 可以用 DAO 和 ODBC 访问"
  - "数据库 [C++], 在 DAO 中访问"
  - "常见问题 [C++], 可访问数据库"
  - "ODBC [C++], 可访问数据源"
  - "ODBC 数据源 [C++], 辅助性"
ms.assetid: c88abb45-526a-467a-a01b-d9396bd63236
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 DAO 和 ODBC 可以访问哪些数据源？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

两组 MFC 类都允许访问广泛的各种数据源，并使编写独立于数据源的应用程序成为可能。  
  
##  <a name="_core_databases_you_can_access_with_dao"></a> 使用 DAO 可以访问的数据库  
 使用 DAO 和 MFC DAO 类，可以访问下列数据源：  
  
-   用数据库引擎版本为 1.x、2.x 和 3.0 的 Microsoft Access 或 Microsoft Visual Basic 创建的、使用 Microsoft Jet 数据库引擎的数据库。  
  
-   可安装的 ISAM 数据库，包括：  
  
    -   dBASE III、dBASE IV 和 dBASE 5.0  
  
    -   Paradox 3.x、4.x 和 5.x 版  
  
-   开放式数据库连接 \(ODBC\) 数据库，包括但不仅限于 Microsoft SQL Server、SYBASE SQL Server 和 ORACLE Server。  若要访问 ODBC 数据库，必须具有希望访问的数据库的适当 ODBC 驱动程序。  有关 Visual C\+\+ 此版本中包括的 ODBC 驱动程序列表以及有关获取其他驱动程序的信息，请参见 [ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)。  
  
-   Microsoft Excel 3.0、4.0、5.0 和 7.0 版工作表。  
  
-   Lotus WKS、WK1、WK3 和 WK4 电子表格。  
  
-   文本文件。  
  
 DAO 在和 Microsoft Jet 数据库引擎可以读取的数据库一起使用时效果最好，这包括以上所有数据库，ODBC 数据源除外。  对于 Microsoft Jet \(.mdb\) 数据库性能最佳。  相对于不附加而直接通过 MFC DAO 类打开外部数据库，将外部表（尤其在 ODBC 数据源中）附加到 .mdb 数据库的效果更好。  
  
##  <a name="_core_databases_you_can_access_with_odbc"></a> 使用 ODBC 可以访问的数据库  
 使用 ODBC 和 MFC ODBC 类，可以访问应用程序用户具有其 ODBC 驱动程序的任何本地或远程数据源。16 位、32 位和 64 位的 ODBC 驱动程序都可用于广泛的数据源。  如果使用的是 Microsoft Jet \(.mdb\) 数据库，使用 DAO 类比 Microsoft Access ODBC 驱动程序更有效。  
  
## 请参阅  
 [关于数据访问的常见问题](../data/data-access-frequently-asked-questions-mfc-data-access.md)