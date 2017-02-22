---
title: "IDispEventSimpleImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IDispEventSimpleImpl"
  - "ATL::IDispEventSimpleImpl"
  - "ATL.IDispEventSimpleImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDispEventSimpleImpl class"
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# IDispEventSimpleImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供 `IDispatch` 方法的实现，这样，而不会获得类型信息从类型库。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
UINT nID,  
class T,  
const IID* pdiid  
>  
class ATL_NO_VTABLE IDispEventSimpleImpl :  
public _IDispEventLocator<nID, pdiid>  
```  
  
#### 参数  
 `nID`  
 源对象的唯一标识符。  当 `IDispEventSimpleImpl` 是复合控件时基类，提供此参数将所需包含控件的资源ID。  在某些情况下，使用一个随机的正整数。  
  
 `T`  
 用户的选件类，从 `IDispEventSimpleImpl`派生。  
  
 `pdiid`  
 此选件类实现事件的调度接口的IID的指针。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IDispEventSimpleImpl::Advise](../Topic/IDispEventSimpleImpl::Advise.md)|生成与默认事件源的连接。|  
|[IDispEventSimpleImpl::DispEventAdvise](../Topic/IDispEventSimpleImpl::DispEventAdvise.md)|生成与事件源的连接。|  
|[IDispEventSimpleImpl::DispEventUnadvise](../Topic/IDispEventSimpleImpl::DispEventUnadvise.md)|中断与事件源的连接。|  
|[IDispEventSimpleImpl::GetIDsOfNames](../Topic/IDispEventSimpleImpl::GetIDsOfNames.md)|返回 **E\_NOTIMPL**。|  
|[IDispEventSimpleImpl::GetTypeInfo](../Topic/IDispEventSimpleImpl::GetTypeInfo.md)|返回 **E\_NOTIMPL**。|  
|[IDispEventSimpleImpl::GetTypeInfoCount](../Topic/IDispEventSimpleImpl::GetTypeInfoCount.md)|返回 **E\_NOTIMPL**。|  
|[IDispEventSimpleImpl::Invoke](../Topic/IDispEventSimpleImpl::Invoke.md)|在事件接收器映射调用事件处理程序的列表。|  
|[IDispEventSimpleImpl::Unadvise](../Topic/IDispEventSimpleImpl::Unadvise.md)|中断与默认事件源的连接。|  
  
## 备注  
 `IDispEventSimpleImpl` 提供实现事件调度接口方法，无需提供每个方法\/事件的代码实现该接口。  `IDispEventSimpleImpl` 提供 `IDispatch` 方法的实现。  只需提供事件的实现您对处理感兴趣。  
  
 `IDispEventSimpleImpl` 与您的选件类的 [事件接收器映射](../Topic/BEGIN_SINK_MAP.md) 一起使用路由事件到适当的处理程序函数。  使用此选件类:  
  
-   添加一 [SINK\_ENTRY\_INFO](../Topic/SINK_ENTRY_INFO.md) 宏到每个事件接收器映射在要处理的每个对象。  
  
-   通过将指针提供每个事件的类型信息。[\_ATL\_FUNC\_INFO](../../atl/reference/atl-func-info-structure.md) 结构作为参数传递给每项。  在x86平台上，`_ATL_FUNC_INFO.cc` 值必须与调用\_\_stdcall的方法回调函数的CC\_CDECL。  
  
-   调用 [DispEventAdvise](../Topic/IDispEventSimpleImpl::DispEventAdvise.md) 生成源对象和基类之间的连接。  
  
-   调用 [DispEventUnadvise](../Topic/IDispEventSimpleImpl::DispEventUnadvise.md) 中断连接。  
  
 必须从 `IDispEventSimpleImpl` 派生\(使用 `nID`的单个值\)需要处理事件的每个对象的。  可以通过unadvising重新使用基类源对象并建议不同的源对象，但是，的源对象的最大数可由单个对象处理一次由 `IDispEventSimpleImpl` 基类的数目。  
  
 **IDispEventSimplImpl** 提供功能和 [IDispEventImpl](../../atl/reference/idispeventimpl-class.md)相同，除此之外，而不是接口的访问类型信息从类型库。  向导生成基于 `IDispEventImpl`仅的代码，但是，您可以手动添加代码使用 `IDispEventSimpleImpl`。  当您没有类型描述事件接口的库也不要避免开销与使用类型库时，请使用 `IDispEventSimpleImpl`。  
  
> [!NOTE]
>  `IDispEventImpl` 和 `IDispEventSimpleImpl` 提供自己 **IUnknown::QueryInterface** 的实现使每个 `IDispEventImpl` 或 `IDispEventSimpleImpl` 基类为单独的标识，同时仍允许直接访问类您的主程序COM对象时成员。  
  
 CE ActiveX事件接收器的ATL实现仅支持返回类型HRESULT或无效的值从您的事件处理程序方法的;任何其他返回值不受支持，并且其行为不确定。  
  
 有关更多信息，请参见 [支持IDispEventImpl](../../atl/supporting-idispeventimpl.md)。  
  
## 继承层次结构  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 `IDispEventSimpleImpl`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [\_ATL\_FUNC\_INFO Structure](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl Class](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventImpl Class](../../atl/reference/idispeventimpl-class.md)   
 [SINK\_ENTRY\_INFO](../Topic/SINK_ENTRY_INFO.md)   
 [Class Overview](../../atl/atl-class-overview.md)