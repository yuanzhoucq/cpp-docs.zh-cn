---
title: mbsrtowcs
ms.date: 11/04/2016
api_name:
- mbsrtowcs
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
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: de7b25ea8a520dfe2c9cb26ec8989624b670dcb9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952051"
---
# <a name="mbsrtowcs"></a>mbsrtowcs

将当前区域设置中的多字节字符字符串转换为相应的宽字符字符串，其中重启功能位于多字节字符的中间。 提供此函数的一个更安全的版本；请参阅 [mbsrtowcs_s](mbsrtowcs-s.md)。

## <a name="syntax"></a>语法

```C
size_t mbsrtowcs(
   wchar_t *wcstr,
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t mbsrtowcs(
   wchar_t (&wcstr)[size],
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>参数

*wcstr*<br/>
用于存储转换生成的宽字符字符串的地址。

*mbstr*<br/>
指向要转换的多字节字符字符串位置的间接指针。

*count*<br/>
要转换并存储在*wcstr*中的最大字符数（不是字节）。

*mbstate*<br/>
指向**mbstate_t**转换状态对象的指针。 如果此值为 null 指针，则使用静态内部转换状态对象。 由于内部**mbstate_t**对象不是线程安全的，因此建议您始终传递您自己的*mbstate*参数。

## <a name="return-value"></a>返回值

返回成功转换的字符数，不包括终止 null 字符（若有）。 如果发生错误，则返回（size_t）（-1），并将**errno**设置为 eilseq 且。

## <a name="remarks"></a>备注

**Mbsrtowcs**函数通过使用*mbstate*中包含的转换状态，将*mbstr*间接指向的多字节字符的字符串转换为存储在*wcstr*所指向的缓冲区中的宽字符。 在遇到终止 null 多字节字符、遇到与当前区域设置中的有效字符不对应的多字节序列，或直到*count*个字符得到. 如果**mbsrtowcs**在计算之前或*计数*时遇到多字节 null 字符（"\ 0"），则它会将其转换为16位终止 null 字符并停止。

因此，仅当**mbsrtowcs**在转换期间遇到多字节 null 字符时，位于*wcstr*的宽字符字符串才以 null 结尾。 如果由*mbstr*和*wcstr*指向的序列重叠，则**mbsrtowcs**的行为不确定。 **mbsrtowcs**受当前区域设置的 LC_TYPE 类别影响。

**Mbsrtowcs**函数的可重启性不同于[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md) 。 转换状态存储在*mbstate*中，以便后续调用相同的或其他可重启的函数。 混合使用可重启函数和不可重启函数时，结果不确定。  例如，如果使用了对**mbsrtowcs**的后续调用而不是**mbstowcs**，则应用程序应使用**mbsrlen**而不是**mbslen**。

如果*wcstr*不是空指针，则在转换因到达终止 null 字符而停止时，将为*mbstr*指向的指针对象分配一个空指针。 否则，它将分配到紧跟已转换出的最后一个多字节字符的地址（若有）。 这将允许调用后续函数以在此调用停止的位置重新调用转换。

如果*wcstr*参数为 null 指针，则忽略*count*参数，并且**mbsrtowcs**返回目标字符串所需的宽字符大小。 如果*mbstate*为 null 指针，则该函数将使用非线程安全的静态内部**mbstate_t**转换状态对象。 如果字符序列*mbstr*没有对应的多字节字符表示形式，则返回-1，并将**Errno**设置为**eilseq 且**。

如果*mbstr* isa null 指针，则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数会将**errno**设置为**EINVAL** ，并返回-1。

在 C++ 中，此函数具有一个调用此函数的更新、更安全副本的模板重载。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>Exceptions

只要当前线程中的函数都不调用**setlocale** （只要此函数正在执行且*mbstate*参数不是 null 指针）， **mbsrtowcs**函数就是多线程安全的。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
