---
title: "vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vsnwprintf_s"
  - "_vsnwprintf_s_l"
  - "_vsnprintf_s"
  - "vsnprintf_s"
  - "_vsnprintf_s_l"
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
  - "_vsnprintf_s"
  - "_vsntprintf_s"
  - "_vsnwprintf_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_vsnprintf_s 函数"
  - "_vsnprintf_s_l 函数"
  - "_vsntprintf_s 函数"
  - "_vsntprintf_s_l 函数"
  - "_vsnwprintf_s 函数"
  - "_vsnwprintf_s_l 函数"
  - "格式化文本 [C++]"
  - "vsnprintf_s 函数"
  - "vsnprintf_s_l 函数"
  - "vsntprintf_s 函数"
  - "vsntprintf_s_l 函数"
  - "vsnwprintf_s 函数"
  - "vsnwprintf_s_l 函数"
ms.assetid: 147ccfce-58c7-4681-a726-ef54ac1c604e
caps.latest.revision: 30
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编写使用指针参数列表的格式化输出。  [vsnprintf、\_vsnprintf、\_vsnprintf\_l、\_vsnwprintf、\_vsnwprintf\_l](../../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 的一些版本提供安全增强功能（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
int vsnprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf_s_l(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vsnwprintf_s(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vsnwprintf_s_l(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
template <size_t size>  
int _vsnprintf_s(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnwprintf_s(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
); // C++ only  
```  
  
#### 参数  
 `buffer`  
 输出的存储位置。  
  
 `sizeOfBuffer`  
 `buffer` 的输出大小作为字符数。  
  
 `count`  
 最大字符数编写\(不包括终止空字符），或者 [\_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 `format`  
 格式规范。  
  
 `argptr`  
 指向参数列表的指针。  
  
 `locale`  
 要使用的区域设置。  
  
 有关更多信息，请参见[格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 返回值  
 如果输出有错误，`vsnprintf_s`、`_vsnprintf_s` 和 `_vsnwprintf_s` 返回编写的字符数，不包括终止空字符或负值。  `vsnprintf_s` 等同于 `_vsnprintf_s`。  包含`vsnprintf_s` 是符合 ANSI 标准。  保留 `_vnsprintf` 的目的是为了向后兼容。  
  
 如果用来存储数据和终止空的存储区超过 `sizeOfBuffer`，则引发无效参数调用处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述，除非 `count` 是 [\_TRUNCATE](../../c-runtime-library/truncate.md)，在这种情况下，尽可能多的字符串将适合 `buffer` 的编写和返回\-1。  如果对无效参数处理程序后继续执行，则这些功能将`buffer` 设置为空字符串，将 `errno` 设置为 `ERANGE`，并返回 \-1。  
  
 如果 `buffer` 或 `format` 是 `NULL` 指针，或者如果 `count` 小于或等于零，则调用无效参数处理程序。  如果允许执行继续，则这些功能将 `EINVAL` 设置为 `errno` 并返回 \-1。  
  
### 错误情况  
  
|`Condition`|Return|`errno`|  
|-----------------|------------|-------------|  
|`buffer` 为  `NULL`|\-1|`EINVAL`|  
|`format` 为  `NULL`|\-1|`EINVAL`|  
|`count` \<\= 0|\-1|`EINVAL`|  
|`sizeOfBuffer`太小 \(并且 `count` \! \= `_TRUNCATE`\)|\-1\(并且 `buffer` 设置为空字符串）|`ERANGE`|  
  
## 备注  
 这些函数中的每一个采用指向参数列表的指针，然后设置格式并记载到 `count` 特定数据的字符到指向由 `buffer` 并追加终止空的内存中。  
  
 如果 `count` 为 [\_TRUNCATE](../../c-runtime-library/truncate.md)，然后当留出终止空的空间时，这些函数编写尽可能多的字符串去符合 `buffer`。  如果整个字符串 \(与终止空\) 符合 `buffer`，然后这些函数返回编写的字符数 \(不包括终止空）;否则，这些函数返回 \-1 指示截断的发生。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
> [!NOTE]
>  为了确保具有终止空的空间，请确保 `count` 严格小于缓冲区的长度，或者使用 `_TRUNCATE`。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小参数\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vsntprintf_s`|`_vsnprintf_s`|`_vsnprintf_s`|`_vsnwprintf_s`|  
|`_vsntprintf_s_l`|`_vsnprintf_s_l`|`_vsnprintf_s_l`|`_vsnwprintf_s_l`|  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`vsnprintf_s`|\<stdio.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
|`_vsnprintf_s`, `_vsnprintf_s_l`|\<stdio.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
|`_vsnwprintf_s`, `_vsnwprintf_s_l`|\<stdio.h\> 或 \<wchar.h\> 或 \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* 仅对 UNIX V 兼容性是必需的。  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_vsnprintf_s.cpp  
#include <stdio.h>  
#include <wtypes.h>  
  
void FormatOutput(LPCSTR formatstring, ...)   
{  
   int nSize = 0;  
   char buff[10];  
   memset(buff, 0, sizeof(buff));  
   va_list args;  
   va_start(args, formatstring);  
   nSize = vsnprintf_s( buff, _countof(buff), _TRUNCATE, formatstring, args);  
   printf("nSize: %d, buff: %s\n", nSize, buff);  
}  
  
int main() {  
   FormatOutput("%s %s", "Hi", "there");  
   FormatOutput("%s %s", "Hi", "there!");  
   FormatOutput("%s %s", "Hi", "there!!");  
}  
```  
  
  **nSize: 8, buff: Hi there**  
**nSize: 9, buff: Hi there\!**  
**nSize: 1, buff: Hi there\!**   
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)