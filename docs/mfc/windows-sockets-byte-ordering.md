---
title: "Windows 套接字： 字节排序 |Microsoft 文档"
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
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5c25a7b2c8240531e1d778d6a119f857032423db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-byte-ordering"></a>Windows 套接字：字节排序
本文和两篇配套文章介绍了 Windows 套接字编程中的若干问题。 本文介绍如何字节排序。 文章中涉及的其他问题： [Windows 套接字： 阻止](../mfc/windows-sockets-blocking.md)和[Windows 套接字： 转换字符串](../mfc/windows-sockets-converting-strings.md)。  
  
 如果你使用或派生自类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，你将需要管理这些问题。 如果你使用或派生自类[CSocket](../mfc/reference/csocket-class.md)，MFC 将为你管理这些问题。  
  
## <a name="byte-ordering"></a>字节排序  
 不同计算机基础结构有时存储使用不同的字节顺序的数据。 例如，基于 Intel 的机在 Macintosh (Motorola) 机的反向顺序存储数据。 调用"Little-endian，"Intel 字节顺序也是网络标准"Big-endian"顺序的相反值。 下表介绍了这些条款。  
  
### <a name="big--and-little-endian-byte-ordering"></a>大-和 Little-endian 字节排序  
  
|字节排序|含义|  
|-------------------|-------------|  
|Big Endian|在左单词末尾的是最高有效字节。|  
|Little-endian|在某个词的右端是最高有效字节。|  
  
 通常，无需担心发送和通过网络接收的数据的字节顺序转换，但在一些情况下在其中你必须转换字节顺序。  
  
## <a name="when-you-must-convert-byte-orders"></a>当必须转换字节顺序  
 你需要将转换的字节顺序在以下情况：  
  
-   传递的需要的网络，而不是要发送到另一台计算机的数据进行解释的信息。 例如，你可能会传递端口和地址，必须了解网络。  
  
-   与之通信的服务器应用程序不是 MFC 应用程序 （和你还没有源代码它）。 这将调用字节顺序转换如果在两台计算机不会共享相同的字节顺序。  
  
## <a name="when-you-do-not-have-to-convert-byte-orders"></a>不需要转换字节顺序  
 你可以避免将转换的字节顺序在以下情况下工作：  
  
-   在这两个端点上的计算机可以同意不交换字节，并且这两台计算机使用相同的字节顺序。  
  
-   你正与进行通信的服务器是 MFC 应用程序。  
  
-   你具有要与通信的服务器的源代码，以便你可以判断显式你是否必须转换字节顺序。  
  
-   你可以移植到 MFC 的服务器。 这是非常易于执行，并且结果通常是较小、 更快的代码。  
  
 使用[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，必须自行管理的任何必要的字节顺序的转换。 Windows 套接字标准化"Big-endian"字节顺序模型，并提供此顺序和其他之间进行转换的函数。 [CArchive](../mfc/reference/carchive-class.md)，但是，这与使用[CSocket](../mfc/reference/csocket-class.md)，使用相反的顺序 ("Little-endian") 中，但`CArchive`负责为你的字节顺序转换的详细信息。 通过使用此标准排序在应用程序，或使用 Windows 套接字字节顺序转换函数，可以使更易于移植你的代码。  
  
 你正在编写两个通信端时，理想情况下使用 MFC 套接字： 在两端都使用 MFC。 如果你正在编写的应用程序将通信与非 MFC 应用程序，如 FTP 服务器，你可能需要管理字节交换自己之前将数据传递给存档对象中，使用 Windows 套接字转换例程**ntohs**， **ntohl**， **htons**，和**htonl**。 在与非 MFC 应用程序通信中使用这些函数的示例所示在本文的后面。  
  
> [!NOTE]
>  当通信的另一端不是 MFC 应用程序时，你还必须避免流式处理 c + + 对象派生自`CObject`成你存档因为接收方将不能处理它们。 请参阅中的说明[Windows 套接字： 使用存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
 有关字节顺序的详细信息，请参阅 Windows SDK 中提供的 Windows 套接字规范。  
  
## <a name="a-byte-order-conversion-example"></a>字节顺序转换示例  
 下面的示例演示的序列化函数`CSocket`使用存档的对象。 它还说明了 Windows 套接字 API 中使用字节顺序转换函数。  
  
 此示例显示了你正在编写与您对该源代码没有访问权限的非 MFC 服务器应用程序进行通信的客户端的方案。 在此方案中，你必须假定非 MFC 服务器使用标准网络字节顺序。 与此相反，MFC 客户端应用程序使用`CArchive`对象`CSocket`对象，和`CArchive`使用"Little-endian"字节顺序，与标准网络的符号相反。  
  
 假设你打算与之通信的非 MFC 服务器有如下所示的消息包建立的协议：  
  
 [!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]  
  
 在 MFC 术语中，这将表示，如下所示：  
  
 [!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]  
  
 C + + 中`struct`是实质上是相同的为类。 `Message`结构可以具有成员函数，如`Serialize`上面的成员函数声明。 `Serialize`成员函数可能如下所示：  
  
 [!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]  
  
 因为一端上的非 MFC 服务器应用程序的字节顺序之间没有明显不匹配，此示例将调用的数据的字节顺序转换和`CArchive`用于 MFC 客户端应用程序在另一端。 该示例演示了几个 Windows 套接字提供的字节顺序转换函数。 下表描述了这些函数。  
  
### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows 套接字字节顺序转换函数  
  
|函数|目标|  
|--------------|-------------|  
|**ntohs**|为主机字节顺序 (big Endian 到 Little-endian) 从网络字节顺序转换为 16 位数量。|  
|**ntohl**|为主机字节顺序 (big Endian 到 Little-endian) 从网络字节顺序转换为 32 位数量。|  
|**Htons**|为网络字节顺序 (Little-endian 到 big Endian) 从主机字节顺序转换为 16 位数量。|  
|**Htonl**|为网络字节顺序 (Little-endian 到 big Endian) 从主机字节顺序转换为 32 位数量。|  
  
 在此示例中的另一点是通信的，非 MFC 应用程序上的另一端的套接字应用程序时，你必须避免执行类似于以下内容：  
  
 `ar << pMsg;`  
  
 其中`pMsg`是指向派生自类的 c + + 对象的指针`CObject`。 这将会发送与对象和服务器相关联的额外 MFC 信息不能理解它，就像它像 MFC 应用程序。  
  
 有关详细信息，请参见:  
  
-   [Windows 套接字：使用 CAsyncSocket 类](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows 套接字：背景](../mfc/windows-sockets-background.md)  
  
-   [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)

