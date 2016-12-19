---
title: "strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "strncpy"
  - "_strncpy_l"
  - "_mbsncpy"
  - "wcsncpy"
  - "_mbsncpy_l"
  - "_wcsncpy_l"
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
  - "_fstrncpy"
  - "strncpy"
  - "_ftcsncpy"
  - "_tcsnccpy_l"
  - "_tcsnccpy"
  - "_mbsncpy"
  - "wcsncpy"
  - "_tcsncpy"
  - "_strncpy_l"
  - "_mbsncpy_l"
  - "_wcsncpy_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fstrncpy 函数"
  - "_ftcsncpy 函数"
  - "_mbsncpy 函数"
  - "_mbsncpy_l 函数"
  - "_strncpy_l 函数"
  - "_tcsnccpy 函数"
  - "_tcsnccpy_l 函数"
  - "_tcsncpy 函数"
  - "_tcsncpy_l 函数"
  - "_wcsncpy_l 函数"
  - "字符 [C++], 复制"
  - "复制字符串的字符"
  - "fstrncpy 函数"
  - "ftcsncpy 函数"
  - "mbsncpy 函数"
  - "mbsncpy_l 函数"
  - "字符串 [C++], 复制"
  - "strncpy 函数"
  - "strncpy_l 函数"
  - "tcsnccpy 函数"
  - "tcsnccpy_l 函数"
  - "tcsncpy 函数"
  - "tcsncpy_l 函数"
  - "wcsncpy 函数"
  - "wcsncpy_l 函数"
ms.assetid: ac4345a1-a129-4f2f-bb8a-373ec58ab8b0
caps.latest.revision: 42
caps.handback.revision: 40
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将一个字符串的字符复制到另一个字符串。  这些函数的更安全版本可用；请参阅 [strncpy\_s、\_strncpy\_s\_l、wcsncpy\_s、\_wcsncpy\_s\_l、\_mbsncpy\_s、\_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)。  
  
> [!IMPORTANT]
>  `_mbsncpy` 和 `_mbsncpy_l` 无法用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/ZH-CN/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
char *strncpy(  
   char *strDest,  
   const char *strSource,  
   size_t count   
);  
char *_strncpy_l(  
   char *strDest,  
   const char *strSource,  
   size_t count,  
   locale_t locale   
);  
wchar_t *wcsncpy(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count   
);  
wchar_t *_wcsncpy_l(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count,  
   locale_t locale   
);  
unsigned char *_mbsncpy(  
   unsigned char *strDest,  
   const unsigned char *strSource,  
   size_t count   
);  
unsigned char *_mbsncpy_l(  
   unsigned char *strDest,  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
char *strncpy(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
char *_strncpy_l(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count,  
   locale_t locale   
); // C++ only  
template <size_t size>  
wchar_t *wcsncpy(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
wchar_t *_wcsncpy_l(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count,  
   locale_t locale   
); // C++ only  
template <size_t size>  
unsigned char *_mbsncpy(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
unsigned char *_mbsncpy_l(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 参数  
 `strDest`  
 目标字符串。  
  
 `strSource`  
 源字符串。  
  
 `count`  
 要复制的字符数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 返回 `strDest`。  没有保留任何返回值以指示错误。  
  
## 备注  
 `strncpy` 函数将 `count` 的初始 `strSource` 字符复制到 `strDest` 并返回 `strDest`。  如果 `count` 小于或等于 `strSource` 的长度，则将不会自动向复制的字符串追加 null 字符。  如果 `count` 大于 `strSource` 的长度，则目标字符串将用长度最长 `count` 的 null 字符填补。  如果源和目标字符串重叠，则 `strncpy` 的行为是未定义的。  
  
> [!IMPORTANT]
>  `strncpy` 将不检查 `strDest` 中空间是否足够；这将使其成为缓冲区溢出的一个可能的原因。  `count` 参数将限制复制的字符数；这不是 `strDest` 的大小限制。  请参见以下示例。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
 如果 `strDest` 或 `strSource` 是一个 `NULL` 指针, 或如果 `count` 小于或等于 0，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许继续执行，则这些函数返回 \-1 并将 `errno` 设置为 `EINVAL`  
  
 `wcsncpy` 和 `_mbsncpy` 分别是 `strncpy` 的宽字符及多字节字符版本。  `wcsncpy` 和 `_mbsncpy` 的参数和返回值将相应变化。  否则这六个函数具有相同行为。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递区域设置而不是其与区域设置相关的行为的当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsncpy`|`strncpy`|`_mbsnbcpy`|`wcsncpy`|  
|`_tcsncpy_l`|`_strncpy_l`|`_mbsnbcpy_l`|`_wcsncpy_l`|  
  
> [!NOTE]
>  `_strncpy_l` 和 `_wcsncpy_l` 没有区域设置依赖项，它们只是为了 `_tcsncpy_l` 提供的，不能直接调用。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strncpy`|\<string.h\>|  
|`wcsncpy`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsncpy`, `_mbsncpy_l`|\<mbstring.h\>|  
  
 有关其他平台兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 以下示例演示 `strncpy` 的使用以及使用不当将如何导致程序 Bug 和安全问题。  编译器将对每个 `strncpy` 调用生成类似下面这样的警告：**crt\_strncpy\_x86.c\(15\) : warning C4996: 'strncpy': This function or variable may be unsafe. Consider using strncpy\_s instead. To disable deprecation, use \_CRT\_SECURE\_NO\_WARNINGS. See online help for details.**  
  
```  
// crt_strncpy_x86.c  
// Use this command in an x86 developer command prompt to compile:   
// cl /TC /W3 crt_strncpy_x86.c  
  
#include <stdio.h>  
#include <string.h>  
  
int main() {  
   char t[20];  
   char s[20];  
   char *p = 0, *q = 0;  
  
   strcpy_s(s, sizeof(s), "AA BB CC");  
   // Note: strncpy is deprecated; consider using strncpy_s instead  
   strncpy(s, "aa", 2);     // "aa BB CC"         C4996  
   strncpy(s + 3, "bb", 2); // "aa bb CC"         C4996  
   strncpy(s, "ZZ", 3);     // "ZZ",              C4996  
                            // count greater than strSource, null added  
   printf("%s\n", s);  
  
   strcpy_s(s, sizeof(s), "AA BB CC");  
   p = strstr(s, "BB");  
   q = strstr(s, "CC");  
   strncpy(s, "aa", p - s - 1);   // "aa BB CC"   C4996  
   strncpy(p, "bb", q - p - 1);   // "aa bb CC"   C4996  
   strncpy(q, "cc",  q - s);      // "aa bb cc"   C4996  
   strncpy(q, "dd", strlen(q));   // "aa bb dd"   C4996  
   printf("%s\n", s);  
  
   // some problems with strncpy  
   strcpy_s(s, sizeof(s), "test");  
   strncpy(t, "this is a very long string", 20 ); // C4996  
   // Danger: at this point, t has no terminating null,  
   // so the printf continues until it runs into one.  
   // In this case, it will print "this is a very long test"  
   printf("%s\n", t);  
  
   strcpy_s(t, sizeof(t), "dogs like cats");  
   printf("%s\n", t);  
  
   strncpy(t + 10, "to chase cars.", 14); // C4996  
   printf("%s\n", t);  
  
   // strncpy has caused a buffer overrun and corrupted string s  
   printf("Buffer overrun: s = '%s' (should be 'test')\n", s);  
   // Since the stack grows from higher to lower addresses, buffer  
   // overruns can corrupt function return addresses on the stack,  
   // which can be exploited to run arbitrary code.  
}  
```  
  
 输出  
  
  **ZZ**  
**aa bb dd**  
**this is a very long test**  
**dogs like cats**  
**dogs like to chase cars.  Buffer overrun: s \= 'ars.' \(should be 'test'\)**  自动变量的布局和错误检测以及代码保护的级别可能随更改的编辑器设置而改变。  此示例在内置其他编译环境或使用其他编译器选项时可能会有不同的结果。  
  
## .NET Framework 等效项  
 [System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbsnbcpy、\_mbsnbcpy\_l](../../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)   
 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [strncpy\_s、\_strncpy\_s\_l、wcsncpy\_s、\_wcsncpy\_s\_l、\_mbsncpy\_s、\_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [strcpy\_s、wcscpy\_s、\_mbscpy\_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)