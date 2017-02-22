---
title: "fpclassify | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fpclassify"
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
apitype: "HeaderDef"
f1_keywords: 
  - "fpclassify"
  - "math/fpclassify"
helpviewer_keywords: 
  - "fpclassify 宏"
  - "fpclassify 函数"
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# fpclassify
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回参数的浮点分类。  
  
## 语法  
  
```  
int fpclassify(   
   /* floating-point */ x   
);  
  
int fpclassify(   
   float x   
); // C++ only  
  
int fpclassify(   
   double x   
); // C++ only  
  
int fpclassify(   
   long double x   
); // C++ only  
  
```  
  
#### 参数  
 `x`  
 要测试的浮点值。  
  
## 返回值  
 `fpclassify` 返回一个整数值，该值指示参数的浮点类 `x`。 此表列出了可能的值返回 `fpclassify`, 在 \< h.h \> 中定义。  
  
|值|描述|  
|-------|--------|  
|`FP_NAN`|Quiet、 发出信号，或不确定的 NaN|  
|`FP_INFINITE`|正或负无穷大|  
|`FP_NORMAL`|一个正数或负数标准化的非零值|  
|`FP_SUBNORMAL`|正数或负数的非规范化的值|  
|`FP_ZERO`|一个值为正或负零值|  
  
## 备注  
 在 C 中， `fpclassify` 是宏; 在 c \+ \+， `fpclassify` 是函数重载使用的参数类型 `float`, ，`double`, ，或 `long double`。 在任一情况下，返回的值取决于参数表达式中，有效类型以及不能对任何中间表示形式。 例如，普通 `double` 或 `long double` 值可以成为无穷大、 不正常，或零值转换为时 `float`。  
  
## 要求  
  
|函数\/宏|必需的标头 \(C\)|必需的标头 \(C\+\+\)|  
|-----------|-----------------|---------------------|  
|`fpclassify`|\<math.h\>|\<math.h\> 或 \<cmath\>|  
  
 `fpclassify` 宏和 `fpclassify` 函数符合 C99 和 C \+ \+ 11 规范。 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [isnan，\_isnan \_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)