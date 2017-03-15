---
title: "多线程处理：如何使用同步类 | Microsoft Docs"
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
  - "MFC [C++], 多线程处理"
  - "多线程处理 [C++], 同步类"
  - "资源 [C++], 多线程处理"
  - "同步 [C++], 多线程处理"
  - "同步类 [C++]"
  - "线程处理 [C++], 同步"
  - "线程处理 [C++], 线程安全类设计"
  - "线程处理 [MFC], 同步类"
  - "线程处理 [MFC], 线程安全类设计"
  - "线程安全类 [C++]"
ms.assetid: f266d4c6-0454-4bda-9758-26157ef74cc5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 多线程处理：如何使用同步类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

写入多线程应用程序时，线程间的同步资源访问是一个常见问题。  两个或多个线程同时访问同一数据会导致不合需要的、不可预知的结果。  例如，一个线程可能正在更新结构的内容，而另一个线程正在读取同一结构的内容。  无法得知读取线程将会收到何种数据：旧数据、新写入的数据或两种数据都有。  MFC 提供了多个同步和同步访问类以帮助解决此问题。  本主题说明了可用的类以及如何在典型的多线程应用程序中使用它们创建线程安全类。  
  
 典型的多线程应用程序具有代表各个线程间要共享的资源的类。  正确设计的完全线程安全类不需要调用任何同步函数。  该类的任何事情都在内部处理，使您可以将精力集中于如何更好地使用类，而不是它如何会损坏。  创建完全线程安全类的有效技术是将同步类合并到资源类中。  将同步类合并到共享类是一个简单的过程。  
  
 以维护链接的帐户列表的应用程序为例。  此应用程序允许在独立的窗口中最多检查三个帐户，但是在任何特定的时间，只能更新一个帐户。  更新帐户后，通过网络将更新的数据发送到数据存档。  
  
 此示例应用程序使用所有这三种类型的同步类。  因为它一次最多允许检查三个帐户，所以它使用 [CSemaphore](../mfc/reference/csemaphore-class.md) 限制对三个视图对象的访问。  当尝试查看第四个帐户时，应用程序或者等到前三个窗口中有一个关闭，或者该尝试失败。  更新帐户时，应用程序使用 [CCriticalSection](../mfc/reference/ccriticalsection-class.md) 确保一次只更新一个帐户。  更新成功后，发出信号 [CEvent](../mfc/reference/cevent-class.md) 以释放等待该事件信号发送的线程。  此线程将新数据发送到数据存档。  
  
##  <a name="_mfc_designing_a_thread.2d.safe_class"></a> 设计线程安全类  
 若要使类完全线程安全，首先将适当的同步类作为数据成员添加到共享类中。  在前面的帐户管理示例中，将 **CSemaphore** 数据成员添加到视图类，将 `CCriticalSection` 数据成员添加到链接的列表类，将 `CEvent` 数据成员添加到数据存储类。  
  
 下一步，将同步调用添加到修改类中的数据或访问受控资源的所有成员函数中。  应该在每个函数中创建 [CSingleLock](../mfc/reference/csinglelock-class.md) 或 [CMultiLock](../mfc/reference/cmultilock-class.md) 对象，并调用该对象的 `Lock` 函数。  当锁定对象超出范围并被销毁时，该对象的析构函数调用 `Unlock` 以释放资源。  当然，如果愿意，可直接调用 `Unlock`。  
  
 用这种方式设计线程安全类使得在多线程应用程序中使用该类与使用非线程安全类一样容易，但却具有更高的安全级别。  将同步对象和同步访问权对象封装到资源的类将提供完全线程安全编程的所有优点，而不会有维护同步代码的缺点。  
  
 下面的代码示例通过使用在共享资源类和 `CSingleLock` 对象中声明的数据成员 `m_CritSection`（`CCriticalSection` 类型），对此方法进行了说明。  通过使用 `m_CritSection` 对象的地址创建 `CSingleLock` 对象，来尝试同步共享资源（从 `CWinThread` 派生）。  尝试锁定资源，一旦锁定，即完成了共享对象上的工作。  完成工作后，即调用 `Unlock` 取消锁定资源。  
  
```  
CSingleLock singleLock(&m_CritSection);  
singleLock.Lock();  
// resource locked  
//.usage of shared resource...  
  
singleLock.Unlock();  
```  
  
> [!NOTE]
>  与其他 MFC 同步类不同的是，`CCriticalSection` 没有计时锁定请求选项。  等待释放线程的时间是无限的。  
  
 此方法的缺点是类将要比没有添加同步对象的相同类慢一些。  而且，如果有一个以上的线程可能删除对象，合并方法不一定始终有效。  在这种情况下，最好维持单独同步对象。  
  
 有关确定在不同情况下使用何种同步类的信息，请参见[多线程编程：何时使用同步类](../parallel/multithreading-when-to-use-the-synchronization-classes.md)。  有关同步的更多信息，请参见 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的[同步](http://msdn.microsoft.com/library/windows/desktop/ms686353)。  有关 MFC 中的多线程支持的更多信息，请参见[使用 C\+\+ 和 MFC 进行多线程编程](../parallel/multithreading-with-cpp-and-mfc.md)。  
  
## 请参阅  
 [使用 C\+\+ 和 MFC 进行多线程编程](../parallel/multithreading-with-cpp-and-mfc.md)