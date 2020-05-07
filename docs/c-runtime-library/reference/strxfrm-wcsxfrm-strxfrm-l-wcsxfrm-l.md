---
title: strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l
ms.date: 4/2/2020
api_name:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
- _o__strxfrm_l
- _o__wcsxfrm_l
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strxfrm
- _tcsxfrm
- wcsxfrm
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
ms.openlocfilehash: 3ab3f978d4162f968f518272612c18767247f2fb
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912351"
---
# <a name="strxfrm-wcsxfrm-_strxfrm_l-_wcsxfrm_l"></a>strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l

根据区域设置特定信息转换字符串。

## <a name="syntax"></a>语法

```C
size_t strxfrm(
   char *strDest,
   const char *strSource,
   size_t count
);
size_t wcsxfrm(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
size_t _strxfrm_l(
   char *strDest,
   const char *strSource,
   size_t count,
   _locale_t locale
);
size_t wcsxfrm_l(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*strDest*<br/>
目标字符串。

*strSource*<br/>
资源字符串。

*计数*<br/>
要放置在*strDest*中的最大字符数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回转换的字符串的长度（不算结尾的 null 字符）。 如果返回值大于或等于*count*，则*strDest*的内容不可预测。 出现错误时，每个函数将设置**errno**并返回**INT_MAX**。 对于无效字符， **errno**设置为**eilseq 且**。

## <a name="remarks"></a>备注

**Strxfrm**函数将*strSource*指向的字符串转换为存储在*strDest*中的新的逐份打印形式。 不超过*count*个字符（包括空字符）会被转换并放入生成的字符串中。 使用区域设置的**LC_COLLATE**类别设置进行转换。 有关**LC_COLLATE**的详细信息，请参阅[setlocale](setlocale-wsetlocale.md)。 **strxfrm**对其与区域设置相关的行为使用当前区域设置;**_strxfrm_l**相同，只不过它使用传入的区域设置而不是当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

转换后，使用两个已转换的字符串调用**strcmp**将生成与对**strcoll**应用于原始两个字符串的调用结果相同的结果。 与**strcoll**和**stricoll**一样， **strxfrm**会根据需要自动处理多字节字符字符串。

**wcsxfrm**是**strxfrm**的宽字符版本;**wcsxfrm**的字符串参数是宽字符指针。 对于**wcsxfrm**，在字符串转换之后，使用两个已转换的字符串对**wcscmp**的调用将产生与对原始两个字符串的**wcscoll**调用的结果相同的结果。 否则， **wcsxfrm**和**strxfrm**的行为相同。 **wcsxfrm**对其与区域设置相关的行为使用当前区域设置;**_wcsxfrm_l**使用传入的区域设置，而不是当前区域设置。

这些函数验证其参数。 如果*strSource*为 null 指针，或*strDest*为**null**指针（除非计数为零），或者*计数*大于**INT_MAX**，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数会将**errno**设置为**EINVAL**并返回**INT_MAX**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

在“C”区域设置中，字符集（ASCII 字符集）中的字符顺序与字典中的字符顺序相同。 但是在其他区域设置中，字符集中的字符顺序可能与字典中的字符顺序不同。 例如，在某些欧洲区域设置中，字符集中的字符“a”（值 0x61）位于字符“&\#x00E4;”（值 0xE4）之前，但在字典顺序中字符“ä”位于字符“a”之前。

在字符集和字典字符顺序不同的区域设置中，对原始字符串使用**strxfrm** ，然后对生成的字符串**strcmp** ，以根据当前区域设置的**LC_COLLATE**类别设置生成字典字符串比较。 因此，若要比较以上区域设置中按字典顺序的两个字符串，请对原始字符串使用**strxfrm** ，并对生成的字符串使用**strcmp** 。 或者，可以对原始字符串使用**strcoll**而不是**strcmp** 。

**strxfrm**基本上是围绕[LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw) **LCMAP_SORTKEY**的包装。

以下表达式的值是保存源字符串的**strxfrm**转换所需的数组大小：

`1 + strxfrm( NULL, string, 0 )`

仅在 "C" 区域设置中， **strxfrm**等效于以下内容：

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**strxfrm**|\<string.h>|
|**wcsxfrm**|\<string.h> 或 \<wchar.h>|
|**_strxfrm_l**|\<string.h>|
|**_wcsxfrm_l**|\<string.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[本地](../../c-runtime-library/locale.md)<br/>
[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
