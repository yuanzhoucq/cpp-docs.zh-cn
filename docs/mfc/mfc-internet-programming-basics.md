---
title: MFC Internet 编程基础知识 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ISAPI extensions, programming with ISAPI
- Internet applications [MFC]
- ISAPI
- ActiveX controls [MFC], Internet
- programming [MFC], Internet
- Web applications [MFC], MFC classes
- ISAPI filters [MFC], programming with ISAPI
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], writing
- Internet applications [MFC], Active technology
- Active technology [MFC]
- Internet content [MFC]
- WinInet classes [MFC]
ms.assetid: 6df2dfd0-6e3f-4587-9d01-2a32f00f8a6f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c7014a55ab51f8a1cbe66093763e9a094dc5f2a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-internet-programming-basics"></a>MFC Internet 编程基础知识
Microsoft 提供了许多 Api 编程客户端和服务器应用程序。 用于 Internet，编写了许多新的应用程序，并为技术、 浏览器功能和安全选项的更改，写入新类型的应用程序。 在客户端计算机，提供对 World Wide Web 访问权限和显示包含文本、 图形、 ActiveX 控件和文档的 HTML 页面上运行浏览器。 服务器提供 FTP、 HTTP 和 gopher 服务和运行使用 CGI 的服务器扩展应用程序。 自定义应用程序可以检索信息，并提供在 Internet 上的数据。  
  
 ![客户端和服务器应用程序](../mfc/media/vc38bq1.gif "vc38bq1")  
  
 MFC 提供支持 Internet 编程的类。 你可以使用[COleControl](../mfc/reference/colecontrol-class.md)和[CDocObjectServer](../mfc/reference/cdocobjectserver-class.md)和相关 MFC 类编写 ActiveX 控件和活动文档。 你可以使用 MFC 类，如[CInternetSession](../mfc/reference/cinternetsession-class.md)， [CFtpConnection](../mfc/reference/cftpconnection-class.md)，和[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)检索文件和使用 FTP，如 Internet 协议的信息HTTP 和 gopher。  
  
## <a name="in-this-section"></a>本节内容  
  
-   [与 Internet 相关的 MFC 类](../mfc/internet-related-mfc-classes.md)  
  
-   [按主题划分的 Internet 信息](../mfc/internet-information-by-topic.md)  
  
-   [按任务划分的 Internet 信息](../mfc/internet-information-by-task.md)  
  
-   [Internet 上的 Active 技术](../mfc/active-technology-on-the-internet.md)  
  
-   [WinInet 基础知识](../mfc/wininet-basics.md)  
  
-   [HTML 基础知识](../mfc/html-basics.md)  
  
-   [HTTP 基础知识](../mfc/http-basics.md)  
  
## <a name="related-sections"></a>相关章节  
  
-   [Internet 上的 ActiveX 控件](../mfc/activex-controls-on-the-internet.md)  
  
-   [Internet 上的活动文档](../mfc/active-documents-on-the-internet.md)  
  
-   [Internet 上的异步名字对象](../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)  
  
-   [MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)  
  
-   [应用程序设计选项](../mfc/application-design-choices.md)  
  
-   [编写 MFC 应用程序](../mfc/writing-mfc-applications.md)  
  
-   [测试 Internet 应用程序](../mfc/testing-internet-applications.md)  
  
-   [Internet 安全性](../mfc/internet-security-cpp.md)  
  
-   [ATL 支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)  
  
##  <a name="_core_web_sites_for_more_information"></a> 有关详细信息的网站  
 有关 Microsoft Internet 技术的其他信息，请参阅[Microsoft Developer Network (MSDN)](http://go.microsoft.com/fwlink/p/?linkid=56322) Web 站点。 （链接更改，恕不另行通知。）  
  
 此网站的开发人员包含使用 Microsoft 开发工具和技术，以及有关最新和即将发布的有关参加会议的顶部情景的信息。 从此页中，你可以跳转到多个相关的开发人员网站，包括.NET 和 XML 开发人员中心。 你还可以下载试用版 Sdk 和示例。  
  
 [World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/p/?linkid=37125)发布的 HTML、 HTTP、 CGI 和其他万维网技术规范。  
  
##  <a name="_core_more_internet_help"></a> 更多 Internet 帮助  
 Windows SDK 的 OLE 部分包含有关 OLE 编程的其他信息。 此信息提供有关使用 Win32 WinInet 函数的直接，而不是通过 MFC 类的详细信息。 它还包含有关 Internet 技术的概述信息。  
  
## <a name="see-also"></a>请参阅  



