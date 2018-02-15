---
title: "_execlp、_wexeclp | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wexeclp
- _execlp
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wexeclp
- wexeclp
- _execlp
dev_langs:
- C++
helpviewer_keywords:
- execlp function
- _execlp function
- _wexeclp function
- wexeclp function
ms.assetid: 7b179163-4bcd-4d6a-8baf-68f886791928
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ccb8839311b3b946461cd8ae1e0c9866c1aa4c2e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="execlp-wexeclp"></a>_execlp，_wexeclp
加载和执行新的子进程。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。  
  
## <a name="syntax"></a>语法  
  
```  
intptr_t _execlp(   
   const char *cmdname,  
   const char *arg0,  
   ... const char *argn,  
   NULL   
);  
intptr_t _wexeclp(   
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   ... const wchar_t *argn,  
   NULL   
);  
```  
  
#### <a name="parameters"></a>参数  
 `cmdname`  
 要执行的文件的路径。  
  
 `arg0, ... argn`  
 指向参数的指针的列表。  
  
## <a name="return-value"></a>返回值  
 如果成功，这些函数不返回到调用进程。 返回值-1 指示错误，在这种情况下`errno`设置全局变量。  
  
|`errno` 值|描述|  
|-------------------|-----------------|  
|`E2BIG`|自变量和环境设置所需的空间超过 32 KB。|  
|`EACCES`|指定的文件具有锁定或共享冲突。|  
|`EINVAL`|参数无效。|  
|`EMFILE`|打开的文件太多 (必须打开指定的文件以确定它是否是可执行文件)。|  
|`ENOENT`|未找到文件或路径。|  
|`ENOEXEC`|指定的文件不是可执行文件或者有无效的可执行文件格式。|  
|`ENOMEM`|没有足够的内存可用于执行更新进程；可用内存损坏；或存在无效的块，指示调用进程未正确分配。|  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 这些函数将加载并执行一个新进程，并将每个命令行实参作为独立的形参传递，并且使用 `PATH` 环境变量以查找要执行的文件。  
  
 `_execlp` 函数将验证其参数。 如果 `cmdname` 或 `arg0` 是空指针或空字符串，这些函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 -1。 将不启动新进程。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|可选标头|  
|--------------|---------------------|---------------------|  
|`_execlp`|\<process.h>|\<errno.h>|  
|`_wexeclp`|\<process.h> 或 \<wchar.h>|\<errno.h>|  
  
 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)中的示例。  
  
## <a name="see-also"></a>请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit、_onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system、_wsystem](../../c-runtime-library/reference/system-wsystem.md)