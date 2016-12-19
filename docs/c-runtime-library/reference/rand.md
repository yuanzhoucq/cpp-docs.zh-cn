---
title: "rand | Microsoft Docs"
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
  - "rand"
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
  - "rand"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "生成伪随机数"
  - "数字, 生成伪随机"
  - "数字, 伪随机"
  - "伪随机数"
  - "rand 函数"
  - "随机数, 生成"
ms.assetid: 75d9df25-7aaf-4a88-b940-2775559634e8
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# rand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成一个伪随机数。  提供该函数的一个更安全版本，请参阅 [rand\_s](../../c-runtime-library/reference/rand-s.md)。  
  
## 语法  
  
```  
int rand( void );  
```  
  
## 返回值  
 如上所述，`rand` 返回一个伪随机数。  无错误返回。  
  
## 备注  
 `rand` 函数返回在范围 0 到 `RAND_MAX` \( 32767\) 的一个伪随机整数。  使用 [srand](../../c-runtime-library/reference/srand.md) 函数在调用 `rand`之前产生伪随机数生成器。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`rand`|\<stdlib.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_rand.c  
// This program seeds the random-number generator  
// with the time, then exercises the rand function.  
//  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <time.h>  
  
void SimpleRandDemo( int n )  
{  
   // Print n random numbers.  
   int i;  
   for( i = 0; i < n; i++ )  
      printf( "  %6d\n", rand() );  
}  
  
void RangedRandDemo( int range_min, int range_max, int n )  
{  
   // Generate random numbers in the half-closed interval  
   // [range_min, range_max). In other words,  
   // range_min <= random number < range_max  
   int i;  
   for ( i = 0; i < n; i++ )  
   {  
      int u = (double)rand() / (RAND_MAX + 1) * (range_max - range_min)  
            + range_min;  
      printf( "  %6d\n", u);  
   }  
}  
  
int main( void )  
{  
   // Seed the random-number generator with the current time so that  
   // the numbers will be different every time we run.  
   srand( (unsigned)time( NULL ) );  
  
   SimpleRandDemo( 10 );  
   printf("\n");  
   RangedRandDemo( -100, 100, 10 );  
}  
```  
  
  **22036**  
 **18330**  
 **11651**  
 **27464**  
 **18093**  
 **3284**  
 **11785**  
 **14686**  
 **11447**  
 **11285**  
 **74**  
 **48**  
 **27**  
 **65**  
 **96**  
 **64**  
 **\-5**  
 **\-42**  
 **\-55**  
 **66**   
## .NET Framework 等效项  
 [系统唯一的类](https://msdn.microsoft.com/en-us/library/system.random.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [srand](../../c-runtime-library/reference/srand.md)   
 [rand\_s](../../c-runtime-library/reference/rand-s.md)