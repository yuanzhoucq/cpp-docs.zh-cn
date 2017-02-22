---
title: "IServiceProviderImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::IServiceProviderImpl<T>"
  - "ATL.IServiceProviderImpl<T>"
  - "ATL.IServiceProviderImpl"
  - "ATL::IServiceProviderImpl"
  - "IServiceProviderImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IServiceProvider 接口, ATL 实现"
  - "IServiceProviderImpl class"
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# IServiceProviderImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供 `IServiceProvider` 接口的默认实现。  
  
## 语法  
  
```  
  
      template <  
   class T  
>   
class ATL_NO_VTABLE IServiceProviderImpl :  
   public IServiceProvider  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IServiceProviderImpl`。  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[IServiceProviderImpl::QueryService](../Topic/IServiceProviderImpl::QueryService.md)|创建或访问指定的服务并返回接口指针。服务的指定接口。|  
  
## 备注  
 `IServiceProvider` 接口查找其GUID指定的一个服务并返回请求的接口的接口指针在服务。  选件类 `IServiceProviderImpl` 提供此接口的默认实现。  
  
 **IServiceProviderImpl** 指定一个方法: [QueryService](../Topic/IServiceProviderImpl::QueryService.md)，创建或访问指定的服务并返回接口指针。服务的指定接口。  
  
 `IServiceProviderImpl` 从 [BEGIN\_SERVICE\_MAP](../Topic/BEGIN_SERVICE_MAP.md) 和结尾开始使用服务映射，与 [END\_SERVICE\_MAP](../Topic/END_SERVICE_MAP.md)。  
  
 服务映射包含两项: [SERVICE\_ENTRY](../Topic/SERVICE_ENTRY.md)，指示所指定的服务ID \(SID\)支持对象和 [SERVICE\_ENTRY\_CHAIN](../Topic/SERVICE_ENTRY_CHAIN.md)，调用 `QueryService` 绑定到另一个对象。  
  
## 继承层次结构  
 `IServiceProvider`  
  
 `IServiceProviderImpl`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)