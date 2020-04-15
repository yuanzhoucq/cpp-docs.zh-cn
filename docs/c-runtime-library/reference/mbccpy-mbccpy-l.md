---
title: _mbccpy、_mbccpy_l
ms.date: 4/2/2020
api_name:
- _mbccpy
- _mbccpy_l
- _o__mbccpy
- _o__mbccpy_l
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
- _mbccpy
- tccpy
- ftccpy
- mbccpy
- _tccpy
- _ftccpy
helpviewer_keywords:
- _tccpy function
- _tccpy_l function
- tccpy_l function
- tccpy function
- mbccpy function
- _mbccpy_l function
- _mbccpy function
- mbccpy_l function
ms.assetid: 13f4de6e-7792-41ac-b319-dd9b135433aa
ms.openlocfilehash: 45f93e370e11cf38fc17da3557b21c636fcbc623
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341267"
---
# <a name="_mbccpy-_mbccpy_l"></a>_mbccpy、_mbccpy_l

将多字节字符从一个字符串复制到另一个字符串。 提供这些函数的更多安全版本；请参阅 [_mbccpy_s、_mbccpy_s_l](mbccpy-s-mbccpy-s-l.md)。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
void _mbccpy(
   unsigned char *dest,
   const unsigned char *src
);
void _mbccpy_l(
   unsigned char *dest,
   const unsigned char *src,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

dest**<br/>
复制目标。

*src*<br/>
要复制的多字节字符。

*现场*<br/>
要使用的区域设置。

## <a name="remarks"></a>备注

**_mbccpy**函数将一个多字节字符从*src*复制到*dest*。

此函数验证其参数。 如果 **_mbccpy**传递了*dest*或*src*的空指针，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则**errno**设置为**EINVAL**。

**_mbccpy**对任何与区域设置相关的行为使用当前区域设置。 **_mbccpy_l**与 **_mbccpy**相同，只不过 **_mbccpy_l**使用传入的任何区域设置相关的行为。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

**安全说明** 使用以 null 结尾的字符串。 以 null 结尾的字符串不得超过目标缓冲区的大小。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。 缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy**|映射到宏或内联函数|**_mbccpy**|映射到宏或内联函数|
|**_tccpy_l**|不适用|**_mbccpy_l**|不适用|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_mbccpy**|\<mbctype.h>|
|**_mbccpy_l**|\<mbctype.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[现场](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
