---
title: 针对旧代码的多线程支持 (Visual C++)
ms.date: 08/27/2018
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
ms.openlocfilehash: 6f76ff42d2e28afe251ce234220051111736d3c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215080"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>针对旧代码的多线程支持 (Visual C++)

视觉C++对象允许同时运行多个并发的执行线程。 使用多线程处理，可以停止后台任务、管理输入的同步流、管理用户界面等。

## <a name="in-this-section"></a>本节内容

[使用 C 和 Win32 进行多线程编程](multithreading-with-c-and-win32.md)<br/>
提供对通过 Microsoft Windows 创建多线程应用程序的支持

[使用 C++ 和 MFC 进行多线程编程](multithreading-with-cpp-and-mfc.md)<br/>
描述什么是进程和线程，以及 MFC 的多线程处理方法是什么。

[多线程和区域设置](multithreading-and-locales.md)<br/>
讨论在多线程应用程序中使用 C 运行库和C++标准库的区域设置功能时所发生的问题。

## <a name="related-sections"></a>相关章节

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
表示应用程序中的执行线程。

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
描述一个纯虚类，该类提供 Win32 中的同步对象所共有的功能。

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
表示一个信号量，它是一个同步对象，允许一个或多个进程中有限数量的线程访问资源。

[CMutex](../mfc/reference/cmutex-class.md)<br/>
表示一个 mutex，是一个允许一个线程以互相排斥的方式访问一个资源的同步对象。

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
表示一个临界区，它是一个同步对象，允许一次一个线程访问资源或代码段。

[CEvent](../mfc/reference/cevent-class.md)<br/>
表示一个事件，该事件是一个允许一个线程通知另一个线程事件已经发生的同步对象。

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
表示多线程程序中用于控制对多个资源的访问的访问控制机制。

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
表示多线程程序中用于控制对一个资源的访问的访问控制机制。
