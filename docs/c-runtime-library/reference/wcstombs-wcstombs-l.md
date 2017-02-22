---
title: "wcstombs、_wcstombs_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wcstombs"
  - "_wcstombs_l"
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
  - "wcstombs"
  - "_wcstombs_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_wcstombs_l 函数"
  - "字符, 转换"
  - "字符串转换, 多字节字符串"
  - "字符串转换, 宽字符"
  - "wcstombs 函数"
  - "wcstombs_l 函数"
  - "宽字符, 转换"
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
caps.latest.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 30
---
# wcstombs、_wcstombs_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将多字节字符序列转换为对应的宽字符序列。  提供这些函数的更多安全版本；请参见 [wcstombs\_s、\_wcstombs\_s\_l](../../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)。  
  
## 语法  
  
```  
size_t wcstombs(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count   
);  
size_t _wcstombs_l(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
size_t wcstombs(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count   
); // C++ only  
template <size_t size>  
size_t _wcstombs_l(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 参数  
 `mbstr`  
 多字节字符序列的地址。  
  
 `wcstr`  
 宽字节字符序列的地址。  
  
 `count`  
 输出在多字节字符串可存储最大字节数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果 `wcstombs` 成功转换多字节字符串，则返回字节数写入输出的多字节字符串，包括终端 `NULL` （任何）。  如果 `mbstr` 参数为 `NULL`，则 `wcstombs` 返回在目标字符串的字符串所需的大小。  如果 `wcstombs` 遇到无法转换为多字节的宽字符，则返回 \-1 ，强制转换成`size_t` 并将 `errno` 设置为 `EILSEQ`。  
  
## 备注  
 `wcstombs` 函数将宽字符串通过 `wcstr` 指向一致的多字节字符并将结果存储在 `mbstr` 数组中。  `count` 参数即指示可以存储在输出的多字节字符串的最大字节数 \(即 `mbstr` 的大小\)。  通常，当转换字符串时不知道需要多少字节。  一些宽字符在输出字符串只需要一个字节；其他需要两个。  如果在输入字符串的每个宽字符有多字节输出字符串的两字节 \(包括 `NULL`\)，确保结果适应。  
  
 如果 `wcstombs` 遇到空宽字符字符 \(L' \\ 0 '\) 或之前，或者当 `count` 发生，则将其转换为 8 位 0 并停止。  因此，只有在转换期间 `wcstombs` 遇到宽字节 null 字符，在 `mbstr` 的多字符字符串以 null 结尾。  如果由 `wcstr` 与 `mbstr` 指向的序列重叠，`wcstombs` 行为是未定义的。  
  
 如果 `mbstr` 参数为 `NULL`，则 `wcstombs` 返回在目标字符串的字符串所需的大小。  
  
 `wcstombs`验证其参数。  如果 `wcstr` 为 `NULL`，或者如果 `count` 大于`INT_MAX`，此函数调用的参数无效处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL`并返回 \-1。  
  
 `wcstombs`使用区域设置相关行为的当前区域设置；和`_wcstombs_l` 相同，但它将使用传递的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`wcstombs`|\<stdlib.h\>|  
|`_wcstombs_l`|\<stdlib.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 此程序阐述 `wcstombs` 函数的行为。  
  
```  
// crt_wcstombs.c  
// compile with: /W3  
// This example demonstrates the use  
// of wcstombs, which converts a string  
// of wide characters to a string of   
// multibyte characters.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    size_t  count;  
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );  
    wchar_t *pWCBuffer = L"Hello, world.";  
  
    printf("Convert wide-character string:\n" );  
  
    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s instead  
    printf("   Characters converted: %u\n",  
            count );  
    printf("    Multibyte character: %s\n\n",  
           pMBBuffer );  
  
    free(pMBBuffer);  
}  
```  
  
  **转换宽字符字符串为：**  
 **已转换的字符：2**  
 **Multibyte 字符：Hello，world。**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs、\_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)