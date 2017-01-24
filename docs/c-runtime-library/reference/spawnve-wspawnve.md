---
title: "_spawnve、_wspawnve | Microsoft Docs"
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
  - "_spawnve"
  - "_wspawnve"
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
  - "wspawnve"
  - "_spawnve"
  - "_wspawnve"
  - "spawnve"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_spawnve 函数"
  - "_wspawnve 函数"
  - "进程创建"
  - "进程, 创建"
  - "进程, 执行新的"
  - "spawnve 函数"
  - "wspawnve 函数"
ms.assetid: 26d1713d-b551-4f21-a07b-e9891a2ae6cf
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _spawnve、_wspawnve
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建并执行更新过程。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
intptr_t _spawnve(  
   int mode,  
   const char *cmdname,  
   const char *const *argv,  
   const char *const *envp   
);  
intptr_t _wspawnve(  
   int mode,  
   const wchar_t *cmdname,  
   const wchar_t *const *argv,  
   const wchar_t *const *envp   
);  
```  
  
#### 参数  
 `mode`  
 调用进程的执行模式。  
  
 `cmdname`  
 要执行的文件的路径。  
  
 `argv`  
 指向参数的指针的数组。  参数 `argv`\[0\] 通常是一个指向实际模式中的路径或保护模式中的程序的指针， `argv`\[1\] 通过 `argv`\[`n`\] 是指向形成新的参数列表的字符串的指针。  参数 `argv`\[`n` \+1\] 必须是一个 `NULL` 指针，用以标记参数列表的末尾。  
  
 `envp`  
 指向环境设置的指针的数组。  
  
## 返回值  
 从同步 `_spawnve` 或 `_wspawnve` \(为 `mode`指定的`_P_WAIT`\) 的返回值是更新过程的退出状态。  异步 `_spawnve` 或 `_wspawnve` 的返回值 \(为 `mode`指定的 `_P_NOWAITO`或`_P_NOWAIT` \) 是处理句柄。  如果进程正常终止，则退出状态为 0。  如果生成的进程专门调用具有非零参数的 `exit` 例程，则可以将退出状态设置为一个非零值。  如果更新过程没有显式设置正退出状态，则正退出状态指示因中止或中断而异常退出。  返回值 –1 表示错误 \(不启动新过程\)。  在这种情况下，`errno` 设置为下列值之一。  
  
 `E2BIG`  
 参数列表超过 1024 个字节。  
  
 `EINVAL`  
 `mode` 参数无效。  
  
 `ENOENT`  
 未找到文件或路径。  
  
 `ENOEXEC`  
 指定的文件不是可执行文件或者有无效的可执行文件格式。  
  
 `ENOMEM`  
 没有足够的内存可用于执行新进程。  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 这些功能中的每个创建并执行一个新进程，通过一组指向命令行参数和一组指向环境设置的指针。  
  
 这些函数验证其参数。  如果 `cmdname` 或 `argv` 是空指针，或者，如果 `argv` 指向空指针或 `argv[0]` 是空字符串，调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则这些功能将 `EINVAL` 设置为 `errno`，并返回 \-1。  不生成任何新进程。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_spawnve`|\<stdio.h\>或 \<process.h\>|  
|`_wspawnve`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 在参见 [\_spawn、\_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)中的示例。  
  
## .NET Framework 等效项  
  
-   [System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)  
  
-   [System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_spawn, \_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [\_exec、\_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_flushall](../../c-runtime-library/reference/flushall.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_onexit、\_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [system、\_wsystem](../../c-runtime-library/reference/system-wsystem.md)