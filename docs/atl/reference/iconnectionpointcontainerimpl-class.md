---
title: "IConnectionPointContainerImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::IConnectionPointContainerImpl"
  - "ATL.IConnectionPointContainerImpl"
  - "ATL.IConnectionPointContainerImpl<T>"
  - "IConnectionPointContainerImpl"
  - "ATL::IConnectionPointContainerImpl<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "connectable objects"
  - "连接点 [C++], container"
  - "IConnectionPointContainerImpl class"
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# IConnectionPointContainerImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现连接点容器管理 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 对象的集合。  
  
## 语法  
  
```  
  
      template<  
   class T   
>  
class ATL_NO_VTABLE IConnectionPointContainerImpl :   
   public IConnectionPointContainer  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IConnectionPointContainerImpl`。  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[IConnectionPointContainerImpl::EnumConnectionPoints](../Topic/IConnectionPointContainerImpl::EnumConnectionPoints.md)|在可连接的对象创建枚举数循环访问连接点支持。|  
|[IConnectionPointContainerImpl::FindConnectionPoint](../Topic/IConnectionPointContainerImpl::FindConnectionPoint.md)|检索接口指针。支持指定的IID的连接点。|  
  
## 备注  
 `IConnectionPointContainerImpl` 实现连接点容器管理 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 对象的集合。  `IConnectionPointContainerImpl` 提供客户端可以调用检索有关可连接对象的更多信息的两个方法:  
  
-   `EnumConnectionPoints` 允许客户端确定输出接口对象支持。  
  
-   `FindConnectionPoint` 允许客户端确定对象是否支持给定的输出接口。  
  
 有关如何使用的信息在ATL连接点，请参见一 [连接点](../../atl/atl-connection-points.md)文章。  
  
## 继承层次结构  
 `IConnectionPointContainer`  
  
 `IConnectionPointContainerImpl`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)   
 [Class Overview](../../atl/atl-class-overview.md)