---
title: "cos、cosf、cosl、cosh、coshf、coshl | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "coshl"
  - "cosh"
  - "cos"
  - "cosl"
  - "cosf"
  - "coshf"
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
  - "coshl"
  - "cos"
  - "cosf"
  - "cosh"
  - "cosl"
  - "coshf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "计算余弦值"
  - "cos 函数"
  - "cosf 函数"
  - "cosh 函数"
  - "coshf 函数"
  - "coshl 函数"
  - "余弦"
  - "余弦, 计算"
  - "cosl 函数"
  - "双曲函数"
  - "三角函数"
ms.assetid: ae90435e-6b68-4a47-a81f-be87d5c08f16
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# cos、cosf、cosl、cosh、coshf、coshl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算余弦值 \(`cos`、`cosf`或 `cosl`\)，或者双曲余弦 \(`cosh`、`coshf`或 `coshl`\)。  
  
## 语法  
  
```  
double cos(   
   double x   
);  
float cos(  
   float x   
);  // C++ only  
long double cos(  
   long double x  
);  // C++ only  
float cosf(   
   float x   
);  
long double cosl(  
   long double x  
);  
double cosh(   
   double x   
);  
float cosh(  
   float x   
);  // C++ only  
long double cosh(  
   long double x  
);  // C++ only  
float coshf(  
   float x   
);  
long double coshl(  
   long double x  
);  
```  
  
#### 参数  
 `x`  
 弧度上的角度。  
  
## 返回值  
 余弦值或 `x`双曲余弦值。  如果 `x` 大于或等于 263 或小于或等于– 263，调用`cos`，`cosf`或 `cosl`的会造成有效位丢失。  
  
 默认情况下，如果`cosh`、`coshf`或 `coshl` 调用的结果太大，该函数返回 `HUGE_VAL` 并将 `errno` 设置为 `ERANGE`。  
  
|输入|SEH 异常|Matherr 异常|  
|--------|------------|----------------|  
|± `QNAN`,`IND`|无|`_DOMAIN`|  
|± ∞  \(`cosf`, `cos`, `cosl`\)|`INVALID`|`_DOMAIN`|  
|x ≥ 7.104760e\+002 \(`cosh`、`coshf`，`coshl`\)|`INEXACT`\+`OVERFLOW`|`OVERFLOW`|  
  
## 备注  
 由于 C\+\+ 允许重载，您可以调用 `cos` 和 `cosh` 的重载，该重载采用和返回 `float` 或 `long double` 值。  在 C 程序中，`cos` 和 `cosh` 始终采用并返回 `double`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`cos`, `cosh`, `cosf`, `coshf`, `cosl`, `coshl`|\<math.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参见 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md) 中的示例。  
  
## .NET Framework 等效项  
  
-   [System::Math::Cos](https://msdn.microsoft.com/en-us/library/system.math.cos.aspx)  
  
-   [System::Math::Cosh](https://msdn.microsoft.com/en-us/library/system.math.cosh.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin、asinf、asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [\_CIcos](../../c-runtime-library/cicos.md)