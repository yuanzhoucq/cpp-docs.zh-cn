---
title: "nextafter、 nextafterf、 nextafterl、 _nextafter、 _nextafterf、 nexttoward、 nexttowardf、 nexttowardl | Microsoft Docs"
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
  - "nextafterf"
  - "_nextafterf"
  - "nextafter"
  - "nextafterl"
  - "_nextafter"
  - "nexttoward"
  - "nexttowardf"
  - "nexttowardl"
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
  - "nextafter"
  - "_nextafter"
  - "nextafterf"
  - "nextafterl"
  - "_nextafterf"
  - "math/nextafter"
  - "math/nextafterf"
  - "math/nextafterl"
  - "nexttoward"
  - "nexttowardf"
  - "nexttowardl"
  - "math/nexttoward"
  - "math/nexttowardf"
  - "math/nexttowardl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_nextafter 函数"
  - "nextafter 函数"
  - "_nextafterf 函数"
  - "nextafterf 函数"
  - "nextafterl 函数"
  - "nexttoward 函数"
  - "nexttowardf 函数"
  - "nexttowardl 函数"
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# nextafter、 nextafterf、 nextafterl、 _nextafter、 _nextafterf、 nexttoward、 nexttowardf、 nexttowardl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回下一个可表示的浮点值。  
  
## 语法  
  
```  
double nextafter(  
   double x,  
   double y   
);  
  
float nextafter(  
   float x,  
   float y   
); /* C++ only, requires <cmath> */  
  
long double nextafter(  
   long double x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
float nextafterf(  
   float x,  
   float y   
);   
  
long double nextafterl(  
   long double x,  
   long double y   
);  
  
double _nextafter(  
   double x,  
   double y   
);  
  
float _nextafterf(  
   float x,  
   float y   
); /* x64 only */  
  
double nexttoward(  
   double x,  
   long double y   
);  
  
float nexttoward(  
   float x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
long double nexttoward(  
   long double x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
float nexttowardf(  
   float x,  
   long double y   
);   
  
long double nexttowardl(  
   long double x,  
   long double y   
);  
```  
  
#### 参数  
 `x`  
 要从启动的浮点值。  
  
 `y`  
 要都用在的浮点值。  
  
## 返回值  
 返回下一步可表示的浮点值之后的返回类型 `x` 的方向 `y`。 如果 `x`\=`y`, ，该函数将返回 `y`, 、 转换为返回类型以及不会触发异常。 如果 `x` 是否不等于 `y`, ，结果是 denormal 或零，设置 FE\_UNDERFLOW 和 FE\_INEXACT 浮点异常状态，并且返回正确的结果。 如果任一 `x` 或 `y` 是 NAN，则返回值是一个输入 Nan。 如果 `x` 是有限的结果是无限期还是无法在类型中表示的、 返回正确的有符号无穷大或 NAN，设置 FE\_OVERFLOW 和 FE\_INEXACT 浮点异常状态，并 `errno` 设置为 ERANGE。  
  
## 备注  
 `nextafter` 和 `nexttoward` 函数系列是等效的除了的参数类型 `y`。 如果 `x` 和 `y` 相等，返回的值为 `y` 转换为返回类型。  
  
 由于 c \+ \+ 允许重载，如果包括 \< cmath \> 你可以调用的重载 `nextafter` 和 `nexttoward` ，可返回 `float` 和 `long double` 类型。 在 C 程序中， `nextafter` 和 `nexttoward` 始终返回 `double`。  
  
 `_nextafter` 和 `_nextafterf` 函数是 Microsoft 专用。`_nextafterf` 函数在编译 x64 时才可用。  
  
## 要求  
  
|例程|必需的标头 \(C\)|必需的标头 \(C\+\+\)|  
|--------|-----------------|---------------------|  
|`nextafter`, `nextafterf`, `nextafterl`, `_nextafterf`, `nexttoward`, `nexttowardf`, `nexttowardl`|\<math.h\>|\<math.h\> 或 \<cmath\>|  
|`_nextafter`|\<float.h\>|\<.h \> 或 \< cfloat \>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [isnan，\_isnan \_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)