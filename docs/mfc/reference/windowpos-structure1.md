---
title: "WINDOWPOS 结构 | Microsoft Docs"
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
  - "WINDOWPOS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WINDOWPOS 结构"
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WINDOWPOS 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`WINDOWPOS` 结构包含有关该窗口的大小和位置的信息。  
  
## 语法  
  
```  
  
      typedef struct tagWINDOWPOS { /* wp */  
   HWND hwnd;  
   HWND hwndInsertAfter;  
   int x;  
   int y;  
   int cx;  
   int cy;  
   UINT flags;  
} WINDOWPOS;  
```  
  
#### 参数  
 *hwnd*  
 标识窗口。  
  
 *hwndInsertAfter*  
 标识后此窗口放置在的窗口。  
  
 *x*  
 定义窗口左边缘的位置。  
  
 *y*  
 定义窗口右边缘的位置。  
  
 `cx`  
 以像素为单位的窗口宽度。  
  
 `cy`  
 以像素为单位的窗口高度。  
  
 `flags`  
 指定窗口定位选项。  此成员可为下列值之一：  
  
-   在**SWP\_DRAWFRAME** 窗口周围绘制帧 \(定义窗口中的类演示\)。  窗口接收 `WM_NCCALCSIZE` 消息。  
  
-   **SWP\_FRAMECHANGED** 将 `WM_NCCALCSIZE` 信息到窗口，窗口大小，即使未更改。  如果不指定此标志，`WM_NCCALCSIZE` 发送时，窗口大小的改变时。  
  
-   **SWP\_HIDEWINDOW** 窗口隐藏。  
  
-   `SWP_NOACTIVATE`窗口便不会被激活。  
  
-   **SWP\_NOCOPYBITS** 将工作区的所有内容。  如果不指定此标志，工作区将有效的内容保存并复制回工作区，在窗口大小和重新定位。  
  
-   `SWP_NOMOVE` 保留当前位置 \(忽略 **x** 和 **y** 成员\)。  
  
-   **SWP\_NOOWNERZORDER** 未改变在 Z 顺序的所有者窗口的位置。  
  
-   `SWP_NOSIZE` 保留当前大小 \(忽略 **cx** 和 **cy** 成员\)。  
  
-   **SWP\_NOREDRAW** 不绘制更改。  
  
-   **SWP\_NOREPOSITION** 和 **SWP\_NOOWNERZORDER**。  
  
-   **SWP\_NOSENDCHANGING** 防止窗口接收 `WM_WINDOWPOSCHANGING` 消息。  
  
-   `SWP_NOZORDER` 保留当前排序 \(忽略 **hwndInsertAfter** 成员\)。  
  
-   显示**SWP\_SHOWWINDOW**窗口。  
  
## 要求  
 **页眉：** 指令  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnWindowPosChanging](../Topic/CWnd::OnWindowPosChanging.md)