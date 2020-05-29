---
title: _ecvt_s
ms.date: 4/2/2020
api_name:
- _ecvt_s
- _o__ecvt_s
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ecvt_s
- _ecvt_s
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
ms.openlocfilehash: 9ac623c6cb80c774184dcb005e6d1d631c498040
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915144"
---
# <a name="_ecvt_s"></a>_ecvt_s

将**双精度**数字转换为字符串。 这是 [_ecvt](ecvt.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t _ecvt_s(
   char * _Buffer,
   size_t _SizeInBytes,
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
);
template <size_t size>
errno_t _ecvt_s(
   char (&_Buffer)[size],
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
); // C++ only
```

### <a name="parameters"></a>参数

*_Buffer*<br/>
使用转换的结果填充指向位字符串的指针。

*_SizeInBytes*<br/>
缓冲区的大小（以字节为单位）。

*_Value*<br/>
要转换的数字。

*_Count*<br/>
存储的数字位数。

*_Dec*<br/>
存储的十进制点位置。

*_Sign*<br/>
转换后的数字的符号。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 如果失败，则返回值为错误代码。 错误代码是在 Errno.h 中定义。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

对于无效参数（如下表中所列），此函数调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数会将**errno**设置为**EINVAL**并返回**EINVAL**。

### <a name="error-conditions"></a>错误条件

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|返回值|*缓冲区*中的值|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**Null**|any|any|any|any|any|**EINVAL**|未修改。|
|Not **NULL** （指向有效内存）|<=0|any|any|any|any|**EINVAL**|未修改。|
|any|any|any|any|**Null**|any|**EINVAL**|未修改。|
|any|any|any|any|any|**Null**|**EINVAL**|未修改。|

## <a name="security-issues"></a>安全问题

如果*缓冲区*未指向有效内存且不为**NULL**，则 **_ecvt_s**可能会产生访问冲突。

## <a name="remarks"></a>备注

**_Ecvt_s**函数将浮点数转换为字符串。 *_Value*参数是要转换的浮点数。 此函数以字符串的形式存储 *_Value*的*计数*位数，并追加一个 null 字符（' \ 0 '）。 如果 *_Value*中的数字位数超过 *_Count*，则将舍入低序位。 如果数字少于*计数*，则用零填充字符串。

字符串中仅存储位数。 可以在调用后从 *_Dec*和 *_Sign*获取小数点的位置和 *_Value*的符号。 *_Dec*参数指向一个整数值，该整数值给定小数点相对于字符串开头的位置。 0 或负整数值表示小数点位于第一个数字的左侧。 *_Sign*参数指向一个整数，该整数指示转换后的数字的符号。 如果整数值为 0，则数值为正值。 否认，数值为负值。

长度 **_CVTBUFSIZE**的缓冲区足以满足任何浮点值。

**_Ecvt_s**和 **_fcvt_s**之间的区别在于 *_Count*参数的解释。 **_ecvt_s**将 *_Count*解释为输出字符串中的总位数，而 **_fcvt_s**会将 *_Count*解释为小数点后的位数。

在 C++ 中，通过模板重载简化此函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

此函数的调试版本首先用0xFE 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|可选标头|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// ecvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( )
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_ecvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 12000
```

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
