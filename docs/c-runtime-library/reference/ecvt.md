---
title: "_ecvt | Microsoft Docs"
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
  - "_ecvt"
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
  - "_ecvt"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ecvt 函数"
  - "转换双精度数字"
  - "ecvt 函数"
  - "数字, 转换"
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ecvt
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将 `double` 数字转换成字符串。  提供该函数的一个更安全版本；请参阅 [\_ecvt\_s](../../c-runtime-library/reference/ecvt-s.md)。  
  
## 语法  
  
```  
char *_ecvt(   
   double value,  
   int count,  
   int *dec,  
   int *sign   
);  
```  
  
#### 参数  
 `value`  
 数字可被转换.  
  
 `count`  
 存储数字的数字。  
  
 `dec`  
 存储小数点的位置。  
  
 `sign`  
 转换后的数的符号  
  
## 返回值  
 `_ecvt` 返回指向数字字符串；如果出错，则为 Null。  
  
## 备注  
 `_ecvt` 函数将浮点数转换为字符字符串。  `value` 参数是转换浮点数。  此函数以存储到 `count` `value` 数字为字符串并在 null 字符 \(“\\ 0 "\)。  如果数字的数目`value` 的溢出 `count`，低位数舍入。  如果小于精度的 `count` 位数，用零填充字符串。  
  
 通过 `_ecvt` 返回的总位数不超过 `_CVTBUFSIZE`。  
  
 只有数字被存储在字符串中。  小数点的位置和`value` 的符号可以在调用之后从 `dec` 和 `sign` 获取。   `dec` 参数指向一个整数值；此整数值指定相对于字符串的开头小数点的位置。  零或负整数值指示小数点位于第一个数的左侧。  到指示所转换的数字符号的整数的 `sign` 参数的位置。  如果整数值为 0，在数字为正数的。  否则，数字为负。  
  
 `_ecvt` 和 `_fcvt` 的差异在于对 `count` 参数的解释不同。  `_ecvt` 将 `count` 解释为输出字符串的总位数，而 `_fcvt` 将 `count` 解释为在小数点后的位数。  
  
 `_ecvt` 和 `_fcvt` 转换使用单个静态分配的缓冲区。  每调用这些例程之一将销毁之前调用的结果。  
  
 此函数验证其参数。  如果`dec` 或 `sign` 为空，或 `count`为0, 则调用无效参数处理程序, 正如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许继续执行，将 `EINVAL` 设置为 `errno`，并返回空。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_ecvt`|\<stdlib.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_ecvt.c  
// compile with: /W3  
// This program uses _ecvt to convert a  
// floating-point number to a character string.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int     decimal,   sign;  
   char    *buffer;  
   int     precision = 10;  
   double  source = 3.1415926535;  
  
   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996  
   // Note: _ecvt is deprecated; consider using _ecvt_s instead  
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",  
           source, buffer, decimal, sign );  
}  
```  
  
  **源数: 3.1415926535 缓冲区: '3141592654' 十进制: 1 符号: 0**   
## .NET Framework 等效项  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)