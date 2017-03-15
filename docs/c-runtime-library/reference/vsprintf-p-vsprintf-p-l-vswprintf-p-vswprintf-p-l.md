---
title: "_vsprintf_p、_vsprintf_p_l、_vswprintf_p、_vswprintf_p_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vsprintf_p"
  - "_vswprintf_p"
  - "_vsprintf_p_l"
  - "_vswprintf_p_l"
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
  - "vsprintf_p"
  - "_vswprintf_p"
  - "_vstprintf_p"
  - "vswprintf_p"
  - "_vsprintf_p"
  - "vstprintf_p"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_vsprintf_p 函数"
  - "_vsprintf_p_l 函数"
  - "_vstprintf_p 函数"
  - "_vstprintf_p_l 函数"
  - "_vswprintf_p 函数"
  - "_vswprintf_p_l 函数"
  - "格式化文本 [C++]"
  - "vsprintf_p 函数"
  - "vsprintf_p_l 函数"
  - "vstprintf_p 函数"
  - "vstprintf_p_l 函数"
  - "vswprintf_p 函数"
  - "vswprintf_p_l 函数"
ms.assetid: 00821c0d-9fee-4d8a-836c-0669cfb11317
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _vsprintf_p、_vsprintf_p_l、_vswprintf_p、_vswprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用指针编写格式化输出的参数列表，能够指定使用格式字符串参数的排序。  
  
## 语法  
  
```  
int _vsprintf_p(  
   char *buffer,  
   size_t sizeInBytes,  
   const char *format,  
   va_list argptr   
);   
int _vsprintf_p_l(  
   char *buffer,  
   size_t sizeInBytes,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);   
int _vswprintf_p(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vswprintf_p_l(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### 参数  
 `buffer`  
 输出的存储位置。  
  
 `sizeInBytes`  
 `buffer` 的字符大小。  
  
 `count`  
 此函数的 Unicode 版所存储的最大字符数。  
  
 `format`  
 格式规范。  
  
 `argptr`  
 指向参数列表的指针。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果输出有错误，`_vsprintf_p`和 `_vswprintf_p`返回编写的字符数，不包括终止空字符或负值。  
  
## 备注  
 这些功能中的每一个采用指向参数列表的指针，然后布局和编写特定数据到由 `buffer`指向的内存。  
  
 这些函数与 `vsprintf_s` 和 `vswprintf_s`的差异仅在于它们支持位置参数。  有关详细信息，请参阅[printf\_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
 如果 `buffer` 或`format` 参数为NULL指针，如果计数为零，或者，如果格式字符串包含无效的格式字符，则无效参数的处理程序如 [参数验证](../../c-runtime-library/parameter-validation.md)所述被调用。  如果允许继续执行，则这些函数返回\-1，并将`errno`设置为`EINVAL`。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|\_UNICODE & \_MBCS 未定义|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vstprintf_p`|`_vsprintf_p`|`_vsprintf_p`|`_vswprintf_p`|  
|`_vstprintf_p_l`|`_vsprintf_p_l`|`_vsprintf_p_l`|`_vswprintf_p_l`|  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_vsprintf_p`, `_vsprintf_p_l`|\<stdio.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
|`_vswprintf_p`, `_vswprintf_p_l`|\<stdio.h\> 或 \<wchar.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* 仅对 UNIX V 兼容性是必需的。  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt__vsprintf_p.c  
// This program uses vsprintf_p to write to a buffer.  
// The size of the buffer is determined by _vscprintf_p.  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <stdarg.h>  
  
void example( char * format, ... )  
{  
    va_list  args;  
    int      len;  
    char     *buffer = NULL;  
  
    va_start( args, format );  
  
    // _vscprintf doesn't count the   
    // null terminating string so we add 1.  
    len = _vscprintf_p( format, args ) + 1;  
  
    // Allocate memory for our buffer  
    buffer = (char*)malloc( len * sizeof(char) );  
    if (buffer)  
    {  
        _vsprintf_p( buffer, len, format, args );  
        puts( buffer );  
        free( buffer );  
    }  
}  
  
int main( void )  
{  
    // First example  
    example( "%2$d %1$c %3$d", '<', 123, 456 );  
  
    // Second example  
    example( "%s", "This is a string" );  
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