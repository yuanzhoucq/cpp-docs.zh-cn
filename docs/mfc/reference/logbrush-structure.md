---
title: "LOGBRUSH 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LOGBRUSH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LOGBRUSH 结构"
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# LOGBRUSH 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`LOGBRUSH` 结构定义画笔的实际样式、颜色和模式。  Windows [CreateBrushIndirect](http://msdn.microsoft.com/library/windows/desktop/dd183487) [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705) 和函数使用。  
  
## 语法  
  
```  
  
      typedef struct tag LOGBRUSH { /* lb */  
   UINT lbStyle;  
   COLORREF lbColor;  
   LONG lbHatch;  
} LOGBRUSH;  
```  
  
#### 参数  
 `lbStyle`  
 指定画笔样式。  `lbStyle` 成员必须是下列样式之一：  
  
-   **BS\_DIBPATTERN** 与设备无关的位图 \(DIB\) 的模式规范定义画笔。  如果 `lbStyle` 为 **BS\_DIBPATTERN**，**lbHatch** 成员包含一个处理到打包的 DIB。  
  
-   **BS\_DIBPATTERNPT** 与设备无关的位图 \(DIB\) 的模式规范定义画笔。  如果 `lbStyle` 为 **BS\_DIBPATTERNPT**，**lbHatch** 成员包含指针到打包的 DIB。  
  
-   **BS\_HATCHED** 孵化的画笔。  
  
-   **BS\_HOLLOW** 凹陷画笔。  
  
-   **BS\_NULL** 和 **BS\_HOLLOW**。  
  
-   **BS\_PATTERN** 定义位图内存的模式画笔。  
  
-   **BS\_SOLID** 纯色画笔。  
  
 `lbColor`  
 指定画笔将用于绘制文本的颜色。  如果 `lbStyle` 是 **BS\_HOLLOW** 或 **BS\_PATTERN**。样式，**lbColor** 被忽略。  如果 `lbStyle` 为 **BS\_DIBPATTERN** 或 **BS\_DIBPATTERNBT**，**lbColor** 低序 [BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md) Word 指定结构的 **bmiColors** 成员是否显式包含红色，绿色，蓝色 \(RGB\) 值或索引到当前的实现逻辑调色板。  此文本**lbColor**值必须为以下值之一：  
  
-   **DIB\_PAL\_COLORS** 表包括颜色数组索引 16 位到当前的实现逻辑调色板。  
  
-   **DIB\_RGB\_COLORS** 常值 RGB 颜色表包含值。  
  
 *lbHatch*  
 指定阴影样式 。  含义取决于与定义的画笔 `lbStyle`样式。  如果 `lbStyle` 为 **BS\_DIBPATTERN**，**lbHatch** 成员包含一个处理到打包的 DIB。  如果 `lbStyle` 为 **BS\_DIBPATTERNPT**，**lbHatch** 成员包含指针到打包的 DIB。  如果 `lbStyle` 为 **BS\_HATCHED**，**lbHatch** 用于成员指定直线的方向创建阴影。  可以是下列值之一：  
  
-   向上`HS_BDIAGONAL` 一 45 度，按从左向右的阴影  
  
-   `HS_CROSS` 水平和垂直的交叉阴影线  
  
-   `HS_DIAGCROSS` 为 45 度、阴影线兼容  
  
-   向下 45 度，阴影的`HS_FDIAGONAL`。  
  
-   `HS_HORIZONTAL` 水平的阴影  
  
-   `HS_VERTICAL` 垂直的阴影  
  
 如果 `lbStyle` 为 **BS\_PATTERN**，则 **lbHatch** 为句柄定义模式的位图。  如果 `lbStyle` 为 **BS\_SOLID** 或 **BS\_HOLLOW**，**lbHatch** 被忽略。  
  
## 备注  
 虽然 **lbColor** 控制阴影画笔的前景色，[CDC::SetBkMode](../Topic/CDC::SetBkMode.md) [CDC::SetBkColor](../Topic/CDC::SetBkColor.md) 函数控制和背景色。  
  
## 要求  
 "头部：" wingdi.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../Topic/CDC::GetCharABCWidths.md)