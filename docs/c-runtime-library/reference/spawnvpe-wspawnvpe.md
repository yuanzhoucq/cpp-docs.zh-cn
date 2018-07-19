---
title: _spawnvpe、_wspawnvpe | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _spawnvpe
- _wspawnvpe
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
- _spawnvpe
- wspawnvpe
- spawnvpe
- _wspawnvpe
dev_langs:
- C++
helpviewer_keywords:
- _wspawnvpe function
- processes, creating
- _spawnvpe function
- processes, executing new
- wspawnvpe function
- process creation
- spawnvpe function
ms.assetid: 3db6394e-a955-4837-97a1-fab1db1e6092
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55016fcc346e5894f5fd3ffe4a8e9a2f43b5ab87
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413552"
---
# <a name="spawnvpe-wspawnvpe"></a>_spawnvpe、_wspawnvpe

创建并执行更新过程。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
intptr_t _spawnvpe(
   int mode,
   const char *cmdname,
   const char *const *argv,
   const char *const *envp
);
intptr_t _wspawnvpe(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>参数

*模式*<br/>
调用进程的执行模式

*cmdname*<br/>
要执行的文件的路径

*argv*<br/>
指向参数的指针的数组。 自变量*argv*[0] 通常是路径指向实际模式中或为程序名称在受保护模式下，和*argv*[1] 通过*argv*[**n**] 是指向构成新参数列表的字符字符串的指针。 自变量*argv*[**n** + 1] 必须是**NULL**指针，用以标记自变量列表的末尾。

*envp*<br/>
指向环境设置的指针的数组

## <a name="return-value"></a>返回值

返回值从同步 **_spawnvpe**或 **_wspawnvpe** (**_P_WAIT**指定的*模式*) 是新的退出状态过程。 返回值从异步 **_spawnvpe**或 **_wspawnvpe** (**_P_NOWAIT**或 **_P_NOWAITO**指定的*模式*) 是进程句柄。 如果进程正常终止，则退出状态为 0。 则可以将退出状态设置为非零值，如果生成的进程专门调用**退出**例程具有非零参数。 如果更新过程没有显式设置正退出状态，则正退出状态指示因中止或中断而异常退出。 返回值-1 指示的错误 （不启动新过程）。 在这种情况下， **errno**设置为以下值之一：

|||
|-|-|
**E2BIG**|参数列表超过 1024 个字节。
**EINVAL**|*模式*参数无效。
**ENOENT**|未找到文件或路径。
**ENOEXEC**|指定的文件不是可执行文件或者有无效的可执行文件格式。
**ENOMEM**|没有足够的内存可用于执行新进程。

有关这些代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

所有这些函数将创建并执行一个新进程，同时将一个指针数组传递给命令行自变量，并将一个指针数组传递给环境设置。 这些函数将使用**路径**环境变量查找要执行的文件。

这些函数验证其参数。 如果任一*cmdname*或*argv*是 null 指针，或如果*argv*指向 null 指针，或*argv*[0] 为空字符串，无效调用的参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将设置**errno**到**EINVAL**，并返回-1。 不生成任何新进程。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_spawnvpe**|\<stdio.h> 或 \<process.h>|
|**_wspawnvpe**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

在参见 [_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)中的示例。

## <a name="see-also"></a>请参阅

[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
