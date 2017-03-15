---
title: "Windows 套接字：使用类 CAsyncSocket | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CAsyncSocket"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAsyncSocket 类, 编程模型"
  - "SOCKET 句柄"
  - "套接字 [C++], 异步操作"
  - "套接字 [C++], 在 Unicode 和 MBCS 字符串之间转换"
  - "Windows 套接字 [C++], 异步"
  - "Windows 套接字 [C++], 转换 Unicode 和 MBCS 字符串"
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Windows 套接字：使用类 CAsyncSocket
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明如何使用类。[CAsyncSocket](../mfc/reference/casyncsocket-class.md) 请注意此类封装 Windows 套接字 API 在很低。  `CAsyncSocket` 由详细知道网络通信的程序员使用，但需要回调使用网络事件通知的。  基于此假设，本文只提供的基本指令。  则可能应考虑使用 `CAsyncSocket`，则需要 Windows 套接字的方便处理在 MFC 应用程序的多个网络协议，但是不想为了牺牲灵活性。  还可能认为您可以比使用 `CSocket`类可以通过直接通信编程可以获得更佳的效率"更为一般性的备用模型。  
  
 `CAsyncSocket`记录在*MFC Reference*中。  Visual C\+\+ 还提供 Windows 套接字规范，位于 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  详细信息留到您。  Visual C\+\+ 不提供 `CAsyncSocket`的示例应用程序。  
  
 如果不指定熟知有关网络通信不需简单解决方案，使用 `CArchive` 对象的类。[CSocket](../mfc/reference/csocket-class.md) 参见 [Windows 套接字：将存档的套接字](../mfc/windows-sockets-using-sockets-with-archives.md)。更多信息。  
  
 本文包含：  
  
-   创建和使用 `CAsyncSocket` 对象。  
  
-   [与 CAsyncSocket 的职责](#_core_your_responsibilities_with_casyncsocket)。  
  
##  <a name="_core_creating_and_using_a_casyncsocket_object"></a> 创建和使用 CAsyncSocket 对象  
  
#### 使用 CAsyncSocket  
  
1.  构造对象并使用 [CAsyncSocket](../mfc/reference/casyncsocket-class.md) 对象创建基础 **SOCKET** 句柄。  
  
     套接字创建执行两阶段 MFC 构造形式。  
  
     例如：  
  
     [!CODE [NVC_MFCSimpleSocket#3](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCSimpleSocket#3)]  
  
     \- 或 \-  
  
     [!CODE [NVC_MFCSimpleSocket#4](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCSimpleSocket#4)]  
  
     上面第一的构造函数在堆栈上创建 `CAsyncSocket` 对象。  第二个构造函数创建堆的 `CAsyncSocket`。  上面第一个 [创建](../Topic/CAsyncSocket::Create.md) 调用使用默认参数创建流套接字。  第二个调用 **创建** 创建具有指定端口和地址的数据报套接字。\(您可以使用任一构造方法的 **创建** 版本。）  
  
     对 **创建** 的参数为：  
  
    -   “端口”:短的整数。  
  
         对于服务器套接字，必须指定端口。  对于套接字，客户通常接受此参数的默认值，允许 Windows 套接字选择端口。  
  
    -   套接字类型：**SOCK\_STREAM** \(默认值\) 或 **SOCK\_DGRAM**。  
  
    -   套接字“Address”，如“”或 ftp.microsoft.com“128.56.22.8”。  
  
         这种网络上的 Internet 协议 \(IP\) 地址。  您可能总是将依赖于该参数的默认值。  
  
     术语“端口套接字”和“地址”。[Windows 套接字：端口和套接字 Addresses](../mfc/windows-sockets-ports-and-socket-addresses.md)解释。  
  
2.  如果套接字是客户，可以使用 [CAsyncSocket::Connect](../Topic/CAsyncSocket::Connect.md)，请连接服务器套接字的套接字。对象，  
  
     \- 或 \-  
  
     如果套接字是服务器，请设置套接字开始侦听 \(带有 [CAsyncSocket::Listen](../Topic/CAsyncSocket::Listen.md)\) 用于从客户端连接尝试。  在收到请求之后连接，请接受它与 [CAsyncSocket::Accept](../Topic/CAsyncSocket::Accept.md)。  
  
     在接受连接后，可以执行此任务。验证密码。  
  
    > [!NOTE]
    >  **接受** 成员函数采用到新，空 `CSocket` 对象的引用作为参数。  在调用 **接受**之前，您必须构建此对象。  如果此套接字对象超出范围，将关闭这些连接。  请勿调用套接此新的 Word 对象的 **创建**。  有关示例，请参见的文章 [Windows 套接字：操作的顺序](../mfc/windows-sockets-sequence-of-operations.md)。  
  
3.  通过调用封装 Windows 套接字 API 函数的 `CAsyncSocket` 对象的成员函数与其他套接字的通信。  
  
     参见 Windows 套接字规范和类" *MFC 参考"中的*[CAsyncSocket](../mfc/reference/casyncsocket-class.md)。  
  
4.  销毁 `CAsyncSocket` 对象。  
  
     如果在堆栈上创建了套接字对象，其调用析构函数的函数，当包含超出范围。  使用 **new** 运算符，如果要创建在堆的套接字对象，就得销毁对象，使用 **删除** 运算符。  
  
     析构函数在销毁对象前调用对象的成员函数。[关闭](../Topic/CAsyncSocket::Close.md)  
  
 有关此序列的代码示例 \(实际上为 `CSocket` 对象\)，请参见 [Windows 套接字：操作的顺序](../mfc/windows-sockets-sequence-of-operations.md)。  
  
##  <a name="_core_your_responsibilities_with_casyncsocket"></a> 你的CAsyncSocket 的职责。  
 在 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)类创建对象时，对象封装 Windows **SOCKET** 句柄并提供该句柄的操作。  当您使用 `CAsyncSocket`时，必须处理可能面临，则直接使用 API 的所有问题。  例如：  
  
-   “阻止”方案。  
  
-   发送和接收的计算机之间的字节顺序差异。  
  
-   转换在 Unicode 和多字节字符集 \(MBCS\) 字符串之间。  
  
 有关这些术语的定义和附加信息，请参见 [Windows 套接字：阻止](../mfc/windows-sockets-blocking.md)，[Windows 套接字：字节顺序](../mfc/windows-sockets-byte-ordering.md)，[Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)。  
  
 尽管这些问题，类 **CAsycnSocket** 可能为您正确的选择，如果应用程序要求所有的灵活性和控件可以获取。  否则，应考虑使用 `CSocket` 类。  `CSocket` 隐藏您从大量的详细信息：它正在发送 Windows 消息在调用期间锁定并可以访问 `CArchive`，管理字节顺序差异和字符串转换您的。  
  
 有关详细信息，请参阅：  
  
-   [Windows 套接字：背景](../mfc/windows-sockets-background.md)  
  
-   [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)  
  
## 请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)