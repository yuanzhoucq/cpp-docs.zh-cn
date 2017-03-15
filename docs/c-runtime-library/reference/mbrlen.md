---
title: "mbrlen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "mbrlen"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "mbrlen"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mbrlen 函数"
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# mbrlen
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定填充当前区域设置中多字节字符所需的字节数，其中重启功能位于多字节字符的中间。  
  
## 语法  
  
```  
size_t mbrlen(  
   const char * str,  
   size_t count,  
   mbstate_t * mbstate  
);  
```  
  
#### 参数  
 `str`  
 指向多字节字符字符串中要检查的下一字节的指针。  
  
 `count`  
 要检查的最大字节数。  
  
 `mbstate`  
 指向 `str` 的初始字节当前移位状态的指针。  
  
## 返回值  
 以下值之一：  
  
 0  
 下一个 `count` 或更少字节将填充代表宽 null 字符的多字节字符。  
  
 1 到 `count`（含）  
 下一个 `count` 或更少的字节填充有效的多字节字符。  返回的值是填充多字节字符的字节数。  
  
 \(size\_t\)\(\-2\)  
 下一个 `count` 字节有利于实现不完整但可能有效的多字节字符，并且已处理所有 `count` 字节。  
  
 \(size\_t\)\(\-1\)  
 发生编码错误。  下一个 `count` 或更少字节数不有利于实现完整且有效的多字节字符。  在这种情况下，`errno` 设置为 EILSEQ 且未指定 `mbstate` 中的转换状态。  
  
## 备注  
 `mbrlen` 函数最多检查由 `count` 指向的字节开头的 `str` 个字节，以确定填充下一个多字节字符（包括任何位移序列）所需的字节数。  它等效于调用 `mbrtowc(NULL, str, count, &mbstate)`，其中 `mbstate` 为用户提供的 `mbstate_t` 对象或库提供的静态内部对象。  
  
 `mbrlen` 函数将保存并使用 `mbstate` 参数中不完整多字节字符的移位状态。  这赋予了 `mbrlen` 必要时在多字节字符中间重启的功能，从而最多检查 `count` 个字节。  如果 `mbstate` 为 null 指针，则 `mbrlen` 使用内部静态的 `mbstate_t` 对象来存储位移状态。  由于内部 `mbstate_t` 对象不是线程安全的，建议始终分配和传递你自己的 `mbstate` 参数。  
  
 `mbrlen` 函数的可重启性不同于 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)。  位移状态存储在 `mbstate` 中，以便后续调用相同函数或其他可重启函数。  混合使用可重启函数和不可重启函数时，结果不确定。  例如，如果使用 `wcsrlen`（而非 `wcslen`）的后续调用，则应用程序应使用 `wcsrtombs`，而不是 `wcstombs.`。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|不适用|不适用|`mbrlen`|不适用|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`mbrlen`|\<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 此示例演示了多字节字符的解释如何取决于当前代码页，并展示了 `mbrlen` 的恢复功能。  
  
```  
 // crt_mbrlen.c  
// Compile by using: cl crt_mbrlen.c  
#include <stdlib.h>  
#include <stdio.h>  
#include <string.h>  
#include <locale.h>  
#include <wchar.h>  
  
size_t Example(const char * pStr)  
{  
    size_t      charLen = 0;  
    size_t      charCount = 0;  
    mbstate_t   mbState = {0};  
  
    while ((charLen = mbrlen(pStr++, 1, &mbState)) != 0 &&  
            charLen != (size_t)-1)  
    {  
        if (charLen != (size_t)-2) // if complete mbcs char,  
        {  
            charCount++;  
        }  
    }   
    return (charCount);  
}   
  
int main( void )  
{  
    int         cp;  
    size_t      charCount = 0;  
    const char  *pSample =   
        "\x82\xD0\x82\xE7\x82\xAA\x82\xC8: Shift-jis hiragana.";  
  
    cp = _getmbcp();  
    charCount = Example(pSample);  
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",   
        cp, pSample, charCount);  
  
    setlocale(LC_ALL, "ja-JP"); // Set Japanese locale  
    _setmbcp(932); // and Japanese multibyte code page  
    cp = _getmbcp();  
    charCount = Example(pSample);  
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",   
        cp, pSample, charCount);  
}  
```  
  
  **代码页：0**  
**é╨éτé¬é╚: Shift\-jis hiragana.  字符计数：29**  
**代码页：932**  
**????: Shift\-jis hiragana.  字符计数：25**    
## .NET Framework 等效项  
 [System::String::Length](https://msdn.microsoft.com/en-us/library/system.string.length.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)