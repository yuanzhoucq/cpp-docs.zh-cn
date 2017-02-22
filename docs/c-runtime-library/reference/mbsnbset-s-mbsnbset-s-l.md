---
title: "_mbsnbset_s、_mbsnbset_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsnbset_s_l"
  - "_mbsnbset_s"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "mbsnbset_s"
  - "_mbsnbset_s_l"
  - "_mbsnbset_s"
  - "mbsnbset_s_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsnbset_s 函数"
  - "_mbsnbset_s_l 函数"
  - "_tcsnset_s 函数"
  - "_tcsnset_s_l 函数"
  - "mbsnbset_s 函数"
  - "mbsnbset_s_l 函数"
  - "tcsnset_s 函数"
  - "tcsnset_s_l 函数"
ms.assetid: 811f92c9-cc31-4bbd-8017-2d1bfc6fb96f
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# _mbsnbset_s、_mbsnbset_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将一个多字节字符串的前 `n` 个字节设置为指定字符。  如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述，这些版本的 [\_mbsnbset、\_mbsnbset\_l](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md) 具有安全性增强功能。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/ZH-CN/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
errno_t _mbsnbset_s(  
   unsigned char *str,  
   size_t size,  
   unsigned int c,  
   size_t count   
);  
errno_t _mbsnbset_s_l(  
   unsigned char *str,  
   size_t size,  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t _mbsnbset_s(  
   unsigned char (&str)[size],  
   unsigned int c,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbsnbset_s_l(  
   unsigned char (&str)[size],  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 参数  
 `str`  
 要修改的字符串。  
  
 `size`  
 字符串缓冲区的大小。  
  
 `c`  
 单字节或多字节字符设置。  
  
 `count`  
 要设置的字节数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果成功，则为零；否则为错误代码。  
  
## 备注  
 `_mbsnbset_s` 和 `_mbsnbset_s_l` 函数最多将 `str` 的前 `count` 个字节设置为 `c`。  如果 `count` 大于 `str` 的长度，则会使用 `str` 的长度而使用 `count`。  如果 `c` 是多字节字符，且不能完全设置到由 `count` 指定的最后一个字节中，则用空白字符填充最后一个字节。  `_mbsnbset_s` 和 `_mbsnbset_s_l` 未在 `str` 的末尾放置终止 null。  
  
 `_mbsnbset_s` 和 `_mbsnbset_s_l` 类似于 `_mbsnset`，只不过它们设置 `c` 的 `count` 个字节而不是 `count` 个字符。  
  
 如果 `str` 为 `NULL` 或 `count` 为零，则此函数将生成无效参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且该函数将返回 `NULL`。  此外，如果 `c` 不是有效的多字节字符，则将 `errno` 设置为 `EINVAL`，并改用一个空格。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  此函数的 `_mbsnbset_s` 版本对与区域设置相关的行为使用当前区域设置，`_mbsnbset_s_l` 版本基本相同，但它改用传入的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，这些函数的使用由模板重载简化；重载可以自动推导出缓冲区长度，从而不再需要指定大小参数。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。  若要禁用此行为，请使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsnset_s`|`_strnset_s`|`_mbsnbset_s`|`_wcsnset_s`|  
|`_tcsnset_s_l`|`_strnset_s _l`|`_mbsnbset_s_l`|`_wcsnset_s_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mbsnbset_s`|\<mbstring.h\>|  
|`_mbsnbset_s_l`|\<mbstring.h\>|  
  
 有关更多兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_mbsnbset_s.c  
#include <mbstring.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[15] = "This is a test";  
   /* Set not more than 4 bytes of string to be *'s */  
   printf( "Before: %s\n", string );  
   _mbsnbset_s( string, sizeof(string), '*', 4 );  
   printf( "After:  %s\n", string );  
}  
```  
  
## 输出  
  **在此之前：这是一项测试**  
**在此之后：\*\*\*\* 是一项测试**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcat、\_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [\_strnset、\_strnset\_l、\_wcsnset、\_wcsnset\_l、\_mbsnset、\_mbsnset\_l](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)