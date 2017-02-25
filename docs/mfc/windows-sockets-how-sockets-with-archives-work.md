---
title: "Windows 套接字：使用存档的套接字如何工作 | Microsoft Docs"
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
  - "套接字 [C++], 同步操作"
  - "套接字 [C++], 使用存档"
  - "同步状态套接字"
  - "两状态套接字对象"
  - "Windows 套接字 [C++], 同步"
  - "Windows 套接字 [C++], 使用存档"
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Windows 套接字：使用存档的套接字如何工作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明对象、[CSocket](../mfc/reference/csocket-class.md)[CSocketFile](../mfc/reference/csocketfile-class.md)[CArchive](../mfc/reference/carchive-class.md) 对象和对象的组合。Windows 套接字简化发送和接收数据。  
  
 文章 [Windows 套接字：套接字的示例使用已存档](../mfc/windows-sockets-example-of-sockets-using-archives.md) 存在 **PacketSerialize** 函数。  在 **PacketSerialize** 的示例工作的存档对象就像将 MFC 对象传递给函数。[序列化](../Topic/CObject::Serialize.md) 重要区别是套接字的存档，附加将不到标准 [CFile](../mfc/reference/cfile-class.md) 对象 \(通常与磁盘文件\)，但对 `CSocketFile` 对象。  而不是连接到磁盘文件，`CSocketFile` 对象连接到 `CSocket` 对象。  
  
 `CArchive` 对象管理的缓冲区。  当单元格 \(\) 时发送的存档缓冲区已满，则写出 `CFile` 对象关联缓冲区的内容。  刷新缓冲区的已存档附加到套接字发送消息与等效。  加载时接收 \(\) 存档缓冲区已满，`CFile` 对象在停止读取之前，缓冲区重新可用。  
  
 `CSocketFile` 类从 `CFile`派生，但是，它不支持 [CFile](../mfc/reference/cfile-class.md) 成员函数如定位功能 \(`Seek`、`GetLength`，`SetLength`，依此类推\)，锁的函数 \(`LockRange`，`UnlockRange`\)，或 `GetPosition` 函数。  任何 [CSocketFile](../mfc/reference/csocketfile-class.md) 对象必须执行将写入或读取字节序列出入关联的 `CSocket` 对象。  由于文件不包含的操作，比如 `Seek` 和 `GetPosition` 没有意义。  `CSocketFile` 从 `CFile`派生，因此，它通常会继承所有这些成员函数。  为了防止这一点，不支持 `CFile` 成员函数在 `CSocketFile` 重写引发 [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)。  
  
 其 `CSocket` 的 `CSocketFile` 对象调用成员函数对象发送或接收数据。  
  
 下图演示在这些对象之间的关系。通信的两侧。  
  
 ![CArchive、CSocketFile 和 CSocket](../Image/vc38IA1.gif "vc38IA1")  
CArchive、CSocketFile 和 CSocket  
  
 此清单复杂性的目的是防止您管理套接字的细节必要性。  在创建文件和套接字、存档，然后开始发送或接收数据通过插入到存档或提取它从存档。  [CArchive](../mfc/reference/carchive-class.md)、[CSocketFile](../mfc/reference/csocketfile-class.md)和 [CSocket](../mfc/reference/csocket-class.md) 在后台管理详细信息。  
  
 `CSocket` 对象实际上是两个状态对象：有时异步 \(状态\) 和通常有时同步。  在其异步的状态，套接字可以接收从框架的异步的通知。  但是，如在一操作时接收或发送套接字数据已同步的。  这意味着套接字应接收不进一步的通知，直到异步同步操作完成。  由于开关模式，可以，例如，执行与下面类似的内容：  
  
 [!CODE [NVC_MFCSimpleSocket#2](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCSimpleSocket#2)]  
  
 如果 `CSocket` 未实现为一个状态对象，接收同类的通知事件可能是可以的，在处理早期通知时。  例如，您可以获取 `OnReceive`，通知在处理 `OnReceive`时。  在以上代码段，从存档的 `str` 可能导致递归。  通过切换状态，`CSocket` 通过防止其他通知以递归。  一般规则是在不通知中的通知。  
  
> [!NOTE]
>  文件，而无需 `CArchive` 对象，`CSocketFile` 还使用，而 \(受限制\)。  默认情况下，`CSocketFile` 构造函数的 `bArchiveCompatible` 参数是 **TRUE**。  这指定对象文件函数用于存档。  若要使用该对象，而无需将，请在 `bArchiveCompatible` 参数中传递 **FALSE**。  
  
 在其“Archive”兼容模式，`CSocketFile` 对象可以提供更好的性能并减少死锁“的危险”。发生死锁，当发送和接收的套接字相互等待，或者等待一常见资源。  这种情况可能发生，如果 `CArchive` 对象与 `CSocketFile` 一起使用它对 `CFile` 对象的方式。  `CFile`存档，可以假定，如果它接收的字节比请求，已到达文件尾。  `CSocketFile`，但是，数据为基于的消息；缓冲区小于请求的字节数不暗含文件尾可以包含各种信息，因此，会收到。  应用程序在不阻止，则可以使用 `CFile`，因此，它可以连续消息，直至读取缓冲区的缓冲区为空时。  `CArchive` 中的 [IsBufferEmpty](../Topic/CArchive::IsBufferEmpty.md) 函数。在这种情况下监视存档的缓冲区的状态十分有用。  
  
 有关更多信息，请参见 [Windows 套接字：将存档的套接字](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
## 请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)   
 [CObject::Serialize](../Topic/CObject::Serialize.md)