---
title: strcat_s、wcscat_s、_mbscat_s、_mbscat_s_l
ms.date: 4/2/2020
api_name:
- strcat_s
- _mbscat_s
- _mbscat_s_l
- wcscat_s
- _o__mbscat_s
- _o__mbscat_s_l
- _o_strcat_s
- _o_wcscat_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strcat_s
- wcscat_s
- _mbscat_s
- _mbscat_s_l
helpviewer_keywords:
- wcscat_s function
- strcat_s function
- mbscat_s function
- strings [C++], appending
- _mbscat_s function
- _mbscat_s_l function
- appending strings
ms.assetid: 0f2f9901-c5c5-480b-98bc-f8f690792fc0
ms.openlocfilehash: f7d890a753638112c4a1bb56cf6093a9510dbee2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910665"
---
# <a name="strcat_s-wcscat_s-_mbscat_s-_mbscat_s_l"></a>strcat_s、wcscat_s、_mbscat_s、_mbscat_s_l

追加字符串。 如 [CRT 中的安全性增强功能](../../c-runtime-library/security-features-in-the-crt.md)所述，这些版本的 [strcat、wcscat、_mbscat](strcat-wcscat-mbscat.md) 具有安全性增强功能。

> [!IMPORTANT]
> 不能在 Windows 运行时中执行的应用程序中使用 **_mbscat_s**和 **_mbscat_s_l** 。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
errno_t strcat_s(
   char *strDestination,
   size_t numberOfElements,
   const char *strSource
);
errno_t wcscat_s(
   wchar_t *strDestination,
   size_t numberOfElements,
   const wchar_t *strSource
);
errno_t _mbscat_s(
   unsigned char *strDestination,
   size_t numberOfElements,
   const unsigned char *strSource
);
errno_t _mbscat_s_l(
   unsigned char *strDestination,
   size_t numberOfElements,
   const unsigned char *strSource,
   _locale_t locale
);
template <size_t size>
errno_t strcat_s(
   char (&strDestination)[size],
   const char *strSource
); // C++ only
template <size_t size>
errno_t wcscat_s(
   wchar_t (&strDestination)[size],
   const wchar_t *strSource
); // C++ only
template <size_t size>
errno_t _mbscat_s(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource
); // C++ only
template <size_t size>
errno_t _mbscat_s_l(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>参数

*strDestination*<br/>
Null 终止的目标字符串缓冲区。

*numberOfElements*<br/>
目标字符串缓冲区的大小。

*strSource*<br/>
以 null 结尾的源字符串缓冲区。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果成功，则为零；如果失败，则为错误代码。

### <a name="error-conditions"></a>错误条件

|*strDestination*|*numberOfElements*|*strSource*|返回值|*StrDestination*的内容|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**NULL**或未终止|any|any|**EINVAL**|未修改|
|any|any|**Null**|**EINVAL**|*strDestination*[0] 设置为0|
|any|0 或过小|any|**ERANGE**|*strDestination*[0] 设置为0|

## <a name="remarks"></a>备注

**Strcat_s**函数将*StrSource*追加到*strDestination* ，并使用空字符终止结果字符串。 *StrSource*的初始字符将覆盖*strDestination*的终止 null 字符。 如果源和目标字符串重叠，则**strcat_s**的行为不确定。

注意，第二个参数是缓冲区的总大小，而不是剩余大小：

```C
char buf[16];
strcpy_s(buf, 16, "Start");
strcat_s(buf, 16, " End");               // Correct
strcat_s(buf, 16 - strlen(buf), " End"); // Incorrect
```

**wcscat_s**和 **_mbscat_s**是**strcat_s**的宽字符和多字节字符版本。 **Wcscat_s**的参数和返回值都是宽字符字符串;**_mbscat_s**的是多字节字符字符串。 否则这三个函数否则具有相同行为。

如果*strDestination*是 null 指针，或不是以 null 结尾的，或者如果*strSource*为**null**指针，或者如果目标字符串过小，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回**EINVAL** ，并将**Errno**设置为**EINVAL**。

具有 **_l**后缀的函数的版本具有相同的行为，但使用传入的区域设置参数而不是当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

这些函数的调试库版本首先用0xFE 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscat_s**|**strcat_s**|**_mbscat_s**|**wcscat_s**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**strcat_s**|\<string.h>|
|**wcscat_s**|\<string.h> 或 \<wchar.h>|
|**_mbscat_s**|\<mbstring.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [strcpy_s、wcscpy_s、_mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md) 中的代码示例。

## <a name="see-also"></a>另请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
