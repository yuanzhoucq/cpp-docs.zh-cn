---
title: _ecvt_s | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _ecvt_s
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
- ecvt_s
- _ecvt_s
dev_langs:
- C++
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6f3cfd36a2a1466a66e4febfcbfc9e00b0b0e47a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="ecvts"></a>_ecvt_s

将转换**double**编号为字符串。 这是 [_ecvt](ecvt.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

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

对于无效参数（如下表中所列），此函数调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，此函数将**errno**到**EINVAL**并返回**EINVAL**。

### <a name="error-conditions"></a>错误条件

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|返回值|中的值*缓冲区*|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**NULL**|任何|任何|任何|任何|任何|**EINVAL**|未修改。|
|不**NULL** （指向有效的内存）|<=0|任何|任何|任何|任何|**EINVAL**|未修改。|
|任何|任何|任何|任何|**NULL**|任何|**EINVAL**|未修改。|
|任何|任何|任何|任何|任何|**NULL**|**EINVAL**|未修改。|

## <a name="security-issues"></a>安全性问题

**_ecvt_s**可能会产生访问冲突，如果*缓冲区*不指向有效内存并且不是**NULL**。

## <a name="remarks"></a>备注

**_Ecvt_s**函数将浮点数转换为字符字符串。 *_Value*参数是要转换的浮点数。 此函数将存储最多*计数*位数 *_Value*作为字符串，并追加 null 字符 (\0)。 如果数字的位数 *_Value*超过 *_Count*，低序位数字舍入。 如果有数不能超过*计数*用零填充数字、 字符串。

字符串中仅存储位数。 小数点和的符号的位置 *_Value*可以从获取 *_Dec*和 *_Sign*后调用。 *_Dec*参数指向提供与该字符串的开头小数点的位置的整数值。 0 或负整数值表示小数点位于第一个数字的左侧。 *_Sign*参数指向一个整数，表示转换后的数字的符号。 如果整数值为 0，则数值为正值。 否认，数值为负值。

缓冲区的长度 **_CVTBUFSIZE**足以满足任何浮点值。

之间的差异 **_ecvt_s**和 **_fcvt_s**处于的解释 *_Count*参数。 **_ecvt_s**解释 *_Count*作为的输出字符串中的位数总数而 **_fcvt_s**解释 *_Count*后的位数的数字的形式小数点。

在 C++ 中，通过模板重载简化此函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

此函数的调试版本首先使用 0xFD 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|可选标头|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
