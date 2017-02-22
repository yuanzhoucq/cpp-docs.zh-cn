---
title: "__min | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__min"
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
apitype: "DLLExport"
f1_keywords: 
  - "__min"
  - "min"
  - "_min"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__min 宏"
  - "_min 宏"
  - "min 宏"
  - "minimum 宏"
ms.assetid: 2037f26c-b48a-4a69-8870-22519f052a3c
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# __min
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回两个值中的较小者。  
  
## 语法  
  
```  
type __min(  
   type a,  
   type b   
);  
```  
  
#### 参数  
 `type`  
 任何数字数据类型。  
  
 `a, b`  
 任何数值类型的值会被比较。  
  
## 返回值  
 两个参数中的小的。  
  
## 备注  
 `__min` 宏对两个值进行比较并返回值较小的一个。  参数可以是任何数字数据类型，有符号或者没有符号。  参数和返回值必须是同一数据类型。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`__min`|\<stdlib.h\>|  
  
## 示例  
  
```  
// crt_minmax.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int a = 10;  
   int b = 21;  
  
   printf( "The larger of %d and %d is %d\n",  a, b, __max( a, b ) );  
   printf( "The smaller of %d and %d is %d\n", a, b, __min( a, b ) );  
}  
```  
  
  **大 10 和 21 是 21**  
**10 和 21 中小的是 10**   
## .NET Framework 等效项  
 [System::Math::Min](https://msdn.microsoft.com/en-us/library/system.math.min.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [\_\_max](../../c-runtime-library/reference/max.md)