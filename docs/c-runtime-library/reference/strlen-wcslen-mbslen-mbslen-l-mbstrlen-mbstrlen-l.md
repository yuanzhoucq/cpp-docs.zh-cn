---
title: "strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbslen"
  - "_mbslen_l"
  - "_mbstrlen"
  - "wcslen"
  - "_mbstrlen_l"
  - "strlen"
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
  - "_mbstrlen"
  - "wcslen"
  - "_tcslen"
  - "_ftcslen"
  - "strlen"
  - "_mbslen"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcslen 函数"
  - "_mbslen 函数"
  - "_mbslen_l 函数"
  - "_mbstrlen 函数"
  - "_mbstrlen_l 函数"
  - "_tcslen 函数"
  - "ftcslen 函数"
  - "长度, 字符串"
  - "mbslen 函数"
  - "mbslen_l 函数"
  - "mbstrlen 函数"
  - "mbstrlen_l 函数"
  - "字符串长度, 获取"
  - "字符串 [C++], 获取长度"
  - "strlen 函数"
  - "tcslen 函数"
  - "wcslen 函数"
ms.assetid: 16462f2a-1e0f-4eb3-be55-bf1c83f374c2
caps.latest.revision: 32
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过使用当前区域设置或指定区域设置获取字符串的长度。  提供这些函数的更安全版本；请参阅 [strnlen、strnlen\_s、wcsnlen、wcsnlen\_s、\_mbsnlen、\_mbsnlen\_l、\_mbstrnlen、\_mbstrnlen\_l](../../c-runtime-library/reference/strnlen-strnlen-s.md)  
  
> [!IMPORTANT]
>  `_mbslen`、`_mbslen_l`、`_mbstrlen` 和 `_mbstrlen_l` 无法用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/zh-cn/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
size_t strlen(    const char *str ); size_t wcslen(    const wchar_t *str  ); size_t _mbslen(    const unsigned char *str  ); size_t _mbslen_l(    const unsigned char *str,    _locale_t locale ); size_t _mbstrlen(    const char *str ); size_t _mbstrlen_l(    const char *str,    _locale_t locale );  
```  
  
#### 参数  
 `str`  
 以 Null 结尾的字符串。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 其中每个函数都将返回 `str` 中的字符数，终止 `NULL` 除外。  不会保留返回值（`_mbstrlen` 和 `_mbstrlen_l` 除外）以指示错误，如果字符串包含无效的多字节字符，将返回 `((size_t)(-1))`。  
  
## 备注  
 `strlen` 会将字符串解释为单字节字符字符串，因此即使该字符串包含多字节字符，其返回值也始终等于字节数。  `wcslen` 是 `strlen` 的宽字符版本；`wcslen` 的参数是宽字符字符串且字符计数采用宽（双字节）字符。  除此以外，`wcslen` 和 `strlen` 的行为完全相同。  
  
 **安全说明**这些函数会引发由缓冲区溢出问题带来的潜在威胁。  缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcslen`|`strlen`|`strlen`|`wcslen`|  
|`_tcsclen`|`strlen`|`_mbslen`|`wcslen`|  
|`_tcsclen_l`|`strlen`|`_mbslen_l`|`wcslen`|  
  
 `_mbslen` 和 `_mbslen_l` 将返回一个多字节字符字符串中的多字节字符数，但它们不会测试多字节字符的有效性。  `_mbstrlen` 和 `_mbstrlen_l` 将测试多字节字符的有效性并识别多字节字符序列。  如果传递到 `_mbstrlen` 或 `_mbstrlen_l` 的字符串包含代码页中的无效多字节字符，则该函数将返回 \-1 并将 `errno` 设置为 `EILSEQ`。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参见[区域设置](../../c-runtime-library/locale.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strlen`|\<string.h\>|  
|`wcslen`|\<string.h\> 或 \<wchar.h\>|  
|`_mbslen`, `_mbslen_l`|\<mbstring.h\>|  
|`_mbstrlen`, `_mbstrlen_l`|\<stdlib.h\>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strlen.c  
// Determine the length of a string. For the multi-byte character  
// example to work correctly, the Japanese language support for  
// non-Unicode programs must be enabled by the operating system.  
  
#include <string.h>  
#include <locale.h>  
  
int main()  
{  
   char* str1 = "Count.";  
   wchar_t* wstr1 = L"Count.";  
   char * mbstr1;  
   char * locale_string;  
  
   // strlen gives the length of single-byte character string  
   printf("Length of '%s' : %d\n", str1, strlen(str1) );  
  
   // wstrlen gives the length of a wide character string  
   wprintf(L"Length of '%s' : %d\n", wstr1, wcslen(wstr1) );  
  
   // A multibyte string: [A] [B] [C] [katakana A] [D] [\0]  
   // in Code Page 932. For this example to work correctly,  
   // the Japanese language support must be enabled by the  
   // operating system.  
   mbstr1 = "ABC" "\x83\x40" "D";  
  
   locale_string = setlocale(LC_CTYPE, "Japanese_Japan");  
  
   if (locale_string == NULL)  
   {  
      printf("Japanese locale not enabled. Exiting.\n");  
      exit(1);  
   }  
   else  
   {  
      printf("Locale set to %s\n", locale_string);  
   }  
  
   // _mbslen will recognize the Japanese multibyte character if the  
   // current locale used by the operating system is Japanese  
   printf("Length of '%s' : %d\n", mbstr1, _mbslen(mbstr1) );  
  
   // _mbstrlen will recognize the Japanese multibyte character  
   // since the CRT locale is set to Japanese even if the OS locale  
   // isnot.   
   printf("Length of '%s' : %d\n", mbstr1, _mbstrlen(mbstr1) );  
   printf("Bytes in '%s' : %d\n", mbstr1, strlen(mbstr1) );     
  
}  
```  
  
  **“Count”的长度。 : 6**  
**“Count”的长度。 : 6**  
**“ABCァD”的长度：5**  
**“ABCァD”的长度：5**  
**“ABCァD”中的字节：6**   
## .NET Framework 等效项  
 [System::String::Length](https://msdn.microsoft.com/en-us/library/system.string.length.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)