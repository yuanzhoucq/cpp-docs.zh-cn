---
title: mbrtoc16、mbrtoc323
ms.date: 11/04/2016
api_name:
- mbrtoc16
- mbrtoc32
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
ms.openlocfilehash: 52bcec5911fdc2ecbb073ae0042777aa4eb2b963
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952451"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

将窄字符串的首个多字节字符转换为等效的 UTF-16 或 UTF-32 字符。

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

*位置*<br/>
指向要转换的多字节字符的**char16_t**或**char32_t**等效项的指针。 如果为 null，则该函数不存储值。

*source*<br/>
指向要转换的多字节字符串的指针。

*max_bytes*<br/>
用于检查要转换的字符的*源*中的最大字节数。 该值应是介于1和字节数之间的值（包括任何 null 终止符）（*源*中剩余）。

State<br/>
指向用于将多字节字符串解释为一个或多个输出字符的**mbstate_t**转换状态对象的指针。

## <a name="return-value"></a>返回值

如果成功，则返回在给定当前*状态*值的情况下应用的第一个条件的值：

|值|条件|
|-----------|---------------|
|0|*从源*转换的*max_bytes*中的下一个或更少字符对应于空宽字符，这是在*目标*不为 null 时存储的值。<br /><br /> *状态*包含初始移位状态。|
|介于1和*max_bytes*（含）之间|返回的值是完成有效多字节字符的*源*字节数。 如果*destination*为 not null，则存储转换后的宽字符。|
|-3|如果*destination*为 not null，则以前对函数的调用生成的下一个宽字符存储在*目标*中。 此调用不会将*源*中的任何字节用于该函数。<br /><br /> 当*源*指向需要多个宽字符表示的多字节字符（例如代理项对）时，会更新*状态值*，以便下一个函数调用写出其他字符。|
|-2|接下来的*max_bytes*字节表示不完整但可能有效的多字节字符。 *目标*中没有存储任何值。 如果*max_bytes*为零，则会出现此结果。|
|-1|发生编码错误。 下一个*max_bytes*或更少的字节不涉及完整且有效的多字节字符。 *目标*中没有存储任何值。<br /><br /> **Eilseq 且**存储在**errno**中，而转换状态*状态*未指定。|

## <a name="remarks"></a>备注

**Mbrtoc16**函数*从源*中读取最多*max_bytes*个字节，以查找第一个完整有效的多字节字符，然后将等效的 utf-16 字符存储在*目标*中。 根据当前线程多字节区域设置解释源字节。 如果多字节字符需要多个 UTF-16 输出字符，如代理项对，则将*状态*值设置为在下一次调用**mbrtoc16**时将下一个 utf-16 字符存储在*目标*中。 **Mbrtoc32**函数相同，但输出存储为32字符。

如果*source*为 null，则这些函数将返回对*目标*为 **""** 的参数使用**null**的参数的等效项，对于*源*，则返回 1; 对于*max_bytes*，则返回1。 将忽略*目标*和*max_bytes*的传递值。

如果*source*不为 null，则函数将在字符串的开头处开始，并检查最多*max_bytes*个字节，以确定完成下一个多字节字符（包括任何移位序列）所需的字节数。 如果检查的字节包含有效且完整的多字节字符，该函数将字符转换为等效的 16 位或 32 位宽字符或字符。 如果*destination*不为 null，则该函数将在目标中存储第一个（并且可能只是）结果字符。 如果需要其他输出字符，则将值设置为 "*状态*"，以便对函数的后续调用输出其他字符并返回值-3。 如果不需要其他输出字符，则*状态*设置为初始移位状态。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**mbrtoc16**、 **mbrtoc32**|\<uchar.h>|\<cuchar>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[c16rtomb、c32rtomb](c16rtomb-c32rtomb1.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbsrtowcs](mbsrtowcs.md)<br/>
[mbsrtowcs_s](mbsrtowcs-s.md)<br/>
