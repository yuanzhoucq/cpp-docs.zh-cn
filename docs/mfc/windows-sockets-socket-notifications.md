---
title: Windows 套接字：套接字通知
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
ms.openlocfilehash: e49001e9693872d23162284df49f128097e68784
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476474"
---
# <a name="windows-sockets-socket-notifications"></a>Windows 套接字：套接字通知

本文介绍在套接字类中的通知函数。 这些成员函数都是框架调用以通知套接字对象的重要事件的回调函数。 通知函数包括：

- [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive)： 向此套接字通知，以便通过调用检索缓冲区中没有数据[接收](../mfc/reference/casyncsocket-class.md#receive)。

- [OnSend](../mfc/reference/casyncsocket-class.md#onsend)： 通知，它现在可通过调用来发送数据的此套接字[发送](../mfc/reference/casyncsocket-class.md#send)。

- [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept)： 通知它可以通过调用接受挂起的连接请求此侦听套接字[接受](../mfc/reference/casyncsocket-class.md#accept)。

- [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect)： 通知其连接尝试完成此连接套接字： 可能成功或错误。

- [OnClose](../mfc/reference/casyncsocket-class.md#onclose)： 通知套接字连接到已关闭此套接字。

    > [!NOTE]
    >  其他通知函数是[OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata)。 此通知告诉接收套接字发送的套接字有要发送的"带外"数据。 带外数据是与每对已连接的流套接字关联的逻辑上独立于通道。 带外通道通常用于发送"紧急"的数据。 MFC 支持带外数据。 高级用户使用的类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)可能需要使用带外通道，但类的用户[CSocket](../mfc/reference/csocket-class.md)我们建议您不要使用它。 更简单的方法是创建用于传递此类数据的第二个套接字。 有关带外数据的详细信息，请参阅 Windows SDK 中提供的 Windows 套接字规范。

如果派生类`CAsyncSocket`，适用于那些网络到你的应用程序感兴趣的事件，您必须重写通知函数。 如果从类派生一个类`CSocket`，可以选择是否要重写感兴趣的通知函数。 此外可以使用`CSocket`本身，这种情况下通知函数默认情况下不执行任何操作。

这些函数都是可重写的回调函数。 `CAsyncSocket` 和`CSocket`转换消息通知，但你必须实现如何通知函数响应，如果你想要使用它们。 通知函数称为在套接字通知感兴趣，例如存在要读取数据的事件的时间。

MFC 调用通知函数，以便你可以在收到通知时自定义套接字的行为。 例如，可能会调用`Receive`从你`OnReceive`通知函数，即在正在通知要读取的数据，则调用`Receive`读取它的权限。 此方法不是必需的但它是一个有效的方案。 或者，你可能会使用通知函数来跟踪进度，打印**跟踪**消息和等等。

可以通过重写派生的套接字类中的通知函数并提供的实现来充分利用这些通知。

在接收或发送数据，如操作期间`CSocket`对象将成为同步。 在同步状态中，对应其他套接字的任何通知将排队等待它想要的通知的当前套接字时。 (例如，在为`Receive`调用时，套接字想要读取的通知。)一旦套接字完成其同步操作，并将再次变为异步，其他套接字可以开始接收排队的通知。

> [!NOTE]
>  在中`CSocket`，则`OnConnect`通知函数从未被调用。 对于连接，您调用`Connect`，这将返回完成连接后 （成功或错误）。 如何处理连接通知是 MFC 实现详细信息。

有关每个通知函数的详细信息，请参阅类下的函数`CAsyncSocket`中*MFC 参考*。 源代码和 MFC 示例有关的信息，请参阅[MFC 示例](../visual-cpp-samples.md)。

有关详细信息，请参见:

- [Windows 套接字：使用 CAsyncSocket 类](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows 套接字：阻止](../mfc/windows-sockets-blocking.md)

- [Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)

- [Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)

