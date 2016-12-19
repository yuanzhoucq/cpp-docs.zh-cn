---
title: "MFC Internet 编程基础知识 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
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
  - "Active 技术 [C++]"
  - "ActiveX 控件 [C++], Internet"
  - "Internet 应用程序 [C++]"
  - "Internet 应用程序 [C++], Active 技术"
  - "Internet 应用程序 [C++], ActiveX 控件"
  - "Internet 应用程序 [C++], 写入"
  - "Internet 内容 [C++]"
  - "ISAPI"
  - "ISAPI 扩展, 使用 ISAPI 编程"
  - "ISAPI 筛选器, 使用 ISAPI 编程"
  - "编程 [C++], Internet"
  - "Web 应用程序 [C++], MFC 类"
  - "WinInet 类"
ms.assetid: 6df2dfd0-6e3f-4587-9d01-2a32f00f8a6f
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC Internet 编程基础知识
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft 为编程的客户端和服务器应用程序提供了许多 API。  许多新应用程序编写的，并且，当 Internet，技术、浏览器功能和安全性选项更改，应用程序编写类型。  在客户端计算机上运行浏览器，提供对和 Web 显示了包含文本、图形、ActiveX 控件和文档的 HTML 页。  使用 CGI，服务器提供 FTP、HTTP 和地鼠服务并运行扩展服务器应用程序。  自定义应用程序在 Internet 可以从中检索信息同时提供数据。  
  
 ![客户端和服务器应用程序](../mfc/media/vc38bq1.png "vc38BQ1")  
  
 MFC 提供支持 Internet 编程的类。  可以使用 [COleControl](../mfc/reference/colecontrol-class.md) 和 [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) 和相关类编写 ActiveX 控件和 MFC 活动文档。  使用 Internet 协议 \(如 HTTP 和 FTP、地鼠，可以使用 MFC 类 \(如 [CInternetSession](../mfc/reference/cinternetsession-class.md)、[CFtpConnection](../mfc/reference/cftpconnection-class.md)和 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) 检索文件和信息。  
  
## 本节内容  
  
-   [与 Internet 相关的 MFC 类](../mfc/internet-related-mfc-classes.md)  
  
-   [按主题划分的 Internet 信息](../mfc/internet-information-by-topic.md)  
  
-   [按任务划分的 Internet 信息](../mfc/internet-information-by-task.md)  
  
-   [Internet 上的 Active 技术](../mfc/active-technology-on-the-internet.md)  
  
-   [WinInet 基础知识](../mfc/wininet-basics.md)  
  
-   [HTML 基础](../mfc/html-basics.md)  
  
-   [HTTP 基础](../mfc/http-basics.md)  
  
## 相关章节  
  
-   [Internet 上的 ActiveX 控件](../mfc/activex-controls-on-the-internet.md)  
  
-   [Internet 上的活动文档](../mfc/active-documents-on-the-internet.md)  
  
-   [Internet 上的异步名字对象](../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [Win32 Internet 扩展 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)  
  
-   [MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)  
  
-   [应用程序设计选择](../mfc/application-design-choices.md)  
  
-   [编写 MFC 应用程序](../mfc/writing-mfc-applications.md)  
  
-   [测试 Internet 应用程序](../mfc/testing-internet-applications.md)  
  
-   [Internet 安全性](../mfc/internet-security-cpp.md)  
  
-   [ATL 支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)  
  
##  <a name="_core_web_sites_for_more_information"></a> 有关站点的详细信息  
 有关 Microsoft Internet 技术的更多信息，请 [Microsoft Developer Network \(MSDN\)](http://go.microsoft.com/fwlink/?LinkID=56322) 参见网站。\(链接可能不另行通知更改。\)  
  
 此开发的网站包含有关使用 Microsoft 开发工具和技术的信息以及有关过去和即将参加会议的最新新闻。  在此页中，可以跳到许多相关开发站点，包括 .NET 和 XML 开发中心。  还可以下载 SDKs beta 和示例。  
  
 [万维网联合会 \(W3C\)](http://go.microsoft.com/fwlink/?LinkID=37125) 发布 HTML、HTTP、CGI 和其他技术万维网的规范。  
  
##  <a name="_core_more_internet_help"></a> 更多帮助 Internet  
 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 的 OLE 节包含有关 OLE 编程的附加信息。  此信息通过 MFC 类提供有关直接使用 WinInet Win32 函数的详细信息，而不是。  它还包含有关 Internet 技术的概述信息。  
  
## 请参阅  
 [MFC Internet Programming \(NIB\)](http://msdn.microsoft.com/zh-cn/0f7a1f3a-385b-4d56-a55b-0d766840c58a)