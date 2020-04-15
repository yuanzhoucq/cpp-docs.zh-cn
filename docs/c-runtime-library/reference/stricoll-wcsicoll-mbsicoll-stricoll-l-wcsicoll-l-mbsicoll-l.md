---
title: _stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l
ms.date: 4/2/2020
api_name:
- _mbsicoll_l
- _stricoll_l
- _mbsicoll
- _wcsicoll_l
- _wcsicoll
- _stricoll
- _o__mbsicoll
- _o__mbsicoll_l
- _o__stricoll
- _o__stricoll_l
- _o__wcsicoll
- _o__wcsicoll_l
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- stricoll
- _stricoll
- _wcsicoll
- mbsicoll_l
- _mbsicoll
- _ftcsicoll
- wcsicoll_l
- _tcsicoll
- mbsicoll
- stricoll_l
helpviewer_keywords:
- code pages, using for string comparisons
- _ftcsicoll function
- _mbsicoll_l function
- _mbsicoll function
- mbsicoll function
- stricoll function
- tcsicoll function
- string comparison [C++], culture-specific
- _tcsicoll function
- _stricoll function
- _stricoll_l function
- _wcsicoll function
- mbsicoll_l function
- stricoll_l function
- strings [C++], comparing by code page
- ftcsicoll function
ms.assetid: 8ec93016-5a49-49d2-930f-721566661d82
ms.openlocfilehash: d726d2d33f8f775d09e6197dfeda6abb91106a53
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355329"
---
# <a name="_stricoll-_wcsicoll-_mbsicoll-_stricoll_l-_wcsicoll_l-_mbsicoll_l"></a>_stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l

使用特定于区域设置的信息比较字符串。

> [!IMPORTANT]
> **_mbsicoll**和 **_mbsicoll_l**不能在 Windows 运行时中执行的应用程序中使用。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _stricoll(
   const char *string1,
   const char *string2
);
int _wcsicoll(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbsicoll(
   const unsigned char *string1,
   const unsigned char *string2
);
int _stricoll_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int _wcsicoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbsicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*字符串1*，*字符串2*<br/>
要比较的 null 终止的字符串。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

每个函数返回一个值，指示*string1*到*string2*的关系，如下所示。

|返回值|string1 与 string2 的关系|
|------------------|----------------------------------------|
|< 0|*字符串1*小于*字符串2*|
|0|*字符串1*与*字符串2*相同|
|> 0|*字符串1*大于*字符串2*|
|**_NLSCMPERROR**|出现了错误。|

这些函数中的每一个都**返回_NLSCMPERROR**。 要使用 **_NLSCMPERROR**，请\<包括 string.h \<> 或 mbstring.h>。 如果*string1*或*string2*在整理序列的域之外包含宽字符代码，**则_wcsicoll**可能会失败。 发生错误时 **，_wcsicoll**可能会将**errno**设置为**EINVAL**。 要检查调用 **_wcsicoll**时的错误，请将**errno**设置为 0，然后在调用 **_wcsicoll**后检查**errno。**

## <a name="remarks"></a>备注

根据当前使用的代码页，每个函数都执行对*string1*和*string2*不区分大小写的比较。 仅在当前代码页中的字符集顺序与字典字符顺序之间存在差异，并且此差异对于字符串比较有关系时，才应使用这些函数。

**_stricmp_stricoll**不同 **_stricoll****，_stricmp**比较受**LC_CTYPE**影响，而 **_stricoll**比较则根据区域设置**LC_CTYPE**和**LC_COLLATE**类别。 有关**LC_COLLATE**类别的详细信息，请参阅[设置区域设置](setlocale-wsetlocale.md)[和区域设置类别](../../c-runtime-library/locale-categories.md)。 没有 **_l**后缀的这些函数的版本使用当前区域设置;具有 **_l**后缀的版本是相同的，只是它们使用传入区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

所有这些函数都验证其参数。 如果*string1*或*string2*是**NULL**指针，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，这些函数将**返回_NLSCMPERROR**并将**errno**设置为**EINVAL**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicoll**|**_stricoll**|**_mbsicoll**|**_wcsicoll**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_stricoll**， **_stricoll_l**|\<string.h>|
|**_wcsicoll**， **_wcsicoll_l**|\<wchar.h>、\<string.h>|
|**_mbsicoll**， **_mbsicoll_l**|\<mbstring.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[现场](../../c-runtime-library/locale.md)<br/>
[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
