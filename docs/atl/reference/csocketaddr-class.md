---
title: "CSocketAddr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSocketAddr"
  - "ATL.CSocketAddr"
  - "ATL::CSocketAddr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSocketAddr class"
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CSocketAddr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类对转换主机名的方法转换为宿主地址，支持IPv4和IPV6格式。  
  
## 语法  
  
```  
  
class CSocketAddr  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CSocketAddr::CSocketAddr](../Topic/CSocketAddr::CSocketAddr.md)|构造函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CSocketAddr::FindAddr](../Topic/CSocketAddr::FindAddr.md)|调用此方法将提供的主机名转换为宿主地址。|  
|[CSocketAddr::FindINET4Addr](../Topic/CSocketAddr::FindINET4Addr.md)|调用此方法将IPv4主机名转换为宿主地址。|  
|[CSocketAddr::FindINET6Addr](../Topic/CSocketAddr::FindINET6Addr.md)|调用此方法将IPv6主机名转换为宿主地址。|  
|[CSocketAddr::GetAddrInfo](../Topic/CSocketAddr::GetAddrInfo.md)|调用此方法返回指向在 **addrinfo** 的特定元素的列表。|  
|[CSocketAddr::GetAddrInfoList](../Topic/CSocketAddr::GetAddrInfoList.md)|调用此方法返回指向 **addrinfo** 列表。|  
  
## 备注  
 此选件类用于查找网络地址用于Windows套接字API函数和套接字包装提供一个IP版本无关的方法在库中。  
  
 用于查找网络地址此选件类的成员使用Win32 API函数 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520)。  
  
 此选件类支持两个IPv4 andIPv6网络地址。  
  
## 要求  
 **Header:** atlsocket.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)