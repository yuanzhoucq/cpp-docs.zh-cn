---
title: 编写多线程 Win32 程序
ms.date: 11/04/2016
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
ms.openlocfilehash: c8536505882ca9a87aec385ca1c42d652ea84ff7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62205512"
---
# <a name="writing-a-multithreaded-win32-program"></a>编写多线程 Win32 程序

当您编写具有多个线程的程序时，必须协调它们的行为和[程序的资源的使用](#_core_sharing_common_resources_between_threads)。 您还必须确保每个线程都会收到[其自己的堆栈](#_core_thread_stacks)。

##  <a name="_core_sharing_common_resources_between_threads"></a> 常见线程之间共享资源

> [!NOTE]
>  从 MFC 的角度的类似讨论，请参阅[多线程处理：编程提示](multithreading-programming-tips.md)和[多线程处理：何时使用同步类](multithreading-when-to-use-the-synchronization-classes.md)。

每个线程都具有其自己的堆栈并注册其自己的 CPU 的副本。 在进程中的所有线程共享其他资源，如文件、 静态数据和堆内存。 使用这些常用资源的线程必须同步。 Win32 提供多种方式来同步资源，包括信号量、 临界区、 事件和互斥体。

当多个线程同时访问静态数据时，应用程序必须提供可能的资源冲突。 请考虑一个程序，一个线程更新一个静态数据结构，其中包含*x*，*y*项显示由另一个线程的坐标。 如果更新线程更改*x*协调并可以更改之前被抢占*y*坐标，显示线程可能会安排之前*y*坐标是更新。 该项目将显示在错误的位置。 通过使用信号量来控制结构的访问，可以避免此问题。

互斥体 (的缩写*mut*ual *ex*clusion) 是一种方法在线程或另一个以异步方式执行的进程之间进行通信。 此通信通常用于协调多个线程或进程的活动通常通过锁定和解锁资源控制共享资源的访问权限。 若要解决此问题*x*，*y*坐标的更新问题，更新线程设置互斥体，该值指示数据结构在使用之前执行更新。 这两个坐标必须处理后，它会清除该互斥体。 显示线程必须等待互斥体要显示在更新之前清除。 等待互斥体的这一过程通常称为因为进程被阻塞，且无法继续，直到清除互斥体互斥体的阻塞。

Bounce.c 程序中所示[多线程 C 程序示例](sample-multithread-c-program.md)使用名为互斥体`ScreenMutex`协调屏幕更新。 它将调用一个显示线程的已准备好将写入到屏幕上，每次`WaitForSingleObject`句柄`ScreenMutex`和常量的无限指示`WaitForSingleObject`调用应阻止互斥体和不会超时。如果`ScreenMutex`被清除，等待函数使其他线程不能干扰显示设置该互斥体，并继续执行线程。 否则，线程阻塞，直到清除互斥体。 当线程完成显示更新时，它通过调用释放此斥锁`ReleaseMutex`。

屏幕显示和静态数据只有两个需要小心管理的资源。 例如，程序可能有多个线程访问同一文件。 由于另一个线程可能已经移动文件指针，因此每个线程读取或写入之前必须重置文件指针。 此外，每个线程必须确保它不占用的时间，它将指针定位和访问文件的时间之间。 这些线程应使用信号量来协调由括号与每个文件访问的文件访问权`WaitForSingleObject`和`ReleaseMutex`调用。 下面的代码示例演示此方法：

```
HANDLE    hIOMutex= CreateMutex (NULL, FALSE, NULL);

WaitForSingleObject( hIOMutex, INFINITE );
fseek( fp, desired_position, 0L );
fwrite( data, sizeof( data ), 1, fp );
ReleaseMutex( hIOMutex);
```

##  <a name="_core_thread_stacks"></a> 线程堆栈

所有应用程序的默认堆栈空间被分配给第一个线程的执行，这被称为线程 1。 因此，必须指定需要多少内存来为每个其他线程的单独堆栈分配您的程序。 操作系统为线程分配附加的堆栈空间，如有必要，但必须指定默认值。

中的第一个参数`_beginthread`调用是一个指向`BounceProc`函数来执行线程。 第二个参数指定的线程的默认堆栈大小。 最后一个参数是传递给一个 ID 号`BounceProc`。 `BounceProc` 使用的 ID 号随机数字生成器的种子和来选择线程的颜色属性和显示字符。

到 C 运行时库或 Win32 API 进行调用的线程必须要有足够的库和它们调用的 API 函数的堆栈空间。 C`printf`函数需要超过 500 个字节的堆栈空间，并调用 Win32 API 例程时，应具有 2k 的堆栈空间可用。

由于每个线程具有其自己的堆栈，您可以避免潜在的冲突数据项可能进行静态数据使用。 设计程序的所有数据，可以是私有的线程使用自动堆栈变量。 Bounce.c 程序中的只有全局变量是互斥体或永远不会更改后进行初始化的变量。

Win32 还提供了线程本地存储 (TLS) 来存储每个线程数据。 有关详细信息，请参阅[线程本地存储 (TLS)](thread-local-storage-tls.md)。

## <a name="see-also"></a>请参阅

[使用 C 和 Win32 进行多线程编程](multithreading-with-c-and-win32.md)
