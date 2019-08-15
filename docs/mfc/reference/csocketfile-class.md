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
ms.openlocfilehash: 3b969f81c0c6e1868a66aeaa1c4d9339792062df
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502453"
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

出于此目的, `CSocketFile`可以将对象`CSocket`附加到对象。 您还可以将`CSocketFile`对象附加`CArchive`到对象, 并通常执行此操作, 以简化使用 MFC 序列化发送和接收数据的操作。

若要对数据进行序列化 (发送), 请将其插入存档`CSocketFile` , 这将调用成员函数将`CSocket`数据写入对象。 若要反序列化 (接收) 数据, 请从存档中提取数据。 这将导致存档调用`CSocketFile`成员函数以`CSocket`从对象中读取数据。

> [!TIP]
>  除了使用`CSocketFile`此处所述的之外, 你还可以将其用作独立的文件对象, 就像`CFile`使用时一样。 你还可以将`CSocketFile`与任何基于存档的 MFC 序列化函数结合使用。 由于`CSocketFile`不支持`CFile`的所有功能, 因此某些默认 MFC 序列化函数与`CSocketFile`不兼容。 这对于`CEditView`类尤其如此。 不应尝试使用`CEditView` `CSocketFile` `CArchive` `CEditView::Serialize`附加到对象的对象对数据进行序列化; 请改用。 `CEditView::SerializeRaw` 函数要求文件对象具有不具有的`CSocketFile`函数 ( `Seek`如)。 `SerializeRaw`

使用`CArchive`与`CSocketFile`和`CSocket::Receive` `PumpMessages(FD_READ)`时, 您可能会遇到这样的情况: 进入循环 (通过) 等待请求的字节数。 `CSocket` 这是因为, 每个 FD_READ 通知仅允许一个接收调用, 但`CSocketFile` `CSocket`每个 FD_READ 允许多个接收调用。 如果在没有要读取的数据时获得 FD_READ, 则该应用程序挂起。 如果永远不会收到其他 FD_READ, 则应用程序会停止通过套接字进行通信。

可以解决此问题, 如下所示。 在套接字类的`CAsyncSocket::IOCtl(FIONREAD, ...)` `Serialize` 方法中,当从套接字读取预期的数据超过一个TCP数据包的大小(网络媒体的最大传输单元)之前,调用,然后调用消息`OnReceive`类的方法。, 通常至少为1096字节。 如果可用数据的大小小于所需的大小, 请等待接收所有数据, 然后开始读取操作。

在下面的示例中`m_dwExpected` , 是用户期望接收的大约字节数。 假设您在代码中的其他位置声明它。

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

有关详细信息, 请参阅[MFC 中的 windows 套接字](../../mfc/windows-sockets-in-mfc.md), [windows 套接字:使用带有存档](../../mfc/windows-sockets-using-sockets-with-archives.md)的套接字和[Windows 套接字 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>要求

**标头:** afxsock

##  <a name="csocketfile"></a>CSocketFile:: CSocketFile

构造 `CSocketFile` 对象。

```
explicit CSocketFile(
    CSocket* pSocket,
    BOOL bArchiveCompatible = TRUE);
```

### <a name="parameters"></a>参数

*pSocket*<br/>
要附加到`CSocketFile`对象的套接字。

*bArchiveCompatible*<br/>
指定文件对象是否用于`CArchive`对象。 仅当你希望以独立方式使用`CSocketFile`对象时, 才传递 FALSE, 因为`CFile`你需要具有某些限制。 此标志更改附加`CArchive` `CSocketFile`到对象的对象管理其缓冲区以便读取的方式。

### <a name="remarks"></a>备注

当对象超出范围或被删除时, 对象的析构函数会将其自身与套接字对象断开。

> [!NOTE]
>  还可用作`CArchive`无对象的 (受限) 文件。 `CSocketFile` 默认情况下, `CSocketFile`构造函数的*bArchiveCompatible*参数为 TRUE。 这会指定文件对象用于存档。 若要在不使用存档的情况下使用 file 对象, 请在*bArchiveCompatible*参数中传递 FALSE。

`CSocketFile`对象在其 "存档兼容" 模式下提供更好的性能, 并降低 "死锁" 的风险。 当发送和接收套接字彼此等待, 或针对公共资源时, 将发生死锁。 如果`CArchive`对象`CFile`与对象的处理方式相同, 则可能会发生这种情况。 `CSocketFile` 对于`CFile`, 存档可以假定, 如果它接收的字节数少于所请求的字节数, 则已到达文件结尾。

但`CSocketFile`对于, 数据是基于消息的; 缓冲区可包含多条消息, 因此, 接收的字节数少于所请求的字节数, 而不表示文件尾。 在这种情况下`CFile`, 应用程序不会被阻止, 这种情况下, 它可以继续从缓冲区读取消息, 直到缓冲区为空。 在这种情况下, [CArchive:: IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty)函数对于监视存档缓冲区的状态很有用。

有关使用的`CSocketFile`详细信息, 请参阅文章[Windows 套接字:将套接字用于](../../mfc/windows-sockets-using-sockets-with-archives.md)存档[和 Windows 套接字:使用存档](../../mfc/windows-sockets-example-of-sockets-using-archives.md)的套接字的示例。

## <a name="see-also"></a>请参阅

[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket 类](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocket 类](../../mfc/reference/csocket-class.md)
