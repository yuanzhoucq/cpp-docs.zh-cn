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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: 62ae534e8080b74ada49cca005811a049055cb65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338903"
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

*p 返回值*<br/>
要转换的字符数。

*wc斯特*<br/>
用于存储转换所生成的宽字符字符串的缓冲区地址。

*大小字内*<br/>
单词中*wcstr*的大小（宽字符）。

*姆布斯特*<br/>
指向要转换的多字节字符字符串位置的间接指针。

*count*<br/>
要存储在*wcstr*缓冲区中的最大宽字符数，不包括终止 null 或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*mbstate*<br/>
指向**mbstate_t**转换状态对象的指针。 如果此值为 null 指针，则使用静态内部转换状态对象。 由于内部**mbstate_t**对象不是线程安全的，因此我们建议您始终传递自己的*mbstate*参数。

## <a name="return-value"></a>返回值

如果转换成功则返回零；如果失败则返回错误代码。

|添加状态|返回值和**差错**|
|---------------------|------------------------------|
|*wcstr*是一个空指针，*大小 InWords* > 0|**埃因瓦尔**|
|*mbstr*是空指针|**埃因瓦尔**|
|*mbstr*间接指向的字符串包含一个对当前区域设置无效的多字节序列。|**EILSEQ**|
|目标缓冲区太小，无法包含转换后的字符串（除非*计数***_TRUNCATE;** 有关详细信息，请参阅备注）|**ERANGE**|

如果发生这些情况中的任何一个，都会调用无效的参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数将返回错误代码并设置表中指示的**errno。**

## <a name="remarks"></a>备注

**mbsrtowcs_s**函数通过使用*mbstate*中包含的转换状态，将*mbstr*间接指向的多字节字符字符串转换为存储在*wcstr*指向的缓冲区中的宽字符。 在满足以下条件之一前，该转换将一直对每个字符执行：

- 遇到一个多字节空字符

- 遇到一个无效的多字节字符

- 存储在*wcstr*缓冲区中的宽字符数等于*计数*。

目标字符串*wcstr*始终为 null 终止，即使在出现错误的情况下也是如此，除非*wcstr*是空指针。

如果*count*是[_TRUNCATE](../../c-runtime-library/truncate.md)的特殊值 **，mbsrtowcs_s**转换尽可能多的字符串，以适应目标缓冲区，同时仍然留有空终止符的空间。

如果**mbsrtowcs_s**成功转换源字符串，它将大小以转换后的字符串和空终止符的宽字符形式放入 *&#42;pReturnValue，* 前提是*pReturnValue*不是空指针。 即使*wcstr*参数是空指针，并允许您确定所需的缓冲区大小，也会发生这种情况。 请注意，如果*wcstr*是空指针，则*忽略计数*。

如果*wcstr*不是空指针，则如果由于达到终止空字符而停止转换，则*mbstr*指向的指针对象将分配一个空指针。 否则，它将分配到紧跟已转换出的最后一个多字节字符的地址（若有）。 这将允许调用后续函数以在此调用停止的位置重新调用转换。

如果*mbstate*是空指针，则使用库内部**mbstate_t**转换状态静态对象。 由于此内部静态对象不是线程安全的，因此我们建议您传递自己的*mbstate*值。

如果**mbsrtowcs_s**遇到在当前区域设置中无效的多字节字符，它将在 *&#42;pReturnValue*中放入 -1，将目标缓冲区*wcstr*设置为空字符串，将**errno**设置到**EILSEQ，** 然后返回**EILSEQ**。

如果*mbstr*和*wcstr*指向的序列重叠，则**mbsrtowcs_s**的行为未定义。 **mbsrtowcs_s**受当前区域设置的LC_TYPE类别的影响。

> [!IMPORTANT]
> 确保*wcstr*和*mbstr*不重叠，并且*该计数*正确反映要转换的多字节字符数。

**mbsrtowcs_s**功能不同于[mbstowcs_s，_mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)它的可重新启动性。 转换状态以*mbstate*存储，用于后续对相同或其他可重新启动函数的调用。 混合使用可重启函数和不可重启函数时，结果不确定。 例如，如果使用后续对**mbsrtowcs_s**的调用而不是**mbstowcs_s**，则应用程序应使用**mbsrlen**而不是**mbslen。**

在 C++ 中，模板重载简化了这些函数的使用；重载可以自动推导出缓冲区长度(不再需要指定大小自变量)，并且它们可以通过使用更新、更安全的对应函数来自动替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="exceptions"></a>例外

如果当前线程调用**setlocale**中没有函数，只要此函数正在执行并且*mbstate*参数不是空指针，则**mbsrtowcs_s**函数是多线程安全的。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**mbsrtowcs_s**|\<wchar.h>|

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s、_mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
