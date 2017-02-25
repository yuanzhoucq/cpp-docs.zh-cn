---
title: "DAO 数据库引擎初始化和终止 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO（数据访问对象）, 初始化"
  - "DAO（数据访问对象）, 终止"
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# DAO 数据库引擎初始化和终止
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当使用 MFC DAO 时对象，必须先初始化然后终止 DAO 数据库引擎，则应用程序或 DLL 之前退出。  两种函数，`AfxDaoInit` 和 `AfxDaoTerm`，请执行这些任务。  
  
### DAO 数据库引擎初始化和终止  
  
|||  
|-|-|  
|[AfxDaoInit](../Topic/AfxDaoInit.md)|初始化 DAO 数据库引擎。|  
|[AfxDaoTerm](../Topic/AfxDaoTerm.md)|终止 DAO 数据库引擎。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)