---
title: "remquo、remquof、remquol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "remquof"
  - "remquo"
  - "remquol"
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
  - "remquof"
  - "remquol"
  - "remquo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remquol 函数"
  - "remquof 函数"
  - "remquo 函数"
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# remquo、remquof、remquol
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算两个整数值的余数，并在参数指定的位置存储与此商的符号相同且大小相似的整数值。  
  
## 语法  
  
```  
double remquo(   
   double numer,  
   double denom,  
   int* quo  
);  
float remquo(   
   float numer,  
   float denom,  
   int* quo  
); /* C++ only */  
long double remquo(   
   long double numer,  
   long double denom,  
   int* quo  
); /* C++ only */  
float remquof(   
   float numer,  
   float denom,  
   int* quo  
);  
long double remquol(   
   long double numer,  
   long double denom,  
   int* quo  
);  
  
```  
  
#### 参数  
 `numer`  
 枚举器。  
  
 `denom`  
 分母。  
  
 `quo`  
 指向存储带有符号和近似大小的商的整数值的指针  
  
## 返回值  
 `remquo` 返回 `x` \/ `y` 的浮点余数。  如果 `y` 的值为 0.0，则 `remquo` 将返回安静 NaN。  有关安静 NaN 的 `printf` 系列的表示形式信息，请参阅 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)。  
  
## 备注  
 `remquo` 函数计算 `x` 除以 `y` 的 `f` 浮点余数，这样  `x` \= `i` `*` `y` \+ `f`，其中 `i` 是整数，`f` 和 `x` 有相同的符号，而且 `f` 的绝对值小于 `y` 的绝对值。  
  
 C\+\+ 允许重载，因此您可以调用 `remquo` 的重载，该重载采用和返回 `float` 或 `long double` 值。  在 C 程序中，`remquo` 始终采用两个双精度值并返回一个双精度值。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`remquo`, `remquof`, `remquol`|\<math.h\>|  
  
 有关兼容性信息，请参见 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```c  
// crt_remquo.c  
// This program displays a floating-point remainder.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double w = -10.0, x = 3.0, z;  
   int quo = 0;  
  
   z = remquo(w, x, &quo);  
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);  
   printf("Approximate signed quotient is %d\n", quo);  
}  
```  
  
  **\-10.00 除以 3.00 的余数是 \-1.000000**  
**大致签名的商为 \-3**   
## .NET Framework 等效项  
 [System::Math::IEEERemainder](https://msdn.microsoft.com/en-us/library/system.math.ieeeremainder.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [ldiv、lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)   
 [fmod, fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [remainder、remainderf、remainderl](../../c-runtime-library/reference/remainder-remainderf-remainderl.md)