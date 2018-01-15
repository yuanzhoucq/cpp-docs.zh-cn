---
title: "多线程处理： 何时使用同步类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- threading [MFC], synchronization classes
- resources [C++], multithreading
- synchronization classes [C++]
- synchronization [C++], multithreading
- controlled resource access [C++]
- synchronization access classes [C++]
- threading [C++], synchronization
- multithreading [C++], synchronization classes
ms.assetid: 4914f54e-68ac-438f-93c9-c013455a657e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 38437983552dfdf2cf6708ec5fd067e06387ea5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-when-to-use-the-synchronization-classes"></a>多线程处理：何时使用同步类
MFC 提供的多线程的类分为两类： 同步对象 ([CSyncObject](../mfc/reference/csyncobject-class.md)， [CSemaphore](../mfc/reference/csemaphore-class.md)， [CMutex](../mfc/reference/cmutex-class.md)， [CCriticalSection](../mfc/reference/ccriticalsection-class.md)，和[CEvent](../mfc/reference/cevent-class.md)) 和同步访问对象 ([CMultiLock](../mfc/reference/cmultilock-class.md)和[CSingleLock](../mfc/reference/csinglelock-class.md))。  
  
 必须控制对资源的访问，以确保资源的完整性时，使用同步类。 同步访问类用于获取对这些受控资源的访问权限。 本主题介绍何时使用每个类。  
  
 若要确定应使用哪个同步类，请询问问题以下一的系列：  
  
1.  应用程序没有要等待的时间才能访问资源发生某些事件 （例如，数据必须先从接收通信端口可以写入文件之前）？  
  
     如果是，使用`CEvent`。  
  
2.  可以多个线程中相同的应用程序访问此资源一次 （例如，你的应用程序允许带有同一文档视图的最多五个窗口）？  
  
     如果是，使用`CSemaphore`。  
  
3.  多个应用程序是否可以使用此资源 （例如，资源 DLL 中是）？  
  
     如果是，使用`CMutex`。  
  
     如果不是，使用`CCriticalSection`。  
  
 **CSyncObject**永远不会直接使用。 它是其他四个同步类的基类。  
  
## <a name="example-1-using-three-synchronization-classes"></a>示例 1： 使用三个同步类  
 例如，需要的应用程序维护帐户的链接的列表。 此应用程序允许最多三个帐户必须在单独的窗口，检查，但只有一个可以在任何特定时间更新。 当更新帐户时，更新后的数据是通过网络发送到的数据存档。  
  
 此示例应用程序使用同步类的所有三种类型。 因为它允许最多三个帐户必须一次检查，它使用`CSemaphore`访问权限限制为三个视图对象。 当尝试查看的第四个帐户时，应用程序，或者等到前三个 windows 之一关闭或者该尝试失败。 当更新帐户时，应用程序使用`CCriticalSection`以确保只有一个帐户更新一次。 更新才能成功后，它发出信号`CEvent`，以释放线程等待事件接收信号。 此线程将新数据发送到数据存档。  
  
## <a name="example-2-using-synchronization-access-classes"></a>示例 2： 使用同步访问类  
 选择要使用的同步访问类甚至更简单。 如果访问单个的受控的资源仅关注你的应用程序，使用`CSingleLock`。 如果它需要为任意数量的受控的资源的访问，使用`CMultiLock`。 在示例 1，`CSingleLock`会已使用，因为每种情况下只有一个资源需要在任何特定时间。  
  
 有关如何使用同步类的信息，请参阅[多线程处理： 如何使用同步类](../parallel/multithreading-how-to-use-the-synchronization-classes.md)。 有关同步的信息，请参阅[同步](http://msdn.microsoft.com/library/windows/desktop/ms686353)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。 有关 MFC 中的多线程处理支持的信息，请参阅[与 c + + 和 MFC 的多线程处理](../parallel/multithreading-with-cpp-and-mfc.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用 C++ 和 MFC 进行多线程编程](../parallel/multithreading-with-cpp-and-mfc.md)