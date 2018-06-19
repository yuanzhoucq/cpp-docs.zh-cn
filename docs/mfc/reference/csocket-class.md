---
title: CSocket 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CSocket [MFC], CSocket
- CSocket [MFC], Attach
- CSocket [MFC], CancelBlockingCall
- CSocket [MFC], Create
- CSocket [MFC], FromHandle
- CSocket [MFC], IsBlocking
- CSocket [MFC], OnMessagePending
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0bfaf418ec78a750f6030683801d00a1450364d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375598"
---
# <a name="csocket-class"></a>CSocket 类
派生自`CAsyncSocket`、 继承其封装 Windows 套接字 API 中，并表示比更高级别的抽象`CAsyncSocket`对象。  
  
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
|[CSocket::Attach](#attach)|将附加**套接字**的句柄`CSocket`对象。|  
|[CSocket::CancelBlockingCall](#cancelblockingcall)|取消当前正在进行一个阻塞调用。|  
|[CSocket::Create](#create)|创建套接字。|  
|[CSocket::FromHandle](#fromhandle)|返回一个指向`CSocket`给定的对象**套接字**处理。|  
|[CSocket::IsBlocking](#isblocking)|确定是否正在执行阻止调用。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSocket::OnMessagePending](#onmessagepending)|在等待阻塞调用完成时调用以挂起消息的处理。|  
  
## <a name="remarks"></a>备注  
 `CSocket` 适用于类`CSocketFile`和`CArchive`来管理发送和接收数据。  
  
 A`CSocket`对象还提供了阻止，这是至关重要的同步操作`CArchive`。 阻止函数，如`Receive`， `Send`， `ReceiveFrom`， `SendTo`，和`Accept`(从所有继承`CAsyncSocket`)，不会返回`WSAEWOULDBLOCK`中的错误`CSocket`。 相反，这些函数等待，直到操作完成。 此外，原始调用将终止并出现错误`WSAEINTR`如果`CancelBlockingCall`时这些函数之一的阻止调用。  
  
 若要使用`CSocket`对象，请调用构造函数中，然后调用`Create`创建基础`SOCKET`处理 (类型`SOCKET`)。 默认参数`Create`创建流套接字，但是，如果你未使用与套接字`CArchive`对象，你可以指定用于相反，创建数据报套接字或绑定到特定端口以创建服务器套接字的参数。 连接到客户端套接字使用`Connect`在客户端和`Accept`服务器端。 然后创建`CSocketFile`对象，并将关联到`CSocket`对象在`CSocketFile`构造函数。 接下来，创建`CArchive`发送的对象，另一个用于接收数据 （如需要），然后将其关联与`CSocketFile`对象在`CArchive`构造函数。 当通信都完成后时，销毁`CArchive`， `CSocketFile`，和`CSocket`对象。 `SOCKET`文章中介绍了数据类型[Windows 套接字： 背景](../../mfc/windows-sockets-background.md)。  
  
 当你使用`CArchive`与`CSocketFile`和`CSocket`，可能会遇到这样的情况其中`CSocket::Receive`进入循环 (通过`PumpMessages(FD_READ)`) 等待请求的字节量。 这是因为 Windows 套接字允许每个 FD_READ 通知，只有一个接收调用，但`CSocketFile`和`CSocket`允许每 FD_READ 的多个接收调用。 如果你收到 FD_READ 要读取的数据时，应用程序挂起。 如果你永远不会获得另一个 FD_READ，应用程序将停止通过套接字进行通信。  
  
 可以解决此问题，如下所示。 在`OnReceive`你套接字类，调用的方法`CAsyncSocket::IOCtl(FIONREAD, ...)`之前调用`Serialize`你消息类时所需的数据从套接字读取超过一个的 TCP 数据包 （最大传输单元为网络中的大小的方法通常至少 1096 字节)。 如果可用的数据的大小小于所需，等待以接收和仅然后开始读取的操作的所有数据。  
  
 在下面的示例中，`m_dwExpected`是近似用户期望接收的字节数。 假定，您将其声明在其他位置中你的代码。  
  
 [!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]  
  
> [!NOTE]
>  在静态链接的 MFC 应用程序中的辅助线程中使用 MFC 套接字时，您必须在使用套接字的每个线程中调用 `AfxSocketInit` 来初始化套接字库。 默认情况下，仅在主线程中调用 `AfxSocketInit`。  
  
 有关详细信息，请参阅[MFC 中的 Windows 套接字](../../mfc/windows-sockets-in-mfc.md)， [Windows 套接字： 使用存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)， [Windows 套接字： 如何使用存档的工作的套接字](../../mfc/windows-sockets-how-sockets-with-archives-work.md)， [Windows 套接字： 操作顺序](../../mfc/windows-sockets-sequence-of-operations.md)， [Windows 套接字： 使用存档的套接字的示例](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAsyncSocket](../../mfc/reference/casyncsocket-class.md)  
  
 `CSocket`  
  
## <a name="requirements"></a>要求  
 **标头：** afxsock.h  
  
##  <a name="attach"></a>  CSocket::Attach  
 调用此成员函数可将附加`hSocket`的句柄`CSocket`对象。  
  
```  
BOOL Attach(SOCKET hSocket);
```  
  
### <a name="parameters"></a>参数  
 `hSocket`  
 包含为套接字的句柄。  
  
### <a name="return-value"></a>返回值  
 如果函数运行成功，则为非零。  
  
### <a name="remarks"></a>备注  
 **套接字**句柄存储在对象的[m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket)数据成员。  
  
 有关详细信息，请参阅[Windows 套接字： 使用存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]  
  
 [!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]  
  
##  <a name="cancelblockingcall"></a>  CSocket::CancelBlockingCall  
 调用此成员函数以取消阻止当前正在进行调用。  
  
```  
void CancelBlockingCall();
```  
  
### <a name="remarks"></a>备注  
 此函数将取消此套接字任何未完成停滞操作。 原始阻止调用将尽快终止并出现错误**WSAEINTR**。  
  
 在阻止的情况下**连接**操作，就会立即可行的但是它可能不可行的套接字资源，直到完成该连接释放，Windows 套接字实现将终止阻止的调用（，然后已重置） 或超时。这是，可能需要明显仅当应用程序会立即尝试打开新的套接字中，（如果有任何套接字），或者连接到相同的对等方。  
  
 而取消任何操作**接受**会使处于不确定状态的套接字。 如果应用程序取消停滞操作套接字上的，应用程序可以依赖于能够套接字上执行的唯一操作是对的调用**关闭**，但其他操作可能在某些 Windows 套接字上工作实现。 如果你需要为你的应用程序的最大的可移植性，你必须注意不要依赖于在取消后执行操作。  
  
 有关详细信息，请参阅[Windows 套接字： 使用存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
##  <a name="create"></a>  CSocket::Create  
 调用**创建**后构造套接字对象创建 Windows 套接字并将其连接的成员函数。  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>参数  
 `nSocketPort`  
 如果你想要选择的端口的 MFC 套接字或 0 开头使用特定端口。  
  
 `nSocketType`  
 **SOCK_STREAM**或**SOCK_DGRAM**。  
  
 `lpszSocketAddress`  
 指向包含连接的套接字，一个以点分隔的数字，如"128.56.22.8"的网络地址的字符串的指针。 传递**NULL**字符串此参数指示**CSocket**实例应侦听的所有网络接口上的客户端活动。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则通过调用检索 0 和特定错误代码`GetLastError`。  
  
### <a name="remarks"></a>备注  
 **创建**然后调用**绑定**将套接字绑定到指定的地址。 支持以下套接字类型：  
  
- **SOCK_STREAM**序列化，提供可靠、 双向、 基于连接的字节流。 为 Internet 地址族使用传输控制协议 (TCP)。  
  
- **SOCK_DGRAM**支持数据报，即无连接的、 不可靠的缓冲区的固定 （通常很小） 的最大长度。 为 Internet 地址族使用用户数据报协议 (UDP)。 若要使用此选项，你必须使用与套接字`CArchive`对象。  
  
    > [!NOTE]
    >  **接受**成员函数会将新的空引用`CSocket`对象作为其参数。 您必须构造此对象，然后才能调用**接受**。 请记住，如果此套接字对象超出范围，该连接将关闭。 不要调用**创建**为此新的套接字对象。  
  
 有关流和数据报套接字的详细信息，请参阅文章[Windows 套接字： 背景](../../mfc/windows-sockets-background.md)， [Windows 套接字： 端口和套接字地址](../../mfc/windows-sockets-ports-and-socket-addresses.md)，和[Windows 套接字： 使用使用存档的套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
##  <a name="csocket"></a>  CSocket::CSocket  
 构造 `CSocket` 对象。  
  
```  
CSocket();
```  
  
### <a name="remarks"></a>备注  
 完成构造后，必须调用**创建**成员函数。  
  
 有关详细信息，请参阅[Windows 套接字： 使用存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
##  <a name="fromhandle"></a>  CSocket::FromHandle  
 返回一个指向`CSocket`对象。  
  
```  
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```  
  
### <a name="parameters"></a>参数  
 `hSocket`  
 包含为套接字的句柄。  
  
### <a name="return-value"></a>返回值  
 指向的指针`CSocket`对象，或**NULL**如果没有任何`CSocket`对象附加到`hSocket`。  
  
### <a name="remarks"></a>备注  
 在给定**套接字**处理，如果`CSocket`对象未附加到该句柄，则成员函数将返回**NULL**并不会创建临时对象。  
  
 有关详细信息，请参阅[Windows 套接字： 使用存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
##  <a name="isblocking"></a>  CSocket::IsBlocking  
 调用此成员函数可确定阻止调用是否正在进行。  
  
```  
BOOL IsBlocking();
```  
  
### <a name="return-value"></a>返回值  
 如果正在阻止套接字; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[Windows 套接字： 使用存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
##  <a name="onmessagepending"></a>  CSocket::OnMessagePending  
 重写该成员函数以从 Windows 查找特定的消息和你的套接字中对其做出响应。  
  
```  
virtual BOOL OnMessagePending();
```  
  
### <a name="return-value"></a>返回值  
 如果该消息已处理; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 这是一个高级可重写。  
  
 框架调用`OnMessagePending`时套接字发送 Windows 消息，使你可以使用来处理你的应用程序感兴趣的消息。 有关如何使用的示例`OnMessagePending`，请参阅文章[Windows 套接字： 从套接字类派生](../../mfc/windows-sockets-deriving-from-socket-classes.md)。  
  
 有关详细信息，请参阅[Windows 套接字： 使用存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
## <a name="see-also"></a>请参阅  
 [CAsyncSocket 类](../../mfc/reference/casyncsocket-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket 类](../../mfc/reference/casyncsocket-class.md)   
 [CSocketFile 类](../../mfc/reference/csocketfile-class.md)
