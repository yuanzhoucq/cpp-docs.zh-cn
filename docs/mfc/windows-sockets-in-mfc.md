---
title: "MFC 中的 Windows 套接字 | Microsoft Docs"
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
  - "MFC [C++], Windows 套接字"
  - "套接字 [C++], MFC"
  - "套接字 [C++], 编程模型"
  - "Windows 套接字 [C++], MFC 支持"
  - "Windows 套接字 [C++], 编程模型"
  - "WINSOCK.DLL"
  - "WSOCK32.DLL"
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# MFC 中的 Windows 套接字
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  MFC 支持 Windows 套接字 1，但不支持。[Windows 套接字 2](http://msdn.microsoft.com/library/windows/desktop/ms740673) Windows 套接字首先 2 随 Windows 98 和版本是随 Windows 2000。  
  
 MFC 提供 Windows 套接字编写提供的网络通信。程序这两种模型，实现在两 MFC 类。  本文介绍这些模型和更多详细信息 MFC 套接字支持。  套接字“”是通信终结点：应用程序与在网络中其他 Windows 套接字应用程序通信的对象。  
  
 有关 Windows 套接字的信息，包括套接字概念的说明，请参见 [Windows 套接字：背景](../mfc/windows-sockets-background.md)。  
  
##  <a name="_core_sockets_programming_models"></a> 编程模型的套接字  
 编程模型的两 MFC Windows 套接字。下面的类支持：  
  
-   `CAsyncSocket`  
  
     此类封装 Windows 套接字 API。  [CAsyncSocket](../mfc/reference/casyncsocket-class.md) 用于知道网络编程并需要编程灵活性直接调用套接字 API 的程序员，而且还需要回调函数使用网络事件通知的。  除了打包套接字外以面向对象形式用于 C\+\+，此类提供的唯一的其他转换某些抽象套接字关联的窗口消息为回调。  有关更多信息，请参见 [Windows 套接字：套接字通知](../mfc/windows-sockets-socket-notifications.md)。  
  
-   `CSocket`  
  
     此类，从 `CAsyncSocket`派生，与套接字提供工作的高级别抽象通过 MFC 对象。[CArchive](../mfc/reference/carchive-class.md) 使用 MFC 的文件序列化协议，将存档的套接字非常相似。  这比 `CAsyncSocket` 模型使得使用。  [CSocket](../mfc/reference/csocket-class.md) 继承封装 Windows 套接字 API 从 `CAsyncSocket` 的大多数成员函数；必须使用某些函数和理解通常编程的套接字。  但是，`CSocket` 管理通信的许多特性需要执行您自己使用原始的 API 或 `CAsyncSocket`类。  最重要的是，`CSocket` 提供锁定 \(与 Windows 消息后台\)，指向 `CArchive`的同步操作是重要的。  
  
 创建和使用 `CSocket` 和 `CAsyncSocket` 对象在 [Windows 套接字：将存档的套接字](../mfc/windows-sockets-using-sockets-with-archives.md) [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)和说明。  
  
##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a> Windows 套接字 \(DLLs\)  
 Microsoft Windows 操作系统提供 Windows 套接字动态链接库 \(DLL\) \(DLL\)。  Visual C\+\+ 提供的相应头文件和库和 Windows 套接字规范。  
  
> [!NOTE]
>  在 Windows NT 和 Windows 2000 下，16 位应用程序的" Windows 套接字支持基于 WINSOCK.DLL。  对于 32 位应用程序，支持在 WSO CK32 .DLL。  提供的 API 与相同，但版本 32 位有参数。扩展为 32 位。  在 Win32 下，提供线程安全。  
  
 有关 Windows 窗体的更多信息，请参见 。  
  
-   [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)  
  
-   [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows 套接字：操作顺序](../mfc/windows-sockets-sequence-of-operations.md)  
  
-   [Windows 套接字：使用存档的套接字的示例](../mfc/windows-sockets-example-of-sockets-using-archives.md)  
  
-   [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows 套接字：套接字通知](../mfc/windows-sockets-socket-notifications.md)  
  
-   [Windows 套接字：阻止](../mfc/windows-sockets-blocking.md)  
  
-   [Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)  
  
-   [Windows 套接字：端口和套接字地址](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
## 请参阅  
 [Windows 套接字](../mfc/windows-sockets.md)