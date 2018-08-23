---
title: 多线程处理： 编程提示 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ad830117323aef807fcebc1ef61b4dfb1900bd9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591306"
---
# <a name="multithreading-programming-tips"></a>多线程处理：编程提示
在访问数据时，多线程应用程序要比单线程应用程序的更加小心。 因为有多个，独立于路径中执行的同时使用多线程应用程序中算法、 数据，或两者必须知道该数据可以由多个线程一次使用。 本主题介绍使用 Microsoft 基础类 (MFC) 库的多线程应用程序进行编程时避免潜在问题的技术。  
  
- [从多个线程访问对象](#_core_accessing_objects_from_multiple_threads)  
  
- [从非 MFC 线程访问 MFC 对象](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)  
  
- [Windows 句柄映射](#_core_windows_handle_maps)  
  
- [在线程之间进行通信](#_core_communicating_between_threads)  
  
##  <a name="_core_accessing_objects_from_multiple_threads"></a> 从多个线程访问对象  
 
由于大小和性能原因，MFC 对象不是线程安全在对象级别，只能在类级别。 这意味着可以有两个单独的线程处理两个不同`CString`对象，但不是处理相同两个线程`CString`对象。 如果一定要有多个线程处理同一个对象，使用适当的 Win32 同步机制，例如临界区保护此类访问。 有关更多有关临界区及其他相关对象，请参阅[同步](http://msdn.microsoft.com/library/windows/desktop/ms686353)Windows SDK 中。  
  
类库在内部使用临界区以保护全局数据结构，如所使用的调试内存分配。  
  
##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> 从非 MFC 线程访问 MFC 对象  
 
如果已创建的线程，而不是使用一种方法中的多线程应用程序[CWinThread](../mfc/reference/cwinthread-class.md)对象，不能从该线程访问其他 MFC 对象。 换而言之，如果你想要从辅助线程访问任何 MFC 对象，则必须创建该线程中所述的方法之一[多线程处理： 创建用户界面线程](../parallel/multithreading-creating-user-interface-threads.md)或[多线程处理：创建辅助线程](../parallel/multithreading-creating-worker-threads.md)。 这些方法是允许类库，用于初始化内部变量处理多线程应用程序的需要是唯一的。  
  
##  <a name="_core_windows_handle_maps"></a> Windows 句柄映射  
 
作为一般规则是，线程可以访问它创建的 MFC 对象。 这是因为临时和永久的 Windows 句柄映射保留在线程本地存储，以帮助保护，从多个线程同时访问。 例如，一个工作线程不能执行计算并调用文档的`UpdateAllViews`成员函数来包含视图上修改的新数据的窗口。 这没有任何影响，因为从映射`CWnd`对象与 Hwnd 是主线程的本地。 这意味着一个线程可能必须从 Windows 句柄映射到 c + + 对象，但另一个线程可能会将此句柄映射到不同的 c + + 对象。 在一个线程中所做的更改将不会反映在其他。  
  
有几种方法解决此问题。 第一个是传递 （例如 HWND) 的各个句柄而不是 c + + 对象与工作线程。 工作线程然后将这些对象添加到其临时映射，通过调用适当`FromHandle`成员函数。 您还可以将该对象通过调用添加到线程的永久映射`Attach`，但仅当可以保证该对象将存在时间超过该线程时，才应进行此操作。  
  
另一种方法是创建用户定义的新消息对应于不同的任务工作线程将执行，并将这些消息发布到应用程序的主窗口使用`::PostMessage`。 此方法是通信的类似于对话，只不过这两个线程正在执行的相同地址空间中的两个不同应用程序。  
  
有关句柄映射的详细信息，请参阅[技术说明 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md)。 有关线程本地存储区的详细信息，请参阅[线程本地存储区](http://msdn.microsoft.com/library/windows/desktop/ms686749)并[使用线程本地存储](http://msdn.microsoft.com/library/windows/desktop/ms686991)Windows SDK 中。  
  
##  <a name="_core_communicating_between_threads"></a> 在线程之间进行通信  
 
MFC 提供了多个类，使线程可以同步对对象以维护线程安全的访问。 中描述了这些类的用法[多线程处理： 如何使用同步类](../parallel/multithreading-how-to-use-the-synchronization-classes.md)并[多线程处理： 何时使用同步类](../parallel/multithreading-when-to-use-the-synchronization-classes.md)。 有关这些对象的详细信息，请参阅[同步](http://msdn.microsoft.com/library/windows/desktop/ms686353)Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  

[使用 C++ 和 MFC 进行多线程编程](../parallel/multithreading-with-cpp-and-mfc.md)