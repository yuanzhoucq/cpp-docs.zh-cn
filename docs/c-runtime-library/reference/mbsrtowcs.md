---
title: mbsrtowcs
ms.date: 4/2/2020
api_name:
- mbsrtowcs
- _o_mbsrtowcs
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
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: 509046e1c55d89cd78b09076838983691423a1ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338881"
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

*wc斯特*<br/>
用于存储转换生成的宽字符字符串的地址。

*姆布斯特*<br/>
指向要转换的多字节字符字符串位置的间接指针。

*count*<br/>
要在*wcstr*中转换和存储的最大字符数（而不是字节数）。

*mbstate*<br/>
指向**mbstate_t**转换状态对象的指针。 如果此值为 null 指针，则使用静态内部转换状态对象。 由于内部**mbstate_t**对象不是线程安全的，因此我们建议您始终传递自己的*mbstate*参数。

## <a name="return-value"></a>返回值

返回成功转换的字符数，不包括终止 null 字符（若有）。 如果发生错误，则返回 （size_t）（-1），并将**errno**设置到 EILSEQ。

## <a name="remarks"></a>备注

**mbsrtowcs**函数通过使用*mbstate*中包含的转换状态，将*mbstr*间接指向的多字节字符字符串转换为存储在*wcstr*指向的缓冲区中的宽字符。 每个字符的转换将继续，直到遇到终止 null 多字节字符、遇到与当前区域设置中的有效字符不对应的多字节序列，或直到*计数*字符已转换。 如果**mbsrtowcs**在*计数*发生之前或发生计数时遇到多字节空字符 （"\0"），它将转换为 16 位终止空字符并停止。

因此，仅当**mbsrtowcs**在转换期间遇到多字节空字符时 *，wcstr*处的宽字符字符串才为 null 终止。 如果*mbstr*和*wcstr*指向的序列重叠，则**mbsrtowcs**的行为未定义。 **mbsrtowcs**受当前区域设置LC_TYPE类别的影响。

**mbsrtowcs**函数不同于[mbstowcs，_mbstowcs_l](mbstowcs-mbstowcs-l.md)它的可重新启动性。 转换状态以*mbstate*存储，用于后续对相同或其他可重新启动函数的调用。 混合使用可重启函数和不可重启函数时，结果不确定。  例如，如果使用对**mbsrtowc 的**后续调用而不是**mbstowcs，** 则应用程序应使用**mbsrlen**而不是**mbslen。**

如果*wcstr*不是空指针，则如果由于达到终止空字符而停止转换，则*mbstr*指向的指针对象将分配一个空指针。 否则，它将分配到紧跟已转换出的最后一个多字节字符的地址（若有）。 这将允许调用后续函数以在此调用停止的位置重新调用转换。

如果*wcstr*参数是空指针，则忽略*count*参数 **，mbsrtowcs**返回目标字符串所需的宽字符大小。 如果*mbstate*是空指针，则函数使用非线程安全静态**mbstate_t**转换状态对象。 如果字符序列*mbstr*没有相应的多字节字符表示形式，则返回 -1 并将**errno**设置为**EILSEQ**。

如果*mbstr*是空指针，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，此函数将**errno**设置到**EINVAL**并返回 -1。

在 C++ 中，此函数具有一个调用此函数的更新、更安全副本的模板重载。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="exceptions"></a>例外

只要此函数正在执行并且*mbstate*参数不是空指针 **，mbsrtowcs**函数是多线程安全的，只要当前线程调用中没有函数**设置局部性**。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
