---
title: strrchr、wcsrchr、_mbsrchr、_mbsrchr_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- strrchr
- wcsrchr
- _mbsrchr
- _mbsrchr_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcsrchr
- _ftcsrchr
- strrchr
- wcsrchr
- _mbsrchr
dev_langs:
- C++
helpviewer_keywords:
- _mbsrchr function
- tcsrchr function
- mbsrchr_l function
- characters [C++], scanning for
- ftcsrchr function
- _tcsrchr function
- strings [C++], scanning
- mbsrchr function
- strrchr function
- scanning strings
- wcsrchr function
- _ftcsrchr function
- _mbsrchr_l function
ms.assetid: 75cf2664-758e-49bb-bf6b-8a139cd474d2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03b0ce2c9bd205f9065c783a4ff4d7e50d0ff803
ms.sourcegitcommit: 04d327940787df1297b72d534f388a035d472af0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2018
ms.locfileid: "39181154"
---
# <a name="strrchr-wcsrchr-mbsrchr-mbsrchrl"></a>strrchr、wcsrchr、_mbsrchr、_mbsrchr_l

扫描字符串以查找某个字符的末次出现位置。

> [!IMPORTANT]
> `_mbsrchr` 和 `_mbsrchr_l` 无法用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
char *strrchr(
   const char *str,
   int c
); // C only
char *strrchr(
   char *str,
   int c
); // C++ only
const char *strrchr(
   const char *str,
   int c
); // C++ only
wchar_t *wcsrchr(
   const wchar_t *str,
   wchar_t c
); // C only
wchar_t *wcsrchr(
   wchar_t *str,
   wchar_t c
); // C++ only
const wchar_t *wcsrchr(
   const wchar_t *str,
   wchar_t c
); // C++ only
unsigned char *_mbsrchr(
   const unsigned char *str,
   unsigned int c
); // C only
unsigned char *_mbsrchr(
   unsigned char *str,
   unsigned int c
); // C++ only
const unsigned char *_mbsrchr(
   const unsigned char *str,
   unsigned int c
); // C++ only
unsigned char *_mbsrchr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C only
unsigned char *_mbsrchr_l(
   unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
const unsigned char *_mbsrchr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>参数

*str*<br/>
要搜索的 null 终止的字符串。

*c*<br/>
要查找的字符。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

将指针返回到的最后一个匹配项*c*中*str*，则为 null *c*找不到。

## <a name="remarks"></a>备注

`strrchr`函数查找字符串的最后一个匹配项*c* (转换为**char**) 中*str*。 搜索包括终止 null 字符。

`wcsrchr` 和 `_mbsrchr` 分别是 `strrchr` 的宽字符及多字节字符版本。 `wcsrchr` 的参数和返回值是宽字符字符串；而 `_mbsrchr` 的则是多字节字符字符串。

在 C 中，这些函数采用**const**的第一个参数的指针。 在 C++ 中，有两个重载可用。 采用指向的重载**const**返回一个指向**const**; 将指针传递到非版本**const**返回一个指向非**常量**. 如果这两个定义宏 _CRT_CONST_CORRECT_OVERLOADS **const**和非-**const**提供了这些函数的版本。 如果需要非**const**行为对于这两个 c + + 重载，定义符号 _CONST_RETURN。

`_mbsrchr` 会验证其参数。 如果*str*为 NULL，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则`errno`设置为 EINVAL 和`_mbsrchr`返回 0。 `strrchr` 和 `wcsrchr` 不会验证其参数。 否则这三个函数否则具有相同行为。

输出值受区域设置; 的 LC_CTYPE 类别设置的设置有关详细信息，请参阅[setlocale](setlocale-wsetlocale.md)。 这些不带 **_l** 后缀的函数版本使用此区域设置相关的行为的当前区域设置；带有 **_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsrchr`|`strrchr`|`_mbsrchr`|`wcsrchr`|
|**不适用**|**不适用**|`_mbsrchr_l`|**不适用**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`strrchr`|\<string.h>|
|`wcsrchr`|\<string.h> 或 \<wchar.h>|
|`_mbsrchr`, `_mbsrchr_l`|\<mbstring.h>|

有关兼容性的更多信息，请参见 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

有关使用 `strrchr` 的示例，请参阅 [strchr](strchr-wcschr-mbschr-mbschr-l.md)。

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strchr、wcschr、_mbschr、_mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
