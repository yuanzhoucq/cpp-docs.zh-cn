---
title: "应用程序设计选择 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序设计 [C++], 设计目标"
  - "应用程序设计 [C++], Internet 应用程序"
  - "应用程序 [MFC], Internet"
  - "客户端应用程序 [C++], 与 Internet 上的服务器应用程序"
  - "设计"
  - "Internet [C++], 与 Intranet"
  - "Internet 应用程序 [C++], 设计应用程序"
  - "服务器应用程序, 与 Internet 上的客户端应用程序"
ms.assetid: 9b96172c-b4d4-4c69-bfb2-226ce0de6d08
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 应用程序设计选择
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当对编程时，对于 Internet，本文讨论某些考虑设计问题。  
  
 本文涵盖的主题包括：  
  
-   [Intranet 与 Internet](#_core_intranet_versus_internet)  
  
-   [客户端或服务器应用程序](#_core_client_or_server_application)  
  
-   [网页：HTML 中，对活动文档，ActiveX 控件](#_core_the_web_page.3a_.html.2c_.activex_documents.2c_.activex_controls)  
  
-   [浏览器或独立应用程序](#_core_browser_or_stand.2d.alone_application)  
  
-   [Internet 上的 COM](#_core_com_on_the_internet)  
  
-   [客户数据下载服务](#_core_client_data_download_services)  
  
 如果您准备开始立即写入程序，请参见 [在 MFC 应用程序](../mfc/writing-mfc-applications.md)。  
  
##  <a name="_core_intranet_versus_internet"></a> Intranet 与 Internet  
 Internet 上运行的多种应用程序和为用户可访问的。浏览器和 Internet 访问。  企业 Intranet 还实现，使用 TCP\/IP 协议和 Web 浏览器，是的公司网络。  Intranet 提供了方便地升级，主要源。公司范围信息。  它们可用于升级软件，用于传递和组成表调查，对于客户支持和的信息发送。  下表比较了 Internet 和 Intranet 的功能。  
  
|Internet|Intranet|  
|--------------|--------------|  
|低带宽|高带宽|  
|数据和降低系统的安全|为数据和系统的控制权限|  
|最小的控件内容|高内容控件|  
  
##  <a name="_core_client_or_server_application"></a> 客户端或服务器应用程序  
 应用程序可以运行在客户端计算机或服务器计算机上。  应用程序服务器上还存储，在 Internet 和运行所下载然后在客户端计算机上。  MFC WinInet 类用于客户端应用程序可以将文件下载。  MFC 和异步名字对象类用于下载文件和控件的属性。  ActiveX 控件和活动文档的类用于客户端应用程序和服务器上下载。从客户端运行的应用程序。  
  
##  <a name="_core_the_web_page.3a_.html.2c_.activex_documents.2c_.activex_controls"></a> 网页：HTML 中，对活动文档，ActiveX 控件  
 Microsoft 提供多种方法可在网页上将内容  网页可以使用标准 HTML 或者 HTML 扩展名，例如对象标记，提供动态内容 \(如 ActiveX 控件。  
  
 典型 Web 浏览器显示 HTML 页。  活动文档也可以以启用 COM 的浏览器的简单单击接口的应用程序数据。  活动文档服务器可以查看文档，在整个工作区执行的完整框架，使用其自己的菜单和工具栏。  
  
 您编写 ActiveX 控件在网页可以从服务器下载异步和显示。  您可以使用脚本语言 \(在 VBScript 将信息发送到服务器之前执行客户端验证。  
  
##  <a name="_core_browser_or_stand.2d.alone_application"></a> 浏览器或独立应用程序  
 可以编写在 HTML 页和活动文档服务器嵌入在浏览器显示的 ActiveX 控件。  可以编写一个包含按钮提交请求在 Web 服务器上运行应用 ISAPI 程序的 HTML 页。  使用浏览器应用程序中，可以编写使用 Internet 协议下载文件和信息向用户的独立应用程序，那么，没有。  
  
##  <a name="_core_com_on_the_internet"></a> Internet 上的 COM  
 ActiveX 控件、活动文档和异步都使用名字对象 \(COM 组件对象模型 \(COM\) 技术\)。  
  
 ActiveX 控件提供动态内容了文档和页面在 Internet 网站。  使用活动文档，COM 可生成 ActiveX 控件和功能文档框架。  
  
 异步名字对象在一个 Internet 环境提供功能使控件正常执行，包括一个增量表示进度或下载数据。  控件必须也可以正常使用可能同时异步检索其数据的其他控件一起使用。  
  
##  <a name="_core_client_data_download_services"></a> 客户数据下载服务  
 将帮助转交客户数据的两组 API 是和 WinINet 异步名字对象。  如果您有大 .gif 和 .avi 文件和 ActiveX 控件在 HTML 页中，可以提高对用户的响应速度通过异步下载，使用名字对象或异步使用 WinInet。  
  
 在 Internet 上常见任务传输数据。  如果已经使用可用技术 \(例如，在中，如果您具有一 ActiveX 控件\)，可以使用异步名字对象进度呈现数据作为其下载。  类似使用 HTTP、FTP 和地鼠，常用的 Internet 协议可以使用 WinInet 传输数据。  方法提供两个协议无关，并且提供抽象层使用为 Winsock 和 TCP\/IP。  可以直接将使用 [WinSock](../mfc/windows-sockets-in-mfc.md)。  
  
 下表总结了使用 MFC 多种传输在 Internet 上的数据。  
  
|使用协议。|在这些条件下|使用这些类|  
|-----------|------------|-----------|  
|[使用异步下载的 Internet 名字对象](../mfc/asynchronous-monikers-on-the-internet.md)|对于使用 COM、ActiveX 控件和任何 Internet 协议的异步传输。|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)，[CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|  
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|有关 HTTP、FTP 和地鼠的 Internet 协议。  数据可以是同步或异步和在整个系统存储在缓存中。|[CInternetSession](../mfc/reference/cinternetsession-class.md) [CFtpFileFind](../mfc/reference/cftpfilefind-class.md) [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)，、和许多。|  
|[WinSock](../mfc/windows-sockets-in-mfc.md)|对于最大效率和控件。  了解 Word 和套接 TCP\/IP 协议的 Requires 了解。|[CSocket](../mfc/reference/csocket-class.md)，[CAsyncSocket](../mfc/reference/casyncsocket-class.md)|  
  
## 请参阅  
 [MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)   
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)   
 [Win32 Internet 扩展 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Internet 上的异步名字对象](../mfc/asynchronous-monikers-on-the-internet.md)