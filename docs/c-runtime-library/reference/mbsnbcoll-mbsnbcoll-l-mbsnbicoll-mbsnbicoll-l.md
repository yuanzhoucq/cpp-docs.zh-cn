---
title: _mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l
ms.date: 4/2/2020
api_name:
- _mbsnbicoll_l
- _mbsnbcoll_l
- _mbsnbcoll
- _mbsnbicoll
- _o__mbsnbcoll
- _o__mbsnbcoll_l
- _o__mbsnbicoll
- _o__mbsnbicoll_l
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
- _mbsnbcoll
- _mbsnbcoll_l
- _mbsnbicoll
- mbsnbcoll_l
helpviewer_keywords:
- _mbsnbcoll_l function
- mbsnbcoll_l function
- _mbsnbcoll function
- _tcsnicoll function
- mbsnbcoll function
- mbsnbicoll_l function
- mbsnbicoll function
- _tcsncoll function
- _mbsnbicoll function
- _mbsnbicoll_l function
- _tcsncoll_l function
- _tcsnicoll_l function
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
ms.openlocfilehash: 0b02a34f9b721e4cfcf07ac3679d0dce166a4ff7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340747"
---
# <a name="_mbsnbcoll-_mbsnbcoll_l-_mbsnbicoll-_mbsnbicoll_l"></a>_mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l

使用多字节代码页信息比较两个多字节字符串的*n*字节。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _mbsnbcoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbcoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
int _mbsnbicoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*字符串1*，*字符串2*<br/>
要比较的字符串。

*count*<br/>
要比较的字节数。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回值指示*string1*和*string2*的子字符串的关系。

|返回值|说明|
|------------------|-----------------|
|< 0|*字符串 1*子字符串小于*string2*子字符串。|
|0|*字符串1*子字符串与*string2*子字符串相同。|
|> 0|*字符串1*子字符串大于*string2*子字符串。|

如果*string1*或*string2*为**NULL**或*计数*大于**INT_MAX，** 则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，这些函数将**返回_NLSCMPERROR**并将**errno**设置为**EINVAL**。 要使用 **_NLSCMPERROR**，请包括 String.h 或 Mbstring.h。

## <a name="remarks"></a>备注

每个函数最多整理*string1*和*string2*中的第一个*计数*字节，并返回一个值，指示*生成*子字符串 1 和*string2*之间的关系。 如果*string1*或*string2*子字符串中的最后字节是引线字节，则比较中不包括它;这些函数仅比较子字符串中的完整字符。 **_mbsnbicoll**是 **_mbsnbcoll**的区分大小写版本。 与[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)和[_mbsnbicmp](mbsnbicmp-mbsnbicmp-l.md)一样 **，_mbsnbcoll****和_mbsnbicoll**根据当前使用的多字节[代码页](../../c-runtime-library/code-pages.md)指定的字典顺序对两个多字节字符串进行整理。

对于一些代码页和对应的字符集，字符集中的字符顺序可能与字典的字符顺序不同。 在“C”区域设置中并非如此：ASCII 字符集中的字符顺序与字典的字符顺序相同。 但是，在某些欧洲代码页中，例如，字符“a”（值 0x61）位于字符“ä”（值 0xE4）之前，但在字典顺序中，字符“ä”位于字符“a”之前。 要在这种情况下按字节对字符串进行字典比较，请使用 **_mbsnbcoll**而不是 **_mbsnbcmp;** 要仅检查字符串相等性，请使用 **_mbsnbcmp**。

由于**coll**函数按字典方式对字符串进行校用比较，而**cmp**函数只是测试字符串相等性，因此**coll**函数比相应的**cmp**版本慢得多。 因此，仅当当前代码页中的字符设置顺序和词典字符顺序存在差异且此差异值得比较时，才应使用**coll**函数。

输出值受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)****。 这些不带 **_l** 后缀的函数版本使用此区域设置相关的行为的当前区域设置；带有 **_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncoll**|[_strncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll**|[_wcsncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsncoll_l**|[_strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll_l**|[_wcsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsnicoll**|[_strnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll**|[_wcsnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|
|**_tcsnicoll_l**|[_strnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll_l**|[_wcsnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_mbsnbcoll**|\<mbstring.h>|
|**_mbsnbcoll_l**|\<mbstring.h>|
|**_mbsnbicoll**|\<mbstring.h>|
|**_mbsnbicoll_l**|\<mbstring.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp、_mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
