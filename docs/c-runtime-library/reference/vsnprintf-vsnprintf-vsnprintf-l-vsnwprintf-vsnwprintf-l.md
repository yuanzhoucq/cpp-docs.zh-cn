---
title: "vsnprintf、_vsnprintf、_vsnprintf_l、_vsnwprintf、_vsnwprintf_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vsnprintf"
  - "_vsnprintf_l"
  - "_vsnwprintf"
  - "_vsnwprintf_l"
  - "_vsnprintf"
  - "_vsnprintf;"
  - "vsnprintf; _vsnprintf"
  - "_vsnwprintf;"
  - "_vsnprintf_l;"
  - "_vsnwprintf_l;"
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
  - "ntoskrnl.exe"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_vsnprintf"
  - "_vsnwprintf"
  - "_vsntprintf"
  - "vsnprintf"
  - "stdio/vsnprintf"
  - "stdio/_vsnprintf"
  - "stdio/_vsnprintf_l"
  - "stdio/_vsnwprintf"
  - "stdio/_vsnwprintf_l"
  - "_vsnprintf_l"
  - "_vsnwprintf_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vsntprintf 函数"
  - "_vsnwprintf_l 函数"
  - "vsnwprintf_l 函数"
  - "vsntprintf_l 函数"
  - "_vsntprintf 函数"
  - "_vsnprintf_l 函数"
  - "vsnprintf 函数"
  - "_vsntprintf_l 函数"
  - "vsnprintf_l 函数"
  - "_vsnwprintf 函数"
  - "_vsnprintf 函数"
  - "格式化文本 [C++]"
  - "vsnwprintf 函数"
ms.assetid: a97f92df-c2f8-4ea0-9269-76920d2d566a
caps.latest.revision: 35
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 35
---
# vsnprintf、_vsnprintf、_vsnprintf_l、_vsnwprintf、_vsnwprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用指向参数列表的指针写入格式化的输出。 提供这些函数的更多安全版本；请参阅 [vsnprintf\_s、\_vsnprintf\_s、\_vsnprintf\_s\_l、\_vsnwprintf\_s、\_vsnwprintf\_s\_l](../../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)。  
  
## 语法  
  
```  
int vsnprintf(  
   char *buffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf(  
   char *buffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf_l(  
   char *buffer,  
   size_t count,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vsnwprintf(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vsnwprintf_l(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
template <size_t size>  
int vsnprintf(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnprintf(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnprintf_l(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnwprintf(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnwprintf_l(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
); // C++ only  
```  
  
#### 参数  
 `buffer`  
 输出的存储位置  
  
 `count`  
 要写入的最大字符数。  
  
 `format`  
 格式规范。  
  
 `argptr`  
 指向参数列表的指针。  
  
 `locale`  
 要使用的区域设置。  
  
 有关更多信息，请参见[格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 返回值  
 `vsnprintf` 函数将返回写入的字符数，不包括终止 null 字符。 如果由指定的缓冲区大小 `count` 足够大，无法包含由指定的输出 `format` 和 `argptr`, 的返回值 `vsnprintf` 是的则会写入，如果不包括 null 字符的字符数 `count` 已足够大。 如果返回值是大于 `count` \-1，输出已被截断。 返回值 \-1 指示发生编码错误。  
  
 同时 `_vsnprintf` 和 `_vsnwprintf` 函数将返回写入要写入的字符数是否小于或等于的字符数 `count`; 如果要写入的字符数超过了 `count`, ，则这些函数返回\-1，指示输出已被截断。  
  
 不论之一编写与否，所有这些函数返回值不包括终止 null。 当 `count` 为零，则返回值函数将可写入，没有的字符数包括任何终止 null。 您可以使用此结果为字符串，其终止 null 分配缓冲区空间不足，然后调用再次要填充的缓冲区的函数。  
  
 如果 `format` 是 `NULL`, ，或者如果 `buffer` 为 NULL 和 `count` 不等于零，这些函数将调用无效参数处理程序，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许继续执行，则这些函数返回 \-1 并将 `errno` 设置为 `EINVAL`。  
  
## 备注  
 这些函数中的每一个函数都将采用指向参数列表的指针，然后设置数据的格式并将多达 `count` 个字符写入 `buffer` 指向的内存中。`vsnprintf` 函数始终会写入一个 null 终止符，即使它截断输出。 当使用 `_vsnprintf` 和 `_vsnwprintf` 时，仅当结尾处有空间时，缓冲区才将以 null 终止（即，如果要写入的字符数小于 `count`）。  
  
> [!IMPORTANT]
>  为了防止某些类型的安全风险，请确保 `format` 不是用户定义的字符串。 有关详细信息，请参阅[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
> [!NOTE]
>  若要确保调用 `_vsnprintf`、`_vsnprintf_l`、`_vsnwprintf` 和 `_vsnwprintf_l` 时具有终止 null 的空间，请确保 `count` 严格小于缓冲区长度并在调用此函数之前将缓冲区初始化为 null。  
>   
>  因为 `vsnprintf` 始终写入的终止 null `count` 参数可能等于缓冲区的大小。  
  
 从 Visual Studio 2015 和 Windows 10 中的 UCRT 开始，`vsnprintf` 不再等于 `_vsnprintf`。`vsnprintf` 函数均符合 C99 标准中; `_vnsprintf` 保留与较旧的 Visual Studio 代码向后兼容。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
 在 C\+\+ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vsntprintf`|`_vsnprintf`|`_vsnprintf`|`_vsnwprintf`|  
|`_vsntprintf_l`|`_vsnprintf_l`|`_vsnprintf_l`|`_vsnwprintf_l`|  
  
## 要求  
  
|例程|必需的标头 \(C\)|必需的标头 \(C\+\+\)|  
|--------|-----------------|---------------------|  
|`vsnprintf`, `_vsnprintf`, `_vsnprintf_l`|\<stdio.h\>|\<stdio.h\> 或 \<cstdio\>|  
|`_vsnwprintf`, `_vsnwprintf_l`|\<stdio.h\> 或 \<wchar.h\>|\<stdio.h\>、\<wchar.h\>、\<cstdio\> 或 \<cwchar\>|  
  
 `_vsnprintf`、`_vsnprintf_l`、`_vsnwprintf` 和 `_vsnwprintf_l` 函数是 Microsoft 特定函数。 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```c  
// crt_vsnwprintf.c  
// compile by using: cl /W3 crt_vsnwprintf.c  
  
// To turn off error C4996, define this symbol:  
#define _CRT_SECURE_NO_WARNINGS  
  
#include <stdio.h>  
#include <wtypes.h>  
  
#define BUFFCOUNT (10)  
  
void FormatOutput(LPCWSTR formatstring, ...)  
{  
    int nSize = 0;  
    wchar_t buff[BUFFCOUNT];  
    memset(buff, 0, sizeof(buff));  
    va_list args;  
    va_start(args, formatstring);  
    // Note: _vsnwprintf is deprecated; consider vsnwprintf_s instead  
    nSize = _vsnwprintf(buff, BUFFCOUNT - 1, formatstring, args); // C4996  
    wprintf(L"nSize: %d, buff: %ls\n", nSize, buff);  
}  
  
int main() {  
    FormatOutput(L"%ls %ls", L"Hi", L"there");  
    FormatOutput(L"%ls %ls", L"Hi", L"there!");  
    FormatOutput(L"%ls %ls", L"Hi", L"there!!");  
}  
```  
  
```Output  
nSize: 8、 爱好者︰ Hi 有 nSize: 9、 爱好者︰ Hi 存在 ！nSize:-1，爱好者︰ Hi 存在 ！  
```  
  
 如果您使用 vsnprintf 相反，以及窄字符串参数的行为更改。`count` 参数可以为整个缓冲区的大小，返回值也将如果已写入的字符数 `count` 是否足够大︰  
  
## 示例  
  
```c  
// crt_vsnprintf.c  
// compile by using: cl /W4 crt_vsnprintf.c  
#include <stdio.h>  
#include <stdarg.h> // for va_list, va_start  
#include <string.h> // for memset  
  
#define BUFFCOUNT (10)  
  
void FormatOutput(char* formatstring, ...)  
{  
    int nSize = 0;  
    char buff[BUFFCOUNT];  
    memset(buff, 0, sizeof(buff));  
    va_list args;  
    va_start(args, formatstring);  
    nSize = vsnprintf(buff, sizeof(buff), formatstring, args);  
    printf("nSize: %d, buff: %s\n", nSize, buff);  
}  
  
int main() {  
    FormatOutput("%s %s", "Hi", "there");   //  8 chars + null  
    FormatOutput("%s %s", "Hi", "there!");  //  9 chars + null  
    FormatOutput("%s %s", "Hi", "there!!"); // 10 chars + null  
}  
```  
  
```Output  
nSize: 8、 爱好者︰ Hi 有 nSize: 9、 爱好者︰ Hi 存在 ！nSize: 10、 爱好者︰ Hi 存在 ！  
```  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)   
 [格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)