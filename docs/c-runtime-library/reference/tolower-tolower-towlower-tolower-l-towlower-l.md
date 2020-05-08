---
title: tolower、_tolower、towlower、_tolower_l、_towlower_l
ms.date: 4/2/2020
api_name:
- _tolower_l
- towlower
- tolower
- _tolower
- _towlower_l
- _o__tolower
- _o__tolower_l
- _o__towlower_l
- _o_tolower
- _o_towlower
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _totlower
- tolower
- _tolower
- towlower
helpviewer_keywords:
- tolower_l function
- _tolower_l function
- totlower function
- string conversion, to different characters
- lowercase, converting to
- tolower function
- string conversion, case
- towlower function
- _tolower function
- _totlower function
- towlower_l function
- case, converting
- characters, converting
- _towlower_l function
ms.assetid: 86e0fc02-94ae-4472-9631-bf8e96f67b92
ms.openlocfilehash: c8b27c4cc618d34d9da9b5884c6db2f525fd2388
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910014"
---
# <a name="tolower-_tolower-towlower-_tolower_l-_towlower_l"></a>tolower、_tolower、towlower、_tolower_l、_towlower_l

将字符转换为小写。

## <a name="syntax"></a>语法

```C
int tolower(
   int c
);
int _tolower(
   int c
);
int towlower(
   wint_t c
);
int _tolower_l(
   int c,
   _locale_t locale
);
int _towlower_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*ansi-c*<br/>
要转换的字符。

*locale*<br/>
用于特定区域设置翻译的区域设置。

## <a name="return-value"></a>返回值

如果可以进行转换，则这些例程会将*c*的副本转换为小写，并返回结果。 没有保留任何返回值以指示错误。

## <a name="remarks"></a>备注

如果可行且相关，则其中的各个例程将指定大写字母转换为小写字母。 **Towlower**的大小写转换是特定于区域设置的。 只改变与当前区域设置相关的字符的大小写。 没有 **_l**后缀的函数使用当前设置的区域设置。 这些具有 **_l**后缀的函数的版本将区域设置用作参数，并使用该区域设置，而不是使用当前设置的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

为了使 **_tolower**提供预期结果， [__isascii](isascii-isascii-iswascii.md)和[isupper](isupper-isupper-l-iswupper-iswupper-l.md)必须返回非零值。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totlower**|**tolower**|**_mbctolower**|**towlower**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_l**|

> [!NOTE]
> **_tolower_l**和 **_towlower_l**没有区域设置依赖关系，因此不应直接调用。 它们由 **_totlower_l**供内部使用。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**tolower**|\<ctype.h>|
|**_tolower**|\<ctype.h>|
|**towlower**|\<ctype.h 1> 或 \<wchar.h 1>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [to 函数](../../c-runtime-library/to-functions.md)中的示例。

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
[to 函数](../../c-runtime-library/to-functions.md)<br/>
[本地](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
