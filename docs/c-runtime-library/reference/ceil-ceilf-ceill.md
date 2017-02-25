---
title: "ceil、ceilf、ceill | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ceilf"
  - "ceil"
  - "ceill"
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
  - "ceil"
  - "ceilf"
  - "ceill"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "计算值的上限"
  - "ceil 函数"
  - "ceilf 函数"
  - "ceill 函数"
ms.assetid: f4e5acab-5c8f-4b10-9ae2-9561e6453718
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# ceil、ceilf、ceill
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算值的上限。  
  
## 语法  
  
```  
double ceil(   
   double x   
);  
float ceil(  
   float x  
);  // C++ only  
long double ceil(  
   long double x  
);  // C++ only  
float ceilf(  
   float x  
);  
long double ceill(  
   long double x  
);  
```  
  
#### 参数  
 `x`  
 浮点值。  
  
## 返回值  
 `ceil` 函数返回表示最小整数的浮点值，该值大于或等于 `x`。  无错误返回。  
  
|输入|SEH 异常|Matherr 异常|  
|--------|------------|----------------|  
|± `QNAN`,`IND`|无|`_DOMAIN`|  
  
 `ceil` 具有使用Streaming SIMD Extensions 2\(SSE2\)的实现。  有关使用SSE2实现的信息和限制，请参见 [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
## 备注  
 由于 C\+\+ 允许重载，可以调用 `ceil`重载函数。  在 C 程序中，`ceil` 始终采用并返回double值。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`ceil`, `ceilf`, `ceill`|\<math.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参阅 [floor](../../c-runtime-library/reference/floor-floorf-floorl.md) 示例。  
  
## .NET Framework 等效项  
 [System::Math::Ceiling](https://msdn.microsoft.com/en-us/library/system.math.ceiling.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [fmod, fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [round、roundf、roundl](../../c-runtime-library/reference/round-roundf-roundl.md)