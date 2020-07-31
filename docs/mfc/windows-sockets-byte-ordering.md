---
title: Windows 套接字：字节排序
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: f00936f3de07df8c1e4d9df1c678b2cfd5f3e3ad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226797"
---
# <a name="windows-sockets-byte-ordering"></a>Windows 套接字：字节排序

本文和两篇配套文章介绍了 Windows 套接字编程中的若干问题。 本文介绍了字节排序。 文章： [Windows socket：阻止](../mfc/windows-sockets-blocking.md)和[Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)中介绍了其他问题。

如果使用类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)或从类派生，则需自行管理这些问题。 如果使用类[CSocket](../mfc/reference/csocket-class.md)或从类派生，则 MFC 会为你进行管理。

## <a name="byte-ordering"></a>字节排序

不同的计算机体系结构有时使用不同的字节顺序存储数据。 例如，基于 Intel 的计算机以 Macintosh （Motorola）计算机的相反顺序存储数据。 Intel 字节顺序称为 "小字节序"，也是网络标准 "大字节序" 顺序的反向。 下表说明了这些术语。

### <a name="big--and-little-endian-byte-ordering"></a>大和小字节序字节排序

|字节排序|含义|
|-------------------|-------------|
|大字节序|最重要的字节位于单词的左侧。|
|小字节序|最重要的字节位于单词的右端。|

通常，您不必担心通过网络发送和接收的数据的字节顺序转换，但在某些情况下，必须转换字节顺序。

## <a name="when-you-must-convert-byte-orders"></a>必须转换字节顺序

需要在以下情况下转换字节顺序：

- 要传递需要由网络解释的信息，而不是发送到另一台计算机的数据。 例如，你可能会传递网络必须理解的端口和地址。

- 要与之通信的服务器应用程序不是 MFC 应用程序（并且您没有该应用程序的源代码）。 如果两台计算机不共享相同的字节顺序，则这将调用字节顺序转换。

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>不需要转换字节顺序时

在以下情况下，你可以避免转换字节顺序：

- 两端的计算机都可以同意不交换字节，并且两台计算机使用相同的字节顺序。

- 要与之通信的服务器是 MFC 应用程序。

- 你具有要与之通信的服务器的源代码，因此你可以明确地判断是否必须转换字节顺序。

- 您可以将服务器移植到 MFC。 这相当简单，而且结果通常更小，代码更快。

使用[CAsyncSocket](../mfc/reference/casyncsocket-class.md)时，必须自行管理任何所需的字节顺序转换。 Windows 套接字对 "大字节序" 字节顺序模型进行标准化，并提供在此顺序和其他顺序之间进行转换的函数。 然而， [CArchive](../mfc/reference/carchive-class.md)用于[CSocket](../mfc/reference/csocket-class.md)，它使用相反的（"小字节序"）顺序，但 `CArchive` 会为你处理字节顺序转换的详细信息。 通过在应用程序中使用此标准排序，或者使用 Windows 套接字字节顺序转换函数，可以使代码更易于移植。

使用 MFC 套接字的理想情况是在同时编写通信的两端：在两端使用 MFC。 如果你正在编写将与非 MFC 应用程序（如 FTP 服务器）进行通信的应用程序，则在将数据传递到 archive 对象之前，你可能需要使用 Windows 套接字转换例程**ntohs**、 **ntohl**、 **htons**和**htonl**来管理自己的字节交换。 本文稍后将显示与非 MFC 应用程序通信时所用的这些功能的示例。

> [!NOTE]
> 如果通信的另一端不是 MFC 应用程序，则还必须避免将派生自的 c + + 对象流式 `CObject` 处理到存档中，因为接收方将无法处理它们。 请参阅[Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)中的说明。

有关字节顺序的详细信息，请参阅 Windows SDK 中提供的 Windows 套接字规范。

## <a name="a-byte-order-conversion-example"></a>字节顺序转换示例

下面的示例演示使用存档的对象的序列化函数 `CSocket` 。 它还说明了如何在 Windows 套接字 API 中使用字节顺序转换函数。

此示例展示了这样一种情况：您正在编写一个客户端，该客户端与您无权访问源代码的非 MFC 服务器应用程序进行通信。 在此方案中，您必须假定非 MFC 服务器使用标准网络字节顺序。 与此相反，MFC 客户端应用程序将 `CArchive` 对象与 `CSocket` 对象结合使用，并 `CArchive` 使用 "小字节序" 字节顺序（与网络标准相反）。

假设你计划与之通信的非 MFC 服务器的消息包具有已建立的协议，如下所示：

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

在 MFC 术语中，这会表达如下：

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

在 c + + 中，与 **`struct`** 类本质上是相同的。 `Message`结构可以具有成员函数，如 `Serialize` 上面声明的成员函数。 该 `Serialize` 成员函数可能如下所示：

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

此示例将对数据进行字节顺序转换，因为一端的非 MFC 服务器应用程序的字节排序与 `CArchive` 另一端上的 mfc 客户端应用程序中使用的字节顺序不匹配。 该示例演示了 Windows 套接字提供的多个字节顺序转换函数。 下表介绍了这些函数。

### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows 套接字字节顺序转换函数

|函数|用途|
|--------------|-------------|
|**ntohs**|将16位数量从网络字节顺序转换为主机字节顺序（大字节序到小字节序）。|
|**ntohl**|将32位的数量从网络字节顺序转换为主机字节顺序（大字节序到小字节序）。|
|**Htons**|将16位数量从主机字节顺序转换为网络字节顺序（从小到大字节序）。|
|**Htonl**|将32位的数量从主机字节顺序转换为网络字节顺序（从小到大字节序）。|

此示例的另一点是，当通信的另一端上的套接字应用程序是非 MFC 应用程序时，必须避免执行如下所示的操作：

`ar << pMsg;`

其中 `pMsg` ，是指向派生自类的 c + + 对象的指针 `CObject` 。 这将发送与对象关联的额外 MFC 信息，服务器将不会对其进行了解，这与它是 MFC 应用程序时一样。

有关详细信息，请参阅：

- [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 套接字：背景](../mfc/windows-sockets-background.md)

- [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)

- [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)
