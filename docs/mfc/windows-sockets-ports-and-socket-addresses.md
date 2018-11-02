---
title: Windows 套接字：端口和套接字地址
ms.date: 11/04/2016
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
ms.openlocfilehash: d132001cb792877e3d476508a6a5bb456dfb5987
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631352"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows 套接字：端口和套接字地址

此文章介绍了术语"port"和"地址"作为与 Windows 套接字一起使用。

##  <a name="_core_port"></a> 端口

一个端口标识可以为其提供服务的唯一进程。 在出现的上下文中，端口是与支持 Windows 套接字的应用程序相关联。 其理念是唯一地标识每个 Windows 套接字应用程序，因此，可以有多个 Windows 套接字应用程序的计算机上同时运行。

某些端口被保留的公共服务，例如 FTP。 应避免使用这些端口，除非你要提供这种服务。 Windows 套接字规范详细介绍这些保留的端口。 WINSOCK 文件。H 还列出了它们。

若要让 Windows 套接字 DLL 为你的选择可用端口，传递的端口值为 0。 MFC 选择大于十进制数 1024 的端口值。 可以检索 MFC 通过调用所选的端口值[CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname)成员函数。

##  <a name="_core_socket_address"></a> 套接字地址

每个套接字对象都与在网络上的 Internet 协议 (IP) 地址相关联。 通常情况下，地址是一个计算机名称，例如"ftp.microsoft.com"或以点分隔的数字，如"128.56.22.8"。

当你拖动以创建套接字时，通常不需要指定你自己的地址。

> [!NOTE]
>  它可能是你的计算机具有多个网卡 （或者某一天这样的计算机上运行你的应用程序，可能），每个元素表示不同的网络。 如果是这样，您可能需要提供一个地址以指定将使用套接字的网络卡。 这是某些高级使用情况和可能的可移植性问题。

有关详细信息，请参见:

- [Windows 套接字：使用 CAsyncSocket 类](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)

- [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)

