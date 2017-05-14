---
title: "wcrtomb | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcrtomb
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
- wcrtomb
dev_langs:
- C++
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
caps.latest.revision: 26
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 599802a3038305dd09fafb4b6fb278d05c13afa4
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="wcrtomb"></a>wcrtomb
将宽字符转换为多字节字符表示形式。 此函数有一个更安全的版本；请参阅 [wcrtomb_s](../../c-runtime-library/reference/wcrtomb-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
size_t wcrtomb(  
   char *mbchar,  
   wchar_t wchar,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t wcrtomb(  
   char (&mbchar)[size],  
   wchar_t wchar,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 [out] `mbchar`  
 生成的多字节转换字符。  
  
 [in] `wchar`  
 要转换的宽字符。  
  
 [in] `mbstate`  
 指向 `mbstate_t` 对象的指针。  
  
## <a name="return-value"></a>返回值  
 返回表示已转换多字节字符所需的字节数，如果发生错误则为 -1。  
  
## <a name="remarks"></a>备注  
 从 `mbstate` 中包含的指定转换状态开始，`wcrtomb` 函数将 `wchar` 的宽字符值转换为 `mbchar` 表示的地址。 返回值为表示相应多字节字符所需的字节数，但该返回值不会超过 `MB_CUR_MAX` 字节。  
  
 如果 `mbstate` 为 null，则会使用包含 `mbchar` 转换状态的内部 `mbstate_t` 对象。 如果字符序列 `wchar` 不具有相应的多字节字符表示形式，则返回 -1 且将 `errno` 设置为 `EILSEQ`。  
  
 `wcrtomb` 函数的可重启性不同于 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)。 转换状态存储在 `mbstate` 中，以便后续调用相同的或其他可重启函数。 混合使用可重启函数和不可重启函数时，结果不确定。 例如，如果使用 `wcsrlen`（而非 `wcsnlen`）的后续调用，则应用程序应使用 `wcsrtombs`，而非 `wcstombs`。  
  
 在 C++ 中，此函数具有一个调用此函数的更新、更安全副本的模板重载。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="exceptions"></a>异常  
 只要当前线程中的函数都不调用 `setlocale`、此函数正在执行且 `mbstate` 是 null，`wcrtomb` 函数就是多线程安全的。  
  
## <a name="example"></a>示例  
  
```  
// crt_wcrtomb.c  
// compile with: /W3  
// This program converts a wide character  
// to its corresponding multibyte character.  
  
#include <string.h>  
#include <stdio.h>  
#include <wchar.h>  
  
int main( void )  
{  
    size_t      sizeOfCovertion = 0;  
    mbstate_t   mbstate;  
    char        mbStr = 0;  
    wchar_t*    wcStr = L"Q";  
  
    // Reset to initial conversion state  
    memset(&mbstate, 0, sizeof(mbstate));  
  
    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996  
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead  
    if (sizeOfCovertion > 0)  
    {  
        printf("The corresponding wide character \"");  
        wprintf(L"%s\"", wcStr);  
        printf(" was converted to the \"%c\" ", mbStr);  
        printf("multibyte character.\n");  
    }  
    else  
    {  
        printf("No corresponding multibyte character "  
               "was found.\n");  
    }  
}  
```  
  
```Output  
The corresponding wide character "Q" was converted to the "Q" multibyte character.  
```  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`wcrtomb`|\<wchar.h>|  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)
