---
title: "isnan，_isnan _isnanf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_isnan"
  - "_isnanf"
  - "isnan"
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
  - "_isnan"
  - "isnan"
  - "math/isnan"
  - "math/_isnan"
  - "math/_isnanf"
  - "_isnanf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NAN（不是数字）"
  - "_isnan 函数"
  - "IEEE 浮点表示形式"
  - "不是数字 (NAN)"
  - "isnan 函数"
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# isnan，_isnan _isnanf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

测试是否有一个浮点值不是数字 \(NAN\)。  
  
## 语法  
  
```  
int isnan(  
   /* floating-point */ x   
); /* C-only macro */  
  
int _isnan(  
   double x   
);  
  
int _isnanf(  
   float x  
); /* x64 only */  
  
template <class T>  
bool isnan(  
   T x  
) throw(); /* C++ only */  
```  
  
#### 参数  
 *x*  
 要测试的浮点值。  
  
## 返回值  
 在 C 中， `isnan` 宏和 `_isnan` 和 `_isnanf` 函数返回一个非零值，如果该参数 `x` 是 NAN; 否则它们会返回 0。  
  
 在 c \+ \+， `isnan` 模板函数将返回 `true` 如果参数 `x` 是 NAN; 否则它们会返回 `false`。  
  
## 备注  
 C `isnan` 宏和 `_isnan` 和 `_isnanf` 函数将测试浮点值 *x*, ，返回一个非零值，如果 *x* 不是数字 \(NAN\) 值。 无法为指定类型的 IEEE 754 浮点格式表示浮点运算的结果，则会生成 NAN。 有关如何将一个 NAN 表示用于输出的信息，请参阅 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)。  
  
 在作为 c \+ \+ 编译时 `isnan` 未定义宏，以及一个 `isnan` 改为定义模板函数。 它将返回类型的值 `bool` 而不是整数。  
  
 `_isnan` 和 `_isnanf` 函数是 Microsoft 专用。`_isnanf` 函数只是在针对 x64 编译时可用。  
  
## 要求  
  
|例程|必需的标头 \(C\)|必需的标头 \(C\+\+\)|  
|--------|-----------------|---------------------|  
|`isnan`, `_isnanf`|\<math.h\>|\<math.h\> 或 \<cmath\>|  
|`_isnan`|\<float.h\>|\<.h \> 或 \< cfloat \>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [\_finite \_finitef](../../c-runtime-library/reference/finite-finitef.md)   
 [\_fpclass \_fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)