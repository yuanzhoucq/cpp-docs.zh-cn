---
title: "_getc_nolock、_getwc_nolock | Microsoft Docs"
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
  - "_getc_nolock"
  - "_getwc_nolock"
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
  - "getc_nolock"
  - "_gettc_nolock"
  - "_getc_nolock"
  - "getwc_nolock"
  - "gettc_nolock"
  - "_getwc_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getc_nolock 函数"
  - "_gettc_nolock 函数"
  - "_getwc_nolock 函数"
  - "字符, 读取"
  - "getc_nolock 函数"
  - "gettc_nolock 函数"
  - "getwc_nolock 函数"
  - "从流中读取字符"
  - "流, 读取字符自"
ms.assetid: eb37b272-e177-41c9-b077-12ce7ffd3b88
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getc_nolock、_getwc_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

读取流的一个字符。  
  
## 语法  
  
```  
int _getc_nolock(   
   FILE *stream   
);  
wint_t _getwc_nolock(   
   FILE *stream   
);  
```  
  
#### 参数  
 `stream`  
 输入流。  
  
## 返回值  
 请参见[getc、getwc](../../c-runtime-library/reference/getc-getwc.md)。  
  
## 备注  
 这些函数与 `getc` 和 `getwc` 是相同，只是不阻止调用线程。  它们可能更快，因为它们不会产生锁定其他线程的开销。  仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_gettc_nolock`|`getc_nolock`|`getc_nolock`|`getwc_nolock`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`getc_nolock`|\<stdio.h\>|  
|`getwc_nolock`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_getc_nolock.c  
// Use getc to read a line from a file.  
  
#include <stdio.h>  
  
int main()  
{  
    char buffer[81];  
    int i, ch;  
    FILE* fp;  
  
    // Read a single line from the file "crt_getc_nolock.txt".  
    fopen_s(&fp, "crt_getc_nolock.txt", "r");  
    if (!fp)  
    {  
       printf("Failed to open file crt_getc_nolock.txt.\n");  
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
  
## 输入:crt\_getc\_nolock.txt  
  
```  
Line the first.  
Line the second.  
```  
  
### Output  
  
```  
Input was: Line the first.  
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