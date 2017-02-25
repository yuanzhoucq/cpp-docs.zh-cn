---
title: "sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_sscanf_s_l"
  - "sscanf_s"
  - "_swscanf_s_l"
  - "swscanf_s"
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
  - "_stscanf_s"
  - "sscanf_s"
  - "swscanf_s"
  - "_swscanf_s_l"
  - "_stscanf_s_l"
  - "_sscanf_s_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_sscanf_s_l 函数"
  - "_stscanf_s 函数"
  - "_stscanf_s_l 函数"
  - "_swscanf_s_l 函数"
  - "读取数据, 字符串"
  - "sscanf_s 函数"
  - "sscanf_s_l 函数"
  - "字符串 [C++], 读取"
  - "字符串 [C++], 读取数据自"
  - "stscanf_s 函数"
  - "stscanf_s_l 函数"
  - "swscanf_s 函数"
  - "swscanf_s_l 函数"
ms.assetid: 956e65c8-00a5-43e8-a2f2-0f547ac9e56c
caps.latest.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 30
---
# sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

读取格式化字符串中的数据。 这些版本的 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md) 具有安全增强功能，如中所述 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 语法  
  
```  
int sscanf_s(  
   const char *buffer,  
   const char *format [,  
   argument ] ...  
);  
int _sscanf_s_l(  
   const char *buffer,  
   const char *format,  
   locale_t locale [,  
   argument ] ...  
);  
int swscanf_s(  
   const wchar_t *buffer,  
   const wchar_t *format [,  
   argument ] ...  
);  
int _swscanf_s_l(  
   const wchar_t *buffer,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ] ...  
);  
```  
  
#### 参数  
 `buffer`  
 存储的数据  
  
 `format`  
 窗体控件字符串。 有关详细信息，请参阅[格式规范字段：scanf 和 wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  
  
 `argument`  
 可选自变量  
  
 `locale`  
 要使用的区域设置  
  
## 返回值  
 其中每个函数将返回成功转换并分配; 的字段数返回值不包括已读取但未分配的字段。 返回值为 0 表示没有分配任何字段。 返回值是 `EOF` 是否有错误或如果在第一次转换之前到达字符串结尾。  
  
 如果 `buffer` 或 `format` 是 `NULL` 调用指针，无效参数处理程序，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许继续执行，则这些函数返回 \-1 并将 `errno` 设置为 `EINVAL`  
  
 有关这些和其他错误代码的信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `sscanf_s` 函数将读取数据从 `buffer` 到由每个给出的位置 `argument`。 格式字符串之后的参数指定指向具有对应于中的类型说明符的类型的变量的指针 `format`。 与安全级别较低版本不同 `sscanf`, ，使用类型字段字符时，缓冲区大小参数是必需 `c`, ，`C`, ，`s`, ，`S`, ，或字符串中包含的控件集 `[]`。 以字符为单位的缓冲区大小必须在每个缓冲区参数，它需要它后立即提供作为一个附加参数。 例如，如果您正在读取为一个字符串，该字符串的缓冲区大小传递，如下所示︰  
  
 `wchar_t ws[10];`  
  
 `swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9`  
  
 缓冲区大小包括终止 null 字符。 宽度规范字段可能用于确保在中读取的标记可放入缓冲区。 如果未使用任何宽度规范字段，并且读取的标记太大以致缓冲区中无法容纳，则不会向该缓冲区写入任何内容。  
  
 对于字符，可读取单个字符，如下所示：  
  
 `wchar_t wc;`  
  
 `swscanf_s(in_str, L"%c", &wc, 1);`  
  
 此示例在输入字符串中读取单个字符，并将其存储在宽字符缓冲区中。 在阅读非 null 终止的字符串的多个字符时，无符号的整数用作宽度规范和缓冲区大小。  
  
 `char c[4];`  
  
 `sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated`  
  
 有关详细信息，请参阅 [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) 和 [scanf 类型字段字符](../../c-runtime-library/scanf-type-field-characters.md)。  
  
> [!NOTE]
>  大小参数的类型具有 `unsigned`，而不具有 `size_t`。 在为 64 位目标编译时，使用静态强制转换来转换 `_countof` 或 `sizeof` 结果为正确的大小。  
  
 `format` 参数控件输入解释字段，并具有相同的形式和函数与 `format` 参数 `scanf_s` 函数。 如果在重叠的字符串之间发生复制，则此行为不确定。  
  
 `swscanf_s` 是的宽字符版本 `sscanf_s;` 参数与 `swscanf_s` 都是宽字符字符串。`sscanf_s` 不处理多字节的十六进制字符。`swscanf_s` 不处理 Unicode 全角十六进制或"兼容性区"字符。 除此以外，`swscanf_s` 和 `sscanf_s` 的行为完全相同。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_stscanf_s`|`sscanf_s`|`sscanf_s`|`swscanf_s`|  
|`_stscanf_s_l`|`_sscanf_s_l`|`_sscanf_s_l`|`_swscanf_s_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`sscanf_s`, `_sscanf_s_l`|\<stdio.h\>|  
|`swscanf_s`, `_swscanf_s_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_sscanf_s.c  
// This program uses sscanf_s to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char  tokenstring[] = "15 12 14...";  
   char  s[81];  
   char  c;  
   int   i;  
   float fp;  
  
   // Input various data from tokenstring:  
   // max 80 character string plus NULL terminator  
   sscanf_s( tokenstring, "%s", s, (unsigned)_countof(s) );  
   sscanf_s( tokenstring, "%c", &c, (unsigned)sizeof(char) );  
   sscanf_s( tokenstring, "%d", &i );  
   sscanf_s( tokenstring, "%f", &fp );  
  
   // Output the data read  
   printf_s( "String    = %s\n", s );  
   printf_s( "Character = %c\n", c );  
   printf_s( "Integer:  = %d\n", i );  
   printf_s( "Real:     = %f\n", fp );  
}  
```  
  
```Output  
字符串 = 15 个字符 = 1 的整数︰ 实际 = 15: = 15.000000  
```  
  
## .NET Framework 等效项  
 请参阅 `Parse` 方法，如 [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fscanf、\_fscanf\_l、fwscanf、\_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [snprintf、\_snprintf、\_snprintf\_l、\_snwprintf、\_snwprintf\_l](../../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)