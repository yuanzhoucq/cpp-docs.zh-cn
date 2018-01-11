---
title: "多线程程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- threading [C++], about threading
- multithreading [C++], about threads
ms.assetid: 02443596-f7e1-48d0-b3a4-39ee0e54e444
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0ff73b4d3a1c8ee6971fbd3f88f491c2a5c76311
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="multithread-programs"></a>多线程程序
基本上，线程是执行通过计划的路径。 它也是 Win32 安排执行的最小单位。 线程包含的堆栈的状态以及 CPU 寄存器中，系统计划程序执行列表中的条目。 每个线程共享进程的所有资源。  
  
 过程包括一个或多个线程和代码、 数据和在内存中程序的其他资源。 典型的程序资源是打开的文件、 信号灯和动态分配的内存。 在系统计划程序使其线程之一执行控制时，将执行程序。 计划程序确定应当运行哪些线程和它们应何时运行。 较低的优先级的线程可能需要等待时更高优先级的线程完成其任务。 在多处理器计算机上计划程序可以将单个线程移到不同的处理器，以平衡 CPU 负载。  
  
 进程中的每个线程都独立运行。 除非您使它们相互可见，线程单独执行，而不会意识到进程中的其他线程。 线程共享公共资源，但是，必须使用信号量或另一种方法的进程间通信协调其工作。 有关同步线程的详细信息，请参阅[编写多线程 Win32 程序](../parallel/writing-a-multithreaded-win32-program.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用 C 和 Win32 进行多线程编程](../parallel/multithreading-with-c-and-win32.md)