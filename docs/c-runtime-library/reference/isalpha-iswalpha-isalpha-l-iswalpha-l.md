---
title: isalpha、iswalpha、_isalpha_l、_iswalpha_l
ms.date: 4/2/2020
api_name:
- iswalpha
- _iswalpha_l
- isalpha
- _isalpha_l
- _o_isalpha
- _o_iswalpha
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _istalpha
- _ismbcalpha_l
- isalpha
- _isalpha_l
- iswalpha
- _istalpha_l
- _iswalpha_l
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
ms.openlocfilehash: 187031adc0b22aff2c5418cd7e0f3e64075f1745
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343933"
---
# <a name="isalpha-iswalpha-_isalpha_l-_iswalpha_l"></a>isalpha、iswalpha、_isalpha_l、_iswalpha_l

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

*C*<br/>
要测试的整数。

*现场*<br/>
要使用的非当前区域设置。

## <a name="return-value"></a>返回值

如果*c*是字母字符的特定表示形式，则每个例程都返回非零。 如果*c*在范围 A - Z 或 a - z 内 **，isalpha**返回非零值。 **iswalpha**仅返回非零值，该宽字符的[正面](isupper-isupper-l-iswupper-iswupper-l.md)或正**惠者**为非零;也就是说，对于任何宽字符，它是实现定义的集之一，其中没有 iswcntrl、iswdigit、iswpunct**iswpunct**或**iswspace**是非零。 **iswcntrl** **iswdigit** 如果*c*不符合测试条件，则每个例程返回 0。

具有 **_l**后缀的这些函数的版本使用传入区域设置参数，而不是当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*c*不是 EOF 或范围 0 到 0xFF（包括）时 **，isalpha**和 **_isalpha_l**的行为未定义。 当使用调试 CRT 库，*并且 c*不是这些值之一时，这些函数将引发断言。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istalpha**|**isalpha**|**_ismbcalpha**|**iswalpha**|
|**_istalpha_l**|**_isalpha_l**|**_ismbcalpha_l**|**_iswalpha_l**|

## <a name="remarks"></a>备注

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**isalpha**|\<ctype.h>|
|**iswalpha**|\<ctype.h 1> 或 \<wchar.h 1>|
|**_isalpha_l**|\<ctype.h>|
|**_iswalpha_l**|\<ctype.h 1> 或 \<wchar.h 1>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
