---
title: "_fcvt | Microsoft Docs"
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
  - "_fcvt"
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
  - "_fcvt"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fcvt 函数"
  - "转换浮点, 为字符串"
  - "fcvt 函数"
  - "浮点函数"
  - "浮点函数, 将数字转换为字符串"
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
caps.latest.revision: 24
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fcvt
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将浮点数转换为字符串。  提供该函数的一个更安全版本；请参阅 [\_fcvt\_s](../../c-runtime-library/reference/fcvt-s.md)。  
  
## 语法  
  
```  
char *_fcvt(   
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
 小数点后数字的位数。  
  
 `dec`  
 指向存储的小数点位置的指针。  
  
 `sign`  
 指向存储的符号指示器的指针。  
  
## 返回值  
 `_fcvt` 返回指向数字字符串，在错误的空。  
  
## 备注  
 `_fcvt` 函数将浮点数转换为空终止字符字符串。  `value` 参数是转换浮点数。  `_fcvt` 存储 `value` 值作为字符串并添加空字符 \(“\\ 0 "\)。  `count` 参数指定小数点后要存储的位数。  多余的数字被四舍五入到 `count` 位置。  如果小于精度的 `count` 位数，用零填充字符串。  
  
 通过 `_fcvt` 返回的总位数不超过 `_CVTBUFSIZE`。  
  
 只有数字被存储在字符串中。  小数点的位置和 `value` 的符号可以在调用之后从 `dec` 和符号获取。   `dec` 参数指向一个整数值；此整数值指定相对于字符串的开头小数点的位置。  零或负整数值指示小数点位于第一个数的左侧。  参数 `value` 指向一个整数表示 `sign` 标记。  如果 `value` 是正，则整数设置为 0，如果 `value` 为负，则设置为一个非零值。  
  
 `_ecvt` 和 `_fcvt` 的差异在于对 `count` 参数的解释不同。  `_ecvt` 将 `count` 解释为输出字符串的总位数，而 `_fcvt` 将 `count` 解释为在小数点后的位数。  
  
 `_ecvt` 和 `_fcvt` 转换使用单个静态分配的缓冲区。  每调用这些例程之一将销毁之前调用的结果。  
  
 此函数验证其参数。  如果`dec` 或 `sign` 为空，或 `count`为0, 则调用无效参数处理程序, 正如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许继续执行，将 `EINVAL` 设置为 `errno`，并返回空。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_fcvt`|\<stdlib.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fcvt.c  
// compile with: /W3  
// This program converts the constant  
// 3.1415926535 to a string and sets the pointer  
// buffer to point to that string.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int  decimal, sign;  
   char *buffer;  
   double source = 3.1415926535;  
  
   buffer = _fcvt( source, 7, &decimal, &sign ); // C4996  
   // Note: _fcvt is deprecated; consider using _fcvt_s instead  
   printf( "source: %2.10f   buffer: '%s'   decimal: %d   sign: %d\n",  
            source, buffer, decimal, sign );  
}  
```  
  
  **源数: 3.1415926535   缓冲区: '31415927'   十进制: 1   符号: 0**   
## .NET Framework 等效项  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)