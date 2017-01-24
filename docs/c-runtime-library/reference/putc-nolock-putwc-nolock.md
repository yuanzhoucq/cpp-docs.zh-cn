---
title: "_putc_nolock、_putwc_nolock | Microsoft Docs"
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
  - "_putc_nolock"
  - "_putwc_nolock"
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
  - "_puttc_nolock"
  - "puttc_nolock"
  - "putwc_nolock"
  - "_putwc_nolock"
  - "_putc_nolock"
  - "putc_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_putc_nolock 函数"
  - "_puttc_nolock 函数"
  - "_putwc_nolock 函数"
  - "字符, 写入"
  - "putc_nolock 函数"
  - "puttc_nolock 函数"
  - "putwc_nolock 函数"
  - "流, 将字符写入到"
ms.assetid: 3cfc7f21-c9e8-4b7f-b0fb-af0d4d85e7e1
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _putc_nolock、_putwc_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

写入流中的字符不锁定线程。  
  
## 语法  
  
```  
  
      int _putc_nolock(  
   int c,  
   FILE *stream   
);  
wint_t _putwc_nolock(  
   wchar_t c,  
   FILE *stream   
);  
```  
  
#### 参数  
 `c`  
 要写入的字符。  
  
 `stream`  
 指向 **FILE** 结构的指针。  
  
## 返回值  
 请参见 **putc, putwc**。  
  
## 备注  
 有`_putc_nolock`和 `_putwc_nolock`后缀的版本是相同的（不包括有**\_nolock** 后缀的），但它们不由其他线程的干扰保护。  它们可能更快，因为它们不会产生锁定其他线程的开销。  仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
 `_putwc_nolock` 是 `_putc_nolock`的宽字符版本；如果流在 ANSI 模式下是公开的则两个函数具有相同行为。  `_putc_nolock` 当前不支持输出到 UNICODE 流。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_puttc_nolock`|`_putc_nolock`|`_putc_nolock`|**\_putwc\_nolock**|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_putc_nolock`|\<stdio.h\>|  
|`_putwc_nolock`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_putc_nolock.c  
/* This program uses putc to write buffer  
 * to a stream. If an error occurs, the program  
 * stops before writing the entire buffer.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char *p, buffer[] = "This is the line of output\n";  
   int  ch;  
  
   ch = 0;  
   /* Make standard out the stream and write to it. */  
   stream = stdout;  
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )  
      ch = _putc_nolock( *p, stream );  
}  
```  
  
## Output  
  
```  
This is the line of output  
```  
  
## .NET Framework 等效项  
  
-   [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
-   [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fputc、fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)