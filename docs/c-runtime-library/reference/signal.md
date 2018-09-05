---
title: signal | Microsoft 文档
ms.custom: ''
ms.date: 04/12/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- signal
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
f1_keywords:
- signal
dev_langs:
- C++
helpviewer_keywords:
- signal function
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f4e349707c22d8c252f56c08ea45fc78609e557
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690623"
---
# <a name="signal"></a>signal

设置中断信号处理。

> [!IMPORTANT]
> 不使用此方法来关闭的情况下的 Microsoft Store 应用，除非在测试或调试方案。 以编程或 UI 方式关闭应用商店应用程序不允许根据[Microsoft Store 策略](/legal/windows/agreements/store-policies)。 有关详细信息，请参阅[UWP 应用程序生命周期](/windows/uwp/launch-resume/app-lifecycle)。

## <a name="syntax"></a>语法

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>参数

*sig*<br/>
信号值。

*func*<br/>
第二个参数是指向要执行的函数。 第一个参数是信号值，第二个参数是可在第一个参数为 SIGFPE 时使用的子代码。

## <a name="return-value"></a>返回值

**信号**返回与给定信号关联的 func 的先前值。 例如，如果以前的值*func*已**SIG_IGN**，返回值也是**SIG_IGN**。 返回值**SIG_ERR**指示错误; 在这种情况下， **errno**设置为**EINVAL**。

有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**信号**函数，进程可以选择以下几种方式来处理来自操作系统的中断信号。 *Sig*自变量是向其中断**信号**响应; 它必须是信号中定义的以下清单常量之一。H.

|*sig*值|描述|
|-----------------|-----------------|
|**SIGABRT**|异常终止|
|**SIGFPE**|浮点错误|
|**SIGILL**|非法指令|
|**SIGINT**|Ctrl+C 信号|
|**SIGSEGV**|非法存储区访问|
|**SIGTERM**|终止请求|

如果*sig*不是上述值，无效参数处理程序会调用，如中所定义[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数可设置**errno**到**EINVAL** ，并返回**SIG_ERR**。

默认情况下**信号**终止调用程序使用退出代码 3，而不考虑的值*sig*。

> [!NOTE]
> **SIGINT**不支持任何 Win32 应用程序。 当 Ctrl+C 中断发生时，Win32 操作系统将专门生成新的线程来处理中断。 这可能导致单线程应用程序（如 UNIX 中的此类应用程序）变成多线程应用程序并导致意外行为。

*Func*自变量是您编写的信号处理程序或到预定义的常量之一的地址**SIG_DFL**或**SIG_IGN**，其中还定义信号中。H. 如果*func*是函数，将其作为给定信号的信号处理程序安装。 信号处理程序的原型需要一个形参*sig*，类型的**int**。操作系统提供了通过实参*sig*发生中断时; 当自变量是生成中断的信号。 因此，您可以在信号处理程序中使用六个清单常量（在前面的表中列出）来确定发生了哪种中断并采取相应措施。 例如，可以调用**信号**两次以将相同的处理程序分配到两个不同的信号，然后测试*sig*采取不同操作的处理程序中的参数根据接收到的信号。

如果要测试的浮点异常 (**SIGFPE**)， *func*指向采用可选的第二个参数的函数是多个浮点型中定义的清单常量之一。H、 窗体**FPE_xxx**。 当**SIGFPE**信号发生时，可以测试以确定浮点异常的类型，然后采取相应的操作的第二个参数的值。 此参数及其可能的值是 Microsoft 扩展名。

有关的值的浮点异常*func*时收到信号，则不重置。 若要从浮点异常恢复，请使用 try/except 子句包围浮点运算。 将[setjmp](setjmp.md) 与 [longjmp](longjmp.md) 一起使用也能恢复。 在任一情况下，调用进程都会继续执行，并保留未定义的进程的浮点状态。

如果信号处理程序返回，调用进程将在收到断点信号后立即继续执行。 无论信号或操作模式的类型如何都是如此。

执行指定的函数前的值*func*设置为**SIG_DFL**。 对于所述，被视为下一个中断信号**SIG_DFL**，除非的干预调用到**信号**另行指定。 您可以使用此功能在所调用的函数中重置信号。

由于信号处理程序例程通常在中断发生时异步调用，当运行时操作不完整且处于未知状态时，您的信号处理程序可能受到控制。 以下列表汇总了一些限制，用来确定您可在信号处理程序例程中使用的函数。

- 发出低级别或 STDIO 执行操作。H I/O 例程 (例如， **printf**或**fread**)。

- 不要调用堆例程或任何使用堆例程 (例如， **malloc**， **_strdup**，或 **_putenv**)。 有关详细信息，请参阅 [malloc](malloc.md)。

- 不要使用生成系统调用任何函数 (例如， **_getcwd**或**时间**)。

- 不要使用**longjmp**除非中断由浮点异常 (即*sig*是**SIGFPE**)。 在这种情况下，通过调用首先重新初始化浮点程序包 **_fpreset**。

- 不要使用任何重叠例程。

程序必须包含浮点代码，如果要捕获**SIGFPE**使用函数的异常。 如果您的程序没有浮点代码并且需要运行库的信号处理代码，则只需声明一个可变双精度值并将其初始化为零：

```C
volatile double d = 0.0f;
```

**SIGILL**并**SIGTERM**信号不会生成在 Windows 下。 包含它们是为了实现 ANSI 兼容。 因此，可以通过设置信号处理程序为这些信号**信号**，你可以通过调用显式生成这些信号[引发](raise.md)。

在通过调用创建的生成进程中不会保留信号设置[_exec](../../c-runtime-library/exec-wexec-functions.md)或[_spawn](../../c-runtime-library/spawn-wspawn-functions.md)函数。 信号设置在新进程中将重置为默认值。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**signal**|\<signal.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

下面的示例演示如何使用**信号**向其添加一些自定义行为**SIGABRT**信号。 有关中止行为的其他信息，请参阅 [_set_abort_behavior](set-abort-behavior.md)。

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
