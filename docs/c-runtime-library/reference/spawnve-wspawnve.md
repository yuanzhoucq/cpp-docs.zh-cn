---
title: _spawnve、_wspawnve
ms.date: 11/04/2016
apiname:
- _spawnve
- _wspawnve
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
- wspawnve
- _spawnve
- _wspawnve
- spawnve
helpviewer_keywords:
- _spawnve function
- spawnve function
- wspawnve function
- processes, creating
- _wspawnve function
- processes, executing new
- process creation
ms.assetid: 26d1713d-b551-4f21-a07b-e9891a2ae6cf
ms.openlocfilehash: 3e3a8d3cf476dfff7c74007ec371c39f5128bbe7
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326467"
---
# <a name="spawnve-wspawnve"></a>_spawnve、_wspawnve

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
指向参数的指针的数组。 自变量*argv*[0] 通常是路径指向实际模式中或为程序名称在受保护模式下，并*argv*[1] 通过*argv*[**n**] 是指向构成新参数列表的字符串。 自变量*argv*[**n** + 1] 必须**NULL**指针，用以标记参数列表的末尾。

*envp*<br/>
指向环境设置的指针的数组。

## <a name="return-value"></a>返回值

从同步的返回值 **_spawnve**或 **_wspawnve** (**_P_WAIT**指定为*模式*) 是新进程的退出状态. 异步的返回值 **_spawnve**或 **_wspawnve** (**_P_NOWAIT**或者 **_P_NOWAITO**指定为*模式*) 是进程句柄。 如果进程正常终止，则退出状态为 0。 如果生成的进程专门调用时将退出状态设置为非零值**退出**例程具有非零参数。 如果更新过程没有显式设置正退出状态，则正退出状态指示因中止或中断而异常退出。 返回值-1 指示的错误 （未启动新进程）。 在这种情况下， **errno**设置为以下值之一。

|||
|-|-|
| **E2BIG** | 参数列表超过 1024 个字节。 |
| **EINVAL** | *模式*参数无效。 |
| **ENOENT** | 未找到文件或路径。 |
| **ENOEXEC** | 指定的文件不是可执行文件或者有无效的可执行文件格式。 |
| **ENOMEM** | 没有足够的内存可用于执行新进程。 |

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

所有这些函数将创建并执行一个新进程，同时将一个指针数组传递给命令行自变量，并将一个指针数组传递给环境设置。

这些函数验证其参数。 如果任一*cmdname*或*argv*是 null 指针，或者，如果*argv*指向 null 指针，或*argv*[0] 为空字符串，无效调用的参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许继续执行，这些函数将设置**errno**到**EINVAL**，并返回-1。 不生成任何新进程。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_spawnve**|\<stdio.h> 或 \<process.h>|
|**_wspawnve**|\<stdio.h> 或 \<wchar.h>|

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
