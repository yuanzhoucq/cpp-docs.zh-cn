---
title: "_spawnlp、_wspawnlp | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wspawnlp
- _spawnlp
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
- _wspawnlp
- wspawnlp
- _spawnlp
dev_langs:
- C++
helpviewer_keywords:
- wspawnlp function
- _spawnlp function
- processes, creating
- processes, executing new
- _wspawnlp function
- process creation
- spawnlp function
ms.assetid: 74fc6e7a-4f24-4103-9387-7177875875e6
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 66172824d106860b6fa4408f85cba4a10bce696e
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="spawnlp-wspawnlp"></a>_spawnlp、_wspawnlp
创建并执行更新过程。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
intptr_t _spawnlp(  
   int mode,  
   const char *cmdname,  
   const char *arg0,  
   const char *arg1,  
   ... const char *argn,  
   NULL   
);  
intptr_t _wspawnlp(  
   int mode,  
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   const wchar_t *arg1,  
   ... const wchar_t *argn,  
   NULL   
);  
```  
  
#### <a name="parameters"></a>参数  
 `mode`  
 调用进程的执行模式。  
  
 `cmdname`  
 要执行的文件的路径。  
  
 `arg0, arg1, ... argn`  
 指向参数的指针的列表。 `arg0` 参数通常是指向 `cmdname`的指针。 参数 `arg1` 到 `argn` 是指向构成新参数列表的字符字符串的指针。 在 `argn` 之后，必须是一个 `NULL` 指针，用以标记参数列表的末尾。  
  
## <a name="return-value"></a>返回值  
 同步 `_spawnlp` 或 `_wspawnlp`（为 `_P_WAIT` 指定的 `mode`）中的返回值是新进程的退出状态。 异步 `_spawnlp` 或 `_wspawnlp` （为`_P_NOWAIT` 指定的 `_P_NOWAITO` 或 `mode`）的返回值是进程句柄。 如果进程正常终止，则退出状态为 0。 如果生成的进程专门调用具有非零参数的 `exit` 例程，则可以将退出状态设置为一个非零值。 如果更新过程没有显式设置正退出状态，则正退出状态指示因中止或中断而异常退出。 返回值-1 指示的错误 （不启动新过程）。 在这种情况下， `errno` 设置为下列值之一。  
  
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
  
 有关这些代码及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 这些函数将创建并执行一个新进程，并将每个命令行实参作为独立的形参传递，并且使用 `PATH` 环境变量以查找要执行的文件。  
  
 这些函数验证其参数。 如果 `cmdname` 或 `arg0` 是空字符串或 null 指针，则这些函数将生成无效的参数异常，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL`，并返回 -1。 不生成任何新进程。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_spawnlp`|\<process.h>|  
|`_wspawnlp`|\<stdio.h> 或 \<wchar.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 在参见 [_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)中的示例。  
  
## <a name="see-also"></a>另请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_flushall](../../c-runtime-library/reference/flushall.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_onexit、_onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [system、_wsystem](../../c-runtime-library/reference/system-wsystem.md)
