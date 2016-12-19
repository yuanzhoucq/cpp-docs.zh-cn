---
title: "trunc、 truncf、 truncl | Microsoft Docs"
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
  - "trunc"
  - "truncf"
  - "truncl"
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
  - "trunc"
  - "truncf"
  - "truncl"
  - "math/trunc"
  - "math/truncf"
  - "math/truncl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "trunc 函数"
  - "truncf 函数"
  - "truncl 函数"
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
caps.latest.revision: 13
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# trunc、 truncf、 truncl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定小于或等于指定的浮点值最接近的整数。  
  
## 语法  
  
```  
double trunc(  
   double x  
);  
  
float trunc(  
   float x  
); //C++ only  
  
long double trunc(  
   long double x  
); //C++ only  
  
float trunc(  
   float x  
); //C++ only  
  
long double truncl(  
   long double x  
);  
  
```  
  
#### 参数  
 \[in\] `x`  
 要截断的值。  
  
## 返回值  
 如果成功，返回的整数值 `x`, ，并向零舍入。  
  
 否则，可能会返回以下值之一︰  
  
|问题|返回|  
|--------|--------|  
|`x` ±INFINITY \=|x|  
|`x` \=  ±0|x|  
|`x` \= NaN|NaN|  
  
 错误报告中指定 [\_matherr](../../c-runtime-library/reference/matherr.md)。  
  
## 备注  
 由于 c \+ \+ 允许重载，你可以调用的重载 `trunc` 采用并返回浮点型和长双精度类型。 在 C 程序中， `trunc` 始终采用并返回一个双精度值。  
  
 最大的浮点值均为确切的整数，因为此函数将不的溢出自己。 但是，您可能会导致溢出到整数类型返回值的函数。  
  
 您可以同时向下舍入通过隐式从浮点转换为整数;但是，这样做很限于可以存储在目标类型的值。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`trunc`, `truncf`,  `truncl`|\<math.h\>|\<cmath\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [ceil、ceilf、ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [round、roundf、roundl](../../c-runtime-library/reference/round-roundf-roundl.md)