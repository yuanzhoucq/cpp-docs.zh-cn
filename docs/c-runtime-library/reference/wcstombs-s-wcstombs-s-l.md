---
title: wcstombs_s、_wcstombs_s_l
ms.date: 4/2/2020
api_name:
- _wcstombs_s_l
- wcstombs_s
- _o__wcstombs_s_l
- _o_wcstombs_s
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
- wcstombs_s
- _wcstombs_s_l
helpviewer_keywords:
- wcstombs_s function
- string conversion, wide characters
- wide characters, converting
- _wcstombs_s_l function
- wcstombs_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
ms.openlocfilehash: c20066cddb3f28d31d2964ec720b64ed49836f65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328050"
---
# <a name="wcstombs_s-_wcstombs_s_l"></a>wcstombs_s、_wcstombs_s_l

将宽字符序列转换为对应的多字节字符序列。 [wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md) 的一个版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t wcstombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count
);

errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);

template <size_t size>
errno_t wcstombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only

template <size_t size>
errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>参数

*p 返回值*<br/>
转换的字符串（包括空终止符）的大小（以字节为单位）。

*姆布斯特*<br/>
生成的已转换多字节字符字符串的缓冲区的地址。

*大小字节*<br/>
*mbstr*缓冲区的大小（以字节为单位）。

*wc斯特*<br/>
指向要转换的宽字符字符串的指针。

*count*<br/>
要存储在*mbstr*缓冲区中的最大字节数，不包括终止空字符，或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果成功，返回零；如果失败，则返回错误代码。

|添加状态|返回值和**差错**|
|---------------------|------------------------------|
|*mbstr*为**NULL，***大小为*> 0|**埃因瓦尔**|
|*wcstr*为**NULL**|**埃因瓦尔**|
|目标缓冲区太小，无法包含转换后的字符串（除非*计数***_TRUNCATE;** 请参阅下面的备注）|**ERANGE**|

如果发生这些情况中的任何一个，都会调用无效参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数将返回错误代码并设置表中指示的**errno。**

## <a name="remarks"></a>备注

**wcstombs_s**函数将*wcstr*指向的宽字符字符串转换为存储在*mbstr*指向的缓冲区中的多字节字符。 在满足以下条件之一前，该转换将一直对每个字符执行：

- 遇到 null 宽字符

- 遇到无法转换的宽字符

- 存储在*mbstr*缓冲区中的字节数等于*计数*。

目标字符串始终以 null 结尾（即使在出错时）。

如果*count*是[_TRUNCATE](../../c-runtime-library/truncate.md)的特殊值，则**wcstombs_s**转换尽可能多的字符串，以容纳到目标缓冲区中，同时仍为空终止符留出空间。 如果字符串被截断，则返回值为**STRUNCATE**，并且转换被视为成功。

如果**wcstombs_s**成功转换源字符串，它将转换后的字符串（包括空终止符）的大小放入 *&#42;pReturnValue（* 前提是*pReturnValue*不是**NULL）。** 即使*mbstr*参数为**NULL，** 并提供一种确定所需缓冲区大小的方法，也会发生这种情况。 请注意，如果*mbstr*为**NULL，** 则忽略*计数*。

如果**wcstombs_s**遇到一个宽字符，它不能转换为多字节字符，它会在 *&#42;pReturnValue*中放置 0，将目标缓冲区设置为空字符串，将**errno**设置到**EILSEQ，** 并返回**EILSEQ**。

如果*wcstr*和*mbstr*指向的序列重叠，**则wcstombs_s**的行为未定义。

> [!IMPORTANT]
> 确保*wcstr*和*mbstr*不重叠，并且*该计数*正确反映要转换的宽字符数。

**wcstombs_s**将当前区域设置用于任何与区域设置相关的行为;**_wcstombs_s_l**与**wcstombs**相同，只是它使用传入区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**wcstombs_s**|\<stdlib.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

此程序说明了**wcstombs_s**函数的行为。

```C
// crt_wcstombs_s.c
// This example converts a wide character
// string to a multibyte character string.
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t   i;
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t*pWCBuffer = L"Hello, world.";

    printf( "Convert wide-character string:\n" );

    // Conversion
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,
               pWCBuffer, (size_t)BUFFER_SIZE );

    // Output
    printf("   Characters converted: %u\n", i);
    printf("    Multibyte character: %s\n\n",
     pMBBuffer );

    // Free multibyte character buffer
    if (pMBBuffer)
    {
    free(pMBBuffer);
    }
}
```

```Output
Convert wide-character string:
   Characters converted: 14
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb_s、_wctomb_s_l](wctomb-s-wctomb-s-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
