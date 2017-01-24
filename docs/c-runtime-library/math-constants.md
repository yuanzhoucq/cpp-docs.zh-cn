---
title: "数学常量 | Microsoft Docs"
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
  - "c.constants"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_USE_MATH_DEFINES 常量"
  - "常量, 算术"
  - "M_1_PI 常量"
  - "M_2_PI 常量"
  - "M_2_SQRTPI 常量"
  - "M_E 常量"
  - "M_LN10 常量"
  - "M_LN2 常量"
  - "M_LOG10E 常量"
  - "M_LOG2E 常量"
  - "M_PI 常量"
  - "M_PI_2 常量"
  - "M_PI_4 常量"
  - "M_SQRT1_2 常量"
  - "M_SQRT2 常量"
  - "数学常量"
  - "USE_MATH_DEFINES 常量"
ms.assetid: db533c3f-6ae8-4520-9d35-c8fabbef3529
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 数学常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
#define _USE_MATH_DEFINES // for C++  
#include <cmath>  
  
#define _USE_MATH_DEFINES // for C  
#include <math.h>  
```  
  
## 备注  
 下列符号值指示的表达式中定义：  
  
|符号|表达式|值|  
|--------|---------|-------|  
|M\_E|e|2.71828182845904523536|  
|M\_LOG2E|log2\(e\)|1.44269504088896340736|  
|M\_LOG10E|log10\(e\)|0.434294481903251827651|  
|M\_LN2|ln\(2\)|0.693147180559945309417|  
|M\_LN10|ln\(10\)|2.30258509299404568402|  
|M\_PI|pi|3.14159265358979323846|  
|M\_PI\_2|pi\/2|1.57079632679489661923|  
|M\_PI\_4|pi\/4|0.785398163397448309616|  
|M\_1\_PI|1\/pi|0.318309886183790671538|  
|M\_2\_PI|2\/pi|0.636619772367581343076|  
|M\_2\_SQRTPI|2\/sqrt\(pi\)|1.12837916709551257390|  
|M\_SQRT2|sqrt\(2\)|1.41421356237309504880|  
|M\_SQRT1\_2|1\/sqrt\(2\)|0.707106781186547524401|  
  
 数学常数在标准 C\/C\+\+ 未定义。  要使用它们，必须首先定义 `_USE_MATH_DEFINES` 并包括 cmath或math.h。  
  
 项目时，在发布模式下时，所生成文件 ATLComTime.h 包括 math.h。  如果在包含的项目还 ATLComTime.h 使用一个或多个数学常数，您必须定义 `_USE_MATH_DEFINES`，在包含 ATLComTime.h 之前。  
  
## 请参阅  
 [全局常量](../c-runtime-library/global-constants.md)