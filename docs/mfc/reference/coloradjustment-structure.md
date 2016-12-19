---
title: "COLORADJUSTMENT 结构 | Microsoft Docs"
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
  - "COLORADJUSTMENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLORADJUSTMENT 结构"
ms.assetid: 67fc4e63-0e0e-4fcb-8c45-aa5ebfefa013
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COLORADJUSTMENT 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

模式，当 `StretchBlt` 为 **HALFTONE**时，`COLORADJUSTMENT` 结构定义 Windows `StretchBlt` 和 **StretchDIBits** 函数使用的颜色。调整值。  
  
## 语法  
  
```  
  
      typedef struct  tagCOLORADJUSTMENT {    /* ca */  
    WORD  caSize;  
    WORD  caFlags;  
    WORD  caIlluminantIndex;  
    WORD  caRedGamma;  
    WORD  caGreenGamma;  
    WORD  caBlueGamma;  
    WORD  caReferenceBlack;  
    WORD  caReferenceWhite;  
    SHORT caContrast;  
    SHORT caBrightness;  
    SHORT caColorfulness;  
    SHORT caRedGreenTint;  
} COLORADJUSTMENT;  
```  
  
#### 参数  
 *caSize*  
 指定结构的大小（以字节为单位）。  
  
 *caFlags*  
 指定应该如何准备输出映像。  该成员可设置为以下值 **NULL** 或的任意组合：  
  
-   **CA\_NEGATIVE** 指定应显示原始图像的负值。  
  
-   **CA\_LOG\_FILTER** 指定一个应用对数函数到输出颜色的最终密度。  当这不足，这将增加颜色对比度。  
  
 *caIlluminantIndex*  
 指定图像对象下显示光源的亮度。  在这种情况下， 设置为下列值之一。  
  
-   **ILLUMINANT\_EQUAL\_ENERGY**  
  
-   **ILLUMINANT\_A**  
  
-   **ILLUMINANT\_B**  
  
-   **ILLUMINANT\_C**  
  
-   **ILLUMINANT\_D50**  
  
-   **ILLUMINANT\_D55**  
  
-   **ILLUMINANT\_D65**  
  
-   **ILLUMINANT\_D75**  
  
-   **ILLUMINANT\_F2**  
  
-   **ILLUMINANT\_TURNGSTEN**  
  
-   **ILLUMINANT\_DAYLIGHT**  
  
-   **ILLUMINANT\_FLUORESCENT**  
  
-   **ILLUMINANT\_NTSC**  
  
 *caRedGamma*  
 为红色指定第 N 个功能校正值主源颜色。  值必须在的范围从 2,500 到 65,000。  值 10,000 表示未启用伽玛矫正。  
  
 *caGreenGamma*  
 为绿色指定第 N 个功能校正值主源颜色。  值必须在的范围从 2,500 到 65,000。  值 10,000 表示未启用伽玛矫正。  
  
 *caBlueGamma*  
 为蓝色指定第 N 个功能校正值主源颜色。  值必须在的范围从 2,500 到 65,000。  值 10,000 表示未启用伽玛矫正。  
  
 *caReferenceBlack*  
 为源颜色黑色指定引用。  比此暗的任何颜色视为相交。  值必须在的范围从 0 到 4,000。  
  
 *caReferenceWhite*  
 为源颜色白色指定引用。  比此光的任何颜色将白色。  值必须在的范围从 6,000 到 10,000。  
  
 *caContrast*  
 指定将应用的量对比度到源对象。  值必须在的范围从 \-100 到 100。  值 0 意味着不对比度调整。  
  
 *caBrightness*  
 指定将应用的量量度到源对象。  值必须在的范围从 \-100 到 100。  值 0 意味着不亮度调整。  
  
 *caColorfulness*  
 指定将应用的量颜色度到源对象。  值必须在的范围从 \-100 到 100。  值 0 意味着不色度调整。  
  
 *caRedGreenTint*  
 指定红色或绿色要应用的淡色调整到源对象。  值必须在的范围从 \-100 到 100。  正数进行调整在红色，并且调整负数在绿色。  次不意味着淡色调整。  
  
## 要求  
 "头部：" wingdi.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetColorAdjustment](../Topic/CDC::GetColorAdjustment.md)