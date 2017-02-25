---
title: "CSocket Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSocket"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSocket class"
  - "SOCKET handle"
  - "sockets classes"
  - "WinSock CSocket class"
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CSocket Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从 `CAsyncSocket`比派生，继承其 Windows 套接字 API 的封装，表示较高级别的抽象 `CAsyncSocket` 对象。  
  
## 语法  
  
```  
class CSocket : public CAsyncSocket  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CSocket::CSocket](../Topic/CSocket::CSocket.md)|构造 `CSocket` 对象。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CSocket::Attach](../Topic/CSocket::Attach.md)|附加 **SOCKET** 句柄 `CSocket` 对象。|  
|[CSocket::CancelBlockingCall](../Topic/CSocket::CancelBlockingCall.md)|移除当前正在进行阻止的调用。|  
|[CSocket::Create](../Topic/CSocket::Create.md)|创建一个套接字。|  
|[CSocket::FromHandle](../Topic/CSocket::FromHandle.md)|返回指向 `CSocket` 对象命名 **SOCKET** 处理。|  
|[CSocket::IsBlocking](../Topic/CSocket::IsBlocking.md)|确定块是否调用正在进行。|  
  
### 受保护的方法  
  
|名称|描述|  
|--------|--------|  
|[CSocket::OnMessagePending](../Topic/CSocket::OnMessagePending.md)|调用过程等待消息，当等待块调用时完成。|  
  
## 备注  
 `CSocket` 与选件类 `CSocketFile` 和 `CArchive` 使用管理发送和接收数据。  
  
 `CSocket` 对象还提供块，对 `CArchive`的同步操作非常重要。  块函数，例如 `Receive`，`Send`，`ReceiveFrom`，`SendTo`，并且，`Accept` \(所有继承 `CAsyncSocket`\)，则不会返回在 `CSocket`的一个 `WSAEWOULDBLOCK` 错误。  相反，这些函数等待，直到操作完成。  此外，原始的调用将停止与该错误 `WSAEINTR`，如果 `CancelBlockingCall` 调用，当其中一种功能块时。  
  
 若要使用 `CSocket` 对象，请调用构造函数，然后调用 `Create` 创建基础 `SOCKET` 句柄 \(类型 `SOCKET`\)。  `Create` 的默认参数创建流，套接字，但，则使用具有 `CArchive` 对象的套接字，可以指定参数创建数据进行套接字，或者绑定到特定端口创建服务器套接字。  在客户端上使用服务器端，的 `Connect` 和 `Accept` 连接到客户端套接字。  然后创建一 `CSocketFile` 对象并将它设置为 `CSocketFile` 构造函数的 `CSocket` 对象。  接下来，创建发送的一 `CArchive` 对象和一个收到的数据 \(根据需要\)，然后将它们与 `CArchive` 构造函数的 `CSocketFile` 对象。  当通信完成时，销毁 `CArchive`、`CSocketFile`和 `CSocket` 对象。  `SOCKET` 数据类型在文章 [Windows 套接字：背景](../../mfc/windows-sockets-background.md)所述。  
  
 当您使用 `CArchive` 和 `CSocketFile` 和 `CSocket`时，可能会遇到 `CSocket::Receive` 输入循环的情况 \( `PumpMessages(FD_READ)`\) 等待请求的少量字节。  这是因为，Windows 套接字只允许一 recv 每个 FD\_READ 通知调用，但是，`CSocketFile` 和 `CSocket` 允许多个 recv 每 FD\_READ 调用。  如果收到 FD\_READ，而没有读取数据，应用程序停止。  如果不会收到另一个 FD\_READ，应用程序停止间通信套接字。  
  
 通过以下方式可以解决此问题。  在您的套接字选件类 `OnReceive` 方法，请调用 `CAsyncSocket::IOCtl(FIONREAD, ...)`，在调用您的邮件类之前 `Serialize` 方法，当从套接字要读取的所需的数据超过一 TCP 数据包时 \(中等的网络，通常至少 1096 个字节的最大传输单位的范围\)。  如果可用数据的大小程度低于必要，等待所有数据接收和此时开始这次读取操作。  
  
 在下面的示例中，`m_dwExpected` 是用户所需接收的近似字节数。  假定，可以在代码中的其他位置声明它。  
  
 [!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/CPP/csocket-class_1.cpp)]  
  
> [!NOTE]
>  在使用 MFC 套接字在静态链接的 MFC 应用程序时的辅助线程，则必须对使用套接字初始化套接字库的每个线程的 `AfxSocketInit`。  默认情况下，`AfxSocketInit` 在主线程仅调用。  
  
 有关更多信息，请参见 [在 MFC 的 Windows 套接字](../../mfc/windows-sockets-in-mfc.md)，[Windows 套接字：使用套接字与存档](../../mfc/windows-sockets-using-sockets-with-archives.md)，[Windows 套接字：套接字具有如何的存档工作](../../mfc/windows-sockets-how-sockets-with-archives-work.md)，[Windows 套接字：操作的顺序](../../mfc/windows-sockets-sequence-of-operations.md)，[Windows 套接字：套接字的示例使用中的存档](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAsyncSocket](../../mfc/reference/casyncsocket-class.md)  
  
 `CSocket`  
  
## 要求  
 **标头：** afxsock.h  
  
## 请参阅  
 [CAsyncSocket Class](../../mfc/reference/casyncsocket-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket Class](../../mfc/reference/casyncsocket-class.md)   
 [CSocketFile Class](../../mfc/reference/csocketfile-class.md)