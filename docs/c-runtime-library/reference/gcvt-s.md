---
title: _gcvt_s
ms.date: 4/2/2020
api_name:
- _gcvt_s
- _o__gcvt_s
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
- _gcvt_s
- gcvt_s
helpviewer_keywords:
- _gcvt_s function
- _CVTBUFSIZE
- floating-point functions, converting number to string
- gcvt_s function
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
ms.openlocfilehash: 83e34bffbe62bf07d2d3f9f649d12607b0e08be7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919416"
---
# <a name="_gcvt_s"></a>_gcvt_s

将浮点值转换为字符串。 这是 [_gcvt](gcvt.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述的安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t _gcvt_s(
   char *buffer,
   size_t sizeInBytes,
   double value,
   int digits
);
template <size_t cchStr>
errno_t _gcvt_s(
   char (&buffer)[cchStr],
   double value,
   int digits
); // C++ only
```

### <a name="parameters"></a>参数

*宽限*<br/>
存储转换结果的缓冲区。

*sizeInBytes*<br/>
缓冲区的大小。

*value*<br/>
要转换的值。

*位数*<br/>
存储的有效位数。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 如果由于无效参数导致失败（请参阅下表中的无效值），则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则返回错误代码。 错误代码是在 Errno.h 中定义。 有关这些错误的列表，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>错误条件

|*宽限*|*sizeInBytes*|*value*|*位数*|返回|*缓冲区*中的值|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**Null**|any|any|any|**EINVAL**|未修改。|
|Not **NULL** （指向有效内存）|零|any|any|**EINVAL**|未修改。|
|Not **NULL** （指向有效内存）|any|any|>= *sizeInBytes*|**EINVAL**|未修改。|

**安全问题**

如果*缓冲区*未指向有效内存且不为**NULL**，则 **_gcvt_s**可以生成访问冲突。

## <a name="remarks"></a>备注

**_Gcvt_s**函数将浮点*值*转换为字符串（包含一个小数点和一个可能的符号字节），并将该字符串存储在*buffer*中。 *缓冲区*应足够大以容纳转换后的值加上自动追加的终止 null 字符。 长度 **_CVTBUFSIZE**的缓冲区足以满足任何浮点值。 如果使用了*数字*+ 1 的缓冲区大小，该函数将不会覆盖缓冲区的末尾，因此请确保为此操作提供足够的缓冲区。 **_gcvt_s**尝试以十进制格式生成*数字*位数。 如果不能，则它将以指数格式生成*位数*。 在转换过程中，可以取消零结尾。

在 C++ 中，通过模板重载简化此函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

此函数的调试版本首先用0xFE 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<error.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_gcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char buf[_CVTBUFSIZE];
    int decimal;
    int sign;
    int err;

    err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);

    if (err != 0)
    {
        printf("_gcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 1.2
```

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
