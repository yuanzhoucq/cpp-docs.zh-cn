---
title: "典型 HTTP 客户端应用程序中的步骤 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序 [MFC], HTTP 客户端"
  - "客户端应用程序 [C++], HTTP"
  - "HTTP 客户端应用程序"
  - "Internet 应用程序 [C++], HTTP 客户端应用程序"
  - "Internet 客户端应用程序 [C++], HTTP 表"
  - "WinInet 类, HTTP"
ms.assetid: f86552e8-8acd-4b23-bdc5-0c3a247ebd74
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 典型 HTTP 客户端应用程序中的步骤
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表显示在典型的 HTTP 客户端应用程序便可能执行还原的步骤：  
  
|目标|您执行的操作|效果|  
|--------|------------|--------|  
|HTTP 开始会话。|[CInternetSession](../mfc/reference/cinternetsession-class.md) 创建对象。|初始化 WinInet 并连接到服务器。|  
|连接到 HTTP 服务器上。|使用 [CInternetSession::GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md)。|返回对象。[CHttpConnection](../mfc/reference/chttpconnection-class.md)|  
|打开 HTTP 请求。|使用 [CHttpConnection::OpenRequest](../Topic/CHttpConnection::OpenRequest.md)。|返回对象。[CHttpFile](../mfc/reference/chttpfile-class.md)|  
|发送 HTTP 请求。|使用 [CHttpFile::AddRequestHeaders](../Topic/CHttpFile::AddRequestHeaders.md) 和 [CHttpFile::SendRequest](../Topic/CHttpFile::SendRequest.md)。|查找文件。  如果没找到文件，将返回错误。|  
|读取文件。|使用 [CHttpFile](../mfc/reference/chttpfile-class.md)。|读取指定的字节数使用提供的缓冲区。|  
|处理异常。|使用 [CInternetException](../mfc/reference/cinternetexception-class.md) 类。|处理所有公共 Internet 异常类型。|  
|HTTP 结束会话。|处理 [CInternetSession](../mfc/reference/cinternetsession-class.md) 对象。|自动清理打开文件句柄和连接。|  
  
## 请参阅  
 [Win32 Internet 扩展 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Internet 客户端类的必备条件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 类编写 Internet 客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)