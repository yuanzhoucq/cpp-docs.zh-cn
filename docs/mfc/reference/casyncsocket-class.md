---
title: CAsyncSocket 类 |Microsoft Docs
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
ms.openlocfilehash: c74bc6a134ea31f3184912192ccbcb3908e64cd3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221520"
---
# <a name="casyncsocket-class"></a>CAsyncSocket 类
表示 Windows 套接字 — 网络通信的终结点。  
  
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
|[CAsyncSocket::Attach](#attach)|将附加的套接字句柄`CAsyncSocket`对象。|  
|[CAsyncSocket::Bind](#bind)|将与套接字关联的本地地址。|  
|[CAsyncSocket::Close](#close)|关闭套接字。|  
|[CAsyncSocket::Connect](#connect)|建立到对等的套接字连接。|  
|[CAsyncSocket::Create](#create)|创建的套接字。|  
|[CAsyncSocket::Detach](#detach)|分离套接字句柄从`CAsyncSocket`对象。|  
|[CAsyncSocket::FromHandle](#fromhandle)|返回一个指向`CAsyncSocket`给定 socket 句柄的对象。|  
|[CAsyncSocket::GetLastError](#getlasterror)|获取失败的最后一个操作的错误状态。|  
|[CAsyncSocket::GetPeerName](#getpeername)|获取对等方套接字的套接字连接到的地址。|  
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|获取到套接字的连接 （句柄 IPv6 地址） 的对等方套接字地址。|  
|[CAsyncSocket::GetSockName](#getsockname)|获取一个套接字的本地名称。|  
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|获取套接字 （句柄 IPv6 地址） 的本地名称。|  
|[CAsyncSocket::GetSockOpt](#getsockopt)|检索套接字选项。|  
|[CAsyncSocket::IOCtl](#ioctl)|控制套接字的模式。|  
|[CAsyncSocket::Listen](#listen)|建立套接字以侦听传入连接请求。|  
|[CAsyncSocket::Receive](#receive)|从套接字接收数据。|  
|[CAsyncSocket::ReceiveFrom](#receivefrom)|接收数据报并存储的源地址。|  
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|接收数据报并存储源地址 （句柄 IPv6 地址）。|  
|[CAsyncSocket::Send](#send)|将数据发送到连接的套接字。|  
|[CAsyncSocket::SendTo](#sendto)|将数据发送到特定目标。|  
|[CAsyncSocket::SendToEx](#sendtoex)|将数据发送到特定目标 （句柄 IPv6 地址）。|  
|[CAsyncSocket::SetSockOpt](#setsockopt)|设置套接字选项。|  
|[CAsyncSocket::ShutDown](#shutdown)|禁用`Send`和/或`Receive`套接字上调用。|  
|[CASyncSocket::Socket](#socket)|分配一个套接字句柄。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAsyncSocket::OnAccept](#onaccept)|通知可通过调用接受挂起的连接请求的侦听套接字`Accept`。|  
|[CAsyncSocket::OnClose](#onclose)|通知套接字连接到它的套接字已关闭。|  
|[CAsyncSocket::OnConnect](#onconnect)|通知连接的套接字连接尝试是否已完成，已成功或错误。|  
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|通知的接收套接字，没有要读取套接字通常紧急邮件上的带外数据。|  
|[CAsyncSocket::OnReceive](#onreceive)|没有要调用来检索数据时通知侦听套接字`Receive`。|  
|[CAsyncSocket::OnSend](#onsend)|通知套接字，它可以将数据发送通过调用`Send`。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CAsyncSocket::operator =](#operator_eq)|将一个新值赋给`CAsyncSocket`对象。|  
|[CAsyncSocket::operator 套接字](#operator_socket)|使用此运算符将检索的套接字句柄`CAsyncSocket`对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CAsyncSocket::m_hSocket](#m_hsocket)|表示附加到此套接字句柄`CAsyncSocket`对象。|  
  
## <a name="remarks"></a>备注  
 类`CAsyncSocket`封装 Windows 套接字函数 API，编程人员想要使用 Windows 套接字与 MFC 一起提供的面向对象的抽象。  
  
 此类基于了解网络通信的假设。 您是负责处理阻塞，字节顺序差异，并 Unicode 和多字节字符之间的转换设置 (MBCS) 字符串。 如果你想更方便的界面，用于为你管理这些问题，请参阅类[CSocket](../../mfc/reference/csocket-class.md)。  
  
 若要使用`CAsyncSocket`对象，请调用其构造函数，然后调用[创建](#create)函数来创建基础套接字句柄 (类型`SOCKET`)，除非在接受套接字上。 为服务器套接字调用[侦听](#listen)成员函数，并为客户端套接字调用[Connect](#connect)成员函数。 应调用服务器套接字[接受](#accept)收到连接请求的函数。 使用剩余`CAsyncSocket`函数来执行套接字之间的通信。 完成后，销毁`CAsyncSocket`对象，如果它在堆上创建; 析构函数自动调用[关闭](#close)函数。 套接字的数据类型本文所述[Windows 套接字： 背景](../../mfc/windows-sockets-background.md)。  
  
> [!NOTE]
>  在静态链接的 MFC 应用程序中的辅助线程中使用 MFC 套接字时，您必须在使用套接字的每个线程中调用 `AfxSocketInit` 来初始化套接字库。 默认情况下，仅在主线程中调用 `AfxSocketInit`。  
  
 有关详细信息，请参阅[Windows 套接字： 使用类 CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md)和相关文章。，又能[Windows Sockets 2 API](/windows/desktop/WinSock/windows-sockets-start-page-2)。  
  
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
 *rConnectedSocket*  
 标识可用于连接的新套接字的引用。  
  
 *lpSockAddr*  
 一个指向[SOCKADDR](../../mfc/reference/sockaddr-structure.md)套接字接收连接的地址的结构，因为识别在网络上。 确切格式*lpSockAddr*参数由时创建套接字时建立的地址族。 如果*lpSockAddr*和/或*lpSockAddrLen*均为 NULL，则返回的已接受的套接字的远程地址信息。  
  
 *lpSockAddrLen*  
 中的地址的长度的指针*lpSockAddr*以字节为单位。 *LpSockAddrLen*是值结果参数： 最初，它应包含指向的空间量*lpSockAddr*; 返回时它将包含返回的地址的实际长度 （以字节为单位）。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则通过调用检索 0 和特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEFAULT *lpSockAddrLen*自变量是太小 (小于的大小[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构)。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字调用正在进行中。  
  
- WSAEINVAL`Listen`未被调用的之前接受。  
  
- WSAEMFILE 队列为空以接受在输入时，提供了不到描述符。  
  
- WSAENOBUFS 无缓冲区空间不可用。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
- WSAEOPNOTSUPP 引用套接字不支持面向连接的服务的类型。  
  
- WSAEWOULDBLOCK 套接字被标记为非阻止性且没有任何连接都存在要接受的。  
  
### <a name="remarks"></a>备注  
 此例程提取挂起连接队列中的第一个连接，使用与此套接字，相同的属性创建新的套接字和将其附加到*rConnectedSocket*。 如果没有挂起的连接在队列中，存在`Accept`将返回零和`GetLastError`返回错误。 已接受的套接字 ( *rConnectedSocket)* 不能用来接受更多连接。 原始套接字将保持打开且正在侦听。  
  
 自变量*lpSockAddr*是填充的连接套接字地址的结果参数，因为识别通信层。 `Accept` 用于如 SOCK_STREAM 基于连接的套接字类型。  
  
##  <a name="asyncselect"></a>  CAsyncSocket::AsyncSelect  
 调用此成员函数以请求为套接字的事件通知。  
  
```  
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>参数  
 *lEvent*  
 一个位掩码，它指定在其中所关注的应用程序的网络事件的组合。  
  
- FD_READ 想要接收通知的准备情况进行读取。  
  
- FD_WRITE 想要接收通知，可用于读取数据时。  
  
- FD_OOB 想要接收的带外数据到达的通知。  
  
- FD_ACCEPT 想要接收传入连接的通知。  
  
- FD_CONNECT 想要接收通知的连接结果。  
  
- FD_CLOSE 想要对等方已关闭套接字时接收通知。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则通过调用检索 0 和特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEINVAL 指示指定的参数之一无效。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字操作正在进行。  
  
### <a name="remarks"></a>备注  
 此函数用于指定哪些 MFC 回调通知函数将调用为套接字。 `AsyncSelect` 自动设置为非阻止模式下的此套接字。 有关详细信息，请参阅文章[Windows 套接字： 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="attach"></a>  CAsyncSocket::Attach  
 调用此成员函数可将附加*hSocket*句柄`CAsyncSocket`对象。  
  
```  
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>参数  
 *hSocket*  
 包含一个套接字的句柄。  
  
 *lEvent*  
 一个位掩码，它指定在其中所关注的应用程序的网络事件的组合。  
  
- FD_READ 想要接收通知的准备情况进行读取。  
  
- FD_WRITE 想要接收通知，可用于读取数据时。  
  
- FD_OOB 想要接收的带外数据到达的通知。  
  
- FD_ACCEPT 想要接收传入连接的通知。  
  
- FD_CONNECT 想要接收通知的连接结果。  
  
- FD_CLOSE 想要对等方已关闭套接字时接收通知。  
  
### <a name="return-value"></a>返回值  
 如果函数运行成功，则为非零。  
  
### <a name="remarks"></a>备注  
 SOCKET 句柄存储在对象的[m_hSocket](#m_hsocket)数据成员。  
  
##  <a name="bind"></a>  CAsyncSocket::Bind  
 调用此成员函数以将本地地址与套接字相关联。  
  
```  
BOOL Bind(
    UINT nSocketPort,  
    LPCTSTR lpszSocketAddress = NULL);

 
BOOL Bind (
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>参数  
 *nSocketPort*  
 用于标识套接字应用程序端口。  
  
 *lpszSocketAddress*  
 网络地址，例如"128.56.22.8"点分数字。 此参数指示将 NULL 传递字符串`CAsyncSocket`实例应侦听的所有网络接口上的客户端活动。  
  
 *lpSockAddr*  
 一个指向[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构，其中包含要分配给此套接字地址。  
  
 *nSockAddrLen*  
 中的地址的长度*lpSockAddr*以字节为单位。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则通过调用检索 0 和特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEADDRINUSE 指定的地址已在使用中。 (请参阅下的 SO_REUSEADDR 套接字选项[SetSockOpt](#setsockopt)。)  
  
- WSAEFAULT *nSockAddrLen*自变量是太小 (小于的大小[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构)。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字调用正在进行中。  
  
- 此端口不支持 WSAEAFNOSUPPORT 指定的地址族。  
  
- WSAEINVAL 套接字已绑定到一个地址。  
  
- 不 WSAENOBUFS 足够放入缓冲区可用，过多连接。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 之前未连接的数据报或流套接字上使用此例程后续`Connect`或`Listen`调用。 它可以接受连接请求之前，侦听服务器套接字必须选择一个端口号，并将它已知 Windows 套接字到通过调用`Bind`。 `Bind` 通过将本地名称分配给未命名的套接字建立套接字的本地关联 （主机地址/端口号）。  
  
##  <a name="casyncsocket"></a>  CAsyncSocket::CAsyncSocket  
 构造一个空的套接字对象。  
  
```  
CAsyncSocket();
```  
  
### <a name="remarks"></a>备注  
 构造对象之后, 必须调用其`Create`成员函数以创建套接字数据结构并将其地址绑定。 (在服务器端的 Windows 套接字通信，当侦听套接字创建要在中使用的套接字`Accept`调用时，不要调用`Create`的套接字。)  
  
##  <a name="close"></a>  CAsyncSocket::Close  
 关闭套接字。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 此函数，以便进一步对它的引用将失败并出现错误 WSAENOTSOCK 释放套接字描述符。 如果这是对基础套接字的最后一个引用，则放弃相关联的命名信息和排队的数据。 套接字对象的析构函数调用`Close`为您。  
  
 有关`CAsyncSocket`，而不是`CSocket`的语义`Close`受 SO_LINGER 和 SO_DONTLINGER 的套接字选项。 有关详细信息，请参阅成员函数`GetSockOpt`。  
  
##  <a name="connect"></a>  CAsyncSocket::Connect  
 调用此成员函数以建立与未连接的流或数据报套接字连接。  
  
```  
BOOL Connect(
    LPCTSTR lpszHostAddress,  
    UINT nHostPort);

 
BOOL Connect(
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>参数  
 *lpszHostAddress*  
 此对象连接的套接字的网络地址： 例如"ftp.microsoft.com"或一个以点分隔的数字，如"128.56.22.8"的计算机的名称。  
  
 *nHostPort*  
 用于标识套接字应用程序端口。  
  
 *lpSockAddr*  
 一个指向[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构，其中包含连接的套接字的地址。  
  
 *nSockAddrLen*  
 中的地址的长度*lpSockAddr*以字节为单位。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则通过调用检索 0 和特定的错误代码[GetLastError](#getlasterror)。 这指示的错误代码为 WSAEWOULDBLOCK，并且你的应用程序正在使用的可重写回叫，如果你的应用程序将收到`OnConnect`消息连接操作完成时。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEADDRINUSE 指定的地址已在使用中。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字调用正在进行中。  
  
- WSAEADDRNOTAVAIL 指定的地址不是可从本地计算机。  
  
- 指定系列中的 WSAEAFNOSUPPORT 地址不能用于此套接字。  
  
- WSAECONNREFUSED 连接尝试被拒绝。  
  
- WSAEDESTADDRREQ 一个目标地址是必需的。  
  
- WSAEFAULT *nSockAddrLen*参数不正确。  
  
- WSAEINVAL 无效主机地址。  
  
- WSAEISCONN 套接字已连接。  
  
- WSAEMFILE 否提供了更多的文件描述符。  
  
- WSAENETUNREACH 网络不能将从此主机访问这一次。  
  
- WSAENOBUFS 无缓冲区空间不可用。 不能连接套接字。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
- WSAETIMEDOUT 连接尝试超时而无需建立连接。  
  
- WSAEWOULDBLOCK 套接字被标记为非阻止性和不能立即完成连接。  
  
### <a name="remarks"></a>备注  
 如果套接字是未绑定、 唯一值分配给本地关联系统，和套接字被标记为绑定。 请注意，如果名称结构的地址字段是全部为零，`Connect`将返回零。 若要获得扩展错误信息，请调用`GetLastError`成员函数。  
  
 对于流套接字 （类型为 SOCK_STREAM），到外主机启动的活动连接。 套接字调用成功完成后，套接字已准备好发送/接收数据。  
  
 对于数据报套接字 （类型为 SOCK_DGRAM），默认目标设置，其将使用在后续`Send`和`Receive`调用。  
  
##  <a name="create"></a>  CAsyncSocket::Create  
 调用`Create`成员函数之后，构造一个套接字对象来创建 Windows 套接字并将其附加。  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>参数  
 *nSocketPort*  
 如果您希望 Windows 套接字，若要选择的端口套接字，则为 0 与一起使用的已知端口。  
  
 *nSocketType*  
 SOCK_STREAM 或 SOCK_DGRAM。  
  
 *lEvent*  
 一个位掩码，它指定在其中所关注的应用程序的网络事件的组合。  
  
- FD_READ 想要接收通知的准备情况进行读取。  
  
- FD_WRITE 想要接收通知以进行写入的准备情况。  
  
- FD_OOB 想要接收的带外数据到达的通知。  
  
- FD_ACCEPT 想要接收传入连接的通知。  
  
- FD_CONNECT 想要接收通知的已完成的连接。  
  
- FD_CLOSE 想要接收的套接字关闭通知。  
  
 *lpszSockAddress*  
 指向一个包含连接的套接字，一个以点分隔的数字，如"128.56.22.8"的网络地址的字符串的指针。此参数指示将 NULL 传递字符串`CAsyncSocket`实例应侦听的所有网络接口上的客户端活动。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则通过调用检索 0 和特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- 不支持指定的地址族 WSAEAFNOSUPPORT。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字操作正在进行。  
  
- WSAEMFILE 否提供了更多的文件描述符。  
  
- WSAENOBUFS 无缓冲区空间不可用。 无法创建套接字。  
  
- 不支持 WSAEPROTONOSUPPORT 指定的端口。  
  
- WSAEPROTOTYPE 指定的端口是此套接字的错误类型。  
  
- 此地址族中不支持 WSAESOCKTNOSUPPORT 指定套接字类型。  
  
### <a name="remarks"></a>备注  
 `Create` 调用[套接字](#socket)如果成功，它将调用[绑定](#bind)将套接字绑定到指定的地址。 支持以下的套接字类型：  
  
- SOCK_STREAM 提供序列化，可靠、 全双工、 基于连接的字节流。 使用传输控制协议 (TCP) 进行 Internet 地址族。  
  
- SOCK_DGRAM 支持数据报，即是无连接不可靠的数据包的固定 （通常很小） 的最大长度。 使用用户数据报协议 (UDP) 为 Internet 地址族。  
  
    > [!NOTE]
    >  `Accept`成员函数将一个新的空引用`CSocket`对象作为其参数。 在调用之前，必须构造此对象`Accept`。 请记住，如果此套接字对象超出范围，该连接将关闭。 不要调用`Create`此新的套接字对象。  
  
> [!IMPORTANT]
> `Create` 是**不**线程安全。  如果你正在调用它在多线程环境中它可以调用的同时由不同的线程，请务必保护使用互斥体或其他同步锁的每个调用。  
  
 有关流和数据报套接字的详细信息，请参阅文章[Windows 套接字： 背景](../../mfc/windows-sockets-background.md)并[Windows 套接字： 端口和套接字地址](../../mfc/windows-sockets-ports-and-socket-addresses.md)和[Windows Sockets 2 API](/windows/desktop/WinSock/windows-sockets-start-page-2).  
  
##  <a name="detach"></a>  CAsyncSocket::Detach  
 调用此成员函数可分离在 SOCKET 句柄*m_hSocket*中的数据成员`CAsyncSocket`对象，并将*m_hSocket*为 NULL。  
  
```  
SOCKET Detach();
```  
  
##  <a name="fromhandle"></a>  CAsyncSocket::FromHandle  
 返回一个指向`CAsyncSocket`对象。  
  
```  
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```  
  
### <a name="parameters"></a>参数  
 *hSocket*  
 包含一个套接字的句柄。  
  
### <a name="return-value"></a>返回值  
 一个指向`CAsyncSocket`对象，或者如果没有，则为 NULL 没有`CAsyncSocket`对象附加到*hSocket*。  
  
### <a name="remarks"></a>备注  
 如果给定的套接字的句柄，如果`CAsyncSocket`对象未附加到该句柄，则成员函数返回 NULL。  
  
##  <a name="getlasterror"></a>  CAsyncSocket::GetLastError  
 调用此成员函数以获取失败的最后一个操作的错误状态。  
  
```  
static int PASCAL GetLastError();
```  
  
### <a name="return-value"></a>返回值  
 返回值指示此线程执行的最后一个 Windows 套接字 API 例程的错误代码。  
  
### <a name="remarks"></a>备注  
 当某个特定成员函数指示已发生错误，`GetLastError`应调用以检索相应的错误代码。 请参阅适用的错误代码的单个成员函数说明的列表。  
  
 有关错误代码的详细信息，请参阅[Windows Sockets 2 API](/windows/desktop/WinSock/windows-sockets-start-page-2)。  
  
##  <a name="getpeername"></a>  CAsyncSocket::GetPeerName  
 调用此成员函数以获取此套接字连接到的对等方套接字地址。  
  
```  
BOOL GetPeerName(
    CString& rPeerAddress,  
    UINT& rPeerPort);

 
BOOL GetPeerName(
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen);
```  
  
### <a name="parameters"></a>参数  
 *rPeerAddress*  
 引用`CString`对象，它接收的以点分隔的数字 IP 地址。  
  
 *rPeerPort*  
 对将存储一个端口是 UINT 引用。  
  
 *lpSockAddr*  
 一个指向[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构，它接收的对等方套接字的名称。  
  
 *lpSockAddrLen*  
 中的地址的长度的指针*lpSockAddr*以字节为单位。 返回时， *lpSockAddrLen*参数中包含的实际大小*lpSockAddr*返回以字节为单位。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则通过调用检索 0 和特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEFAULT *lpSockAddrLen*参数不是足够大。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字调用正在进行中。  
  
- WSAENOTCONN 套接字未连接。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 若要处理 IPv6 地址，请使用[CAsyncSocket::GetPeerNameEx](#getpeernameex)。  
  
##  <a name="getpeernameex"></a>  CAsyncSocket::GetPeerNameEx  
 调用此成员函数以获取到此套接字的连接 （句柄 IPv6 地址） 的对等方套接字地址。  
  
```  
BOOL GetPeerNameEx(
    CString& rPeerAddress,  
    UINT& rPeerPort);
```  
  
### <a name="parameters"></a>参数  
 *rPeerAddress*  
 引用`CString`对象，它接收的以点分隔的数字 IP 地址。  
  
 *rPeerPort*  
 对将存储一个端口是 UINT 引用。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则通过调用检索 0 和特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEFAULT *lpSockAddrLen*参数不是足够大。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字调用正在进行中。  
  
- WSAENOTCONN 套接字未连接。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 此函数等同于[CAsyncSocket::GetPeerName](#getpeername) ，只不过它处理 IPv6 地址也较旧的协议。  
  
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
 *rSocketAddress*  
 引用`CString`对象，它接收的以点分隔的数字 IP 地址。  
  
 *rSocketPort*  
 对将存储一个端口是 UINT 引用。  
  
 *lpSockAddr*  
 一个指向[SOCKADDR](../../mfc/reference/sockaddr-structure.md)接收套接字地址的结构。  
  
 *lpSockAddrLen*  
 中的地址的长度的指针*lpSockAddr*以字节为单位。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则通过调用检索 0 和特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEFAULT *lpSockAddrLen*参数不是足够大。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字操作正在进行。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
- 套接字不已绑定到包含的地址 WSAEINVAL `Bind`。  
  
### <a name="remarks"></a>备注  
 此调用时尤其有用`Connect`已调用而无需这样做`Bind`第一次; 此调用将提供可以确定由系统设置的本地关联的唯一方法。  
  
 若要处理 IPv6 地址，请使用[CAsyncSocket::GetSockNameEx](#getsocknameex)  
  
##  <a name="getsocknameex"></a>  CAsyncSocket::GetSockNameEx  
 调用此成员函数可获取套接字 （句柄 IPv6 地址） 的本地名称。  
  
```  
BOOL GetSockNameEx(
    CString& rSocketAddress,  
    UINT& rSocketPort);
```  
  
### <a name="parameters"></a>参数  
 *rSocketAddress*  
 引用`CString`对象，它接收的以点分隔的数字 IP 地址。  
  
 *rSocketPort*  
 对将存储一个端口是 UINT 引用。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则通过调用检索 0 和特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEFAULT *lpSockAddrLen*参数不是足够大。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字操作正在进行。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
- 套接字不已绑定到包含的地址 WSAEINVAL `Bind`。  
  
### <a name="remarks"></a>备注  
 此调用是相同[CAsyncSocket::GetSockName](#getsockname) ，只不过它处理 IPv6 地址也较旧的协议。  
  
 此调用时尤其有用`Connect`已调用而无需这样做`Bind`第一次; 此调用将提供可以确定由系统设置的本地关联的唯一方法。  
  
##  <a name="getsockopt"></a>  CAsyncSocket::GetSockOpt  
 调用此成员函数以检索套接字选项。  
  
```  
BOOL GetSockOpt(
    int nOptionName,  
    void* lpOptionValue,  
    int* lpOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>参数  
 *nOptionName*  
 为其值是要检索的套接字选项。  
  
 *lpOptionValue*  
 指向在其中请求的选项的值是要返回的缓冲区的指针。 在缓冲区中返回与所选的选项相关联的值*lpOptionValue*。 指向整数*lpOptionLen*最初应包含以字节为单位; 此缓冲区的大小和返回时，它将设置为返回的值的大小。 对于 SO_LINGER，这将的大小`LINGER`结构; 对于所有其他选项，它将是一个布尔值的大小或**int**，具体取决于选项。 请参阅选项和备注部分中的其大小的列表。  
  
 *lpOptionLen*  
 指针的大小*lpOptionValue*以字节为单位的缓冲区。  
  
 *nLevel*  
 在其中定义了选项; 级别唯一支持的级别为 SOL_SOCKET 和 IPPROTO_TCP。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则通过调用检索 0 和特定的错误代码[GetLastError](#getlasterror)。 如果使用永远不会设置一个选项`SetSockOpt`，然后`GetSockOpt`返回选项的默认值。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEFAULT *lpOptionLen*参数无效。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字操作正在进行。  
  
- WSAENOPROTOOPT 选项是未知或不受支持。 具体而言，SO_BROADCAST 不支持在类型 SOCK_STREAM SO_ACCEPTCONN、 SO_DONTLINGER、 SO_KEEPALIVE、 SO_LINGER 和 SO_OOBINLINE 时不支持对类型 SOCK_DGRAM 的套接字的套接字上。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 `GetSockOpt` 检索与在任何状态下，任何类型的套接字关联的套接字选项的当前值并将存储中的结果*lpOptionValue*。 选项会影响套接字操作，例如路由的数据包、 带外数据传输等操作。  
  
 支持以下选项`GetSockOpt`。 类型标识的数据所处理的类型*lpOptionValue*。 TCP_NODELAY 选项使用级别 IPPROTO_TCP;所有其他选项使用级别 SOL_SOCKET。  
  
|“值”|类型|含义|  
|-----------|----------|-------------|  
|SO_ACCEPTCONN|BOOL|正在侦听套接字。|  
|SO_BROADCAST|BOOL|套接字用于广播消息的传输配置。|  
|SO_DEBUG|BOOL|启用调试。|  
|SO_DONTLINGER|BOOL|如果为 true，则禁用 SO_LINGER 选项。|  
|SO_DONTROUTE|BOOL|禁用路由。|  
|SO_ERROR|**int**|检索错误状态并清除。|  
|SO_KEEPALIVE|BOOL|发送 keep-alive。|  
|SO_LINGER|`struct LINGER`|返回当前 linger 选项。|  
|SO_OOBINLINE|BOOL|带外数据正在接收正常数据流中。|  
|SO_RCVBUF|int|接收缓冲区大小。|  
|SO_REUSEADDR|BOOL|套接字可绑定到已在使用的地址。|  
|SO_SNDBUF|**int**|发送缓冲区大小。|  
|SO_TYPE|**int**|套接字 (例如，SOCK_STREAM) 的类型。|  
|TCP_NODELAY|BOOL|为发送合并禁用 Nagle 算法。|  
  
 不支持的 Berkeley Software Distribution (BSD) 选项`GetSockOpt`是：  
  
|“值”|类型|含义|  
|-----------|----------|-------------|  
|SO_RCVLOWAT|**int**|收到的低水印。|  
|SO_RCVTIMEO|**int**|接收超时。|  
|SO_SNDLOWAT|**int**|发送的低水印。|  
|SO_SNDTIMEO|**int**|发送超时。|  
|IP_OPTIONS||获取在 IP 标头中的选项。|  
|TCP_MAXSEG|**int**|获取 TCP 最大段大小。|  
  
 调用`GetSockOpt`与不受支持的选项将导致的错误代码为 WSAENOPROTOOPT 从返回`GetLastError`。  
  
##  <a name="ioctl"></a>  CAsyncSocket::IOCtl  
 调用此成员函数可控制套接字的模式。  
  
```  
BOOL IOCtl(
    long lCommand,  
    DWORD* lpArgument);
```  
  
### <a name="parameters"></a>参数  
 *lCommand*  
 要在套接字上执行的命令。  
  
 *lpArgument*  
 指向参数的指针*lCommand*。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则通过调用检索 0 和特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEINVAL *lCommand*不是有效的命令，或*lpArgument*不是可接受参数*lCommand*，或该命令不是适用于该类型提供的套接字.  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字操作正在进行。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 可以在任何状态的任何套接字上使用此例程。 它用于获取或检索与套接字，独立于协议和通信子系统关联的操作参数。 支持以下命令：  
  
- FIONBIO 启用或禁用非阻止模式套接字上。 *LpArgument*参数指向`DWORD`，这是如果非阻止模式下将启用，非零值为零，则禁用。 如果`AsyncSelect`发出套接字，则如果尝试使用`IOCtl`设置套接字回到阻止模式下的将失败并 WSAEINVAL。 若要设置回阻止模式套接字并防止出现 WSAEINVAL 错误，应用程序必须首先禁用`AsyncSelect`通过调用`AsyncSelect`与*lEvent*参数等于 0，然后调用`IOCtl`。  
  
- FIONREAD 确定的最大可以与一个读取的字节数`Receive`此套接字发出调用。 *LpArgument*参数指向`DWORD`在其中`IOCtl`将结果存储。 FIONREAD 此套接字类型 SOCK_STREAM 的是，如果在单个返回的可读取的数据总量`Receive`; 这通常是相同为套接字上排队的总数据量。 如果此套接字的类型 SOCK_DGRAM，FIONREAD 返回套接字上排队的第一个数据报的大小。  
  
- SIOCATMARK 确定是否已读取所有带外数据。 这仅适用于的类型已配置的行中接收的任何带外数据 (SO_OOBINLINE) SOCK_STREAM 套接字。 如果没有带外数据正在等待读取，该操作将返回非零值。 否则它将返回 0 和下一步`Receive`或`ReceiveFrom`上执行套接字将检索某些或所有前面的"标记"的数据; 该应用程序应使用 SIOCATMARK 操作来确定是否保留了任何数据。 如果前面的"紧急"（带外） 数据的任何正常数据，它将按顺序接收它们。 (请注意，`Receive`或`ReceiveFrom`永远不会混合在同一调用中的带外并处于正常状态数据。)*LpArgument*参数指向`DWORD`在其中`IOCtl`将结果存储。  
  
 此函数是的子集`ioctl()`因为在 Berkeley 套接字中使用。 具体而言，没有相当于 FIOASYNC，SIOCATMARK 时仅套接字级别的命令受支持的命令。  
  
##  <a name="listen"></a>  CAsyncSocket::Listen  
 调用此成员函数以侦听传入连接请求。  
  
```  
BOOL Listen(int nConnectionBacklog = 5);
```  
  
### <a name="parameters"></a>参数  
 *nConnectionBacklog*  
 挂起的连接的队列可以增长到的最大长度。 有效范围是从 1 到 5。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则通过调用检索 0 和特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- 已进行 WSAEADDRINUSE 尝试要使用的地址上进行侦听。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字操作正在进行。  
  
- 没有与绑定套接字 WSAEINVAL`Bind`或已连接。  
  
- WSAEISCONN 套接字已连接。  
  
- WSAEMFILE 否提供了更多的文件描述符。  
  
- WSAENOBUFS 无缓冲区空间不可用。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
- 被引用的套接字的支持的类型不是的 WSAEOPNOTSUPP`Listen`操作。  
  
### <a name="remarks"></a>备注  
 若要接受连接，套接字首次创建使用`Create`，使用指定的传入连接积压`Listen`，然后使用接受连接和`Accept`。 `Listen` 仅适用于套接字的支持的连接，也就是说，这些类型 SOCK_STREAM。 此套接字将进入"被动"模式已确认和队列的进程中的挂起接受传入的连接。  
  
 此函数通常由服务器 （或想要接受连接的任何应用程序），可以一次同时拥有多个连接请求： 如果连接请求到达与队列已满时，客户端将接收并指出了错误WSAECONNREFUSED。  
  
 `Listen` 尝试继续提交时没有可用的端口 （描述符）。 它将接受连接，直到该队列为空。 如果端口变得可用，稍后调用`Listen`或`Accept`将如果可能，请重新填充到当前或最新"积压工作，"队列并重新开始侦听传入连接。  
  
##  <a name="m_hsocket"></a>  CAsyncSocket::m_hSocket  
 包含封装此套接字的套接字句柄`CAsyncSocket`对象。  
  
```  
SOCKET m_hSocket;  
```  
  
##  <a name="onaccept"></a>  CAsyncSocket::OnAccept  
 由框架调用以通知它可以通过调用接受挂起的连接请求的侦听套接字[接受](#accept)成员函数。  
  
```  
virtual void OnAccept(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 *nErrorCode*  
 一个套接字上的最新错误。 以下的错误代码适用于`OnAccept`成员函数：  
  
- **0**成功执行的函数。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[Windows 套接字： 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="onclose"></a>  CAsyncSocket::OnClose  
 由框架调用以通知此套接字连接的套接字由其进程关闭。  
  
```  
virtual void OnClose(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 *nErrorCode*  
 一个套接字上的最新错误。 以下的错误代码应用于`OnClose`成员函数：  
  
- **0**成功执行的函数。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAECONNRESET 的远程端重置连接。  
  
- 由于超时或其他故障，WSAECONNABORTED 连接已中止。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[Windows 套接字： 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="onconnect"></a>  CAsyncSocket::OnConnect  
 由框架调用以通知此连接的套接字完成其连接尝试是否成功或错误。  
  
```  
virtual void OnConnect(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 *nErrorCode*  
 一个套接字上的最新错误。 以下的错误代码应用于`OnConnect`成员函数：  
  
- **0**成功执行的函数。  
  
- WSAEADDRINUSE 指定的地址已在使用中。  
  
- WSAEADDRNOTAVAIL 指定的地址不是可从本地计算机。  
  
- 指定系列中的 WSAEAFNOSUPPORT 地址不能用于此套接字。  
  
- 强制性拒绝 WSAECONNREFUSED 尝试连接。  
  
- WSAEDESTADDRREQ 一个目标地址是必需的。  
  
- WSAEFAULT *lpSockAddrLen*参数不正确。  
  
- WSAEINVAL 套接字已绑定到一个地址。  
  
- WSAEISCONN 套接字已连接。  
  
- WSAEMFILE 否提供了更多的文件描述符。  
  
- WSAENETUNREACH 网络不能将从此主机访问这一次。  
  
- WSAENOBUFS 无缓冲区空间不可用。 不能连接套接字。  
  
- WSAENOTCONN 套接字未连接。  
  
- WSAENOTSOCK 描述符是一个文件，未一个套接字。  
  
- WSAETIMEDOUT 连接尝试超时而无需建立连接。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  在中[CSocket](../../mfc/reference/csocket-class.md)，则`OnConnect`通知函数从未被调用。 对于连接，您只需调用`Connect`，这将返回完成连接后 （成功或错误）。 如何处理连接通知是 MFC 实现详细信息。  
  
 有关详细信息，请参阅[Windows 套接字： 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]  
  
##  <a name="onoutofbanddata"></a>  CAsyncSocket::OnOutOfBandData  
 由框架调用以通知的接收套接字的发送套接字有要发送的带外数据。  
  
```  
virtual void OnOutOfBandData(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 *nErrorCode*  
 一个套接字上的最新错误。 以下的错误代码应用于`OnOutOfBandData`成员函数：  
  
- **0**成功执行的函数。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
### <a name="remarks"></a>备注  
 带外数据是一个逻辑上独立于通道，与已连接的套接字类型 SOCK_STREAM 的每一对相关联。 通道通常用于发送紧急的数据。  
  
 MFC 支持带外数据，但是类的用户`CAsyncSocket`我们建议您不要使用它。 更简单的方法是创建用于传递此类数据的第二个套接字。 有关带外数据的详细信息，请参阅[Windows 套接字： 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="onreceive"></a>  CAsyncSocket::OnReceive  
 由框架调用以通知此套接字可以通过调用检索到的缓冲区中已有数据`Receive`成员函数。  
  
```  
virtual void OnReceive(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 *nErrorCode*  
 一个套接字上的最新错误。 以下的错误代码应用于`OnReceive`成员函数：  
  
- **0**成功执行的函数。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[Windows 套接字： 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]  
  
##  <a name="onsend"></a>  CAsyncSocket::OnSend  
 由框架调用以通知套接字，它现在可通过调用来发送数据`Send`成员函数。  
  
```  
virtual void OnSend(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 *nErrorCode*  
 一个套接字上的最新错误。 以下的错误代码应用于`OnSend`成员函数：  
  
- **0**成功执行的函数。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[Windows 套接字： 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]  
  
##  <a name="operator_eq"></a>  CAsyncSocket::operator =  
 将一个新值赋给`CAsyncSocket`对象。  
  
```  
void operator=(const CAsyncSocket& rSrc);
```  
  
### <a name="parameters"></a>参数  
 *rSrc*  
 向现有的引用`CAsyncSocket`对象。  
  
### <a name="remarks"></a>备注  
 调用此函数可将复制的现有`CAsyncSocket`对象和另一个`CAsyncSocket`对象。  
  
##  <a name="operator_socket"></a>  CAsyncSocket::operator 套接字  
 使用此运算符将检索的套接字句柄`CAsyncSocket`对象。  
  
```  
operator SOCKET() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，套接字对象; 的句柄否则，为 NULL。  
  
### <a name="remarks"></a>备注  
 句柄可用于直接调用 Windows Api。  
  
##  <a name="receive"></a>  CAsyncSocket::Receive  
 调用此成员函数可从套接字接收数据。  
  
```  
virtual int Receive(
    void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>参数  
 *lpBuf*  
 传入数据的缓冲区。  
  
 *nBufLen*  
 长度*lpBuf*以字节为单位。  
  
 *nFlags*  
 指定的方式进行调用。 此函数的语义由套接字选项和*nFlags*参数。 通过将以下值之一结合使用 c + + 构造后者**或**运算符：  
  
- MSG_PEEK 查看传入数据。 将数据复制到缓冲区，但不是会从输入队列中。  
  
- MSG_OOB 处理带外数据。  
  
### <a name="return-value"></a>返回值  
 如果未发生错误，`Receive`返回接收的字节数。 如果连接已关闭，则返回 0。 否则为返回值为 SOCKET_ERROR，并且可以通过调用来检索特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAENOTCONN 套接字未连接。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字操作正在进行。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
- 指定 WSAEOPNOTSUPP MSG_OOB，但不类型 SOCK_STREAM 套接字。  
  
- WSAESHUTDOWN 套接字已关闭;不能调用`Receive`对套接字后`ShutDown`已调用使用了*nHow*设置为 0 或 2。  
  
- WSAEWOULDBLOCK 套接字被标记为非阻止性和`Receive`操作将阻塞。  
  
- WSAEMSGSIZE 数据报太大而无法放入指定的缓冲区，已被截断。  
  
- 没有与绑定套接字 WSAEINVAL `Bind`。  
  
- 由于超时或其他故障，WSAECONNABORTED 虚拟线路已中止。  
  
- 远程端置 WSAECONNRESET 虚拟线路。  
  
### <a name="remarks"></a>备注  
 此函数用于连接的流或数据报套接字，用于读取传入的数据。  
  
 针对的类型 SOCK_STREAM 套接字，则返回的信息是目前最多提供的缓冲区的大小。 如果已配置为在行中接收的带外数据 （套接字选项 SO_OOBINLINE） 套接字和带外数据未读，则将返回仅带外数据。 应用程序可以使用`IOCtlSIOCATMARK`选项或[OnOutOfBandData](#onoutofbanddata)以确定是否任何多带外数据将保留可供读取。  
  
 对于数据报套接字，数据提取自第一个排队数据报，最多提供的缓冲区的大小。 如果数据报值大于提供的缓冲区，使用数据报的第一个部分填充缓冲区，则多余的数据将丢失，和`Receive`SOCKET_ERROR 的具有错误代码的值设置为 WSAEMSGSIZE 返回。 如果没有任何传入的数据在套接字可用，并提供错误代码设置为 WSAEWOULDBLOCK 返回 SOCKET_ERROR 的值。 [OnReceive](#onreceive)回调函数可用于确定当更多数据到达时。  
  
 如果套接字类型 SOCK_STREAM 且远程端已关闭的情况下连接正常，`Receive`将立即完成并接收到的 0 字节。 如果连接已被重置，`Receive`将失败并出现错误 WSAECONNRESET。  
  
 `Receive` 应为每次只有一次调用[CAsyncSocket::OnReceive](#onreceive)调用。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CAsyncSocket::OnReceive](#onreceive)。  
  
##  <a name="receivefrom"></a>  CAsyncSocket::ReceiveFrom  
 调用此成员函数要接收数据报并存储中的源地址[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构中或在*rSocketAddress*。  
  
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
 *lpBuf*  
 传入数据的缓冲区。  
  
 *nBufLen*  
 长度*lpBuf*以字节为单位。  
  
 *rSocketAddress*  
 引用`CString`对象，它接收的以点分隔的数字 IP 地址。  
  
 *rSocketPort*  
 对将存储一个端口是 UINT 引用。  
  
 *lpSockAddr*  
 一个指向[SOCKADDR](../../mfc/reference/sockaddr-structure.md)保留在返回的源地址的结构。  
  
 *lpSockAddrLen*  
 中的源地址的长度的指针*lpSockAddr*以字节为单位。  
  
 *nFlags*  
 指定的方式进行调用。 此函数的语义由套接字选项和*nFlags*参数。 通过将以下值之一结合使用 c + + 构造后者**或**运算符：  
  
- MSG_PEEK 查看传入数据。 将数据复制到缓冲区，但不是会从输入队列中。  
  
- MSG_OOB 处理带外数据。  
  
### <a name="return-value"></a>返回值  
 如果未发生错误，`ReceiveFrom`返回接收的字节数。 如果连接已关闭，则返回 0。 否则为返回值为 SOCKET_ERROR，并且可以通过调用来检索特定的错误代码`GetLastError`。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEFAULT *lpSockAddrLen*参数无效： *lpSockAddr*缓冲区是否太小，无法容纳对等节点地址。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字操作正在进行。  
  
- 没有与绑定套接字 WSAEINVAL `Bind`。  
  
- WSAENOTCONN 套接字未连接 (仅 SOCK_STREAM)。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
- 指定 WSAEOPNOTSUPP MSG_OOB，但不类型 SOCK_STREAM 套接字。  
  
- WSAESHUTDOWN 套接字已关闭;不能调用`ReceiveFrom`对套接字后`ShutDown`已调用使用了*nHow*设置为 0 或 2。  
  
- WSAEWOULDBLOCK 套接字被标记为非阻止性和`ReceiveFrom`操作将阻塞。  
  
- WSAEMSGSIZE 数据报太大而无法放入指定的缓冲区，已被截断。  
  
- 由于超时或其他故障，WSAECONNABORTED 虚拟线路已中止。  
  
- 远程端置 WSAECONNRESET 虚拟线路。  
  
### <a name="remarks"></a>备注  
 此函数用于读取 （可能是连接） 的套接字上的传入数据和捕获从其发送数据的地址。  
  
 若要处理 IPv6 地址，请使用[CAsyncSocket::ReceiveFromEx](#receivefromex)。  
  
 针对的类型 SOCK_STREAM 套接字，则返回的信息是目前最多提供的缓冲区的大小。 如果已配置为在行中接收的带外数据 （套接字选项 SO_OOBINLINE） 套接字和带外数据未读，则将返回仅带外数据。 应用程序可以使用`IOCtlSIOCATMARK`选项或`OnOutOfBandData`以确定是否任何多带外数据将保留可供读取。 *LpSockAddr*并*lpSockAddrLen* SOCK_STREAM 套接字，将忽略参数。  
  
 对于数据报套接字，数据提取自第一个排队数据报，最多提供的缓冲区的大小。 如果数据报值大于提供的缓冲区，使用消息的第一个部分填充缓冲区，则多余的数据将丢失，和`ReceiveFrom`SOCKET_ERROR 的具有错误代码的值设置为 WSAEMSGSIZE 返回。  
  
 如果*lpSockAddr*为非零值，和套接字类型 SOCK_DGRAM 的是，将它发送数据的套接字的网络地址复制到相应[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构。 指向的值*lpSockAddrLen*初始化为此结构的大小，并且修改返回以指示存储在其中的地址的实际大小。 如果没有任何传入的数据可用套接字，`ReceiveFrom`调用等待数据到达除非套接字是非阻止性。 在这种情况下，并提供错误代码设置为 WSAEWOULDBLOCK 返回 SOCKET_ERROR 的值。 `OnReceive`回调可以用于确定当更多数据到达时。  
  
 如果套接字类型 SOCK_STREAM 且远程端已关闭的情况下连接正常，`ReceiveFrom`将立即完成并接收到的 0 字节。  
  
##  <a name="receivefromex"></a>  CAsyncSocket::ReceiveFromEx  
 调用此成员函数要接收数据报并存储中的源地址[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构中或在*rSocketAddress* （处理 IPv6 地址）。  
  
```  
int ReceiveFromEx(
    void* lpBuf,  
    int nBufLen,  
    CString& rSocketAddress,  
    UINT& rSocketPort,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>参数  
 *lpBuf*  
 传入数据的缓冲区。  
  
 *nBufLen*  
 长度*lpBuf*以字节为单位。  
  
 *rSocketAddress*  
 引用`CString`对象，它接收的以点分隔的数字 IP 地址。  
  
 *rSocketPort*  
 对将存储一个端口是 UINT 引用。  
  
 *nFlags*  
 指定的方式进行调用。 此函数的语义由套接字选项和*nFlags*参数。 通过将以下值之一结合使用 c + + 构造后者**或**运算符：  
  
- MSG_PEEK 查看传入数据。 将数据复制到缓冲区，但不是会从输入队列中。  
  
- MSG_OOB 处理带外数据。  
  
### <a name="return-value"></a>返回值  
 如果未发生错误，`ReceiveFromEx`返回接收的字节数。 如果连接已关闭，则返回 0。 否则为返回值为 SOCKET_ERROR，并且可以通过调用来检索特定的错误代码`GetLastError`。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEFAULT *lpSockAddrLen*参数无效： *lpSockAddr*缓冲区是否太小，无法容纳对等节点地址。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字操作正在进行。  
  
- 没有与绑定套接字 WSAEINVAL `Bind`。  
  
- WSAENOTCONN 套接字未连接 (仅 SOCK_STREAM)。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
- 指定 WSAEOPNOTSUPP MSG_OOB，但不类型 SOCK_STREAM 套接字。  
  
- WSAESHUTDOWN 套接字已关闭;不能调用`ReceiveFromEx`对套接字后`ShutDown`已调用使用了*nHow*设置为 0 或 2。  
  
- WSAEWOULDBLOCK 套接字被标记为非阻止性和`ReceiveFromEx`操作将阻塞。  
  
- WSAEMSGSIZE 数据报太大而无法放入指定的缓冲区，已被截断。  
  
- 由于超时或其他故障，WSAECONNABORTED 虚拟线路已中止。  
  
- 远程端置 WSAECONNRESET 虚拟线路。  
  
### <a name="remarks"></a>备注  
 此函数用于读取 （可能是连接） 的套接字上的传入数据和捕获从其发送数据的地址。  
  
 此函数等同于[CAsyncSocket::ReceiveFrom](#receivefrom) ，只不过它处理 IPv6 地址也较旧的协议。  
  
 针对的类型 SOCK_STREAM 套接字，则返回的信息是目前最多提供的缓冲区的大小。 如果已配置为在行中接收的带外数据 （套接字选项 SO_OOBINLINE） 套接字和带外数据未读，则将返回仅带外数据。 应用程序可以使用`IOCtlSIOCATMARK`选项或`OnOutOfBandData`以确定是否任何多带外数据将保留可供读取。 *LpSockAddr*并*lpSockAddrLen* SOCK_STREAM 套接字，将忽略参数。  
  
 对于数据报套接字，数据提取自第一个排队数据报，最多提供的缓冲区的大小。 如果数据报值大于提供的缓冲区，使用消息的第一个部分填充缓冲区，则多余的数据将丢失，和`ReceiveFromEx`SOCKET_ERROR 的具有错误代码的值设置为 WSAEMSGSIZE 返回。  
  
 如果*lpSockAddr*为非零值，和套接字类型 SOCK_DGRAM 的是，将它发送数据的套接字的网络地址复制到相应[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构。 指向的值*lpSockAddrLen*初始化为此结构的大小，并且修改返回以指示存储在其中的地址的实际大小。 如果没有任何传入的数据可用套接字，`ReceiveFromEx`调用等待数据到达除非套接字是非阻止性。 在这种情况下，并提供错误代码设置为 WSAEWOULDBLOCK 返回 SOCKET_ERROR 的值。 `OnReceive`回调可以用于确定当更多数据到达时。  
  
 如果套接字类型 SOCK_STREAM 且远程端已关闭的情况下连接正常，`ReceiveFromEx`将立即完成并接收到的 0 字节。  
  
##  <a name="send"></a>  CAsyncSocket::Send  
 调用此成员函数以连接的套接字上发送的数据。  
  
```  
virtual int Send(
    const void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>参数  
 *lpBuf*  
 包含要传输的数据的缓冲区。  
  
 *nBufLen*  
 中的数据的长度*lpBuf*以字节为单位。  
  
 *nFlags*  
 指定的方式进行调用。 此函数的语义由套接字选项和*nFlags*参数。 通过将以下值之一结合使用 c + + 构造后者**或**运算符：  
  
- MSG_DONTROUTE 指定的数据不应受约束路由。 Windows 套接字供应商可以选择忽略此标志。  
  
- MSG_OOB 发送带外数据 (仅 SOCK_STREAM)。  
  
### <a name="return-value"></a>返回值  
 如果未发生错误，`Send`返回发送的字符总数。 (请注意，这可能会少于所指示的数量*nBufLen*。)否则为返回值为 SOCKET_ERROR，并且可以通过调用来检索特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEACCES 请求的地址是广播的地址，但未设置适当的标志。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字操作正在进行。  
  
- WSAEFAULT *lpBuf*参数不是有效的部件的用户地址空间中。  
  
- 必须重置 WSAENETRESET 连接，因为 Windows 套接字实现将其删除。  
  
- WSAENOBUFS Windows 套接字实现报告缓冲区死锁。  
  
- WSAENOTCONN 套接字未连接。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
- 指定 WSAEOPNOTSUPP MSG_OOB，但不类型 SOCK_STREAM 套接字。  
  
- WSAESHUTDOWN 套接字已关闭;不能调用`Send`对套接字后`ShutDown`已调用使用了*nHow*设置为 1 或 2。  
  
- WSAEWOULDBLOCK 套接字被标记为非阻止性和请求的操作会阻止。  
  
- WSAEMSGSIZE 套接字的类型 SOCK_DGRAM，并且数据报大于支持的 Windows 套接字实现的最大值。  
  
- 没有与绑定套接字 WSAEINVAL `Bind`。  
  
- 由于超时或其他故障，WSAECONNABORTED 虚拟线路已中止。  
  
- 远程端置 WSAECONNRESET 虚拟线路。  
  
### <a name="remarks"></a>备注  
 `Send` 用于编写在连接的流或数据报套接字的传出数据。 对于数据报套接字，必须格外小心不能超过最大的 IP 数据包大小的基础的子网，这由给定`iMaxUdpDg`中的元素[WSADATA](../../mfc/reference/wsadata-structure.md)由返回结构`AfxSocketInit`。 如果数据太长，以原子方式通过基础协议，返回的错误 WSAEMSGSIZE 是通过`GetLastError`，和不传输任何数据。  
  
 请注意，对于数据报套接字的成功完成的`Send`并不表示数据已成功传递。  
  
 在`CAsyncSocket`SOCK_STREAM 类型的对象，写入的字节数可介于 1 和请求的长度，具体取决于本地和外来主机上的缓冲区可用性。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CAsyncSocket::OnSend](#onsend)。  
  
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
 *lpBuf*  
 包含要传输的数据的缓冲区。  
  
 *nBufLen*  
 中的数据的长度*lpBuf*以字节为单位。  
  
 *nHostPort*  
 用于标识套接字应用程序端口。  
  
 *lpszHostAddress*  
 此对象连接的套接字的网络地址： 例如"ftp.microsoft.com，"或一个以点分隔的数字，如"128.56.22.8"的计算机的名称。  
  
 *nFlags*  
 指定的方式进行调用。 此函数的语义由套接字选项和*nFlags*参数。 通过将以下值之一结合使用 c + + 构造后者**或**运算符：  
  
- MSG_DONTROUTE 指定的数据不应受约束路由。 Windows 套接字供应商可以选择忽略此标志。  
  
- MSG_OOB 发送带外数据 (仅 SOCK_STREAM)。  
  
 *lpSockAddr*  
 一个指向[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构，其中包含目标套接字的地址。  
  
 *nSockAddrLen*  
 中的地址的长度*lpSockAddr*以字节为单位。  
  
### <a name="return-value"></a>返回值  
 如果未发生错误，`SendTo`返回发送的字符总数。 (请注意，这可能会少于所指示的数量*nBufLen*。)否则为返回值为 SOCKET_ERROR，并且可以通过调用来检索特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEACCES 请求的地址是广播的地址，但未设置适当的标志。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字操作正在进行。  
  
- WSAEFAULT *lpBuf*或*lpSockAddr*参数不是用户地址空间的一部分或*lpSockAddr*参数是太小 (小于大小[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构)。  
  
- WSAEINVAL 的主机名无效。  
  
- 必须重置 WSAENETRESET 连接，因为 Windows 套接字实现将其删除。  
  
- WSAENOBUFS Windows 套接字实现报告缓冲区死锁。  
  
- WSAENOTCONN 套接字未连接 (仅 SOCK_STREAM)。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
- 指定 WSAEOPNOTSUPP MSG_OOB，但不类型 SOCK_STREAM 套接字。  
  
- WSAESHUTDOWN 套接字已关闭;不能调用`SendTo`对套接字后`ShutDown`已调用使用了*nHow*设置为 1 或 2。  
  
- WSAEWOULDBLOCK 套接字被标记为非阻止性和请求的操作会阻止。  
  
- WSAEMSGSIZE 套接字的类型 SOCK_DGRAM，并且数据报大于支持的 Windows 套接字实现的最大值。  
  
- 由于超时或其他故障，WSAECONNABORTED 虚拟线路已中止。  
  
- 远程端置 WSAECONNRESET 虚拟线路。  
  
- WSAEADDRNOTAVAIL 指定的地址不是可从本地计算机。  
  
- 指定系列中的 WSAEAFNOSUPPORT 地址不能用于此套接字。  
  
- WSAEDESTADDRREQ 一个目标地址是必需的。  
  
- WSAENETUNREACH 网络不能将从此主机访问这一次。  
  
### <a name="remarks"></a>备注  
 `SendTo` 数据报或流套接字上使用，用于编写针对套接字的传出数据。 对于数据报套接字，必须格外小心不能超过最大的 IP 数据包大小的基础的子网，这由给定`iMaxUdpDg`中的元素[WSADATA](../../mfc/reference/wsadata-structure.md)结构通过填写[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). 如果数据太长，以原子方式通过基础协议，返回的错误 WSAEMSGSIZE，并不传输任何数据。  
  
 请注意，成功完成`SendTo`并不表示数据已成功传递。  
  
 `SendTo` 仅用于 SOCK_DGRAM 套接字将数据报发送到由标识特定的套接字*lpSockAddr*参数。  
  
 若要将广播发送 （上 SOCK_DGRAM 仅) 中的地址*lpSockAddr*参数应构造使用特殊的 IP 地址 INADDR_BROADCAST （Windows 套接字标头文件 WINSOCK 中定义。H） 一起使用的目标的端口号。 或者，如果*lpszHostAddress*参数为 NULL，套接字配置进行广播。 它是广播数据报超出开始可以进行碎片，其大小通常不建议使用这表明数据报 （不包括标头） 的数据部分应不超过 512 个字节。  
  
 若要处理 IPv6 地址，请使用[CAsyncSocket::SendToEx](#sendtoex)。  
  
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
 *lpBuf*  
 包含要传输的数据的缓冲区。  
  
 *nBufLen*  
 中的数据的长度*lpBuf*以字节为单位。  
  
 *nHostPort*  
 用于标识套接字应用程序端口。  
  
 *lpszHostAddress*  
 此对象连接的套接字的网络地址： 例如"ftp.microsoft.com，"或一个以点分隔的数字，如"128.56.22.8"的计算机的名称。  
  
 *nFlags*  
 指定的方式进行调用。 此函数的语义由套接字选项和*nFlags*参数。 通过将以下值之一结合使用 c + + 构造后者**或**运算符：  
  
- MSG_DONTROUTE 指定的数据不应受约束路由。 Windows 套接字供应商可以选择忽略此标志。  
  
- MSG_OOB 发送带外数据 (仅 SOCK_STREAM)。  
  
### <a name="return-value"></a>返回值  
 如果未发生错误，`SendToEx`返回发送的字符总数。 (请注意，这可能会少于所指示的数量*nBufLen*。)否则为返回值为 SOCKET_ERROR，并且可以通过调用来检索特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEACCES 请求的地址是广播的地址，但未设置适当的标志。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字操作正在进行。  
  
- WSAEFAULT *lpBuf*或*lpSockAddr*参数不是用户地址空间的一部分或*lpSockAddr*参数是太小 (小于大小[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构)。  
  
- WSAEINVAL 的主机名无效。  
  
- 必须重置 WSAENETRESET 连接，因为 Windows 套接字实现将其删除。  
  
- WSAENOBUFS Windows 套接字实现报告缓冲区死锁。  
  
- WSAENOTCONN 套接字未连接 (仅 SOCK_STREAM)。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
- 指定 WSAEOPNOTSUPP MSG_OOB，但不类型 SOCK_STREAM 套接字。  
  
- WSAESHUTDOWN 套接字已关闭;不能调用`SendToEx`对套接字后`ShutDown`已调用使用了*nHow*设置为 1 或 2。  
  
- WSAEWOULDBLOCK 套接字被标记为非阻止性和请求的操作会阻止。  
  
- WSAEMSGSIZE 套接字的类型 SOCK_DGRAM，并且数据报大于支持的 Windows 套接字实现的最大值。  
  
- 由于超时或其他故障，WSAECONNABORTED 虚拟线路已中止。  
  
- 远程端置 WSAECONNRESET 虚拟线路。  
  
- WSAEADDRNOTAVAIL 指定的地址不是可从本地计算机。  
  
- 指定系列中的 WSAEAFNOSUPPORT 地址不能用于此套接字。  
  
- WSAEDESTADDRREQ 一个目标地址是必需的。  
  
- WSAENETUNREACH 网络不能将从此主机访问这一次。  
  
### <a name="remarks"></a>备注  
 此方法等同于[CAsyncSocket::SendTo](#sendto) ，只不过它处理 IPv6 地址也较旧的协议。  
  
 `SendToEx` 数据报或流套接字上使用，用于编写针对套接字的传出数据。 对于数据报套接字，必须格外小心不能超过最大的 IP 数据包大小的基础的子网，这由给定`iMaxUdpDg`中的元素[WSADATA](../../mfc/reference/wsadata-structure.md)结构通过填写[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). 如果数据太长，以原子方式通过基础协议，返回的错误 WSAEMSGSIZE，并不传输任何数据。  
  
 请注意，成功完成`SendToEx`并不表示数据已成功传递。  
  
 `SendToEx` 仅用于 SOCK_DGRAM 套接字将数据报发送到由标识特定的套接字*lpSockAddr*参数。  
  
 若要将广播发送 （上 SOCK_DGRAM 仅) 中的地址*lpSockAddr*参数应构造使用特殊的 IP 地址 INADDR_BROADCAST （Windows 套接字标头文件 WINSOCK 中定义。H） 一起使用的目标的端口号。 或者，如果*lpszHostAddress*参数为 NULL，套接字配置进行广播。 它是广播数据报超出开始可以进行碎片，其大小通常不建议使用这表明数据报 （不包括标头） 的数据部分应不超过 512 个字节。  
  
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
 *nOptionName*  
 为其值将设置套接字选项。  
  
 *lpOptionValue*  
 指向在其中提供请求的选项的值的缓冲区的指针。  
  
 *nOptionLen*  
 大小*lpOptionValue*以字节为单位的缓冲区。  
  
 *nLevel*  
 在其中定义了选项; 级别唯一支持的级别为 SOL_SOCKET 和 IPPROTO_TCP。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则通过调用检索 0 和特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEFAULT *lpOptionValue*不是有效的进程地址空间部分。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字操作正在进行。  
  
- WSAEINVAL *nLevel*无效，或中的信息*lpOptionValue*无效。  
  
- 当设置 SO_KEEPALIVE，WSAENETRESET 连接已超时。  
  
- WSAENOPROTOOPT 选项是未知或不受支持。 具体而言，SO_BROADCAST 不支持在类型 SOCK_STREAM SO_DONTLINGER、 SO_KEEPALIVE、 SO_LINGER 和 SO_OOBINLINE 时不支持对类型 SOCK_DGRAM 的套接字的套接字上。  
  
- 当设置 SO_KEEPALIVE WSAENOTCONN 连接已重置。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 `SetSockOpt` 设置与中的任何状态的任何类型的套接字关联的套接字选项的当前值。 尽管选项可以在多个协议级别存在，但此规范只定义最高"套接字"级别中存在的选项。 选项会影响套接字操作，如是否加急的数据是在流中收到正常数据，是否可以在套接字上发送广播的消息，并且其他操作。  
  
 有两种类型的套接字选项： 布尔选项启用或禁用功能或行为和它需要整数值或结构的选项。 若要启用布尔选项， *lpOptionValue*指向非零的整数。 若要禁用选项*lpOptionValue*指向一个等于零的整数。 *nOptionLen*应等于`sizeof(BOOL)`布尔选项。 有关其他选项， *lpOptionValue*指向的整数或结构，其中包含所需的值对于选项，并*nOptionLen*是整数或结构的长度。  
  
 SO_LINGER 控制时未发送的数据排队套接字上执行的操作和`Close`函数调用以关闭套接字。  
  
 默认情况下，不能绑定套接字 (请参阅[绑定](#bind)) 到其已在使用本地地址。 有时，但是，它可能需要"重新使用"在这种方式中的地址。 因为由本地和远程地址的组合唯一标识每个连接，所以也绑定到相同的本地地址，只要远程地址是不同的两个套接字出现任何问题。  
  
 若要通知的 Windows 套接字实现的`Bind`应不允许对套接字的调用，因为所需的地址已在使用另一套接字，该应用程序应设置套接字发出之前 SO_REUSEADDR 套接字选项`Bind`调用。 请注意，该选项仅在时解释`Bind`调用： 因此是不必要 （但是无害） 上的套接字，则不需要绑定到现有的地址，设置选项和设置或重置后的选项`Bind`调用具有此计算机或任何其他套接字不起作用。  
  
 应用程序可以请求 Windows 套接字实现通过开启 SO_KEEPALIVE 套接字选项启用"保持连接"上的数据包的传输控制协议 (TCP) 连接使用。 Windows 套接字实现不需要支持使用 keep-alive： 如果是这样，是特定于实现的精确语义，但应符合 RFC 1122 的 4.2.3.6 节:"的 Internet 主机要求-通信层。" 如果删除连接作为结果的"keep-alive"返回的错误代码 WSAENETRESET 是正在进行中的任何调用套接字，和任何后续调用将因 WSAENOTCONN。  
  
 TCP_NODELAY 选项将禁用 Nagle 算法。 使用 Nagle 算法来减少的小型数据包由主机发送缓冲请求未确认的发送数据，直到可以发送一个完全尺寸的数据包数。 但是，对于某些应用程序，此算法会妨碍性能，并且 TCP_NODELAY 可用于将其关闭。 应用程序编写器不应设置 TCP_NODELAY，除非这样做的影响因此是易于理解和所需的因为设置 TCP_NODELAY 可以对网络性能产生严重的负面影响。 TCP_NODELAY 是唯一支持的使用级别 IPPROTO_TCP; 套接字选项所有其他选项使用级别 SOL_SOCKET。  
  
 如果应用程序设置 SO_DEBUG 选项，某些实现 Windows 套接字提供输出调试信息。  
  
 支持以下选项`SetSockOpt`。 类型标识的数据所处理的类型*lpOptionValue*。  
  
|“值”|类型|含义|  
|-----------|----------|-------------|  
|SO_BROADCAST|BOOL|允许在套接字上的广播消息的传输。|  
|SO_DEBUG|BOOL|记录调试信息。|  
|SO_DONTLINGER|BOOL|不会阻止`Close`等待未发送的数据要发送。 设置此选项等同于将设置与 SO_LINGER`l_onoff`设置为零。|  
|SO_DONTROUTE|BOOL|不路由： 直接向接口发送。|  
|SO_KEEPALIVE|BOOL|发送 keep-alive。|  
|SO_LINGER|`struct LINGER`|Linger`Close`如果未发送的数据是否存在。|  
|SO_OOBINLINE|BOOL|接收正常数据流中的带外数据。|  
|SO_RCVBUF|**int**|指定接收缓冲区大小。|  
|SO_REUSEADDR|BOOL|允许要绑定到已在使用的地址的套接字。 (请参阅[绑定](#bind)。)|  
|SO_SNDBUF|**int**|指定发送的缓冲区大小。|  
|TCP_NODELAY|BOOL|为发送合并禁用 Nagle 算法。|  
  
 不支持的 Berkeley Software Distribution (BSD) 选项`SetSockOpt`是：  
  
|“值”|类型|含义|  
|-----------|----------|-------------|  
|SO_ACCEPTCONN|BOOL|套接字侦听|  
|SO_ERROR|**int**|获取错误状态并清除。|  
|SO_RCVLOWAT|**int**|收到的低水印。|  
|SO_RCVTIMEO|**int**|接收超时|  
|SO_SNDLOWAT|**int**|发送的低水印。|  
|SO_SNDTIMEO|**int**|发送超时。|  
|SO_TYPE|**int**|套接字的类型。|  
|IP_OPTIONS||在 IP 标头中设置选项字段。|  
  
##  <a name="shutdown"></a>  CAsyncSocket::ShutDown  
 调用此成员函数以禁用发送时，收到，或两个套接字上。  
  
```  
BOOL ShutDown(int nHow = sends);
```  
  
### <a name="parameters"></a>参数  
 *nHow*  
 一个标志，介绍哪些类型的操作将不再允许，请使用下列枚举的值：  
  
- **接收 = 0**  
  
- **将发送 = 1**  
  
- **同时 = 2**  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则通过调用检索 0 和特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于此成员函数：  
  
- WSANOTINITIALISED 一个成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必须使用此 API 之前发生。  
  
- WSAENETDOWN Windows 套接字实现检测到的网络子系统失败。  
  
- WSAEINVAL *nHow*无效。  
  
- 返回 WSAEINPROGRESS 一个阻止 Windows 套接字操作正在进行。  
  
- WSAENOTCONN 套接字未连接 (仅 SOCK_STREAM)。  
  
- WSAENOTSOCK 描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 `ShutDown` 用于所有类型的套接字上禁用接收、 传输，或这两者。 如果*nHow*为 0，则后续接收的套接字将不允许使用。 这没有任何影响较低的协议层上。  
  
 有关传输控制协议 (TCP) TCP 窗口不会更改并且将传入的数据之前窗口已用尽，接受 （但不是确认）。 有关用户数据报协议 (UDP)，传入数据报是接受并已排队。 将在任何情况下生成 ICMP 错误数据包。 如果*nHow*为 1，不允许后续发送。 对于 TCP 套接字会发送 FIN。 设置*nHow*为 2 同时禁用发送和接收上文所述。  
  
 请注意，`ShutDown`不会关闭套接字，并附加到套接字的资源将不前不会释放`Close`调用。 应用程序不应依赖于能够重复使用套接字之后它已关闭。 具体而言，Windows 套接字实现不需要支持使用`Connect`针对此类套接字。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CAsyncSocket::OnReceive](#onreceive)。  
  
##  <a name="socket"></a>  CASyncSocket::Socket  
 分配一个套接字句柄。  
  
```  
BOOL Socket(
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    int nProtocolType = 0,  
    int nAddressFormat = PF_INET);
```  
  
### <a name="parameters"></a>参数  
 *nSocketType*  
 指定`SOCK_STREAM`或`SOCK_DGRAM`。  
  
 *lEvent*  
 指定在其中所关注的应用程序的网络事件的组合的位掩码。  
  
- `FD_READ`： 想要接收通知的准备情况进行读取。  
  
- `FD_WRITE`： 想要接收通知以进行写入的准备情况。  
  
- `FD_OOB`： 想要接收的带外数据到达的通知。  
  
- `FD_ACCEPT`： 想要接收传入连接的通知。  
  
- `FD_CONNECT`： 想要接收通知的已完成的连接。  
  
- `FD_CLOSE`： 想要接收的套接字关闭通知。  
  
 *nProtocolType*  
 若要与特定于所指示的地址族的套接字一起使用的协议。  
  
 *nAddressFormat*  
 地址系列规范。  
  
### <a name="return-value"></a>返回值  
 成功时返回 `TRUE`，失败时返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法分配套接字句柄。 它不会调用[CAsyncSocket::Bind](#bind)将套接字绑定到指定的地址，以使您需要调用`Bind`更高版本才能将套接字绑定到指定的地址。 可以使用[CAsyncSocket::SetSockOpt](#setsockopt)之前它所绑定设置套接字选项。  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CSocket 类](../../mfc/reference/csocket-class.md)   
 [CSocketFile 类](../../mfc/reference/csocketfile-class.md)
