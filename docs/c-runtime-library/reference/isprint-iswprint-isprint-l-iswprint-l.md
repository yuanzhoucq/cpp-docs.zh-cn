---
title: isprint、iswprint、_isprint_l、_iswprint_l
ms.date: 11/04/2016
apiname:
- iswprint
- isprint
- _isprint_l
- _iswprint_l
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- iswprint
- _istprint
- isprint
helpviewer_keywords:
- _istprint function
- iswprint function
- _iswprint_l function
- isprint_l function
- istprint function
- isprint function
- iswprint_l function
- _isprint_l function
ms.assetid: a8bbcdb0-e8d0-4d8c-ae4e-56d3bdee6ca3
ms.openlocfilehash: aab604076f8a2e2eee0eefe20f08f46ae5388a34
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210115"
---
# <a name="isprint-iswprint-isprintl-iswprintl"></a>isprint、iswprint、_isprint_l、_iswprint_l

确定整数是否表示可打印字符。

## <a name="syntax"></a>语法

```C
int isprint(
   int c
);
int iswprint(
   wint_t c
);
int _isprint_l(
   int c,
   _locale_t locale
);
int _iswprint_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*c*<br/>
要测试的整数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

这些例程返回非零值如果*c*是可打印字符的特定表示形式。 **isprint**返回非零值，如果*c*是可打印字符，其中包括空格字符 (0x20-0x7E)。 **iswprint**返回非零值，如果*c*是可打印宽字符，这包括空格宽字符。 每个例程将返回 0，如果*c*不满足测试条件。

这些函数的测试条件的结果取决于**LC_CTYPE**的区域设置的类别设置影响; 请参阅[setlocale、 _wsetlocale](setlocale-wsetlocale.md)有关详细信息。 不具有这些函数的版本 **_l**后缀，请使用当前区域设置的任何依赖于区域设置的行为; 具有的版本 **_l**后缀完全相同，只不过它们使用改用已传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

行为**isprint**并 **_isprint_l**未定义当*c*不是 EOF 或在范围 0 到 0xff 内，非独占。 使用调试 CRT 库时， *c*是不包含其中一个值，函数将引发断言。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _unicode|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istprint**|**isprint**|[_ismbcprint](ismbcgraph-functions.md)|**iswprint**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**isprint**|\<ctype.h>|
|**iswprint**|\<ctype.h 1> 或 \<wchar.h 1>|
|**_isprint_l**|\<ctype.h>|
|**_iswprint_l**|\<ctype.h 1> 或 \<wchar.h 1>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
