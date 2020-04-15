---
title: mbrtoc16、mbrtoc323
ms.date: 4/2/2020
api_name:
- mbrtoc16
- mbrtoc32
- _o_mbrtoc16
- _o_mbrtoc32
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: 91755d19eacf73f19700eed7fffbffc529d4e235
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340982"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

将字符串中的第一个 UTF-8 多字节字符转换为等效的 UTF-16 或 UTF-32 字符。

## <a name="syntax"></a>语法

```C
size_t mbrtoc16(
   char16_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);

size_t mbrtoc32(
   char32_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);
```

### <a name="parameters"></a>参数

*目的地*\
指向要转换的uTF-8的**char16_t**或**等效**char32_t个。 如果为 null，则函数不存储值。

*源*\
指向要转换的 UTF-8 多字节字符串。

*max_bytes*\
要检查要转换的字符的*源*中的最大字节数。 此参数应该是一个介于 1 和字节数之间的值，包括任何空终止符，保留在*源*中。

*状态*\
指向用于将 UTF-8 多字节字符串解释为一个或多个输出字符**的mbstate_t**转换状态对象的指针。

## <a name="return-value"></a>返回值

成功时，返回应用这些条件中的第一个条件的值，给定当前*状态*值：

|“值”|条件|
|-----------|---------------|
|0|从*源*转换的下一*个max_bytes*或更少的字符对应于空宽字符，即*目标*不为空时存储的值。<br /><br /> *状态*包含初始移位状态。|
|1 至*max_bytes*之间 ， 包括|返回的值是完成有效多字节字符的*源*字节数。 如果*目标*不是 null，则存储转换的宽字符。|
|-3|如果*目标*不是 null，则以前调用函数产生的下一个宽字符已存储在*目标*中。 此函数调用不会使用*源*中的字节。<br /><br /> 当*源*指向需要多个宽字符来表示的 UTF-8 多字节字符（例如，代理项对）时，将更新*状态*值，以便下一个函数调用写入附加字符。|
|-2|下一*个max_bytes*字节表示不完整但可能有效的 UTF-8 多字节字符。 *目标*中未存储任何值。 如果*max_bytes*为零，则可能发生此结果。|
|-1|发生编码错误。 下一*个max_bytes*或更少的字节不会有助于完整和有效的 UTF-8 多字节字符。 *目标*中未存储任何值。<br /><br /> **EILSEQ**存储在**errno 中**，并且转换状态值*状态*未指定。|

## <a name="remarks"></a>备注

**mbrtoc16**函数从*源*读取最多*max_bytes*个字节，以查找第一个完整、有效的 UTF-8 多字节字符，然后在*目标*中存储等效的 UTF-16 字符。 如果字符需要多个 UTF-16 输出字符（如代理项对），则*状态*值设置为在下一次调用**mbrtoc16**时将下一个 UTF-16 字符存储在*目标*中。 **mbrtoc32**函数相同，但输出存储为 UTF-32 字符。

如果*源*为 null，这些函数返回使用**NULL**参数为*源*`""`（空，空终止字符串）*进行的调用*的等效项，以及*max_bytes*的 1。 将忽略*目标*值和*max_bytes。*

如果*源*不为空，则函数从字符串的开头开始，并最多检查*max_bytes*个字节以确定完成下一个 UTF-8 多字节字符（包括任何移位序列）所需的字节数。 如果检查的字节包含有效且完整的 UTF-8 多字节字符，则该函数将该字符转换为等效的 16 位或 32 位宽字符或字符。 如果*目标*不为空，则函数在目标中存储第一个（可能也是唯一）结果字符。 如果需要其他输出字符，则以*状态*设置值，以便随后对函数的调用输出附加字符并返回值 -3。 如果不需要更多的输出字符，则*状态*设置为初始移位状态。

要将非 UTF-8 多字节字符转换为 UTF-16 LE 字符，请使用[mbrtowc、mbtowc](mbrtowc.md)[或_mbtowc_l](mbtowc-mbtowc-l.md)函数。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**姆布托茨16** **，mbrtoc32**|\<uchar.h>|\<cuchar>|

有关其他兼容性信息，请参阅[兼容性](../compatibility.md)。

## <a name="see-also"></a>另请参阅

[数据转换](../data-conversion.md)\
[现场](../locale.md)\
[多字节字符序列的解释](../interpretation-of-multibyte-character-sequences.md)\
[c16r墓，c32r墓](c16rtomb-c32rtomb1.md)\
[姆布尔托万](mbrtowc.md)\
[姆布斯尔托茨](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
