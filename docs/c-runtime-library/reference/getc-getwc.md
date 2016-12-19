---
title: "getc、getwc | Microsoft Docs"
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
  - "getwc"
  - "getc"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_gettc"
  - "getwc"
  - "_gettchar"
  - "getc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_gettc 函数"
  - "字符, 读取"
  - "getc 函数"
  - "gettc 函数"
  - "getwc 函数"
  - "getwchar 函数"
  - "从流中读取字符"
  - "流, 读取字符自"
ms.assetid: 354ef514-d0c7-404b-92f5-995f6a834bb3
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# getc、getwc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从流中读取一个字符。  
  
## 语法  
  
```  
int getc(   
   FILE *stream   
);  
wint_t getwc(   
   FILE *stream   
);  
```  
  
#### 参数  
 `stream`  
 输入流。  
  
## 返回值  
 返回读取的字符。  若要指示读取错误或文件结束的条件，`getc` 返回`EOF`， `getwc` 返回 `WEOF`。  对于 `getc`，请使用 `ferror` 或 `feof` 来检查是否有错误或文件结束。  如果 `stream`是`NULL`，`getc` 和`getwc`调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则这些函数返回 `EOF`\(或`getwc`的`WEOF`），并设置`errno`为`EINVAL`。  
  
 有关这些内容的更多信息以及其他错误代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 每个例程读取文件当前位置的单个字符并将文件指针 \(如果定义\) 指向下一字符。  文件与`stream` 关联。  
  
 这些函数将锁定调用线程，因此线程安全。  有关非固定版本，请参见 [\_getc\_nolock、\_getwc\_nolock](../../c-runtime-library/reference/getc-nolock-getwc-nolock.md)。  
  
 实例特定的备注。  
  
|例程|备注|  
|--------|--------|  
|`getc`|和 `fgetc`相同，但是实现可作为函数和宏。|  
|`getwc`|`getc`的宽字符版本。  根据`stream`是以文本模式还是二进制模式打开， 读取多字节字符或宽字符 。|  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|-----------------------------|----------------|-------------------|  
|`_gettc`|`getc`|`getc`|`getwc`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`getc`|\<stdio.h\>|  
|`getwc`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_getc.c  
// Use getc to read a line from a file.  
  
#include <stdio.h>  
  
int main()  
{  
    char buffer[81];  
    int i, ch;  
    FILE* fp;  
  
    // Read a single line from the file "crt_getc.txt".   
  
    fopen_s(&fp, "crt_getc.txt", "r");  
    if (!fp)  
    {  
       printf("Failed to open file crt_getc.txt.\n");  
       exit(1);  
    }  
  
    for (i = 0; (i < 80) && ((ch = getc(fp)) != EOF)  
                         && (ch != '\n'); i++)  
    {  
        buffer[i] = (char) ch;  
    }  
  
    // Terminate string with a null character   
    buffer[i] = '\0';  
    printf( "Input was: %s\n", buffer);  
  
    fclose(fp);  
}  
```  
  
## 输入:crt\_getc.txt  
  
```  
Line one.  
Line two.  
```  
  
### Output  
  
```  
Input was: Line one.  
```  
  
## .NET Framework 等效项  
  
-   [System::IO::StreamReader::Read](https://msdn.microsoft.com/en-us/library/system.io.streamreader.read.aspx)  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fgetc、fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [\_getch、\_getwch](../../c-runtime-library/reference/getch-getwch.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)   
 [ungetc、ungetwc](../../c-runtime-library/reference/ungetc-ungetwc.md)