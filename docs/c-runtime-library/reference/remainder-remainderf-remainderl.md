---
title: "remainder、remainderf、remainderl | Microsoft Docs"
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
  - "remainderl"
  - "remainder"
  - "remainderf"
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
  - "remainderf"
  - "remainder"
  - "remainderl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remainderf"
  - "remainderl"
  - "remainder"
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# remainder、remainderf、remainderl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算两浮点值商的余数，四舍五入为最接近的整数值。  
  
## 语法  
  
```  
double remainder(   
   double numer,  
   double denom  
);  
float remainder(   
   float numer,  
   float denom  
); /* C++ only */  
long double remainder(   
   long double numer,  
   long double denom  
); /* C++ only */  
float remainderf(   
   float numer,  
   float denom  
);  
long double remainderl(   
   long double numer,  
   long double denom  
);  
  
```  
  
#### 参数  
 `numer`  
 枚举器。  
  
 `denom`  
 分母。  
  
## 返回值  
 `x` \/ `y`浮点余数。  如果 `y` 的值为 0.0，则 `remainder` 将返回安静 NaN。  有关安静 NaN 的 `printf` 系列的表示形式信息，请参阅 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)。  
  
## 备注  
 `remainder` 函数计算浮点余数`r` 的 `x` \/ `y` ，以至于 `x` \= `n` \* `y` \+ `r`, `n` 是最接近 `x` \/ `y` 的整数，并且 `n` 为偶数无论&#124; `n`为多少。 \- `x` \/ `y` &#124; \= 1\/2.  当 `r` \= 0，`r` 与 `x` 符号相同。  
  
 由于 C\+\+ 允许重载，因此您可以调用 `remainder` 的重载，该重载采用和返回 `float` 或 `long double` 值。  在 C 程序中，`remainder` 始终采用两个双精度值并返回一个双精度值。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`remainder`, `remainderf`, `remainderl`|\<math.h\>|  
  
 有关兼容性信息，请参见 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```c  
// crt_remainder.c  
// This program displays a floating-point remainder.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double w = -10.0, x = 3.0, z;  
  
   z = remainder(w, x);  
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);  
}  
```  
  
  **\-10.00 除以 3.00 的余数是 \-1.000000**   
## .NET Framework 等效项  
 [System::Math::IEEERemainder](https://msdn.microsoft.com/en-us/library/system.math.ieeeremainder.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [ldiv、lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)   
 [fmod, fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [remquo、remquof、remquol](../../c-runtime-library/reference/remquo-remquof-remquol.md)