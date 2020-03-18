---
title: 使用 C 和 Win32 进行多线程编程
ms.date: 08/09/2019
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
ms.openlocfilehash: 1764561e0b2b43b8a89d8a1eb2e85d84ce33c4fc
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427355"
---
# <a name="multithreading-with-c-and-win32"></a>使用 C 和 Win32 进行多线程编程

Microsoft C/C++编译器（MSVC）支持创建多线程应用程序。 如果你的应用程序需要执行可能导致用户界面无法响应的昂贵操作，请考虑使用多个线程。

使用 MSVC，可以通过多种方式来编程多个线程：可以使用/WinRT C++和 Windows 运行时库、Microsoft 基础类（MFC）库、 C++/cli 和 .net 运行时，也可以使用 C 运行时库和 Win32 API。 本文介绍 C 中的多线程处理。有关示例代码，请参阅[C 中的示例多线程程序](sample-multithread-c-program.md)。

## <a name="multithread-programs"></a>多线程程序

线程基本上是通过程序执行的路径。 它也是 Win32 计划的最小执行单位。 线程由堆栈、CPU 寄存器的状态以及系统计划程序执行列表中的条目组成。 每个线程都共享进程的所有资源。

进程包含一个或多个线程，以及内存中程序的代码、数据和其他资源。 典型的程序资源包括打开的文件、信号量和动态分配的内存。 当系统计划程序提供其线程执行控制之一时，程序执行。 计划程序将确定应运行的线程以及应运行的线程。 较低优先级的线程可能需要等待较高优先级的线程完成其任务。 在多处理器计算机上，计划程序可将单个线程移动到不同的处理器来平衡 CPU 负载。

进程中的每个线程都独立运行。 除非使它们彼此可见，否则线程会单独执行并不知道进程中的其他线程。 但是，共享公共资源的线程必须使用信号量或其他进程间通信方法来协调其工作。 有关同步线程的详细信息，请参阅[编写多线程 Win32 程序](#writing-a-multithreaded-win32-program)。

## <a name="library-support-for-multithreading"></a>多线程编程的库支持

现在，所有版本的 CRT 都支持多线程处理，但某些函数的非锁定版本除外。 有关详细信息，请参阅[多线程库性能](../c-runtime-library/multithreaded-libraries-performance.md)。 有关可与代码链接的 CRT 版本的信息，请参阅[crt 库功能](../c-runtime-library/crt-library-features.md)。

## <a name="include-files-for-multithreading"></a>多线程编程的包含文件

标准 CRT 包含文件在库中实现 C 运行时库函数时将其声明为。 如果编译器选项指定[__fastcall 或 __vectorcall](../build/reference/gd-gr-gv-gz-calling-convention.md)调用约定，则编译器假设应使用 register 调用约定调用所有函数。 运行时库函数使用 C 调用约定，标准包含文件中的声明通知编译器生成对这些函数的正确外部引用。

## <a name="crt-functions-for-thread-control"></a>线程控制的 CRT 函数

所有 Win32 程序至少有一个线程。 任何线程都可以创建其他线程。 线程可以快速完成其工作，然后终止，也可以在程序的整个生命周期内保持活动状态。

CRT 库为线程创建和终止提供以下函数： [_beginthread、_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)、 [_endthread 和 _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)。

如果操作成功，则 `_beginthread` 和 `_beginthreadex` 函数会创建一个新线程并返回一个线程标识符。 如果线程完成执行，则该线程会自动终止。 或者，它可以通过调用 `_endthread` 或 `_endthreadex`自行终止。

> [!NOTE]
> 如果从使用 libcmt.lib 生成的程序调用 C 运行时例程，则必须使用 `_beginthread` 或 `_beginthreadex` 函数启动线程。 不要使用 Win32 函数 `ExitThread` 和 `CreateThread`。 如果有多个线程被阻止，等待挂起线程完成对 C 运行时数据结构的访问，则使用 `SuspendThread` 会导致死锁。

### <a name="_core_the__beginthread_function"></a>_Beginthread 和 _beginthreadex 函数

`_beginthread` 和 `_beginthreadex` 函数创建新线程。 线程与进程中的其他线程共享进程的代码段和数据段，但具有其自己的唯一寄存器值、堆栈空间和当前指令地址。 系统为每个线程提供 CPU 时间，以便进程中的所有线程都可以并发执行。

`_beginthread` 和 `_beginthreadex` 与 Win32 API 中的[CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)函数类似，但具有以下差异：

- 它们初始化某些 C 运行时库变量。 仅在线程中使用 C 运行时库时，这一点很重要。

- `CreateThread` 有助于提供对安全属性的控制。 您可以使用此函数启动处于挂起状态的线程。

如果成功，则 `_beginthread` 和 `_beginthreadex` 返回新线程的句柄; 否则返回错误代码。

### <a name="_core_the__endthread_function"></a>_Endthread 和 _endthreadex 函数

[_Endthread](../c-runtime-library/reference/endthread-endthreadex.md)函数终止由 `_beginthread` 创建的线程（同样，`_endthreadex` 终止 `_beginthreadex`所创建的线程）。 线程完成后会自动终止。 `_endthread` 和 `_endthreadex` 适用于从线程内部进行的条件终止。 例如，专用于通信处理的线程可能会在无法获取通信端口的控制时退出。

## <a name="writing-a-multithreaded-win32-program"></a>编写多线程 Win32 程序

编写具有多个线程的程序时，必须协调其行为和[程序资源的使用](#_core_sharing_common_resources_between_threads)。 此外，请确保每个线程都接收[其自己的堆栈](#_core_thread_stacks)。

### <a name="_core_sharing_common_resources_between_threads"></a>在线程之间共享公共资源

> [!NOTE]
> 有关 MFC 视图中的类似讨论，请参见[多线程处理：编程提示](multithreading-programming-tips.md)和[多线程处理：何时使用同步类](multithreading-when-to-use-the-synchronization-classes.md)。

每个线程都有自己的堆栈及其自己的 CPU 寄存器副本。 其他资源（如文件、静态数据和堆内存）由进程中的所有线程共享。 必须同步使用这些公共资源的线程。 Win32 提供多种方法来同步资源，包括信号量、关键部分、事件和互斥体。

当多个线程访问静态数据时，您的程序必须提供可能的资源冲突。 请考虑一个程序，其中一个线程更新静态数据结构，其中包含要由另一个线程显示的项的*x*，*y*坐标。 如果更新线程改变*x*坐标并在它可以更改*y*坐标之前被抢占，则可能会在更新*y*坐标之前安排显示线程。 该项将显示在错误的位置。 可以通过使用信号量来控制对结构的访问来避免此问题。

Mutex （short for *mut*ual *ex*clusion）是在彼此异步执行的线程或进程之间进行通信的方式。 这种通信可以用于协调多个线程或进程的活动，通常通过锁定和解锁资源来控制对共享资源的访问。 若要解决此*x*，*y*坐标更新问题，更新线程将设置一个互斥体，指示在执行更新之前数据结构正在使用。 这会在处理完这两个坐标之后清除互斥体。 在更新显示之前，显示线程必须等待互斥体清楚。 等待 mutex 的这一过程通常称为互斥体，因为该进程已被阻止，*并且在互斥*体清除之前无法继续。

[示例多线程 c 程序](sample-multithread-c-program.md)中显示的弹跳 c 程序使用名为 `ScreenMutex` 的 mutex 来协调屏幕更新。 每当其中一个显示线程准备写入屏幕时，它会调用与句柄的 `WaitForSingleObject`，以 `ScreenMutex` 并始终无限，以指示 `WaitForSingleObject` 调用应在互斥体上阻塞，而不会超时。如果 `ScreenMutex` 清楚，则 wait 函数将设置互斥体，以便其他线程无法干扰显示，并继续执行该线程。 否则，在清除互斥体之前，将阻止线程。 当线程完成显示更新时，它通过调用 `ReleaseMutex`来释放互斥体。

屏幕显示和静态数据只是需要仔细管理的两个资源。 例如，程序可能有多个线程访问同一文件。 由于另一个线程可能已移动文件指针，因此，每个线程都必须在读取或写入之前重置文件指针。 此外，每个线程都必须确保其定位指针的时间和访问文件时的时间不会被抢占。 这些线程应使用信号量来协调对文件的访问，方法是对 `WaitForSingleObject` 和 `ReleaseMutex` 调用的每个文件访问进行括号。 下面的代码示例演示了此方法：

```C
HANDLE    hIOMutex = CreateMutex (NULL, FALSE, NULL);

WaitForSingleObject( hIOMutex, INFINITE );
fseek( fp, desired_position, 0L );
fwrite( data, sizeof( data ), 1, fp );
ReleaseMutex( hIOMutex);
```

### <a name="_core_thread_stacks"></a>线程堆栈

应用程序的所有默认堆栈空间都分配给第一个执行线程，这称为 "线程 1"。 因此，你必须为程序需要的每个其他线程指定为单独的堆栈分配多少内存。 如果需要，操作系统将为线程分配其他堆栈空间，但必须指定默认值。

`_beginthread` 调用中的第一个参数是一个指向 `BounceProc` 函数的指针，该函数执行线程。 第二个参数指定线程的默认堆栈大小。 最后一个参数是传递给 `BounceProc`的 ID 号。 `BounceProc` 使用 ID 号来设定随机数生成器的种子，并选择线程的颜色属性和显示字符。

调用 C 运行库或 Win32 API 的线程必须为它们调用的库和 API 函数留出足够的堆栈空间。 C `printf` 函数需要超过500个字节的堆栈空间，并且在调用 Win32 API 例程时，您应该有2K 字节的堆栈空间可用。

由于每个线程都有自己的堆栈，因此可以使用尽可能少的静态数据来避免对数据项产生潜在的冲突。 设计你的程序，以便对可以专用于线程的所有数据使用自动堆栈变量。 反弹程序中唯一的全局变量是互斥体或在初始化后从不更改的变量。

Win32 还提供线程本地存储（TLS）来存储每个线程的数据。 有关详细信息，请参阅[线程本地存储（TLS）](thread-local-storage-tls.md)。

## <a name="avoiding-problem-areas-with-multithread-programs"></a>避免与多线程程序有关的问题

创建、链接或执行多线程 C 程序时可能会遇到几个问题。 下表描述了一些更常见的问题。 （有关从 MFC 角度进行类似的讨论，请参见[多线程处理：编程提示](multithreading-programming-tips.md)。）

|问题|可能的原因|
|-------------|--------------------|
|您将看到一个消息框，表明您的程序导致了保护冲突。|许多 Win32 编程错误都会导致保护冲突。 保护冲突的一个常见原因是间接将数据分配给 null 指针。 因为这会导致程序尝试访问不属于它的内存，所以会发出保护冲突。<br /><br /> 检测保护冲突原因的简单方法是使用调试信息编译程序，然后通过 Visual Studio 环境中的调试器运行该程序。 出现保护错误时，Windows 会将控制转移到调试器，并将光标置于引起问题的行上。|
|您的程序会生成许多编译和链接错误。|您可以通过将编译器的警告等级设置为其最高值之一并留意警告消息，来消除许多潜在问题。 通过使用第3级或第4级警告等级选项，您可以检测无意的数据转换、缺少函数原型以及非 ANSI 功能的使用。|

## <a name="see-also"></a>另请参阅

[针对旧代码的多线程支持C++（Visual）](multithreading-support-for-older-code-visual-cpp.md)\
[C 中的示例多线程程序](sample-multithread-c-program.md)\
[线程本地存储（TLS）](thread-local-storage-tls.md)\
[利用/WinRT\ 进行C++并发和异步操作](/windows/uwp/cpp-and-winrt-apis/concurrency)
[使用 C++ 和 MFC 进行多线程编程](multithreading-with-cpp-and-mfc.md)
