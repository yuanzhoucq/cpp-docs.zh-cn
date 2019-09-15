---
title: c16rtomb, c32rtomb
ms.date: 01/22/2018
api_name:
- c16rtomb
- c32rtomb
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
ms.openlocfilehash: a16effe48442ccbb5144b57ead2fb15c908fe898
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943432"
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

State<br/>
指向**mbstate_t**对象的指针。

## <a name="return-value"></a>返回值

数组对象*mbchar*中存储的字节数，包括任何移位序列。 如果*wchar*不是有效的宽字符，则返回值（**size_t**）（-1）， **errno**设置为**eilseq 且**，*状态*的值未指定。

## <a name="remarks"></a>备注

**C16rtomb**函数将 utf-16 字符*wchar*转换为当前区域设置中的等效多字节窄字符序列。 如果*mbchar*不是空指针，则该函数将转换后的序列存储在由*mbchar*指向的数组对象中。 最多**MB_CUR_MAX**字节存储在*mbchar*中，*状态*设置为生成的多字节移位状态。    如果*wchar*是 null 宽字符，则会存储还原初始移位状态所需的序列，如果需要，后面跟 null 字符，*状态*设置为初始转换状态。 **C32rtomb**函数是相同的，但会转换32字符。

如果*mbchar*为 null 指针，则行为等效于调用函数的函数，该函数将内部缓冲区替换为*mbchar* ，将宽 null 字符替换为*wchar*。

通过*状态*转换状态对象，您可以对此函数和其他保留多字节输出字符的移位状态的可重启函数进行后续调用。 混合使用可重启和非可重启的函数时，或者如果在可重启的函数调用之间进行了**setlocale**调用，则结果是不确定的。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**c16rtomb**、 **c32rtomb**|C, C++: \<uchar.h>|

有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtoc16、mbrtoc32](mbrtoc16-mbrtoc323.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
