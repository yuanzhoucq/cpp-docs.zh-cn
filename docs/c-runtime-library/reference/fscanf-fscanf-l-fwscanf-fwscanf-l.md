---
title: "fscanf、_fscanf_l、fwscanf、_fwscanf_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fscanf"
  - "_fwscanf_l"
  - "_fscanf_l"
  - "fwscanf"
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
  - "fscanf"
  - "fwscanf"
  - "_ftscanf_l"
  - "_fwscanf_l"
  - "_ftscanf"
  - "_fscanf_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fscanf_l 函数"
  - "_ftscanf 函数"
  - "_ftscanf_l 函数"
  - "_fwscanf_l 函数"
  - "数据 [CRT], 从流中读取"
  - "格式化的数据 [C++], 从流中读取"
  - "fscanf 函数"
  - "fscanf_l 函数"
  - "ftscanf 函数"
  - "ftscanf_l 函数"
  - "fwscanf 函数"
  - "fwscanf_l 函数"
  - "流 [C++], 读取格式化数据自"
ms.assetid: 9004e978-6c5f-4bb2-98fd-51e5948933f2
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# fscanf、_fscanf_l、fwscanf、_fwscanf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从流中读取格式化数据。  提供这些函数的更多安全版本；请参见 [fscanf\_s、\_fscanf\_s\_l、fwscanf\_s、\_fwscanf\_s\_l](../../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)。  
  
## 语法  
  
```  
int fscanf(   
   FILE *stream,  
   const char *format [,  
   argument ]...   
);  
int _fscanf_l(   
   FILE *stream,  
   const char *format,  
   locale_t locale [,  
   argument ]...   
);  
int fwscanf(   
   FILE *stream,  
   const wchar_t *format [,  
   argument ]...   
);  
int _fwscanf_l(   
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
 每个函数返回成功转换并分配的字段数量；返回值不包括已读取但未分配的字段。  返回值为 0 表示未分配字段。  如果出现错误，或者，如果在第一个转换之前到达文件流的末尾，则返回值是 `fscanf` 的 `EOF` 和 `fwscanf`。  
  
 这些函数验证其参数。  如果 `stream` 或 `format` 是 null 指针，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，则这些函数返回 `EOF` 并将 `errno` 设置为 `EINVAL`。  
  
## 备注  
 `fscanf` 函数从 `stream` 当前位置中读取数据到由 `argument` 参数列表（如果有）给定的位置中。   `argument` 列表中的每个参数必须是指向类型变量的指针，此类型需与`format`中的类型说明符对应。  `format` 可控制输入字段的解释，并且形式和功能与 `scanf` 的 `format` 参数相同；请参见 [scanf](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 了解 `format` 的相关介绍。  
  
 `fwscanf` 是 `fscanf` 的宽字符版本；`fwscanf` 的格式参数是宽字符字符串。  如果流在 ANSI 模式中打开，这些函数具有相同的行为。  `fscanf` 当前不支持 UNICODE 流的输入。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE 和 & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|-------------------------------|----------------|-------------------|  
|`_ftscanf`|`fscanf`|`fscanf`|`fwscanf`|  
|`_ftscanf_l`|`_fscanf_l`|`_fscanf_l`|`_fwscanf_l`|  
  
 有关详细信息，请参阅 [格式规范字段— scanf 和 wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fscanf`, `_fscanf_l`|\<stdio.h\>|  
|`fwscanf`, `_fwscanf_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fscanf.c  
// compile with: /W3  
// This program writes formatted  
// data to a file. It then uses fscanf to  
// read the various data back from the file.  
  
#include <stdio.h>  
  
FILE *stream;  
  
int main( void )  
{  
   long l;  
   float fp;  
   char s[81];  
   char c;  
  
   if( fopen_s( &stream, "fscanf.out", "w+" ) != 0 )  
      printf( "The file fscanf.out was not opened\n" );  
   else  
   {  
      fprintf( stream, "%s %ld %f%c", "a-string",   
               65000, 3.14159, 'x' );  
      // Security caution!  
      // Beware loading data from a file without confirming its size,  
      // as it may lead to a buffer overrun situation.  
  
      // Set pointer to beginning of file:  
      fseek( stream, 0L, SEEK_SET );  
  
      // Read data back from file:  
      fscanf( stream, "%s", s );   // C4996  
      fscanf( stream, "%ld", &l ); // C4996  
  
      fscanf( stream, "%f", &fp ); // C4996  
      fscanf( stream, "%c", &c );  // C4996  
      // Note: fscanf is deprecated; consider using fscanf_s instead  
  
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
 [\_cscanf、\_cscanf\_l、\_cwscanf、\_cwscanf\_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [fscanf\_s、\_fscanf\_s\_l、fwscanf\_s、\_fwscanf\_s\_l](../../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)