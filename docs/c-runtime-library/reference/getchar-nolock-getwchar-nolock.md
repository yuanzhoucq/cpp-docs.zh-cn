---
title: "_getchar_nolock、_getwchar_nolock | Microsoft Docs"
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
  - "_getchar_nolock"
  - "_getwchar_nolock"
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
  - "getwchar_nolock"
  - "_getwchar_nolock"
  - "_getchar_nolock"
  - "getchar_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getchar_nolock 函数"
  - "_getwchar_nolock 函数"
  - "字符, 读取"
  - "getchar_nolock 函数"
  - "getwchar_nolock 函数"
  - "标准输入, 读取自"
ms.assetid: dc49ba60-0647-4ae9-aa9a-a0618b1666de
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getchar_nolock、_getwchar_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从标准输入中读取一个字符。  
  
## 语法  
  
```  
int _getchar_nolock( void );  
wint_t _getwchar_nolock( void );  
```  
  
## 返回值  
 请参见 [getchar、getwchar](../../c-runtime-library/reference/getchar-getwchar.md)。  
  
## 备注  
 `_getchar_nolock` 和 `_getwchar_nolock` 与 `getchar` 和 `getwchar`分别是相同的，除了它们不能避免来自由其他线程的干扰。  它们可能更快，因为它们不会产生锁定其他线程的开销。  仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_gettchar_nolock`|`_getchar_nolock`|`_getchar_nolock`|`_getwchar_nolock`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_getchar_nolock`|\<stdio.h\>|  
|`_getwchar_nolock`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_getchar_nolock.c  
// Use _getchar_nolock to read a line from stdin.   
  
#include <stdio.h>  
  
int main()  
{  
    char buffer[81];  
    int i, ch;  
  
    for (i = 0; (i < 80) && ((ch = _getchar_nolock()) != EOF)  
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
  
-   [System::IO::StreamReader::Read](https://msdn.microsoft.com/en-us/library/system.io.streamreader.read.aspx)  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [fgetc、fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [\_getch、\_getwch](../../c-runtime-library/reference/getch-getwch.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)   
 [ungetc、ungetwc](../../c-runtime-library/reference/ungetc-ungetwc.md)