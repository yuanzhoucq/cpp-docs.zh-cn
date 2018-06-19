---
title: _mbccpy_s、_mbccpy_s_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbccpy_s
- _mbccpy_s_l
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
apitype: DLLExport
f1_keywords:
- _mbccpy_s_l
- mbccpy_s_l
- mbccpy_s
- _mbccpy_s
dev_langs:
- C++
helpviewer_keywords:
- tccpy_s_l function
- _tccpy_s function
- _mbccpy_s function
- mbccpy_s function
- tccpy_s function
- mbccpy_s_l function
- _tccpy_s_l function
- _mbccpy_s_l function
ms.assetid: b6e965fa-53c1-4ec3-85ef-a1c4b4f2b2da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a3a52314209b62c818623e315757dcd358ec491
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404023"
---
# <a name="mbccpys-mbccpysl"></a>_mbccpy_s、_mbccpy_s_l

将一个多字节字符从一个字符串复制到另一个字符串。 这些版本的 [_mbccpy、_mbccpy_l](mbccpy-mbccpy-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
errno_t _mbccpy_s(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src
);
errno_t _mbccpy_s_l(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src,
   locale_t locale
);
template <size_t size>
errno_t _mbccpy_s(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbccpy_s_l(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src,
   locale_t locale
); // C++ only
```

### <a name="parameters"></a>参数

*dest*<br/>
复制目标。

*buffSizeInBytes*<br/>
目标缓冲区的大小。

*pCopied*<br/>
填充复制的字节数（如果成功则为 1 或 2）。 传递**NULL**如果你不关心数。

*src*<br/>
要复制的多字节字符。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果成功，则为零；如果失败，则为错误代码。 如果*src*或*dest*是**NULL**，或如果多个**buffSizeinBytes**字节都要复制到*dest*，然后调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，函数将返回**EINVAL**和**errno**设置为**EINVAL**。

## <a name="remarks"></a>备注

**_Mbccpy_s**函数将复制一个多字节字符从*src*到*dest*。 如果*src*未指向所确定的隐式调用那样多字节字符的前导字节[_ismbblead](ismbblead-ismbblead-l.md)，然后单字节的*src*复制到的点。 如果*src*指向前导字节，但下一个字节 0 和因此无效，则 0 复制到*dest*， **errno**设置为**EILSEQ**，与函数返回**EILSEQ**。

**_mbccpy_s**不附加 null 终止符的占用; 但是，如果*src*指向 null 字符，则该 null 将复制到*dest* （这是只是常规的单字节副本）。

中的值*pCopied*填入复制的字节数。 如果操作成功，则可能的值为 1 和 2。 如果**NULL**传递在中，忽略此参数。

|*src*|复制到*目标*|*pCopied*|返回值|
|-----------|----------------------|---------------|------------------|
|非前导字节|非前导字节|1|0|
|0|0|1|0|
|前导字节，后跟非零值|前导字节，后跟非零值|2|0|
|前导字节，后跟 0|0|1|**EILSEQ**|

请注意，第二行只是第一行的特殊情况。 另请注意，此表假定*buffSizeInBytes* >= *pCopied*。

**_mbccpy_s**的任何区域设置相关行为使用当前区域设置。 **_mbccpy_s_l**等同于 **_mbccpy_s**只不过 **_mbccpy_s_l**使用为任何区域设置相关的行为传入的区域设置。

在 C++ 中，通过模板重载简化这些函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|映射到宏或内联函数。|**_mbccpy_s**|映射到宏或内联函数。|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
