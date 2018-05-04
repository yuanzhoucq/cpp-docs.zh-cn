---
title: mbsrtowcs_s | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- mbsrtowcs_s
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
- mbsrtowcs_s
dev_langs:
- C++
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8885d11c7fca10c63077464020a8bbab2b6f3ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="mbsrtowcss"></a>mbsrtowcs_s

将当前区域设置中的多字节字符字符串转换为宽字符字符串表示形式。 这是 [mbsrtowcs](mbsrtowcs.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t * wcstr,
   size_t sizeInWords,
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
);
template <size_t size>
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t (&wcstr)[size],
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
); // C++ only
```

### <a name="parameters"></a>参数

*pReturnValue*<br/>
要转换的字符数。

*wcstr*<br/>
用于存储转换所生成的宽字符字符串的缓冲区地址。

*sizeInWords*<br/>
大小*wcstr*字 （宽字符）。

*mbstr*<br/>
指向要转换的多字节字符字符串位置的间接指针。

*count*<br/>
宽字符存储中的最大数*wcstr*缓冲区，不包括终止 null 或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*mbstate*<br/>
指向的指针**mbstate_t**转换状态对象。 如果此值为 null 指针，则使用静态内部转换状态对象。 因为内部**mbstate_t**对象不是线程安全，我们建议始终传递你自己*mbstate*参数。

## <a name="return-value"></a>返回值

如果转换成功则返回零；如果失败则返回错误代码。

|错误条件|返回值和**errno**|
|---------------------|------------------------------|
|*wcstr*是 null 指针和*sizeInWords* > 0|**EINVAL**|
|*mbstr*是 null 指针|**EINVAL**|
|字符串间接指向的*mbstr*包含不是有效的当前区域设置的多字节序列。|**EILSEQ**|
|目标缓冲区是太小，无法包含转换的字符串 (除非*计数*是 **_TRUNCATE**; 有关详细信息，请参阅备注)|**ERANGE**|

如果发生这些情况中的任何一个，都会调用无效的参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，函数将返回错误代码和设置**errno**表中所示。

## <a name="remarks"></a>备注

**Mbsrtowcs_s**函数将转换的间接指向的多字节字符字符串*mbstr*存储指向的缓冲区中的宽字符*wcstr*，也可由使用中包含的转换状态*mbstate*。 在满足以下条件之一前，该转换将一直对每个字符执行：

- 遇到一个多字节空字符

- 遇到一个无效的多字节字符

- 存储中的宽字符数*wcstr*缓冲等于*计数*。

目标字符串*wcstr*是始终以 null 结尾的即使在出错，除非*wcstr*是 null 指针。

如果*计数*是特殊值[_TRUNCATE](../../c-runtime-library/truncate.md)， **mbsrtowcs_s**将尽可能多的字符串作为将放入目标缓冲区中，同时仍保持 null 的空间终结器。

如果**mbsrtowcs_s**成功转换了源字符串，它将大小放在宽字符转换的字符串和 null 终止符到 *&#42;pReturnValue*、 提供*pReturnValue*不是 null 指针。 发生这种情况即使*wcstr*自变量为 null 指针，并允许你确定所需的缓冲区大小。 请注意，如果*wcstr*是 null 指针，*计数*将被忽略。

如果*wcstr*不是 null 指针，指向指针对象*mbstr*赋给 null 指针，则在转换因到达终止 null 字符而停止。 否则，它将分配到紧跟已转换出的最后一个多字节字符的地址（若有）。 这将允许调用后续函数以在此调用停止的位置重新调用转换。

如果*mbstate*是 null 指针，内部库**mbstate_t**使用转换状态静态对象。 由于此内部静态对象不是线程安全的因此我们建议传递你自己*mbstate*值。

如果**mbsrtowcs_s**遇到在当前的区域中，不是有效的多字节字符它将为-1 放在 *&#42;pReturnValue*，设置目标缓冲区*wcstr*为空字符串，将设置**errno**到**EILSEQ**，并返回**EILSEQ**。

如果指向的序列*mbstr*和*wcstr*重叠的行为**mbsrtowcs_s**是不确定的。 **mbsrtowcs_s**受到当前区域设置中 LC_TYPE 类别。

> [!IMPORTANT]
> 确保*wcstr*和*mbstr*未重叠，且*计数*正确反映了要转换的多字节字符的数量。

**Mbsrtowcs_s**函数不同于[mbstowcs_s、 _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)通过其可重启性。 转换状态存储在*mbstate*以便后续调用相同的或其他可重启函数。 混合使用可重启函数和不可重启函数时，结果不确定。 例如，应用程序应使用**mbsrlen**而不是**mbslen**，如果的后续调用**mbsrtowcs_s**而不是使用**mbstowcs_s**.

在 C++ 中，模板重载简化了这些函数的使用；重载可以自动推导出缓冲区长度(不再需要指定大小自变量)，并且它们可以通过使用更新、更安全的对应函数来自动替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>异常

**Mbsrtowcs_s**函数是多线程安全，如果当前线程调用中的函数不**setlocale** ，只要此函数正在执行和*mbstate*自变量是不是 null 指针。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**mbsrtowcs_s**|\<wchar.h>|

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s、_mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
