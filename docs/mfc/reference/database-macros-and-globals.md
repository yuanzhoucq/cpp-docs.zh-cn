---
title: "数据库宏和全局函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
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
  - "数据库全局 [C++]"
  - "数据库宏 [C++]"
  - "全局数据库函数 [C++]"
  - "全局函数 [C++], 数据库函数"
  - "宏 [C++], MFC 数据库"
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
caps.latest.revision: 13
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 数据库宏和全局函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下面的宏列出和全局变量适用于基于 ODBC 的数据库应用程序。  它们不用于基于 DAO 的应用程序。  
  
 在 MFC 4.2 版之前，`AFX_SQL_ASYNC` 宏和 `AFX_SQL_SYNC` 提供了异步操作能够生成时间。其他进程。  从 MFC，因为 MFC ODBC 类仅使用了同步操作，4.2 开始，这些宏的实现更改。  宏 `AFX_ODBC_CALL` 是新为 MFC 4.2。  
  
### 数据库宏  
  
|||  
|-|-|  
|[AFX\_ODBC\_CALL](../Topic/AFX_ODBC_CALL.md)|调用返回 `SQL_STILL_EXECUTING`的 ODBC API 函数。  `AFX_ODBC_CALL` 被反复调用函数，直到不再返回 `SQL_STILL_EXECUTING`。|  
|[AFX\_SQL\_ASYNC](../Topic/AFX_SQL_ASYNC.md)|调用 `AFX_ODBC_CALL`。|  
|[AFX\_SQL\_SYNC](../Topic/AFX_SQL_SYNC.md)|调用不返回 `SQL_STILL_EXECUTING`的 ODBC API 函数。|  
  
### 数据库全局  
  
|||  
|-|-|  
|[AfxGetHENV](../Topic/AfxGetHENV.md)|处理检索到 ODBC 环境正在使用由 MFC。  在直接 ODBC 调用中使用此句柄。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)