---
title: "_fcvt | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fcvt
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
- _fcvt
dev_langs:
- C++
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 0e2bad41f044046fd0f75a30989c1f39adb69560
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="fcvt"></a>_fcvt
将浮点数转换为字符串。 提供此函数的更安全的版本；请参阅 [_fcvt_s](../../c-runtime-library/reference/fcvt-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
char *_fcvt(   
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
 小数点后面的数字位数。  
  
 `dec`  
 指向存储的小数点位置的指针。  
  
 `sign`  
 指向存储的符号指示符的指针。  
  
## <a name="return-value"></a>返回值  
 `_fcvt` 返回指向数字字符串的指针；如果发生错误，则为 NULL。  
  
## <a name="remarks"></a>备注  
 `_fcvt` 函数将浮点数转换为以 null 结尾的字符串。 `value` 参数是要转换的浮点数。 `_fcvt` 将 `value` 的位数存储为字符串，并追加一个空字符 ('\0')。 `count` 参数指定此小数点后要存储的数字位数。 多余的位数被舍入到 `count` 位置。 如果小于精确到 `count` 的位数，则字符串使用零填充。  
  
 由 `_fcvt` 返回的数字的总位数将不能超过 `_CVTBUFSIZE`。  
  
 字符串中仅存储位数。 小数点位置和 `value` 的符号可以在调用后从 `dec` 和符号中获取。 `dec` 参数指向整数值；此整数值指定相对于字符串开头的小数点的位置。 零或负整数值表示小数点位于第一个数字的左侧。 参数 `sign` 指向一个整数值，表示 `value` 的符号。 如果 `value` 为正数，则整数设置为 0，如果 `value` 为负数，则整数设置为非零数。  
  
 `_ecvt` 和 `_fcvt` 之间的差异在于对 `count` 参数的解释。 `_ecvt` 将 `count` 解释为输出字符串中的数字总位数，而 `_fcvt` 将 `count` 解释为小数点后面的数字位数。  
  
 `_ecvt` 和 `_fcvt` 使用用于转换的单个静态分配的缓冲区。 对每个例程的每次调用都会破坏上一次调用的结果。  
  
 此函数验证其参数。 如果 `dec` 或 `sign` 为 NULL，或 `count` 为 0，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则 `errno` 被设置为 `EINVAL` 且返回 NULL。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`_fcvt`|\<stdlib.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
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
  
```Output  
source: 3.1415926535   buffer: '31415927'   decimal: 1   sign: 0  
```  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [_gcvt](../../c-runtime-library/reference/gcvt.md)
