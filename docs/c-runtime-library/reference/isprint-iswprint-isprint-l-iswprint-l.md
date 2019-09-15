---
title: isprint、iswprint、_isprint_l、_iswprint_l
ms.date: 11/04/2016
api_name:
- iswprint
- isprint
- _isprint_l
- _iswprint_l
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 282b72fcec84f8096ce0d54cd114e756aeafbc85
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953749"
---
# <a name="isprint-iswprint-_isprint_l-_iswprint_l"></a>isprint、iswprint、_isprint_l、_iswprint_l

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

如果*c*是可打印字符的特定表示形式，则每个例程将返回非零值。 如果*c*是可打印字符，则**isprint**将返回一个非零值，其中包含空格字符（0x20-0x7E）。 如果*c*是可打印宽字符，则**iswprint**将返回一个非零值，这包括空间宽字符。 如果*c*不满足测试条件，则这些例程都将返回0。

这些函数的测试条件的结果取决于区域设置的**LC_CTYPE**类别设置;有关详细信息，请参阅[setlocale、_wsetlocale](setlocale-wsetlocale.md) 。 这些不带 **_l**后缀的函数的版本对与区域设置相关的行为使用当前区域设置;具有 **_l**后缀的版本是相同的，只不过它们使用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*c*不是 EOF 或介于0到0xff （含0和0xff），则**isprint**和 **_isprint_l**的行为是不确定的。 当使用调试 CRT 库并且*c*不是这些值之一时，函数将引发断言。

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
