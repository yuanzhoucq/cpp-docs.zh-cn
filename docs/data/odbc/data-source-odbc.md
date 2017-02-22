---
title: "数据源 (ODBC) | Microsoft Docs"
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
  - "CDatabase 类, 数据源连接"
  - "配置 ODBC 数据源"
  - "ODBC 数据源"
  - "ODBC 数据源, 配置"
  - "ODBC 数据源, 由 CDatabase 表示"
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 数据源 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 按照数据库术语，数据源是数据、访问该数据所需的信息和该数据源位置的特定集合，其中的数据源位置可用数据源名称描述。  若要使用类 [CDatabase](../../mfc/reference/cdatabase-class.md)，数据源必须是您已通过开放式数据库连接 \(ODBC\) 管理器配置的一个数据源。  例如，数据源可以是通过网络在 Microsoft SQL Server 上运行的远程数据库，也可以是本地目录中的 Microsoft Access 文件。  通过您的应用程序，可以访问任何具有其 ODBC 驱动程序的数据源。  
  
 在您的应用程序中一次可以有一个或多个活动数据源，每一活动数据源用一个 `CDatabase` 对象表示。  您还可以同时具有多条到任一数据源的连接。  根据所安装的驱动程序和 ODBC 驱动程序的功能，可以连接到远程或本地数据源。  有关数据源和 ODBC 管理器的更多信息，请参见 [ODBC](../../data/odbc/odbc-basics.md) 和 [ODBC 管理器](../../data/odbc/odbc-administrator.md)。  
  
 以下主题更深入地描述了数据源：  
  
-   [数据源：管理连接 \(ODBC\)](../../data/odbc/data-source-managing-connections-odbc.md)  
  
-   [数据源：确定数据源的架构 \(ODBC\)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)  
  
## 请参阅  
 [开放式数据库连接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)