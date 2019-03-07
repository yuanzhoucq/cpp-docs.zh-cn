---
title: CSocketFile 类
ms.date: 11/04/2016
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
helpviewer_keywords:
- CSocketFile [MFC], CSocketFile
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
ms.openlocfilehash: f3fa73320ae34283b0cdac559111a53a879c031c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274266"
---
# <a name="csocketfile-class"></a>CSocketFile 类

用于通过 Windows 套接字在网络中发送和接收数据的 `CFile` 对象。

## <a name="syntax"></a>语法

```
class CSocketFile : public CFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSocketFile::CSocketFile](#csocketfile)|构造 `CSocketFile` 对象。|

## <a name="remarks"></a>备注

可以将附加`CSocketFile`对象传递给`CSocket`实现此目的的对象。 也可以，并通常，附加`CSocketFile`对象传递给`CArchive`来简化发送和接收数据使用 MFC 序列化的对象。

要序列化数据 （发送），应将其插入到存档，其中调用`CSocketFile`成员函数以将数据写入到`CSocket`对象。 要反序列化 （接收） 存档中提取数据。 这会导致要调用的存档`CSocketFile`成员函数从中读取数据`CSocket`对象。

> [!TIP]
>  除了使用以外`CSocketFile`如下所述，您可以使用它作为独立的文件对象，就像可以使用`CFile`，将其基类。 此外可以使用`CSocketFile`与任何基于存档的 MFC 序列化函数。 因为`CSocketFile`不支持的所有`CFile`的功能，某些默认 MFC 序列化函数都不符合`CSocketFile`。 这更是如此的`CEditView`类。 不应尝试序列化`CEditView`通过数据`CArchive`对象附加到`CSocketFile`对象使用`CEditView::SerializeRaw`; 使用`CEditView::Serialize`相反。 `SerializeRaw`函数需要的文件对象具有函数，如`Seek`，则该`CSocketFile`没有。

当你使用`CArchive`与`CSocketFile`并`CSocket`，可能会遇到这种情况其中`CSocket::Receive`进入一个循环 (通过`PumpMessages(FD_READ)`) 等待所需的字节数。 这是因为 Windows 套接字允许每个 FD_READ 通知仅一次接收调用，但`CSocketFile`和`CSocket`允许每 FD_READ 的多个接收调用。 如果没有要读取的数据时收到 FD_READ，应用程序挂起。 如果永远不会收到另一个 FD_READ，应用程序将停止通过套接字进行通信。

可以按如下所示解决此问题。 在中`OnReceive`套接字类，调用方法`CAsyncSocket::IOCtl(FIONREAD, ...)`在调用之前`Serialize`消息类时预期的数据从套接字读取超过了一个 TCP 数据包 （最大传输单位的网络中的大小的方法通常至少 1096 字节)。 如果可用数据的大小小于所需，等待要接收和仅然后开始读取的操作的所有数据。

在以下示例中，`m_dwExpected`是近似的用户期望接收的字节数。 假设，将其声明其他位置在代码中。

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

有关详细信息，请参阅[MFC 中的 Windows 套接字](../../mfc/windows-sockets-in-mfc.md)， [Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)，以及[Windows Sockets 2 API](/windows/desktop/WinSock/windows-sockets-start-page-2)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>要求

**标头：** afxsock.h

##  <a name="csocketfile"></a>  CSocketFile::CSocketFile

构造 `CSocketFile` 对象。

```
explicit CSocketFile(
    CSocket* pSocket,
    BOOL bArchiveCompatible = TRUE);
```

### <a name="parameters"></a>参数

*pSocket*<br/>
要将附加到的套接字`CSocketFile`对象。

*bArchiveCompatible*<br/>
指定文件的对象是否为用于`CArchive`对象。 传递 FALSE 仅当你想要使用`CSocketFile`对象以独立的方式，就像独立`CFile`对象，但存在某些限制。 此标志会更改如何`CArchive`对象附加到`CSocketFile`对象管理进行读取其缓冲区。

### <a name="remarks"></a>备注

对象的析构函数取消关联本身从套接字对象超出范围或被删除的对象时。

> [!NOTE]
>  一个`CSocketFile`还可用作 （受限） 文件，如果没有`CArchive`对象。 默认情况下`CSocketFile`构造函数的*bArchiveCompatible*参数为 TRUE。 这指定为用于存档文件对象。 若要使用但未存档的文件对象，传入 FALSE *bArchiveCompatible*参数。

在"存档兼容"模式下，`CSocketFile`对象提供了更好的性能并减少了危险"死锁"。 这两个发送和接收套接字等待相互关联，或为常见的资源时，将发生死锁。 如果这种情况下可能会出现`CArchive`对象使用过`CSocketFile`的方式与其处理`CFile`对象。 使用`CFile`，存档可以假定，如果它收到较少的字节数比请求它时，文件结尾达到了。

使用`CSocketFile`，但是，数据是基于消息; 缓冲区中可以包含多条消息，因此接收请求的字节数少于并不表示文件结尾。 在此情况下不会阻止应用程序，因为它可能与`CFile`，并且可以继续从缓冲区读取消息，直到缓冲区为空。 [CArchive::IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty)函数可用于监视在这种情况中的存档文件的缓冲区的状态。

有关详细信息的使用`CSocketFile`，请参阅文章[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)和[Windows 套接字：使用存档的套接字的示例](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。

## <a name="see-also"></a>请参阅

[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket 类](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocket 类](../../mfc/reference/csocket-class.md)
