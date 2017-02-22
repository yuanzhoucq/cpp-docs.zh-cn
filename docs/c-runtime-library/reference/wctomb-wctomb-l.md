---
title: "wctomb、_wctomb_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wctomb_l"
  - "wctomb"
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
  - "wctomb"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_wctomb_l 函数"
  - "字符, 转换"
  - "字符串转换, 多字节字符串"
  - "字符串转换, 宽字符"
  - "wctomb 函数"
  - "wctomb_l 函数"
  - "宽字符, 转换"
ms.assetid: 4a543f0e-5516-4d81-8ff2-3c5206f02ed5
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# wctomb、_wctomb_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将一个宽字符转换为相应的多字节字符。  提供这些函数的更多安全版本；请参见 [wctomb\_s、\_wctomb\_s\_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)。  
  
## 语法  
  
```  
int wctomb(  
   char *mbchar,  
   wchar_t wchar   
);  
int _wctomb_l(  
   char *mbchar,  
   wchar_t wchar,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `mbchar`  
 一个多字节字符的地址。  
  
 `wchar`  
 一个宽字符。  
  
## 返回值  
 如果 `wctomb` 将宽字符为多字节字符，则返回宽字符的字节数\(不超过`MB_CUR_MAX`\) 。  如果 `wchar` 是宽字符的空字符 \(L'\\0'\)，`wctomb` 返回 1。  如果目标指针`mbchar`是NULL，`wctomb` 返回 0。  如果当前区域设置不允许转换，`wctomb` 返回 \-1，并将`errno` 设置为 `EILSEQ`。  
  
## 备注  
 `wctomb` 函数将其 `wchar` 参数转换为对应的多字节字符并将结果存储在 `mbchar`。  在所有程序可以调用从任意点的函数。  `wctomb`使用区域设置相关行为的当前区域设置；`_wctomb_l`和 `wctomb`相同，但它将使用传递的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 `wctomb`验证其参数。  如果 `mbchar` 是 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回\-1。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`wctomb`|\<stdlib.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 此程序阐述wctomb函数的行为。  
  
```  
// crt_wctomb.cpp  
// compile with: /W3  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int i;  
   wchar_t wc = L'a';  
   char *pmb = (char *)malloc( MB_CUR_MAX );  
  
   printf( "Convert a wide character:\n" );  
   i = wctomb( pmb, wc ); // C4996  
   // Note: wctomb is deprecated; consider using wctomb_s  
   printf( "   Characters converted: %u\n", i );  
   printf( "   Multibyte character: %.1s\n\n", pmb );  
}  
```  
  
  **转换宽字符：**  
 **已转换的字符：1**  
 **多字节字符：a**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs、\_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)