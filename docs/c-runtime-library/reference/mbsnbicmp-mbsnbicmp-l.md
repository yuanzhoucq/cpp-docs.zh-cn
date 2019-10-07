---
title: _mbsnbicmp、_mbsnbicmp_l
ms.date: 11/04/2016
api_name:
- _mbsnbicmp_l
- _mbsnbicmp
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
- _strnicmp
- _wcsnicmp_l
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _tcsnicmp
- _strnicmp_l
- _tcsnicmp_l
- _wcsnicmp
- _mbsnbicmp_l
helpviewer_keywords:
- _tcsnicmp_l function
- _strnicmp function
- mbsnbicmp_l function
- _wcsnicmp_l function
- _mbsnbicmp function
- _mbsnbicmp_l function
- _tcsnicmp function
- _strnicmp_l function
- mbsnbicmp function
- _wcsnicmp function
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
ms.openlocfilehash: 19ffa4c47f0144ba136607fe5cef09e9bd65374f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952191"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp、_mbsnbicmp_l

比较两个多字节字符字符串的**n**个字节，忽略大小写。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _mbsnbicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>参数

*string1*、 *string2*<br/>
要比较的 null 终止的字符串。

*count*<br/>
要比较的字节数。

## <a name="return-value"></a>返回值

返回值指示子字符串之间的关系。

|返回值|描述|
|------------------|-----------------|
|< 0|*string1*子串小于*string2*子串。|
|0|*string1*子字符串与*string2*子字符串相同。|
|> 0|大于*string2*子字符串的*string1*子串。|

出现错误时， **_mbsnbicmp**返回 **_NLSCMPERROR**，它是在字符串 .h 和 mbstring.h 中定义的。

## <a name="remarks"></a>备注

**_Mbsnbicmp**函数最多可执行*string1*和*string2*的第一个*计数*字节的序号比较。 通过将每个字符转换为小写来执行比较;[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)是 **_mbsnbicmp**的区分大小写的版本。 如果在比较*计数*字符之前的任一字符串中达到终止 null 字符，则比较结束。 如果在比较*计数*字符之前的任一字符串中达到终止 null 字符时字符串相等，则较短的字符串较小。

**_mbsnbicmp**类似于[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)，只不过它将字符串向上比较，而不是按字符进行*计数*。

两个包含位于 ASCII 表中“Z”和“a”之间的字符（“[”、“\\”、“]”、“^”、“_”和“\`”）的字符串将有不同的比较结果，具体取决于它们的大小写形式。 例如，如果比较采用小写形式（"abcde...z" > "abcd ^"），则两个字符串 "ABCDE...Z" 和 "ABCD ^" 比较一种方式（"ABCDE...Z" < "ABCD ^"）（如果它为大写）。

**_mbsnbicmp**根据当前使用的[多字节代码页](../../c-runtime-library/code-pages.md)识别多字节字符序列。 它不受当前区域设置影响。

如果*string1*或*string2*是 null 指针， **_mbsnbicmp**将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将返回 **_NLSCMPERROR** ，并将**Errno**设置为**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md) 的示例。

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
