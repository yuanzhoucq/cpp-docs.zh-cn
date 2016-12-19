---
title: "_pclose | Microsoft Docs"
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
  - "_pclose"
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
  - "_pclose"
  - "pclose"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_pclose 函数"
  - "pclose 函数"
  - "管道, 关闭"
ms.assetid: e2e31a9e-ba3a-4124-bcbb-c4040110b3d3
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _pclose
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

等待一个新的命令处理器并在关联的管道中关闭流。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
  
      int _pclose(  
FILE *stream   
);  
```  
  
#### 参数  
 `stream`  
 从上一个`_popen`的调用中返回值。  
  
## 返回值  
 如果发生错误，则返回停止的命令处理器的退出状态或– 1。  返回值的格式与`_cwait`相同，除了低字节和高字节部分要交换。  如果流是 **NULL**，`_pclose` 设置 `errno` 到 `EINVAL` 并返回 \-1。  
  
 有关这些内容以及其他错误代码的详细信息，请参阅 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_pclose`函数查找由相关`_popen`调用的命令处理器\(Cmd.exe\)的过程ID，在新的命令处理器中执行 [\_cwait](../../c-runtime-library/reference/cwait.md) 调用，然后关闭在关联管道的流。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_pclose`|\<stdio.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_pipe](../../c-runtime-library/reference/pipe.md)   
 [\_popen、\_wpopen](../../c-runtime-library/reference/popen-wpopen.md)