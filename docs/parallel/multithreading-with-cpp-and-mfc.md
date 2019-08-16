---
title: 使用 C++ 和 MFC 进行多线程编程
ms.date: 08/27/2018
helpviewer_keywords:
- MFC [C++], multithreading
- threading [C++], MFC
- worker threads [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], about threading
- CWinThread class, purpose of
- multithreading [C++], MFC
- threading [MFC]
- user interface threads [C++]
ms.assetid: 979605f8-3988-44b5-ac9c-b8cce7fcce14
ms.openlocfilehash: eaf28404b06e9b0bf6126d8bbc140bf46cff37da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512010"
---
# <a name="multithreading-with-c-and-mfc"></a>使用 C++ 和 MFC 进行多线程编程

Microsoft 基础类 (MFC) 库为多线程应用程序提供支持。 本主题介绍进程和线程以及用于多线程处理的 MFC 方法。

进程是应用程序的执行实例。 例如, 双击记事本图标时, 将启动一个运行记事本的进程。

线程是进程内的执行路径。 启动记事本时, 操作系统会创建一个进程, 并开始执行该进程的主线程。 此线程终止时, 会执行此过程。 通过启动代码以函数地址的形式向操作系统提供此主线程。 通常, 它是所提供的`main`或`WinMain`函数的地址。

如果需要, 可以在应用程序中创建其他线程。 当您不希望用户等待完成时, 您可能希望执行此操作来处理后台或维护任务。 MFC 应用程序中的所有线程都由[CWinThread](../mfc/reference/cwinthread-class.md)对象表示。 在大多数情况下, 你甚至不必显式创建这些对象。改为调用框架 helper 函数[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), 该函数将`CWinThread`创建对象。

MFC 区分两种类型的线程: 用户界面线程和工作线程。 用户界面线程通常用于处理用户输入并响应用户生成的事件和消息。 工作线程通常用于完成无需用户输入的任务 (例如重新计算)。 Win32 API 不区分线程类型;只需知道线程的起始地址, 就可以开始执行线程。 MFC 通过为用户界面中的事件提供消息泵来专门处理用户界面线程。 `CWinApp`是用户界面线程对象的一个示例, 因为它派生自`CWinThread`并处理用户生成的事件和消息。

在多个线程可能需要访问同一对象的情况下, 应特别注意。 [多线程处理：编程提示](multithreading-programming-tips.md)介绍了可用于解决在这些情况下可能会出现的问题的技术。 [多线程处理：如何使用同步类](multithreading-how-to-use-the-synchronization-classes.md)介绍了如何使用可用于将访问从多个线程同步到单个对象的类。

编写和调试多线程编程本质上是一项复杂而棘手的任务, 因为必须确保一次不会有多个线程访问对象。 多线程处理主题并不介绍多线程编程的基本知识, 只是如何在多线程程序中使用 MFC。 Visual C++中包含的多线程 MFC 示例说明了 MFC 不包含的几个多线程添加功能和 Win32 api;但是, 它们只是一个开始点。

有关操作系统如何处理进程和线程的详细信息, 请参阅 Windows SDK 中的[进程和线程](/windows/win32/ProcThread/processes-and-threads)。

有关 MFC 多线程支持的详细信息, 请参阅以下主题:

- [多线程处理：创建用户界面线程](multithreading-creating-user-interface-threads.md)

- [多线程处理：创建工作线程](multithreading-creating-worker-threads.md)

- [多线程处理：如何使用同步类](multithreading-how-to-use-the-synchronization-classes.md)

- [多线程处理：终止线程](multithreading-terminating-threads.md)

- [多线程处理：编程提示](multithreading-programming-tips.md)

- [多线程处理：何时使用同步类](multithreading-when-to-use-the-synchronization-classes.md)

## <a name="see-also"></a>请参阅

[针对旧代码的多线程支持 (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)
