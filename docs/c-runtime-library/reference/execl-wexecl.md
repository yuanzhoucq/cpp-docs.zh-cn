---
title: "_execl、_wexecl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_execl"
  - "_wexecl"
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
  - "api-ms-win-crt-process-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_execl"
  - "_wexecl"
  - "wexecl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_execl 函数"
  - "_wexecl 函数"
  - "execl 函数"
  - "wexecl 函数"
ms.assetid: 81fefb8a-0a06-4221-b2bc-be18e38e89f4
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _execl、_wexecl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

加载和执行新的子进程。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
intptr_t _execl(   
   const char *cmdname,  
   const char *arg0,  
   ... const char *argn,  
   NULL   
);  
intptr_t _wexecl(  
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   ... const wchar_t *argn,  
   NULL   
);  
```  
  
#### 参数  
 `cmdname`  
 要执行的文件的路径。  
  
 `arg0`, `...``argn`  
 指向参数的指针列表。  
  
## 返回值  
 如果成功，这些函数不返回到调用进程。  返回值 –1 表示错误，在此情况下将会设置 `errno` 全局变量。  
  
|errno 值|描述|  
|-------------|--------|  
|`E2BIG`|参数和环境设置所需的空间超过 32 KB。|  
|`EACCES`|指定的文件具有锁定或共享冲突。|  
|`EINVAL`|无效参数 \(一个或多个参数是一个空指针或空字符串\)。|  
|`EMFILE`|打开的文件太多 \(必须打开指定的文件以确定它是否是可执行文件\)。|  
|`ENOENT`|未找到文件或路径。|  
|`ENOEXEC`|指定的文件不是可执行文件或者有无效的可执行文件格式。|  
|`ENOMEM`|没有足够的内存可用于执行更新进程；可用内存损坏；或存在无效的块，指示调用进程未正确分配。|  
  
## 备注  
 这些函数中的每一个加载并执行新进程，通过每个命令行参数作为单独的参数。  第一个参数是命令或可执行文件，文件名，第二个参数应与第一个相同。  在执行进程中，它是 `argv[0]` 。  第三个参数是第一个参数，`argv[1]`进程正在执行。  
  
 `_execl` 函数验证其参数.  如果 `cmdname` 或 `arg0` 是 null 指针或空字符串，这些函数调用的参数无效处理程序如 [参数验证](../../c-runtime-library/parameter-validation.md)所述（如果执行允许继续，这些函数将 `errno`设置为 `EINVAL` 并且返回 \-1）。  不执行任何新进程。  
  
## 要求  
  
|功能|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_execl`|\<process.h\>|\<errno.h\>|  
|`_wexecl`|\<process.h\> 或 \<wchar.h\>|\<errno.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 在参见 [\_exec、\_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)中的示例。  
  
## .NET Framework 等效项  
  
-   [System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)  
  
-   [System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_exec、\_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_onexit、\_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_spawn, \_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system、\_wsystem](../../c-runtime-library/reference/system-wsystem.md)