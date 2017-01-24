---
title: "putc、putwc | Microsoft Docs"
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
  - "putwc"
  - "putc"
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
  - "_puttc"
  - "putwc"
  - "putc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_puttc 函数"
  - "字符, 写入"
  - "putc 函数"
  - "puttc 函数"
  - "putwc 函数"
  - "流, 将字符写入到"
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# putc、putwc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符写入流。  
  
## 语法  
  
```  
  
      int putc(  
   int c,  
   FILE *stream   
);  
wint_t putwc(  
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
 返回已写好的字符。  若要指示错误或文件结尾情况，`putc` 和 `putchar` 返回 `EOF`; `putwc` ， `putwchar` 返回 **WEOF**。  对于所有的四个程序，请使用 [ferror](../../c-runtime-library/reference/ferror.md) 或 [feof](../../c-runtime-library/reference/feof.md) 检测错误或文件结尾。  如果 `stream` 是 null 指针，则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，则这些函数返回 `EOF`或**WEOF** 并将  `errno`设置为  `EINVAL`。  
  
 有关这些内容的更多信息以及其他错误代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `putc` 程序写入单个字符 `c` 到当前位置的输出 `stream` 。  任何整数可以传递给 `putc`，但是仅较低的8位被写入。  `putchar` 程序与**putc\(** `c`**,stdout \)**相同。  对于每个程序，如果读取错误，流的错误指示器会被设置。  `putc` 和 `putchar` 分别类似于 `fputc` 和 `_fputchar`，但是都以函数和宏实现 \(请参见 [在函数和宏之间选择](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)\)。  `putwc` 和 `putwchar` 分别为 `putc` 和 `putchar`的宽字符版本.  如果流在 ANSI 模式中打开，`putwc` 和 `putc` 会具有相同的行为。  `putc` 当前不支持输出到 UNICODE 流。  
  
 有**\_nolock** 后缀的版本是相同的，但它们不能阻止其他线程的干扰。  有关详细信息，请参阅 **\_putc\_nolock, \_putwc\_nolock**。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_puttc`|`putc`|`putc`|**putwc**|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`putc`|\<stdio.h\>|  
|`putwc`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_putc.c  
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
      ch = putc( *p, stream );  
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