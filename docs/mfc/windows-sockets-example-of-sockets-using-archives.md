---
title: Windows 套接字：使用存档的套接字的示例
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 253a65430ae230fbc4deeb9bd5288f28237310d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371079"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows 套接字：使用存档的套接字的示例

本文提供了使用类[CSocket](../mfc/reference/csocket-class.md)的示例。 该示例使用`CArchive`对象通过套接字对数据进行序列化。 请注意，这不是文件序列化或从文件。

下面的示例说明了如何使用存档通过`CSocket`对象发送和接收数据。 该示例的设计是使应用程序的两个实例（在同一台计算机上或网络上的不同计算机上）交换数据。 一个实例发送数据，另一个实例接收和确认这些数据。 任一应用程序都可以启动交换，也可以充当服务器或作为另一个应用程序的客户端。 以下函数在应用程序的视图类中定义：

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

此示例中最重要的是其结构与 MFC`Serialize`函数的结构平行。 成员`PacketSerialize`函数由带**其他**子句的**if**语句组成。 该函数接收两个[CArchive](../mfc/reference/carchive-class.md)引用作为参数 *：arData*和*arAck*。 如果*arData*存档对象设置为存储（发送），则执行**如果**分支;否则，如果*arData*设置为加载（接收），则函数将采用**其他**分支。 有关 MFC 中序列化的详细信息，请参阅[序列化](../mfc/how-to-make-a-type-safe-collection.md)。

> [!NOTE]
> *arAck*存档对象假定与*arData*相反。 如果*arData*用于发送，*则 arAck*接收，反之亦然。

对于发送，示例函数循环指定的次数，每次生成一些随机数据用于演示目的。 您的应用程序将从某些源（如文件）获取真实数据。 *arData*存档的插入运算符 （**<<**） 用于发送三个连续数据块的流：

- 指定数据性质的"标头"（在本例中 *，bValue*变量的值和将发送多少个副本）。

   此示例随机生成这两个项。

- 数据的副本的指定数量。

   循环的内部**发送** *bValue*指定的次数。

- 接收器向其用户显示的名为*strText*的字符串。

对于接收，该函数的操作类似，只不过它使用存档的提取运算符 （**>>**） 从存档获取数据。 接收应用程序验证它接收的数据，显示最终的"已接收"消息，然后发送回一条消息，显示"已发送"，以便发送应用程序显示。

在此通信模型中，"接收"一词（在*strText*变量中发送的消息）用于在通信的另一端显示，因此它向接收用户指定已收到一定数量的数据包。 接收方使用类似字符串进行回复，该字符串显示"已发送"，以便显示在原始发件人的屏幕上。 收到两个字符串表示已成功通信。

> [!CAUTION]
> 如果您要编写 MFC 客户端程序来与建立的（非 MFC）服务器通信，则请勿通过存档发送 C++ 对象。 除非服务器是了解要发送的对象类型的 MFC 应用程序，否则它将无法接收和取消序列化对象。 一文中的示例[Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)显示了此类型的通信。

有关详细信息，请参阅 Windows 套接字规范 **：htonl、htons、ntohl** **、ntohs**。 **htons** **ntohl** 此外，有关详细信息，请参阅：

- [Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows 套接字：背景](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>另请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)<br/>
[C存档：正在存储](../mfc/reference/carchive-class.md#isstoring)<br/>
[C存档：：操作员 <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[C存档：：操作员 >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[C存档：冲洗](../mfc/reference/carchive-class.md#flush)<br/>
[CObject：序列化](../mfc/reference/cobject-class.md#serialize)
