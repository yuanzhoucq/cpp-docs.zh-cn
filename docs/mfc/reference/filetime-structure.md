---
title: "FILETIME 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FILETIME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FILETIME 结构"
ms.assetid: e09557e2-b6d7-4dd5-a5b9-6328bca88595
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# FILETIME 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`FILETIME` 结构表示为 100 纳秒间隔的数量为 64 位值之后 1601 年 1 月 1 日。  
  
## 语法  
  
```  
  
      typedef struct _FILETIME {  
   DWORD dwLowDateTime;   /* low 32 bits  */  
   DWORD dwHighDateTime;  /* high 32 bits */  
} FILETIME, *PFILETIME, *LPFILETIME;  
```  
  
#### 参数  
 *dwLowDateTime*  
 指定文件时的右下角 32 位。  
  
 *dwHighDateTime*  
 指定文件时的高 32 位。  
  
## 要求  
 **标头:** windef.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../Topic/CTime::CTime.md)