---
title: "mbrtowc | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: de5737e8427d88b192d59291fc7b4805a7f6510b
ms.lasthandoff: 02/24/2017

---
# <a name="mbrtowc"></a>mbrtowc
将当前区域设置中的多字节字符转换为等效的宽字符，使其重启功能位于多字节字符的中间。  
  
## <a name="syntax"></a>语法  
  
```  
size_t mbrtowc(  
   wchar_t *wchar,  
   const char *mbchar,  
   size_t count,  
   mbstate_t *mbstate  
);  
```  
  
#### <a name="parameters"></a>参数  
 `wchar`  
 要接收已转换的宽字符字符串（类型 `wchar_t`)的宽字符的地址。 如果不需要返回任何宽字符，则此值可为 null 指针。  
  
 `mbchar`  
 字节（多字节字符）序列的地址。  
  
 `count`  
 要检查的字节数。  
  
 `mbstate`  
 指向转换状态对象的指针。 如果此值为 null 指针，则函数使用静态的内部转换状态对象。 由于内部 `mbstate_t` 对象不是线程安全的，建议始终传递你自己的 `mbstate` 参数。  
  
## <a name="return-value"></a>返回值  
 以下值之一：  
  
 0  
 如果 `count` 不是 null 指针，则下一个 `wchar` 或更少的字节将填充表示 null 宽字符的多字节字符，其中 null 宽字符存储在 `wchar` 中。  
  
 1 到 `count`（含）  
 下一个 `count` 或更少的字节填充有效的多字节字符。 返回的值是填充多字节字符的字节数。 如果 `wchar` 不是 null 指针，则等效的宽字符存储在 `wchar` 中。  
  
 (size_t)(-1)  
 发生编码错误。 下一个 `count` 或更少字节数不有利于实现完整且有效的多字节字符。 在这种情况下，`errno` 设置为 EILSEQ 且未指定 `mbstate` 中的转换位移状态。  
  
 (size_t)(-2)  
 下一个 `count` 字节填充有利于实现不完整但可能有效的多字节字符，并已处理了所有 `count` 字节数。 `wchar` 中未存储任何值，但已更新 `mbstate` 以重新启动该函数。  
  
## <a name="remarks"></a>备注  
 如果 `mbchar` 为 null 指针，则该函数等效于调用：  
  
 `mbrtowc(NULL, "", 1, &mbstate)`  
  
 在此情况下，将忽略参数 `wchar` 和 `count` 的值。  
  
 如果 `mbchar` 不是 null 指针，则该函数将检查来自 `count` 的 `mbchar` 字节以确定填充下一个多字节字符所需的字节数。 如果下一个字符是有效的，则相应的多字节字符在不是 null 指针时将存储在 `wchar` 中。 如果字符为相应的宽 null 字符，则 `mbstate` 结果状态是初始转换状态。  
  
 `mbrtowc` 函数的可重启性不同于 [mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)。 转换状态存储在 `mbstate` 中，以便后续调用相同的或其他可重启函数。 混合使用可重启函数和不可重启函数时，结果不确定。  例如，如果使用 `wcsrlen`（而非 `wcslen`）的后续调用，则应用程序应使用 `wcsrtombs`，而不是 `wcstombs`。  
  
## <a name="example"></a>示例  
 将多字节字符转换为其等效的宽字符。  
  
```  
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
  
## <a name="sample-output"></a>示例输出  
  
```  
Locale set to: "French_Canada.1252"  
Conversion succeeded!  
Multibyte String: AaBbCcÜïα∩≡xXyYzZ  
WC String: AaBbCcÜïα∩≡xXyYzZ  
```  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`mbrtowc`|\<wchar.h>|  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)
