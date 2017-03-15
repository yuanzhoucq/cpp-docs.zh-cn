---
title: "Windows 套接字：阻止 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "阻止模式套接字"
  - "套接字 [C++], 不同 Windows 平台上的行为"
  - "套接字 [C++], 阻止模式"
  - "Windows 套接字 [C++], 阻止模式"
  - "Windows 套接字 [C++], Windows 平台"
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Windows 套接字：阻止
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文和两指南手册演示 Windows Sockets 编程的一些问题。  本文包含锁。  文章中介绍的其他问题：[Windows Sockets：字节顺序](../mfc/windows-sockets-byte-ordering.md) 和 [Windows Sockets：转换字符串](../mfc/windows-sockets-converting-strings.md)。  
  
 如果使用或派生自类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，将需要管理这些问题。  如果使用或派生自类[CSocket](../mfc/reference/csocket-class.md)，MFC 为您管理这些。  
  
## 阻塞  
 套接字可以在“锁定模式”或“非阻止性模式”中。套接字的函数在锁定 \(或同步\) 模式中不返回直到它们可以完成它们的操作。  这会阻止调用是因为该函数调用的套接字无法执行任何操作\) 阻止 \- 该调用返回。  为 **Receive** 成员函数的调用，如，可能需要一个随机长时间完成，它在等待发送的应用程序发送 \(这是，如果您使用 `CSocket`，或用于锁的 `CAsyncSocket` \)。  如果 `CAsyncSocket` 对象处于非阻碍模式（异步操作），调用立即返回，当前错误代码可检索 [获得最后一个错误](../Topic/CAsyncSocket::GetLastError.md) 成员的函数，它是 **WSAEWOULDBLOCK**，由于模式指示调用将会阻塞位置不立即返回。\(`CSocket` 不返回 **WSAEWOULDBLOCK**。  该类为您管理锁。\)  
  
 套接字行为在 32 位和 64 位操作系统下 \(如 Windows 95 或 Windows 98\) 对比在 16 位操作系统下 \(如 Windows 3.1\)将有所不同。  与 16 位操作系统不同，在 32 位和 64 位操作系统使用抢先多任务并提供多线程处理。  在 32 位和 64 位操作系统下，在单独的辅助线程中放置套接字。  应用程序中在线程的套接字可以阻止，而不会干扰其他活动，在阻塞上也不会花费计算时间。  有关多线程编程的信息，请参见知识库文章 [多线程处理](../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
> [!NOTE]
>  在多线程应用，可以使用 `CSocket` 的锁定特性简化编程，而不影响的用户界面响应速度。  通过在主线程处理用户交互以及在替换线程处理`CSocket` 进程，可以分隔这些逻辑操作。  在非多线程应用程序中，必须结合这两种活动并将它们作为单个线程处理，通常意味着使用 `CAsyncSocket`，因此可以处理通信请求按需或重写 `CSocket::OnMessagePending` 处理用户操作，在长期同步活动期间。  
  
 余下讨论为面向 16 位操作系统的程序员：  
  
 通常，如果您使用 `CAsyncSocket`，应避免使用锁定操作而是用异步操作。  例如，在异步操作中，从在调用 **Receive**后接收 **WSAEWOULDBLOCK** 错误代码的点处，直到 `OnReceive` 成员函数调用通知您可以再次阅读。  异步调用通过调用套接字的相应通知回调函数调用，例如 [OnReceive](../Topic/CAsyncSocket::OnReceive.md)。  
  
 在 Windows 下，阻止调用视为错误约定。  默认情况下， [CAsyncSocket](../mfc/reference/casyncsocket-class.md) 支持异步调用，必须使用回调通知管理锁。  另一方面，[CSocket](../mfc/reference/csocket-class.md)类是同步的。  它正在发送 Windows 消息和管理您的锁定。  
  
 有关阻塞的更多信息，请参见 Windows Sockets 规范。  有关" on "函数的更多信息，请参见 [Windows Sockets：套接字通知](../mfc/windows-sockets-socket-notifications.md) 和 [Windows Sockets：派生自套接字类](../mfc/windows-sockets-deriving-from-socket-classes.md)。  
  
 有关详细信息，请参阅：  
  
-   [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows 套接字：背景](../mfc/windows-sockets-background.md)  
  
-   [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)  
  
## 请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)   
 [CAsyncSocket::OnSend](../Topic/CAsyncSocket::OnSend.md)