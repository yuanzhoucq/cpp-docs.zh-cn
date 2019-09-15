---
title: signal
ms.date: 04/12/2018
api_name:
- signal
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- signal
helpviewer_keywords:
- signal function
ms.openlocfilehash: 04869412272725108911f13857585e650ad20ab9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948105"
---
# <a name="signal"></a>signal

设置中断信号处理。

> [!IMPORTANT]
> 不要使用此方法关闭 Microsoft Store 的应用程序，除非在测试或调试方案中。 根据[Microsoft Store 策略](/legal/windows/agreements/store-policies)，不允许以编程方式或 UI 方式关闭应用商店应用。 有关详细信息，请参阅[UWP 应用生命周期](/windows/uwp/launch-resume/app-lifecycle)。

## <a name="syntax"></a>语法

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>参数

*sig*<br/>
信号值。

*func*<br/>
第二个参数是指向要执行的函数的指针。 第一个参数是信号值，第二个参数是可在第一个参数为 SIGFPE 时使用的子代码。

## <a name="return-value"></a>返回值

**信号**返回与给定信号关联的值的上一个值。 例如，如果*函数*的上一个值为**SIG_IGN**，则返回值也是**SIG_IGN**。 **SIG_ERR**的返回值指示错误;在这种情况下， **errno**设置为**EINVAL**。

有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

使用**信号**功能，进程可以从几种方法中选择一种来处理来自操作系统的中断信号。 *Sig*参数是**信号**响应的中断;它必须是在 "信号" 中定义的以下清单常量之一。高.

|*sig*值|描述|
|-----------------|-----------------|
|**SIGABRT**|异常终止|
|**SIGFPE**|浮点错误|
|**SIGILL**|非法指令|
|**SIGINT**|Ctrl+C 信号|
|**SIGSEGV**|非法存储区访问|
|**SIGTERM**|终止请求|

如果*sig*不是上述值之一，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所定义。 如果允许执行继续，则此函数会将**errno**设置为**EINVAL**并返回**SIG_ERR**。

默认情况下，**信号**使用退出代码3终止调用程序，与*sig*的值无关。

> [!NOTE]
> 任何 Win32 应用程序都不支持**SIGINT** 。 当 Ctrl+C 中断发生时，Win32 操作系统将专门生成新的线程来处理中断。 这可能导致单线程应用程序（如 UNIX 中的此类应用程序）变成多线程应用程序并导致意外行为。

*Func*参数是写入信号处理程序的地址，或者是在信号中定义的预定义常量**SIG_DFL**或**SIG_IGN**之一。高. 如果*func*是一个函数，则该函数将作为给定信号的信号处理程序安装。 信号处理程序的原型需要一个**int**类型的形参（ *sig*）。当发生中断时，操作系统将通过*sig*提供实参：参数是生成中断的信号。 因此，您可以在信号处理程序中使用六个清单常量（在前面的表中列出）来确定发生了哪种中断并采取相应措施。 例如，可以调用**信号**两次，将同一处理程序分配给两个不同的信号，然后测试处理程序中的*sig*参数，以根据收到的信号采取不同的操作。

如果要测试浮点异常（**SIGFPE**），则*func*指向一个函数，该函数采用可选的第二个参数，该参数是在 FLOAT 中定义的多个清单常量中的一个。H，格式为**FPE_xxx**。 出现**SIGFPE**信号时，可以测试第二个参数的值以确定浮点异常的类型，然后采取相应的操作。 此参数及其可能的值是 Microsoft 扩展名。

对于浮点异常，接收信号时不会重置*func*值。 若要从浮点异常恢复，请使用 try/except 子句包围浮点运算。 将[setjmp](setjmp.md) 与 [longjmp](longjmp.md) 一起使用也能恢复。 在任一情况下，调用进程都会继续执行，并保留未定义的进程的浮点状态。

如果信号处理程序返回，调用进程将在收到断点信号后立即继续执行。 无论信号或操作模式的类型如何都是如此。

在执行指定的函数之前， *func*的值将设置为**SIG_DFL**。 下一个中断信号将按对**SIG_DFL**的描述进行处理，除非对**信号**的干预调用另行指定。 您可以使用此功能在所调用的函数中重置信号。

由于信号处理程序例程通常在中断发生时异步调用，当运行时操作不完整且处于未知状态时，您的信号处理程序可能受到控制。 以下列表汇总了一些限制，用来确定您可在信号处理程序例程中使用的函数。

- 不要发出低级别或 STDIO.H。H i/o 例程（例如**printf**或**fread**）。

- 不要调用堆例程或任何使用堆例程的例程（例如， **malloc**、 **_strdup**或 **_putenv**）。 有关详细信息，请参阅 [malloc](malloc.md)。

- 不要使用生成系统调用的任何函数（例如， **_getcwd**或**time**）。

- 不要使用**longjmp** ，除非中断是由浮点异常导致的（即， *sig*为**SIGFPE**）。 在这种情况下，首先使用对 **_fpreset**的调用重新初始化浮点程序包。

- 不要使用任何重叠例程。

如果某个程序要使用函数捕获**SIGFPE**异常，则该程序必须包含浮点代码。 如果您的程序没有浮点代码并且需要运行库的信号处理代码，则只需声明一个可变双精度值并将其初始化为零：

```C
volatile double d = 0.0f;
```

**SIGILL**和**SIGTERM**信号不会在 Windows 下生成。 包含它们是为了实现 ANSI 兼容。 因此，可以通过使用**信号**为这些信号设置信号处理程序，还可以通过调用[raise](raise.md)显式生成这些信号。

信号设置不会保留在通过调用[_exec](../../c-runtime-library/exec-wexec-functions.md)或[_spawn](../../c-runtime-library/spawn-wspawn-functions.md)函数创建的生成进程中。 信号设置在新进程中将重置为默认值。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**signal**|\<signal.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

下面的示例演示如何使用**信号**将一些自定义行为添加到**SIGABRT**信号。 有关中止行为的其他信息，请参阅 [_set_abort_behavior](set-abort-behavior.md)。

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

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_fpreset](fpreset.md)<br/>
[_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
