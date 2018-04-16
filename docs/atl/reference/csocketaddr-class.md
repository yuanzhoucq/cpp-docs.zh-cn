---
title: "CSocketAddr 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cadd771e6c3a9e7addb6893b4427183cfff293c9
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
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
|[CSocketAddr::FindINET4Addr](#findinet4addr)|调用此方法将 IPv4 主机名转换为主机地址。|  
|[CSocketAddr::FindINET6Addr](#findinet6addr)|调用此方法将 IPv6 主机名转换为主机地址。|  
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|调用此方法以返回到中的特定元素的指针**addrinfo**列表。|  
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|调用此方法以返回一个指向**addrinfo**列表。|  
  
## <a name="remarks"></a>备注  
 此类提供 API 函数和库中的套接字包装，套接字不可知的方法，用于查找与 Windows 一起使用的网络地址的 IP 版本。  
  
 用于查找网络地址的此类成员都使用 Win32 API 函数[getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520)。  
  
 此类支持这两个 IPv4 andIPv6 网络地址。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlsocket.h  
  
##  <a name="csocketaddr"></a>CSocketAddr::CSocketAddr  
 构造函数。  
  
```
CSocketAddr();
```  
  
### <a name="remarks"></a>备注  
 创建一个新`CSocketAddr`对象，然后初始化包含有关主机的响应信息的链接的列表。  
  
##  <a name="findaddr"></a>CSocketAddr::FindAddr  
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
 `szHost`  
 主机名或以点分隔的 IP 地址。  
  
 *szPortOrServiceName*  
 端口号或主机上的服务名称。  
  
 `nPortNo`  
 端口号。  
  
 `flags`  
 0 或 AI_PASSIVE、 AI_CANONNAME 或 AI_NUMERICHOST 的组合。  
  
 *addr_family*  
 地址系列 （例如 PF_INET)。  
  
 `sock_type`  
 套接字类型 （如 SOCK_STREAM)。  
  
 *ai_proto*  
 协议 （如 IPPROTO_IP 或 IPPROTO_IPV6）。  
  
### <a name="return-value"></a>返回值  
 如果成功计算地址，则返回零。 返回一个非零的 Windows 套接字错误代码失败。 如果成功，计算的地址存储在可能使用引用的链接列表`CSocketAddr::GetAddrInfoList`和`CSocketAddr::GetAddrInfo`。  
  
### <a name="remarks"></a>备注  
 主机名称参数还可以是 IPv4 或 IPv6 格式。 此方法调用 Win32 API 函数[getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520)来执行转换。  
  
##  <a name="findinet4addr"></a>CSocketAddr::FindINET4Addr  
 调用此方法将 IPv4 主机名转换为主机地址。  
  
```
int FindINET4Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```  
  
### <a name="parameters"></a>参数  
 `szHost`  
 主机名或以点分隔的 IP 地址。  
  
 `nPortNo`  
 端口号。  
  
 `flags`  
 0 或 AI_PASSIVE、 AI_CANONNAME 或 AI_NUMERICHOST 的组合。  
  
 `sock_type`  
 套接字类型 （如 SOCK_STREAM)。  
  
### <a name="return-value"></a>返回值  
 如果成功计算地址，则返回零。 返回一个非零的 Windows 套接字错误代码失败。 如果成功，计算的地址存储在可能使用引用的链接列表`CSocketAddr::GetAddrInfoList`和`CSocketAddr::GetAddrInfo`。  
  
### <a name="remarks"></a>备注  
 此方法调用 Win32 API 函数[getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520)来执行转换。  
  
##  <a name="findinet6addr"></a>CSocketAddr::FindINET6Addr  
 调用此方法将 IPv6 主机名转换为主机地址。  
  
```
int FindINET6Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```  
  
### <a name="parameters"></a>参数  
 `szHost`  
 主机名或以点分隔的 IP 地址。  
  
 `nPortNo`  
 端口号。  
  
 `flags`  
 0 或 AI_PASSIVE、 AI_CANONNAME 或 AI_NUMERICHOST 的组合。  
  
 `sock_type`  
 套接字类型 （如 SOCK_STREAM)。  
  
### <a name="return-value"></a>返回值  
 如果成功计算地址，则返回零。 返回一个非零的 Windows 套接字错误代码失败。 如果成功，计算的地址存储在可能使用引用的链接列表`CSocketAddr::GetAddrInfoList`和`CSocketAddr::GetAddrInfo`。  
  
### <a name="remarks"></a>备注  
 此方法调用 Win32 API 函数[getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520)来执行转换。  
  
##  <a name="getaddrinfo"></a>CSocketAddr::GetAddrInfo  
 调用此方法以返回到中的特定元素的指针**addrinfo**列表。  
  
```
addrinfo* const GetAddrInfoint nIndex = 0) const;
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 对中的特定元素的引用[addrinfo](http://msdn.microsoft.com/library/windows/desktop/ms737530)列表。  
  
### <a name="return-value"></a>返回值  
 返回一个指向**addrinfo**结构引用`nIndex`中包含有关主机的响应信息的链接列表。  
  
##  <a name="getaddrinfolist"></a>CSocketAddr::GetAddrInfoList  
 调用此方法以返回一个指向**addrinfo**列表。  
  
```
addrinfo* const GetAddrInfoList() const;
```  
  
### <a name="return-value"></a>返回值  
 指向一个或多个链接列表`addrinfo`包含有关主机的响应信息的结构。 有关详细信息，请参阅[addrinfo 结构](https://msdn.microsoft.com/library/windows/desktop/ms737530)。
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
