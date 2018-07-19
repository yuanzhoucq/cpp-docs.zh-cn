---
title: _isctype、iswctype、_isctype_l、_iswctype_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _isctype_l
- iswctype
- _iswctype_l
- _isctype
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
- iswctype
- _isctype
- _isctype_l
- _iswctype
- isctype
- iswctype_l
- isctype_l
- _iswctype_l
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a9ca4580ba19c4efc342186c0c3b348d76ce94e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402543"
---
# <a name="isctype-iswctype-isctypel-iswctypel"></a>_isctype、iswctype、_isctype_l、_iswctype_l

测试*c*由指定的 ctype 属性*desc*自变量。 为每个有效的值*desc*，没有等效的宽字符分类例程。

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

*Desc*<br/>
用于测试的属性。 这通常使用 ctype 或 [wctype](wctype.md) 进行检索。

*locale*<br/>
用于任何依赖于区域设置测试的区域设置。

## <a name="return-value"></a>返回值

**_isctype**和**iswctype**返回非零值，如果*c*具有指定的属性*desc*中的当前区域设置或如果它不为 0。 使用这些函数的版本 **_l**后缀是相同，只不过它们使用传递区域设置而不是当前区域设置其区域设置相关的行为。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

行为 **_isctype**和 **_isctype_l**如果是未定义*c*不是 EOF 或在 0 到 0xFF，非独占的范围。 使用 CRT 调试库时和*c*是不是一种这些值，函数引发的断言。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|n/a|**_isctype**|n/a|**_iswctype**|
|n/a|**_isctype_l**|n/a|**_iswctype_l**|

## <a name="requirements"></a>要求

|例程|必需的标头|
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
