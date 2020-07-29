---
title: CAsyncSocket 类
ms.date: 06/25/2020
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
ms.openlocfilehash: 95d24c9fb9e432a54705a6b8f9fa7638affad2d2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195091"
---
# <a name="casyncsocket-class"></a>CAsyncSocket 类

表示 Windows 套接字，即网络通信终结点。

## <a name="syntax"></a>语法

```
class CAsyncSocket : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAsyncSocket：： CAsyncSocket](#casyncsocket)|构造 `CAsyncSocket` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CAsyncSocket：： Accept](#accept)|接受套接字上的连接。|
|[CAsyncSocket：： AsyncSelect](#asyncselect)|请求套接字的事件通知。|
|[CAsyncSocket：： Attach](#attach)|将套接字句柄附加到 `CAsyncSocket` 对象。|
|[CAsyncSocket：： Bind](#bind)|将本地地址与套接字关联。|
|[CAsyncSocket：： Close](#close)|关闭套接字。|
|[CAsyncSocket：： Connect](#connect)|建立与对等套接字的连接。|
|[CAsyncSocket::Create](#create)|创建套接字。|
|[CAsyncSocket：： CreateEx](#createex)|使用高级选项创建套接字。|
|[CAsyncSocket：:D etach](#detach)|从对象分离套接字句柄 `CAsyncSocket` 。|
|[CAsyncSocket：： FromHandle](#fromhandle)|`CAsyncSocket`给定套接字句柄，返回指向对象的指针。|
|[CAsyncSocket：： GetLastError](#getlasterror)|获取上次失败的操作的错误状态。|
|[CAsyncSocket：： GetPeerName](#getpeername)|获取套接字连接到的对等套接字的地址。|
|[CAsyncSocket：： GetPeerNameEx](#getpeernameex)|获取套接字连接到的对等套接字的地址（处理 IPv6 地址）。|
|[CAsyncSocket：： GetSockName](#getsockname)|获取套接字的本地名称。|
|[CAsyncSocket：： GetSockNameEx](#getsocknameex)|获取套接字的本地名称（处理 IPv6 地址）。|
|[CAsyncSocket：： GetSockOpt](#getsockopt)|检索套接字选项。|
|[CAsyncSocket：： IOCtl](#ioctl)|控制套接字的模式。|
|[CAsyncSocket：：侦听](#listen)|建立用于侦听传入连接请求的套接字。|
|[CAsyncSocket：： Receive](#receive)|从套接字接收数据。|
|[CAsyncSocket：： ReceiveFrom](#receivefrom)|接收数据报并存储源地址。|
|[CAsyncSocket：： ReceiveFromEx](#receivefromex)|接收数据报并存储源地址（处理 IPv6 地址）。|
|[CAsyncSocket：： Send](#send)|将数据发送到连接的套接字。|
|[CAsyncSocket：： SendTo](#sendto)|向特定目标发送数据。|
|[CAsyncSocket：： SendToEx](#sendtoex)|将数据发送到特定目标（处理 IPv6 地址）。|
|[CAsyncSocket：： SetSockOpt](#setsockopt)|设置套接字选项。|
|[CAsyncSocket：： ShutDown](#shutdown)|`Send` `Receive` 在套接字上禁用和/或调用。|
|[CASyncSocket：：套接字](#socket)|分配套接字句柄。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CAsyncSocket：： OnAccept](#onaccept)|通知侦听套接字它可以通过调用来接受挂起的连接请求 `Accept` 。|
|[CAsyncSocket：： OnClose](#onclose)|通知套接字连接到它的套接字已关闭。|
|[CAsyncSocket：： OnConnect](#onconnect)|通知连接套接字连接尝试已完成（无论是成功还是错误）。|
|[CAsyncSocket：： OnOutOfBandData](#onoutofbanddata)|通知接收套接字存在要在套接字上读取的带外数据，通常为紧急消息。|
|[CAsyncSocket：： OnReceive](#onreceive)|通知侦听套接字有要通过调用检索的数据 `Receive` 。|
|[CAsyncSocket：： OnSend](#onsend)|通知套接字它可以通过调用发送数据 `Send` 。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CAsyncSocket：： operator =](#operator_eq)|将新值分配给 `CAsyncSocket` 对象。|
|[CAsyncSocket：： operator 套接字](#operator_socket)|使用此运算符检索对象的套接字句柄 `CAsyncSocket` 。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CAsyncSocket：： m_hSocket](#m_hsocket)|指示附加到此对象的套接字句柄 `CAsyncSocket` 。|

## <a name="remarks"></a>备注

类 `CAsyncSocket` 封装 Windows 套接字函数 API，为想要结合使用 Windows 套接字的程序员提供面向对象的抽象。

此类基于你了解网络通信的假设。 您负责处理阻止、字节顺序差异以及 Unicode 和多字节字符集（MBCS）字符串之间的转换。 如果需要更方便的界面来管理这些问题，请参阅类[CSocket](../../mfc/reference/csocket-class.md)。

若要使用 `CAsyncSocket` 对象，请调用其构造函数，然后调用[create](#create)函数以创建基础套接字句柄（类型 `SOCKET` ），但接受的套接字除外。 对于服务器套接字，调用[侦听](#listen)成员函数; 对于客户端套接字，调用[Connect](#connect)成员函数。 服务器套接字应在收到连接请求时调用[Accept](#accept)函数。 使用剩余的 `CAsyncSocket` 函数来执行套接字间的通信。 完成后， `CAsyncSocket` 如果对象是在堆上创建的，则销毁对象; 析构函数会自动调用[Close](#close)函数。 套接字数据类型在[Windows 套接： Background](../../mfc/windows-sockets-background.md)一文中进行了介绍。

> [!NOTE]
> 在静态链接的 MFC 应用程序中的辅助线程中使用 MFC 套接字时，您必须在使用套接字的每个线程中调用 `AfxSocketInit` 来初始化套接字库。 默认情况下，仅在主线程中调用 `AfxSocketInit`。

有关详细信息，请参阅[Windows 套接字：使用类 CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md)和相关文章，以及[WINDOWS socket 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>要求

**标头：** afxsock

## <a name="casyncsocketaccept"></a><a name="accept"></a>CAsyncSocket：： Accept

调用此成员函数以接受套接字上的连接。

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>参数

*rConnectedSocket*<br/>
一个引用，用于标识可用于连接的新套接字。

*lpSockAddr*<br/>
指向[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的指针，该结构接收连接套接字的地址（在网络上是已知的）。 *LpSockAddr*参数的准确格式由创建套接字时建立的地址族决定。 如果*lpSockAddr*和/或*lpSockAddrLen*等于 NULL，则不会返回有关已接受的套接字的远程地址的任何信息。

*lpSockAddrLen*<br/>
一个指针，指向*lpSockAddr*中地址的长度（以字节为单位）。 *LpSockAddrLen*是一个值-result 参数：它最初应该包含*lpSockAddr*指向的空间量;返回时，将包含返回的地址的实际长度（以字节为单位）。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEFAULT *lpSockAddrLen*参数太小（小于[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的大小）。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字调用。

- `Listen`接受之前未调用 WSAEINVAL。

- WSAEMFILE 当条目为 "接受" 时，队列为空，并且没有可用的描述符。

- WSAENOBUFS 无缓冲区空间可用。

- WSAENOTSOCK 描述符不是套接字。

- WSAEOPNOTSUPP 引用的套接字不是支持面向连接的服务的类型。

- WSAEWOULDBLOCK 套接字标记为非阻止，不存在要接受的连接。

### <a name="remarks"></a>备注

此例程提取挂起连接的队列中的第一个连接，创建具有与此套接字相同的属性的新套接字，并将其附加到*rConnectedSocket*。 如果队列中没有挂起的连接，则 `Accept` 返回零并 `GetLastError` 返回错误。 接受的套接字（ *rConnectedSocket）* 不能用于接受更多连接。 原始套接字保持打开和侦听。

参数*lpSockAddr*是一个结果参数，该参数使用连接套接字的地址进行填充，与通信层已知。 `Accept`用于基于连接的套接字类型，如 SOCK_STREAM。

## <a name="casyncsocketasyncselect"></a><a name="asyncselect"></a>CAsyncSocket：： AsyncSelect

调用此成员函数以请求套接字的事件通知。

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>参数

*lEvent*<br/>
一个位掩码，指定应用程序感兴趣的网络事件的组合。

- FD_READ 想要接收有关读取准备情况的通知。

- FD_WRITE 想要在数据可供读取时接收通知。

- FD_OOB 希望接收带外数据到达的通知。

- FD_ACCEPT 想要接收传入连接的通知。

- FD_CONNECT 想要接收连接结果的通知。

- FD_CLOSE 希望在对等方关闭套接字时接收通知。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEINVAL 指示指定的参数之一无效。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字操作。

### <a name="remarks"></a>备注

此函数用于指定将为套接字调用哪些 MFC 回调通知函数。 `AsyncSelect`自动将此套接字设置为非阻止模式。 有关详细信息，请参阅[Windows 套接字：套接字通知](../../mfc/windows-sockets-socket-notifications.md)一文。

## <a name="casyncsocketattach"></a><a name="attach"></a>CAsyncSocket：： Attach

调用此成员函数以将*hSocket*句柄附加到 `CAsyncSocket` 对象。

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>参数

*hSocket*<br/>
包含套接字的句柄。

*lEvent*<br/>
一个位掩码，指定应用程序感兴趣的网络事件的组合。

- FD_READ 想要接收有关读取准备情况的通知。

- FD_WRITE 想要在数据可供读取时接收通知。

- FD_OOB 希望接收带外数据到达的通知。

- FD_ACCEPT 想要接收传入连接的通知。

- FD_CONNECT 想要接收连接结果的通知。

- FD_CLOSE 希望在对等方关闭套接字时接收通知。

### <a name="return-value"></a>返回值

如果函数运行成功，则为非零。

### <a name="remarks"></a>备注

套接字句柄存储在对象的[m_hSocket](#m_hsocket)数据成员中。

## <a name="casyncsocketbind"></a><a name="bind"></a>CAsyncSocket：： Bind

调用此成员函数以将本地地址与套接字关联。

```
BOOL Bind(
    UINT nSocketPort,
    LPCTSTR lpszSocketAddress = NULL);

BOOL Bind (
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>参数

*nSocketPort*<br/>
标识套接字应用程序的端口。

*lpszSocketAddress*<br/>
网络地址，一种点号，如 "128.56.22.8"。 如果为此参数传递 NULL 字符串，则指示该 `CAsyncSocket` 实例应侦听所有网络接口上的客户端活动。

*lpSockAddr*<br/>
指向[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的指针，该结构包含要分配给此套接字的地址。

*nSockAddrLen*<br/>
*LpSockAddr*中地址的长度（以字节为单位）。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 下面的列表介绍了可能返回的一些错误。 有关完整列表，请参阅[Windows 套接字错误代码](/windows/win32/winsock/windows-sockets-error-codes-2)。

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEADDRINUSE 指定的地址已被使用。 （请参阅[SetSockOpt](#setsockopt)下的 SO_REUSEADDR 套接字选项。）

- WSAEFAULT *nSockAddrLen*参数太小（小于[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的大小）。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字调用。

- WSAEAFNOSUPPORT 此端口不支持指定的地址族。

- WSAEINVAL 套接字已绑定到地址。

- WSAENOBUFS 可用缓冲区不足，连接太多。

- WSAENOTSOCK 描述符不是套接字。

### <a name="remarks"></a>备注

在后续或调用之前，此例程用于未连接的数据报或流套接字 `Connect` `Listen` 。 在接受连接请求之前，侦听服务器套接字必须选择端口号，并通过调用使其对 Windows 套接字是已知的 `Bind` 。 `Bind`通过向未命名套接字分配本地名称，建立套接字的本地关联（主机地址/端口号）。

## <a name="casyncsocketcasyncsocket"></a><a name="casyncsocket"></a>CAsyncSocket：： CAsyncSocket

构造空套接对象。

```
CAsyncSocket();
```

### <a name="remarks"></a>备注

构造对象之后，必须调用其 `Create` 成员函数来创建套接字数据结构并绑定其地址。 （在 Windows 套接字通信的服务器端，当侦听套接字创建要在调用中使用的套接字时， `Accept` 不会调用 `Create` 该套接字。）

## <a name="casyncsocketclose"></a><a name="close"></a>CAsyncSocket：： Close

关闭套接字。

```
virtual void Close();
```

### <a name="remarks"></a>备注

此函数将释放套接字描述符，以便进一步引用它将失败，并出现错误 WSAENOTSOCK。 如果这是对基础套接字的最后一个引用，则将丢弃关联的命名信息和排队数据。 套接字对象的析构函数 `Close` 会为您调用。

对于 `CAsyncSocket` ，但不适用于 `CSocket` ， `Close` SO_LINGER 和 SO_DONTLINGER 的套接字选项会影响的语义。 有关详细信息，请参阅成员函数 `GetSockOpt` 。

## <a name="casyncsocketconnect"></a><a name="connect"></a>CAsyncSocket：： Connect

调用此成员函数以建立与未连接的流或数据报套接字的连接。

```
BOOL Connect(
    LPCTSTR lpszHostAddress,
    UINT nHostPort);

BOOL Connect(
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>参数

*lpszHostAddress*<br/>
此对象连接的套接字的网络地址：计算机名（例如 "ftp.microsoft.com"）或点分数字，如 "128.56.22.8"。

*nHostPort*<br/>
标识套接字应用程序的端口。

*lpSockAddr*<br/>
指向[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的指针，该结构包含连接的套接字的地址。

*nSockAddrLen*<br/>
*LpSockAddr*中地址的长度（以字节为单位）。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 如果这指示 WSAEWOULDBLOCK 的错误代码，并且你的应用程序使用可重写的回调， `OnConnect` 则当连接操作完成时，你的应用程序将收到一条消息。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEADDRINUSE 指定的地址已被使用。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字调用。

- WSAEADDRNOTAVAIL 指定的地址在本地计算机上不可用。

- 指定系列中的 WSAEAFNOSUPPORT 地址不能用于此套接字。

- WSAECONNREFUSED 尝试连接被拒绝。

- WSAEDESTADDRREQ 目标地址是必需的。

- WSAEFAULT *nSockAddrLen*参数不正确。

- WSAEINVAL 无效的主机地址。

- WSAEISCONN 套接字已连接。

- WSAEMFILE 没有更多可用的文件描述符。

- WSAENETUNREACH 无法从此主机访问网络。

- WSAENOBUFS 无缓冲区空间可用。 无法连接套接字。

- WSAENOTSOCK 描述符不是套接字。

- 在未建立连接的情况下，WSAETIMEDOUT 尝试连接超时。

- WSAEWOULDBLOCK 套接字标记为非阻止，连接无法立即完成。

### <a name="remarks"></a>备注

如果套接字是未绑定的，则系统会将唯一值分配给本地关联，并将套接字标记为绑定。 请注意，如果名称结构的 address 字段均为零，则 `Connect` 将返回零。 若要获取扩展的错误信息，请调用 `GetLastError` 成员函数。

对于 stream socket （类型 SOCK_STREAM），活动连接将启动到外部主机。 当套接字调用成功完成时，套接字就可以发送/接收数据。

对于数据报套接字（类型 SOCK_DGRAM），将设置默认目标，将在后续 `Send` 和调用中使用 `Receive` 。

## <a name="casyncsocketcreate"></a><a name="create"></a>CAsyncSocket：： Create

`Create`构造套接字对象之后调用成员函数以创建 Windows 套接字并附加它。

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>参数

*nSocketPort*<br/>
要与套接字一起使用的已知端口，或者如果希望 Windows 套接字选择端口，则为0。

*nSocketType*<br/>
SOCK_STREAM 或 SOCK_DGRAM。

*lEvent*<br/>
一个位掩码，指定应用程序感兴趣的网络事件的组合。

- FD_READ 想要接收有关读取准备情况的通知。

- FD_WRITE 想要接收有关写入准备情况的通知。

- FD_OOB 希望接收带外数据到达的通知。

- FD_ACCEPT 想要接收传入连接的通知。

- FD_CONNECT 想要接收已完成连接的通知。

- FD_CLOSE 想要接收套接字关闭通知。

*lpszSockAddress*<br/>
指向字符串的指针，该字符串包含连接的套接字的网络地址，如 "128.56.22.8"。如果为此参数传递 NULL 字符串，则指示该 `CAsyncSocket` 实例应侦听所有网络接口上的客户端活动。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEAFNOSUPPORT 不支持指定的地址族。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字操作。

- WSAEMFILE 没有更多可用的文件描述符。

- WSAENOBUFS 无缓冲区空间可用。 无法创建套接字。

- WSAEPROTONOSUPPORT 不支持指定的端口。

- WSAEPROTOTYPE 为此套接字指定的端口类型错误。

- WSAESOCKTNOSUPPORT 此地址系列不支持指定的套接字类型。

### <a name="remarks"></a>备注

`Create`调用[套接字](#socket)，如果成功，它将调用[bind](#bind)将套接字绑定到指定的地址。 支持以下套接字类型：

- SOCK_STREAM 提供经过序列化的、可靠且基于连接的双字节流。 为 Internet 地址系列使用传输控制协议（TCP）。

- SOCK_DGRAM 支持数据报，该数据报为固定的（通常为小）最大长度的无连接和不可靠的数据包。 对 Internet 地址系列使用用户数据报协议（UDP）。

    > [!NOTE]
    >  `Accept`成员函数使用新的空 `CSocket` 对象作为其参数。 在调用之前，必须构造此对象 `Accept` 。 请记住，如果此套接字对象超出范围，则连接将关闭。 不要 `Create` 为此新的套接字对象调用。

> [!IMPORTANT]
> `Create`**不**是线程安全的。  如果要在多线程环境中调用它，而该环境可以由不同的线程同时调用，请确保使用 mutex 或其他同步锁来保护每个调用。

有关流和数据报套接字的详细信息，请参阅文章[Windows socket：背景](../../mfc/windows-sockets-background.md)和[windows 套接字：端口和套接字地址](../../mfc/windows-sockets-ports-and-socket-addresses.md)和[windows 套接字 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="casyncsocketcreateex"></a><a name="createex"></a>CAsyncSocket：： CreateEx

`CreateEx`构造套接字对象之后调用成员函数以创建 Windows 套接字并附加它。

需要提供高级选项（如套接字类型）时，请使用此函数。

```
BOOL CreateEx(
    ADDRINFOT* pAI,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>参数

*pAI*<br/>
指向[ADDRINFOT](https://docs.microsoft.com/windows/win32/api/ws2def/ns-ws2def-addrinfoa)的指针，用于保存套接字信息，如系列和套接字类型。

*lEvent*<br/>
一个位掩码，指定应用程序感兴趣的网络事件的组合。

- FD_READ 想要接收有关读取准备情况的通知。

- FD_WRITE 想要接收有关写入准备情况的通知。

- FD_OOB 希望接收带外数据到达的通知。

- FD_ACCEPT 想要接收传入连接的通知。

- FD_CONNECT 想要接收已完成连接的通知。

- FD_CLOSE 想要接收套接字关闭通知。

### <a name="return-value"></a>返回值

请参阅[Create （）](#return-value-5)的返回值。

### <a name="remarks"></a>备注

请参阅[Create （）](#remarks-8)的备注。

## <a name="casyncsocketdetach"></a><a name="detach"></a>CAsyncSocket：:D etach

调用此成员函数以从对象中分离*m_hSocket*数据成员的套接字句柄 `CAsyncSocket` ，并将*m_hSocket*设置为 NULL。

```
SOCKET Detach();
```

## <a name="casyncsocketfromhandle"></a><a name="fromhandle"></a>CAsyncSocket：： FromHandle

返回一个指向对象的指针 `CAsyncSocket` 。

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>参数

*hSocket*<br/>
包含套接字的句柄。

### <a name="return-value"></a>返回值

指向对象的指针 `CAsyncSocket` ; 如果没有 `CAsyncSocket` 连接到*hSocket*的对象，则为 NULL。

### <a name="remarks"></a>备注

给定套接字句柄时，如果 `CAsyncSocket` 对象未附加到句柄，成员函数将返回 NULL。

## <a name="casyncsocketgetlasterror"></a><a name="getlasterror"></a>CAsyncSocket：： GetLastError

调用此成员函数以获取上次失败的操作的错误状态。

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>返回值

返回值指示此线程执行的最后一个 Windows 套接字 API 例程的错误代码。

### <a name="remarks"></a>备注

当特定成员函数指示发生了错误时， `GetLastError` 应调用来检索相应的错误代码。 有关适用的错误代码的列表，请参阅单个成员函数说明。

有关错误代码的详细信息，请参阅[Windows 套接字 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="casyncsocketgetpeername"></a><a name="getpeername"></a>CAsyncSocket：： GetPeerName

调用此成员函数以获取此套接字连接到的对等套接字的地址。

```
BOOL GetPeerName(
    CString& rPeerAddress,
    UINT& rPeerPort);

BOOL GetPeerName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>参数

*rPeerAddress*<br/>
对 `CString` 接收点分数字 IP 地址的对象的引用。

*rPeerPort*<br/>
引用存储端口的 UINT。

*lpSockAddr*<br/>
指向[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的指针，该结构接收对等套接字的名称。

*lpSockAddrLen*<br/>
一个指针，指向*lpSockAddr*中地址的长度（以字节为单位）。 返回时， *lpSockAddrLen*参数包含返回的*lpSockAddr*的实际大小（以字节为单位）。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEFAULT *lpSockAddrLen*参数不够大。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字调用。

- WSAENOTCONN 套接字未连接。

- WSAENOTSOCK 描述符不是套接字。

### <a name="remarks"></a>备注

若要处理 IPv6 地址，请使用[CAsyncSocket：： GetPeerNameEx](#getpeernameex)。

## <a name="casyncsocketgetpeernameex"></a><a name="getpeernameex"></a>CAsyncSocket：： GetPeerNameEx

调用此成员函数以获取此套接字连接到的对等套接字的地址（处理 IPv6 地址）。

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>参数

*rPeerAddress*<br/>
对 `CString` 接收点分数字 IP 地址的对象的引用。

*rPeerPort*<br/>
引用存储端口的 UINT。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEFAULT *lpSockAddrLen*参数不够大。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字调用。

- WSAENOTCONN 套接字未连接。

- WSAENOTSOCK 描述符不是套接字。

### <a name="remarks"></a>备注

此函数与[CAsyncSocket：： GetPeerName](#getpeername)相同，不同之处在于它处理 IPv6 地址和旧协议。

## <a name="casyncsocketgetsockname"></a><a name="getsockname"></a>CAsyncSocket：： GetSockName

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

*rSocketAddress*<br/>
对 `CString` 接收点分数字 IP 地址的对象的引用。

*rSocketPort*<br/>
引用存储端口的 UINT。

*lpSockAddr*<br/>
指向[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的指针，该结构接收套接字地址。

*lpSockAddrLen*<br/>
一个指针，指向*lpSockAddr*中地址的长度（以字节为单位）。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEFAULT *lpSockAddrLen*参数不够大。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字操作。

- WSAENOTSOCK 描述符不是套接字。

- WSAEINVAL 套接字尚未绑定到地址 `Bind` 。

### <a name="remarks"></a>备注

如果未执行此操作，则此调用会特别有用 `Connect` `Bind` ; 此调用提供的唯一方法是确定系统已设置的本地关联。

若要处理 IPv6 地址，请使用[CAsyncSocket：： GetSockNameEx](#getsocknameex)

## <a name="casyncsocketgetsocknameex"></a><a name="getsocknameex"></a>CAsyncSocket：： GetSockNameEx

调用此成员函数以获取套接字的本地名称（处理 IPv6 地址）。

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>参数

*rSocketAddress*<br/>
对 `CString` 接收点分数字 IP 地址的对象的引用。

*rSocketPort*<br/>
引用存储端口的 UINT。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEFAULT *lpSockAddrLen*参数不够大。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字操作。

- WSAENOTSOCK 描述符不是套接字。

- WSAEINVAL 套接字尚未绑定到地址 `Bind` 。

### <a name="remarks"></a>备注

此调用与[CAsyncSocket：： GetSockName](#getsockname)相同，不同之处在于它处理 IPv6 地址和旧协议。

如果未执行此操作，则此调用会特别有用 `Connect` `Bind` ; 此调用提供的唯一方法是确定系统已设置的本地关联。

## <a name="casyncsocketgetsockopt"></a><a name="getsockopt"></a>CAsyncSocket：： GetSockOpt

调用此成员函数以检索套接字选项。

```
BOOL GetSockOpt(
    int nOptionName,
    void* lpOptionValue,
    int* lpOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>参数

*nOptionName*<br/>
要为其检索值的套接字选项。

*lpOptionValue*<br/>
指向缓冲区的指针，请求的选项的值将返回到该缓冲区。 与所选选项关联的值将在缓冲区*lpOptionValue*中返回。 *LpOptionLen*所指向的整数应最初包含此缓冲区的大小（以字节为单位）;返回时，它将被设置为返回的值的大小。 对于 SO_LINGER，这将是结构的大小 `LINGER` ; 对于所有其他选项，它将是布尔值或的大小 **`int`** ，具体取决于选项。 请参阅 "备注" 部分中的选项列表及其大小。

*lpOptionLen*<br/>
一个指针，指向*lpOptionValue*缓冲区的大小（以字节为单位）。

*nLevel*<br/>
定义选项的级别;仅 SOL_SOCKET 和 IPPROTO_TCP 支持的级别。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 如果某个选项从未设置为 `SetSockOpt` ，则 `GetSockOpt` 返回该选项的默认值。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEFAULT *lpOptionLen*参数无效。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字操作。

- WSAENOPROTOOPT 选项未知或不受支持。 具体而言，SO_BROADCAST 在类型 SOCK_STREAM 的套接字上不受支持，而 SO_ACCEPTCONN、SO_DONTLINGER、SO_KEEPALIVE、SO_LINGER 和 SO_OOBINLINE 在类型 SOCK_DGRAM 的插槽上不受支持。

- WSAENOTSOCK 描述符不是套接字。

### <a name="remarks"></a>备注

`GetSockOpt`检索与任意类型的任何类型的套接字关联的套接字选项的当前值，并将结果存储在*lpOptionValue*中。 选项会影响套接字操作，例如路由数据包、带外数据传输等。

支持以下选项 `GetSockOpt` 。 类型标识*lpOptionValue*寻址的数据类型。 TCP_NODELAY 选项使用 level IPPROTO_TCP;所有其他选项都使用 level SOL_SOCKET。

|值|类型|含义|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|套接字正在侦听。|
|SO_BROADCAST|BOOL|套接字配置为传输广播消息。|
|SO_DEBUG|BOOL|启用调试。|
|SO_DONTLINGER|BOOL|如果为 true，则禁用 SO_LINGER 选项。|
|SO_DONTROUTE|BOOL|已禁用路由。|
|SO_ERROR|**`int`**|检索错误状态并清除。|
|SO_KEEPALIVE|BOOL|正在发送 keep-alive。|
|SO_LINGER|`struct LINGER`|返回当前逗留选项。|
|SO_OOBINLINE|BOOL|正在正常数据流中接收带外数据。|
|SO_RCVBUF|int|接收的缓冲区大小。|
|SO_REUSEADDR|BOOL|可以将套接字绑定到已在使用中的地址。|
|SO_SNDBUF|**`int`**|发送的缓冲区大小。|
|SO_TYPE|**`int`**|套接字的类型（例如，SOCK_STREAM）。|
|TCP_NODELAY|BOOL|为发送合并禁用 Nagle 算法。|

不支持的 Berkeley 软件分发（BSD）选项 `GetSockOpt` 包括：

|值|类型|含义|
|-----------|----------|-------------|
|SO_RCVLOWAT|**`int`**|接收低水位线。|
|SO_RCVTIMEO|**`int`**|接收超时。|
|SO_SNDLOWAT|**`int`**|发送低水位线。|
|SO_SNDTIMEO|**`int`**|发送超时。|
|IP_OPTIONS||获取 IP 标头中的选项。|
|TCP_MAXSEG|**`int`**|获取 TCP 最大段大小。|

`GetSockOpt`使用不受支持的选项调用将导致从返回错误代码 WSAENOPROTOOPT `GetLastError` 。

## <a name="casyncsocketioctl"></a><a name="ioctl"></a>CAsyncSocket：： IOCtl

调用此成员函数来控制套接字的模式。

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>参数

*lCommand*<br/>
要在套接字上执行的命令。

*lpArgument*<br/>
指向*lCommand*的参数的指针。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEINVAL *lCommand*不是有效的命令，或者*lpArgument*不是适用于*lCommand*的可接受参数，或者该命令不适用于提供的套接字类型。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字操作。

- WSAENOTSOCK 描述符不是套接字。

### <a name="remarks"></a>备注

此例程可用于任何状态的任何套接字。 它用于获取或检索与套接字关联的操作参数，与协议和通信子系统无关。 支持以下命令：

- FIONBIO 启用或禁用套接字上的非阻止模式。 *LpArgument*参数指向 `DWORD` ，如果要启用非阻止模式，则为非零值，如果要禁用则为零。 如果已 `AsyncSelect` 在套接字上发出，则尝试使用将 `IOCtl` 套接字设置回阻止模式的任何尝试都将失败，并出现 WSAEINVAL。 若要将套接字设置回阻止模式并防止 WSAEINVAL 错误，应用程序必须首先 `AsyncSelect` 通过 `AsyncSelect` 将*lEvent*参数设置为0来进行调用，然后调用 `IOCtl` 。

- FIONREAD 确定通过此套接字的一次调用可以读取的最大字节数 `Receive` 。 *LpArgument*参数指向 `DWORD` `IOCtl` 存储结果的。 如果此套接字的类型为 SOCK_STREAM，则 FIONREAD 返回可在单个中读取的数据总量 `Receive` ; 这通常与套接字上排队的数据总量相同。 如果此套接字的类型为 SOCK_DGRAM，则 FIONREAD 将返回在套接字上排队的第一个数据报的大小。

- SIOCATMARK 确定是否已读取所有带外数据。 这仅适用于类型 SOCK_STREAM 的套接字，该套接字已配置为可在任何带外数据的内联接收（SO_OOBINLINE）。 如果没有带外数据正在等待读取，则操作将返回非零值。 否则，它将返回0，然后，在 `Receive` `ReceiveFrom` 套接字上执行的下一个或执行的操作将检索某些或所有数据，然后应用程序应使用 SIOCATMARK 操作来确定是否保留任何数据。 如果 "紧急" （带外）数据之前有任何常规数据，则会按顺序接收数据。 （请注意， `Receive` 或 `ReceiveFrom` 决不会在同一调用中混合带外和普通数据。）*LpArgument*参数指向 `DWORD` `IOCtl` 存储结果的。

此函数是 `ioctl()` Berkeley 套接字中使用的的子集。 具体而言，不会有与 FIOASYNC 等效的命令，而 SIOCATMARK 是唯一受支持的套接字级别命令。

## <a name="casyncsocketlisten"></a><a name="listen"></a>CAsyncSocket：：侦听

调用此成员函数以侦听传入连接请求。

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>参数

*nConnectionBacklog*<br/>
挂起连接的队列可以增长到的最大长度。 有效范围是从1到5。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEADDRINUSE 尝试侦听正在使用的地址。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字操作。

- WSAEINVAL 套接字尚未与绑定， `Bind` 或已连接。

- WSAEISCONN 套接字已连接。

- WSAEMFILE 没有更多可用的文件描述符。

- WSAENOBUFS 无缓冲区空间可用。

- WSAENOTSOCK 描述符不是套接字。

- WSAEOPNOTSUPP 引用的套接字不属于支持操作的类型 `Listen` 。

### <a name="remarks"></a>备注

为了接受连接，首先使用创建套接字，使用为 `Create` 传入连接指定积压工作（backlog）， `Listen` 然后使用接受连接 `Accept` 。 `Listen`仅适用于支持连接的套接字，即 SOCK_STREAM 类型。 此套接字将置于 "被动" 模式，在该模式下，传入的连接被确认并排队等待进程接受。

此函数通常由服务器（或任何需要接受连接的应用程序）用于一次可以有多个连接请求：如果连接请求到达队列已满，则客户端将收到错误，指示 WSAECONNREFUSED。

`Listen`如果没有可用的端口（描述符），则尝试继续运行 rationally。 在清空队列之前，它将接受连接。 如果端口变为可用，稍后对或的 `Listen` 调用 `Accept` 会将队列重新填充到当前或最新的 "积压工作（backlog）"，并继续侦听传入连接。

## <a name="casyncsocketm_hsocket"></a><a name="m_hsocket"></a>CAsyncSocket：： m_hSocket

包含此对象封装的套接字的套接字句柄 `CAsyncSocket` 。

```
SOCKET m_hSocket;
```

## <a name="casyncsocketonaccept"></a><a name="onaccept"></a>CAsyncSocket：： OnAccept

由框架调用，以通知侦听套接字它可以通过调用[accept](#accept)成员函数接受挂起的连接请求。

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>参数

*nErrorCode*<br/>
套接字上的最新错误。 以下错误代码适用于 `OnAccept` 成员函数：

- **0**已成功执行该函数。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

### <a name="remarks"></a>备注

有关详细信息，请参阅[Windows 套接字：套接字通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketonclose"></a><a name="onclose"></a>CAsyncSocket：： OnClose

由框架调用以通知此套接字，连接的套接字已由其进程关闭。

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>参数

*nErrorCode*<br/>
套接字上的最新错误。 以下错误代码适用于 `OnClose` 成员函数：

- **0**已成功执行该函数。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAECONNRESET 连接被远程端重置。

- WSAECONNABORTED 由于超时或其他故障，连接已中止。

### <a name="remarks"></a>备注

有关详细信息，请参阅[Windows 套接字：套接字通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketonconnect"></a><a name="onconnect"></a>CAsyncSocket：： OnConnect

由框架调用，用于通知此连接套接字其连接尝试已完成（无论是成功还是错误）。

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>参数

*nErrorCode*<br/>
套接字上的最新错误。 以下错误代码适用于 `OnConnect` 成员函数：

- **0**已成功执行该函数。

- WSAEADDRINUSE 指定的地址已被使用。

- WSAEADDRNOTAVAIL 指定的地址在本地计算机上不可用。

- 指定系列中的 WSAEAFNOSUPPORT 地址不能用于此套接字。

- WSAECONNREFUSED 尝试连接被强制拒绝。

- WSAEDESTADDRREQ 目标地址是必需的。

- WSAEFAULT *lpSockAddrLen*参数不正确。

- WSAEINVAL 套接字已绑定到地址。

- WSAEISCONN 套接字已连接。

- WSAEMFILE 没有更多可用的文件描述符。

- WSAENETUNREACH 无法从此主机访问网络。

- WSAENOBUFS 无缓冲区空间可用。 无法连接套接字。

- WSAENOTCONN 套接字未连接。

- WSAENOTSOCK 描述符是一个文件，而不是套接字。

- WSAETIMEDOUT 在未建立连接的情况下尝试连接超时。

### <a name="remarks"></a>备注

> [!NOTE]
> 在[CSocket](../../mfc/reference/csocket-class.md)中， `OnConnect` 从不调用通知函数。 对于连接，只需调用 `Connect` ，当连接完成（成功或错误）时，将返回。 如何处理连接通知是 MFC 实现的详细信息。

有关详细信息，请参阅[Windows 套接字：套接字通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

## <a name="casyncsocketonoutofbanddata"></a><a name="onoutofbanddata"></a>CAsyncSocket：： OnOutOfBandData

由框架调用，以通知接收套接字发送套接字具有要发送的带外数据。

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>参数

*nErrorCode*<br/>
套接字上的最新错误。 以下错误代码适用于 `OnOutOfBandData` 成员函数：

- **0**已成功执行该函数。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

### <a name="remarks"></a>备注

带外数据是一个逻辑上独立的通道，与 SOCK_STREAM 类型的每对连接套接字相关联。 通道通常用于发送紧急数据。

MFC 支持带外数据，但不建议使用类的用户 `CAsyncSocket` 。 更简单的方法是创建另一个套接字用于传递此类数据。 有关带外数据的详细信息，请参阅[Windows 套接字：套接字通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketonreceive"></a><a name="onreceive"></a>CAsyncSocket：： OnReceive

由框架调用，以通知此套接字存在缓冲区中的数据，可通过调用成员函数来检索这些数据 `Receive` 。

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>参数

*nErrorCode*<br/>
套接字上的最新错误。 以下错误代码适用于 `OnReceive` 成员函数：

- **0**已成功执行该函数。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

### <a name="remarks"></a>备注

有关详细信息，请参阅[Windows 套接字：套接字通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

## <a name="casyncsocketonsend"></a><a name="onsend"></a>CAsyncSocket：： OnSend

由框架调用，以通知套接字现在可以通过调用 `Send` 成员函数发送数据。

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>参数

*nErrorCode*<br/>
套接字上的最新错误。 以下错误代码适用于 `OnSend` 成员函数：

- **0**已成功执行该函数。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

### <a name="remarks"></a>备注

有关详细信息，请参阅[Windows 套接字：套接字通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

## <a name="casyncsocketoperator-"></a><a name="operator_eq"></a>CAsyncSocket：： operator =

将新值分配给 `CAsyncSocket` 对象。

```cpp
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>参数

*.Rsrc*<br/>
对现有对象的引用 `CAsyncSocket` 。

### <a name="remarks"></a>备注

调用此函数可将现有 `CAsyncSocket` 对象复制到另一个 `CAsyncSocket` 对象。

## <a name="casyncsocketoperator-socket"></a><a name="operator_socket"></a>CAsyncSocket：： operator 套接字

使用此运算符检索对象的套接字句柄 `CAsyncSocket` 。

```
operator SOCKET() const;
```

### <a name="return-value"></a>返回值

如果成功，则为套接字对象的句柄;否则为 NULL。

### <a name="remarks"></a>备注

您可以使用句柄直接调用 Windows Api。

## <a name="casyncsocketreceive"></a><a name="receive"></a>CAsyncSocket：： Receive

调用此成员函数以从套接字接收数据。

```
virtual int Receive(
    void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
传入数据的缓冲区。

*nBufLen*<br/>
*LpBuf*的长度（以字节为单位）。

*nFlags*<br/>
指定进行调用的方式。 此函数的语义由套接字选项和*nFlags*参数确定。 后者通过将以下任意值与 c + +**或**运算符组合起来来构造：

- MSG_PEEK 查看传入数据。 数据将复制到缓冲区中，但不会从输入队列中删除。

- MSG_OOB 处理带外数据。

### <a name="return-value"></a>返回值

如果未发生错误，则 `Receive` 返回已接收的字节数。 如果连接已关闭，则返回0。 否则，将返回值 SOCKET_ERROR，并通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAENOTCONN 套接字未连接。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字操作。

- WSAENOTSOCK 描述符不是套接字。

- 已指定 WSAEOPNOTSUPP MSG_OOB，但套接字的类型不是 SOCK_STREAM。

- WSAESHUTDOWN 套接字已关闭;`Receive` `ShutDown` 调用*nHow*设置为0或2后，不能对套接字调用。

- WSAEWOULDBLOCK 套接字标记为非阻塞， `Receive` 操作会阻止。

- WSAEMSGSIZE 数据报太大，无法放入指定的缓冲区，并且已被截断。

- WSAEINVAL 未绑定套接字 `Bind` 。

- WSAECONNABORTED 由于超时或其他故障，虚拟线路已中止。

- WSAECONNRESET 远程端重置了虚拟线路。

### <a name="remarks"></a>备注

此函数用于连接的流或数据报套接字，用于读取传入的数据。

对于类型 SOCK_STREAM 的套接字，会返回当前提供的、返回的缓冲区大小的信息。 如果套接字已配置为带外数据（套接字选项 SO_OOBINLINE）的内联接收，并且带外数据未读，则只会返回带外数据。 应用程序可以使用 `IOCtlSIOCATMARK` 选项或[OnOutOfBandData](#onoutofbanddata)来确定是否仍在读取任何带外数据。

对于数据报套接字，将从第一个排队的数据报中提取数据，直到达到所提供的缓冲区大小。 如果数据报大于所提供的缓冲区，则使用数据报的第一部分填充缓冲区，多余的数据会丢失，并 `Receive` 返回值 SOCKET_ERROR 并将错误代码设置为 WSAEMSGSIZE。 如果套接字中没有可用的传入数据，将返回值 SOCKET_ERROR，并将错误代码设置为 WSAEWOULDBLOCK。 可以使用[OnReceive](#onreceive)回调函数来确定更多的数据何时到达。

如果套接字的类型为 SOCK_STREAM，而且远程端已正常关闭连接，则 `Receive` 会立即完成，并收到0个字节。 如果连接已重置，则 `Receive` 将失败，并出现错误 WSAECONNRESET。

`Receive`每次调用[CAsyncSocket：： OnReceive](#onreceive)时，只应调用一次。

### <a name="example"></a>示例

  请参阅[CAsyncSocket：： OnReceive](#onreceive)的示例。

## <a name="casyncsocketreceivefrom"></a><a name="receivefrom"></a>CAsyncSocket：： ReceiveFrom

调用此成员函数以接收数据报，并在[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构或*rSocketAddress*中存储源地址。

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

*nBufLen*<br/>
*LpBuf*的长度（以字节为单位）。

*rSocketAddress*<br/>
对 `CString` 接收点分数字 IP 地址的对象的引用。

*rSocketPort*<br/>
引用存储端口的 UINT。

*lpSockAddr*<br/>
指向[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的指针，该结构在返回时保存源地址。

*lpSockAddrLen*<br/>
一个指针，指向*lpSockAddr*中源地址的长度（以字节为单位）。

*nFlags*<br/>
指定进行调用的方式。 此函数的语义由套接字选项和*nFlags*参数确定。 后者通过将以下任意值与 c + +**或**运算符组合起来来构造：

- MSG_PEEK 查看传入数据。 数据将复制到缓冲区中，但不会从输入队列中删除。

- MSG_OOB 处理带外数据。

### <a name="return-value"></a>返回值

如果未发生错误，则 `ReceiveFrom` 返回已接收的字节数。 如果连接已关闭，则返回0。 否则，将返回 SOCKET_ERROR 的值，并且可以通过调用来检索特定的错误代码 `GetLastError` 。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEFAULT *lpSockAddrLen*参数无效： *lpSockAddr*缓冲区太小，无法容纳对等地址。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字操作。

- WSAEINVAL 未绑定套接字 `Bind` 。

- WSAENOTCONN 套接字未连接（仅 SOCK_STREAM）。

- WSAENOTSOCK 描述符不是套接字。

- 已指定 WSAEOPNOTSUPP MSG_OOB，但套接字的类型不是 SOCK_STREAM。

- WSAESHUTDOWN 套接字已关闭;`ReceiveFrom` `ShutDown` 调用*nHow*设置为0或2后，不能对套接字调用。

- WSAEWOULDBLOCK 套接字标记为非阻塞， `ReceiveFrom` 操作会阻止。

- WSAEMSGSIZE 数据报太大，无法放入指定的缓冲区，并且已被截断。

- WSAECONNABORTED 由于超时或其他故障，虚拟线路已中止。

- WSAECONNRESET 远程端重置了虚拟线路。

### <a name="remarks"></a>备注

此函数用于读取（可能连接的）套接字上的传入数据，并捕获从中发送数据的地址。

若要处理 IPv6 地址，请使用[CAsyncSocket：： ReceiveFromEx](#receivefromex)。

对于类型 SOCK_STREAM 的套接字，会返回当前提供的、返回的缓冲区大小的信息。 如果套接字已配置为带外数据（套接字选项 SO_OOBINLINE）的内联接收，并且带外数据未读，则只会返回带外数据。 应用程序可以使用 `IOCtlSIOCATMARK` 选项，或 `OnOutOfBandData` 确定是否仍然需要读取任何带外数据。 对于 SOCK_STREAM 套接字，将忽略*lpSockAddr*和*lpSockAddrLen*参数。

对于数据报套接字，将从第一个排队的数据报中提取数据，直到达到所提供的缓冲区大小。 如果数据报大于所提供的缓冲区，则使用消息的第一部分填充缓冲区，超过的数据将会丢失，并 `ReceiveFrom` 返回值 SOCKET_ERROR 并将错误代码设置为 WSAEMSGSIZE。

如果*lpSockAddr*为非零值，并且套接字为 SOCK_DGRAM 类型，则发送数据的套接字的网络地址会复制到相应的[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构。 *LpSockAddrLen*所指向的值将初始化为此结构的大小，并将在返回时修改以指示存储在该处的地址的实际大小。 如果套接字中没有可用的传入数据，则 `ReceiveFrom` 调用将等待数据到达，除非套接字处于非阻止状态。 在这种情况下，将返回值 SOCKET_ERROR，并将错误代码设置为 WSAEWOULDBLOCK。 `OnReceive`可以使用回调来确定更多的数据何时到达。

如果套接字的类型为 SOCK_STREAM，而且远程端已正常关闭连接，则 `ReceiveFrom` 会立即完成，并收到0个字节。

## <a name="casyncsocketreceivefromex"></a><a name="receivefromex"></a>CAsyncSocket：： ReceiveFromEx

调用此成员函数以接收数据报，并将源地址存储在[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构或*rSocketAddress*中（处理 IPv6 地址）。

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

*nBufLen*<br/>
*LpBuf*的长度（以字节为单位）。

*rSocketAddress*<br/>
对 `CString` 接收点分数字 IP 地址的对象的引用。

*rSocketPort*<br/>
引用存储端口的 UINT。

*nFlags*<br/>
指定进行调用的方式。 此函数的语义由套接字选项和*nFlags*参数确定。 后者通过将以下任意值与 c + +**或**运算符组合起来来构造：

- MSG_PEEK 查看传入数据。 数据将复制到缓冲区中，但不会从输入队列中删除。

- MSG_OOB 处理带外数据。

### <a name="return-value"></a>返回值

如果未发生错误，则 `ReceiveFromEx` 返回已接收的字节数。 如果连接已关闭，则返回0。 否则，将返回 SOCKET_ERROR 的值，并且可以通过调用来检索特定的错误代码 `GetLastError` 。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEFAULT *lpSockAddrLen*参数无效： *lpSockAddr*缓冲区太小，无法容纳对等地址。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字操作。

- WSAEINVAL 未绑定套接字 `Bind` 。

- WSAENOTCONN 套接字未连接（仅 SOCK_STREAM）。

- WSAENOTSOCK 描述符不是套接字。

- 已指定 WSAEOPNOTSUPP MSG_OOB，但套接字的类型不是 SOCK_STREAM。

- WSAESHUTDOWN 套接字已关闭;`ReceiveFromEx` `ShutDown` 调用*nHow*设置为0或2后，不能对套接字调用。

- WSAEWOULDBLOCK 套接字标记为非阻塞， `ReceiveFromEx` 操作会阻止。

- WSAEMSGSIZE 数据报太大，无法放入指定的缓冲区，并且已被截断。

- WSAECONNABORTED 由于超时或其他故障，虚拟线路已中止。

- WSAECONNRESET 远程端重置了虚拟线路。

### <a name="remarks"></a>备注

此函数用于读取（可能连接的）套接字上的传入数据，并捕获从中发送数据的地址。

此函数与[CAsyncSocket：： ReceiveFrom](#receivefrom)相同，不同之处在于它处理 IPv6 地址和旧协议。

对于类型 SOCK_STREAM 的套接字，会返回当前提供的、返回的缓冲区大小的信息。 如果套接字已配置为带外数据（套接字选项 SO_OOBINLINE）的内联接收，并且带外数据未读，则只会返回带外数据。 应用程序可以使用 `IOCtlSIOCATMARK` 选项，或 `OnOutOfBandData` 确定是否仍然需要读取任何带外数据。 对于 SOCK_STREAM 套接字，将忽略*lpSockAddr*和*lpSockAddrLen*参数。

对于数据报套接字，将从第一个排队的数据报中提取数据，直到达到所提供的缓冲区大小。 如果数据报大于所提供的缓冲区，则使用消息的第一部分填充缓冲区，超过的数据将会丢失，并 `ReceiveFromEx` 返回值 SOCKET_ERROR 并将错误代码设置为 WSAEMSGSIZE。

如果*lpSockAddr*为非零值，并且套接字为 SOCK_DGRAM 类型，则发送数据的套接字的网络地址会复制到相应的[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构。 *LpSockAddrLen*所指向的值将初始化为此结构的大小，并将在返回时修改以指示存储在该处的地址的实际大小。 如果套接字中没有可用的传入数据，则 `ReceiveFromEx` 调用将等待数据到达，除非套接字处于非阻止状态。 在这种情况下，将返回值 SOCKET_ERROR，并将错误代码设置为 WSAEWOULDBLOCK。 `OnReceive`可以使用回调来确定更多的数据何时到达。

如果套接字的类型为 SOCK_STREAM，而且远程端已正常关闭连接，则 `ReceiveFromEx` 会立即完成，并收到0个字节。

## <a name="casyncsocketsend"></a><a name="send"></a>CAsyncSocket：： Send

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

*nBufLen*<br/>
*LpBuf*中数据的长度（以字节为单位）。

*nFlags*<br/>
指定进行调用的方式。 此函数的语义由套接字选项和*nFlags*参数确定。 后者通过将以下任意值与 c + +**或**运算符组合起来来构造：

- MSG_DONTROUTE 指定数据不应受路由的限制。 Windows 套接字供应商可以选择忽略此标志。

- MSG_OOB 发送带外数据（仅 SOCK_STREAM）。

### <a name="return-value"></a>返回值

如果未发生错误，则 `Send` 返回已发送的字符总数。 （请注意，这可能小于*nBufLen*指示的数字）。否则，将返回值 SOCKET_ERROR，并通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEACCES 请求的地址是广播地址，但未设置适当的标志。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字操作。

- WSAEFAULT *lpBuf*参数不在用户地址空间的有效部分中。

- WSAENETRESET 必须重置连接，因为 Windows 套接字实现已将其删除。

- WSAENOBUFS Windows 套接字实现报告缓冲区死锁。

- WSAENOTCONN 套接字未连接。

- WSAENOTSOCK 描述符不是套接字。

- 已指定 WSAEOPNOTSUPP MSG_OOB，但套接字的类型不是 SOCK_STREAM。

- WSAESHUTDOWN 套接字已关闭;在 `Send` `ShutDown` *nHow*设置为1或2的情况调用之后，不能在套接字上调用。

- WSAEWOULDBLOCK 套接字标记为非阻止，请求的操作将会阻止。

- WSAEMSGSIZE 套接字的类型为 SOCK_DGRAM，数据报大于 Windows 套接字实现所支持的最大值。

- WSAEINVAL 未绑定套接字 `Bind` 。

- WSAECONNABORTED 由于超时或其他故障，虚拟线路已中止。

- WSAECONNRESET 远程端重置了虚拟线路。

### <a name="remarks"></a>备注

`Send`用于写入已连接的流或数据报套接字上的传出数据。 对于数据报套接字，必须注意不超过基础子网的最大 IP 数据包大小，该大小由 `iMaxUdpDg` 返回的[WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)结构中的元素提供 `AfxSocketInit` 。 如果数据太长，无法通过基础协议以原子方式传递，则会通过来返回错误 WSAEMSGSIZE `GetLastError` ，并且不会传输任何数据。

请注意，对于数据报套接字，成功完成后 `Send` 并不表示数据已成功传递。

在 `CAsyncSocket` SOCK_STREAM 类型的对象上，所写入的字节数可以介于1和请求的长度之间，具体取决于本地和外部主机上的缓冲可用性。

### <a name="example"></a>示例

  请参阅[CAsyncSocket：： OnSend](#onsend)的示例。

## <a name="casyncsocketsendto"></a><a name="sendto"></a>CAsyncSocket：： SendTo

调用此成员函数以将数据发送到特定目标。

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

*nBufLen*<br/>
*LpBuf*中数据的长度（以字节为单位）。

*nHostPort*<br/>
标识套接字应用程序的端口。

*lpszHostAddress*<br/>
此对象连接的套接字的网络地址：计算机名称（如 "ftp.microsoft.com"）或点分数字，如 "128.56.22.8"。

*nFlags*<br/>
指定进行调用的方式。 此函数的语义由套接字选项和*nFlags*参数确定。 后者通过将以下任意值与 c + +**或**运算符组合起来来构造：

- MSG_DONTROUTE 指定数据不应受路由的限制。 Windows 套接字供应商可以选择忽略此标志。

- MSG_OOB 发送带外数据（仅 SOCK_STREAM）。

*lpSockAddr*<br/>
指向[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的指针，该结构包含目标套接字的地址。

*nSockAddrLen*<br/>
*LpSockAddr*中地址的长度（以字节为单位）。

### <a name="return-value"></a>返回值

如果未发生错误，则 `SendTo` 返回已发送的字符总数。 （请注意，这可能小于*nBufLen*指示的数字）。否则，将返回值 SOCKET_ERROR，并通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEACCES 请求的地址是广播地址，但未设置适当的标志。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字操作。

- WSAEFAULT *lpBuf*或*lpSockAddr*参数不是用户地址空间的一部分，或者*lpSockAddr*参数太小（小于[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的大小）。

- WSAEINVAL 主机名无效。

- WSAENETRESET 必须重置连接，因为 Windows 套接字实现已将其删除。

- WSAENOBUFS Windows 套接字实现报告缓冲区死锁。

- WSAENOTCONN 套接字未连接（仅 SOCK_STREAM）。

- WSAENOTSOCK 描述符不是套接字。

- 已指定 WSAEOPNOTSUPP MSG_OOB，但套接字的类型不是 SOCK_STREAM。

- WSAESHUTDOWN 套接字已关闭;在 `SendTo` `ShutDown` *nHow*设置为1或2的情况调用之后，不能在套接字上调用。

- WSAEWOULDBLOCK 套接字标记为非阻止，请求的操作将会阻止。

- WSAEMSGSIZE 套接字的类型为 SOCK_DGRAM，数据报大于 Windows 套接字实现所支持的最大值。

- WSAECONNABORTED 由于超时或其他故障，虚拟线路已中止。

- WSAECONNRESET 远程端重置了虚拟线路。

- WSAEADDRNOTAVAIL 指定的地址在本地计算机上不可用。

- 指定系列中的 WSAEAFNOSUPPORT 地址不能用于此套接字。

- WSAEDESTADDRREQ 目标地址是必需的。

- WSAENETUNREACH 无法从此主机访问网络。

### <a name="remarks"></a>备注

`SendTo`用在数据报或流套接字上，用于写入套接字上的传出数据。 对于数据报套接字，必须注意不超过底层子网的最大 IP 数据包大小， `iMaxUdpDg` [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)结构中的元素由[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)填充。 如果数据太长，无法通过基础协议以原子方式传递，则会返回错误 WSAEMSGSIZE，并且不会传输任何数据。

请注意，成功完成后 `SendTo` 并不表示数据已成功传递。

`SendTo`仅在 SOCK_DGRAM 套接字上使用，以将数据报发送到由*lpSockAddr*参数标识的特定套接字。

若要发送广播（仅在 SOCK_DGRAM 上），应使用特殊的 IP INADDR_BROADCAST 地址（在 Windows 套接头文件 WINSOCK 中定义）构造*lpSockAddr*参数中的地址。H）以及目标端口号。 或者，如果*lpszHostAddress*参数为 NULL，则会为广播配置套接字。 通常情况下，广播数据报会可取到超过碎片的大小，这意味着数据报的数据部分（不包括标头）不应超过512个字节。

若要处理 IPv6 地址，请使用[CAsyncSocket：： SendToEx](#sendtoex)。

## <a name="casyncsocketsendtoex"></a><a name="sendtoex"></a>CAsyncSocket：： SendToEx

调用此成员函数以将数据发送到特定目标（处理 IPv6 地址）。

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

*nBufLen*<br/>
*LpBuf*中数据的长度（以字节为单位）。

*nHostPort*<br/>
标识套接字应用程序的端口。

*lpszHostAddress*<br/>
此对象连接的套接字的网络地址：计算机名称（如 "ftp.microsoft.com"）或点分数字，如 "128.56.22.8"。

*nFlags*<br/>
指定进行调用的方式。 此函数的语义由套接字选项和*nFlags*参数确定。 后者通过将以下任意值与 c + +**或**运算符组合起来来构造：

- MSG_DONTROUTE 指定数据不应受路由的限制。 Windows 套接字供应商可以选择忽略此标志。

- MSG_OOB 发送带外数据（仅 SOCK_STREAM）。

### <a name="return-value"></a>返回值

如果未发生错误，则 `SendToEx` 返回已发送的字符总数。 （请注意，这可能小于*nBufLen*指示的数字）。否则，将返回值 SOCKET_ERROR，并通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEACCES 请求的地址是广播地址，但未设置适当的标志。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字操作。

- WSAEFAULT *lpBuf*或*lpSockAddr*参数不是用户地址空间的一部分，或者*lpSockAddr*参数太小（小于[SOCKADDR](/windows/win32/winsock/sockaddr-2)结构的大小）。

- WSAEINVAL 主机名无效。

- WSAENETRESET 必须重置连接，因为 Windows 套接字实现已将其删除。

- WSAENOBUFS Windows 套接字实现报告缓冲区死锁。

- WSAENOTCONN 套接字未连接（仅 SOCK_STREAM）。

- WSAENOTSOCK 描述符不是套接字。

- 已指定 WSAEOPNOTSUPP MSG_OOB，但套接字的类型不是 SOCK_STREAM。

- WSAESHUTDOWN 套接字已关闭;在 `SendToEx` `ShutDown` *nHow*设置为1或2的情况调用之后，不能在套接字上调用。

- WSAEWOULDBLOCK 套接字标记为非阻止，请求的操作将会阻止。

- WSAEMSGSIZE 套接字的类型为 SOCK_DGRAM，数据报大于 Windows 套接字实现所支持的最大值。

- WSAECONNABORTED 由于超时或其他故障，虚拟线路已中止。

- WSAECONNRESET 远程端重置了虚拟线路。

- WSAEADDRNOTAVAIL 指定的地址在本地计算机上不可用。

- 指定系列中的 WSAEAFNOSUPPORT 地址不能用于此套接字。

- WSAEDESTADDRREQ 目标地址是必需的。

- WSAENETUNREACH 无法从此主机访问网络。

### <a name="remarks"></a>备注

此方法与[CAsyncSocket：： SendTo](#sendto)相同，不同之处在于它处理 IPv6 地址和旧协议。

`SendToEx`用在数据报或流套接字上，用于写入套接字上的传出数据。 对于数据报套接字，必须注意不超过底层子网的最大 IP 数据包大小， `iMaxUdpDg` [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)结构中的元素由[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)填充。 如果数据太长，无法通过基础协议以原子方式传递，则会返回错误 WSAEMSGSIZE，并且不会传输任何数据。

请注意，成功完成后 `SendToEx` 并不表示数据已成功传递。

`SendToEx`仅在 SOCK_DGRAM 套接字上使用，以将数据报发送到由*lpSockAddr*参数标识的特定套接字。

若要发送广播（仅在 SOCK_DGRAM 上），应使用特殊的 IP INADDR_BROADCAST 地址（在 Windows 套接头文件 WINSOCK 中定义）构造*lpSockAddr*参数中的地址。H）以及目标端口号。 或者，如果*lpszHostAddress*参数为 NULL，则会为广播配置套接字。 通常情况下，广播数据报会可取到超过碎片的大小，这意味着数据报的数据部分（不包括标头）不应超过512个字节。

## <a name="casyncsocketsetsockopt"></a><a name="setsockopt"></a>CAsyncSocket：： SetSockOpt

调用此成员函数以设置套接字选项。

```
BOOL SetSockOpt(
    int nOptionName,
    const void* lpOptionValue,
    int nOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>参数

*nOptionName*<br/>
要为其设置值的套接字选项。

*lpOptionValue*<br/>
指向缓冲区的指针，在此缓冲区中提供请求选项的值。

*nOptionLen*<br/>
*LpOptionValue*缓冲区的大小（以字节为单位）。

*nLevel*<br/>
定义选项的级别;仅 SOL_SOCKET 和 IPPROTO_TCP 支持的级别。

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEFAULT *lpOptionValue*不在进程地址空间的有效部分。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字操作。

- WSAEINVAL *nLevel*无效，或者*lpOptionValue*中的信息无效。

- 设置 SO_KEEPALIVE 后，WSAENETRESET 连接已超时。

- WSAENOPROTOOPT 选项未知或不受支持。 具体而言，SO_BROADCAST 在类型 SOCK_STREAM 的套接字上不受支持，而 SO_DONTLINGER、SO_KEEPALIVE、SO_LINGER 和 SO_OOBINLINE 在类型 SOCK_DGRAM 的插槽上不受支持。

- 设置 SO_KEEPALIVE 后，WSAENOTCONN 连接已重置。

- WSAENOTSOCK 描述符不是套接字。

### <a name="remarks"></a>备注

`SetSockOpt`设置与任何类型的套接字关联的套接字选项的当前值（以任何状态表示）。 尽管选项可以存在于多个协议级别，但此规范仅定义位于最上面的 "套接字" 级别的选项。 选项会影响套接字操作，例如是否在正常数据流中接收加急数据、是否可以在套接字上发送广播消息等等。

有两种类型的套接字选项：启用或禁用功能或行为的布尔选项，以及需要整数值或结构的选项。 若要启用布尔选项， *lpOptionValue*将指向非零整数。 若要禁用选项*lpOptionValue* ，请将其指向等于零的整数。 对于布尔选项， *nOptionLen*应等于 `sizeof(BOOL)` 。 对于其他选项， *lpOptionValue*指向包含选项所需值的整数或结构， *nOptionLen*是整数或结构的长度。

SO_LINGER 控制当未发送的数据在套接字上排队时执行的操作，并且 `Close` 调用该函数关闭套接字。

默认情况下，不能将套接字绑定（请参阅[Bind](#bind)）到已在使用中的本地地址。 然而，在这种情况下，可能需要以这种方式 "重新使用" 地址。 由于每个连接都是由本地和远程地址的组合唯一标识的，因此，只要远程地址不同，将两个套接字绑定到相同的本地地址就没有问题。

若要通知 Windows 套接字实现 `Bind` 不应禁用套接字上的调用，因为另一个套接字已使用了所需的地址，则应用程序应在发出调用之前设置套接字的 SO_REUSEADDR 套接字选项 `Bind` 。 请注意，此选项仅在调用时才会被解释 `Bind` ：因此，不需要（但无害）在不绑定到现有地址的套接字上设置选项，并且在调用后设置或重置该选项 `Bind` 不会对此或任何其他套接字产生任何影响。

应用程序可以通过打开 SO_KEEPALIVE 套接字选项来请求 Windows 套接字实现允许在传输控制协议（TCP）连接上使用 "保持活动状态" 数据包。 Windows 套接字实现不需要支持 keep-alive：否则，精确的语义是特定于实现的，但应遵循 RFC 1122： "Internet 主机的要求-通信层" 中的4.2.3.6 部分。 如果由于 "保持 http 连接" 而删除了某个连接，则错误代码 WSAENETRESET 将返回到该套接字上正在进行的任何调用，并且任何后续调用都将失败，并返回 WSAENOTCONN。

TCP_NODELAY 选项禁用 Nagle 算法。 Nagle 算法用于通过缓冲未确认的发送数据来减少主机发送的小型数据包数量，直到可以发送全尺寸的数据包。 但是，对于某些应用程序，此算法可能会降低性能，并 TCP_NODELAY 可用于将其关闭。 应用程序编写器不应将 TCP_NODELAY 设置为，除非此操作的影响非常清楚并且需要，因为设置 TCP_NODELAY 可能会对网络性能产生严重的负面影响。 TCP_NODELAY 是唯一受支持的套接字选项，它使用 level IPPROTO_TCP;所有其他选项都使用 level SOL_SOCKET。

如果 SO_DEBUG 选项由应用程序设置，Windows 套接字的某些实现将提供输出调试信息。

支持以下选项 `SetSockOpt` 。 类型标识*lpOptionValue*寻址的数据类型。

|值|类型|含义|
|-----------|----------|-------------|
|SO_BROADCAST|BOOL|允许在套接字上传输广播消息。|
|SO_DEBUG|BOOL|记录调试信息。|
|SO_DONTLINGER|BOOL|请勿阻止 `Close` 正在等待发送未发送的数据。 设置此选项等效于设置 `l_onoff` 设置为零的 SO_LINGER。|
|SO_DONTROUTE|BOOL|不路由：直接发送到接口。|
|SO_KEEPALIVE|BOOL|发送 keep-alive。|
|SO_LINGER|`struct LINGER`|逗留 `Close` 未发送的数据是否存在。|
|SO_OOBINLINE|BOOL|接收正常数据流中的带外数据。|
|SO_RCVBUF|**`int`**|指定接收的缓冲区大小。|
|SO_REUSEADDR|BOOL|允许将套接字绑定到已在使用中的地址。 （请参见[绑定](#bind)。）|
|SO_SNDBUF|**`int`**|指定发送的缓冲区大小。|
|TCP_NODELAY|BOOL|为发送合并禁用 Nagle 算法。|

不支持的 Berkeley 软件分发（BSD）选项 `SetSockOpt` 包括：

|值|类型|含义|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|套接字正在侦听|
|SO_ERROR|**`int`**|获取错误状态并清除。|
|SO_RCVLOWAT|**`int`**|接收低水位线。|
|SO_RCVTIMEO|**`int`**|接收超时|
|SO_SNDLOWAT|**`int`**|发送低水位线。|
|SO_SNDTIMEO|**`int`**|发送超时。|
|SO_TYPE|**`int`**|套接字的类型。|
|IP_OPTIONS||在 IP 标头中设置选项字段。|

## <a name="casyncsocketshutdown"></a><a name="shutdown"></a>CAsyncSocket：： ShutDown

调用此成员函数可在套接字上禁用发送、接收或同时禁用这两者。

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>参数

*nHow*<br/>
使用以下枚举值描述将不再允许哪些类型的操作的标志：

- **接收 = 0**

- **send = 1**

- **两者均为2**

### <a name="return-value"></a>返回值

如果函数成功，则为非零值;否则为0，可以通过调用[GetLastError](#getlasterror)来检索特定的错误代码。 以下错误适用于此成员函数：

- WSANOTINITIALISED 成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。

- WSAENETDOWN Windows 套接字实现检测到网络子系统出现故障。

- WSAEINVAL *nHow*无效。

- 返回 WSAEINPROGRESS 正在进行阻止型 Windows 套接字操作。

- WSAENOTCONN 套接字未连接（仅 SOCK_STREAM）。

- WSAENOTSOCK 描述符不是套接字。

### <a name="remarks"></a>备注

`ShutDown`用于所有类型的套接字来禁用接收和/或传输。 如果*nHow*为0，则不允许在套接字上进行后续接收。 这不会影响较低协议层。

对于传输控制协议（TCP），TCP 窗口不会更改，并且将接受传入的数据（但不确认），直到窗口耗尽。 对于用户数据报协议（UDP），会接受并排队传入的数据报。 在任何情况下，都不会生成 ICMP 错误数据包。 如果*nHow*为1，则不允许后续发送。 对于 TCP 套接字，将发送一个 FIN。 将*nHow*设置为2将禁用发送和接收，如上所述。

请注意，不会 `ShutDown` 关闭套接字，在调用之前，不会释放附加到套接字的资源 `Close` 。 应用程序不应依赖于在关闭套接字后是否能够重复使用它。 特别是，Windows 套接字实现不需要支持 `Connect` 在此类套接字上使用。

### <a name="example"></a>示例

  请参阅[CAsyncSocket：： OnReceive](#onreceive)的示例。

## <a name="casyncsocketsocket"></a><a name="socket"></a>CASyncSocket：：套接字

分配套接字句柄。

```
BOOL Socket(
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    int nProtocolType = 0,
    int nAddressFormat = PF_INET);
```

### <a name="parameters"></a>参数

*nSocketType*<br/>
指定 `SOCK_STREAM` 或 `SOCK_DGRAM` 。

*lEvent*<br/>
一个位掩码，指定应用程序感兴趣的网络事件的组合。

- `FD_READ`：希望接收有关读取准备情况的通知。

- `FD_WRITE`：希望接收有关写入准备情况的通知。

- `FD_OOB`：希望接收带外数据到达时的通知。

- `FD_ACCEPT`：希望接收传入连接的通知。

- `FD_CONNECT`：希望接收已完成连接的通知。

- `FD_CLOSE`：希望接收套接字关闭通知。

*nProtocolType*<br/>
要与特定于所指示的地址族的套接字一起使用的协议。

*nAddressFormat*<br/>
地址系列规范。

### <a name="return-value"></a>返回值

成功时返回 `TRUE`，失败时返回 `FALSE`。

### <a name="remarks"></a>备注

此方法分配套接字句柄。 它不会调用[CAsyncSocket：： bind](#bind)将套接字绑定到指定地址，因此你需要在以后调用 `Bind` 以将套接字绑定到指定的地址。 在绑定之前，可以使用[CAsyncSocket：： SetSockOpt](#setsockopt)设置套接字选项。

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CSocket 类](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile 类](../../mfc/reference/csocketfile-class.md)
