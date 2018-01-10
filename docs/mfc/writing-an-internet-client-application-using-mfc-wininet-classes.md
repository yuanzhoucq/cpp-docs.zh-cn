---
title: "编写 Internet 客户端应用程序使用 MFC WinInet 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Internet client applications [MFC]
- WinInet classes [MFC], programming
- Internet client applications [MFC], writing
- Internet applications [MFC], WinInet
- Internet applications [MFC], client applications
- MFC, Internet applications
ms.assetid: a2c4a40c-a94e-4b3e-9dbf-f8a8dc8e5428
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 07b97d4af18ff560a48aadb3ba71b61609f82a85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="writing-an-internet-client-application-using-mfc-wininet-classes"></a>使用 MFC WinInet 类编写 Internet 客户端应用程序
每个 Internet 客户端应用程序的基础是 Internet 会话。 MFC 实现 Internet 会话作为类的对象[CInternetSession](../mfc/reference/cinternetsession-class.md)。 通过使用此类，您可以创建一个 Internet 会话或多个同时会话。  
  
 若要与服务器通信，你需要[CInternetConnection](../mfc/reference/cinternetconnection-class.md)对象以及`CInternetSession`。 你可以创建`CInternetConnection`使用[cinternetsession:: Getftpconnection](../mfc/reference/cinternetsession-class.md#getftpconnection)， [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection)，或[CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection). 所有这些调用都特定于协议类型。 这些调用不会在服务器上打开文件以进行读取或编写。 如果您打算读取或写入数据，则必须执行单独的步骤打开文件。  
  
 对于大多数 Internet 会话，`CInternetSession`对象可与中现有手工[CInternetFile](../mfc/reference/cinternetfile-class.md)对象：  
  
-   对于 Internet 会话，必须创建的实例[CInternetSession](../mfc/reference/cinternetsession-class.md)。  
  
-   如果 Internet 会话读取或写入数据，则必须创建的实例`CInternetFile`(或其子类、 [CHttpFile](../mfc/reference/chttpfile-class.md)或[CGopherFile](../mfc/reference/cgopherfile-class.md))。 读取数据的最简单方法是调用[cinternetsession:: Openurl](../mfc/reference/cinternetsession-class.md#openurl)。 此函数将分析您提供的统一资源定位器 (URL)、打开与 URL 指定的服务器的连接并返回一个只读的 `CInternetFile` 对象。 `CInternetSession::OpenURL` 并不会特定于一种协议类型 - 同一调用适用于所有 FTP、HTTP 或 gopher URL。 `CInternetSession::OpenURL` 甚至会处理本地文件（返回 `CStdioFile` 而非 `CInternetFile`）。  
  
-   如果 Internet 会话不读取或写入数据，而是执行其他任务（如删除 FTP 目录中的文件），则您可能不需要创建 `CInternetFile` 的实例。  
  
 可通过两种方法创建 `CInternetFile` 对象：  
  
-   如果使用 `CInternetSession::OpenURL` 建立服务器连接，则调用 `OpenURL` 将返回 `CStdioFile`。  
  
-   如果使用**cinternetsession:: Getftpconnection**， `GetGopherConnection`，或`GetHttpConnection`若要建立服务器连接，必须调用`CFtpConnection::OpenFile`， `CGopherConnection::OpenFile`，或**chttpconnection::，**分别返回`CInternetFile`， `CGopherFile`，或`CHttpFile`分别。  
  
 根据你创建的基于泛型 Internet 客户端中实现 Internet 客户端应用程序的步骤有所不同**OpenURL**或特定于协议的客户端使用之一**GetConnection**函数。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [如何编写常规配合 FTP、 HTTP 和 gopher 的 Internet 客户端应用](../mfc/steps-in-a-typical-internet-client-application.md)  
  
-   [如何编写打开文件的 FTP 客户端应用](../mfc/steps-in-a-typical-ftp-client-application.md)  
  
-   [如何编写的 FTP 客户端应用程序不会打开一个文件，但执行目录操作，如删除的文件](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)  
  
-   [如何编写 gopher 客户端应用程序](../mfc/steps-in-a-typical-gopher-client-application.md)  
  
-   [如何编写 HTTP 客户端应用程序](../mfc/steps-in-a-typical-http-client-application.md)  
  
## <a name="see-also"></a>请参阅  
 [Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [用于创建 Internet 客户端应用程序的 MFC 类](../mfc/mfc-classes-for-creating-internet-client-applications.md)   
 [Internet 客户端类的必备条件](../mfc/prerequisites-for-internet-client-classes.md)
