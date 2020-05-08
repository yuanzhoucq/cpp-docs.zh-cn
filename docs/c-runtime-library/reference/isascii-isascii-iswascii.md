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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 3e04b85c9ce7519593802c21311315d534dce6a5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919792"
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

*ansi-c*<br/>
要测试的整数。

## <a name="return-value"></a>返回值

如果**c**是 ASCII 字符的特定表示形式，则每个例程将返回非零值。 如果**c**是 ASCII 字符（在 0X00-0x7f 范围内）， **__isascii**将返回一个非零值。 如果**c**是 ASCII 字符的宽字符表示形式，则**iswascii**将返回一个非零值。 如果**c**不满足测试条件，则这些例程都将返回0。

## <a name="remarks"></a>备注

**__Isascii**和**iswascii**都作为宏实现，除非定义了预处理器宏 _CTYPE_DISABLE_MACROS。

为了向后兼容， **isascii**仅在未定义[&#95;&#95;STDC&#95;&#95;](../../preprocessor/predefined-macros.md)或定义为0时才作为宏实现;否则为未定义。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**isascii**、 **__isascii**|C：\<ctype.h><br /><br /> C++：\<cctype> 或 \<ctype.h>|
|**iswascii**|C：\<wctype.h 1>、\<ctype.h 1>，或 \<wchar.h 1><br /><br /> C++：\<cwctype 1>、\<cctype 1>、\<wctype.h 1>、\<ctype.h 1>，或 \<wchar.h 1>|

**Isascii**、 **__isascii**和**iswascii**函数是 Microsoft 特定的。 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[本地](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
