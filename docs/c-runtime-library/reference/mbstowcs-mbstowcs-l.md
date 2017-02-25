---
title: "mbstowcs、_mbstowcs_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "mbstowcs"
  - "_mbstowcs_l"
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
  - "mbstowcs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbstowcs_l 函数"
  - "mbstowcs 函数"
  - "mbstowcs_l 函数"
ms.assetid: 96696b27-e068-4eeb-8006-3f7a0546ae6d
caps.latest.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 30
---
# mbstowcs、_mbstowcs_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将多字节字符序列转换为对应的宽字符序列。  提供这些函数的更多安全版本；请参见 [mbstowcs\_s, \_mbstowcs\_s\_l](../../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)。  
  
## 语法  
  
```  
size_t mbstowcs(  
   wchar_t *wcstr,  
   const char *mbstr,  
   size_t count   
);  
size_t _mbstowcs_l(  
   wchar_t *wcstr,  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
size_t mbstowcs(  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count   
); // C++ only  
template <size_t size>  
size_t _mbstowcs_l(  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 参数  
 \[out\] `wcstr`  
 宽字节字符序列的地址。  
  
 \[in\] `mbstr`  
 多字节字符序列的空终止字符的地址。  
  
 \[in\] `count`  
 多字节的最大字符数来转换  
  
 \[in\] `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果 `mbstowcs` 成功转换源字符串，并返回转换的多字节字符。  如果 `wcstr` 参数为 `NULL`，则函数返回目标字符串\(宽字符\) 的需要的大小。  如果 `mbstowcs` 遇到无效的多字节字符，则返回 1。  如果返回值为 `count`，宽字符串不是以 null 结尾。  
  
> [!IMPORTANT]
>  确保 `wcstr` 和 `mbstr` 无重叠，并且`count` 恰好指出要转换的多字节字符的数量。  
  
## 备注  
 `mbstowcs` 函数将转换 `count` 的多字节字符的最大数到 `mbstr` 指向的当前区域设置适当取决于相应的宽字符的字符串。  在 `wcstr`表示形式的地址，它存储生成的宽字符串*。*结果类似于调用一系列 `mbtowc`。  如果遇到 `mbstowcs` 单字节 null 字符 \(“\\ 0 "\) 或之前，或者当 `count` 发生，它转换空字符为宽字符字符 \(L”\\ 0 "\) 和结束。  因此，只有在一个 null 遇到转换 `wcstr` 的宽字符字符串以 null 结尾。  如果由 `wcstr` 与 `mbstr` 指向的序列重叠，行为是未定义的。  
  
 如果 `wcstr` 参数为 `NULL`，则 `mbstowcs` 将返回由转换而来的宽字符数目，不包括 null 结束符。  源字符串必须以 null 结束，将返回正确的值。  如果需要生成的宽字符字符串以 Null 终止，请添加到返回的值。  
  
 如果 `mbstr` 的参数为 `NULL`，或 `count` 为 \> `INT_MAX`；调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则误差设置为 `EINVAL`，并函数返回 \-1。  
  
 `mbstowcs`使用相关行为的当前区域设置；和`_mbstowcs_l`  相同，但它将使用传递的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`mbstowcs`|\<stdlib.h\>|  
|`_mbstowcs_l`|\<stdlib.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_mbstowcs.c  
// compile with: /W3  
// illustrates the behavior of the mbstowcs function  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <locale.h>  
  
int main( void )  
{  
    size_t size;  
    int nChar = 2; // number of characters to convert  
    int requiredSize;  
  
    unsigned char    *pmbnull  = NULL;  
    unsigned char    *pmbhello = NULL;  
    char* localeInfo;  
  
    wchar_t *pwchello = L"\x3042\x3043"; // 2 Hiragana characters  
    wchar_t *pwc;  
  
    /* Enable the Japanese locale and codepage */  
    localeInfo = setlocale(LC_ALL, "Japanese_Japan.932");  
    printf("Locale information set to %s\n", localeInfo);  
  
    printf( "Convert to multibyte string:\n" );  
  
    requiredSize = wcstombs( NULL, pwchello, 0); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s  
    printf("  Required Size: %d\n", requiredSize);  
  
    /* Add one to leave room for the null terminator. */  
    pmbhello = (unsigned char *)malloc( requiredSize + 1);  
    if (! pmbhello)  
    {  
        printf("Memory allocation failure.\n");  
        return 1;  
    }  
    size = wcstombs( pmbhello, pwchello, requiredSize + 1); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s  
    if (size == (size_t) (-1))  
    {  
        printf("Couldn't convert string. Code page 932 may"  
                " not be available.\n");  
        return 1;  
    }  
    printf( "  Number of bytes written to multibyte string: %u\n",  
            (unsigned int) size );  
    printf( "  Hex values of the " );  
    printf( " multibyte characters: %#.2x %#.2x %#.2x %#.2x\n",  
            pmbhello[0], pmbhello[1], pmbhello[2], pmbhello[3] );  
    printf( "  Codepage 932 uses 0x81 to 0x9f as lead bytes.\n\n");  
  
    printf( "Convert back to wide-character string:\n" );  
  
    /* Assume we don't know the length of the multibyte string.  
     Get the required size in characters, and allocate enough space. */  
  
    requiredSize = mbstowcs(NULL, pmbhello, 0); // C4996  
    /* Add one to leave room for the NULL terminator */  
    pwc = (wchar_t *)malloc( (requiredSize + 1) * sizeof( wchar_t ));  
    if (! pwc)  
    {  
        printf("Memory allocation failure.\n");  
        return 1;  
    }  
    size = mbstowcs( pwc, pmbhello, requiredSize + 1); // C4996  
    if (size == (size_t) (-1))  
    {  
       printf("Couldn't convert string--invalid multibyte character.\n");  
    }  
    printf( "  Characters converted: %u\n", (unsigned int)size );  
    printf( "  Hex value of first 2" );  
    printf( " wide characters: %#.4x %#.4x\n\n", pwc[0], pwc[1] );  
    free(pwc);  
    free(pmbhello);  
}  
```  
  
  **区域信息设置为 Japanese\_Japan.932**  
**转换为多字节：**  
 **所需大小 大小:4**  
 **写入多字节字符字符串字节数：4**  
 **多字节字符的十六进制值：0x82 0xa0 0x82 0xa1**  
 **代码页932采用0X81到0x9F来作为前导字节。**  
**转换会宽字符字符串为:**  
 **已转换的字符：2**  
 **前 2 个宽字符的十六进制值：0x3042 0x3043**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)