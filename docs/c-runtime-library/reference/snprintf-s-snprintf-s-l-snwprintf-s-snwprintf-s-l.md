---
title: "_snprintf_s、_snprintf_s_l、_snwprintf_s、_snwprintf_s_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _snprintf_s
- _snprintf_s_l
- _snwprintf_s
- _snwprintf_s_l
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _snwprintf_s_l
- _sntprintf_s_l
- snprintf_s_l
- _snprintf_s_l
- _sntprintf_s
- _snprintf_s
- snprintf_s
- _snwprintf_s
- snwprintf_s_l
- snwprintf_s
- sntprintf_s
- sntprintf_s_l
dev_langs: C++
helpviewer_keywords:
- _snprintf_s_l function
- _snwprintf_s_l function
- _sntprintf_s_l function
- snwprintf_s_l function
- snprintf_s function
- _snprintf_s function
- snprintf_s_l function
- _sntprintf_s function
- sntprintf_s_l function
- sntprintf_s function
- snwprintf_s function
- _snwprintf_s function
- formatted text [C++]
ms.assetid: 9336ab86-13e5-4a29-a3cd-074adfee6891
caps.latest.revision: "32"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b0af77da88c86cdd42dabd10dd3228a5da405aae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="snprintfs-snprintfsl-snwprintfs-snwprintfsl"></a>_snprintf_s、_snprintf_s_l、_snwprintf_s、_snwprintf_s_l
将格式化的数据写入字符串。 这些版本的 [snprintf、_snprintf、_snprintf_l、_snwprintf、_snwprintf_l](../../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## <a name="syntax"></a>语法  
  
```  
int _snprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format [,  
   argument] ...   
);  
int _snprintf_s_l(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _snwprintf_s(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format [,  
   argument] ...   
);  
int _snwprintf_s_l(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
template <size_t size>  
int _snprintf_s(  
   char (&buffer)[size],  
   size_t count,  
   const char *format [,  
   argument] ...   
); // C++ only  
template <size_t size>  
int _snwprintf_s(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format [,  
   argument] ...   
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 `buffer`  
 输出的存储位置。  
  
 `sizeOfBuffer`  
 输出的存储位置大小。 `_snprintf_s` 的 `bytes` 中的大小或 `_snwprintf_s` 的 `words` 中的大小。  
  
 `Count`  
 可存储的最大字符数，或 [_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 `format`  
 窗体控件字符串。  
  
 `argument`  
 可选参数。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 `_snprintf_s` 返回 `buffer` 中存储的字符数，不包括终止 null 字符。 `_snwprintf_s` 返回存储在 `buffer` 中的宽字符数，不包括中止 null 宽字符。  
  
 如果存储数据和终止 null 所需的存储超过 `sizeOfBuffer`，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果在调用无效参数处理程序后继续执行，这些函数会将 `buffer` 设置为空字符串、`errno` 设置为 `ERANGE`，并返回 -1。  
  
 如果 `buffer` 或 `format` 是一个 `NULL` 指针，或如果 `count` 小于或等于 0，则将调用无效参数处理程序。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 -1。  
  
 有关这些及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `_snprintf_s` 函数格式化并将 `count` 或更少字符存储在 `buffer` 中，并追加终止 null。 每个参数（如果有）根据 `format` 中相应的格式规范进行转换和输出。 格式设置与 `printf` 系列函数一致，请参阅[格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。 如果在重叠的字符串之间发生复制，则此行为不确定。  
  
 如果 `count` 是 [_TRUNCATE](../../c-runtime-library/truncate.md)，则保留终止 null 空间时 `_snprintf_s` 将写入 `buffer` 中可容纳的尽可能多的字符串。 如果在 `buffer` 中可容纳整个字符串（包括终止 null），则 `_snprintf_s` 将返回写入的字符数（不包括终止 null）；否则，`_snprintf_s` 会返回 -1 以指明发生截断。  
  
> [!IMPORTANT]
>  确保 `format` 不是用户定义的字符串。  
  
 `_snwprintf_s` 是 `_snprintf_s`的宽字符版本；`_snwprintf_s` 的指针参数是宽字符串。 `_snwprintf_s` 中对编码错误的检测可能与 `_snprintf_s` 中不同。 `_snwprintf_s` 就像 `swprintf_s`，将输出写入字符串，而非 `FILE` 类型的目标。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
 在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_sntprintf_s`|`_snprintf_s`|`_snprintf_s`|`_snwprintf_s`|  
|`_sntprintf_s_l`|`_snprintf_s_l`|`_snprintf_s_l`|`_snwprintf_s_l`|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_snprintf_s`, `_snprintf_s_l`|\<stdio.h>|  
|`_snwprintf_s`, `_snwprintf_s_l`|\<stdio.h> 或 \<wchar.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
// crt_snprintf_s.cpp  
// compile with: /MTd  
  
// These #defines enable secure template overloads  
// (see last part of Examples() below)  
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1   
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT 1  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <crtdbg.h>  // For _CrtSetReportMode  
#include <errno.h>  
  
// This example uses a 10-byte destination buffer.  
  
int snprintf_s_tester( const char * fmt, int x, size_t count )  
{  
   char dest[10];  
  
   printf( "\n" );  
  
   if ( count == _TRUNCATE )  
      printf( "%zd-byte buffer; truncation semantics\n",  
               _countof(dest) );  
   else  
      printf( "count = %zd; %zd-byte buffer\n",  
               count, _countof(dest) );  
  
   int ret = _snprintf_s( dest, _countof(dest), count, fmt, x );  
  
   printf( "    new contents of dest: '%s'\n", dest );  
  
   return ret;  
}  
  
void Examples()  
{  
   // formatted output string is 9 characters long: "<<<123>>>"  
   snprintf_s_tester( "<<<%d>>>", 121, 8 );  
   snprintf_s_tester( "<<<%d>>>", 121, 9 );  
   snprintf_s_tester( "<<<%d>>>", 121, 10 );  
  
   printf( "\nDestination buffer too small:\n" );  
  
   snprintf_s_tester( "<<<%d>>>", 1221, 10 );  
  
   printf( "\nTruncation examples:\n" );  
  
   int ret = snprintf_s_tester( "<<<%d>>>", 1221, _TRUNCATE );  
   printf( "    truncation %s occur\n", ret == -1 ? "did"  
                                                  : "did not" );  
  
   ret = snprintf_s_tester( "<<<%d>>>", 121, _TRUNCATE );  
   printf( "    truncation %s occur\n", ret == -1 ? "did"  
                                                  : "did not" );  
   printf( "\nSecure template overload example:\n" );  
  
   char dest[10];  
   _snprintf( dest, 10, "<<<%d>>>", 12321 );  
   // With secure template overloads enabled (see #defines  
   // at top of file), the preceding line is replaced by  
   //    _snprintf_s( dest, _countof(dest), 10, "<<<%d>>>", 12345 );  
   // Instead of causing a buffer overrun, _snprintf_s invokes  
   // the invalid parameter handler.  
   // If secure template overloads were disabled, _snprintf would  
   // write 10 characters and overrun the dest buffer.  
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
  
```Output  
  
count = 8; 10-byte buffer  
    new contents of dest: '<<<121>>'  
  
count = 9; 10-byte buffer  
    new contents of dest: '<<<121>>>'  
  
count = 10; 10-byte buffer  
    new contents of dest: '<<<121>>>'  
  
Destination buffer too small:  
  
count = 10; 10-byte buffer  
Invalid parameter handler invoked: ("Buffer too small", 0)  
    new contents of dest: ''  
  
Truncation examples:  
  
10-byte buffer; truncation semantics  
    new contents of dest: '<<<1221>>'  
    truncation did occur  
  
10-byte buffer; truncation semantics  
    new contents of dest: '<<<121>>>'  
    truncation did not occur  
  
Secure template overload example:  
Invalid parameter handler invoked: ("Buffer too small", 0)  
    new contents of dest: ''  
```  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [fprintf、_fprintf_l、fwprintf、_fwprintf_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、_printf_l、wprintf、_wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf、_scanf_l、wscanf、_wscanf_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf、_sscanf_l、swscanf、_swscanf_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)