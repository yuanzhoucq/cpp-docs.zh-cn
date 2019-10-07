---
title: _spawnl、_wspawnl
ms.date: 11/04/2016
api_name:
- _wspawnl
- _spawnl
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- spawnl
- wspawnl
- _wspawnl
- _spawnl
helpviewer_keywords:
- spawnl function
- processes, creating
- _spawnl function
- processes, executing new
- _wspawnl function
- wspawnl function
- process creation
ms.assetid: dd4584c9-7173-4fc5-b93a-6e7d3c2316d7
ms.openlocfilehash: b39e76b010fd0d3b9ae3dc8d0104c69ce97ac87e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947826"
---
# <a name="_spawnl-_wspawnl"></a>_spawnl、_wspawnl

创建并执行更新过程。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
intptr_t _spawnl(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL
);
intptr_t _wspawnl(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *arg0,
   const wchar_t *arg1,
   ... const wchar_t *argn,
   NULL
);
```

### <a name="parameters"></a>参数

*模式*<br/>
调用进程的执行模式。

*cmdname*<br/>
要执行的文件的路径。

*arg0*， *arg1*，.。。*argn*<br/>
指向参数的指针的列表。 *Arg0*参数通常是指向*cmdname*的指针。 参数*arg1*到*argn*是指向构成新参数列表的字符串的指针。 在*argn*之后，必须有一个**NULL**指针，用于标记参数列表的末尾。

## <a name="return-value"></a>返回值

同步 **_spawnl**或 **_wspawnl** （为*mode*指定的 **_P_WAIT** ）的返回值是新进程的退出状态。 异步 **_spawnl**或 **_wspawnl** （为*Mode*指定的 **_P_NOWAIT**或 **_P_NOWAITO** ）的返回值是进程句柄。 如果进程正常终止，则退出状态为 0。 如果生成的进程专门使用非零参数调用**exit**例程，则可以将退出状态设置为一个非零值。 如果更新过程没有显式设置正退出状态，则正退出状态指示因中止或中断而异常退出。 返回值-1 表示错误（不启动新进程）。 在这种情况下， **errno**设置为以下值之一。

|||
|-|-|
| **E2BIG** | 参数列表超过 1024 个字节。 |
| **EINVAL** | *mode*参数无效。 |
| **ENOENT** | 未找到文件或路径。 |
| **ENOEXEC** | 指定的文件不是可执行文件或者有无效的可执行文件格式。 |
| **ENOMEM** | 没有足够的内存可用于执行新进程。 |

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

这些函数验证其参数。 如果*cmdname*或*arg0*为空字符串或 null 指针，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数会将**errno**设置为**EINVAL**，并返回-1。 不生成任何新进程。

## <a name="remarks"></a>备注

这些函数将创建并执行一个新进程，并将每个命令行实参作为独立的形参传递。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_spawnl**|\<process.h>|
|**_wspawnl**|\<stdio.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

在参见 [_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)中的示例。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
