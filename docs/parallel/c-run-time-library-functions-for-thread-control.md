---
title: C 运行时库函数线程控制的 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _beginthread function
- _endthread function
- threading [C++], controlling threads
- multithreading [C++], controlling threads
- _beginthreadex function
- _endthreadex function
ms.assetid: 39d0529c-c392-4c6f-94f5-105d1e8054e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a505bae156edba6798812b807d7ab5c6ea9e396
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="c-run-time-library-functions-for-thread-control"></a>线程控制的 C 运行库函数
所有 Win32 程序都具有至少一个线程。 任何线程可以创建其他线程。 线程可以快速完成其工作，然后终止，或它可以将保持活动状态的生存期内程序。  
  
 LIBCMT 和 MSVCRT C 运行时库的线程创建和终止提供以下函数： [_beginthread、 _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)和[_endthread、 _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)。  
  
 `_beginthread`和`_beginthreadex`函数创建新线程，如果操作成功返回线程标识符。 如果它完成时执行，或者它可以通过调用终止本身线程自动终止`_endthread`或`_endthreadex`。  
  
> [!NOTE]
>  如果想要从生成与 Libcmt.lib 程序中调用 C 运行时例程，则必须启动与线程`_beginthread`或`_beginthreadex`函数。 不要使用 Win32 函数`ExitThread`和`CreateThread`。 使用`SuspendThread`多个线程被阻止等待挂起的线程以完成其访问权限的 C 运行时数据结构时可能会导致死锁。  
  
##  <a name="_core_the__beginthread_function"></a> _Beginthread 和 _beginthreadex 函数  
 `_beginthread`和`_beginthreadex`函数用来创建新线程。 线程与其他进程中的线程共享一个进程的代码和数据段，但有其自己的唯一寄存器值、 堆栈空间和当前的指令地址。 系统，CPU 时间向每个线程，以便可以并发执行的过程中的所有线程。  
  
 `_beginthread` 和`_beginthreadex`类似于[CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) Win32 API 中的函数，但是具有这些差异：  
  
-   它们将初始化某些 C 运行时库变量。 这是重要只有当在线程中使用 C 运行时库。  
  
-   `CreateThread` 有助于提供控制的安全属性。 此函数可用于启动处于挂起状态的线程。  
  
 `_beginthread` 和`_beginthreadex`返回的句柄到新线程如果成功或错误代码，如果时出错。  
  
##  <a name="_core_the__endthread_function"></a> _Endthread 和 _endthreadex 函数  
 [_Endthread](../c-runtime-library/reference/endthread-endthreadex.md)函数将终止创建的线程`_beginthread`(同样，`_endthreadex`终止创建的线程`_beginthreadex`)。 在完成时，自动终止线程。 `_endthread` 和`_endthreadex`可用于从一个线程内的条件终止。 例如，线程专用于通信处理，可以退出如果无法获取通信端口的控制。  
  
## <a name="see-also"></a>请参阅  
 [使用 C 和 Win32 进行多线程编程](../parallel/multithreading-with-c-and-win32.md)