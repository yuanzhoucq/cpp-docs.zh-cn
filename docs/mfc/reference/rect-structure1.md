---
title: "RECT 结构 | Microsoft Docs"
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
  - "LPRECT"
  - "RECT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LPRECT 结构"
  - "RECT 结构"
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RECT 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`RECT`结构定义矩形左上角和右下角的坐标。  
  
## 语法  
  
```  
  
      typedef struct tagRECT {   
   LONG left;  
   LONG top;  
   LONG right;  
   LONG bottom;  
} RECT;  
```  
  
## 成员  
 `left`  
 指定矩形左上角的 x 坐标。  
  
 `top`  
 指定矩形左上角的 y 坐标。  
  
 `right`  
 指定矩形右下角的 x 坐标。  
  
 `bottom`  
 指定矩形右下角的 y 坐标。  
  
## 示例  
 [!code-cpp[NVC_MFC_Utilities#38](../../mfc/codesnippet/CPP/rect-structure1_1.cpp)]  
  
## 要求  
 **标头:** windef.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRect Class](../../atl-mfc-shared/reference/crect-class.md)