---
title: "线程控制的 C 运行库函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_beginthread 函数"
  - "_beginthreadex 函数"
  - "_endthread 函数"
  - "_endthreadex 函数"
  - "多线程处理 [C++], 控制线程"
  - "线程处理 [C++], 控制线程"
ms.assetid: 39d0529c-c392-4c6f-94f5-105d1e8054e4
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 线程控制的 C 运行库函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

所有 Win32 程序都至少有一个线程。  任何线程都可以创建附加线程。  线程可以快速完成其工作，然后终止；也可以在程序的生存期内保持活动状态。  
  
 LIBCMT 和 MSVCRT C 运行库提供以下用于创建和终止线程的函数：[\_beginthread、\_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) 和 [\_endthread、\_endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)。  
  
 `_beginthread` 和 `_beginthreadex` 函数创建新线程；如果操作成功，则返回线程标识符。  线程完成执行时自动终止，或者可通过调用 `_endthread` 或 `_endthreadex` 自行终止。  
  
> [!NOTE]
>  如果要从使用 Libcmt.lib 生成的程序调用 C 运行时例程，则必须使用 `_beginthread` 或 `_beginthreadex` 函数启动线程。  不要使用 Win32 函数 `ExitThread` 和 `CreateThread`。  如果有一个以上的线程在等待挂起的线程完成它对 C 运行时数据结构的访问时被阻塞，使用 `SuspendThread` 会导致死锁。  
  
##  <a name="_core_the__beginthread_function"></a> \_beginthread 和 \_beginthreadex 函数  
 `_beginthread` 和 `_beginthreadex` 函数用来创建新线程。  线程与进程中的其他线程共享进程的代码和数据段，但是线程具有自己的唯一寄存器值、堆栈空间和当前指令地址。  系统给予每个线程 CPU 时间，使进程中的所有线程都可以同时执行。  
  
 `_beginthread` 和 `_beginthreadex` 与 Win32 API 中的 [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) 函数类似，但有如下差异：  
  
-   它们初始化某些 C 运行库变量。  只有在线程中使用 C 运行库时，这一点才很重要。  
  
-   `CreateThread` 帮助提供对安全特性的控制。  可以使用此函数启动处于挂起状态的线程。  
  
 如果成功的话，`_beginthread` 和 `_beginthreadex` 返回新线程的句柄；如果有错误的话，则返回错误代码。  
  
##  <a name="_core_the__endthread_function"></a> \_endthread 和 \_endthreadex 函数  
 [\_endthread](../c-runtime-library/reference/endthread-endthreadex.md) 函数终止由 `_beginthread` 创建的线程（同样，`_endthreadex` 终止由 `_beginthreadex` 创建的线程）。  线程会在完成时自动终止。  `_endthread` 和 `_endthreadex` 用于从线程内部进行条件终止。  例如，专门用于通信处理的线程若无法获取对通信端口的控制，则会退出。  
  
## 请参阅  
 [使用 C 和 Win32 进行多线程编程](../parallel/multithreading-with-c-and-win32.md)