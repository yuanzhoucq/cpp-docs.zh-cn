---
title: "ABCFLOAT 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ABCFLOAT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ABCFLOAT 结构"
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# ABCFLOAT 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`ABCFLOAT` 结构包含字体字符" A、B 和 C的宽度。  
  
## 语法  
  
```  
  
      typedef struct _ABCFLOAT { /* abcf */  
   FLOAT abcfA;  
   FLOAT abcfB;  
   FLOAT abcfC;  
} ABCFLOAT;  
```  
  
#### 参数  
 *abcfA*  
 指定字符的一个时间间隔。  A 间隔是添加到当前位置的距离在绘制字符标志符号。  
  
 *abcfB*  
 指定字符的B空间。  B 空间是字符标志的绘制的宽度。  
  
 *abcfC*  
 指定字符的C空间。  C空间是添加到当前位置的距离来提供空白字符到字符字形的右边。  
  
## 备注  
 A、B 和 C。宽度测量沿字体的基线对齐。行。  字符始终递增 \(宽度\) 字符为从 A、B 和 C空间的总和。  A或C空间可以是负值来指示 下挂 或上挂。  
  
## 要求  
 "头部：" wingdi.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../Topic/CDC::GetCharABCWidths.md)