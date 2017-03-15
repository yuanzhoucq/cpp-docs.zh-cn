---
title: "Windows 套接字：使用存档的套接字的示例 | Microsoft Docs"
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
  - "示例 [MFC], Windows 套接字"
  - "套接字 [C++], 使用存档"
  - "Windows 套接字 [C++], 使用存档"
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Windows 套接字：使用存档的套接字的示例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文代表使用 [CSocket](../mfc/reference/csocket-class.md)类的实例。  示例使用 `CArchive` 对象通过套接字序列化数据。  注意这不是文档序列化方式文件。  
  
 下面的示例演示如何通过 `CSocket` 对象使用存档发送和接收数据。  该示例设计，以便应用程序 \(在同一计算机或网络上不同的计算机\) 交换数据的两个实例。  一个实例发送数据，其他实例接收并执行。  任何应用程序可启动交换，因此，为可以做为其他应用程序的服务器或客户端。  以下功能在应用程序的视图类中定义：  
  
 [!CODE [NVC_MFCSimpleSocket#1](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCSimpleSocket#1)]  
  
 有关此示例的最重要的功能是 MFC `Serialize` 函数的结构并行。  **PacketSerialize** 成员函数包含 **else** 子句的 **if** 语句。  函数接收两个 [CArchive](../mfc/reference/carchive-class.md) 引用作为参数：`arData` 和 `arAck`。  如果 `arData` 存档对象为存储 \(发送\)，**if**分支执行；否则，如果`arData`用于加载 \(接收\) 设置，函数采用 **else** 分支。  有关 MFC 序列化的详细信息，请参见 [序列化](../mfc/how-to-make-a-type-safe-collection.md)。  
  
> [!NOTE]
>  假定存档 `arAck` 对象是与 `arData`相反。  如果 `arData` 为发送，`arAck` 接收，并且，计数器为 true。  
  
 对于发送，示例函数循环指定的次数，每次生成一些关于演示目的的随机数据。  应用程序将获取某些源的真实数据，如文件。  `arData` 存档粘贴运算符 \(**\<\<**\) 用于将发送三个连续出现的区块流：  
  
-   指定数据的性质的“标题”\(在此例中，`bValue` 的变量值，多少复制将发送\)。  
  
     此示例中的两项都是随机生成。  
  
-   数据的副本的指定的数目。  
  
     内部 **for** 循环将发送 `bValue` 的指定的时间数目。  
  
-   字符串`strText` 是该接收器显示给用户的。  
  
 对于接收，函数操作类似，除了使用存档提取运算符 \(**\>\>**\) 从存档获取数据。  接收应用程序验证数据，显示最终“接收的消息”，然后发送应用程序显示“发送”消息。  
  
 在此通信模型中，”接收“字，`strText` 变量发送的消息，用于显示在通信的另一端，因此，它告诉接收用户已接收的数据包的数量。  接收器响应为“发送”的相似字符串，在原始发件人屏幕的显示。  两个字符串指示成功的通信已经发生。  
  
> [!CAUTION]
>  如果编写 MFC 客户端程序与建立的 \(非 MFC\) 服务器通信，绝对不要通过档案传递 C\+\+ 对象。  除非服务器是知道要发送对象的类型的 MFC 应用程序，否则它无法接收和反序列化对象。  文章的一个例子[Windows 套接字：字节顺序](../mfc/windows-sockets-byte-ordering.md) 显示了此类型的关系。  
  
 有关更多信息，请参见Windows套接字规范：**htonl**, **htons**, **ntohl**, **ntohs**。  此外，有关详细信息，请参阅：  
  
-   [Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows 套接字：背景](../mfc/windows-sockets-background.md)  
  
## 请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)   
 [CArchive::IsStoring](../Topic/CArchive::IsStoring.md)   
 [CArchive::operator \<\<](../Topic/CArchive::operator%20%3C%3C.md)   
 [CArchive::operator \>\>](../Topic/CArchive::operator%20%3E%3E.md)   
 [CArchive::Flush](../Topic/CArchive::Flush.md)   
 [CObject::Serialize](../Topic/CObject::Serialize.md)