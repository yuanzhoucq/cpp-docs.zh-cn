---
title: wcsrtombs_s | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wcsrtombs_s
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
- wcsrtombs_s
dev_langs:
- C++
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94e27965d1660f4c344d0026bbfce8685a935c7a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417296"
---
# <a name="wcsrtombss"></a>wcsrtombs_s

将宽字符字符串转换为多字节字符串表示形式。 [wcsrtombs](wcsrtombs.md) 的一个版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>参数

*pReturnValue*<br/>
要转换的字符数。

*mbstr*<br/>
生成的已转换多字节字符字符串的缓冲区的地址。

*sizeInBytes*<br/>
以字节为单位的大小*mbstr*缓冲区。

*wcstr*<br/>
指向要转换的宽字符字符串的指针。

*count*<br/>
最大存储中的字节数*mbstr*缓冲区，或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*mbstate*<br/>
指向的指针**mbstate_t**转换状态对象。

## <a name="return-value"></a>返回值

如果成功，返回零；如果失败，则返回错误代码。

|错误条件|返回值和**errno**|
|---------------------|------------------------------|
|*mbstr*是**NULL**和*sizeInBytes* > 0|**EINVAL**|
|*wcstr*是**NULL**|**EINVAL**|
|目标缓冲区是太小，无法包含转换的字符串 (除非*计数*是 **_TRUNCATE**; 请参阅下面的备注)|**ERANGE**|

如果发生这些情况中的任何一个，都会调用无效参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，函数将返回错误代码和设置**errno**表中所示。

## <a name="remarks"></a>备注

**Wcsrtombs_s**函数将指向的宽字符字符串转换*wcstr*到存储指向的缓冲区中的多字节字符*mbstr*，使用中包含的转换状态*mbstate*。 在满足以下条件之一前，该转换将一直对每个字符执行：

- 遇到 null 宽字符

- 遇到无法转换的宽字符

- 存储中的字节数*mbstr*缓冲等于*计数*。

目标字符串始终以 null 结尾（即使在出错时）。

如果*计数*是特殊值[_TRUNCATE](../../c-runtime-library/truncate.md)，然后**wcsrtombs_s**将尽可能多的字符串作为将放入目标缓冲区中，同时仍保持 null 的空间终结器。

如果**wcsrtombs_s**成功转换了源字符串，它会将大小，以字节为单位的转换的字符串，包括 null 终止符，更改为 *&#42;pReturnValue* (提供*pReturnValue*不**NULL**)。 发生这种情况即使*mbstr*自变量是**NULL** ，并提供了一种方法来确定所需的缓冲区大小。 请注意，如果*mbstr*是**NULL**，*计数*将被忽略。

如果**wcsrtombs_s**遇到宽字符不能转换为多字节字符，它将为-1 放在 *\*pReturnValue*，将目标缓冲区设置为一个空字符串，设置**errno**到**EILSEQ**，并返回**EILSEQ**。

如果指向的序列*wcstr*和*mbstr*重叠的行为**wcsrtombs_s**是不确定的。 **wcsrtombs_s**受到当前区域设置中 LC_TYPE 类别。

> [!IMPORTANT]
> 确保*wcstr*和*mbstr*未重叠，且*计数*正确地反映了要转换的宽字符数。

**Wcsrtombs_s**函数不同于[wcstombs_s、 _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md)通过其可重启性。 转换状态存储在*mbstate*以便后续调用相同的或其他可重启函数。 混合使用可重启函数和不可重启函数时，结果不确定。 例如，应用程序将使用**wcsrlen**而非**wcslen**，如果的后续调用**wcsrtombs_s**而不是使用**wcstombs_s**.

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>异常

**Wcsrtombs_s**函数是多线程安全，前提是当前线程中的函数不调用**setlocale**时执行此函数和*mbstate*为 null。

## <a name="example"></a>示例

```cpp
// crt_wcsrtombs_s.cpp
//
// This code example converts a wide
// character string into a multibyte
// character string.
//

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

void main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    errno_t         err;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);
    if (err == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfully converted.\n" );
    }
}
```

```Output
The string was successfully converted.
```

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**wcsrtombs_s**|\<wchar.h>|

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
