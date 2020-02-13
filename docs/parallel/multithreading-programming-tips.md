---
title: 多线程处理： MFC 编程提示
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
ms.openlocfilehash: 79e7d440b478c759c5d4fd683d6af3423e7e8661
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140451"
---
# <a name="multithreading-mfc-programming-tips"></a>多线程处理： MFC 编程提示

多线程应用程序需要比单线程应用程序更严格的关注，以确保按预期顺序执行操作，并且由多个线程访问的任何数据都不会损坏。 本主题介绍在通过 Microsoft 基础类（MFC）库对多线程应用程序进行编程时可能出现的问题的方法。

- [从多个线程访问对象](#_core_accessing_objects_from_multiple_threads)

- [从非 MFC 线程访问 MFC 对象](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)

- [Windows 句柄映射](#_core_windows_handle_maps)

- [线程间通信](#_core_communicating_between_threads)

## <a name="_core_accessing_objects_from_multiple_threads"></a>从多个线程访问对象

MFC 对象本身不是线程安全的。 两个单独的线程不能操作同一个对象，除非您使用 MFC 同步类和/或适当的 Win32 同步对象（如临界区）。 有关关键部分和其他相关对象的详细信息，请参阅 Windows SDK 中的[同步](/windows/win32/Sync/synchronization)。

类库在内部使用关键部分来保护全局数据结构，例如调试内存分配使用的结构。

## <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a>从非 MFC 线程访问 MFC 对象

如果你的多线程应用程序以与使用[CWinThread](../mfc/reference/cwinthread-class.md)对象不同的方式创建线程，则无法从该线程访问其他 MFC 对象。 换言之，如果您想要从辅助线程访问任何 MFC 对象，则必须使用[多线程处理：创建用户界面线程](multithreading-creating-user-interface-threads.md)或[多线程处理：创建辅助线程](multithreading-creating-worker-threads.md)中所述的方法之一创建该线程。 这些方法是允许类库初始化处理多线程应用程序所需的内部变量的唯一方法。

## <a name="_core_windows_handle_maps"></a>Windows 句柄映射

作为一般规则，线程只能访问它创建的 MFC 对象。 这是因为，临时和永久的 Windows 句柄映射保存在线程本地存储中，以帮助防止同时访问多个线程。 例如，工作线程无法执行计算，然后调用文档的 `UpdateAllViews` 成员函数，使包含修改的新数据的窗口。 这根本不会有任何影响，因为从 `CWnd` 对象到 Hwnd 的映射在主线程中是本地的。 这意味着一个线程可能具有从 Windows 句柄到C++对象的映射，但其他线程可能会将该相同句柄映射到不同C++的对象。 在一个线程中所做的更改不会反映在另一个线程中。

有多种方法可以解决此问题。 第一种方式是将各个句柄（如 HWND）而不C++是对象传递到工作线程。 然后，工作线程通过调用相应的 `FromHandle` 成员函数将这些对象添加到其临时映射。 你还可以通过调用 `Attach`将对象添加到线程的永久映射中，但仅当确保对象的长度超过线程时才应执行此操作。

另一种方法是创建新的用户定义的消息，使其与工作线程执行的不同任务相对应，并使用 `::PostMessage`将这些消息发布到应用程序的主窗口。 这种通信方法与两个不同的应用程序对话类似，不同之处在于这两个线程在同一地址空间中执行。

有关句柄映射的详细信息，请参阅[技术说明 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md)。 有关线程本地存储的详细信息，请参阅[线程本地存储](/windows/win32/ProcThread/thread-local-storage)和使用 Windows SDK 中的[线程本地存储](/windows/win32/ProcThread/using-thread-local-storage)。

## <a name="_core_communicating_between_threads"></a>线程间通信

MFC 提供了多个类，这些类允许线程同步对对象的访问以保持线程安全。 [多线程处理：如何使用同步类](multithreading-how-to-use-the-synchronization-classes.md)和[多线程处理：何时使用同步类](multithreading-when-to-use-the-synchronization-classes.md)中介绍了这些类的用法。 有关这些对象的详细信息，请参阅 Windows SDK 中的[同步](/windows/win32/Sync/synchronization)。

## <a name="see-also"></a>另请参阅

[使用 C++ 和 MFC 进行多线程编程](multithreading-with-cpp-and-mfc.md)
