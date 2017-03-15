---
title: "_ungetch、_ungetwch、_ungetch_nolock、_ungetwch_nolock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ungetch_nolock"
  - "_ungetwch_nolock"
  - "_ungetwch"
  - "_ungetch"
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
  - "api-ms-win-crt-conio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_ungetch_nolock"
  - "ungetwch"
  - "ungetch_nolock"
  - "_ungetwch"
  - "ungetch"
  - "ungetwch_nolock"
  - "_ungetch"
  - "_ungettch_nolock"
  - "_ungettch"
  - "_ungetwch_nolock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ungetch 函数"
  - "_ungetch_nolock 函数"
  - "_ungettch 函数"
  - "_ungettch_nolock 函数"
  - "_ungetwch 函数"
  - "_ungetwch_nolock 函数"
  - "字符, 推送回控制台"
  - "ungetch_nolock 函数"
  - "ungettch 函数"
  - "ungettch_nolock 函数"
  - "ungetwch 函数"
  - "ungetwch_nolock 函数"
ms.assetid: 70ae71c6-228c-4883-a57d-de6d5f873825
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _ungetch、_ungetwch、_ungetch_nolock、_ungetwch_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

推回从控制台读取的最后一个字符。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _ungetch(  
   int c   
);  
wint_t _ungetwch(  
   wint_t c   
);  
int _ungetch_nolock(  
   int c   
);  
wint_t _ungetwch_nolock(  
   wint_t c   
);  
```  
  
#### 参数  
 `c`  
 要推出的字符。  
  
## 返回值  
 如果成功，两个函数返回字符 `c`。  如果出现错误，`_ungetch` 返回 `EOF` 的值，`_ungetwch`返回`WEOF`。  
  
## 备注  
 这些函数将字符 `c` 推回控制台，使 `c` 成为`_getch` 或 `_getche`读取的下一个 \(或`_getwch` 或`_getwche`\)。  如果是在之下之前多次调用读取，`_ungetch` 和 `_ungetwch` 失败。  `c` 参数可能不是 `EOF` \(或 `WEOF`\)。  
  
 除了它们不由其他线程干扰保护，`_nolock` 后缀的版本相同。  它们可能更快，因为它们不会产生锁定其他线程的开销。  仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_ungettch`|`_ungetch`|`_ungetch`|`_ungetwch`|  
|`_ungettch_nolock`|`_ungetch_nolock`|`_ungetch_nolock`|`_ungetwch_nolock`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_ungetch`, `_ungetch_nolock`|\<conio.h\>|  
|`_ungetwch`, `_ungetwch_nolock`|\<conio.h\> 或 \<wchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_ungetch.c  
// compile with: /c  
// In this program, a white-space delimited   
// token is read from the keyboard. When the program   
// encounters a delimiter, it uses _ungetch to replace   
// the character in the keyboard buffer.  
//  
  
#include <conio.h>  
#include <ctype.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char buffer[100];  
   int count = 0;  
   int ch;  
  
   ch = _getche();  
   while( isspace( ch ) )      // Skip preceding white space.  
      ch = _getche();  
   while( count < 99 )         // Gather token.  
   {  
      if( isspace( ch ) )      // End of token.  
         break;  
      buffer[count++] = (char)ch;  
      ch = _getche();  
   }  
   _ungetch( ch );            // Put back delimiter.  
   buffer[count] = '\0';      // Null terminate the token.  
   printf( "\ntoken = %s\n", buffer );  
}  
```  
  
  **`White`token \= White**   
## 请参阅  
 [控制台和端口 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cscanf、\_cscanf\_l、\_cwscanf、\_cwscanf\_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [\_getch、\_getwch](../../c-runtime-library/reference/getch-getwch.md)