---
title: 应用程序设计选择
ms.date: 11/04/2016
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
ms.openlocfilehash: cdb294e4ab808a7e4cbcec457f6e744eff9f12cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394658"
---
# <a name="application-design-choices"></a>应用程序设计选择

本文讨论了一些用于 Internet 编程时要考虑的设计问题。

在本文中涵盖的主题包括：

- [Intranet 与 Internet](#_core_intranet_versus_internet)

- [客户端或服务器应用程序](#_core_client_or_server_application)

- [](#_core_the_web_page)

- [浏览器或独立的应用程序](#_core_browser_or_standalone)

- [在 Internet 上的 COM](#_core_com_on_the_internet)

- [客户端数据下载服务](#_core_client_data_download_services)

如果你已准备好开始编写应用程序现在，请参阅[编写 MFC 应用程序](../mfc/writing-mfc-applications.md)。

##  <a name="_core_intranet_versus_internet"></a> Intranet 与 Internet

许多应用程序在 Internet 上运行，并使用浏览器和 Internet 访问权限的任何人都可访问。 企业还将实现 intranet，这是公司范围内使用 TCP/IP 协议的网络和 Web 浏览器。 企业内部网提供一个可轻松地升级、 中央来源，公司范围内的信息。 它们可以使用软件升级、 交付和制成表格调查、 客户支持和传送信息。 下表比较了 Internet 和 intranet 的功能。

|Internet|Intranet|
|--------------|--------------|
|低带宽|高带宽|
|减少的数据和系统的安全性|对数据和系统的受控的访问|
|内容的最低限度的控制|内容很大的控制|

##  <a name="_core_client_or_server_application"></a> 客户端或服务器应用程序

客户端计算机上或服务器计算机上可能运行你的应用程序。 你的应用程序可能还会存储在服务器上，通过 Internet 下载并运行客户端计算机上。 MFC WinInet 类用于客户端应用程序来下载文件。 MFC 和异步名字对象类用于下载文件，并控制属性。 客户端应用程序和从客户端上运行的服务器下载的应用程序使用的 ActiveX 控件和活动文档类。

##  <a name="_core_the_web_page"></a> 网页：HTML 中，活动文档中，ActiveX 控件

Microsoft 提供了几种方法在网页上提供的内容。 网页可使用标准 HTML 或 HTML 扩展，如对象标记，以提供动态内容，例如 ActiveX 控件。

Web 浏览器通常显示的 HTML 页面。 活动文档还可以支持 COM 的浏览器的简单点击的界面中显示应用程序的数据。 活动文档服务器可以在整个客户端区域中，具有其自己的菜单和工具栏显示您的文档、 完整的框架。

可以从服务器上以异步方式下载并在网页上显示您编写的 ActiveX 控件。 VBScript 等脚本语言可用于执行之前将信息发送到服务器的客户端验证。

##  <a name="_core_browser_or_standalone"></a> 浏览器或独立的应用程序

您可以编写嵌入在 HTML 页和浏览器中查看的活动文档服务器中的 ActiveX 控件。 您可以编写 HTML 页面包含一个用于提交的请求的 Web 服务器上运行 ISAPI 应用程序按钮。 可以编写使用 Internet 协议下载文件并显示信息到用户，而完全不必使用浏览器应用程序的独立应用程序。

##  <a name="_core_com_on_the_internet"></a> 在 Internet 上的 COM

ActiveX 控件、 活动文档和异步名字对象都使用 COM （组件对象模型） 技术。

ActiveX 控件在 Internet 站点上提供对文档和页面的动态内容。 使用 COM 可以构建 ActiveX 控件和使用活动文档的完整框架文档。

异步名字对象提供功能，使控件来执行也在 Internet 环境中，包括增量或渐进式意味着若要下载数据。 控件还必须处理也还可能检索其数据以异步方式在同一时间其他控件。

##  <a name="_core_client_data_download_services"></a> 客户端数据下载服务

两组 Api，可帮助您的客户端传输数据是 WinInet 和异步名字对象。 如果有大型.gif 和.avi 文件和 HTML 页面上的 ActiveX 控件，则可以通过下载以异步方式，通过使用异步名字对象或以异步方式使用 WinInet 增加到用户的响应能力。

在 Internet 上很常见的任务将数据传输。 如果已使用 Active 技术 （例如，如果您有一个 ActiveX 控件），可以使用异步名字对象以渐进式呈现数据，因为它会下载。 可以使用 WinInet 将使用常见的 Internet 协议，如 HTTP、 FTP 和 gopher 的数据传输。 这两种方法提供协议之间的独立性，并提供使用 WinSock 和 TCP/IP 的抽象层。 您仍然可以使用[WinSock](../mfc/windows-sockets-in-mfc.md)直接。

下表总结了几种使用 MFC 通过 Internet 传输数据。

|使用此协议|在这些情况下|使用这些类|
|-----------------------|----------------------------|-------------------------|
|[Internet 下载使用异步名字对象](../mfc/asynchronous-monikers-on-the-internet.md)|有关使用 COM，ActiveX 控件的异步传输和任何 Internet 协议。|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)， [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|为 HTTP、 FTP 和 gopher 的 Internet 协议。 数据可以同步或异步方式传输和存储在系统范围的缓存。|[CInternetSession](../mfc/reference/cinternetsession-class.md)， [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)， [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)，等等。|
|[WinSock](../mfc/windows-sockets-in-mfc.md)|以最大的效率和控制。 需要了解套接字和 TCP/IP 协议。|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>请参阅

[MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Internet 上的异步名字对象](../mfc/asynchronous-monikers-on-the-internet.md)
