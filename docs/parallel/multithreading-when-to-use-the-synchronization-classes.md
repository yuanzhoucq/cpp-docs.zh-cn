---
title: 多线程处理：何时使用同步类
ms.date: 08/27/2018
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
ms.openlocfilehash: 72cf5310704c1ae959cc012146a03dd32cff4068
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284367"
---
# <a name="multithreading-when-to-use-the-mfc-synchronization-classes"></a>多线程处理：何时使用同步类

MFC 提供的多线程的类分为两类： 同步对象 ([CSyncObject](../mfc/reference/csyncobject-class.md)， [CSemaphore](../mfc/reference/csemaphore-class.md)， [CMutex](../mfc/reference/cmutex-class.md)， [CCriticalSection](../mfc/reference/ccriticalsection-class.md)，并[CEvent](../mfc/reference/cevent-class.md)) 和同步访问对象 ([CMultiLock](../mfc/reference/cmultilock-class.md)并[CSingleLock](../mfc/reference/csinglelock-class.md))。

当必须控制对资源的访问以确保资源的完整性时，使用同步类。 同步访问类用于获取对这些受控资源的访问权限。 本主题介绍何时使用每个类。

若要确定应使用哪个同步类，询问以下一系列问题：

1. 应用程序没有等待某个操作发生之前其可以访问的资源 （例如，数据必须从接收通信端口可以写入文件之前）？

   如果是，使用`CEvent`。

2. 可以多个线程中相同的应用程序访问此资源中一次 （例如，你的应用程序允许最多五个 windows 与同一文档视图）？

   如果是，使用`CSemaphore`。

3. 多个应用程序可以使用此资源 （例如，资源 DLL 中是）？

   如果是，使用`CMutex`。

   如果不是，使用`CCriticalSection`。

`CSyncObject` 永远不会直接使用。 它是其他四个同步类的基类。

## <a name="example-1-using-three-synchronization-classes"></a>示例 1：使用三个同步类

例如，需要维护帐户的链接的列表的应用程序。 此应用程序，最多三个帐户要检查其在单独的窗口，但只有一个可以更新在任何特定的时间。 当更新帐户时，更新后的数据是通过网络发送到数据存档。

此示例应用程序使用所有三种类型的同步类。 因为它允许最多三个帐户一次检查，它使用`CSemaphore`来限制对三个视图对象的访问。 当尝试查看的第四个帐户时，或者等到其中一个前三个窗口关闭或发生故障的应用程序。 当更新帐户时，应用程序使用`CCriticalSection`来确保只有一个帐户更新一次。 更新成功后，它将信号通知`CEvent`，以释放一个线程等待事件收到信号。 此线程将新数据发送到数据存档。

## <a name="example-2-using-synchronization-access-classes"></a>示例 2：使用同步访问类

选择要使用的同步访问类更简单。 如果你的应用程序与访问单个的受控的资源仅而言，使用`CSingleLock`。 如果它需要访问多个受控任何的资源一个，请使用`CMultiLock`。 示例 1 中，`CSingleLock`应使用，因为每种情况下在任何特定时间需要一个资源。

有关如何使用同步类的信息，请参阅[多线程处理：如何使用同步类](multithreading-how-to-use-the-synchronization-classes.md)。 有关同步的信息，请参阅[同步](/windows/desktop/Sync/synchronization)Windows SDK 中。 有关在 MFC 中的多线程处理支持信息，请参阅[使用 c + + 和 MFC 多线程处理](multithreading-with-cpp-and-mfc.md)。

## <a name="see-also"></a>请参阅

[使用 C++ 和 MFC 进行多线程编程](multithreading-with-cpp-and-mfc.md)
