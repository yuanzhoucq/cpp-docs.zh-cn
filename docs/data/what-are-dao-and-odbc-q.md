---
title: "什么是 DAO 和 ODBC？ | Microsoft Docs"
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
  - "DAO（数据访问对象）, 和 ODBC"
  - "ODBC, 关于 ODBC"
ms.assetid: 22cc2f75-7ff6-47bc-ac56-56a40591104c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 什么是 DAO 和 ODBC？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

数据访问对象 \(DAO\) 和开放式数据库连接 \(ODBC\) 都是 API，为您提供了编写独立于任何特定数据库管理系统 \(DBMS\) 的应用程序的能力。  
  
 使用 Microsoft Access Basic 或 Microsoft Visual Basic 的数据库程序员对 DAO 很熟悉。  DAO 使用 Microsoft Jet 数据库引擎提供一组数据访问对象：数据库对象、tabledef 和 querydef 对象、记录集对象以及其他对象。  DAO 与 .mdb 文件（如 Microsoft Access 创建的 .mdb 文件）一起使用效果最佳，但是也可以通过 DAO 和 Microsoft Jet 数据库引擎访问 ODBC 数据源。  
  
 ODBC 提供了不同的数据库供应商通过针对特定 DBMS 的 ODBC 驱动程序实现的 API。  程序使用此 API 调用 ODBC 驱动程序管理器，后者将调用传递到适当的驱动程序。  然后，此驱动程序使用 SQL 与 DBMS 进行交互。  
  
> [!NOTE]
>  ODBC 是 Microsoft Windows 开放式标准体系结构 \(WOSA\) 的重要组成部分。  围绕 Microsoft Jet 数据库引擎对 DAO 进行了优化，但仍可以使用该引擎访问 ODBC 和其他外部数据源，并且独特的 ODBC API 和基于它的 MFC 类仍可用，并且仍在数据库工具的选择中扮演着自己的角色。  
  
## 请参阅  
 [关于数据访问的常见问题](../data/data-access-frequently-asked-questions-mfc-data-access.md)