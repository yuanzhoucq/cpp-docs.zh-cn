---
title: "_execlpe、_wexeclpe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_execlpe"
  - "_wexeclpe"
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
  - "_wexeclpe"
  - "execlpe"
  - "wexeclpe"
  - "_execlpe"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_execlpe 函数"
  - "_wexeclpe 函数"
  - "execlpe 函数"
  - "wexeclpe 函数"
ms.assetid: 07b861da-3e7e-4f1d-bb80-ad69b55e5162
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# _execlpe、_wexeclpe
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

加载和执行新的子进程。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
intptr_t _execlpe(   
   const char *cmdname,  
   const char *arg0,  
   ... const char *argn,  
   NULL,  
   const char *const *envp   
);  
intptr_t _wexeclpe(   
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   ... const wchar_t *argn,  
   NULL,  
   const wchar_t *const *envp   
);  
```  
  
#### 参数  
 `cmdname`  
 要执行的文件的路径。  
  
 `arg0`, `...``argn`  
 指向参数的指针数组。  
  
 `envp`  
 指向环境设置的指针的数组。  
  
## 返回值  
 如果成功，这些函数不返回到调用进程。  返回值 –1 表示错误，在此情况下将会设置 `errno` 全局变量。  
  
|`errno` 值|描述|  
|---------------|--------|  
|`E2BIG`|参数和环境设置所需的空间超过 32 KB。|  
|`EACCES`|指定的文件具有锁定或共享冲突。|  
|`EINVAL`|无效参数。|  
|`EMFILE`|打开的文件太多 \(必须打开指定的文件以确定它是否是可执行文件\)。|  
|`ENOENT`|未找到文件或路径。|  
|`ENOEXEC`|指定的文件不是可执行文件或者有无效的可执行文件格式。|  
|`ENOMEM`|没有足够的内存可用于执行更新进程；可用内存损坏；或存在无效的块，指示调用进程未正确分配。|  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 每一个函数加载并且执行一个新的进程，把每一个命令行的参数作为独立的参数进行传递，并且给环境设置传递一个数组指针。  这些函数使用 `PATH` 环境变量查找要执行的文件。  
  
 `_execlpe` 函数验证其参数.  如果 `cmdname` 或 `arg0` 为空指针或空字符串，这些函数调用无效参数处理程序如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则这些功能将 `EINVAL` 设置为 `errno` 并返回 \-1。  不启动任何新进程。  
  
## 要求  
  
|功能|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_execlpe`|\<process.h\>|\<errno.h\>|  
|`_wexeclpe`|\<process.h\> 或\<wchar.h\>|\<errno.h\>|  
  
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