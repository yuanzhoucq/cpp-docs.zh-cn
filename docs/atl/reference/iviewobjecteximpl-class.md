---
title: "IViewObjectExImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::IViewObjectExImpl<T>"
  - "ATL.IViewObjectExImpl"
  - "ATL::IViewObjectExImpl"
  - "ATL.IViewObjectExImpl<T>"
  - "IViewObjectExImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], drawing"
  - "advise sinks"
  - "IViewObjectEx ATL implementation"
  - "IViewObjectExImpl class"
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IViewObjectExImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现 **IUnknown** 并提供 [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763)、 [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318)和 [IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375) 接口的默认实现。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
class T   
>  
class ATL_NO_VTABLE IViewObjectExImpl :  
public IViewObjectEx  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IViewObjectExImpl`。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IViewObjectExImpl::Draw](../Topic/IViewObjectExImpl::Draw.md)|绘制控件的表示形式设备上下文上的。|  
|[IViewObjectExImpl::Freeze](../Topic/IViewObjectExImpl::Freeze.md)|冻结控件的绘制的表示形式，因此它不更改直到 `Unfreeze`。  ATL实现返回 **E\_NOTIMPL**。|  
|[IViewObjectExImpl::GetAdvise](../Topic/IViewObjectExImpl::GetAdvise.md)|如果有一个，检索控件的现有建议使用性接收器连接。|  
|[IViewObjectExImpl::GetColorSet](../Topic/IViewObjectExImpl::GetColorSet.md)|返回控件使用的逻辑调色板进行绘制。  ATL实现返回 **E\_NOTIMPL**。|  
|[IViewObjectExImpl::GetExtent](../Topic/IViewObjectExImpl::GetExtent.md)|从控件选件类数据成员 [CComControlBase::m\_sizeExtent](../Topic/CComControlBase::m_sizeExtent.md)检索在HIMETRIC单元\(每个单元0.01毫米控件的显示范围）。|  
|[IViewObjectExImpl::GetNaturalExtent](../Topic/IViewObjectExImpl::GetNaturalExtent.md)|有关使用的对象提供从容器的大小提示，用户调整其大小。|  
|[IViewObjectExImpl::GetRect](../Topic/IViewObjectExImpl::GetRect.md)|返回描述一个请求的绘制的各个方面的矩形。  ATL实现返回 **E\_NOTIMPL**。|  
|[IViewObjectExImpl::GetViewStatus](../Topic/IViewObjectExImpl::GetViewStatus.md)|返回有关对象的不透明度的信息，以及绘图方面支持。|  
|[IViewObjectExImpl::QueryHitPoint](../Topic/IViewObjectExImpl::QueryHitPoint.md)|检查指定的点是否在指定的矩形并返回该 `pHitResult`的一个 [HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187) 值。|  
|[IViewObjectExImpl::QueryHitRect](../Topic/IViewObjectExImpl::QueryHitRect.md)|检查控件的显示矩形是否在指定的位置矩形重叠的任意点并返回该 `pHitResult`的一个 **HITRESULT** 值。|  
|[IViewObjectExImpl::SetAdvise](../Topic/IViewObjectExImpl::SetAdvise.md)|设置控件和建议接收器之间的连接，因此该接收器会收到通知有关控件的视图中的更改。|  
|[IViewObjectExImpl::Unfreeze](../Topic/IViewObjectExImpl::Unfreeze.md)|解冻控件的绘制的表示形式。  ATL实现返回 **E\_NOTIMPL**。|  
  
## 备注  
 [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763)、 [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318)和 [IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375) 接口允许控件直接显示自身和创建和管理建议接收器通知容器控件中显示的更改。  **IViewObjectEx** 接口提供扩展控件的功能支持例如无闪烁的绘图，非矩形和透明控件和命中测试\(例如，在关闭鼠标单击控件必须将考虑）。  选件类 `IViewObjectExImpl` 提供这些接口的默认实现并将信息发送实现 **IUnknown** 到转储计算机进行编译。  
  
## 继承层次结构  
 `IViewObjectEx`  
  
 `IViewObjectExImpl`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX Controls Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [教程](../../atl/active-template-library-atl-tutorial.md)   
 [创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)   
 [Class Overview](../../atl/atl-class-overview.md)