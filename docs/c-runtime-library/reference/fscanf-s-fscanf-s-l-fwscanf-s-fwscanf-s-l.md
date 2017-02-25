---
title: "fscanf_s、_fscanf_s_l、fwscanf_s、_fwscanf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fwscanf_s"
  - "_fscanf_s_l"
  - "_fwscanf_s_l"
  - "fscanf_s"
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
  - "_fwscanf_s_l"
  - "_fscanf_s_l"
  - "fscanf_s"
  - "_ftscanf_s_l"
  - "_ftscanf_s"
  - "fwscanf_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fscanf_s_l 函数"
  - "_ftscanf_s 函数"
  - "_ftscanf_s_l 函数"
  - "_fwscanf_s_l 函数"
  - "数据 [CRT], 从流中读取"
  - "格式化的数据 [C++], 从流中读取"
  - "fscanf_s 函数"
  - "fscanf_s_l 函数"
  - "ftscanf_s 函数"
  - "ftscanf_s_l 函数"
  - "fwscanf_s 函数"
  - "fwscanf_s_l 函数"
  - "流 [C++], 读取格式化数据自"
ms.assetid: b6e88194-714b-4322-be82-1cc0b343fe01
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# fscanf_s、_fscanf_s_l、fwscanf_s、_fwscanf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从流中读取格式化数据。  [fscanf、\_fscanf\_l、fwscanf、\_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md) 的这些版本如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
## 语法  
  
```  
int fscanf_s(   
   FILE *stream,  
   const char *format [,  
   argument ]...   
);  
int _fscanf_s_l(   
   FILE *stream,  
   const char *format,  
   locale_t locale [,  
   argument ]...   
);  
int fwscanf_s(   
   FILE *stream,  
   const wchar_t *format [,  
   argument ]...   
);  
int _fwscanf_s_l(   
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ]...   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
 `format`  
 窗体控件字符串。  
  
 `argument`  
 可选参数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 每个函数返回成功转换并分配的字段数量；返回值不包括已读取但未分配的字段。  返回值为 0 表示未分配字段。  如果出现错误，或者，如果在第一个转换之前到达文件流的末尾，则返回值是 `fscanf_s` 的 `EOF` 和 `fwscanf_s`。  
  
 这些函数验证其参数。  如果 `stream` 是无效的文件指针，或者 `format` 是 null 指针，则这些函数将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，则这些函数返回 `EOF` 并将 `errno` 设置为 `EINVAL`。  
  
## 备注  
 `fscanf_s` 函数从 `stream` 当前位置中读取数据到由 `argument` 参数列表（如果有）给定的位置中。   `argument` 列表中的每个参数必须是指向类型变量的指针，此类型需与`format`中的类型说明符对应。  `format` 控件输入字段的说明并且具有的窗体和函数和 `scanf_s`的 `format` 参数相同；想了解 `format`的声明，请参见 [格式规范字段：scanf 和 wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md) 。`fwscanf_s` 是 `fscanf_s`的宽字符版本； `fwscanf_s` 的 format 参数是宽字符字符串。  如果流在 ANSI 模式中打开，这些函数具有相同的行为。  `fscanf_s` 当前不支持 UNICODE 流的输入。  
  
 更安全函数（具有 `_s` 后缀）和其他版本之间的主要差异在于更安全函数需要每个 `c`、`C`、`s`、`S` 和 `[` 类型字段的字符数作为紧跟该变量的参数传递。  有关更多信息，请参见[scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)和[scanf 宽度规范](../../c-runtime-library/scanf-width-specification.md)。  
  
> [!NOTE]
>  大小参数的类型为 `unsigned` 而非 `size_t`。  
  
 这些带有 `_l` 后缀的函数的版本相同，除了它们传递的是区域设置参数而不是当前线程区域设置。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_ftscanf_s`|`fscanf_s`|`fscanf_s`|`fwscanf_s`|  
|`_ftscanf_s_l`|`_fscanf_s_l`|`_fscanf_s_l`|`_fwscanf_s_l`|  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fscanf_s`, `_fscanf_s_l`|\<stdio.h\>|  
|`fwscanf_s`, `_fwscanf_s_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fscanf_s.c  
// This program writes formatted  
// data to a file. It then uses fscanf to  
// read the various data back from the file.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
FILE *stream;  
  
int main( void )  
{  
   long l;  
   float fp;  
   char s[81];  
   char c;  
  
   errno_t err = fopen_s( &stream, "fscanf.out", "w+" );  
   if( err )  
      printf_s( "The file fscanf.out was not opened\n" );  
   else  
   {  
      fprintf_s( stream, "%s %ld %f%c", "a-string",   
               65000, 3.14159, 'x' );  
      // Set pointer to beginning of file:  
      fseek( stream, 0L, SEEK_SET );  
  
      // Read data back from file:  
      fscanf_s( stream, "%s", s, _countof(s) );  
      fscanf_s( stream, "%ld", &l );  
  
      fscanf_s( stream, "%f", &fp );  
      fscanf_s( stream, "%c", &c, 1 );  
  
      // Output data read:  
      printf( "%s\n", s );  
      printf( "%ld\n", l );  
      printf( "%f\n", fp );  
      printf( "%c\n", c );  
  
      fclose( stream );  
   }  
}  
```  
  
  **一个字符串**  
**65000**  
**3.141590**  
**x**   
## .NET Framework 等效项  
 [System::IO::StreamReader::ReadLine](https://msdn.microsoft.com/en-us/library/system.io.streamreader.readline.aspx).也可参见 `Parse` 方法，如 [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_cscanf\_s、\_cscanf\_s\_l、\_cwscanf\_s、\_cwscanf\_s\_l](../../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)   
 [fprintf\_s、\_fprintf\_s\_l、fwprintf\_s、\_fwprintf\_s\_l](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)   
 [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [sscanf\_s、\_sscanf\_s\_l、swscanf\_s、\_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)   
 [fscanf、\_fscanf\_l、fwscanf、\_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)