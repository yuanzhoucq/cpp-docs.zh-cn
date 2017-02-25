---
title: "ungetc、ungetwc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ungetwc"
  - "ungetc"
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
  - "_ungettc"
  - "ungetwc"
  - "ungetc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ungettc 函数"
  - "字符, 推送回流"
  - "ungetc 函数"
  - "ungettc 函数"
  - "ungetwc 函数"
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# ungetc、ungetwc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将一个字符推入流中。  
  
## 语法  
  
```  
int ungetc(  
   int c,  
   FILE *stream   
);  
wint_t ungetwc(  
   wint_t c,  
   FILE *stream   
);  
```  
  
#### 参数  
 `c`  
 要推出的字符。  
  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## 返回值  
 如果成功，这些函数都返回一个字符参数 `c`*。*如果 `c` 不能推回，或者未读取字符，输入流未更改，并且 `ungetc` 返回 `EOF`; `ungetwc` 返回 `WEOF`。  如果 `stream` 是 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许继续执行，返回`EOF` 或 `WEOF` ，并将 `errno` 设置为 `EINVAL`。  
  
 有关这些属性和其他错误代码的信息，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `ungetc` 函数将字符 `c` 推到 `stream` 上并清除文件结尾指示符。  流必须处于打开状态，用于读取。  在 `stream`上 的一个子序列读取操作从 `c`开始*。*使用 `ungetc`，推送 `EOF` 到流中的尝试将被忽略。  
  
 如果在字符从流中读取之前调用`fflush`、`fseek`、`fsetpos`或 `rewind`，在流中`ungetc`的字符可能被清除 。  文件位置指示符将具有字符推回之前的值。  与流相应的外部存储保持不变。  在成功 `ungetc` 调用文本流的基础上，文件位置指示符是未指定的，直到所有已推回的字符读取或被丢弃。  在每次成功的 `ungetc` 调用二进制流，文件位置指示符递减；如果调用前，它的值是 0，在调用后值是未定义。  
  
 如果 `ungetc` 被调用两次而没有读取，或者，没有这两次调用之间的文件定位操作，结果是不可预知的。  调用 `fscanf`后，`ungetc` 的调用可能失败后，除非另一个读取操作 \(例如 `getc`\) 执行了。  这是因为，`fscanf` 调用 `ungetc`。  
  
 `ungetwc` 是 `ungetc`的宽字符版本。  但是，在每次成功的 `ungetwc` 调用文本或二进制流，文件位置指示符的值是未指定的，直到所有已推回的字符读取或被丢弃。  
  
 这些函数在执行期间是线程安全和锁定敏感数据。  有关非固定版本，请参见 [\_ungetc\_nolock、\_ungetwc\_nolock](../../c-runtime-library/reference/ungetc-nolock-ungetwc-nolock.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_ungettc`|`ungetc`|`ungetc`|`ungetwc`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`ungetc`|\<stdio.h\>|  
|`ungetwc`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_ungetc.c  
// This program first converts a character  
// representation of an unsigned integer to an integer. If  
// the program encounters a character that is not a digit,  
// the program uses ungetc to replace it in the  stream.  
//  
  
#include <stdio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
   int result = 0;  
  
   // Read in and convert number:  
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )  
      result = result * 10 + ch - '0';    // Use digit.  
   if( ch != EOF )  
      ungetc( ch, stdin );                // Put nondigit back.  
   printf( "Number = %d\nNext character in stream = '%c'",   
            result, getchar() );  
}  
```  
  
  **`521a`数字 \= 521**  
**在流中的下一个字符 \=“a”**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)