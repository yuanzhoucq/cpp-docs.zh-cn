---
title: isblank、iswblank、_isblank_l、_iswblank_l
ms.date: 11/04/2016
apiname:
- isblank
- _isblank_l
- iswblank
- _iswblank_l
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
- _iswblank_l
- isblank
- _istblank_l
- _istblank
- _isblank_l
- iswblank
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
ms.openlocfilehash: eb088c4056e2277e188d7f98a57dd36216d013ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497313"
---
# <a name="isblank-iswblank-isblankl-iswblankl"></a>isblank、iswblank、_isblank_l、_iswblank_l

确定整数是否表示空格字符。

## <a name="syntax"></a>语法

```C
int isblank(
   int c
);
int iswblank(
   wint_t c
);
int _isblank_l(
   int c,
   _locale_t locale
);
int _iswblank_l(
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

这些例程返回非零值如果*c*是空格或水平制表符的特定表示形式，或者是特定于区域设置的一系列用于文本行中分隔单词字符之一。 **isblank**返回非零值，如果*c*是空格字符 (0x20) 或水平制表符 (0x09)。 测试条件的结果**isblank**取决于函数**LC_CTYPE**类别设置的区域设置; 有关详细信息，请参阅[setlocale、 _wsetlocale](setlocale-wsetlocale.md). 不具有这些函数的版本 **_l**后缀，请使用当前区域设置的任何依赖于区域设置的行为; 具有的版本 **_l**后缀完全相同，只不过它们使用改用已传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

**iswblank**返回非零值，如果*c*是对应于标准空间的宽字符或水平制表符字符。

行为**isblank**并 **_isblank_l**未定义当*c*不是 EOF 或在范围 0 到 0xff 内，非独占。 使用调试 CRT 库时， *c*是不包含其中一个值，函数将引发断言。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istblank**|**isblank**|[_ismbcblank](ismbcgraph-functions.md)|**iswblank**|
|**_istblank_l**|**_isblank_l**|[_ismbcblank_l](ismbcgraph-functions.md)|**_iswblank_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**isblank**|\<ctype.h>|
|**iswblank**|\<ctype.h 1> 或 \<wchar.h 1>|
|**_isblank_l**|\<ctype.h>|
|**_iswblank_l**|\<ctype.h 1> 或 \<wchar.h 1>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
