---
title: "Windows 套接字：背景 | Microsoft Docs"
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
  - "通信 [C++], 域"
  - "数据类型 [C++], 套接字"
  - "数据报套接字 [C++]"
  - "电子邮件 [C++]"
  - "电子邮件 [C++], 编程"
  - "Internet 协议套件"
  - "邮件 [C++]"
  - "邮件 [C++], 编程"
  - "面向记录的数据 [C++]"
  - "顺序数据流"
  - "SOCKET 句柄"
  - "套接字 [C++], 流套接字"
  - "流套接字 [C++]"
  - "Windows 套接字 [C++], 流套接字"
  - "X 窗口服务器"
ms.assetid: f60d4ed2-bf23-4a0e-98d2-fee77e8473dd
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows 套接字：背景
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明 Windows 套接字的特性和用途。  文章还包括：  
  
-   [定义 “套接字”](#_core_definition_of_a_socket)。  
  
-   [描述该套接字的图柄数据类型](#_core_the_socket_data_type)。  
  
-   [描述套接字的用法](#_core_uses_for_sockets)。  
  
 Windows 套接字规范定义了 Microsoft Windows 的二进制兼容的网络编程接口。  Windows 套接字是在加州大学伯克利分校的Berkeley Software Distribution \(BSD，版本 4.3\) 的 UNIX 套接字的基础上实现的。  规范包含 BSD 样式套接字实例和特定于Windows的扩展。  使用 Windows 套接字许可应用程序通过符合 Windows 套接字 API 的任何网络通信。  在 Win32 中，Windows 套接字提供线程安全。  
  
 许多网络软件供应商在网络协议（包括传输控制协议 \/Internet 协议 \(TCP\/IP\)，复制 internet 系统 \(XNS\)，迪吉多的 DECNet 协议、Novell Corporation 的 Internet 数据包交换\/排序的打包的交换 \(IPX\/SPX\) 和其他协议）下支持 Windows 套接字。  虽然当前 Windows 套接字规范定义了 TCP\/IP 套接字的抽象，但是任何网络协议可以通过提供实现 Windows 套接字的动态链接库 \(DLL\) 的自身版本来符合 Windows 套接字的规范。  用Windows 套接字编写的商务应用程序的示例包括 X Windows服务器、最终模拟器和电子邮件系统。  
  
> [!NOTE]
>  Windows 套接字的目的是提取基础网络，因此您不必了解该网络，您的应用程序可在支持套接字的所有网络上运行。  因此，本文档不讨论网络协议详细信息。  
  
 Microsoft 基础类库 \(MFC\) 提供两种类来支持Windows 套接字 API 的编程。  其中的一个类，`CSocket`，提供高级抽象来简化网络通信编程。  
  
 Windows 套接字规范，Windows 套接字：微软Windows下网络计算的开放接口，现在在1.1版中，被发展为由许多在TCP \/ IP社区的个人和公司使用的开放网络标准，且可任意使用。  通过使用 Internet 协议套件，套接字编程模型当前支持“通信字段”。  在[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中，该规范是可用的。  
  
> [!TIP]
>  由于套接字使用 Internet 协议套件，因此它们是在“信息高速路”上支持 Internet 通信的应用程序的首选路径。  
  
##  <a name="_core_definition_of_a_socket"></a> 套接字的定义  
 套接字是一个通信终点——一个对象，通过该对象，Windows 套接字应用程序在网络上发送或接收数据包。  套接字具有类型且与运行的进程相关，因此，它可以有名称。  目前，泛型套接字只与同一“通信字段"的使用 Internet 协议套件的其他套接字交换数据。  
  
 这两种套接字是双向的；它们是在两个方向可同时通信的数据流 \(全双工\)。  
  
 两个套接字类型是可用的：  
  
-   流套接字  
  
     流套接字提供不记录边界的数据流：字节流。  请确保数据流的发送，正确排序和非重复性。  
  
-   数据报套接字  
  
     数据报套接字不保证记录型数据流的发送和按顺序序发送或非重复性。  
  
 “排序”表示数据包是按顺序发送。“非重复性”意味着你只能获取特定数据包一次。  
  
> [!NOTE]
>  在一些网络协议下，例如 XNS，流可能是面向记录，作为记录流，而不是字节流。  但是，在较常见的 TCP\/IP 协议下，流是字节流。  Windows 套接字提供了与基础协议无关的抽象级别。  
  
 有关更多类型和在哪种情况该使用哪种套接字的信息，请参阅[Windows 套接字: 流套接字](../mfc/windows-sockets-stream-sockets.md) and [Windows 套接字: 数据报套接字](../mfc/windows-sockets-datagram-sockets.md).  
  
##  <a name="_core_the_socket_data_type"></a> 套接字数据类型  
 每个 MFC 套接字对象封装了 Windows 套接字对象的图柄。  这种图柄的数据类型是**SOCKET**。  一个**SOCKET**图柄类似于窗口的`HWND`。  MFC 套接字类在封装的句柄中提供操作。  
  
 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]详细描述了**SOCKET**数据类型。  请参见Windows 套接字下的“套接字数据类型和错误值”。  
  
##  <a name="_core_uses_for_sockets"></a> 套接字的使用  
 至少在以下3种通信上下文中，套接字是非常有用：  
  
-   客户端\/服务器模型。  
  
-   点对点方案，如消息应用程序。  
  
-   通过接收的应用程序调用函数来解释消息，进行远程过程调用 \(RPC\)。  
  
> [!TIP]
>  使用 MFC 套接字的理想情况是在您编写通信端点时：在两端都使用 MFC。  有关该主题的更多信息，包括如何处理你和非MFC应用程序通信的情况，请参见[Windows套接字: 字节排序](../mfc/windows-sockets-byte-ordering.md)。  
  
 有关更多信息，请参见Windows套接字规范：**ntohs**, **ntohl**, **htons**, **htonl**。  另外，请参见下列主题：  
  
-   [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows 套接字：使用存档的套接字的示例](../mfc/windows-sockets-example-of-sockets-using-archives.md)  
  
-   [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
## 请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)