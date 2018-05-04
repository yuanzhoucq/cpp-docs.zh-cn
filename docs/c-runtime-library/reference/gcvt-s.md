---
title: _gcvt_s | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _gcvt_s
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
- _gcvt_s
- gcvt_s
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a2bd12a63db064bca0c880484f99a2df9d210f8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="gcvts"></a>_gcvt_s

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

*buffer*<br/>
存储转换结果的缓冲区。

*sizeInBytes*<br/>
缓冲区的大小。

*value*<br/>
要转换的值。

*digits*<br/>
存储的有效位数。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 如果由于无效参数导致失败（请参阅下表中的无效值），则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则返回错误代码。 错误代码是在 Errno.h 中定义的。 有关这些错误的列表，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>错误条件

|*buffer*|*sizeInBytes*|*value*|*digits*|返回|中的值*缓冲区*|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**NULL**|任何|任何|任何|**EINVAL**|未修改。|
|不**NULL** （指向有效的内存）|零|任何|任何|**EINVAL**|未修改。|
|不**NULL** （指向有效的内存）|任何|任何|>= *sizeInBytes*|**EINVAL**|未修改。|

**安全问题**

**_gcvt_s**可以生成访问冲突，如果*缓冲区*不指向有效内存并且不是**NULL**。

## <a name="remarks"></a>备注

**_Gcvt_s**函数将转换浮点*值*为字符字符串 （其中包括小数点和可能的登录字节），并将存储中的字符串*缓冲区*. *缓冲区*应足够大，以适应转换后的值加上会自动追加终止 null 字符。 缓冲区的长度 **_CVTBUFSIZE**足以满足任何浮点值。 如果缓冲区大小为*数字*+ 则使用 1，该函数将不会覆盖末尾的缓冲区，因此请确保提供足够的缓冲区对于此操作。 **_gcvt_s**尝试生成*数字*以十进制格式的数字。 如果无法实现，它会生成*数字*指数格式的数字。 在转换过程中，可以取消零结尾。

在 C++ 中，通过模板重载简化此函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

此函数的调试版本首先使用 0xFD 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<error.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
