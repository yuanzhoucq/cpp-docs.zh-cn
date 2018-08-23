---
title: iscsym、iscsymf、__iscsym、__iswcsym、__iscsymf、__iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _iswcsym_l
- __iswcsym
- __iscsym
- _iswcsymf_l
- _iscsym_l
- __iswcsymf
- __iscsymf
- _iscsymf_l
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
- _iswcsym_l
- _iswcsymf_l
- iscsymf
- iswcsymf
- __iswcsym
- __iswcsymf
- iscsym
- iswcsym
- __iscsym
- _iscsym_l
- _iscsymf_l
- __iscsymf
- ctype/iscsym
- ctype/iscsymf
- ctype/__iscsym
- ctype/__iscsymf
- ctype/__iscsym_l
- ctype/__iscsymf_l
- ctype/__iswcsym
- ctype/__iswcsymf
- ctype/__iswcsym_l
- ctype/__iswcsymf_l
dev_langs:
- C++
helpviewer_keywords:
- iscsymf_l function
- iswsym_l function
- _iswcsym_l function
- iscsym_l function
- _iscsymf_l function
- _iswcsymf_l function
- _iscsym_l function
- __iscsym function
- __iswcsymf function
- iswsymf_l function
- __iscsymf function
- __iswcsym function
- iscsym function
- iscsymf function
ms.assetid: 944dfb99-f2b8-498c-9f55-dbcf370d0a2c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b1561e93fc19832607d304f3d087ab33b04040de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401917"
---
# <a name="iscsym-iscsymf-iscsym-iswcsym-iscsymf-iswcsymf-iscsyml-iswcsyml-iscsymfl-iswcsymfl"></a>iscsym、iscsymf、__iscsym、__iswcsym、__iscsymf、__iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l

确定整数是否表示可在标识符中使用的字符。

## <a name="syntax"></a>语法

```C
int __iscsym(
   int c
);
int __iswcsym(
   wint_t c
);
int __iscsymf(
   int c
);
int __iswcsymf(
   wint_t c
);
int _iscsym_l(
   int c,
   _locale_t locale
);
int _iswcsym_l(
   wint_t c,
   _locale_t locale
);
int _iscsymf_l(
   int c,
   _locale_t locale
);
int _iswcsymf_l(
   wint_t c,
   _locale_t locale
);
#define iscsym __iscsym
#define iscsymf __iscsymf
```

### <a name="parameters"></a>参数

*c*<br/>
要测试的整数。 *c*应在 0-255 窄字符版本的函数的范围内。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

同时 **__iscsym**和 **__iswcsym**返回非零值，如果*c*是字母、 下划线或数字。 同时 **__iscsymf**和 **__iswcsymf**返回非零值，如果*c*是一个字母或下划线。 这些例程都返回 0 如果*c*不满足测试条件。 使用这些函数的版本 **_l**后缀是相同，只不过它们使用*区域设置*为其区域设置相关的行为传入而不是当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

## <a name="remarks"></a>备注

除非定义了预处理器宏 _CTYPE_DISABLE_MACROS，否则这些例程将被定义为宏。 在使用这些例程的宏版本时，可多次计算参数。 使用参数列表中带副作用的表达式时要小心。

为了向后兼容， **iscsym**和**iscsymf**定义为宏时，才[ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md)未定义或定义为 0;否则，它们是不确定。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**iscsym**， **iscsymf**， **__iscsym**， **__iswcsym**， **__iscsymf**， **__iswcsymf**， **_iscsym_l**， **_iswcsym_l**， **_iscsymf_l**， **_iswcsymf_l**|C：\<ctype.h><br /><br /> C++：\<cctype> 或 \<ctype.h>|

**Iscsym**， **iscsymf**， **__iscsym**， **__iswcsym**， **__iscsymf**， **__iswcsymf**， **_iscsym_l**， **_iswcsym_l**， **_iscsymf_l**，和 **_iswcsymf_l**例程Microsoft 专用。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
