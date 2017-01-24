---
title: "编写多线程 Win32 程序 | Microsoft Docs"
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
  - "通信 [C++], 在线程之间"
  - "多线程处理 [C++], 共享公共资源"
  - "多线程处理 [C++], 线程堆栈"
  - "mutex [C++]"
  - "互斥 [C++]"
  - "资源 [C++], 多线程处理"
  - "共享的资源 [C++]"
  - "堆栈 [C++]"
  - "线程堆栈 [C++]"
  - "线程处理 [C++], 共享公共资源"
  - "线程处理 [C++], 线程堆栈"
ms.assetid: 1415f47d-417f-4f42-949b-946fb28aab0e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 编写多线程 Win32 程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

编写具有多线程的程序时，必须协调这些线程的行为和[程序资源的用法](#_core_sharing_common_resources_between_threads)。  还必须确定每个线程接收[自己的堆栈](#_core_thread_stacks)。  
  
##  <a name="_core_sharing_common_resources_between_threads"></a> 线程间共享公共资源  
  
> [!NOTE]
>  有关从 MFC 角度进行的类似讨论，请参见[多线程处理：编程提示](../parallel/multithreading-programming-tips.md)和[多线程处理：何时使用同步类](../parallel/multithreading-when-to-use-the-synchronization-classes.md)。  
  
 每个线程具有自己的堆栈和自己的 CPU 寄存器副本。  其他资源（如文件、静态数据和堆内存）由进程中的所有线程共享。  使用这些公共资源的线程必须同步。  Win32 提供了几种同步资源的方式，包括信号、临界区、事件和互斥体。  
  
 当多线程访问静态数据时，程序必须提供可能的资源冲突。  假定有这样一个程序，一个线程更新静态数据结构，该结构包含要由其他线程显示的项的 *x*,*y* 坐标。  如果更新线程更改了 *x* 坐标并且在更改 *y* 坐标之前被取代，则可能会在更新 *y* 坐标之前安排显示线程。  该项可能会在错误的位置显示。  通过使用信号灯控制对结构的访问，可以避免此问题。  
  
 互斥体（*mut*ual *ex*clusion 的缩写）是异步执行的线程或进程间通信的方式。  此通信通常用于协调多个线程或进程的活动，通常通过锁定和取消锁定资源控制对共享资源的访问。  为解决此 *x*,*y* 坐标的更新问题，更新线程将设置 mutex，在执行更新之前指示数据结构正在使用。  更新线程将在两个坐标全部处理完之后清除互斥体。  显示线程在更新显示之前必须等待清除互斥体。  由于进程被阻止且直到清除 mutex 后才能继续，因此等待 mutex 的进程通常称为在 mutex 上“阻止”。  
  
 [多线程 C 程序示例](../parallel/sample-multithread-c-program.md)中显示的 Bounce.c 程序使用名为 `ScreenMutex` 的 mutex 协调屏幕更新。  每当其中的一个显示线程准备写入屏幕时，将调用 **WaitForSingleObject**，使用 `ScreenMutex` 的句柄和常数 **INFINITE** 指示 **WaitForSingleObject** 调用应该在互斥体上阻止但不应该超时。  如果清除了 `ScreenMutex`，等待函数将设置互斥体，使其他线程不能影响显示并继续执行该线程。  否则，线程将阻止，直到清除互斥体。  线程完成显示更新后，通过调用 **ReleaseMutex** 释放互斥体。  
  
 需要小心管理的资源只有屏幕显示和静态数据两种。  例如，程序可能有多个线程访问同一文件。  由于其他线程可能已经移动了文件指针，因此每个线程在读取或写入之前必须重新设置文件指针。  另外，每个线程必须确保在它定位指针和访问文件两个时间之间没有被替换。  这些线程应该通过用 **WaitForSingleObject** 和 **ReleaseMutex** 调用将每个文件的访问括起来，以使用信号灯协调对文件的访问。  下面的代码示例演示此项技术：  
  
```  
HANDLE    hIOMutex= CreateMutex (NULL, FALSE, NULL);  
  
WaitForSingleObject( hIOMutex, INFINITE );  
fseek( fp, desired_position, 0L );  
fwrite( data, sizeof( data ), 1, fp );  
ReleaseMutex( hIOMutex);  
```  
  
##  <a name="_core_thread_stacks"></a> 线程堆栈  
 应用程序的所有默认堆栈空间都被分配到称为线程 1 的第一个执行线程。  因此，必须为程序所需的每个附加线程的单独堆栈指定分配的内存量。  如果必要，操作系统将为线程分配附加的堆栈空间，但必须指定默认值。  
  
 `_beginthread` 调用中的第一个参数是指向将要执行线程的 **BounceProc** 函数的指针。  第二个参数指定线程的默认堆栈大小。  最后一个参数是传递到 **BounceProc** 的 ID 号。  **BounceProc** 用 ID 号为随机数生成器提供种子，并选择线程的颜色特性和显示字符。  
  
 调用 C 运行库或 Win32 API 的线程必须要有足够的堆栈空间用于所调用的库和 API 函数。  C `printf` 函数需要 500 多个字节的堆栈空间，调用 Win32 API 例程时应该有 2K 的可用堆栈空间。  
  
 因为每个线程都自己的堆栈，因此可以通过尽可能少地使用静态数据而避免潜在的数据项冲突。  对于线程可私有的所有数据，将程序设计为使用自动堆栈变量。  Bounce.c 程序中仅有的全局变量是 mutex 或初始化之后不再更改的变量。  
  
 Win32 还提供“线程本地存储”\(TLS\)，存储基于线程的数据。  有关详细信息，请参阅[线程本地存储 \(TLS\)](../parallel/thread-local-storage-tls.md)。  
  
## 请参阅  
 [使用 C 和 Win32 进行多线程编程](../parallel/multithreading-with-c-and-win32.md)