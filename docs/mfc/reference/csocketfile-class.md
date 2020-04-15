---
title: 套接字文件类
ms.date: 11/04/2016
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
helpviewer_keywords:
- CSocketFile [MFC], CSocketFile
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
ms.openlocfilehash: 83810a05925e5c8302240b61d95c131fdd78b426
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318159"
---
# <a name="csocketfile-class"></a>套接字文件类

用于通过 Windows 套接字在网络中发送和接收数据的 `CFile` 对象。

## <a name="syntax"></a>语法

```
class CSocketFile : public CFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[套接字文件：：套接字文件](#csocketfile)|构造 `CSocketFile` 对象。|

## <a name="remarks"></a>备注

为此，`CSocketFile`可以将对象附加到`CSocket`对象。 您还可以（通常也可以）将`CSocketFile`对象附加到对象，`CArchive`以简化使用 MFC 序列化发送和接收数据。

要序列化（发送）数据，请将其插入到存档中，存档调用`CSocketFile`成员函数将数据写入`CSocket`对象。 要从存档中提取（接收）数据。 这将导致存档调用`CSocketFile`成员函数从`CSocket`对象读取数据。

> [!TIP]
> 除了按照`CSocketFile`此处所述使用外，还可以将其用作独立文件对象，就像可以使用`CFile`它的基类一样。 您还可以使用`CSocketFile`任何基于存档的 MFC 序列化功能。 由于`CSocketFile`不支持所有`CFile`功能，因此某些默认 MFC 序列化功能与`CSocketFile`不兼容。 `CEditView`类尤其如此。 不应尝试`CEditView`使用`CArchive``CSocketFile``CEditView::SerializeRaw`改`CEditView::Serialize`用。 函数`SerializeRaw`期望文件对象具有没有 的`Seek``CSocketFile`函数，例如 。

使用`CArchive``CSocketFile`和`CSocket`时，可能会遇到`CSocket::Receive`输入循环 （由`PumpMessages(FD_READ)`） 等待请求的字节数的情况。 这是因为 Windows 套接字仅允许每个FD_READ通知一个 recv `CSocketFile` `CSocket`调用，并且允许每个FD_READ多个 recv 调用。 如果在没有要读取的数据时获得FD_READ，应用程序将挂起。 如果您从未获得另一个FD_READ，应用程序将停止通过套接字进行通信。

您可以按照如下方式解决此问题。 在`OnReceive`套接字类中，当从`CAsyncSocket::IOCtl(FIONREAD, ...)`套接字读取`Serialize`的预期数据超过一个 TCP 数据包（网络介质的最大传输单元，通常至少 1096 字节）时，在调用消息类的方法之前调用。 如果可用数据的大小小于所需大小，请等待接收所有数据，然后仅启动读取操作。

在下面的示例中，`m_dwExpected`是用户希望接收的大约字节数。 假定您在代码的其他位置声明它。

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

有关详细信息，请参阅 MFC 中的[Windows 套接字](../../mfc/windows-sockets-in-mfc.md)[、Windows 套接字：使用带存档的套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)以及[Windows 套接字 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>要求

**标题：** afxsock.h

## <a name="csocketfilecsocketfile"></a><a name="csocketfile"></a>套接字文件：：套接字文件

构造 `CSocketFile` 对象。

```
explicit CSocketFile(
    CSocket* pSocket,
    BOOL bArchiveCompatible = TRUE);
```

### <a name="parameters"></a>参数

*pSocket*<br/>
要附加到`CSocketFile`对象的套接字。

*b 存档兼容*<br/>
指定文件对象是否用于`CArchive`对象。 仅当您希望以独立方式使用`CSocketFile`对象时，才像独立`CFile`对象一样，具有某些限制，才传递 FALSE。 此标志更改附加到`CArchive``CSocketFile`对象的对象管理其缓冲区以进行读取的方式。

### <a name="remarks"></a>备注

当对象超出范围或删除时，对象的析构函数会与套接字对象分离。

> [!NOTE]
> 还可以`CSocketFile`用作没有`CArchive`对象的（受限）文件。 默认情况下，`CSocketFile`构造函数的*bArchive 兼容*参数为 TRUE。 这指定文件对象用于存档。 要使用没有存档的文件对象，请使用*bArchive 兼容*参数中的 FALSE。

在其"存档兼容"模式下，`CSocketFile`对象提供更好的性能并减少"死锁"的危险。 当发送和接收套接字相互等待或等待公共资源时，将发生死锁。 如果`CArchive`对象的工作方式与`CSocketFile``CFile`对象一起工作，则可能发生此情况。 使用`CFile`时，存档可以假定，如果接收的字节数少于其请求的字节数，则已达到文件结尾。

但是`CSocketFile`，对于 ，数据是基于消息的;缓冲区可以包含多条消息，因此接收少于请求的字节数并不意味着文件结束。 在这种情况下，应用程序不会像 在`CFile`中阻止，因为它可以使用 ，它可以继续从缓冲区读取消息，直到缓冲区为空。 [在这种情况下，CArchive：isBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty)函数可用于监视存档缓冲区的状态。

有关 使用`CSocketFile`的详细信息，请参阅[Windows 套接字：使用带存档](../../mfc/windows-sockets-using-sockets-with-archives.md)和 Windows[套接字的套接字：使用存档的套接字示例](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。

## <a name="see-also"></a>另请参阅

[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket 类](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocket 类](../../mfc/reference/csocket-class.md)
