---
title: Windows 套接字：字节排序
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: 50548202483c4d9d4471ad2c600270c4df4503e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371066"
---
# <a name="windows-sockets-byte-ordering"></a>Windows 套接字：字节排序

本文和两篇配套文章介绍了 Windows 套接字编程中的若干问题。 本文介绍字节排序。 其他问题在文章中介绍[：Windows套接字：阻止](../mfc/windows-sockets-blocking.md)和[Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)。

如果您使用或派生自类[CAsyncSocket，](../mfc/reference/casyncsocket-class.md)则需要自己管理这些问题。 如果您使用或派生自[CSocket](../mfc/reference/csocket-class.md)类，MFC 会为您管理它们。

## <a name="byte-ordering"></a>字节订购

不同的机器体系结构有时使用不同的字节顺序存储数据。 例如，基于英特尔的机器以 Macintosh （摩托罗拉） 机器的相反顺序存储数据。 英特尔字节顺序称为"小 Endian"，也是网络标准"大Endian"订单的反面。 下表解释了这些术语。

### <a name="big--and-little-endian-byte-ordering"></a>大和小恩地字节订购

|字节排序|含义|
|-------------------|-------------|
|大恩迪安|最重要的字节位于单词的左端。|
|小恩迪安|最重要的字节位于单词的右端。|

通常，您不必担心通过网络发送和接收的数据的字节顺序转换，但在某些情况下必须转换字节订单。

## <a name="when-you-must-convert-byte-orders"></a>当您必须转换字节订单时

您需要在以下情况下转换字节订单：

- 您传递的信息需要由网络解释，而不是您发送到另一台计算机的数据。 例如，您可以传递端口和地址，而网络必须了解这些端口和地址。

- 与您通信的服务器应用程序不是 MFC 应用程序（并且您没有它的源代码）。 如果两台计算机不共享相同的字节顺序，则这将调用字节订单转换。

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>当您不必转换字节订单时

在以下情况下，可以避免转换字节订单的工作：

- 两端的计算机可以同意不交换字节，并且两台计算机使用相同的字节顺序。

- 您要通信的服务器是 MFC 应用程序。

- 您拥有要通信的服务器的源代码，因此您可以显式判断是否必须转换字节订单。

- 您可以将服务器移植到 MFC。 这是相当容易做到的，结果通常是更小，更快的代码。

使用[CAsyncSocket，](../mfc/reference/casyncsocket-class.md)您必须自己管理任何必要的字节顺序转换。 Windows 套接字可标准化"大 Endian"字节顺序模型，并提供在此顺序和其他订单之间转换的功能。 [但是，CArchive，](../mfc/reference/carchive-class.md)你与[CSocket](../mfc/reference/csocket-class.md)一起使用，使用相反（"小Endian"）顺序，但`CArchive`会为您处理字节顺序转换的详细信息。 通过在应用程序中使用此标准排序或使用 Windows 套接字字节顺序转换功能，可以使代码更加便携。

使用 MFC 套接字的理想情况是，当您写入通信的两端时：在两端使用 MFC。 如果您正在编写一个将与非 MFC 应用程序（如 FTP 服务器）通信的应用程序，则可能需要在将数据传递到存档对象之前，使用 Windows Sockets 转换例程**ntohs、ntohl、htons**和**htonl**来管理**htons**字节交换。 **ntohs** 本文后面会介绍与非 MFC 应用程序通信中使用的这些函数的示例。

> [!NOTE]
> 当通信的另一端不是 MFC 应用程序时，还必须避免将派生C++`CObject`对象流式传输到存档中，因为接收方将无法处理它们。 请参阅 Windows[套接字中的注释：使用带存档的套接字](../mfc/windows-sockets-using-sockets-with-archives.md)。

有关字节订单的详细信息，请参阅 Windows SDK 中可用的 Windows 套接字规范。

## <a name="a-byte-order-conversion-example"></a>字节顺序转换示例

下面的示例显示了使用存档`CSocket`的对象的序列化函数。 它还说明了在 Windows 套接字 API 中使用字节顺序转换功能。

此示例介绍一个方案，其中您编写的客户端与无法访问源代码的非 MFC 服务器应用程序进行通信。 在这种情况下，您必须假定非 MFC 服务器使用标准网络字节顺序。 相反，MFC 客户端应用程序使用`CArchive`对象与`CSocket`对象，并使用`CArchive`"小 Endian"字节顺序，这与网络标准相反。

假设您计划与其通信的非 MFC 服务器具有消息数据包的已建立协议，如下所示：

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

用MFC的术语，这将表达如下：

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

在C++中，**结构**本质上与类是一回事。 结构`Message`可以具有成员函数，如上面声明`Serialize`的成员函数。 成员`Serialize`函数可能如下所示：

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

此示例要求数据字节顺序转换，因为一端的非 MFC 服务器应用程序的字节排序与另一端 MFC 客户端应用程序`CArchive`中使用的字节排序之间存在明显的不匹配。 该示例说明了 Windows 套接字提供的几个字节顺序转换功能。 下表描述了这些功能。

### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows 套接字字节顺序转换功能

|函数|目标|
|--------------|-------------|
|**ntohs**|将 16 位数量从网络字节顺序转换为主机字节顺序（大 Endian 到小 Endian）。|
|**ntohl**|将 32 位数量从网络字节顺序转换为主机字节顺序（大 Endian 到小 Endian）。|
|**霍顿斯**|将 16 位数量从主机字节顺序转换为网络字节顺序（小 Endian 到大 Endian）。|
|**赫托恩**|将 32 位数量从主机字节顺序转换为网络字节顺序（小 Endian 到大 Endian）。|

此示例的另一点是，当通信另一端的套接字应用程序是非 MFC 应用程序时，必须避免执行以下操作：

`ar << pMsg;`

其中`pMsg`是指向从类`CObject`派生C++对象的指针。 这将发送与对象关联的额外 MFC 信息，服务器将无法理解它，就像它是 MFC 应用程序一样。

有关详细信息，请参阅：

- [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 套接字：背景](../mfc/windows-sockets-background.md)

- [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)

- [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)
