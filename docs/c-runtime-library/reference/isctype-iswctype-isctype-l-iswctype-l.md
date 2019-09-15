---
title: _isctype、iswctype、_isctype_l、_iswctype_l
ms.date: 11/04/2016
api_name:
- _isctype_l
- iswctype
- _iswctype_l
- _isctype
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswctype
- _isctype
- _isctype_l
- _iswctype
- isctype
- iswctype_l
- isctype_l
- _iswctype_l
helpviewer_keywords:
- isctype_l function
- iswctype_l function
- iswctype function
- _isctype function
- _isctype_l function
- _iswctype_l function
- isctype function
- _iswctype function
ms.assetid: cf7509b7-12fc-4d95-8140-ad2eb98173d3
ms.openlocfilehash: 9fefb852f8ebd34b932842ee4c12b53f79b29641
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954400"
---
# <a name="_isctype-iswctype-_isctype_l-_iswctype_l"></a>_isctype、iswctype、_isctype_l、_iswctype_l

针对*desc*参数指定的 ctype 属性测试*c* 。 对于*desc*的每个有效值，都有一个等效的宽字符分类例程。

## <a name="syntax"></a>语法

```C
int _isctype(
   int c,
   _ctype_t desc
);
int _isctype_l(
   int c,
   _ctype_t desc,
   _locale_t locale
);
int iswctype(
   wint_t c,
   wctype_t desc
);
int _iswctype_l(
   wint_t c,
   wctype_t desc,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*c*<br/>
要测试的整数。

*desc*<br/>
用于测试的属性。 这通常使用 ctype 或 [wctype](wctype.md) 进行检索。

*locale*<br/>
用于任何依赖于区域设置测试的区域设置。

## <a name="return-value"></a>返回值

如果*c*具有在当前区域设置中由*desc*指定的属性，则 **_isctype**和**iswctype**将返回一个非零值，如果不是，则返回0。 这些带有 **_l**后缀的函数的版本相同，只不过它们使用传入的区域设置，而不是其与区域设置相关的行为的当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*c*不是 EOF 或介于0到0xff （含0和0xff），则 **_isctype**和 **_isctype_l**的行为是不确定的。 当使用调试 CRT 库并且*c*不是这些值之一时，函数将引发断言。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|n/a|**_isctype**|n/a|**_iswctype**|
|n/a|**_isctype_l**|n/a|**_iswctype_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_isctype**|\<ctype.h>|
|**iswctype**|\<ctype.h 1> 或 \<wchar.h 1>|
|**_isctype_l**|\<ctype.h>|
|**_iswctype_l**|\<ctype.h 1> 或 \<wchar.h 1>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
