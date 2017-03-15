---
title: "ODBC 和 MFC | Microsoft Docs"
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
  - "连接 [C++], 数据源"
  - "连接 [C++], 数据库"
  - "数据源 [C++], 连接"
  - "数据库连接 [C++], MFC ODBC 类"
  - "数据库 [C++], 连接"
  - "MFC [C++], ODBC 和"
  - "ODBC [C++], MFC"
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# ODBC 和 MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  若要将 MFC 数据库类用于 Win32 平台（如 Windows NT），必须具有数据源的相应 ODBC 驱动程序。  有些驱动程序包括在 Visual C\+\+ 中；而有些可从 Microsoft 和其他供应商处得到。  有关更多信息，请参见 [ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。  
  
 本主题介绍了 Microsoft 基础类 \(MFC\) 库的基于 ODBC 的数据库类的主要概念，并概述了这些类是如何共同发挥作用的。  有关 ODBC 和 MFC 的更多信息，请参见以下主题：  
  
-   [连接到数据源](../../data/odbc/connecting-to-a-data-source.md)  
  
-   [选择和操作记录](../../data/odbc/selecting-and-manipulating-records.md)  
  
-   [在窗体中显示和操作数据](../../data/odbc/displaying-and-manipulating-data-in-a-form.md)  
  
-   [使用文档和视图](../../data/odbc/working-with-documents-and-views.md)  
  
-   [访问 ODBC 和 SQL](../../data/odbc/access-to-odbc-and-sql.md)  
  
-   [有关 MFC ODBC 类的其他阅读材料](../../data/odbc/further-reading-about-the-mfc-odbc-classes.md)  
  
 基于 ODBC 的 MFC 数据库类的目的在于提供对任何可使用 ODBC 驱动程序的数据库的访问。  因为这些类使用 ODBC，所以您的应用程序可以对许多数据格式不同和本地\/远程配置不同的数据进行访问。  您不必编写专用代码来处理不同的数据库管理系统 \(DBMS\)。  只要您的用户具有适用于要访问的数据的 ODBC 驱动程序，他们就可以使用您的程序操作存储在那里的表中的数据。  
  
## 请参阅  
 [开放式数据库连接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)