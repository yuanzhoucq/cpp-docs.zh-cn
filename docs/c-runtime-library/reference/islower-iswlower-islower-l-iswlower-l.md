---
title: islower、iswlower、_islower_l、_iswlower_l
ms.date: 11/04/2016
apiname:
- iswlower
- _islower_l
- islower
- _iswlower_l
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
- _istlower
- islower
- _ismbclower_l
- _liswlower_l
- _istlower_l
- _iswlower_l
- _islower _l
- _islower_l
- iswlower
helpviewer_keywords:
- _islower _l function
- _ismbclower_l function
- islower function
- _iswlower_l function
- _liswlower_l function
- _istlower_l function
- istlower function
- _istlower function
- iswlower function
- _islower_l function
ms.assetid: fcc3b70a-2b47-45fd-944d-e5c1942e6457
ms.openlocfilehash: 14510d38f5bb4890f98c39b49ca17adc2be3ff41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594124"
---
# <a name="islower-iswlower-islowerl-iswlowerl"></a>islower、iswlower、_islower_l、_iswlower_l

确定整数是否表示小写字符。

## <a name="syntax"></a>语法

```C
int islower(
   int c
);
int iswlower(
   wint_t c
);
int islower_l(
   int c,
   _locale_t locale
);
int _iswlower_l(
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

这些例程返回非零值如果*c*是小写字符的特定表示形式。 **islower**返回非零值，如果*c*是一个小写字符 (a-z)。 **iswlower**返回非零值，如果*c*是宽字符对应于一个小写字母，或者如果*c*是之一实现定义的宽字符，对于该宽**iswcntrl**， **iswdigit**， **iswpunct**，或者**iswspace**为非零值。 每个例程将返回 0，如果*c*不满足测试条件。

具有这些函数的版本 **_l**后缀为其区域设置相关的行为使用传入的区域设置而不是当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

行为**islower**并 **_islower_l**未定义当*c*不是 EOF 或在范围 0 到 0xff 内，非独占。 使用调试 CRT 库时， *c*是不包含其中一个值，函数将引发断言。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istlower**|**islower**|[_ismbclower](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**iswlower**|
|**_istlower_l**|`_islower _l`|[_ismbclower_l](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**_liswlower_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**islower**|\<ctype.h>|
|**iswlower**|\<ctype.h 1> 或 \<wchar.h 1>|
|**_islower_l**|\<ctype.h>|
|**_swlower_l**|\<ctype.h 1> 或 \<wchar.h 1>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
