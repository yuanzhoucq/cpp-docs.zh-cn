---
title: "abort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "abort"
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
  - "Abort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "abort 函数"
  - "中止当前进程"
  - "进程, 正在中止"
ms.assetid: a797783b-40ed-4bdb-a2cd-14ffede39e8a
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# abort
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

中止当前进程并返回错误代码。  
  
> [!NOTE]
>  不要使用此方法关闭 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序，除非在测试或调试方案中。  根据 [Windows 8 应用程序证书要求](http://go.microsoft.com/fwlink/?LinkId=262889)，禁止以编程或 UI 方式关闭 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序。  有关详情，请参阅[应用程序生命周期（Windows 应用商店应用）](http://go.microsoft.com/fwlink/?LinkId=262853)。  
  
## 语法  
  
```  
void abort( void );  
```  
  
## 返回值  
 `abort` 并不向调用进程返回控件。  默认情况下，它会检查是否有中止信号处理程序，如果设置了，它就会引发 `SIGABRT`。  然后，`abort` 终止当前进程并将退出代码返回到父进程。  
  
## 备注  
 **Microsoft 专用**  
  
 默认情况下，当使用调试运行时库生成应用程序时，`abort` 例程会在引发 `SIGABRT` 前显示错误消息。  对于在控制台模式中运行的控制台应用程序，该消息将发送到 `STDERR`。  窗口模式下运行的 Windows 桌面应用程序和控制台在消息框中显示消息。  若要取消消息，请使用 [\_set\_abort\_behavior](../../c-runtime-library/reference/set-abort-behavior.md) 清除 `_WRITE_ABORT_MSG` 标志。  显示的消息取决于运行时使用的环境版本。  对于使用 Visual C\+\+ 的最新版本而生成的应用程序，消息类似于：  
  
 `R6010`  
  
 `- abort() has been called`  
  
 在 C 运行库的早期版本中，此消息显示为：  
  
 “`This application has requested the Runtime to terminate it in an unusual way. Please contact the application's support team for more information.`”  
  
 在调试模式下编译程序时，消息框显示“中止”、“重试”或“忽略”选项。  如果用户选择“中止”，程序会立即停止并返回为 3 的退出代码。  如果用户选择“重试”，将调用调试器进行实时调试（如果可用）。  如果用户选择“忽略”，`abort` 将继续正常进程。  
  
 在发布和调试版本中，`abort` 将检查是否已设置中止信号处理程序。  如果设置了非默认的通知处理程序，`abort` 将调用 `raise(SIGABRT)`。  使用[信号](../../c-runtime-library/reference/signal.md)功能可关联中止信号处理函数与 `SIGABRT` 信号。  您可执行自定义操作（例如，清理资源或记录信息），并在处理函数中用您自己的错误代码终止应用程序。  如果未定义自定义信号处理程序，`abort` 则不会引发 `SIGABRT` 信号。  
  
 默认情况下，在桌面或控制台应用程序的飞调试生成中，`abort` 然后调用 Windows 错误报告机制 \(Dr。  Watson\) 向 Microsoft 报告失败。  此行为可通过调用 `_set_abort_behavior` 和设置或者屏蔽 `_CALL_REPORTFAULT` 标志启用或禁用。  设置标志后，Windows 显示一个带有诸如“出现问题导致程序停止正常工作”的文本的消息框。用户可以选择“调用”按钮来调用一个调试器，或者选择“关闭程序”按钮停止具有操作系统定义为错误代码的应用程序。  
  
 如果未调用 Windows 错误报告处理程序，则 `abort` 将调用 [\_exit](../../c-runtime-library/reference/exit-exit-exit.md) 以终止进程（显示退出代码 3），并将控件返回到父进程或操作系统中。  `_exit` 不刷新流缓冲区也不执行 `atexit`\/`_onexit` 处理。  
  
 有关 CRT 调试的更多信息，请参阅 [CRT 调试方法](../Topic/CRT%20Debugging%20Techniques.md)。  
  
 **结束 Microsoft 专用**  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`abort`|\<process.h\> 或 \<stdlib.h\>|  
  
## 示例  
 如果尝试失败，以下程序尝试打开文件并中止。  
  
```c  
// crt_abort.c  
// compile with: /TC  
// This program demonstrates the use of  
// the abort function by attempting to open a file  
// and aborts if the attempt fails.  
  
#include  <stdio.h>  
#include  <stdlib.h>  
  
int main( void )  
{  
    FILE    *stream = NULL;  
    errno_t err = 0;  
  
    err = fopen_s(&stream, "NOSUCHF.ILE", "r" );  
    if ((err != 0) || (stream == NULL))  
    {  
        perror( "File could not be opened" );  
        abort();  
    }  
    else  
    {  
        fclose( stream );  
    }  
}  
```  
  
  **无法打开文件：该文件或目录不存在**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅 [平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [使用 abort](../../cpp/using-abort.md)   
 [abort 函数](../../c-language/abort-function-c.md)   
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_exec、\_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [raise](../../c-runtime-library/reference/raise.md)   
 [signal](../../c-runtime-library/reference/signal.md)   
 [\_spawn, \_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)   
 [\_DEBUG](../../c-runtime-library/debug.md)   
 [\_set\_abort\_behavior](../../c-runtime-library/reference/set-abort-behavior.md)