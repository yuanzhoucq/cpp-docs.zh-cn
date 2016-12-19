---
title: "使用 MFC WinInet 类编写 Internet 客户端应用程序 | Microsoft Docs"
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
  - "Internet 应用程序, 客户端应用程序"
  - "Internet 应用程序, WinInet"
  - "Internet 客户端应用程序"
  - "Internet 客户端应用程序, 写入"
  - "MFC, Internet 应用程序"
  - "WinInet 类, 编程"
ms.assetid: a2c4a40c-a94e-4b3e-9dbf-f8a8dc8e5428
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 MFC WinInet 类编写 Internet 客户端应用程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每 Internet 客户端应用程序的基础是 Internet 会话。  MFC 实现 Internet 会话作为类对象。[CInternetSession](../mfc/reference/cinternetsession-class.md) 使用此类，您可以创建一个 Internet 会话或多个同时会话。  
  
 若要与服务器通信，您需要 [CInternetConnection](../mfc/reference/cinternetconnection-class.md) 对象以及 `CInternetSession`。  使用 [CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md)[CInternetSession::GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md)[CInternetSession::GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md)、或，可以创建 `CInternetConnection`。  这些调用中的每一特定于类型协议。  这些调用不打开服务器上的文件读取或写入的。  如果要读取或写入数据，您必须打开文件，在一个单独步骤。  
  
 对于多数 Internet 会话，`CInternetSession` 对象的工作使与 [CInternetFile](../mfc/reference/cinternetfile-class.md) 对象：  
  
-   对于 Internet 会话，必须创建的实例。[CInternetSession](../mfc/reference/cinternetsession-class.md)  
  
-   如果 Internet 会话读取或写入数据，必须创建 `CInternetFile` 实例 \(或其子类、[CHttpFile](../mfc/reference/chttpfile-class.md) 或 [CGopherFile](../mfc/reference/cgopherfile-class.md)\)。  易于读取数据的方法将调用。[CInternetSession::OpenURL](../Topic/CInternetSession::OpenURL.md) 此函数分析本地资源定位器您提供的 URL 打开 \(URL\)，与服务器的连接以指定的，并且返回一只读的 `CInternetFile` 对象。  `CInternetSession::OpenURL` 并非特定于一个协议类型 \- 任何 FTP、HTTP 或地鼠 URL 的同一调用工作。  `CInternetSession::OpenURL` 甚至包含本地文件 \(返回 `CStdioFile` 而非 `CInternetFile`\)。  
  
-   如果 Internet 会话未读取或不写入数据，但是，该 FTP 目录执行其他任务，如删除文件，您可能不需要创建 `CInternetFile`的实例。  
  
 可以使用下列两种方法创建 `CInternetFile` 对象：  
  
-   如果使用 `CInternetSession::OpenURL` 生成服务器连接，调用 `OpenURL` 返回 `CStdioFile`。  
  
-   如果使用 **CInternetSession::GetFtpConnection**、`GetGopherConnection`或 `GetHttpConnection` 生成服务器连接，必须调用单个 `CFtpConnection::OpenFile`、`CGopherConnection::OpenFile`或 **CHttpConnection::OpenRequest,** 返回，`CInternetFile`，`CGopherFile`或 `CHttpFile`。  
  
 在 Internet 实现客户端应用程序的步骤更改取决于您是创建基于 **OpenURL** 的一般 Internet 客户或使用某一 **GetConnection** 函数的协议特定的客户。  
  
## 您想进一步了解什么？  
  
-   [如何编写实现一般使用 FTP、HTTP 和地鼠的 Internet 客户端应用程序？](../mfc/steps-in-a-typical-internet-client-application.md)  
  
-   [如何写入 FTP 打开文件的客户端应用程序？](../mfc/steps-in-a-typical-ftp-client-application.md)  
  
-   [如何编写没有打开文件，但 FTP 客户端应用程序执行某目录操作，如删除文件？](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)  
  
-   [如何编写地鼠客户端应用程序？](../mfc/steps-in-a-typical-gopher-client-application.md)  
  
-   [如何编写 HTTP 客户端应用程序？](../mfc/steps-in-a-typical-http-client-application.md)  
  
## 请参阅  
 [Win32 Internet 扩展 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [用于创建 Internet 客户端应用程序的 MFC 类](../mfc/mfc-classes-for-creating-internet-client-applications.md)   
 [Internet 客户端类的必备条件](../mfc/prerequisites-for-internet-client-classes.md)