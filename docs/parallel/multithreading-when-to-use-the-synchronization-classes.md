---
title: 多线程处理：何时使用 MFC 同步类
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
ms.openlocfilehash: cb68487e036093ce4718c39c18c9d1e75afe0f7c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511995"
---
# <a name="multithreading-when-to-use-the-mfc-synchronization-classes"></a>多线程处理：何时使用 MFC 同步类

随 MFC 一起提供的多线程类分为两类: 同步对象 ([CSyncObject](../mfc/reference/csyncobject-class.md)、 [CSemaphore](../mfc/reference/csemaphore-class.md)、 [CMutex](../mfc/reference/cmutex-class.md)、 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)和[CEvent](../mfc/reference/cevent-class.md)) 和同步访问对象 ([CMultiLock](../mfc/reference/cmultilock-class.md)和[CSingleLock](../mfc/reference/csinglelock-class.md))。

当必须控制对资源的访问以确保资源的完整性时, 将使用同步类。 同步访问类用于获取对这些受控资源的访问权限。 本主题介绍何时使用每个类。

若要确定应该使用哪个同步类, 请询问以下问题:

1. 应用程序必须等待发生某些事情才能访问资源 (例如, 在将数据写入文件之前必须从通信端口接收数据)？

   如果是, 请`CEvent`使用。

2. 同一应用程序中的多个线程是否可以一次访问此资源 (例如, 您的应用程序允许在同一文档中使用最多5个具有视图的窗口)？

   如果是, 请`CSemaphore`使用。

3. 多个应用程序是否可以使用此资源 (例如, 资源在 DLL 中)？

   如果是, 请`CMutex`使用。

   如果不是, `CCriticalSection`则使用。

`CSyncObject`永远不会直接使用。 它是其他四个同步类的基类。

## <a name="example-1-using-three-synchronization-classes"></a>示例 1：使用三个同步类

例如, 使用维护链接列表的应用程序。 此应用程序允许在单独的窗口中检查最多三个帐户, 但在任何特定时间只能更新一个帐户。 帐户更新后, 更新的数据将通过网络发送到数据存档。

此示例应用程序使用所有三种类型的同步类。 由于它允许一次最多查看三个帐户, 因此它将使用`CSemaphore`限制对三个视图对象的访问。 当尝试查看第四个帐户时, 应用程序会等待, 直到前三个窗口中有一个关闭或失败。 在更新帐户时, 应用程序将使用`CCriticalSection`确保一次只更新一个帐户。 更新成功后, 将发出信号`CEvent`, 以释放等待事件发出信号的线程。 此线程将新数据发送到数据存档。

## <a name="example-2-using-synchronization-access-classes"></a>示例 2：使用同步访问类

选择要使用的同步访问类更为简单。 如果你的应用程序与仅访问单个受控资源相关, 请`CSingleLock`使用。 如果需要访问大量受控资源中的任何一个, 请使用`CMultiLock`。 在示例1中`CSingleLock` , 会使用, 因为在每种情况下, 在任何特定时间都只需要一个资源。

有关如何使用同步类的信息, 请参见[多线程处理:如何使用同步类](multithreading-how-to-use-the-synchronization-classes.md)。 有关同步的详细信息, 请参阅 Windows SDK 中的[同步](/windows/win32/Sync/synchronization)。 有关 MFC 中的多线程支持的信息, 请参阅[带和 mfc 的C++多线程](multithreading-with-cpp-and-mfc.md)处理。

## <a name="see-also"></a>请参阅

[使用 C++ 和 MFC 进行多线程编程](multithreading-with-cpp-and-mfc.md)
