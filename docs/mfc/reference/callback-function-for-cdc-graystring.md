---
title: "CDC::GrayString 的回调函数 | Microsoft Docs"
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
  - "Callback Function for CDC::GrayString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "回调函数, 对于 CDC::GrayString"
ms.assetid: 5217e183-df48-426b-931b-6245022ca36f
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDC::GrayString 的回调函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

*OutputFunc* 是逐个应用程序供应的回调函数名称的占位符。  
  
## 语法  
  
```  
  
      BOOL CALLBACK EXPORT OutputFunc(   
   HDC hDC,   
   LPARAM lpData,   
   int nCount    
);  
```  
  
#### 参数  
 `hDC`  
 标识使用 `nWidth` 以及 `nHeight` 和指定高度的位图的内存设备上下文至少宽度设置为 `GrayString`。  
  
 `lpData`  
 指向要绘制的字符串。  
  
 `nCount`  
 指定字符数输出。  
  
## 返回值  
 回调函数的返回值必须是指示成功的 **TRUE** ;否则它是 **FALSE**。  
  
## 备注  
 回调函数 \(\)*OutputFunc*必须绘制图像相对于坐标 \(0,0\) 而不是 \(*x*，*y\)*。  
  
## 要求  
 **标头:** afxwin.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GrayString](../Topic/CDC::GrayString.md)