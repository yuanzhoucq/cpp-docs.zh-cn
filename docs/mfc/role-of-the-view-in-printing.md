---
title: "视图在打印中的作用 | Microsoft Docs"
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
  - "CView 类, 打印中的角色"
  - "OnDraw 方法, 和打印"
  - "打印 [MFC], OnDraw 方法"
  - "打印 [MFC], 视图"
  - "打印视图"
  - "视图, 打印"
ms.assetid: 8d4a3c8e-1fce-4edc-b608-94cb5f3e487e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 视图在打印中的作用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

视图中打印其关联文档还模拟两个重要的影响。  
  
 视图：  
  
-   在打印机使用同一 [OnDraw](../Topic/CView::OnDraw.md) 代码绘制。在屏幕绘制。  
  
-   管理划分文档打印到的页面。  
  
 有关打印的更多信息以及打印视图的效果，请参见 [打印和打印预览](../mfc/printing-and-print-preview.md)。  
  
## 请参阅  
 [使用视图](../mfc/using-views.md)