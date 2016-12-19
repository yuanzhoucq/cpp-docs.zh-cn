---
title: "贝塞尔函数：_j0、_j1、_jn、_y0、_y1、_yn | Microsoft Docs"
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
  - "_j0"
  - "_j1"
  - "_jn"
  - "_y0"
  - "_y1"
  - "_yn"
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
  - "c.bessel"
  - "_j0"
  - "_j1"
  - "_jn"
  - "_y0"
  - "_y1"
  - "_yn"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "贝塞尔函数"
  - "_j0 函数"
  - "_j1 函数"
  - "_jn 函数"
  - "_y0 函数"
  - "_y1 函数"
  - "_yn 函数"
ms.assetid: a21a8bf1-df9d-4ba0-a8c2-e7ef71921d96
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 贝塞尔函数：_j0、_j1、_jn、_y0、_y1、_yn
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算第一种或第二种贝塞尔函数，顺序为 0、1 或 n。 星期四贝塞尔函数通常用于电磁波理论的数学学科中。  
  
## 语法  
  
```  
double _j0(   
   double x   
);  
double _j1(   
   double x   
);  
double _jn(   
   int n,  
   double x   
);  
double _y0(   
   double x   
);  
double _y1(   
   double x   
);  
double _yn(   
   int n,  
   double x   
);  
```  
  
#### 参数  
 `x`  
 浮点值。  
  
 `n`  
 Bessel 函数的整数顺序。  
  
## 返回值  
 每个例程将返回 `x` 贝塞尔函数。 如果 `x` 在 `_y0`、`_y1` 或 `_yn` 函数中为负，则例程会将 `errno` 设置为 `EDOM`，将 `_DOMAIN` 错误消息打印到 `stderr`并返回 `_HUGE_VAL`。 您可通过使用 `_matherr` 来修改错误处理。  
  
## 备注  
 `_j0`、`_j1` 和 `_jn` 例程将返回第一种贝塞尔函数：顺序分别为 0、1 和 n。  
  
|输入|SEH 异常|Matherr 异常|  
|--------|------------|----------------|  
|± `QNAN`,`IND`|`INVALID`|`_DOMAIN`|  
  
 `_y0`、`_y1` 和 `_yn` 例程将返回第二种 Bessel 函数：顺序分别为 0、1 和 n。  
  
|输入|SEH 异常|Matherr 异常|  
|--------|------------|----------------|  
|± `QNAN`,`IND`|`INVALID`|`_DOMAIN`|  
|± 0|`ZERODIVIDE`|`_SING`|  
|&#124;x&#124;\<0.0|`INVALID`|`_DOMAIN`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_j0`, `_j1`, `_jn`, `_y0`, `_y1`, `_yn`|\<cmath\> \(C\+\+\), \<math.h\> \(C, C\+\+\)|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_bessel1.c  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.387;  
   int n = 3, c;  
  
   printf( "Bessel functions for x = %f:\n", x );  
   printf( " Kind   Order  Function     Result\n\n" );  
   printf( " First  0      _j0( x )     %f\n", _j0( x ) );  
   printf( " First  1      _j1( x )     %f\n", _j1( x ) );  
   for( c = 2; c < 5; c++ )  
      printf( " First  %d      _jn( %d, x )  %f\n", c, c, _jn( c, x ) );  
   printf( " Second 0      _y0( x )     %f\n", _y0( x ) );  
   printf( " Second 1      _y1( x )     %f\n", _y1( x ) );  
   for( c = 2; c < 5; c++ )  
      printf( " Second %d      _yn( %d, x )  %f\n", c, c, _yn( c, x ) );  
}  
```  
  
```Output  
x = 2.387000 的贝塞尔函数：种类   顺序  函数     结果 第一种  0      _j0( x )     0.009288 第一种  1      _j1( x )     0.522941 第一种  2      _jn( 2, x )  0.428870 第一种  3      _jn( 3, x )  0.195734 第一种  4      _jn( 4, x )  0.063131 Second 0      _y0( x )     0.511681 第二种 1      _y1( x )     0.094374 第二种 2      _yn( 2, x )  -0.432608 第二种 3      _yn( 3, x )  -0.819314 第二种 4      _yn( 4, x )  -1.626833  
```  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)