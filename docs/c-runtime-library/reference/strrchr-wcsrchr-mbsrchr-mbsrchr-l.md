---
title: "strrchr、wcsrchr、_mbsrchr、_mbsrchr_l | Microsoft Docs"
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
  - "strrchr"
  - "wcsrchr"
  - "_mbsrchr"
  - "_mbsrchr_l"
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
  - "_tcsrchr"
  - "_ftcsrchr"
  - "strrchr"
  - "wcsrchr"
  - "_mbsrchr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsrchr 函数"
  - "_mbsrchr 函数"
  - "_mbsrchr_l 函数"
  - "_tcsrchr 函数"
  - "字符 [C++], 扫描"
  - "ftcsrchr 函数"
  - "mbsrchr 函数"
  - "mbsrchr_l 函数"
  - "扫描字符串"
  - "字符串 [C++], 扫描"
  - "strrchr 函数"
  - "tcsrchr 函数"
  - "wcsrchr 函数"
ms.assetid: 75cf2664-758e-49bb-bf6b-8a139cd474d2
caps.latest.revision: 28
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strrchr、wcsrchr、_mbsrchr、_mbsrchr_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

浏览一个字符串字符最后出现的位置。  
  
> [!IMPORTANT]
>  `_mbsrchr` 和 `_mbsrchr_l` 不能在 Windows 运行时执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
char *strrchr(  
   const char *str,  
   int c   
); // C only  
char *strrchr(  
   char *str,  
   int c   
); // C++ only  
const char *strrchr(  
   const char *str,  
   int c   
); // C++ only  
wchar_t *wcsrchr(  
   const wchar_t *str,  
   wchar_t c   
); // C only  
wchar_t *wcsrchr(  
   wchar_t *str,  
   wchar_t c   
); // C++ only  
const wchar_t *wcsrchr(  
   const wchar_t *str,  
   wchar_t c   
); // C++ only  
unsigned char *_mbsrchr(  
   const unsigned char *str,  
   unsigned int c   
); // C only  
unsigned char *_mbsrchr(  
   unsigned char *str,  
   unsigned int c   
); // C++ only  
const unsigned char *_mbsrchr(  
   const unsigned char *str,  
   unsigned int c   
); // C++ only  
unsigned char *_mbsrchr_l(  
   const unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C only  
unsigned char *_mbsrchr_l(  
   unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C++ only  
const unsigned char *_mbsrchr_l(  
   const unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C++ only  
```  
  
#### 参数  
 `str`  
 要搜索的 null 终止的字符串。  
  
 `c`  
 要定位的字符。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果`c`找不到，则返回在 `str`或 `NULL` 中最后指向`c` 的指针。  
  
## 备注  
 `strrchr` 函数在 `str`中查找最后出现 的 `c` \(转换为 `char`\) 。  搜索包括终止 null 字符\)。  
  
 `wcsrchr` 和 `_mbsrchr` 是宽字符，属于 `strrchr` 的多节字字符版本。  参数和 `wcsrchr`  的返回值是宽字符字符串；`_mbsrchr` 的参数和返回值为多字节字符字符串。  
  
 在 C 中，这些函数采用第一个参数的一个 `const` 指针。  在 C\+\+ 中，有两个重载可用。  采用指向 `const` 的指针的重载返回指向 `const` 的指针；采用指向非`const` 的版本的指针返回指向非`const` 的指针。  如果这些函数的 `const` 和非`const` 版本可用，则会定义宏 \_CONST\_CORRECT\_OVERLOADS。  如果这两个 C\+\+ 重载都需要非 `const` 行为，请定义符号 \_CONST\_RETURN。  
  
 `_mbsrchr`验证其参数。  如果 `str` 是 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许继续执行，将`errno`  设置为 `EINVAL`  并且 `_mbsrchr`  返回0 。  `strrchr` 和 `wcsrchr` 不验证其参数。  否则这三个函数否则具有相同行为。  
  
 输出值受区域设置的 `LC_CTYPE`  类别设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsrchr`|`strrchr`|`_mbsrchr`|`wcsrchr`|  
|**无**|**无**|`_mbsrchr_l`|**无**|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strrchr`|\<string.h\>|  
|`wcsrchr`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsrchr`, `_mbsrchr_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 有关使用 `strrchr` 的示例，请参见 [strchr](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)。  
  
## .NET Framework 等效项  
 [System::String::LastIndexOf](https://msdn.microsoft.com/en-us/library/system.string.lastindexof.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strchr、wcschr、\_mbschr、\_mbschr\_l](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)   
 [strcspn、wcscspn、\_mbscspn、\_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strpbrk、wcspbrk、\_mbspbrk、\_mbspbrk\_l](../../c-runtime-library/reference/strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)