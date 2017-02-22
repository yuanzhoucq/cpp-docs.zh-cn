---
title: "copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "copysignf"
  - "copysignl"
  - "_copysignl"
  - "_copysign"
  - "_copysignf"
  - "copysign"
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
  - "_copysignl"
  - "copysign"
  - "copysignf"
  - "_copysign"
  - "copysignl"
  - "_copysignf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_copysign 函数"
  - "_copysignf 函数"
  - "_copysignl 函数"
  - "copysign 函数"
  - "copysignf 函数"
  - "copysignl 函数"
ms.assetid: 009216d6-72a2-402d-aa6c-91d924b2c9e4
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回一个值，该值大小同一个参数，符号同另一个参数。  
  
## 语法  
  
```  
double copysign(   
   double x,  
   double y   
);  
float copysign(   
   float x,  
   float y   
); // C++ only  
long double copysign(   
   long double x,  
   long double y   
); // C++ only  
float copysignf(   
   float x,  
   float y   
); // C++ only  
long double copysignl(   
   long double x,  
   long double y   
); // C++ only  
double _copysign(   
   double x,  
   double y   
);  
long double _copysignl(   
   long double x,  
   long double y   
);  
```  
  
#### 参数  
 `x`  
 结果的大小取决于返回的浮点值。  
  
 `y`  
 结果的符号取决于返回的浮点值。  
  
 [浮点支持实例](../../c-runtime-library/floating-point-support.md)  
  
## 返回值  
 `copysign` 函数返回结合了`x`的大小和 `y`的符号的浮点值。  无错误返回。  
  
## 备注  
 由于 C\+\+ 允许重载，因此您可以调用 `copysign` 的重载，该重载采用和返回 `float` 或 `long double` 值。  在 C 程序中，`copysign` 始终采用并返回 `double`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_copysign`|\<float.h\>|  
|`copysign`, `copysignf`, `copysignl`, `_copysignf` `_copysignl`|\<math.h\>|  
  
 有关更多兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [fabs、 fabsf fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [\_chgsign、\_chgsignf、\_chgsignl](../../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)