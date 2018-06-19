---
title: 多线程处理： 如何使用同步类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], multithreading
- threading [MFC], synchronization classes
- resources [C++], multithreading
- thread-safe classes [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], thread-safe class design
- threading [C++], synchronization
- multithreading [C++], synchronization classes
- threading [C++], thread-safe class design
ms.assetid: f266d4c6-0454-4bda-9758-26157ef74cc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49b0737a794216c4899b280bc049a1cdc0fe0948
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689020"
---
# <a name="multithreading-how-to-use-the-synchronization-classes"></a>多线程处理：如何使用同步类
编写多线程应用程序时，同步线程之间的资源访问权限是一个常见问题。 具有两个或多个线程同时访问相同的数据可能会导致不必要和不可预知的结果。 例如，一个线程可能正在更新的结构的内容时另一个线程正在读取的内容相同的结构。 它是未知读取线程将会收到哪些数据： 旧的数据、 新写入的数据，或可能两者的混合。 MFC 提供了大量的同步和同步访问类，以帮助解决此问题。 本主题说明可用的类以及如何使用它们在典型的多线程应用程序创建线程安全类。  
  
 典型的多线程应用程序具有表示在线程间共享的资源的类。 正确设计的完全的线程安全类不需要您才能调用任何同步函数。 所有内容到类，使您能够集中精力如何最有效地使用类，关于如何可能会损坏不在内部处理。 一种用于创建完全的线程安全类的有效方法是同步类合并到的资源类。 将同步类合并到共享的类是一个简单的过程。  
  
 例如，需要的应用程序维护帐户的链接的列表。 此应用程序允许最多三个帐户必须在单独的窗口，检查，但只有一个可以在任何特定时间更新。 当更新帐户时，更新后的数据是通过网络发送到的数据存档。  
  
 此示例应用程序使用同步类的所有三种类型。 因为它允许最多三个帐户必须一次检查，它使用[CSemaphore](../mfc/reference/csemaphore-class.md)访问权限限制为三个视图对象。 当尝试查看的第四个帐户时，应用程序，或者等到前三个 windows 之一关闭或者该尝试失败。 当更新帐户时，应用程序使用[CCriticalSection](../mfc/reference/ccriticalsection-class.md)以确保只有一个帐户更新一次。 更新才能成功后，它发出信号[CEvent](../mfc/reference/cevent-class.md)，以释放线程等待事件接收信号。 此线程将新数据发送到数据存档。  
  
##  <a name="_mfc_designing_a_thread.2d.safe_class"></a> 设计的线程安全类  
 若要使类完全的线程安全，首先将适当的同步类作为数据成员添加到共享的类中。 在以前的帐户管理示例中， **CSemaphore**数据成员将添加到视图类中，`CCriticalSection`数据成员将添加到链接列表类，和一个`CEvent`数据成员将添加到数据存储类。  
  
 接下来，添加对所有成员函数的修改的类中的数据或访问受控的资源的同步调用。 在每个函数中，你应创建[CSingleLock](../mfc/reference/csinglelock-class.md)或[CMultiLock](../mfc/reference/cmultilock-class.md)对象并调用该对象的`Lock`函数。 当锁定对象超出范围，并被销毁时，该对象的析构函数调用`Unlock`以释放资源。 当然，你可以调用`Unlock`直接如果你想。  
  
 设计你的线程安全类，以这种方式使它可以用于多线程应用程序作为轻松地为非线程安全类，但具有更高级别的安全。 到资源的类中封装的同步对象和同步访问对象提供完全的线程安全编程而无需维护同步代码的缺点的所有好处。  
  
 下面的代码示例演示此方法使用的数据成员， `m_CritSection` (类型的`CCriticalSection`)，在共享的资源类中声明和`CSingleLock`对象。 共享资源的同步 (派生自`CWinThread`) 尝试通过创建`CSingleLock`对象使用的地址`m_CritSection`对象。 尝试锁定资源，并且一旦锁定，共享的对象上完成工作。 完成工作后，资源是通过调用解锁`Unlock`。  
  
```  
CSingleLock singleLock(&m_CritSection);  
singleLock.Lock();  
// resource locked  
//.usage of shared resource...  
  
singleLock.Unlock();  
```  
  
> [!NOTE]
>  `CCriticalSection`其他 MFC 同步与类不同，没有已超时的锁请求的选项。 线程变为可用，等待一段时间为无限期。  
  
 这种方法的缺点是类，将不添加的同步对象的情况下会比同一类稍慢。 此外，如果有机会在多个线程可能会删除对象，合并的方法不始终有效。 在此情况下，它是更好的做法维护单独的同步对象。  
  
 有关确定何种同步类在不同的情况下使用的信息，请参阅[多线程处理： 何时使用同步类](../parallel/multithreading-when-to-use-the-synchronization-classes.md)。 有关同步的详细信息，请参阅[同步](http://msdn.microsoft.com/library/windows/desktop/ms686353)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。 有关 MFC 中的多线程处理支持的详细信息，请参阅[与 c + + 和 MFC 的多线程处理](../parallel/multithreading-with-cpp-and-mfc.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用 C++ 和 MFC 进行多线程编程](../parallel/multithreading-with-cpp-and-mfc.md)