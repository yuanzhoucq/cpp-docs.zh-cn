---
title: _execvpe，_wexecvpe
ms.date: 4/2/2020
api_name:
- _execvpe
- _wexecvpe
- _o__execvpe
- _o__wexecvpe
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
- wexecvpe
- _wexecvpe
- _execvpe
helpviewer_keywords:
- wexecvpe function
- execvpe function
- _wexecvpe function
- _execvpe function
ms.assetid: c0c3c986-d9c0-4814-a96c-10f0b3092766
ms.openlocfilehash: dd2e4c91affe211cc58a2f1c147646172f3f34c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347645"
---
# <a name="_execvpe-_wexecvpe"></a>_execvpe，_wexecvpe

加载并运行新的子进程。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
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

### <a name="parameters"></a>参数

*cmdname*<br/>
要执行的文件的路径。

*Argv*<br/>
指向参数的指针的数组。

*恩vp*<br/>
指向环境设置的指针的数组。

## <a name="return-value"></a>返回值

如果成功，这些函数不返回到调用进程。 返回值 -1 表示错误，在这种情况下将设置**errno**全局变量。

|**errno**值|说明|
|-------------------|-----------------|
|**E2BIG**|自变量和环境设置所需的空间超过 32 KB。|
|**EACCES**|指定的文件具有锁定或共享冲突。|
|**EMFILE**|打开的文件太多。 （必须打开指定的文件以确定它是否是可执行文件。）|
|**埃诺恩特**|未找到文件或路径。|
|**ENOEXEC**|指定的文件不是可执行文件或者有无效的可执行文件格式。|
|**ENOMEM**|没有足够的内存可用于执行新进程；可用内存损坏；或存在无效块（这表明调用进程未进行正确分配）。|

有关这些代码及其他返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

其中每个函数都将加载并执行一个新进程，同时将一个指针数组传递给命令行自变量，并将一个指针数组传递给环境设置。 这些函数使用**PATH**环境变量来查找要执行的文件。

**_execvpe**函数验证其参数。 如果*cmdname*是空指针，或者如果*argv*是空指针、指向空数组的指针或指向包含空字符串作为第一个参数的数组的指针，则这些函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，这些函数将**errno**设置为**EINVAL**并返回 -1。 不启动任何进程。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|可选标头|
|--------------|---------------------|---------------------|
|**_execvpe**|\<process.h>|\<errno.h>|
|**_wexecvpe**|\<process.h> 或 \<wchar.h>|\<errno.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)中的示例。

## <a name="see-also"></a>另请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[中止](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
