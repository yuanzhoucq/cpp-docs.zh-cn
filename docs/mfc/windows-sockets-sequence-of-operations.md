---
title: "Windows 套接字：操作顺序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "套接字 [C++], 操作"
  - "套接字 [C++], 流套接字"
  - "流套接字 [C++]"
  - "Windows 套接字 [C++], 操作"
  - "Windows 套接字 [C++], 流套接字"
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Windows 套接字：操作顺序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文一起说明，服务器和客户套接字的操作序列。  由于套接字使用 `CArchive` 对象，所以它们都是 [stream sockets](../mfc/windows-sockets-stream-sockets.md) （流套接字）。  
  
## 流套接字通信的操作步骤  
 构造 `CSocketFile` 对象，下面的操作`CAsyncSocket` 和 `CSocket`是准确 \(有某些个参数差异\)。  之后，`CSocket` 操作步骤是严格的。  下表阐释了设置客户端和服务器之间的通信的操作序列。  
  
### 设置服务器和客户端之间通信  
  
|服务器|客户端|  
|---------|---------|  
|`// construct a socket`<br /><br /> `CSocket sockSrvr;`|`// construct a socket`<br /><br /> `CSocket sockClient;`|  
|`// create the SOCKET`<br /><br /> `sockSrvr.Create(nPort);`1,2|`// create the SOCKET`<br /><br /> `sockClient.Create( );`2|  
|`// start listening`<br /><br /> `sockSrvr.Listen( );`||  
||`// seek a connection`<br /><br /> `sockClient.Connect(strAddr, nPort);`3,4|  
|`// construct a new, empty socket`<br /><br /> `CSocket sockRecv;`<br /><br /> `// accept connection`<br /><br /> `sockSrvr.Accept( sockRecv );` 5||  
|`// construct file object`<br /><br /> `CSocketFile file(&sockRecv);`|`// construct file object`<br /><br /> `CSocketFile file(&sockClient);`|  
|`// construct an archive`<br /><br /> `CArchive arIn(&file,`  `CArchive::load);`<br /><br /> \- 或 \-<br /><br /> `CArchive arOut(&file,`  `CArchive::store);`<br /><br /> – 或两者 –|`// construct an archive`<br /><br /> `CArchive arIn(&file,`  `CArchive::load);`<br /><br /> \- 或 \-<br /><br /> `CArchive arOut(&file,`  `CArchive::store);`<br /><br /> – 或两者 –|  
|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> \- 或 \-<br /><br /> `arOut << dwValue;`6|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> \- 或 \-<br /><br /> `arOut << dwValue;`6|  
  
 1.  其中 `nPort` 为端口号。  有关端口的详细信息，请参见 [Windows 套接字：端口和套接字地址](../mfc/windows-sockets-ports-and-socket-addresses.md)。  
  
 2.  服务器必须始终指定一个端口，供客户端连接。  **创建** 调用有时也指定地址。  在客户端，请使用默认参数，该操作请求 MFC 使用任何可用端口。  
  
 3.  其中 `nPort` 为端口号， *strAddr* 是计算机地址或 Internet 协议 \(IP\) 地址。  
  
 4.  计算机地址可以采用多种形式：“ftp.microsoft.com”，“microsoft.com”。  IP 地址使用“点缀数字”格式 "127.54.67.32”。  **Connect** 函数检测此地址是否为点缀数字 \(尽管它不检查以确保数字是在网络上有效的\)。  如果不是，**Connect** 会假设采用其他计算机名称的形式之一。  
  
 5.  如果在服务器端调用 **Accept** 时，您传递了一个引用给新的套接字对象。  必须先构建此对象，但是不要调用它的 **创建**。  记住，如果此套接字对象超出范围，连接将关闭。  MFC 连接新对象到 **SOCKET** 句柄。  您可以构造套接字在栈上，或者堆上，见演示。  
  
 6.  当它们超出范围时，将关闭文档和套接字文件。  当对象超出范围或删除时，该套接字对象的析构函数也为套接字对象调用 [Close](../Topic/CAsyncSocket::Close.md) 成员函数。  
  
## 有关序列的其他说明  
 在前面的表中用于流套接字显示的调用序列。  数据报套接字，无连接的，而不需要 [CAsyncSocket::Connect](../Topic/CAsyncSocket::Connect.md)[Listen](../Topic/CAsyncSocket::Listen.md) 和 [Accept](../Topic/CAsyncSocket::Accept.md) 调用 \(虽然您可以选择使用 **Connect**\)。  相反，如果使用类 `CAsyncSocket`，该数据报套接字使用 `CAsyncSocket::SendTo` 和 `ReceiveFrom` 成员函数。\(如果您使用数据报套接字的 **Connect**，则使用 **Send** 和 **Receive**。\)由于 `CArchive` 不用于数据报，如果是数据报，请勿与存档一起使用套接字 `CSocket`。  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md) 不支持所有 `CFile` 函数；`CFile` 成员如 `Seek`，对套接字通信没有意义，是无效的。  因此，一些默认 MFC `Serialize` 函数与 `CSocketFile` 不兼容。  `CEditView` 类尤其如此。  不应尝试通过使用 `CEditView::SerializeRaw` 序列化 `CEditView` 数据通过`CArchive` 对象将其附加到 `CSocketFile` 对象；使用 **CEditView::Serialize** 代替\(非文档\)。  [SerializeRaw](../Topic/CEditView::SerializeRaw.md) 函数期望文件对象含有如 `Seek` 函数，然而 `CSocketFile` 不支持。  
  
 有关详细信息，请参阅：  
  
-   [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows 套接字：端口和套接字地址](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
-   [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)  
  
## 请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)   
 [CSocket Class](../mfc/reference/csocket-class.md)   
 [CAsyncSocket::Create](../Topic/CAsyncSocket::Create.md)   
 [CAsyncSocket::Close](../Topic/CAsyncSocket::Close.md)