---
title: "getchar、getwchar | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "getchar"
  - "getwchar"
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
  - "getwchar"
  - "GetChar"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_gettchar 函数"
  - "字符, 读取"
  - "gettchar 函数"
  - "getwchar 函数"
  - "标准输入, 读取自"
ms.assetid: 19fda588-3e33-415c-bb60-dd73c028086a
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# getchar、getwchar
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从标准输入中读取一个字符。  
  
## 语法  
  
```  
int getchar();  
wint_t getwchar();  
```  
  
## 返回值  
 返回读取的字符。  若要指示读取错误或文件结束的条件，`getchar` `returns EOF`和 `getwchar` 返回 `WEOF`。  对于 `getchar`，请使用 `ferror` 或 `feof` 来检查是否有错误或文件结束。  
  
## 备注  
 每个实例从 `stdin` 读取单个字符并增量将关联的文件指针指向下一个字符。  `getchar` 与 [\_fgetchar](../../c-runtime-library/reference/fgetc-fgetwc.md) 相同，但是，它作为函数和作为宏被实现。  
  
 这些函数将锁定调用线程，因此线程安全。  有关非固定版本，请参见 [\_getchar\_nolock、\_getwchar\_nolock](../../c-runtime-library/reference/getchar-nolock-getwchar-nolock.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_gettchar`|`getchar`|`getchar`|`getwchar`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`getchar`|\<stdio.h\>|  
|`getwchar`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_getchar.c  
// Use getchar to read a line from stdin.  
  
#include <stdio.h>  
  
int main()  
{  
    char buffer[81];  
    int i, ch;  
  
    for (i = 0; (i < 80) && ((ch = getchar()) != EOF)  
                         && (ch != '\n'); i++)  
    {  
        buffer[i] = (char) ch;  
    }  
  
    // Terminate string with a null character   
    buffer[i] = '\0';  
    printf( "Input was: %s\n", buffer);  
}  
```  
  
  **`此文本`的输入是：此文本**   
## .NET Framework 等效项  
  
-   [System::IO::StreamReader::Read](https://msdn.microsoft.com/en-us/library/system.io.streamreader.read.aspx).  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [fgetc、fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [\_getch、\_getwch](../../c-runtime-library/reference/getch-getwch.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)   
 [ungetc、ungetwc](../../c-runtime-library/reference/ungetc-ungetwc.md)