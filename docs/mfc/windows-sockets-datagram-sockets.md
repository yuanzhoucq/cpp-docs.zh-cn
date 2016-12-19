---
title: "Windows 套接字：数据报套接字 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数据报套接字 [C++]"
  - "套接字 [C++], 双向数据流"
  - "套接字 [C++], 数据报"
  - "Windows 套接字 [C++], 双向数据流"
  - "Windows 套接字 [C++], 数据报"
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows 套接字：数据报套接字
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文介绍数据报套接字，可用两个 Windows 套接字的类型之一。\(其他类型为 [流套接字](../mfc/windows-sockets-stream-sockets.md)。\)  
  
 数据报套接字支持没有确保排序或 unduplicated 的双向数据流。  数据报也不保证会是可靠；它们可能无法达到。  数据报数据可能达到中失败和副本可能，但在数据记录的边界，而记录，只要小于接收器的内部大小限制。  您负责管理先后顺序和可靠性。可靠性 \(往往是好、在局域网 \[\]，但这样小于在 \[\] 广域网 WAN，例如 Internet。\)  
  
 数据报“无连接”，即，显式连接未生成；将信息发送数据报到指定的套接字，并可以接收来自指定的套接字的消息。  
  
 数据报套接字的网络系统时钟保持示例是在中同步的应用程序。  这演示数据报套接字的其他功能。那些至少设置的：到大量的网络地址的消息广播。  
  
 数据报套接字数据流的方向与记录套接字好。  有关数据报套接字的更多信息，请参见 Windows 套接字规范，[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中可用。  
  
## 请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)   
 [Windows 套接字：背景](../mfc/windows-sockets-background.md)