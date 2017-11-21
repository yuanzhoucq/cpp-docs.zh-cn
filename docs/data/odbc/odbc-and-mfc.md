---
title: "ODBC 和 MFC |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC [C++], MFC
- connections [C++], databases
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- MFC [C++], ODBC and
- database connections [C++], MFC ODBC classes
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f4e90281b3202303fa95e44684f8250259d0d653
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="odbc-and-mfc"></a>ODBC 和 MFC
> [!NOTE]
>  若要使用的 MFC 数据库类，必须具有适当的 ODBC 驱动程序的数据源。 用于 SQL Server 的最新 Microsoft ODBC 驱动程序[Microsoft ODBC Driver 13 for SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=50420)。 大多数数据库供应商提供适用于 Windows 的 ODBC 驱动程序。 
  
 本主题介绍了 Microsoft 基础类 (MFC) 库的基于 ODBC 数据库类的主要概念，并提供了概述类如何协同工作。 有关 ODBC 和 MFC 的详细信息，请参阅以下主题：  
  
-   [连接到数据源](connecting-to-a-data-source.md)  
  
-   [选择和操作记录](selecting-and-manipulating-records.md)  
  
-   [在窗体中显示和操作数据](displaying-and-manipulating-data-in-a-form.md)  
  
-   [使用文档和视图](working-with-documents-and-views.md)  
  
-   [访问 ODBC 和 SQL](access-to-odbc-and-sql.md)  
  
-   [有关 MFC ODBC 类的其他阅读材料](further-reading-about-the-mfc-odbc-classes.md)  
  
 基于 ODBC 的 MFC 数据库类旨在提供对任何数据库所在的 ODBC 驱动程序有可用的访问权限。 因为这些类使用 ODBC，你的应用程序可以访问在许多不同的数据格式和不同的本地/远程配置的数据。 无需编写专用代码来处理不同的数据库管理系统 (Dbms)。 只要你的用户具有合适的 ODBC 驱动程序他们想要访问的数据，它们可以使用你的程序来操作存储在那里的表中的数据。  
  
## <a name="see-also"></a>另请参阅  
 [开放式数据库连接 (ODBC)](open-database-connectivity-odbc.md)