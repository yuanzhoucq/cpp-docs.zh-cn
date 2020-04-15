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
ms.openlocfilehash: 3f0a7a9a90250ede7b112cfbd9bc1ca14d583356
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318197"
---
# <a name="csocket-class"></a>CSocket 类

派生自`CAsyncSocket`继承其 Windows 套接字 API 的封装，并且表示比`CAsyncSocket`对象更高的抽象级别。

## <a name="syntax"></a>语法

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[套接字：：套接字](#csocket)|构造 `CSocket` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[套接字：：连接](#attach)|将 SOCKET 句柄附加到`CSocket`对象。|
|[套接字：：取消封锁呼叫](#cancelblockingcall)|取消当前正在进行的阻塞呼叫。|
|[套接字：：创建](#create)|创建套接字。|
|[套接字：：从手柄](#fromhandle)|返回指向`CSocket`对象的指针，给定一个 SOCKET 句柄。|
|[套接字：：正在阻塞](#isblocking)|确定阻止呼叫是否正在进行。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[套接字：：打开消息挂起](#onmessagepending)|在等待阻塞调用完成时调用以处理挂起的消息。|

## <a name="remarks"></a>备注

`CSocket`与类`CSocketFile`一起工作`CArchive`，并管理数据的发送和接收。

对象`CSocket`还提供阻塞，这对于`CArchive`的同步操作至关重要。 `Receive`阻止函数，如 ， `Send` `ReceiveFrom`、`SendTo`和`Accept`（全部继承`CAsyncSocket`自 ）， 不会在`WSAEWOULDBLOCK`中`CSocket`返回错误。 相反，这些函数等待操作完成。 此外，如果`CancelBlockingCall`在这些函数之一处于阻塞时调用，则原始调用将终止与错误 WSAEINTR。

要使用`CSocket`对象，请调用构造函数，然后调用`Create`以创建基础 SOCKET 句柄（类型 SOCKET）。 创建流套接字`Create`的默认参数，但如果不将套接字与`CArchive`对象一起使用，则可以指定一个参数来改为创建 datagram 套接字，或者绑定到特定端口以创建服务器套接字。 使用`Connect`客户端和`Accept`服务器端连接到客户端套接字。 然后创建一`CSocketFile`个对象并将其关联到`CSocket`构造函数中`CSocketFile`的对象。 接下来，创建用于`CArchive`发送的对象和用于接收数据的对象（根据需要），然后将它们与`CSocketFile``CArchive`构造函数中的对象相关联。 通信完成后，销毁`CArchive`、`CSocketFile`和`CSocket`对象。 在[Windows 套接字：背景](../../mfc/windows-sockets-background.md)） 一文中介绍了 SOCKET 数据类型。

使用`CArchive``CSocketFile`和`CSocket`时，可能会遇到`CSocket::Receive`输入循环 （由`PumpMessages(FD_READ)`） 等待请求的字节数的情况。 这是因为 Windows 套接字仅允许每个FD_READ通知一个 recv `CSocketFile` `CSocket`调用，并且允许每个FD_READ多个 recv 调用。 如果在没有要读取的数据时获得FD_READ，应用程序将挂起。 如果您从未获得另一个FD_READ，应用程序将停止通过套接字进行通信。

您可以按照如下方式解决此问题。 在`OnReceive`套接字类中，当从`CAsyncSocket::IOCtl(FIONREAD, ...)`套接字读取`Serialize`的预期数据超过一个 TCP 数据包（网络介质的最大传输单元，通常至少 1096 字节）时，在调用消息类的方法之前调用。 如果可用数据的大小小于所需大小，请等待接收所有数据，然后仅启动读取操作。

在下面的示例中，`m_dwExpected`是用户希望接收的大约字节数。 假定您在代码的其他位置声明它。

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
> 在静态链接的 MFC 应用程序中的辅助线程中使用 MFC 套接字时，您必须在使用套接字的每个线程中调用 `AfxSocketInit` 来初始化套接字库。 默认情况下，仅在主线程中调用 `AfxSocketInit`。

有关详细信息，请参阅 MFC 中的[Windows 套接字](../../mfc/windows-sockets-in-mfc.md)[、Windows 套接字：使用带存档的套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)[、Windows 套接字：具有存档的套接字的工作原理](../../mfc/windows-sockets-how-sockets-with-archives-work.md)[、Windows 套接字：操作顺序](../../mfc/windows-sockets-sequence-of-operations.md)[、Windows 套接字：使用存档的套接字示例](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>要求

**标题：** afxsock.h

## <a name="csocketattach"></a><a name="attach"></a>套接字：：连接

调用此成员函数以将`hSocket`句柄附加到`CSocket`对象。

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>参数

*hSocket*<br/>
包含套接字的句柄。

### <a name="return-value"></a>返回值

如果函数运行成功，则为非零。

### <a name="remarks"></a>备注

SOCKET 句柄存储在对象的[m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket)数据成员中。

有关详细信息，请参阅[Windows 套接字：使用带存档的套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

## <a name="csocketcancelblockingcall"></a><a name="cancelblockingcall"></a>套接字：：取消封锁呼叫

调用此成员函数以取消当前正在进行的阻塞呼叫。

```
void CancelBlockingCall();
```

### <a name="remarks"></a>备注

此功能取消此套接字的任何未完成的阻塞操作。 原始阻塞调用将尽快终止与错误 WSAEINTR。

在阻塞`Connect`操作的情况下，Windows Sockets 实现将尽快终止阻塞调用，但在连接完成（然后重置）或超时之前，可能无法释放套接字资源。仅当应用程序立即尝试打开新套接字（如果没有可用套接字）或连接到同一对等体时，这才可能明显。

取消除任外的任何操作`Accept`都会使套接字处于不确定状态。 如果应用程序取消对套接字的阻塞操作，则应用程序可以依赖于对套接字执行的唯一操作是调用`Close`，尽管其他操作可能在某些 Windows 套接字实现上工作。 如果希望应用程序具有最大可移植性，则必须小心不要依赖于取消后执行的操作。

有关详细信息，请参阅[Windows 套接字：使用带存档的套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="csocketcreate"></a><a name="create"></a>套接字：：创建

在构造套接字对象后调用 **"创建**成员"函数以创建 Windows 套接字并附加它。

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>参数

*nSocket端口*<br/>
要与套接字一起使用的特定端口，如果希望 MFC 选择端口，则为 0。

*nSocket 类型*<br/>
SOCK_STREAM或SOCK_DGRAM。

*lpszSocket地址*<br/>
指向包含连接套接字的网络地址的字符串的指针，虚线数字，如"128.56.22.8"。 传递此参数的 NULL 字符串指示`CSocket`实例应侦听所有网络接口上的客户端活动。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0，可以通过调用`GetLastError`检索特定的错误代码。

### <a name="remarks"></a>备注

`Create`然后调用`Bind`将套接字绑定到指定的地址。 支持以下套接字类型：

- SOCK_STREAM 提供序列化、可靠、双向、基于连接的字节流。 对互联网地址系列使用传输控制协议 （TCP）。

- SOCK_DGRAM支持数据图，这是固定（通常较小）最大长度的无连接不可靠的缓冲区。 对 Internet 地址系列使用用户数据图协议 （UDP）。 要使用此选项，不得将套接字与对象一`CArchive`起使用。

    > [!NOTE]
    >  成员`Accept`函数以引用新的空`CSocket`对象作为其参数。 在调用`Accept`之前，必须构造此对象。 请记住，如果此套接字对象超出范围，连接将关闭。 不要调用`Create`此新套接字对象。

有关流和数据报套接字的详细信息，请参阅[文章 Windows 套接字：背景](../../mfc/windows-sockets-background.md)[、Windows 套接字：端口和套接字地址](../../mfc/windows-sockets-ports-and-socket-addresses.md)，以及[Windows 套接字：使用带存档的套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="csocketcsocket"></a><a name="csocket"></a>套接字：：套接字

构造 `CSocket` 对象。

```
CSocket();
```

### <a name="remarks"></a>备注

构造后，必须调用`Create`成员函数。

有关详细信息，请参阅[Windows 套接字：使用带存档的套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="csocketfromhandle"></a><a name="fromhandle"></a>套接字：：从手柄

返回指向`CSocket`对象的指针。

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>参数

*hSocket*<br/>
包含套接字的句柄。

### <a name="return-value"></a>返回值

指向`CSocket`对象的指针，如果没有附加到`CSocket`*hSocket*的对象，则为 NULL。

### <a name="remarks"></a>备注

当给定一个 SOCKET 句柄`CSocket`时，如果对象未附加到句柄，成员函数将返回 NULL，并且不创建临时对象。

有关详细信息，请参阅[Windows 套接字：使用带存档的套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="csocketisblocking"></a><a name="isblocking"></a>套接字：：正在阻塞

调用此成员函数以确定阻止呼叫是否正在进行。

```
BOOL IsBlocking();
```

### <a name="return-value"></a>返回值

如果套接字阻塞，则非零;否则 0。

### <a name="remarks"></a>备注

有关详细信息，请参阅[Windows 套接字：使用带存档的套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="csocketonmessagepending"></a><a name="onmessagepending"></a>套接字：：打开消息挂起

重写此成员函数以查找 Windows 中的特定消息，并在套接字中响应它们。

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>返回值

处理消息时非零;否则 0。

### <a name="remarks"></a>备注

这是一个高级的可重写。

框架在套`OnMessagePending`接字正在泵送 Windows 消息时调用，以便您有机会处理应用程序感兴趣的消息。 有关如何使用`OnMessagePending`的示例，请参阅[Windows 套接字：从套接字类派生](../../mfc/windows-sockets-deriving-from-socket-classes.md)的文章。

有关详细信息，请参阅[Windows 套接字：使用带存档的套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="see-also"></a>另请参阅

[CAsyncSocket 类](../../mfc/reference/casyncsocket-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket 类](../../mfc/reference/casyncsocket-class.md)<br/>
[套接字文件类](../../mfc/reference/csocketfile-class.md)
