---
title: "使用文档和视图 | Microsoft Docs"
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
  - "文档 [C++], MFC"
  - "MFC [C++], 文档"
  - "MFC [C++], 视图"
  - "视图 [C++], MFC"
ms.assetid: 349b142d-1c5a-4b99-9de4-241e41d3d2f1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用文档和视图
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft 基础类 \(MFC\) 库的许多功能都依赖于文档\/视图结构。  通常，文档存储您的数据，视图在框架窗口的工作区显示您的数据并管理用户与数据的交互。  视图与文档进行通信以得到和更新数据。  您可以在有框架时或无框架时使用数据库类。  
  
 有关在框架中使用数据库类的更多信息，请参见 [MFC：结合文档和视图使用数据库类](../../data/mfc-using-database-classes-with-documents-and-views.md)。  
  
 默认情况下，“MFC 应用程序向导”在没有数据库支持下创建主干应用程序。  但是，您可以选择包括最小数据库支持或者更完全的基于窗体的支持的选项。  有关应用程序向导选项的更多信息，请参见 [MFC 应用程序向导的数据库支持](../../mfc/reference/database-support-mfc-application-wizard.md)。  
  
 您还可以在不完全使用文档\/视图结构时使用数据库类。  有关更多信息，请参见 [MFC：不结合文档和视图使用数据库类](../../data/mfc-using-database-classes-without-documents-and-views.md)。  
  
## 请参阅  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)