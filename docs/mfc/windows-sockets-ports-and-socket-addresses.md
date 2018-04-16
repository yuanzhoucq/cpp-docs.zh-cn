---
title: "Windows 套接字： 端口和套接字地址 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c7b2e15761815b75ba8001ad4eb5a5c276f5056
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows 套接字：端口和套接字地址
此文章介绍了使用术语"端口"和"地址"作为用于 Windows 套接字。  
  
##  <a name="_core_port"></a>端口  
 端口标识可以为其提供服务的唯一进程。 在存在的上下文中，端口是与支持 Windows 套接字的应用程序相关联。 思路是来唯一地标识每个 Windows 套接字应用程序，因此你可以在同一时间的计算机上运行的多个 Windows 套接字应用程序。  
  
 某些端口被保留供公共服务，如 FTP。 应避免使用这些端口，除非你要提供该类型的服务。 Windows 套接字规范详细介绍这些保留的端口。 WINSOCK 文件。H 也会列出它们。  
  
 若要让 Windows 套接字 DLL 为您选择可用端口，请为端口值传递 0。 MFC 选择大于 1024 十进制的端口值。 你可以检索 MFC 选择通过调用的端口值[CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname)成员函数。  
  
##  <a name="_core_socket_address"></a>套接字地址  
 每个套接字对象都与网络上的 Internet 协议 (IP) 地址相关联。 通常，地址是计算机名称，如"ftp.microsoft.com"或以点分隔的数字，如"128.56.22.8"。  
  
 当您寻求创建套接字时，通常不需要指定你自己的地址。  
  
> [!NOTE]
>  很可能是您的计算机有多个网卡 （或者你的应用程序可能有一天此类的计算机上运行），每个元素表示其他网络。 如果是这样，你可能需要提供要指定套接字将使用的网络卡的地址。 这是某些高级的用法且可能可移植性问题。  
  
 有关详细信息，请参见:  
  
-   [Windows 套接字：使用 CAsyncSocket 类](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)

