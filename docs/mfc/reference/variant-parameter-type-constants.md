---
title: "变量参数类型常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VTS_YPOS_HIMETRIC"
  - "VTS_PICTURE"
  - "VTS_FONT"
  - "VTS_XPOS_HIMETRIC"
  - "VTS_XPOS_PIXELS"
  - "VTS_XSIZE_HIMETRIC"
  - "VTS_YPOS_PIXELS"
  - "VTS_TRISTATE"
  - "VTS_HANDLE"
  - "VTS_YSIZE_HIMETRIC"
  - "VTS_COLOR"
  - "VTS_OPTEXCLUSIVE"
  - "VTS_YSIZE_PIXELS"
  - "VTS_XSIZE_PIXELS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "变量数据常量"
  - "变量"
  - "变量, 参数类型常量"
  - "VTS_COLOR 常量"
  - "VTS_FONT 常量"
  - "VTS_HANDLE 常量"
  - "VTS_OPTEXCLUSIVE 常量"
  - "VTS_PICTURE 常量"
  - "VTS_TRISTATE 常量"
  - "VTS_XPOS_HIMETRIC 常量"
  - "VTS_XPOS_PIXELS 常量"
  - "VTS_XSIZE_HIMETRIC 常量"
  - "VTS_XSIZE_PIXELS 常量"
  - "VTS_YPOS_HIMETRIC 常量"
  - "VTS_YPOS_PIXELS 常量"
  - "VTS_YSIZE_HIMETRIC 常量"
  - "VTS_YSIZE_PIXELS 常量"
ms.assetid: de99c7a9-7aae-4dc4-b723-40c6380543ab
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 变量参数类型常量
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题列出一用于设计的不同参数类型使用 Microsoft 基础类库类的新的 OLE 控件的常数。  
  
 下面是类常量的列表：  
  
##  <a name="_mfc_variant_data_constants"></a> 不同的常数数据  
  
-   **VTS\_COLOR** 32 位整数用于显示 RGB 颜色值。  
  
-   对字体 OLE 对象的 **IFontDisp** 接口的指针**VTS\_FONT**。  
  
-   **VTS\_HANDLE**窗口句柄值。  
  
-   将 OLE 图片对象的 `IPictureDisp` 接口的指针**VTS\_PICTURE**。  
  
-   打算用于在一组控件的控件的**VTS\_OPTEXCLUSIVE** 16 位值，如单选按钮。  此通知类型容器，如果一个控件组中具有 **TRUE** 值，另必须是 **FALSE**。  
  
-   用于可以具有三个可能值之一的属性**VTS\_TRISTATE** 16 位带符号整数 \(，选择清除不可用\)，例如，复选框。  
  
-   **HIMETRIC** 中单元用于表示沿 x 轴的位置**VTS\_XPOS\_HIMETRIC** 32 位无符号整数。  
  
-   **HIMETRIC** 中单元用于表示沿 Y 轴移动的位置**VTS\_YPOS\_HIMETRIC** 32 位无符号整数。  
  
-   以像素用于表示沿 x 轴的位置**VTS\_XPOS\_PIXELS** 32 位无符号整数。  
  
-   以像素用于表示沿 Y 轴移动的位置**VTS\_YPOS\_PIXELS** 32 位无符号整数。  
  
-   **VTS\_XSIZE\_PIXELS** 32 位无符号整数用于表示屏幕对象的宽度 \(以像素为单位\)。  
  
-   **VTS\_YSIZE\_PIXELS** 32 位无符号整数用于表示屏幕对象的高度 \(以像素为单位\)。  
  
-   **VTS\_XSIZE\_HIMETRIC** 32 位无符号整数用于表示屏幕对象的宽度。**HIMETRIC** 单元的。  
  
-   **VTS\_YSIZE\_HIMETRIC** 32 位无符号整数用于表示屏幕对象的高度单位在 **HIMETRIC** 的。  
  
    > [!NOTE]
    >  除了 **VTS\_FONT** 和 **VTS\_PICTURE**之外，其他不同的常数的所有不同类型定义，提供了指向不同的常数。数据，  使用 **VTS\_P**`constantname` 约定，这些常量名为。  例如，**VTS\_PCOLOR** 是指向 **VTS\_COLOR** 常数。  
  
## 要求  
 "头部：" afxdisp.h  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)