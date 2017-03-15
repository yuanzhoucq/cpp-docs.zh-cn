---
title: "asin、asinf、asinl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "asinf"
  - "asinl"
  - "asin"
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
  - "asin"
  - "asinl"
  - "asinf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "反正弦函数"
  - "asin 函数"
  - "asinf 函数"
  - "asinl 函数"
  - "三角函数"
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# asin、asinf、asinl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算反正弦值。  
  
## 语法  
  
```  
double asin(   
   double x   
);  
float asin(  
   float x  
);  // C++ only  
long double asin(  
   long double x  
);  // C++ only  
float asinf (   
   float x   
);  
long double asinl(  
   long double x  
);  
```  
  
#### 参数  
 `x`  
 要计算的反正弦值。  
  
## 返回值  
 `asin` 函数返回`x`的反正弦值 \(反正弦值函数\) ，弧度范围在–π\/2到π\/2。  
  
 默认情况下，如果 `x` 小于–1 或大于 1，`asin`返回未定义值。  
  
|输入|SEH 异常|Matherr 异常|  
|--------|------------|----------------|  
|± ∞|`INVALID`|`_DOMAIN`|  
|± `QNAN`,`IND`|无|`_DOMAIN`|  
|&#124;x&#124;\>1|`INVALID`|`_DOMAIN`|  
  
## 备注  
 由于 C\+\+ 允许重载，可以调用 `asin`的拥有 `float` 和 `long double` 值的重载函数。  在 C 程序中，`asin` 始终采用并返回double值。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`asin`, `asinf`, `asinl`|\<math.h\>|  
  
## 示例  
 有关详细信息，请参阅[acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)。  
  
## .NET Framework 等效项  
 [System::Math::Asin](https://msdn.microsoft.com/en-us/library/system.math.asin.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)