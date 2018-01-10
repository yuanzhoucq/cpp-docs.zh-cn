---
title: "如何 WinInet 便于创建 Internet 客户端应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9c79404f296df09afb177930897064b8455217d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>WinInet 如何简化 Internet 客户端应用程序的创建
Win32 Internet 扩展或 WinInet，提供对常见的 Internet 协议，包括 gopher、 FTP 和 HTTP 访问。 使用 WinInet，你可以无需处理 WinSock、 TCP/IP 或特定 Internet 协议的详细信息来编写 Internet 客户端应用程序在编程中，较高级别。 WinInet 对于所有三个协议，使用熟悉的 Win32 API 界面提供一致的函数集。 这种一致性最大程度减少需要进行如果基础协议 （例如，从 HTTP 到 FTP) 更改的代码更改。  
  
 Visual c + + 提供两种方法供你使用 WinInet。 你可以直接调用 Win32 Internet 函数 （请参阅适用于详细信息的 Windows SDK 中的 OLE 文档） 或者你可以使用通过 WinInet [MFC WinInet 类](../mfc/mfc-classes-for-creating-internet-client-applications.md)。  
  
 **你可以使用 WinInet 到：**  
  
-   下载 HTML 页面。  
  
     HTTP 是用来将 HTML 页从服务器传输到客户端浏览器的协议。  
  
-   发送 FTP 请求要上载或下载文件或获取目录列表。  
  
     一个典型的请求是匿名登录，要下载的文件。  
  
-   用于访问 Internet 上的资源使用 gopher 的菜单系统。  
  
     菜单项可以是几种类型，包括其他菜单，您可以搜索的索引的数据库、 新闻组或文件。  
  
 对于所有三个协议，建立连接，服务器上，向发出请求并关闭连接。  
  
 **MFC WinInet 类更加容易：**  
  
-   一样轻松地从硬盘读取文件读取从 HTTP、 FTP 和 gopher 服务器的信息。  
  
-   使用 HTTP、 FTP 和 gopher 协议，而无需直接向 WinSock 或 TCP/IP 的编程。  
  
     使用 Win32 Internet 函数的开发人员不需要以熟悉 TCP/IP 或 Windows 套接字。 你可以仍编程套接字级别中，使用 WinSock 和 TCP/IP 协议直接，但是它是更容易地通过 Internet 使用 MFC WinInet 类来访问 HTTP、 FTP 和 gopher 协议。 对于许多常见的操作，开发人员不需要了解他们正在使用的特定协议的详细信息。  
  
 可以由你的计算机到 Internet 上的其他计算机的客户端的许多操作可能需要长时间。 这些操作的速度通常都会受限于您的网络连接的速度，但它们可能还会影响其他网络流量和操作的复杂性。 例如，连接到远程 FTP 服务器上，需要你的计算机首先查找该服务器以查找其地址的名称。 然后，你的应用程序将尝试连接到该地址上的服务器。 连接打开后，您的计算机和远程服务器将发起与文件传输协议的对话之前您实际上可以使用连接以检索文件。  
  
## <a name="see-also"></a>请参阅  
 [Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [MFC 如何简化 Internet 客户端应用程序的创建](../mfc/how-mfc-makes-it-easier-to-create-internet-client-applications.md)

