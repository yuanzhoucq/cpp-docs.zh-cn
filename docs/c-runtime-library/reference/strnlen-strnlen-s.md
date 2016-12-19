---
title: "strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l | Microsoft Docs"
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
  - "wcsnlen"
  - "strnlen_s"
  - "_mbstrnlen"
  - "_mbsnlen_l"
  - "_mbstrnlen_l"
  - "strnlen"
  - "wcsnlen_s"
  - "_mbsnlen"
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
  - "wcsnlen"
  - "strnlen_s"
  - "_mbsnlen"
  - "_mbsnlen_l"
  - "_tcsnlen"
  - "_tcscnlen"
  - "_mbstrnlen_l"
  - "wcsnlen_s"
  - "_mbstrnlen"
  - "strnlen"
  - "_tcscnlen_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnlen 函数"
  - "_mbsnlen_l 函数"
  - "_mbstrnlen 函数"
  - "_mbstrnlen_l 函数"
  - "_tcscnlen 函数"
  - "_tcscnlen_l 函数"
  - "_tcsnlen 函数"
  - "长度, 字符串"
  - "mbsnlen 函数"
  - "mbsnlen_l 函数"
  - "mbstrnlen 函数"
  - "mbstrnlen_l 函数"
  - "字符串长度"
  - "strnlen 函数"
  - "strnlen_l 函数"
  - "strnlen_s 函数"
  - "wcsnlen 函数"
  - "wcsnlen_l 函数"
  - "wcsnlen_s 函数"
ms.assetid: cc05ce1c-72ea-4ae4-a7e7-4464e56e5f80
caps.latest.revision: 35
caps.handback.revision: 33
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用当前区域设置或已传入的一个区域设置获取字符串的长度。  这些是 [strlen、wcslen、\_mbslen、\_mbslen\_l、\_mbstrlen、\_mbstrlen\_l](../../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md) 的更加安全的版本。  
  
> [!IMPORTANT]
>  `_mbsnlen`、`_mbsnlen_l`、`_mbstrnlen` 和 `_mbstrnlen_l` 无法用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/ZH-CN/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
size_t strnlen(  
   const char *str,  
   size_t numberOfElements   
);  
size_t strnlen_s(  
   const char *str,  
   size_t numberOfElements   
);  
size_t wcsnlen(  
   const wchar_t *str,  
   size_t numberOfElements  
);  
size_t wcsnlen_s(  
   const wchar_t *str,  
   size_t numberOfElements  
);  
size_t _mbsnlen(  
   const unsigned char *str,  
   size_t numberOfElements  
);  
size_t _mbsnlen_l(  
   const unsigned char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
size_t _mbstrnlen(  
   const char *str,  
   size_t numberOfElements  
);  
size_t _mbstrnlen_l(  
   const char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `str`  
 以 Null 结尾的字符串。  
  
 `numberOfElements`  
 字符串缓冲区的大小。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 这些函数将返回字符串中的字符数，不包括以 null 结尾的字符。  如果字符串的第一个 `numberOfElements` 字节中不包含 null 终止符，（或 `wcsnlen` 的宽字符），则返回 `numberOfElements` 以指示错误条件；以 null 结尾的字符串的长度严格小于 `numberOfElements`。  
  
 如果字符串包含无效的多字节字符，则 `_mbstrnlen` 和 `_mbstrnlen_l` 将返回 \-1。  
  
## 备注  
  
> [!NOTE]
>  `strnlen` 不是 `strlen` 的替代方法；应将 `strnlen` 仅用于计算已知大小的缓冲区中传入的不受信任数据的大小，例如网络数据包。  `strnlen` 计算长度，但是如果该字符串是非终止的，则它不会超过缓冲区的末尾。  对于其他情况，请使用 `strlen`。  （同一情况适用于 `wcsnlen`、`_mbsnlen` 和 `_mbstrnlen`。）  
  
 其中每个函数都将返回 `str` 中的字符数，不包括以 null 结尾的字符。  但是，`strnlen` 和 `strnlen_s` 会将字符串解释为单字节字符字符串，因此即使该字符串包含多字节字符，返回值也始终等于字节数。  `wcsnlen` 和 `wcsnlen_s` 分别是 `strnlen` 和 `strnlen_s` 的宽字符版本；`wcsnlen` 和 `wcsnlen_s` 的参数是宽字符字符串且字符计数以宽字符为单位。  除此以外，`wcsnlen` 和 `strnlen` 的行为完全相同，`strnlen_s` 和 `wcsnlen_s` 也是如此。  
  
 `strnlen`、`wcsnlen,` 和 `_mbsnlen` 不会验证其参数。  如果 `str` 是 `NULL`，则会发生访问冲突。  
  
 `strnlen_s` 和 `wcsnlen_s` 将验证其参数。  如果 `str` 是 `NULL`，则函数返回 0。  
  
 `_mbstrnlen` 也会验证其参数。  如果 `str` 为 `NULL` 或 `numberOfElements` 大于 `INT_MAX`，则如[参数验证](../../c-runtime-library/parameter-validation.md)中所述，`_mbstrnlen` 将生成无效的参数异常。  如果允许执行继续，则 `_mbstrnlen` 会将 `errno` 设置为 `EINVAL` 并返回 \-1。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsnlen`|`strnlen`|`strnlen`|`wcsnlen`|  
|`_tcscnlen`|`strnlen`|`_mbsnlen`|`wcsnlen`|  
|`_tcscnlen_l`|`strnlen`|`_mbsnlen_l`|`wcsnlen`|  
  
 `_mbsnlen` 和 `_mbstrnlen` 以多字节字符字符串格式返回多字节字符的数量。  `_mbsnlen` 根据当前正在使用的多字节代码页或已传入的区域设置来识别多字节字符序列；它不会测试多字节字符的有效性。  `_mbstrnlen` 将测试多字节字符的有效性并识别多字节字符序列。  如果传递给 `_mbstrnlen` 的字符串包含无效的多字节字符，则 `errno` 将设置为 `EILSEQ`。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些函数的版本相同，差异在于不包含 `_l` 后缀的版本使用与此区域设置相关的行为的当前区域设置，而包含 `_l` 后缀的版本则使用传入的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strnlen`, `strnlen_s`|\<string.h\>|  
|`wcsnlen`, `wcsnlen_s`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsnlen`, `_mbsnlen_l`|\<mbstring.h\>|  
|`_mbstrnlen`, `_mbstrnlen_l`|\<stdlib.h\>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strnlen.c  
  
#include <string.h>  
  
int main()  
{  
   // str1 is 82 characters long. str2 is 159 characters long   
  
   char* str1 = "The length of a string is the number of characters\n"  
               "excluding the terminating null.";  
   char* str2 = "strnlen takes a maximum size. If the string is longer\n"  
                "than the maximum size specified, the maximum size is\n"  
                "returned rather than the actual size of the string.";  
   size_t len;  
   size_t maxsize = 100;  
  
   len = strnlen(str1, maxsize);  
   printf("%s\n Length: %d \n\n", str1, len);  
  
   len = strnlen(str2, maxsize);  
   printf("%s\n Length: %d \n", str2, len);  
}  
```  
  
  **字符串的长度就是字符数**  
**不包括终止 null。  长度：82**   
**strnlen 采用最大大小。  如果字符串长于**  
**指定的最大大小，则将返回最大大小，**  
**而不是该字符串的实际大小。  长度：100**    
## .NET Framework 等效项  
 [System::String::Length](https://msdn.microsoft.com/en-us/library/system.string.length.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [strncpy\_s、\_strncpy\_s\_l、wcsncpy\_s、\_wcsncpy\_s\_l、\_mbsncpy\_s、\_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)