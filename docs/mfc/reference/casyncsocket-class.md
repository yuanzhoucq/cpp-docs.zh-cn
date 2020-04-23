---
title: CAsyncSocket 类
ms.date: 09/03/2019
f1_keywords:
- CAsyncSocket
- AFXSOCK/CAsyncSocket
- AFXSOCK/CAsyncSocket::CAsyncSocket
- AFXSOCK/CAsyncSocket::Accept
- AFXSOCK/CAsyncSocket::AsyncSelect
- AFXSOCK/CAsyncSocket::Attach
- AFXSOCK/CAsyncSocket::Bind
- AFXSOCK/CAsyncSocket::Close
- AFXSOCK/CAsyncSocket::Connect
- AFXSOCK/CAsyncSocket::Create
- AFXSOCK/CAsyncSocket::Detach
- AFXSOCK/CAsyncSocket::FromHandle
- AFXSOCK/CAsyncSocket::GetLastError
- AFXSOCK/CAsyncSocket::GetPeerName
- AFXSOCK/CAsyncSocket::GetPeerNameEx
- AFXSOCK/CAsyncSocket::GetSockName
- AFXSOCK/CAsyncSocket::GetSockNameEx
- AFXSOCK/CAsyncSocket::GetSockOpt
- AFXSOCK/CAsyncSocket::IOCtl
- AFXSOCK/CAsyncSocket::Listen
- AFXSOCK/CAsyncSocket::Receive
- AFXSOCK/CAsyncSocket::ReceiveFrom
- AFXSOCK/CAsyncSocket::ReceiveFromEx
- AFXSOCK/CAsyncSocket::Send
- AFXSOCK/CAsyncSocket::SendTo
- AFXSOCK/CAsyncSocket::SendToEx
- AFXSOCK/CAsyncSocket::SetSockOpt
- AFXSOCK/CAsyncSocket::ShutDown
- AFXSOCK/CASyncSocket::Socket
- AFXSOCK/CAsyncSocket::OnAccept
- AFXSOCK/CAsyncSocket::OnClose
- AFXSOCK/CAsyncSocket::OnConnect
- AFXSOCK/CAsyncSocket::OnOutOfBandData
- AFXSOCK/CAsyncSocket::OnReceive
- AFXSOCK/CAsyncSocket::OnSend
- AFXSOCK/CAsyncSocket::m_hSocket
helpviewer_keywords:
- CAsyncSocket [MFC], CAsyncSocket
- CAsyncSocket [MFC], Accept
- CAsyncSocket [MFC], AsyncSelect
- CAsyncSocket [MFC], Attach
- CAsyncSocket [MFC], Bind
- CAsyncSocket [MFC], Close
- CAsyncSocket [MFC], Connect
- CAsyncSocket [MFC], Create
- CAsyncSocket [MFC], Detach
- CAsyncSocket [MFC], FromHandle
- CAsyncSocket [MFC], GetLastError
- CAsyncSocket [MFC], GetPeerName
- CAsyncSocket [MFC], GetPeerNameEx
- CAsyncSocket [MFC], GetSockName
- CAsyncSocket [MFC], GetSockNameEx
- CAsyncSocket [MFC], GetSockOpt
- CAsyncSocket [MFC], IOCtl
- CAsyncSocket [MFC], Listen
- CAsyncSocket [MFC], Receive
- CAsyncSocket [MFC], ReceiveFrom
- CAsyncSocket [MFC], ReceiveFromEx
- CAsyncSocket [MFC], Send
- CAsyncSocket [MFC], SendTo
- CAsyncSocket [MFC], SendToEx
- CAsyncSocket [MFC], SetSockOpt
- CAsyncSocket [MFC], ShutDown
- CASyncSocket [MFC], Socket
- CAsyncSocket [MFC], OnAccept
- CAsyncSocket [MFC], OnClose
- CAsyncSocket [MFC], OnConnect
- CAsyncSocket [MFC], OnOutOfBandData
- CAsyncSocket [MFC], OnReceive
- CAsyncSocket [MFC], OnSend
- CAsyncSocket [MFC], m_hSocket
ms.assetid: cca4d5a1-aa0f-48bd-843e-ef0e2d7fc00b
ms.openlocfilehash: e384be534bdbb355554c28383e9e214e9084f217
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753028"
---
# <a name="casyncsocket-class"></a>CAsyncSocket 类

表示 Windows 套接字 - 网络通信的终结点。

## <a name="syntax"></a>语法

```
class CAsyncSocket : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[同步套接：：CAsyncSocket](#casyncsocket)|构造 `CAsyncSocket` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAsyncSocket：接受](#accept)|接受套接字上的连接。|
|[同步套接：：异步选择](#asyncselect)|请求套接字的事件通知。|
|[同步套接：：附加](#attach)|将套接字句柄附加到`CAsyncSocket`对象。|
|[CAsyncSocket：：绑定](#bind)|将本地地址与套接字关联。|
|[CAsyncSocket：关闭](#close)|关闭插座。|
|[CAsyncSocket：连接](#connect)|建立到对等套接字的连接。|
|[CAsyncSocket::Create](#create)|创建套接字。|
|[CAsyncSocket：:D](#detach)|从`CAsyncSocket`对象分离套接字句柄。|
|[CAsyncSocket：从手柄](#fromhandle)|返回指向`CAsyncSocket`对象的指针，给定套接字句柄。|
|[CAsyncSocket：：获取上次错误](#getlasterror)|获取上次失败操作的错误状态。|
|[CAsyncSocket：获取对等名称](#getpeername)|获取套接字连接到的对等套接字的地址。|
|[CAsyncSocket：获取对等名称Ex](#getpeernameex)|获取套接字连接到的对等套接字的地址（处理 IPv6 地址）。|
|[CAsyncSocket：获取索克名称](#getsockname)|获取套接字的本地名称。|
|[CAsyncSocket：：获取索诺克名称Ex](#getsocknameex)|获取套接字的本地名称（处理 IPv6 地址）。|
|[CAsyncSocket：getSockOpt](#getsockopt)|检索套接字选项。|
|[CAsyncSocket：：IOCtl](#ioctl)|控制套接字的模式。|
|[CAsyncSocket：听](#listen)|建立一个套接字以侦听传入连接请求。|
|[CAsyncSocket：接收](#receive)|从套接字接收数据。|
|[CAsyncSocket：接收来自](#receivefrom)|接收数据报并存储源地址。|
|[CAsyncSocket：：接收来自Ex](#receivefromex)|接收数据报并存储源地址（处理 IPv6 地址）。|
|[CAsyncSocket：发送](#send)|将数据发送到连接的套接字。|
|[同步套接：：发送至](#sendto)|将数据发送到特定目标。|
|[同步套接：：发送](#sendtoex)|将数据发送到特定目标（处理 IPv6 地址）。|
|[CAsyncSocket：setSockOpt](#setsockopt)|设置套接字选项。|
|[同步套接：：关闭](#shutdown)|禁用`Send`套接字上的`Receive`和/或呼叫。|
|[卡同步插槽：：套接字](#socket)|分配套接字句柄。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CAsyncSocket：：接受](#onaccept)|通知侦听套接字，它可以通过调用`Accept`来接受挂起的连接请求。|
|[同步套接：：关闭](#onclose)|通知连接到它的套接字已关闭。|
|[CAsyncSocket：打开连接](#onconnect)|通知连接套接字的连接尝试已完成，无论是成功还是错误。|
|[CAsyncsocket：：在带外数据上](#onoutofbanddata)|通知接收套接字在套接字上读取带外数据，通常是紧急消息。|
|[CAsyncSocket：打开接收](#onreceive)|通知侦听套接字，通过调用`Receive`来检索数据。|
|[CAsyncSocket：打开发送](#onsend)|通知套接字，它可以通过调用`Send`发送数据。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAsyncSocket：：运算符 |](#operator_eq)|为`CAsyncSocket`对象分配新值。|
|[CAsyncSocket：：操作员](#operator_socket)|使用此运算符检索`CAsyncSocket`对象的 SOCKET 句柄。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CAsyncSocket：m_hSocket](#m_hsocket)|指示附加到此`CAsyncSocket`对象的 SOCKET 句柄。|

## <a name="remarks"></a>备注

类`CAsyncSocket`封装 Windows 套接字函数 API，为希望与 MFC 结合使用 Windows 套接字的程序员提供面向对象的抽象。

此类基于您了解网络通信的假设。 您负责处理 Unicode 和多字节字符集 （MBCS） 字符串之间的阻塞、字节顺序差异和转换。 如果想要一个更方便的界面来为您管理这些问题，请参阅[类 CSocket](../../mfc/reference/csocket-class.md)。

要使用`CAsyncSocket`对象，请调用其构造函数，然后调用[Create](#create)函数以创建基础套接字句柄（`SOCKET`类型），但接受的套接字除外。 对于服务器套接字，调用[侦听](#listen)成员函数，对于客户端套接字，调用[Connect](#connect)成员函数。 服务器套接字应在收到连接请求时调用[Accept](#accept)函数。 使用其余`CAsyncSocket`功能在套接字之间执行通信。 完成后，`CAsyncSocket`如果对象是在堆上创建的，则销毁该对象;析构函数自动调用[Close](#close)函数。 在[Windows 套接字：背景](../../mfc/windows-sockets-background.md)） 一文中介绍了 SOCKET 数据类型。

> [!NOTE]
> 在静态链接的 MFC 应用程序中的辅助线程中使用 MFC 套接字时，您必须在使用套接字的每个线程中调用 `AfxSocketInit` 来初始化套接字库。 默认情况下，仅在主线程中调用 `AfxSocketInit`。

有关详细信息，请参阅[Windows 套接字：使用类 CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md)和相关文章，以及[Windows 套接字 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>要求

**标题：** afxsock.h

## <a name="casyncsocketaccept"></a><a name="accept"></a>CAsyncSocket：接受

调用此成员函数以接受套接字上的连接。

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>参数

*rConnectedSocket*<br/>
标识可用于连接的新套接字的引用。

*lpSockAddr*<br/>
指向[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的指针，该结构接收连接套接字的地址，在网络上已知。 *lpSockAddr*参数的确切格式由创建套接字时建立的地址族确定。 如果*lpSockAddr*和/或*lpSockAddrLen*等于 NULL，则不会返回有关接受套接字的远程地址的信息。

*lpSockAddrLen*<br/>
以*lpSockAddr（* 以字节为单位）指向地址长度的指针。 *lpSockAddrLen*是一个值结果参数：它最初应包含*lpSockAddr*指向的空间量;返回时，它将包含返回的地址的实际长度（以字节为单位）。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- wsAEFAULT *lpSockAddrLen*参数太小（小于[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的大小）。

- WSAEINPROGRESS 阻止 Windows 套接字调用正在进行中。

- 在接受之前未调用`Listen`WSAEINVAL。

- WSAEMFILE 队列在输入时为空，但不存在可用的描述符。

- WSAENOBUFS 没有可用的缓冲区空间。

- WSANotSOCK 描述符不是套接字。

- WSAEOPNOTSUPP 引用的套接字不是支持面向连接的服务的类型。

- WSAETOBLOCK 套接字标记为非阻塞，并且不存在要接受的连接。

### <a name="remarks"></a>备注

此例程提取挂起连接队列中的第一个连接，创建具有相同套接字属性的新套接字，并将其附加到*rConnectedSocket*。 如果队列中不存在挂起的连接，`Accept`则返回零并`GetLastError`返回错误。 接受的套接字 （ *rConnectedSocket）* 不能用于接受更多连接。 原始插座保持打开和侦听。

参数*lpSockAddr*是一个结果参数，该参数填充了连接套接字的地址，如通信层所知。 `Accept`用于基于连接的套接字类型，如SOCK_STREAM。

## <a name="casyncsocketasyncselect"></a><a name="asyncselect"></a>同步套接：：异步选择

调用此成员函数以请求套接字的事件通知。

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>参数

*lEvent*<br/>
指定应用程序感兴趣的网络事件的组合的位掩码。

- FD_READ希望收到准备阅读的通知。

- FD_WRITE希望在数据可供读取时收到通知。

- FD_OOB希望收到带外数据到达的通知。

- FD_ACCEPT希望接收传入连接的通知。

- FD_CONNECT希望收到连接结果的通知。

- FD_CLOSE希望当同字套字已由对等体关闭时接收通知。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEINVAL 指示其中一个指定的参数无效。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在进行中。

### <a name="remarks"></a>备注

此功能用于指定要为套接字调用哪些 MFC 回调通知函数。 `AsyncSelect`自动将此套接字设置为非阻塞模式。 有关详细信息，请参阅文章 Windows[套接字：套接字通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketattach"></a><a name="attach"></a>同步套接：：附加

调用此成员函数将*hSocket*句柄附加到`CAsyncSocket`对象。

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>参数

*hSocket*<br/>
包含套接字的句柄。

*lEvent*<br/>
指定应用程序感兴趣的网络事件的组合的位掩码。

- FD_READ希望收到准备阅读的通知。

- FD_WRITE希望在数据可供读取时收到通知。

- FD_OOB希望收到带外数据到达的通知。

- FD_ACCEPT希望接收传入连接的通知。

- FD_CONNECT希望收到连接结果的通知。

- FD_CLOSE希望当同字套字已由对等体关闭时接收通知。

### <a name="return-value"></a>返回值

如果函数运行成功，则为非零。

### <a name="remarks"></a>备注

SOCKET 句柄存储在对象的[m_hSocket](#m_hsocket)数据成员中。

## <a name="casyncsocketbind"></a><a name="bind"></a>CAsyncSocket：：绑定

调用此成员函数将本地地址与套接字相关联。

```
BOOL Bind(
    UINT nSocketPort,
    LPCTSTR lpszSocketAddress = NULL);

BOOL Bind (
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>参数

*nSocket端口*<br/>
标识套接字应用程序的端口。

*lpszSocket地址*<br/>
网络地址，虚数如"128.56.22.8"。 传递此参数的 NULL 字符串指示`CAsyncSocket`实例应侦听所有网络接口上的客户端活动。

*lpSockAddr*<br/>
指向[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的指针，其中包含要分配给此套接字的地址。

*恩索克·阿德尔伦*<br/>
以*lpSockAddr（* 以字节为单位）的地址长度。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 下面的列表涵盖了可能返回的一些错误。 有关完整列表，请参阅[Windows 套接字错误代码](/windows/win32/winsock/windows-sockets-error-codes-2)。

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEADDRINUSE 指定的地址已在使用中。 （请参阅[SetSockOpt](#setsockopt)下的SO_REUSEADDR套接字选项 。

- wsAEFAULT *nSockAddrLen*参数太小（小于[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的大小）。

- WSAEINPROGRESS 阻止 Windows 套接字调用正在进行中。

- 此端口不支持指定的地址族。

- WSAEINVAL 套接字已绑定到地址。

- WSAENOBUFS 没有足够的可用缓冲区，连接太多。

- WSANotSOCK 描述符不是套接字。

### <a name="remarks"></a>备注

此例程在后续`Connect`或`Listen`调用之前在未连接的数据报或流套接字上使用。 在接收连接请求之前，侦听服务器套接字必须选择端口号，并通过调用`Bind`来使其为 Windows 套接字。 `Bind`通过将本地名称分配给未命名的套接字，建立套接字的本地关联（主机地址/端口号）。

## <a name="casyncsocketcasyncsocket"></a><a name="casyncsocket"></a>同步套接：：CAsyncSocket

构造空白套接字对象。

```
CAsyncSocket();
```

### <a name="remarks"></a>备注

构造对象后，必须调用其成员`Create`函数以创建 SOCKET 数据结构并绑定其地址。 （在 Windows 套接字通信的服务器端，当侦听套接字创建要在`Accept`呼叫中使用的套接字时`Create`，您不会调用该套接字。

## <a name="casyncsocketclose"></a><a name="close"></a>CAsyncSocket：关闭

关闭插座。

```
virtual void Close();
```

### <a name="remarks"></a>备注

此函数释放套接字描述符，以便进一步引用它将失败与错误 WSANOTSOCK。 如果这是对基础套接字的最后一个引用，则将丢弃关联的命名信息和排队数据。 套接字对象的析构函数会`Close`为你调用。

对于`CAsyncSocket`，但不适用于`CSocket`，的`Close`语义受套接字选项SO_LINGER和SO_DONTLINGER。 有关详细信息，请参阅成员函数`GetSockOpt`。

## <a name="casyncsocketconnect"></a><a name="connect"></a>CAsyncSocket：连接

调用此成员函数以建立与未连接的流或数据报接字的连接。

```
BOOL Connect(
    LPCTSTR lpszHostAddress,
    UINT nHostPort);

BOOL Connect(
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>参数

*lpszHost 地址*<br/>
此对象连接到的套接字的网络地址：计算机名称（如"ftp.microsoft.com"）或虚线数字（如"128.56.22.8"）。

*nHostPort*<br/>
标识套接字应用程序的端口。

*lpSockAddr*<br/>
指向包含连接套接字地址的[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的指针。

*恩索克·阿德尔伦*<br/>
以*lpSockAddr（* 以字节为单位）的地址长度。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 如果这表示 WSAEWILLBLOCK 的错误代码，并且应用程序正在使用可重写的回调，则应用程序将在连接操作完成后收到消息`OnConnect`。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEADDRINUSE 指定的地址已在使用中。

- WSAEINPROGRESS 阻止 Windows 套接字调用正在进行中。

- WSAEADDRNOTA 指定地址不在本地计算机中。

- 指定族中的 WSAEAFNOSUPPORT 地址不能与此套接字一起使用。

- WSAECONN被拒绝连接尝试。

- 需要地址。

- wsAEFAULT *nSockAddrLen*参数不正确。

- WSAEINVAL 无效主机地址。

- WSAEISCONN 插座已连接。

- WSAEMFILE 没有更多的文件描述符可用。

- 此时无法从此主机到达网络。

- WSAENOBUFS 没有可用的缓冲区空间。 无法连接插座。

- WSANotSOCK 描述符不是套接字。

- WSATimeDOUT 尝试在不建立连接的情况下连接超时。

- WSAE到格，套接字被标记为非阻塞，连接无法立即完成。

### <a name="remarks"></a>备注

如果套接字未绑定，则系统将唯一值分配给本地关联，并且套接字标记为绑定。 请注意，如果名称结构的地址字段为全零，`Connect`则返回零。 要获取扩展的错误信息，`GetLastError`请调用成员函数。

对于流套接字（类型SOCK_STREAM），将启动到外接主机的活动连接。 当套接字调用成功完成时，套接字已准备好发送/接收数据。

对于数据图套接字（类型SOCK_DGRAM），将设置默认目标，该目标将用于后续`Send`和`Receive`调用。

## <a name="casyncsocketcreate"></a><a name="create"></a>CAsyncSocket：创建

构造套`Create`接字对象后调用成员函数以创建 Windows 套接字并附加它。

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>参数

*nSocket端口*<br/>
要与套接字一起使用的已知端口，如果希望 Windows 套接字选择端口，则为 0。

*nSocket 类型*<br/>
SOCK_STREAM或SOCK_DGRAM。

*lEvent*<br/>
指定应用程序感兴趣的网络事件的组合的位掩码。

- FD_READ希望收到准备阅读的通知。

- FD_WRITE希望收到准备写作的通知。

- FD_OOB希望收到带外数据到达的通知。

- FD_ACCEPT希望接收传入连接的通知。

- FD_CONNECT希望收到已完成连接的通知。

- FD_CLOSE希望收到套接字关闭通知。

*lpszSock 地址*<br/>
指向包含连接套接字的网络地址的字符串的指针，虚线数字，如"128.56.22.8"。传递此参数的 NULL 字符串指示`CAsyncSocket`实例应侦听所有网络接口上的客户端活动。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEAFNOSUPPORT 不支持指定的地址族。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在进行中。

- WSAEMFILE 没有更多的文件描述符可用。

- WSAENOBUFS 没有可用的缓冲区空间。 无法创建套接字。

- WSAEPROTONOSUPPORT 不支持指定的端口。

- WSAEPROTOTYPE 指定端口是此套接字的错误类型。

- WSAESOCKTNOSUPPORT 此地址系列中不支持指定的套接字类型。

### <a name="remarks"></a>备注

`Create`调用[套接字](#socket)，如果成功，它将调用[Bind](#bind)以绑定套接字到指定的地址。 支持以下套接字类型：

- SOCK_STREAM 提供序列化、可靠、全双工、基于连接的字节流。 对互联网地址系列使用传输控制协议 （TCP）。

- SOCK_DGRAM支持数据图，这是固定（通常较小）最大长度的无连接不可靠数据包。 对 Internet 地址系列使用用户数据报协议 （UDP）。

    > [!NOTE]
    >  成员`Accept`函数以引用新的空`CSocket`对象作为其参数。 在调用`Accept`之前，必须构造此对象。 请记住，如果此套接字对象超出范围，连接将关闭。 不要调用`Create`此新套接字对象。

> [!IMPORTANT]
> `Create`**不是**线程安全的。  如果在多线程环境中调用它，不同线程可以同时调用它，请确保使用互斥体或其他同步锁保护每个调用。

有关流和数据报套接字的详细信息，请参阅 Windows[套接字：后台](../../mfc/windows-sockets-background.md)和[Windows 套接字：端口和套接字地址和](../../mfc/windows-sockets-ports-and-socket-addresses.md) [Windows 套接字 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="casyncsocketdetach"></a><a name="detach"></a>CAsyncSocket：:D

调用此成员函数以将*m_hSocket*数据成员中的 SOCKET 句柄从对象`CAsyncSocket`中分离出来，并将*m_hSocket*设置为 NULL。

```
SOCKET Detach();
```

## <a name="casyncsocketfromhandle"></a><a name="fromhandle"></a>CAsyncSocket：从手柄

返回指向`CAsyncSocket`对象的指针。

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>参数

*hSocket*<br/>
包含套接字的句柄。

### <a name="return-value"></a>返回值

指向`CAsyncSocket`对象的指针，如果没有附加到`CAsyncSocket`*hSocket*的对象，则为 NULL。

### <a name="remarks"></a>备注

当给定一个 SOCKET 句柄`CAsyncSocket`时，如果对象未附加到句柄，则成员函数将返回 NULL。

## <a name="casyncsocketgetlasterror"></a><a name="getlasterror"></a>CAsyncSocket：：获取上次错误

调用此成员函数以获取上次失败操作的错误状态。

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>返回值

返回值指示此线程执行的最后一个 Windows 套接字 API 例程的错误代码。

### <a name="remarks"></a>备注

当特定成员函数指示已发生错误时，`GetLastError`应调用以检索相应的错误代码。 有关适用错误代码的列表，请参阅各个成员函数说明。

有关错误代码的详细信息，请参阅 Windows[套接字 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="casyncsocketgetpeername"></a><a name="getpeername"></a>CAsyncSocket：获取对等名称

调用此成员函数以获取此套接字所连接到的对等套接字的地址。

```
BOOL GetPeerName(
    CString& rPeerAddress,
    UINT& rPeerPort);

BOOL GetPeerName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>参数

*r 佩尔地址*<br/>
对接收虚`CString`线数 IP 地址的对象的引用。

*rPeerPort*<br/>
引用存储端口的 UINT。

*lpSockAddr*<br/>
指向接收对等套接字名称的[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的指针。

*lpSockAddrLen*<br/>
以*lpSockAddr（* 以字节为单位）指向地址长度的指针。 返回时 *，lpSockAddrLen*参数包含以字节为单位返回的*lpSockAddr*的实际大小。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEFAULT *lpSockAddrLen*参数不够大。

- WSAEINPROGRESS 阻止 Windows 套接字调用正在进行中。

- WSAENOTCONN 插座未连接。

- WSANotSOCK 描述符不是套接字。

### <a name="remarks"></a>备注

要处理 IPv6 地址，请使用[CAsyncSocket：：获取对等名称Ex](#getpeernameex)。

## <a name="casyncsocketgetpeernameex"></a><a name="getpeernameex"></a>CAsyncSocket：获取对等名称Ex

调用此成员函数获取此套接字连接到的对等套接字的地址（处理 IPv6 地址）。

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>参数

*r 佩尔地址*<br/>
对接收虚`CString`线数 IP 地址的对象的引用。

*rPeerPort*<br/>
引用存储端口的 UINT。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEFAULT *lpSockAddrLen*参数不够大。

- WSAEINPROGRESS 阻止 Windows 套接字调用正在进行中。

- WSAENOTCONN 插座未连接。

- WSANotSOCK 描述符不是套接字。

### <a name="remarks"></a>备注

此功能与[CAsyncSocket：getPeerName](#getpeername)相同，只不过它处理 IPv6 地址以及较旧的协议。

## <a name="casyncsocketgetsockname"></a><a name="getsockname"></a>CAsyncSocket：获取索克名称

调用此成员函数以获取套接字的本地名称。

```
BOOL GetSockName(
    CString& rSocketAddress,
    UINT& rSocketPort);

BOOL GetSockName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>参数

*rSocket地址*<br/>
对接收虚`CString`线数 IP 地址的对象的引用。

*rSocket端口*<br/>
引用存储端口的 UINT。

*lpSockAddr*<br/>
指向接收套接字地址的[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的指针。

*lpSockAddrLen*<br/>
以*lpSockAddr（* 以字节为单位）指向地址长度的指针。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEFAULT *lpSockAddrLen*参数不够大。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在进行中。

- WSANotSOCK 描述符不是套接字。

- WSAEINVAL 套接字未绑定到 带`Bind`的地址。

### <a name="remarks"></a>备注

此调用在未进行第一`Connect``Bind`次调用的情况下特别有用;此调用提供了确定系统已设置的本地关联的唯一方法。

要处理 IPv6 地址，请使用[CAsyncSocket：：getSockNameEx](#getsocknameex)

## <a name="casyncsocketgetsocknameex"></a><a name="getsocknameex"></a>CAsyncSocket：：获取索诺克名称Ex

调用此成员函数获取套接字的本地名称（处理 IPv6 地址）。

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>参数

*rSocket地址*<br/>
对接收虚`CString`线数 IP 地址的对象的引用。

*rSocket端口*<br/>
引用存储端口的 UINT。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEFAULT *lpSockAddrLen*参数不够大。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在进行中。

- WSANotSOCK 描述符不是套接字。

- WSAEINVAL 套接字未绑定到 带`Bind`的地址。

### <a name="remarks"></a>备注

此调用与[CAsyncSocket：getSockName](#getsockname)相同，只不过它处理 IPv6 地址以及较旧的协议。

此调用在未进行第一`Connect``Bind`次调用的情况下特别有用;此调用提供了确定系统已设置的本地关联的唯一方法。

## <a name="casyncsocketgetsockopt"></a><a name="getsockopt"></a>CAsyncSocket：getSockOpt

调用此成员函数以检索套接字选项。

```
BOOL GetSockOpt(
    int nOptionName,
    void* lpOptionValue,
    int* lpOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>参数

*nOption名称*<br/>
要为其检索值的套接字选项。

*lpOption值*<br/>
指向要返回所请求选项的值的缓冲区的指针。 与所选选项关联的值将返回缓冲区*lpOptionValue*。 *lpOptionLen*指向的整数最初应包含此缓冲区的大小（以字节为单位）;并在返回时，它将设置为返回的值的大小。 对于SO_LINGER，这将是一个`LINGER`结构的大小;对于所有其他选项，它将是 BOOL 或**int**的大小，具体取决于选项。 请参阅"备注"部分中的选项及其大小列表。

*lpOptionLen*<br/>
指向以字节为单位的*lpOptionValue*缓冲区大小的指针。

*n 级别*<br/>
定义选项的级别;唯一支持的级别是SOL_SOCKET和IPPROTO_TCP。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 如果从未使用`SetSockOpt`设置选项，则`GetSockOpt`返回该选项的默认值。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEFAULT *lpOptionlen*参数无效。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在进行中。

- WSAENOPROTOOPT 选项未知或不受支持。 特别是，SOCK_STREAM类型的套接字不支持SO_BROADCAST，而SOCK_DGRAM类型的套接字不支持SO_ACCEPTCONN、SO_DONTLINGER、SO_KEEPALIVE、SO_LINGER和SO_OOBINLINE。

- WSANotSOCK 描述符不是套接字。

### <a name="remarks"></a>备注

`GetSockOpt`检索与任何类型的套接字关联的套接字选项的当前值，并将结果存储在*lpOptionValue*中。 选项会影响套接字操作，例如数据包的路由、带外数据传输等。

支持 以下选项。 `GetSockOpt` 类型标识*lpOptionValue*寻址的数据类型。 TCP_NODELAY选项使用IPPROTO_TCP级别;所有其他选项使用级别SOL_SOCKET。

|“值”|类型|含义|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|插座正在侦听。|
|SO_BROADCAST|BOOL|套接字配置为传输广播消息。|
|SO_DEBUG|BOOL|已启用调试。|
|SO_DONTLINGER|BOOL|如果为 true，则禁用SO_LINGER选项。|
|SO_DONTROUTE|BOOL|路由已禁用。|
|SO_ERROR|**int**|检索错误状态并清除。|
|SO_KEEPALIVE|BOOL|正在发送保持生命。|
|SO_LINGER|`struct LINGER`|返回当前留日选项。|
|SO_OOBINLINE|BOOL|在正常数据流中接收带外数据。|
|SO_RCVBUF|int|接收的缓冲区大小。|
|SO_REUSEADDR|BOOL|套接字可以绑定到已在使用的地址。|
|SO_SNDBUF|**int**|发送的缓冲区大小。|
|SO_TYPE|**int**|套接字的类型（例如，SOCK_STREAM）。|
|TCP_NODELAY|BOOL|为发送合并禁用 Nagle 算法。|

伯克利软件分发 （BSD） 选项不支持`GetSockOpt`：

|“值”|类型|含义|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|接收低水位线。|
|SO_RCVTIMEO|**int**|接收超时。|
|SO_SNDLOWAT|**int**|发送低水位线。|
|SO_SNDTIMEO|**int**|发送超时。|
|IP_OPTIONS||获取 IP 标头中的选项。|
|TCP_MAXSEG|**int**|获取 TCP 最大段大小。|

使用`GetSockOpt`不支持的选项调用将导致从`GetLastError`返回 WSAENOPROTOOPT 的错误代码。

## <a name="casyncsocketioctl"></a><a name="ioctl"></a>CAsyncSocket：：IOCtl

调用此成员函数以控制套接字模式。

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>参数

*lCommand*<br/>
要对套接字执行的操作。

*lp参数*<br/>
指向*lCommand*的参数的指针。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEINVAL *lCommand*不是一个有效的命令，或者*lpArgument*不是*lCommand*的可接受参数，或者该命令不适用于提供的套接字类型。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在进行中。

- WSANotSOCK 描述符不是套接字。

### <a name="remarks"></a>备注

此例程可用于任何状态的任何套接字。 它用于获取或检索与套接字关联的操作参数，独立于协议和通信子系统。 支持以下命令：

- FIONBIO 启用或禁用插座上的非阻塞模式。 *lpArgument 参数*指向`DWORD`，如果启用非阻塞模式，则该参数为非零;如果要禁用该参数，则为零。 如果在`AsyncSelect`套接字上已发出，则任何尝试将`IOCtl`套接字设置为阻塞模式的尝试都将失败，而 WSAEINVAL 也会失败。 要将套接字设置为阻塞模式并防止 WSAEINVAL 错误，应用程序必须先通过调用`AsyncSelect``AsyncSelect` *lEvent*参数等于 0 来禁用，然后`IOCtl`调用 。

- FIONREAD 确定通过一个`Receive`调用从该套接字读取的最大字节数。 *lpArgument 参数*指向`IOCtl`存储结果`DWORD`的 。 如果此套接字的类型为SOCK_STREAM，FIONREAD 返回可在单个`Receive`中读取的数据总量;这通常与套接字上排队的数据总量相同。 如果此套接字的类型为 SOCK_DGRAM，FIONREAD 返回在套接字上排队的第一个数据报的大小。

- SIOCATMARK 确定是否已读取所有带外数据。 这仅适用于已配置为在线接收任何带外数据（SO_OOBINLINE）的类型SOCK_STREAM套接字。 如果没有等待读取带外数据，则操作将返回非零。 否则，它将返回 0，在下`Receive`一`ReceiveFrom`个或对套接字执行的数据将检索"标记"前面的部分或全部数据;否则，在套接字上执行的下一个或执行的数据将检索到 "标记"之前的部分或全部数据。应用程序应使用 SIOCATMARK 操作来确定是否存在任何数据。 如果"紧急"（带外）数据之前有任何正常数据，则按顺序接收。 （请注意，或`Receive``ReceiveFrom`永远不会在同一调用中混合带外数据和正常数据。*lpArgument 参数*指向`IOCtl`存储结果`DWORD`的 。

此函数是伯克利套接`ioctl()`字中使用的子集。 特别是，没有相当于FIOASYNC的命令，而SIOCATMARK是唯一支持的套接字级命令。

## <a name="casyncsocketlisten"></a><a name="listen"></a>CAsyncSocket：听

调用此成员函数以侦听传入连接请求。

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>参数

*n连接积压*<br/>
挂起连接队列可以增长到的最大长度。 有效范围为 1 到 5。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- 已尝试侦听正在使用的地址。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在进行中。

- WSAEINVAL 套接字尚未绑定`Bind`或已连接。

- WSAEISCONN 插座已连接。

- WSAEMFILE 没有更多的文件描述符可用。

- WSAENOBUFS 没有可用的缓冲区空间。

- WSANotSOCK 描述符不是套接字。

- WSAEOPNOTSUPP 引用的套接字不是支持该`Listen`操作的类型。

### <a name="remarks"></a>备注

要接受连接，首先使用`Create`创建套接字，使用`Listen`指定传入连接的积压工作，然后使用`Accept`接受连接。 `Listen`仅适用于支持连接的套接字，即SOCK_STREAM类型的套接字。 此套接字被置于"被动"模式，其中传入连接被确认并排队等待进程接受。

此函数通常由服务器（或任何想要接受连接的应用程序）使用，这些服务器（或任何应用程序）一次可能有多个连接请求：如果连接请求到达时队列已满，则客户端将收到一个错误，指示 WSAECONNREFUSED。

`Listen`尝试在没有可用端口（描述符）时继续合理运行。 它将接受连接，直到队列清空。 如果端口可用，则稍后调用`Listen`或`Accept`将队列重新填充到当前或最新的"积压"，如果可能，并继续侦听传入连接。

## <a name="casyncsocketm_hsocket"></a><a name="m_hsocket"></a>CAsyncSocket：m_hSocket

包含此`CAsyncSocket`对象封装的套接字的 SOCKET 句柄。

```
SOCKET m_hSocket;
```

## <a name="casyncsocketonaccept"></a><a name="onaccept"></a>CAsyncSocket：：接受

由框架调用以通知侦听套接字，它可以通过调用[Accept](#accept)成员函数来接受挂起的连接请求。

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>参数

*n错误代码*<br/>
套接字上的最新错误。 以下错误代码适用于`OnAccept`成员函数：

- **0**已成功执行函数。

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

### <a name="remarks"></a>备注

有关详细信息，请参阅[Windows 套接字：套接字通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketonclose"></a><a name="onclose"></a>同步套接：：关闭

由框架调用，以通知此套接字由其进程关闭连接的套接字。

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>参数

*n错误代码*<br/>
套接字上的最新错误。 以下错误代码适用于`OnClose`成员函数：

- **0**已成功执行函数。

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAECONNRESET 连接被远程端重置。

- WSAECONABORTED 由于超时或其他故障导致连接中止。

### <a name="remarks"></a>备注

有关详细信息，请参阅[Windows 套接字：套接字通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketonconnect"></a><a name="onconnect"></a>CAsyncSocket：打开连接

框架调用以通知此连接套接字，其连接尝试已完成，无论是成功还是错误。

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>参数

*n错误代码*<br/>
套接字上的最新错误。 以下错误代码适用于`OnConnect`成员函数：

- **0**已成功执行函数。

- WSAEADDRINUSE 指定的地址已在使用中。

- WSAEADDRNOTA 指定地址不在本地计算机中。

- 指定族中的 WSAEAFNOSUPPORT 地址不能与此套接字一起使用。

- WSAECONN一条连接尝试被强行拒绝。

- 需要地址。

- WSAEFAULT *lpSockAddrLen*参数不正确。

- WSAEINVAL 套接字已绑定到地址。

- WSAEISCONN 插座已连接。

- WSAEMFILE 没有更多的文件描述符可用。

- 此时无法从此主机到达网络。

- WSAENOBUFS 没有可用的缓冲区空间。 无法连接插座。

- WSAENOTCONN 插座未连接。

- WSAENOTSOCK 描述符是文件，而不是套接字。

- WSAETIMEDOUT 尝试连接超时而不建立连接。

### <a name="remarks"></a>备注

> [!NOTE]
> 在[CSocket](../../mfc/reference/csocket-class.md)`OnConnect`中，永远不会调用通知函数。 对于连接，只需调用`Connect`，连接完成后将返回（成功或错误）。 如何处理连接通知是 MFC 实现的详细信息。

有关详细信息，请参阅[Windows 套接字：套接字通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

## <a name="casyncsocketonoutofbanddata"></a><a name="onoutofbanddata"></a>CAsyncsocket：：在带外数据上

由框架调用以通知接收套接字发送套接字具有要发送的带外数据。

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>参数

*n错误代码*<br/>
套接字上的最新错误。 以下错误代码适用于`OnOutOfBandData`成员函数：

- **0**已成功执行函数。

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

### <a name="remarks"></a>备注

带外数据是一个逻辑上独立的通道，与SOCK_STREAM类型的每对连接的套接字相关联。 通道通常用于发送紧急数据。

MFC 支持带外数据，但禁止类`CAsyncSocket`用户使用它。 更简单的方法是创建第二个套接字以传递此类数据。 有关带外数据的详细信息，请参阅[Windows 套接字：套接字通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketonreceive"></a><a name="onreceive"></a>CAsyncSocket：打开接收

由框架调用以通知此套接字缓冲区中有可以通过调用`Receive`成员函数检索的数据。

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>参数

*n错误代码*<br/>
套接字上的最新错误。 以下错误代码适用于`OnReceive`成员函数：

- **0**已成功执行函数。

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

### <a name="remarks"></a>备注

有关详细信息，请参阅[Windows 套接字：套接字通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

## <a name="casyncsocketonsend"></a><a name="onsend"></a>CAsyncSocket：打开发送

由框架调用，以通知套接字，它现在可以通过调用`Send`成员函数发送数据。

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>参数

*n错误代码*<br/>
套接字上的最新错误。 以下错误代码适用于`OnSend`成员函数：

- **0**已成功执行函数。

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

### <a name="remarks"></a>备注

有关详细信息，请参阅[Windows 套接字：套接字通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

## <a name="casyncsocketoperator-"></a><a name="operator_eq"></a>CAsyncSocket：：运算符 |

为`CAsyncSocket`对象分配新值。

```cpp
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>参数

*rSrc*<br/>
对现有`CAsyncSocket`对象的引用。

### <a name="remarks"></a>备注

调用此函数以将现有`CAsyncSocket`对象复制到另一`CAsyncSocket`个对象。

## <a name="casyncsocketoperator-socket"></a><a name="operator_socket"></a>CAsyncSocket：：操作员

使用此运算符检索`CAsyncSocket`对象的 SOCKET 句柄。

```
operator SOCKET() const;
```

### <a name="return-value"></a>返回值

如果成功，则处理 SOCKET 对象的句柄;如果成功，则处理否则，NULL。

### <a name="remarks"></a>备注

您可以使用该句柄直接调用 Windows API。

## <a name="casyncsocketreceive"></a><a name="receive"></a>CAsyncSocket：接收

调用此成员函数从套接字接收数据。

```
virtual int Receive(
    void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
传入数据的缓冲区。

*恩布夫伦*<br/>
以字节为单位的*lpBuf*的长度。

*nFlags*<br/>
指定调用的方式。 此函数的语义由套接字选项和*nFlags*参数决定。 后者是通过将以下任一值与C++ **OR**运算符组合而成的：

- MSG_PEEK查看传入数据。 数据将复制到缓冲区中，但不会从输入队列中删除。

- MSG_OOB处理带外数据。

### <a name="return-value"></a>返回值

如果未发生错误，`Receive`则返回接收的字节数。 如果连接已关闭，则返回 0。 否则，将返回SOCKET_ERROR值，并且可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAENOTCONN 插座未连接。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在进行中。

- WSANotSOCK 描述符不是套接字。

- 已指定 WSAOpNOTSUPp MSG_OOB，但套接字不是类型SOCK_STREAM。

- WSAE关闭 插座已关闭;在使用*nHow* `Receive`设置为 0`ShutDown`或 2 调用后，无法调用套接字。

- WSAEANDBLOCK 套接字标记为非阻塞，`Receive`操作将阻塞。

- WSAEMSGSIZE 数据报太大，无法放入指定的缓冲区并被截断。

- WSAEINVAL 套接字未绑定使用`Bind`。

- WSAECONABORTED 虚拟电路由于超时或其他故障而中止。

- WSAECONNRESET 虚拟电路被远程端重置。

### <a name="remarks"></a>备注

此功能用于连接的流或数据报接字，用于读取传入数据。

对于SOCK_STREAM类型的套接字，返回截至提供的缓冲区大小的当前可用信息。 如果套接字已配置为在线接收带外数据（套接字选项SO_OOBINLINE），并且未读取带外数据，则仅返回带外数据。 应用程序可以使用`IOCtlSIOCATMARK`选项或[OnOutOfBandData](#onoutofbanddata)来确定是否还需要更多的带外数据读取。

对于 Datagram 套接字，将从第一个排队的数据报中提取数据，最多为提供的缓冲区大小。 如果数据报大于提供的缓冲区，则缓冲区将填充数据报的第一部分，多余的数据将丢失，并`Receive`返回一个值SOCKET_ERROR，错误代码设置为 WSAEMSGSIZE。 如果套接字上没有传入数据可用，则返回一个值SOCKET_ERROR，错误代码设置为 WSAETOBLOCK。 [OnReceive](#onreceive)回调功能可用于确定更多数据到达时间。

如果套接字的类型为SOCK_STREAM并且远程端已正常关闭连接，则将立即完成 0`Receive`字节。 如果连接已重置，则 a`Receive`将失败，错误为 WSAECONNRESET。

`Receive`每次[调用 CAsyncSocket 时](#onreceive)，应只调用一次：onReceive。

### <a name="example"></a>示例

  请参阅[CAsyncSocket 的示例：：打开接收](#onreceive)。

## <a name="casyncsocketreceivefrom"></a><a name="receivefrom"></a>CAsyncSocket：接收来自

调用此成员函数以接收数据报，并将源地址存储在[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构或*rSocket 地址*中。

```
int ReceiveFrom(
    void* lpBuf,
    int nBufLen,
    CString& rSocketAddress,
    UINT& rSocketPort,
    int nFlags = 0);

int ReceiveFrom(
    void* lpBuf,
    int nBufLen,
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen,
    int nFlags = 0);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
传入数据的缓冲区。

*恩布夫伦*<br/>
以字节为单位的*lpBuf*的长度。

*rSocket地址*<br/>
对接收虚`CString`线数 IP 地址的对象的引用。

*rSocket端口*<br/>
引用存储端口的 UINT。

*lpSockAddr*<br/>
指向[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的指针，该结构在返回时保存源地址。

*lpSockAddrLen*<br/>
指向*以 lpSockAddr*为单位的源地址长度的指针（以字节为单位）。

*nFlags*<br/>
指定调用的方式。 此函数的语义由套接字选项和*nFlags*参数决定。 后者是通过将以下任一值与C++ **OR**运算符组合而成的：

- MSG_PEEK查看传入数据。 数据将复制到缓冲区中，但不会从输入队列中删除。

- MSG_OOB处理带外数据。

### <a name="return-value"></a>返回值

如果未发生错误，`ReceiveFrom`则返回接收的字节数。 如果连接已关闭，则返回 0。 否则，将返回SOCKET_ERROR值，并且可以通过调用`GetLastError`检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEFAULT *lpSockAddrLen*参数无效 *：lpSockAddr*缓冲区太小，无法容纳对等地址。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在进行中。

- WSAEINVAL 套接字未绑定使用`Bind`。

- WSAENOTCONN 插座未连接（仅SOCK_STREAM）。

- WSANotSOCK 描述符不是套接字。

- 已指定 WSAOpNOTSUPp MSG_OOB，但套接字不是类型SOCK_STREAM。

- WSAE关闭 插座已关闭;在使用*nHow* `ReceiveFrom`设置为 0`ShutDown`或 2 调用后，无法调用套接字。

- WSAEANDBLOCK 套接字标记为非阻塞，`ReceiveFrom`操作将阻塞。

- WSAEMSGSIZE 数据报太大，无法放入指定的缓冲区并被截断。

- WSAECONABORTED 虚拟电路由于超时或其他故障而中止。

- WSAECONNRESET 虚拟电路被远程端重置。

### <a name="remarks"></a>备注

此功能用于读取（可能已连接的）套接字上的传入数据，并捕获从中发送数据的地址。

要处理 IPv6 地址，请使用[CAsyncSocket：：接收从前。](#receivefromex)

对于SOCK_STREAM类型的套接字，返回截至提供的缓冲区大小的当前可用信息。 如果套接字已配置为在线接收带外数据（套接字选项SO_OOBINLINE），并且未读取带外数据，则仅返回带外数据。 应用程序可以使用 该`IOCtlSIOCATMARK`选项或`OnOutOfBandData`确定是否还需要读取任何带外数据。 对于SOCK_STREAM套接字，将忽略*lpSockAddr*和*lpSockAddrLen*参数。

对于 Datagram 套接字，将从第一个排队的数据报中提取数据，最多为提供的缓冲区大小。 如果数据报大于提供的缓冲区，则缓冲区将填充消息的第一部分，多余的数据将丢失，并`ReceiveFrom`返回一个值 SOCKET_ERROR，错误代码设置为 WSAMSGSIZE。

如果*lpSockAddr*是非零，并且套接字的类型为SOCK_DGRAM，则发送数据的套接字的网络地址将复制到相应的[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构。 *lpSockAddrLen*指向的值初始化为此结构的大小，并在返回时修改以指示存储在那里的地址的实际大小。 如果套接字没有传入数据可用，`ReceiveFrom`则呼叫将等待数据到达，除非套接字未阻塞。 在这种情况下，将返回SOCKET_ERROR值，并将错误代码设置为 WSAETOBLOCK。 `OnReceive`回调可用于确定更多数据到达时间。

如果套接字的类型为SOCK_STREAM并且远程端已正常关闭连接，则将立即完成 0`ReceiveFrom`字节。

## <a name="casyncsocketreceivefromex"></a><a name="receivefromex"></a>CAsyncSocket：：接收来自Ex

调用此成员函数以接收数据报，并将源地址存储在[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构或*rSocket 地址*（句柄 IPv6 地址）中。

```
int ReceiveFromEx(
    void* lpBuf,
    int nBufLen,
    CString& rSocketAddress,
    UINT& rSocketPort,
    int nFlags = 0);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
传入数据的缓冲区。

*恩布夫伦*<br/>
以字节为单位的*lpBuf*的长度。

*rSocket地址*<br/>
对接收虚`CString`线数 IP 地址的对象的引用。

*rSocket端口*<br/>
引用存储端口的 UINT。

*nFlags*<br/>
指定调用的方式。 此函数的语义由套接字选项和*nFlags*参数决定。 后者是通过将以下任一值与C++ **OR**运算符组合而成的：

- MSG_PEEK查看传入数据。 数据将复制到缓冲区中，但不会从输入队列中删除。

- MSG_OOB处理带外数据。

### <a name="return-value"></a>返回值

如果未发生错误，`ReceiveFromEx`则返回接收的字节数。 如果连接已关闭，则返回 0。 否则，将返回SOCKET_ERROR值，并且可以通过调用`GetLastError`检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEFAULT *lpSockAddrLen*参数无效 *：lpSockAddr*缓冲区太小，无法容纳对等地址。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在进行中。

- WSAEINVAL 套接字未绑定使用`Bind`。

- WSAENOTCONN 插座未连接（仅SOCK_STREAM）。

- WSANotSOCK 描述符不是套接字。

- 已指定 WSAOpNOTSUPp MSG_OOB，但套接字不是类型SOCK_STREAM。

- WSAE关闭 插座已关闭;在使用*nHow* `ReceiveFromEx`设置为 0`ShutDown`或 2 调用后，无法调用套接字。

- WSAEANDBLOCK 套接字标记为非阻塞，`ReceiveFromEx`操作将阻塞。

- WSAEMSGSIZE 数据报太大，无法放入指定的缓冲区并被截断。

- WSAECONABORTED 虚拟电路由于超时或其他故障而中止。

- WSAECONNRESET 虚拟电路被远程端重置。

### <a name="remarks"></a>备注

此功能用于读取（可能已连接的）套接字上的传入数据，并捕获从中发送数据的地址。

此功能与[CAsyncSocket：ReceiveFrom](#receivefrom)相同，只不过它处理 IPv6 地址以及较旧的协议。

对于SOCK_STREAM类型的套接字，返回截至提供的缓冲区大小的当前可用信息。 如果套接字已配置为在线接收带外数据（套接字选项SO_OOBINLINE），并且未读取带外数据，则仅返回带外数据。 应用程序可以使用 该`IOCtlSIOCATMARK`选项或`OnOutOfBandData`确定是否还需要读取任何带外数据。 对于SOCK_STREAM套接字，将忽略*lpSockAddr*和*lpSockAddrLen*参数。

对于 Datagram 套接字，将从第一个排队的数据报中提取数据，最多为提供的缓冲区大小。 如果数据报大于提供的缓冲区，则缓冲区将填充消息的第一部分，多余的数据将丢失，并`ReceiveFromEx`返回一个值 SOCKET_ERROR，错误代码设置为 WSAMSGSIZE。

如果*lpSockAddr*是非零，并且套接字的类型为SOCK_DGRAM，则发送数据的套接字的网络地址将复制到相应的[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构。 *lpSockAddrLen*指向的值初始化为此结构的大小，并在返回时修改以指示存储在那里的地址的实际大小。 如果套接字没有传入数据可用，`ReceiveFromEx`则呼叫将等待数据到达，除非套接字未阻塞。 在这种情况下，将返回SOCKET_ERROR值，并将错误代码设置为 WSAETOBLOCK。 `OnReceive`回调可用于确定更多数据到达时间。

如果套接字的类型为SOCK_STREAM并且远程端已正常关闭连接，则将立即完成 0`ReceiveFromEx`字节。

## <a name="casyncsocketsend"></a><a name="send"></a>CAsyncSocket：发送

调用此成员函数以在连接的套接字上发送数据。

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
包含要传输的数据的缓冲区。

*恩布夫伦*<br/>
以*lpBuf（* 以字节为单位）的数据长度。

*nFlags*<br/>
指定调用的方式。 此函数的语义由套接字选项和*nFlags*参数决定。 后者是通过将以下任一值与C++ **OR**运算符组合而成的：

- MSG_DONTROUTE 指定数据不应受路由约束。 Windows 套接字供应商可以选择忽略此标志。

- MSG_OOB发送带外数据（仅限SOCK_STREAM）。

### <a name="return-value"></a>返回值

如果未发生错误，`Send`则返回发送的字符总数。 （请注意，这可能小于*nBufLen*指示的数字。否则，将返回SOCKET_ERROR值，并且可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEACCES 请求的地址是广播地址，但未设置相应的标志。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在进行中。

- WSAEFAULT *lpBuf*参数不在用户地址空间的有效部分。

- 必须重置连接，因为 Windows 套接字实现将其丢弃。

- WSAENOBUFS Windows 套接字实现报告缓冲区死锁。

- WSAENOTCONN 插座未连接。

- WSANotSOCK 描述符不是套接字。

- 已指定 WSAOpNOTSUPp MSG_OOB，但套接字不是类型SOCK_STREAM。

- WSAE关闭 插座已关闭;在使用*nHow* `Send`设置为 1`ShutDown`或 2 调用后，无法调用套接字。

- WSAEANDBLOCK 套接字标记为非阻塞，请求的操作将阻塞。

- WSAEMSGSIZE 套接字的类型为SOCK_DGRAM，并且数据报比 Windows 套接字实现支持的最大值要大。

- WSAEINVAL 套接字未绑定使用`Bind`。

- WSAECONABORTED 虚拟电路由于超时或其他故障而中止。

- WSAECONNRESET 虚拟电路被远程端重置。

### <a name="remarks"></a>备注

`Send`用于在连接的流或数据图套接字上写入传出数据。 对于 Datagram 套接字，必须小心不要超过基础子网的最大 IP 数据包大小，该大小由 返回`iMaxUdpDg``AfxSocketInit`的[WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)结构中的元素给出。 如果数据太长，无法通过基础协议以原子方式传递，则通过`GetLastError`返回错误 WSAEMSGSIZE，并且不会传输任何数据。

请注意，对于数据报套接字，成功完成`Send`的 并不表示数据已成功传递。

在`CAsyncSocket`SOCK_STREAM类型的对象上，写入的字节数可以介于 1 和请求的长度之间，具体取决于本地主机和外主机上的缓冲区可用性。

### <a name="example"></a>示例

  请参阅[CAsyncSocket 的示例：：打开。](#onsend)

## <a name="casyncsocketsendto"></a><a name="sendto"></a>同步套接：：发送至

调用此成员函数将数据发送到特定目标。

```
int SendTo(
    const void* lpBuf,
    int nBufLen,
    UINT nHostPort,
    LPCTSTR lpszHostAddress = NULL,
    int nFlags = 0);

int SendTo(
    const void* lpBuf,
    int nBufLen,
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen,
    int nFlags = 0);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
包含要传输的数据的缓冲区。

*恩布夫伦*<br/>
以*lpBuf（* 以字节为单位）的数据长度。

*nHostPort*<br/>
标识套接字应用程序的端口。

*lpszHost 地址*<br/>
此对象连接到的套接字的网络地址：计算机名称（如"ftp.microsoft.com"）或虚线数字（如"128.56.22.8"）。

*nFlags*<br/>
指定调用的方式。 此函数的语义由套接字选项和*nFlags*参数决定。 后者是通过将以下任一值与C++ **OR**运算符组合而成的：

- MSG_DONTROUTE 指定数据不应受路由约束。 Windows 套接字供应商可以选择忽略此标志。

- MSG_OOB发送带外数据（仅限SOCK_STREAM）。

*lpSockAddr*<br/>
指向包含目标套接字地址的[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的指针。

*恩索克·阿德尔伦*<br/>
以*lpSockAddr（* 以字节为单位）的地址长度。

### <a name="return-value"></a>返回值

如果未发生错误，`SendTo`则返回发送的字符总数。 （请注意，这可能小于*nBufLen*指示的数字。否则，将返回SOCKET_ERROR值，并且可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEACCES 请求的地址是广播地址，但未设置相应的标志。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在进行中。

- wsAEFAULT *lpBuf*或*lpSockAddr*参数不是用户地址空间的一部分，或者*lpSockAddr*参数太小（小于[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的大小）。

- WSAEINVAL 主机名无效。

- 必须重置连接，因为 Windows 套接字实现将其丢弃。

- WSAENOBUFS Windows 套接字实现报告缓冲区死锁。

- WSAENOTCONN 插座未连接（仅SOCK_STREAM）。

- WSANotSOCK 描述符不是套接字。

- 已指定 WSAOpNOTSUPp MSG_OOB，但套接字不是类型SOCK_STREAM。

- WSAE关闭 插座已关闭;在使用*nHow* `SendTo`设置为 1`ShutDown`或 2 调用后，无法调用套接字。

- WSAEANDBLOCK 套接字标记为非阻塞，请求的操作将阻塞。

- WSAEMSGSIZE 套接字的类型为SOCK_DGRAM，并且数据报比 Windows 套接字实现支持的最大值要大。

- WSAECONABORTED 虚拟电路由于超时或其他故障而中止。

- WSAECONNRESET 虚拟电路被远程端重置。

- WSAEADDRNOTA 指定地址不在本地计算机中。

- 指定族中的 WSAEAFNOSUPPORT 地址不能与此套接字一起使用。

- 需要地址。

- 此时无法从此主机到达网络。

### <a name="remarks"></a>备注

`SendTo`用于数据报或流套接字，用于在套接字上写入传出数据。 对于数据图套接字，必须注意不要超过基础子网的最大 IP 数据包大小，这是由[由 AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)填写的[WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)结构中`iMaxUdpDg`的元素给出的。 如果数据太长，无法通过基础协议以原子方式传递，则返回错误 WSAEMSGSIZE，并且不会传输任何数据。

请注意，成功完成 的`SendTo`并不表示数据已成功传递。

`SendTo`仅用于SOCK_DGRAM套接字，将数据报发送到*lpSockAddr*参数标识的特定套接字。

要发送广播（仅在SOCK_DGRAM），应使用特殊 IP 地址INADDR_BROADCAST（在 Windows 套接字头文件 WINSOCK 中定义）构造*lpSockAddr*参数中的地址。H） 连同预期的端口号。 或者，如果*lpszHost地址*参数为 NULL，则配置套接字用于广播。 通常不建议广播数据报超过发生碎片的大小，这意味着数据报（不包括标头）的数据部分不应超过 512 字节。

要处理 IPv6 地址，请使用[CAsyncSocket：：SendToEx](#sendtoex)。

## <a name="casyncsocketsendtoex"></a><a name="sendtoex"></a>同步套接：：发送

调用此成员函数将数据发送到特定目标（处理 IPv6 地址）。

```
int SendToEx(
    const void* lpBuf,
    int nBufLen,
    UINT nHostPort,
    LPCTSTR lpszHostAddress = NULL,
    int nFlags = 0);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
包含要传输的数据的缓冲区。

*恩布夫伦*<br/>
以*lpBuf（* 以字节为单位）的数据长度。

*nHostPort*<br/>
标识套接字应用程序的端口。

*lpszHost 地址*<br/>
此对象连接到的套接字的网络地址：计算机名称（如"ftp.microsoft.com"）或虚线数字（如"128.56.22.8"）。

*nFlags*<br/>
指定调用的方式。 此函数的语义由套接字选项和*nFlags*参数决定。 后者是通过将以下任一值与C++ **OR**运算符组合而成的：

- MSG_DONTROUTE 指定数据不应受路由约束。 Windows 套接字供应商可以选择忽略此标志。

- MSG_OOB发送带外数据（仅限SOCK_STREAM）。

### <a name="return-value"></a>返回值

如果未发生错误，`SendToEx`则返回发送的字符总数。 （请注意，这可能小于*nBufLen*指示的数字。否则，将返回SOCKET_ERROR值，并且可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEACCES 请求的地址是广播地址，但未设置相应的标志。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在进行中。

- wsAEFAULT *lpBuf*或*lpSockAddr*参数不是用户地址空间的一部分，或者*lpSockAddr*参数太小（小于[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的大小）。

- WSAEINVAL 主机名无效。

- 必须重置连接，因为 Windows 套接字实现将其丢弃。

- WSAENOBUFS Windows 套接字实现报告缓冲区死锁。

- WSAENOTCONN 插座未连接（仅SOCK_STREAM）。

- WSANotSOCK 描述符不是套接字。

- 已指定 WSAOpNOTSUPp MSG_OOB，但套接字不是类型SOCK_STREAM。

- WSAE关闭 插座已关闭;在使用*nHow* `SendToEx`设置为 1`ShutDown`或 2 调用后，无法调用套接字。

- WSAEANDBLOCK 套接字标记为非阻塞，请求的操作将阻塞。

- WSAEMSGSIZE 套接字的类型为SOCK_DGRAM，并且数据报比 Windows 套接字实现支持的最大值要大。

- WSAECONABORTED 虚拟电路由于超时或其他故障而中止。

- WSAECONNRESET 虚拟电路被远程端重置。

- WSAEADDRNOTA 指定地址不在本地计算机中。

- 指定族中的 WSAEAFNOSUPPORT 地址不能与此套接字一起使用。

- 需要地址。

- 此时无法从此主机到达网络。

### <a name="remarks"></a>备注

此方法与[CAsyncSocket：：SendTo](#sendto)相同，只不过它处理 IPv6 地址以及较旧的协议。

`SendToEx`用于数据报或流套接字，用于在套接字上写入传出数据。 对于数据图套接字，必须注意不要超过基础子网的最大 IP 数据包大小，这是由[由 AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)填写的[WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)结构中`iMaxUdpDg`的元素给出的。 如果数据太长，无法通过基础协议以原子方式传递，则返回错误 WSAEMSGSIZE，并且不会传输任何数据。

请注意，成功完成 的`SendToEx`并不表示数据已成功传递。

`SendToEx`仅用于SOCK_DGRAM套接字，将数据报发送到*lpSockAddr*参数标识的特定套接字。

要发送广播（仅在SOCK_DGRAM），应使用特殊 IP 地址INADDR_BROADCAST（在 Windows 套接字头文件 WINSOCK 中定义）构造*lpSockAddr*参数中的地址。H） 连同预期的端口号。 或者，如果*lpszHost地址*参数为 NULL，则配置套接字用于广播。 通常不建议广播数据报超过发生碎片的大小，这意味着数据报（不包括标头）的数据部分不应超过 512 字节。

## <a name="casyncsocketsetsockopt"></a><a name="setsockopt"></a>CAsyncSocket：setSockOpt

调用此成员函数以设置套接字选项。

```
BOOL SetSockOpt(
    int nOptionName,
    const void* lpOptionValue,
    int nOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>参数

*nOption名称*<br/>
要为其设置值的套接字选项。

*lpOption值*<br/>
指向提供所请求选项的值的缓冲区的指针。

*nOptionLen*<br/>
*lpOptionValue*缓冲区的大小（以字节为单位）。

*n 级别*<br/>
定义选项的级别;唯一支持的级别是SOL_SOCKET和IPPROTO_TCP。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEFAULT *lpOptionValue*不在进程地址空间的有效部分。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在进行中。

- WSAEINVAL *nLevel*无效，或者*lpOptionValue*中的信息无效。

- 设置SO_KEEPALIVE时，WSAENETRESET 连接已超时。

- WSAENOPROTOOPT 选项未知或不受支持。 特别是，SOCK_STREAM类型的套接字不支持SO_BROADCAST，而SOCK_DGRAM类型的套接字不支持SO_DONTLINGER、SO_KEEPALIVE、SO_LINGER和SO_OOBINLINE。

- 设置SO_KEEPALIVE时，已重置 WSANOTCONN 连接。

- WSANotSOCK 描述符不是套接字。

### <a name="remarks"></a>备注

`SetSockOpt`设置与任何类型、任何类型的套接字关联的套接字选项的当前值。 尽管选项可以存在于多个协议级别，但此规范仅定义存在于最上层"套接字"级别的选项。 选项会影响套接字操作，例如在正常数据流中是否接收加急数据、是否可以在套接字上发送广播消息等。

有两种类型的套接字选项：启用或禁用特征或行为的布尔选项，以及需要整数值或结构的选项。 要启用布尔选项 *，lpOptionValue*指向非零整数。 要禁用选项*lpOptionValue，* 请指向等于零的整数。 *nOptionLen*应等于`sizeof(BOOL)`布尔选项。 对于其他选项 *，lpOptionValue*指向包含该选项所需值的整数或结构 *，nOptionLen*是整数或结构的长度。

SO_LINGER控制在套接字上排队时执行的操作，`Close`并且调用函数关闭套接字。

默认情况下，无法将套接字绑定（请参阅[绑定](#bind)） 绑定到已在使用的本地地址。 但是，有时最好以这种方式"重用"地址。 由于每个连接都由本地地址和远程地址的组合唯一标识，因此只要远程地址不同，将两个套接字绑定到同一本地地址是没有问题的。

要通知 Windows 套接字实现`Bind`，不应禁止对套接字进行调用，因为其他套接字已在使用所需的地址，应用程序应在发出`Bind`呼叫之前为套接字设置SO_REUSEADDR套接字选项。 请注意，该选项仅在`Bind`调用时进行解释：因此，没有必要（但无害）在未绑定到现有地址的套接字上设置该选项，并在`Bind`调用后设置或重置该选项对此或任何其他套接字没有影响。

应用程序可以通过打开SO_KEEPALIVE套接字选项请求 Windows 套接字实现启用传输控制协议 （TCP） 连接上的"保持活动"数据包。 Windows 套接字实现不需要支持使用保持-生命：如果是，则精确的语义是特定于实现的，但应符合 RFC 1122 的第 4.2.3.6 节："Internet 主机的要求 - 通信层"。 如果由于"保持"而断开连接，错误代码 WSAENETRESET 将返回到套接字上正在进行的任何调用，并且任何后续调用都将在 WSAENOTCONN 中失败。

TCP_NODELAY选项禁用 Nagle 算法。 Nagle 算法用于通过缓冲未确认的发送数据，直到发送全尺寸数据包来减少主机发送的小数据包数。 但是，对于某些应用程序，此算法可能会妨碍性能，并且TCP_NODELAY可用于将其关闭。 应用程序编写器不应设置TCP_NODELAY除非对这样做的影响是广为人知和想要的，因为设置TCP_NODELAY会对网络性能产生重大的负面影响。 TCP_NODELAY是唯一受支持的套接字选项，它使用级别IPPROTO_TCP;所有其他选项使用级别SOL_SOCKET。

如果SO_DEBUG选项由应用程序设置，则 Windows 套接字的某些实现提供输出调试信息。

支持 以下选项。 `SetSockOpt` 类型标识*lpOptionValue*寻址的数据类型。

|“值”|类型|含义|
|-----------|----------|-------------|
|SO_BROADCAST|BOOL|允许在套接字上传输广播消息。|
|SO_DEBUG|BOOL|记录调试信息。|
|SO_DONTLINGER|BOOL|不要阻止`Close`等待发送未发送的数据。 设置此选项等效于将SO_LINGER`l_onoff`设置为零。|
|SO_DONTROUTE|BOOL|不要路由：直接发送到接口。|
|SO_KEEPALIVE|BOOL|发送保持生命。|
|SO_LINGER|`struct LINGER`|`Close`如果存在未发送的数据。|
|SO_OOBINLINE|BOOL|在正常数据流中接收带外数据。|
|SO_RCVBUF|**int**|指定接收的缓冲区大小。|
|SO_REUSEADDR|BOOL|允许将套接字绑定到已使用的地址。 （请参阅[绑定](#bind)。）|
|SO_SNDBUF|**int**|为发送指定缓冲区大小。|
|TCP_NODELAY|BOOL|为发送合并禁用 Nagle 算法。|

伯克利软件分发 （BSD） 选项不支持`SetSockOpt`：

|“值”|类型|含义|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|套接字正在侦听|
|SO_ERROR|**int**|获取错误状态并清除。|
|SO_RCVLOWAT|**int**|接收低水位线。|
|SO_RCVTIMEO|**int**|接收超时|
|SO_SNDLOWAT|**int**|发送低水位线。|
|SO_SNDTIMEO|**int**|发送超时。|
|SO_TYPE|**int**|套接字的类型。|
|IP_OPTIONS||在 IP 标头中设置选项字段。|

## <a name="casyncsocketshutdown"></a><a name="shutdown"></a>同步套接：：关闭

调用此成员函数以禁用套接字上的发送、接收或两者。

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>参数

*n 如何*<br/>
使用以下枚举值描述不再允许的操作类型的标志：

- **接收 = 0**

- **发送 = 1**

- **两者 = 2**

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- 在使用此 API 之前，必须成功进行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字实现检测到网络子系统失败。

- WSAEINVAL *nHow*无效。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在进行中。

- WSAENOTCONN 插座未连接（仅SOCK_STREAM）。

- WSANotSOCK 描述符不是套接字。

### <a name="remarks"></a>备注

`ShutDown`用于所有类型的插座，以禁用接收、传输或两者。 如果*nHow*为 0，则不允许在套接字上后续接收。 这对下级协议层没有影响。

对于传输控制协议 （TCP），TCP 窗口不会更改，在窗口用尽之前将接受（但未确认）传入数据。 对于用户数据图协议 （UDP），接受传入的图和排队。 在任何情况下，也不会生成 ICMP 错误数据包。 如果*nHow*是 1，则不允许后续发送。 对于 TCP 套接字，将发送 FIN。 按照上述方式将 nHow 设置为 *"2"* 将禁用发送和接收。

请注意，`ShutDown`不会关闭套接字，并且在调用之前`Close`不会释放附加到套接字的资源。 应用程序不应依赖于在关闭套接字后能够重用它。 特别是，不需要 Windows 套接字实现来支持在此类套接字`Connect`上使用。

### <a name="example"></a>示例

  请参阅[CAsyncSocket 的示例：：打开接收](#onreceive)。

## <a name="casyncsocketsocket"></a><a name="socket"></a>卡同步插槽：：套接字

分配套接字句柄。

```
BOOL Socket(
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    int nProtocolType = 0,
    int nAddressFormat = PF_INET);
```

### <a name="parameters"></a>参数

*nSocket 类型*<br/>
指定`SOCK_STREAM``SOCK_DGRAM`或 。

*lEvent*<br/>
指定应用程序感兴趣的网络事件组合的位掩码。

- `FD_READ`：要收到准备阅读的通知。

- `FD_WRITE`：要收到准备写作的通知。

- `FD_OOB`：要接收带外数据到达的通知。

- `FD_ACCEPT`：要接收传入连接的通知。

- `FD_CONNECT`：要接收已完成连接的通知。

- `FD_CLOSE`：要接收套接字关闭通知。

*n协议类型*<br/>
与特定于指示的地址族的套接字一起使用的协议。

*n地址格式*<br/>
地址系列规范。

### <a name="return-value"></a>返回值

成功时返回 `TRUE`，失败时返回 `FALSE`。

### <a name="remarks"></a>备注

此方法分配套接字句柄。 它不调用[CAsyncSocket：：绑定](#bind)以将套接字绑定到指定的地址，因此您需要稍后调用`Bind`以将套接字绑定到指定的地址。 您可以使用[CAsyncSocket：setSockOpt](#setsockopt)在绑定之前设置套接字选项。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CSocket 类](../../mfc/reference/csocket-class.md)<br/>
[套接字文件类](../../mfc/reference/csocketfile-class.md)
