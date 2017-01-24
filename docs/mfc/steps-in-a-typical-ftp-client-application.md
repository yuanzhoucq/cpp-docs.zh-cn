---
title: "典型 FTP 客户端应用程序中的步骤 | Microsoft Docs"
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
  - "FTP（文件传输协议）"
  - "FTP（文件传输协议）, 客户端应用程序"
  - "Internet 应用程序, FTP 客户端应用程序"
  - "Internet 客户端应用程序, FTP 表"
  - "WinInet 类, FTP"
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 典型 FTP 客户端应用程序中的步骤
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

典型的 FTP 客户端应用程序 [CInternetSession](../mfc/reference/cinternetsession-class.md) [CFtpConnection](../mfc/reference/cftpconnection-class.md) 创建和对象。  请注意这些 MFC WinInet 类实际不控制代理类型将设置为；IIS。  
  
 并且，请参见以下知识库文章：  
  
-   如何：与基于 CERN 代理的 FTP 使用 WinInet API \(文章 ID:Q166961\)  
  
-   示例：与基于 CERN 的密码保护的代理 \(文章 ID 的 FTP:Q216214\)  
  
-   Internet 服务管理器无法显示安装了代理服务 \(文章 ID:Q216802\)  
  
 下表显示在典型的 FTP 客户端应用程序便可能执行还原的步骤。  
  
|目标|采取的操作|效果|  
|--------|-----------|--------|  
|FTP 会话开始。|创建 [CInternetSession](../mfc/reference/cinternetsession-class.md) 对象。|初始化 WinInet 并连接到服务器。|  
|连接到 FTP服务器。|使用 [CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md)。|返回 [CFtpConnection](../mfc/reference/cftpconnection-class.md) 对象。|  
|转到服务器上个新的FTP目录。|使用 [CFtpConnection::SetCurrentDirectory](../Topic/CFtpConnection::SetCurrentDirectory.md)。|更改当前连接到服务器上的目录。|  
|查找在 FTP 目录的第一个文件。|使用 [CFtpFileFind::FindFile](../Topic/CFtpFileFind::FindFile.md)。|查找第一个文件。  如果没有找到文件，则返回错误。|  
|查找在 FTP 目录的下一个文件。|使用 [CFtpFileFind::FindNextFile](../Topic/CFtpFileFind::FindNextFile.md)。|查找下一个文件。  如果没找到文件，将返回错误。|  
|打开 **FindFile** 或 `FindNextFile` 中找到的文件读取或写入的。|使用 [CFtpConnection::OpenFile](../Topic/CFtpConnection::OpenFile.md)，可以使用 [FindFile](../Topic/CFtpFileFind::FindFile.md) 或 [FindNextFile](../Topic/CFtpFileFind::FindNextFile.md)返回的文件名。|打开服务器上读取或写入的文件。  返回 [CInternetFile](../mfc/reference/cinternetfile-class.md) 对象的长度。|  
|对文件的读取或写入。|使用 [CInternetFile::Read](../Topic/CInternetFile::Read.md) 或 [CInternetFile::Write](../Topic/CInternetFile::Write.md)。|读取或写入指定的字节数，则使用提供的缓冲区。|  
|处理异常。|使用 [CInternetException](../mfc/reference/cinternetexception-class.md) 类。|处理所有公共 Internet 异常类型。|  
|结束FTP会话。|处理 [CInternetSession](../mfc/reference/cinternetsession-class.md) 对象。|自动清理打开文件句柄和连接。|  
  
## 请参阅  
 [Win32 Internet 扩展 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Internet 客户端类的必备条件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 类编写 Internet 客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)