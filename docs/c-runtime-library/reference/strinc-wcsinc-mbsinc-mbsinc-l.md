---
title: _strinc、_wcsinc、_mbsinc、_mbsinc_l
ms.date: 11/04/2016
apiname:
- _mbsinc
- _wcsinc
- _mbsinc_l
- _strinc
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
- mbsinc_l
- _strinc
- strinc
- _mbsinc
- _wcsinc
- wcsinc
- mbsinc
- _mbsinc_l
helpviewer_keywords:
- _mbsinc function
- wcsinc function
- mbsinc_l function
- _strinc function
- strinc function
- _mbsinc_l function
- mbsinc function
- _wcsinc function
- _tcsinc function
- tcsinc function
ms.assetid: 54685943-8e2c-45e9-a559-2d94930dc6b4
ms.openlocfilehash: 48bc7caa5dbc2d2e7eec847bfa5135d13bcd83c0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499472"
---
# <a name="_strinc-_wcsinc-_mbsinc-_mbsinc_l"></a>_strinc、_wcsinc、_mbsinc、_mbsinc_l

比字符串指针提前一个字符。

> [!IMPORTANT]
> **_mbsinc**和 **_mbsinc_l**不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
char *_strinc(
   const char *current,
   _locale_t locale
);
wchar_t *_wcsinc(
   const wchar_t *current,
   _locale_t locale
);
unsigned char *_mbsinc(
   const unsigned char *current
);
unsigned char *_mbsinc_l(
   const unsigned char *current,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*current*<br/>
字符指针。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

其中每个例程都将返回一个指向紧跟在*当前*后面的字符的指针。

## <a name="remarks"></a>备注

**_Mbsinc**函数返回一个指针, 该指针指向紧跟在*当前*后面的多字节字符的第一个字节。 **_mbsinc**根据当前正在使用的[多字节代码页](../../c-runtime-library/code-pages.md)识别多字节字符序列; **_mbsinc_l**是相同的, 只不过它改用传入的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在 Tchar 中定义的一般文本函数 **_tcsinc**映射到 **_mbsinc** (如果已定义 **_MBCS** ); 如果定义了 **_wcsinc** , 则映射到 **_UNICODE** 。 否则, **_tcsinc**将映射到 **_strinc**。 **_strinc**和 **_wcsinc**是 **_mbsinc**的单字节字符和宽字符版本。 仅为此映射提供了 **_strinc**和 **_wcsinc** , 否则不应使用它。 有关详细信息，请参阅[使用一般文本映射](../../c-runtime-library/using-generic-text-mappings.md)和[一般文本映射](../../c-runtime-library/generic-text-mappings.md)。

如果*current*为**NULL**, 则调用无效参数处理程序, 如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续, 则此函数将返回**EINVAL** , 并将**Errno**设置为**EINVAL**。

> [!IMPORTANT]
> 这些函数可能容易受到的缓冲区溢出的威胁。 缓冲区溢出可以用于系统攻击，因为它们可能使权限的提升不能确保。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_mbsinc**|\<mbstring.h>|
|**_mbsinc_l**|\<mbstring.h>|
|**_strinc**|\<tchar.h>|
|**_wcsinc**|\<tchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdec、_wcsdec、_mbsdec、_mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strnextc、_wcsnextc、_mbsnextc、_mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
[_strninc、_wcsninc、_mbsninc、_mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
