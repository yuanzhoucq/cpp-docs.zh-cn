---
title: ispunct、iswpunct、_ispunct_l、_iswpunct_l
ms.date: 11/04/2016
apiname:
- ispunct
- _iswpunct_l
- iswpunct
- _ispunct_l
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
apitype: DLLExport
f1_keywords:
- iswpunct
- _istpunct
- ispunct
helpviewer_keywords:
- _istpunct function
- _ispunct_l function
- iswpunct function
- ispunct function
- istpunct function
- ispunct_l function
- _iswpunct_l function
- iswpunct_l function
ms.assetid: 94403240-85c8-40a4-9c2b-e3e95c729c76
ms.openlocfilehash: 209f94bb8f9d3338f62b719d4d4b94b152ed5ab7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62286530"
---
# <a name="ispunct-iswpunct-ispunctl-iswpunctl"></a>ispunct、iswpunct、_ispunct_l、_iswpunct_l

确定整数是否表示标点字符。

## <a name="syntax"></a>语法

```C
int ispunct(
   int c
);
int iswpunct(
   wint_t c
);
int _ispunct_l(
   int c,
   _locale_t locale
);
int _iswpunct_l(
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

这些例程返回非零值如果*c*是标点字符的特定表示形式。 **ispunct**返回非零值不是空格字符或字符的任何可打印字符**isalnum**为非零值。 **iswpunct**返回非零值不是空格宽字符或宽字符的任何可打印宽字符**iswalnum**为非零值。 每个例程将返回 0，如果*c*不满足测试条件。

测试条件的结果**ispunct**函数取决于**LC_CTYPE**区域设置类别设置影响; 请参阅[setlocale、 _wsetlocale](setlocale-wsetlocale.md)有关详细信息。 不具有这些函数的版本 **_l**后缀，请使用当前区域设置的任何依赖于区域设置的行为; 具有的版本 **_l**后缀完全相同，只不过它们使用改用已传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

行为**ispunct**并 **_ispunct_l**未定义当*c*不是 EOF 或在范围 0 到 0xff 内，非独占。 使用调试 CRT 库时， *c*是不包含其中一个值，函数将引发断言。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istpunct**|**ispunct**|[_ismbcpunct](ismbcgraph-functions.md)|**iswpunct**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**ispunct**|\<ctype.h>|
|**iswpunct**|\<ctype.h 1> 或 \<wchar.h 1>|
|**_ispunct_l**|\<ctype.h>|
|**_iswpunct_l**|\<ctype.h 1> 或 \<wchar.h 1>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
