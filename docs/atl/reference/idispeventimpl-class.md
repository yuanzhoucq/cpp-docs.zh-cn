---
title: "IDispEventImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IDispEventImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDispEventImpl class"
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDispEventImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供 `IDispatch` 方法的实现。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
UINT nID,  
class T,  
const IID* pdiid= &IID_NULL,  
const GUID* plibid= &GUID_NULL,  
WORD wMajor= 0,  
WORD wMinor= 0,  
class tihclass= CcomTypeInfoHolder  
>  
class ATL_NO_VTABLE IDispEventImpl :  
public IDispEventSimpleImpl<nID, T, pdiid>  
```  
  
#### 参数  
 `nID`  
 源对象的唯一标识符。  当 `IDispEventImpl` 是复合控件时基类，提供此参数将所需包含控件的资源ID。  在某些情况下，使用一个随机的正整数。  
  
 `T`  
 用户的选件类，从 `IDispEventImpl`派生。  
  
 `pdiid`  
 此选件类实现事件的调度接口的IID的指针。  在类型 `plibid`、 `wMajor`和 `wMinor`表示的库必须定义此接口。  
  
 `plibid`  
 用于定义调度接口的类型库的指针指向由 `pdiid`。  如果 **&GUID\_NULL**，类型库从对象源添加将加载事件。  
  
 `wMajor`  
 类型库的主版本。  默认值为 0。  
  
 `wMinor`  
 类型库的次版本。  默认值为 0。  
  
 `tihclass`  
 用于的选件类管理 `T`的类型信息。  默认值为类型 `CComTypeInfoHolder`选件类;但是，除 `CComTypeInfoHolder`外，还可以通过提供类型的选件类重写此模板参数。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[IDispEventImpl::\_tihclass](../../atl/reference/idispeventimpl-class.md)|用于的选件类管理类型信息。  默认为 `CComTypeInfoHolder`。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[IDispEventImpl::IDispEventImpl](../Topic/IDispEventImpl::IDispEventImpl.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IDispEventImpl::GetFuncInfoFromId](../Topic/IDispEventImpl::GetFuncInfoFromId.md)|设置指定的调度标识符的功能索引。|  
|[IDispEventImpl::GetIDsOfNames](../Topic/IDispEventImpl::GetIDsOfNames.md)|映射一个成员和可选设置参数名称与相应设置整数Dispid。|  
|[IDispEventImpl::GetTypeInfo](../Topic/IDispEventImpl::GetTypeInfo.md)|检索对象的类型信息。|  
|[IDispEventImpl::GetTypeInfoCount](../Topic/IDispEventImpl::GetTypeInfoCount.md)|检索类型信息接口的数字。|  
|[IDispEventImpl::GetUserDefinedType](../Topic/IDispEventImpl::GetUserDefinedType.md)|检索一个用户定义的类型的基本类型。|  
  
## 备注  
 `IDispEventImpl` 提供实现事件调度接口方法，无需提供每个方法\/事件的代码实现该接口。  `IDispEventImpl` 提供 `IDispatch` 方法的实现。  只需提供事件的实现您对处理感兴趣。  
  
 `IDispEventImpl` 与您的选件类的 [事件接收器映射](../Topic/BEGIN_SINK_MAP.md) 一起使用路由事件到适当的处理程序函数。  使用此选件类:  
  
 添加一 [SINK\_ENTRY](../Topic/SINK_ENTRY.md) 或 [SINK\_ENTRY\_EX](../Topic/SINK_ENTRY_EX.md) 宏到每个事件接收器映射在要处理的每个对象。  当使用 `IDispEventImpl` 为复合控件的基类时，可以在事件接收器映射可以调用 [AtlAdviseSinkMap](../Topic/AtlAdviseSinkMap.md) 生成并中断与事件源的连接所有项。  在某些情况下，或者更大的控件，需要 [DispEventAdvise](../Topic/IDispEventSimpleImpl::DispEventAdvise.md) 生成源对象和基类之间的连接。  调用 [DispEventUnadvise](../Topic/IDispEventSimpleImpl::DispEventUnadvise.md) 中断连接。  
  
 必须从 `IDispEventImpl` 派生\(使用 `nID`的单个值\)需要处理事件的每个对象的。  可以通过unadvising重新使用基类源对象并建议不同的源对象，但是，的源对象的最大数可由单个对象处理一次由 `IDispEventImpl` 基类的数目。  
  
 `IDispEventImpl` 提供功能和 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)相同，不同之处在于，它从类型库获取有关接口的类型信息\(而不是它的形式提供指向 [\_ATL\_FUNC\_INFO](../../atl/reference/atl-func-info-structure.md) 结构。  当您没有类型描述事件接口的库也不要避免开销与使用类型库时，请使用 `IDispEventSimpleImpl`。  
  
> [!NOTE]
>  `IDispEventImpl` 和 `IDispEventSimpleImpl` 提供自己 **IUnknown::QueryInterface** 的实现使每个 `IDispEventImpl` 和 `IDispEventSimpleImpl` 基类为单独的标识，同时仍允许直接访问类您的主程序COM对象时成员。  
  
 CE ActiveX事件接收器的ATL实现仅支持返回类型HRESULT或无效的值从您的事件处理程序方法的;任何其他返回值不受支持，并且其行为不确定。  
  
 有关更多信息，请参见 [支持IDispEventImpl](../../atl/supporting-idispeventimpl.md)。  
  
## 继承层次结构  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)  
  
 `IDispEventImpl`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [\_ATL\_FUNC\_INFO Structure](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl Class](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventSimpleImpl Class](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK\_ENTRY](../Topic/SINK_ENTRY.md)   
 [SINK\_ENTRY\_EX](../Topic/SINK_ENTRY_EX.md)   
 [SINK\_ENTRY\_INFO](../Topic/SINK_ENTRY_INFO.md)   
 [Class Overview](../../atl/atl-class-overview.md)