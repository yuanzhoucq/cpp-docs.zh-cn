---
title: mbsrtowcs_s
ms.date: 4/2/2020
api_name:
- mbsrtowcs_s
- _o_mbsrtowcs_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: 72a20396b2f0f75d79baa64619deef8a0c1e00ba
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915500"
---
# <a name="mbsrtowcs_s"></a>mbsrtowcs_s

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
*Wcstr*的大小（宽字符）。

*mbstr*<br/>
指向要转换的多字节字符字符串位置的间接指针。

*计数*<br/>
要存储在*wcstr*缓冲区中的宽字符的最大数量，不包括终止 null 或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*mbstate*<br/>
指向**mbstate_t**转换状态对象的指针。 如果此值为 null 指针，则使用静态内部转换状态对象。 由于内部**mbstate_t**对象不是线程安全的，因此建议您始终传递自己的*mbstate*参数。

## <a name="return-value"></a>返回值

如果转换成功则返回零；如果失败则返回错误代码。

|添加状态|返回值和**errno**|
|---------------------|------------------------------|
|*wcstr*是 null 指针， *sizeInWords* > 0|**EINVAL**|
|*mbstr*是 null 指针|**EINVAL**|
|*Mbstr*间接指向的字符串包含一个对当前区域设置无效的多字节序列。|**EILSEQ**|
|目标缓冲区太小，无法包含转换后的字符串（除非 **_TRUNCATE**了*count* ; 有关详细信息，请参阅 "备注"）|**ERANGE**|

如果发生这些情况中的任何一个，都会调用无效的参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将返回错误代码并按表中所示设置**errno** 。

## <a name="remarks"></a>备注

**Mbsrtowcs_s**函数使用*mbstate*中包含的转换状态，将*mbstr*间接指向的多字节字符的字符串转换为存储在由*wcstr*指向的缓冲区中的宽字符。 在满足以下条件之一前，该转换将一直对每个字符执行：

- 遇到一个多字节空字符

- 遇到一个无效的多字节字符

- 存储在*wcstr*缓冲区中的宽字符数等于*count*。

目标字符串*wcstr*始终以 null 结尾（即使在发生错误的情况下），除非*wcstr*为 null 指针。

如果*count*是[_TRUNCATE](../../c-runtime-library/truncate.md)的特殊值，则**mbsrtowcs_s**会将尽可能多的字符串转换为目标缓冲区的大小，同时仍然为 null 终止符留下空间。

如果**mbsrtowcs_s**成功转换源字符串，则它会将转换后的字符串的宽字符和 null 终止符的大小放入 *&#42;pReturnValue*，前提是*pReturnValue*不是 null 指针。 即使*wcstr*参数是 null 指针，并允许你确定所需的缓冲区大小，也会发生这种情况。 请注意，如果*wcstr*为 null 指针，则忽略*count* 。

如果*wcstr*不是空指针，则在转换因到达终止 null 字符而停止时，将为*mbstr*指向的指针对象分配一个空指针。 否则，它将分配到紧跟已转换出的最后一个多字节字符的地址（若有）。 这将允许调用后续函数以在此调用停止的位置重新调用转换。

如果*mbstate*为 null 指针，则使用库内部**mbstate_t**转换状态静态对象。 由于此内部静态对象不是线程安全的，因此我们建议您传递自己的*mbstate*值。

如果**mbsrtowcs_s**遇到在当前区域设置中无效的多字节字符，它将在 *&#42;pReturnValue*中放置-1，将目标缓冲区*wcstr*设置为空字符串，将**Errno**设置为**eilseq 且**，并返回**eilseq 且**。

如果由*mbstr*和*wcstr*指向的序列重叠，则**mbsrtowcs_s**的行为是不确定的。 **mbsrtowcs_s**受当前区域设置的 LC_TYPE 类别的影响。

> [!IMPORTANT]
> 确保*wcstr*和*mbstr*不重叠，并且该*计数*正确反映了要转换的多字节字符的数量。

**Mbsrtowcs_s**函数不同于可重启性[_mbstowcs_s_l mbstowcs_s](mbstowcs-s-mbstowcs-s-l.md) 。 转换状态存储在*mbstate*中，以便后续调用相同的或其他可重启的函数。 混合使用可重启函数和不可重启函数时，结果不确定。 例如，如果使用了对**mbsrtowcs_s**的后续调用而不是**mbstowcs_s**，则应用程序应使用**mbsrlen**而不是**mbslen**。

在 C++ 中，模板重载简化了这些函数的使用；重载可以自动推导出缓冲区长度(不再需要指定大小自变量)，并且它们可以通过使用更新、更安全的对应函数来自动替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="exceptions"></a>例外

如果当前线程中的函数都不调用**setlocale** ，只要此函数正在执行并且*mbstate*参数不是 null 指针， **mbsrtowcs_s**函数就是多线程安全的。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**mbsrtowcs_s**|\<wchar.h>|

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[本地](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s、_mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
