---
title: 针对旧代码 （Visual c + +） 的多线程处理支持 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b1b301186036460acc07a526267503da8b97678
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "43132097"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>针对旧代码的多线程支持 (Visual C++)
Visual c + + 可以具有多个并发线程的同时运行的执行。 使用多线程处理，可以派生出后台任务、 管理同时发生的输入流、 管理用户界面，以及更多内容。  
  
## <a name="in-this-section"></a>本节内容  
 
[使用 C 和 Win32 进行多线程编程](multithreading-with-c-and-win32.md)  
为与 Microsoft Windows 中创建多线程应用程序提供支持  
  
[使用 C++ 和 MFC 进行多线程编程](multithreading-with-cpp-and-mfc.md)  
描述什么是进程和线程以及 MFC 的方法的多线程处理是。  
  
[多线程和区域设置](multithreading-and-locales.md)  
讨论如何使用 C 运行时库和 c + + 标准库中的多线程应用程序的区域设置功能时出现的问题。  
  
## <a name="related-sections"></a>相关章节  
 
[CWinThread](../mfc/reference/cwinthread-class.md)  
表示应用程序中的执行线程。  
  
[CSyncObject](../mfc/reference/csyncobject-class.md)  
描述一个纯虚拟类，提供 Win32 中的同步对象所共有的功能。  
  
[CSemaphore](../mfc/reference/csemaphore-class.md)  
表示一个信号量，这是一个允许有限的数量的线程中一个或多个进程访问资源的同步对象。  
  
[CMutex](../mfc/reference/cmutex-class.md)  
表示一个 mutex，是一个允许一个线程以互相排斥的方式访问一个资源的同步对象。  
  
[CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
表示一个临界区，这是一个每次访问资源或代码段的允许一个线程的同步对象。  
  
[CEvent](../mfc/reference/cevent-class.md)  
表示一个事件，这是一个允许一个线程通知事件已发生的另一个线程的同步对象。  
  
[CMultiLock](../mfc/reference/cmultilock-class.md)  
表示多线程程序中用于控制对多个资源的访问的访问控制机制。  
  
[CSingleLock](../mfc/reference/csinglelock-class.md)  
表示多线程程序中用于控制对一个资源的访问的访问控制机制。  