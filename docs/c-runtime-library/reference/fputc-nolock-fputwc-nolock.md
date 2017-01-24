---
title: "_fputc_nolock、_fputwc_nolock | Microsoft Docs"
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
  - "_fputwc_nolock"
  - "_fputc_nolock"
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
  - "_fputc_nolock"
  - "fputwc_nolock"
  - "fputc_nolock"
  - "fputtc_nolock"
  - "_fputwc_nolock"
  - "_fputtc_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fputc_nolock 函数"
  - "_fputtc_nolock 函数"
  - "_fputwc_nolock 函数"
  - "fputc_nolock 函数"
  - "fputtc_nolock 函数"
  - "fputwc_nolock 函数"
  - "流, 将字符写入到"
ms.assetid: c63eb3ad-58fa-46d0-9249-9c25f815eab9
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fputc_nolock、_fputwc_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

写入流中的字符不锁定线程。  
  
## 语法  
  
```  
int _fputc_nolock(  
   int c,  
   FILE *stream   
);  
wint_t _fputwc_nolock(  
   wchar_t c,  
   FILE *stream   
);  
```  
  
#### 参数  
 `c`  
 要写入的字符。  
  
 `stream`  
 指向 `FILE`结构的指针。  
  
## 返回值  
 这些函数都返回一个写好的字符。  有关的错误信息，请参阅[fputc、fputwc](../../c-runtime-library/reference/fputc-fputwc.md)。  
  
## 备注  
 `_fputc_nolock` 和 `_fputwc_nolock` 与 `fputc` 和 `fputwc`分别是相同的，除了它们不能避免来自由其他线程的干扰。  它们可能更快，因为它们不会产生锁定其他线程的开销。  仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
 如果流在 ANSI 模式中打开，这两个函数具有相同的行为。  `_fputc_nolock` 当前不支持输出到 UNICODE 流。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_fputtc_nolock`|`_fputc_nolock`|`_fputc_nolock`|`_fputwc_nolock`|  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_fputc_nolock`|\<stdio.h\>|  
|`_fputwc_nolock`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fputc_nolock.c  
// This program uses _fputc_nolock  
// to send a character array to stdout.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char strptr1[] = "This is a test of _fputc_nolock!!\n";  
   char *p;  
  
   // Print line to stream using fputc.   
   p = strptr1;  
   while( (*p != '\0') && _fputc_nolock( *(p++), stdout ) != EOF ) ;  
  
}  
```  
  
  **这是一个 \_fputc\_nolock 的测试\!\!**   
## .NET Framework 等效项  
  
-   [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
-   [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fgetc、fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)