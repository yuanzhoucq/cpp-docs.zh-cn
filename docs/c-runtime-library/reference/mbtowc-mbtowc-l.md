---
title: "mbtowc、_mbtowc_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "mbtowc"
  - "_mbtowc_l"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "mbtowc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbtowc_l 函数"
  - "mbtowc 函数"
  - "mbtowc_l 函数"
ms.assetid: dfd1c8a7-e73a-4307-9353-53b70b45d4d1
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# mbtowc、_mbtowc_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将多字节字符转换为相应的宽字符  
  
## 语法  
  
```  
int mbtowc(  
   wchar_t *wchar,  
   const char *mbchar,  
   size_t count   
);  
int _mbtowc_l(  
   wchar_t *wchar,  
   const char *mbchar,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 参数  
 *wchar*  
 宽字符 \( `wchar_t`类型\) 的地址。  
  
 `mbchar`  
 多字节字符的字节序列的地址。  
  
 *count*  
 检查字节数。  
  
 *Locale — 区域设置*  
 要使用的区域设置。  
  
## 返回值  
 如果 **mbchar** 不为 **NULL**，并且，如果 `mbchar` 指向有效窗体的多字节字符的对象，`mbtowc` 在多字节字符的字节长度返回。  如果 `mbchar` 是 **NULL** 或它指向的对象是宽字符字符 \(L' \\ 0 '\) 中，函数返回 0。  如果 `mbchar` 所指向的对象不能构成在第一  字符内的有效字节字符， 返回– 1。  
  
## 备注  
 `mbtowc` 函数转换 *次数* 或低字节指向的 `mbchar`，因此，如果 `mbchar` 不为 **NULL**，则对相应的宽字符。  `mbtowc` 存储发生的宽字符在 *wchar，* 因此，如果 *wchar* 不是 **NULL**。  `mbtowc` 大于 `MB_CUR_MAX` 字节不检查更多。 `mbtowc` 为区域设置相关行为使用当前区域设置；`_mbtowc_l` 相同，但它将使用的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`mbtowc`|\<stdlib.h\>|  
|**\_mbtowc\_l**|\<stdlib.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_mbtowc.c  
/* Illustrates the behavior of the mbtowc function  
 */  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
    int      i;  
    char    *pmbc    = (char *)malloc( sizeof( char ) );  
    wchar_t  wc      = L'a';  
    wchar_t *pwcnull = NULL;  
    wchar_t *pwc     = (wchar_t *)malloc( sizeof( wchar_t ) );  
    printf( "Convert a wide character to multibyte character:\n" );  
    wctomb_s( &i, pmbc, sizeof(char), wc );  
    printf( "  Characters converted: %u\n", i );  
    printf( "  Multibyte character: %x\n\n", *pmbc );  
  
    printf( "Convert multibyte character back to a wide "  
            "character:\n" );  
    i = mbtowc( pwc, pmbc, MB_CUR_MAX );  
    printf( "  Bytes converted: %u\n", i );  
    printf( "  Wide character: %x\n\n", *pwc );  
    printf( "Attempt to convert when target is NULL\n" );  
    printf( "  returns the length of the multibyte character:\n" );  
    i = mbtowc( pwcnull, pmbc, MB_CUR_MAX );  
    printf( "  Length of multibyte character: %u\n\n", i );  
  
    printf( "Attempt to convert a NULL pointer to a" );  
    printf( " wide character:\n" );  
    pmbc = NULL;  
    i = mbtowc( pwc, pmbc, MB_CUR_MAX );  
    printf( "  Bytes converted: %u\n", i );  
}  
```  
  
## Output  
  
```  
Convert a wide character to multibyte character:  
  Characters converted: 1  
  Multibyte character: 61  
  
Convert multibyte character back to a wide character:  
  Bytes converted: 1  
  Wide character: 61  
  
Attempt to convert when target is NULL  
  returns the length of the multibyte character:  
  Length of multibyte character: 1  
  
Attempt to convert a NULL pointer to a wide character:  
  Bytes converted: 0  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)