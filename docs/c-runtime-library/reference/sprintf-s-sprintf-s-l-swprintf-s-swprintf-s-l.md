---
title: "sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _swprintf_s_l
- _sprintf_s_l
- swprintf_s
- sprintf_s
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
- swprintf_s
- sprintf_s
- stdio/sprintf_s
- stdio/swprintf_s
- stdio/_sprintf_s_l
- stdio/_swprintf_s_l
- _sprintf_s_l
- _swprintf_s_l
dev_langs: C++
helpviewer_keywords:
- stprintf_s function
- stprintf_s_l function
- swprintf_s_l function
- sprintf_s function
- swprintf_s function
- _swprintf_s_l function
- sprintf_s_l function
- _stprintf_s_l function
- _stprintf_s function
- _sprintf_s_l function
- formatted text [C++]
ms.assetid: 424f0a29-22ef-40e8-b565-969f5f57782f
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e1dda25ab045262dffb34085519f4cf8b8bf226c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="sprintfs-sprintfsl-swprintfs-swprintfsl"></a>sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l
将设置格式的数据写入字符串。 如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述，这些版本的 [sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) 具有安全性增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
int sprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   const char *format,  
   ...   
);  
int _sprintf_s_l(  
   char *buffer,  
   size_t sizeOfBuffer,  
   const char *format,  
   locale_t locale,  
   ...   
);  
int swprintf_s(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   const wchar_t *format,  
   ...  
);  
int _swprintf_s_l(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   const wchar_t *format,  
   locale_t locale,  
   ...  
);  
template <size_t size>  
int sprintf_s(  
   char (&buffer)[size],  
   const char *format,  
   ...   
); // C++ only  
template <size_t size>  
int swprintf_s(  
   wchar_t (&buffer)[size],  
   const wchar_t *format,  
   ...  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 `buffer`  
 输出的存储位置  
  
 `sizeOfBuffer`  
 可存储的最多字符数。  
  
 `format`  
 格式控件字符串  
  
 `...`  
 要设置格式的可选参数  
  
 `locale`  
 要使用的区域设置。  
  
 有关更多信息，请参见 [格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## <a name="return-value"></a>返回值  
 写入的字符数或-1，如果出现错误。 如果 `buffer` 或 `format` 是 null 指针， `sprintf_s` 和 `swprintf_s` 将返回 -1 并将 `errno` 设置为 `EINVAL`。  
  
 `sprintf_s` 返回存储在 `buffer`中的字节数，不包括终止 null 字符。 `swprintf_s` 返回存储在 `buffer`中的宽字符数，不包括中止 null 宽字符。  
  
## <a name="remarks"></a>备注  
 `sprintf_s` 函数存储 `buffer` 中的一系列字符和值并设置格式。 每个 `argument` （如果有）根据 `format`中相应的格式规范进行转换和输出。 该格式包括普通字符，其形式和函数与 `format` printf [的](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)参数相同。 null 字符追加在写入的最后一个字符后。 如果在重叠的字符串之间发生复制，则此行为不确定。  
  
 `sprintf_s` 和 `sprintf` 之间的一个主要区别是， `sprintf_s` 检查格式字符串中的有效格式设置字符，而 `sprintf` 仅检查格式字符串或缓冲区是否为 `NULL` 指针。 如果任一检查失败，将调用无效参数处理程序，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将返回 -1 并将 `errno` 设置为 `EINVAL`。  
  
 `sprintf_s` 和 `sprintf` 之间的另一主要区别是， `sprintf_s` 使用长度参数来指定字符中输出缓冲区的大小。 如果缓冲区对于格式化文本（包括终止 null）来说太小，则将通过在 `buffer[0]`处放置 null 字符而将缓冲区设置为空字符串，并调用无效的参数处理程序。 与 `_snprintf`不同， `sprintf_s` 可保证缓冲区以 null 终止（除非缓冲区大小为零）。  
  
 `swprintf_s` 是 `sprintf_s`的宽字符版本； `swprintf_s` 的指针参数是宽字符串。 `swprintf_s` 中的编码错误检测可能与 `sprintf_s` 中的不同。 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
 在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度（不再需要指定大小参数），并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
 `sprintf_s` 的一些版本可在缓冲区过小时对所发生的情况进行更多控制。 有关更多信息，请参见 [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](../../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_stprintf_s`|`sprintf_s`|`sprintf_s`|`swprintf_s`|  
|`_stprintf_s_l`|`_sprintf_s_l`|`_sprintf_s_l`|`_swprintf_s_l`|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`sprintf_s`， `_sprintf_s_l`|C: \<stdio.h><br /><br /> C++: \<cstdio> 或 \<stdio.h>|  
|`swprintf_s`， `_swprintf_s_l`|C: \<stdio.h> 或 \<wchar.h><br /><br /> C++: \<cstdio>、\<cwchar>、\<stdio.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_sprintf_s.c  
// This program uses sprintf_s to format various  
// data and place them in the string named buffer.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   char  buffer[200], s[] = "computer", c = 'l';  
   int   i = 35, j;  
   float fp = 1.7320534f;  
  
   // Format and print various data:   
   j  = sprintf_s( buffer, 200,     "   String:    %s\n", s );  
   j += sprintf_s( buffer + j, 200 - j, "   Character: %c\n", c );  
   j += sprintf_s( buffer + j, 200 - j, "   Integer:   %d\n", i );  
   j += sprintf_s( buffer + j, 200 - j, "   Real:      %f\n", fp );  
  
   printf_s( "Output:\n%s\ncharacter count = %d\n", buffer, j );  
}  
```  
  
```Output  
Output:  
   String:    computer  
   Character: l  
   Integer:   35  
   Real:      1.732053  
  
character count = 79  
```  
  
## <a name="example"></a>示例  
  
```  
// crt_swprintf_s.c  
// wide character example  
// also demonstrates swprintf_s returning error code  
#include <stdio.h>  
  
int main( void )  
{  
   wchar_t buf[100];  
   int len = swprintf_s( buf, 100, L"%s", L"Hello world" );  
   printf( "wrote %d characters\n", len );  
   len = swprintf_s( buf, 100, L"%s", L"Hello\xffff world" );  
   // swprintf_s fails because string contains WEOF (\xffff)  
   printf( "wrote %d characters\n", len );  
}  
```  
  
```Output  
wrote 11 characters  
wrote -1 characters  
```  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fprintf、_fprintf_l、fwprintf、_fwprintf_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、_printf_l、wprintf、_wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf、_scanf_l、wscanf、_wscanf_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf、_sscanf_l、swscanf、_swscanf_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)