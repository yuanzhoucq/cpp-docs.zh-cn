---
title: "signal | Microsoft 文档"
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: signal
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords: signal
dev_langs: C++
helpviewer_keywords: signal function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 337bc5e222ee7fcb313d0b7ea0722dbb5cacea75
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2018
---
# <a name="signal"></a>signal

设置中断信号处理。

> [!IMPORTANT]
> 不要使用此方法可以在测试或调试方案中关闭除 Microsoft 应用商店应用。 编程或 UI 方式关闭应用商店应用程序不允许根据[Microsoft 存储策略](http://go.microsoft.com/fwlink/?LinkId=865936)。 有关详细信息，请参阅[UWP 应用生命周期](http://go.microsoft.com/fwlink/p/?LinkId=865934)。

## <a name="syntax"></a>语法

```C
void (__cdecl *signal(
   int sig,
   void (__cdecl *func ) (int [, int ] )))(int);
```

### <a name="parameters"></a>参数
_sig_  
信号值。

_func_  
要执行的函数。 第一个参数是信号值，第二个参数是可在第一个参数为 SIGFPE 时使用的子代码。

## <a name="return-value"></a>返回值

`signal`返回的先前值_func_ ，具有与给定信号关联。 例如，如果以前的值_func_已`SIG_IGN`，返回值也为`SIG_IGN`。 `SIG_ERR` 的返回值表示错误；在这种情况下，`errno` 将设置为 `EINVAL`。

有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

利用 `signal` 函数，进程可以从几种方法中选择一种来处理来自操作系统的中断信号。 _Sig_自变量是的中断`signal`响应; 它必须是定义信号中的以下清单常量之一。H。

|_sig_值|描述|
|-----------------|-----------------|
|`SIGABRT`|异常终止|
|`SIGFPE`|浮点错误|
|`SIGILL`|非法指令|
|`SIGINT`|Ctrl+C 信号|
|`SIGSEGV`|非法存储区访问|
|`SIGTERM`|终止请求|

如果_sig_不是一个的上述值的无效参数处理程序会调用，如中定义[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 `SIG_ERR`。

默认情况下，`signal`终止调用程序，而不考虑的值的退出代码 3， _sig_。

> [!NOTE]
> 任何 Win32 应用程序都不支持 `SIGINT`。 当 Ctrl+C 中断发生时，Win32 操作系统将专门生成新的线程来处理中断。 这可能导致单线程应用程序（如 UNIX 中的此类应用程序）变成多线程应用程序并导致意外行为。

_Func_自变量是你编写的信号处理或预定义常量之一的地址`SIG_DFL`或`SIG_IGN`，信号中也定义。H。 如果_func_是一个函数，为给定信号的信号处理程序安装。 信号处理程序的原型需要一个的形式自变量， _sig_，类型的`int`。 操作系统提供通过实参_sig_发生中断时; 当自变量是生成中断的信号。 因此，您可以在信号处理程序中使用六个清单常量（在前面的表中列出）来确定发生了哪种中断并采取相应措施。 例如，你可以调用`signal`两次来将同一处理程序分配给两个不同的信号，然后测试_sig_中要采取不同的操作的处理程序自变量基于收到的信号。

如果你要测试浮点异常 (`SIGFPE`)， _func_指向采用可选的第二个参数之一的几个清单常量的函数-浮点数中定义。H-窗体的`FPE_xxx`。 当 `SIGFPE` 信号发生时，您可以测试第二个参数的值以确定浮点异常的类型，然后采取相应措施。 此参数及其可能的值是 Microsoft 扩展名。

对于浮点异常，值_func_不会重置时接收到信号。 若要从浮点异常恢复，请使用 try/except 子句包围浮点运算。 将[setjmp](../../c-runtime-library/reference/setjmp.md) 与 [longjmp](../../c-runtime-library/reference/longjmp.md) 一起使用也能恢复。 在任一情况下，调用进程都会继续执行，并保留未定义的进程的浮点状态。

如果信号处理程序返回，调用进程将在收到断点信号后立即继续执行。 无论信号或操作模式的类型如何都是如此。

执行指定的函数之前的值_func_设置为`SIG_DFL`。 下一个中断信号将按照为 `SIG_DFL` 描述的方法处理，除非对 `signal` 的干预调用另行指定。 您可以使用此功能在所调用的函数中重置信号。

由于信号处理程序例程通常在中断发生时异步调用，当运行时操作不完整且处于未知状态时，您的信号处理程序可能受到控制。 以下列表汇总了一些限制，用来确定您可在信号处理程序例程中使用的函数。

- 不要发出低级别或 STDIO.H I/O 例程（例如，`printf` 或 `fread`）。

- 不要调用堆例程或任何使用堆例程的例程（例如，`malloc`、`_strdup` 或 `_putenv`）。 有关详细信息，请参阅 [malloc](../../c-runtime-library/reference/malloc.md)。

- 不要使用生成系统调用的任何函数（例如，`_getcwd` 或 `time`）。

- 不要使用`longjmp`除非中断由浮点异常 (也就是说， _sig_是`SIGFPE`)。 在这种情况下，首先应使用对 `_fpreset` 的调用重新初始化浮点程序包。

- 不要使用任何重叠例程。

如果某个程序要使用函数捕获 `SIGFPE` 异常，该程序必须包含浮点代码。 如果您的程序没有浮点代码并且需要运行库的信号处理代码，则只需声明一个可变双精度值并将其初始化为零：

`volatile double d = 0.0f;`

`SIGILL` 和 `SIGTERM` 信号不会在 Windows 下产生。 包含它们是为了实现 ANSI 兼容。 因此，可以使用 `signal` 为这些信号设置信号处理程序，还可以通过调用 [raise](../../c-runtime-library/reference/raise.md) 显式生成这些信号。

信号设置不会保存在通过调用 `_exec` or `_spawn` 函数生成的生成进程中。 信号设置在新进程中将重置为默认值。

## <a name="requirements"></a>惠?

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`signal`|\<signal.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

以下示例演示如何使用 `signal` 将一些自定义行为添加到 `SIGABRT` 信号。 有关中止行为的其他信息，请参阅 [_set_abort_behavior](../../c-runtime-library/reference/set-abort-behavior.md)。

```C
// crt_signal.c
// compile with: /EHsc /W4
// Use signal to attach a signal handler to the abort routine
#include <stdlib.h>
#include <signal.h>
#include <tchar.h>

void SignalHandler(int signal)
{
    if (signal == SIGABRT) {
        // abort signal handler code
    } else {
        // ...
    }
}

int main()
{
    typedef void (*SignalHandlerPointer)(int);

    SignalHandlerPointer previousHandler;
    previousHandler = signal(SIGABRT, SignalHandler);

    abort();
}
```

```Output
This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)  
[abort](../../c-runtime-library/reference/abort.md)  
[_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)  
[exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)  
[_fpreset](../../c-runtime-library/reference/fpreset.md)  
[_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)  
