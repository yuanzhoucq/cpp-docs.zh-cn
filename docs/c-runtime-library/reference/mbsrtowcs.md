---
title: mbsrtowcs | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- mbsrtowcs
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
- mbsrtowcs
dev_langs:
- C++
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a886e3d0ec58d137fbd39e767e11f48364ce7a0b
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
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
最大字符数 （不字节数） 将转换并将存储在*wcstr*。

*mbstate*<br/>
指向的指针**mbstate_t**转换状态对象。 如果此值为 null 指针，则使用静态内部转换状态对象。 因为内部**mbstate_t**对象不是线程安全，我们建议始终传递你自己*mbstate*参数。

## <a name="return-value"></a>返回值

返回成功转换的字符数，不包括终止 null 字符（若有）。 返回 (如果出错，并且设置 size_t)(-1) **errno**为 EILSEQ。

## <a name="remarks"></a>备注

**Mbsrtowcs**函数将转换的间接指向的多字节字符字符串*mbstr*，到指向的缓冲区中存储的宽字符*wcstr*，也可由使用中包含的转换状态*mbstate*。 转换将一直对每个字符遇到任一终止 null 多字节字符时，遇到与当前区域设置中的有效字符不对应的多字节序列时，或直到*计数*已转换字符。 如果**mbsrtowcs**遇到多字节 null 字符 (\0) 之前或当*计数*发生，它将其转换为 16 位终止 null 字符并停止。

因此，在宽字符字符串*wcstr*是以 null 结尾的仅当**mbsrtowcs**在转换过程中遇到多字节 null 字符。 如果指向的序列*mbstr*和*wcstr*重叠的行为**mbsrtowcs**是不确定的。 **mbsrtowcs**受到当前区域设置中 LC_TYPE 类别。

**Mbsrtowcs**函数不同于[mbstowcs，_mbstowcs_l](mbstowcs-mbstowcs-l.md)通过其可重启性。 转换状态存储在*mbstate*以便后续调用相同的或其他可重启函数。 混合使用可重启函数和不可重启函数时，结果不确定。  例如，应用程序应使用**mbsrlen**而不是**mbslen**，如果的后续调用**mbsrtowcs**而不是使用**mbstowcs**.

如果*wcstr*不是 null 指针，指向指针对象*mbstr*赋给 null 指针，则在转换因到达终止 null 字符而停止。 否则，它将分配到紧跟已转换出的最后一个多字节字符的地址（若有）。 这将允许调用后续函数以在此调用停止的位置重新调用转换。

如果*wcstr*参数为 null 指针，*计数*忽略自变量和**mbsrtowcs**以目标字符串的宽字符形式返回所需的大小。 如果*mbstate*是 null 指针，该函数使用非线程安全的静态内部**mbstate_t**转换状态对象。 如果字符序列*mbstr*没有相应的多字节字符表示形式，则返回-1 和**errno**设置为**EILSEQ**。

如果*mbstr*是空指针，无效参数处理程序调用中所述，[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数将**errno**到**EINVAL**并返回-1。

在 C++ 中，此函数具有一个调用此函数的更新、更安全副本的模板重载。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>异常

**Mbsrtowcs**函数是多线程安全，前提是当前线程中的函数不调用**setlocale** ，只要此函数正在执行和*mbstate*参数不是 null 指针。

## <a name="requirements"></a>要求

|例程|必需的标头|
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
