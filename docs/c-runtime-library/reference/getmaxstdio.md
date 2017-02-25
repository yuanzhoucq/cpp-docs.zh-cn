---
title: "_getmaxstdio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getmaxstdio"
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
  - "_getmaxstdio"
  - "getmaxstdio"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_getmaxstdio 函数"
  - "文件 [C++], 打开的数量"
  - "getmaxstdio 函数"
  - "打开文件, 获取数量"
ms.assetid: 700ca8ce-4a8c-4e00-9467-dfa9d6b831a0
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _getmaxstdio
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回允许在 I\/O 流级同时打开的文件数。  
  
## 语法  
  
```  
int _getmaxstdio( void );  
```  
  
## 返回值  
 返回一个数表示可以在 `stdio` 级同时打开的文件数。  
  
## 备注  
 使用 [\_setmaxstdio](../../c-runtime-library/reference/setmaxstdio.md) 配置允许在 `stdio` 级同时打开的文件数。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_getmaxstdio`|\<stdio.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_setmaxstdio.c  
// The program retrieves the maximum number  
// of open files and prints the results  
// to the console.  
  
#include <stdio.h>  
  
int main()  
{  
   printf( "%d\n", _getmaxstdio());  
  
   _setmaxstdio(2048);  
  
   printf( "%d\n", _getmaxstdio());  
}  
```  
  
  **512**  
**2048**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)