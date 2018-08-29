---
title: 线程控制的 C 运行时库函数 |Microsoft Docs
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
ms.openlocfilehash: 2eaa1a0589cb001658b18144e06956eebd302287
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131849"
---
# <a name="c-run-time-library-functions-for-thread-control"></a>线程控制的 C 运行库函数
所有 Win32 程序都具有至少一个线程。 任何线程都可以创建其他线程。 一个线程可以快速完成其工作，然后终止; 或它可以将保持活动状态的程序的生命周期。  
  
LIBCMT 和 msvcrt 系统 C 运行时库提供用于线程创建和终止的以下功能： [_beginthread、 _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)并[_endthread、 _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)。  
  
`_beginthread`和`_beginthreadex`函数创建一个新线程，并返回线程标识符，如果操作成功。 该线程会自动终止它完成执行，则它可以通过调用终止自身`_endthread`或`_endthreadex`。  
  
> [!NOTE]
> 如果要从使用 Libcmt.lib 构建的程序调用 C 运行时例程，则必须启动与您的线程`_beginthread`或`_beginthreadex`函数。 不使用 Win32 函数`ExitThread`和`CreateThread`。 使用`SuspendThread`可能会导致死锁时多个线程被阻塞，等待挂起的线程以完成对 C 运行时数据结构的访问权限。  
  
##  <a name="_core_the__beginthread_function"></a> _Beginthread 和 _beginthreadex 函数  
 
`_beginthread`和`_beginthreadex`函数创建一个新线程。 线程与进程中的其他线程共享进程的代码和数据段，但有其自己唯一的寄存器值、 堆栈空间和当前指令地址。 系统向每个线程，提供 CPU 时间，使进程中的所有线程可并发都执行。  
  
`_beginthread` 并`_beginthreadex`类似于[CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) Win32 API 中的函数，但具有这些差异：  
  
- 它们初始化某些 C 运行时库变量。 这一点只有在您的线程中使用 C 运行时库。  
  
- `CreateThread` 帮助提供对安全属性的控制。 此函数可用于启动线程处于挂起状态。  
  
 `_beginthread` 和`_beginthreadex`返回的句柄到新的线程如果成功或错误代码，如果出现错误。  
  
##  <a name="_core_the__endthread_function"></a> _Endthread 和 _endthreadex 函数  
 
[_Endthread](../c-runtime-library/reference/endthread-endthreadex.md)函数将终止创建的线程`_beginthread`(同样，`_endthreadex`终止创建的线程`_beginthreadex`)。 在完成时，自动终止线程。 `_endthread` 和`_endthreadex`可用于从线程内的条件性终止。 一个线程专门用于通讯处理，例如，可以退出如果无法控制的通信端口。  
  
## <a name="see-also"></a>请参阅  
 
[使用 C 和 Win32 进行多线程编程](multithreading-with-c-and-win32.md)