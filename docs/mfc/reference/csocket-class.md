---
title: CSocket 类
ms.date: 11/04/2016
f1_keywords:
- CSocket
- AFXSOCK/CSocket
- AFXSOCK/CSocket::CSocket
- AFXSOCK/CSocket::Attach
- AFXSOCK/CSocket::CancelBlockingCall
- AFXSOCK/CSocket::Create
- AFXSOCK/CSocket::FromHandle
- AFXSOCK/CSocket::IsBlocking
- AFXSOCK/CSocket::OnMessagePending
helpviewer_keywords:
- CSocket [MFC], CSocket
- CSocket [MFC], Attach
- CSocket [MFC], CancelBlockingCall
- CSocket [MFC], Create
- CSocket [MFC], FromHandle
- CSocket [MFC], IsBlocking
- CSocket [MFC], OnMessagePending
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
ms.openlocfilehash: a861e557b7368d13d615aaf796faded93c72b040
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266557"
---
# <a name="csocket-class"></a>CSocket 类

派生自`CAsyncSocket`，继承其封装 Windows 套接字 API，而表示抽象比更高级别的`CAsyncSocket`对象。

## <a name="syntax"></a>语法

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSocket::CSocket](#csocket)|构造 `CSocket` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSocket::Attach](#attach)|将附加的套接字句柄`CSocket`对象。|
|[CSocket::CancelBlockingCall](#cancelblockingcall)|取消当前正在阻止调用。|
|[CSocket::Create](#create)|创建的套接字。|
|[CSocket::FromHandle](#fromhandle)|返回一个指向`CSocket`给定 SOCKET 句柄的对象。|
|[CSocket::IsBlocking](#isblocking)|确定阻止调用是否正在进行中。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CSocket::OnMessagePending](#onmessagepending)|等待阻止调用完成时调用以处理挂起的消息。|

## <a name="remarks"></a>备注

`CSocket` 适用于类`CSocketFile`和`CArchive`管理发送和接收的数据。

一个`CSocket`对象还提供了阻塞，这是至关重要的同步操作`CArchive`。 阻塞函数，如`Receive`， `Send`， `ReceiveFrom`， `SendTo`，并`Accept`(从所有继承`CAsyncSocket`)，不会返回`WSAEWOULDBLOCK`中的错误`CSocket`。 相反，这些函数等待，直到操作完成。 此外，原始调用如果将终止并显示错误 WSAEINTR`CancelBlockingCall`时这些函数之一阻止调用。

若要使用`CSocket`对象，请调用构造函数中，然后调用`Create`创建基础套接字句柄 （类型套接字）。 默认参数`Create`创建流套接字，但如果不使用与套接字`CArchive`对象，可以指定的参数，而是创建一个数据报套接字或绑定到特定端口以创建服务器套接字。 连接到客户端套接字`Connect`客户端和`Accept`服务器端。 然后创建`CSocketFile`对象，并将它关联到`CSocket`对象中`CSocketFile`构造函数。 接下来，创建`CArchive`用于将发送对象，一个用于接收数据 （根据需要），并将其关联与`CSocketFile`对象中`CArchive`构造函数。 当通信都完成后时，销毁`CArchive`， `CSocketFile`，和`CSocket`对象。 套接字的数据类型本文所述[Windows 套接字：背景](../../mfc/windows-sockets-background.md)。

当你使用`CArchive`与`CSocketFile`并`CSocket`，可能会遇到这种情况其中`CSocket::Receive`进入一个循环 (通过`PumpMessages(FD_READ)`) 等待所需的字节数。 这是因为 Windows 套接字允许每个 FD_READ 通知仅一次接收调用，但`CSocketFile`和`CSocket`允许每 FD_READ 的多个接收调用。 如果没有要读取的数据时收到 FD_READ，应用程序挂起。 如果永远不会收到另一个 FD_READ，应用程序将停止通过套接字进行通信。

可以按如下所示解决此问题。 在中`OnReceive`套接字类，调用方法`CAsyncSocket::IOCtl(FIONREAD, ...)`在调用之前`Serialize`消息类时预期的数据从套接字读取超过了一个 TCP 数据包 （最大传输单位的网络中的大小的方法通常至少 1096 字节)。 如果可用数据的大小小于所需，等待要接收和仅然后开始读取的操作的所有数据。

在以下示例中，`m_dwExpected`是近似的用户期望接收的字节数。 假设，将其声明其他位置在代码中。

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
>  在静态链接的 MFC 应用程序中的辅助线程中使用 MFC 套接字时，您必须在使用套接字的每个线程中调用 `AfxSocketInit` 来初始化套接字库。 默认情况下，仅在主线程中调用 `AfxSocketInit`。

有关详细信息，请参阅[MFC 中的 Windows 套接字](../../mfc/windows-sockets-in-mfc.md)， [Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)， [Windows 套接字：使用存档的套接字如何工作](../../mfc/windows-sockets-how-sockets-with-archives-work.md)， [Windows 套接字：操作顺序](../../mfc/windows-sockets-sequence-of-operations.md)， [Windows 套接字：使用存档的套接字的示例](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>要求

**标头：** afxsock.h

##  <a name="attach"></a>  CSocket::Attach

调用此成员函数可将附加`hSocket`句柄`CSocket`对象。

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>参数

*hSocket*<br/>
包含一个套接字的句柄。

### <a name="return-value"></a>返回值

如果函数运行成功，则为非零。

### <a name="remarks"></a>备注

SOCKET 句柄存储在对象的[m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket)数据成员。

有关详细信息，请参阅[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

##  <a name="cancelblockingcall"></a>  CSocket::CancelBlockingCall

调用此成员函数以取消当前正在阻止调用。

```
void CancelBlockingCall();
```

### <a name="remarks"></a>备注

此函数将取消此套接字的任何未完成的阻塞操作。 原始的阻止调用将尽快终止错误 WSAEINTR。

在阻止的情况下`Connect`操作，只要可行的但是它不可能的套接字资源释放该连接已完成 （，然后被重置） 之前，Windows 套接字实现将终止阻止的调用或操作已超时。这是可能需要明显仅当应用程序会立即尝试打开新的套接字中，（如果有没有套接字），或连接到对等方。

而不取消任何操作`Accept`可以使处于不确定状态的套接字。 如果应用程序取消阻止对套接字操作，则该应用程序可以依赖于能够执行套接字上的唯一操作是对的调用`Close`，尽管其他操作可能在某些 Windows 套接字实现上运行。 如果你需要为应用程序的最大可移植性，您必须小心，不要依赖于在取消后执行操作。

有关详细信息，请参阅[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="create"></a>  CSocket::Create

调用**创建**成员函数之后，构造一个套接字对象来创建 Windows 套接字并将其附加。

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>参数

*nSocketPort*<br/>
如果你想要选择的端口的 MFC 套接字或 0 开头使用特定端口。

*nSocketType*<br/>
SOCK_STREAM 或 SOCK_DGRAM。

*lpszSocketAddress*<br/>
指向一个包含连接的套接字，一个以点分隔的数字，如"128.56.22.8"的网络地址的字符串的指针。 此参数指示将 NULL 传递字符串`CSocket`实例应侦听的所有网络接口上的客户端活动。

### <a name="return-value"></a>返回值

如果函数成功，则非零值否则通过调用检索 0 和特定的错误代码`GetLastError`。

### <a name="remarks"></a>备注

`Create` 然后，调用`Bind`将套接字绑定到指定的地址。 支持以下的套接字类型：

- SOCK_STREAM 提供序列化，可靠、 双向、 基于连接的字节流。 使用传输控制协议 (TCP) 进行 Internet 地址族。

- SOCK_DGRAM 支持数据报，即无连接、 不可靠的固定 （通常很小） 的最大长度的缓冲区。 使用用户数据报协议 (UDP) 为 Internet 地址族。 若要使用此选项，您必须使用与套接字`CArchive`对象。

    > [!NOTE]
    >  `Accept`成员函数将一个新的空引用`CSocket`对象作为其参数。 在调用之前，必须构造此对象`Accept`。 请记住，如果此套接字对象超出范围，该连接将关闭。 不要调用`Create`此新的套接字对象。

有关流和数据报套接字的详细信息，请参阅文章[Windows 套接字：背景](../../mfc/windows-sockets-background.md)， [Windows 套接字：端口和套接字地址](../../mfc/windows-sockets-ports-and-socket-addresses.md)，和[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="csocket"></a>  CSocket::CSocket

构造 `CSocket` 对象。

```
CSocket();
```

### <a name="remarks"></a>备注

完成构造后，必须调用`Create`成员函数。

有关详细信息，请参阅[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="fromhandle"></a>  CSocket::FromHandle

返回一个指向`CSocket`对象。

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>参数

*hSocket*<br/>
包含一个套接字的句柄。

### <a name="return-value"></a>返回值

一个指向`CSocket`对象，或者如果没有，则为 NULL 没有`CSocket`对象附加到*hSocket*。

### <a name="remarks"></a>备注

如果给定的套接字的句柄，如果`CSocket`对象未附加到该句柄，则成员函数返回 NULL 并不会创建临时对象。

有关详细信息，请参阅[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="isblocking"></a>  CSocket::IsBlocking

调用此成员函数以确定是否阻止调用正在进行中。

```
BOOL IsBlocking();
```

### <a name="return-value"></a>返回值

如果阻止套接字; 非零值否则为 0。

### <a name="remarks"></a>备注

有关详细信息，请参阅[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="onmessagepending"></a>  CSocket::OnMessagePending

重写此成员函数以从 Windows 查找特定消息并在套接字中对其做出响应。

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>返回值

如果该消息已处理; 非零值否则为 0。

### <a name="remarks"></a>备注

这是一种高级可重写。

框架将调用`OnMessagePending`时套接字发送 Windows 消息，以便您有机会处理你的应用程序感兴趣的消息。 有关如何使用的示例`OnMessagePending`，请参阅文章[Windows 套接字：从套接字类派生](../../mfc/windows-sockets-deriving-from-socket-classes.md)。

有关详细信息，请参阅[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="see-also"></a>请参阅

[CAsyncSocket 类](../../mfc/reference/casyncsocket-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket 类](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile 类](../../mfc/reference/csocketfile-class.md)
