---
title: "Windows 套接字：流套接字 | Microsoft Docs"
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
  - "套接字 [C++], 流套接字"
  - "流套接字 [C++]"
  - "Windows 套接字 [C++], 流套接字"
ms.assetid: 31faaa34-a995-493f-a30b-b8115293d619
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Windows 套接字：流套接字
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文描述流套接字，是两个Windows套接字类型之一。\(另外一个类型是[数据报套接字](../mfc/windows-sockets-datagram-sockets.md)。\)  
  
 流套接字提供没有记录边界的数据流：一种双向的字节流（应用程序是全双工：它能通过套接字传输和接收）。  流可以用于传送顺序的，无重复的数据。“顺序的”表示数据包是按顺序发送的。“非重复性”意味着你只能获取特定数据包一次。流信息的接收是有保障的，并且流非常适合于处理大量数据。  
  
 网络传输层会破坏或组合数据，将其数据放入到大小合适的包数据包中。  类`CSocket`会为你处理装箱和拆箱操作。  
  
 基于显式连接的流：套接字 A 请求一个到套接字B的连接；套接字 B 接受或拒绝连接请求。  
  
 打电话为流提供了一个很好的类比。  在正常情况下，接收方听到的顺序就是您说话的顺序，没有重复，没有丢失。  流套接字很合适，比如，为了实现文件传输协议 \(FTP\)，这个协议可以传输任意大小的ASCII或二进制文件。  
  
 当需要确保数据必须到达，并且数据很大时，流套接字要优于数据报套接字。  有关流套接字的更多信息，请参见 Windows 套接字规范。  在[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中，该规范是可用的。  
  
 为了向所有的接收套接字广播，使用流套接字是要优于使用数据报套接字的应用程序的，因为  
  
-   广播模型会受到网络洪水\(或“风暴”\)的问题。  
  
-   随后使用的客户端服务器模式更加高效。  
  
-   流模型提供可靠的数据传输，数据报模型则不能。  
  
-   最终模型利用了在Unicode和ANSI套接字应用程序间通信的能力，是类CArchive赋予类CSocket的。  
  
    > [!NOTE]
    >  如果使用 `CSocket`类，则必须使用流。  如果指定套接字类型为 **SOCK\_DGRAM**，则MFC断言失败。  
  
## 请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)   
 [Windows 套接字：背景](../mfc/windows-sockets-background.md)