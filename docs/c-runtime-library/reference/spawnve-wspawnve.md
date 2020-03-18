---
title: _spawnve、_wspawnve
ms.date: 11/04/2016
api_name:
- _spawnve
- _wspawnve
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
- wspawnve
- _spawnve
- _wspawnve
helpviewer_keywords:
- _spawnve function
- spawnve function
- wspawnve function
- processes, creating
- _wspawnve function
- processes, executing new
- process creation
ms.assetid: 26d1713d-b551-4f21-a07b-e9891a2ae6cf
ms.openlocfilehash: 37f8b6737fbd2b36c1482790a34dc386936b704b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442713"
---
# <a name="_spawnve-_wspawnve"></a>_spawnve、_wspawnve

创建并执行更新过程。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
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

### <a name="parameters"></a>参数

*模式*<br/>
调用进程的执行模式。

*cmdname*<br/>
要执行的文件的路径。

*argv*<br/>
指向参数的指针的数组。 参数*argv*[0] 通常是一个指向实际模式中的路径或保护模式中的程序的指针，而*argv*[1] 通过*argv*[**n**] 是指向构成新参数列表的字符串的指针。 参数*argv*[**n** + 1] 必须是**NULL**指针，才能标记参数列表的末尾。

*envp*<br/>
指向环境设置的指针的数组。

## <a name="return-value"></a>返回值

同步 **_spawnve**或 **_wspawnve** （为*mode*指定 **_P_WAIT** ）的返回值是新进程的退出状态。 异步 **_spawnve**或 **_wspawnve** （为*mode*指定的 **_P_NOWAIT**或 **_P_NOWAITO** ）的返回值是进程句柄。 如果进程正常终止，则退出状态为 0。 如果生成的进程专门使用非零参数调用**exit**例程，则可以将退出状态设置为一个非零值。 如果更新过程没有显式设置正退出状态，则正退出状态指示因中止或中断而异常退出。 返回值-1 表示错误（不启动新进程）。 在这种情况下， **errno**设置为以下值之一。

|||
|-|-|
| **E2BIG** | 参数列表超过 1024 个字节。 |
| **EINVAL** | *mode*参数无效。 |
| **ENOENT** | 未找到文件或路径。 |
| **ENOEXEC** | 指定的文件不是可执行文件或者有无效的可执行文件格式。 |
| **ENOMEM** | 没有足够的内存可用于执行新进程。 |

有关这些代码及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

所有这些函数将创建并执行一个新进程，同时将一个指针数组传递给命令行自变量，并将一个指针数组传递给环境设置。

这些函数验证其参数。 如果*cmdname*或*argv*为空指针，或者如果*argv*指向 null 指针，或者*argv [0*] 为空字符串，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数会将**errno**设置为**EINVAL**，并返回-1。 不生成任何新进程。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_spawnve**|\<stdio.h> 或 \<process.h>|
|**_wspawnve**|\<stdio.h> 或 \<wchar.h>|

有关兼容性的详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)中的示例。

## <a name="see-also"></a>另请参阅

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
