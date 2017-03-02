---
title: "CAsyncSocket 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAsyncSocket
dev_langs:
- C++
helpviewer_keywords:
- network communications
- asynchronous Windows Sockets
- CAsyncSocket class
- Windows Sockets [C++], asynchronous
- communications [C++], network
- sockets [C++], Windows
ms.assetid: cca4d5a1-aa0f-48bd-843e-ef0e2d7fc00b
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c7a175fc12146d98becc5d06f80e975df5b5a008
ms.lasthandoff: 02/24/2017

---
# <a name="casyncsocket-class"></a>CAsyncSocket 类
表示 Windows 套接字 — 网络通信的终结点。  
  
## <a name="syntax"></a>语法  
  
```  
class CAsyncSocket : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CAsyncSocket::CAsyncSocket](#casyncsocket)|构造 `CAsyncSocket` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAsyncSocket::Accept](#accept)|接受的套接字上的连接。|  
|[CAsyncSocket::AsyncSelect](#asyncselect)|请求的套接字的事件通知。|  
|[CAsyncSocket::Attach](#attach)|将附加到套接字句柄`CAsyncSocket`对象。|  
|[CAsyncSocket::Bind](#bind)|将与套接字关联的本地地址。|  
|[CAsyncSocket::Close](#close)|关闭套接字。|  
|[CAsyncSocket::Connect](#connect)|建立到对等方套接字连接。|  
|[CAsyncSocket::Create](#create)|创建的套接字。|  
|[CAsyncSocket::Detach](#detach)|分离从套接字句柄`CAsyncSocket`对象。|  
|[CAsyncSocket::FromHandle](#fromhandle)|返回一个指向`CAsyncSocket`给定套接字句柄的对象。|  
|[CAsyncSocket::GetLastError](#getlasterror)|获取失败的最后一个操作的错误状态。|  
|[CAsyncSocket::GetPeerName](#getpeername)|获取对等方套接字对套接字连接到的地址。|  
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|获取对等方套接字的套接字是连接 （句柄 IPv6 地址） 的地址。|  
|[CAsyncSocket::GetSockName](#getsockname)|获取套接字的本地名称。|  
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|获取套接字 （句柄 IPv6 地址） 的本地名称。|  
|[CAsyncSocket::GetSockOpt](#getsockopt)|检索套接字选项。|  
|[CAsyncSocket::IOCtl](#ioctl)|控制的套接字的模式。|  
|[CAsyncSocket::Listen](#listen)|建立套接字以侦听传入的连接请求。|  
|[CAsyncSocket::Receive](#receive)|从套接字接收数据。|  
|[CAsyncSocket::ReceiveFrom](#receivefrom)|接收数据报并存储了源地址。|  
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|接收数据报并存储了源地址 （句柄 IPv6 地址）。|  
|[CAsyncSocket::Send](#send)|将数据发送到连接的套接字。|  
|[CAsyncSocket::SendTo](#sendto)|将数据发送到特定目标。|  
|[CAsyncSocket::SendToEx](#sendtoex)|将数据发送到特定目标 （句柄 IPv6 地址）。|  
|[CAsyncSocket::SetSockOpt](#setsockopt)|设置套接字选项。|  
|[CAsyncSocket::ShutDown](#shutdown)|禁用**发送**和/或**接收**调用的套接字上。|  
|[CASyncSocket::Socket](#socket)|分配套接字句柄。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAsyncSocket::OnAccept](#onaccept)|通知它可以通过调用接受挂起的连接请求的侦听套接字**接受**。|  
|[CAsyncSocket::OnClose](#onclose)|通知的套接字连接到它的套接字已关闭。|  
|[CAsyncSocket::OnConnect](#onconnect)|通知连接的套接字连接尝试是否已完成，无论成功或错误。|  
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|通知的接收套接字有要读取的套接字，通常紧急邮件上的带外数据。|  
|[CAsyncSocket::OnReceive](#onreceive)|没有要通过调用检索数据时通知侦听套接字**接收**。|  
|[CAsyncSocket::OnSend](#onsend)|它可通过调用发送数据通知套接字**发送**。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CAsyncSocket::operator =](#operator_eq)|将一个新值赋给`CAsyncSocket`对象。|  
|[CAsyncSocket::operator 套接字](#operator_socket)|使用此运算符可检索**套接字**的 handle`CAsyncSocket`对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CAsyncSocket::m_hSocket](#m_hsocket)|指示**套接字**句柄附加到此`CAsyncSocket`对象。|  
  
## <a name="remarks"></a>备注  
 类`CAsyncSocket`封装 Windows 套接字函数 API 中，对于那些想要与 MFC 一起使用 Windows 套接字程序员提供的面向对象的抽象。  
  
 此类基于了解网络通信的假设。 您是负责处理阻塞，字节顺序的差异，并 Unicode 和多字节字符之间的转换设置 (MBCS) 字符串。 如果您希望更方便的界面，将为您管理这些问题，请参阅类[CSocket](../../mfc/reference/csocket-class.md)。  
  
 若要使用`CAsyncSocket`对象，请调用其构造函数，然后调用[创建](#create)函数来创建基础套接字句柄 (类型`SOCKET`)，除非在接受套接字上。 对于服务器套接字调用[侦听](#listen)成员函数，并为客户端套接字调用[连接](#connect)成员函数。 应调用服务器套接字[接受](#accept)收到连接请求的函数。 使用其余`CAsyncSocket`函数来执行套接字之间的通信。 完成后，销毁`CAsyncSocket`对象，如果它在堆上创建; 析构函数自动调用[关闭](#close)函数。 `SOCKET`文章中介绍的数据类型[Windows 套接字︰ 背景](../../mfc/windows-sockets-background.md)。  
  
> [!NOTE]
>  在静态链接的 MFC 应用程序中的辅助线程中使用 MFC 套接字时，您必须在使用套接字的每个线程中调用 `AfxSocketInit` 来初始化套接字库。 默认情况下，仅在主线程中调用 `AfxSocketInit`。  
  
 有关详细信息，请参阅[Windows 套接字︰ 使用类 CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) ，相关文章，以及[Windows Sockets 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAsyncSocket`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxsock.h  
  
##  <a name="a-nameaccepta--casyncsocketaccept"></a><a name="accept"></a>CAsyncSocket::Accept  
 调用该成员函数以接受套接字上的连接。  
  
```  
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,  
    SOCKADDR* lpSockAddr = NULL,  
    int* lpSockAddrLen = NULL);
```  
  
### <a name="parameters"></a>参数  
 `rConnectedSocket`  
 标识可用于连接了新套接字的引用。  
  
 `lpSockAddr`  
 一个指向[SOCKADDR](../../mfc/reference/sockaddr-structure.md)套接字结构，它接收连接的地址，因为识别在网络上。 确切格式`lpSockAddr`参数由时创建的套接字时建立的地址族。 如果`lpSockAddr`和/或`lpSockAddrLen`等于**NULL**，则不返回有关远程地址接受的套接字的任何信息。  
  
 `lpSockAddrLen`  
 中的地址的长度的指针`lpSockAddr`以字节为单位。 `lpSockAddrLen`是值结果的参数︰ 它最初应包含所指向的空间量`lpSockAddr`; 返回时它将包含返回的地址的实际长度 （以字节为单位）。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0 和特定错误代码可以检索通过调用[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpSockAddrLen`参数是太小 (小于大小[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构)。  
  
- **返回 WSAEINPROGRESS**阻止 Windows 套接字调用正在进行。  
  
- **WSAEINVAL** `Listen`未接受调用的之前。  
  
- **WSAEMFILE**队列为空，在接受的输入而不没有可用的任何描述符。  
  
- `WSAENOBUFS`没有缓冲区空间不可用。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP**引用套接字不支持面向连接的服务的类型。  
  
- **WSAEWOULDBLOCK**套接字被标记为非阻止且没有任何连接都存在要接受的。  
  
### <a name="remarks"></a>备注  
 此例程提取挂起的连接的队列中的第一个连接，使用与此套接字，相同的属性创建了新套接字并将其附加到`rConnectedSocket`。 如果没有挂起的连接在队列中，存在**接受**返回零和`GetLastError`返回错误。 接受的套接字 ( *rConnectedSocket)*不能用来接受更多的连接。 打开并开始侦听，将保持原始套接字。  
  
 参数`lpSockAddr`是填充连接套接字时，该地址的结果参数，因为识别通信层。 **接受**用于基于连接的套接字类型如**SOCK_STREAM**。  
  
##  <a name="a-nameasyncselecta--casyncsocketasyncselect"></a><a name="asyncselect"></a>CAsyncSocket::AsyncSelect  
 调用该成员函数以请求为套接字的事件通知。  
  
```  
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>参数  
 `lEvent`  
 位掩码，它指定在其中应用程序感兴趣的网络事件的组合。  
  
- **FD_READ**想要接收通知的准备工作以进行读取。  
  
- **FD_WRITE**希望可供读取数据时收到通知。  
  
- **FD_OOB**想要接收通知的带外数据的到达。  
  
- **FD_ACCEPT**想要接收通知的传入连接。  
  
- **FD_CONNECT**想要接收通知的连接的结果。  
  
- **FD_CLOSE**想要的套接字已关闭对等方时接收通知。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0 和特定错误代码可以检索通过调用[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEINVAL**表明指定的参数之一无效。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
### <a name="remarks"></a>备注  
 此函数用于指定哪些 MFC 回调通知函数将调用为套接字。 `AsyncSelect`自动将此套接字设置为非锁定模式。 有关详细信息，请参阅文章[Windows 套接字︰ 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="a-nameattacha--casyncsocketattach"></a><a name="attach"></a>CAsyncSocket::Attach  
 调用此成员函数可将附加`hSocket`的句柄`CAsyncSocket`对象。  
  
```  
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>参数  
 `hSocket`  
 包含为套接字的句柄。  
  
 `lEvent`  
 位掩码，它指定在其中应用程序感兴趣的网络事件的组合。  
  
- **FD_READ**想要接收通知的准备工作以进行读取。  
  
- **FD_WRITE**希望可供读取数据时收到通知。  
  
- **FD_OOB**想要接收通知的带外数据的到达。  
  
- **FD_ACCEPT**想要接收通知的传入连接。  
  
- **FD_CONNECT**想要接收通知的连接的结果。  
  
- **FD_CLOSE**想要的套接字已关闭对等方时接收通知。  
  
### <a name="return-value"></a>返回值  
 如果函数运行成功，则为非零。  
  
### <a name="remarks"></a>备注  
 **套接字**句柄存储在该对象的[m_hSocket](#m_hsocket)数据成员。  
  
##  <a name="a-namebinda--casyncsocketbind"></a><a name="bind"></a>CAsyncSocket::Bind  
 调用该成员函数以将本地地址与套接字相关联。  
  
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
 用于标识套接字应用程序的端口。  
  
 `lpszSocketAddress`  
 网络地址，如"128.56.22.8"圆点分隔数。 传递**NULL**字符串为此参数指示**CAsyncSocket**实例应侦听的所有网络接口上的客户端活动。  
  
 `lpSockAddr`  
 一个指向[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构，其中包含要分配给此套接字地址。  
  
 `nSockAddrLen`  
 中的地址长度`lpSockAddr`以字节为单位。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0 和特定错误代码可以检索通过调用[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEADDRINUSE**指定的地址已在使用。 (请参阅**SO_REUSEADDR**套接字选项下的[SetSockOpt](#setsockopt)。)  
  
- **WSAEFAULT** `nSockAddrLen`参数是太小 (小于大小[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构)。  
  
- **返回 WSAEINPROGRESS**阻止 Windows 套接字调用正在进行。  
  
- **WSAEAFNOSUPPORT**此端口不支持指定的地址族。  
  
- **WSAEINVAL**套接字已绑定到一个地址。  
  
- `WSAENOBUFS`没有足够的缓冲区可用，过多连接。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 之前未连接的数据报或流套接字上使用此例程后续**连接**或`Listen`调用。 它可以接受连接请求之前，侦听服务器套接字必须选择一个端口号，并将它已知对 Windows 套接字通过调用**绑定**。 **将绑定**通过将本地名称分配给未命名的套接字建立套接字的本地关联 （主机地址/端口号）。  
  
##  <a name="a-namecasyncsocketa--casyncsocketcasyncsocket"></a><a name="casyncsocket"></a>CAsyncSocket::CAsyncSocket  
 构造一个空的套接字对象。  
  
```  
CAsyncSocket();
```  
  
### <a name="remarks"></a>备注  
 构造该对象，则必须调用其**创建**成员函数来创建**套接字**数据结构，并将其地址的绑定。 (在服务器端的 Windows 套接字通信，当侦听套接字创建要在中使用的套接字**接受**调用时，不要调用**创建**对于此套接字。)  
  
##  <a name="a-nameclosea--casyncsocketclose"></a><a name="close"></a>CAsyncSocket::Close  
 关闭套接字。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 此函数释放的套接字描述符，以便进一步对它的引用将失败并出现错误**WSAENOTSOCK**。 如果这是对基础套接字的最后一个引用，将丢弃关联的命名信息和排队的数据。 套接字对象析构函数调用**关闭**为您。  
  
 有关`CAsyncSocket`，但不是能为`CSocket`的语义**关闭**受套接字选项**SO_LINGER**和**SO_DONTLINGER**。 有关详细信息，请参见成员函数`GetSockOpt`。  
  
##  <a name="a-nameconnecta--casyncsocketconnect"></a><a name="connect"></a>CAsyncSocket::Connect  
 调用此成员函数来建立与未连接的流或数据报套接字连接。  
  
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
 此对象连接的套接字的网络地址︰ 如"ftp.microsoft.com"或一个以点分隔的数字，如"128.56.22.8"的计算机的名称。  
  
 `nHostPort`  
 用于标识套接字应用程序的端口。  
  
 `lpSockAddr`  
 一个指向[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构，其中包含连接的套接字的地址。  
  
 `nSockAddrLen`  
 中的地址长度`lpSockAddr`以字节为单位。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0 和特定错误代码可以检索通过调用[GetLastError](#getlasterror)。 如果这指示的错误代码为**WSAEWOULDBLOCK**，并且您的应用程序正在使用可重写的回调，则应用程序将收到`OnConnect`消息时连接操作已完成。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEADDRINUSE**指定的地址已在使用。  
  
- **返回 WSAEINPROGRESS**阻止 Windows 套接字调用正在进行。  
  
- **WSAEADDRNOTAVAIL**指定的地址不在本地计算机中可用。  
  
- **WSAEAFNOSUPPORT**用这个套接字，不能使用指定系列中的地址。  
  
- **WSAECONNREFUSED**尝试连接被拒绝。  
  
- **WSAEDESTADDRREQ**目标地址是必需的。  
  
- **WSAEFAULT** `nSockAddrLen`参数不正确。  
  
- **WSAEINVAL**无效的主机地址。  
  
- **WSAEISCONN**套接字已连接。  
  
- **WSAEMFILE**没有更多的文件描述符。  
  
- **WSAENETUNREACH**网络不能将从此主机访问这一次。  
  
- `WSAENOBUFS`没有缓冲区空间不可用。 无法连接套接字。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAETIMEDOUT**尝试连接超时而无需建立一个连接。  
  
- **WSAEWOULDBLOCK**套接字被标记为非阻塞，并且无法立即完成连接。  
  
### <a name="remarks"></a>备注  
 如果套接字是未绑定、 唯一值分配给本地关联由系统和套接字被标记为绑定。 请注意，如果名称结构的地址字段是零，**连接**将返回零。 若要获得扩展错误信息，请调用`GetLastError`成员函数。  
  
 有关流套接字 (类型**SOCK_STREAM**)，向外主机启动的活动连接。 套接字调用成功完成后，套接字已准备好发送/接收数据。  
  
 数据报套接字 (类型**SOCK_DGRAM**)，默认目标设置，它将在后续使用**发送**和**接收**调用。  
  
##  <a name="a-namecreatea--casyncsocketcreate"></a><a name="create"></a>CAsyncSocket::Create  
 调用**创建**后构造套接字对象创建 Windows 套接字并将其附加的成员函数。  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>参数  
 `nSocketPort`  
 如果您希望 Windows 套接字选择的端口套接字或 0 开头使用众所周知的端口。  
  
 `nSocketType`  
 **SOCK_STREAM**或**SOCK_DGRAM**。  
  
 `lEvent`  
 位掩码，它指定在其中应用程序感兴趣的网络事件的组合。  
  
- **FD_READ**想要接收通知的准备工作以进行读取。  
  
- **FD_WRITE**想要接收通知的准备工作以进行写入。  
  
- **FD_OOB**想要接收通知的带外数据的到达。  
  
- **FD_ACCEPT**想要接收通知的传入连接。  
  
- **FD_CONNECT**想要接收通知的已完成的连接。  
  
- **FD_CLOSE**想要接收通知的套接字关闭。  
  
 *lpszSockAddress*  
 指向一个包含连接的套接字，一个以点分隔的数字，如"128.56.22.8"的网络地址的字符串的指针。传递**NULL**字符串为此参数指示**CAsyncSocket**实例应侦听的所有网络接口上的客户端活动。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0 和特定错误代码可以检索通过调用[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEAFNOSUPPORT**不支持指定的地址族。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEMFILE**没有更多的文件描述符。  
  
- `WSAENOBUFS`没有缓冲区空间不可用。 无法创建套接字。  
  
- **WSAEPROTONOSUPPORT**不支持指定的端口。  
  
- **WSAEPROTOTYPE**指定的端口是此套接字错误的类型。  
  
- **WSAESOCKTNOSUPPORT**指定套接字类型不支持此地址族中。  
  
### <a name="remarks"></a>备注  
 **创建**调用[套接字](#socket)如果成功，它会调用[绑定](#bind)将套接字绑定到指定的地址。 支持以下的套接字类型︰  
  
- **SOCK_STREAM**进行序列化，提供可靠、 全双工、 基于连接的字节流。 使用传输控制协议 (TCP) 为 Internet 地址族。  
  
- **SOCK_DGRAM**支持数据报，固定 （通常很小） 的最大长度的无连接的、 不可靠的数据包。 使用用户数据报协议 (UDP) 为 Internet 地址族。  
  
    > [!NOTE]
    >  **接受**成员函数会将新的空的引用`CSocket`对象作为其参数。 您必须在调用之前先构造此对象**接受**。 请记住，如果此套接字对象超出范围，该连接将关闭。 不要调用**创建**为此新的套接字对象。  
  
> [!IMPORTANT]
> **创建**是**不**线程安全。  如果您正在调用它在多线程环境中可以在其中它无法调用同时由不同的线程，请务必保护与互斥锁或其他同步锁的每个调用。  
  
 有关流和数据报套接字的详细信息，请参阅文章[Windows 套接字︰ 背景](../../mfc/windows-sockets-background.md)和[Windows 套接字︰ 端口和套接字地址](../../mfc/windows-sockets-ports-and-socket-addresses.md)和[Windows Sockets 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673)。  
  
##  <a name="a-namedetacha--casyncsocketdetach"></a><a name="detach"></a>CAsyncSocket::Detach  
 调用此成员函数以分离**套接字**以处理`m_hSocket`数据成员从`CAsyncSocket`对象并设置`m_hSocket`到**NULL**。  
  
```  
SOCKET Detach();
```  
  
##  <a name="a-namefromhandlea--casyncsocketfromhandle"></a><a name="fromhandle"></a>CAsyncSocket::FromHandle  
 返回一个指向`CAsyncSocket`对象。  
  
```  
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```  
  
### <a name="parameters"></a>参数  
 `hSocket`  
 包含为套接字的句柄。  
  
### <a name="return-value"></a>返回值  
 一个指向`CAsyncSocket`对象，或**NULL**是否存在任何`CAsyncSocket`对象附加到`hSocket`。  
  
### <a name="remarks"></a>备注  
 在给定**套接字**处理，如果`CAsyncSocket`对象未附加到该句柄，成员函数将返回**NULL**。  
  
##  <a name="a-namegetlasterrora--casyncsocketgetlasterror"></a><a name="getlasterror"></a>CAsyncSocket::GetLastError  
 调用该成员函数以获取有关失败的最后一个操作的错误状态。  
  
```  
static int PASCAL GetLastError();
```  
  
### <a name="return-value"></a>返回值  
 返回值表示此线程执行的最后一个 Windows 套接字 API 例程的错误代码。  
  
### <a name="remarks"></a>备注  
 当某个特定成员函数指示已发生错误，`GetLastError`应调用以检索相应的错误代码。 请参阅单独的成员函数的描述有关列表的相应错误代码。  
  
 有关错误代码的详细信息，请参阅[Windows Sockets 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673)。  
  
##  <a name="a-namegetpeernamea--casyncsocketgetpeername"></a><a name="getpeername"></a>CAsyncSocket::GetPeerName  
 调用该成员函数以获取此套接字连接到的对等方套接字地址。  
  
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
 引用`CString`对象，它接收的以点分隔的数字 IP 地址。  
  
 `rPeerPort`  
 引用**UINT**存储一个端口。  
  
 `lpSockAddr`  
 一个指向[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构，它接收的对等方套接字的名称。  
  
 `lpSockAddrLen`  
 中的地址的长度的指针`lpSockAddr`以字节为单位。 返回时，`lpSockAddrLen`参数中包含的实际大小`lpSockAddr`返回以字节为单位。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0 和特定错误代码可以检索通过调用[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpSockAddrLen`参数不是足够大。  
  
- **返回 WSAEINPROGRESS**阻止 Windows 套接字调用正在进行。  
  
- **WSAENOTCONN**套接字未连接。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 若要处理 IPv6 地址，使用[CAsyncSocket::GetPeerNameEx](#getpeernameex)。  
  
##  <a name="a-namegetpeernameexa--casyncsocketgetpeernameex"></a><a name="getpeernameex"></a>CAsyncSocket::GetPeerNameEx  
 调用该成员函数以获取此套接字是连接 （句柄 IPv6 地址） 的对等方套接字地址。  
  
```  
BOOL GetPeerNameEx(
    CString& rPeerAddress,  
    UINT& rPeerPort);
```  
  
### <a name="parameters"></a>参数  
 `rPeerAddress`  
 引用`CString`对象，它接收的以点分隔的数字 IP 地址。  
  
 `rPeerPort`  
 引用**UINT**存储一个端口。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0 和特定错误代码可以检索通过调用[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpSockAddrLen`参数不是足够大。  
  
- **返回 WSAEINPROGRESS**阻止 Windows 套接字调用正在进行。  
  
- **WSAENOTCONN**套接字未连接。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 此函数相当于[CAsyncSocket::GetPeerName](#getpeername)之处在于它可以处理 IPv6 地址也较旧的协议。  
  
##  <a name="a-namegetsocknamea--casyncsocketgetsockname"></a><a name="getsockname"></a>CAsyncSocket::GetSockName  
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
 引用`CString`对象，它接收的以点分隔的数字 IP 地址。  
  
 `rSocketPort`  
 引用**UINT**存储一个端口。  
  
 `lpSockAddr`  
 一个指向[SOCKADDR](../../mfc/reference/sockaddr-structure.md)接收套接字地址结构。  
  
 `lpSockAddrLen`  
 中的地址的长度的指针`lpSockAddr`以字节为单位。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0 和特定错误代码可以检索通过调用[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpSockAddrLen`参数不是足够大。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEINVAL**套接字尚未绑定到具有的地址**绑定**。  
  
### <a name="remarks"></a>备注  
 此调用时尤其有用**连接**已拨通而无需这样做**绑定**第一次; 此调用将提供通过它可以确定已由系统设置的本地关联的唯一方法。  
  
 若要处理 IPv6 地址，使用[CAsyncSocket::GetSockNameEx](#getsocknameex)  
  
##  <a name="a-namegetsocknameexa--casyncsocketgetsocknameex"></a><a name="getsocknameex"></a>CAsyncSocket::GetSockNameEx  
 调用此成员函数可获取套接字 （句柄 IPv6 地址） 的本地名称。  
  
```  
BOOL GetSockNameEx(
    CString& rSocketAddress,  
    UINT& rSocketPort);
```  
  
### <a name="parameters"></a>参数  
 `rSocketAddress`  
 引用`CString`对象，它接收的以点分隔的数字 IP 地址。  
  
 `rSocketPort`  
 引用**UINT**存储一个端口。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0 和特定错误代码可以检索通过调用[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpSockAddrLen`参数不是足够大。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEINVAL**套接字尚未绑定到具有的地址**绑定**。  
  
### <a name="remarks"></a>备注  
 此调用是相同[CAsyncSocket::GetSockName](#getsockname)之处在于它可以处理 IPv6 地址也较旧的协议。  
  
 此调用时尤其有用**连接**已拨通而无需这样做**绑定**第一次; 此调用将提供通过它可以确定已由系统设置的本地关联的唯一方法。  
  
##  <a name="a-namegetsockopta--casyncsocketgetsockopt"></a><a name="getsockopt"></a>CAsyncSocket::GetSockOpt  
 调用此成员函数以检索套接字选项。  
  
```  
BOOL GetSockOpt(
    int nOptionName,  
    void* lpOptionValue,  
    int* lpOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>参数  
 `nOptionName`  
 为其值是要检索的套接字选项。  
  
 `lpOptionValue`  
 指向在其中请求的选项的值是要返回的缓冲区的指针。 在缓冲区中返回与所选选项相关联的值`lpOptionValue`。 指向整数`lpOptionLen`最初应包含以字节为单位; 此缓冲区的大小，并且在返回时，它将设置为返回的值的大小。 有关**SO_LINGER**，这将是大小`LINGER`结构; 对于所有其他选项，它将被的大小**BOOL**或`int`，具体选项取决于。 请参阅选项及其大小在备注部分中的列表。  
  
 `lpOptionLen`  
 指针指向的大小`lpOptionValue`以字节为单位的缓冲区。  
  
 `nLevel`  
 在其中定义了选项; 级别仅支持的级别为**SOL_SOCKET**和**IPPROTO_TCP**。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0 和特定错误代码可以检索通过调用[GetLastError](#getlasterror)。 如果具有永远不会设置一个选项`SetSockOpt`，然后`GetSockOpt`返回选项的默认值。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpOptionLen`参数无效。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAENOPROTOOPT**的选项是未知或不受支持。 特别是， **SO_BROADCAST**不支持对类型的套接字**SOCK_STREAM**，尽管**SO_ACCEPTCONN**， **SO_DONTLINGER**， **SO_KEEPALIVE**， **SO_LINGER**，和**SO_OOBINLINE**不支持对类型的套接字**SOCK_DGRAM**。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 `GetSockOpt`检索与任何状态中的任何类型的套接字关联的套接字选项的当前值并将存储中的结果`lpOptionValue`。 选项会影响套接字操作，如路由数据包，带外数据传输，诸如此类。  
  
 为支持以下选项`GetSockOpt`。 类型标识的寻址的数据类型`lpOptionValue`。 **TCP_NODELAY**选项使用级别**IPPROTO_TCP**; 所有其他选项，请使用级别**SOL_SOCKET**。  
  
|值|类型|含义|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|套接字正在侦听。|  
|**SO_BROADCAST**|**BOOL**|套接字已配置为广播消息的传输。|  
|**SO_DEBUG**|**BOOL**|启用调试。|  
|**SO_DONTLINGER**|**BOOL**|如果为 true， **SO_LINGER**选项处于禁用状态。|  
|**SO_DONTROUTE**|**BOOL**|路由处于禁用状态。|  
|**SO_ERROR**|`int`|检索有关错误的状态并清除。|  
|**SO_KEEPALIVE**|**BOOL**|Keep-alive 将被发送。|  
|**SO_LINGER**|**LINGER 结构**|返回当前延迟选项。|  
|**SO_OOBINLINE**|**BOOL**|带外数据正在接收正常数据流中。|  
|**SO_RCVBUF**|`int`|接收缓冲区大小。|  
|**SO_REUSEADDR**|**BOOL**|套接字可以绑定到的地址已在使用该地址。|  
|**SO_SNDBUF**|`int`|发送缓冲区大小。|  
|**SO_TYPE**|`int`|套接字类型 (例如， **SOCK_STREAM**)。|  
|**TCP_NODELAY**|**BOOL**|为发送合并禁用 Nagle 算法。|  
  
 不支持的 Berkeley 软件分发 (BSD) 选项`GetSockOpt`是︰  
  
|值|类型|含义|  
|-----------|----------|-------------|  
|**SO_RCVLOWAT**|`int`|收到的低水印。|  
|**SO_RCVTIMEO**|`int`|接收超时。|  
|**SO_SNDLOWAT**|`int`|发送的低水印。|  
|**SO_SNDTIMEO**|`int`|发送超时。|  
|**IP_OPTIONS**||会显示在 IP 标头中的选项。|  
|**TCP_MAXSEG**|`int`|获取 TCP 最大段大小。|  
  
 调用`GetSockOpt`使用不受支持的选项将导致的错误代码为**WSAENOPROTOOPT**从重返回`GetLastError`。  
  
##  <a name="a-nameioctla--casyncsocketioctl"></a><a name="ioctl"></a>CAsyncSocket::IOCtl  
 调用此成员函数可控制套接字的模式。  
  
```  
BOOL IOCtl(
    long lCommand,  
    DWORD* lpArgument);
```  
  
### <a name="parameters"></a>参数  
 `lCommand`  
 要执行的套接字上的命令。  
  
 `lpArgument`  
 指向参数的指针`lCommand`。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0 和特定错误代码可以检索通过调用[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEINVAL** `lCommand`不是有效的命令，或`lpArgument`不是可接受参数`lCommand`，或该命令不是适用于该类型提供的套接字。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 可以在任何状态的任何套接字上使用此例程。 它用于获取或检索与套接字，独立于协议和通信子系统相关联的操作参数。 支持下列命令︰  
  
- **FIONBIO**启用或禁用非阻止模式套接字上的。 `lpArgument`参数指向`DWORD`，即如果非阻止模式下将启用，则非零值并为零被禁用。 如果`AsyncSelect`上发出套接字时，则若要使用的任何尝试**IOCtl**设置回阻止模式套接字将失败，并**WSAEINVAL**。 若要将重置为阻止模式套接字并防止**WSAEINVAL**错误，应用程序，首先必须禁用`AsyncSelect`通过调用`AsyncSelect`与`lEvent`参数等于 0，然后调用**IOCtl**。  
  
- **FIONREAD**确定最大可以与一个读取的字节数**接收**从此套接字调用。 `lpArgument`参数指向`DWORD`顺序**IOCtl**存储结果。 如果此套接字类型**SOCK_STREAM**， **FIONREAD**在单个返回的数据可以读取总量**接收**; 这是正常情况下相同的为套接字上排队的总数据量。 如果此套接字类型**SOCK_DGRAM**， **FIONREAD**返回第一个数据报的大小的套接字上排队。  
  
- **SIOCATMARK**确定是否已读取所有带外数据。 这仅适用于类型的套接字**SOCK_STREAM**其已配置为带外的任何数据行中接收 ( **SO_OOBINLINE**)。 如果等待没有带外数据可供读取，则该操作将返回非零值。 否则返回 0，并且下一个**接收**或`ReceiveFrom`上执行套接字将检索某些或所有前面的"标记"的数据; 该应用程序应使用**SIOCATMARK**运算来确定是否保留了任何数据。 如果没有任何普通的数据，前面的"紧急"（带内） 数据，它将按顺序接收。 (请注意，**接收**或`ReceiveFrom`永远不会将混合使用相同的调用中的带外和正常数据。)`lpArgument`参数指向`DWORD`顺序**IOCtl**存储结果。  
  
 此函数是子集**ioctl()**当用在 Berkeley 套接字。 特别是，没有命令等效于**FIOASYNC**，尽管**SIOCATMARK**是只套接字级别命令这受支持。  
  
##  <a name="a-namelistena--casyncsocketlisten"></a><a name="listen"></a>CAsyncSocket::Listen  
 调用该成员函数以侦听传入连接请求。  
  
```  
BOOL Listen(int nConnectionBacklog = 5);
```  
  
### <a name="parameters"></a>参数  
 *nConnectionBacklog*  
 挂起的连接的队列可能增长到的最大长度。 有效范围是从 1 到 5。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0 和特定错误代码可以检索通过调用[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEADDRINUSE**尝试侦听地址正在使用中。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEINVAL**尚未与绑定套接字**绑定**或已连接。  
  
- **WSAEISCONN**套接字已连接。  
  
- **WSAEMFILE**没有更多的文件描述符。  
  
- `WSAENOBUFS`没有缓冲区空间不可用。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP**引用套接字的支持的类型不是`Listen`操作。  
  
### <a name="remarks"></a>备注  
 为接受连接，首先需要创建套接字与**创建**，使用指定的传入连接积压`Listen`，然后使用接受连接和**接受**。 `Listen`仅适用于套接字，即支持连接，这些类型**SOCK_STREAM**。 此套接字被放入"被动"模式下，确认且队列由进程中的挂起接受传入连接。  
  
 此函数通常由服务器 （或想要接受连接的任何应用程序），可以一次有多个连接请求︰ 如果与完整的队列中收到连接请求，客户端将收到一条含有相对值的指示**WSAECONNREFUSED**。  
  
 `Listen`尝试继续正常工作理性时没有可用的端口 （描述符）。 之前该队列为空，它将接受连接。 如果端口可用后，稍后调用`Listen`或**接受**将重新填充队列向当前或最近"积压工作中，"如果可能，并重新开始侦听传入连接。  
  
##  <a name="a-namemhsocketa--casyncsocketmhsocket"></a><a name="m_hsocket"></a>CAsyncSocket::m_hSocket  
 包含**套接字**处理为套接字封装由此`CAsyncSocket`对象。  
  
```  
SOCKET m_hSocket;  
```  
  
##  <a name="a-nameonaccepta--casyncsocketonaccept"></a><a name="onaccept"></a>CAsyncSocket::OnAccept  
 由框架调用以通知它可以通过调用接受挂起的连接请求的侦听套接字[接受](#accept)成员函数。  
  
```  
virtual void OnAccept(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 `nErrorCode`  
 套接字上最新的错误。 以下的错误代码适用于`OnAccept`成员函数︰  
  
- **0**已成功执行的函数。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[Windows 套接字︰ 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="a-nameonclosea--casyncsocketonclose"></a><a name="onclose"></a>CAsyncSocket::OnClose  
 由框架来通知此套接字已连接套接字已由其进程关闭调用。  
  
```  
virtual void OnClose(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 `nErrorCode`  
 套接字上最新的错误。 以下的错误代码适用于`OnClose`成员函数︰  
  
- **0**已成功执行的函数。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAECONNRESET**的远程端重置连接。  
  
- **WSAECONNABORTED**连接已中止由于超时或其他故障。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[Windows 套接字︰ 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="a-nameonconnecta--casyncsocketonconnect"></a><a name="onconnect"></a>CAsyncSocket::OnConnect  
 由框架来通知此连接的套接字完成其连接尝试是否成功或错误地调用。  
  
```  
virtual void OnConnect(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 `nErrorCode`  
 套接字上最新的错误。 以下的错误代码适用于`OnConnect`成员函数︰  
  
- **0**已成功执行的函数。  
  
- **WSAEADDRINUSE**指定的地址已在使用。  
  
- **WSAEADDRNOTAVAIL**指定的地址不在本地计算机中可用。  
  
- **WSAEAFNOSUPPORT**用这个套接字，不能使用指定系列中的地址。  
  
- **WSAECONNREFUSED**强制性拒绝尝试连接。  
  
- **WSAEDESTADDRREQ**目标地址是必需的。  
  
- **WSAEFAULT** `lpSockAddrLen`参数不正确。  
  
- **WSAEINVAL**套接字已绑定到一个地址。  
  
- **WSAEISCONN**套接字已连接。  
  
- **WSAEMFILE**没有更多的文件描述符。  
  
- **WSAENETUNREACH**网络不能将从此主机访问这一次。  
  
- `WSAENOBUFS`没有缓冲区空间不可用。 无法连接套接字。  
  
- **WSAENOTCONN**套接字未连接。  
  
- **WSAENOTSOCK**描述符是一个文件，不是一个套接字。  
  
- **WSAETIMEDOUT**尝试连接超时而无需建立一个连接。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  在[CSocket](../../mfc/reference/csocket-class.md)、`OnConnect`在于︰ 绝不调用通知函数。 对于连接，您只需调用**连接**，它将返回完成连接后 （成功或错误）。 如何处理连接通知是 MFC 实现的细节。  
  
 有关详细信息，请参阅[Windows 套接字︰ 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAsyncSocket #&1;](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]  
  
##  <a name="a-nameonoutofbanddataa--casyncsocketonoutofbanddata"></a><a name="onoutofbanddata"></a>CAsyncSocket::OnOutOfBandData  
 由框架用于通知的接收套接字上发送的套接字有要发送的带外数据调用。  
  
```  
virtual void OnOutOfBandData(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 `nErrorCode`  
 套接字上最新的错误。 以下的错误代码适用于`OnOutOfBandData`成员函数︰  
  
- **0**已成功执行的函数。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
### <a name="remarks"></a>备注  
 带外数据是与已连接套接字类型的每一对相关联的逻辑上独立通道**SOCK_STREAM**。 通道通常用于发送紧急数据。  
  
 MFC 支持带外数据，但类的用户`CAsyncSocket`我们建议您不要使用它。 更简便的方法是创建第二个套接字来传递此类数据。 有关带外数据的详细信息，请参阅[Windows 套接字︰ 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="a-nameonreceivea--casyncsocketonreceive"></a><a name="onreceive"></a>CAsyncSocket::OnReceive  
 由框架调用以通知此套接字可以通过调用检索到的缓冲区中没有数据**接收**成员函数。  
  
```  
virtual void OnReceive(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 `nErrorCode`  
 套接字上最新的错误。 以下的错误代码适用于`OnReceive`成员函数︰  
  
- **0**已成功执行的函数。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[Windows 套接字︰ 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAsyncSocket #&2;](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]  
  
##  <a name="a-nameonsenda--casyncsocketonsend"></a><a name="onsend"></a>CAsyncSocket::OnSend  
 由框架调用以通知套接字，它现在可通过调用来发送数据**发送**成员函数。  
  
```  
virtual void OnSend(int nErrorCode);
```  
  
### <a name="parameters"></a>参数  
 `nErrorCode`  
 套接字上最新的错误。 以下的错误代码适用于`OnSend`成员函数︰  
  
- **0**已成功执行的函数。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[Windows 套接字︰ 套接字通知](../../mfc/windows-sockets-socket-notifications.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAsyncSocket #&3;](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]  
  
##  <a name="a-nameoperatoreqa--casyncsocketoperator-"></a><a name="operator_eq"></a>CAsyncSocket::operator =  
 将一个新值赋给`CAsyncSocket`对象。  
  
```  
void operator=(const CAsyncSocket& rSrc);
```  
  
### <a name="parameters"></a>参数  
 `rSrc`  
 对现有的引用`CAsyncSocket`对象。  
  
### <a name="remarks"></a>备注  
 调用此函数可复制现有`CAsyncSocket`对象传递给另一个`CAsyncSocket`对象。  
  
##  <a name="a-nameoperatorsocketa--casyncsocketoperator-socket"></a><a name="operator_socket"></a>CAsyncSocket::operator 套接字  
 使用此运算符可检索**套接字**的 handle`CAsyncSocket`对象。  
  
```  
operator SOCKET() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功的句柄**套接字**对象; 否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 该句柄可用于直接调用 Windows Api。  
  
##  <a name="a-namereceivea--casyncsocketreceive"></a><a name="receive"></a>CAsyncSocket::Receive  
 调用该成员函数以从套接字接收数据。  
  
```  
virtual int Receive(
    void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>参数  
 `lpBuf`  
 对于传入的数据缓冲区。  
  
 `nBufLen`  
 长度`lpBuf`以字节为单位。  
  
 `nFlags`  
 指定在其中进行调用的方式。 此函数的语义由套接字选项和`nFlags`参数。 后者通过组合构成的以下值中任意使用 c + +`OR`运算符︰  
  
- **MSG_PEEK**扫视传入数据。 数据复制到缓冲区，但不是会从输入队列中删除。  
  
- **MSG_OOB**处理带外数据。  
  
### <a name="return-value"></a>返回值  
 如果没有出现错误，**接收**返回接收的字节数。 如果连接已关闭，则返回 0。 否则为值为**SOCKET_ERROR**返回，并且可以通过调用检索特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAENOTCONN**套接字未连接。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP MSG_OOB**指定了，但对套接字类型不是**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**的套接字关闭; 不能调用**接收**后套接字上`ShutDown`已调用了与`nHow`设置为 0 或 2。  
  
- **WSAEWOULDBLOCK**套接字被标记为非阻塞和**接收**操作将阻塞。  
  
- **WSAEMSGSIZE**数据报太大，以至于无法放入指定的缓冲区且已被截断。  
  
- **WSAEINVAL**尚未与绑定套接字**绑定**。  
  
- **WSAECONNABORTED**由于超时或其他故障虚拟线路已中止。  
  
- **WSAECONNRESET**虚拟线路已重置的远程端。  
  
### <a name="remarks"></a>备注  
 此函数用于连接的流或数据报套接字，用于读取传入的数据。  
  
 对于类型的套接字**SOCK_STREAM**，如返回目前提供的缓冲区的大小最多的信息。 如果已配置为行中的带外数据的接收套接字 (套接字选项**SO_OOBINLINE**) 和带外数据为未读，则将返回仅带外的扩展数据。 应用程序可以使用**IOCtlSIOCATMARK**选项或[OnOutOfBandData](#onoutofbanddata)以确定是否任何更多的带数据将保留可供读取。  
  
 对于数据报套接字，从第一个排队数据报，直到达到提供的缓冲区的大小被提取数据。 数据报大于提供的缓冲区，如果与数据报的第一个部分填充了缓冲区，多余的数据将丢失，并且**接收**返回的值为**SOCKET_ERROR**并提供错误代码设置为**WSAEMSGSIZE**。 如果没有传入数据则可以从套接字，值为**SOCKET_ERROR**并提供错误代码设置为返回**WSAEWOULDBLOCK**。 [OnReceive](#onreceive)回调函数可以用于确定当更多数据到达时。  
  
 如果套接字类型**SOCK_STREAM** ，远程端已经正常，关闭该连接**接收**将立即完成并接收到的 0 字节。 如果连接已被重置，**接收**将失败，出现错误**WSAECONNRESET**。  
  
 **接收**应为每次只有一次调用[CAsyncSocket::OnReceive](#onreceive)调用。  
  
### <a name="example"></a>示例  
  请参阅示例[CAsyncSocket::OnReceive](#onreceive)。  
  
##  <a name="a-namereceivefroma--casyncsocketreceivefrom"></a><a name="receivefrom"></a>CAsyncSocket::ReceiveFrom  
 调用此成员函数来接收数据报和存储中的源地址[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构中或在`rSocketAddress`。  
  
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
 对于传入的数据缓冲区。  
  
 `nBufLen`  
 长度`lpBuf`以字节为单位。  
  
 `rSocketAddress`  
 引用`CString`对象，它接收的以点分隔的数字 IP 地址。  
  
 `rSocketPort`  
 引用**UINT**存储一个端口。  
  
 `lpSockAddr`  
 一个指向[SOCKADDR](../../mfc/reference/sockaddr-structure.md)保留在返回的源地址的结构。  
  
 `lpSockAddrLen`  
 中的源地址的长度的指针`lpSockAddr`以字节为单位。  
  
 `nFlags`  
 指定在其中进行调用的方式。 此函数的语义由套接字选项和`nFlags`参数。 后者通过组合构成的以下值中任意使用 c + +`OR`运算符︰  
  
- **MSG_PEEK**扫视传入数据。 数据复制到缓冲区，但不是会从输入队列中删除。  
  
- **MSG_OOB**处理带外数据。  
  
### <a name="return-value"></a>返回值  
 如果没有出现错误，`ReceiveFrom`返回接收的字节数。 如果连接已关闭，则返回 0。 否则为值为**SOCKET_ERROR**返回，并且可以通过调用检索特定的错误代码`GetLastError`。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpSockAddrLen`参数无效︰`lpSockAddr`缓冲区是否太小，无法容纳的对等方地址。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEINVAL**尚未与绑定套接字**绑定**。  
  
- **WSAENOTCONN**套接字未连接 ( **SOCK_STREAM**仅)。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP MSG_OOB**指定了，但对套接字类型不是**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**的套接字关闭; 不能调用`ReceiveFrom`后套接字上`ShutDown`已调用了与`nHow`设置为 0 或 2。  
  
- **WSAEWOULDBLOCK**套接字被标记为非阻塞和`ReceiveFrom`操作将阻塞。  
  
- **WSAEMSGSIZE**数据报太大，以至于无法放入指定的缓冲区且已被截断。  
  
- **WSAECONNABORTED**由于超时或其他故障虚拟线路已中止。  
  
- **WSAECONNRESET**虚拟线路已重置的远程端。  
  
### <a name="remarks"></a>备注  
 此函数用于读取传入的数据 （可能是连接） 套接字上并捕获从其发送数据的地址。  
  
 若要处理 IPv6 地址，使用[CAsyncSocket::ReceiveFromEx](#receivefromex)。  
  
 对于类型的套接字**SOCK_STREAM**，如返回目前提供的缓冲区的大小最多的信息。 如果已配置为行中的带外数据的接收套接字 (套接字选项**SO_OOBINLINE**) 和带外数据为未读，则将返回仅带外的扩展数据。 应用程序可以使用**IOCtlSIOCATMARK**选项或`OnOutOfBandData`以确定是否任何更多的带数据将保留可供读取。 `lpSockAddr`和`lpSockAddrLen`将忽略**SOCK_STREAM**套接字。  
  
 对于数据报套接字，从第一个排队数据报，直到达到提供的缓冲区的大小被提取数据。 如果数据报大于提供的缓冲区，与消息的第一个部分填充了缓冲区，多余的数据将丢失，并且`ReceiveFrom`返回的值为**SOCKET_ERROR**并提供错误代码设置为**WSAEMSGSIZE**。  
  
 如果`lpSockAddr`不为零，并且对套接字类型是**SOCK_DGRAM**，将它发送数据的套接字的网络地址复制到相应[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构。 指向的值`lpSockAddrLen`初始化为此结构的大小并返回指示的地址存储在那里的实际大小上修改。 如果没有传入数据在套接字，可用`ReceiveFrom`呼叫等待数据到达除非套接字是阻塞。 在这种情况下，值为**SOCKET_ERROR**并提供错误代码设置为返回**WSAEWOULDBLOCK**。 `OnReceive`回调可以用于确定当更多数据到达时。  
  
 如果套接字类型**SOCK_STREAM** ，远程端已经正常，关闭该连接`ReceiveFrom`将立即完成并接收到的 0 字节。  
  
##  <a name="a-namereceivefromexa--casyncsocketreceivefromex"></a><a name="receivefromex"></a>CAsyncSocket::ReceiveFromEx  
 调用此成员函数来接收数据报和存储中的源地址[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构中或在`rSocketAddress`（处理 IPv6 地址）。  
  
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
 对于传入的数据缓冲区。  
  
 `nBufLen`  
 长度`lpBuf`以字节为单位。  
  
 `rSocketAddress`  
 引用`CString`对象，它接收的以点分隔的数字 IP 地址。  
  
 `rSocketPort`  
 引用**UINT**存储一个端口。  
  
 `nFlags`  
 指定在其中进行调用的方式。 此函数的语义由套接字选项和`nFlags`参数。 后者通过组合构成的以下值中任意使用 c + +`OR`运算符︰  
  
- **MSG_PEEK**扫视传入数据。 数据复制到缓冲区，但不是会从输入队列中删除。  
  
- **MSG_OOB**处理带外数据。  
  
### <a name="return-value"></a>返回值  
 如果没有出现错误，`ReceiveFromEx`返回接收的字节数。 如果连接已关闭，则返回 0。 否则为值为**SOCKET_ERROR**返回，并且可以通过调用检索特定的错误代码`GetLastError`。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpSockAddrLen`参数无效︰`lpSockAddr`缓冲区是否太小，无法容纳的对等方地址。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEINVAL**尚未与绑定套接字**绑定**。  
  
- **WSAENOTCONN**套接字未连接 ( **SOCK_STREAM**仅)。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP MSG_OOB**指定了，但对套接字类型不是**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**的套接字关闭; 不能调用`ReceiveFromEx`后套接字上`ShutDown`已调用了与`nHow`设置为 0 或 2。  
  
- **WSAEWOULDBLOCK**套接字被标记为非阻塞和`ReceiveFromEx`操作将阻塞。  
  
- **WSAEMSGSIZE**数据报太大，以至于无法放入指定的缓冲区且已被截断。  
  
- **WSAECONNABORTED**由于超时或其他故障虚拟线路已中止。  
  
- **WSAECONNRESET**虚拟线路已重置的远程端。  
  
### <a name="remarks"></a>备注  
 此函数用于读取传入的数据 （可能是连接） 套接字上并捕获从其发送数据的地址。  
  
 此函数相当于[CAsyncSocket::ReceiveFrom](#receivefrom)之处在于它可以处理 IPv6 地址也较旧的协议。  
  
 对于类型的套接字**SOCK_STREAM**，如返回目前提供的缓冲区的大小最多的信息。 如果已配置为行中的带外数据的接收套接字 (套接字选项**SO_OOBINLINE**) 和带外数据为未读，则将返回仅带外的扩展数据。 应用程序可以使用**IOCtlSIOCATMARK**选项或`OnOutOfBandData`以确定是否任何更多的带数据将保留可供读取。 `lpSockAddr`和`lpSockAddrLen`将忽略**SOCK_STREAM**套接字。  
  
 对于数据报套接字，从第一个排队数据报，直到达到提供的缓冲区的大小被提取数据。 如果数据报大于提供的缓冲区，与消息的第一个部分填充了缓冲区，多余的数据将丢失，并且`ReceiveFromEx`返回的值为**SOCKET_ERROR**并提供错误代码设置为**WSAEMSGSIZE**。  
  
 如果`lpSockAddr`不为零，并且对套接字类型是**SOCK_DGRAM**，将它发送数据的套接字的网络地址复制到相应[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构。 指向的值`lpSockAddrLen`初始化为此结构的大小并返回指示的地址存储在那里的实际大小上修改。 如果没有传入数据在套接字，可用`ReceiveFromEx`呼叫等待数据到达除非套接字是阻塞。 在这种情况下，值为**SOCKET_ERROR**并提供错误代码设置为返回**WSAEWOULDBLOCK**。 `OnReceive`回调可以用于确定当更多数据到达时。  
  
 如果套接字类型**SOCK_STREAM** ，远程端已经正常，关闭该连接`ReceiveFromEx`将立即完成并接收到的 0 字节。  
  
##  <a name="a-namesenda--casyncsocketsend"></a><a name="send"></a>CAsyncSocket::Send  
 调用该成员函数以在连接的套接字上发送数据。  
  
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
 指定在其中进行调用的方式。 此函数的语义由套接字选项和`nFlags`参数。 后者通过组合构成的以下值中任意使用 c + +`OR`运算符︰  
  
- **MSG_DONTROUTE**数据应该不会受到路由的指定。 Windows 套接字供应商可以选择忽略此标志。  
  
- **MSG_OOB**发送带外数据 ( **SOCK_STREAM**仅)。  
  
### <a name="return-value"></a>返回值  
 如果没有出现错误，**发送**返回发送字符的总数。 (请注意，这可以是由指示的数字小于`nBufLen`。)否则为值为**SOCKET_ERROR**返回，并且可以通过调用检索特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEACCES**请求的地址是广播的地址，但未设置适当的标志。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEFAULT** `lpBuf`参数不是用户地址空间的有效部分。  
  
- **WSAENETRESET**必须重置该连接，因为 Windows 套接字实现将其删除。  
  
- `WSAENOBUFS`Windows 套接字实现报告缓冲区死锁。  
  
- **WSAENOTCONN**套接字未连接。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP MSG_OOB**指定了，但对套接字类型不是**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**的套接字关闭; 不能调用**发送**后套接字上`ShutDown`已调用了与`nHow`设置为 1 或 2。  
  
- **WSAEWOULDBLOCK**套接字被标记为非阻塞和所请求的操作将阻塞。  
  
- **WSAEMSGSIZE**套接字是类型的**SOCK_DGRAM**，并且大于支持的 Windows 套接字实现最大数据报。  
  
- **WSAEINVAL**尚未与绑定套接字**绑定**。  
  
- **WSAECONNABORTED**由于超时或其他故障虚拟线路已中止。  
  
- **WSAECONNRESET**虚拟线路已重置的远程端。  
  
### <a name="remarks"></a>备注  
 **发送**用来写入已连接的流或数据报套接字上的传出数据。 对于数据报套接字，必须小心不能超过最大 IP 数据包大小的基础的子网、 向其授予通过**iMaxUdpDg**中的元素[WSADATA](../../mfc/reference/wsadata-structure.md)由返回结构`AfxSocketInit`。 如果数据太长，以原子方式通过底层协议错误**WSAEMSGSIZE**通过返回`GetLastError`，并且无数据传输。  
  
 请注意，对于数据报套接字成功完成**发送**并不表示数据已成功传递。  
  
 在`CAsyncSocket`类型的对象**SOCK_STREAM**，介于 1 和请求的长度，具体取决于本地和外来主机上的缓冲区可用性可写入的字节数。  
  
### <a name="example"></a>示例  
  请参阅示例[CAsyncSocket::OnSend](#onsend)。  
  
##  <a name="a-namesendtoa--casyncsocketsendto"></a><a name="sendto"></a>CAsyncSocket::SendTo  
 调用该成员函数以将数据发送到特定目标。  
  
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
 用于标识套接字应用程序的端口。  
  
 `lpszHostAddress`  
 此对象连接的套接字的网络地址︰ 如"ftp.microsoft.com，"或一个以点分隔的数字，如"128.56.22.8"的计算机的名称。  
  
 `nFlags`  
 指定在其中进行调用的方式。 此函数的语义由套接字选项和`nFlags`参数。 后者通过组合构成的以下值中任意使用 c + +`OR`运算符︰  
  
- **MSG_DONTROUTE**数据应该不会受到路由的指定。 Windows 套接字供应商可以选择忽略此标志。  
  
- **MSG_OOB**发送带外数据 ( **SOCK_STREAM**仅)。  
  
 `lpSockAddr`  
 一个指向[SOCKADDR](../../mfc/reference/sockaddr-structure.md)包含目标套接字地址结构。  
  
 `nSockAddrLen`  
 中的地址长度`lpSockAddr`以字节为单位。  
  
### <a name="return-value"></a>返回值  
 如果没有出现错误，`SendTo`返回发送字符的总数。 (请注意，这可以是由指示的数字小于`nBufLen`。)否则为值为**SOCKET_ERROR**返回，并且可以通过调用检索特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEACCES**请求的地址是广播的地址，但未设置适当的标志。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEFAULT** `lpBuf`或`lpSockAddr`参数不是用户地址空间的一部分或`lpSockAddr`参数是太小 (小于大小[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构)。  
  
- **WSAEINVAL**主机名无效。  
  
- **WSAENETRESET**必须重置该连接，因为 Windows 套接字实现将其删除。  
  
- `WSAENOBUFS`Windows 套接字实现报告缓冲区死锁。  
  
- **WSAENOTCONN**套接字未连接 ( **SOCK_STREAM**仅)。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP MSG_OOB**指定了，但对套接字类型不是**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**的套接字关闭; 不能调用`SendTo`后套接字上`ShutDown`已调用了与`nHow`设置为 1 或 2。  
  
- **WSAEWOULDBLOCK**套接字被标记为非阻塞和所请求的操作将阻塞。  
  
- **WSAEMSGSIZE**套接字是类型的**SOCK_DGRAM**，并且大于支持的 Windows 套接字实现最大数据报。  
  
- **WSAECONNABORTED**由于超时或其他故障虚拟线路已中止。  
  
- **WSAECONNRESET**虚拟线路已重置的远程端。  
  
- **WSAEADDRNOTAVAIL**指定的地址不在本地计算机中可用。  
  
- **WSAEAFNOSUPPORT**用这个套接字，不能使用指定系列中的地址。  
  
- **WSAEDESTADDRREQ**目标地址是必需的。  
  
- **WSAENETUNREACH**网络不能将从此主机访问这一次。  
  
### <a name="remarks"></a>备注  
 `SendTo`在数据报或流的套接字上使用，用于编写套接字上的传出数据。 对于数据报套接字，必须小心不能超过最大 IP 数据包大小的基础的子网、 向其授予通过**iMaxUdpDg**中的元素[WSADATA](../../mfc/reference/wsadata-structure.md)结构通过填写[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)。 如果数据太长，以原子方式通过底层协议错误**WSAEMSGSIZE**返回，并且无数据传输。  
  
 请注意，在成功完成`SendTo`并不表示数据已成功传递。  
  
 `SendTo`仅在上使用**SOCK_DGRAM**套接字能够为特定的套接字由标识发送的数据报`lpSockAddr`参数。  
  
 若要发送广播 (上**SOCK_DGRAM**仅) 中的地址`lpSockAddr`参数应使用专用的 IP 地址构造**INADDR_BROADCAST** （Windows 套接字标头文件 WINSOCK 中定义。H） 一起使用的目标的端口号。 或者，如果`lpszHostAddress`参数是**NULL**，套接字被配置为广播。 通常建议不要对广播数据报超出其大小从该处所出现的碎片，这表明数据报 （不包括标头） 的数据部分不应超过 512 个字节。  
  
 若要处理 IPv6 地址，使用[CAsyncSocket::SendToEx](#sendtoex)。  
  
##  <a name="a-namesendtoexa--casyncsocketsendtoex"></a><a name="sendtoex"></a>CAsyncSocket::SendToEx  
 调用该成员函数以将数据发送到特定目标 （句柄 IPv6 地址）。  
  
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
 用于标识套接字应用程序的端口。  
  
 `lpszHostAddress`  
 此对象连接的套接字的网络地址︰ 如"ftp.microsoft.com，"或一个以点分隔的数字，如"128.56.22.8"的计算机的名称。  
  
 `nFlags`  
 指定在其中进行调用的方式。 此函数的语义由套接字选项和`nFlags`参数。 后者通过组合构成的以下值中任意使用 c + +`OR`运算符︰  
  
- **MSG_DONTROUTE**数据应该不会受到路由的指定。 Windows 套接字供应商可以选择忽略此标志。  
  
- **MSG_OOB**发送带外数据 ( **SOCK_STREAM**仅)。  
  
### <a name="return-value"></a>返回值  
 如果没有出现错误，`SendToEx`返回发送字符的总数。 (请注意，这可以是由指示的数字小于`nBufLen`。)否则为值为**SOCKET_ERROR**返回，并且可以通过调用检索特定的错误代码[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEACCES**请求的地址是广播的地址，但未设置适当的标志。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEFAULT** `lpBuf`或`lpSockAddr`参数不是用户地址空间的一部分或`lpSockAddr`参数是太小 (小于大小[SOCKADDR](../../mfc/reference/sockaddr-structure.md)结构)。  
  
- **WSAEINVAL**主机名无效。  
  
- **WSAENETRESET**必须重置该连接，因为 Windows 套接字实现将其删除。  
  
- `WSAENOBUFS`Windows 套接字实现报告缓冲区死锁。  
  
- **WSAENOTCONN**套接字未连接 ( **SOCK_STREAM**仅)。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
- **WSAEOPNOTSUPP MSG_OOB**指定了，但对套接字类型不是**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**的套接字关闭; 不能调用`SendToEx`后套接字上`ShutDown`已调用了与`nHow`设置为 1 或 2。  
  
- **WSAEWOULDBLOCK**套接字被标记为非阻塞和所请求的操作将阻塞。  
  
- **WSAEMSGSIZE**套接字是类型的**SOCK_DGRAM**，并且大于支持的 Windows 套接字实现最大数据报。  
  
- **WSAECONNABORTED**由于超时或其他故障虚拟线路已中止。  
  
- **WSAECONNRESET**虚拟线路已重置的远程端。  
  
- **WSAEADDRNOTAVAIL**指定的地址不在本地计算机中可用。  
  
- **WSAEAFNOSUPPORT**用这个套接字，不能使用指定系列中的地址。  
  
- **WSAEDESTADDRREQ**目标地址是必需的。  
  
- **WSAENETUNREACH**网络不能将从此主机访问这一次。  
  
### <a name="remarks"></a>备注  
 此方法等同于[CAsyncSocket::SendTo](#sendto)之处在于它可以处理 IPv6 地址也较旧的协议。  
  
 `SendToEx`在数据报或流的套接字上使用，用于编写套接字上的传出数据。 对于数据报套接字，必须小心不能超过最大 IP 数据包大小的基础的子网、 向其授予通过**iMaxUdpDg**中的元素[WSADATA](../../mfc/reference/wsadata-structure.md)结构通过填写[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)。 如果数据太长，以原子方式通过底层协议错误**WSAEMSGSIZE**返回，并且无数据传输。  
  
 请注意，在成功完成`SendToEx`并不表示数据已成功传递。  
  
 `SendToEx`仅在上使用**SOCK_DGRAM**套接字能够为特定的套接字由标识发送的数据报`lpSockAddr`参数。  
  
 若要发送广播 (上**SOCK_DGRAM**仅) 中的地址`lpSockAddr`参数应使用专用的 IP 地址构造**INADDR_BROADCAST** （Windows 套接字标头文件 WINSOCK 中定义。H） 一起使用的目标的端口号。 或者，如果`lpszHostAddress`参数是**NULL**，套接字被配置为广播。 通常建议不要对广播数据报超出其大小从该处所出现的碎片，这表明数据报 （不包括标头） 的数据部分不应超过 512 个字节。  
  
##  <a name="a-namesetsockopta--casyncsocketsetsockopt"></a><a name="setsockopt"></a>CAsyncSocket::SetSockOpt  
 调用该成员函数以设置套接字选项。  
  
```  
BOOL SetSockOpt(
    int nOptionName,  
    const void* lpOptionValue,  
    int nOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>参数  
 `nOptionName`  
 套接字选项值要为其设置。  
  
 `lpOptionValue`  
 指向在其中提供所请求的选项的值的缓冲区的指针。  
  
 `nOptionLen`  
 大小`lpOptionValue`以字节为单位的缓冲区。  
  
 `nLevel`  
 在其中定义了选项; 级别仅支持的级别为**SOL_SOCKET**和**IPPROTO_TCP**。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0 和特定错误代码可以检索通过调用[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEFAULT** `lpOptionValue`不是有效的一部分中的进程地址空间。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAEINVAL** `nLevel`无效，或中的信息`lpOptionValue`无效。  
  
- **WSAENETRESET**连接超时时时**SO_KEEPALIVE**设置。  
  
- **WSAENOPROTOOPT**的选项是未知或不受支持。 特别是， **SO_BROADCAST**不支持对类型的套接字**SOCK_STREAM**，尽管**SO_DONTLINGER**， **SO_KEEPALIVE**， **SO_LINGER**，和**SO_OOBINLINE**不支持对类型的套接字**SOCK_DGRAM**。  
  
- **WSAENOTCONN**连接已重置时**SO_KEEPALIVE**设置。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 `SetSockOpt`设置与中的任何状态的任何类型的套接字关联的套接字选项的当前值。 尽管选项可以在多个协议级别存在，该规范仅定义位于最顶部的"套接字"级别的选项。 选项会影响套接字操作，如是否加急的数据中接收正常数据流是否广播的消息可以发送的套接字上，依次类推。  
  
 有两种类型的套接字选项︰ 用于启用或禁用功能或行为，布尔选项以及需要的一个整数值或结构的选项。 若要启用布尔选项，`lpOptionValue`指向非零的整数。 若要禁用选项`lpOptionValue`指向等于零的整数。 `nOptionLen`应等于**sizeof （bool)**布尔选项。 有关其他选项，`lpOptionValue`指向整数或结构，其中包含选项，所需的值和`nOptionLen`是整数或结构的长度。  
  
 **SO_LINGER**控件时所采取的操作未发送的数据是否已排队的插座和**关闭**调用函数来关闭套接字。  
  
 默认情况下，不能将绑定套接字 (请参阅[绑定](#bind)) 到其已在使用本地地址。 有时，但是，它可能需要"重新使用"这种方式中的一个地址。 因为由本地和远程地址的组合唯一标识每个连接，所以也具有绑定到相同的本地地址，只要远程地址是不同的两个插座没问题。  
  
 通知 Windows 套接字实现的**绑定**应不允许在套接字上的调用，因为所需的地址已被另一套接字使用、 应用程序应设置**SO_REUSEADDR**套接字的套接字选项之前发出**绑定**调用。 请注意，该选项只在的时间解释**绑定**调用︰ 因此是不必要 （但是无害） 将在套接字它并不是绑定到一个现有地址，选项设置以及设置或重置之后选项**绑定**调用具有对此没有影响或任何其他套接字。  
  
 应用程序可以请求 Windows 套接字实现通过开启启用"保持活动状态"上的数据包的传输控制协议 (TCP) 连接使用**SO_KEEPALIVE**套接字选项。 Windows 套接字实现不需要支持 keep-alive 利用︰ 如果是这样的精确语义是特定于实现的但应符合 4.2.3.6 的 RFC 1122:"Internet 主机要求-通信层。" 如果删除连接"keep-alive"因而产生的错误代码**WSAENETRESET**套接字，返回到正在进行的任何调用，任何后续调用将失败并**WSAENOTCONN**。  
  
 **TCP_NODELAY**选项禁用 Nagle 算法。 Nagle 算法用于减少通过缓冲未确认的发送数据，直到可以发送一个完全尺寸的数据包由主机发送的小型数据包数。 但是，对于某些应用程序此算法可能会降低性能，并**TCP_NODELAY**可用来将其关闭。 应用程序编写器不应设置**TCP_NODELAY**除非执行此操作的影响是易于理解和所需的因为设置**TCP_NODELAY**会对网络性能产生明显的负面影响。 **TCP_NODELAY**是唯一支持的套接字选项的使用级别**IPPROTO_TCP**; 所有其他选项，请使用级别**SOL_SOCKET**。  
  
 Windows 套接字提供某些实现输出调试信息，如果**SO_DEBUG**基于应用程序设置选项。  
  
 为支持以下选项`SetSockOpt`。 类型标识的寻址的数据类型`lpOptionValue`。  
  
|值|类型|含义|  
|-----------|----------|-------------|  
|**SO_BROADCAST**|**BOOL**|允许在套接字上的广播消息的传输。|  
|**SO_DEBUG**|**BOOL**|记录调试信息。|  
|**SO_DONTLINGER**|**BOOL**|不要阻止**关闭**等待未发送的数据被发送。 设置此选项等效于设置**SO_LINGER**与**l_onoff**将设置为零。|  
|**SO_DONTROUTE**|**BOOL**|不路由︰ 直接对接口发送。|  
|**SO_KEEPALIVE**|**BOOL**|发送 keep-alive。|  
|**SO_LINGER**|**LINGER 结构**|在逗留**关闭**如果未发送的数据是否存在。|  
|**SO_OOBINLINE**|**BOOL**|接收正常数据流中的带外数据。|  
|**SO_RCVBUF**|`int`|指定接收缓冲区大小。|  
|**SO_REUSEADDR**|**BOOL**|允许将套接字绑定到的地址已在使用该地址。 (See [Bind](#bind).)|  
|**SO_SNDBUF**|`int`|指定发送的缓冲区大小。|  
|**TCP_NODELAY**|**BOOL**|为发送合并禁用 Nagle 算法。|  
  
 不支持的 Berkeley 软件分发 (BSD) 选项`SetSockOpt`是︰  
  
|值|类型|含义|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|套接字正在侦听|  
|**SO_ERROR**|`int`|获取错误状态并清除。|  
|**SO_RCVLOWAT**|`int`|收到的低水印。|  
|**SO_RCVTIMEO**|`int`|接收超时|  
|**SO_SNDLOWAT**|`int`|发送的低水印。|  
|**SO_SNDTIMEO**|`int`|发送超时。|  
|**SO_TYPE**|`int`|套接字类型。|  
|**IP_OPTIONS**||在 IP 标头中设置选项字段。|  
  
##  <a name="a-nameshutdowna--casyncsocketshutdown"></a><a name="shutdown"></a>CAsyncSocket::ShutDown  
 调用该成员函数以禁用发送时，收到，或两者的套接字上。  
  
```  
BOOL ShutDown(int nHow = sends);
```  
  
### <a name="parameters"></a>参数  
 `nHow`  
 介绍哪些类型的操作的标志将不再允许使用，使用下列枚举的值︰  
  
- **接收 = 0**  
  
- **将发送 = 1**  
  
- **同时 = 2**  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0 和特定错误代码可以检索通过调用[GetLastError](#getlasterror)。 以下错误适用于该成员函数︰  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)使用此 API 之前必须发生。  
  
- **WSAENETDOWN** Windows 套接字实现检测到的网络子系统失败。  
  
- **WSAEINVAL** `nHow`无效。  
  
- **返回 WSAEINPROGRESS**正在阻塞的 Windows 套接字操作。  
  
- **WSAENOTCONN**套接字未连接 ( **SOCK_STREAM**仅)。  
  
- **WSAENOTSOCK**描述符不是一个套接字。  
  
### <a name="remarks"></a>备注  
 `ShutDown`用于在所有类型的套接字上接收和 / 或传输，禁用。 如果`nHow`为 0，则后续接收的套接字将不允许。 这没有任何影响较低的协议层上。  
  
 有关传输控制协议 (TCP) TCP 窗口中不会更改并且传入的数据将会接受 （但不是确认），直到用尽窗口中。 有关用户数据报协议 (UDP) 传入的数据报接受并排队。 将在任何情况下生成 ICMP 错误数据包。 如果`nHow`为 1，随后将被禁用。 对于 TCP 套接字中，将发送 FIN。 设置`nHow`为 2 同时禁用发送和接收上文所述。  
  
 请注意，`ShutDown`不关闭连接到套接字的套接字，不会被释放之前**关闭**调用。 应用程序不应依赖于能够后关闭。 重新使用套接字。 特别是，Windows 套接字实现不需要支持使用**连接**此类套接字上。  
  
### <a name="example"></a>示例  
  请参阅示例[CAsyncSocket::OnReceive](#onreceive)。  
  
##  <a name="a-namesocketa--casyncsocketsocket"></a><a name="socket"></a>CASyncSocket::Socket  
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
 指定在其中应用程序感兴趣的网络事件的组合的位掩码。  
  
- `FD_READ`︰ 想要接收通知的准备工作以进行读取。  
  
- `FD_WRITE`︰ 想要接收通知的准备工作以进行写入。  
  
- `FD_OOB`︰ 想要接收通知的带外数据的到达。  
  
- `FD_ACCEPT`︰ 想要接收通知的传入连接。  
  
- `FD_CONNECT`︰ 想要接收通知的已完成的连接。  
  
- `FD_CLOSE`︰ 想要接收通知的套接字关闭。  
  
 `nProtocolType`  
 若要与特定于所指示的地址族的套接字一起使用的协议。  
  
 `nAddressFormat`  
 地址族的规范。  
  
### <a name="return-value"></a>返回值  
 成功时返回 `TRUE`，失败时返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 该方法分配套接字句柄。 它没有调用[CAsyncSocket::Bind](#bind)将套接字绑定到指定的地址，以使您需要调用`Bind`更高版本才能将套接字绑定到指定的地址。 您可以使用[CAsyncSocket::SetSockOpt](#setsockopt)之前它所绑定设置套接字选项。  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CSocket 类](../../mfc/reference/csocket-class.md)   
 [CSocketFile 类](../../mfc/reference/csocketfile-class.md)

