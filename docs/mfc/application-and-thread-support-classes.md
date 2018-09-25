---
title: 应用程序和线程支持类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.support
dev_langs:
- C++
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce9c799c8dbc2a98c7d45dfa9a2e444024c9a7a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412310"
---
# <a name="application-and-thread-support-classes"></a>应用程序和线程支持类

每个应用程序具有一个且只有一个应用程序对象;此对象协调正在运行的程序中的其他对象和派生自`CWinApp`。

Microsoft 基础类 (MFC) 库支持多个应用程序中的执行线程。 所有应用程序必须具有至少一个线程;通过使用的线程在`CWinApp`对象是此主线程。

`CWinThread` 封装操作系统的线程处理功能的一部分。 若要使多个线程的使用，MFC 还提供同步的对象类来提供对 Win32 同步对象的 c + + 接口。

## <a name="application-and-thread-classes"></a>应用程序和线程类

[CWinApp](../mfc/reference/cwinapp-class.md)<br/>
封装用于初始化、 运行和终止应用程序的代码。 将从此类派生您的应用程序对象。

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
所有线程的基类。 直接使用，或从派生类`CWinThread`如果你的线程执行用户界面功能。 `CWinApp` 派生自 `CWinThread`。

## <a name="synchronization-object-classes"></a>同步对象类

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
同步对象类的基类。

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
允许访问的对象在单个进程中只有一个线程同步类。

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
同步类，一个与指定的最大同时访问的对象数之间。

[CMutex](../mfc/reference/cmutex-class.md)<br/>
一个同步类，仅允许一个线程中任意数量的进程访问的对象。

[CEvent](../mfc/reference/cevent-class.md)<br/>
当事件发生时通知应用程序同步类。

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
在线程安全类的成员函数中使用上一个同步对象锁定。

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
在线程安全类的成员函数中使用锁定的同步对象的数组中的一个或多个同步对象。

## <a name="related-classes"></a>相关的类

[CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)<br/>
分析命令行用于启动应用程序。

[CWaitCursor](../mfc/reference/cwaitcursor-class.md)<br/>
将等待光标放在屏幕上。 在长时间的操作过程中使用。

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
处理停靠控件条的状态数据持久的存储。

[CRecentFileList](../mfc/reference/crecentfilelist-class.md)<br/>
维护最近使用的 (MRU) 文件列表。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)

