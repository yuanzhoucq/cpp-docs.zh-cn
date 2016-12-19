---
title: "acos、acosf、acosl | Microsoft Docs"
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
  - "acosf"
  - "acos"
  - "acosl"
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
  - "acos"
  - "acosl"
  - "acosf"
  - "math/acosf"
  - "math/acosl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "acos 函数"
  - "acosf 函数"
  - "acosl 函数"
  - "反余弦函数"
  - "三角函数"
ms.assetid: 00b89c48-8faf-4824-aa95-fa4349a4975d
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# acos、acosf、acosl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算反余弦值。  
  
## 语法  
  
```  
double acos(   
   double x   
);  
float acos(  
   float x   
);   // C++ only  
long double acos(  
   long double x  
);   // C++ only  
float acosf(  
   float x   
);  
long double acosl(  
   long double x  
);  
```  
  
#### 参数  
 `x`  
 当值在\-1到1之间，可以计算反余弦值 \(反余弦值\)。  
  
## 返回值  
 `acos` 函数返回反余弦 `x` 在范围 0 到π之间的弧度。  
  
 默认情况下，如果 `x` 小于–1 或大于 1，`acos`返回未定义值。  
  
|输入|SEH 异常|Matherr 异常|  
|--------|------------|----------------|  
|± ∞|`INVALID`|`_DOMAIN`|  
|± QNAN,IND|无|`_DOMAIN`|  
|&#124;x&#124;\>1|`INVALID`|`_DOMAIN`|  
  
## 备注  
 由于 C\+\+ 允许重载，您可以调用`acos` 的重载，该重载采用和返回 `float` 和 `long double` 值.  在 C 程序中，`acos` 始终采用并返回 `double`。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`acos`, `acosf`, `acosl`|\<math.h\>|\<errno.h\>|  
  
## 示例  
 此程序提示在 \-1 到 1 范围内的值。  在此范围之外的输入值导致`_DOMAIN`错误消息。  如果输入有效值，程序打印反正弦和该值反余弦值。  
  
```  
// crt_asincos.c  
// arguments: 0  
  
#include <math.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main( int ac, char* av[] )  
{  
    double  x,  
            y;  
    errno_t err;   
  
    // argument checking  
    if (ac != 2)  
    {  
        fprintf_s( stderr, "Usage: %s <number between -1 and 1>\n",  
                   av[0]);  
        return 1;  
    }  
  
    // Convert argument into a double value  
    if ((err = sscanf_s( av[1], "%lf", &x )) != 1)  
    {  
        fprintf_s( stderr, "Error converting argument into ",  
                   "double value.\n");  
        return 1;  
    }  
  
    // Arcsine of X  
    y = asin( x );  
    printf_s( "Arcsine of %f = %f\n", x, y );  
  
    // Arccosine of X  
    y = acos( x );  
    printf_s( "Arccosine of %f = %f\n", x, y );  
}  
```  
  
  **0.000000的反正弦值\=0.000000**  
**0.000000反余弦值\= 1.570796**   
## .NET Framework 等效项  
 [System::Math::Acos](https://msdn.microsoft.com/en-us/library/system.math.acos.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [asin、asinf、asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)