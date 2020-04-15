---
title: strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l
ms.date: 4/2/2020
api_name:
- wcscoll
- _mbscoll
- _mbscoll_l
- strcoll
- _strcoll_l
- _wcscoll_l
- _o__mbscoll
- _o__mbscoll_l
- _o__strcoll_l
- _o__wcscoll_l
- _o_strcoll
- _o_wcscoll
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
- wcscoll
- _mbscoll
- _tcscoll
- _ftcscoll
helpviewer_keywords:
- code pages, using for string comparisons
- mbscoll function
- wcscoll_l function
- ftcscoll function
- wcscoll function
- _strcoll_l function
- tcscoll function
- _ftcscoll function
- _tcscoll function
- _wcscoll_l function
- _mbscoll function
- strcoll_l function
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: 900a7540-c7ec-4c2f-b292-7a85f63e3fe8
ms.openlocfilehash: 9cbf24fafa78ac6a53a99abf0d1bb1ab3a0625c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358114"
---
# <a name="strcoll-wcscoll-_mbscoll-_strcoll_l-_wcscoll_l-_mbscoll_l"></a>strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l

使用当前区域设置或指定的 LC_COLLATE 转换状态类别比较字符串。

> [!IMPORTANT]
> **_mbscoll****和_mbscoll_l**不能在 Windows 运行时中执行的应用程序中使用。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int strcoll(
   const char *string1,
   const char *string2
);
int wcscoll(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscoll(
   const unsigned char *string1,
   const unsigned char *string2
);
int _strcoll_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int wcscoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbscoll_l(
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

这些函数中的每一个都会在错误时**返回_NLSCMPERROR。** 要使用 **_NLSCMPERROR**，请包括 String。H 或 MBSTRING。H。 如果*string1*或*string2*为**NULL，** 或者在整理序列的域之外包含宽字符代码，**则 wcscoll**可能会失败。 当发生错误时 **，wcscoll**可能会将**errno**设置为**EINVAL**。 要检查呼叫**wcscoll**时的错误，请将**errno**设置为 0，然后在调用**wcscoll**后检查**errno。**

## <a name="remarks"></a>备注

根据当前使用的代码页，每个函数都执行*string1*和*string2*的区分大小写比较。 仅在当前代码页中的字符集顺序与字典字符顺序之间存在差异，并且此差异对于字符串比较有关系时，才应使用这些函数。

所有这些函数都验证其参数。 如果*string1*或*string2*是空指针，或者如果*计数*大于**INT_MAX，** 则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，这些函数将**返回_NLSCMPERROR**并将**errno**设置为**EINVAL**。

两个字符串的比较是一个与区域设置相关的操作，因为每个区域设置对排序字符有不同的规则。 没有 **_l**后缀的这些函数的版本使用此与区域设置相关的行为使用当前线程区域设置;具有 **_l**后缀的版本与没有后缀的相应函数相同，只不过它们使用作为参数传入的区域设置而不是当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscoll**|**strcoll**|**_mbscoll**|**wcscoll**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**strcoll**|\<string.h>|
|**wcscoll**|\<wchar.h>、\<string.h>|
|**_mbscoll**， **_mbscoll_l**|\<mbstring.h>|
|**_strcoll_l**|\<string.h>|
|**_wcscoll_l**|\<wchar.h>、\<string.h>|

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
