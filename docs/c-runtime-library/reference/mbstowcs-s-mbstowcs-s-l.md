---
title: mbstowcs_s, _mbstowcs_s_l
ms.date: 11/04/2016
apiname:
- _mbstowcs_s_l
- mbstowcs_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
ms.openlocfilehash: 7a1c29118c48bbbb5358e7d7ea57296f7ec908a8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499761"
---
# <a name="mbstowcs_s-_mbstowcs_s_l"></a>mbstowcs_s, _mbstowcs_s_l

将多字节字符序列转换为对应的宽字符序列。 这些版本的 [mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

## <a name="syntax"></a>语法

```C
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count
);
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>参数

*pReturnValue*<br/>
要转换的字符数。

*wcstr*<br/>
用于转换所生成的宽字符串的缓冲区地址。

*sizeInWords*<br/>
*Wcstr*缓冲区的大小 (以单词为限)。

*mbstr*<br/>
Null 终止的多字节字符序列的地址。

*计数*<br/>
要存储在*wcstr*缓冲区中的宽字符的最大数量, 不包括终止 Null 或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果成功，返回零；如果失败，则返回错误代码。

|错误条件|返回值和**errno**|
|---------------------|------------------------------|
|*wcstr*为**NULL** , *sizeInWords* > 0|**EINVAL**|
|*mbstr*为**NULL**|**EINVAL**|
|目标缓冲区太小, 无法包含转换后的字符串 (除非*计数*为 **_TRUNCATE**; 请参阅下面的备注)|**ERANGE**|
|*wcstr*不为**NULL** , *sizeInWords* = = 0|**EINVAL**|

如果发生这些情况中的任何一个，都会调用无效参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续, 则该函数将返回错误代码并按表中所示设置**errno** 。

## <a name="remarks"></a>备注

**Mbstowcs_s**函数将*mbstr*指向的多字节字符的字符串转换为存储在*wcstr*所指向的缓冲区中的宽字符。 在满足以下条件之一前，该转换将一直对每个字符执行：

- 遇到一个多字节空字符

- 遇到一个无效的多字节字符

- 存储在*wcstr*缓冲区中的宽字符数等于*count*。

目标字符串始终以 null 结尾（即使在出错时）。

如果*count*是特殊值[_TRUNCATE](../../c-runtime-library/truncate.md), 则**mbstowcs_s**会将尽可能多的字符串转换为目标缓冲区的大小, 同时仍然为 null 终止符留下空间。

如果**mbstowcs_s**成功转换了源字符串, 它会将转换后的字符串 (包括 null 终止符) 的宽字符大小放入 *&#42;pReturnValue* (前提是*pReturnValue*不为**null**)。 即使*wcstr*参数为**NULL** , 并且提供了一种方法来确定所需的缓冲区大小, 也会发生这种情况。 请注意, 如果*wcstr*为**NULL**, 则忽略*count* , 而*sizeInWords*必须为0。

如果**mbstowcs_s**遇到无效的多字节字符, 它将在 *&#42;pReturnValue*中放置 0, 将目标缓冲区设置为空字符串, 将**errno**设置为**eilseq 且**, 并返回**eilseq 且**。

如果由*mbstr*和*wcstr*指向的序列重叠, 则**mbstowcs_s**的行为不确定。

> [!IMPORTANT]
> 确保*wcstr*和*mbstr*不重叠, 并且该*计数*正确反映了要转换的多字节字符的数量。

**mbstowcs_s**为任何与区域设置相关的行为使用当前区域设置; **_mbstowcs_s_l**是相同的, 只不过它使用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**mbstowcs_s**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
