---
title: "_execvpe、_wexecvpe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_execvpe"
  - "_wexecvpe"
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
  - "wexecvpe"
  - "execvpe"
  - "_wexecvpe"
  - "_execvpe"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_execvpe 函数"
  - "_wexecvpe 函数"
  - "execvpe 函数"
  - "wexecvpe 函数"
ms.assetid: c0c3c986-d9c0-4814-a96c-10f0b3092766
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _execvpe、_wexecvpe
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

加载并运行新的子进程。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/ZH-CN/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
intptr_t _execvpe(   
   const char *cmdname,  
   const char *const *argv,  
   const char *const *envp   
);  
intptr_t _wexecvpe(   
   const wchar_t *cmdname,  
   const wchar_t *const *argv,  
   const wchar_t *const *envp   
);  
```  
  
#### 参数  
 `cmdname`  
 要执行的文件的路径。  
  
 `argv`  
 指向参数的指针的数组。  
  
 `envp`  
 指向环境设置的指针的数组。  
  
## 返回值  
 如果成功，这些函数不返回到调用进程。  返回值 –1 表示错误，在此情况下将会设置 `errno` 全局变量。  
  
|`errno` 值|说明|  
|---------------|--------|  
|`E2BIG`|参数和环境设置所需的空间超过 32 KB。|  
|`EACCES`|指定的文件具有锁定或共享冲突。|  
|`EMFILE`|打开的文件太多。  （必须打开指定的文件以确定它是否是可执行文件。）|  
|`ENOENT`|未找到文件或路径。|  
|`ENOEXEC`|指定的文件不是可执行文件或者有无效的可执行文件格式。|  
|`ENOMEM`|没有足够的内存可用于执行新进程；可用内存损坏；或存在无效块（这表明调用进程未进行正确分配）。|  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 其中每个函数都将加载并执行一个新进程，同时将一个指针数组传递给命令行参数，并将一个指针数组传递给环境设置。  这些函数使用 `PATH` 环境变量查找要执行的文件。  
  
 `_execvpe` 函数将验证其参数。  如果 `cmdname` 为空指针，或如果 `argv` 为空指针、指向一个空数组的指针或指向包含一个空字符串作为第一个参数的数组的指针，则这些函数调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 \-1。  不启动任何进程。  
  
## 要求  
  
|函数|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_execvpe`|\<process.h\>|\<errno.h\>|  
|`_wexecvpe`|\<process.h\> 或 \<wchar.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
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