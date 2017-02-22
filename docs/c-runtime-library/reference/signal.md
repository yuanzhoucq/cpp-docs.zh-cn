---
title: "signal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "signal"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "signal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "signal 函数"
ms.assetid: 094118de-d789-4063-b4f4-cffcc80bf29d
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# signal
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置中断信号处理。  
  
> [!IMPORTANT]
>  不要使用此方法关闭 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序，除非在测试或调试方案中。  根据 [的3.6节Windows 8 应用程序证书要求](http://go.microsoft.com/fwlink/?LinkId=262889)，禁止以编程或 UI 方式关闭 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序。  有关详情，请参阅[应用程序生命周期（Windows 应用商店应用）](http://go.microsoft.com/fwlink/?LinkId=262853)。  
  
## 语法  
  
```  
void (__cdecl *signal(  
   int sig,   
   void (__cdecl *func ) (int [, int ] )))   
   (int);  
```  
  
#### 参数  
 `sig`  
 信号值。  
  
 `func`  
 要执行的函数。  第一个参数是信号值，第二个参数是子码，可以在第一个参数是 SIGFPE 时使用。  
  
## 返回值  
 `signal` 返回与给定信号联系的 `func` 以前的值。  例如，因此，如果 `func` 以前的值是 `SIG_IGN`，返回值也是 `SIG_IGN`。  返回值 `SIG_ERR` 表示错误，在此情况下将设置`errno`为`EINVAL`。  
  
 请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)查找有关返回代码的详细信息。  
  
## 备注  
 `signal` 函数激活一个从多种方式中选择一个来处理来自操作系统的中断信号的进程。  `sig` 参数是 `signal` 响应的中断；它必须是下列在 SIGNAL.H. 定义下的清单常数之一，。  
  
|`sig` 值|描述|  
|-------------|--------|  
|`SIGABRT`|Abnormal termination|  
|`SIGFPE`|浮点错误|  
|`SIGILL`|非法指令|  
|`SIGINT`|CTRL\+C 信号|  
|`SIGSEGV`|非法存储区访问|  
|`SIGTERM`|停止请求|  
  
 如果 `sig` 不是以上值其中的一个，调用无效参数处理程序，在 [参数验证](../../c-runtime-library/parameter-validation.md) 定义中。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回 `SIG_ERR`。  
  
 默认情况下，无论 `sig` 的值, `signal` 停止并以退出代码 3调用程序。  
  
> [!NOTE]
>  `SIGINT` 不被任何 Win32 应用程序支持。  当 CTRL\+C 中断发生时，Win32 操作系统专门生成新的线程来处理中断。  这可能导致单线程应用程序，例如在NUIX中，将多线程和导致意外行为。  
  
 `func` 自变量是一个您写的信号的地址，或者是预定义常量 `SIG_DFL` 或 `SIG_IGN` 中的一个，在 SIGNALH 中定义的。  如果 `func` 是函数，则会安装为特定的信号通知处理程序。  该信号处理程序的原型需要一个形式参数，`sig`，`int` 类型。  发生中断时，操作系统通过 `sig` 提供实参；这个参数是产生中断的信号。  因此，则在你的信号处理程序中可以使用六个清单常数 \(在前面表中列出\) 来确定发生了什么中断并采取适当的操作。  例如，可以调用 `signal` 两次来分配相同的处理程序添加到两个不同的信号，然后测试在处理程序 `sig` 中的参数是基于不同信号产生不同操作。  
  
 如果为浮点异常 \(`SIGFPE`\) 测试，`func` 指向一个函数，这个函数采用可选的第二个参数是\-定义在 FLOAT.H \-窗体 `FPE_xxx` 的清单常量之一。  当 `SIGFPE` 信号发生时，可以测试第二个参数的值判断浮点异常类型然后执行适当的操作。  此参数及其可能的值是 Microsoft 扩展名。  
  
 对于浮点异常，当接收到信号时，`func` 的值，不会被重置。  想要从浮点异常回复，使用try\/except子句包围浮点运算。  通过使用 [setjmp](../../c-runtime-library/reference/setjmp.md) 与 [longjmp](../../c-runtime-library/reference/longjmp.md)恢复也是可能的。  另一种情况，调用进程继续执行，并且处理为定义进程的浮点状态。  
  
 如果信号处理返回，调用进程直接从接受断点信号的点继续执行。  这是真实的，无论是哪种信号或操作模式的类型。  
  
 在指定的函数被执行前，`func` 的值设置为 `SIG_DFL`。  下中断信号被作为用于描述 `SIG_DFL`，除非中间调用 `signal` 的除外。  你可以使用特殊的功能在被调用函数中重置信号。  
  
 因为信号处理程序例程通在中断发生时常被称为异步，你的信号能会得到控制时，运行时操作并不完整，并处于未知状态。  以下列表总结了确定的限制哪些功能在您的信号处理程序实例来使用。  
  
-   不要发出低级别或 STDIO.H I\/O 实例 \(例如，`printf` 或 `fread`\)。  
  
-   不要调用堆实例或使用堆实例的实例 \(，`malloc`、`_strdup`或 `_putenv`\)。  有关更多信息，请参见[malloc](../../c-runtime-library/reference/malloc.md)。  
  
-   不要使用任何生成系统调用的函数 \(例如，`_getcwd` 或 `time`\)。  
  
-   不要使用 `longjmp`，除非该中断由一个浮点异常导致的 \(即 `sig` 是 `SIGFPE`\)。  在这种情况下，首先通过调用`_fpreset`来重新初始化浮点程序包。  
  
-   不要使用任何复盖实例。  
  
 如果它是通过使用此函数,捕获 `SIGFPE` 异常，程序必须包含浮点代码。  如果程序不具有浮点代码并且不需要运行库的信号处理代码，请声明变量二进制文件并将其初始化为零：  
  
```  
volatile double d = 0.0f;   
```  
  
 `SIGILL` 和 `SIGTERM` 信号不会在 Windows 下产生。  它们包括了ANSI相容性。  因此，可以使用 `signal`设置这些信号的信号处理程序，并且您也可以通过调用 [raise](../../c-runtime-library/reference/raise.md)显式还生成这些信号。  
  
 信号设置不保存在通过调用`_exec` or `_spawn` 函数生成的进程。  信号设置在新的进程中被重置为中的默认值。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`signal`|\<signal.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 下面的示例演示如何使用 `signal` 添加一些自定义到 `SIGABRT` 信号。  有关中止行为的更多信息，请参见 [\_set\_abort\_behavior](../../c-runtime-library/reference/set-abort-behavior.md)。  
  
```cpp  
// crt_signal.c  
// compile with: /EHsc /W4  
// Use signal to attach a signal handler to the abort routine  
#include <stdlib.h>  
#include <signal.h>  
#include <tchar.h>  
  
void SignalHandler(int signal)  
{  
    if (signal == SIGABRT) {  
        // abort signal handler code  
    } else {  
        // ...  
    }  
}  
  
int main()  
{  
    typedef void (*SignalHandlerPointer)(int);  
  
    SignalHandlerPointer previousHandler;  
    previousHandler = signal(SIGABRT, SignalHandler);  
  
    abort();  
}  
  
```  
  
  **此应用程序已请求运行时以异常方式终止它。**  
**请与应用程序技术支持团队联系，以便获得更多信息。**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [\_exec、\_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_fpreset](../../c-runtime-library/reference/fpreset.md)   
 [\_spawn, \_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)