---
title: Windows 套接字：套接字通知
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
ms.openlocfilehash: 10dbe6c0e1f486257c50efc4acf917cd9d596630
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167766"
---
# <a name="windows-sockets-socket-notifications"></a>Windows 套接字：套接字通知

本文介绍套接字类中的通知函数。 这些成员函数是一个回调函数，框架将调用该函数以通知你的套接字对象重要事件。 通知函数为：

- [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive)：通知此套接字存在缓冲区中的数据，以便通过调用[Receive](../mfc/reference/casyncsocket-class.md#receive)来检索数据。

- [OnSend](../mfc/reference/casyncsocket-class.md#onsend)：通知此套接字它现在可以通过调用[send](../mfc/reference/casyncsocket-class.md#send)发送数据。

- [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept)：通知此侦听套接字它可以通过调用[accept](../mfc/reference/casyncsocket-class.md#accept)接受挂起的连接请求。

- [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect)：通知此连接套接字其连接尝试已完成：可能成功或可能有错误。

- [OnClose](../mfc/reference/casyncsocket-class.md#onclose)：通知此套接字它所连接的套接字已关闭。

    > [!NOTE]
    >  其他通知函数为[OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata)。 此通知告知接收套接字，发送套接字具有要发送的 "带外" 数据。 带外数据是一个逻辑上独立的通道，与每对连接的流套接字相关联。 带外通道通常用于发送 "紧急" 数据。 MFC 支持带外数据。 使用类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)的高级用户可能需要使用带外通道，但不建议使用[CSocket](../mfc/reference/csocket-class.md)类的用户。 更简单的方法是创建另一个套接字用于传递此类数据。 有关带外数据的详细信息，请参阅 Windows SDK 中提供的 Windows 套接字规范。

如果从类 `CAsyncSocket`派生，则必须为应用程序所需的那些网络事件重写通知函数。 如果从类 `CSocket`派生类，则可以选择是否覆盖相关的通知函数。 你还可以使用 `CSocket` 本身，在这种情况下，通知函数默认不执行任何操作。

这些函数是可重写的回调函数。 `CAsyncSocket` 和 `CSocket` 将消息转换为通知，但必须实现通知功能的响应方式（如果你想要使用它们）。 通知函数在套接字接收到相关事件时调用，如存在要读取的数据。

MFC 调用通知函数以便在收到通知时自定义套接字的行为。 例如，你可以从 `OnReceive` 通知函数（即，在收到要读取的数据的通知）中调用 `Receive`，并调用 `Receive` 来读取它。 此方法不是必需的，但这是一个有效的方案。 作为替代方法，你可以使用通知函数跟踪进度、打印**跟踪**消息等。

可以通过重写派生套接类中的通知函数并提供实现来利用这些通知。

在操作（如接收或发送数据）期间，`CSocket` 对象将成为同步对象。 在同步状态下，任何适用于其他套接字的通知都会排队等候，当前套接字会等待它所需的通知。 （例如，在 `Receive` 调用期间，套接字需要读取通知。）套接字完成同步操作并再次变为异步后，其他套接字就可以开始接收排队的通知。

> [!NOTE]
> 在 `CSocket`中，永远不会调用 `OnConnect` 通知函数。 对于连接，你调用 `Connect`，这将在连接完成（成功或错误）时返回。 如何处理连接通知是 MFC 实现的详细信息。

有关每个通知函数的详细信息，请参阅*MFC 参考*中的类 `CAsyncSocket` 下的函数。 有关 MFC 示例的源代码和信息，请参阅[Mfc 示例](../overview/visual-cpp-samples.md#mfc-samples)。

有关详细信息，请参阅：

- [Windows 套接字：使用 CAsyncSocket 类](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows 套接字：阻止](../mfc/windows-sockets-blocking.md)

- [Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)

- [Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>另请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)
