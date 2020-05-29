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
ms.openlocfilehash: 89f3e5c108de1cf7b3b73a33a08e2c50b1333c92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374632"
---
# <a name="application-design-choices"></a>应用程序设计选择

本文讨论了在为 Internet 编程时需要考虑的一些设计问题。

本文涵盖的主题包括：

- [内联网与互联网](#_core_intranet_versus_internet)

- [客户端或服务器应用程序](#_core_client_or_server_application)

- [网页](#_core_the_web_page)

- [浏览器或独立应用程序](#_core_browser_or_standalone)

- [互联网上的 COM](#_core_com_on_the_internet)

- [客户端数据下载服务](#_core_client_data_download_services)

如果您现在准备开始编写程序，请参阅[编写 MFC 应用程序](../mfc/writing-mfc-applications.md)。

## <a name="intranet-versus-internet"></a><a name="_core_intranet_versus_internet"></a>内联网与互联网

许多应用程序在 Internet 上运行，任何具有浏览器和 Internet 访问权限的人都可以访问这些应用程序。 企业还在实施内部网，这些内部网是使用 TCP/IP 协议和 Web 浏览器的全公司网络。 内联网为全公司的信息提供了易于升级的中央来源。 它们可用于升级软件、交付和制表调查、客户支持以及信息传递。 下表比较了互联网和内联网的功能。

|Internet|Intranet|
|--------------|--------------|
|低带宽|高带宽|
|降低数据和系统的安全性|对数据和系统的受控访问|
|对内容的最小控制|对内容的高度控制|

## <a name="client-or-server-application"></a><a name="_core_client_or_server_application"></a>客户端或服务器应用程序

您的应用程序可能在客户端计算机或服务器计算机上运行。 您的应用程序也可能存储在服务器上，然后通过 Internet 下载并在客户端计算机上运行。 MFC WinInet 类用于客户端应用程序下载文件。 MFC 和异步名字对象类用于下载文件和控制属性。 ActiveX 控件和活动文档的类用于客户端应用程序和从服务器下载以在客户端上运行的应用程序。

## <a name="the-web-page-html-active-documents-activex-controls"></a><a name="_core_the_web_page"></a>网页：HTML、活动文档、活动X控件

Microsoft 提供了几种在网页上提供内容的方法。 网页可以使用标准 HTML 或 HTML 扩展名（如对象标记）来提供动态内容（如 ActiveX 控件）。

Web 浏览器通常显示 HTML 页面。 活动文档还可以在启用 COM 的浏览器的简单点击界面中显示应用程序的数据。 活动文档服务器可以显示文档，整个工作区中的完整框架，并拥有自己的菜单和工具栏。

可以从服务器异步下载您编写的 ActiveX 控件，并显示在网页上。 在将信息发送到服务器之前，可以使用脚本语言（如 VBScript）执行客户端验证。

## <a name="browser-or-stand-alone-application"></a><a name="_core_browser_or_standalone"></a>浏览器或独立应用程序

您可以编写嵌入在 HTML 页中的 ActiveX 控件，也可以编写在浏览器中查看的 Active 文档服务器。 您可以编写包含按钮的 HTML 页，以提交在 Web 服务器上运行 ISAPI 应用程序的请求。 您可以编写一个独立的应用程序，该应用程序使用 Internet 协议下载文件和向用户显示信息，而无需使用浏览器应用程序。

## <a name="com-on-the-internet"></a><a name="_core_com_on_the_internet"></a>互联网上的 COM

ActiveX 控件、活动文档和异步名字器都使用 COM（组件对象模型）技术。

ActiveX 控件为 Internet 网站上的文档和页面提供动态内容。 使用 COM，您可以使用 Active 文档构建 ActiveX 控件和全帧文档。

异步名字器提供功能，使控件能够在 Internet 环境中很好地运行，包括下载数据的增量或渐进方法。 控件还必须与可能同时异步检索其数据的其他控件很好地配合。

## <a name="client-data-download-services"></a><a name="_core_client_data_download_services"></a>客户端数据下载服务

两组有助于将数据传输到客户端的 API 是 WinInet 和异步名字。 如果您的 HTML 页面上有较大的 .gif 和 .avi 文件和 ActiveX 控件，则可以通过异步下载（通过使用异步名字）或使用 WinInet 异步来提高用户的响应能力。

互联网上的一项常见任务是传输数据。 如果您已经在使用 Active 技术（例如，如果您有 ActiveX 控件），则可以使用异步名字对象在数据下载时逐步呈现数据。 您可以使用 WinInet 使用常见的 Internet 协议（如 HTTP、FTP 和 gopher）传输数据。 这两种方法都提供了协议独立性，并提供一个抽象层来使用 WinSock 和 TCP/IP。 您仍然可以直接使用[温索克](../mfc/windows-sockets-in-mfc.md)。

下表总结了使用 MFC 通过互联网传输数据的几种方法。

|使用此协议|在这些条件下|使用这些类|
|-----------------------|----------------------------|-------------------------|
|[使用异步网站进行互联网下载](../mfc/asynchronous-monikers-on-the-internet.md)|对于使用 COM、ActiveX 控件和任何 Internet 协议进行异步传输。|[CAsyncMoniker文件](../mfc/reference/casyncmonikerfile-class.md)， [CDataPath属性](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|用于 HTTP、FTP 和 gopher 的 Internet 协议。 数据可以同步或异步传输，并存储在系统范围的缓存中。|[C互联网会话](../mfc/reference/cinternetsession-class.md)， [CFtpFile查找](../mfc/reference/cftpfilefind-class.md)， [CGopher文件查找](../mfc/reference/cgopherfilefind-class.md)， 和更多.|
|[温索克](../mfc/windows-sockets-in-mfc.md)|实现最高的效率和控制。 需要了解套接字和 TCP/IP 协议。|[套接字](../mfc/reference/csocket-class.md)， [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>另请参阅

[MFC 互联网编程任务](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC 互联网编程基础知识](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 互联网扩展（WinInet）](../mfc/win32-internet-extensions-wininet.md)<br/>
[互联网上的异步月客](../mfc/asynchronous-monikers-on-the-internet.md)
