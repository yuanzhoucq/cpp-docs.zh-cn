---
title: "vsprintf、_vsprintf_l、vswprintf、_vswprintf_l、__vswprintf_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vswprintf_l"
  - "_vsprintf_l"
  - "vsprintf"
  - "vswprintf"
  - "__vswprintf_l"
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
  - "vstprintf"
  - "vswprintf"
  - "_vstprintf"
  - "vsprintf"
  - "__vswprintf_l"
  - "_vsprintf_l"
  - "_vswprintf_l"
  - "vswprintf_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__vswprintf_l 函数"
  - "_vsprintf_l 函数"
  - "_vstprintf 函数"
  - "_vstprintf_l 函数"
  - "_vswprintf_l 函数"
  - "缓冲区溢出"
  - "缓冲区, 避免溢出"
  - "缓冲区, 缓冲区溢出"
  - "格式化文本"
  - "vsprintf 函数"
  - "vsprintf_l 函数"
  - "vstprintf 函数"
  - "vstprintf_l 函数"
  - "vswprintf 函数"
  - "vswprintf_l 函数"
ms.assetid: b8ef1c0d-58f9-4a18-841a-f1a989e1c29b
caps.latest.revision: 32
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 32
---
# vsprintf、_vsprintf_l、vswprintf、_vswprintf_l、__vswprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编写使用指针参数列表的格式化输出。  有关这些函数的更多安全版本，请参见 [vsprintf\_s、\_vsprintf\_s\_l、vswprintf\_s、\_vswprintf\_s\_l](../../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)。  
  
## 语法  
  
```  
int vsprintf(  
   char *buffer,  
   const char *format,  
   va_list argptr   
);   
int _vsprintf_l(  
   char *buffer,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);   
int vswprintf(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vswprintf_l(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
int __vswprintf_l(  
   wchar_t *buffer,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
template <size_t size>  
int vsprintf(  
   char (&buffer)[size],  
   const char *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsprintf_l(  
   char (&buffer)[size],  
   const char *format,  
   locale_t locale,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int vswprintf(  
   wchar_t (&buffer)[size],  
   const wchar_t *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vswprintf_l(  
   wchar_t (&buffer)[size],  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
); // C++ only  
```  
  
#### 参数  
 `buffer`  
 输出的存储位置。  
  
 `count`  
 `UNICODE` 版本中此函数的 Unicode 版所存储的最大字符数.  
  
 `format`  
 格式规范。  
  
 `argptr`  
 指向参数列表的指针。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果输出有错误，`vsprintf`和 `vswprintf`返回编写的字符数，不包括终止空字符或负值。  如果 `buffer` 或 `format` 是 null 指针，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则这些函数返回 \-1 并将 `errno` 设置为 `EINVAL`。  
  
 有关这些属性和其他错误代码的信息，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 这些功能中的每一个采用指向参数列表的指针，然后布局和编写特定数据到由 `buffer`指向的内存。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
> [!IMPORTANT]
>  使用 `vsprintf`，无法限制编写的字符数，这意味着使用此函数的代码易出现缓冲区溢出。  使用 [\_vsnprintf](../../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 或调用 [\_vscprintf](../../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md) 确定需要多大的缓冲区。  此外，请确保 `format` 不是用户定义的字符串。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
 `vswprintf` 符合 ISO C 标准，需要 `size_t` 类型的第二个参数，即`count`。  若要强制早期非标准行为，请定义 `_CRT_NON_CONFORMING_SWPRINTFS.`旧行为可能不会出现在将来的版本中，因此应更改代码使用新的一致的行为。  
  
 在 C\+\+ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vstprintf`|`vsprintf`|`vsprintf`|`vswprintf`|  
|`_vstprintf_l`|`_vsprintf_l`|`_vsprintf_l`|`_vswprintf_l`|  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`vsprintf`, `_vsprintf_l`|\<stdio.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
|`vswprintf`, `_vswprintf_l`|\<stdio.h\> 或 \<wchar.h\> 或 \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* 仅对 UNIX V 兼容性是必需的。  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_vsprintf.c  
// compile with: /W3  
// This program uses vsprintf to write to a buffer.  
// The size of the buffer is determined by _vscprintf.  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <stdarg.h>  
  
void test( char * format, ... )  
{  
    va_list args;  
    int     len;  
    char    *buffer;  
  
    // retrieve the variable arguments  
    va_start( args, format );  
  
    len = _vscprintf( format, args ) // _vscprintf doesn't count  
                                + 1; // terminating '\0'  
  
    buffer = (char*)malloc( len * sizeof(char) );  
  
    vsprintf( buffer, format, args ); // C4996  
    // Note: vsprintf is deprecated; consider using vsprintf_s instead  
    puts( buffer );  
  
    free( buffer );  
}  
  
int main( void )  
{  
   test( "%d %c %d", 123, '<', 456 );  
   test( "%s", "This is a string" );  
}  
```  
  
  **123 \< 456**  
**这是一个字符串。**   
## .NET Framework 等效项  
 [System::String::Format](https://msdn.microsoft.com/en-us/library/system.string.format.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)   
 [格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)