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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: e33840e772de770e0f05ae45d2c2d4bec7e09939
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348045"
---
# <a name="_ecvt_s"></a>_ecvt_s

将**双**数转换为字符串。 这是 [_ecvt](ecvt.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

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

对于无效参数（如下表中所列），此函数调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，此函数将**errno**设置到**EINVAL**并返回**EINVAL**。

### <a name="error-conditions"></a>错误条件

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|返回值|*缓冲区*中的值|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**空**|any|any|any|any|any|**埃因瓦尔**|未修改。|
|**非 NULL（** 指向有效内存）|<=0|any|any|any|any|**埃因瓦尔**|未修改。|
|any|any|any|any|**空**|any|**埃因瓦尔**|未修改。|
|any|any|any|any|any|**空**|**埃因瓦尔**|未修改。|

## <a name="security-issues"></a>安全问题

如果*缓冲区*不指向有效内存且不是**NULL，_ecvt_s**可能会生成访问冲突。 **NULL**

## <a name="remarks"></a>备注

**_ecvt_s**函数将浮点数转换为字符串。 *_Value*参数是要转换的浮点数。 此函数最多存储 *_Value**的数字作为字符串*，并追加一个空字符 （'\0'）。 如果 *_Value*的数字数超过 *_Count，* 则低阶数字为四舍五入。 如果*数字少于计数*数字，则字符串将用零填充。

字符串中仅存储位数。 小数点的位置和 *_Value*标志可以从*调用后_Dec**和_Sign*获得。 *_Dec*参数指向一个整数值，该值给出相对于字符串开头的小数点的位置。 0 或负整数值表示小数点位于第一个数字的左侧。 *_Sign*参数指向指示转换数字符号的整数。 如果整数值为 0，则数值为正值。 否认，数值为负值。

长度 **_CVTBUFSIZE**缓冲区对于任何浮点值都足够。

**_ecvt_s**和 **_fcvt_s**的区别在于 *_Count参数的解释*。 **_ecvt_s**将 *_Count*解释为输出字符串中的总位数，而 **_fcvt_s**将 *_Count*解释为小数点之后的位数。

在 C++ 中，通过模板重载简化此函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

此函数的调试版本首先用 0xFE 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

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
