---
title: _mbsnbicmp、_mbsnbicmp_l
ms.date: 4/2/2020
api_name:
- _mbsnbicmp_l
- _mbsnbicmp
- _o__mbsnbicmp
- _o__mbsnbicmp_l
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
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
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
ms.openlocfilehash: 80d2708396cdaeb86c25932c3d13129fb318719a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340576"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp、_mbsnbicmp_l

比较两个多字节字符串的**n**字节，并忽略大小写。

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

*字符串1*，*字符串2*<br/>
要比较的 null 终止的字符串。

*count*<br/>
要比较的字节数。

## <a name="return-value"></a>返回值

返回值指示子字符串之间的关系。

|返回值|说明|
|------------------|-----------------|
|< 0|*字符串 1*子字符串小于*string2*子字符串。|
|0|*字符串1*子字符串与*string2*子字符串相同。|
|> 0|*字符串1*子字符串大于*string2*子字符串。|

在错误时 **，_mbsnbicmp**返回 **_NLSCMPERROR**，在 String.h 和 Mbstring.h 中定义。

## <a name="remarks"></a>备注

**_mbsnbicmp**函数最多执行*string1*和*string2*的第一个*计数*字节的位级比较。 通过将每个字符转换为小写来执行比较;[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)是 **_mbsnbicmp**区分大小写的版本。 如果在比较*计数*字符之前在任一字符串中到达终止空字符，则比较结束。 如果在比较*计数*字符之前在任一字符串中到达终止空字符时，字符串相等，则较短的字符串较小。

**_mbsnbicmp**与[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)类似，只是它将字符串向上比较为*计数*字节而不是按字符。

两个包含位于 ASCII 表中“Z”和“a”之间的字符（“[”、“\\”、“]”、“^”、“_”和“\`”）的字符串将有不同的比较结果，具体取决于它们的大小写形式。 例如，如果比较小写（"abcde">"abcd"）和"ABCDE"<"ABCD_"）是大写，则两个字符串"ABCDE"和"ABCD+"比较一种方法。

**_mbsnbicmp**根据当前使用的[多字节代码页](../../c-runtime-library/code-pages.md)识别多字节字符序列。 它不受当前区域设置影响。

如果*string1*或*string2*是空指针 **，_mbsnbicmp**调用参数[验证](../../c-runtime-library/parameter-validation.md)中所述的无效参数处理程序。 如果允许继续执行，则函数将**返回_NLSCMPERROR**并将**errno**设置到**EINVAL**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md) 的示例。

## <a name="see-also"></a>另请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
