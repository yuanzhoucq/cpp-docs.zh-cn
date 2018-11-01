---
title: _fcvt_s
ms.date: 04/05/2018
apiname:
- _fcvt_s
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
- fcvt_s
- _fcvt_s
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
ms.openlocfilehash: 51ff3c675f1f53aee9beab629b17193164a2e7eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536839"
---
# <a name="fcvts"></a>_fcvt_s

将浮点数转换为字符串。 这是 [_fcvt](fcvt.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t _fcvt_s(
   char* buffer,
   size_t sizeInBytes,
   double value,
   int count,
   int *dec,
   int *sign
);
template <size_t size>
errno_t _fcvt_s(
   char (&buffer)[size],
   double value,
   int count,
   int *dec,
   int *sign
); // C++ only
```

### <a name="parameters"></a>参数

*buffer*<br/>
所提供的缓冲区将保留转换的结果。

*sizeInBytes*<br/>
缓冲区的大小（以字节为单位）。

*value*<br/>
要转换的数字。

*count*<br/>
小数点后面的数字位数。

*dec*<br/>
指向存储的小数点位置的指针。

*sign*<br/>
指向存储的符号指示符的指针。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 如果失败，则返回值为错误代码。 错误代码是在 ERRNO.h 中定义的。 有关这些错误的列表，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

对于无效参数（如下表中所列），此函数调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，此函数可设置**errno**到**EINVAL** ，并返回**EINVAL**。

### <a name="error-conditions"></a>错误条件

|*buffer*|*sizeInBytes*|值|count|dec|Sign|返回|中的值*缓冲区*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**NULL**|任何|任何|任何|任何|任何|**EINVAL**|未修改。|
|不**NULL** （指向有效内存）|<=0|任何|任何|任何|任何|**EINVAL**|未修改。|
|任何|任何|任何|任何|**NULL**|任何|**EINVAL**|未修改。|
|任何|任何|任何|任何|任何|**NULL**|**EINVAL**|未修改。|

## <a name="security-issues"></a>安全性问题

**_fcvt_s**时，可能会产生访问冲突*缓冲区*不指向有效内存且不**NULL**。

## <a name="remarks"></a>备注

**_Fcvt_s**函数将浮点数转换为以 null 结尾的字符串。 *值*参数是要转换的浮点数。 **_fcvt_s**存储的位数*值*作为一个字符串，并追加 null 字符 (\0)。 *计数*参数指定要存储在小数点后的位数。 多余的位数被舍入到*计数*放置。 如果少于*计数*用零填充数字的精度，该字符串。

字符串中仅存储位数。 小数点和的符号的位置*值*可从此*dec*并*登录*后调用。 *Dec*参数指向一个整数值; 此整数值指定相对于字符串开头的小数点的位置。 零或负整数值表示小数点位于第一个数字的左侧。 将参数*符号*指向一个整数，指示的符号*值*。 整数设置为 0，如果*值*为正，设置为非零数字*值*为负。

缓冲区长度 **_CVTBUFSIZE**足以满足任何浮点值。

之间的差异 **_ecvt_s**并 **_fcvt_s**中的解释*计数*参数。 **_ecvt_s**解释*计数*输出字符串中的位数总数和 **_fcvt_s**解释*计数*后的位数小数点。

在 C++ 中，通过模板重载简化此函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

此函数的调试版本首先使用 0xFD 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|可选标头|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<stdlib.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

**库：** [CRT 库功能](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// fcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_fcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 120000
```

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
