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
ms.openlocfilehash: 2a131323e64b1bf67f76ec92e7a3e4fcba899661
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496349"
---
# <a name="csocketaddr-class"></a>CSocketAddr 类

此类提供了一些方法, 用于将主机名转换为主机地址, 同时支持 IPv4 和 IPV6 格式。

## <a name="syntax"></a>语法

```
class CSocketAddr
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSocketAddr::CSocketAddr](#csocketaddr)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSocketAddr::FindAddr](#findaddr)|调用此方法可将提供的主机名转换为主机地址。|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|调用此方法可将 IPv4 主机名转换为主机地址。|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|调用此方法可将 IPv6 主机名称转换为主机地址。|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|调用此方法以返回指向`addrinfo`列表中特定元素的指针。|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|调用此方法以返回指向`addrinfo`列表的指针。|

## <a name="remarks"></a>备注

此类提供了一种与 IP 版本无关的方法来查找网络地址, 以便与库中的 Windows 套接字 API 函数和套接字包装一起使用。

用于查找网络地址的此类的成员使用 Win32 API 函数[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)。 调用函数的 ANSI 或 UNICODE 版本, 具体取决于是否为 ANSI 或 UNICODE 编译你的代码。

此类支持 IPv4 andIPv6 网络地址。

## <a name="requirements"></a>要求

**标头:** atlsocket

##  <a name="csocketaddr"></a>  CSocketAddr::CSocketAddr

构造函数。

```
CSocketAddr();
```

### <a name="remarks"></a>备注

创建一个新`CSocketAddr`的对象并初始化链接列表, 其中包含有关主机的响应信息。

##  <a name="findaddr"></a>  CSocketAddr::FindAddr

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
主机名或以点分隔的 IP 地址。

*szPortOrServiceName*<br/>
主机上的服务的端口号或名称。

*nPortNo*<br/>
端口号。

*flags*<br/>
0或 AI_PASSIVE、AI_CANONNAME 或 AI_NUMERICHOST 的组合。

*addr_family*<br/>
地址系列 (如 PF_INET)。

*sock_type*<br/>
套接字类型 (如 SOCK_STREAM)。

*ai_proto*<br/>
协议 (如 IPPROTO_IP 或 IPPROTO_IPV6)。

### <a name="return-value"></a>返回值

如果成功计算地址, 则返回零。 失败时返回非零的 Windows 套接字错误代码。 如果成功, 则计算的地址存储在可使用`CSocketAddr::GetAddrInfoList`和`CSocketAddr::GetAddrInfo`引用的链接列表中。

### <a name="remarks"></a>备注

主机名参数可以是 IPv4 格式或 IPv6 格式。 此方法调用 Win32 API 函数[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)来执行转换。

##  <a name="findinet4addr"></a>  CSocketAddr::FindINET4Addr

调用此方法可将 IPv4 主机名转换为主机地址。

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>参数

*szHost*<br/>
主机名或以点分隔的 IP 地址。

*nPortNo*<br/>
端口号。

*flags*<br/>
0或 AI_PASSIVE、AI_CANONNAME 或 AI_NUMERICHOST 的组合。

*sock_type*<br/>
套接字类型 (如 SOCK_STREAM)。

### <a name="return-value"></a>返回值

如果成功计算地址, 则返回零。 失败时返回非零的 Windows 套接字错误代码。 如果成功, 则计算的地址存储在可使用`CSocketAddr::GetAddrInfoList`和`CSocketAddr::GetAddrInfo`引用的链接列表中。

### <a name="remarks"></a>备注

此方法调用 Win32 API 函数[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)来执行转换。

##  <a name="findinet6addr"></a>  CSocketAddr::FindINET6Addr

调用此方法可将 IPv6 主机名称转换为主机地址。

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>参数

*szHost*<br/>
主机名或以点分隔的 IP 地址。

*nPortNo*<br/>
端口号。

*flags*<br/>
0或 AI_PASSIVE、AI_CANONNAME 或 AI_NUMERICHOST 的组合。

*sock_type*<br/>
套接字类型 (如 SOCK_STREAM)。

### <a name="return-value"></a>返回值

如果成功计算地址, 则返回零。 失败时返回非零的 Windows 套接字错误代码。 如果成功, 则计算的地址存储在可使用`CSocketAddr::GetAddrInfoList`和`CSocketAddr::GetAddrInfo`引用的链接列表中。

### <a name="remarks"></a>备注

此方法调用 Win32 API 函数[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)来执行转换。

##  <a name="getaddrinfo"></a>  CSocketAddr::GetAddrInfo

调用此方法以返回指向`addrinfo`列表中特定元素的指针。

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
对[addrinfo](/windows/win32/api/ws2def/ns-ws2def-addrinfow)列表中的特定元素的引用。

### <a name="return-value"></a>返回值

返回一个指向`addrinfo`结构的指针, 该结构包含有关主机的响应信息的链接列表中的*nIndex*引用的结构。

##  <a name="getaddrinfolist"></a>  CSocketAddr::GetAddrInfoList

调用此方法以返回指向`addrinfo`列表的指针。

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>返回值

一个指针, 指向包含有关主机的响应`addrinfo`信息的一个或多个结构的链接列表。 有关详细信息, 请参阅[addrinfo 结构](/windows/win32/api/ws2def/ns-ws2def-addrinfow)。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
