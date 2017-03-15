---
title: "_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_sprintf_p"
  - "_swprintf_p_l"
  - "_swprintf_p"
  - "_sprintf_p_l"
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
  - "_sprintf_p"
  - "_swprintf_p_l"
  - "_sprintf_p_l"
  - "_swprintf_p"
  - "sprintf_p"
  - "swprint_p_l"
  - "swprintf_p"
  - "swprintf_p_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sprintf_p_l 函数"
  - "swprintf_p 函数"
  - "swprintf_p_l 函数"
  - "_sprintf_p 函数"
  - "_sprintf_p_l 函数"
  - "_swprintf_p 函数"
  - "sprintf_p 函数"
  - "_stprintf_p 函数"
  - "stprintf_p 函数"
  - "_swprintf_p_l 函数"
  - "stprintf_p_l 函数"
  - "格式化文本 [C++]"
  - "_stprintf_p_l 函数"
ms.assetid: a2ae78e8-6b0c-48d5-87a9-ea2365b0693d
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编写字符串格式的数据为能够指定排序参数使用格式字符串。  
  
## 语法  
  
```  
int _sprintf_p(  
   char *buffer,  
   size_t sizeOfBuffer,  
   const char *format [,  
   argument] ...   
);  
int _sprintf_p_l(  
   char *buffer,  
   size_t sizeOfBuffer,  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _swprintf_p(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   const wchar_t *format [,  
   argument]...  
);  
int _swprintf_p_l(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] …   
);  
```  
  
#### 参数  
 `buffer`  
 输出的存储位置  
  
 `sizeOfBuffer`  
 可存储的最多字符数。  
  
 `format`  
 格式控件字符串  
  
 `argument`  
 可选参数  
  
 `locale`  
 要使用的区域设置。  
  
 有关更多信息，请参见[格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 返回值  
 写入的字符数或 \-1（如果发生错误）。  
  
## 备注  
 `_sprintf_p`  函数存储 `buffer` 中的一系列字符和值并设置格式。  每个 `argument`（如果有）根据 `format` 中相应的格式规范进行转换和输出。  该格式包括普通字符，其形式和函数与 `printf_p` 的 `format` 参数相同。  一个 `NULL` 字符追加在写入的最后一个字符后。  如果在重叠的字符串之间发生复制，则此行为不确定。   `_sprintf_p` 和 `sprintf_s` 的不同之处在于 `_sprintf_p` 支持位置参数，它在格式化字符串使用参数时荀彧指定顺序。  有关详细信息，请参阅[printf\_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)。  
  
 `_swprintf_p` 是 `_sprintf_p`的宽字符版本；`_swprintf_p` 的指针参数是宽字符串。  `_swprintf_p` 中的编码错误检测可能与 `_sprintf_p` 中的不同。  `_swprintf_p` 和 `fwprintf_p` 运行方式相同，但 `_swprintf_p` 向字符串而不是向 `FILE` 类型的目标写入字符串，并且，`_swprintf_p` 需要 `count` 参数指定要写入的最大字符数。  这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
 `_sprintf_p` 返回存储在 `buffer` 中的字节数，不包括终止 `NULL` 字符。  `_swprintf_p` 返回存储在 `buffer` 中的宽字符数，不包括中止 `NULL` 宽字符。  如果 `buffer` 或者 `format` 是空指针，如果格式字符串包含无效格式字符，无效参数调用处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则这些函数返回 \-1 并将 `errno` 设置为 `EINVAL`。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE & 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|-------------------------------|----------------|-------------------|  
|`_stprintf_p`|`_sprintf_p`|`_sprintf_p`|`_swprintf_p`|  
|`_stprintf_p_l`|`_sprintf_p_l`|`_sprintf_p_l`|`_swprintf_p_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_sprintf_p`, `_sprintf_p_l`|\<stdio.h\>|  
|`_swprintf_p`, `_swprintf_p_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_sprintf_p.c  
// This program uses _sprintf_p to format various  
// data and place them in the string named buffer.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
    char     buffer[200],  
            s[] = "computer", c = 'l';  
    int      i = 35,  
            j;  
    float    fp = 1.7320534f;  
  
    // Format and print various data:   
    j  = _sprintf_p( buffer, 200,  
                     "   String:    %s\n", s );  
    j += _sprintf_p( buffer + j, 200 - j,   
                     "   Character: %c\n", c );  
    j += _sprintf_p( buffer + j, 200 - j,   
                     "   Integer:   %d\n", i );  
    j += _sprintf_p( buffer + j, 200 - j,   
                     "   Real:      %f\n", fp );  
  
    printf( "Output:\n%s\ncharacter count = %d\n",   
            buffer, j );  
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
// crt_swprintf_p.c  
// This is the wide character example which  
// also demonstrates _swprintf_p returning  
// error code.  
#include <stdio.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    wchar_t buffer[BUFFER_SIZE];  
    int     len;  
  
    len = _swprintf_p(buffer, BUFFER_SIZE, L"%2$s %1$d",  
                      0, L" marbles in your head.");  
    _printf_p( "Wrote %d characters\n", len );  
  
    // _swprintf_p fails because string contains WEOF (\xffff)  
    len = _swprintf_p(buffer, BUFFER_SIZE, L"%s",   
                      L"Hello\xffff world" );  
    _printf_p( "Wrote %d characters\n", len );  
}  
```  
  
  **Wrote 24 characters**  
**Wrote \-1 characters**   
## .NET Framework 等效项  
 [System::String::Format](https://msdn.microsoft.com/en-us/library/system.string.format.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_fprintf\_p、\_fprintf\_p\_l、\_fwprintf\_p、\_fwprintf\_p\_l](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [\_printf\_p、\_printf\_p\_l、\_wprintf\_p、\_wprintf\_p\_l](../../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [sscanf\_s、\_sscanf\_s\_l、swscanf\_s、\_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)   
 [printf\_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)