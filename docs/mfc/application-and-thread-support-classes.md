---
title: "应用程序和线程支持类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.support
dev_langs: C++
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2859687c72a674f496e039a4f4b32795cfa4604d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="application-and-thread-support-classes"></a>应用程序和线程支持类
每个应用程序具有一个且仅有一个应用程序对象;此对象协调正在运行的程序中的其他对象，并从派生`CWinApp`。  
  
 Microsoft 基础类 (MFC) 库支持多个应用程序中的执行线程。 所有应用程序必须具有至少一个线程;通过使用的线程你`CWinApp`对象是此主线程。  
  
 `CWinThread`封装操作系统的线程处理功能的一部分。 若要使使用多个线程更轻松，MFC 还提供同步对象类，用于提供 Win32 同步对象的 c + + 接口。  
  
## <a name="application-and-thread-classes"></a>应用程序和线程类  
 [CWinApp](../mfc/reference/cwinapp-class.md)  
 封装用于初始化、 运行和终止应用程序的代码。 将从此类派生应用程序对象。  
  
 [CWinThread](../mfc/reference/cwinthread-class.md)  
 所有线程的基类。 直接使用，或从派生类`CWinThread`如果你的线程执行用户界面功能。 `CWinApp` 派生自 `CWinThread`。  
  
## <a name="synchronization-object-classes"></a>同步对象类  
 [CSyncObject](../mfc/reference/csyncobject-class.md)  
 同步对象类的基类。  
  
 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
 同步类，该类允许访问的对象的单个进程中只有一个线程。  
  
 [CSemaphore](../mfc/reference/csemaphore-class.md)  
 同步类，该类允许一个，指定的最大同时访问的对象数之间。  
  
 [CMutex](../mfc/reference/cmutex-class.md)  
 同步类，该类允许任意数量的访问的对象的进程中只有一个线程。  
  
 [CEvent](../mfc/reference/cevent-class.md)  
 当已发生事件时通知应用程序同步类。  
  
 [CSingleLock](../mfc/reference/csinglelock-class.md)  
 中的线程安全类成员函数用于锁定上一个同步对象。  
  
 [CMultiLock](../mfc/reference/cmultilock-class.md)  
 中的线程安全类成员函数用于锁定从同步对象的数组的一个或多个同步对象。  
  
## <a name="related-classes"></a>相关的类  
 [CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)  
 分析命令行与你的程序已启动。  
  
 [CWaitCursor](../mfc/reference/cwaitcursor-class.md)  
 在屏幕上将等待光标。 在长时间的操作过程中使用。  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 处理停靠控件条的状态数据的持久性存储的区。  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 维护最近使用的 (MRU) 文件列表。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../mfc/class-library-overview.md)

