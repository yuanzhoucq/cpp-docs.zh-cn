---
title: isascii、__isascii、iswascii
ms.date: 4/2/2020
api_name:
- iswascii
- __isascii
- _o_iswascii
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
- iswascii
- istascii
- __isascii
- _istascii
- isascii
- ctype/isascii
- ctype/__isascii
- corecrt_wctype/iswascii
helpviewer_keywords:
- __isascii function
- _isascii function
- isascii function
- _istascii function
- istascii function
- iswascii function
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
ms.openlocfilehash: aeb9c27fee4d179cc16caa50c6f0aae521402beb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343914"
---
# <a name="isascii-__isascii-iswascii"></a>isascii、__isascii、iswascii

确定特定字符是否是 ASCII 字符。

## <a name="syntax"></a>语法

```C
int __isascii(
   int c
);
int iswascii(
   wint_t c
);

#define isascii __isascii
```

### <a name="parameters"></a>参数

*C*<br/>
要测试的整数。

## <a name="return-value"></a>返回值

如果**c**是 ASCII 字符的特定表示形式，则每个例程都返回非零。 如果**c**是 ASCII 字符（范围为 0x00 - 0x7F），__isascii返回非零值。 **__isascii** 如果**c**是 ASCII 字符的宽字符表示形式，**则 iswascii**返回一个非零值。 如果**c**不符合测试条件，则每个例程返回 0。

## <a name="remarks"></a>备注

除非定义了处理器前宏_CTYPE_DISABLE_MACROS，否则 **__isascii**和**iswascii**都作为宏实现。

对于向后兼容性，只有在未定义或定义为 0 [&#95;&#95;STDC&#95;&#95;](../../preprocessor/predefined-macros.md)时，才将**isascii**作为宏实现;否则，它是未定义的。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**伊卡西**， **__isascii**|C：\<ctype.h><br /><br /> C++：\<cctype> 或 \<ctype.h>|
|**iswascii**|C：\<wctype.h 1>、\<ctype.h 1>，或 \<wchar.h 1><br /><br /> C++：\<cwctype 1>、\<cctype 1>、\<wctype.h 1>、\<ctype.h 1>，或 \<wchar.h 1>|

**isascii，__isascii**和**iswascii**功能是微软特有的。 **__isascii** 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
