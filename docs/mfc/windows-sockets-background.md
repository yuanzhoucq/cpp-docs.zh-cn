---
title: Windows 套接字： 背景 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record-oriented data [MFC]
- e-mail [MFC]
- Internet Protocol Suite
- mail [MFC]
- communications [MFC], domain
- Windows Sockets [MFC], stream sockets
- mail [MFC], programming for
- sockets [MFC], stream sockets
- datagram sockets [MFC]
- SOCKET handle
- data types [MFC], socket
- e-mail [MFC], programming for
- X Window servers
- sequenced data flow
- stream sockets [MFC]
ms.assetid: f60d4ed2-bf23-4a0e-98d2-fee77e8473dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fda86bbbeb49bcb253348ed02abef4fb8d4cff9c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="windows-sockets-background"></a>Windows 套接字：背景
此文章介绍了的性质和用途的 Windows 套接字。 文章还：  
  
-   [定义的术语"套接字"](#_core_definition_of_a_socket)。  
  
-   [描述的套接字句柄数据类型](#_core_the_socket_data_type)。  
  
-   [描述用于套接字](#_core_uses_for_sockets)。  
  
 Windows 套接字规范定义适用于 Microsoft Windows 的二进制兼容网络编程接口。 Windows 套接字基于 UNIX 套接字实现在 Berkeley Software Distribution (BSD，版本 4.3) 从在 Berkeley 的加利福尼亚大学。 规范包括 BSD 样式套接字例程和特定于 Windows 的扩展。 使用 Windows 套接字允许你的应用程序能够通过 Windows 套接字 API 符合任何网络通信。 在 Win32 中，Windows 套接字提供对线程安全。  
  
 许多网络软件供应商下包括传输控制协议 /internet 协议 (TCP/IP)，Xerox 网络系统 (XNS) 数字设备 Corporation DECNet 协议，Novell Corporation Internet 的网络协议支持 Windows 套接字数据包交换/有序打包交换 (IPX/SPX) 和其他人。 尽管存在的 Windows 套接字规范定义 TCP/IP 套接字抽象，则任何网络协议可以通过提供其自己的实现 Windows 套接字的动态链接库 (DLL) 的版本符合 Windows 套接字。 使用 Windows 套接字编写的商业应用程序的示例包括 X Windows 服务器、 终端仿真程序和电子邮件系统。  
  
> [!NOTE]
>  Windows 套接字的目的是抽象出来基础网络，以便无需非常了解该网络，因此你的应用程序可以在任何支持套接字的网络上运行。 因此，本文档不讨论网络协议的详细的信息。  
  
 Microsoft 基础类库 (MFC) 通过提供两个类来支持使用 Windows 套接字 API 编程。 这些类之一`CSocket`，提供高级别的抽象，来简化你的网络通信编程。  
  
 Windows 套接字规范，Windows 套接字： 网络计算在 Microsoft windows，现在在 1.1 版中，打开接口由个人和公司 TCP/IP 社区中的一大组作为一种开放网络标准进行开发和是自由地可供使用。 套接字当前编程模型支持一个"通信域"，使用 Internet 协议套件。 该规范是在 Windows SDK 中可用。  
  
> [!TIP]
>  由于套接字使用 Internet 协议套件，它们是用于支持"信息高速公路。"上的 Internet 通信的应用程序的首选的路由  
  
##  <a name="_core_definition_of_a_socket"></a> 套接字定义  
 套接字是通信终结点-通过该 Windows 套接字应用程序发送，或通过网络接收数据包的对象。 套接字的类型并处于与正在运行的进程，并且它可能具有名称。 目前，套接字通常交换仅与其他"通信在同一域中，"使用 Internet 协议套件的套接字的数据。  
  
 这两种类型的套接字是双向;它们是可以同时在两个方向传达的数据流 （全双工）。  
  
 提供了两个套接字类型：  
  
-   流套接字  
  
     为没有记录边界的数据流提供流套接字： 字节流。 流保证传递并进行正确排序和不重复。  
  
-   数据报套接字  
  
     数据报套接字支持面向记录的数据流，此数据不能保证传递并不可能为按顺序发送或不重复。  
  
 "排序"意味着，数据包将被传输发送的顺序。 "无重复"，则意味着仅一次获取一个特定的数据包。  
  
> [!NOTE]
>  在某些网络协议，如 XNS，在将流是面向为个记录流，而不是流的字节的记录。 但是，更常见的 TCP/IP 协议下, 流是字节流。 Windows 套接字提供一个独立于基础协议的抽象级别。  
  
 有关这些类型信息和哪种类型的套接字在哪些情况下使用，请参阅[Windows 套接字： 流套接字](../mfc/windows-sockets-stream-sockets.md)和[Windows 套接字： 数据报套接字](../mfc/windows-sockets-datagram-sockets.md)。  
  
##  <a name="_core_the_socket_data_type"></a> 套接字数据类型  
 每个 MFC 套接字对象封装 Windows 套接字对象的句柄。 此句柄的数据类型是**套接字**。 A**套接字**句柄是类似于`HWND`窗口。 MFC 套接字类提供封装句柄上的操作。  
  
 **套接字**数据类型在 Windows SDK 中的详细信息中所述。 在 Windows 套接字下，请参阅"套接字数据类型和错误值"。  
  
##  <a name="_core_uses_for_sockets"></a> 套接字的用途  
 套接字是在至少三个通信的上下文中非常有用：  
  
-   客户端/服务器模型。  
  
-   对等方案，例如消息传送应用程序。  
  
-   通过让解释作为函数调用消息接收应用程序进行远程过程调用 (RPC)。  
  
> [!TIP]
>  你正在编写两个通信端时，理想情况下使用 MFC 套接字： 在两端都使用 MFC。 本主题中，包括如何在与非 MFC 应用程序通信时管理这种情况的详细信息请参阅[Windows 套接字： 字节排序](../mfc/windows-sockets-byte-ordering.md)。  
  
 有关详细信息，请参阅 Windows 套接字规范： **ntohs**， **ntohl**， **htons**， **htonl**。 另请参阅以下主题：  
  
-   [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows 套接字：使用存档的套接字的示例](../mfc/windows-sockets-example-of-sockets-using-archives.md)  
  
-   [Windows 套接字：使用 CAsyncSocket 类](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)

