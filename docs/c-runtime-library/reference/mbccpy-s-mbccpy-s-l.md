---
title: _mbccpy_s、_mbccpy_s_l
ms.date: 4/2/2020
api_name:
- _mbccpy_s
- _mbccpy_s_l
- _o__mbccpy_s
- _o__mbccpy_s_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbccpy_s_l
- mbccpy_s_l
- mbccpy_s
- _mbccpy_s
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
ms.openlocfilehash: 08df395c6978c84b3f53ed0b07ce988afd0249f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341236"
---
# <a name="_mbccpy_s-_mbccpy_s_l"></a>_mbccpy_s、_mbccpy_s_l

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

dest**<br/>
复制目标。

*福西斯字节*<br/>
目标缓冲区的大小。

*p复制*<br/>
填充复制的字节数（如果成功则为 1 或 2）。 如果您不关心该号码，则通过**NULL。**

*src*<br/>
要复制的多字节字符。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果成功，则为零；如果失败，则为错误代码。 如果*src*或*dest*为**NULL，** 或者如果将多个**buffSizein字节**字节复制到*dest，* 则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数返回**EINVAL，errno**设置为**EINVAL**。 **errno**

## <a name="remarks"></a>备注

**_mbccpy_s**函数将一个多字节字符从*src*复制到*dest*。 如果*src*不指向由对[_ismbblead](ismbblead-ismbblead-l.md)的隐式调用确定的多字节字符的引线字节，则复制*src*指向的单个字节。 如果*src*指向一个引线字节，但下面的字节是 0，因此无效，则 0 被复制到*dest* **，errno**设置为**EILSEQ**，并且函数返回**EILSEQ**。

**_mbccpy_s**不追加空终止符;否则，_mbccpy_s将附加空终止符。但是，如果*src*指向空字符，则该空将复制到*dest（* 这只是常规的单字节副本）。

*pCopied*中的值用复制的字节数填充。 如果操作成功，则可能的值为 1 和 2。 如果传入**NULL，** 则忽略此参数。

|*src*|复制到*dest*|*p复制*|返回值|
|-----------|----------------------|---------------|------------------|
|非前导字节|非前导字节|1|0|
|0|0|1|0|
|前导字节，后跟非零值|前导字节，后跟非零值|2|0|
|前导字节，后跟 0|0|1|**EILSEQ**|

请注意，第二行只是第一行的特殊情况。 另请注意，该表假定*为 buffsizeInBYpb* >= *pcopied*。

**_mbccpy_s**对任何与区域设置相关的行为使用当前区域设置。 **_mbccpy_s_l**与 **_mbccpy_s**相同，只是 **_mbccpy_s_l**使用传入的任何区域设置相关的行为。

在 C++ 中，通过模板重载简化这些函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|映射到宏或内联函数。|**_mbccpy_s**|映射到宏或内联函数。|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[现场](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
