---
title: 使用 c + + 和 MFC 多线程处理 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1f5f1ea1d8d6578b631da772522a0a852d11c89
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "43132189"
---
# <a name="multithreading-with-c-and-mfc"></a>使用 C++ 和 MFC 进行多线程编程
Microsoft 基础类 (MFC) 库提供多线程应用程序的支持。 本主题描述进程、 线程和 MFC 方法多线程处理。  
  
进程是正在执行的应用程序实例。 例如，双击记事本图标，则启动运行记事本的进程。  
  
线程是进程内执行的路径。 启动记事本时，操作系统会创建一个进程并开始执行该过程的主线程。 当此线程终止时，因此执行过程。 此主线程中的函数地址形式的启动代码提供给操作系统。 通常情况下，是的地址`main`或`WinMain`提供的函数。  
  
如果您希望，可以在应用程序中创建其他线程。 您可能想要执行此操作以你不希望用户等待它们完成时处理后台或维护任务。 由 MFC 应用程序中的所有线程[CWinThread](../mfc/reference/cwinthread-class.md)对象。 在大多数情况下，您甚至无需显式创建这些对象，改为调用框架 helper 函数[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，这将创建`CWinThread`为您的对象。  
  
MFC 区分两种类型的线程： 用户界面线程和工作线程。 用户界面线程通常用于处理用户输入和响应事件和用户生成的消息。 工作线程通常用于完成任务，如重新计算，不需要用户输入的。 Win32 API 不区分类型的线程;它只需知道线程的起始地址，因此它可以开始执行线程。 MFC 专门通过提供用户界面中的事件消息泵处理用户界面线程。 `CWinApp` 是一种用户界面线程对象，因为它派生`CWinThread`和处理事件和用户生成的消息。  
  
其中多个线程可能会要求对同一对象的访问的情况下，应给予特别关注。 [多线程处理： 编程提示](multithreading-programming-tips.md)介绍可用于在这些情况下可能出现的问题的解决方法。 [多线程处理： 如何使用同步类](multithreading-how-to-use-the-synchronization-classes.md)介绍如何使用可用于同步对单个对象从多个线程访问的类。  
  
编写和调试多线程的编程本质上是一项复杂棘手的任务，因为您必须确保一次多个线程访问对象。 多线程处理主题没有讲述多线程编程，只是说明了如何在多线程程序中使用 MFC 的基础知识。 Visual c + + 中包含的多线程的 MFC 示例阐释了一些多线程添加功能和 Win32 Api 通过 MFC; 不包含但是，它们仅用于为起始点。  
  
有关操作系统如何处理进程和线程的详细信息，请参阅[进程和线程](/windows/desktop/ProcThread/processes-and-threads)Windows SDK 中。  
  
有关 MFC 多线程支持的详细信息，请参阅以下主题：  
  
- [多线程处理：创建用户界面线程](multithreading-creating-user-interface-threads.md)  
  
- [多线程处理：创建辅助线程](multithreading-creating-worker-threads.md)  
  
- [多线程处理：如何使用同步类](multithreading-how-to-use-the-synchronization-classes.md)  
  
- [多线程处理：终止线程](multithreading-terminating-threads.md)  
  
- [多线程处理：编程提示](multithreading-programming-tips.md)  
  
- [多线程处理：何时使用同步类](multithreading-when-to-use-the-synchronization-classes.md)  
  
## <a name="see-also"></a>请参阅  
 
[针对旧代码的多线程支持 (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)