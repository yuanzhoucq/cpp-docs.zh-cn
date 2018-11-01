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
ms.openlocfilehash: 1f23f57582d9f65ca728beac2c83804dff9935a4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612896"
---
# <a name="strinc-wcsinc-mbsinc-mbsincl"></a>_strinc、_wcsinc、_mbsinc、_mbsinc_l

比字符串指针提前一个字符。

> [!IMPORTANT]
> **_mbsinc**并 **_mbsinc_l**不能在 Windows 运行时中执行的应用程序中使用。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

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

每个例程将指针返回到紧跟在后面的字符*当前*。

## <a name="remarks"></a>备注

**_Mbsinc**函数返回一个指向紧跟在后面的多字节字符的第一个字节*当前*。 **_mbsinc**识别多字节字符序列根据[多字节代码页](../../c-runtime-library/code-pages.md)当前正在使用;**_mbsinc_l**具有完全相同，只不过它改用传入的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

一般文本函数 **_tcsinc**映射到 Tchar.h 中定义 **_mbsinc**如果 **_MBCS**已经定义，或设置为 **_wcsinc**如果 **_UNICODE**已定义。 否则为 **_tcsinc**映射到 **_strinc**。 **_strinc**并 **_wcsinc**单字节字符和宽字符版本的 **_mbsinc**。 **_strinc**并 **_wcsinc**仅为此映射提供，否则不应使用。 有关详细信息，请参阅[使用一般文本映射](../../c-runtime-library/using-generic-text-mappings.md)和[一般文本映射](../../c-runtime-library/generic-text-mappings.md)。

如果*当前*是**NULL**，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数返回**EINVAL** ，并设置**errno**到**EINVAL**。

> [!IMPORTANT]
> 这些函数可能容易受到的缓冲区溢出的威胁。 缓冲区溢出可以用于系统攻击，因为它们可能使权限的提升不能确保。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/desktop/SecBP/avoiding-buffer-overruns)。

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
