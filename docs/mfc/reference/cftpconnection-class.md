---
title: "CFtpConnection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFtpConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFtpConnection class"
  - "FTP（文件传输协议）, 建立连接"
  - "Internet connections, FTP"
  - "Internet services, FTP"
ms.assetid: 5e3a0501-8893-49cf-a3d5-0628d8d6b936
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CFtpConnection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理您的组件与Internet服务器的FTP连接并允许目录和文件的直接处理在该服务器。  
  
## 语法  
  
```  
class CFtpConnection : public CInternetConnection  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CFtpConnection::CFtpConnection](../Topic/CFtpConnection::CFtpConnection.md)|构造 `CFtpConnection` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CFtpConnection::Command](../Topic/CFtpConnection::Command.md)|发送一个命令直接到FTP服务器。|  
|[CFtpConnection::CreateDirectory](../Topic/CFtpConnection::CreateDirectory.md)|在服务器上创建一个目录。|  
|[CFtpConnection::GetCurrentDirectory](../Topic/CFtpConnection::GetCurrentDirectory.md)|获取此连接的当前内容。|  
|[CFtpConnection::GetCurrentDirectoryAsURL](../Topic/CFtpConnection::GetCurrentDirectoryAsURL.md)|获取此连接的当前内容作为URL。|  
|[CFtpConnection::GetFile](../Topic/CFtpConnection::GetFile.md)|联接服务器获取文件|  
|[CFtpConnection::OpenFile](../Topic/CFtpConnection::OpenFile.md)|打开在中连接到的服务器的文件。|  
|[CFtpConnection::PutFile](../Topic/CFtpConnection::PutFile.md)|在服务器上放置一个文件。|  
|[CFtpConnection::Remove](../Topic/CFtpConnection::Remove.md)|从服务器上删除文件。|  
|[CFtpConnection::RemoveDirectory](../Topic/CFtpConnection::RemoveDirectory.md)|从服务器移除该示例将指定的内容。|  
|[CFtpConnection::Rename](../Topic/CFtpConnection::Rename.md)|对服务器的重命名文件。|  
|[CFtpConnection::SetCurrentDirectory](../Topic/CFtpConnection::SetCurrentDirectory.md)|设置当前FTP目录。|  
  
## 备注  
 FTP是MFC WinInet选件类识别的三Internet服务之一。  
  
 使用FTP Internet服务器若要通信，必须先创建 [CInternetSession](../../mfc/reference/cinternetsession-class.md)实例，然后创建 `CFtpConnection` 对象。  您从不直接创建一 `CFtpConnection` 对象;相反，请调用 [CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md)，创建 `CFtpConnection` 对象并返回指向它。  
  
 若要了解更多信息 `CFtpConnection` 与其他MFC Internet选件类，请参见文章 [编程时WinInet的Internet](../../mfc/win32-internet-extensions-wininet.md)。  有关与使用其他两个支持服务的更多信息，HTTP和地鼠，请参见选件类 [CHttpConnection](../../mfc/reference/chttpconnection-class.md) 和 [CGopherConnection](../../mfc/reference/cgopherconnection-class.md)。  
  
## 示例  
 在 [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) 选件参见类概述中的示例。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CFtpConnection`  
  
## 要求  
 **Header:** afxinet.h  
  
## 请参阅  
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [CInternetSession Class](../../mfc/reference/cinternetsession-class.md)