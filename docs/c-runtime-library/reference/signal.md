---
title: "signal | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: 094118de-d789-4063-b4f4-cffcc80bf29d
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 1f05c16dff5bd490866a58fcd36ae28cba862fdd
ms.lasthandoff: 02/24/2017

---
# <a name="signal"></a>signal
设置中断信号处理。  
  
> [!IMPORTANT]
>  不要使用此方法关闭 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序，除非在测试或调试方案中。 根据 [Windows 8 应用认证要求](http://go.microsoft.com/fwlink/?LinkId=262889)中第 3.6 节的说明，禁止以编程或 UI 方式关闭 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用。 有关详细信息，请参阅[应用程序生命周期（Windows 应用商店应用）](http://go.microsoft.com/fwlink/?LinkId=262853)。  
  
## <a name="syntax"></a>语法  
  
```  
void (__cdecl *signal(  
   int sig,   
   void (__cdecl *func ) (int [, int ] )))   
   (int);  
```  
  
#### <a name="parameters"></a>参数  
 `sig`  
 信号值。  
  
 `func`  
 要执行的函数。 第一个参数是信号值，第二个参数是可在第一个参数为 SIGFPE 时使用的子代码。  
  
## <a name="return-value"></a>返回值  
 `signal` 返回与给定信号关联的 `func` 的上一个值。 例如，如果 `func` 的上一个值是 `SIG_IGN`，则返回值也是 `SIG_IGN`。 `SIG_ERR` 的返回值表示错误；在这种情况下，`errno` 将设置为 `EINVAL`。  
  
 有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 利用 `signal` 函数，进程可以从几种方法中选择一种来处理来自操作系统的中断信号。 `sig` 参数是 `signal` 响应的中断；它必须是在 SIGNAL.H. 中定义的以下清单常量之一。  
  
|`sig` 值|说明|  
|-----------------|-----------------|  
|`SIGABRT`|异常终止|  
|`SIGFPE`|浮点错误|  
|`SIGILL`|非法指令|  
|`SIGINT`|Ctrl+C 信号|  
|`SIGSEGV`|非法存储区访问|  
|`SIGTERM`|终止请求|  
  
 如果 `sig` 不是上述值之一，则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所定义。 如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 `SIG_ERR`。  
  
 默认情况下，无论 `signal` 的值如何，`sig` 都将终止调用程序并显示退出代码 3。  
  
> [!NOTE]
> 任何 Win32 应用程序都不支持  `SIGINT`。 当 Ctrl+C 中断发生时，Win32 操作系统将专门生成新的线程来处理中断。 这可能导致单线程应用程序（如 UNIX 中的此类应用程序）变成多线程应用程序并导致意外行为。  
  
 `func` 参数是您编写的信号处理程序的地址，或者预定义常量 `SIG_DFL` 或 `SIG_IGN` 之一（也在 SIGNAL.H 中定义）的地址。 如果 `func` 是函数，则它会作为给定信号的信号处理程序安装。 该信号处理程序的原型需要一个 `sig` 类型的形参 `int`。 当发生中断时，操作系统将通过 `sig` 提供实参；此参数是生成中断的信号。 因此，您可以在信号处理程序中使用六个清单常量（在前面的表中列出）来确定发生了哪种中断并采取相应措施。 例如，您可以调用 `signal` 两次来将同一处理程序分配给两个不同的信号，然后测试处理程序中的 `sig` 参数以基于收到的信号采取不同的措施。  
  
 如果要测试浮点异常 (`SIGFPE`)，`func` 将指向采用可选的第二个参数的函数，此参数是在 FLOAT.H 中定义的采用 `FPE_xxx` 形式的几个清单常量之一。 当 `SIGFPE` 信号发生时，您可以测试第二个参数的值以确定浮点异常的类型，然后采取相应措施。 此参数及其可能的值是 Microsoft 扩展名。  
  
 对于浮点异常，在接收到信号时不会重置 `func` 的值。 若要从浮点异常恢复，请使用 try/except 子句包围浮点运算。 将[setjmp](../../c-runtime-library/reference/setjmp.md) 与 [longjmp](../../c-runtime-library/reference/longjmp.md) 一起使用也能恢复。 在任一情况下，调用进程都会继续执行，并保留未定义的进程的浮点状态。  
  
 如果信号处理程序返回，调用进程将在收到断点信号后立即继续执行。 无论信号或操作模式的类型如何都是如此。  
  
 在执行指定的函数前，`func` 的值将设置为 `SIG_DFL`。 下一个中断信号将按照为 `SIG_DFL` 描述的方法处理，除非对 `signal` 的干预调用另行指定。 您可以使用此功能在所调用的函数中重置信号。  
  
 由于信号处理程序例程通常在中断发生时异步调用，当运行时操作不完整且处于未知状态时，您的信号处理程序可能受到控制。 以下列表汇总了一些限制，用来确定您可在信号处理程序例程中使用的函数。  
  
-   不要发出低级别或 STDIO.H I/O 例程（例如，`printf` 或 `fread`）。  
  
-   不要调用堆例程或任何使用堆例程的例程（例如，`malloc`、`_strdup` 或 `_putenv`）。 有关详细信息，请参阅 [malloc](../../c-runtime-library/reference/malloc.md)。  
  
-   不要使用生成系统调用的任何函数（例如，`_getcwd` 或 `time`）。  
  
-   不要使用 `longjmp`，除非中断是由浮点异常导致的（即，`sig` 是 `SIGFPE`）。 在这种情况下，首先应使用对 `_fpreset` 的调用重新初始化浮点程序包。  
  
-   不要使用任何重叠例程。  
  
 如果某个程序要使用函数捕获 `SIGFPE` 异常，该程序必须包含浮点代码。 如果您的程序没有浮点代码并且需要运行库的信号处理代码，则只需声明一个可变双精度值并将其初始化为零：  
  
`volatile double d = 0.0f;`  
  
 `SIGILL` 和 `SIGTERM` 信号不会在 Windows 下产生。 包含它们是为了实现 ANSI 兼容。 因此，可以使用 `signal` 为这些信号设置信号处理程序，还可以通过调用 [raise](../../c-runtime-library/reference/raise.md) 显式生成这些信号。  
  
 信号设置不会保存在通过调用 `_exec` or `_spawn` 函数生成的生成进程中。 信号设置在新进程中将重置为默认值。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`signal`|\<signal.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 以下示例演示如何使用 `signal` 将一些自定义行为添加到 `SIGABRT` 信号。 有关中止行为的其他信息，请参阅 [_set_abort_behavior](../../c-runtime-library/reference/set-abort-behavior.md)。  
  
```cpp  
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
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_fpreset](../../c-runtime-library/reference/fpreset.md)   
 [_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)
