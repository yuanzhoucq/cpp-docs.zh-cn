---
title: "_isatty | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_isatty"
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
  - "_isatty"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_isatty 函数"
  - "字符设备检查"
  - "检查字符设备"
  - "isatty 函数"
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _isatty
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定文件描述符与字符设备是否相关。  
  
## 语法  
  
```  
  
      int _isatty(  
int fd   
);  
```  
  
#### 参数  
 `fd`  
 引用要测试的计算机上的文件描述符。  
  
## 返回值  
 如果描述符与字符设备相关，`_isatty` 返回一个非零值。  否则，`_isatty` 返回0 。  
  
## 备注  
 `_isatty` 函数确定 `fd` 是否与字符设备 \(终端、控件台、打印机或串行端口\)相关。  
  
 此函数验证 `fd` 参数。  如果 `fd` 是一个坏的文件指针，无效参数处理程序将被调用，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数返回 0 并将 `errno` 设置为 `EBADF`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_isatty`|\<io.h\>|  
  
 有关更多兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_isatty.c  
/* This program checks to see whether  
 * stdout has been redirected to a file.  
 */  
  
#include <stdio.h>  
#include <io.h>  
  
int main( void )  
{  
   if( _isatty( _fileno( stdout ) ) )  
      printf( "stdout has not been redirected to a file\n" );  
   else  
      printf( "stdout has been redirected to a file\n");  
}  
```  
  
## 示例输出  
  
```  
stdout has not been redirected to a file  
```  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)