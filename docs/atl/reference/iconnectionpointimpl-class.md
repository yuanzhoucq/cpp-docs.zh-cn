---
title: "IConnectionPointImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.IConnectionPointImpl"
  - "IConnectionPointImpl"
  - "ATL::IConnectionPointImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "连接点 [C++], 实现"
  - "IConnectionPointImpl class"
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# IConnectionPointImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现连接点。  
  
## 语法  
  
```  
  
      template<  
   class T,  
   const IID* piid,  
   class CDV = CComDynamicUnkArray   
>  
class ATL_NO_VTABLE IConnectionPointImpl :  
   public _ICPLocator< piid >  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IConnectionPointImpl`。  
  
 `piid`  
 由表示的接口的IID的指针连接点对象。  
  
 `CDV`  
 管理连接的选件类。  默认值为 [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，允许无限制的连接。  还可以使用 [CComUnkArray](../../atl/reference/ccomunkarray-class.md)，指定连接的内置的数字。  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[IConnectionPointImpl::Advise](../Topic/IConnectionPointImpl::Advise.md)|生成之间的连接连接点和接收器。|  
|[IConnectionPointImpl::EnumConnections](../Topic/IConnectionPointImpl::EnumConnections.md)|创建一个枚举器通过的连接重复连接点。|  
|[IConnectionPointImpl::GetConnectionInterface](../Topic/IConnectionPointImpl::GetConnectionInterface.md)|检索表示接口的IID连接点。|  
|[IConnectionPointImpl::GetConnectionPointContainer](../Topic/IConnectionPointImpl::GetConnectionPointContainer.md)|检索接口指针可连接的对象。|  
|[IConnectionPointImpl::Unadvise](../Topic/IConnectionPointImpl::Unadvise.md)|停止通过 `Advise`以前生成的连接。|  
  
### 公共数据成员  
  
|名称|描述|  
|--------|--------|  
|[IConnectionPointImpl::m\_vec](../Topic/IConnectionPointImpl::m_vec.md)|管理连接连接点。|  
  
## 备注  
 `IConnectionPointImpl` 实现连接点，允许对象显示一个输出接口在客户端。  客户端实现在调用接收器的对象的此接口。  
  
 ATL使用 [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) 实现可连接的对象。  在每个可连接的对象内连接点表示一个输出接口，这是由 `piid`。  选件类 *CDV* 管理之间的连接连接点和接收器。  每个连接都是唯一的“cookie标识的”。  
  
 有关使用的更多信息在ATL连接点，请参见一 [连接点](../../atl/atl-connection-points.md)文章。  
  
## 继承层次结构  
 `_ICPLocator`  
  
 `IConnectionPointImpl`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318)   
 [Class Overview](../../atl/atl-class-overview.md)