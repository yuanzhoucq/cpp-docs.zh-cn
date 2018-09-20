---
title: Wininet 如何更轻松地创建 Internet 客户端应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 356027e151dcc94891b9c4043e4f1af8b2f0b947
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430909"
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>WinInet 如何简化 Internet 客户端应用程序的创建

Win32 Internet 扩展或 WinInet，提供对常用的 Internet 协议，包括 gopher、 FTP 和 HTTP 访问。 使用 WinInet，可以编写无需处理与 WinSock、 TCP/IP 或特定的 Internet 协议的详细信息的编程中，较高级别上的 Internet 客户端应用程序。 WinInet 为所有三个协议的熟悉的 Win32 API 界面提供一组一致的函数。 这种一致性降至最低，使基础协议发生变化 （例如，从 HTTP 到 FTP) 时所需的代码更改。

Visual c + + 提供了两种方法供你使用 WinInet。 可以直接调用 Win32 Internet 函数 （请参阅 Windows SDK for 的详细信息中的 OLE 文档），也可以使用通过 WinInet [MFC WinInet 类](../mfc/mfc-classes-for-creating-internet-client-applications.md)。

**您可以使用 WinInet 到：**

- 下载 HTML 页面。

     HTTP 是用来将 HTML 页面从服务器传输到客户端浏览器的协议。

- 发送 FTP 请求，以将上传或下载文件或获取目录列表。

     一个典型的请求是匿名登录，下载的文件。

- 用于访问 Internet 上的资源使用 gopher 的菜单系统。

     菜单项可以是几种类型，包括其他菜单、 带索引的数据库，您可以搜索、 新闻组或文件。

为所有三个协议建立的连接、 向服务器发送请求和关闭连接。

**MFC WinInet 类可以轻松快速地：**

- 作为从硬盘读取文件轻松地读取来自 HTTP、 FTP 和 gopher 服务器的信息。

- 使用 HTTP、 FTP 和 gopher 协议而无需直接向 WinSock 或 TCP/IP 的编程。

     使用 Win32 Internet 函数的开发人员不需要熟悉 TCP/IP 或 Windows 套接字。 您可以仍编程在套接字级别中，直接使用 WinSock 和 TCP/IP 协议，但更加方便地通过 Internet 使用 MFC WinInet 类访问 HTTP、 FTP 和 gopher 协议。 对于许多常见操作，开发人员不需要知道他们正在使用的特定协议的详细信息。

可以通过您的计算机到 Internet 上的其他计算机的客户端的许多操作可能需要长时间。 这些操作的速度通常会受到速度的网络连接，但它们可能也会受到其他网络流量和操作的复杂性。 例如，连接到远程 FTP 服务器上，需要您的计算机首次查找要查找其地址，该服务器的名称。 然后，你的应用程序将尝试连接到该地址的服务器。 一旦打开连接时，您的计算机和远程服务器将启动与文件传输协议的会话才能实际使用该连接以检索文件。

## <a name="see-also"></a>请参阅

[Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[MFC 如何简化 Internet 客户端应用程序的创建](../mfc/how-mfc-makes-it-easier-to-create-internet-client-applications.md)

