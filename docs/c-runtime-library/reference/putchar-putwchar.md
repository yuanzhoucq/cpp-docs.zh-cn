---
title: "putchar、putwchar | Microsoft Docs"
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
  - "putchar"
  - "putwchar"
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
  - "putchar"
  - "putwchar"
  - "_puttchar"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_puttchar 函数"
  - "字符, 写入"
  - "putchar 函数"
  - "putwchar 函数"
  - "标准输出, 写入"
ms.assetid: 93657c7f-cca1-4032-8e3a-cd6ab6193748
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# putchar、putwchar
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

写入一个字符到 **stdout**。  
  
## 语法  
  
```  
  
      int putchar(  
   int c   
);  
wint_t putwchar(  
   wchar_t c   
);  
```  
  
#### 参数  
 `c`  
 要写入的字符。  
  
## 返回值  
 返回已写好的字符。  若要指示错误或文件结尾条件，`putc` 和 `putchar` 返回 `EOF`; `putwc` 和 `putwchar` 返回 **WEOF**。  对于所有四个实例，请使用 [ferror](../../c-runtime-library/reference/ferror.md) 或 [feof](../../c-runtime-library/reference/feof.md) 检查错误或文件结尾。  如果传递一个空指针 `stream`,这些函数将生成一个无效的参数异常，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则这些函数返回 `EOF` 或 **WEOF** 并将 `errno` 设置为 `EINVAL`.  
  
 有关这些内容的更多信息以及其他错误代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `putc` 实例写入单个字符 `stream`到当前位置的输出 `c` 。  任何整数可以传递给 `putc`，但是仅较低的8位被写入。  `putchar` 实例与**putc\(** `c`**,stdout \)**相同。  对于每个实例，如果读取错误，流的错误指示器会被设置。  `putc` 和 `putchar` 分别类似于 `fputc` 和 `_fputchar`，但是实现函数和宏 \(请参见 [选择在函数和宏之间](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)\)。  `putwc` 和 `putwchar` 分别为 `putc` 和 `putchar`的宽字符版本。  
  
 有**\_nolock** 后缀的版本是相同的，但它们不由其他线程的干扰保护。  它们可能更快，因为它们不会产生锁定其他线程的开销。  仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_puttchar`|`putchar`|`putchar`|**putwchar**|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`putchar`|\<stdio.h\>|  
|`putwchar`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_putchar.c  
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
  
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )  
      ch = putchar( *p );  
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