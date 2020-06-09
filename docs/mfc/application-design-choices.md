---
title: 应用程序设计选择
ms.date: 09/12/2019
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
ms.openlocfilehash: 5ae6d5d3087720a1cfed3fcc33569ed4bed0ebfd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616028"
---
# <a name="application-design-choices"></a>应用程序设计选择

本文讨论在对 Internet 进行编程时要考虑的一些设计问题。

本文中涵盖的主题包括：

- [Intranet 与 Internet](#_core_intranet_versus_internet)

- [客户端或服务器应用程序](#_core_client_or_server_application)

- [网页](#_core_the_web_page)

- [浏览器或独立应用程序](#_core_browser_or_standalone)

- [Internet 上的 COM](#_core_com_on_the_internet)

- [客户端数据下载服务](#_core_client_data_download_services)

如果你现在已准备好开始编写程序，请参阅[编写 MFC 应用程序](writing-mfc-applications.md)。

## <a name="intranet-versus-internet"></a><a name="_core_intranet_versus_internet"></a>Intranet 与 Internet

许多应用程序都在 Internet 上运行，并且具有浏览器和 Internet 访问权限的任何人都可以访问。 企业还使用 TCP/IP 协议和 Web 浏览器实现了企业范围的网络。 Intranet 为公司范围内的信息提供了一个易于升级的中心源。 它们可用于升级软件、提供和针对调查、用于客户支持以及用于信息传送。 下表对 Internet 和 intranet 的功能进行了比较。

|Internet|Intranet|
|--------------|--------------|
|低带宽|高带宽|
|降低了数据和系统的安全性|控制对数据和系统的访问|
|最小内容控制|内容的高控制|

## <a name="client-or-server-application"></a><a name="_core_client_or_server_application"></a>客户端或服务器应用程序

您的应用程序可以在客户端计算机或服务器计算机上运行。 您的应用程序也可以存储在服务器上，然后在 Internet 上下载并在客户端计算机上运行。 MFC WinInet 类用于客户端应用程序下载文件。 MFC 和异步名字对象类用于下载文件和控件属性。 ActiveX 控件和活动文档的类用于客户端应用程序和从服务器下载以在客户端上运行的应用程序。

## <a name="the-web-page-html-active-documents-activex-controls"></a><a name="_core_the_web_page"></a>网页： HTML、活动文档、ActiveX 控件

Microsoft 提供了多种方法来提供网页上的内容。 网页可以使用标准 HTML 或 HTML 扩展名（如对象标记）来提供动态内容，如 ActiveX 控件。

Web 浏览器通常显示 HTML 页面。 活动文档还可以在启用 COM 的浏览器的简单点击界面中显示应用程序的数据。 你的活动文档服务器可以在整个工作区中显示完整的文档，并具有自己的菜单和工具栏。

你编写的 ActiveX 控件可以从服务器异步下载并显示在网页上。 您可以使用一种脚本语言（如 VBScript）来执行客户端验证，然后将信息发送到服务器。

## <a name="browser-or-stand-alone-application"></a><a name="_core_browser_or_standalone"></a>浏览器或独立应用程序

您可以编写嵌入到 HTML 页中的 ActiveX 控件，以及在浏览器中查看的活动文档服务器。 你可以编写包含按钮的 HTML 页面，以提交在 Web 服务器上运行 ISAPI 应用程序的请求。 你可以编写一个独立的应用程序，该应用程序使用 Internet 协议下载文件并向用户显示信息，而无需使用浏览器应用程序。

## <a name="com-on-the-internet"></a><a name="_core_com_on_the_internet"></a>Internet 上的 COM

ActiveX 控件、活动文档和异步名字对象均使用 COM （组件对象模型）技术。

ActiveX 控件向 Internet 站点上的文档和页面提供动态内容。 使用 COM，可以使用活动文档生成 ActiveX 控件和全框架文档。

异步名字对象提供了一些功能，使控件能够在 Internet 环境中正常运行，包括用于下载数据的增量或渐进方式。 控件还必须与其他控件同时工作，这些控件也可能同时以异步方式检索数据。

## <a name="client-data-download-services"></a><a name="_core_client_data_download_services"></a>客户端数据下载服务

可帮助将数据传输到客户端的两组 Api 为 WinInet 和异步名字对象。 如果 HTML 页面上有大量 .gif 和 .avi 文件和 ActiveX 控件，则可以通过使用异步名字对象异步下载或异步使用 WinInet，提高用户的响应能力。

Internet 上的常见任务正在传输数据。 如果已在使用活动技术（例如，如果你有 ActiveX 控件），则可以使用异步名字对象在下载数据时逐步呈现数据。 可以使用 WinInet 使用常见 Internet 协议（如 HTTP、FTP 和 gopher）传输数据。 这两种方法提供协议独立性，并使用 WinSock 和 TCP/IP 提供抽象层。 你仍可以直接使用[WinSock](windows-sockets-in-mfc.md) 。

下表汇总了几种使用 MFC 在 Internet 上传输数据的方法。

|使用此协议|在这些情况下|使用这些类|
|-----------------------|----------------------------|-------------------------|
|[使用异步名字对象下载 Internet](asynchronous-monikers-on-the-internet.md)|对于使用 COM、ActiveX 控件和任意 Internet 协议的异步传输。|[CAsyncMonikerFile](reference/casyncmonikerfile-class.md)、 [CDataPathProperty](reference/cdatapathproperty-class.md)|
|[WinInet](win32-internet-extensions-wininet.md)|用于 HTTP、FTP 和 gopher 的 Internet 协议。 数据可以同步或异步传输，并存储在系统范围的缓存中。|[CInternetSession](reference/cinternetsession-class.md)、 [CFtpFileFind](reference/cftpfilefind-class.md)、 [CGopherFileFind](reference/cgopherfilefind-class.md)等。|
|[WinSock](windows-sockets-in-mfc.md)|以实现最高效率和控制。 需要了解套接字和 TCP/IP 协议。|[CSocket](reference/csocket-class.md)、 [CAsyncSocket](reference/casyncsocket-class.md)|

## <a name="see-also"></a>另请参阅

[MFC Internet 编程任务](mfc-internet-programming-tasks.md)<br/>
[MFC Internet 编程基础知识](mfc-internet-programming-basics.md)<br/>
[Win32 Internet 扩展（WinInet）](win32-internet-extensions-wininet.md)<br/>
[Internet 上的异步名字对象](asynchronous-monikers-on-the-internet.md)
