---
title: "_strlwr_s、_strlwr_s_l、_mbslwr_s、_mbslwr_s_l、_wcslwr_s、_wcslwr_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strlwr_s_l"
  - "_mbslwr_s_l"
  - "_mbslwr_s"
  - "_wcslwr_s"
  - "_strlwr_s"
  - "_wcslwr_s_l"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_strlwr_s_l"
  - "_strlwr_s"
  - "mbslwr_s_l"
  - "strlwr_s_l"
  - "_wcslwr_s"
  - "strlwr_s"
  - "mbslwr_s"
  - "_wcslwr_s_l"
  - "wcslwr_s_l"
  - "_tcslwr_s"
  - "_tcslwr_s_l"
  - "_mbslwr_s_l"
  - "wcslwr_s"
  - "_mbslwr_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbslwr_s 函数"
  - "_mbslwr_s_l 函数"
  - "_strlwr_s 函数"
  - "_strlwr_s_l 函数"
  - "_tcslwr_s 函数"
  - "_tcslwr_s_l 函数"
  - "_wcslwr_s 函数"
  - "_wcslwr_s_l 函数"
  - "大小写, 转换"
  - "转换大小写, CRT 函数"
  - "mbslwr_s 函数"
  - "mbslwr_s_l 函数"
  - "字符串转换 [C++], 大小写"
  - "字符串 [C++], 大小写"
  - "字符串 [C++], 转换大小写"
  - "strlwr_s 函数"
  - "strlwr_s_l 函数"
  - "tcslwr_s 函数"
  - "tcslwr_s_l 函数"
  - "wcslwr_s 函数"
  - "wcslwr_s_l 函数"
ms.assetid: 4883d31b-bdac-4049-83a1-91dfdeceee79
caps.latest.revision: 42
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 42
---
# _strlwr_s、_strlwr_s_l、_mbslwr_s、_mbslwr_s_l、_wcslwr_s、_wcslwr_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符串转换为小写，使用当前区域设置或传递的区域设置对象。  [\_strlwr、\_wcslwr、\_mbslwr、\_strlwr\_l、\_wcslwr\_l、\_mbslwr\_l](../../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md) 的这些版本如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
> [!IMPORTANT]
>  `_mbslwr_s` 和 `_mbslwr_s_l` 不能在 Windows 运行时执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
errno_t _strlwr_s(  
   char *str,  
   size_t numberOfElements  
);  
errno_t _strlwr_s_l(  
   char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
errno_t _mbslwr_s(  
   unsigned char *str,  
   size_t numberOfElements  
);  
errno_t _mbslwr_s_l(  
   unsigned char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
errno_t _wcslwr_s(  
   wchar_t *str,  
   size_t numberOfElements  
);  
errno_t _wcslwr_s_l(  
   wchar_t *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
template <size_t size>  
errno_t _strlwr_s(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _strlwr_s_l(  
   char (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t _mbslwr_s(  
   unsigned char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _mbslwr_s_l(  
   unsigned char (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t _wcslwr_s(  
   wchar_t (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _wcslwr_s_l(  
   wchar_t (&str)[size],  
   _locale_t locale  
); // C++ only  
```  
  
#### 参数  
 `str`  
 转换空终止字符串为小写。  
  
 `numberOfElements`  
 缓冲区的大小。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果成功，则为零；如果失败，则为非零错误代码。  
  
 这些函数验证其参数。  如果 `str` 不是有效的空终止字符串，调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则函数返回 `EINVAL` 并设置 `errno` 为 `EINVAL`。  如果 `numberOfElements` 比该字符串的长度短，函数仍然返回 `EINVAL` 并将 `errno` 设置到 `EINVAL`。  
  
## 备注  
 `_strlwr_s` 函数转换，例如，在 `str` 的所有大写字母转换为小写。  `_mbslwr_s` 是 `_strlwr_s`的多字节字符版本。`_wcslwr_s` 是 `_strlwr_s`的宽字符版本。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小参数\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。  若要禁用此行为，请使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcslwr_s`|`_strlwr_s`|`_mbslwr_s`|`_wcslwr_s`|  
|`_tcslwr_s_l`|`_strlwr_s_l`|`_mbslwr_s_l`|`_wcslwr_s_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strlwr_s`, `_strlwr_s_l`|\<string.h\>|  
|`_mbslwr_s`, `_mbslwr_s_l`|\<mbstring.h\>|  
|`_wcslwr_s`, `_wcslwr_s_l`|\<string.h\> 或 \<wchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strlwr_s.cpp  
// This program uses _strlwr_s and _strupr_s to create  
// uppercase and lowercase copies of a mixed-case string.  
//  
  
#include <string.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main()  
{  
   char str[] = "The String to End All Strings!";  
   char *copy1, *copy2;  
   errno_t err;  
  
   err = _strlwr_s( copy1 = _strdup(str), strlen(str) + 1);  
   err = _strupr_s( copy2 = _strdup(str), strlen(str) + 1);  
  
   printf( "Mixed: %s\n", str );  
   printf( "Lower: %s\n", copy1 );  
   printf( "Upper: %s\n", copy2 );  
  
   free( copy1 );  
   free( copy2 );  
  
   return 0;  
}  
```  
  
  **Mixed：所有字符串的结束字符串！**  
**Lower：所有字符串的结束字符串！**  
**Upper：所有字符串的结束字符串！**   
## .NET Framework 等效项  
 [System::String::ToLower](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_strupr\_s、\_strupr\_s\_l、\_mbsupr\_s、\_mbsupr\_s\_l、\_wcsupr\_s、\_wcsupr\_s\_l](../../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)