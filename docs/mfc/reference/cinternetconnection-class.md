---
title: "CInternetConnection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CInternetConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asynchronous connections"
  - "CInternetConnection class"
  - "Internet connections"
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CInternetConnection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理您的组件与Internet服务器的连接。  
  
## 语法  
  
```  
class CInternetConnection : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CInternetConnection::CInternetConnection](../Topic/CInternetConnection::CInternetConnection.md)|构造 `CInternetConnection` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CInternetConnection::GetContext](../Topic/CInternetConnection::GetContext.md)|获取此连接对象的上下文ID。|  
|[CInternetConnection::GetServerName](../Topic/CInternetConnection::GetServerName.md)|获取服务器的名称与连接。|  
|[CInternetConnection::GetSession](../Topic/CInternetConnection::GetSession.md)|获取一个指向 [CInternetSession](../../mfc/reference/cinternetsession-class.md) 对象与连接。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CInternetConnection::operator HINTERNET](../Topic/CInternetConnection::operator%20HINTERNET.md)|对于Internet会话的句柄。|  
  
## 备注  
 它是MFC选件类的 [CFtpConnection](../../mfc/reference/cftpconnection-class.md)、 [CHttpConnection](../../mfc/reference/chttpconnection-class.md)和 [CGopherConnection](../../mfc/reference/cgopherconnection-class.md)基类。  这些选件每个类都将进行通信提供附加功能与单个HTTP、FTP或地鼠服务器。  
  
 直接与Internet服务器若要连接，您必须具有 [CInternetSession](../../mfc/reference/cinternetsession-class.md) 对象和 `CInternetConnection` 对象。  
  
 若要了解有关WinInet选件类的工作原理，请参见文章 [编程时WinInet的Internet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetConnection`  
  
## 要求  
 **Header:** afxinet.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)