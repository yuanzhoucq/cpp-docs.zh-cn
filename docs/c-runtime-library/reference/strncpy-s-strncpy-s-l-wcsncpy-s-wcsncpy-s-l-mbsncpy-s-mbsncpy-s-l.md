---
title: "strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l | Microsoft Docs"
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
  - "_mbsncpy_s_l"
  - "wcsncpy_s"
  - "_strncpy_s_l"
  - "strncpy_s"
  - "_mbsncpy_s"
  - "_wcsncpy_s_l"
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
  - "_tcsncpy_s"
  - "_wcsncpy_s_l"
  - "strncpy_s"
  - "_strncpy_s_l"
  - "wcsncpy_s"
  - "_tcsncpy_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnbcpy_s 函数"
  - "_mbsnbcpy_s_l 函数"
  - "_strncpy_s_l 函数"
  - "_tcsncpy_s 函数"
  - "_tcsncpy_s_l 函数"
  - "_wcsncpy_s_l 函数"
  - "复制字符串"
  - "mbsncpy_s 函数"
  - "mbsncpy_s_l 函数"
  - "字符串 [C++], 复制"
  - "strncpy_s 函数"
  - "strncpy_s_l 函数"
  - "wcsncpy_s 函数"
  - "wcsncpy_s_l 函数"
ms.assetid: a971c800-94d1-4d88-92f3-a2fe236a4546
caps.latest.revision: 47
caps.handback.revision: 45
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将一个字符串的字符复制给另一个。[strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md) 的这些版本如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
> [!IMPORTANT]
>  `_mbsncpy_s` 和 `_mbsncpy_s_l` 不能在 Windows 运行时中执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
errno_t strncpy_s(  
   char *strDest,  
   size_t numberOfElements,  
   const char *strSource,  
   size_t count  
);  
errno_t _strncpy_s_l(  
   char *strDest,  
   size_t numberOfElements,  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
);  
errno_t wcsncpy_s(  
   wchar_t *strDest,  
   size_t numberOfElements,  
   const wchar_t *strSource,  
   size_t count   
);  
errno_t _wcsncpy_s_l(  
   wchar_t *strDest,  
   size_t numberOfElements,  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
);  
errno_t _mbsncpy_s(  
   unsigned char *strDest,  
   size_t numberOfElements,  
   const unsigned char *strSource,  
   size_t count   
);  
errno_t _mbsncpy_s_l(  
   unsigned char *strDest,  
   size_t numberOfElements,  
   const unsigned char *strSource,  
   size_t count,  
   locale_t locale  
);  
template <size_t size>  
errno_t strncpy_s(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count  
); // C++ only  
template <size_t size>  
errno_t _strncpy_s_l(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t wcsncpy_s(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _wcsncpy_s_l(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t _mbsncpy_s(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbsncpy_s_l(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count,  
   locale_t locale  
); // C++ only  
```  
  
#### 参数  
 `strDest`  
 目标字符串。  
  
 `numberOfElements`  
 目标字符串中的字符数。  
  
 `strSource`  
 源字符串。  
  
 `count`  
 要复制的字符数，或者[\_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果成功则为零，如果截断事件发生，则`STRUNCATE`，否则为错误代码。  
  
### 错误情况  
  
|`strDest`|`numberOfElements`|`strSource`|返回值|`strDest` 的内容|  
|---------------|------------------------|-----------------|---------|-------------------|  
|`NULL`|any|any|`EINVAL`|未修改|  
|any|any|`NULL`|`EINVAL`|`strDest`\[0\] 设置为 0|  
|any|0|any|`EINVAL`|未修改|  
|not `NULL`|太小|any|`ERANGE`|`strDest`\[0\] 设置为 0|  
  
## 备注  
 这些函数想要复制 `strSource` 的第一个字符 `D` 到 `strDest`，`D` 是 `count`的较小值 和 `strSource`的长度。  如果这些 `D` 字符将适合于 `strDest` （其大小是 `numberOfElements`），仍然留出 null结束符的位置，然后这些字符被复制并追加null结束符；否则，`strDest`\[0\] 设置为在 null 字符和无效的参数调用处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 验证描述。  
  
 与上面段有异常。  如果 `count` 是 `_TRUNCATE`，则相同数量的 `strSource` 将复制到 `strDest`，同时仍然保留 null 结束符的空间。  
  
 例如，  
  
 `char dst[5];`  
  
 `strncpy_s(dst, 5, "a long string", 5);`  
  
 意味着我们请求 `strncpy_s` 复制五个字符到五个字节的缓冲区；这不会留下 null 结束符的空间，因此 `strncpy_s` 只有0空间的字符串和调用无效参数处理程序。  
  
 如果截断行为是必需的，请使用 `_TRUNCATE` 或 \(`size` – 1\):  
  
 `strncpy_s(dst, 5, "a long string", _TRUNCATE);`  
  
 `strncpy_s(dst, 5, "a long string", 4);`  
  
 请注意不同的 `strncpy`，如果 `count` 比 `strSource`的长，目标字符串不用零填充该字符 `count`的长度。  
  
 如果源和目标字符串重叠，则 `strncpy_s` 的行为未定义。  
  
 如果 `strDest` 或 `strSource` 是 `NULL`，或者 `numberOfElements` 为 0，则是无效参数调用处理程序。  如果允许执行继续，则该函数返回 `EINVAL` 并将 `errno` 设置为 `EINVAL`。  
  
 `wcsncpy_s` 和 `_mbsncpy_s` 是宽字符，属于 `strncpy_s` 的多节字字符版本。  参数和 `wcsncpy_s` 的返回值和 `mbsncpy_s` 相应地改变。  否则这六个函数具有相同行为。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小参数\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。  若要禁用此行为，请使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsncpy_s`|`strncpy_s`|`_mbsnbcpy_s`|`wcsncpy_s`|  
|`_tcsncpy_s_l`|`_strncpy_s_l`|`_mbsnbcpy_s_l`|`_wcsncpy_s_l`|  
  
> [!NOTE]
>  \_strncpy\_s\_l， `_wcsncpy_s_l` 和 `_mbsncpy_s_l` 没有区域设置依赖项以及为 `_tcsncpy_s_l` 做准备和不打算直接调用。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strncpy_s`, `_strncpy_s_l`|\<string.h\>|  
|`wcsncpy_s`, `_wcsncpy_s_l`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsncpy_s`, `_mbsncpy_s_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strncpy_s_1.cpp  
// compile with: /MTd  
  
// these #defines enable secure template overloads  
// (see last part of Examples() below)  
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1   
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT 1  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <crtdbg.h>  // For _CrtSetReportMode  
#include <errno.h>  
  
// This example uses a 10-byte destination buffer.  
  
errno_t strncpy_s_tester( const char * src,  
                          int count )  
{  
   char dest[10];  
  
   printf( "\n" );  
  
   if ( count == _TRUNCATE )  
      printf( "Copying '%s' to %d-byte buffer dest with truncation semantics\n",  
               src, _countof(dest) );  
   else  
      printf( "Copying %d chars of '%s' to %d-byte buffer dest\n",  
              count, src, _countof(dest) );  
  
   errno_t err = strncpy_s( dest, _countof(dest), src, count );  
  
   printf( "    new contents of dest: '%s'\n", dest );  
  
   return err;  
}  
  
void Examples()  
{  
   strncpy_s_tester( "howdy", 4 );  
   strncpy_s_tester( "howdy", 5 );  
   strncpy_s_tester( "howdy", 6 );  
  
   printf( "\nDestination buffer too small:\n" );  
   strncpy_s_tester( "Hi there!!", 10 );  
  
   printf( "\nTruncation examples:\n" );  
  
   errno_t err = strncpy_s_tester( "How do you do?", _TRUNCATE );  
   printf( "    truncation %s occur\n", err == STRUNCATE ? "did"  
                                                       : "did not" );  
  
   err = strncpy_s_tester( "Howdy.", _TRUNCATE );  
   printf( "    truncation %s occur\n", err == STRUNCATE ? "did"  
                                                       : "did not" );  
  
   printf( "\nSecure template overload example:\n" );  
  
   char dest[10];  
   strncpy( dest, "very very very long", 15 );  
   // With secure template overloads enabled (see #defines at  
   // top of file), the preceding line is replaced by  
   //    strncpy_s( dest, _countof(dest), "very very very long", 15 );  
   // Instead of causing a buffer overrun, strncpy_s invokes  
   // the invalid parameter handler.  
   // If secure template overloads were disabled, strncpy would  
   // copy 15 characters and overrun the dest buffer.  
   printf( "    new contents of dest: '%s'\n", dest );  
}  
  
void myInvalidParameterHandler(  
   const wchar_t* expression,  
   const wchar_t* function,   
   const wchar_t* file,   
   unsigned int line,   
   uintptr_t pReserved)  
{  
   wprintf(L"Invalid parameter handler invoked: %s\n", expression);  
}  
  
int main( void )  
{  
   _invalid_parameter_handler oldHandler, newHandler;  
  
   newHandler = myInvalidParameterHandler;  
   oldHandler = _set_invalid_parameter_handler(newHandler);  
   // Disable the message box for assertions.  
   _CrtSetReportMode(_CRT_ASSERT, 0);  
  
   Examples();  
}  
```  
  
  **复制“howdy”的4个字符到10字节缓冲区的 dest**  
 **dest 的新内容：“howd”**  
**复制“howdy”的5个字符到10字节缓冲区的 dest**  
 **dest 的新内容：“howdy”**  
**复制“howdy”的6个字符到10字节缓冲区的 dest**  
 **dest 的新内容：“howdy”**  
**目标缓冲区太小：**  
**复制“Hi there\!\!”中的10个字符到10字节缓冲区 dest**  
**无效参数调用处理程序：\(L "缓冲区太小”&& 0\)**  
 **dest 的新内容："**  
**截断示例：**  
**通过截断语义复制“How do you do？”10个字节缓冲区 dest**  
 **dest 的新内容：“How do yo”**  
 **截断发生**  
**通过截断语义复制“Howdy.”到10个字节缓冲区 dest**  
 **dest 的新内容：“Howdy.”**  
 **截断没有发生**  
**安全模板重载示例：**  
**无效参数调用处理程序：\(L "缓冲区太小”&& 0\)**  
 **dest 的新内容："**   
## 示例  
  
```  
// crt_strncpy_s_2.c  
// contrasts strncpy and strncpy_s  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char a[20] = "test";  
   char s[20];  
  
   // simple strncpy usage:  
  
   strcpy_s( s, 20, "dogs like cats" );  
   printf( "Original string:\n   '%s'\n", s );  
  
   // Here we can't use strncpy_s since we don't   
   // want null termination  
   strncpy( s, "mice", 4 );  
   printf( "After strncpy (no null-termination):\n   '%s'\n", s );  
   strncpy( s+5, "love", 4 );  
   printf( "After strncpy into middle of string:\n   '%s'\n", s );  
  
   // If we use strncpy_s, the string is terminated   
   strncpy_s( s, _countof(s), "mice", 4 );  
   printf( "After strncpy_s (with null-termination):\n   '%s'\n", s );  
  
}  
```  
  
  **原始字符串：**  
 **“dogs like cats”**  
**在 strncpy 之后 \(而非 null 结束符\):**  
 **“mice like cats”**  
**strncpy 转换为字符串中间：**  
 **”mice love cats“**  
**在 strncpy\_s 后 \(包含 null 结束符\):**  
 **“mice”**   
## .NET Framework 等效项  
 [System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbsnbcpy、\_mbsnbcpy\_l](../../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)   
 [strcat\_s、wcscat\_s、\_mbscat\_s](../../c-runtime-library/reference/strcat-s-wcscat-s-mbscat-s.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy\_s、wcscpy\_s、\_mbscpy\_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)   
 [strncat\_s、\_strncat\_s\_l、wcsncat\_s、\_wcsncat\_s\_l、\_mbsncat\_s、\_mbsncat\_s\_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)