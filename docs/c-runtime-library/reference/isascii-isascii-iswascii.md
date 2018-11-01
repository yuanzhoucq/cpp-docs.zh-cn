---
title: isascii、__isascii、iswascii
ms.date: 11/04/2016
apiname:
- iswascii
- __isascii
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
ms.openlocfilehash: d150e7bb335dc77ed86f445128eebf97b8be5ac3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433652"
---
# <a name="isascii-isascii-iswascii"></a>isascii、__isascii、iswascii

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

*c*<br/>
要测试的整数。

## <a name="return-value"></a>返回值

这些例程返回非零值如果**c**是 ASCII 字符的特定表示形式。 **__isascii**返回非零值，如果**c**是 ASCII 字符 （位于范围 0x00-0x7F）。 **iswascii**返回非零值，如果**c**是 ASCII 字符的宽字符表示形式。 每个例程将返回 0，如果**c**不满足测试条件。

## <a name="remarks"></a>备注

这两 **__isascii**并**iswascii**除非定义了预处理器宏 _ctype_disable_macros，否则作为宏实现。

为了向后兼容**isascii**宏仅当作为实现[ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md)未定义或定义为 0; 否则是不确定。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**isascii**， **__isascii**|C：\<ctype.h><br /><br /> C++：\<cctype> 或 \<ctype.h>|
|**iswascii**|C：\<wctype.h 1>、\<ctype.h 1>，或 \<wchar.h 1><br /><br /> C++：\<cwctype 1>、\<cctype 1>、\<wctype.h 1>、\<ctype.h 1>，或 \<wchar.h 1>|

**Isascii**， **__isascii**并**iswascii**是 Microsoft 特定函数的函数。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
