---
title: "数学错误常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_PLOSS"
  - "_UNDERFLOW"
  - "_TLOSS"
  - "_SING"
  - "_DOMAIN"
  - "_OVERFLOW"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_DOMAIN 常量"
  - "_OVERFLOW 常量"
  - "_PLOSS 常量"
  - "_SING 常量"
  - "_TLOSS 常量"
  - "_UNDERFLOW 常量"
  - "DOMAIN 常量"
  - "数学错误常量"
  - "OVERFLOW 常量"
  - "PLOSS 常量"
  - "SING 常量"
  - "TLOSS 常量"
  - "UNDERFLOW 常量"
ms.assetid: 4be933a6-674e-45a5-8ac9-090023542f5b
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 数学错误常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <math.h>  
  
```  
  
## 备注  
 运行时库的算术例程可以生成错误数学常数。  
  
 如下所述，这些错误，对应于 MATH.H 定义的异常类型和当数学异常发生时，`_matherr` 函数的返回值。  
  
|常量|含义|  
|--------|--------|  
|`_DOMAIN`|函数的参数是该函数为外部域。|  
|`_OVERFLOW`|结果太大而无法在函数的返回类型中表示。|  
|`_PLOSS`|重要部分发生丢失。|  
|`_SING`|奇点参数：函数的参数有非法值。\(例如， 0被传递给要求非零值的函数。\)|  
|`_TLOSS`|发生全部重要部分的丢失。|  
|`_UNDERFLOW`|结果太小而无法表示。|  
  
## 请参阅  
 [\_matherr](../c-runtime-library/reference/matherr.md)   
 [全局常量](../c-runtime-library/global-constants.md)