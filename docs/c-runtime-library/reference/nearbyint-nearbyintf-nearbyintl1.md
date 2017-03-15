---
title: "nearbyint、 nearbyintf、 nearbyintl1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "nearbyint"
  - "nearbyintf"
  - "nerabyintl"
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
  - "nearbyint"
  - "nearbyintf"
  - "nearbyintl"
  - "math/nearbyint"
  - "math/narbyintf"
  - "math/narbyintl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nearbyint 函数"
  - "nearbyintf 函数"
  - "nearbyintl 函数"
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# nearbyint、 nearbyintf、 nearbyintl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将舍入为一个整数，指定的浮点值，并以浮点格式返回该值。  
  
## 语法  
  
```  
double nearbyint(  
   double x  
);  
  
float nearbyint(  
   float x  
); //C++ only  
  
long double nearbyint(  
   long double x  
); //C++ only  
  
float nearbyintf(  
   float x  
);  
  
long double nearbyintl(  
   long double x  
);  
  
```  
  
#### 参数  
 \[in\] `x`  
 要舍入的值。  
  
## 返回值  
 如果成功，返回 `x`, ，舍入到最接近的整数，如中定义的 fegetround 使用当前舍入格式。 否则，该函数可能会返回以下值之一︰  
  
|问题|返回|  
|--------|--------|  
|`x` ±INFINITY \=|±INFINITY，未经修改的形式|  
|`x` \= ±0|±0，未经修改的形式|  
|`x` \= NaN|NaN|  
  
 通过不报告错误 [\_matherr](../../c-runtime-library/reference/matherr.md); 具体而言，此函数不会报告任何 FE\_INEXACT 异常。  
  
## 备注  
 此函数的主要区别和 `rint` 是此函数不会引发不精确的浮点异常。  
  
 最大的浮点值均为确切的整数，因为此函数将永远不会溢出重试。相反，输出可能会溢出的返回值，具体取决于函数的版本中，您将使用。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`nearbyint`, `nearbyintf`,  `nearbyintl`|\<math.h\>|\<cmath\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)