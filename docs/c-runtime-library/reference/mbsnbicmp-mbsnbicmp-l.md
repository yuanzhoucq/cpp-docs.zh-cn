---
title: _mbsnbicmp、_mbsnbicmp_l
ms.date: 11/04/2016
apiname:
- _mbsnbicmp_l
- _mbsnbicmp
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
apitype: DLLExport
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
ms.openlocfilehash: 059d0781e465f6491f27fd634bbc4479104bc12f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331293"
---
# <a name="mbsnbicmp-mbsnbicmpl"></a>_mbsnbicmp、_mbsnbicmp_l

比较**n**字节的两个多字节字符字符串，并忽略大小写。

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

*string1*， *string2*<br/>
要比较的 null 终止的字符串。

*count*<br/>
要比较的字节数。

## <a name="return-value"></a>返回值

返回值指示子字符串之间的关系。

|返回值|描述|
|------------------|-----------------|
|< 0|*string1*的子字符串小于*string2*子字符串。|
|0|*string1*子字符串等于*string2*子字符串。|
|> 0|*string1*子字符串大于*string2*子字符串。|

发生错误时， **_mbsnbicmp**返回 **_NLSCMPERROR**，String.h 和 Mbstring.h 中定义。

## <a name="remarks"></a>备注

**_Mbsnbicmp**函数执行的最多前的序号比较*计数*字节*string1*并*string2*。 通过将转换为小写; 每个字符进行比较[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)是区分大小写的版本 **_mbsnbicmp**。 如果在任一字符串中到达终止 null 字符，则比较停止*计数*字符进行比较。 如果字符串是否相等时终止 null 字符已到达字符串之前*计数*字符进行比较，较短的字符串是较小者。

**_mbsnbicmp**类似于[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)，只不过它将进行比较的字符串最多*计数*而不是由字符的字节数。

两个包含位于 ASCII 表中“Z”和“a”之间的字符（“[”、“\\”、“]”、“^”、“_”和“\`”）的字符串将有不同的比较结果，具体取决于它们的大小写形式。 例如，两个字符串"ABCDE"和"ABCD ^"进行比较的一种方法，如果比较采用小写形式 ("abcde">"abcd ^") 和另一种方法 ("ABCDE"<"ABCD ^") 如果采用大写形式。

**_mbsnbicmp**识别多字节字符序列根据[多字节代码页](../../c-runtime-library/code-pages.md)当前正在使用。 它不受当前区域设置影响。

如果任一*string1*或*string2*是 null 指针 **_mbsnbicmp**调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md). 如果允许执行继续，该函数返回 **_NLSCMPERROR** ，并设置**errno**到**EINVAL**。

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
