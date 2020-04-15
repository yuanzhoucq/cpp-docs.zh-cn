---
title: _ismbblead、_ismbblead_l
description: 描述 Microsoft C 运行时库 （CRT） _ismbblead和_ismbblead_l功能。
ms.date: 4/2/2020
api_name:
- _ismbblead_l
- _ismbblead
- _o__ismbblead
- _o__ismbblead_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ismbblead_l
- istlead
- _ismbblead
- _ismbblead_l
- ismbblead
- _istlead
helpviewer_keywords:
- _ismbblead_l function
- ismbblead function
- _ismbblead function
- istlead function
- ismbblead_l function
- _istlead function
ms.assetid: 2abc6f75-ed5c-472e-bfd0-e905a1835ccf
ms.openlocfilehash: ee3085d49a27f2f3c97c6578463cf3a0598b73c7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343579"
---
# <a name="_ismbblead-_ismbblead_l"></a>_ismbblead、_ismbblead_l

测试字符以确定它是否是多字节字符的引线字节。

## <a name="syntax"></a>语法

```C
int _ismbblead(
   unsigned int c
);
int _ismbblead_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*C*\
要测试的整数。

*现场*\
要使用的区域设置。

## <a name="return-value"></a>返回值

如果整数*c*是多字节字符的第一个字节，则返回非零值。

## <a name="remarks"></a>备注

多字节字符由前导字节后跟尾随字节构成。 通过在给定字符集中的特定范围来辨别前导字节。 例如，仅在代码页 932 中，潜在顾客字节的范围范围为 0x81 - 0x9F 和 0xE0 - 0xFC。

**_ismbblead**使用当前区域设置进行与区域设置相关的行为。 **_ismbblead_l**是相同的，只是它使用传入区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

当区域设置为 UTF-8 时 **，_ismbblead**和 **_ismbblead_l**始终返回 0（false），无论*c*是否为引线字节。

**_ismbblead**和 **_ismbblead_l**是特定于 Microsoft 的，而不是标准 C 库的一部分。 我们不建议您在需要便携式代码的地方使用它们。 对于标准 C 兼容性，请使用**mbrlen。**

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>通用文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead**|始终返回 false|**_ismbblead**|始终返回 false|

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_ismbblead**|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|
|**_ismbblead_l**|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|

\* 适用于测试条件的清单常量。

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字节分类](../../c-runtime-library/byte-classification.md)\
[_ismbb例程](../../c-runtime-library/ismbb-routines.md)\
[mbrlen](mbrlen.md)
