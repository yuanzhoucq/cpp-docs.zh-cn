---
title: "WinInet 如何简化 Internet 客户端应用程序的创建 | Microsoft Docs"
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
  - "Windows 套接字 [C++], 与 WinInet"
  - "WinInet 类, Internet 客户端应用程序"
  - "WinInet 类, 与 WinSock"
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# WinInet 如何简化 Internet 客户端应用程序的创建
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Win32 Internet 扩展或 WinInet，提供对常规 Internet 协议，包括地鼠、HTTP 和 FTP。  使用 WinInet，您可以编写、Internet 客户端应用程序编程，在高级别，无需处理 Winsock TCP\/IP、或特定 Internet 协议详细信息。  WinInet 为所有三协议提供一致的一组函数，以熟悉 Win32 API 接口。  此一致性尽量减少需要进行的代码更改，则基础协议更改 \(例如，从到 FTP HTTP\)。  
  
 Visual C\+\+ 提供两种方法。使用 WinInet。  可以调用 Win32 函数 Internet \(直接查看 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 的 OLE 文档以了解更多信息\) 或您可以通过 [MFC WinInet 类](../mfc/mfc-classes-for-creating-internet-client-applications.md)使用 WinInet。  
  
 **可以使用 WinInet:**  
  
-   下载 HTML 页。  
  
     HTTP 是协议转交从服务器 HTML 页的客户端浏览器。  
  
-   FTP 发送请求上载或下载文件或来获取目录列表。  
  
     典型的请求都下载文件的匿名登录。  
  
-   为访问 Internet 上的资源使用地鼠的菜单系统。  
  
     菜单项可能是若干类型，这些对象包括其他菜单、可以搜索的一个数据库索引，新闻组或文件。  
  
 对于所有三协议，可以建立连接，使服务器请求，然后关闭连接。  
  
 **MFC WinInet 类更加方便：**  
  
-   读取从 HTTP、FTP 和地鼠服务器的信息一样轻松地与从硬盘读取文件。  
  
-   使用 HTTP、FTP 和地鼠协议，不直接为 Winsock 编程或 TCP\/IP。  
  
     Internet 使用 Win32 函数的开发人员不需要熟悉 Windows 或 TCP\/IP 套接字。  可以直接将编程在套接字级别，使用 Winsock 和 TCP\/IP 协议，但使用 MFC WinInet 类访问 HTTP、FTP 和地鼠协议在 Internet 上更容易。  对于许多常见操作，它们使用的开发人员不需要知道特定协议详细信息。  
  
 可由计算机执行为其他计算机上的客户在 Internet 上许多操作可能需要很长时间。  这些操作的速度由网络连接速度通常限制，但它们可能受其他网络流量和操作的复杂性也会影响。  连接到远程的 FTP 服务器，例如，需要计算机首先查找该服务器名称找到其地址。  然后应用程序将尝试连接到服务器在该地址。  一旦打开连接，计算机和远程服务器将启动与文件传输协议 \(FTP\) 的对话，在实际使用连接检索文件之前。  
  
## 请参阅  
 [Win32 Internet 扩展 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [MFC 如何简化 Internet 客户端应用程序的创建](../mfc/how-mfc-makes-it-easier-to-create-internet-client-applications.md)