---
title: c16rtomb, c32rtomb
ms.date: 10/22/2019
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
ms.openlocfilehash: 8f480d9b450b528275fea78ae878269fa6a4fa54
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811062"
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb, c32rtomb

将 UTF-16 或 UTF-32 宽字符转换为 UTF-8 多字节字符。

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

*mbchar*\
指向用于存储转换后的 UTF-8 多字节字符的数组的指针。

*wchar*\
要转换的宽字符。

*状态*\
指向**mbstate_t**对象的指针。

## <a name="return-value"></a>返回值

数组对象*mbchar*中存储的字节数，包括任何移位序列。 如果*wchar*不是有效的宽字符，则返回值（**size_t**）（-1）， **errno**设置为**eilseq 且**，*状态*的值未指定。

## <a name="remarks"></a>备注

**C16rtomb**函数将 utf-16 LE 字符*wchar*转换为等效的 utf-8 多字节窄字符序列。 如果*mbchar*不是空指针，则该函数将转换后的序列存储在由*mbchar*指向的数组对象中。 最多**MB_CUR_MAX**字节存储在*mbchar*中，*状态*设置为生成的多字节移位状态。

如果*wchar*是 null 宽字符，则会存储还原初始移位状态所需的序列，如果需要，后面跟 null 字符。 *状态*设置为初始转换状态。 **C32rtomb**函数是相同的，但会转换32字符。

如果*mbchar*为 null 指针，则行为等效于调用函数的函数，该函数将内部缓冲区替换为*mbchar* ，将宽 null 字符替换为*wchar*。

通过*状态*转换状态对象，您可以对此函数和其他保留多字节输出字符的移位状态的可重启函数进行后续调用。 混合使用可重启和不可重启的功能时，结果是不确定的。

若要将 UTF-16 字符转换为非 UTF-8 多字节字符，请使用[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)、 [wcstombs_s 或 _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md)函数。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**c16rtomb**、 **c32rtomb**|C, C++: \<uchar.h>|

有关兼容性信息，请参阅 [兼容性](../compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../data-conversion.md)\
[区域设置](../locale.md)\
[多字节字符序列的解释](../interpretation-of-multibyte-character-sequences.md)\
[mbrtoc16、mbrtoc32](mbrtoc16-mbrtoc323.md)\
[wcrtomb](wcrtomb.md)\
[wcrtomb_s](wcrtomb-s.md)
