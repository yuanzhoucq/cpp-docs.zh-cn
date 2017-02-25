---
title: "vfscanf、vfwscanf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "vfwscanf"
  - "vfscanf"
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
  - "vfwscanf"
  - "_vftscanf"
  - "vfscanf"
dev_langs: 
  - "C++"
ms.assetid: c06450ef-03f1-4d24-a8ac-d2dd98847918
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# vfscanf、vfwscanf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从流中读取格式化数据。  有关这些函数的更多安全版本，请参见 [vfscanf\_s、vfwscanf\_s](../../c-runtime-library/reference/vfscanf-s-vfwscanf-s.md)。  
  
## 语法  
  
```  
int vfscanf(   
   FILE *stream,  
   const char *format,  
   va_list argptr   
);  
int vfwscanf(   
   FILE *stream,  
   const wchar_t *format,  
   va_list argptr   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
 `format`  
 窗体控件字符串。  
  
 `arglist`  
 变量参数列表。  
  
## 返回值  
 每个函数返回成功转换并分配的字段数量；返回值不包括已读取但未分配的字段。  返回值为 0 表示未分配字段。  如果出现错误，或者，如果文件流的末尾在第一个转换之前到达，则返回值是 `vfscanf` 和 `vfwscanf`的 `EOF`。  
  
 这些函数验证其参数。  如果 `stream` 或 `format` 是 null 指针，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，则这些函数返回 `EOF` 并将 `errno` 设置为 `EINVAL`。  
  
## 备注  
 `vfscanf` 函数将 `stream` 当前位置中的数据读取到由 `arglist` 参数列表给定的位置中。  列表中的每个参数必须是指向类型变量的指针，此类型需与 `format` 中的类型说明符对应。  `format` 可控制输入字段的解释，并且形式和功能与 `scanf` 的 `format` 参数相同；请参见 [scanf](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 了解 `format` 的相关介绍。  
  
 `vfwscanf` 是 `vfscanf` 的宽字符版本；`vfwscanf` 的格式参数是宽字符字符串。  如果流在 ANSI 模式中打开，这些函数具有相同的行为。  `vfscanf` 不支持 UNICODE 流的输入。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vftscanf`|`vfscanf`|`vfscanf`|`vfwscanf`|  
  
 有关详细信息，请参阅 [格式规范字段：scanf 和 wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`vfscanf`|\<stdio.h\>|  
|`vfwscanf`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_vfscanf.c  
// compile with: /W3  
// This program writes formatted  
// data to a file. It then uses vfscanf to  
// read the various data back from the file.  
  
#include <stdio.h>  
#include <stdarg.h>  
  
FILE *stream;  
  
int call_vfscanf(FILE * istream, char * format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vfscanf(istream, format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main(void)  
{  
    long l;  
    float fp;  
    char s[81];  
    char c;  
  
    if (fopen_s(&stream, "vfscanf.out", "w+") != 0)  
    {  
        printf("The file vfscanf.out was not opened\n");  
    }  
    else  
    {  
        fprintf(stream, "%s %ld %f%c", "a-string",  
            65000, 3.14159, 'x');  
        // Security caution!  
        // Beware loading data from a file without confirming its size,  
        // as it may lead to a buffer overrun situation.  
  
        // Set pointer to beginning of file:  
        fseek(stream, 0L, SEEK_SET);  
  
        // Read data back from file:  
        call_vfscanf(stream, "%s %ld %f%c", s, &l, &fp, &c);  
  
        // Output data read:   
        printf("%s\n", s);  
        printf("%ld\n", l);  
        printf("%f\n", fp);  
        printf("%c\n", c);  
  
        fclose(stream);  
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
 [vfscanf\_s、vfwscanf\_s](../../c-runtime-library/reference/vfscanf-s-vfwscanf-s.md)