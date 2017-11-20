---
title: "_gcvt | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _gcvt
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords: _gcvt
dev_langs: C++
helpviewer_keywords:
- _gcvt function
- _CVTBUFSIZE
- gcvt function
- floating-point functions, converting number to string
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 5761411e-c06b-409a-912f-810fe7f4bcb5
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 40fba941afd4f5acd8883acdf236273b72afb60c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="gcvt"></a>_gcvt
将浮点值转换为字符串，并将其存储在缓冲区中。 此函数有一个更安全的版本；请参阅 [_gcvt_s](../../c-runtime-library/reference/gcvt-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
char *_gcvt(   
   double value,  
   int digits,  
   char *buffer   
);  
```  
  
#### <a name="parameters"></a>参数  
 `value`  
 要转换的值。  
  
 `digits`  
 存储的有效位数。  
  
 `buffer`  
 结果的存储位置。  
  
## <a name="return-value"></a>返回值  
 `_gcvt` 返回指向数字字符串的指针。  
  
## <a name="remarks"></a>备注  
 `_gcvt` 函数将浮点 `value` 转换为字符串（它包括小数点和可能的登录字节），并将字符串存储在 `buffer` 中。 `buffer` 应足够大以容纳转换后的值加上一个会自动追加的端接空字符。 如果已使用 `digits` + 1 的缓冲区大小，该函数将覆盖缓冲区的末尾。 这是因为转换后的字符串包含小数点，并且可以包含符号和指数信息。 没有为溢出进行预配。 `_gcvt` 尝试生成十进制格式的 `digits` 数字。 如果不能，则将生成指数格式的 `digits` 数字。 在转换过程中，可以取消零结尾。  
  
 `_CVTBUFSIZE` 的 `buffer` 长度足以满足任何浮点值。  
  
 此函数验证其参数。 如果 `buffer` 为 `NULL`，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 `NULL`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_gcvt`|\<stdlib.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
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
  
```Output  
The following numbers were converted by _gcvt(value,12,buffer):  
buffer: '-1234567890.12' (14 chars)  
buffer: '-12345678901.2' (14 chars)  
buffer: '-123456789012' (13 chars)  
buffer: '-1.23456789012e+012' (19 chars)  
  
buffer: '-12.3456789012' (14 chars)  
buffer: '-1.23456789012' (14 chars)  
buffer: '-0.123456789012' (15 chars)  
buffer: '-1.23456789012e-002' (19 chars)  
```  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [_fcvt](../../c-runtime-library/reference/fcvt.md)