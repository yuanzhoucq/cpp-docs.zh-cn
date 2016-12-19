---
title: "wcrtomb | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wcrtomb"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wcrtomb"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "字符, 转换"
  - "多字节字符"
  - "wcrtomb 函数"
  - "宽字符, 转换"
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
caps.latest.revision: 26
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wcrtomb
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将宽字符转换为它的多字节字符形式。  提供该函数的一个更安全版本；请参阅 [wcrtomb\_s](../../c-runtime-library/reference/wcrtomb-s.md)。  
  
## 语法  
  
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
  
#### 参数  
 \[out\] `mbchar`  
 生成的多字节转换字符。  
  
 \[in\] `wchar`  
 要转换的宽字符。  
  
 \[in\] `mbstate`  
 指向 `mbstate_t` 对象的指针。  
  
## 返回值  
 返回需要的字节数表示转换的多字节字符，否则如果出错返回a\-1。  
  
## 备注  
 `wcrtomb` 函数将一个宽字符转换为，在特定转换状态开始，包括`mbstate`，从在 `wchar` 包括的值，到通过 `mbchar` 地址形式。  返回值是表示对应的多字节字符所需的字节数，但是它不会返回大于 `MB_CUR_MAX` 的。  
  
 如果 `mbstate` 为 null，则使用包含 `mbchar` 转换状态的内部 `mbstate_t` 对象。  如果字符序列 `wchar` 没有一个对应的多字节字符形式，则返回 a\-1并且将`errno` 设置为 `EILSEQ`。  
  
 `wcrtomb` 函数重启不同于 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md) 。  转换状态存储在 `mbstate` 随后调用相同或其他可重新启动的函数。  当混淆重启和非重启函数的使用时，则结果未定义。  例如，如果随后调用 `wcsrtombs` 而不是 `wcstombs`，则应用程序应使用 `wcsrlen` 而不是 `wcsnlen`。  
  
 在 C\+\+ 中，该函数具有模板重载，以调用该函数的更新、更安全副本。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## 异常  
 `wcrtomb` 函数是多线程安全的，只要当函数正在执行和 `mbstate` 为空时，在当前线程中无函数调用 `setlocale`。  
  
## 示例  
  
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
  
  **相应的宽字符 “Q” 被转换到 ”Q “ 多字节字符。**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`wcrtomb`|\<wchar.h\>|  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)