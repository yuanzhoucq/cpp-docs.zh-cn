---
title: "Windows 套接字：从套接字类派生 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "派生类, 从套接字类"
  - "套接字 [C++], 从套接字类派生"
  - "Windows 套接字 [C++], 从套接字类派生"
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows 套接字：从套接字类派生
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文描述了可以通过从某套接字类派生自己的类来获取某些功能。  
  
 您可以从 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)或[CSocket](../mfc/reference/csocket-class.md) 派生自己的类来添加自定义的功能。  具体说来，这些类提供大量可以重写的虚成员函数。  这些函数包括 [OnReceive](../Topic/CAsyncSocket::OnReceive.md)，[OnSend](../Topic/CAsyncSocket::OnSend.md)，[OnAccept](../Topic/CAsyncSocket::OnAccept.md)，[OnConnect](../Topic/CAsyncSocket::OnConnect.md)和[OnClose](../Topic/CAsyncSocket::OnClose.md)。  您可以重写在派生的套接字类的函数，利用它们提供的网络事件发生的通知。  框架调用这些通知回调函数通知重要套接字事件，例如可以开始阅读接收的数据。  有关通知函数的更多信息，请参见 [Windows 套接字：套接字通知](../mfc/windows-sockets-socket-notifications.md)。  
  
 此外，`CSocket` 类提供成员函数 [OnMessagePending](../Topic/CSocket::OnMessagePending.md) \(高级可重写\)。  当套接字发送 Windows 消息时，MFC 调用此函数。  可以重写 `OnMessagePending` ,查找从窗口的特定信息和响应这些事件。  
  
 当等待锁时调用完成时，`CSocket`提供的`OnMessagePending` 的默认版本检查 `WM_PAINT` 消息的消息队列。  分配绘制消息以提高显示质量。  除执行一些有用的操作以外，这也说明了一种可以重写函数的方式。  请考虑使用以下任务`OnMessagePending` 作为另一个示例。  当等待网络事务完成时，假定显示无模式对话框中。  对话框包含用户可用来取消阻塞事务的取消按钮。  `OnMessagePending` 的重写可能发送与此无模式对话框相关的消息。  
  
 在 `OnMessagePending` 重写中，返回 **TRUE** 或返回从 `OnMessagePending`的基类版本的调用。  如果执行仍需执行的工作，请调用的基类版本。  
  
 有关详细信息，请参阅：  
  
-   [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows 套接字：阻止](../mfc/windows-sockets-blocking.md)  
  
-   [Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)  
  
## 请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)