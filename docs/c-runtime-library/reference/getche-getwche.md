---
title: "_getche、_getwche | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getwche"
  - "_getche"
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
  - "getwche"
  - "_getche"
  - "_getwche"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_getche 函数"
  - "_getwche 函数"
  - "字符, 从控制台获取"
  - "控制台, 读取自"
  - "getche 函数"
  - "getwche 函数"
ms.assetid: eac978a8-c43a-4130-938f-54f12e2a0fda
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _getche、_getwche
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从控制台中获取字符，并需要回显。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _getche( void );  
wint_t _getwche( void );  
```  
  
## 返回值  
 返回读取的字符。  无错误返回。  
  
## 备注  
 `_getche` 和 `_getwche` 函数从控制台读取单个字符并回显，这意味着字符显示在控制台中。  这些函数均不可用于读取 CTRL\+C。  在读取功能键或箭头键时，每个函数都将被调用两次；第一次调用返回 0 或 0xE0，第二次调用返回实际的键码。  
  
 这些函数将锁定调用线程，因此线程安全。  有关非锁定版本，请参见 [\_getche\_nolock、\_getwche\_nolock](../../c-runtime-library/reference/getche-nolock-getwche-nolock.md)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_getche`|`_getche`|`_getch`|`_getwche`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_getche`|\<conio.h\>|  
|`_getwche`|\<conio.h\> 或 \<wchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_getche.c  
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
      ch = _getche();  
      ch = toupper( ch );  
   } while( ch != 'Y' );  
  
   _putch( ch );  
   _putch( '\r' );    // Carriage return  
   _putch( '\n' );    // Line feed       
}  
```  
  
  **`abcdey`在完成中密钥键入时键入“Y”: Y**   
## .NET Framework Equivalent  
 不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [控制台和端口 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cgets、\_cgetws](../../c-runtime-library/cgets-cgetws.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [\_ungetch、\_ungetwch、\_ungetch\_nolock、\_ungetwch\_nolock](../../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)