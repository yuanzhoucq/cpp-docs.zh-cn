---
title: "_mbsnbset、_mbsnbset_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsnbset"
  - "_mbsnbset_l"
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
  - "mbsnbset"
  - "mbsnbset_l"
  - "_mbsnbset"
  - "_mbsnbset_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnbset 函数"
  - "_mbsnbset_l 函数"
  - "_tcsnset 函数"
  - "_tcsnset_l 函数"
  - "mbsnbset 函数"
  - "mbsnbset_l 函数"
  - "tcsnset 函数"
  - "tcsnset_l 函数"
ms.assetid: 8e46ef75-9a56-42d2-a522-a08450c67c19
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbsnbset、_mbsnbset_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置多字节字符字符串的第一个 `n` 字节到指定的字符。  有关这些函数的更多安全版本，请参见 [\_mbsnbset\_s、\_mbsnbset\_s\_l](../../c-runtime-library/reference/mbsnbset-s-mbsnbset-s-l.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
unsigned char *_mbsnbset(  
   unsigned char *str,  
   unsigned int c,  
   size_t count   
);  
unsigned char *_mbsnbset_l(  
   unsigned char *str,  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `str`  
 要修改的字符串。  
  
 `c`  
 单字节或多字节字符集。  
  
 `count`  
 要设置的字节数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 `_mbsnbset`返回指向修改后的字符串的指针。  
  
## 备注  
 `_mbsnbset` 和 `_mbsnbset_l` 函数设置，至多，`str` 的第一个 `count` 字节到 `c`。  如果 `count` 比 `str`的长度更长时，使用`str` 代替 `count`。  如果 `c` 是多字节字符，而且不能完全设置为 `count`指定的最后一个字节，最后一个字节填充空白字符。  `_mbsnbset` 和 `_mbsnbset_l`在 `str`的末尾放置一个终止 null 。  
  
 `_mbsnbset` 和 `_mbsnbset_l`类似于 `_mbsnset`，除此之外，设置 `count` 字节而不是 `c`的`count` 字符。  
  
 如果 `str` 是 `NULL` 或 `count` 为零，函数生成无效的参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回`NULL`。  此外，如果 `c` 不是有效的多字节字符，`errno` 设置为 `EINVAL`，并使用空格。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些带有 `_mbsnbset` 后缀的函数的版本为区域设置相关相关行为使用当前区域设置；带有`_mbsnbset_l` 版本的相同，只不过它们使用区域设置参数通过。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 **安全说明** 此 API 会导致由缓冲区溢出问题引起的潜在威胁。  缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsnset`|`_strnset`|`_mbsnbset`|`_wcsnset`|  
|`_tcsnset_l`|`_strnset_l`|`_mbsnbset_l`|`_wcsnset_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mbsnbset`|\<mbstring.h\>|  
|`_mbsnbset_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_mbsnbset.c  
// compile with: /W3  
#include <mbstring.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[15] = "This is a test";  
   /* Set not more than 4 bytes of string to be *'s */  
   printf( "Before: %s\n", string );  
   _mbsnbset( string, '*', 4 ); // C4996  
   // Note; _mbsnbset is deprecated; consider _mbsnbset_s  
   printf( "After:  %s\n", string );  
}  
```  
  
## Output  
  
```  
Before: This is a test  
After:  **** is a test  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcat、\_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [\_strnset、\_strnset\_l、\_wcsnset、\_wcsnset\_l、\_mbsnset、\_mbsnset\_l](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)