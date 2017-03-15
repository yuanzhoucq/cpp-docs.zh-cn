---
title: "_fputchar、_fputwchar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fputchar"
  - "_fputwchar"
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
  - "fputtchar"
  - "_fputwchar"
  - "fputwchar"
  - "_fputtchar"
  - "fputchar"
  - "_fputchar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fputchar 函数"
  - "_fputtchar 函数"
  - "_fputwchar 函数"
  - "fputchar 函数"
  - "fputtchar 函数"
  - "fputwchar 函数"
  - "标准输出, 写入"
ms.assetid: b92ff600-a924-4f2b-b0e7-3097ee31bdff
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _fputchar、_fputwchar
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符写入 `stdout`。  
  
## 语法  
  
```  
int _fputchar(  
   int c   
);  
wint_t _fputwchar(  
   wchar_t c   
);  
```  
  
#### 参数  
 `c`  
 要写入的字符。  
  
## 返回值  
 这些函数都返回一个写好的字符。  为 `_fputchar`，`EOF` 的返回值指示错误。  为 `_fputwchar`，`WEOF` 的返回值指示错误。  如果 c 为 `NULL`，这些函数生成无效的参数异常，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则这些函数返回 `EOF`（或`WEOF`）并将`errno`设置为`EINVAL`。  
  
 有关这些属性和其他错误代码的详细信息，请参阅 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 这两个函数将单字符`stdout`写入`c`，并提出了适当的指标。  `_fputchar` 与 `fputc(``stdout )`相等。  也与`putchar`等效，但是仅实现为函数，而不是函数和宏。  不同于 `fputc` 和 `putchar`，这些函数不兼容与 ANSI 标准。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_fputtchar`|`_fputchar`|`_fputchar`|`_fputwchar`|  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_fputchar`|\<stdio.h\>|  
|`_fputwchar`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fputchar.c  
// This program uses _fputchar  
// to send a character array to stdout.  
  
#include <stdio.h>  
  
int main( void )  
{  
    char strptr[] = "This is a test of _fputchar!!\n";  
    char *p = NULL;  
  
    // Print line to stream using _fputchar.   
    p = strptr;  
    while( (*p != '\0') && _fputchar( *(p++) ) != EOF )  
      ;  
}  
```  
  
  **这是一个 \_fputchar 的测试\!\!**   
## .NET Framework 等效项  
  
-   [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
-   [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fgetc、fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)