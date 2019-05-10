---
title: _fcvt
ms.date: 04/05/2018
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
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
ms.openlocfilehash: ae9323e3bb629fd61b35a8c844b00bfcc73235bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334835"
---
# <a name="fcvt"></a>_fcvt

将浮点数转换为字符串。 提供此函数的更安全的版本；请参阅 [_fcvt_s](fcvt-s.md)。

## <a name="syntax"></a>语法

```C
char *_fcvt(
   double value,
   int count,
   int *dec,
   int *sign
);
```

### <a name="parameters"></a>参数

*值*<br/>
要转换的数字。

*count*<br/>
小数点后面的数字位数。

*dec*<br/>
指向存储的小数点位置的指针。

*sign*<br/>
指向存储的符号指示符的指针。

## <a name="return-value"></a>返回值

**_fcvt**返回指向数字的字符串的指针**NULL**出错。

## <a name="remarks"></a>备注

**_Fcvt**函数将浮点数转换为以 null 结尾的字符串。 *值*参数是要转换的浮点数。 **_fcvt**存储的位数*值*作为一个字符串，并追加 null 字符 (\0)。 *计数*参数指定要存储在小数点后的位数。 多余的位数被舍入到*计数*放置。 如果少于*计数*用零填充数字的精度，该字符串。

返回的总位数 **_fcvt**将不会超过 **_CVTBUFSIZE**。

字符串中仅存储位数。 小数点和的符号的位置*值*可从此*dec*并在调用后的登录。 *Dec*参数指向一个整数值; 此整数值指定相对于字符串开头的小数点的位置。 零或负整数值表示小数点位于第一个数字的左侧。 将参数*符号*指向一个整数，指示的符号*值*。 整数设置为 0，如果*值*为正，设置为非零数字*值*为负。

之间的差异 **_ecvt**并 **_fcvt**中的解释*计数*参数。 **_ecvt**解释*计数*输出字符串中的位数总数而 **_fcvt**解释*计数*后的位数小数点。

**_ecvt**并 **_fcvt**使用单个静态分配的缓冲区用于转换。 对每个例程的每次调用都会破坏上一次调用的结果。

此函数验证其参数。 如果*dec*或*登录*是**NULL**，或者*计数*为 0，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**并**NULL**返回。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
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

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_gcvt](gcvt.md)<br/>
