---
title: isalpha、iswalpha、_isalpha_l、_iswalpha_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- iswalpha
- _iswalpha_l
- isalpha
- _isalpha_l
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
- _istalpha
- _ismbcalpha_l
- isalpha
- _isalpha_l
- iswalpha
- _istalpha_l
- _iswalpha_l
dev_langs:
- C++
helpviewer_keywords:
- _iswalpha_l function
- _isalpha_l function
- _ismbcalpha_l function
- _istalpha_l function
- _ismbcalpha function
- isalpha function
- iswalpha function
- istalpha function
- _istalpha function
ms.assetid: ed6cc2be-c4b0-4475-87ac-bc06d8c23064
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28d533a7865a49df7cc962e0f2cc392f5e56d95d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="isalpha-iswalpha-isalphal-iswalphal"></a>isalpha、iswalpha、_isalpha_l、_iswalpha_l

确定整数是否表示字母字符。

## <a name="syntax"></a>语法

```C
int isalpha(
   int c
);
int iswalpha(
   wint_t c
);
int _isalpha_l(
   int c,
   _locale_t locale
);
int _iswalpha_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*c*<br/>
要测试的整数。

*locale*<br/>
要使用的非当前区域设置。

## <a name="return-value"></a>返回值

每个这些例程返回非零如果*c*是字母字符的特定表示。 **isalpha**返回非零值，如果*c*在 A-Z 或 a-z 范围内。 **iswalpha**为其返回非零值仅对宽字符[iswupper](isupper-isupper-l-iswupper-iswupper-l.md)或**iswlower**为非零值; 即为任何宽字符，它是一个为设置的实现定义的且没有**iswcntrl**， **iswdigit**， **iswpunct**，或**iswspace**为非零值。 这些例程都返回 0 如果*c*不满足测试条件。

这些函数具有的版本 **_l**后缀使用传入的区域设置参数而不是当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

行为**isalpha**和 **_isalpha_l**如果是未定义*c*不是 EOF 或在 0 到 0xFF，非独占的范围。 使用 CRT 调试库时和*c*是不是一种这些值，函数引发的断言。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istalpha**|**isalpha**|**_ismbcalpha**|**iswalpha**|
|**_istalpha_l**|**_isalpha_l**|**_ismbcalpha_l**|**_iswalpha_l**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**isalpha**|\<ctype.h>|
|**iswalpha**|\<ctype.h 1> 或 \<wchar.h 1>|
|**_isalpha_l**|\<ctype.h>|
|**_iswalpha_l**|\<ctype.h 1> 或 \<wchar.h 1>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
