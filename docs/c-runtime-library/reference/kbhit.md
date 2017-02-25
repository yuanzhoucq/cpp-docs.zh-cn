---
title: "kbhit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_kbhit"
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
  - "kbhit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "kbhit 函数"
ms.assetid: e82a1cc9-bbec-4150-b678-a7e433220fe4
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _kbhit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检查控制台的键盘输入。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
  
int _kbhit( void );  
```  
  
## 返回值  
 当一个键被按下，`_kbhit` 将返回一个非零值。  否则，则将返回 0。  
  
## 备注  
 `_kbhit` 函数通过最近的击键以检查控制台。  如果函数返回一个非零值，则输入在缓冲区等待。  然后程序可以调用 `_getch` 或 `_getche` 捕获该键击。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_kbhit`|\<conio.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_kbhit.c  
// compile with: /c  
/* This program loops until the user  
 * presses a key. If _kbhit returns nonzero, a  
 * keystroke is waiting in the buffer. The program  
 * can call _getch or _getche to get the keystroke.  
 */  
  
#include <conio.h>  
#include <stdio.h>  
  
int main( void )  
{  
   /* Display message until key is pressed. */  
   while( !_kbhit() )  
      _cputs( "Hit me!! " );  
  
   /* Use _getch to throw key away. */  
   printf( "\nKey struck was '%c'\n", _getch() );  
}  
```  
  
## 示例输出  
  
```  
Hit me!! Hit me!! Hit me!! Hit me!! Hit me!! Hit me!! Hit me!!  
Key struck was 'q'   
```  
  
## 请参阅  
 [控制台和端口 I\/O](../../c-runtime-library/console-and-port-i-o.md)