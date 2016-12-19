---
title: "POINT 结构 | Microsoft Docs"
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
  - "POINT"
  - "LPPOINT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LPPOINT 结构"
  - "POINT 结构"
ms.assetid: 965736d8-4e53-41b6-9b8b-6961992dd21f
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# POINT 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

该 **POINT**结构定义在x*\-*点和y坐标。  
  
## 语法  
  
```  
  
      typedef struct tagPOINT {  
   LONG x;  
   LONG y;  
} POINT;  
```  
  
#### 参数  
 *x*  
 指定点的 x 坐标。  
  
 *y*  
 指定点的 y 坐标。  
  
## 示例  
 [!code-cpp[NVC_MFC_Utilities#37](../../mfc/codesnippet/CPP/point-structure1_1.cpp)]  
  
## 要求  
 **标头:** windef.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPoint Class](../../atl-mfc-shared/reference/cpoint-class.md)