---
title: "vsprintf_s、_vsprintf_s_l、vswprintf_s、_vswprintf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vswprintf_s_l"
  - "vsprintf_s"
  - "vswprintf_s"
  - "_vsprintf_s_l"
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
  - "vswprintf_s"
  - "vsprintf_s"
  - "_vstprintf_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_vstprintf_s_l 函数"
  - "vsprintf_s_l 函数"
  - "_vstprintf_s 函数"
  - "vswprintf_s 函数"
  - "vstprintf_s 函数"
  - "vstprintf_s_l 函数"
  - "vswprintf_s_l 函数"
  - "vsprintf_s 函数"
  - "_vsprintf_s_l 函数"
  - "格式化文本 [C++]"
  - "_vswprintf_s_l 函数"
ms.assetid: 60e90518-57f0-4f1b-b732-f62a69702833
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# vsprintf_s、_vsprintf_s_l、vswprintf_s、_vswprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编写使用指针参数列表的格式化输出。  [vsprintf、\_vsprintf\_l、vswprintf、\_vswprintf\_l、\_\_vswprintf\_l](../../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md) 的一些版本提供安全增强功能（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
int vsprintf_s(  
   char *buffer,  
   size_t numberOfElements,  
   const char *format,  
   va_list argptr   
);   
int _vsprintf_s_l(  
   char *buffer,  
   size_t numberOfElements,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);   
int vswprintf_s(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vswprintf_s_l(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
template <size_t size>  
int vsprintf_s(  
   char (&buffer)[size],  
   const char *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int vswprintf_s(  
   wchar_t (&buffer)[size],  
   const wchar_t *format,  
   va_list argptr   
); // C++ only  
```  
  
#### 参数  
 `buffer`  
 输出的存储位置。  
  
 `numberOfElements`  
 `buffer` 的字符大小。  
  
 `format`  
 格式规范。  
  
 `argptr`  
 指向参数列表的指针。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果输出有错误，`vsprintf_s`和 `vswprintf_s`返回编写的字符数，不包括终止空字符或负值。  如果 `buffer` 或 `format` 是空指针，如果数量为零，或如果格式字符串包含无效格式字符，则调用无效参数处理程序，正如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许继续执行，则这些函数返回\-1，并将`errno`设置为`EINVAL`。  
  
 有关这些属性和其他错误代码的信息，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 这些功能中的每一个采用指向参数列表的指针，然后布局和编写特定数据到由 `buffer`指向的内存。  
  
 `vswprintf_s` 符合对于 `vswprintf` 的 ISO C 标准，需要第二个参数 `count` 的 `size_t` 类型。  
  
 这些函数与非安全版本的差异仅因为安全版本支持位置参数。  有关详细信息，请参阅[printf\_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小参数\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|\_UNICODE & \_MBCS 未定义|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vstprintf_s`|`vsprintf_s`|`vsprintf_s`|`vswprintf_s`|  
|`_vstprintf_s_l`|`_vsprintf_s_l`|`_vsprintf_s_l`|`_vswprintf_s_l`|  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`vsprintf_s`, `_vsprintf_s_l`|\<stdio.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
|`vswprintf_s`, `_vswprintf_s_l`|\<stdio.h\> 或 \<wchar.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* 仅对 UNIX V 兼容性是必需的。  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_vsprintf_s.c  
// This program uses vsprintf_s to write to a buffer.  
// The size of the buffer is determined by _vscprintf.  
  
#include <stdlib.h>  
#include <stdarg.h>  
  
void test( char * format, ... )  
{  
   va_list args;  
   int len;  
   char * buffer;  
  
   va_start( args, format );  
   len = _vscprintf( format, args ) // _vscprintf doesn't count  
                               + 1; // terminating '\0'  
   buffer = malloc( len * sizeof(char) );  
   vsprintf_s( buffer, len, format, args );  
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