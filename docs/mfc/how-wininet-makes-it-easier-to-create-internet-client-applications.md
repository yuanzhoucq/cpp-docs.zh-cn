---
title: WinInet 如何简化 Internet 客户端应用程序的创建
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
ms.openlocfilehash: 54f63da7451dfef39a33e6b437be938cb1652326
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624576"
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>WinInet 如何简化 Internet 客户端应用程序的创建

Win32 Internet 扩展（即 WinInet）提供对常见 Internet 协议（包括 gopher、FTP 和 HTTP）的访问权限。 使用 WinInet，你可以在更高的编程级别编写 Internet 客户端应用程序，而无需处理 WinSock、TCP/IP 或特定 Internet 协议的详细信息。 WinInet 为所有三个协议提供一组一致的功能，其中包含熟悉的 Win32 API 接口。 如果基础协议发生更改（例如，从 FTP 到 HTTP），则此一致性会使所需的代码更改降到最低。

Visual C++ 提供了两种使用 WinInet 的方式。 可以直接调用 Win32 Internet 函数（有关详细信息，请参阅 Windows SDK 中的 OLE 文档），也可以通过[MFC wininet 类](mfc-classes-for-creating-internet-client-applications.md)使用 WinInet。

**可以使用 WinInet 执行以下操作：**

- 下载 HTML 页面。

   HTTP 是用于将 HTML 页面从服务器传输到客户端浏览器的协议。

- 发送 FTP 请求以上载或下载文件或获取目录列表。

   典型的请求是用于下载文件的匿名登录。

- 使用 gopher 的菜单系统访问 Internet 上的资源。

   菜单项可以是多种类型，包括其他菜单、可以搜索的索引数据库、新闻组或文件。

对于所有三个协议，建立连接、向服务器发出请求，并关闭连接。

**MFC WinInet 类便于：**

- 从 HTTP、FTP 和 gopher 服务器读取信息，与从硬盘读取文件一样容易。

- 使用 HTTP、FTP 和 gopher 协议，而无需直接编程到 WinSock 或 TCP/IP。

   使用 Win32 Internet 函数的开发人员不需要熟悉 TCP/IP 或 Windows 套接字。 你仍可以使用 WinSock 和 TCP/IP 协议直接在套接字级别进行编程，但使用 MFC WinInet 类在 Internet 上访问 HTTP、FTP 和 gopher 协议更为简单。 对于许多常见操作，开发人员无需知道他们所使用的特定协议的详细信息。

您的计算机可作为客户端在 Internet 上的其他计算机上执行的许多操作可能需要很长时间。 这些操作的速度通常受网络连接速度的限制，但也可能会受到其他网络流量和操作的复杂性的影响。 例如，连接到远程 FTP 服务器要求您的计算机首先查找该服务器的名称来查找其地址。 然后，应用程序将尝试连接到该地址的服务器。 打开连接后，你的计算机和远程服务器将启动与文件传输协议的会话，然后才能实际使用连接来检索文件。

## <a name="see-also"></a>另请参阅

[Win32 Internet 扩展（WinInet）](win32-internet-extensions-wininet.md)<br/>
[MFC 如何简化 Internet 客户端应用程序的创建](how-mfc-makes-it-easier-to-create-internet-client-applications.md)
