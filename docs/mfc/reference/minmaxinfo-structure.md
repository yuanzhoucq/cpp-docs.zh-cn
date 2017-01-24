---
title: "MINMAXINFO 结构 | Microsoft Docs"
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
  - "MINMAXINFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MINMAXINFO 结构"
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MINMAXINFO 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`MINMAXINFO` 结构包含有关该窗口的最大大小的信息和位置及其最小和最大次数跟踪范围。  
  
## 语法  
  
```  
  
      typedef struct tagMINMAXINFO {  
   POINT ptReserved;  
   POINT ptMaxSize;  
   POINT ptMaxPosition;  
   POINT ptMinTrackSize;  
   POINT ptMaxTrackSize;  
} MINMAXINFO;  
```  
  
#### 参数  
 *ptReserved*  
 保留以供内部使用。  
  
 *ptMaxSize*  
 最大化指定的宽度 \(point.x\) 和"最大化的高度 \(point.y\) 窗口。  
  
 `ptMaxPosition`  
 最大化窗口的指定 \(point.x\) 左侧的位置和最大化窗口的大小 \(point.y\) 顶部的位置。  
  
 *ptMinTrackSize*  
 指定最小宽度和最小 point.x 跟踪 \(\) 的高度 \(point.y\) 的跟踪窗口。  
  
 *ptMaxTrackSize*  
 指定最大跟踪宽度 \(point.x\) 和最大跟踪的高度 \(point.y\) 窗口。  
  
## 要求  
 **页眉：** 指令  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnGetMinMaxInfo](../Topic/CWnd::OnGetMinMaxInfo.md)