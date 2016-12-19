---
title: "Windows 套接字：套接字通知 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "通知, 套接字"
  - "套接字 [C++], 通知"
  - "Windows 套接字 [C++], 通知"
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows 套接字：套接字通知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在本文套接字类说明通知函数。  这些成员函数是通知重要事件套接字的框架对象调用的回调函数。  通知功能：  
  
-   [OnReceive](../Topic/CAsyncSocket::OnReceive.md):此通知套接字具有缓冲区中的数据。可以检索通过调用 [Receive](../Topic/CAsyncSocket::Receive.md)。  
  
-   [OnSend](../Topic/CAsyncSocket::OnSend.md):此通知套接字它可以通过 [发送](../Topic/CAsyncSocket::Send.md)调用现在发送数据。  
  
-   [OnAccept](../Topic/CAsyncSocket::OnAccept.md):此通知侦听的套接字它能接受暂停连接请求通过调用 [接受](../Topic/CAsyncSocket::Accept.md)。  
  
-   [OnConnect](../Topic/CAsyncSocket::OnConnect.md):请注意此连接的套接字连接其尝试完成：\(或许成功或错误。  
  
-   [OnClose](../Topic/CAsyncSocket::OnClose.md):通知其连接到此的套接字套接字关闭。  
  
    > [!NOTE]
    >  附加通知函数是 [OnOutOfBandData](../Topic/CAsyncSocket::OnOutOfBandData.md)。  此通知调用套接接收 Word 发送的套接字将“发送带外”的数据。  带外数据是一个或多个逻辑无关联合访问的。每对连接流的套接字。  带外通道通常用于发送“紧急”数据。  MFC支持处理带外数据。  高级用户与 [CAsyncSocket](../mfc/reference/casyncsocket-class.md) 类一起使用可能需要使用带外通道，但用户从 [CSocket](../mfc/reference/csocket-class.md) 类的使用方式不鼓励使用。  简单的方法会创建传递这样的数据第二套接字。  有关带外数据的更多信息，请参见 Windows 套接字规范，[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中可用。  
  
 如果从 `CAsyncSocket`类进行派生，必须重写这些网络事件通知相关函数到应用程序。  如果从类 `CSocket`派生类，它是否选择重写通知相关的函数。  然后通知函数没有。默认执行情况下，您可以使用 `CSocket`。  
  
 这些函数是可重写的回调函数。  `CAsyncSocket` 和 `CSocket` 将消息到通知，但是，您必须实现函数通知如何响应，则要使用它们。  通知函数，在调用套接字时通知感兴趣的事件时，例如要读取的数据出现。  
  
 则得到通知时，MFC 通知调用套接字函数可自定义的行为。  例如，您可能从 `OnReceive` 调用的 **Receive** 通知函数，即，在通知具有读的数据，则调用 **Receive** 读取它。  此方法不是必需的，但是，它是有效的方案。  或者，您可能使用该通知函数跟踪进度，print **TRACE** 消息，依此类推。  
  
 通过重写在派生的类通知函数和套接字中提供实现利用这些通知。  
  
 在一操作时 \(接收或发送数据，`CSocket` 对象变为同步。  在同步状态期间，对其他套接字意味着的所有通知队列，当所需的套接字当前等待通知时。在调用 **Receive** 期间，\(例如套接字，需要通知，读取。\)一旦套接字完成其同步操作并再次变为异步的，则另套接字开始接收队列的通知。  
  
> [!NOTE]
>  在 `CSocket`中，`OnConnect` 通知函数从不调用。  对于连接，您调用 **连接**，将返回，连接完成时 \(成功或假\)。  连接通知的处理方式是 MFC 实现详细信息。  
  
 有关每个通知函数的信息，请参见函数在" *MFC 参考"中的*类 `CAsyncSocket` 下。  有关源代码以及有关 MFC 示例，请参见 [MFC 示例](../top/visual-cpp-samples.md)。  
  
 有关详细信息，请参阅：  
  
-   [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows 套接字：阻止](../mfc/windows-sockets-blocking.md)  
  
-   [Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)  
  
## 请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)