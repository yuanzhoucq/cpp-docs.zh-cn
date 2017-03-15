---
title: "_locking 常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_LK_RLCK"
  - "_LK_NBLCK"
  - "_LK_LOCK"
  - "_LK_NBRLCK"
  - "_LK_UNLCK"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_LK_LOCK 常量"
  - "_LK_NBLCK 常量"
  - "_LK_NBRLCK 常量"
  - "_LK_RLCK 常量"
  - "_LK_UNLCK 常量"
  - "LK_LOCK 常量"
  - "LK_NBLCK 常量"
  - "LK_NBRLCK 常量"
  - "LK_RLCK 常量"
  - "LK_UNLCK 常量"
ms.assetid: c3dc92c8-60e3-4d29-9f50-5d217627c8ad
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# _locking 常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <sys/locking.h>  
  
```  
  
## 备注  
 在调用的 *模式* 参数设置为 `_locking` 锁定函数指定的要执行的操作。  
  
 清单常数 *模式* 参数必须为下列之一。  
  
 `_LK_LOCK`  
 锁定指定字节。  如果字节无法锁定，函数在 1 秒后再次调用。  如果10 多次尝试后字节无法锁定后，函数返回 FALSE。  
  
 `_LK_RLCK`  
 与 `_LK_LOCK` 相同。  
  
 `_LK_NBLCK`  
 锁定指定字节。  如果字节无法锁定，函数返回 FALSE。  
  
 `_LK_NBRLCK`  
 与 `_LK_NBLCK` 相同。  
  
 `_LK_UNLCK`  
 解开指定字节。\(之前必须已锁定字节。\)  
  
## 请参阅  
 [\_locking](../c-runtime-library/reference/locking.md)   
 [全局常量](../c-runtime-library/global-constants.md)