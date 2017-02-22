---
title: "CHandle Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CHandle"
  - "ATL::CHandle"
  - "CHandle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHandle class"
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CHandle Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供创建和使用处理对象。  
  
## 语法  
  
```  
  
class CHandle  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CHandle::CHandle](../Topic/CHandle::CHandle.md)|构造函数。|  
|[CHandle::~CHandle](../Topic/CHandle::~CHandle.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CHandle::Attach](../Topic/CHandle::Attach.md)|调用此方法附加到现有处理的 `CHandle` 对象。|  
|[CHandle::Close](../Topic/CHandle::Close.md)|调用此方法关闭 `CHandle` 对象。|  
|[CHandle::Detach](../Topic/CHandle::Detach.md)|调用此方法分离 `CHandle` 对象的句柄。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CHandle::operator HANDLE](../Topic/CHandle::operator%20HANDLE.md)|返回存储句柄的值。|  
|[CHandle::operator \=](../Topic/CHandle::operator%20=.md)|赋值运算符。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CHandle::m\_h](../Topic/CHandle::m_h.md)|存储句柄的成员变量。|  
  
## 备注  
 可以使用 `CHandle` 对象，当需要处理:主要区别在于 `CHandle` 对象将被自动删除。  
  
> [!NOTE]
>  而其他使用INVALID\_HANDLE\_VALUE，某些API函数将使用NULL为空或无效处理。  `CHandle` 仅使用NULL，并会将INVALID\_HANDLE\_VALUE作为实际处理。  如果调用可返回INVALID\_HANDLE\_VALUE API，您应检查此值在调用 [CHandle::Attach](../Topic/CHandle::Attach.md) 或通过之前对 `CHandle` 构造函数和通过NULL。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)