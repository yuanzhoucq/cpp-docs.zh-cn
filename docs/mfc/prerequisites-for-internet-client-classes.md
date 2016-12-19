---
title: "Internet 客户端类的必备条件 | Microsoft Docs"
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
  - "类 [C++], 连接"
  - "连接 [C++], 类"
  - "文件 [C++], 读取"
  - "文件 [C++], 写入"
  - "FTP（文件传输协议）, MFC 类"
  - "Gopher 客户端应用程序"
  - "Gopher 系统必备"
  - "HTTP, 针对 Internet 客户端的系统必备"
  - "Internet [C++], 连接"
  - "Internet 客户端类系统必备 [C++]"
  - "Internet 文件 [C++], 写入"
  - "系统必备, Internet 客户端类"
  - "URL [C++], Internet 客户端应用程序"
ms.assetid: c51d1dfe-260c-4228-8100-e4efd90e9599
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Internet 客户端类的必备条件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Internet 客户端执行的某些操作 \(如读取文件，\) 的必备软件的操作 \(在这种情况下，为 Internet 连接\)。  下表列出了的系统必备部分客户端操作。  
  
### 常规 Internet URL \(Gopher 工具、FTP 或 HTTP\)  
  
|操作|系统必备|  
|--------|----------|  
|建立连接。|[CInternetSession](../mfc/reference/cinternetsession-class.md) 创建 Internet 建立客户端应用程序的基础。|  
|打开 URL。|建立连接。  调用 [CInternetSession::OpenURL](../Topic/CInternetSession::OpenURL.md)。  `OpenURL` 函数返回一只读的资源对象。|  
|URL 读取数据。|打开 URL。  调用 [CInternetFile::Read](../Topic/CInternetFile::Read.md)。|  
|Internet 选项设置。|建立连接。  调用 [CInternetSession::SetOption](../Topic/CInternetSession::SetOption.md)。|  
|将调用函数的状态信息。|建立连接。  调用 [CInternetSession::EnableStatusCallback](../Topic/CInternetSession::EnableStatusCallback.md)。  重写处理调用的 [CInternetSession::OnStatusCallback](../Topic/CInternetSession::OnStatusCallback.md)。|  
  
### FTP  
  
|操作|系统必备|  
|--------|----------|  
|创建 FTP 连接。|[CInternetSession](../mfc/reference/cinternetsession-class.md) 创建为此 Internet 客户端应用程序的基础。  创建调用 [CFtpConnection](../mfc/reference/cftpconnection-class.md) 对象的 [CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md)。|  
|查找第一个资源。|创建 FTP 连接。  [CFtpFileFind](../mfc/reference/cftpfilefind-class.md) 创建对象。  调用 [CFtpFileFind::FindFile](../Topic/CFtpFileFind::FindFile.md)。|  
|枚举所有可用资源。|查找第一个文件。  调用 [CFtpFileFind::FindNextFile](../Topic/CFtpFileFind::FindNextFile.md)，直到返回错误。|  
|FTP 打开文件。|创建 FTP 连接。  调用 [CFtpConnection::OpenFile](../Topic/CFtpConnection::OpenFile.md)[CInternetFile](../mfc/reference/cinternetfile-class.md) 创建并打开对象。|  
|FTP 读取文件。|打开具有读取访问 FTP 的文件。  调用 [CInternetFile::Read](../Topic/CInternetFile::Read.md)。|  
|对 FTP 文件的写入。|打开具有写访问 FTP 的文件。  调用 [CInternetFile::Write](../Topic/CInternetFile::Write.md)。|  
|更改服务器的客户的目录。|创建 FTP 连接。  调用 [CFtpConnection::SetCurrentDirectory](../Topic/CFtpConnection::SetCurrentDirectory.md)。|  
|检索服务器上的客户端上的当前目录。|创建 FTP 连接。  调用 [CFtpConnection::GetCurrentDirectory](../Topic/CFtpConnection::GetCurrentDirectory.md)。|  
  
### HTTP  
  
|操作|系统必备|  
|--------|----------|  
|生成 HTTP 连接。|[CInternetSession](../mfc/reference/cinternetsession-class.md) 创建为此 Internet 客户端应用程序的基础。  创建调用 [CHttpConnection](../mfc/reference/chttpconnection-class.md) 对象的 [CInternetSession::GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md)。|  
|HTTP 打开文件。|生成 HTTP 连接。  创建调用 [CHttpFile](../mfc/reference/chttpfile-class.md) 对象的 [CHttpConnection::OpenRequest](../Topic/CHttpConnection::OpenRequest.md)。  调用 [CHttpFile::AddRequestHeaders](../Topic/CHttpFile::AddRequestHeaders.md)。  调用 [CHttpFile::SendRequest](../Topic/CHttpFile::SendRequest.md)。|  
|HTTP 读取文件。|HTTP 打开文件。  调用 [CInternetFile::Read](../Topic/CInternetFile::Read.md)。|  
|获取有关 HTTP 请求的信息。|生成 HTTP 连接。  创建调用 [CHttpFile](../mfc/reference/chttpfile-class.md) 对象的 [CHttpConnection::OpenRequest](../Topic/CHttpConnection::OpenRequest.md)。  调用 [CHttpFile::QueryInfo](../Topic/CHttpFile::QueryInfo.md)。|  
  
### Gopher 工具  
  
|操作|系统必备|  
|--------|----------|  
|生成地鼠连接。|[CInternetSession](../mfc/reference/cinternetsession-class.md) 创建为此 Internet 客户端应用程序的基础。  创建调用 [CGopherConnection](../mfc/reference/cgopherconnection-class.md)的 [CInternetSession::GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md)。|  
|查找当前目录中的第一个文件。|生成地鼠连接。  [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md) 创建对象。  创建调用 [CGopherLocator](../mfc/reference/cgopherlocator-class.md) 对象的 [CGopherConnection::CreateLocator](../Topic/CGopherConnection::CreateLocator.md)。  定位器传递到 [CGopherFileFind::FindFile](../Topic/CGopherFileFind::FindFile.md)。  如果您之后，需要调用 [CGopherFileFind::GetLocator](../Topic/CGopherFileFind::GetLocator.md) 获取文件的定位器。|  
|枚举所有可用文件。|查找第一个文件。  调用 [CGopherFileFind::FindNextFile](../Topic/CGopherFileFind::FindNextFile.md)，直到返回错误。|  
|打开地鼠文件。|生成地鼠连接。  创建带有 [CGopherConnection::CreateLocator](../Topic/CGopherConnection::CreateLocator.md) 的一台地鼠定位器或查找具有的 [CGopherFileFind::GetLocator](../Topic/CGopherFileFind::GetLocator.md)一个定位符 \(URL\)。  调用 [CGopherConnection::OpenFile](../Topic/CGopherConnection::OpenFile.md)。|  
|读取地鼠文件。|打开地鼠文件。  使用 [CGopherFile](../mfc/reference/cgopherfile-class.md)。|  
  
## 请参阅  
 [Win32 Internet 扩展 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [用于创建 Internet 客户端应用程序的 MFC 类](../mfc/mfc-classes-for-creating-internet-client-applications.md)   
 [使用 MFC WinInet 类编写 Internet 客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)