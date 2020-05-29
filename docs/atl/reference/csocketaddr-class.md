---
title: CSocketAddr 类
ms.date: 10/22/2018
f1_keywords:
- CSocketAddr
- ATLSOCKET/ATL::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::FindAddr
- ATLSOCKET/ATL::CSocketAddr::FindINET4Addr
- ATLSOCKET/ATL::CSocketAddr::FindINET6Addr
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfo
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfoList
helpviewer_keywords:
- CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
ms.openlocfilehash: 66d33d62212389a2b0f318250c1c16a99167c6eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330684"
---
# <a name="csocketaddr-class"></a>CSocketAddr 类

此类提供了将主机名转换为主机地址的方法，支持 IPv4 和 IPV6 格式。

## <a name="syntax"></a>语法

```
class CSocketAddr
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[套接字器：：套接字器](#csocketaddr)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[套接字器：：查找添加器](#findaddr)|调用此方法可将提供的主机名转换为主机地址。|
|[套接字器：：查找INET4Addr](#findinet4addr)|调用此方法将 IPv4 主机名转换为主机地址。|
|[套接字器：：查找INET6Addr](#findinet6addr)|调用此方法将 IPv6 主机名转换为主机地址。|
|[CSocketAddr：获取AddrInfo](#getaddrinfo)|调用此方法以返回指向列表中特定元素的`addrinfo`指针。|
|[套接字器：：获取AddrInfoList](#getaddrinfolist)|调用此方法以返回指向列表的`addrinfo`指针。|

## <a name="remarks"></a>备注

此类提供了一种与 IP 版本无关的方法，用于查找网络地址，以便与库中的 Windows 套接字 API 函数和套接字包装器配合使用。

此类成员用于查找网络地址，使用 Win32 API 函数[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)。 根据代码是为 ANSI 还是 UNICODE 编译的，调用该函数的 ANSI 或 UNICODE 版本。

此类同时支持 IPv4 和 IPv6 网络地址。

## <a name="requirements"></a>要求

**标题：** atlsocket.h

## <a name="csocketaddrcsocketaddr"></a><a name="csocketaddr"></a>套接字器：：套接字器

构造函数。

```
CSocketAddr();
```

### <a name="remarks"></a>备注

创建新`CSocketAddr`对象并初始化包含有关主机的响应信息的链接列表。

## <a name="csocketaddrfindaddr"></a><a name="findaddr"></a>套接字器：：查找添加器

调用此方法可将提供的主机名转换为主机地址。

```
int FindAddr(
    const TCHAR *szHost,
    const TCHAR *szPortOrServiceName,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);

int FindAddr(
    const TCHAR *szHost,
    int nPortNo,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);
```

### <a name="parameters"></a>参数

*szHost*<br/>
主机名或虚点 IP 地址。

*szPortOr服务名称*<br/>
主机上的端口号或服务名称。

*n波特诺*<br/>
端口号。

*标志*<br/>
0 或AI_PASSIVE、AI_CANONNAME或AI_NUMERICHOST的组合。

*addr_family*<br/>
地址族（如PF_INET）。

*sock_type*<br/>
套接字类型（如SOCK_STREAM）。

*ai_proto*<br/>
协议（如IPPROTO_IP或IPPROTO_IPV6）。

### <a name="return-value"></a>返回值

如果地址计算成功，则返回零。 在发生故障时返回非零 Windows 套接字错误代码。 如果成功，计算的地址将存储在链接`CSocketAddr::GetAddrInfoList`列表中，该列表可以使用 和`CSocketAddr::GetAddrInfo`引用。

### <a name="remarks"></a>备注

主机名参数可能采用 IPv4 或 IPv6 格式。 此方法调用 Win32 API 函数[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)来执行转换。

## <a name="csocketaddrfindinet4addr"></a><a name="findinet4addr"></a>套接字器：：查找INET4Addr

调用此方法将 IPv4 主机名转换为主机地址。

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>参数

*szHost*<br/>
主机名或虚点 IP 地址。

*n波特诺*<br/>
端口号。

*标志*<br/>
0 或AI_PASSIVE、AI_CANONNAME或AI_NUMERICHOST的组合。

*sock_type*<br/>
套接字类型（如SOCK_STREAM）。

### <a name="return-value"></a>返回值

如果地址计算成功，则返回零。 在发生故障时返回非零 Windows 套接字错误代码。 如果成功，计算的地址将存储在链接`CSocketAddr::GetAddrInfoList`列表中，该列表可以使用 和`CSocketAddr::GetAddrInfo`引用。

### <a name="remarks"></a>备注

此方法调用 Win32 API 函数[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)来执行转换。

## <a name="csocketaddrfindinet6addr"></a><a name="findinet6addr"></a>套接字器：：查找INET6Addr

调用此方法将 IPv6 主机名转换为主机地址。

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>参数

*szHost*<br/>
主机名或虚点 IP 地址。

*n波特诺*<br/>
端口号。

*标志*<br/>
0 或AI_PASSIVE、AI_CANONNAME或AI_NUMERICHOST的组合。

*sock_type*<br/>
套接字类型（如SOCK_STREAM）。

### <a name="return-value"></a>返回值

如果地址计算成功，则返回零。 在发生故障时返回非零 Windows 套接字错误代码。 如果成功，计算的地址将存储在链接`CSocketAddr::GetAddrInfoList`列表中，该列表可以使用 和`CSocketAddr::GetAddrInfo`引用。

### <a name="remarks"></a>备注

此方法调用 Win32 API 函数[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)来执行转换。

## <a name="csocketaddrgetaddrinfo"></a><a name="getaddrinfo"></a>CSocketAddr：获取AddrInfo

调用此方法以返回指向列表中特定元素的`addrinfo`指针。

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
对[addrinfo](/windows/win32/api/ws2def/ns-ws2def-addrinfow)列表中特定元素的引用。

### <a name="return-value"></a>返回值

返回指向链接列表中`addrinfo`*nIndex*引用的结构的指针，其中包含有关主机的响应信息。

## <a name="csocketaddrgetaddrinfolist"></a><a name="getaddrinfolist"></a>套接字器：：获取AddrInfoList

调用此方法以返回指向列表的`addrinfo`指针。

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>返回值

指向包含有关主机的响应信息的一`addrinfo`个或多个结构的链接列表。 有关详细信息，请参阅[addrinfo 结构](/windows/win32/api/ws2def/ns-ws2def-addrinfow)。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
