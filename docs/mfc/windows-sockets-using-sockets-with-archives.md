---
title: "Windows 套接字：对存档使用套接字 | Microsoft Docs"
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
  - "存档 [C++], 和 Windows 套接字"
  - "CSocket 类, 编程模型"
  - "套接字 [C++], 使用存档"
  - "Windows 套接字 [C++], 存档"
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Windows 套接字：对存档使用套接字
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文介绍[CSocket 编程模型](#_core_the_csocket_programming_model) 类 [CSocket](../mfc/reference/csocket-class.md) 提供比类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)抽象级别更高的套接字支持。  `CSocket`使用MFC 序列化协议版本将数据传出，来自通过MFC 对象[CArchive](../mfc/reference/carchive-class.md)对象套接字数据。  `CSocket` 提供锁定 \(在后台管理窗口消息\) 并可以访问 `CArchive`，管理通信的许多特性，您必须亲自使用原始的 API 或 `CAsyncSocket`类。  
  
> [!TIP]
>  您可以单独使用 `CSocket` 类，`CAsyncSocket`用作更方便的版本，但是，最简单的编程模型是使用 `CArchive` 对象的 `CSocket`。  
  
 有关套接字实现使用的存档如何工作的更多信息，请参见 [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)。  有关代码示例，请参见[Windows 套接字：操作顺序](../mfc/windows-sockets-sequence-of-operations.md)和 [Windows 套接字：使用存档的套接字的示例](../mfc/windows-sockets-example-of-sockets-using-archives.md)。  有关可以通过派生自己获取类从套接字类的某些功能的信息，请参见 [Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)。  
  
> [!NOTE]
>  如果编写 MFC 客户端程序与建立 \(非 MFC\) 服务器通信，绝对不要通过档案传递 C\+\+ 对象。  除非服务器是知道要发送对象类型的 MFC 应用程序，否则它无法接收和反序列化对象。  关于通信材料与非 MFC 应用程序，另请参见文章 [Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)  
  
##  <a name="_core_the_csocket_programming_model"></a> CSocket 编程模型  
 使用 `CSocket` 对象涉及创建和将几个 MFC 类对象关联到一起。  在以下一般过程，每个步骤均由服务器套接字和客户套接字采用，除了步骤 3，每套接字类型需要其他操作。  
  
> [!TIP]
>  运行时，当客户端应用程序寻求连接时，服务器应用程序开始通常先准备好并“侦听”。  如果服务器未就绪，当客户尝试连接，则通常需要用户应用程序尝试再次连接。  
  
#### 设置服务器和客户之间的通信使用安全套接字  
  
1.  构造 [](../mfc/reference/csocket-class.md "CSocket Class") 对象。  
  
2.  使用对象创建基础 **SOCKET** 句柄。  
  
     对于 `CSocket`，客户端对象，除非您需要数据报套接字，则通常应使用默认参数到 [创建](../Topic/CAsyncSocket::Create.md)。  对于 `CSocket` 服务器对象，则在 **创建** 调用都必须指定端口。  
  
    > [!NOTE]
    >  `CArchive` 不适用于数据报套接字。  如果想要为数据报套接字使用 `CSocket`，必须使用类，因为您将使用 `CAsyncSocket`，即，无需存档。  由于数据报是不可靠 \(没有确保到达以及可能重复或退出序列\)，它们通过存档与序列化兼容。  希望序列化操作可靠以及按顺序完成。  如果您尝试对数据报与 `CArchive` 对象一起使用 `CSocket`，MFC 断言失败。  
  
3.  如果套接字是客户端，请调用 [CAsyncSocket::Connect](../Topic/CAsyncSocket::Connect.md) 连接服务器套接字的套接字对象。  
  
     \- 或 \-  
  
     如果套接字是服务器，开始调用 [CAsyncSocket::Listen](../Topic/CAsyncSocket::Listen.md) 侦听来自客户端的连接尝试。  连接在收到请求之后，通过调用 [CAsyncSocket::Accept](../Topic/CAsyncSocket::Accept.md)接受。  
  
    > [!NOTE]
    >  **接受** 成员函数采用到新，空 `CSocket` 对象的引用作为参数。  在调用 **接受**之前，您必须构建此对象。  如果此套接字对象超出范围，将关闭这些连接。  请勿调用套接此新 Word 对象的 **创建**。  
  
4.  创建一个[CSocketFile](../mfc/reference/csocketfile-class.md) 对象，将 `CSocket` 对象与它关联。  
  
5.  创建加载 \(接收\) 或存储 \(发送\) 数据的[CArchive](../mfc/reference/carchive-class.md)对象。  存档与`CSocketFile`对象关联。  
  
     记住`CArchive` 在数据报套接字中无效。  
  
6.  使用传递数据的 `CArchive` 对象在客户端和服务器之间套接字。  
  
     记住特定 `CArchive` 对象只将一方向的数据：用于加载 \(接收\) 或存储 \(发送\)。  有时，将使用两个 `CArchive` 对象：一个发送数据，其他的接收确认书。  
  
     在接受连接并将存档之后，可以执行此任务作为验证密码。  
  
7.  销毁、存档、套接字文件和套接 Word 对象。  
  
    > [!NOTE]
    >  具体而言 `CArchive` 类提供 `IsBufferEmpty` 成员函数可与 `CSocket`类一起使用。  例如，如果缓冲区包含多个数据信息需要一直循环，直到所有读取，并清空缓冲区。  否则，一通知具有接收的数据可能不会延迟。  使用 `IsBufferEmpty` 确保检索所有数据。  
  
 文章 [Windows 套接字：操作顺序](../mfc/windows-sockets-sequence-of-operations.md) 阐释此过程的双方使用示例的代码。  
  
 有关详细信息，请参阅：  
  
-   [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)  
  
## 请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)   
 [CSocket::Create](../Topic/CSocket::Create.md)