---
title: "针对旧代码的多线程支持 (Visual C++) | Microsoft Docs"
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
  - "并发编程 [C++]"
  - "多个并发线程"
  - "多线程"
  - "多线程处理 [C++]"
  - "多线程处理 [C++], 关于多线程处理"
  - "编程 [C++], 多线程"
  - "线程处理 [C++]"
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 针对旧代码的多线程支持 (Visual C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 使您可以同时运行多个并行执行的线程。  使用多线程处理，可以派生出后台任务、管理同时发生的输入流、管理用户界面，等等。  
  
## 本节内容  
 [使用 C 和 Win32 进行多线程处理](../../parallel/multithreading-with-c-and-win32.md)  
 为创建 Microsoft Windows 多线程应用程序提供支持  
  
 [使用 C\+\+ 和 MFC 进行多线程处理](../../parallel/multithreading-with-cpp-and-mfc.md)  
 描述什么是进程和线程以及 MFC 的多线程处理方法是什么。  
  
 [多线程和区域设置](../../parallel/multithreading-and-locales.md)  
 讨论在多线程应用程序中使用 C 运行库和标准 C\+\+ 库的区域设置功能时引发的问题。  
  
## 相关章节  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
 表示应用程序中的执行线程。  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
 描述一个纯虚类，该类提供 Win32 中的同步对象所共有的功能。  
  
 [CSemaphore](../../mfc/reference/csemaphore-class.md)  
 表示一个信号量，是一个允许一个或多个进程中的有限多个线程访问一个资源的同步对象。  
  
 [CMutex](../../mfc/reference/cmutex-class.md)  
 表示一个 mutex，是一个允许一个线程以互相排斥的方式访问一个资源的同步对象。  
  
 [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)  
 表示一个临界区，是一个允许一个线程同时访问一个资源或代码段的同步对象。  
  
 [CEvent](../../mfc/reference/cevent-class.md)  
 表示一个事件，是一个允许一个线程通知另一个线程事件已经发生的同步对象。  
  
 [CMultiLock](../../mfc/reference/cmultilock-class.md)  
 表示多线程程序中用于控制对多个资源的访问的访问控制机制。  
  
 [CSingleLock](../../mfc/reference/csinglelock-class.md)  
 表示多线程程序中用于控制对一个资源的访问的访问控制机制。  
  
 [\(NOTINBUILD\)Visual C\+\+ Programming Methodologies](http://msdn.microsoft.com/zh-cn/0822f806-fa81-4b65-bf0f-1e2921f30c95)  
 提供有关下列内容的主题链接：描述有关 Visual C\+\+ 库的概念信息和讨论各种编码技术和方法。