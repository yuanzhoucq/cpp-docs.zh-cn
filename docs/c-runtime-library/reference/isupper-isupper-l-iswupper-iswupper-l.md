---
title: isupper、_isupper_l、iswupper、_iswupper_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- isupper
- iswupper
- _iswupper_l
- _isupper_l
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
- isupper
- _istupper
- iswupper
dev_langs:
- C++
helpviewer_keywords:
- istupper function
- iswupper function
- isupper_l function
- _isupper_l function
- iswupper_l function
- _istupper function
- _iswupper_l function
- isupper function
ms.assetid: da2bcc9f-241c-48c0-9a0e-ad273827e16a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1d58fc8e10fbc533787fe0e7b99194e282bb906f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="isupper-isupperl-iswupper-iswupperl"></a>isupper、_isupper_l、iswupper、_iswupper_l

确定整数是否表示大写字符。

## <a name="syntax"></a>语法

```C
int isupper(
   int c
);
int _isupper_l (
   int c,
   _locale_t locale
);
int iswupper(
   wint_t c
);
int _iwsupper_l(
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

每个这些例程返回非零如果*c*是一个大写字母的特定表示。 **isupper**返回非零值，如果*c*是大写字符 (A-Z)。 **iswupper**返回非零值，如果*c*是宽字符对应于一个大写字母，或如果*c*哪些要么是实现定义的宽字符集之一**iswcntrl**， **iswdigit**， **iswpunct**，或**iswspace**为非零值。 这些例程都返回 0 如果*c*不满足测试条件。

这些函数具有的版本 **_l**后缀其区域设置相关行为使用传入的区域设置而不是当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

行为**isupper**和 **_isupper_l**如果是未定义*c*不是 EOF 或在 0 到 0xFF，非独占的范围。 使用 CRT 调试库时和*c*是不是一种这些值，函数引发的断言。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istupper**|**isupper**|[_ismbcupper](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**iswupper**|
|**_istupper_l**|**_isupper_l**|[_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**_iswupper_l**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**isupper**|\<ctype.h>|
|**_isupper_l**|\<ctype.h>|
|**iswupper**|\<ctype.h 1> 或 \<wchar.h 1>|
|**_iswupper_l**|\<ctype.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
