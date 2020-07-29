---
title: Windows 套接字：使用存档的套接字的示例
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 275a6c274648225fedcec9d42c280f77af68158e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226771"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows 套接字：使用存档的套接字的示例

本文举例介绍了如何使用类[CSocket](../mfc/reference/csocket-class.md)。 该示例使用 `CArchive` 对象来通过套接字序列化数据。 请注意，这并不是从文件到文件的序列化。

下面的示例演示如何使用存档通过对象发送和接收数据 `CSocket` 。 该示例旨在使应用程序的两个实例（在同一台计算机上或网络上的不同计算机上）交换数据。 一个实例发送数据，另一个实例接收并确认。 这两个应用程序都可以启动 exchange，也可以充当其他应用程序的服务器或客户端。 在应用程序的视图类中定义了以下函数：

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

此示例最重要的一点是其结构与 MFC 函数的结构类似 `Serialize` 。 此 `PacketSerialize` 成员函数包含 **`if`** 包含子句的语句 **`else`** 。 函数收到两个[CArchive](../mfc/reference/carchive-class.md)引用作为参数： *arData*和*arAck*。 如果将*arData*存档对象设置为存储（发送），则 **`if`** 分支执行; 否则，如果将*arData*设置为加载（接收），则该函数将使用该 **`else`** 分支。 有关 MFC 中的序列化的详细信息，请参阅[序列化](../mfc/how-to-make-a-type-safe-collection.md)。

> [!NOTE]
> 假定*arAck* archive 对象与*arData*相反。 如果*arData*用于发送，则*arAck*接收，并且反向为 true。

对于发送，示例函数会循环执行指定的次数，每次生成一些随机数据以用于演示目的。 您的应用程序将从某些源（如文件）获取实际数据。 *ArData*存档的插入运算符（ **<<** ）用于发送三个连续数据块的流：

- 指定数据性质的 "标头" （在本例中为*bValue*变量的值以及将发送多少个副本）。

   对于本示例，这两项都是随机生成的。

- 指定的数据副本数。

   内部 **`for`** 循环发送*bValue*指定的次数。

- 一个名为*strText*的字符串，接收方向其用户显示此字符串。

对于接收，函数的操作方式类似，只是它使用存档的提取运算符（ **>>** ）从存档中获取数据。 接收应用程序将验证其收到的数据，显示最终的 "接收" 消息，然后发回一条消息，其中显示了发送应用程序要显示的 "已发送" 消息。

在此通信模型中，"Received" 一词是指在*strText*变量中发送的消息，用于在通信的另一端显示，因此它指定接收用户已收到一定数量的数据包。 接收方使用类似于 "已发送" 的字符串进行答复，以便在原始发送方的屏幕上显示。 收到两个字符串都表明发生了成功的通信。

> [!CAUTION]
> 如果您要编写 MFC 客户端程序来与建立的（非 MFC）服务器通信，则请勿通过存档发送 C++ 对象。 除非服务器是了解要发送的对象类型的 MFC 应用程序，否则它将无法接收和反序列化您的对象。 [Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)一文中的示例显示了此类型的通信。

有关详细信息，请参阅 Windows 套接字规范： **htonl**、 **htons**、 **ntohl**、 **ntohs**。 此外，有关详细信息，请参阅：

- [Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows 套接字：背景](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>另请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive：： IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive：： operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive：： operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive：： Flush](../mfc/reference/carchive-class.md#flush)<br/>
[CObject：：串行化](../mfc/reference/cobject-class.md#serialize)
