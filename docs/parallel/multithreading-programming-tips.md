---
title: 多线程处理：MFC 编程提示
ms.date: 08/27/2018
helpviewer_keywords:
- multithreading [C++], programming tips
- handle maps [C++]
- access control [C++], multithreading
- objects [C++], multiple threads and
- non-MFC threads [C++]
- threading [MFC], programming tips
- critical sections [C++]
- synchronization [C++], multithreading
- programming [C++], multithreaded
- communications [C++], between threads
- threading [C++], best practices
- troubleshooting [C++], multithreading
- Windows handle maps [C++]
ms.assetid: ad14cc70-c91c-4c24-942f-13a75e58bf8a
ms.openlocfilehash: e89d0d534638f7216f142bc3f86633a59b8b0ff7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62212420"
---
# <a name="multithreading-mfc-programming-tips"></a>多线程处理：MFC 编程提示

多线程应用程序要比单线程应用程序以确保操作会以预期顺序，并且未损坏的多个线程访问任何数据的更加小心。 本主题介绍使用 Microsoft 基础类 (MFC) 库的多线程应用程序进行编程时避免潜在问题的技术。

- [从多个线程访问对象](#_core_accessing_objects_from_multiple_threads)

- [从非 MFC 线程访问 MFC 对象](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)

- [Windows 句柄映射](#_core_windows_handle_maps)

- [在线程之间进行通信](#_core_communicating_between_threads)

##  <a name="_core_accessing_objects_from_multiple_threads"></a> 从多个线程访问对象

MFC 对象不是单独线程安全。 两个单独的线程无法处理同一对象，除非您使用 MFC 同步类和/或适当的 Win32 同步对象，如临界区。 有关更多有关临界区及其他相关对象，请参阅[同步](/windows/desktop/Sync/synchronization)Windows SDK 中。

类库在内部使用临界区以保护全局数据结构，如所使用的调试内存分配。

##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> 从非 MFC 线程访问 MFC 对象

如果已创建的线程，而不是使用一种方法中的多线程应用程序[CWinThread](../mfc/reference/cwinthread-class.md)对象，不能从该线程访问其他 MFC 对象。 换而言之，如果你想要从辅助线程访问任何 MFC 对象，则必须创建该线程中所述的方法之一[多线程处理：创建用户界面线程](multithreading-creating-user-interface-threads.md)或[多线程处理：创建辅助线程](multithreading-creating-worker-threads.md)。 这些方法是允许类库，用于初始化内部变量处理多线程应用程序的需要是唯一的。

##  <a name="_core_windows_handle_maps"></a> Windows 句柄映射

作为一般规则是，线程可以访问它创建的 MFC 对象。 这是因为临时和永久的 Windows 句柄映射保留在线程本地存储，以帮助保护，从多个线程同时访问。 例如，一个工作线程不能执行计算并调用文档的`UpdateAllViews`成员函数来包含视图上修改的新数据的窗口。 这没有任何影响，因为从映射`CWnd`对象与 Hwnd 是主线程的本地。 这意味着一个线程可能必须从 Windows 句柄的映射C++对象，而另一个线程可能会将该句柄映射到不同C++对象。 在一个线程中所做的更改将不会反映在其他。

有几种方法解决此问题。 第一种是传递 （例如 HWND) 的各个句柄而不是C++对象与工作线程。 工作线程然后将这些对象添加到其临时映射，通过调用适当`FromHandle`成员函数。 您还可以将该对象通过调用添加到线程的永久映射`Attach`，但仅当可以保证该对象将存在时间超过该线程时，才应进行此操作。

另一种方法是创建用户定义的新消息对应于不同的任务工作线程将执行，并将这些消息发布到应用程序的主窗口使用`::PostMessage`。 此方法是通信的类似于对话，只不过这两个线程正在执行的相同地址空间中的两个不同应用程序。

有关句柄映射的详细信息，请参阅[技术说明 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md)。 有关线程本地存储区的详细信息，请参阅[线程本地存储区](/windows/desktop/ProcThread/thread-local-storage)并[使用线程本地存储](/windows/desktop/ProcThread/using-thread-local-storage)Windows SDK 中。

##  <a name="_core_communicating_between_threads"></a> 在线程之间进行通信

MFC 提供了多个类，使线程可以同步对对象以维护线程安全的访问。 中描述了这些类的用法[多线程处理：如何使用同步类](multithreading-how-to-use-the-synchronization-classes.md)和[多线程处理：何时使用同步类](multithreading-when-to-use-the-synchronization-classes.md)。 有关这些对象的详细信息，请参阅[同步](/windows/desktop/Sync/synchronization)Windows SDK 中。

## <a name="see-also"></a>请参阅

[使用 C++ 和 MFC 进行多线程编程](multithreading-with-cpp-and-mfc.md)
