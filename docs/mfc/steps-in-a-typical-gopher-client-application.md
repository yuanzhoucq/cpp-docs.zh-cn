---
title: "典型 Gopher 客户端应用程序中的步骤 | Microsoft Docs"
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
  - "Gopher 客户端应用程序"
  - "Internet 应用程序, gopher 客户端应用程序"
  - "Internet 客户端应用程序, gopher 表"
  - "WinInet 类, gopher"
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 典型 Gopher 客户端应用程序中的步骤
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表显示在典型的 gopher 客户端应用程序便可能执行还原的步骤。  
  
|目标|采取的操作|效果|  
|--------|-----------|--------|  
|开始地鼠会话。|创建 [CInternetSession](../mfc/reference/cinternetsession-class.md) 对象。|初始化 WinInet 并连接到服务器。|  
|跳转至 gopher 服务器。|使用 [CInternetSession::GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md)。|返回对象[CGopherConnection](../mfc/reference/cgopherconnection-class.md)。|  
|查找在地鼠的第一个资源。|使用 [CGopherFileFind::FindFile](../Topic/CGopherFileFind::FindFile.md)。|查找第一个文件。  如果没有找到文件，则返回错误。|  
|查找在地鼠的下一个资源。|使用 [CGopherFileFind::FindNextFile](../Topic/CGopherFileFind::FindNextFile.md)。|查找下一个文件。  如果没找到文件，将返回错误。|  
|打开 **FindFile** 或 `FindNextFile` 中找到的文件读取的。|使用 [CGopherFileFind::GetLocator](../Topic/CGopherFileFind::GetLocator.md)，获取地鼠定位器。  使用 [CGopherConnection::OpenFile](../Topic/CGopherConnection::OpenFile.md)。|定位器打开指定的文件。  `OpenFile` 方法返回 [CGopherFile](../mfc/reference/cgopherfile-class.md) 对象。|  
|打开文件使用所提供的地鼠定位器。|使用 [CGopherConnection::CreateLocator](../Topic/CGopherConnection::CreateLocator.md)，创建地鼠定位器。  使用 [CGopherConnection::OpenFile](../Topic/CGopherConnection::OpenFile.md)。|定位器打开指定的文件。  `OpenFile` 方法返回 [CGopherFile](../mfc/reference/cgopherfile-class.md) 对象。|  
|从文件中读取|使用 [CGopherFile](../mfc/reference/cgopherfile-class.md)。|读取指定的字节数，则使用提供的缓冲区。|  
|处理异常。|使用 [CInternetException](../mfc/reference/cinternetexception-class.md) 类。|处理所有公共 Internet 异常类型。|  
|结束地鼠会话。|处理 [CInternetSession](../mfc/reference/cinternetsession-class.md) 对象。|自动清理打开文件句柄和连接。|  
  
## 请参阅  
 [Win32 Internet 扩展 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Internet 客户端类的必备条件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 类编写 Internet 客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)