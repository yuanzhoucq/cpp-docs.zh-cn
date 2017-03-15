---
title: "Windows 套接字：字节排序 | Microsoft Docs"
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
  - "套接字编程中的字节顺序问题"
  - "套接字 [C++], 字节顺序问题"
  - "Windows 套接字 [C++], 字节顺序问题"
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Windows 套接字：字节排序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文和两指南手册演示 Windows Sockets 编程的一些问题。  本文包括字节顺序。  文章中介绍的其他问题：[Windows Sockets：块](../mfc/windows-sockets-blocking.md) 和 [Windows Sockets：转换字符串](../mfc/windows-sockets-converting-strings.md)。  
  
 如果使用或派生自类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，将需要管理这些问题。  如果使用或派生自类[CSocket](../mfc/reference/csocket-class.md)，MFC 为您管理这些。  
  
## 字节顺序  
 不同的机器结构采用不同的字节顺序存储数据。  例如，在 Motorola Macintosh 计算机\) \(相反的顺序基于 Intel 的计算机存储数据。  Intel Little\-Endian 字节顺序，名为“”，也是网络标准“Big\-Endian”顺序相反。  下表说明这些术语。  
  
### 大和小端字节排序  
  
|字节顺序|含义|  
|----------|--------|  
|大端|大端表示最大的有效字节位于单词的左端。|  
|小端|大端表示最大的有效字节位于单词的右端。|  
  
 通常，您不必担心您通过网络发送和接收的数据的字节序列转换，但必须将字节顺序的情况。  
  
## 当必须将字节顺序  
 需要在以下情况下转换字节顺序：  
  
-   您需要通过网络传递的信息解释，而您发送到另一台数据相对的。  例如，您可能将端口和网络地址，必须理解。  
  
-   您进行的服务器应用不是 MFC 应用程序 \(并在没有它的源代码\)。  此调用字节序列转换，如果两台计算机不共享同样字节顺序。  
  
## 在不必将转换字节顺序  
 可以避免在以下情况下转换字节顺序工作：  
  
-   在两端的计算机上授予不交换字节，因此，两台计算机上使用相同字节顺序。  
  
-   您的服务器使用的是 MFC 应用程序。  
  
-   您将使用的服务器上的源代码，所以，可以显式分辨率是否必须将字节顺序。  
  
-   服务器可以移植到 MFC。  这非常轻松执行，并且，结果通常更小，更快的代码。  
  
 使用 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)时，必须管理所需的字节序列转换。  Windows 套接字标准化“Big\-Endian”字节顺序并提供函数。此顺序和其他类型之间的转换。  [CArchive](../mfc/reference/carchive-class.md)，但是，可以使用 [CSocket](../mfc/reference/csocket-class.md)相反，使用 \(“Little\-Endian”\) 排序，但是，`CArchive` 负责字节序列转换详细信息了。  使用顺序应用程序或使用 Windows 套接字字节序列转换函数的此标准，可以使代码更可移植。  
  
 使用 MFC 套接字的理想情况是在您编写通信端点时：在两端都使用 MFC。  如果编写的非 MFC 应用程序将如通信，FTP 服务器，您的应用程序可能需要管理字节交换使用 Windows 套接字转换程序 **ntohs**、**ntohl**、**htons**和 **htonl**之前，在将数据传递到存档，对象。  在进行这些函数的示例使用非 MFC 应用程序之后。在本文。  
  
> [!NOTE]
>  当不存在的另一端。不是 MFC 应用程序时，还必须避免流从 `CObject` 派生的 C\+\+ 对象到存档，因为该接收器不能够处理它们。  参见 [Windows 套接字：将存档的套接字](../mfc/windows-sockets-using-sockets-with-archives.md)的注释。  
  
 有关字节顺序的更多信息，请参见 Windows 套接字规范，[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中可用。  
  
## 字节序列转换示例  
 下面的示例演示如何使用已存档的 `CSocket` 对象序列化的函数。  使用在 Windows 套接字，API 的字节序列转换函数还说明。  
  
 此示例提供是在编写客户与非 MFC 服务器应用程序不具有访问源代码的一种方案。  在这种情况下，必须假定，非 MFC 服务器使用标准 Web 字节顺序。  相反，MFC 客户端应用程序使用 `CSocket` 对象的 `CArchive` 对象和 `CArchive` 使用“Little\-Endian”字节顺序，则网络标准的相反值。  
  
 假定您有一条消息通信计划数据包中的协议建立如下所示的非 MFC 服务器：  
  
 [!CODE [NVC_MFCSimpleSocket#5](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCSimpleSocket#5)]  
  
 在 MFC 术语，这表示如下：  
  
 [!CODE [NVC_MFCSimpleSocket#6](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCSimpleSocket#6)]  
  
 在 C\+\+，`struct` 实际上是内容与类相同。  `Message` 结构可以具有成员函数，如中声明的 `Serialize` 成员函数前面。  `Serialize` 成员函数如下所示：:  
  
 [!CODE [NVC_MFCSimpleSocket#7](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCSimpleSocket#7)]  
  
 此示例调用数据字节序列转换，因为存在字节顺序非 MFC 服务器应用于一个和上另一结束在 MFC 端的客户端应用程序的 `CArchive` 之间广泛的不匹配。  示例说明 Windows 套接字提供的几字节序列转换函数。  下表描述了这些函数。  
  
### Windows 套接字字节序列转换函数  
  
|功能|用途|  
|--------|--------|  
|**ntohs**|转换为 16 位数。从网络字节顺序为托管 \(字节顺序 Big\-Endian 为 little\-endian\)。|  
|**ntohl**|转换为 32 位数。从网络字节顺序为托管 \(字节顺序 Big\-Endian 为 little\-endian\)。|  
|**Htons**|转换为 16 位数。从网络字节顺序为托管 \(字节顺序大端为小端\)。|  
|**Htonl**|转换为 32 位数。从网络字节顺序为托管 \(字节顺序大端为小端\)。|  
  
 此示例在另另一点是，一端通信的套接字应用程序非 MFC 应用程序时，则必须避免执行与下面类似的内容：  
  
 `ar << pMsg;`  
  
 其中 `pMsg` 是指针对从类派生的。. C\+\+ 对象的 `CObject`。  这是发送额外 MFC 的信息与对象，服务器不能理解，那么，将，如果是 MFC 应用程序。  
  
 有关详细信息，请参阅：  
  
-   [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows 套接字：背景](../mfc/windows-sockets-background.md)  
  
-   [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)  
  
## 请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)