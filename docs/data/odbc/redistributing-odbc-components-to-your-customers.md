---
title: "为客户重新分发 ODBC 组件 | Microsoft Docs"
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
  - "组件 [C++]"
  - "组件 [C++], 分发"
  - "组件 [C++], 重新分发"
  - "ODBC 管理器"
  - "ODBC 组件, 重新分发"
  - "ODBC, 分发组件"
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 为客户重新分发 ODBC 组件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果将 ODBC 管理器的功能合并到您的应用程序中，则还必须将运行这些程序的文件分布给您的用户。  这些 ODBC 文件驻留在 Visual C\+\+ 光盘的 \\OS\\System 目录下。  在同一目录下的 Redistrb.wri 文件和许可协议包含可重新分布的 ODBC 文件列表。  
  
 请参考该文档以获取有关您计划附带的任何 ODBC 驱动程序的信息。  您需要确定附带哪些 DLL 和其他文件。  
  
 还应该阅读[安装数据库支持](../../data/installing-database-support-mfc-atl.md)（它提供有关 ODBC 组件和驱动器的信息）和[重新发布控件](../../data/ado-rdo/redistributing-controls.md)（它解释如何重新发布 ActiveX 控件）。  
  
 除此之外，多数情况下还需要包括一个文件。  Odbccr32.dll 是 ODBC 游标库。  该库赋予 1 级驱动程序前滚和后滚的功能。  它还提供了支持快照的能力。  有关 ODBC 游标库的更多信息，请参见 [ODBC：ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
 下列主题提供有关通过数据库类使用 ODBC 的更多信息：  
  
-   [ODBC：ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
-   [ODBC：配置 ODBC 数据源](../../data/odbc/odbc-configuring-an-odbc-data-source.md)  
  
-   [ODBC：直接调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)  
  
## 请参阅  
 [ODBC 基础](../../data/odbc/odbc-basics.md)   
 [ODBC 管理器](../../data/odbc/odbc-administrator.md)