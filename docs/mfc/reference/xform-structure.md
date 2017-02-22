---
title: "XFORM 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "XFORM"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "XFORM 结构"
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# XFORM 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`XFORM` 结构都有以下形式：  
  
## 语法  
  
```  
  
      typedef struct  tagXFORM {  /* xfrm */  
    FLOAT eM11;  
    FLOAT eM12;  
    FLOAT eM21;  
    FLOAT eM22;  
    FLOAT eDx;  
    FLOAT eDy;  
} XFORM;  
```  
  
## 备注  
 `XFORM` 结构指定世界空间对页空间转换。  **eDx** 和 **eDy** 成员指定水平和垂直转换，组件。  下表根据操作查看如何使用其他成员，例如：  
  
|Operation|eM11|eM12|eM21|eM22|  
|---------------|----------|----------|----------|----------|  
|`Rotation`|旋转角度余弦值|旋转角度余弦值|旋转角度负正弦值|旋转角度余弦值|  
|**缩放**|水平缩放组件|Nothing|Nothing|垂直缩放组件|  
|**剪切**|Nothing|水平的大于率性常数|垂直于率性常数|Nothing|  
|**反射**|水平的反射组件|Nothing|Nothing|垂直的反射组件|  
  
## 要求  
 "头部：" wingdi.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../Topic/CRgn::CreateFromData.md)