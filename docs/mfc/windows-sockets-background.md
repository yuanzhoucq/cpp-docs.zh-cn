---
title: Windows 套接字：背景
ms.date: 11/04/2016
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
ms.openlocfilehash: 93342f734d1e475cbae1b7e3025c59e6e6f73284
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468024"
---
# <a name="windows-sockets-background"></a>Windows 套接字：背景

本文介绍的性质和用途的 Windows 套接字。 本文还：

- [定义术语"套接字"](#_core_definition_of_a_socket)。

- [描述的套接字句柄的数据类型](#_core_the_socket_data_type)。

- [介绍了使用套接字](#_core_uses_for_sockets)。

Windows 套接字规范定义的 Microsoft Windows 二进制文件兼容的网络编程接口。 Windows 套接字基于 UNIX 套接字实现在 Berkeley Software Distribution (BSD，版本 4.3) 从在 Berkeley 的加利福尼亚大学。 规范包括 BSD 样式套接字例程和特定于 Windows 的扩展。 使用 Windows 套接字允许应用程序以符合 Windows 套接字 API 的任何网络上通信。 在 Win32 中，Windows 套接字提供线程安全性。

许多网络软件供应商网络协议，包括传输控制协议 /internet 协议 (TCP/IP)，Xerox 网络系统 (XNS) Digital Equipment Corporation DECNet 协议，Novell Corporation Internet 下支持 Windows 套接字数据包交换/有序打包交换 (IPX/SPX) 和其他人。 虽然存在的 Windows 套接字规范定义用于 TCP/IP 的套接字抽象，但可以使用 Windows 套接字中通过提供其自己的实现 Windows 套接字的动态链接库 (DLL) 的版本符合任何网络协议。 使用 Windows 套接字编写的商业应用程序的示例包括 X Windows 服务器、 终端仿真程序和电子邮件系统。

> [!NOTE]
>  Windows 套接字的目的是抽象出底层网络，以便不需要非常了解该网络，因此你的应用程序可以在任何支持套接字的网络上运行。 因此，此文档中未讨论网络协议的详细的信息。

Microsoft 基础类库 (MFC) 通过提供两个类支持使用 Windows 套接字 API 进行编程。 这些类之一`CSocket`，提供高级别的抽象来简化您的网络通信编程。

Windows 套接字规范，Windows 套接字： 为网络计算在 Microsoft Windows，现在在 1.1 版中，打开接口的个人和公司 TCP/IP 社区中的一大组开发作为一个开放的网络标准和是使用免费提供。 套接字编程模型支持一个"通信的域"目前，使用 Internet 协议套件。 该规范是在 Windows SDK 中提供。

> [!TIP]
>  由于套接字使用 Internet 协议套件，因此它们是支持"信息高速公路。"上的 Internet 通信的应用程序的首选的路由

##  <a name="_core_definition_of_a_socket"></a> 一个套接字的定义

一个套接字是通信终结点，通过该 Windows 套接字应用程序发送或接收的数据包的网络的对象。 套接字的类型与正在运行的进程，并且它可能具有的名称。 目前，套接字通常与交换数据仅同一"通信域中，"使用 Internet 协议套件中的其他套接字。

这两种类型的套接字是双向;它们是可以同时在两个方向传递的数据流 （全双工）。

提供了两个套接字类型：

- Stream 套接字

   为没有记录边界的数据流提供 Stream 套接字： 字节流。 流保证传递并进行正确排序和不重复。

- 数据报套接字

   数据报，不能保证传递和可能不会进行序列化作为套接字支持面向记录的数据流发送或不重复。

"序列化"表示的数据包会发送顺序传递。 "无重复"意味着一次只能获取一个特定的数据包。

> [!NOTE]
>  在某些网络协议，如 XNS，流可以是面向记录的记录的流而不是字节流。 但是，更常见的 TCP/IP 协议，在流是字节流。 Windows 套接字提供独立于基础协议的抽象的级别。

有关这些类型的信息和哪种类型的套接字在哪些情况下使用，请参阅[Windows 套接字： 套接字 Stream](../mfc/windows-sockets-stream-sockets.md)并[Windows 套接字： 数据报套接字](../mfc/windows-sockets-datagram-sockets.md)。

##  <a name="_core_the_socket_data_type"></a> 套接字的数据类型

每个 MFC 套接字对象将封装 Windows 套接字对象的句柄。 此句柄的数据类型是**套接字**。 一个**套接字**句柄是类似于`HWND`窗口。 MFC 套接字类提供了封装句柄上的操作。

**套接字**数据类型 Windows SDK 中的详细信息中所述。 在下，Windows 套接字，请参阅"套接字的数据类型和错误值"。

##  <a name="_core_uses_for_sockets"></a> 套接字的用途

套接字是至少三个通信的上下文中非常有用：

- 客户端/服务器模型。

- 对等方案，例如消息传递应用程序。

- 通过让解释与函数调用消息接收应用程序进行远程过程调用 (RPC)。

> [!TIP]
>  理想情况下使用 MFC 套接字是编写两个通信端时： 在两端都使用 MFC。 本主题中，包括如何与非 MFC 应用程序，在通信时管理这种情况的详细信息请参阅[Windows 套接字： 字节排序](../mfc/windows-sockets-byte-ordering.md)。

有关详细信息，请参阅 Windows 套接字规范： **ntohs**， **ntohl**， **htons**， **htonl**。 此外，请参阅以下主题：

- [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows 套接字：使用存档的套接字的示例](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows 套接字：使用 CAsyncSocket 类](../mfc/windows-sockets-using-class-casyncsocket.md)

## <a name="see-also"></a>请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)

