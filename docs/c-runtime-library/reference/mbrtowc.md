---
title: mbrtowc | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- mbrtowc
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
- mbrtowc
dev_langs:
- C++
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 256c3df754607d0d9321f87d565e2ce94491035c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
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
若要接收已转换的宽字符字符串的宽字符的地址 (类型**wchar_t**)。 如果不需要返回任何宽字符，则此值可为 null 指针。

*mbchar*<br/>
字节（多字节字符）序列的地址。

*count*<br/>
要检查的字节数。

*mbstate*<br/>
指向转换状态对象的指针。 如果此值为 null 指针，则函数使用静态的内部转换状态对象。 因为内部**mbstate_t**对象不是线程安全，我们建议始终传递你自己*mbstate*自变量。

## <a name="return-value"></a>返回值

以下值之一：

0 下一步*计数*或更少字节将填充表示 null 宽字符，它存储在多字节字符*wchar*，如果*wchar*不是 null 指针。

1 到*计数*(含） 之间的下一步*计数*或更少的字节填充有效多字节字符。 返回的值是填充多字节字符的字节数。 等效的宽字符存储在*wchar*，如果*wchar*不是 null 指针。

(size_t)(-1)发生编码错误。 下一步*计数*或更少字节数不有利于实现完整且有效的多字节字符。 在这种情况下， **errno**设置为 EILSEQ 且中的转换位移状态*mbstate*未指定。

(size_t)(-2)下一步*计数*字节数有利于实现不完整但可能有效的多字节字符，并且所有*计数*已处理的字节数。 中存储任何值*wchar*，但*mbstate*被更新，以重新启动该函数。

## <a name="remarks"></a>备注

如果*mbchar*是 null 指针，该函数等效于调用：

`mbrtowc(NULL, "", 1, &mbstate)`

在此情况下，这些参数的值*wchar*和*计数*将被忽略。

如果*mbchar*不是 null 指针，该函数将检查*计数*个字节从*mbchar*以确定所需完成下一步所需的字节数多字节字符。 如果下一个字符是有效的将相应的多字节字符存储在*wchar*如果它不是 null 指针。 如果字符是相应的宽 null 字符，结果状态的*mbstate*是初始转换状态。

**Mbrtowc**函数不同于[mbtowc、 _mbtowc_l](mbtowc-mbtowc-l.md)通过其可重启性。 转换状态存储在*mbstate*以便后续调用相同的或其他可重启函数。 混合使用可重启函数和不可重启函数时，结果不确定。  例如，应用程序应使用**wcsrlen**而不是**wcslen**如果的后续调用**wcsrtombs**而不是使用**wcstombs**.

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

|例程|必需的标头|
|-------------|---------------------|
|**mbrtowc**|\<wchar.h>|

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
