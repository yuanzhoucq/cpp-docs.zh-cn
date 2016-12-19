---
title: "CHttpConnection Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CHttpConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHttpConnection class"
  - "连接到服务器"
  - "连接到服务器, HTTP 服务器"
  - "连接 [C++], HTTP"
  - "HTTP 连接"
  - "HTTP 服务器, 连接"
  - "Internet connections, HTTP"
  - "Internet protocols"
  - "Internet protocols, HTTP"
  - "Internet server, HTTP"
  - "protocols, HTTP"
  - "服务器, 连接"
ms.assetid: a402b662-c445-4988-800d-c8278551babe
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHttpConnection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理您的组件与HTTP服务器的连接。  
  
## 语法  
  
```  
class CHttpConnection : public CInternetConnection  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CHttpConnection::CHttpConnection](../Topic/CHttpConnection::CHttpConnection.md)|创建一个 `CHttpConnection` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CHttpConnection::OpenRequest](../Topic/CHttpConnection::OpenRequest.md)|打开HTTP请求。|  
  
## 备注  
 HTTP是MFC WinInet选件类实现三Internet服务器协议之一。  
  
 选件类 `CHttpConnection` 包含一个构造函数和一个成员函数，[OpenRequest](../Topic/CHttpConnection::OpenRequest.md)，管理与服务器的连接与HTTP协议。  
  
 与HTTP服务器若要通信，必须先创建 [CInternetSession](../../mfc/reference/cinternetsession-class.md)实例，然后创建 [CHttpConnection](#_mfc_chttpconnection) 对象。  您从不直接创建一 `CHttpConnection` 对象;相反，请调用 [CInternetSession::GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md)，创建 `CHttpConnection` 对象并返回指向它。  
  
 若要了解更多信息 `CHttpConnection` 与其他MFC Internet选件类，请参见文章 [编程时WinInet的Internet](../../mfc/win32-internet-extensions-wininet.md)。  有关连接到使用其他两个支持的Internet协议的服务器的更多信息，地鼠和FTP，请参见选件类 [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) 和 [CFtpConnection](../../mfc/reference/cftpconnection-class.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CHttpConnection`  
  
## 要求  
 **Header:** afxinet.h  
  
## 请参阅  
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [CHttpFile Class](../../mfc/reference/chttpfile-class.md)