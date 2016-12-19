---
title: "CInternetSession Class | Microsoft Docs"
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
  - "CInternetSession"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInternetSession class"
  - "Internet sessions"
ms.assetid: ef54feb4-9d0f-4e65-a45d-7a4cf6c40e51
caps.latest.revision: 25
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInternetSession Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建和初始化一个或多个同时Internet会话，并且，如果需要，在中，描述您的代理服务器的连接。  
  
## 语法  
  
```  
class CInternetSession : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CInternetSession::CInternetSession](../Topic/CInternetSession::CInternetSession.md)|构造 `CInternetSession` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CInternetSession::Close](../Topic/CInternetSession::Close.md)|当Internet会话终止时，关闭Internet连接。|  
|[CInternetSession::EnableStatusCallback](../Topic/CInternetSession::EnableStatusCallback.md)|建立一状态回调实例。|  
|[CInternetSession::GetContext](../Topic/CInternetSession::GetContext.md)|当Internet会话终止时，关闭Internet连接。|  
|[CInternetSession::GetCookie](../Topic/CInternetSession::GetCookie.md)|返回指定的URL及其所有父的URL cookie。|  
|[CInternetSession::GetCookieLength](../Topic/CInternetSession::GetCookieLength.md)|检索指定cookie的长度变量存储缓冲区。|  
|[CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md)|开始使用服务器上的一个FTP会话。  登录用户。|  
|[CInternetSession::GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md)|打开尝试打开连接的应用程序的一地鼠服务器。|  
|[CInternetSession::GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md)|打开尝试打开连接的应用程序的一个HTTP服务器。|  
|[CInternetSession::OnStatusCallback](../Topic/CInternetSession::OnStatusCallback.md)|在状态回调启用时，更新操作的状态。|  
|[CInternetSession::OpenURL](../Topic/CInternetSession::OpenURL.md)|分析并打开URL。|  
|[CInternetSession::SetCookie](../Topic/CInternetSession::SetCookie.md)|设置指定URL的cookie。|  
|[CInternetSession::SetOption](../Topic/CInternetSession::SetOption.md)|设置Internet会话的选项。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CInternetSession::operator HINTERNET](../Topic/CInternetSession::operator%20HINTERNET.md)|对当前Internet会话的句柄。|  
  
## 备注  
 如果需要应用程序的持续时间维护您的Internet连接，可以创建选件类 [CWinApp](../../mfc/reference/cwinapp-class.md)的 `CInternetSession` 成员。  
  
 一旦创建了一个Internet会话，可以调用 [OpenURL](../Topic/CInternetSession::OpenURL.md)。  `CInternetSession` 通过调用全局函数将分析您的URL [AfxParseURL](../Topic/AfxParseURL.md)。  无论协议类型，`CInternetSession` 解释URL和管理断点。  它可以处理对本地文件标识的URL资源“file:\/\/”。  `OpenURL` 将返回指向 [CStdioFile](../../mfc/reference/cstdiofile-class.md) 对象为通过它是否是本地文件。  
  
 使用 `OpenURL`，或者您在Internet服务器的URL，可以读取从站点的信息。  如果要对位于服务器中的文件中对服务实现\(例如，HTTP、FTP或地鼠\)事件，必须生成与该服务器的适当连接。  若要打开特定类型的连接来直接与特定的服务，请使用以下成员函数之一：  
  
-   打开与地鼠服务的连接的[GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md)。  
  
-   打开与HTTP服务的连接的[GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md)。  
  
-   打开与FTP服务的连接的[GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md)。  
  
 [SetOption](../Topic/CInternetSession::SetOption.md) 允许您设置会话的查询选项，如超时值，重试次数的数字，依此类推。  
  
 `CInternetSession` 成员函数 [SetCookie](../Topic/CInternetSession::SetCookie.md)、 [GetCookie](../Topic/CInternetSession::GetCookie.md)和 [GetCookieLength](../Topic/CInternetSession::GetCookieLength.md) 提供用于管理Win32 cookie数据库，服务器和脚本维护客户端工作站的状态信息。  
  
 有关编程任务的基本Internet的更多信息，请参见文章 [Internet第一步:WinInet](../../mfc/wininet-basics.md)。  有关使用MFC WinInet选件类的一般信息，请参见文章 [编程时WinInet的Internet](../../mfc/win32-internet-extensions-wininet.md)。  
  
> [!NOTE]
>  `CInternetSession` 将引发不支持的服务类型的 [AfxThrowNotSupportedException](../Topic/AfxThrowNotSupportedException.md)。  只有以下服务类型是当前支持:FTP、HTTP、地鼠和文件。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetSession`  
  
## 要求  
 **Header:** afxinet.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [CHttpConnection Class](../../mfc/reference/chttpconnection-class.md)   
 [CFtpConnection Class](../../mfc/reference/cftpconnection-class.md)   
 [CGopherConnection Class](../../mfc/reference/cgopherconnection-class.md)