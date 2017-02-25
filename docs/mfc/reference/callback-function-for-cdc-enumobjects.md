---
title: "CDC::EnumObjects 的回调函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Callback Function for CDC::EnumObjects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "回调函数, 用于 CDC::EnumObjects"
ms.assetid: 380088b1-88a5-4fb4-bbb5-dd9e8386572b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# CDC::EnumObjects 的回调函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

*ObjectFunc* 名称为应用程序所提供的函数名称的占位符。  
  
## 语法  
  
```  
  
      int CALLBACK EXPORT ObjectFunc(   
   LPSTR lpszLogObject,   
   LPSTR* lpData    
);  
```  
  
#### 参数  
 *lpszLogObject*  
 为包含有关对象的逻辑属性的信息或 [LOGPEN](../../mfc/reference/logpen-structure.md) [LOGBRUSH](../../mfc/reference/logbrush-structure.md) 数据结构的位置。  
  
 `lpData`  
 到应用程序所提供数据的点传递给 `EnumObjects` 函数。  
  
## 返回值  
 回调函数返回 `int`。  此值返回是用户定义。  如果回调函数返回 0，`EnumObjects` 之前停止枚举。  
  
## 备注  
 必须导出实际名称。  
  
## 要求  
 **标头:** afxwin.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::EnumObjects](../Topic/CDC::EnumObjects.md)