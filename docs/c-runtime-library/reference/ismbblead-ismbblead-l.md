---
title: _ismbblead、_ismbblead_l
description: 描述 Microsoft C 运行时库（CRT） _ismbblead 和 _ismbblead_l 函数。
ms.date: 01/08/2020
api_name:
- _ismbblead_l
- _ismbblead
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
ms.openlocfilehash: 6a7bb992eeeb9c66a7cbdea0ed34cf797d374617
ms.sourcegitcommit: 7bd3567fc6a0e7124aab51cad63bbdb44a99a848
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755033"
---
# <a name="_ismbblead-_ismbblead_l"></a>_ismbblead、_ismbblead_l

测试一个字符，以确定它是否是多字节字符的前导字节。

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

*c*\
要测试的整数。

*区域设置*\
要使用的区域设置。

## <a name="return-value"></a>返回值

如果整数*c*是多字节字符的第一个字节，则返回一个非零值。

## <a name="remarks"></a>备注

多字节字符由前导字节后跟尾随字节构成。 通过在给定字符集中的特定范围来辨别前导字节。 例如，仅在代码页932中，前导字节范围为 0x81-0x9F 和 0xE0-0xFC。

**_ismbblead**将当前区域设置用于与区域设置相关的行为。 **_ismbblead_l**相同，只不过它使用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果区域设置为 UTF-8， **_ismbblead**和 **_ismbblead_l**总是返回0（false），而无论*c*是否为前导字节。

**_ismbblead**和 **_Ismbblead_l**特定于 Microsoft，而不是标准 C 库的一部分。 建议你不要在需要可移植代码的位置使用它们。 对于标准 C 兼容性，请改用**mbrlen** 。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead**|始终返回 false|**_ismbblead**|始终返回 false|

## <a name="requirements"></a>需求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_ismbblead**|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|
|**_ismbblead_l**|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|

\* 适用于测试条件的清单常量。

有关兼容性的详细信息，请参阅 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字节分类](../../c-runtime-library/byte-classification.md)\
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)\
[mbrlen](mbrlen.md)
