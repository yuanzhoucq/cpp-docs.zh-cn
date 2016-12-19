---
title: "在典型 FTP 客户端应用程序中用于删除文件的步骤 | Microsoft Docs"
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
  - "FTP（文件传输协议）, 客户端应用程序"
  - "Internet 应用程序, FTP 客户端应用程序"
  - "Internet 客户端应用程序, FTP 删除"
  - "WinInet 类, FTP"
ms.assetid: 2c347a96-c0a4-4827-98fe-668406e552bc
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在典型 FTP 客户端应用程序中用于删除文件的步骤
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表显示了执行删除文件的典型的 FTP 客户端应用程序可能执行的步骤。  
  
|目标|采取的操作|效果|  
|--------|-----------|--------|  
|FTP 会话开始。|创建 [CInternetSession](../mfc/reference/cinternetsession-class.md) 对象。|初始化 WinInet 并连接到服务器。|  
|连接到 FTP服务器。|使用 [CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md)。|返回 [CFtpConnection](../mfc/reference/cftpconnection-class.md) 对象。|  
|检查确保处于 FTP 服务器上的正确目录。|使用 [CFtpConnection::GetCurrentDirectory](../Topic/CFtpConnection::GetCurrentDirectory.md) 或 [CFtpConnection::GetCurrentDirectoryAsURL](../Topic/CFtpConnection::GetCurrentDirectoryAsURL.md)。|根据您选择的成员函数返回当前连接到服务器上的目录的名称或 URL。|  
|转到服务器上个新的FTP目录。|使用 [CFtpConnection::SetCurrentDirectory](../Topic/CFtpConnection::SetCurrentDirectory.md)。|更改当前连接到服务器上的目录。|  
|查找在 FTP 目录的第一个文件。|使用 [CFtpFileFind::FindFile](../Topic/CFtpFileFind::FindFile.md)。|查找第一个文件。  如果没有找到文件，则返回错误。|  
|查找在 FTP 目录的下一个文件。|使用 [CFtpFileFind::FindNextFile](../Topic/CFtpFileFind::FindNextFile.md)。|查找下一个文件。  如果没找到文件，将返回错误。|  
|删除**FindFile** 或 `FindNextFile`中找到的文件。|使用 [CFtpConnection::Remove](../Topic/CFtpConnection::Remove.md)，使用 **FindFile** 或 `FindNextFile`返回的文件名。|删除服务器上读取或写入的文件。|  
|处理异常。|使用 [CInternetException](../mfc/reference/cinternetexception-class.md) 类。|处理所有公共 Internet 异常类型。|  
|结束FTP会话。|处理 [CInternetSession](../mfc/reference/cinternetsession-class.md) 对象。|自动清理打开文件句柄和连接。|  
  
## 请参阅  
 [Win32 Internet 扩展 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Internet 客户端类的必备条件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 类编写 Internet 客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)