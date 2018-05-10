---
title: 编写多线程的 Win32 程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- thread stacks [C++]
- resources [C++], multithreading
- stacks [C++]
- shared resources [C++]
- threading [C++], sharing common resources
- multithreading [C++], thread stacks
- multithreading [C++], sharing common resources
- mutual exclusion [C++]
- communications [C++], between threads
- mutex [C++]
- threading [C++], thread stacks
ms.assetid: 1415f47d-417f-4f42-949b-946fb28aab0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d88add7830316ae192a728f9c9ff10320657eaf
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="writing-a-multithreaded-win32-program"></a>编写多线程 Win32 程序
当你编写具有多个线程的程序时，你必须协调它们的行为和[的程序的资源使用](#_core_sharing_common_resources_between_threads)。 你还必须确保每个线程接收[其自己的堆栈](#_core_thread_stacks)。  
  
##  <a name="_core_sharing_common_resources_between_threads"></a> 线程间共享公共资源  
  
> [!NOTE]
>  从 MFC 角度来看的类似讨论，请参阅[多线程处理： 编程提示](../parallel/multithreading-programming-tips.md)和[多线程处理： 何时使用同步类](../parallel/multithreading-when-to-use-the-synchronization-classes.md)。  
  
 每个线程都有其自己的堆栈，并注册其自己的 CPU 副本。 其他资源，如文件、 静态数据和堆内存中进程共享的所有线程。 必须要同步线程使用这些常用资源。 Win32 提供多种方式来同步资源，包括信号量、 临界区、 事件和互斥。  
  
 当多个线程访问静态数据时，程序必须提供可能的资源冲突。 请考虑一个线程更新静态数据结构包含的程序*x*，*y*坐标项要显示的另一个线程。 如果更新线程更改*x*协调的方式以及在它可以更改之前被取代*y*坐标，显示线程可以将其计划之前*y*坐标是更新。 该项目将显示在错误的位置。 通过使用信号量来控制结构的访问，可避免此问题。  
  
 互斥体 (短，无法用于*mut*ual *ex*clusion) 是一种在线程或另一个以异步方式执行的进程之间进行通信。 通常使用此通信对活动进行协调的多个线程或进程，通常通过锁定和解锁资源控制共享资源的访问。 为了解决此问题*x*，*y*坐标的更新问题，更新线程设置 mutex，指示的数据结构在使用之前执行更新。 这两个坐标必须处理后，它将清除互斥体。 显示线程必须等待要显示在更新之前已经很明确的互斥体。 此等待互斥体的过程通常称为阻止上互斥体，因为该过程被阻止，直到清除互斥体无法继续。  
  
 中显示的 Bounce.c 程序[多线程 C 程序示例](../parallel/sample-multithread-c-program.md)使用名为互斥体`ScreenMutex`要协调屏幕更新。 它将调用一个显示线程已准备好将写入到屏幕上，每次**WaitForSingleObject**的句柄与`ScreenMutex`和常量**无限**，则指示**WaitForSingleObject**调用应阻塞的互斥体和不会超时。如果`ScreenMutex`被清除，等待函数设置互斥体，因此其他线程无法显示会妨碍并继续执行线程。 否则，线程阻塞，直到清除互斥体。 当在线程完成显示更新时，将通过调用释放互斥体**ReleaseMutex**。  
  
 屏幕显示和静态数据仅包含两个需要小心管理的资源。 例如，程序可能有多个线程访问同一文件。 由于另一个线程可能已经移动文件指针，因此每个线程读取或写入之前必须重置文件指针。 此外，每个线程必须确保它指针定位至的时间和它所访问该文件的时间之间不抢占。 这些线程应使用信号量来协调对文件的访问通过包括与每个文件访问**WaitForSingleObject**和**ReleaseMutex**调用。 下面的代码示例演示此方法：  
  
```  
HANDLE    hIOMutex= CreateMutex (NULL, FALSE, NULL);  
  
WaitForSingleObject( hIOMutex, INFINITE );  
fseek( fp, desired_position, 0L );  
fwrite( data, sizeof( data ), 1, fp );  
ReleaseMutex( hIOMutex);  
```  
  
##  <a name="_core_thread_stacks"></a> 线程堆栈  
 所有应用程序的默认堆栈空间分配给第一个线程的执行，这被称为线程 1。 因此，你必须指定需要多少内存来为每个其他线程的单独堆栈分配程序。 操作系统为线程分配附加的堆栈空间，如有必要，但你必须指定默认值。  
  
 中的第一个自变量`_beginthread`调用是一个指向**BounceProc**函数，执行线程。 第二个参数指定线程的默认堆栈大小。 最后一个参数是传递给一个 ID 号**BounceProc**。 **BounceProc**使用的 ID 号随机数字生成器种子并选择线程的颜色属性和显示字符。  
  
 到 C 运行库或 Win32 API 进行调用的线程必须要有足够的库和它们所调用的 API 函数的堆栈空间。 C`printf`函数需要多于 500 个字节的堆栈空间，并且调用 Win32 API 例程时，你应拥有 2k 的堆栈空间可用。  
  
 由于每个线程具有其自己的堆栈，你可以通过避免潜在冲突数据项尽可能使用可能进行静态数据。 设计你的程序的所有数据可以是私有的线程中使用自动堆栈变量。 Bounce.c 程序中的只有全局变量为互斥体或永远不会更改后它们将初始化的变量。  
  
 Win32 还提供了线程本地存储 (TLS) 来存储每个线程数据。 有关详细信息，请参阅[线程本地存储 (TLS)](../parallel/thread-local-storage-tls.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用 C 和 Win32 进行多线程编程](../parallel/multithreading-with-c-and-win32.md)