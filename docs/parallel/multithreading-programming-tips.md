---
title: 多线程处理： 编程提示 |Microsoft 文档
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
ms.openlocfilehash: b9c4241b9257244de840db1f57c5e7abcb32f206
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689982"
---
# <a name="multithreading-programming-tips"></a>多线程处理：编程提示
在访问数据时，多线程应用程序要比使用单线程应用程序的更加小心。 由于有多个，独立的路径中执行的同时在中使用多线程应用程序，算法、 数据，或两者必须知道该数据无法通过多个线程一次使用。 本主题介绍使用 Microsoft 基础类 (MFC) 库的多线程应用程序进行编程时避免潜在问题的技术。  
  
-   [从多个线程访问的对象](#_core_accessing_objects_from_multiple_threads)  
  
-   [从非 MFC 线程访问 MFC 对象](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)  
  
-   [Windows 句柄映射](#_core_windows_handle_maps)  
  
-   [线程之间的通信](#_core_communicating_between_threads)  
  
##  <a name="_core_accessing_objects_from_multiple_threads"></a> 从多个线程访问的对象  
 由于大小和性能原因，MFC 对象不是线程安全在对象级别，只能在类级别。 这意味着你可以有两个单独的线程操作两个不同`CString`对象，但不是两个线程操作相同`CString`对象。 如果一定要有多个线程操作相同的对象，请与相应的 Win32 同步机制，例如临界区保护此类访问权限。 有关详细信息，有关关键部分和其他相关对象，请参阅[同步](http://msdn.microsoft.com/library/windows/desktop/ms686353)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
 类库内部使用临界区以保护全局数据结构，例如曾使用的调试内存分配。  
  
##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> 从非 MFC 线程访问 MFC 对象  
 如果你有一个多线程的应用程序中而不是使用一种方法创建线程[CWinThread](../mfc/reference/cwinthread-class.md)对象，不能从该线程访问其他 MFC 对象。 换而言之，如果你想要从辅助线程访问任何 MFC 对象，则必须创建该线程中所述的方法的其中一条[多线程处理： 创建用户界面线程](../parallel/multithreading-creating-user-interface-threads.md)或[多线程处理：创建辅助线程](../parallel/multithreading-creating-worker-threads.md)。 这些方法是仅允许类库初始化处理多线程应用程序所必需的内部变量的那些。  
  
##  <a name="_core_windows_handle_maps"></a> Windows 句柄映射  
 作为一般规则，线程可以访问它创建的 MFC 对象。 这是因为临时和永久 Windows 句柄映射保留在线程本地存储，可帮助维护从多个线程同时访问的保护。 例如，一个工作线程不能执行计算，然后调用文档的`UpdateAllViews`成员函数来包含如何修改对新数据的视图的窗口。 此项不起作用，因为从映射`CWnd`对象添加到`HWND`是主线程的本地。 这意味着一个线程可能具有 c + + 对象、 从 Windows 句柄的映射，但另一个线程可能会将此句柄映射到不同的 c + + 对象。 在一个线程中所做的更改将不会反映另一部分中。  
  
 有多种解决此问题。 第一种是将单个句柄传递 (如`HWND`) 而不是 c + + 对象到辅助线程。 工作线程然后将这些对象添加到其临时映射，通过调用适当`FromHandle`成员函数。 你还可以将该对象通过调用添加到线程的永久映射**附加**，但仅当则可保证该对象将存在时间长于线程时，才应进行此操作。  
  
 另一种方法是创建新用户定义消息对应于不同的任务将执行你的工作线程，并将其发布到应用程序的主窗口的这些消息使用 **:: PostMessage**。 此方法是通信的类似于两个不同的应用程序对话，只不过这两个线程在相同的地址空间中一起执行。  
  
 有关句柄映射的详细信息，请参阅[技术说明 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md)。 有关线程本地存储区的详细信息，请参阅[线程本地存储区](http://msdn.microsoft.com/library/windows/desktop/ms686749)和[使用线程本地存储](http://msdn.microsoft.com/library/windows/desktop/ms686991)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
##  <a name="_core_communicating_between_threads"></a> 线程之间的通信  
 MFC 提供了大量的类，使线程对象以维护线程安全的访问进行同步。 中描述了这些类的用法[多线程处理： 如何使用同步类](../parallel/multithreading-how-to-use-the-synchronization-classes.md)和[多线程处理： 何时使用同步类](../parallel/multithreading-when-to-use-the-synchronization-classes.md)。 有关这些对象的详细信息，请参阅[同步](http://msdn.microsoft.com/library/windows/desktop/ms686353)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
## <a name="see-also"></a>请参阅  
 [使用 C++ 和 MFC 进行多线程编程](../parallel/multithreading-with-cpp-and-mfc.md)