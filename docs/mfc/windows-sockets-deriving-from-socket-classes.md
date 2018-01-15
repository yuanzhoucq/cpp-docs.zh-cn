---
title: "Windows 套接字： 从套接字类派生 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- derived classes [MFC], from socket classes
- Windows Sockets [MFC], deriving from socket classes
- sockets [MFC], deriving from socket classes
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 63f8b8f735b62c1cbfedd50320bf65cec5905632
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-deriving-from-socket-classes"></a>Windows 套接字：从套接字类派生
本文介绍了一些你可以通过从一个套接字类派生您自己的类来获得的功能。  
  
 你可以从派生您自己的套接字类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)或[CSocket](../mfc/reference/csocket-class.md)添加你自己的功能。 具体而言，这些类提供大量可以重写虚拟成员函数。 这些功能包括[OnReceive](../mfc/reference/casyncsocket-class.md#onreceive)， [OnSend](../mfc/reference/casyncsocket-class.md#onsend)， [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept)， [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect)，和[OnClose](../mfc/reference/casyncsocket-class.md#onclose)。 您可以利用它们提供网络事件发生时通知你派生的套接字类中重写函数。 框架调用以通知你重要的套接字事件，如收到的数据在可以开始阅读这些通知回调函数。 有关通知函数的详细信息，请参阅[Windows 套接字： 套接字通知](../mfc/windows-sockets-socket-notifications.md)。  
  
 此外，类`CSocket`提供[OnMessagePending](../mfc/reference/csocket-class.md#onmessagepending)成员函数 (一个高级可重写)。 MFC 套接字发送基于 Windows 的消息时调用此函数。 您可以重写`OnMessagePending`以从 Windows 查找特定的消息并对其进行响应。  
  
 默认版本`OnMessagePending`类中提供`CSocket`检查消息队列中的`WM_PAINT`等待阻塞调用完成时的消息。 它将调度绘画消息以提高显示质量。 除了执行一些有用的任务，此演示一种方法可能会重写函数自己。 作为另一个示例，请考虑使用`OnMessagePending`以下任务。 假设在等待网络事务完成时显示无模式对话框。 对话框中包含用户可以使用来取消正在阻塞的事务花费很长时间的取消按钮。 你`OnMessagePending`重写可能会发送到此无模式对话框中相关的消息。  
  
 在你`OnMessagePending`重写时，请返回**TRUE**或到基类版本的调用返回`OnMessagePending`。 如果它执行你仍然想要完成的工作，则调用基类版本。  
  
 有关详细信息，请参见:  
  
-   [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows 套接字：使用 CAsyncSocket 类](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows 套接字：阻止](../mfc/windows-sockets-blocking.md)  
  
-   [Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)

