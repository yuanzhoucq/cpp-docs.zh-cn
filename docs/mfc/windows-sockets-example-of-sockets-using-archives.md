---
title: Windows 套接字： 使用存档的套接字示例 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6613e38a19987abcc9f95288e9d1cb6957b076a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427272"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows 套接字：使用存档的套接字的示例

本文提供了一个示例使用类的[CSocket](../mfc/reference/csocket-class.md)。 该示例采用`CArchive`通过套接字的数据进行序列化的对象。 请注意，这不是文档序列化到或文件。

下面的示例演示如何使用存档发送和接收数据通过`CSocket`对象。 示例被设计，以便两个实例 （在同一台计算机上或在网络上的不同计算机上） 的应用程序交换数据。 一个实例将发送数据，这在其他实例接收和确认。 任一应用程序可以发起交换，并可以为服务器或另一个应用程序的客户端可以执行的操作。 应用程序的视图类中定义的以下函数：

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

有关此示例的最重要一点是其结构类似，MFC`Serialize`函数。 `PacketSerialize`成员函数组成**如果**语句**其他**子句。 该函数接收两个[CArchive](../mfc/reference/carchive-class.md)作为参数的引用： *arData*并*arAck*。 如果*arData*存档对象设置为存储 （发送），**如果**分支执行; 否则为如果*arData*设置用于加载 （接收） 该函数采用**其他**分支。 有关在 MFC 中的序列化的详细信息，请参阅[序列化](../mfc/how-to-make-a-type-safe-collection.md)。

> [!NOTE]
>  *ArAck*存档对象被假定为相反*arData*。 如果*arData*是用于发送， *arAck*接收，并反过来也是如此。

用于发送，示例函数循环超过指定的次数，每次生成一些随机数据用于演示目的。 你的应用程序从某个源，如文件中获取真实数据。 *ArData*存档的插入运算符 (**<<**) 用于发送的数据的三个连续块的流：

- "标头"，它指定数据的性质 (在本例中为的值*bValue*变量，并将发送多少份副本)。

     这两个项都是随机生成此示例。

- 指定的数据的副本数。

     内部**有关**循环发送*bValue*指定的次数。

- 一个字符串，调用*strText* ，接收方显示其用户。

用于接收，该函数的操作相似，只不过它使用存档的提取运算符 (**>>**) 以从存档中获取数据。 接收应用程序发送的应用程序以显示有关验证它接收的数据，显示最终的"Received"消息，然后发回一条消息，指出"已发送"。

发送消息在此通信模型中，"Received"一词*strText*变量，是显示在另一端的通信，因此它指定到接收用户一定数量的数据包数据已被接收到。 接收方会回复原始发件人的屏幕显示"发送"，显示的相似字符串。 这两个字符串的回执指示发生了成功通信。

> [!CAUTION]
>  如果您要编写 MFC 客户端程序来与建立的（非 MFC）服务器通信，则请勿通过存档发送 C++ 对象。 除非服务器是了解要发送的对象类型的 MFC 应用程序，它将无法接收和反序列化您的对象。 示例，请参见文章[Windows 套接字： 字节排序](../mfc/windows-sockets-byte-ordering.md)显示了此类型的通信。

有关详细信息，请参阅 Windows 套接字规范： **htonl**， **htons**， **ntohl**， **ntohs**。 此外，有关详细信息，请参阅：

- [Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows 套接字：背景](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive::operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::Flush](../mfc/reference/carchive-class.md#flush)<br/>
[Cobject:: Serialize](../mfc/reference/cobject-class.md#serialize)

