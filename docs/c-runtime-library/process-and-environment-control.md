---
title: "进程和环境控制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.programs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "环境控制例程"
  - "父进程"
  - "过程控制例程"
  - "进程, 管理任务"
  - "进程, 启动"
  - "进程, stopping"
ms.assetid: 7fde74c3-c2a6-4d15-84b8-092160d60c3e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 进程和环境控制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用进程控制程序启动，停止和管理程序内部的进程。  使用环境控件程序获取和更改有关操作系统环境的信息。  
  
### 进程和环境控制函数  
  
|例程|使用|.NET Framework 等效项|  
|--------|--------|------------------------|  
|[abort](../c-runtime-library/reference/abort.md)|终止进程没有刷新缓冲区或调用被 `atexit` 和 `_onexit`注册的函数|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md)|逻辑错误的测试|[\<caps:sentence id\="tgt14" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[\_ASSERT, \_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 宏|与 `assert`类似，但是只在运行库的调试版本中可用|[\<caps:sentence id\="tgt17" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[atexit](../c-runtime-library/reference/atexit.md)|在程序结束执行的计划程序。|[\<caps:sentence id\="tgt20" sentenceid\="db022fa9aa2a12937c3610e3eb32e80f" class\="tgtSentence"\>System::Diagnostics::Process::Exited\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.exited.aspx)|  
|[\_beginthread、\_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)|在 Windows 操作系统进程上创建新线程|[\<caps:sentence id\="tgt23" sentenceid\="221e38ecc6535bce91af4e1a19f464d1" class\="tgtSentence"\>System::Threading::Thread::Start\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.threading.thread.start.aspx)|  
|[退出 。](../c-runtime-library/reference/cexit-c-exit.md)|执行 `exit` 终止程序 \(例如刷新缓冲区\)，然后返回控件去调用程序，没有终止进程。|[\<caps:sentence id\="tgt26" sentenceid\="46302f19d05c09c5875a795cb64800f9" class\="tgtSentence"\>System::Diagnostics::Process 类\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.closemainwindow.aspx)|  
|[\- 退出...](../c-runtime-library/reference/cexit-c-exit.md)|执行 `_exit` 终止程序，然后在没有结束进程的情况下返回控件去给调用程序。|[\<caps:sentence id\="tgt29" sentenceid\="46302f19d05c09c5875a795cb64800f9" class\="tgtSentence"\>System::Diagnostics::Process 类\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.closemainwindow.aspx)|  
|[\_cwait](../c-runtime-library/reference/cwait.md)|等待直到另一个进程停止。|[\<caps:sentence id\="tgt32" sentenceid\="d9c88c429eaacaa9f37d91d29bc6504e" class\="tgtSentence"\>System::Diagnostics::Process::WaitForExit\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.waitforexit.aspx)|  
|[\_endthread、\_endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)|终止Windows 操作系统线程|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_execl、\_wexecl](../c-runtime-library/reference/execl-wexecl.md)|利用自变量列表执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execle、\_wexecle](../c-runtime-library/reference/execle-wexecle.md)|以自变量列表和给定环境执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execlp、\_wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|使用 `PATH` 变量和参数列表，执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execlpe、\_wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|使用 `PATH` 变量，给定的环境和参数列表执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execv、\_wexecv](../c-runtime-library/reference/execv-wexecv.md)|利用自变量数组执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execve、\_wexecve](../c-runtime-library/reference/execve-wexecve.md)|以自变量数组和给定环境执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execvp、\_wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|使用 `PATH` 变量和参数数组，执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execvpe、\_wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|使用 `PATH` 变量，给定的环境和参数数组执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[exit](../c-runtime-library/reference/exit-exit-exit.md)|调用由 `atexit` 和 `_onexit` 注册的函数，刷新所有缓冲区，请关闭所有开启文件，并且终止进程|[\<caps:sentence id\="tgt64" sentenceid\="811a70e90f150f212690505b37a46c0f" class\="tgtSentence"\>System::Diagnostics::Process::Kill\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.kill.aspx)|  
|[退出](../c-runtime-library/reference/exit-exit-exit.md)|立即终止进程，不调用 `atexit` 或 `_onexit` 或刷新缓冲区|[\<caps:sentence id\="tgt67" sentenceid\="811a70e90f150f212690505b37a46c0f" class\="tgtSentence"\>System::Diagnostics::Process::Kill\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.kill.aspx)|  
|[getenv, \_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md), [getenv\_s、\_wgetenv\_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|获取环境变量的值|[\<caps:sentence id\="tgt70" sentenceid\="795988b9277d74ea3b722ecd42dcb29d" class\="tgtSentence"\>System::Environment::GetEnvironmentVariable\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.environment.getenvironmentvariable.aspx)|  
|[\_getpid](../c-runtime-library/reference/getpid.md)|获得进程 ID 号|[\<caps:sentence id\="tgt73" sentenceid\="745b82c461dc74b15540e9622f7cd7bd" class\="tgtSentence"\>System::Diagnostics::Process::Id\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.id.aspx)|  
|[longjmp](../c-runtime-library/reference/longjmp.md)|还原堆栈保存环境；使用它来执行非本地 `goto`|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_onexit](../c-runtime-library/reference/onexit-onexit-m.md)|在程序终止时执行的计划程序；使用和 Microsoft C\/C\+\+ 兼容的版本7.0 和更早的版本|[\<caps:sentence id\="tgt81" sentenceid\="db022fa9aa2a12937c3610e3eb32e80f" class\="tgtSentence"\>System::Diagnostics::Process::Exited\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.exited.aspx)|  
|[\_pclose](../c-runtime-library/reference/pclose.md)|等待新的命令处理器并关闭在相关管道的流|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[perror、\_wperror](../c-runtime-library/reference/perror-wperror.md)|打印错误消息。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_pipe](../c-runtime-library/reference/pipe.md)|创建一个读写操作的管道。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_popen、\_wpopen](../c-runtime-library/reference/popen-wpopen.md)|创建管道并执行命令|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_putenv, \_wputenv](../c-runtime-library/reference/putenv-wputenv.md), [\_putenv\_s、\_wputenv\_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)|添加或更改环境变量的值|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[raise](../c-runtime-library/reference/raise.md)|发送信号调用进程|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[setjmp](../c-runtime-library/reference/setjmp.md)|保存堆栈环境；使用执行非本地 `goto`|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[signal](../c-runtime-library/reference/signal.md)|处理中断信号|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_spawnl、\_wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|用指定的参数列表创建并执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnle、\_wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|用指定的参数列表和环境创建并执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnlp、\_wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|使用 `PATH` 变量和指定的参数列表，创建并执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnlpe、\_wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|使用 `PATH` 变量,指定的环境和参数列表，创建并执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnv、\_wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|用指定的参数数组创建并执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnve、\_wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|用指定的参数数组和环境创建并执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnvp、\_wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|使用 `PATH` 变量和指定的参数数组，创建并执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnvpe、\_wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|使用 `PATH` 变量,指定的环境和参数数组，创建并执行新的进程|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[system、\_wsystem](../c-runtime-library/reference/system-wsystem.md)|执行操作系统命令|[System::Diagnostics::Process 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)，[System::Diagnostics::ProcessStartInfo 类](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)|  
  
 在 Windows 操作系统中，已经产生的进程与正在产生的进程等效。  所有进程可以使用`_cwait` 等待已知进程ID的任何其他进程。  
  
 `_exec` 和与`_spawn` 系列之间的差别在于 `_spawn` 函数可以从新的进程返回控件去调用进程。  在 `_spawn` 函数中，除非 `_P_OVERLAY` 指定，则调用进程和新的进程都存在内存中。  在 `_exec` 函数中，新的进程覆盖调用的进程，因此，控件不能返回到调用进程，除非错误发在尝试启动执行新的进程。  
  
 区别在 `_exec` 系列中的函数，以及那些在 `_spawn` 系列中，涉及定位文件的方法作为新的进程被执行，窗体中的参数传递给新的进程，设置环境的方法如下表所示。  使用传递参数列表的函数，当参数的数目是常量或在编译时已知时。  使用传递指向包含参数数组的一个函数，当参数的数目在运行是被确定。  下表中的信息也适用于 `_spawn` 和 `_exec` 函数的宽字符副本。  
  
### \_spawn 和\_exec 函数族  
  
|函数|使用路径变量查找文件|参数传递约定|环境设置|  
|--------|----------------|------------|----------|  
|`_execl, _spawnl`|否|List|从调用进程中继承|  
|`_execle, _spawnle`|否|List|新进程指向环境表格的指针作为最后的参数传递|  
|`_execlp, _spawnlp`|是|List|从调用进程中继承|  
|`_execlpe, _spawnlpe`|是|List|新进程指向环境表格的指针作为最后的参数传递|  
|`_execv, _spawnv`|否|数组|从调用进程中继承|  
|`_execve, _spawnve`|否|数组|新进程指向环境表格的指针作为最后的参数传递|  
|`_execvp, _spawnvp`|是|数组|从调用进程中继承|  
|`_execvpe, _spawnvpe`|是|数组|新进程指向环境表格的指针作为最后的参数传递|  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)