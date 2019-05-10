---
title: _mbsnbcat_s、_mbsnbcat_s_l
ms.date: 11/04/2016
apiname:
- _mbsnbcat_s_l
- _mbsnbcat_s
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
- _mbsnbcat_s
- mbsnbcat_s
- _mbsnbcat_s_l
- mbsnbcat_s_l
helpviewer_keywords:
- _tcsncat function
- mbsnbcat_s function
- _mbsnbcat_s function
- _mbsnbcat_s_l function
- _tcsncat_s_l function
- tcsncat_s_l function
- mbsnbcat_s_l function
- tcsncat function
ms.assetid: 2c9e9be7-d979-4a54-8ada-23428b6648a9
ms.openlocfilehash: d7e7a9d121336486e590ca3bd9e3967b02a2df08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331514"
---
# <a name="mbsnbcats-mbsnbcatsl"></a>_mbsnbcat_s、_mbsnbcat_s_l

将追加到多字节字符字符串，最多，第一个**n**的另一个多字节字符字符串的字节数。 这些版本的 [_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
errno_t _mbsnbcat_s(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count
);
errno_t _mbsnbcat_s_l(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbcat_s(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbcat_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>参数

*dest*<br/>
以 null 终止的多字节字符目标字符串。

*sizeInBytes*<br/>
大小*dest*以字节为单位的缓冲区。

*src*<br/>
以 null 终止的多字节字符源字符串。

*count*<br/>
中的字节数*src*要追加到*dest*。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果成功，则为零；否则为错误代码。

### <a name="error-conditions"></a>错误条件

|**dest**|*sizeInBytes*|*src*|返回值|
|------------|-------------------|-----------|------------------|
|**NULL**|任何|任何|**EINVAL**|
|任意|<= 0|任何|**EINVAL**|
|任意|任何|**NULL**|**EINVAL**|

如果出现任何一个错误状态，该函数生成无效参数错误，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果处理错误，则该函数将返回**EINVAL** ，并设置**errno**到**EINVAL**。

## <a name="remarks"></a>备注

**_Mbsnbcat_s**函数将追加到*dest*，最多，第一个*计数*字节*src*。如果字节紧跟在 null 字符*dest*是前导字节，它会覆盖的初始字节*src*。否则为的初始字节*src*覆盖的终止 null 字符*dest*。 如果 null 字节出现在*src*之前*计数*字节追加 **_mbsnbcat_s**追加从所有字节*src*，最多为 null字符。 如果*计数*大于的长度*src*，时长*src*用来代替*计数*。 生成的字符串由 null 字符终止。 如果复制出现在重叠的字符串之间，则该行为不确定。

输出值受的设置**LC_CTYPE**的区域设置的类别设置影响; 请参阅[setlocale、 _wsetlocale](setlocale-wsetlocale.md)有关详细信息。 这些函数的版本是相同的不同之处在于不具有 **_l**后缀使用当前区域设置以及是否有那些 **_l**后缀改为使用区域设置参数的传入。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度，从而不再需要指定大小自变量，并且它们可以自动使用更新、更安全的函数替换较旧、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

这些函数的调试版本首先用 0xFD 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat_s**|[wcsncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_s_l**|**_strncat_s_l**|**_mbsnbcat_s_l**|**_wcsncat_s_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_mbsnbcat_s**|\<mbstring.h>|
|**_mbsnbcat_s_l**|\<mbstring.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy、_mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbcpy_s、_mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md)<br/>
[_mbsnbset、_mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)<br/>
