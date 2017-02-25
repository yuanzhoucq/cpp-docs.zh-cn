---
title: "多线程处理：何时使用同步类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "受控制的资源访问 [C++]"
  - "多线程处理 [C++], 同步类"
  - "资源 [C++], 多线程处理"
  - "同步 [C++], 多线程处理"
  - "同步访问类 [C++]"
  - "同步类 [C++]"
  - "线程处理 [C++], 同步"
  - "线程处理 [MFC], 同步类"
ms.assetid: 4914f54e-68ac-438f-93c9-c013455a657e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 多线程处理：何时使用同步类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供的多线程类分为两类：同步对象（[CSyncObject](../mfc/reference/csyncobject-class.md)、[CSemaphore](../mfc/reference/csemaphore-class.md)、[CMutex](../mfc/reference/cmutex-class.md)、[CCriticalSection](../mfc/reference/ccriticalsection-class.md) 和 [CEvent](../mfc/reference/cevent-class.md)）和同步访问对象（[CMultiLock](../mfc/reference/cmultilock-class.md) 和 [CSingleLock](../mfc/reference/csinglelock-class.md)）。  
  
 当必须控制对资源的访问以确保资源的完整性时，使用同步类。  同步访问类用于获取对这些资源的访问权。  本主题介绍各个类的适用情况。  
  
 若要确定应使用的同步类，请询问以下一系列问题：  
  
1.  是否必须等到发生某事时，应用程序才能访问资源（例如，在将数据写入文件之前，必须先从通信端口接收它）？  
  
     如果是，请使用 `CEvent`。  
  
2.  同一应用程序内的多个线程是否可以同时访问此资源（例如，应用程序允许在同一文档上最多同时打开五个带有视图的窗口）？  
  
     如果是，请使用 `CSemaphore`。  
  
3.  是否可以有一个以上的应用程序使用此资源（例如，资源在 DLL 中）？  
  
     如果是，请使用 `CMutex`。  
  
     如果不是，请使用 `CCriticalSection`。  
  
 从不直接使用 **CSyncObject**。  它是其他四个同步类的基类。  
  
## 示例 1：使用三个同步类  
 以维护链接的帐户列表的应用程序为例。  此应用程序允许在独立的窗口中最多检查三个帐户，但是在任何特定的时间，只能更新一个帐户。  更新帐户后，通过网络将更新的数据发送到数据存档。  
  
 此示例应用程序使用所有这三种类型的同步类。  因为它一次最多允许检查三个帐户，所以它使用 `CSemaphore` 限制对三个视图对象的访问。  当尝试查看第四个帐户时，应用程序或者等到前三个窗口中有一个关闭，或者该尝试失败。  更新帐户时，应用程序使用 `CCriticalSection` 确保一次只更新一个帐户。  更新成功后，发出信号 `CEvent` 以释放等待该事件信号发送的线程。  此线程将新数据发送到数据存档。  
  
## 示例 2：使用同步访问类  
 选择要使用的同步访问类更为简单。  如果应用程序只与访问单个受控资源有关，请使用 `CSingleLock`。  如果需要访问多个受控资源中的任何一个，则使用 `CMultiLock`。  在示例 1 中，应使用 `CSingleLock`，因为在每种情况下，任何特定时间都只需要一个资源。  
  
 有关如何使用同步类的信息，请参见[多线程处理：如何使用同步类](../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  有关同步的信息，请参见 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的[同步](http://msdn.microsoft.com/library/windows/desktop/ms686353)。  有关 MFC 中多线程处理支持的信息，请参见[使用 C\+\+ 和 MFC 进行多线程处理](../parallel/multithreading-with-cpp-and-mfc.md)。  
  
## 请参阅  
 [使用 C\+\+ 和 MFC 进行多线程编程](../parallel/multithreading-with-cpp-and-mfc.md)