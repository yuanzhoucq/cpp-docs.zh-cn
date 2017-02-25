---
title: "IObjectWithSiteImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::IObjectWithSiteImpl"
  - "ATL.IObjectWithSiteImpl<T>"
  - "IObjectWithSiteImpl"
  - "ATL.IObjectWithSiteImpl"
  - "ATL::IObjectWithSiteImpl<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IObjectWithSiteImpl class"
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# IObjectWithSiteImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类的方法允许对象与其站点通信。  
  
## 语法  
  
```  
  
      template<  
   class T   
>  
class ATL_NO_VTABLE IObjectWithSiteImpl :  
   public IObjectWithSite  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IObjectWithSiteImpl`。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IObjectWithSiteImpl::GetSite](../Topic/IObjectWithSiteImpl::GetSite.md)|查询接口指针的站点。|  
|[IObjectWithSiteImpl::SetChildSite](../Topic/IObjectWithSiteImpl::SetChildSite.md)|提供对象与网站的 **IUnknown** 指针。|  
|[IObjectWithSiteImpl::SetSite](../Topic/IObjectWithSiteImpl::SetSite.md)|提供对象与网站的 **IUnknown** 指针。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[IObjectWithSiteImpl::m\_spUnkSite](../Topic/IObjectWithSiteImpl::m_spUnkSite.md)|管理站点的 **IUnknown** 指针。|  
  
## 备注  
 [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) 接口允许对象与其站点通信。  选件类 `IObjectWithSiteImpl` 提供此接口的默认实现并将信息发送实现 **IUnknown** 到转储计算机进行编译。  
  
 `IObjectWithSiteImpl` 指定两个方法。  客户端首次调用 `SetSite`，通过站点的 **IUnknown** 指针。  此指针在对象中存储，并且可以传递给 `GetSite`的调用之后进行检索。  
  
 通常，可以从 `IObjectWithSiteImpl` 派生您的选件类，在创建不是控件的对象时。  对于控件，从 [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)派生您的选件类，还提供了网站指针。  从 `IObjectWithSiteImpl` 和 `IOleObjectImpl`不要派生您的选件类。  
  
## 继承层次结构  
 `IObjectWithSite`  
  
 `IObjectWithSiteImpl`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)