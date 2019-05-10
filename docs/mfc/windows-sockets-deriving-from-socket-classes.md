---
title: Windows 套接字：从套接字类派生
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from socket classes
- Windows Sockets [MFC], deriving from socket classes
- sockets [MFC], deriving from socket classes
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
ms.openlocfilehash: 12ab66cfd9212cd79752e2f6359b857194c6428c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385253"
---
# <a name="windows-sockets-deriving-from-socket-classes"></a>Windows 套接字：从套接字类派生

本文介绍了一些您可以通过从一个套接字类派生您自己的类来获得的功能。

可以从派生您自己的套接字类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)或[CSocket](../mfc/reference/csocket-class.md)添加您自己的功能。 具体而言，这些类提供多个可以重写虚拟成员函数。 这些函数包括[OnReceive](../mfc/reference/casyncsocket-class.md#onreceive)， [OnSend](../mfc/reference/casyncsocket-class.md#onsend)， [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept)， [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect)，并[OnClose](../mfc/reference/casyncsocket-class.md#onclose)。 您可以利用它们提供的网络事件发生时通知你派生的套接字类中重写函数。 框架调用以通知你重要的套接字的事件，如接收数据，在可以开始阅读这些通知回调函数。 有关通知函数的详细信息，请参阅[Windows 套接字：套接字通知](../mfc/windows-sockets-socket-notifications.md)。

此外，类`CSocket`提供[OnMessagePending](../mfc/reference/csocket-class.md#onmessagepending)成员函数 (一种高级可重写)。 MFC 套接字发送基于 Windows 的消息时调用此函数。 您可以重写`OnMessagePending`从 Windows 中查找特定消息并对其做出响应。

默认版本`OnMessagePending`类中提供`CSocket`等待阻止调用完成时将检查消息队列中的 WM_PAINT 消息。 它将分派提高显示质量的绘制消息。 除了添加有用的功能，这说明了一种方法可能会重写函数自己。 作为另一个示例，请考虑使用`OnMessagePending`以下任务。 假设您在等待网络事务完成时显示无模式对话框。 对话框中包含一个取消按钮，用户可用于取消正在阻塞的事务花费很长时间。 你`OnMessagePending`重写可能会发送到此无模式对话框相关的消息。

在你`OnMessagePending`重写，返回**TRUE**或通过调用基类版本返回`OnMessagePending`。 如果执行你仍然想要完成的工作，请调用基类版本。

有关详细信息，请参见:

- [Windows 套接字：结合使用套接字和存档](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 套接字：阻止](../mfc/windows-sockets-blocking.md)

- [Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)

- [Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)
