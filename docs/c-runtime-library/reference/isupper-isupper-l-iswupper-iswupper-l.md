---
title: isupper、_isupper_l、iswupper、_iswupper_l
ms.date: 4/2/2020
api_name:
- isupper
- iswupper
- _iswupper_l
- _isupper_l
- _o_isupper
- _o_iswupper
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- isupper
- _istupper
- iswupper
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
ms.openlocfilehash: 49aab47a72e7065cbd90935a431f59ec74b562ac
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910402"
---
# <a name="isupper-_isupper_l-iswupper-_iswupper_l"></a>isupper、_isupper_l、iswupper、_iswupper_l

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

*ansi-c*<br/>
要测试的整数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果*c*是大写字母的特定表示形式，则每个例程将返回非零值。 如果*c*是一个大写字符（a-z），则**isupper**将返回一个非零值。 如果*c*是对应于大写字母的宽字符，或者如果*c*是实现定义的宽字符集（其中， **iswcntrl**、 **iswdigit**、 **iswpunct**或**iswspace**均不为零）中的一个，则**iswupper**将返回一个非零值。 如果*c*不满足测试条件，则这些例程都将返回0。

这些具有 **_l**后缀的函数的版本使用传入的区域设置，而不是其与区域设置相关的行为的当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*c*不是 EOF 或介于0到0xff （含0和0xff），则**isupper**和 **_isupper_l**的行为是不确定的。 当使用调试 CRT 库并且*c*不是这些值之一时，函数将引发断言。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istupper**|**isupper**|[_ismbcupper](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**iswupper**|
|**_istupper_l**|**_isupper_l**|[_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**_iswupper_l**|

## <a name="remarks"></a>备注

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**isupper**|\<ctype.h>|
|**_isupper_l**|\<ctype.h>|
|**iswupper**|\<ctype.h 1> 或 \<wchar.h 1>|
|**_iswupper_l**|\<ctype.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[本地](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
