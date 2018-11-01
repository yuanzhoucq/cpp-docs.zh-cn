---
title: strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l
ms.date: 11/04/2016
apiname:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 4e4f5bb6639cbeee0f004f94f09177c08394d43e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590978"
---
# <a name="strxfrm-wcsxfrm-strxfrml-wcsxfrml"></a>strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l

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
源字符串。

*count*<br/>
最大数目的字符将放入*strDest*。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回转换的字符串的长度（不算结尾的 null 字符）。 如果返回值是大于或等于*计数*，则内容*strDest*是不可预知的。 发生错误时，每个函数可设置**errno** ，并返回**INT_MAX**。 无效的字符，对于**errno**设置为**EILSEQ**。

## <a name="remarks"></a>备注

**Strxfrm**指向的字符串函数转换*strSource*中新的排序中存储的窗体*strDest*。 不能超过*计数*字符，包括 null 字符，已转换并放入生成的字符串。 使用的区域设置进行转换**LC_COLLATE**类别设置。 有关详细信息**LC_COLLATE**，请参阅[setlocale](setlocale-wsetlocale.md)。 **strxfrm**其区域设置相关的行为; 使用当前区域设置 **_strxfrm_l**是完全相同，只不过它使用传入中而不是当前区域设置的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

转换到的调用完成之后**strcmp**与两个已转换的字符串将产生与调用相同的结果**strcoll**应用到原始的两个字符串。 如同**strcoll**并**stricoll**， **strxfrm**自动处理的是根据多字节字符字符串。

**wcsxfrm**是宽字符版本**strxfrm**; 的字符串参数**wcsxfrm**都是宽字符指针。 有关**wcsxfrm**后，将字符串转换，先调用**wcscmp**与两个已转换的字符串将产生与调用相同的结果**wcscoll**应用于原始的两个字符串。 **wcsxfrm**并**strxfrm**行为相同。 **wcsxfrm**其区域设置相关的行为; 使用当前区域设置 **_wcsxfrm_l**使用而不是当前区域设置中传入的区域设置。

这些函数验证其参数。 如果*strSource*是空指针，或*strDest*是**NULL**指针 （除非计数为零），或者如果*计数*大于**INT_MAX**，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许继续执行，这些函数将设置**errno**到**EINVAL**并返回**INT_MAX**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

在“C”区域设置中，字符集（ASCII 字符集）中的字符顺序与字典中的字符顺序相同。 但是在其他区域设置中，字符集中的字符顺序可能与字典中的字符顺序不同。 例如，在某些欧洲区域设置中，字符集中的字符“a”（值 0x61）位于字符“&\#x00E4;”（值 0xE4）之前，但在字典顺序中字符“ä”位于字符“a”之前。

在为其的字符集和字典字符顺序不同的区域设置中，使用**strxfrm**对原始字符串，然后**strcmp**对结果字符串以生成按字典顺序的字符串根据当前区域设置的比较**LC_COLLATE**类别设置。 因此，若要比较两个以上的区域设置中按字典顺序的字符串，请使用**strxfrm**对原始字符串，然后**strcmp**对结果字符串。 或者，可以使用**strcoll**而非**strcmp**对原始字符串。

**strxfrm**基本上是一个包装[LCMapString](/windows/desktop/api/winnls/nf-winnls-lcmapstringa)与**LCMAP_SORTKEY**。

下面的表达式的值是包含所需的数组的大小**strxfrm**转换源字符串：

`1 + strxfrm( NULL, string, 0 )`

在"C"区域设置仅**strxfrm**等效于以下：

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strxfrm**|\<string.h>|
|**wcsxfrm**|\<string.h> 或 \<wchar.h>|
|**_strxfrm_l**|\<string.h>|
|**_wcsxfrm_l**|\<string.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
