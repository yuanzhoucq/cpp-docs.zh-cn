---
title: 多线程处理：如何使用 MFC 同步类
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
ms.openlocfilehash: 26a059e378edb92f5ff7f4e788ded90678e0c129
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511869"
---
# <a name="multithreading-how-to-use-the-mfc-synchronization-classes"></a>多线程处理：如何使用 MFC 同步类

在编写多线程应用程序时, 同步线程间的资源访问是一个常见问题。 如果两个或多个线程同时访问相同的数据, 则可能导致意外的和不可预知的结果。 例如, 一个线程可能会更新结构的内容, 而另一个线程正在读取相同结构的内容。 未知的是读取线程将接收的数据: 旧数据、新写入的数据, 或者两者的组合。 MFC 提供了许多同步和同步访问类来帮助解决此问题。 本主题介绍了可用的类, 以及如何使用它们在典型的多线程应用程序中创建线程安全的类。

典型的多线程应用程序有一个类, 该类表示要在线程之间共享的资源。 正确设计的完全线程安全类不要求您调用任何同步函数。 所有内容都是在内部处理的, 使你能够专注于如何最好地使用类, 而不是将其损坏的方式。 创建完全线程安全类的一种有效方法是将同步类合并到资源类中。 将同步类合并到共享类中的过程非常简单。

例如, 使用维护链接列表的应用程序。 此应用程序允许在单独的窗口中检查最多三个帐户, 但在任何特定时间只能更新一个帐户。 帐户更新后, 更新的数据将通过网络发送到数据存档。

此示例应用程序使用所有三种类型的同步类。 由于它允许一次最多检查三个帐户, 因此它使用[CSemaphore](../mfc/reference/csemaphore-class.md)来限制对三个视图对象的访问。 当尝试查看第四个帐户时, 应用程序会等待, 直到前三个窗口中有一个关闭或失败。 帐户更新后, 应用程序将使用[CCriticalSection](../mfc/reference/ccriticalsection-class.md)来确保一次只更新一个帐户。 更新成功后, 它会发出信号, 指示[CEvent](../mfc/reference/cevent-class.md), 它释放等待事件发出信号的线程。 此线程将新数据发送到数据存档。

##  <a name="_mfc_designing_a_thread.2d.safe_class"></a>设计线程安全类

若要使类完全是线程安全的, 请首先将相应的同步类作为数据成员添加到共享类中。 在以前的帐户管理示例中, `CSemaphore`数据成员将添加到视图类`CCriticalSection` , 将数据成员添加到链接`CEvent`列表类, 然后将数据成员添加到数据存储类中。

接下来, 添加对修改类中的数据或访问受控资源的所有成员函数的同步调用。 在每个函数中, 应创建[CSingleLock](../mfc/reference/csinglelock-class.md)或[CMultiLock](../mfc/reference/cmultilock-class.md)对象, 并调用该对象的`Lock`函数。 当锁对象超出范围并被销毁时, 对象的析构函数会为您`Unlock`调用, 同时释放资源。 当然, 您可以根据需要`Unlock`直接调用。

以这种方式设计线程安全类, 可以在多线程应用程序中轻松地将其用作非线程安全类, 但具有更高的安全级别。 将同步对象和同步访问对象封装到资源的类中可提供完全线程安全编程的所有好处, 而不会保留同步代码的缺点。

下面的代码示例通过使用在`m_CritSection` `CSingleLock`共享资源类和对象中声明的数据`CCriticalSection`成员 (类型为), 演示了此方法。 使用对象地址`CSingleLock`创建对象, 尝试同步共享`CWinThread`资源 (派生自)。 `m_CritSection` 尝试锁定资源, 并在获取时对共享对象执行工作。 工作完成后, 将通过调用来`Unlock`解锁资源。

```
CSingleLock singleLock(&m_CritSection);
singleLock.Lock();
// resource locked
//.usage of shared resource...

singleLock.Unlock();
```

> [!NOTE]
> `CCriticalSection`与其他 MFC 同步类不同, 不具有定时锁请求选项。 线程进入空闲状态的等待时间是无限的。

此方法的缺点是, 类将略微慢于没有添加同步对象的相同类。 此外, 如果有可能有多个线程可能会删除该对象, 则合并方法可能并不总是有效。 在这种情况下, 最好维护单独的同步对象。

有关确定在不同情况下要使用哪些同步类的信息, [请参阅多线程处理:使用同步类](multithreading-when-to-use-the-synchronization-classes.md)的时间。 有关同步的详细信息, 请参阅 Windows SDK 中的[同步](/windows/win32/Sync/synchronization)。 有关 MFC 中的多线程支持的详细信息, 请参阅[带和 mfc 的C++多线程](multithreading-with-cpp-and-mfc.md)处理。

## <a name="see-also"></a>请参阅

[使用 C++ 和 MFC 进行多线程编程](multithreading-with-cpp-and-mfc.md)
