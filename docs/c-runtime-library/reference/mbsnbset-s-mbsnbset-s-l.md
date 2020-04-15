---
title: _mbsnbset_s、_mbsnbset_s_l
ms.date: 4/2/2020
api_name:
- _mbsnbset_s_l
- _mbsnbset_s
- _o__mbsnbset_s
- _o__mbsnbset_s_l
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
- mbsnbset_s
- _mbsnbset_s_l
- _mbsnbset_s
- mbsnbset_s_l
helpviewer_keywords:
- tcsnset_s function
- mbsnbset_s function
- mbsnbset_s_l function
- _mbsnbset_s_l function
- _tcsnset_s_l function
- _mbsnbset_s function
- _tcsnset_s function
- tcsnset_s_l function
ms.assetid: 811f92c9-cc31-4bbd-8017-2d1bfc6fb96f
ms.openlocfilehash: 0ecfac1f9c0f1f9aeb8de85411b0b2f696b578e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81339012"
---
# <a name="_mbsnbset_s-_mbsnbset_s_l"></a>_mbsnbset_s、_mbsnbset_s_l

将多字节字符串的第一个**n**字节设置为指定的字符。 这些版本的 [_mbsnbset、_mbsnbset_l](mbsnbset-mbsnbset-l.md) 具有安全性增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
errno_t _mbsnbset_s(
   unsigned char *str,
   size_t size,
   unsigned int c,
   size_t count
);
errno_t _mbsnbset_s_l(
   unsigned char *str,
   size_t size,
   unsigned int c,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbset_s(
   unsigned char (&str)[size],
   unsigned int c,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbset_s_l(
   unsigned char (&str)[size],
   unsigned int c,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>参数

*Str*<br/>
要修改的字符串。

*大小*<br/>
字符串缓冲区的大小。

*C*<br/>
单字节或多字节字符设置。

*count*<br/>
要设置的字节数。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果成功，则为零；否则为错误代码。

## <a name="remarks"></a>备注

**_mbsnbset_s**和 **_mbsnbset_s_l**函数最多设置*str*到*c*的第一个*计数*字节。 如果*计数*大于*str*的长度，则使用*str*的长度而不是*计数*。 如果*c*是多字节字符，并且不能完全设置为由*count*指定的最后一个字节，则最后一个字节将填充一个空白字符。 **_mbsnbset_s**和 **_mbsnbset_s_l**不会在*str*的末尾放置终止 null。

**_mbsnbset_s**和 **_mbsnbset_s_l**类似于 **_mbsnset，** 只是它们设置*计数*字节而不是*计算* *c*的字符。

如果*str*为**NULL**或*计数*为零，则此函数将生成无效参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行 **，errno**将设置为**EINVAL，** 并且函数返回**NULL**。 此外，如果*c*不是有效的多字节字符，**则 errno**设置为**EINVAL，** 并改用空格。

输出值受区域设置**LC_CTYPE**类别设置的影响;有关详细信息[，请参阅集本地设置_wsetlocale。](setlocale-wsetlocale.md) 此函数**的_mbsnbset_s**版本使用此与区域设置相关的行为的当前区域设置;**_mbsnbset_s_l**版本相同，只是它使用传入区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，这些函数的使用由模板重载简化；重载可以自动推导出缓冲区长度，从而不再需要指定大小自变量。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

这些函数的调试库版本首先用 0xFE 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnset_s**|**_strnset_s**|**_mbsnbset_s**|**_wcsnset_s**|
|**_tcsnset_s_l**|`_strnset_s _l`|**_mbsnbset_s_l**|**_wcsnset_s_l**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_mbsnbset_s**|\<mbstring.h>|
|**_mbsnbset_s_l**|\<mbstring.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_mbsnbset_s.c
#include <mbstring.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 bytes of string to be *'s */
   printf( "Before: %s\n", string );
   _mbsnbset_s( string, sizeof(string), '*', 4 );
   printf( "After:  %s\n", string );
}
```

## <a name="output"></a>输出

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>另请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_strnset、_strnset_l、_wcsnset、_wcsnset_l、_mbsnset、_mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
