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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426551"
---
# <a name="csocket-class"></a>CSocket 类

派生自 `CAsyncSocket`，继承其 Windows 套接字 API 的封装，并表示比 `CAsyncSocket` 对象的更高的抽象级别。

## <a name="syntax"></a>语法

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CSocket：： CSocket](#csocket)|构造 `CSocket` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSocket：： Attach](#attach)|将套接字句柄附加到 `CSocket` 的对象。|
|[CSocket：： CancelBlockingCall](#cancelblockingcall)|取消当前正在进行的阻止调用。|
|[CSocket：： Create](#create)|创建套接字。|
|[CSocket：： FromHandle](#fromhandle)|给定套接字句柄，返回指向 `CSocket` 对象的指针。|
|[CSocket：： IsBlocking](#isblocking)|确定阻塞调用是否正在进行。|

### <a name="protected-methods"></a>受保护方法

|名称|说明|
|----------|-----------------|
|[CSocket：： OnMessagePending](#onmessagepending)|调用以在等待阻塞调用完成时处理挂起消息。|

## <a name="remarks"></a>备注

`CSocket` 与类一起使用 `CSocketFile` 和 `CArchive` 来管理数据的发送和接收。

`CSocket` 对象还提供了阻止功能，这对 `CArchive`同步操作至关重要。 阻止函数（如 `Receive`、`Send`、`ReceiveFrom`、`SendTo`和 `Accept` （所有继承自 `CAsyncSocket`）在 `WSAEWOULDBLOCK` 中不会返回 `CSocket`错误。 相反，这些函数将等待，直到操作完成。 此外，如果在其中一个函数正在阻止时调用 `CancelBlockingCall`，则原始调用将终止，并出现错误 WSAEINTR。

若要使用 `CSocket` 对象，请调用构造函数，然后调用 `Create` 以创建基础套接字句柄（类型为套接）。 `Create` 的默认参数会创建一个流套接字，但如果不将套接字与 `CArchive` 对象一起使用，则可以指定参数以创建数据报套接字，或绑定到特定端口来创建服务器套接字。 使用客户端上的 `Connect` 连接到客户端套接字，并在服务器端 `Accept`。 然后创建一个 `CSocketFile` 对象并将其与 `CSocketFile` 构造函数中的 `CSocket` 对象关联。 接下来，创建一个用于发送的 `CArchive` 对象，并创建一个用于接收数据的（根据需要），然后将它们与 `CArchive` 构造函数中的 `CSocketFile` 对象关联。 通信完成后，销毁 `CArchive`、`CSocketFile`和 `CSocket` 对象。 套接字数据类型在[Windows 套接： Background](../../mfc/windows-sockets-background.md)一文中进行了介绍。

如果将 `CArchive` 与 `CSocketFile` 和 `CSocket`结合使用，则可能会遇到 `CSocket::Receive` 进入循环（通过 `PumpMessages(FD_READ)`）等待请求的字节数的情况。 这是因为，每个 FD_READ 通知中的 Windows 套接字只允许一个接收调用，但是 `CSocketFile` 和 `CSocket` 允许每个 FD_READ 多次接收调用。 如果在没有要读取的数据的情况下收到 FD_READ，应用程序将挂起。 如果永远不会获得其他 FD_READ，应用程序将停止通过套接字进行通信。

可以解决此问题，如下所示。 在套接字类的 `OnReceive` 方法中，当从套接字读取预期的数据超过一个 TCP 数据包的大小（通常至少为1096字节）时，请调用 `CAsyncSocket::IOCtl(FIONREAD, ...)`，然后再调用消息类的 `Serialize` 方法。 如果可用数据的大小小于所需的大小，请等待接收所有数据，然后开始读取操作。

在下面的示例中，`m_dwExpected` 是用户预期接收的大约字节数。 假设您在代码中的其他位置声明它。

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
>  在静态链接的 MFC 应用程序中的辅助线程中使用 MFC 套接字时，您必须在使用套接字的每个线程中调用 `AfxSocketInit` 来初始化套接字库。 默认情况下，仅在主线程中调用 `AfxSocketInit`。

有关详细信息，请参阅[MFC 中的 Windows 套接字](../../mfc/windows-sockets-in-mfc.md)， [windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)， [Windows 套接字：使用存档的套接字如何工作](../../mfc/windows-sockets-how-sockets-with-archives-work.md)， [windows 套接字：操作顺序](../../mfc/windows-sockets-sequence-of-operations.md)， [windows 套接字：使用存档的套接字的示例](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>要求

**标头：** afxsock

##  <a name="attach"></a>CSocket：： Attach

调用此成员函数以将 `hSocket` 句柄附加到 `CSocket` 对象。

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>parameters

*hSocket*<br/>
包含套接字的句柄。

### <a name="return-value"></a>返回值

如果函数运行成功，则为非零。

### <a name="remarks"></a>备注

套接字句柄存储在对象的[m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket)数据成员中。

有关详细信息，请参阅[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

##  <a name="cancelblockingcall"></a>CSocket：： CancelBlockingCall

调用此成员函数可取消当前正在进行的阻止调用。

```
void CancelBlockingCall();
```

### <a name="remarks"></a>备注

此函数取消此套接字的任何未完成的阻止操作。 原始阻塞调用将尽快终止，并出现错误 WSAEINTR。

在阻止 `Connect` 操作的情况下，Windows 套接字实现将尽快终止阻止调用，但在连接完成（然后重置）或超时之前，不可能会释放套接字资源。仅当应用程序立即尝试打开新的套接字（如果没有可用的套接字）或连接到同一对等节点时，这可能会很明显。

取消除 `Accept` 以外的任何操作都可以使套接字处于不确定状态。 如果应用程序取消对套接字的阻止操作，则应用程序能够在套接字上执行的唯一操作是对 `Close`的调用，但其他操作可能适用于某些 Windows 套接字实现。 如果希望应用程序具有最大的可移植性，则必须注意不要依赖于在取消后执行操作。

有关详细信息，请参阅[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="create"></a>CSocket：： Create

构造套接字对象后，调用**create**成员函数以创建 Windows 套接字并附加它。

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>parameters

*nSocketPort*<br/>
要与套接字一起使用的特定端口，或者如果想要 MFC 选择端口，则为0。

*nSocketType*<br/>
SOCK_STREAM 或 SOCK_DGRAM。

*lpszSocketAddress*<br/>
指向字符串的指针，该字符串包含连接的套接字的网络地址，如 "128.56.22.8"。 为此参数传递 NULL 字符串指示 `CSocket` 实例应侦听所有网络接口上的客户端活动。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0，可以通过调用 `GetLastError`来检索特定的错误代码。

### <a name="remarks"></a>备注

然后 `Create` 调用 `Bind` 将套接字绑定到指定的地址。 支持以下套接字类型：

- SOCK_STREAM 提供了顺序的、可靠且基于连接的字节流。 对 Internet 地址系列使用传输控制协议（TCP）。

- SOCK_DGRAM 支持数据报，该数据报为固定的（通常是较小）的无连接和不可靠缓冲区。 为 Internet 地址系列使用用户数据报协议（UDP）。 若要使用此选项，则不能将套接字与 `CArchive` 对象一起使用。

    > [!NOTE]
    >  `Accept` 成员函数使用一个新的空 `CSocket` 对象作为其参数。 在调用 `Accept`之前，必须构造此对象。 请记住，如果此套接字对象超出范围，则连接将关闭。 请勿为此新的套接字对象调用 `Create`。

有关流和数据报套接字的详细信息，请参阅文章[Windows socket：背景](../../mfc/windows-sockets-background.md)、 [Windows 套接字：端口和套接字地址](../../mfc/windows-sockets-ports-and-socket-addresses.md)和[Windows 套接字：将套接字与存档配合使用](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="csocket"></a>CSocket：： CSocket

构造 `CSocket` 对象。

```
CSocket();
```

### <a name="remarks"></a>备注

构造后，必须调用 `Create` 成员函数。

有关详细信息，请参阅[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="fromhandle"></a>CSocket：： FromHandle

返回一个指向 `CSocket` 对象的指针。

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>parameters

*hSocket*<br/>
包含套接字的句柄。

### <a name="return-value"></a>返回值

指向 `CSocket` 对象的指针; 如果没有任何附加到*hSocket*的 `CSocket` 对象，则为 NULL。

### <a name="remarks"></a>备注

给定套接字句柄时，如果 `CSocket` 对象未附加到句柄，则成员函数将返回 NULL，并且不会创建临时对象。

有关详细信息，请参阅[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="isblocking"></a>CSocket：： IsBlocking

调用此成员函数以确定阻塞调用是否正在进行。

```
BOOL IsBlocking();
```

### <a name="return-value"></a>返回值

如果套接字正在阻止，则为非零值;否则为0。

### <a name="remarks"></a>备注

有关详细信息，请参阅[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="onmessagepending"></a>CSocket：： OnMessagePending

重写此成员函数以查找来自 Windows 的特定消息，并在你的套接字中响应这些消息。

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>返回值

如果消息已处理，则为非零值;否则为0。

### <a name="remarks"></a>备注

这是一种高级的可重写。

当套接字正在泵处理 Windows 消息时，框架会调用 `OnMessagePending`，这样您就有机会处理应用程序感兴趣的消息。 有关如何使用 `OnMessagePending`的示例，请参阅[Windows 套接字：从套接字派生的类](../../mfc/windows-sockets-deriving-from-socket-classes.md)。

有关详细信息，请参阅[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="see-also"></a>另请参阅

[CAsyncSocket 类](../../mfc/reference/casyncsocket-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket 类](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile 类](../../mfc/reference/csocketfile-class.md)
