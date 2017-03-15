---
title: "vsscanf_s、vswscanf_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "vswscanf_s"
  - "vsscanf_s"
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
  - "vsscanf_s"
  - "vswscanf_s"
  - "_vstscanf_s"
dev_langs: 
  - "C++"
ms.assetid: 7b732e68-c6f4-4579-8917-122f5a7876e1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# vsscanf_s、vswscanf_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从字符串中读取格式化数据。  [vsscanf、vswscanf](../../c-runtime-library/reference/vsscanf-vswscanf.md) 的这些版本如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
## 语法  
  
```  
int vsscanf_s(  
   const char *buffer,  
   const char *format,  
   va_list argptr  
);   
int vswscanf_s(  
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
  
 如果 `buffer` 或 `format` 是 `NULL` 指针，无效参数处理器程序将按 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述进行调用。  如果允许执行继续，则这些函数返回 \-1 并将 `errno` 设置为 `EINVAL`  
  
 有关这些属性和其他错误代码的更多信息，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `vsscanf_s` 函数将 `buffer` 中的数据读取到由 `arglist` 参数列表中每项参数给定的位置中。  参数列表中的参数指定指向具有类型的变量，此类型必须对应于 `format` 中的类型说明符。  不同于较不安全的版本 `vsscanf`，当你使用类型字段字符 `c`、`C`、`s`、 `S` 或封闭在 `[]` 中的字符串控件集时，需要缓冲区域大小参数。  字符中的缓冲区区域大小必须作为其他参数提供，紧跟需要其的每个缓冲区参数。  
  
 缓冲区大小区域包括终止 null。  宽度规范字段可用于确保读取的标记将放入缓冲区。  如果未使用宽度规范字段，而标记读入又太大以致无法容纳在缓冲区中，则该缓冲区将不写入任何内容。  
  
 有关更多信息，请参见[scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)和[scanf 类型字段字符](../../c-runtime-library/scanf-type-field-characters.md)。  
  
> [!NOTE]
>  大小参数的类型为 `unsigned` 而非 `size_t`。  
  
 `format` 参数控制输入字段的解释，并且形式和函数都与 `scanf_s` 功能的 `format` 参数相同。  如果复制出现在重叠的字符串之间，则该行为不确定。  
  
 `vswscanf_s` 是 `vsscanf_s` 的宽字符版本；`vswscanf_s` 的参数是宽字符字符串。  `vsscanf_s` 不处理多字节十六进制字符。  `vswscanf_s` 不处理 Unicode 全角十六进制或“兼容性区域”字符。  否则，`vswscanf_s` 和 `vsscanf_s` 行为相同。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vstscanf_s`|`vsscanf_s`|`vsscanf_s`|`vswscanf_s`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`vsscanf_s`|\<stdio.h\>|  
|`vswscanf_s`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_vsscanf_s.c  
// compile with: /W3  
// This program uses vsscanf_s to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
#include <stdarg.h>  
#include <stdlib.h>  
  
int call_vsscanf_s(char *tokenstring, char *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vsscanf_s(tokenstring, format, arglist);  
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
    call_vsscanf_s(tokenstring, "%80s", s, _countof(s));  
    call_vsscanf_s(tokenstring, "%c", &c, sizeof(char));  
    call_vsscanf_s(tokenstring, "%d", &i);  
    call_vsscanf_s(tokenstring, "%f", &fp);  
  
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
 [sscanf\_s、\_sscanf\_s\_l、swscanf\_s、\_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vsscanf、vswscanf](../../c-runtime-library/reference/vsscanf-vswscanf.md)