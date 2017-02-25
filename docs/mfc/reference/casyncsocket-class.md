---
title: "CAsyncSocket Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAsyncSocket"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asynchronous Windows Sockets"
  - "CAsyncSocket class"
  - "通信 [C++], 网络"
  - "network communications"
  - "sockets [C++], Windows"
  - "Windows Sockets [C++], 异步"
ms.assetid: cca4d5a1-aa0f-48bd-843e-ef0e2d7fc00b
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CAsyncSocket Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示Windows存储—网络通信终结点。  
  
## 语法  
  
```  
class CAsyncSocket : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAsyncSocket::CAsyncSocket](../Topic/CAsyncSocket::CAsyncSocket.md)|构造 `CAsyncSocket` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAsyncSocket::Accept](../Topic/CAsyncSocket::Accept.md)|接受在套接字的连接。|  
|[CAsyncSocket::AsyncSelect](../Topic/CAsyncSocket::AsyncSelect.md)|请求事件通知套接字。|  
|[CAsyncSocket::Attach](../Topic/CAsyncSocket::Attach.md)|附加套接字处理的 `CAsyncSocket` 对象。|  
|[CAsyncSocket::Bind](../Topic/CAsyncSocket::Bind.md)|将一个本地地址与套接字。|  
|[CAsyncSocket::Close](../Topic/CAsyncSocket::Close.md)|关闭套接字。|  
|[CAsyncSocket::Connect](../Topic/CAsyncSocket::Connect.md)|生成与对等类套接字的连接。|  
|[CAsyncSocket::Create](../Topic/CAsyncSocket::Create.md)|创建一个套接字。|  
|[CAsyncSocket::Detach](../Topic/CAsyncSocket::Detach.md)|分离 `CAsyncSocket` 对象的一个套接字处理。|  
|[CAsyncSocket::FromHandle](../Topic/CAsyncSocket::FromHandle.md)|返回指向 `CAsyncSocket` 对象命名套接字处理。|  
|[CAsyncSocket::GetLastError](../Topic/CAsyncSocket::GetLastError.md)|获取失败的最后一个操作的错误状态。|  
|[CAsyncSocket::GetPeerName](../Topic/CAsyncSocket::GetPeerName.md)|获取套接字连接对等类套接字的地址。|  
|[CAsyncSocket::GetPeerNameEx](../Topic/CAsyncSocket::GetPeerNameEx.md)|获取套接字连接对等类套接字的地址\(处理IPv6地址）。|  
|[CAsyncSocket::GetSockName](../Topic/CAsyncSocket::GetSockName.md)|获取本地名称套接字。|  
|[CAsyncSocket::GetSockNameEx](../Topic/CAsyncSocket::GetSockNameEx.md)|获取本地名称\(套接字处理IPv6地址）。|  
|[CAsyncSocket::GetSockOpt](../Topic/CAsyncSocket::GetSockOpt.md)|检索套接字选项。|  
|[CAsyncSocket::IOCtl](../Topic/CAsyncSocket::IOCtl.md)|控件套接字的模式。|  
|[CAsyncSocket::Listen](../Topic/CAsyncSocket::Listen.md)|建立一个套接字侦听传入连接请求。|  
|[CAsyncSocket::Receive](../Topic/CAsyncSocket::Receive.md)|接收从套接字的数据。|  
|[CAsyncSocket::ReceiveFrom](../Topic/CAsyncSocket::ReceiveFrom.md)|接收数据的图形并存储源点地址。|  
|[CAsyncSocket::ReceiveFromEx](../Topic/CAsyncSocket::ReceiveFromEx.md)|接收数据的图形并存储源点地址\(处理IPv6地址）。|  
|[CAsyncSocket::Send](../Topic/CAsyncSocket::Send.md)|数据发送到已连接的套接字。|  
|[CAsyncSocket::SendTo](../Topic/CAsyncSocket::SendTo.md)|数据发送到特定目标。|  
|[CAsyncSocket::SendToEx](../Topic/CAsyncSocket::SendToEx.md)|数据发送到特定目标\(处理IPv6地址）。|  
|[CAsyncSocket::SetSockOpt](../Topic/CAsyncSocket::SetSockOpt.md)|设置套接字选项。|  
|[CAsyncSocket::ShutDown](../Topic/CAsyncSocket::ShutDown.md)|禁用 **Send** 和 **Receive** 在套接字调用。|  
|[CASyncSocket::Socket](../Topic/CASyncSocket::Socket.md)|分配一个套接字处理。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CAsyncSocket::OnAccept](../Topic/CAsyncSocket::OnAccept.md)|通知一个侦听的套接字它是否可以接受等待连接请求通过调用 **Accept**。|  
|[CAsyncSocket::OnClose](../Topic/CAsyncSocket::OnClose.md)|通知套接字套接字连接到其关闭。|  
|[CAsyncSocket::OnConnect](../Topic/CAsyncSocket::OnConnect.md)|通知一个连接的套接字连接尝试完成的，是否成功或错误。|  
|[CAsyncSocket::OnOutOfBandData](../Topic/CAsyncSocket::OnOutOfBandData.md)|通知一个接收的套接字在套接字要读取的带外数据，通常一紧急消息。|  
|[CAsyncSocket::OnReceive](../Topic/CAsyncSocket::OnReceive.md)|通知一个侦听的套接字具有调用将检索的数据 **Receive**。|  
|[CAsyncSocket::OnSend](../Topic/CAsyncSocket::OnSend.md)|通知套接字则可以通过调用 **Send**发送数据。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CAsyncSocket::operator \=](../Topic/CAsyncSocket::operator%20=.md)|赋新值。`CAsyncSocket` 对象。|  
|[CAsyncSocket::operator SOCKET](../Topic/CAsyncSocket::operator%20SOCKET.md)|使用此运算符检索 `CAsyncSocket` 对象的 **套接字** 处理。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAsyncSocket::m\_hSocket](../Topic/CAsyncSocket::m_hSocket.md)|指示附加 **套接字** 处理此 `CAsyncSocket` 对象。|  
  
## 备注  
 选件类 `CAsyncSocket` 封装Windows存储功能API，提供面向对象的抽象。若要使用MFC一起使用Windows套接字的程序员。  
  
 此选件类根据假定您了解网络通信。  应负责处理块，字节顺序差异以及将Unicode和多字节字符集\(mbcs\)字符串之间。  如果希望这些管理的更方便的接口为问题，请参见选件类 [CSocket](../../mfc/reference/csocket-class.md)。  
  
 若要使用 `CAsyncSocket` 对象，请调用其构造函数，然后调用 [创建](../Topic/CAsyncSocket::Create.md) 函数创建基础套接字处理\(类型 `SOCKET`\)，不包括在可接受的套接字。  对于服务器套接字调用 [侦听](../Topic/CAsyncSocket::Listen.md) 成员函数，因此，客户端套接字需要 [连接](../Topic/CAsyncSocket::Connect.md) 成员函数。  服务器套接字应要求 [接受](../Topic/CAsyncSocket::Accept.md) 函数接收连接请求。  使用"剩余 `CAsyncSocket` 函数执行套接字之间的通信。  在完成，销毁 `CAsyncSocket` 对象是否在堆中创建的;析构函数自动调用 [关闭](../Topic/CAsyncSocket::Close.md) 功能。  `SOCKET` 数据类型在文章 [Windows套接字:背景](../../mfc/windows-sockets-background.md)所述。  
  
> [!NOTE]
>  在使用MFC套接字在静态链接的MFC应用程序时的辅助线程，则必须对使用套接字初始化套接字库的每个线程的 `AfxSocketInit`。  默认情况下，`AfxSocketInit` 在主线程仅调用。  
  
 有关更多信息，请参见 [Windows套接字:使用选件类CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) 和相关文章。，以及 [Windows套接字2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAsyncSocket`  
  
## 要求  
 **标头:** afxsock.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CSocket Class](../../mfc/reference/csocket-class.md)   
 [CSocketFile Class](../../mfc/reference/csocketfile-class.md)