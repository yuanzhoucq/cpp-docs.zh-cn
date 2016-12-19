---
title: "sscanf、_sscanf_l、swscanf、_swscanf_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "swscanf"
  - "sscanf"
  - "_sscanf_l"
  - "_swscanf_l"
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
  - "_sscanf_l"
  - "_stscanf"
  - "swscanf"
  - "_stscanf_l"
  - "sscanf"
  - "_swscanf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_sscanf_l 函数"
  - "_stscanf 函数"
  - "_stscanf_l 函数"
  - "_swscanf_l 函数"
  - "读取数据, 字符串"
  - "sscanf 函数"
  - "sscanf_l 函数"
  - "字符串 [C++], 读取"
  - "字符串 [C++], 读取数据自"
  - "stscanf 函数"
  - "stscanf_l 函数"
  - "swscanf 函数"
  - "swscanf_l 函数"
ms.assetid: c2dcf0d2-9798-499f-a4a8-06f7e2b9a80c
caps.latest.revision: 26
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sscanf、_sscanf_l、swscanf、_swscanf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从字符串中读取格式化数据。  提供这些函数的更多安全版本；请参见 [sscanf\_s、\_sscanf\_s\_l、swscanf\_s、\_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)。  
  
## 语法  
  
```  
int sscanf(  
   const char *buffer,  
   const char *format [,  
   argument ] ...   
);  
int _sscanf_l(  
   const char *buffer,  
   const char *format,  
   locale_t locale [,  
   argument ] ...   
);  
int swscanf(  
   const wchar_t *buffer,  
   const wchar_t *format [,  
   argument ] ...   
);  
int _swscanf_l(  
   const wchar_t *buffer,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ] ...   
);  
```  
  
#### 参数  
 `buffer`  
 已存储的数据  
  
 `format`  
 窗体控件字符串。  有关更多信息，请参见[格式规范](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  
  
 `argument`  
 可选参数  
  
 `locale`  
 要使用的区域设置  
  
## 返回值  
 每个函数返回成功转换并分配的字段数量；返回值不包括已读取但未分配的字段。  返回值为 0 表示未分配字段。  如果出现错误，或者，如果在第一个转换之前到达字符串的末尾，则返回值是 `EOF`。  
  
 如果 `buffer` 或 `format` 是 `NULL` 指针，无效参数处理器程序将按 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述进行调用。  如果允许执行继续，则这些函数返回 \-1 并将 `errno` 设置为 `EINVAL`。  
  
 有关这些属性和其他错误代码的信息，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `sscanf` 函数读取 `buffer` 的数据到每个 `argument`给出的位置。   `argument` 列表中的每个参数必须是指向类型变量的指针，此类型需与`format`中的类型说明符对应。  `format` 参数控制输入字段的解释，并且形式和函数都与 `scanf` 功能的 `format` 参数相同。  如果复制出现在重叠的字符串之间，则该行为不确定。  
  
> [!IMPORTANT]
>  用 `sscanf` 读取字符串时，始终指定 `%s` 格式的宽度（例如，`"%32s"` 而非 `"%s"`）；否则，不适当的格式输入可能会导致缓冲区溢出。  
  
 `swscanf` 是 `sscanf` 的宽字符版本；`swscanf` 的参数是宽字符串。  `sscanf`不处理多字节十六进制字符。  `swscanf` 不处理 Unicode 全角十六进制或“兼容性区域”字符。  除此以外，`swscanf` 和 `sscanf` 的行为完全相同。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|\_UNICODE & \_MBCS not defined|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------------|----------------|-------------------|  
|`_stscanf`|`sscanf`|`sscanf`|`swscanf`|  
|`_stscanf_l`|`_sscanf_l`|`_sscanf_l`|`_swscanf_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`sscanf`, `_sscanf_l`|\<stdio.h\>|  
|`swscanf`, `_swscanf_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_sscanf.c  
// compile with: /W3  
// This program uses sscanf to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char  tokenstring[] = "15 12 14...";  
   char  s[81];  
   char  c;  
   int   i;  
   float fp;  
  
   // Input various data from tokenstring:  
   // max 80 character string:  
   sscanf( tokenstring, "%80s", s ); // C4996  
   sscanf( tokenstring, "%c", &c );  // C4996  
   sscanf( tokenstring, "%d", &i );  // C4996  
   sscanf( tokenstring, "%f", &fp ); // C4996  
   // Note: sscanf is deprecated; consider using sscanf_s instead  
  
   // Output the data read  
   printf( "String    = %s\n", s );  
   printf( "Character = %c\n", c );  
   printf( "Integer:  = %d\n", i );  
   printf( "Real:     = %f\n", fp );  
}  
```  
  
  **字符串 \= 15**  
**字符“\= 1”**  
**整数：\= 15**  
**Real：\= 15.000000**   
## .NET Framework 等效项  
 请参见 `Parse` 方法，如 [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fscanf、\_fscanf\_l、fwscanf、\_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [snprintf、\_snprintf、\_snprintf\_l、\_snwprintf、\_snwprintf\_l](../../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)