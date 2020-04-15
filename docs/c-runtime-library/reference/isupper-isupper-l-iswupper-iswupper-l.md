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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 713689649b33873796b7a73bad6a4ac6e8acc998
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342800"
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

*C*<br/>
要测试的整数。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果*c*是大写字母的特定表示形式，则每个例程都返回非零。 如果*c*是大写字符 （A - Z），**则半价**返回非零值。 如果*c*是对应于大写字母的宽字符，或者如果*c*是实现定义的宽字符集之一，则**iswwupper**返回一个非零值，其中任何 iswcntrl、iswwdigit、iswpunct 或**iswspace**都不是零。 **iswcntrl** **iswdigit** **iswpunct** 如果*c*不符合测试条件，则每个例程返回 0。

具有 **_l**后缀的这些函数的版本使用传入区域设置，而不是当前区域设置，用于其与区域设置相关的行为。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*c*不是 EOF 或范围 0 到 0xFF（包括）时，**则 _isupper_l****的行为未定义**。 当使用调试 CRT 库，*并且 c*不是这些值之一时，这些函数将引发断言。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istupper**|**是**|[_ismbcupper](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**异种**|
|**_istupper_l**|**_isupper_l**|[_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**_iswupper_l**|

## <a name="remarks"></a>备注

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**是**|\<ctype.h>|
|**_isupper_l**|\<ctype.h>|
|**异种**|\<ctype.h 1> 或 \<wchar.h 1>|
|**_iswupper_l**|\<ctype.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
