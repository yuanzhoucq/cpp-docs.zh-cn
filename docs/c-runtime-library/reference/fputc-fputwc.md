---
title: "fputc、fputwc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fputc"
  - "fputwc"
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
  - "fputc"
  - "fputwc"
  - "_fputtc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fputtc 函数"
  - "fputc 函数"
  - "fputtc 函数"
  - "fputwc 函数"
  - "流, 将字符写入到"
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# fputc、fputwc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符写入流。  
  
## 语法  
  
```  
int fputc(  
   int c,  
   FILE *stream   
);  
wint_t fputwc(  
   wchar_t c,  
   FILE *stream   
);  
```  
  
#### 参数  
 `c`  
 要写入的字符。  
  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## 返回值  
 这些函数都返回一个写好的字符。  为 `fputc`，`EOF` 的返回值指示错误。  为 `fputwc`，`WEOF` 的返回值指示错误。  如果 `stream` 为 `NULL`, 则函数调用无效参数处理程序, 如  [参数验证](../../c-runtime-library/parameter-validation.md)所述.  如果允许执行继续，则这些函数返回 `EOF` 并将 `errno` 设置为 `EINVAL`。  
  
 有关这些内容的更多信息以及其他错误代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 这些功能在关联的文件位置指示器（如果定义）编写单个字符 `c` 并根据需要事先指示。  在 `fputc` 和 `fputwc`中, 文件与 `stream`*.*关联如果文件不支持位置请求或以附加方式打开，字符追加到流的末尾。  
  
 如果流在 ANSI 模式中打开，这两个函数具有相同的行为。  `fputc` 当前不支持输出到 UNICODE 流。  
  
 与 `_nolock` 后缀的版本与相同，但它们不由其他线程的干扰保护。  有关详细信息，请参阅[\_fputc\_nolock、\_fputwc\_nolock](../../c-runtime-library/reference/fputc-nolock-fputwc-nolock.md).  
  
 实例特定的备注。  
  
|例程|备注|  
|--------|--------|  
|`fputc`|与 `putc`等效，但是仅实现为函数，而不是函数和宏。|  
|`fputwc`|`fputc`的宽字符版本。  编写 `c` 作为多字节字符或宽字符，根据 `stream` 是以文本模式还是二进制模式打开。|  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_fputtc`|`fputc`|`fputc`|`fputwc`|  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fputc`|\<stdio.h\>|  
|`fputwc`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fputc.c  
// This program uses fputc  
// to send a character array to stdout.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char strptr1[] = "This is a test of fputc!!\n";  
   char *p;  
  
   // Print line to stream using fputc.   
   p = strptr1;  
   while( (*p != '\0') && fputc( *(p++), stdout ) != EOF ) ;  
  
}  
```  
  
  **这是一个 fputc 的测试\!\!**   
## .NET Framework 等效项  
  
-   [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
-   [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fgetc、fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)