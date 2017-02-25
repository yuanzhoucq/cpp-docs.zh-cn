---
title: "滚动条样式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SBS_VERT"
  - "SBS_SIZEBOXBOTTOMRIGHTALIGN"
  - "SBS_LEFTALIGN"
  - "SBS_RIGHTALIGN"
  - "SBS_TOPALIGN"
  - "SBS_SIZEBOXTOPLEFTALIGN"
  - "SBS_BOTTOMALIGN"
  - "SBS_SIZEBOX"
  - "SBS_HORZ"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SBS_BOTTOMALIGN 常量"
  - "SBS_HORZ 常量"
  - "SBS_LEFTALIGN 常量"
  - "SBS_RIGHTALIGN 常量"
  - "SBS_SIZEBOX 常量"
  - "SBS_SIZEBOXBOTTOMRIGHTALIGN 常量"
  - "SBS_SIZEBOXTOPLEFTALIGN 常量"
  - "SBS_TOPALIGN 常量"
  - "SBS_VERT 常量"
  - "滚动条, 样式"
ms.assetid: 8bcde35b-387d-49ae-bdd6-7cda9f5dae26
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 滚动条样式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   **SBS\_BOTTOMALIGN** 与 **SBS\_HORZ** 使用的样式。  滚动条的下边缘对齐。在 **创建** 成员函数中指定矩形下边缘。  系统具有滚动条滚动条的默认高度。  
  
-   **SBS\_HORZ**指定一个水平滚动条。  如果 **SBS\_BOTTOMALIGN** 和 **SBS\_TOPALIGN**，样式不指定滚动条具有给定的高度、宽度和位置。**创建** 成员函数。  
  
-   **SBS\_LEFTALIGN**与**SBS\_VERT**风格。  滚动条的左边缘对齐。在 **创建** 成员函数中指定矩形左边缘。  系统具有滚动条滚动条的默认宽。  
  
-   **SBS\_RIGHTALIGN**与**SBS\_VERT**风格。  滚动条的右边缘对齐。在 **创建** 成员函数中指定矩形右边缘。  系统具有滚动条滚动条的默认宽。  
  
-   **SBS\_SIZEBOX** 指定一种大小控制块。  如果 **SBS\_SIZEBOXBOTTOMRIGHTALIGN** 和 **SBS\_SIZEBOXTOPLEFTALIGN**，样式不指定大小控制块具有给定的高度、宽度和位置。**创建** 成员函数。  
  
-   **SBS\_SIZEBOXBOTTOMRIGHTALIGN** 与 **SBS\_SIZEBOX** 使用的样式。  大小控制块的右下角对齐。在 **创建** 成员函数中指定矩形的右下角。  控制块大小有系统调整框的默认大小。  
  
-   **SBS\_SIZEBOXTOPLEFTALIGN** 与 **SBS\_SIZEBOX** 使用的样式。  大小控制块的左上角对齐。在 **创建** 成员函数中指定矩形的左上角。  控制块大小有系统调整框的默认大小。  
  
-   **SBS\_SIZEGRIP** 并 **SBS\_SIZEBOX**相同，但是，与一个凸出的边缘。  
  
-   **SBS\_TOPALIGN** 与 **SBS\_HORZ** 使用的样式。  滚动条的上边缘对齐。在 **创建** 成员函数中指定矩形上边缘。  系统具有滚动条滚动条的默认高度。  
  
-   **SBS\_VERT**指定垂直滚动条。  如果 **SBS\_RIGHTALIGN** 和 **SBS\_LEFTALIGN**，样式不指定滚动条具有给定的高度、宽度和位置。**创建** 成员函数。  
  
## 请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)   
 [CScrollBar::Create](../Topic/CScrollBar::Create.md)   
 [Scroll Bar Control Styles](http://msdn.microsoft.com/library/windows/desktop/bb787533)