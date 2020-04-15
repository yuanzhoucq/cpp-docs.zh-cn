---
title: mbstowcs_s, _mbstowcs_s_l
ms.date: 4/2/2020
api_name:
- _mbstowcs_s_l
- mbstowcs_s
- _o__mbstowcs_s_l
- _o_mbstowcs_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
ms.openlocfilehash: 07d694a7430f23e2f9600a5d2b147bcee2ef0e09
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338808"
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

*p 返回值*<br/>
要转换的字符数。

*wc斯特*<br/>
用于转换所生成的宽字符串的缓冲区地址。

*大小字内*<br/>
单词中*wcstr*缓冲区的大小。

*姆布斯特*<br/>
Null 终止的多字节字符序列的地址。

*count*<br/>
要存储在*wcstr*缓冲区中的最大宽字符数，不包括终止 null 或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果成功，返回零；如果失败，则返回错误代码。

|添加状态|返回值和**差错**|
|---------------------|------------------------------|
|*wcstr*为**NULL，***大小 >* 0|**埃因瓦尔**|
|*mbstr*为**NULL**|**埃因瓦尔**|
|目标缓冲区太小，无法包含转换后的字符串（除非*计数***_TRUNCATE;** 请参阅下面的备注）|**ERANGE**|
|*wcstr*不是**NULL，***大小 InWords* = 0|**埃因瓦尔**|

如果发生这些情况中的任何一个，都会调用无效参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数将返回错误代码并设置表中指示的**errno。**

## <a name="remarks"></a>备注

**mbstowcs_s**函数将*mbstr*指向的多字节字符字符串转换为存储在*wcstr*指向的缓冲区中的宽字符。 在满足以下条件之一前，该转换将一直对每个字符执行：

- 遇到一个多字节空字符

- 遇到一个无效的多字节字符

- 存储在*wcstr*缓冲区中的宽字符数等于*计数*。

目标字符串始终以 null 结尾（即使在出错时）。

如果*count*是[特殊值_TRUNCATE，](../../c-runtime-library/truncate.md)则**mbstowcs_s**转换尽可能多的字符串，以适应目标缓冲区，同时仍然留有空终止符的空间。

如果**mbstowcs_s**成功转换源字符串，它将转换后的字符串（包括空终止符）的大小放入 *&#42;pReturnValue（* 前提是*pReturnValue*不是**NULL）。** 即使*wcstr*参数为**NULL，** 并提供一种确定所需缓冲区大小的方法，也会发生这种情况。 请注意，如果*wcstr*为**NULL，** 则忽略*计数*，*大小 InWords*必须为 0。

如果**mbstowcs_s**遇到无效的多字节字符，它将在*pReturnValue&#42;* 中放入 0，将目标缓冲区设置为空字符串，将**errno**设置到**EILSEQ，** 并返回**EILSEQ**。

如果*mbstr*和*wcstr*指向的序列重叠，则**mbstowcs_s**的行为未定义。

> [!IMPORTANT]
> 确保*wcstr*和*mbstr*不重叠，并且*该计数*正确反映要转换的多字节字符数。

**mbstowcs_s**将当前区域设置用于任何与区域设置相关的行为;**_mbstowcs_s_l**是相同的，只是它使用传入区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**mbstowcs_s**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
