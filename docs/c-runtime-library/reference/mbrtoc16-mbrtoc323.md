---
title: mbrtoc16, mbrtoc323
ms.date: 11/04/2016
apiname:
- mbrtoc16
- mbrtoc32
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: f8573ac321772d19141be0228891b290ba48b217
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331579"
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

*destination*<br/>
指向**char16_t**或**char32_t**等效的要转换的多字节字符。 如果为 null，则该函数不存储值。

*source*<br/>
指向要转换的多字节字符串的指针。

*max_bytes*<br/>
中的字节的最大数*源*要检查其要转换的字符。 这应是一个，包括任何 null 终止符中的剩余的字节数之间的值*源*。

*state*<br/>
指向**mbstate_t**来解释为一个或多个输出字符的多字节字符串的转换状态对象。

## <a name="return-value"></a>返回值

如果成功，返回的值的第一个应用这些条件，假定当前*状态*值：

|“值”|条件|
|-----------|---------------|
|0|下一步*max_bytes*或从较少的字符转换*源*对应于 null 宽字符，即如果存储的值*目标*不为 null。<br /><br /> *状态*包含初始位移状态。|
|介于 1 和*max_bytes*(含） 之间|返回的值是字节数*源*完成有效多字节字符。 如果将存储在转换后的宽字符*目标*不为 null。|
|-3|已从以前调用该函数生成下一个宽字符存储在*目标*如果*目标*不为 null。 从任何字节*源*供此调用函数。<br /><br /> 当*源*指向多字节字符需要多个宽字符表示 （例如，代理项对），则*状态*，以便在下一次函数调用写入更新值 扩展的其他字符。|
|-2|下一步*max_bytes*字节表示不完整，但可能有效的多字节字符。 没有值存储在*目标*。 如果，则会出现此结果*max_bytes*为零。|
|-1|发生编码错误。 下一步*max_bytes*或更少的字节并影响完整、 有效的多字节字符。 没有值存储在*目标*。<br /><br /> **EILSEQ**存储在**errno**和转换状态*状态*未指定。|

## <a name="remarks"></a>备注

**Mbrtoc16**函数最多读取*max_bytes*个字节从*源*以查找第一个完整的有效多字节字符，然后存储等效的 utf-16在字符*目标*。 根据当前线程多字节区域设置解释源字节。 如果多字节字符需要多个 UTF 16 输出字符，如代理项对，则*状态*值设置为存储中的下一个 utf-16 字符*目标*到下一次调用**mbrtoc16**。 **Mbrtoc32**函数完全相同，但输出存储为 UTF-32 字符。

如果*源*为的 null，这些函数将返回使用的参数进行调用的等效**NULL**有关*目标*， **""** 为*源*，，1 表示*max_bytes*。 传递的值*目标*并*max_bytes*将被忽略。

如果*源*是不为 null，该函数从字符串开头开始并最多检查*max_bytes*字节以确定完成下一个多字节字符所需的字节数包括任何位移序列。 如果检查的字节包含有效且完整的多字节字符，该函数将字符转换为等效的 16 位或 32 位宽字符或字符。 如果*目标*不为 null，第一个 （并且可能是唯一） 结果字符在目标中的函数存储。 如果需要其他输出字符，设置了值*状态*，以便后续调用该函数输出其他字符并返回-3 的值。 如果没有更多输出字符是必需的然后*状态*设置为初始位移状态。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**mbrtoc16**， **mbrtoc32**|\<uchar.h>|\<cuchar>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[c16rtomb、c32rtomb](c16rtomb-c32rtomb1.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbsrtowcs](mbsrtowcs.md)<br/>
[mbsrtowcs_s](mbsrtowcs-s.md)<br/>
