---
title: Windows 套接字：使用存档的套接字如何工作
ms.date: 11/19/2018
helpviewer_keywords:
- Windows Sockets [MFC], synchronous
- sockets [MFC], synchronous operation
- sockets [MFC], with archives
- synchronous state socket
- Windows Sockets [MFC], with archives
- two-state socket object
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
ms.openlocfilehash: f6101193c85e41fbf82681b0b2ae1e09e4162f87
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52174907"
---
# <a name="windows-sockets-how-sockets-with-archives-work"></a>Windows 套接字：使用存档的套接字如何工作

本文介绍如何[CSocket](../mfc/reference/csocket-class.md)对象， [CSocketFile](../mfc/reference/csocketfile-class.md)对象，和一个[CArchive](../mfc/reference/carchive-class.md)对象组合以简化发送和接收通过 Windows 数据套接字。

文章[Windows 套接字： 套接字的使用存档示例](../mfc/windows-sockets-example-of-sockets-using-archives.md)显示`PacketSerialize`函数。 中的存档对象`PacketSerialize`示例非常类似于存档对象传递给 MFC[序列化](../mfc/reference/cobject-class.md#serialize)函数。 关键的区别是，针对套接字，存档并不附加到一种标准[CFile](../mfc/reference/cfile-class.md) （通常使用的磁盘文件相关联） 的对象而`CSocketFile`对象。 而不是连接到磁盘文件，`CSocketFile`对象连接到`CSocket`对象。

一个`CArchive`对象管理缓冲区。 存储 （发送） 存档的缓冲区已满时，关联`CFile`对象写出缓冲区的内容。 正在刷新的缓冲区的附加到套接字存档相当于将发送一条消息。 当加载 （接收） 存档的缓冲区已满，`CFile`对象停止读取，直到缓冲区重新变为可用。

类`CSocketFile`派生自`CFile`，但它不支持[CFile](../mfc/reference/cfile-class.md)成员函数，如定位函数 (`Seek`， `GetLength`， `SetLength`，依此类推)，锁定函数 （`LockRange`， `UnlockRange`)，或`GetPosition`函数。 所有[CSocketFile](../mfc/reference/csocketfile-class.md)对象必须执行操作是写入或读取到或从关联的字节序列`CSocket`对象。 由于不涉及一个文件，因此操作，例如`Seek`和`GetPosition`而言毫无意义。 `CSocketFile` 派生自`CFile`，因此它通常会继承所有这些成员函数。 若要避免此情形，不受支持`CFile`成员函数将被重写`CSocketFile`引发[CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)。

`CSocketFile`对象调用成员函数的其`CSocket`要发送或接收数据对象。

下图显示通信的两面上的这些对象之间的关系。

![CArchive、 CSocketFile 和 CSocket](../mfc/media/vc38ia1.gif "CArchive、 CSocketFile 和 CSocket") <br/>
CArchive、CSocketFile 和 CSocket

此明显的目的是复杂性的防止您的自行管理的套接字的详细信息。 创建套接字、 文件和存档，然后首先将其插入到存档或从存档中解压缩的发送或接收数据。 [CArchive](../mfc/reference/carchive-class.md)， [CSocketFile](../mfc/reference/csocketfile-class.md)，和[CSocket](../mfc/reference/csocket-class.md)管理在后台的详细信息。

一个`CSocket`对象实际上是一个两个状态对象： 有时异步 （常用状态） 和有时同步。 在其异步状态套接字可以从框架接收异步通知。 但是，如接收或发送数据操作期间，套接字变为同步。 这意味着套接字会收到无需再异步通知，直到完成同步操作。 因为它将切换模式，例如，可以执行类似于以下内容：

[!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/cpp/windows-sockets-how-sockets-with-archives-work_1.cpp)]

如果`CSocket`未实现为两个状态对象，它可以接收相同类型的事件的其他通知，而在处理前一次通知。 例如，可能会得到`OnReceive`通知处理时`OnReceive`。 在上述代码片段中，提取`str`从存档可能导致递归。 通过切换状态，`CSocket`可以阻止其他通知，从而防止递归。 一般规则是内部通知的任何通知。

> [!NOTE]
> 一个`CSocketFile`还可用作 （受限） 文件，如果没有`CArchive`对象。 默认情况下`CSocketFile`构造函数的*bArchiveCompatible*参数是**TRUE**。 这指定为用于存档文件对象。 若要使用但未存档的文件对象，将传递**FALSE**中*bArchiveCompatible*参数。

在"存档兼容"模式下，`CSocketFile`对象提供了更好的性能并减少了危险"死锁"。 当这两个发送和接收套接字都等待对方，或等待常见资源发生死锁。 如果这种情况下可能会出现`CArchive`对象使用过`CSocketFile`的方式与其处理`CFile`对象。 使用`CFile`，存档可以假定，如果它收到较少的字节数比请求它时，文件结尾达到了。 使用`CSocketFile`，但是，数据是基于消息; 缓冲区中可以包含多条消息，因此接收请求的字节数少于并不表示文件结尾。 在此情况下不会阻止应用程序，因为它可能与`CFile`，并且可以继续从缓冲区读取消息，直到缓冲区为空。 [IsBufferEmpty](../mfc/reference/carchive-class.md#isbufferempty)函数，在`CArchive`用于监视在这种情况中的存档文件的缓冲区的状态。

有关详细信息，请参阅[Windows 套接字： 使用存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)

## <a name="see-also"></a>请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)<br/>
[Cobject:: Serialize](../mfc/reference/cobject-class.md#serialize)
