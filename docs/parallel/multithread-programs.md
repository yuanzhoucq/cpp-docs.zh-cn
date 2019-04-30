---
title: 多线程程序
ms.date: 11/04/2016
helpviewer_keywords:
- threading [C++], about threading
- multithreading [C++], about threads
ms.assetid: 02443596-f7e1-48d0-b3a4-39ee0e54e444
ms.openlocfilehash: fd10893ecd33d39b531b9451dec708ea31c121d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407817"
---
# <a name="multithread-programs"></a>多线程程序

线程实质上是执行的通过计划路径。 它也是 Win32 安排执行的最小单位。 一个线程包含的堆栈，CPU 寄存器和系统计划程序的执行列表中条目的状态。 每个线程共享进程的所有资源。

过程包括一个或多个线程和代码、 数据和在内存中程序的其他资源。 典型的程序资源是打开的文件、 semaphore 以及动态分配的内存。 当系统调度器掌控它的一个线程执行时，程序执行。 计划程序确定应运行哪些线程以及何时运行。 较低优先级的线程可能必须等待较高优先级线程完成其任务。 在多处理器计算机上计划程序可以将单个线程移到不同的处理器，以平衡 CPU 负载。

在进程中的每个线程都独立运行。 除非使其可见，单独执行的线程，并不会意识到的进程中的其他线程。 线程共享公共资源，但是，必须使用信号量或另一种方法的进程间通信协调其工作。 有关同步线程的详细信息，请参阅[编写多线程 Win32 程序](writing-a-multithreaded-win32-program.md)。

## <a name="see-also"></a>请参阅

[使用 C 和 Win32 进行多线程编程](multithreading-with-c-and-win32.md)
