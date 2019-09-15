---
title: mbrtowc
ms.date: 11/04/2016
api_name:
- mbrtowc
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
- mbrtowc
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
ms.openlocfilehash: b4c68ae8df9821d862b9f742d8a8ef7ace19c981
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952450"
---
# <a name="mbrtowc"></a>mbrtowc

将当前区域设置中的多字节字符转换为等效的宽字符，使其重启功能位于多字节字符的中间。

## <a name="syntax"></a>语法

```C
size_t mbrtowc(
   wchar_t *wchar,
   const char *mbchar,
   size_t count,
   mbstate_t *mbstate
);
```

### <a name="parameters"></a>参数

*wchar*<br/>
用于接收已转换的宽字符字符串（类型为**wchar_t**）的宽字符的地址。 如果不需要返回任何宽字符，则此值可为 null 指针。

*mbchar*<br/>
字节（多字节字符）序列的地址。

*count*<br/>
要检查的字节数。

*mbstate*<br/>
指向转换状态对象的指针。 如果此值为 null 指针，则函数使用静态的内部转换状态对象。 由于内部**mbstate_t**对象不是线程安全的，因此建议您始终传递您自己的*mbstate*参数。

## <a name="return-value"></a>返回值

以下值之一：

0如果*wchar*不是 null 指针，则下一个*计数*或更少的字节将填充表示 null 宽字符的多字节字符，该字符存储在*wchar*中。

1表示*计数*，不包括下一个*计数*或更少的字节完成有效的多字节字符。 返回的值是填充多字节字符的字节数。 如果*wchar*不是 null 指针，则等效的宽字符存储在*wchar*中。

（size_t）（-1）发生编码错误。 下一个*计数*或更少的字节不涉及完整且有效的多字节字符。 在这种情况下， **errno**设置为 eilseq 且，而*mbstate*中的转换移位状态为未指定。

（size_t）（-2）下一个*计数*字节导致了不完整但可能有效的多字节字符，并且已处理所有*计数*字节。 不会在*wchar*中存储任何值，但会更新*mbstate*以重新启动该函数。

## <a name="remarks"></a>备注

如果*mbchar*为 null 指针，则函数等效于调用：

`mbrtowc(NULL, "", 1, &mbstate)`

在这种情况下，将忽略*wchar*和*count*参数的值。

如果*mbchar*不是空指针，则该函数将检查来自*mbchar*的*计数*字节，以确定完成下一个多字节字符所需的字节数。 如果下一个字符是有效的，则相应的多字节字符将存储在*wchar*中（如果它不是空指针）。 如果字符为相应的宽 null 字符，则*mbstate*的生成状态是初始转换状态。

**Mbrtowc**函数的可重启性不同于[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md) 。 转换状态存储在*mbstate*中，以便后续调用相同的或其他可重启的函数。 混合使用可重启函数和不可重启函数时，结果不确定。  例如，如果使用对**wcsrtombs**的后续调用而不是**wcstombs**，应用程序应使用**wcsrlen**而不是**wcslen** 。

## <a name="example"></a>示例

将多字节字符转换为其等效的宽字符。

```cpp
// crt_mbrtowc.cpp

#include <stdio.h>
#include <mbctype.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

#define BUF_SIZE 100

int Sample(char* szIn, wchar_t* wcOut, int nMax)
{
    mbstate_t   state = {0}; // Initial state
    size_t      nConvResult,
                nmbLen = 0,
                nwcLen = 0;
    wchar_t*    wcCur = wcOut;
    wchar_t*    wcEnd = wcCur + nMax;
    const char* mbCur = szIn;
    const char* mbEnd = mbCur + strlen(mbCur) + 1;
    char*       szLocal;

    // Sets all locale to French_Canada.1252
    szLocal = setlocale(LC_ALL, "French_Canada.1252");
    if (!szLocal)
    {
        printf("The fuction setlocale(LC_ALL, \"French_Canada.1252\") failed!\n");
        return 1;
    }

    printf("Locale set to: \"%s\"\n", szLocal);

    // Sets the code page associated current locale's code page
    // from a previous call to setlocale.
    if (_setmbcp(_MB_CP_SBCS) == -1)
    {
        printf("The fuction _setmbcp(_MB_CP_SBCS) failed!");
        return 1;
    }

    while ((mbCur < mbEnd) && (wcCur < wcEnd))
    {
        //
        nConvResult = mbrtowc(wcCur, mbCur, 1, &state);
        switch (nConvResult)
        {
            case 0:
            {  // done
                printf("Conversion succeeded!\nMultibyte String: ");
                printf(szIn);
                printf("\nWC String: ");
                wprintf(wcOut);
                printf("\n");
                mbCur = mbEnd;
                break;
            }

            case -1:
            {  // encoding error
                printf("The call to mbrtowc has detected an encoding error.\n");
                mbCur = mbEnd;
                break;
            }

            case -2:
            {  // incomplete character
                if   (!mbsinit(&state))
                {
                    printf("Currently in middle of mb conversion, state = %x\n", state);
                    // state will contain data regarding lead byte of mb character
                }

                ++nmbLen;
                ++mbCur;
                break;
            }

            default:
            {
                if   (nConvResult > 2) // The multibyte should never be larger than 2
                {
                    printf("Error: The size of the converted multibyte is %d.\n", nConvResult);
                }

                ++nmbLen;
                ++nwcLen;
                ++wcCur;
                ++mbCur;
            break;
            }
        }
    }

   return 0;
}

int main(int argc, char* argv[])
{
    char    mbBuf[BUF_SIZE] = "AaBbCc\x9A\x8B\xE0\xEF\xF0xXyYzZ";
    wchar_t wcBuf[BUF_SIZE] = {L''};

    return Sample(mbBuf, wcBuf, BUF_SIZE);
}
```

### <a name="sample-output"></a>示例输出

```Output
Locale set to: "French_Canada.1252"
Conversion succeeded!
Multibyte String: AaBbCcÜïα∩≡xXyYzZ
WC String: AaBbCcÜïα∩≡xXyYzZ
```

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**mbrtowc**|\<wchar.h>|

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
