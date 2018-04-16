---
title: "_ecvt | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _ecvt
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
f1_keywords:
- _ecvt
dev_langs:
- C++
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee37eb3623f27f4fb6883b2d16fc4c21c2a960c1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="ecvt"></a>_ecvt
将 `double` 编号转换为字符串。 提供此函数的更安全的版本；请参阅 [_ecvt_s](../../c-runtime-library/reference/ecvt-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
char *_ecvt(   
   double value,  
   int count,  
   int *dec,  
   int *sign   
);  
```  
  
#### <a name="parameters"></a>参数  
 `value`  
 要转换的数字。  
  
 `count`  
 存储的数字位数。  
  
 `dec`  
 存储的十进制点位置。  
  
 `sign`  
 转换后的数字的符号。  
  
## <a name="return-value"></a>返回值  
 `_ecvt` 返回指向数字字符串的指针；如果发生错误，则为 NULL。  
  
## <a name="remarks"></a>备注  
 `_ecvt` 函数将浮点数转换为字符串。 `value` 参数是要转换的浮点数。 此函数最多存储 `count` 位 `value` 作为字符串，并追加空字符 ('\0')。 如果 `value` 中的数字位数超过 `count`，则低位数字被舍入。 如果数字位数少于 `count`，则字符串使用零来填充。  
  
 由 `_ecvt` 返回的数字的总位数将不能超过 `_CVTBUFSIZE`。  
  
 字符串中仅存储位数。 小数点位置和 `value` 的符号可以在调用后从 `dec` 和 `sign` 中获取。 `dec` 参数指向整数值；此整数值给定相对于字符串开头的小数点的位置。 0 或负整数值表示小数点位于第一个数字的左侧。 `sign` 参数指向一个整数，表示转换后的数字的符号。 如果整数值为 0，则数值为正值。 否认，数值为负值。  
  
 `_ecvt` 和 `_fcvt` 之间的差异在于对 `count` 参数的解释。 `_ecvt` 将 `count` 解释为输出字符串中的数字总位数，而 `_fcvt` 将 `count` 解释为小数点后面的数字位数。  
  
 `_ecvt` 和 `_fcvt` 使用用于转换的单个静态分配的缓冲区。 每次调用这些例程都会破坏上一次调用的结果。  
  
 此函数验证其参数。 如果 `dec` 或 `sign` 为 NULL，或 `count` 为 0，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则 `errno` 被设置为 `EINVAL` 且返回 NULL。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`_ecvt`|\<stdlib.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
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
  
```Output  
source: 3.1415926535   buffer: '3141592654'  decimal: 1  sign: 0  
```  
  
## <a name="see-also"></a>请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [_gcvt](../../c-runtime-library/reference/gcvt.md)