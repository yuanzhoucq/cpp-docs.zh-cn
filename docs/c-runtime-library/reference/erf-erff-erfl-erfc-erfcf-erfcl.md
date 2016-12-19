---
title: "erf、erff、erfl、erfc、erfcf、erfcl | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "erff"
  - "erfl"
  - "erf"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "erfl"
  - "erf"
  - "erff"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "erf 函数"
  - "erff 函数"
  - "erfl 函数"
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# erf、erff、erfl、erfc、erfcf、erfcl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算某个值的误差函数或补余误差函数。  
  
## 语法  
  
```  
double erf(    double x ); float erf(    float x ); // C++ only long double erf(    long double x ); // C++ only float erff(    float x ); long double erfl(    long double x ); double erfc(    double x ); float erfc(    float x ); // C++ only long double erfc(    long double x ); // C++ only float erfcf(    float x ); long double erfcl(    long double x );  
```  
  
#### 参数  
 `x`  
 浮点值。  
  
## 返回值  
 `erf` 函数返回 `x` 的高斯误差函数。  `erfc` 函数返回 `x` 的补余高斯误差函数。  
  
## 备注  
 `erf` 函数计算 x 的高斯误差函数，定义如下：  
  
 ![x 的错误函数](../../c-runtime-library/reference/media/crt_erf_formula.png "CRT\_erf\_formula")  
  
 将补余高斯误差函数定义为 1 – erf\(x\)。  `erf` 函数返回一个介于 \-1.0 到 1.0 之间的值。  无错误返回。  `erfc` 函数返回一个介于 0 到 2 之间的值。  如果 `x` 对于 `erfc` 而言太大，则将 `errno` 变量设置为 `ERANGE`。  
  
 由于 C\+\+ 允许重载，因此你可以调用采用并返回 `float` 和 `long double` 类型的 `erf` 和 `erfc` 重载。  在 C 程序中，`erf` 和 `erfc` 始终采用并返回 `double`。  
  
## 要求  
  
|函数|必需的标头|  
|--------|-----------|  
|`erf`, `erff`, `erfl`, `erfc`, `erfcf`, `erfcl`|\<math.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)