---
title: 进程和环境控制 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- processes, stopping
- processes, administrative tasks
- parent process
- processes, starting
- environment control routines
- process control routines
ms.assetid: 7fde74c3-c2a6-4d15-84b8-092160d60c3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e52284db986ec642724f97aae75a9af004339b40
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392466"
---
# <a name="process-and-environment-control"></a>进程和环境控制

使用进程控制例程启动、停止和管理程序内的进程。 使用环境控制例程获取和更改与操作系统环境有关的信息。

## <a name="process-and-environment-control-functions"></a>进程和环境控制函数

|例程所返回的值|使用|
|-------------|---------|
|[abort](../c-runtime-library/reference/abort.md)|中止进程而无需刷新缓冲区或调用通过 atexit 和 _onexit 注册的函数|
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md)|测试逻辑错误|
|[_ASSERT、_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 宏|类似于 assert，但仅在运行时库的调试版本中可用|
|[atexit](../c-runtime-library/reference/atexit.md)|在程序终止时执行的计划例程|
|[_beginthread、_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)|在 Windows 操作系统进程中创建新的线程|
|[_cexit](../c-runtime-library/reference/cexit-c-exit.md)|执行 exit 终止过程（例如刷新缓冲区），然后在不终止进程的情况下将控制权返回到调用程序|
|[_c_exit](../c-runtime-library/reference/cexit-c-exit.md)|执行 _exit 终止过程，然后在不终止进程的情况下将控制权返回到调用程序|
|[_cwait](../c-runtime-library/reference/cwait.md)|请等待，直到另一个进程终止|
|[_endthread、_endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)|终止一个 Windows 操作系统线程|
|[_execl、_wexecl](../c-runtime-library/reference/execl-wexecl.md)|使用参数列表执行新进程|
|[_execle、_wexecle](../c-runtime-library/reference/execle-wexecle.md)|使用参数列表和给定的环境执行新进程|
|[_execlp、_wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|使用 PATH 变量和参数列表执行新进程|
|[_execlpe、_wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|使用 PATH 变量、给定的环境和参数列表执行新进程 |
|[_execv、_wexecv](../c-runtime-library/reference/execv-wexecv.md)|使用参数数组执行新进程|
|[_execve、_wexecve](../c-runtime-library/reference/execve-wexecve.md)|使用参数数组和给定的环境执行新进程|
|[_execvp、_wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|使用 PATH 变量和参数数组执行新进程|
|[_execvpe、_wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|使用 PATH 变量、给定的环境和参数数组执行新进程|
|[exit](../c-runtime-library/reference/exit-exit-exit.md)|调用通过 atexit 和 _onexit 注册的函数，刷新所有缓冲区，关闭所有打开的文件，然后终止进程|
|[_exit](../c-runtime-library/reference/exit-exit-exit.md)|立即终止进程，无需调用 atexit 或 _onexit 或刷新缓冲区|
|[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)、[getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|获取环境变量的值|
|[_getpid](../c-runtime-library/reference/getpid.md)|获取进程 ID 号|[System::Diagnostics::Process::Id](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.id.aspx)|
|[longjmp](../c-runtime-library/reference/longjmp.md)|还原保存的堆栈环境；使用它来执行非本地 goto|
|[_onexit](../c-runtime-library/reference/onexit-onexit-m.md)|在程序终止时执行的计划例程；用于与 Microsoft C/C++ 版本 7.0 和更早版本的兼容性|
|[_pclose](../c-runtime-library/reference/pclose.md)|等待新命令处理器并关闭关联管道上的流|
|[perror、_wperror](../c-runtime-library/reference/perror-wperror.md)|打印错误消息|
|[_pipe](../c-runtime-library/reference/pipe.md)|创建用于读取和写入的管道|
|[_popen、_wpopen](../c-runtime-library/reference/popen-wpopen.md)|创建管道，然后执行命令|
|[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)、[_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)|添加或更改环境变量的值|
|[raise](../c-runtime-library/reference/raise.md)|将信号发送到调用进程|
|[setjmp](../c-runtime-library/reference/setjmp.md)|保存堆栈环境；用于执行非本地 goto|
|[signal](../c-runtime-library/reference/signal.md)|处理中断信号|
|[_spawnl、_wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|使用指定的参数列表创建和执行新进程|
|[_spawnle、_wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|使用指定的参数列表和环境创建和执行新进程|
|[_spawnlp、_wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|使用 PATH 变量和指定的参数列表创建和执行新进程|
|[_spawnlpe、_wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|使用 PATH 变量、指定的环境和参数列表创建和执行新进程|
|[_spawnv、_wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|使用指定的参数数组创建和执行新进程|
|[_spawnve、_wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|使用指定的环境和参数数组创建和执行新进程|
|[_spawnvp、_wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|使用 PATH 变量和指定的参数数组创建和执行新进程|
|[_spawnvpe、_wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|使用 PATH 变量、指定的环境和参数数组创建和执行新进程|
|[system、_wsystem](../c-runtime-library/reference/system-wsystem.md)|执行操作系统命令|

 在 Windows 操作系统中，生成的进程等同于正在生成的进程。 任何进程都可以使用 _cwait 等待其进程 ID 为已知的任何其他进程。

 _exec 和 _spawn 系列间的差异是：_spawn 函数可以将新进程中的控制权返回到调用进程。 在 _spawn 函数中，除非已指定 _P_OVERLAY，否则调用进程以及新进程都存在于内存中。 在 _exec 函数中，新进程将覆盖调用进程，因此除非在尝试启动新进程的执行中发生错误，否则控制权不能返回到调用进程。

 如下表所示，_exec 系列中函数间的差异以及 _spawn 系列中函数间的差异涉及以下方面：查找要作为新进程执行的文件的方法、参数传递到新进程的形式和设置环境的方法。 如果参数的数目为常数或在编译时已知，请使用传递参数列表的函数。 如果参数的数目需要在运行时确定，请使用将指针传递到包含参数的数组中的函数。 下表中的信息还适用于 _spawn 和 _exec 函数的宽字符对应项。

### <a name="spawn-and-exec-function-families"></a>_spawn 和 _exec 函数系列

|函数|使用 PATH 变量查找文件|参数传递约定|环境设置|
|---------------|--------------------------------------|----------------------------------|--------------------------|
|_execl、_spawnl|否|列表|继承自调用进程|
|_execle、_spawnle|否|列表|指向作为最后一个参数传递的新进程的环境表|
|_execlp、_spawnlp|是|列表|继承自调用进程|
|_execvpe、_spawnvpe|是|数组|指向作为最后一个参数传递的新进程的环境表|
|_execlpe、_spawnlpe|是|列表|指向作为最后一个参数传递的新进程的环境表|
|_execv、_spawnv|否|数组|继承自调用进程|
|_execve、_spawnve|否|数组|指向作为最后一个参数传递的新进程的环境表|
|_execvp、_spawnvp|是|数组|继承自调用进程|

## <a name="see-also"></a>请参阅

[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
