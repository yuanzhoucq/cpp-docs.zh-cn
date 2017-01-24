---
title: "多线程处理：编程提示 | Microsoft Docs"
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
  - "访问控制 [C++], 多线程处理"
  - "通信 [C++], 在线程之间"
  - "临界区 [C++]"
  - "句柄映射 [C++]"
  - "多线程处理 [C++], 编程提示"
  - "非 MFC 线程 [C++]"
  - "对象 [C++], 多线程与"
  - "编程 [C++], 多线程"
  - "同步 [C++], 多线程处理"
  - "线程处理 [C++], 最佳做法"
  - "线程处理 [MFC], 编程提示"
  - "疑难解答 [C++], 多线程处理"
  - "Windows 句柄映射 [C++]"
ms.assetid: ad14cc70-c91c-4c24-942f-13a75e58bf8a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 多线程处理：编程提示
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

访问数据时，使用多线程应用程序比使用单线程应用程序要更加小心。  因为在多线程应用程序中同时有多个独立的执行路径正在使用，算法或数据或两者都必须注意：可以有一个以上的线程同时使用数据。  本主题说明在使用 Microsoft 基础类 \(MFC\) 库编制多线程应用程序时避免发生潜在问题的技术。  
  
-   [从多线程访问对象](#_core_accessing_objects_from_multiple_threads)  
  
-   [从非 MFC 线程访问 MFC 对象](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)  
  
-   [Windows 句柄映射](#_core_windows_handle_maps)  
  
-   [线程间通信](#_core_communicating_between_threads)  
  
##  <a name="_core_accessing_objects_from_multiple_threads"></a> 从多线程访问对象  
 由于大小和性能原因，MFC 对象在对象级别不是线程安全的，而只是在类级别线程安全。  这表明可以有两个独立的线程操作两个不同的 `CString` 对象，但不能有两个线程操作同一个 `CString` 对象。  如果一定要有多个线程操作同一个对象，请用适当的 Win32 同步机制（如临界区）保护此类访问权。  有关临界区和其他相关对象的更多信息，请参见 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的[同步](http://msdn.microsoft.com/library/windows/desktop/ms686353)。  
  
 类库内部使用临界区以保护全局数据结构，例如调试存储分配使用的结构。  
  
##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> 从非 MFC 线程访问 MFC 对象  
 如果多线程应用程序使用 [CWinThread](../../mfc/reference/cwinthread-class.md) 对象以外的方式创建线程，则不能从该线程访问其他 MFC 对象。  换句话说，如果要从次要线程访问任何 MFC 对象，则必须用[多线程编程：创建用户界面线程](../../parallel/multithreading-creating-user-interface-threads.md)或[多线程编程：创建辅助线程](../../parallel/multithreading-creating-worker-threads.md)中所述的方法之一创建该线程。  只有这些方法才允许类库初始化处理多线程应用程序所需的内部变量。  
  
##  <a name="_core_windows_handle_maps"></a> Windows 句柄映射  
 作为通用规则，线程只能访问它创建的 MFC 对象。  这是因为临时和永久性 Windows 句柄映射保留在线程本地存储中，以对它进行保护，确保不能有多个线程同时访问它。  例如，辅助线程不能执行计算并调用文档的 `UpdateAllViews` 成员函数来修改包含新数据视图的窗口。  此操作将不会有任何效果，因为从 `CWnd` 对象到 `HWND` 的映射是主线程的本地映射。  这意味着一个线程可能有从 Windows 句柄到 C\+\+ 对象的映射，但是另一个线程可能会将此句柄映射到其他 C\+\+ 对象。  在一个线程内所做的更改将不会反映在另一个线程中。  
  
 有几种方式可以避免此问题。  首先是将各个句柄（如 `HWND`）而不是 C\+\+ 对象传递到辅助线程。  然后，辅助线程通过调用适当 `FromHandle` 成员函数将这些对象添加到它的临时映射。  还可以通过调用 **Attach** 将对象添加到线程的永久映射，但只有在保证对象比线程存在的时间长时，才应当进行此操作。  
  
 另一个方法是创建新的与辅助线程将要执行的不同任务相对应的用户定义消息，并使用 **::PostMessage** 将这些消息发布到应用程序的主窗口。  此通信方法类似于两个不同的应用程序在对话，只不过这两个线程在同一地址空间中执行。  
  
 有关句柄映射的更多信息，请参见[技术说明 3](../../mfc/tn003-mapping-of-windows-handles-to-objects.md)。  有关线程本地存储的更多信息，请参见 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的[线程本地存储](http://msdn.microsoft.com/library/windows/desktop/ms686749)和[使用线程本地存储](http://msdn.microsoft.com/library/windows/desktop/ms686991)。  
  
##  <a name="_core_communicating_between_threads"></a> 线程间通信  
 MFC 提供了多个类，使线程可以同步访问对象以维护线程安全。  [多线程编程：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)和[多线程编程：何时使用同步类](../../parallel/multithreading-when-to-use-the-synchronization-classes.md)中描述了这些类的用法。  有关这些对象的更多信息，请参见 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的[同步](http://msdn.microsoft.com/library/windows/desktop/ms686353)。  
  
## 请参阅  
 [使用 C\+\+ 和 MFC 进行多线程编程](../../parallel/multithreading-with-cpp-and-mfc.md)