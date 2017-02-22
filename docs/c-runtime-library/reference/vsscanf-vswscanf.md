---
title: "vsscanf、vswscanf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "vsscanf"
  - "vswscanf"
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
  - "_vstscanf"
  - "vsscanf"
  - "vswscanf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vsscanf 函数"
  - "vswscanf 函数"
ms.assetid: e96180f2-df46-423d-b4eb-0a49ab819bde
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# vsscanf、vswscanf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从字符串中读取格式化数据。  有关这些函数的更多安全版本，请参见 [vsscanf\_s、vswscanf\_s](../../c-runtime-library/reference/vsscanf-s-vswscanf-s.md)。  
  
## 语法  
  
```  
int vsscanf(  
   const char *buffer,  
   const char *format,  
   va_list arglist  
);  
int vswscanf(  
   const wchar_t *buffer,  
   const wchar_t *format,  
   va_list arglist  
);  
```  
  
#### 参数  
 `buffer`  
 已存储的数据  
  
 `format`  
 窗体控件字符串。  有关详细信息，请参阅 [格式规范字段：scanf 和 wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  
  
 `arglist`  
 变量参数列表。  
  
## 返回值  
 每个函数返回成功转换并分配的字段数量；返回值不包括已读取但未分配的字段。  返回值为 0 表示未分配字段。  如果出现错误，或者，如果在第一个转换之前到达字符串的末尾，则返回值是 `EOF`。  
  
 如果 `buffer` 或 `format` 是 `NULL` 指针，无效参数处理器程序将按 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述进行调用。  如果允许执行继续，则这些函数返回 \-1 并将 `errno` 设置为 `EINVAL`。  
  
 有关这些属性和其他错误代码的更多信息，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `vsscanf` 函数将从 `buffer` 读取的数据写入由 `arglist` 参数列表每项参数给定的位置中。  列表中的每个参数都必须是指向某个变量的指针，该变量类型与 `format` 中的类型说明符相对应。  `format` 参数控制输入字段的解释，并且形式和函数都与 `scanf` 功能的 `format` 参数相同。  如果复制出现在重叠的字符串之间，则该行为不确定。  
  
> [!IMPORTANT]
>  当使用 `vsscanf` 读取字符串时，始终指定 `%s` 格式的宽度（例如，`"%32s"` 而非 `"%s"`）；否则，不正确的格式输入可能会导致缓冲区溢出。  
  
 `vswscanf` 是 `vsscanf` 的宽字符版本；`vswscanf` 的参数是宽字符字符串。  `vsscanf` 不处理多字节十六进制字符。  `vswscanf` 不处理 Unicode 全角十六进制或“兼容性区域”字符。  否则，`vswscanf` 和 `vsscanf` 行为相同。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vstscanf`|`vsscanf`|`vsscanf`|`vswscanf`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`vsscanf`|\<stdio.h\>|  
|`vswscanf`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_vsscanf.c  
// compile with: /W3  
// This program uses vsscanf to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
#include <stdarg.h>  
  
int call_vsscanf(char *tokenstring, char *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vsscanf(tokenstring, format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main( void )  
{  
    char  tokenstring[] = "15 12 14...";  
    char  s[81];  
    char  c;  
    int   i;  
    float fp;  
  
    // Input various data from tokenstring:  
    // max 80 character string:  
    call_vsscanf(tokenstring, "%80s", s);  
    call_vsscanf(tokenstring, "%c", &c);  
    call_vsscanf(tokenstring, "%d", &i);  
    call_vsscanf(tokenstring, "%f", &fp);  
  
    // Output the data read  
    printf("String    = %s\n", s);  
    printf("Character = %c\n", c);  
    printf("Integer:  = %d\n", i);  
    printf("Real:     = %f\n", fp);  
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
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vsscanf\_s、vswscanf\_s](../../c-runtime-library/reference/vsscanf-s-vswscanf-s.md)