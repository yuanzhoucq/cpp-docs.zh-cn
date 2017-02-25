---
title: "_gcvt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_gcvt"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_gcvt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CVTBUFSIZE"
  - "_gcvt 函数"
  - "转换, 浮点到字符串"
  - "CVTBUFSIZE"
  - "浮点函数, 将数字转换为字符串"
  - "gcvt 函数"
  - "数字, 转换为字符串"
  - "字符串 [C++], 从浮点转换"
ms.assetid: 5761411e-c06b-409a-912f-810fe7f4bcb5
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# _gcvt
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将浮点值转换为字符串，存在缓冲区。  该函数的一个更安全版本可利用；请参阅 [\_gcvt\_s](../../c-runtime-library/reference/gcvt-s.md)。  
  
## 语法  
  
```  
char *_gcvt(   
   double value,  
   int digits,  
   char *buffer   
);  
```  
  
#### 参数  
 `value`  
 要转换的值。  
  
 `digits`  
 存储的有效位数。  
  
 `buffer`  
 结果的存储位置。  
  
## 返回值  
 `_gcvt`返回指向数字字符串的指针。  
  
## 备注  
 `_gcvt` 函数将浮点 `value`转换为字符字符串（ 包含小数点和一种符号字节\)，并存储在`buffer`中。  `buffer` 应该足够大以容纳转换的值和自动追加的终止 null 字符。  如果使用`digits`的缓冲区大小\+1，函数覆盖缓冲区的末尾。  这是因为，转换的字符串包含小数点，并且可包含符号和指数信息。  没有规定溢出。  `_gcvt` 尝试产生十进制格式的`digits`数值。  如果不能，它产生指数格式`digits`的数值。  在转换中，尾随零转换可能被抑制。  
  
 `buffer`的`_CVTBUFSIZE`长度对于任何浮点数值都是足够的。  
  
 此函数验证其参数。  如果 `buffer` 是 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回 `NULL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_gcvt`|\<stdlib.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_gcvt.c  
// compile with: /W3  
#include <stdlib.h>  
#include <stdio.h>  
#include <string.h>  
  
int main( void )  
{  
   char buffer[_CVTBUFSIZE];  
   double value = -1234567890.123;  
   printf( "The following numbers were converted by _gcvt(value,12,buffer):\n" );  
   _gcvt( value, 12, buffer ); // C4996  
   // Note: _gcvt is deprecated; consider using _gcvt_s instead  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value *= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value *= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value *= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
  
   printf( "\n" );  
   value = -12.34567890123;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value /= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value /= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value /= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
}  
```  
  
  **下面数字按\_gcvt \(值，12，缓冲区\) 转换：**  
**缓冲区：“\-1234567890.12 " \(14 个字符\)**  
**缓冲区：“\-12345678901.2 " \(14 个字符\)**  
**缓冲区：“\-123456789012 " \(13 个字符\)**  
**缓冲区：“\-1.23456789012e\+012”\(19 个字符\)**  
**缓冲区：“\-1234567890.12 " \(14 个字符\)**  
**缓冲区：“\-1234567890.12 " \(14 个字符\)**  
**缓冲区：“\-0.123456789012 " \(15 个字符\)**  
**缓冲区：“\-1.23456789012e\-002”\(19 个字符\)**   
## .NET Framework 等效项  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)