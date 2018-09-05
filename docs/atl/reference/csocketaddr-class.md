---
title: CSocketAddr 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSocketAddr
- ATLSOCKET/ATL::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::FindAddr
- ATLSOCKET/ATL::CSocketAddr::FindINET4Addr
- ATLSOCKET/ATL::CSocketAddr::FindINET6Addr
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfo
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfoList
dev_langs:
- C++
helpviewer_keywords:
- CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0eba14e7b8a251fdc1287fc413e2c4ebcd7ae77
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766173"
---
# <a name="csocketaddr-class"></a>CSocketAddr 类

此类提供用于将主机名转换为主机地址，支持 IPv4 和 IPV6 格式的方法。

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
|[CSocketAddr::FindAddr](#findaddr)|调用此方法将提供的主机名转换为主机地址。|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|调用此方法以将 IPv4 主机名转换为主机地址。|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|调用此方法以将 IPv6 主机名转换为主机地址。|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|调用此方法以返回到中的特定元素的指针`addrinfo`列表。|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|调用此方法以返回一个指向`addrinfo`列表。|

## <a name="remarks"></a>备注

此类提供 API 函数和库中的套接字包装器，套接字不可知的方法，用于查找与 Windows 配合使用的网络地址的 IP 版本。

用于查找网络地址的此类成员使用 Win32 API 函数[getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)。

此类支持这两个 IPv4 andIPv6 网络地址。

## <a name="requirements"></a>要求

**标头：** atlsocket.h

##  <a name="csocketaddr"></a>  CSocketAddr::CSocketAddr

构造函数。

```
CSocketAddr();
```

### <a name="remarks"></a>备注

创建一个新`CSocketAddr`对象，然后初始化链接的列表，其中包含有关主机的响应信息。

##  <a name="findaddr"></a>  CSocketAddr::FindAddr

调用此方法将提供的主机名转换为主机地址。

```
int FindAddr(
    const char *szHost,
    const char *szPortOrServiceName,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);

int FindAddr(
    const char *szHost,
    int nPortNo,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);
```

### <a name="parameters"></a>参数

*szHost*  
主机名或以点分隔的 IP 地址。

*szPortOrServiceName*  
端口号或主机上的服务的名称。

*nPortNo*  
端口号。

*flags*  
0 或 AI_PASSIVE、 AI_CANONNAME 或 AI_NUMERICHOST 的组合。

*addr_family*  
地址系列 （例如 PF_INET)。

*sock_type*  
套接字类型 （如 SOCK_STREAM)。

*ai_proto*  
协议 （如 IPPROTO_IP 或 IPPROTO_IPV6）。

### <a name="return-value"></a>返回值

如果地址计算成功，则返回零。 在失败时返回非零值的 Windows 套接字错误代码。 如果成功，计算的地址存储在可能使用引用的链接列表`CSocketAddr::GetAddrInfoList`和`CSocketAddr::GetAddrInfo`。

### <a name="remarks"></a>备注

主机名称参数可能是 IPv4 或 IPv6 格式。 此方法调用 Win32 API 函数[getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)来执行此转换。

##  <a name="findinet4addr"></a>  CSocketAddr::FindINET4Addr

调用此方法以将 IPv4 主机名转换为主机地址。

```
int FindINET4Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```

### <a name="parameters"></a>参数

*szHost*  
主机名或以点分隔的 IP 地址。

*nPortNo*  
端口号。

*flags*  
0 或 AI_PASSIVE、 AI_CANONNAME 或 AI_NUMERICHOST 的组合。

*sock_type*  
套接字类型 （如 SOCK_STREAM)。

### <a name="return-value"></a>返回值

如果地址计算成功，则返回零。 在失败时返回非零值的 Windows 套接字错误代码。 如果成功，计算的地址存储在可能使用引用的链接列表`CSocketAddr::GetAddrInfoList`和`CSocketAddr::GetAddrInfo`。

### <a name="remarks"></a>备注

此方法调用 Win32 API 函数[getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)来执行此转换。

##  <a name="findinet6addr"></a>  CSocketAddr::FindINET6Addr

调用此方法以将 IPv6 主机名转换为主机地址。

```
int FindINET6Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```

### <a name="parameters"></a>参数

*szHost*  
主机名或以点分隔的 IP 地址。

*nPortNo*  
端口号。

*flags*  
0 或 AI_PASSIVE、 AI_CANONNAME 或 AI_NUMERICHOST 的组合。

*sock_type*  
套接字类型 （如 SOCK_STREAM)。

### <a name="return-value"></a>返回值

如果地址计算成功，则返回零。 在失败时返回非零值的 Windows 套接字错误代码。 如果成功，计算的地址存储在可能使用引用的链接列表`CSocketAddr::GetAddrInfoList`和`CSocketAddr::GetAddrInfo`。

### <a name="remarks"></a>备注

此方法调用 Win32 API 函数[getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)来执行此转换。

##  <a name="getaddrinfo"></a>  CSocketAddr::GetAddrInfo

调用此方法以返回到中的特定元素的指针`addrinfo`列表。

```
addrinfo* const GetAddrInfoint nIndex = 0) const;
```

### <a name="parameters"></a>参数

*nIndex*  
对中的特定元素的引用[addrinfo](https://msdn.microsoft.com/library/windows/desktop/ms737530)列表。

### <a name="return-value"></a>返回值

返回一个指向`addrinfo`引用的结构*nIndex*中包含有关主机的响应信息的链接列表。

##  <a name="getaddrinfolist"></a>  CSocketAddr::GetAddrInfoList

调用此方法以返回一个指向`addrinfo`列表。

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>返回值

指向一个或多个链接列表的`addrinfo`结构包含有关主机的响应信息。 有关详细信息，请参阅[addrinfo 结构](https://msdn.microsoft.com/library/windows/desktop/ms737530)。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
