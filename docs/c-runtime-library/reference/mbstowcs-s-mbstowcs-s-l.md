---
title: mbstowcs_s、_mbstowcs_s_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
dev_langs:
- C++
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f366e01fbaa8da5c0dbc96ff4da324611e132f1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="mbstowcss-mbstowcssl"></a>mbstowcs_s, _mbstowcs_s_l

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
大小*wcstr*中单词的缓冲区。

*mbstr*<br/>
Null 终止的多字节字符序列的地址。

*count*<br/>
宽字符存储中的最大数*wcstr*缓冲区，不包括终止 null 或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果成功，返回零；如果失败，则返回错误代码。

|错误条件|返回值和**errno**|
|---------------------|------------------------------|
|*wcstr*是**NULL**和*sizeInWords* > 0|**EINVAL**|
|*mbstr*是**NULL**|**EINVAL**|
|目标缓冲区是太小，无法包含转换的字符串 (除非*计数*是 **_TRUNCATE**; 请参阅下面的备注)|**ERANGE**|
|*wcstr*不**NULL**和*sizeInWords* = = 0|**EINVAL**|

如果发生这些情况中的任何一个，都会调用无效参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，函数将返回错误代码和设置**errno**表中所示。

## <a name="remarks"></a>备注

**Mbstowcs_s**函数将指向的多字节字符的字符串转换*mbstr*存储指向的缓冲区中的宽字符*wcstr*。 在满足以下条件之一前，该转换将一直对每个字符执行：

- 遇到一个多字节空字符

- 遇到一个无效的多字节字符

- 存储中的宽字符数*wcstr*缓冲等于*计数*。

目标字符串始终以 null 结尾（即使在出错时）。

如果*计数*是特殊值[_TRUNCATE](../../c-runtime-library/truncate.md)，然后**mbstowcs_s**将尽可能多的字符串作为将放入目标缓冲区中，同时仍保持 null 的空间终结器。

如果**mbstowcs_s**成功转换了源字符串，它将大小放在宽字符的转换的字符串，包括 null 终止符，更改为 *&#42;pReturnValue* (提供*pReturnValue*不**NULL**)。 发生这种情况即使*wcstr*自变量是**NULL** ，并提供了一种方法来确定所需的缓冲区大小。 请注意，如果*wcstr*是**NULL**，*计数*将被忽略，和*sizeInWords*必须为 0。

如果**mbstowcs_s**遇到无效的多字节字符，它将 0 放在 *&#42;pReturnValue*，将目标缓冲区设置为一个空字符串，设置**errno**到**EILSEQ**，并返回**EILSEQ**。

如果指向的序列*mbstr*和*wcstr*重叠的行为**mbstowcs_s**是不确定的。

> [!IMPORTANT]
> 确保*wcstr*和*mbstr*未重叠，且*计数*正确反映了要转换的多字节字符的数量。

**mbstowcs_s**的任何区域设置相关行为，则使用当前区域设置 **_mbstowcs_s_l**具有完全相同，只不过它改用已传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**mbstowcs_s**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
