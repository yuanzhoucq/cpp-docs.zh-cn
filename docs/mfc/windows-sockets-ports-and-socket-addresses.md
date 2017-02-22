---
title: "Windows 套接字：端口和套接字地址 | Microsoft Docs"
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
  - "地址 [C++], 套接字"
  - "端口 [C++]"
  - "端口 [C++], 定义"
  - "套接字 [C++], 地址"
  - "套接字 [C++], 端口"
  - "Windows 套接字 [C++], 地址"
  - "Windows 套接字 [C++], 端口"
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Windows 套接字：端口和套接字地址
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明术语“迁移”，并且“解决”。使用 Windows 套接字。  
  
##  <a name="_core_port"></a> 端口  
 端口可以提供确定服务的单个进程。  在当前上下文，端口与支持 Windows 套接 Word 的应用程序。  目的是唯一标识每 Windows 套接 Word 应用程序，以便您可以同时运行多计算机上的 Windows 套接字应用程序。  
  
 一些端口用于常见的服务是保留的关键字，例如 FTP。  除非提供，该服务应避免使用这些端口。  Windows 套接字详细规范这些保留的端口。  文件 WINSOCK.H 还列出它们。  
  
 若要使 Windows 套接字 DLL 选择您的活动端口，将 0 作为端口值。  MFC 选择端口值大的小数大于 1,024。  可以检索 MFC 通过调用 [CAsyncSocket::GetSockName](../Topic/CAsyncSocket::GetSockName.md) 成员函数选择的端口值。  
  
##  <a name="_core_socket_address"></a> 套接字地址  
 每套接字对象与网络上的 Internet 协议 \(IP\) 地址。  通常，地址是一个计算机名称，如“”或 ftp.microsoft.com 一个带项目数，如“128.56.22.8”。  
  
 在寻求创建套接字时，通常不需要自行指定的地址。  
  
> [!NOTE]
>  可能的计算机上有多个网络卡 \(或应用程序在此类计算机可能运行某天\)，表示不同的网络的每个。  在这种情况下，您可能需要提供地址指定哪个网卡套接字是使用。  这确保是高级使用情况和可能的可移植性问题。  
  
 有关详细信息，请参阅：  
  
-   [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows 套接字：将存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)  
  
## 请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)