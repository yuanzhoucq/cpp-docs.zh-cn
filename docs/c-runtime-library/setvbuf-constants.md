---
title: "setvbuf 常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_IOFBF"
  - "_IONBF"
  - "_IOLBF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_IOFBF 常量"
  - "_IOLBF 常量"
  - "_IONBF 常量"
  - "IOFBF 常量"
  - "IOLBF 常量"
  - "IONBF 常量"
ms.assetid: a6ec4dd5-1f24-498c-871a-e874cd28d33c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# setvbuf 常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <stdio.h>  
  
```  
  
## 备注  
 这些常量表示缓冲区的 `setvbuf`。  
  
 下面的清单常数为可能的值：  
  
|常量|含义|  
|--------|--------|  
|`_IOFBF`|完全缓冲的：为 `setvbuf` 使用在调用指定的缓冲区，其范围是在 `setvbuf` 调用中指定。  如果缓冲区的指针是 **NULL**，使用指定的大小自动分配的缓冲区。|  
|`_IOLBF`|与 `_IOFBF` 相同。|  
|`_IONBF`|无论参数在对 `setvbuf`的调用，缓冲区不可用。|  
  
## 请参阅  
 [setbuf](../c-runtime-library/reference/setbuf.md)   
 [全局常量](../c-runtime-library/global-constants.md)