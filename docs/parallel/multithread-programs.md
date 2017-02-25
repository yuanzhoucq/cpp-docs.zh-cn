---
title: "多线程程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "多线程处理 [C++], 关于线程"
  - "线程处理 [C++], 关于线程处理"
ms.assetid: 02443596-f7e1-48d0-b3a4-39ee0e54e444
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 多线程程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

线程实质上是程序中的执行路径。  也是 Win32 安排的最小执行单元。  线程包括堆栈、CPU 寄存器的状态和系统计划程序执行列表中的项。  每个线程共享所有进程的资源。  
  
 进程包括一个或多个线程和代码、数据和内存中的其他程序资源。  典型的程序资源是打开的文件、信号灯和动态分配的内存。  当系统计划程序给予其中的一个线程执行控制时，即执行程序。  计划程序确定应当运行哪些线程以及它们应当何时运行。  较低优先级的线程可能必须等到较高优先级的线程完成任务后才能运行。  在多处理器计算机上，计划程序可以将单个线程移到不同的处理器以平衡 CPU 负荷。  
  
 进程中的每个线程都独立运行。  除非使这些线程相互可见，否则线程分别执行，对进程中的其他线程一无所知。  线程共享公共资源，但是，必须使用信号灯或其他进程间的通信方法协调它们的工作。  有关同步线程的更多信息，请参见[编写多线程 Win32 程序](../parallel/writing-a-multithreaded-win32-program.md)。  
  
## 请参阅  
 [使用 C 和 Win32 进行多线程编程](../parallel/multithreading-with-c-and-win32.md)