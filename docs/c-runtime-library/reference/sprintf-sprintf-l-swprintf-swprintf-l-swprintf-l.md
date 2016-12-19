---
title: "sprintf、_sprintf_l、swprintf、_swprintf_l、__swprintf_l | Microsoft Docs"
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
  - "__swprintf_l"
  - "sprintf"
  - "_sprintf_l"
  - "_swprintf_l"
  - "swprintf"
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
apitype: "DLLExport"
f1_keywords: 
  - "_stprintf_l"
  - "__swprintf_l"
  - "sprintf_l"
  - "swprintf"
  - "_sprintf_l"
  - "sprintf"
  - "_stprintf"
  - "stprintf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "__swprintf_l 函数"
  - "_CRT_NON_CONFORMING_SWPRINTFS"
  - "_sprintf_l 函数"
  - "_stprintf 函数"
  - "_stprintf_l 函数"
  - "_swprintf_l 函数"
  - "格式化文本 [C++]"
  - "sprintf 函数"
  - "sprintf_l 函数"
  - "stprintf 函数"
  - "stprintf_l 函数"
  - "字符串 [C++], 写入"
  - "swprintf 函数"
  - "swprintf_l 函数"
ms.assetid: f6efe66f-3563-4c74-9455-5411ed939b81
caps.latest.revision: 36
caps.handback.revision: 34
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sprintf、_sprintf_l、swprintf、_swprintf_l、__swprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将设置格式的数据写入字符串。  可提供某些函数的更多安全版本，请参阅 [sprintf\_s、\_sprintf\_s\_l、swprintf\_s、\_swprintf\_s\_l](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)。  安全版本 `swprintf` 和 `_swprintf_l` 不采用 `count` 参数。  
  
## 语法  
  
```  
int sprintf(  
   char *buffer,  
   const char *format [,  
   argument] ...   
);  
int _sprintf_l(  
   char *buffer,  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int swprintf(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format [,  
   argument]...  
);  
int _swprintf_l(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
int __swprintf_l(  
   wchar_t *buffer,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
template <size_t size>  
int sprintf(  
   char (&buffer)[size],  
   const char *format [,  
   argument] ...   
); // C++ only  
template <size_t size>  
int _sprintf_l(  
   char (&buffer)[size],  
   const char *format,  
   locale_t locale [,  
   argument] ...   
); // C++ only  
  
```  
  
#### 参数  
 `buffer`  
 输出的存储位置  
  
 `count`  
 要存储在 Unicode 版的此函数中的最大字符数。  
  
 `format`  
 格式控件字符串  
  
 `argument`  
 可选参数  
  
 `locale`  
 要使用的区域设置。  
  
 有关更多信息，请参见[格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 返回值  
 写入的字符数或 \-1（如果发生错误）。  如果 `buffer` 或 `format` 是空指针，则调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许继续执行，则这些函数返回 \-1 并将 `errno` 设置为 `EINVAL`。  
  
 `sprintf` 返回存储在 `buffer` 中的字节数，不包括终止 null 字符。  `swprintf` 返回存储在 `buffer` 中的宽字符数，不包括中止 null 宽字符。  
  
## 备注  
 `sprintf` 函数存储 `buffer` 中的一系列字符和值并设置格式。  每个 `argument`（如果有）根据 `format` 中相应的格式规范进行转换和输出。  该格式包括普通字符，其形式和函数与 `format`printf 的 [参数相同。](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) null 字符追加在写入的最后一个字符后。  如果在重叠的字符串之间发生复制，则此行为不确定。  
  
> [!IMPORTANT]
>  使用 `sprintf`，无法限制写入的字符数，这意味着使用 `sprintf` 的代码容易受到缓冲区溢出的影响。  请考虑使用相关的函数 [\_snprintf](../../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)，其可指定写入 `buffer` 的最大字符数，或使用 [\_scprintf](../../c-runtime-library/reference/scprintf-scprintf-l-scwprintf-scwprintf-l.md) 来确定需要多大的缓冲区。  同样，确保 `format` 不是用户定义的字符串。  
  
 `swprintf` 是 `sprintf`的宽字符版本；`swprintf` 的指针参数是宽字符串。  `swprintf` 中的编码错误检测可能与 `sprintf` 中的不同。  `swprintf` 和 `fwprintf` 行为完全相同，只不过 `swprintf` 将输出写入到一个字符串，而不是类型 `FILE` 的目标，并且 `swprintf` 需要 `count` 参数来指定要写入的最大字符数。  这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
 `swprintf` 符合 ISO C 标准，其需要类型为的 `size_t` 第二个参数 `count`。  若要强制旧的非标准行为，请定义 `_CRT_NON_CONFORMING_SWPRINTFS`。  在未来版本中，可能会删除旧行为，因此应将代码更改为使用新的符合标准行为。  
  
 在 C\+\+ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_stprintf`|`sprintf`|`sprintf`|`_swprintf`|  
|`_stprintf_l`|`_sprintf_l`|`_sprintf_l`|`__swprintf_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`sprintf`, `_sprintf_l`|\<stdio.h\>|  
|`swprintf`, `_swprintf_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_sprintf.c  
// compile with: /W3  
// This program uses sprintf to format various  
// data and place them in the string named buffer.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char  buffer[200], s[] = "computer", c = 'l';  
   int   i = 35, j;  
   float fp = 1.7320534f;  
  
   // Format and print various data:   
   j  = sprintf( buffer,     "   String:    %s\n", s ); // C4996  
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996  
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996  
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996  
   // Note: sprintf is deprecated; consider using sprintf_s instead  
  
   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );  
}  
```  
  
  **输出：**  
 **String:    computer**  
 **Character: l**  
 **Integer:   35**  
 **Real:      1.732053**  
**character count \= 79**   
## 示例  
  
```  
// crt_swprintf.c  
// wide character example  
// also demonstrates swprintf returning error code  
#include <stdio.h>  
  
int main( void )  
{  
   wchar_t buf[100];  
   int len = swprintf( buf, 100, L"%s", L"Hello world" );  
   printf( "wrote %d characters\n", len );  
   len = swprintf( buf, 100, L"%s", L"Hello\xffff world" );  
   // swprintf fails because string contains WEOF (\xffff)  
   printf( "wrote %d characters\n", len );  
}  
```  
  
  **wrote 11 characters**  
**wrote \-1 characters**   
## .NET Framework 等效项  
 [System::String::Format](https://msdn.microsoft.com/en-us/library/system.string.format.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)