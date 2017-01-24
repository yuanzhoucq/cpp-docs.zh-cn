---
title: "使用 C++ 和 MFC 进行多线程编程 | Microsoft Docs"
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
  - "CWinThread 类, 目的"
  - "MFC [C++], 多线程处理"
  - "多线程处理 [C++], MFC"
  - "同步 [C++], 多线程处理"
  - "同步类 [C++]"
  - "线程处理 [C++], MFC"
  - "线程处理 [MFC]"
  - "线程处理 [MFC], 关于线程处理"
  - "用户界面线程 [C++]"
  - "辅助线程 [C++]"
ms.assetid: 979605f8-3988-44b5-ac9c-b8cce7fcce14
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 C++ 和 MFC 进行多线程编程
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft 基础类 \(MFC\) 库提供多线程应用程序支持。  本主题描述进程、线程和 MFC 多线程处理方法。  
  
 进程是应用程序的执行实例。  例如，双击“记事本”图标时，将启动运行“记事本”的进程。  
  
 线程是进程内的执行路径。  启动“记事本”时，操作系统创建进程并开始执行该进程的主线程。  此线程终止时，进程也终止。  启动代码以函数地址的形式将此主线程提供给操作系统。  通常是所提供的 **main** 函数或 `WinMain` 函数的地址。  
  
 如果愿意，可以在应用程序中创建其他线程。  如果在处理后台任务或维护任务时不希望用户等待这些任务完成，则可能需要创建其他线程。  MFC 应用程序中的所有线程都由 [CWinThread](../../mfc/reference/cwinthread-class.md) 对象表示。  大多数情况下，甚至不必显式创建这些对象，而只需调用框架 Helper 函数 [AfxBeginThread](../Topic/AfxBeginThread.md)，该函数将为您创建 `CWinThread` 对象。  
  
 MFC 区分两种类型的线程：用户界面线程和辅助线程。  用户界面线程通常用于处理用户输入及响应用户生成的事件和消息。  辅助线程通常用于完成不需要用户输入的任务（如重新计算）。  Win32 API 不区分线程类型；它只需要了解线程的起始地址以开始执行线程。  MFC 为用户界面中的事件提供消息泵，从而对用户界面线程进行专门处理。  `CWinApp` 是用户界面线程对象的一个示例，因为它从 `CWinThread` 派生并对用户生成的事件和消息进行处理。  
  
 应特别注意以下情况：可能有不止一个线程需要访问同一对象。  [多线程处理：编程提示](../../parallel/multithreading-programming-tips.md) 介绍了一些可以避免在这些情况下可能发生的问题的技术。  [多线程处理：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)说明如何使用可用的类从多个线程同步访问一个对象。  
  
 编写和调试多线程处理本身是一项复杂棘手的任务，因为您必须确保一次只能有一个线程访问对象。  多线程处理主题没有讲述多线程处理的基础知识，而只是说明了如何在多线程程序中使用 MFC。  Visual C\+\+ 中包含的多线程 MFC 示例阐释了几种多线程“添加功能”和 MFC 中未包含的 Win32 API，但只是一些入门知识。  
  
 有关操作系统如何处理进程和线程的更多信息，请参见 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的[进程和线程](http://msdn.microsoft.com/library/windows/desktop/ms684841)。  
  
 有关 MFC 多线程支持的更多信息，请参见以下主题：  
  
-   [多线程处理：创建用户界面线程](../../parallel/multithreading-creating-user-interface-threads.md)  
  
-   [多线程处理：创建辅助线程](../../parallel/multithreading-creating-worker-threads.md)  
  
-   [多线程处理：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)  
  
-   [多线程处理：终止线程](../../parallel/multithreading-terminating-threads.md)  
  
-   [多线程处理：编程提示](../../parallel/multithreading-programming-tips.md)  
  
-   [多线程处理：何时使用同步类](../../parallel/multithreading-when-to-use-the-synchronization-classes.md)  
  
## 请参阅  
 [针对旧代码的多线程支持 \(Visual C\+\+\)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)