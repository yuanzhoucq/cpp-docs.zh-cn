---
title: Windows 套接字： 套接字通知 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b51bf2b562f0d4eff5b9cfef557e62f996d53470
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385575"
---
# <a name="windows-sockets-socket-notifications"></a>Windows 套接字：套接字通知
本文介绍套接字类中的通知函数。 这些成员函数是框架调用以通知你的重要事件的套接字对象的回调函数。 通知函数包括：  
  
-   [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive)： 通知此套接字，在它通过调用来检索的缓冲区中没有数据[接收](../mfc/reference/casyncsocket-class.md#receive)。  
  
-   [OnSend](../mfc/reference/casyncsocket-class.md#onsend)： 通知此套接字，它现在可通过调用来发送数据[发送](../mfc/reference/casyncsocket-class.md#send)。  
  
-   [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept)： 通知它可以通过调用接受挂起的连接请求此侦听套接字[接受](../mfc/reference/casyncsocket-class.md#accept)。  
  
-   [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect)： 通知其连接尝试完成此连接套接字： 可能成功或错误。  
  
-   [OnClose](../mfc/reference/casyncsocket-class.md#onclose)： 通知它连接到的套接字已关闭此套接字。  
  
    > [!NOTE]
    >  其他通知函数是[OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata)。 此通知告诉接收套接字的发送的套接字有要发送的"带外"数据。 带外数据是与连接的流套接字的每对关联的逻辑上独立于通道。 带外通道通常用于将"紧急"的数据发送。 MFC 支持带外数据。 高级用户使用类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)可能需要使用带外通道，但用户类[CSocket](../mfc/reference/csocket-class.md)我们建议您不要使用它。 更方便的方法是创建用于传递此类数据的第二个套接字。 有关带外数据的详细信息，请参阅 Windows SDK 中提供的 Windows 套接字规范。  
  
 如果可以从类派生`CAsyncSocket`，适用于那些网络应用程序感兴趣的事件，您必须重写通知函数。 如果从类派生一个类`CSocket`，它是你选择是否覆盖感兴趣的通知函数。 你还可以使用`CSocket`本身，在这种情况下通知函数默认为不执行任何操作。  
  
 这些函数都是可重写的回调函数。 `CAsyncSocket` 和`CSocket`转换消息通知，但你必须实现如何通知函数响应，如果你想要使用它们。 套接字通知的感兴趣，例如要读取的数据的存在的事件时，调用通知函数。  
  
 MFC 调用通知函数，以允许您会收到通知时自定义套接字的行为。 例如，你可能会调用**接收**从你`OnReceive`通知函数，即在上通知没有要读取数据，你调用**接收**读取它。 此方法不是必需的但它是一个有效的方案。 作为替代方法，你可能会使用通知函数来跟踪进度，打印**跟踪**消息，依次类推。  
  
 通过重写派生的套接字类中的通知函数，并提供实现，可以充分利用这些通知。  
  
 在接收或发送数据，如操作期间`CSocket`对象变为同步。 在同步状态中，当前的套接字等待它想的通知时，对应其他套接字任何通知将排队。 (例如，在**接收**调用，套接字想的通知，以便读取。)后套接字完成其同步操作，并再次变为异步，其他套接字可以开始接收排队的通知。  
  
> [!NOTE]
>  在`CSocket`、`OnConnect`在于： 绝不调用通知函数。 对于连接，你调用**连接**，这样就会返回完成连接后 （成功或错误）。 如何处理连接通知是 MFC 实现的详细信息。  
  
 有关每个通知函数的详细信息，请参阅下类函数`CAsyncSocket`中*MFC 参考*。 源代码和 MFC 示例的信息，请参阅[MFC 示例](../visual-cpp-samples.md)。  
  
 有关详细信息，请参见:  
  
-   [Windows 套接字：使用 CAsyncSocket 类](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows 套接字：阻止](../mfc/windows-sockets-blocking.md)  
  
-   [Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)

