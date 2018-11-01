---
title: Windows 套接字：字节排序
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: 74d3b53ae3ab476ef1224caed91f31929fcce1ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453946"
---
# <a name="windows-sockets-byte-ordering"></a>Windows 套接字：字节排序

本文和两篇配套文章介绍了 Windows 套接字编程中的若干问题。 本文介绍如何字节顺序。 文章中介绍了其他问题： [Windows 套接字： 阻止](../mfc/windows-sockets-blocking.md)并[Windows 套接字： 转换字符串](../mfc/windows-sockets-converting-strings.md)。

如果使用或派生自类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，将需要自行管理这些问题。 如果使用或派生自类[CSocket](../mfc/reference/csocket-class.md)，MFC 将为您管理它们。

## <a name="byte-ordering"></a>字节排序

有时，不同的计算机体系结构将存储数据使用不同的字节顺序。 例如，基于 Intel 的计算机将数据存储的 Macintosh (Motorola) 机相反的顺序。 Intel 字节顺序，称为"Little-endian"也是网络标准"big Endian"顺序的相反。 下表说明了这些术语。

### <a name="big--and-little-endian-byte-ordering"></a>大-和 Little-endian 字节顺序

|字节排序|含义|
|-------------------|-------------|
|Big Endian|最高有效字节位于某个词的左端。|
|小字节序|最高有效字节位于某个词的右端。|

通常情况下，无需担心如何发送和接收通过网络数据的字节顺序转换，但在有些情况下，必须将字节顺序转换在其中。

## <a name="when-you-must-convert-byte-orders"></a>当必须将字节顺序转换

需要进行转换的字节顺序在以下情况下：

- 要传递的需要解释的网络，而不是您正在向另一台计算机发送的数据的信息。 例如，您可能会将端口和地址，必须了解网络。

- 服务器应用程序与其进行通信的 MFC 应用程序 （并不为其没有源代码）。 这将调用的字节顺序转换如果在两台计算机不会共享相同的字节顺序。

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>不需要转换字节顺序

你可以避免转换在以下情况下的字节顺序的工作：

- 在这两个端点上的计算机可以同意不交换字节，并且这两台计算机使用相同的字节顺序。

- 与通信的服务器是一个 MFC 应用程序。

- 必须与通信的服务器的源代码以便您可以知道明确您是否必须转换字节顺序。

- 您可以移植到 MFC 的服务器。 这是相当轻松地完成，并且结果通常是更小、 更快的代码。

使用[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，必须自行管理任何必要的字节顺序转换。 Windows 套接字标准化"big Endian"字节顺序模型，并提供此顺序和其他人之间进行转换的函数。 [CArchive](../mfc/reference/carchive-class.md)，但是，与使用该[CSocket](../mfc/reference/csocket-class.md)，使用相反 ("Little-endian") 的顺序，但`CArchive`负责为您的字节顺序转换的详细信息。 通过使用此应用程序中的标准排序或使用 Windows 套接字字节顺序转换函数，可以使更易于移植您的代码。

理想情况下使用 MFC 套接字是编写两个通信端时： 在两端都使用 MFC。 如果你正在编写的应用程序将通信与非 MFC 应用程序，如 FTP 服务器，您可能需要管理字节交换自己之前将数据传递给存档对象中，使用 Windows 套接字转换例程**ntohs**， **ntohl**， **htons**，和**htonl**。 在本文后面部分会显示与非 MFC 应用程序的通信中使用这些函数的示例。

> [!NOTE]
>  如果另一端的通信不是一个 MFC 应用程序，您还必须避免流式处理 c + + 对象派生自`CObject`到您的存档因为接收方将无法再来处理它们。 请参阅中的说明[Windows 套接字： 使用存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)。

有关字节顺序的详细信息，请参阅 Windows SDK 中提供的 Windows 套接字规范。

## <a name="a-byte-order-conversion-example"></a>字节顺序转换示例

下面的示例演示的序列化函数`CSocket`使用存档的对象。 它还阐释了使用 Windows 套接字 API 中的字节顺序转换函数。

此示例显示了要在其中编写与非 MFC 服务器应用程序可以对源代码没有访问权限进行通信的客户端的方案。 在此方案中，您必须假定非 MFC 服务器使用标准网络字节顺序。 与此相反，MFC 客户端应用程序使用`CArchive`对象使用`CSocket`对象，和`CArchive`使用"Little-endian"字节顺序，标准网络相反。

假设您计划与其进行通信的非 MFC 服务器具有如下所示的消息包的已建立的协议：

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

在 MFC 术语中，这就表示，如下所示：

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

C + +**结构**是作为类实质上是相同的操作。 `Message`结构可以具有成员函数，例如`Serialize`成员函数声明上方。 `Serialize`成员函数可能如下所示：

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

因为字节顺序的另一端上的非 MFC 服务器应用程序之间没有明显不匹配，此示例将调用的数据的字节顺序转换和`CArchive`用于 MFC 客户端应用程序的另一端。 该示例演示了几个 Windows 套接字提供的字节顺序转换函数。 下表描述了这些函数。

### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows 套接字字节顺序转换函数

|函数|目标|
|--------------|-------------|
|**ntohs**|将 16 位数量由网络字节顺序转换为主机字节顺序 (big Endian 到小 Endian)。|
|**ntohl**|将 32 位数量由网络字节顺序转换为主机字节顺序 (big Endian 到小 Endian)。|
|**Htons**|将 16 位数量由主机字节顺序转换为网络字节顺序 (小 Endian 对 big Endian)。|
|**Htonl**|将 32 位数量由主机字节顺序转换为网络字节顺序 (小 Endian 对 big Endian)。|

在此示例中的另一点是，非 MFC 应用程序通信的另一端上的套接字应用程序时，您必须避免出现如下所示：

`ar << pMsg;`

其中`pMsg`是指向派生类中的 c + + 对象的`CObject`。 这将发送与对象和服务器相关联的额外 MFC 信息不能理解它，就像它是一样的 MFC 应用程序。

有关详细信息，请参见:

- [Windows 套接字：使用 CAsyncSocket 类](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 套接字：背景](../mfc/windows-sockets-background.md)

- [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)

- [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)

