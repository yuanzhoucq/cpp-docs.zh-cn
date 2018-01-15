---
title: "多线程处理与 c + + 和 MFC |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 14d076865cd83837e2de218ad0189c037c78cd83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-with-c-and-mfc"></a>使用 C++ 和 MFC 进行多线程编程
Microsoft 基础类 (MFC) 库提供支持多线程应用程序。 本主题介绍进程、 线程和 MFC 方法为多线程处理。  
  
 进程处于正在执行的应用程序实例。 例如，双击记事本图标时，你将启动运行记事本过程。  
  
 线程是执行的进程中的路径。 当你启动记事本时，操作系统创建进程，并开始执行该过程的主线程。 当此线程终止时，因此执行该过程。 此主线程中的函数地址窗体的启动代码提供给操作系统。 通常情况下，它是的地址**主要**或`WinMain`提供的函数。  
  
 如果你想，你可以在你的应用程序中创建其他线程。 你可能想要执行此操作可在不希望用户等待它们完成时处理背景或维护任务。 MFC 应用程序中的所有线程都由[CWinThread](../mfc/reference/cwinthread-class.md)对象。 在大多数情况下，你甚至无需显式创建这些对象;改为调用框架帮助程序函数[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，这将创建`CWinThread`为你的对象。  
  
 MFC 区分两种类型的线程： 用户界面线程和辅助线程。 用户界面线程通常用于处理用户输入并响应事件和用户生成的消息。 工作线程通常用于完成任务，例如重新计算，不需要用户输入。 Win32 API 不区分类型的一个线程。它只需知道线程的起始地址，因此它可以开始执行该线程。 MFC 专门通过提供用户界面中的事件的消息泵处理用户界面线程。 `CWinApp`是一种用户界面线程对象，因为它派生自`CWinThread`和处理事件和用户生成的消息。  
  
 其中多个线程可能要求对同一对象的访问的情况下应特别注意。 [多线程处理： 编程提示](../parallel/multithreading-programming-tips.md)介绍可用于避免在这些情况下，可能会出现的问题的技术。 [多线程处理： 如何使用同步类](../parallel/multithreading-how-to-use-the-synchronization-classes.md)介绍如何使用可从多个线程对单个对象的访问进行同步的类。  
  
 编写和调试多线程的编程本质上是一项复杂且棘手的任务，因为你必须确保一次多个线程访问对象。 多线程处理主题没有讲述多线程编程，只是说明了如何在多线程程序中使用 MFC 的基础的知识。 包含 Visual c + + 中的多线程的 MFC 示例阐释几多线程的添加功能，通过 MFC; 不包含 Win32 Api但是，它们是仅用于为起始点。  
  
 有关如何操作系统将处理进程和线程的详细信息，请参阅[进程和线程](http://msdn.microsoft.com/library/windows/desktop/ms684841)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
 有关 MFC 多线程处理支持的详细信息，请参阅以下主题：  
  
-   [多线程处理：创建用户界面线程](../parallel/multithreading-creating-user-interface-threads.md)  
  
-   [多线程处理：创建辅助线程](../parallel/multithreading-creating-worker-threads.md)  
  
-   [多线程处理：如何使用同步类](../parallel/multithreading-how-to-use-the-synchronization-classes.md)  
  
-   [多线程处理：终止线程](../parallel/multithreading-terminating-threads.md)  
  
-   [多线程处理：编程提示](../parallel/multithreading-programming-tips.md)  
  
-   [多线程处理：何时使用同步类](../parallel/multithreading-when-to-use-the-synchronization-classes.md)  
  
## <a name="see-also"></a>请参阅  
 [针对旧代码的多线程支持 (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)