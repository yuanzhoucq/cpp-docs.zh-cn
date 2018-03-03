---
title: "应用程序设计选择 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- design
- application design [MFC], design goals
- application design [MFC], Internet applications
- Internet applications [MFC], designing applications
- Internet [MFC], vs. intranets
- applications [MFC], Internet
- server applications [MFC], vs. client applications on Internet
- client applications [MFC], vs. server applications on Internet
ms.assetid: 9b96172c-b4d4-4c69-bfb2-226ce0de6d08
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4b78c4c086b40f786d86411c99279245704a48a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="application-design-choices"></a>应用程序设计选择
此文章介绍了一些用于 Internet 编程时要考虑的设计问题。  
  
 本文中涵盖的主题包括：  
  
-   [Intranet 与 Internet](#_core_intranet_versus_internet)  
  
-   [客户端或服务器应用程序](#_core_client_or_server_application)  
  
-   [](#_core_the_web_page)  
  
-   [浏览器或独立的应用程序](#_core_browser_or_standalone)  
  
-   [在 Internet 上的 COM](#_core_com_on_the_internet)  
  
-   [客户端数据下载服务](#_core_client_data_download_services)  
  
 如果你已准备好开始编写你的程序现在，请参阅[编写 MFC 应用程序](../mfc/writing-mfc-applications.md)。  
  
##  <a name="_core_intranet_versus_internet"></a>Intranet 与 Internet  
 许多应用程序在 Internet 上运行，并使用浏览器和 Internet 访问权限的任何人都可以访问。 企业还将实现 intranet，也不能使用 TCP/IP 协议的公司范围内网络 Web 浏览器。 企业内部网提供源轻松升级，中央以便公司范围内的信息。 它们可以使用为升级软件，用于传送发放调查并、 客户支持和信息传递。 下表比较了 Internet 和 intranet 的功能。  
  
|Internet|Intranet|  
|--------------|--------------|  
|低带宽|高带宽|  
|降低了的安全性的数据和系统|对数据和系统受控访问权限|  
|内容的最低限度的控制|内容很大的控制|  
  
##  <a name="_core_client_or_server_application"></a>客户端或服务器应用程序  
 客户端计算机上或服务器计算机上可能运行你的应用程序。 你的应用程序可能也是存储在服务器上，然后通过 Internet 下载并运行客户端计算机上。 客户端应用程序使用的 MFC WinInet 类用于下载文件。 MFC 和异步名字对象类用于下载文件和控制属性。 ActiveX 控件和活动文档类用于客户端应用程序以及从服务器在客户端上运行下载的应用程序。  
  
##  <a name="_core_the_web_page"></a>网页： HTML，活动文档中，ActiveX 控件  
 Microsoft 提供了多种方法可以提供在网页上的内容。 网页可以使用标准 HTML 或 HTML 扩展名，如对象标记，以提供动态内容，如 ActiveX 控件。  
  
 Web 浏览器通常显示 HTML 页。 活动文档还可以在启用 COM 的浏览器的简单的点，请单击界面中显示你的应用程序数据。 活动文档服务器可以在整个客户端区域中，使用其自己的菜单和工具栏显示您的文档、 全帧。  
  
 可以从服务器以异步方式下载并在网页上显示你编写的 ActiveX 控件。 如 VBScript 脚本语言可用于执行之前将信息发送到服务器的客户端验证。  
  
##  <a name="_core_browser_or_standalone"></a>浏览器或独立的应用程序  
 你可以编写嵌入在 HTML 页和在浏览器中查看的活动文档服务器中的 ActiveX 控件。 你可以编写包含一个按钮以提交请求以在 Web 服务器上运行 ISAPI 应用程序的 HTML 页面。 你可以编写一个独立应用程序使用 Internet 协议下载文件并对你的用户，显示的信息，而完全不必使用浏览器应用程序。  
  
##  <a name="_core_com_on_the_internet"></a>在 Internet 上的 COM  
 ActiveX 控件、 活动文档和异步名字对象所有使用 COM （组件对象模型） 技术。  
  
 ActiveX 控件在 Internet 站点上提供对文档和页面的动态内容。 使用 COM 可以构建 ActiveX 控件和使用活动文档的完整框架文档。  
  
 异步名字对象提供功能，以启用控件来执行很好地在 Internet 环境中，包括增量或渐进式意味着若要下载数据。 控件必须也能顺利用于还可能检索其数据以异步方式在同一时间的其他控件。  
  
##  <a name="_core_client_data_download_services"></a>客户端数据下载服务  
 两个集的 Api 来帮助你的客户端传输数据是 WinInet 和异步名字对象。 如果你有大型.gif 和.avi 文件和 HTML 页上的 ActiveX 控件，你可以通过异步，下载应通过使用异步名字对象或以异步方式使用 WinInet 增加到用户的响应能力。  
  
 在 Internet 上的一项常见任务在传输数据。 如果你已将 Active 技术 （例如，如果你有 ActiveX 控件），可以使用异步名字对象下载渐进式地呈现数据。 你可以使用 WinInet 传输使用常见的 Internet 协议，如 HTTP、 FTP 和 gopher 的数据。 这两种方法提供协议之间的独立性，并提供到使用 WinSock 和 TCP/IP 抽象层。 你仍然可以使用[WinSock](../mfc/windows-sockets-in-mfc.md)直接。  
  
 下表总结了多种方法可以使用 MFC 通过 Internet 传输数据。  
  
|使用此协议|在这些情况下|使用这些类|  
|-----------------------|----------------------------|-------------------------|  
|[Internet 下载使用异步名字对象](../mfc/asynchronous-monikers-on-the-internet.md)|对于异步传输使用 COM，ActiveX 控件和任何 Internet 协议。|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)， [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|  
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|为针对 HTTP、 FTP 和 gopher 的 Internet 协议。 数据可以同步或异步传输和存储在系统级缓存。|[CInternetSession](../mfc/reference/cinternetsession-class.md)， [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)， [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)，以及更多。|  
|[WinSock](../mfc/windows-sockets-in-mfc.md)|以最大效率和控制。 需要了解的套接字和 TCP/IP 协议。|[CSocket](../mfc/reference/csocket-class.md)， [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|  
  
## <a name="see-also"></a>请参阅  
 [MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)   
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)   
 [Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Internet 上的异步名字对象](../mfc/asynchronous-monikers-on-the-internet.md)

