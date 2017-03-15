---
title: "应用程序和线程支持类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.support"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序对象 [C++], 线程支持类"
  - "应用程序支持类 [C++]"
  - "锁定类"
  - "同步类, 多线程处理"
  - "线程支持类 [C++]"
  - "线程处理 [MFC]"
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 应用程序和线程支持类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每个应用程序只有具有的应用程序对象；此对象与在运行程序的其他对象并从 `CWinApp`派生。  
  
 Microsoft 基础类 \(MFC\) 库支持执行多个线程在应用程序中。  所有应用程序必须至少有一个线程；`CWinApp` 对象使用的线程处于此主线程。  
  
 `CWinThread` 封装操作系统线程的功能的一部分。  若要使用多个线程可以更容易，MFC 还提供同步对象类提供基于 C 接口以 . C\+\+ Win32 同步对象。  
  
## 应用程序和线程支持类  
 [CWinApp](../mfc/reference/cwinapp-class.md)  
 封装代码初始化，运行和终止应用程序。  您从该类中派生应用程序对象。  
  
 [CWinThread](../mfc/reference/cwinthread-class.md)  
 所有线程的基类。  如果线程执行用户接口函数，则使用直接或从 `CWinThread` 派生类。  `CWinApp` 是从 `CWinThread` 中派生的。  
  
## 同步对象类  
 [CSyncObject](../mfc/reference/csyncobject-class.md)  
 同步对象类的基类。  
  
 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
 仅允许在单个进程中的线程访问对象的同步类。  
  
 [CSemaphore](../mfc/reference/csemaphore-class.md)  
 允许在一个同步类和同时访问之间存在着指定的最大数对象。  
  
 [CMutex](../mfc/reference/cmutex-class.md)  
 仅允许不论几个进程中的线程访问对象的同步类。  
  
 [CEvent](../mfc/reference/cevent-class.md)  
 当事件发生，通知应用程序编写同步类。  
  
 [CSingleLock](../mfc/reference/csinglelock-class.md)  
 用于在线程安全类的成员函数上锁定一个同步对象。  
  
 [CMultiLock](../mfc/reference/cmultilock-class.md)  
 用于在线程安全类的成员函数。锁定的一个或多个同步对象同步对象。  
  
## 相关类  
 [CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)  
 分析启动程序的命令行。  
  
 [CWaitCursor](../mfc/reference/cwaitcursor-class.md)  
 屏幕上会将等待光标放置。  使用在长时间操作过程。  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 句柄永久性存储控件条停靠状态数据。  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 保留最近使用的文件列表\(MRU\)。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)