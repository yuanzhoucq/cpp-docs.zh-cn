---
title: "_FREEENTRY、_USEDENTRY | Microsoft Docs"
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
  - "USEDENTRY"
  - "_USEDENTRY"
  - "_FREEENTRY"
  - "FREEENTRY"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_FREEENTRY 常量"
  - "_USEDENTRY 常量"
  - "FREEENTRY 常量"
  - "USEDENTRY 常量"
ms.assetid: 26f658e6-6846-4a4e-9984-262cfe392770
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _FREEENTRY、_USEDENTRY
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
#include <malloc.h>  
```  
  
## 备注  
 这些常量表示 `_heapwalk` 例程分配的值设置为 **\_HEAPINFO** 的结构的**\_useflag** 元素。  它们指示堆输出的状态。  
  
## 请参阅  
 [\_heapwalk](../c-runtime-library/reference/heapwalk.md)   
 [全局常量](../c-runtime-library/global-constants.md)