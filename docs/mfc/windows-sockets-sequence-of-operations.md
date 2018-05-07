---
title: Windows 套接字： 操作顺序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], operations
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- sockets [MFC], operations
- stream sockets [MFC]
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93fe2221e25951a53340d5da97f7d5c48ce477cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="windows-sockets-sequence-of-operations"></a>Windows 套接字：操作顺序
并排比较，本文说明了用于服务器套接字和客户端套接字的操作顺序。 因为套接字使用`CArchive`对象，它们都不一定[流套接字](../mfc/windows-sockets-stream-sockets.md)。  
  
## <a name="sequence-of-operations-for-a-stream-socket-communication"></a>用于流套接字通信的操作顺序  
 构造的时点之前`CSocketFile`对象，按以下顺序为准确 （有一些参数区别） 两个`CAsyncSocket`和`CSocket`。 从那一刻开始，该序列是严格的`CSocket`。 下表说明了用于设置客户端和服务器之间的通信的操作顺序。  
  
### <a name="setting-up-communication-between-a-server-and-a-client"></a>设置服务器和客户端之间的通信  
  
|服务器|客户端|  
|------------|------------|  
|`// construct a socket`<br /><br /> `CSocket sockSrvr;`|`// construct a socket`<br /><br /> `CSocket sockClient;`|  
|`// create the SOCKET`<br /><br /> `sockSrvr.Create(nPort);`1,2|`// create the SOCKET`<br /><br /> `sockClient.Create( );`2|  
|`// start listening`<br /><br /> `sockSrvr.Listen( );`||  
||`// seek a connection`<br /><br /> `sockClient.Connect(strAddr, nPort);`3,4|  
|`// construct a new, empty socket`<br /><br /> `CSocket sockRecv;`<br /><br /> `// accept connection`<br /><br /> `sockSrvr.Accept( sockRecv );` 5||  
|`// construct file object`<br /><br /> `CSocketFile file(&sockRecv);`|`// construct file object`<br /><br /> `CSocketFile file(&sockClient);`|  
|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> -或-<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> -或这两个-|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> -或-<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> -或这两个-|  
|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> -或-<br /><br /> `arOut << dwValue;`6|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> -或-<br /><br /> `arOut << dwValue;`6|  
  
 1. 其中`nPort`是端口号。 请参阅[Windows 套接字： 端口和套接字地址](../mfc/windows-sockets-ports-and-socket-addresses.md)有关端口的详细信息。  
  
 2. 服务器必须始终指定的端口，以便客户端可以连接。 **创建**调用有时也指定一个地址。 在客户端，使用默认参数，这要求 MFC 使用的任何可用端口。  
  
 3. 其中`nPort`是端口号和*strAddr*是机地址或 Internet 协议 (IP) 地址。  
  
 4. 机地址可以采用多种形式:"ftp.microsoft.com"、"microsoft.com"。 IP 地址使用"以点分隔数"的窗体"如 127.54.67.32"。 **连接**函数检查以查看是否地址圆点分隔的数 （尽管它不会检查以确保该数字是网络上有效的计算机）。 如果没有，**连接**假定的某种其他形式的计算机名称。  
  
 5. 当调用**接受**在服务器端中，将传递对新的套接字对象的引用。 首先，必须先构造此对象但不是调用**创建**它。 请记住，如果此套接字对象超出范围，该连接将关闭。 MFC 连接到的新对象**套接字**处理。 您可以构造在堆栈上，如所示，或在堆上的套接字。  
  
 6. 存档和套接字文件关闭时，它们超出范围。 套接字对象的析构函数还调用[关闭](../mfc/reference/casyncsocket-class.md#close)为套接字对象超出范围或删除的对象时的成员函数。  
  
## <a name="additional-notes-about-the-sequence"></a>有关序列的其他说明  
 对于流套接字是上表中显示的调用顺序。 不需要数据报套接字，即无连接[CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect)，[侦听](../mfc/reference/casyncsocket-class.md#listen)，和[接受](../mfc/reference/casyncsocket-class.md#accept)调用 (尽管你可以选择使用**连接**)。 相反，如果你使用的类`CAsyncSocket`，数据报套接字使用`CAsyncSocket::SendTo`和`ReceiveFrom`成员函数。 (如果你使用**连接**借助数据报套接字，你使用**发送**和**接收**。)因为`CArchive`不起作用不使用数据报，与`CSocket`以数据报套接字是否存档。  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md)不支持的所有`CFile`的功能;`CFile`成员，如`Seek`，这使套接字通信，没有意义都不可用。 因此，某些默认 MFC`Serialize`函数与不兼容`CSocketFile`。 这是尤其如此`CEditView`类。 不应尝试序列化`CEditView`数据通过`CArchive`对象附加到`CSocketFile`对象使用`CEditView::SerializeRaw`; 使用**CEditView::Serialize**改为 （未记录）。 [SerializeRaw](../mfc/reference/ceditview-class.md#serializeraw)函数需要的文件对象，以包含函数，如`Seek`，则该`CSocketFile`不支持。  
  
 有关详细信息，请参见:  
  
-   [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows 套接字：使用 CAsyncSocket 类](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows 套接字：端口和套接字地址](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
-   [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)   
 [CSocket 类](../mfc/reference/csocket-class.md)   
 [CAsyncSocket::Create](../mfc/reference/casyncsocket-class.md#create)   
 [CAsyncSocket::Close](../mfc/reference/casyncsocket-class.md#close)

