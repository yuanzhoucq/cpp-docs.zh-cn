---
title: "wctob | Microsoft Docs"
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
  - "wctob"
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
  - "wctob"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "字符, 转换"
  - "wctob 函数"
  - "宽字符, 转换"
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
caps.latest.revision: 14
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wctob
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定宽字符是否对应于多字节字符并返回其多字节字符表示。  
  
## 语法  
  
```  
int wctob(  
   wint_t wchar  
);  
```  
  
#### 参数  
 `wchar`  
 要转换的值。  
  
## 返回值  
 如果 `wctob` 成功转换宽字符，则返回它的多字节字符表示，这仅在多字节字符长恰好为一个字节。  如果`wctob` 遇到宽字符字符，它无法转换为多字节字符或多字节字符不止一个字节，则返回 a\-1。  
  
## 备注  
 如果多字节字符长恰好为一个字节，`wctob` 函数通过返回 `int` 值，将`wchar` 包含的宽字符转换为传递的对应的多字节字符。  
  
 如果 `wctob` 不成功，并且对应的多字节字符未找到，函数将 `errno` 设置为 `EILSEQ` 并返回 \-1。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`wctob`|\<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 此程序阐述 `wcstombs` 函数的行为。  
  
```  
// crt_wctob.c  
#include <stdio.h>  
#include <wchar.h>  
  
int main( void )  
{  
    int     bChar = 0;  
    wint_t  wChar = 0;  
  
    // Set the corresponding wide character to exactly one byte.  
    wChar = (wint_t)'A';  
  
    bChar = wctob( wChar );  
    if (bChar == WEOF)  
    {  
        printf( "No corresponding multibyte character was found.\n");  
    }  
    else  
    {  
        printf( "Determined the corresponding multibyte character to"  
                " be \"%c\".\n", bChar);  
    }  
}  
  
```  
  
  **确定对应的多字节字符为“A”。**   
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