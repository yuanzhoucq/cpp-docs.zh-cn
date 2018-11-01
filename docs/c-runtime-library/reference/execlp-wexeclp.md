---
title: _execlp，_wexeclp
ms.date: 11/04/2016
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
helpviewer_keywords:
- execlp function
- _execlp function
- _wexeclp function
- wexeclp function
ms.assetid: 7b179163-4bcd-4d6a-8baf-68f886791928
ms.openlocfilehash: db13263ca4574d59821d5783b9ae83f278fef14d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506634"
---
# <a name="execlp-wexeclp"></a>_execlp，_wexeclp

加载和执行新的子进程。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
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

### <a name="parameters"></a>参数

*cmdname*<br/>
要执行的文件的路径。

*arg0*，...*argn*<br/>
指向参数的指针的列表。

## <a name="return-value"></a>返回值

如果成功，这些函数不返回到调用进程。 返回值-1 指示错误，在这种情况下**errno**设置全局变量。

|**errno**值|描述|
|-------------------|-----------------|
|**E2BIG**|自变量和环境设置所需的空间超过 32 KB。|
|**EACCES**|指定的文件具有锁定或共享冲突。|
|**EINVAL**|参数无效。|
|**EMFILE**|打开的文件太多 (必须打开指定的文件以确定它是否是可执行文件)。|
|**ENOENT**|未找到文件或路径。|
|**ENOEXEC**|指定的文件不是可执行文件或者有无效的可执行文件格式。|
|**ENOMEM**|没有足够的内存可用于执行更新进程；可用内存损坏；或存在无效的块，指示调用进程未正确分配。|

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

所有这些函数将加载并执行新进程，每个命令行实参作为独立的形参传递，并使用**路径**环境变量查找要执行的文件。

**_Execlp**函数验证其参数。 如果*cmdname*或*arg0*是空指针或空字符串，这些函数将调用无效参数处理程序中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许继续执行，这些函数将设置**errno**到**EINVAL**并返回-1。 将不启动新进程。

## <a name="requirements"></a>要求

|函数|必需的标头|可选标头|
|--------------|---------------------|---------------------|
|**_execlp**|\<process.h>|\<errno.h>|
|**_wexeclp**|\<process.h> 或 \<wchar.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)中的示例。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
