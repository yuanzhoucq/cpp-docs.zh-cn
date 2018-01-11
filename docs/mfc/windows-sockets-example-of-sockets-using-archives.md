---
title: "Windows 套接字： 使用存档的套接字示例 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0e70e8ecc14496b03bc758d91f078a926f33532
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows 套接字：使用存档的套接字的示例
本文介绍了使用类的示例[CSocket](../mfc/reference/csocket-class.md)。 该示例使用`CArchive`对象要序列化数据通过套接字。 请注意，这不是文档序列化到或从文件。  
  
 下面的示例演示如何使用存档发送和接收数据通过`CSocket`对象。 该示例进行设计，以便两个实例 （在同一计算机上或在网络上的不同计算机上） 的应用程序交换数据。 一个实例将发送数据，也不能在其他实例接收确认。 任一应用程序可以发起交换，并请可为服务器或另一个应用程序的客户端。 应用程序的视图类中定义的以下函数：  
  
 [!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]  
  
 有关此示例的最重要事项是其结构与 MFC 相似`Serialize`函数。 **PacketSerialize**成员函数组成**如果**语句**其他**子句。 该函数接收两个[CArchive](../mfc/reference/carchive-class.md)作为参数的引用：`arData`和`arAck`。 如果`arData`存档对象设置用于存储 （发送），**如果**执行分支; 否则为如果`arData`设置用于加载 （接收） 函数**其他**分支。 有关 MFC 中的序列化的详细信息，请参阅[序列化](../mfc/how-to-make-a-type-safe-collection.md)。  
  
> [!NOTE]
>  `arAck`存档对象被假定为相反`arData`。 如果`arData`是用于发送，`arAck`接收，反之将然。  
  
 用于发送，示例函数超过指定的次数，生成一些随机数据用于演示目的每次循环。 你的应用程序要从某些来源，如文件中获得的真实数据。 `arData`存档的插入运算符 (**<<**) 用于发送的数据的三个连续的块流：  
  
-   "标头"，指定数据的性质 (在此情况下，值`bValue`变量，将发送多少副本)。  
  
     这两个项都是随机生成此示例。  
  
-   指定的数据副本数。  
  
     内部**为**循环发送`bValue`指定重试次数。  
  
-   一个字符串，调用`strText`接收方显示给用户。  
  
 用于接收，函数的操作相似，只不过它使用存档的提取运算符 (**>>**) 从存档获取数据。 接收应用程序发送的应用程序，以显示有关验证它接收、 显示最终的"接收到"消息，然后再发送回一条消息，指出"发送"的数据。  
  
 在此通信模型中，单词"接收"消息将发送`strText`变量，是用于显示在另一端的通信，因此它向接收用户指定已经接收了一定数量的数据包。 接收方在原始发件人的屏幕显示"发送"，以显示的相似字符串与答复。 这两个字符串的回执指示发生了成功通信。  
  
> [!CAUTION]
>  如果您要编写 MFC 客户端程序来与建立的（非 MFC）服务器通信，则请勿通过存档发送 C++ 对象。 除非服务器是 MFC 应用程序理解的各种您想要发送的对象，它将无法接收和反序列化对象。 示例，请参见文章[Windows 套接字： 字节排序](../mfc/windows-sockets-byte-ordering.md)显示此类型的通信。  
  
 有关详细信息，请参阅 Windows 套接字规范： **htonl**， **htons**， **ntohl**， **ntohs**。 此外，有关详细信息，请参阅：  
  
-   [Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows 套接字：背景](../mfc/windows-sockets-background.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)   
 [CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)   
 [CArchive::operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)   
 [CArchive::operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)   
 [CArchive::Flush](../mfc/reference/carchive-class.md#flush)   
 [Cobject:: Serialize](../mfc/reference/cobject-class.md#serialize)

