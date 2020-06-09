---
title: 应用程序和线程支持类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.support
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
ms.openlocfilehash: 7e64cc50a121f457b7e32e0ed549db2fa9950843
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619437"
---
# <a name="application-and-thread-support-classes"></a>应用程序和线程支持类

每个应用程序都有一个且只有一个应用程序对象;此对象协调正在运行的程序中的其他对象，派生自 `CWinApp` 。

Microsoft 基础类（MFC）库支持在一个应用程序中执行多个线程。 所有应用程序都必须至少有一个线程;对象使用的线程 `CWinApp` 是此主线程。

`CWinThread`封装操作系统的部分线程功能。 为了使使用多个线程更加简单，MFC 还提供了同步对象类，以提供到 Win32 同步对象的 c + + 接口。

## <a name="application-and-thread-classes"></a>应用程序和线程类

[CWinApp](reference/cwinapp-class.md)<br/>
封装代码以初始化、运行和终止应用程序。 您将从此类派生您的应用程序对象。

[CWinThread](reference/cwinthread-class.md)<br/>
所有线程的基类。 `CWinThread`如果你的线程执行用户界面函数，则直接使用或从派生类。 `CWinApp` 派生自 `CWinThread`。

## <a name="synchronization-object-classes"></a>同步对象类

[CSyncObject](reference/csyncobject-class.md)<br/>
同步对象类的基类。

[CCriticalSection](reference/ccriticalsection-class.md)<br/>
一个同步类，只允许一个进程中的一个线程访问对象。

[CSemaphore](reference/csemaphore-class.md)<br/>
一个同步类，该同步类允许同时访问一个对象和一个指定的最大数量。

[CMutex](reference/cmutex-class.md)<br/>
一个同步类，只允许任意数量的进程中的一个线程访问对象。

[CEvent](reference/cevent-class.md)<br/>
一个同步类，在事件发生时通知应用程序。

[CSingleLock](reference/csinglelock-class.md)<br/>
在线程安全类的成员函数中用于锁定一个同步对象。

[CMultiLock](reference/cmultilock-class.md)<br/>
在线程安全类的成员函数中用于锁定同步对象数组中的一个或多个同步对象。

## <a name="related-classes"></a>相关类

[CCommandLineInfo](reference/ccommandlineinfo-class.md)<br/>
分析您的程序启动时所用的命令行。

[CWaitCursor](reference/cwaitcursor-class.md)<br/>
将等待光标置于屏幕上。 在漫长的操作过程中使用。

[CDockState](reference/cdockstate-class.md)<br/>
处理控件条的停靠状态数据的持久存储。

[CRecentFileList](reference/crecentfilelist-class.md)<br/>
维护最近使用的（MRU）文件列表。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
