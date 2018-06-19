---
title: CAsyncSocket 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5eaefa40be2a6cf1d57326c2135d848fa08dbc87
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357684"
---
# <a name="casyncsocket-class"></a>CAsyncSocket 类
表示 Windows 套接字-网络通信的终结点。  
  
## <a name="syntax"></a>语法  
  
```  
class CAsyncSocket : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAsyncSocket::CAsyncSocket](#casyncsocket)|构造 `CAsyncSocket` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAsyncSocket::Accept](#accept)|接受套接字上的连接。|  
|[CAsyncSocket::AsyncSelect](#asyncselect)|套接字的请求事件通知。|  
|[CAsyncSocket::Attach](#attach)|将附加到套接字句柄`CAsyncSocket`对象。|  
|[CAsyncSocket::Bind](#bind)|将与套接字关联的本地地址。|  
|[CAsyncSocket::Close](#close)|关闭套接字。|  
|[CAsyncSocket::Connect](#connect)|建立为对等套接字连接。|  
|[CAsyncSocket::Create](#create)|创建套接字。|  
|[CAsyncSocket::Detach](#detach)|分离从套接字句柄`CAsyncSocket`对象。|  
|[CAsyncSocket::FromHandle](#fromhandle)|返回一个指向`CAsyncSocket`给定套接字句柄的对象。|  
|[CAsyncSocket::GetLastError](#getlasterror)|获取失败的最后一个操作的错误状态。|  
|[CAsyncSocket::GetPeerName](#getpeername)|获取套接字连接到的对等套接字的地址。|  
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|获取到套接字的连接 （句柄 IPv6 地址） 的对等套接字的地址。|  
|[CAsyncSocket::GetSockName](#getsockname)|获取套接字的本地名称。|  
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|获取套接字 （句柄 IPv6 地址） 的本地名称。|  
|[CAsyncSocket::GetSockOpt](#getsockopt)|检索套接字选项。|  
|[CAsyncSocket::IOCtl](#ioctl)|控制的套接字的模式。|  
|[CAsyncSocket::Listen](#listen)|建立的套接字侦听传入连接请求。|  
|[CAsyncSocket::Receive](#receive)|从套接字接收数据。|  
|[CAsyncSocket::ReceiveFrom](#receivefrom)|接收数据报并将存储的源地址。|  
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|接收数据报并将存储的源地址 （句柄 IPv6 地址）。|  
|[CAsyncSocket::Send](#send)|将数据发送到连接的套接字。|  
|[CAsyncSocket::SendTo](#sendto)|将数据发送到特定目标。|  
|[CAsyncSocket::SendToEx](#sendtoex)|将数据发送到特定目标 （句柄 IPv6 地址）。|  
|[CAsyncSocket::SetSockOpt](#setsockopt)|设置套接字选项。|  
|[CAsyncSocket::ShutDown](#shutdown)|禁用**发送**和/或**接收**套接字上调用。|  
|[CASyncSocket::Socket](#socket)|分配套接字句柄。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAsyncSocket::OnAccept](#onaccept)|通知它可以通过调用接受挂起的连接请求的侦听套接字**接受**。|  
|[CAsyncSocket::OnClose](#onclose)|通知套接字连接到它的套接字已关闭。|  
|[CAsyncSocket::OnConnect](#onconnect)|通知连接的套接字连接尝试是否已完成，成功或错误。|  
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|通知的接收套接字没有要读取套接字，通常紧急邮件上的带外数据。|  
|[CAsyncSocket::OnReceive](#onreceive)|通知侦听套接字是否有数据要检索通过调用**接收**。|  
|[CAsyncSocket::OnSend](#onsend)|通知套接字，它可发送数据，通过调用**发送**。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CAsyncSocket::operator =](#operator_eq)|将新值赋给`CAsyncSocket`对象。|  
|[CAsyncSocket::operator 套接字](#operator_socket)|此运算符用于检索**套接字**的 handle`CAsyncSocket`对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CAsyncSocket::m_hSocket](#m_hsocket)|指示**套接字**句柄附加到此`CAsyncSocket`对象。|  
  
## <a name="remarks"></a>备注  
 类`CAsyncSocket`封装 Windows 套接字函数 API，为想要与 MFC 一起使用 Windows 套接字的程序员提供的面向对象的抽象。  
  
 此类基于你了解网络通信的假设。 你将负责处理阻止，字节顺序的差异，并 Unicode 和多字节字符之间的转换设置 (MBCS) 字符串。 如果你希望更方便的界面，将为您管理这些问题，请参阅类[CSocket](../../mfc/reference/csocket-class.md)。  
  
 若要使用`CAsyncSocket`对象，请调用其构造函数，然后调用[创建](#create)函数来创建基础套接字句柄 (类型`SOCKET`)，除非在接受套接字上。 服务器套接字调用[侦听](#listen)成员函数和客户端套接字调用[连接](#connect)成员函数。 服务器套接字应调用[接受](#accept)收到连接请求的函数。 使用剩余`CAsyncSocket`函数来执行套接字之间的通信。 完成后，销毁`CAsyncSocket`对象是在堆上创建; 析构函数自动调用[关闭](#close)函数。 `SOCKET`文章中介绍了数据类型[Windows 套接字： 背景](../../mfc/windows-sockets-background.md)。  
  
> [!NOTE]
>  在静态链接的 MFC 应用程序中的辅助线程中使用 MFC 套接字时，您必须在使用套接字的每个线程中调用 `AfxSocketInit` 来初始化套接字库。 默认情况下，仅在主线程中调用 `AfxSocketInit`。  
  
 有关详细信息，请参阅[Windows 套接字： 使用类 CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md)和相关文章。，以及[Windows 套接字 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAsyncSocket`  
  
## <a name="requirements"></a>要求  
 **标头：** afxsock.h  
  
##  <a name="accept"></a>  CAsyncSocket::Accept  
 调用此成员函数可接受套接字上的连接。  
  
```  
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,  
    SOCKADDR* lpSockAddr = NULL,  
    int* lpSockAddrLen = NULL);
```  
  
### <a name="parameters"></a>参数  
 `rConnectedSocket`  
 标识可用于连接的新套接字的引用。  
  
 `lpSockAddr`  
 指向的指针[SOCKADDR](../../mfc/reference/sockaddr-structure.md)套接字接收连接的地址的结构，因为在网络上识别。 确切格式`lpSockAddr`自变量由套接字已创建时建立的地址族。 如果`lpSockAddr`和/或`lpSockAddrLen`等于**NULL**，则不返回有关远程地址接受套接字的任何信息。  
  
 `lpSockAddrLen`  
 中的地址的长度的指针`lpSockAddr`以字节为单位。 `lpSockAddrLen`是值结果参数： 它最初应包含指向的空间量`lpSockAddr`; 返回时它将包含返回的地址的实际长度 （以字节为单位）。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则通过调用检索 0 和特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpSockAddrLen`自变量是太小 (小于的大小[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构)。  
  
- **返回 WSAEINPROGRESS**阻止 Windows 套接字调用正在进行。  
  
- **WSAEINVAL** `Listen`未调用的之前接受。  
  
- **WSAEMFILE**队列为空以接受在输入时，并且有可用的任何描述符。  
  
- `WSAENOBUFS` 没有缓冲区空间不可用。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP**引用套接字不支持面向连接的服务类型。  
  
- **WSAEWOULDBLOCK**套接字被标记为非阻塞并且没有连接存在才能被接受。  
  
### <a name="remarks"></a>备注  
 此例程提取挂起连接的队列中的第一个连接，与此套接字，相同的属性创建新的套接字，并将其附加到`rConnectedSocket`。 如果没有挂起的连接在队列中，存在**接受**返回零和`GetLastError`返回错误。 接受的套接字 ( *rConnectedSocket)* 不能用于接受更多连接。 原始的套接字保持打开，但侦听。  
  
 自变量`lpSockAddr`因为识别的通信层是使用的地址的连接的套接字，填充的结果参数。 **接受**用于基于连接的套接字类型如**SOCK_STREAM**。  
  
##  <a name="asyncselect"></a>  CAsyncSocket::AsyncSelect  
 调用此成员函数以请求获得对于套接字的事件通知。  
  
```  
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>参数  
 `lEvent`  
 一个位屏蔽，它指定应用程序感兴趣的网络事件的组合。  
  
- **FD_READ**想要接收通知以进行读取的准备情况。  
  
- **FD_WRITE**想要接收通知，可供读取的数据时。  
  
- **FD_OOB**想要接收的带外数据到达的通知。  
  
- **FD_ACCEPT**想要接收通知的传入连接。  
  
- **FD_CONNECT**想要接收的连接结果的通知。  
  
- **FD_CLOSE**希望在套接字已关闭对等方时收到通知。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则通过调用检索 0 和特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEINVAL**指示指定的参数之一无效。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
### <a name="remarks"></a>备注  
 此函数用于指定哪些 MFC 回调通知函数将调用为套接字。 `AsyncSelect` 自动将此套接字设置为阻止模式下。 有关详细信息，请参阅文章[Windows 套接字： 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="attach"></a>  CAsyncSocket::Attach  
 调用此成员函数可将附加`hSocket`的句柄`CAsyncSocket`对象。  
  
```  
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>参数  
 `hSocket`  
 包含为套接字的句柄。  
  
 `lEvent`  
 一个位屏蔽，它指定应用程序感兴趣的网络事件的组合。  
  
- **FD_READ**想要接收通知以进行读取的准备情况。  
  
- **FD_WRITE**想要接收通知，可供读取的数据时。  
  
- **FD_OOB**想要接收的带外数据到达的通知。  
  
- **FD_ACCEPT**想要接收通知的传入连接。  
  
- **FD_CONNECT**想要接收的连接结果的通知。  
  
- **FD_CLOSE**希望在套接字已关闭对等方时收到通知。  
  
### <a name="return-value"></a>返回值  
 如果函数运行成功，则为非零。  
  
### <a name="remarks"></a>备注  
 **套接字**句柄存储在对象的[m_hSocket](#m_hsocket)数据成员。  
  
##  <a name="bind"></a>  CAsyncSocket::Bind  
 调用此成员函数可将与套接字关联的本地地址。  
  
```  
BOOL Bind(
    UINT nSocketPort,  
    LPCTSTR lpszSocketAddress = NULL);

 
BOOL Bind (
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>参数  
 `nSocketPort`  
 标识套接字应用程序的端口。  
  
 `lpszSocketAddress`  
 网络地址，如"128.56.22.8"圆点分隔数。 传递**NULL**字符串此参数指示**CAsyncSocket**实例应侦听的所有网络接口上的客户端活动。  
  
 `lpSockAddr`  
 指向的指针[SOCKADDR](../../mfc/reference/sockaddr-structure.md)包含要分配给此套接字地址结构。  
  
 `nSockAddrLen`  
 中的地址的长度`lpSockAddr`以字节为单位。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则通过调用检索 0 和特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEADDRINUSE**指定的地址已在使用。 (请参阅**SO_REUSEADDR**套接字选项下的[SetSockOpt](#setsockopt)。)  
  
- **WSAEFAULT** `nSockAddrLen`自变量是太小 (小于的大小[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构)。  
  
- **返回 WSAEINPROGRESS**阻止 Windows 套接字调用正在进行。  
  
- **WSAEAFNOSUPPORT**此端口不支持指定的地址族。  
  
- **WSAEINVAL**套接字已绑定到一个地址。  
  
- `WSAENOBUFS` 没有足够的缓冲区可用，过多连接。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 此例程使用未连接的数据报或流套接字上之前后续**连接**或`Listen`调用。 它可以接受连接请求之前，侦听服务器套接字必须选择一个端口号，并将它已知对 Windows 套接字通过调用**绑定**。 **将绑定**建立通过将本地名称分配给未命名的套接字的套接字的本地关联 （主机地址/端口号）。  
  
##  <a name="casyncsocket"></a>  CAsyncSocket::CAsyncSocket  
 构造一个空的套接字对象。  
  
```  
CAsyncSocket();
```  
  
### <a name="remarks"></a>备注  
 在构造对象之后, 必须调用其**创建**成员函数来创建**套接字**数据结构，并将其地址的绑定。 (在服务器端的 Windows 套接字通信，当侦听套接字创建要在中使用的套接字**接受**调用，请勿调用**创建**该套接字。)  
  
##  <a name="close"></a>  CAsyncSocket::Close  
 关闭套接字。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 此函数释放的套接字描述符，以便进一步对它的引用将失败并出现错误**WSAENOTSOCK**。 如果这是对基础套接字的最后引用，将丢弃关联的命名信息和排队的数据。 套接字对象的析构函数调用**关闭**为你。  
  
 有关`CAsyncSocket`，但不是能为`CSocket`的语义**关闭**受套接字选项**SO_LINGER**和**SO_DONTLINGER**。 有关详细信息，请参阅成员函数`GetSockOpt`。  
  
##  <a name="connect"></a>  CAsyncSocket::Connect  
 调用此成员函数可建立到未连接的流或数据报套接字连接。  
  
```  
BOOL Connect(
    LPCTSTR lpszHostAddress,  
    UINT nHostPort);

 
BOOL Connect(
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>参数  
 `lpszHostAddress`  
 此对象连接到的套接字的网络地址： 一个计算机名称，例如"ftp.microsoft.com"或一个以点分隔的数字，如"128.56.22.8"。  
  
 `nHostPort`  
 标识套接字应用程序的端口。  
  
 `lpSockAddr`  
 指向的指针[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构，其中包含连接的套接字的地址。  
  
 `nSockAddrLen`  
 中的地址的长度`lpSockAddr`以字节为单位。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则通过调用检索 0 和特定错误代码[GetLastError](#getlasterror)。 如果这指示的错误代码为**WSAEWOULDBLOCK**，和你的应用程序使用可重写回调时，你的应用程序将收到`OnConnect`消息时连接操作已完成。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEADDRINUSE**指定的地址已在使用。  
  
- **返回 WSAEINPROGRESS**阻止 Windows 套接字调用正在进行。  
  
- **WSAEADDRNOTAVAIL**指定的地址不是可从本地计算机。  
  
- **WSAEAFNOSUPPORT**指定系列中的地址不能用于此套接字。  
  
- **WSAECONNREFUSED**连接尝试被拒绝。  
  
- **WSAEDESTADDRREQ**目标地址是必需的。  
  
- **WSAEFAULT** `nSockAddrLen`参数不正确。  
  
- **WSAEINVAL**无效主机地址。  
  
- **WSAEISCONN**套接字已连接。  
  
- **WSAEMFILE**没有更多的文件描述符。  
  
- **WSAENETUNREACH**网络无法在此时间到达从此主机。  
  
- `WSAENOBUFS` 没有缓冲区空间不可用。 无法连接套接字。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAETIMEDOUT**尝试连接超时而无需建立连接。  
  
- **WSAEWOULDBLOCK**套接字被标记为锁定，并且无法立即完成连接。  
  
### <a name="remarks"></a>备注  
 如果是未绑定套接字、 唯一值分配给本地关联系统和套接字标记为绑定。 请注意，如果名称结构的地址字段是所有零**连接**将返回零。 若要获得扩展的错误信息，调用`GetLastError`成员函数。  
  
 有关流套接字 (类型**SOCK_STREAM**)，活动连接启动到外的主机。 套接字调用成功完成后，套接字已准备好发送/接收数据。  
  
 对于数据报套接字 (类型**SOCK_DGRAM**)，设置默认目标，将在以后使用它**发送**和**接收**调用。  
  
##  <a name="create"></a>  CAsyncSocket::Create  
 调用**创建**后构造套接字对象创建 Windows 套接字并将其连接的成员函数。  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>参数  
 `nSocketPort`  
 如果你想要选择的端口的 Windows 套接字的套接字或 0 开头要使用的已知端口。  
  
 `nSocketType`  
 **SOCK_STREAM**或**SOCK_DGRAM**。  
  
 `lEvent`  
 一个位屏蔽，它指定应用程序感兴趣的网络事件的组合。  
  
- **FD_READ**想要接收通知以进行读取的准备情况。  
  
- **FD_WRITE**想要接收通知以进行写入的准备情况。  
  
- **FD_OOB**想要接收的带外数据到达的通知。  
  
- **FD_ACCEPT**想要接收通知的传入连接。  
  
- **FD_CONNECT**想要接收已完成的连接的通知。  
  
- **FD_CLOSE**想要接收通知的套接字闭包。  
  
 *lpszSockAddress*  
 指向包含连接的套接字，一个以点分隔的数字，如"128.56.22.8"的网络地址的字符串的指针。传递**NULL**字符串此参数指示**CAsyncSocket**实例应侦听的所有网络接口上的客户端活动。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则通过调用检索 0 和特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEAFNOSUPPORT**不支持指定的地址族。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEMFILE**没有更多的文件描述符。  
  
- `WSAENOBUFS` 没有缓冲区空间不可用。 无法创建套接字。  
  
- **WSAEPROTONOSUPPORT**不支持指定的端口。  
  
- **WSAEPROTOTYPE**指定的端口是此套接字的错误类型。  
  
- **WSAESOCKTNOSUPPORT**指定套接字类型不支持此地址族中。  
  
### <a name="remarks"></a>备注  
 **创建**调用[套接字](#socket)如果成功，将调用[绑定](#bind)将套接字绑定到指定的地址。 支持以下套接字类型：  
  
- **SOCK_STREAM**提供序列化，可靠、 全双工、 基于连接的字节流。 为 Internet 地址族使用传输控制协议 (TCP)。  
  
- **SOCK_DGRAM**支持数据报，即无连接的、 不可靠的数据包的固定 （通常很小） 的最大长度。 为 Internet 地址族使用用户数据报协议 (UDP)。  
  
    > [!NOTE]
    >  **接受**成员函数会将新的空引用`CSocket`对象作为其参数。 您必须构造此对象，然后才能调用**接受**。 请记住，如果此套接字对象超出范围，该连接将关闭。 不要调用**创建**为此新的套接字对象。  
  
> [!IMPORTANT]
> **创建**是**不**线程安全。  如果正在调用它在多线程环境中时，它也可以调用同时不同的线程，请务必保护每个调用具有互斥体或其他同步锁。  
  
 有关流和数据报套接字的详细信息，请参阅文章[Windows 套接字： 背景](../../mfc/windows-sockets-background.md)和[Windows 套接字： 端口和套接字地址](../../mfc/windows-sockets-ports-and-socket-addresses.md)和[Windows 套接字 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
##  <a name="detach"></a>  CAsyncSocket::Detach  
 调用此成员函数可分离**套接字**在中处理`m_hSocket`中的数据成员`CAsyncSocket`对象，并将`m_hSocket`到**NULL**。  
  
```  
SOCKET Detach();
```  
  
##  <a name="fromhandle"></a>  CAsyncSocket::FromHandle  
 返回一个指向`CAsyncSocket`对象。  
  
```  
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```  
  
### <a name="parameters"></a>参数  
 `hSocket`  
 包含为套接字的句柄。  
  
### <a name="return-value"></a>返回值  
 指向的指针`CAsyncSocket`对象，或**NULL**如果没有任何`CAsyncSocket`对象附加到`hSocket`。  
  
### <a name="remarks"></a>备注  
 在给定**套接字**处理，如果`CAsyncSocket`对象未附加到该句柄，则成员函数将返回**NULL**。  
  
##  <a name="getlasterror"></a>  CAsyncSocket::GetLastError  
 调用此成员函数以获取有关失败的最后一个操作的错误状态。  
  
```  
static int PASCAL GetLastError();
```  
  
### <a name="return-value"></a>返回值  
 返回值指示此线程执行的最后一个 Windows 套接字 API 例程的错误代码。  
  
### <a name="remarks"></a>备注  
 当某个特定成员函数指示已发生错误，`GetLastError`应调用以检索相应的错误代码。 请参阅单独的成员函数描述，有关列表适用的错误代码。  
  
 有关错误代码的详细信息，请参阅[Windows 套接字 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673)。  
  
##  <a name="getpeername"></a>  CAsyncSocket::GetPeerName  
 调用此成员函数可获取此套接字连接到的对等套接字地址。  
  
```  
BOOL GetPeerName(
    CString& rPeerAddress,  
    UINT& rPeerPort);

 
BOOL GetPeerName(
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen);
```  
  
### <a name="parameters"></a>参数  
 `rPeerAddress`  
 引用`CString`收到以点分隔的数字 IP 地址的对象。  
  
 `rPeerPort`  
 引用**UINT**存储一个端口。  
  
 `lpSockAddr`  
 指向的指针[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构，它接收的对等套接字的名称。  
  
 `lpSockAddrLen`  
 中的地址的长度的指针`lpSockAddr`以字节为单位。 返回时，`lpSockAddrLen`自变量包含的实际大小`lpSockAddr`返回以字节为单位。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则通过调用检索 0 和特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpSockAddrLen`参数不是足够大。  
  
- **返回 WSAEINPROGRESS**阻止 Windows 套接字调用正在进行。  
  
- **WSAENOTCONN**套接字未连接。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 若要处理 IPv6 地址，使用[CAsyncSocket::GetPeerNameEx](#getpeernameex)。  
  
##  <a name="getpeernameex"></a>  CAsyncSocket::GetPeerNameEx  
 调用此成员函数可获取到此套接字的连接 （句柄 IPv6 地址） 的对等套接字地址。  
  
```  
BOOL GetPeerNameEx(
    CString& rPeerAddress,  
    UINT& rPeerPort);
```  
  
### <a name="parameters"></a>参数  
 `rPeerAddress`  
 引用`CString`收到以点分隔的数字 IP 地址的对象。  
  
 `rPeerPort`  
 引用**UINT**存储一个端口。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则通过调用检索 0 和特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpSockAddrLen`参数不是足够大。  
  
- **返回 WSAEINPROGRESS**阻止 Windows 套接字调用正在进行。  
  
- **WSAENOTCONN**套接字未连接。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 此函数是与相同[CAsyncSocket::GetPeerName](#getpeername) ，只不过它处理 IPv6 地址以及较旧的协议。  
  
##  <a name="getsockname"></a>  CAsyncSocket::GetSockName  
 调用此成员函数可获取套接字的本地名称。  
  
```  
BOOL GetSockName(
    CString& rSocketAddress,  
    UINT& rSocketPort);

 
BOOL GetSockName(
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen);
```  
  
### <a name="parameters"></a>参数  
 `rSocketAddress`  
 引用`CString`收到以点分隔的数字 IP 地址的对象。  
  
 `rSocketPort`  
 引用**UINT**存储一个端口。  
  
 `lpSockAddr`  
 指向的指针[SOCKADDR](../../mfc/reference/sockaddr-structure.md)接收的套接字地址的结构。  
  
 `lpSockAddrLen`  
 中的地址的长度的指针`lpSockAddr`以字节为单位。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则通过调用检索 0 和特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpSockAddrLen`参数不是足够大。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEINVAL**套接字已不绑定到包含的地址**绑定**。  
  
### <a name="remarks"></a>备注  
 时，此调用是特别有用**连接**已调用而无需这样做**绑定**首先; 此调用提供了你可以依据确定已设置的本地关联的唯一方法系统。  
  
 若要处理 IPv6 地址，使用[CAsyncSocket::GetSockNameEx](#getsocknameex)  
  
##  <a name="getsocknameex"></a>  CAsyncSocket::GetSockNameEx  
 调用此成员函数可获取套接字 （句柄 IPv6 地址） 的本地名称。  
  
```  
BOOL GetSockNameEx(
    CString& rSocketAddress,  
    UINT& rSocketPort);
```  
  
### <a name="parameters"></a>参数  
 `rSocketAddress`  
 引用`CString`收到以点分隔的数字 IP 地址的对象。  
  
 `rSocketPort`  
 引用**UINT**存储一个端口。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则通过调用检索 0 和特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpSockAddrLen`参数不是足够大。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEINVAL**套接字已不绑定到包含的地址**绑定**。  
  
### <a name="remarks"></a>备注  
 此调用是相同[CAsyncSocket::GetSockName](#getsockname) ，只不过它处理 IPv6 地址以及较旧的协议。  
  
 时，此调用是特别有用**连接**已调用而无需这样做**绑定**首先; 此调用提供了你可以依据确定已设置的本地关联的唯一方法系统。  
  
##  <a name="getsockopt"></a>  CAsyncSocket::GetSockOpt  
 调用此成员函数可检索套接字选项。  
  
```  
BOOL GetSockOpt(
    int nOptionName,  
    void* lpOptionValue,  
    int* lpOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>参数  
 `nOptionName`  
 为其值是要检索套接字选项。  
  
 `lpOptionValue`  
 指向在其中请求选项的值是要返回的缓冲区的指针。 在缓冲区中返回与所选的选项关联的值`lpOptionValue`。 指向整数`lpOptionLen`最初应包含以字节为单位; 此缓冲区的大小，并且返回时，它将设置为返回的值的大小。 有关**SO_LINGER**，这将是大小`LINGER`结构; 对于所有其他选项，它将为的大小**BOOL**或`int`，具体选项取决于。 请参阅选项和备注部分中的其大小的列表。  
  
 `lpOptionLen`  
 指向的大小的`lpOptionValue`以字节为单位的缓冲区。  
  
 `nLevel`  
 从该处选项定义; 级别仅支持级别**SOL_SOCKET**和**IPPROTO_TCP**。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则通过调用检索 0 和特定错误代码[GetLastError](#getlasterror)。 如果具有永远不会设置一个选项`SetSockOpt`，然后`GetSockOpt`返回选项的默认值。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpOptionLen`自变量无效。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAENOPROTOOPT**选项为未知或不受支持。 具体而言， **SO_BROADCAST**不支持的类型的套接字**SOCK_STREAM**，虽然**SO_ACCEPTCONN**， **SO_DONTLINGER**， **SO_KEEPALIVE**， **SO_LINGER**，和**SO_OOBINLINE**不支持在类型的套接字上**SOCK_DGRAM**。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 `GetSockOpt` 检索与任何状态中的任何类型的套接字关联的套接字选项的当前值并将存储中的结果`lpOptionValue`。 选项会影响套接字操作，如路由数据包，带外数据传输，依次类推。  
  
 支持以下选项`GetSockOpt`。 类型标识的类型的数据由`lpOptionValue`。 **TCP_NODELAY**选项使用级别**IPPROTO_TCP**; 所有其他选项使用级别**SOL_SOCKET**。  
  
|值|类型|含义|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|套接字正在侦听。|  
|**SO_BROADCAST**|**BOOL**|套接字广播消息的传输配置。|  
|**SO_DEBUG**|**BOOL**|启用调试。|  
|**SO_DONTLINGER**|**BOOL**|如果为 true， **SO_LINGER**选项处于禁用状态。|  
|**SO_DONTROUTE**|**BOOL**|路由处于禁用状态。|  
|**SO_ERROR**|`int`|检索错误状态并清除。|  
|**SO_KEEPALIVE**|**BOOL**|Keep-alive 将被发送。|  
|**SO_LINGER**|**结构延迟**|返回当前的延迟选项。|  
|**SO_OOBINLINE**|**BOOL**|带外数据正在接收正常数据流中。|  
|**SO_RCVBUF**|`int`|接收缓冲区大小。|  
|**SO_REUSEADDR**|**BOOL**|套接字可绑定到已在使用的地址。|  
|**SO_SNDBUF**|`int`|发送缓冲区大小。|  
|**SO_TYPE**|`int`|套接字的类型 (例如， **SOCK_STREAM**)。|  
|**TCP_NODELAY**|**BOOL**|为发送合并禁用 Nagle 算法。|  
  
 不支持的 Berkeley 软件分发 (BSD) 选项`GetSockOpt`是：  
  
|值|类型|含义|  
|-----------|----------|-------------|  
|**SO_RCVLOWAT**|`int`|接收低水位线。|  
|**SO_RCVTIMEO**|`int`|接收超时。|  
|**SO_SNDLOWAT**|`int`|发送低水位线。|  
|**SO_SNDTIMEO**|`int`|发送超时时。|  
|**IP_OPTIONS**||获取 IP 标头中的选项。|  
|**TCP_MAXSEG**|`int`|获取 TCP 最大的段大小。|  
  
 调用`GetSockOpt`的不受支持的选项将导致的错误代码为**WSAENOPROTOOPT**从重返回`GetLastError`。  
  
##  <a name="ioctl"></a>  CAsyncSocket::IOCtl  
 调用此成员函数可控制套接字的模式。  
  
```  
BOOL IOCtl(
    long lCommand,  
    DWORD* lpArgument);
```  
  
### <a name="parameters"></a>参数  
 `lCommand`  
 套接字上执行该命令。  
  
 `lpArgument`  
 指向参数的指针`lCommand`。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则通过调用检索 0 和特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEINVAL** `lCommand`不是一个有效命令，或`lpArgument`不是可接受参数`lCommand`，或该命令不是适用于该类型提供的套接字。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 可在任何状态的任何套接字上使用此例程。 它用于获取或检索与套接字，独立于协议和通信子系统关联的操作参数。 支持以下命令：  
  
- **FIONBIO**启用或禁用的套接字上的非锁定模式。 `lpArgument`参数指向`DWORD`，即如果非阻止模式下是启用则为非 0 和零如果它是被禁用。 如果`AsyncSelect`然后尝试使用已发出对套接字， **IOCtl**设置回阻止模式套接字将失败并**WSAEINVAL**。 若要设置回阻止模式套接字，并且允许**WSAEINVAL**错误，应用程序，必须先禁用`AsyncSelect`通过调用`AsyncSelect`与`lEvent`参数等于 0，然后调用**IOCtl**.  
  
- **FIONREAD**确定的最大可具有一个读取的字节数**接收**从此套接字调用。 `lpArgument`参数指向`DWORD`顺序**IOCtl**存储结果。 如果此套接字的类型是**SOCK_STREAM**， **FIONREAD**在单个返回的数据可以读取该总量**接收**; 这是通常的总量相同套接字上排队的数据。 如果此套接字的类型是**SOCK_DGRAM**， **FIONREAD**返回在套接字上排队的第一个数据报的大小。  
  
- **SIOCATMARK**确定是否已读取所有带外数据。 这仅适用于类型的套接字**SOCK_STREAM**已经配置为在行接收的任何带外数据 ( **SO_OOBINLINE**)。 如果没有带外数据正在等待读取，操作将返回非零。 否则它将返回 0，和下一页**接收**或`ReceiveFrom`上执行套接字将检索某些或所有前面"标记"的数据; 应用程序应使用**SIOCATMARK**操作确定是否保留了任何数据。 如果没有任何前面的"紧急"（带内） 数据的标准数据，它将按顺序接收它们。 (请注意，**接收**或`ReceiveFrom`将不能混合使用相同的调用中的带外和正常数据。)`lpArgument`参数指向`DWORD`顺序**IOCtl**存储结果。  
  
 此函数是的子集**ioctl()** 使用在 Berkeley 套接字。 具体而言，没有命令等效于**FIOASYNC**，虽然**SIOCATMARK**是支持的套接字仅级命令。  
  
##  <a name="listen"></a>  CAsyncSocket::Listen  
 调用此成员函数以侦听传入连接请求。  
  
```  
BOOL Listen(int nConnectionBacklog = 5);
```  
  
### <a name="parameters"></a>参数  
 *nConnectionBacklog*  
 挂起的连接的队列可以增长到的最大长度。 有效范围是从 1 到 5。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则通过调用检索 0 和特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEADDRINUSE**尝试侦听中使用的地址。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEINVAL**不通过绑定套接字**绑定**或已连接。  
  
- **WSAEISCONN**套接字已连接。  
  
- **WSAEMFILE**没有更多的文件描述符。  
  
- `WSAENOBUFS` 没有缓冲区空间不可用。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP**引用套接字不支持的类型属于`Listen`操作。  
  
### <a name="remarks"></a>备注  
 若要接受连接，套接字首次创建与**创建**，使用指定的传入连接的积压工作`Listen`，然后使用接受连接和**接受**。 `Listen` 仅适用于支持的连接，即的套接字类型的**SOCK_STREAM**。 此套接字被放入其中传入的连接是确认，队列由进程中的挂起接受"被动"模式。  
  
 由服务器 （或想要接受连接的任何应用程序） 通常使用此函数一次无法具有多个连接请求： 如果与完整队列中收到连接请求，客户端将收到一条含有相对值的指示**WSAECONNREFUSED**。  
  
 `Listen` 尝试继续无可用的端口 （描述符） 时理性作用。 它将接受连接，直到该队列为空。 如果端口变成可用状态，稍后调用`Listen`或**接受**将尽可能重填到当前或最新"积压工作，"队列并恢复侦听传入连接。  
  
##  <a name="m_hsocket"></a>  CAsyncSocket::m_hSocket  
 包含**套接字**句柄封装此套接字`CAsyncSocket`对象。  
  
```  
SOCKET m_hSocket;  
```  
  
##  <a name="onaccept"></a>  CAsyncSocket::OnAccept  
 由框架用于通知它可以通过调用接受挂起的连接请求的侦听套接字调用[接受](#accept)成员函数。  
  
```  
virtual void OnAccept(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 `nErrorCode`  
 套接字上最新的错误。 以下的错误代码适用于`OnAccept`成员函数：  
  
- **0**成功执行的函数。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[Windows 套接字： 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="onclose"></a>  CAsyncSocket::OnClose  
 由框架调用以通知此套接字其进程关闭连接的套接字。  
  
```  
virtual void OnClose(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 `nErrorCode`  
 套接字上最新的错误。 以下的错误代码应用于`OnClose`成员函数：  
  
- **0**成功执行的函数。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAECONNRESET**的远程端重置连接。  
  
- **WSAECONNABORTED**连接已中止由于超时或其他故障。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[Windows 套接字： 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="onconnect"></a>  CAsyncSocket::OnConnect  
 由框架调用以通知此连接的套接字完成其连接尝试是否成功或错误。  
  
```  
virtual void OnConnect(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 `nErrorCode`  
 套接字上最新的错误。 以下的错误代码应用于`OnConnect`成员函数：  
  
- **0**成功执行的函数。  
  
- **WSAEADDRINUSE**指定的地址已在使用。  
  
- **WSAEADDRNOTAVAIL**指定的地址不是可从本地计算机。  
  
- **WSAEAFNOSUPPORT**指定系列中的地址不能用于此套接字。  
  
- **WSAECONNREFUSED**强制拒绝连接尝试。  
  
- **WSAEDESTADDRREQ**目标地址是必需的。  
  
- **WSAEFAULT** `lpSockAddrLen`参数不正确。  
  
- **WSAEINVAL**套接字已绑定到一个地址。  
  
- **WSAEISCONN**套接字已连接。  
  
- **WSAEMFILE**没有更多的文件描述符。  
  
- **WSAENETUNREACH**网络无法在此时间到达从此主机。  
  
- `WSAENOBUFS` 没有缓冲区空间不可用。 无法连接套接字。  
  
- **WSAENOTCONN**套接字未连接。  
  
- **WSAENOTSOCK**描述符是文件，不的套接字。  
  
- **WSAETIMEDOUT**而无需建立连接，连接尝试操作已超时。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  在[CSocket](../../mfc/reference/csocket-class.md)、`OnConnect`在于： 绝不调用通知函数。 对于连接，你只需调用**连接**，这样就会返回完成连接后 （成功或错误）。 如何处理连接通知是 MFC 实现的详细信息。  
  
 有关详细信息，请参阅[Windows 套接字： 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]  
  
##  <a name="onoutofbanddata"></a>  CAsyncSocket::OnOutOfBandData  
 由框架调用以通知的接收套接字的发送套接字有要发送的带外数据。  
  
```  
virtual void OnOutOfBandData(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 `nErrorCode`  
 套接字上最新的错误。 以下的错误代码应用于`OnOutOfBandData`成员函数：  
  
- **0**成功执行的函数。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
### <a name="remarks"></a>备注  
 带外数据是在与每个对连接套接字的类型相关联的逻辑上独立于通道**SOCK_STREAM**。 通道通常用来发送紧急数据。  
  
 MFC 支持带外数据，但是，类的非用户`CAsyncSocket`我们建议您不要使用它。 更方便的方法是创建用于传递此类数据的第二个套接字。 有关带外数据的详细信息，请参阅[Windows 套接字： 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="onreceive"></a>  CAsyncSocket::OnReceive  
 由框架用于通知此套接字可通过调用检索缓冲区中没有数据调用**接收**成员函数。  
  
```  
virtual void OnReceive(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 `nErrorCode`  
 套接字上最新的错误。 以下的错误代码应用于`OnReceive`成员函数：  
  
- **0**成功执行的函数。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[Windows 套接字： 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]  
  
##  <a name="onsend"></a>  CAsyncSocket::OnSend  
 由框架用于通知的套接字，它现在可通过调用来发送数据调用**发送**成员函数。  
  
```  
virtual void OnSend(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 `nErrorCode`  
 套接字上最新的错误。 以下的错误代码应用于`OnSend`成员函数：  
  
- **0**成功执行的函数。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[Windows 套接字： 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]  
  
##  <a name="operator_eq"></a>  CAsyncSocket::operator =  
 将新值赋给`CAsyncSocket`对象。  
  
```  
void operator=(const CAsyncSocket& rSrc);
```  
  
### <a name="parameters"></a>参数  
 `rSrc`  
 对现有的引用`CAsyncSocket`对象。  
  
### <a name="remarks"></a>备注  
 调用此函数可将复制的现有`CAsyncSocket`到另一个对象`CAsyncSocket`对象。  
  
##  <a name="operator_socket"></a>  CAsyncSocket::operator 套接字  
 此运算符用于检索**套接字**的 handle`CAsyncSocket`对象。  
  
```  
operator SOCKET() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功的句柄**套接字**对象; 否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 句柄可用于直接调用 Windows Api。  
  
##  <a name="receive"></a>  CAsyncSocket::Receive  
 调用此成员函数以从套接字接收数据。  
  
```  
virtual int Receive(
    void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>参数  
 `lpBuf`  
 传入的数据缓冲区。  
  
 `nBufLen`  
 长度`lpBuf`以字节为单位。  
  
 `nFlags`  
 指定在其中进行调用的方法。 此函数的语义由套接字选项和`nFlags`参数。 后者通过组合构成的以下值的任何使用 c + +`OR`运算符：  
  
- **MSG_PEEK**扫视传入数据。 此数据复制到缓冲区，但不是会从输入队列中删除。  
  
- **MSG_OOB**处理带外数据。  
  
### <a name="return-value"></a>返回值  
 如果未发生错误，**接收**返回接收的字节数。 如果连接已关闭，则返回 0。 否则为值为**SOCKET_ERROR**返回，可以通过调用检索特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAENOTCONN**套接字未连接。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP MSG_OOB**已指定，但套接字的类型不是**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**套接字已关闭，但并不能调用**接收**后套接字上`ShutDown`已使用调用`nHow`设置为 0 或 2。  
  
- **WSAEWOULDBLOCK**套接字被标记为非阻止与**接收**操作将阻塞。  
  
- **WSAEMSGSIZE**数据报太大而无法放入指定的缓冲区，已被截断。  
  
- **WSAEINVAL**不通过绑定套接字**绑定**。  
  
- **WSAECONNABORTED**虚拟线路已由于超时或其他故障而中止。  
  
- **WSAECONNRESET**虚拟线路已重置远程端。  
  
### <a name="remarks"></a>备注  
 此函数用于连接的流或数据报套接字并用于读取传入数据。  
  
 类型的套接字**SOCK_STREAM**，如在返回多原样多大小所提供的缓冲区的当前可用的信息。 如果已为带外数据行中接收配置套接字 (套接字选项**SO_OOBINLINE**) 并且带外数据是未读，则将返回仅的带数据。 应用程序可以使用**IOCtlSIOCATMARK**选项或[OnOutOfBandData](#onoutofbanddata)以确定是否更的带保留了任何数据可供读取。  
  
 对于数据报套接字，从第一个排队数据报，直到达到所提供的缓冲区的大小被提取数据。 如果数据报大于所提供的缓冲区，与数据报的第一个部分填充了缓冲区，多余的数据将丢失，和**接收**返回的值**SOCKET_ERROR** ，错误代码设置为**WSAEMSGSIZE**。 如果没有传入的数据位于套接字，值为**SOCKET_ERROR**返回错误代码设置为与**WSAEWOULDBLOCK**。 [OnReceive](#onreceive)回调函数可以用于确定当更多数据到达时。  
  
 如果套接字的类型是**SOCK_STREAM** ，远程端已经正常，关闭连接**接收**将立即完成并接收的 0 字节数。 如果连接已被重置，**接收**将失败并出现错误**WSAECONNRESET**。  
  
 **接收**应该为每次仅一次调用[CAsyncSocket::OnReceive](#onreceive)调用。  
  
### <a name="example"></a>示例  
  请参阅示例[CAsyncSocket::OnReceive](#onreceive)。  
  
##  <a name="receivefrom"></a>  CAsyncSocket::ReceiveFrom  
 调用此成员函数来接收数据报和存储中的源地址[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构或在`rSocketAddress`。  
  
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
 `lpBuf`  
 传入的数据缓冲区。  
  
 `nBufLen`  
 长度`lpBuf`以字节为单位。  
  
 `rSocketAddress`  
 引用`CString`收到以点分隔的数字 IP 地址的对象。  
  
 `rSocketPort`  
 引用**UINT**存储一个端口。  
  
 `lpSockAddr`  
 指向的指针[SOCKADDR](../../mfc/reference/sockaddr-structure.md)保留后返回的源地址的结构。  
  
 `lpSockAddrLen`  
 中的源地址的长度的指针`lpSockAddr`以字节为单位。  
  
 `nFlags`  
 指定在其中进行调用的方法。 此函数的语义由套接字选项和`nFlags`参数。 后者通过组合构成的以下值的任何使用 c + +`OR`运算符：  
  
- **MSG_PEEK**扫视传入数据。 此数据复制到缓冲区，但不是会从输入队列中删除。  
  
- **MSG_OOB**处理带外数据。  
  
### <a name="return-value"></a>返回值  
 如果未发生错误，`ReceiveFrom`返回接收的字节数。 如果连接已关闭，则返回 0。 否则为值为**SOCKET_ERROR**返回，可以通过调用检索特定错误代码`GetLastError`。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpSockAddrLen`自变量无效：`lpSockAddr`缓冲区是否太小，无法容纳对等节点地址。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEINVAL**不通过绑定套接字**绑定**。  
  
- **WSAENOTCONN**套接字未连接 ( **SOCK_STREAM**仅)。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP MSG_OOB**已指定，但套接字的类型不是**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**套接字已关闭，但并不能调用`ReceiveFrom`后套接字上`ShutDown`已使用调用`nHow`设置为 0 或 2。  
  
- **WSAEWOULDBLOCK**套接字被标记为非阻止与`ReceiveFrom`操作将阻塞。  
  
- **WSAEMSGSIZE**数据报太大而无法放入指定的缓冲区，已被截断。  
  
- **WSAECONNABORTED**虚拟线路已由于超时或其他故障而中止。  
  
- **WSAECONNRESET**虚拟线路已重置远程端。  
  
### <a name="remarks"></a>备注  
 此函数用于读取传入数据 （可能是连接） 的套接字上和捕获从其发送数据的地址。  
  
 若要处理 IPv6 地址，使用[CAsyncSocket::ReceiveFromEx](#receivefromex)。  
  
 类型的套接字**SOCK_STREAM**，如在返回多原样多大小所提供的缓冲区的当前可用的信息。 如果已为带外数据行中接收配置套接字 (套接字选项**SO_OOBINLINE**) 并且带外数据是未读，则将返回仅的带数据。 应用程序可以使用**IOCtlSIOCATMARK**选项或`OnOutOfBandData`以确定是否更的带保留了任何数据可供读取。 `lpSockAddr`和`lpSockAddrLen`参数将被忽略的**SOCK_STREAM**套接字。  
  
 对于数据报套接字，从第一个排队数据报，直到达到所提供的缓冲区的大小被提取数据。 如果数据报大于所提供的缓冲区，与消息的第一个部分填充了缓冲区，多余的数据将丢失，和`ReceiveFrom`返回的值**SOCKET_ERROR** ，错误代码设置为**WSAEMSGSIZE**。  
  
 如果`lpSockAddr`不为零，且套接字的类型**SOCK_DGRAM**，套接字它发送数据的网络地址复制到相应[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构。 指向的值`lpSockAddrLen`初始化为此结构的大小和修改返回以指示存储在那里的地址的实际大小。 如果没有传入的数据是否可用在套接字，`ReceiveFrom`调用等待数据到达除非套接字是锁定。 在这种情况下，值为**SOCKET_ERROR**返回错误代码设置为与**WSAEWOULDBLOCK**。 `OnReceive`回调可以用于确定当更多数据到达时。  
  
 如果套接字的类型是**SOCK_STREAM** ，远程端已经正常，关闭连接`ReceiveFrom`将立即完成并接收的 0 字节数。  
  
##  <a name="receivefromex"></a>  CAsyncSocket::ReceiveFromEx  
 调用此成员函数来接收数据报和存储中的源地址[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构或在`rSocketAddress`（处理 IPv6 地址）。  
  
```  
int ReceiveFromEx(
    void* lpBuf,  
    int nBufLen,  
    CString& rSocketAddress,  
    UINT& rSocketPort,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>参数  
 `lpBuf`  
 传入的数据缓冲区。  
  
 `nBufLen`  
 长度`lpBuf`以字节为单位。  
  
 `rSocketAddress`  
 引用`CString`收到以点分隔的数字 IP 地址的对象。  
  
 `rSocketPort`  
 引用**UINT**存储一个端口。  
  
 `nFlags`  
 指定在其中进行调用的方法。 此函数的语义由套接字选项和`nFlags`参数。 后者通过组合构成的以下值的任何使用 c + +`OR`运算符：  
  
- **MSG_PEEK**扫视传入数据。 此数据复制到缓冲区，但不是会从输入队列中删除。  
  
- **MSG_OOB**处理带外数据。  
  
### <a name="return-value"></a>返回值  
 如果未发生错误，`ReceiveFromEx`返回接收的字节数。 如果连接已关闭，则返回 0。 否则为值为**SOCKET_ERROR**返回，可以通过调用检索特定错误代码`GetLastError`。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpSockAddrLen`自变量无效：`lpSockAddr`缓冲区是否太小，无法容纳对等节点地址。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEINVAL**不通过绑定套接字**绑定**。  
  
- **WSAENOTCONN**套接字未连接 ( **SOCK_STREAM**仅)。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP MSG_OOB**已指定，但套接字的类型不是**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**套接字已关闭，但并不能调用`ReceiveFromEx`后套接字上`ShutDown`已使用调用`nHow`设置为 0 或 2。  
  
- **WSAEWOULDBLOCK**套接字被标记为非阻止与`ReceiveFromEx`操作将阻塞。  
  
- **WSAEMSGSIZE**数据报太大而无法放入指定的缓冲区，已被截断。  
  
- **WSAECONNABORTED**虚拟线路已由于超时或其他故障而中止。  
  
- **WSAECONNRESET**虚拟线路已重置远程端。  
  
### <a name="remarks"></a>备注  
 此函数用于读取传入数据 （可能是连接） 的套接字上和捕获从其发送数据的地址。  
  
 此函数是与相同[CAsyncSocket::ReceiveFrom](#receivefrom) ，只不过它处理 IPv6 地址以及较旧的协议。  
  
 类型的套接字**SOCK_STREAM**，如在返回多原样多大小所提供的缓冲区的当前可用的信息。 如果已为带外数据行中接收配置套接字 (套接字选项**SO_OOBINLINE**) 并且带外数据是未读，则将返回仅的带数据。 应用程序可以使用**IOCtlSIOCATMARK**选项或`OnOutOfBandData`以确定是否更的带保留了任何数据可供读取。 `lpSockAddr`和`lpSockAddrLen`参数将被忽略的**SOCK_STREAM**套接字。  
  
 对于数据报套接字，从第一个排队数据报，直到达到所提供的缓冲区的大小被提取数据。 如果数据报大于所提供的缓冲区，与消息的第一个部分填充了缓冲区，多余的数据将丢失，和`ReceiveFromEx`返回的值**SOCKET_ERROR** ，错误代码设置为**WSAEMSGSIZE**。  
  
 如果`lpSockAddr`不为零，且套接字的类型**SOCK_DGRAM**，套接字它发送数据的网络地址复制到相应[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构。 指向的值`lpSockAddrLen`初始化为此结构的大小和修改返回以指示存储在那里的地址的实际大小。 如果没有传入的数据是否可用在套接字，`ReceiveFromEx`调用等待数据到达除非套接字是锁定。 在这种情况下，值为**SOCKET_ERROR**返回错误代码设置为与**WSAEWOULDBLOCK**。 `OnReceive`回调可以用于确定当更多数据到达时。  
  
 如果套接字的类型是**SOCK_STREAM** ，远程端已经正常，关闭连接`ReceiveFromEx`将立即完成并接收的 0 字节数。  
  
##  <a name="send"></a>  CAsyncSocket::Send  
 调用此成员函数以在连接的套接字上发送数据。  
  
```  
virtual int Send(
    const void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>参数  
 `lpBuf`  
 包含要传输的数据的缓冲区。  
  
 `nBufLen`  
 中的数据的长度`lpBuf`以字节为单位。  
  
 `nFlags`  
 指定在其中进行调用的方法。 此函数的语义由套接字选项和`nFlags`参数。 后者通过组合构成的以下值的任何使用 c + +`OR`运算符：  
  
- **MSG_DONTROUTE**指定数据应不会受到路由。 Windows 套接字供应商可以选择忽略此标志。  
  
- **MSG_OOB**将带外数据发送 ( **SOCK_STREAM**仅)。  
  
### <a name="return-value"></a>返回值  
 如果未发生错误，**发送**返回发送的字符的总数。 (请注意，这可以是由指示的数字小于`nBufLen`。)否则为值为**SOCKET_ERROR**返回，可以通过调用检索特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEACCES**请求的地址是广播的地址，但未设置相应的标志。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEFAULT** `lpBuf`自变量不是有效的用户地址空间的一部分。  
  
- **WSAENETRESET**必须重置连接，因为 Windows 套接字实现将其删除。  
  
- `WSAENOBUFS` Windows 套接字实现报告缓冲区死锁。  
  
- **WSAENOTCONN**套接字未连接。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP MSG_OOB**已指定，但套接字的类型不是**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**套接字已关闭，但并不能调用**发送**后套接字上`ShutDown`已使用调用`nHow`设置为 1 或 2。  
  
- **WSAEWOULDBLOCK**套接字被标记为非阻止和请求的操作会阻止。  
  
- **WSAEMSGSIZE**套接字属于类型**SOCK_DGRAM**，并且数据报大于支持的 Windows 套接字实现的最大。  
  
- **WSAEINVAL**不通过绑定套接字**绑定**。  
  
- **WSAECONNABORTED**虚拟线路已由于超时或其他故障而中止。  
  
- **WSAECONNRESET**虚拟线路已重置远程端。  
  
### <a name="remarks"></a>备注  
 **发送**用于写入连接的流或数据报套接字上的传出数据。 对于数据报套接字，必须小心不能超过最大的 IP 数据包大小的基础的子网，向其授予通过**iMaxUdpDg**中的元素[WSADATA](../../mfc/reference/wsadata-structure.md)结构返回`AfxSocketInit`。 如果数据太长，以原子方式通过基础协议，该错误**WSAEMSGSIZE**通过返回`GetLastError`，和不传输任何数据。  
  
 请注意，对于数据报套接字的成功完成**发送**不指示已成功传递数据。  
  
 上`CAsyncSocket`类型的对象**SOCK_STREAM**，写入的字节数可介于 1 和请求的长度，具体取决于在本地和外的主机上的缓冲区可用性。  
  
### <a name="example"></a>示例  
  请参阅示例[CAsyncSocket::OnSend](#onsend)。  
  
##  <a name="sendto"></a>  CAsyncSocket::SendTo  
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
 `lpBuf`  
 包含要传输的数据的缓冲区。  
  
 `nBufLen`  
 中的数据的长度`lpBuf`以字节为单位。  
  
 `nHostPort`  
 标识套接字应用程序的端口。  
  
 `lpszHostAddress`  
 此对象连接到的套接字的网络地址： 一个计算机名称，例如"ftp.microsoft.com，"或一个以点分隔的数字，如"128.56.22.8"。  
  
 `nFlags`  
 指定在其中进行调用的方法。 此函数的语义由套接字选项和`nFlags`参数。 后者通过组合构成的以下值的任何使用 c + +`OR`运算符：  
  
- **MSG_DONTROUTE**指定数据应不会受到路由。 Windows 套接字供应商可以选择忽略此标志。  
  
- **MSG_OOB**将带外数据发送 ( **SOCK_STREAM**仅)。  
  
 `lpSockAddr`  
 指向的指针[SOCKADDR](../../mfc/reference/sockaddr-structure.md)包含目标套接字地址结构。  
  
 `nSockAddrLen`  
 中的地址的长度`lpSockAddr`以字节为单位。  
  
### <a name="return-value"></a>返回值  
 如果未发生错误，`SendTo`返回发送的字符的总数。 (请注意，这可以是由指示的数字小于`nBufLen`。)否则为值为**SOCKET_ERROR**返回，可以通过调用检索特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEACCES**请求的地址是广播的地址，但未设置相应的标志。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEFAULT** `lpBuf`或`lpSockAddr`参数不是用户地址空间的一部分或`lpSockAddr`自变量是太小 (小于的大小[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构)。  
  
- **WSAEINVAL**的主机名无效。  
  
- **WSAENETRESET**必须重置连接，因为 Windows 套接字实现将其删除。  
  
- `WSAENOBUFS` Windows 套接字实现报告缓冲区死锁。  
  
- **WSAENOTCONN**套接字未连接 ( **SOCK_STREAM**仅)。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP MSG_OOB**已指定，但套接字的类型不是**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**套接字已关闭，但并不能调用`SendTo`后套接字上`ShutDown`已使用调用`nHow`设置为 1 或 2。  
  
- **WSAEWOULDBLOCK**套接字被标记为非阻止和请求的操作会阻止。  
  
- **WSAEMSGSIZE**套接字属于类型**SOCK_DGRAM**，并且数据报大于支持的 Windows 套接字实现的最大。  
  
- **WSAECONNABORTED**虚拟线路已由于超时或其他故障而中止。  
  
- **WSAECONNRESET**虚拟线路已重置远程端。  
  
- **WSAEADDRNOTAVAIL**指定的地址不是可从本地计算机。  
  
- **WSAEAFNOSUPPORT**指定系列中的地址不能用于此套接字。  
  
- **WSAEDESTADDRREQ**目标地址是必需的。  
  
- **WSAENETUNREACH**网络无法在此时间到达从此主机。  
  
### <a name="remarks"></a>备注  
 `SendTo` 在数据报或流套接字上使用，用于编写套接字上的传出数据。 对于数据报套接字，必须小心不能超过最大的 IP 数据包大小的基础的子网，向其授予通过**iMaxUdpDg**中的元素[WSADATA](../../mfc/reference/wsadata-structure.md)结构通过填写[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)。 如果数据太长，以原子方式通过基础协议，该错误**WSAEMSGSIZE**返回，并不传输任何数据。  
  
 请注意，成功完成`SendTo`不指示已成功传递数据。  
  
 `SendTo` 仅对使用**SOCK_DGRAM**将数据报发送到由标识的特定套接字的套接字`lpSockAddr`参数。  
  
 若要发送广播 (上**SOCK_DGRAM**仅) 中的地址`lpSockAddr`应使用专用的 IP 地址构造参数**INADDR_BROADCAST** （在 Windows 套接字标头中定义文件 WINSOCK。H） 一起使用的预期的端口号。 或者，如果`lpszHostAddress`参数是**NULL**，套接字配置广播。 通常建议不要对广播数据报超出其大小的碎片可以发生，这表明数据报 （不包括标头） 的数据部分不应超过 512 个字节。  
  
 若要处理 IPv6 地址，使用[CAsyncSocket::SendToEx](#sendtoex)。  
  
##  <a name="sendtoex"></a>  CAsyncSocket::SendToEx  
 调用此成员函数以将数据发送到特定目标 （句柄 IPv6 地址）。  
  
```  
int SendToEx(
    const void* lpBuf,  
    int nBufLen,  
    UINT nHostPort,  
    LPCTSTR lpszHostAddress = NULL,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>参数  
 `lpBuf`  
 包含要传输的数据的缓冲区。  
  
 `nBufLen`  
 中的数据的长度`lpBuf`以字节为单位。  
  
 `nHostPort`  
 标识套接字应用程序的端口。  
  
 `lpszHostAddress`  
 此对象连接到的套接字的网络地址： 一个计算机名称，例如"ftp.microsoft.com，"或一个以点分隔的数字，如"128.56.22.8"。  
  
 `nFlags`  
 指定在其中进行调用的方法。 此函数的语义由套接字选项和`nFlags`参数。 后者通过组合构成的以下值的任何使用 c + +`OR`运算符：  
  
- **MSG_DONTROUTE**指定数据应不会受到路由。 Windows 套接字供应商可以选择忽略此标志。  
  
- **MSG_OOB**将带外数据发送 ( **SOCK_STREAM**仅)。  
  
### <a name="return-value"></a>返回值  
 如果未发生错误，`SendToEx`返回发送的字符的总数。 (请注意，这可以是由指示的数字小于`nBufLen`。)否则为值为**SOCKET_ERROR**返回，可以通过调用检索特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEACCES**请求的地址是广播的地址，但未设置相应的标志。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEFAULT** `lpBuf`或`lpSockAddr`参数不是用户地址空间的一部分或`lpSockAddr`自变量是太小 (小于的大小[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构)。  
  
- **WSAEINVAL**的主机名无效。  
  
- **WSAENETRESET**必须重置连接，因为 Windows 套接字实现将其删除。  
  
- `WSAENOBUFS` Windows 套接字实现报告缓冲区死锁。  
  
- **WSAENOTCONN**套接字未连接 ( **SOCK_STREAM**仅)。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP MSG_OOB**已指定，但套接字的类型不是**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**套接字已关闭，但并不能调用`SendToEx`后套接字上`ShutDown`已使用调用`nHow`设置为 1 或 2。  
  
- **WSAEWOULDBLOCK**套接字被标记为非阻止和请求的操作会阻止。  
  
- **WSAEMSGSIZE**套接字属于类型**SOCK_DGRAM**，并且数据报大于支持的 Windows 套接字实现的最大。  
  
- **WSAECONNABORTED**虚拟线路已由于超时或其他故障而中止。  
  
- **WSAECONNRESET**虚拟线路已重置远程端。  
  
- **WSAEADDRNOTAVAIL**指定的地址不是可从本地计算机。  
  
- **WSAEAFNOSUPPORT**指定系列中的地址不能用于此套接字。  
  
- **WSAEDESTADDRREQ**目标地址是必需的。  
  
- **WSAENETUNREACH**网络无法在此时间到达从此主机。  
  
### <a name="remarks"></a>备注  
 此方法等同于[CAsyncSocket::SendTo](#sendto) ，只不过它处理 IPv6 地址以及较旧的协议。  
  
 `SendToEx` 在数据报或流套接字上使用，用于编写套接字上的传出数据。 对于数据报套接字，必须小心不能超过最大的 IP 数据包大小的基础的子网，向其授予通过**iMaxUdpDg**中的元素[WSADATA](../../mfc/reference/wsadata-structure.md)结构通过填写[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)。 如果数据太长，以原子方式通过基础协议，该错误**WSAEMSGSIZE**返回，并不传输任何数据。  
  
 请注意，成功完成`SendToEx`不指示已成功传递数据。  
  
 `SendToEx` 仅对使用**SOCK_DGRAM**将数据报发送到由标识的特定套接字的套接字`lpSockAddr`参数。  
  
 若要发送广播 (上**SOCK_DGRAM**仅) 中的地址`lpSockAddr`应使用专用的 IP 地址构造参数**INADDR_BROADCAST** （在 Windows 套接字标头中定义文件 WINSOCK。H） 一起使用的预期的端口号。 或者，如果`lpszHostAddress`参数是**NULL**，套接字配置广播。 通常建议不要对广播数据报超出其大小的碎片可以发生，这表明数据报 （不包括标头） 的数据部分不应超过 512 个字节。  
  
##  <a name="setsockopt"></a>  CAsyncSocket::SetSockOpt  
 调用此成员函数可设置套接字选项。  
  
```  
BOOL SetSockOpt(
    int nOptionName,  
    const void* lpOptionValue,  
    int nOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>参数  
 `nOptionName`  
 为其值是要设置套接字选项。  
  
 `lpOptionValue`  
 指向在其中提供请求的选项的值的缓冲区的指针。  
  
 `nOptionLen`  
 大小`lpOptionValue`以字节为单位的缓冲区。  
  
 `nLevel`  
 从该处选项定义; 级别仅支持级别**SOL_SOCKET**和**IPPROTO_TCP**。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则通过调用检索 0 和特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpOptionValue`不是有效的进程地址空间的一部分。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEINVAL** `nLevel`无效，或中的信息`lpOptionValue`无效。  
  
- **WSAENETRESET**连接超时时时**SO_KEEPALIVE**设置。  
  
- **WSAENOPROTOOPT**选项为未知或不受支持。 具体而言， **SO_BROADCAST**不支持的类型的套接字**SOCK_STREAM**，虽然**SO_DONTLINGER**， **SO_KEEPALIVE**， **SO_LINGER**，和**SO_OOBINLINE**不支持在类型的套接字上**SOCK_DGRAM**。  
  
- **WSAENOTCONN**连接已重置时**SO_KEEPALIVE**设置。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 `SetSockOpt` 设置与任何状态中的任何类型的套接字关联的套接字选项的当前值。 尽管选项可以在多个协议级别存在，但此规范仅定义存在的最顶部的"套接字"级别的选项。 选项会影响套接字操作，如是否加急的数据接收正常数据流中是否广播的消息可以发送的套接字上，依次类推。  
  
 有两种类型的套接字选项： 用于启用或禁用功能或行为，布尔选项以及需要的整数值或结构的选项。 若要启用布尔选项，`lpOptionValue`指向非零的整数。 若要禁用选项`lpOptionValue`指向等于零的整数。 `nOptionLen` 应该等于**sizeof(BOOL)** 布尔选项。 有关其他选项，`lpOptionValue`指向整数或结构，其中包含选项时，所需的值和`nOptionLen`是整数或结构的长度。  
  
 **SO_LINGER**时所采取的操作未发送的数据是否已排队插槽的控件和**关闭**函数调用以关闭套接字。  
  
 默认情况下，不能绑定套接字 (请参阅[绑定](#bind)) 到一个本地地址，这已在使用。 有时，但是，它可能需要进行"重新使用"以这种方式的地址。 由于通过本地和远程地址的组合唯一标识每个连接，因此不使用具有绑定到相同的本地地址，前提是远程地址是不同的两个套接字没问题。  
  
 以通知 Windows 套接字实现的**绑定**应不允许在套接字上的调用，因为所需的地址已在使用另一个套接字，应用程序应设置**SO_REUSEADDR**套接字的套接字选项发出之前**绑定**调用。 请注意，选项仅在时解释**绑定**调用： 因此非常必要 （且无害） 设置即无法绑定到现有地址，套接字上的选项和设置或重置后的选项**绑定**调用具有对此没有影响或任何其他套接字。  
  
 应用程序可以请求 Windows 套接字实现通过打开启用"保持活动状态"上的数据包的传输控制协议 (TCP) 连接使用**SO_KEEPALIVE**套接字选项。 Windows 套接字实现不需要支持使用 keep-alive： 如果是这样，特定于实现精确的语义，但应符合 4.2.3.6 的 RFC 1122:"Internet 主机要求-通信层。" 如果删除连接"keep-alive"的结果为错误代码**WSAENETRESET**套接字，返回的任何正在进行的调用，任何后续调用将失败并**WSAENOTCONN**。  
  
 **TCP_NODELAY**选项禁用 Nagle 算法。 使用 Nagle 算法以减少缓冲未确认的发送数据，直到可以发送一个完全尺寸的数据包发送由主机的小型数据包数。 但是，对于某些应用程序此算法将会降低性能，和**TCP_NODELAY**可用来将其关闭。 应用程序编写器不应设置**TCP_NODELAY**除非这样的影响是易于理解和所需的因为设置**TCP_NODELAY**可以对网络性能产生严重的负面影响. **TCP_NODELAY**是唯一支持的套接字选项使用级别**IPPROTO_TCP**; 所有其他选项使用级别**SOL_SOCKET**。  
  
 Windows 套接字提供某些实现输出调试信息，如果**SO_DEBUG**应用程序设置选项。  
  
 支持以下选项`SetSockOpt`。 类型标识的类型的数据由`lpOptionValue`。  
  
|值|类型|含义|  
|-----------|----------|-------------|  
|**SO_BROADCAST**|**BOOL**|允许广播消息的套接字上的传输。|  
|**SO_DEBUG**|**BOOL**|记录调试信息。|  
|**SO_DONTLINGER**|**BOOL**|不阻止**关闭**等待发送的未发送数据。 设置此选项等效于设置**SO_LINGER**与**l_onoff**设置为零。|  
|**SO_DONTROUTE**|**BOOL**|不路由： 直接向接口发送。|  
|**SO_KEEPALIVE**|**BOOL**|发送 keep-alive。|  
|**SO_LINGER**|**结构延迟**|Linger**关闭**如果未发送的数据是否存在。|  
|**SO_OOBINLINE**|**BOOL**|接收正常数据流中的带外数据。|  
|**SO_RCVBUF**|`int`|指定的缓冲区大小接收。|  
|**SO_REUSEADDR**|**BOOL**|允许将套接字绑定到已在使用的地址。 (请参阅[绑定](#bind)。)|  
|**SO_SNDBUF**|`int`|指定发送的缓冲区大小。|  
|**TCP_NODELAY**|**BOOL**|为发送合并禁用 Nagle 算法。|  
  
 不支持的 Berkeley 软件分发 (BSD) 选项`SetSockOpt`是：  
  
|值|类型|含义|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|侦听套接字|  
|**SO_ERROR**|`int`|获取错误状态并清除。|  
|**SO_RCVLOWAT**|`int`|接收低水位线。|  
|**SO_RCVTIMEO**|`int`|接收超时|  
|**SO_SNDLOWAT**|`int`|发送低水位线。|  
|**SO_SNDTIMEO**|`int`|发送超时时。|  
|**SO_TYPE**|`int`|套接字的类型。|  
|**IP_OPTIONS**||将选项字段设置 IP 标头中。|  
  
##  <a name="shutdown"></a>  CAsyncSocket::ShutDown  
 调用此成员函数以禁用发送，接收，或同时在对套接字。  
  
```  
BOOL ShutDown(int nHow = sends);
```  
  
### <a name="parameters"></a>参数  
 `nHow`  
 一个标志，用于描述哪些类型的操作将不再允许，使用下列枚举的值：  
  
- **接收 = 0**  
  
- **发送 = 1**  
  
- **同时 = 2**  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则通过调用检索 0 和特定错误代码[GetLastError](#getlasterror)。 对此成员函数应用了以下错误：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须在使用此 API 之前发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEINVAL** `nHow`无效。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAENOTCONN**套接字未连接 ( **SOCK_STREAM**仅)。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 `ShutDown` 用于在所有类型的套接字上禁用接收、 传输，或这两者。 如果`nHow`为 0，在上的后续接收套接字将不允许。 这在较低的协议层上无效。  
  
 有关传输控制协议 (TCP) 中，TCP 窗口不会更改并且传入的数据将会接受 （但不是确认），直到用完窗口。 有关用户数据报协议 (UDP) 中，传入数据报接受并排队。 将在任何情况下生成 ICMP 错误数据包。 如果`nHow`为 1，后续发送不允许。 对于 TCP 套接字中，将发送 FIN。 设置`nHow`为 2 同时禁用发送和接收上文所述。  
  
 请注意，`ShutDown`不关闭套接字执行，并附加到套接字的资源不会被释放之前**关闭**调用。 应用程序不应依赖于能够重复使用套接字之后它已关闭。 具体而言，Windows 套接字实现不需要支持使用**连接**此类套接字上。  
  
### <a name="example"></a>示例  
  请参阅示例[CAsyncSocket::OnReceive](#onreceive)。  
  
##  <a name="socket"></a>  CASyncSocket::Socket  
 分配套接字句柄。  
  
```  
BOOL Socket(
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    int nProtocolType = 0,  
    int nAddressFormat = PF_INET);
```  
  
### <a name="parameters"></a>参数  
 `nSocketType`  
 指定`SOCK_STREAM`或`SOCK_DGRAM`。  
  
 `lEvent`  
 一个位掩码，指定应用程序感兴趣的网络事件的组合。  
  
- `FD_READ`： 想要接收通知以进行读取的准备情况。  
  
- `FD_WRITE`： 想要接收通知以进行写入的准备情况。  
  
- `FD_OOB`： 想要接收的带外数据到达的通知。  
  
- `FD_ACCEPT`： 想要接收通知的传入连接。  
  
- `FD_CONNECT`： 想要接收已完成的连接的通知。  
  
- `FD_CLOSE`： 想要接收通知的套接字闭包。  
  
 `nProtocolType`  
 要用于特定于指示的地址系列的套接字的协议。  
  
 `nAddressFormat`  
 地址系列规范。  
  
### <a name="return-value"></a>返回值  
 成功时返回 `TRUE`，失败时返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法分配的套接字句柄。 它不会调用[CAsyncSocket::Bind](#bind)将套接字绑定到指定的地址，以使你需要调用`Bind`更高版本才能将套接字绑定到指定的地址。 你可以使用[CAsyncSocket::SetSockOpt](#setsockopt)之前会将其绑定设置套接字选项。  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CSocket 类](../../mfc/reference/csocket-class.md)   
 [CSocketFile 类](../../mfc/reference/csocketfile-class.md)
