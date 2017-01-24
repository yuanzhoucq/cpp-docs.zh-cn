---
title: "wcrtomb_s | Microsoft Docs"
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
  - "wcrtomb_s"
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
  - "wcrtomb_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "将转换的宽字符"
  - "wcrtomb_s 函数"
  - "多字节字符"
  - "将转换的字符"
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wcrtomb_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将宽字符转换为它的多字节字符表示形式。 版本 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md) 因安全性增强中所述 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 语法  
  
```  
errno_t wcrtomb_s(  
   size_t *pReturnValue,  
   char *mbchar,  
   size_t sizeOfmbchar,  
   wchar_t *wchar,  
   mbstate_t *mbstate  
);  
template <size_t size>  
errno_t wcrtomb_s(  
   size_t *pReturnValue,  
   char (&mbchar)[size],  
   wchar_t *wchar,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### 参数  
 \[out\] `pReturnValue`  
 返回写入的字节数或\-1，如果发生了错误。  
  
 \[out\] `mbchar`  
 生成的多字节转换字符。  
  
 \[in\] `sizeOfmbchar`  
 大小 `mbchar` 变量以字节为单位。  
  
 \[in\] `wchar`  
 要转换的宽字符。  
  
 \[in\] `mbstate`  
 指向 `mbstate_t` 对象的指针。  
  
## 返回值  
 返回零或 `errno` 如果发生错误，则值。  
  
## 备注  
 `wcrtomb_s` 函数将转换的宽字符，从中包含的指定的转换状态开始 `mbstate`, 中, 包含的值从 `wchar`, ，放入所表示的地址 `mbchar`。`pReturnValue` 值将数目的字节转换，但不是能超过 `MB_CUR_MAX` 字节，否则为\-1 时出错。  
  
 如果 `mbstate` 为 null，内部 `mbstate_t` 使用转换状态。 如果该字符包含在 `wchar` 不具有相应的多字节字符，值 `pReturnValue` 将为\-1，则函数将返回 `errno` 值 `EILSEQ`。  
  
 `wcrtomb_s` 函数不同于 [wctomb\_s、\_wctomb\_s\_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md) 通过其可重启性。 转换状态存储在 `mbstate` 中，以便后续调用相同的或其他可重启函数。 混合使用可重启函数和不可重启函数时，结果不确定。 例如，应用程序将使用 `wcsrlen` 而不是 `wcslen`, ，如果对的后续调用 `wcsrtombs_s` 而不是使用了 `wcstombs_s.`  
  
 C \+ \+ 中使用此函数是由模板重载简化;重载可以自动推导出缓冲区长度 （不再需要指定大小参数），并且可以自动使用它们更新、 更安全的对应项替换较旧的、 不安全的函数。 有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## 异常  
 `wcrtomb_s` 函数是多线程安全，前提是当前线程中的函数不调用 `setlocale` 执行此函数时，使用与 `mbstate` 为 null。  
  
## 示例  
  
```  
// crt_wcrtomb_s.c  
// This program converts a wide character  
// to its corresponding multibyte character.  
//  
  
#include <string.h>  
#include <stdio.h>  
#include <wchar.h>  
  
int main( void )  
{  
    errno_t     returnValue;  
    size_t      pReturnValue;  
    mbstate_t   mbstate;  
    size_t      sizeOfmbStr = 1;  
    char        mbchar = 0;  
    wchar_t*    wchar = L"Q\0";  
  
    // Reset to initial conversion state  
    memset(&mbstate, 0, sizeof(mbstate));  
  
    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),  
                            *wchar, &mbstate);  
    if (returnValue == 0) {  
        printf("The corresponding wide character \"");  
        wprintf(L"%s\"", wchar);  
        printf(" was converted to a the \"%c\" ", mbchar);  
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
对应的宽字符"Q"已转换为"Q"的多字节字符。  
```  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`wcrtomb_s`|\<wchar.h\>|  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)