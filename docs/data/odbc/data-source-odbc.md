---
title: 数据源 (ODBC) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 842a8bf3faadcf96b4f44441e45dc94d5679f9f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="data-source-odbc"></a>数据源 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 在数据库术语中，数据源是一组特定的数据，访问该数据和数据源，可以使用数据源名称描述的位置所需的信息。 若要使用类[CDatabase](../../mfc/reference/cdatabase-class.md)，数据源必须是一个已配置通过开放式数据库连接 (ODBC) 管理器。 数据源的示例包括在 Microsoft SQL Server 上运行跨网络或本地目录中的 Microsoft Access 文件的远程数据库。 从应用程序，你可以访问您对其具有 ODBC 驱动程序的任何数据源。  
  
 你可以一次，你的应用程序中处于活动状态的一个或多个数据源，每个表示`CDatabase`对象。 你还可以同时进行的多个连接到任何数据源。 你可以连接到远程，以及对本地数据源，具体取决于已安装的驱动程序和 ODBC 驱动程序的功能。 有关数据源和 ODBC 管理器的详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)和[ODBC 管理器](../../data/odbc/odbc-administrator.md)。  
  
 以下主题更深入地有关数据源：  
  
-   [数据源：管理连接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)  
  
-   [数据源：确定数据源的架构 (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)  
  
## <a name="see-also"></a>请参阅  
 [开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)