---
title: _spawnv、_wspawnv
ms.date: 4/2/2020
api_name:
- _wspawnv
- _spawnv
- _o__spawnv
- _o__wspawnv
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wspawnv
- _spawnv
- _wspawnv
helpviewer_keywords:
- wspawnv function
- processes, creating
- _spawnv function
- processes, executing new
- process creation
- _wspawnv function
- spawnv function
ms.assetid: 72360ef4-dfa9-44c1-88c1-b3ecb660aa7d
ms.openlocfilehash: f4a4d695e265c28efd1b9da8588752d8b2635163
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355898"
---
# <a name="_spawnv-_wspawnv"></a>_spawnv、_wspawnv

创建并执行更新过程。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
intptr_t _spawnv(
   int mode,
   const char *cmdname,
   const char *const *argv
);
intptr_t _wspawnv(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>参数

*模式*<br/>
调用进程的执行模式。

*cmdname*<br/>
要执行的文件的路径。

*Argv*<br/>
指向参数的指针的数组。 参数*argv*{0} 通常是指向实际模式下的路径或受保护模式下的程序名称的指针 *，argv*[1] 到*argv*=**n**= 是指向构成新参数列表的字符串的指针。 参数*argv*=**n** [1] 必须是**NULL**指针，以标记参数列表的末尾。

## <a name="return-value"></a>返回值

来自同步 **_spawnv**或 **_wspawnv**的返回值 **（_P_WAIT**为*模式*指定）是新进程的退出状态。 来自异步 **_spawnv**或 **_wspawnv（_P_NOWAIT**或 **_wspawnv**为*模式*指定的 **_P_NOWAITO）** 的返回值是进程句柄。 如果进程正常终止，则退出状态为 0。 如果生成的进程专门使用非零参数调用**退出**例程，则可以将退出状态设置为非零值。 如果更新过程没有显式设置正退出状态，则正退出状态指示因中止或中断而异常退出。 返回值 -1 表示错误（未启动新进程）。 在这种情况下 **，errno**设置为以下值之一。

|||
|-|-|
| **E2BIG** | 参数列表超过 1024 个字节。 |
| **埃因瓦尔** | *模式*参数无效。 |
| **埃诺恩特** | 未找到文件或路径。 |
| **ENOEXEC** | 指定的文件不是可执行文件或者有无效的可执行文件格式。 |
| **ENOMEM** | 没有足够的内存可用于执行新进程。 |

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

所有这些函数将创建并执行一个新进程，同时将一个指针数组传递给命令行参数。

这些函数验证其参数。 如果*cmdname*或*argv*是空指针，或者如果*argv*指向空指针，或者*argv*[0] 是空字符串，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，这些函数将**errno**设置为**EINVAL**，并返回 -1。 不生成任何新进程。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_spawnv**|\<stdio.h> 或 \<process.h>|
|**_wspawnv**|\<stdio.h> 或 \<wchar.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

在参见 [_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)中的示例。

## <a name="see-also"></a>另请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[中止](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
