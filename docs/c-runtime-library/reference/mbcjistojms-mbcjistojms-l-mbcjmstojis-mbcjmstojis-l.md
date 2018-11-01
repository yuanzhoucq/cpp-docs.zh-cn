---
title: _mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l
ms.date: 11/04/2016
apiname:
- _mbcjistojms
- _mbcjmstojis
- _mbcjistojms_l
- _mbcjmstojis_l
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
- mbcjistojms
- _mbcjistojms
- _mbcjistojms_l
- _mbcjmstojis_l
- _mbcjmstojis
- mbcjmstojis_l
- mbcjistojms_l
- mbcjmstojis
helpviewer_keywords:
- _mbcjmstojis_l function
- _mbcjistojms function
- mbcjmstojis function
- _mbcjistojms_l function
- _mbcjmstojis function
- mbcjistojms function
- mbcjmstojis_l function
- mbcjistojms_l function
ms.assetid: dece5127-b337-40a4-aa10-53320a2c9432
ms.openlocfilehash: 22cf8eeb5f99b6abee624aa3b1d06246d7230652
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665889"
---
# <a name="mbcjistojms-mbcjistojmsl-mbcjmstojis-mbcjmstojisl"></a>_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l

在日本行业标准 (JIS) 和日本 Microsoft (JMS) 字符之间转换。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
unsigned int _mbcjistojms(
   unsigned int c
);
unsigned int _mbcjistojms_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbcjmstojis(
   unsigned int c
);
unsigned int _mbcjmstojis_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*c*<br/>
要转换的字符。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

在日文区域设置中，这些函数将返回经转换的字符或者在转换不可用时返回 0。 在非日文区域设置中，这些函数将返回传入的字符。

## <a name="remarks"></a>备注

**_Mbcjistojms**函数将日本行业标准 (JIS) 字符转换为 Microsoft 日文汉字 (转义 JIS) 字符。 仅当前导和结尾字节处于 0x21-0x7E 范围，转换的字符。 如果超出此范围是前导字节或结尾字节**errno**设置为**EILSEQ**。 有关此代码及其他错误代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**_Mbcjmstojis**函数将 Shift JIS 字符转换为 JIS 字符。 仅当处于范围内 0x81-0x9F 或 0xE0-0xFC 前导字节和结尾字节处于 0x40-0x7E 或 0x80-0xFC 被转换的字符。 请注意该范围内的一些码位未分配字符，因此无法进行转换。

该值*c*其较高的 8 位表示要转换的字符的前导字节，其低 8 位表示结尾字节，应为 16 位值。

输出值受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)。 这些不带 **_l** 后缀的函数版本使用此区域设置相关的行为的当前区域设置；带有 **_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在早期版本中， **_mbcjistojms**并 **_mbcjmstojis**调用**jistojms**并**jmstojis**分别。 **_mbcjistojms**， **_mbcjistojms_l**， **_mbcjmstojis**并 **_mbcjmstojis_l**应改为使用。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_mbcjistojms**|\<mbstring.h>|
|**_mbcjistojms_l**|\<mbstring.h>|
|**_mbcjmstojis**|\<mbstring.h>|
|**_mbcjmstojis_l**|\<mbstring.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)<br/>
