---
title: _mbccpy、_mbccpy_l
ms.date: 11/04/2016
api_name:
- _mbccpy
- _mbccpy_l
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
ms.openlocfilehash: 98ae2eb75949077d02b98ba3aec75da534e93884
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952697"
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

dest<br/>
复制目标。

*src*<br/>
要复制的多字节字符。

*locale*<br/>
要使用的区域设置。

## <a name="remarks"></a>备注

**_Mbccpy**函数将一个多字节字符从*src*复制到*目标*。

此函数验证其参数。 如果向 **_mbccpy**传递了用于*dest*或*src*的空指针，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将**errno**设置为**EINVAL**。

**_mbccpy**为任何与区域设置相关的行为使用当前区域设置。 **_mbccpy_l**与 **_mbccpy**相同，不同之处在于 **_mbccpy_l**使用传入的区域设置用于任何依赖于区域设置的行为。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

**安全说明** 使用以 null 结尾的字符串。 以 null 结尾的字符串不得超过目标缓冲区的大小。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。 缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy**|映射到宏或内联函数|**_mbccpy**|映射到宏或内联函数|
|**_tccpy_l**|n/a|**_mbccpy_l**|n/a|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_mbccpy**|\<mbctype.h>|
|**_mbccpy_l**|\<mbctype.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
