---
title: "lrint、 lrintf、 lrintl、 llrint、 llrintf、 llrintl | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "lrint"
  - "lrintl"
  - "lrintf"
  - "llrint"
  - "llrintf"
  - "llrintl"
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
  - "lrint"
  - "lrintf"
  - "lrintl"
  - "llrint"
  - "llrintf"
  - "llrintl"
  - "math/lrint"
  - "math/lrintf"
  - "math/lrintl"
  - "math/llrint"
  - "math/llrintf"
  - "math/llrintl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "lrint 函数"
  - "lrintf 函数"
  - "lrintl 函数"
  - "llrint 函数"
  - "llrintf 函数"
  - "llrintl 函数"
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# lrint、 lrintf、 lrintl、 llrint、 llrintf、 llrintl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过使用当前舍入模式和方向舍入到最接近的整数值，指定的浮点值。  
  
## 语法  
  
```  
long int lrint(  
   double x  
);  
  
long int lrint(  
   float x  
); //C++ only  
  
long int lrint(  
   long double x  
); //C++ only  
  
long int lrintf(  
   float x  
);  
  
long int lrintl(  
   long double x  
);  
  
long long int llrint(  
   double x  
);  
  
long long int llrint(  
   float x  
); //C++ only  
  
long long int llrint(  
   long double x  
); //C++ only  
  
long long int llrintf(  
   float x  
);  
  
long long int llrintl(  
   long double x  
);  
  
```  
  
#### 参数  
 \[in\] `x`  
 要舍入的值。  
  
## 返回值  
 如果成功，返回的舍入的整数值 `x`。  
  
|问题|返回|  
|--------|--------|  
|`x` 不在范围之内的返回类型<br /><br /> `x` \= ±∞<br /><br /> `x` \= NaN|引发 FE\_INVALID，并返回零 \(0\)。|  
  
## 备注  
 由于 c \+ \+ 允许重载，你可以调用的重载 `lrint` 和 `llrint` 那些需要浮点型和长双精度类型。 在 C 程序中， `lrint` 和 `llrint` 始终会采用一个双精度值。  
  
 如果 `x` 不表示浮点等效项的整数值，这些函数将引发 FE\_INEXACT。  
  
 **Microsoft 专用**︰ 如果结果为范围之外的返回类型，或当参数为 NaN 或无穷大，则返回值是定义的实现。 Microsoft 编译器会返回零 \(0\) 值。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`lrint`, `lrintf`, `lrintl`, `llrint`, `llrintf`, `llrintl`|\<math.h\>|\<cmath\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)