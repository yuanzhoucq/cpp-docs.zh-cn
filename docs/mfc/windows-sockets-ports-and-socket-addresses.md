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
ms.openlocfilehash: 791bf07c927e80e65e0fda79fae8a50235bc2def
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371048"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows 套接字：端口和套接字地址

本文介绍了与 Windows 套接字一起使用的术语"端口"和"地址"。

## <a name="port"></a><a name="_core_port"></a>港口

端口标识可为其提供服务的唯一进程。 在本上下文中，端口与支持 Windows 套接字的应用程序相关联。 其理念是唯一标识每个 Windows 套接字应用程序，以便可以同时在计算机上运行多个 Windows 套接字应用程序。

某些端口保留用于公共服务，如 FTP。 除非提供此类服务，否则应避免使用这些端口。 Windows 套接字规范详细介绍了这些保留端口。 文件 WINSOCK。H 还列出了它们。

要让 Windows 套接字 DLL 为您选择可用的端口，请传递 0 作为端口值。 MFC 选择大于 1，024 小数的端口值。 您可以通过调用[CAsyncSocket：：getSockName](../mfc/reference/casyncsocket-class.md#getsockname)成员函数来检索 MFC 选择的端口值。

## <a name="socket-address"></a><a name="_core_socket_address"></a>套接字地址

每个套接字对象都与网络上的 Internet 协议 （IP） 地址相关联。 通常，地址是计算机名称，如"ftp.microsoft.com"或虚线数字，如"128.56.22.8"。

当您寻求创建套接字时，通常不需要指定自己的地址。

> [!NOTE]
> 您的计算机可能有多个网卡（或者您的应用程序可能有一天在这样的计算机上运行），每个网卡代表不同的网络。 如果是这样，您可能需要提供一个地址来指定套接字将使用的网卡。 这肯定是一个高级用法和可能的可移植性问题。

有关详细信息，请参阅：

- [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)

- [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)
