---
title: "CGopherConnection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CGopherConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CGopherConnection class"
  - "连接到服务器"
  - "连接到服务器, gopher servers"
  - "gopher 协议"
  - "gopher server"
  - "Internet connections, gopher"
  - "Internet server, gopher"
  - "protocols, gopher"
  - "服务器, 连接"
  - "服务, gopher"
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CGopherConnection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理您的地鼠Internet服务器的连接。  
  
> [!NOTE]
>  选件类 `CGopherConnection`、 `CGopherFile`、 `CGopherFileFind`、 `CGopherLocator` 及其成员已弃用，因为它们在Windows XP平台不起作用，但是，它们将继续在以前的平台。  
  
## 语法  
  
```  
class CGopherConnection : public CInternetConnection  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CGopherConnection::CGopherConnection](../Topic/CGopherConnection::CGopherConnection.md)|构造 `CGopherConnection` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CGopherConnection::CreateLocator](../Topic/CGopherConnection::CreateLocator.md)|创建一 [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) 对象查找在地鼠服务器的文件。|  
|[CGopherConnection::GetAttribute](../Topic/CGopherConnection::GetAttribute.md)|检索有关地鼠对象的属性信息。|  
|[CGopherConnection::OpenFile](../Topic/CGopherConnection::OpenFile.md)|打开地鼠文件。|  
  
## 备注  
 地鼠服务是MFC WinInet选件类识别的三Internet服务之一。  
  
 选件类 `CGopherConnection` 包含管理地鼠服务的构造函数和三个附加成员函数: [OpenFile](../Topic/CGopherConnection::OpenFile.md)、 [CreateLocator](../Topic/CGopherConnection::CreateLocator.md)和 [GetAttribute](../Topic/CGopherConnection::GetAttribute.md)。  
  
 与地鼠Internet服务器若要通信，必须先创建 [CInternetSession](../../mfc/reference/cinternetsession-class.md)实例，然后调用 [CInternetSession::GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md)，创建 `CGopherConnection` 对象并返回指向它。  您从不直接创建一 `CGopherConnection` 对象。  
  
 若要了解更多信息 `CGopherConnection` 与其他MFC Internet选件类，请参见文章 [编程时WinInet的Internet](../../mfc/win32-internet-extensions-wininet.md)。  有关使用其他两个支持的Internet服务的更多信息，FTP和HTTP看到选件类 [CHttpConnection](../../mfc/reference/chttpconnection-class.md) 和 [CFtpConnection](../../mfc/reference/cftpconnection-class.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CGopherConnection`  
  
## 要求  
 **Header:** afxinet.h  
  
## 请参阅  
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFtpConnection Class](../../mfc/reference/cftpconnection-class.md)   
 [CHttpConnection Class](../../mfc/reference/chttpconnection-class.md)   
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [CGopherLocator Class](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFile Class](../../mfc/reference/cgopherfile-class.md)   
 [CInternetSession Class](../../mfc/reference/cinternetsession-class.md)