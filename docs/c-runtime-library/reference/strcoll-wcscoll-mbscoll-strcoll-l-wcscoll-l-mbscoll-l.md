---
title: strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wcscoll
- _mbscoll
- _mbscoll_l
- strcoll
- _strcoll_l
- _wcscoll_l
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcscoll
- _mbscoll
- _tcscoll
- _ftcscoll
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7ea6a480ad5600a69cae31033c4abc28ed78e5e
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451919"
---
# <a name="strcoll-wcscoll-mbscoll-strcolll-wcscolll-mbscolll"></a>strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l

使用当前区域设置或指定的 LC_COLLATE 转换状态类别比较字符串。

> [!IMPORTANT]
> **_mbscoll**和 **_mbscoll_l**不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

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

*string1*， *string2*<br/>
要比较的 null 终止的字符串。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

其中每个函数返回一个值，该值的关系*string1*到*string2*、，如下所示。

|返回值|string1 与 string2 的关系|
|------------------|----------------------------------------|
|< 0|*string1*小于*string2*|
|0|*string1*等于*string2*|
|> 0|*string1*大于*string2*|

其中每个函数返回 **_NLSCMPERROR**发生错误时。 若要使用 **_NLSCMPERROR**，包括其中某一字符串。H 或 MBSTRING。H。 **wcscoll**如果任一可能会失败*string1*或*string2*是**NULL**或包含排序序列域外部的宽字符代码。 发生错误时， **wcscoll**可能设置**errno**到**EINVAL**。 若要在调用中的错误检查**wcscoll**，将其设置**errno**为 0，然后检查**errno**之后调用**wcscoll**。

## <a name="remarks"></a>备注

其中每个函数执行区分大小写的比较*string1*和*string2*根据当前正在使用的代码页。 仅在当前代码页中的字符集顺序与字典字符顺序之间存在差异，并且此差异对于字符串比较有关系时，才应使用这些函数。

所有这些函数都验证其参数。 如果任一*string1*或*string2*是 null 指针，或如果*计数*大于**INT_MAX**，则调用无效参数处理程序中, 所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将返回 **_NLSCMPERROR**并设置**errno**到**EINVAL**。

两个字符串的比较是一个与区域设置相关的操作，因为每个区域设置对排序字符有不同的规则。 版本的这些功能，而不必 **_l**后缀使用区域设置相关的行为的当前线程的区域设置; 的版本与 **_l**后缀是相同与对应的函数而不使用后缀，只不过它们使用作为而不是当前区域设置参数中传递的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

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

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[区域设置](../../c-runtime-library/locale.md)<br/>
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
