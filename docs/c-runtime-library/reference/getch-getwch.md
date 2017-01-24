---
title: "_getch、_getwch | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getch"
  - "_getwch"
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
  - "getwch"
  - "_getch"
  - "_getwch"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getch 函数"
  - "_getwch 函数"
  - "字符, 从控制台获取"
  - "控制台, 读取自"
  - "getch 函数"
  - "getwch 函数"
ms.assetid: cc116be7-cff2-4274-970f-5e7b18ccc05c
caps.latest.revision: 26
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getch、_getwch
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从控件中获取字符而无需回显。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _getch( void );  
wint_t _getwch( void );  
```  
  
## 返回值  
 返回读取的字符。  无错误返回。  
  
## 备注  
 `_getch` 和`_getwch` 的功能是从控件读取单个字符，而无需回显字符。  这些函数均不可用于读取 CTRL\+C。  在读取功能键或箭头键时，每个函数都将被调用两次；第一次调用返回 0 或 0xE0，第二次调用返回实际的键码。  
  
 这些函数将锁定调用线程，因此线程安全。  有关非锁定版本，请参见 [\_getch\_nolock、\_getwch\_nolock](../../c-runtime-library/reference/getch-nolock-getwch-nolock.md)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_gettch`|`_getch`|`_getch`|`_getwch`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_getch`|\<conio.h\>|  
|`_getwch`|\<conio.h\> 或 \<wchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_getch.c  
// compile with: /c  
// This program reads characters from  
// the keyboard until it receives a 'Y' or 'y'.  
  
#include <conio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
  
   _cputs( "Type 'Y' when finished typing keys: " );  
   do  
   {  
      ch = _getch();  
      ch = toupper( ch );  
   } while( ch != 'Y' );  
  
   _putch( ch );  
   _putch( '\r' );    // Carriage return  
   _putch( '\n' );    // Line feed    
}  
```  
  
  **`abcdey`在完成中密钥键入时键入“Y”: Y**   
## .NET Framework 等量  
 不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [控制台和端口 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_getche、\_getwche](../../c-runtime-library/reference/getche-getwche.md)   
 [\_cgets、\_cgetws](../../c-runtime-library/cgets-cgetws.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [\_ungetch、\_ungetwch、\_ungetch\_nolock、\_ungetwch\_nolock](../../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)