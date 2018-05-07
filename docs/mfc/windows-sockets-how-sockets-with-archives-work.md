---
title: Windows 套接字： 使用存档的套接字如何 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], synchronous
- sockets [MFC], synchronous operation
- sockets [MFC], with archives
- synchronous state socket
- Windows Sockets [MFC], with archives
- two-state socket object
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c03ae586e346be2ba1e7c71475b69318ded0dd18
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="windows-sockets-how-sockets-with-archives-work"></a>Windows 套接字：使用存档的套接字如何工作
此文章介绍了如何[CSocket](../mfc/reference/csocket-class.md)对象， [CSocketFile](../mfc/reference/csocketfile-class.md)对象，和一个[CArchive](../mfc/reference/carchive-class.md)对象结合来简化发送和接收数据通过 Windows套接字。  
  
 文章[Windows 套接字： 套接字的使用存档示例](../mfc/windows-sockets-example-of-sockets-using-archives.md)显示**PacketSerialize**函数。 中的存档对象**PacketSerialize**示例才会非常类似于传递到 MFC 的存档对象[序列化](../mfc/reference/cobject-class.md#serialize)函数。 基本差异是，对于套接字，存档并不附加到一种标准[CFile](../mfc/reference/cfile-class.md) （通常使用的磁盘文件相关联） 的对象而`CSocketFile`对象。 而不是连接到磁盘文件，`CSocketFile`对象连接到`CSocket`对象。  
  
 A`CArchive`对象管理的缓冲区。 存储 （发送） 存档的缓冲区已满时，一个关联`CFile`对象写出的缓冲区的内容。 刷新的缓冲区的存档的套接字附加相当于发送消息。 当加载 （接收） 存档的缓冲区已满，`CFile`对象停止读取，直到缓冲区重新变为可用。  
  
 类`CSocketFile`派生自`CFile`，但它不支持[CFile](../mfc/reference/cfile-class.md)成员函数，如定位函数 (`Seek`， `GetLength`， `SetLength`，依次类推)，锁定函数 （`LockRange`， `UnlockRange`)，或`GetPosition`函数。 所有[CSocketFile](../mfc/reference/csocketfile-class.md)对象必须执行操作是写入或读取的字节到或从关联的序列`CSocket`对象。 由于不涉及到一个文件，因此操作，如`Seek`和`GetPosition`而言毫无意义。 `CSocketFile` 派生自`CFile`，因此它通常将继承所有这些成员函数。 若要阻止此操作，请使用不受支持`CFile`中重写成员函数是`CSocketFile`引发[CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)。  
  
 `CSocketFile`对象调用成员函数的其`CSocket`对象发送或接收数据。  
  
 下图显示的通信的两端上的这些对象之间的关系。  
  
 ![CArchive、 CSocketFile 和 CSocket](../mfc/media/vc38ia1.gif "vc38ia1")  
CArchive、CSocketFile 和 CSocket  
  
 这种明显复杂性旨在使您不必自行管理的套接字的详细信息。 创建套接字、 文件和存档，然后通过将其插入到存档或从存档中提取开始发送或接收数据。 [CArchive](../mfc/reference/carchive-class.md)， [CSocketFile](../mfc/reference/csocketfile-class.md)，和[CSocket](../mfc/reference/csocket-class.md)管理在幕后的详细信息。  
  
 A`CSocket`对象实际上是一个双态对象： 有时异步 （常用状态） 和有时同步。 在其异步状态，套接字可以从框架接收异步通知。 但是，如接收或发送数据操作期间，套接字变为同步。 这意味着套接字将接收不进行其他异步通知，直到同步操作已完成。 由于套接字切换模式，例如，可以执行类似于以下内容：  
  
 [!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/cpp/windows-sockets-how-sockets-with-archives-work_1.cpp)]  
  
 如果`CSocket`未实现为两个状态对象，它可以为相同类型的事件的其他通知你已在处理时接收前一次的通知。 例如，你可能获得`OnReceive`处理时通知`OnReceive`。 在上述代码片段中，提取`str`从存档可能导致递归。 通过切换状态，`CSocket`通过阻止其他通知禁止递归。 一般规则是通知内的没有通知。  
  
> [!NOTE]
>  A`CSocketFile`还可用作 （受限） 文件，而没有`CArchive`对象。 默认情况下，`CSocketFile`构造函数的`bArchiveCompatible`参数是**TRUE**。 此特性指定的文件对象有用于存档。 若要使用但未存档的文件对象，将传递**FALSE**中`bArchiveCompatible`参数。  
  
 在"存档兼容"模式下，`CSocketFile`对象提供更好的性能并减少的危险"死锁"。 当等待相互关联，或等待常见的资源这两个发送和接收套接字时，将发生死锁。 如果这种情况下可能会出现`CArchive`对象结合`CSocketFile`与其处理的方式`CFile`对象。 与`CFile`，存档可以假定，如果它收到较少的字节数比其请求，文件结尾已达到。 与`CSocketFile`，但是，数据是基于消息; 缓冲区中可以包含多条消息，因此接收请求的字节数少于并不意味着文件结尾。 在此情况下不会阻止应用程序，因为它可能与`CFile`，它可以继续从缓冲区中读取消息，直到缓冲区为空。 [IsBufferEmpty](../mfc/reference/carchive-class.md#isbufferempty)函数中`CArchive`可用于监视这种情况下的存档的缓冲区的状态。  
  
 有关详细信息，请参阅[Windows 套接字： 使用存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)   
 [Cobject:: Serialize](../mfc/reference/cobject-class.md#serialize)

