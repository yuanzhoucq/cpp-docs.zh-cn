---
title: "abs、 labs、 llabs、 _abs64 | Microsoft Docs"
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
  - "abs"
  - "_abs64"
  - "labs"
  - "llabs"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "stdlib/_abs64"
  - "math/abs"
  - "_abs64"
  - "abs"
  - "labs"
  - "math/labs"
  - "llabs"
  - "math/llabs"
  - "cmath/abs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "绝对值"
  - "abs 函数"
  - "abs64 函数"
  - "_abs64 函数"
  - "计算绝对值"
ms.assetid: 60f789d1-4a1e-49f5-9e4e-0bdb277ea26a
caps.latest.revision: 29
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# abs、 labs、 llabs、 _abs64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算参数的绝对值。  
  
## 语法  
  
```  
int abs(   
   int n   
);  
long abs(   
   long n   
);   // C++ only  
long long abs(   
   long long n   
);   // C++ only  
double abs(   
   double n   
);   // C++ only  
long double abs(  
   long double n  
);   // C++ only  
float abs(  
   float n   
);   // C++ only  
long labs(  
   long n   
);  
long long llabs(  
   long long n   
);  
__int64 _abs64(   
   __int64 n   
);  
```  
  
#### 参数  
 `n`  
 数字值。  
  
## 返回值  
 `abs`, ，`labs`, ，`llabs` 和 `_abs64` 函数将返回参数的绝对值 `n`。 无错误返回。  
  
## 备注  
 由于 c \+ \+ 允许重载，你可以调用的重载 `abs` 采用并返回 `long`, ，`long long`, ，`float`, ，`double`, ，和 `long double` 值。 这些重载 \< cmath \> 标头中定义。 在 C 程序中， `abs` 始终采用并返回 int。  
  
 **Microsoft 专用**  
  
 由于可以通过使用任何整数类型表示为负的整数的范围是大于正整数可以通过使用该类型表示的范围，则可以提供对这些函数不能转换的参数。 如果参数的绝对值的数值不能表示的返回类型 `abs` 函数将返回未更改的参数值。 具体而言， `abs(INT_MIN)` 返回 `INT_MIN`, ，`labs(LONG_MIN)` 返回 `LONG_MIN`, ，`llabs(LLONG_MIN)` 返回 `LLONG_MIN`, ，和 `_abs64(_I64_MIN)` 返回 `_I64_MIN`。 这意味着， `abs` 函数不能用于保证正数值。  
  
 **结束 Microsoft 专用**  
  
## 要求  
  
|例程|必需的 C 标头|必需的 c \+ \+ 标头|  
|--------|--------------|--------------------|  
|`abs`, `labs`, `llabs`|\< h.h \> 或 \< stdlib.h \>|\< cmath \>，\< cstdlib \>，\< stdlib.h \> 或 \< h.h \>|  
|`_abs64`|\<stdlib.h\>|\< cstdlib \> 或 \< stdlib.h \>|  
  
 若要使用的重载的版本 `abs` c \+ \+ 中必须包含 \< cmath \> 标头。  
  
## 示例  
 此程序计算并显示几个数字的绝对值。  
  
```c  
// crt_abs.c  
// Build: cl /W3 /TC crt_abs.c  
// This program demonstrates the use of the abs function  
// by computing and displaying the absolute values of  
// several numbers.  
  
#include <stdio.h>  
#include <math.h>  
#include <stdlib.h>  
#include <limits.h>  
  
int main( void )  
{  
    int ix = -4;  
    long lx = -41567L;  
    long long llx = -9876543210LL;  
    __int64 wx = -1;  
  
    // absolute 32 bit integer value  
    printf_s("The absolute value of %d is %d\n", ix, abs(ix));  
  
    // absolute long integer value  
    printf_s("The absolute value of %ld is %ld\n", lx, labs(lx));  
  
    // absolute long long integer value  
    printf_s("The absolute value of %lld is %lld\n", llx, llabs(llx));  
  
    // absolute 64 bit integer value  
    printf_s("The absolute value of 0x%.16I64x is 0x%.16I64x\n", wx,   
        _abs64(wx));  
  
    // Integer error cases:  
    printf_s("Microsoft implementation-specific results:\n");  
    printf_s(" abs(INT_MIN) returns %d\n", abs(INT_MIN));  
    printf_s(" labs(LONG_MIN) returns %ld\n", labs(LONG_MIN));  
    printf_s(" llabs(LLONG_MIN) returns %lld\n", llabs(LLONG_MIN));  
    printf_s(" _abs64(_I64_MIN) returns 0x%.16I64x\n", _abs64(_I64_MIN));  
}  
```  
  
```Output  
-4 的绝对值是的 4-41567 的绝对值是的 41567-9876543210 的绝对值是的 9876543210 0xffffffffffffffff 的绝对值是 0x0000000000000001 Microsoft 特定于实现的结果︰ abs(INT_MIN) 返回介于-2147483648 labs(LONG_MIN) 返回介于-2147483648 llabs(LLONG_MIN) 返回-9223372036854775808 _abs64(_I64_MIN) 返回 0x8000000000000000  
  
```  
  
## .NET Framework 等效项  
 [System::Math::Abs](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [\_cabs](../../c-runtime-library/reference/cabs.md)   
 [fabs、 fabsf fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [imaxabs](../../c-runtime-library/reference/imaxabs.md)