---
title: 多线程处理： 如何使用 MFC 同步类
ms.date: 08/27/2018
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
ms.openlocfilehash: 0f8304c3b45f87dadc2317de95a0b30b54baffa0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604160"
---
# <a name="multithreading-how-to-use-the-mfc-synchronization-classes"></a>多线程处理： 如何使用 MFC 同步类

编写多线程应用程序时，同步在线程之间的资源访问权限是一个常见问题。 具有两个或多个线程同时访问相同的数据可能会导致不必要和不可预知的结果。 例如，一个线程可能正在更新结构的内容而另一个线程正在读取相同的结构的内容。 不知道哪些数据读取线程将收到： 旧的数据、 新写入的数据，或可能是两者的混合。 MFC 提供了多个同步和同步访问类，以帮助解决此问题。 本主题介绍可用的类以及如何使用它们在典型的多线程应用程序创建线程安全类。

典型的多线程应用程序有一个类，表示要在线程之间共享的资源。 正确设计的完全线程安全类不需要您可以调用任意同步函数。 所有内容到类，从而可以专注于如何充分利用类，关于如何可能会遭到损坏不在内部处理。 创建完全线程安全类的有效方法是同步类合并到的资源类。 将同步类合并到共享的类是一个简单的过程。

例如，需要维护帐户的链接的列表的应用程序。 此应用程序，最多三个帐户要检查其在单独的窗口，但只有一个可以更新在任何特定的时间。 当更新帐户时，更新后的数据是通过网络发送到数据存档。

此示例应用程序使用所有三种类型的同步类。 因为它允许最多三个帐户一次检查，它使用[CSemaphore](../mfc/reference/csemaphore-class.md)来限制对三个视图对象的访问。 当尝试查看的第四个帐户时，或者等到其中一个前三个窗口关闭或发生故障的应用程序。 当更新帐户时，应用程序使用[CCriticalSection](../mfc/reference/ccriticalsection-class.md)来确保只有一个帐户更新一次。 更新成功后，它指示[CEvent](../mfc/reference/cevent-class.md)，以释放一个线程等待事件收到信号。 此线程将新数据发送到数据存档。

##  <a name="_mfc_designing_a_thread.2d.safe_class"></a> 设计一个线程安全类

若要使一个类完全线程安全，首先将适当的产品类为数据成员添加到共享类中。 在前面的帐户管理示例`CSemaphore`数据成员将添加到视图类`CCriticalSection`数据成员将添加到链接列表类，和一个`CEvent`数据成员将添加到数据存储类。

接下来，添加到所有成员函数中修改的类中的数据或访问受控的资源的同步调用。 在每个函数中，您应创建[CSingleLock](../mfc/reference/csinglelock-class.md)或[CMultiLock](../mfc/reference/cmultilock-class.md)对象并调用该对象的`Lock`函数。 当锁定对象超出范围，并被销毁后时，该对象的析构函数调用`Unlock`以释放资源。 当然，您可以调用`Unlock`直接的前提。

设计您的线程安全类以这种方式使得它可以作为方便地为非线程安全类，但具有更高级别的安全性的多线程应用中使用。 其中的同步对象和同步访问对象封装到资源的类提供了完全线程安全编程而无需维护同步代码的缺点的所有权益。

下面的代码示例演示此方法通过使用数据成员`m_CritSection`(类型的`CCriticalSection`)，在共享的资源类中声明和一个`CSingleLock`对象。 共享资源的同步 (派生自`CWinThread`) 通过创建尝试`CSingleLock`对象使用的地址`m_CritSection`对象。 尝试锁定该资源，而且，一旦锁定，共享对象上完成工作。 完成工作后，资源是通过调用未锁定`Unlock`。

```
CSingleLock singleLock(&m_CritSection);
singleLock.Lock();
// resource locked
//.usage of shared resource...

singleLock.Unlock();
```

> [!NOTE]
> `CCriticalSection`其他 MFC 同步与类不同，没有定时的锁定请求的选项。 线程变为可用的等待时间是无限的。

此方法的缺点是，该类将比同一类稍慢而无需添加的同步对象。 此外，如果有多个线程可能会删除该对象的机会，合并的方法不始终有效。 在这种情况下，它是更好的做法维护单独的同步对象。

有关确定要在不同情况下使用哪些同步类的信息，请参阅[多线程处理： 何时使用同步类](multithreading-when-to-use-the-synchronization-classes.md)。 有关同步的详细信息，请参阅[同步](/windows/desktop/Sync/synchronization)Windows SDK 中。 有关在 MFC 中的多线程支持的详细信息，请参阅[使用 c + + 和 MFC 多线程处理](multithreading-with-cpp-and-mfc.md)。

## <a name="see-also"></a>请参阅

[使用 C++ 和 MFC 进行多线程编程](multithreading-with-cpp-and-mfc.md)