---
title: c16rtomb, c32rtomb
ms.date: 01/22/2018
apiname:
- c16rtomb
- c32rtomb
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
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
ms.openlocfilehash: ad58184c7bab6f95a842bda5f9eb545f09434a3e
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702773"
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb, c32rtomb

在当前区域设置中将 UTF-16 或 UTF-32 宽字符转换为多字节字符。

## <a name="syntax"></a>语法

```C
size_t c16rtomb(
    char *mbchar,
    char16_t wchar,
    mbstate_t *state
);
size_t c32rtomb(
    char *mbchar,
    char32_t wchar,
    mbstate_t *state
);
```

### <a name="parameters"></a>参数

*mbchar*<br/>
指向用于存储转换后的多字节字符的数组的指针。

*wchar*<br/>
要转换的宽字符。

*state*<br/>
一个指向**mbstate_t**对象。

## <a name="return-value"></a>返回值

数组对象中存储的字节数*mbchar*，包括任何位移序列。 如果*wchar*不是有效的宽字符，值 (**size_t**返回)(-1) **errno**设置为**EILSEQ**，和值*状态*未指定。

## <a name="remarks"></a>备注

**C16rtomb**函数将 utf-16 字符*wchar*到当前区域设置中的等效多字节窄字符序列。 如果*mbchar*不是 null 指针，指向已转换的序列数组对象中的函数存储*mbchar*。 最多**MB_CUR_MAX**中存储的字节*mbchar*，并*状态*设置为生成的多字节位移状态。    如果*wchar*是 null 宽字符，则为所需的序列还原初始位移状态存储中，如果需要后跟 null 字符，并且*状态*设置为初始转换状态。 **C32rtomb**函数完全相同，但将 UTF-32 字符转换。

如果*mbchar*是空指针，该行为相当于替换内部缓冲区的函数调用*mbchar*和宽 null 字符*wchar*。

*状态*转换状态对象，可对此函数和其他维护的多字节输出字符的移位状态的可重启函数执行后续调用。 如果混合使用可重启和非可重启函数，或如果调用，结果不确定**setlocale**可重启函数调用之间进行。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**c16rtomb**， **c32rtomb**|C, C++: \<uchar.h>|

有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtoc16、mbrtoc32](mbrtoc16-mbrtoc323.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
