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
ms.openlocfilehash: 1c4a6dc6740660d1097785578cdac355983cad18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360118"
---
# <a name="windows-sockets-background"></a>Windows 套接字：背景

本文介绍了 Windows 套接字的性质和用途。 本文还：

- [定义术语"套接字"。](#_core_definition_of_a_socket)

- [描述 SOCKET 句柄数据类型](#_core_the_socket_data_type)。

- [描述套接字的用数](#_core_uses_for_sockets)。

Windows 套接字规范为 Microsoft Windows 定义了二进制兼容的网络编程接口。 Windows 套接字基于加州大学伯克利分校的"伯克利软件分发"（BSD，版本 4.3）中的 UNIX 套接字实现。 该规范包括 BSD 样式的套接字例程和特定于 Windows 的扩展。 使用 Windows 套接字允许应用程序跨任何符合 Windows 套接字 API 的网络进行通信。 在 Win32 上，Windows 插槽提供线程安全性。

许多网络软件供应商根据网络协议支持 Windows 套接字，包括传输控制协议/互联网协议 （TCP/IP）、Xerox 网络系统 （XNS）、数字设备公司的 DECNet 协议、Novell 公司的互联网数据包交换/序列打包交换 （IPX/SPX） 等。 尽管当前 Windows 套接字规范定义了 TCP/IP 的套接字抽象，但任何网络协议都可以通过提供实现 Windows 套接字的动态链接库 （DLL） 自己的版本来符合 Windows 套接字。 使用 Windows 套接字编写的商业应用程序的示例包括 X Windows 服务器、终端仿真器和电子邮件系统。

> [!NOTE]
> Windows 套接字的目的是抽象化基础网络，这样您就不必了解该网络，因此应用程序可以在支持套接字的任何网络上运行。 因此，本文档不讨论网络协议的详细信息。

Microsoft 基础类库 （MFC） 通过提供两个类支持使用 Windows 套接字 API 进行编程。 其中一个类`CSocket`提供了高级抽象，以简化网络通信编程。

Windows 套接字规范"Windows 套接字：微软 Windows 下网络计算的开放界面"现已推出 1.1 版，由 TCP/IP 社区中的一大群个人和公司开发为开放网络标准，可免费使用。 套接字编程模型目前支持一个"通信域"，使用 Internet 协议套件。 该规范在 Windows SDK 中可用。

> [!TIP]
> 由于套接字使用 Internet 协议套件，因此它们是支持"信息高速公路"上 Internet 通信的应用程序的首选路由。

## <a name="definition-of-a-socket"></a><a name="_core_definition_of_a_socket"></a>套接字的定义

套接字是通信终结点 ， Windows 套接字应用程序通过网络发送或接收数据包的对象。 套接字具有类型，并且与正在运行的进程相关联，并且可能具有名称。 目前，套接字通常仅与同一"通信域"中的其他套接字交换数据，后者使用 Internet 协议套件。

这两种套接字都是双向的;它们是可同时双向通信的数据流（全双工）。

有两种套接字类型可用：

- 流套接字

   流套接字提供没有记录边界的数据流：字节流。 保证流被传递，并正确排序和未重复。

- 数据报套接字

   Datagram 套接字支持不保证传递的面向记录的数据流，并且可能无法按已发送或未重复的顺序排序。

"排序"表示数据包按发送的顺序传递。 "未重复"表示您只能获取一次特定数据包。

> [!NOTE]
> 在某些网络协议（如 XNS ）可以面向记录，作为记录流而不是字节流。 但是，在更常见的 TCP / IP 协议是字节流。 Windows 套接字提供独立于基础协议的抽象级别。

有关这些类型的以及要在哪些情况下使用哪种套接字的信息，请参阅[Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)和[Windows 套接字：Datagram 套接字](../mfc/windows-sockets-datagram-sockets.md)。

## <a name="the-socket-data-type"></a><a name="_core_the_socket_data_type"></a>SOCKET 数据类型

每个 MFC 套接字对象都封装到 Windows 套接字对象的句柄。 此句柄的数据类型是**SOCKET**。 **SOCKET**句柄类似于窗口的。 `HWND` MFC 套接字类提供对封装句柄的操作。

在 Windows SDK 中详细介绍了**SOCKET**数据类型。 请参阅 Windows 套接字下的"套接字数据类型和错误值"。

## <a name="uses-for-sockets"></a><a name="_core_uses_for_sockets"></a>用于套接字

套接字至少在三个通信上下文中非常有用：

- 客户端/服务器模型。

- 对等方案，如消息传递应用程序。

- 通过让接收应用程序将消息解释为函数调用来进行远程过程调用 （RPC）。

> [!TIP]
> 使用 MFC 套接字的理想情况是，当您写入通信的两端时：在两端使用 MFC。 有关本主题的详细信息（包括如何在与非 MFC 应用程序通信时如何管理案例），请参阅[Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)。

有关详细信息，请参阅 Windows 套接字规范：ntohs、ntohl、Htons、htonl 。 **ntohs** **ntohl** **htons** **htonl** 此外，请参阅以下主题：

- [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows 套接字：使用存档的套接字的示例](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

## <a name="see-also"></a>另请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)
