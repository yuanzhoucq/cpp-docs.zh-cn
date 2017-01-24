---
title: "WINDOWPLACEMENT 结构 | Microsoft Docs"
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
  - "WINDOWPLACEMENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WINDOWPLACEMENT 结构"
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WINDOWPLACEMENT 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`WINDOWPLACEMENT` 结构包含有关窗口中的位置的信息的屏幕上的 \#\#\#.  
  
## 语法  
  
```  
  
      typedef struct tagWINDOWPLACEMENT {     /* wndpl */  
   UINT length;  
   UINT flags;  
   UINT showCmd;  
   POINT ptMinPosition;  
   POINT ptMaxPosition;  
   RECT rcNormalPosition;  
} WINDOWPLACEMENT;  
```  
  
#### 参数  
 *length*  
 以字节，结构指定长度，\#\#\#.  
  
 `flags`  
 指定控制最小化窗口和窗口位置方法还原的标志。  该成员可为下列标记之一或两步：  
  
-   **WPF\_SETMINPOSITION** 指定两种最小化窗口的 x 和 y 位置可以是指定的 \#\#\#.必须指定此标志坐标是否在 **ptMinPosition** 成员设置。  
  
-   **WPF\_RESTORETOMAXIMIZED** 指定的窗口将还原最大化，无论它是否处于最大化，则减少。  当下次窗口还原，这将有效。  它不更改恢复默认行为。  在 **SW\_SHOWMINIMIZED** 值为 **showCmd** 成员时，指定此标志有效。  
  
 *showCmd*  
 指定窗口的当前状态显示。  该成员可以是下列值之一：  
  
-   **SW\_HIDE** 窗口隐藏并通过活动到另一个窗口。  
  
-   **SW\_MINIMIZE** 使指定窗口并激活在系统的列表的顶级窗口。  
  
-   **SW\_RESTORE** 激活并显示窗口。  如果窗口最大化或最小化，窗口将还原为其原始大小和位置 \(等同于 **SW\_SHOWNORMAL**\)。  
  
-   **SW\_SHOW** 激活窗口并显示在其当前大小和位置。  
  
-   **SW\_SHOWMAXIMIZED** 激活窗口并显示其为最大化窗口的大小。  
  
-   **SW\_SHOWMINIMIZED** 窗口激活和显示为图标。  
  
-   **SW\_SHOWMINNOACTIVE** 窗口显示为图标。  可保留当前活动的窗口中。  
  
-   **SW\_SHOWNA** 显示其当前状态的窗口。  可保留当前活动的窗口中。  
  
-   **SW\_SHOWNOACTIVATE** 显示其最近大小和位置的窗口。  可保留当前活动的窗口中。  
  
-   **SW\_SHOWNORMAL** 激活并显示窗口。  如果窗口最大化或最小化，窗口将还原为其原始大小和位置 \(等同于 **SW\_RESTORE**\)。  
  
 *ptMinPosition*  
 在窗口处于最小化时，用于指定窗口的左上角的位置。  
  
 `ptMaxPosition`  
 当窗口为最大化时，用于指定窗口的左上角的位置。  
  
 *rcNormalPosition*  
 指定窗口的坐标时，窗口位于正常 \(还原\) 时的位置。  
  
## 要求  
 **页眉：** 指令  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::SetWindowPlacement](../Topic/CWnd::SetWindowPlacement.md)