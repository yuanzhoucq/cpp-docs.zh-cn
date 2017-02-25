---
title: "getpid | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getpid"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "getpid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "getpid 函数"
ms.assetid: d3e13bae-9a0c-4f33-86d3-ec9df9519285
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _getpid
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取进程标识  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [\/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
int _getpid( void );  
```  
  
## 返回值  
 返回从系统获取的进程 ID。 无错误返回。  
  
## 备注  
 `_getpid` 函数从系统获取进程 ID。 进程 ID 唯一标识调用进程。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_getpid`|\<process.h\>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_getpid.c  
// This program uses _getpid to obtain  
// the process ID and then prints the ID.  
  
#include <stdio.h>  
#include <process.h>  
  
int main( void )  
{  
   // If run from command line, shows different ID for   
   // command line than for operating system shell.  
  
   printf( "Process id: %d\n", _getpid() );  
}  
```  
  
```Output  
进程 ID：3584  
```  
  
## .NET Framework 等效项  
 [System::Diagnostics::Process::Id](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.id.aspx)  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_mktemp、\_wmktemp](../../c-runtime-library/reference/mktemp-wmktemp.md)