---
title: "wcsrtombs | Microsoft Docs"
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
  - "wcsrtombs"
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
  - "wcsrtombs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "wcsrtombs 函数"
  - "字符串转换, 宽字符"
  - "宽字符, 字符串"
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
caps.latest.revision: 26
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wcsrtombs
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将宽字符字符串转换为多字节字符串表示形式。  提供该函数的一个更安全版本；请参阅 [wcsrtombs\_s](../../c-runtime-library/reference/wcsrtombs-s.md)。  
  
## 语法  
  
```  
size_t wcsrtombs(  
   char *mbstr,  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t wcsrtombs(  
   char (&mbstr)[size],  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### 参数  
 \[out\] `mbstr`  
 发生转换的多字符字符串的地址位置。  
  
 \[in\] `wcstr`  
 间接指向要转换的宽字节字符串的位置。  
  
 \[in\] `count`  
 要转换的字符数。  
  
 \[in\] `mbstate`  
 指向`mbstate_t`转换状态对象的指针。  
  
## 返回值  
 返回成功转换的字符的数量，不包括空终止空字符 \(如果有\)，否则如果发生错误 a \-1。  
  
## 备注  
 `wcsrtombs` 函数转换宽字节字符串，开始在 `mbstate`中指定的转换状态，从`wcstr`中间接指向的值，到 `mbstr`的地址。  每个字符的转换会继续直到：在遇到 null 终止的宽字节字符后，当遇到非相应的字符时，或者下一个字符将超出`count`包含的限制时。  如果 `wcsrtombs` 遇到空宽字符字符 \(L' \\ 0 '\) 或之前，或者当 `count` 发生，则将其转换为 8 位 0 并停止。  
  
 因此，只有在转换期间 `wcsrtombs` 遇到宽字节 null 字符，在 `mbstr` 的多字符字符串以 null 结尾。  如果由 `wcstr` 与 `mbstr` 指向的序列重叠，`wcsrtombs` 行为是未定义的。  `wcsrtombs` 受当前区域设置的 LC\_TYPE 类别的影响。  
  
 `wcsrtombs` 函数重启不同于 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md) 。  转换状态存储在 `mbstate` 随后调用相同或其他可重新启动的函数。  当混淆重启和非重启函数的使用时，则结果未定义。例如，如果随后调用 `wcsrtombs` 而不是 `wcstombs`，则应用程序应使用 `wcsrlen` 而不是 `wcsnlen`。  
  
 如果 `mbstr` 参数为 `NULL`，则 `wcsrtombs` 返回在目标字符串的字符串所需的大小。  如果 `mbstate` 为 null，则使用内部 `mbstate_t` 状态转换。  如果字符序列 `wchar` 没有一个对应的多字节字符形式，则返回 a\-1并且将`errno` 设置为 `EILSEQ`。  
  
 在 C\+\+ 中，该函数具有模板重载，以调用该函数的更新、更安全副本。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## 异常  
 `wcsrtombs` 函数是多线程安全的，只要当函数正在执行和 `mbstate` 为非空时，在当前线程中无函数调用 `setlocale`。  
  
## 示例  
  
```  
// crt_wcsrtombs.cpp  
// compile with: /W3  
// This code example converts a wide  
// character string into a multibyte  
// character string.  
  
#include <stdio.h>  
#include <memory.h>  
#include <wchar.h>  
#include <errno.h>  
  
#define MB_BUFFER_SIZE 100  
  
int main()  
{  
    const wchar_t   wcString[] =   
                    {L"Every good boy does fine."};  
    const wchar_t   *wcsIndirectString = wcString;  
    char            mbString[MB_BUFFER_SIZE];  
    size_t          countConverted;  
    mbstate_t       mbstate;  
  
    // Reset to initial shift state  
    ::memset((void*)&mbstate, 0, sizeof(mbstate));  
  
    countConverted = wcsrtombs(mbString, &wcsIndirectString,  
                               MB_BUFFER_SIZE, &mbstate); // C4996  
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s  
    if (errno == EILSEQ)  
    {  
        printf( "An encoding error was detected in the string.\n" );  
    }  
    else   
    {  
        printf( "The string was successfuly converted.\n" );  
    }  
}  
```  
  
  **字符串转换成功。**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`wcsrtombs`|\<wchar.h\>|  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb\_s](../../c-runtime-library/reference/wcrtomb-s.md)   
 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)