---
title: "IOleObjectImpl Class | Microsoft Docs"
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
  - "ATL.IOleObjectImpl"
  - "ATL.IOleObjectImpl<T>"
  - "ATL::IOleObjectImpl"
  - "ATL::IOleObjectImpl<T>"
  - "IOleObjectImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], communication between container and control"
  - "IOleObject, ATL 实现"
  - "IOleObjectImpl class"
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IOleObjectImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现 **IUnknown** 是容器与控件进行通信的主体接口。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
class T   
>  
class ATL_NO_VTABLE IOleObjectImpl :  
public IOleObject  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IOleObjectImpl`。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IOleObjectImpl::Advise](../Topic/IOleObjectImpl::Advise.md)|生成与控件的建议使用性连接。|  
|[IOleObjectImpl::Close](../Topic/IOleObjectImpl::Close.md)|从运行更改控件的状态以填充。|  
|[IOleObjectImpl::DoVerb](../Topic/IOleObjectImpl::DoVerb.md)|调用控件执行其枚举操作之一。|  
|[IOleObjectImpl::DoVerbDiscardUndo](../Topic/IOleObjectImpl::DoVerbDiscardUndo.md)|通知控件放弃任何取消保留状态。|  
|[IOleObjectImpl::DoVerbHide](../Topic/IOleObjectImpl::DoVerbHide.md)|调用控件从视图中移除其用户界面。|  
|[IOleObjectImpl::DoVerbInPlaceActivate](../Topic/IOleObjectImpl::DoVerbInPlaceActivate.md)|运行控件并安装窗口，但是，不安装该控件的用户界面。|  
|[IOleObjectImpl::DoVerbOpen](../Topic/IOleObjectImpl::DoVerbOpen.md)|在单独的窗口会使控件在打开进行编辑。|  
|[IOleObjectImpl::DoVerbPrimary](../Topic/IOleObjectImpl::DoVerbPrimary.md)|当用户双击控件时，执行指定的操作。  控件定义事件，通常激活就地的控件。|  
|[IOleObjectImpl::DoVerbShow](../Topic/IOleObjectImpl::DoVerbShow.md)|显示一个新插入的控件给用户。|  
|[IOleObjectImpl::DoVerbUIActivate](../Topic/IOleObjectImpl::DoVerbUIActivate.md)|激活就地控件并显示控件的用户界面，例如菜单和工具栏。|  
|[IOleObjectImpl::EnumAdvise](../Topic/IOleObjectImpl::EnumAdvise.md)|枚举控件的建议使用性连接。|  
|[IOleObjectImpl::EnumVerbs](../Topic/IOleObjectImpl::EnumVerbs.md)|枚举控件的事件。|  
|[IOleObjectImpl::GetClientSite](../Topic/IOleObjectImpl::GetClientSite.md)|检索控件的客户端站点。|  
|[IOleObjectImpl::GetClipboardData](../Topic/IOleObjectImpl::GetClipboardData.md)|从剪贴板检索数据。  ATL实现返回 **E\_NOTIMPL**。|  
|[IOleObjectImpl::GetExtent](../Topic/IOleObjectImpl::GetExtent.md)|检索控件的显示区域的边界。|  
|[IOleObjectImpl::GetMiscStatus](../Topic/IOleObjectImpl::GetMiscStatus.md)|检索控件的状态。|  
|[IOleObjectImpl::GetMoniker](../Topic/IOleObjectImpl::GetMoniker.md)|检索控件的标记。  ATL实现返回 **E\_NOTIMPL**。|  
|[IOleObjectImpl::GetUserClassID](../Topic/IOleObjectImpl::GetUserClassID.md)|检索控件的选件类标识符。|  
|[IOleObjectImpl::GetUserType](../Topic/IOleObjectImpl::GetUserType.md)|检索控件的用户类型的名称。|  
|[IOleObjectImpl::InitFromData](../Topic/IOleObjectImpl::InitFromData.md)|初始化从选定数据的控件。  ATL实现返回 **E\_NOTIMPL**。|  
|[IOleObjectImpl::IsUpToDate](../Topic/IOleObjectImpl::IsUpToDate.md)|检查该控件是否是最新的。  ATL实现返回 `S_OK`。|  
|[IOleObjectImpl::OnPostVerbDiscardUndo](../Topic/IOleObjectImpl::OnPostVerbDiscardUndo.md)|调用 [DoVerbDiscardUndo](../Topic/IOleObjectImpl::DoVerbDiscardUndo.md) 在取消状态之后丢弃。|  
|[IOleObjectImpl::OnPostVerbHide](../Topic/IOleObjectImpl::OnPostVerbHide.md)|调用 [DoVerbHide](../Topic/IOleObjectImpl::DoVerbHide.md) 在控件之后隐藏。|  
|[IOleObjectImpl::OnPostVerbInPlaceActivate](../Topic/IOleObjectImpl::OnPostVerbInPlaceActivate.md)|调用 [DoVerbInPlaceActivate](../Topic/IOleObjectImpl::DoVerbInPlaceActivate.md) 在控件之后就地激活。|  
|[IOleObjectImpl::OnPostVerbOpen](../Topic/IOleObjectImpl::OnPostVerbOpen.md)|调用 [DoVerbOpen](../Topic/IOleObjectImpl::DoVerbOpen.md)，控件为编辑器中打开了在单独的窗口之后。|  
|[IOleObjectImpl::OnPostVerbShow](../Topic/IOleObjectImpl::OnPostVerbShow.md)|调用 [DoVerbShow](../Topic/IOleObjectImpl::DoVerbShow.md)，控件变得可见之后。|  
|[IOleObjectImpl::OnPostVerbUIActivate](../Topic/IOleObjectImpl::OnPostVerbUIActivate.md)|调用 [DoVerbUIActivate](../Topic/IOleObjectImpl::DoVerbUIActivate.md)，在活动之后控件的用户界面。|  
|[IOleObjectImpl::OnPreVerbDiscardUndo](../Topic/IOleObjectImpl::OnPreVerbDiscardUndo.md)|调用 [DoVerbDiscardUndo](../Topic/IOleObjectImpl::DoVerbDiscardUndo.md) 在取消状态之前丢弃。|  
|[IOleObjectImpl::OnPreVerbHide](../Topic/IOleObjectImpl::OnPreVerbHide.md)|调用 [DoVerbHide](../Topic/IOleObjectImpl::DoVerbHide.md) 在控件之前隐藏。|  
|[IOleObjectImpl::OnPreVerbInPlaceActivate](../Topic/IOleObjectImpl::OnPreVerbInPlaceActivate.md)|调用 [DoVerbInPlaceActivate](../Topic/IOleObjectImpl::DoVerbInPlaceActivate.md) 在控件前就地激活。|  
|[IOleObjectImpl::OnPreVerbOpen](../Topic/IOleObjectImpl::OnPreVerbOpen.md)|调用 [DoVerbOpen](../Topic/IOleObjectImpl::DoVerbOpen.md)，控件为编辑器中打开了在单独的窗口之前。|  
|[IOleObjectImpl::OnPreVerbShow](../Topic/IOleObjectImpl::OnPreVerbShow.md)|调用 [DoVerbShow](../Topic/IOleObjectImpl::DoVerbShow.md)，控件变得可见之前。|  
|[IOleObjectImpl::OnPreVerbUIActivate](../Topic/IOleObjectImpl::OnPreVerbUIActivate.md)|调用 [DoVerbUIActivate](../Topic/IOleObjectImpl::DoVerbUIActivate.md)，活动之前控件的用户界面。|  
|[IOleObjectImpl::SetClientSite](../Topic/IOleObjectImpl::SetClientSite.md)|通知其客户端站点的控件容器的。|  
|[IOleObjectImpl::SetColorScheme](../Topic/IOleObjectImpl::SetColorScheme.md)|建议配色方案对控件的应用程序，因此，如果有的话）。  ATL实现返回 **E\_NOTIMPL**。|  
|[IOleObjectImpl::SetExtent](../Topic/IOleObjectImpl::SetExtent.md)|设置控件的显示区域的边界。|  
|[IOleObjectImpl::SetHostNames](../Topic/IOleObjectImpl::SetHostNames.md)|通知控件容器应用程序的名称，并且该容器文档。|  
|[IOleObjectImpl::SetMoniker](../Topic/IOleObjectImpl::SetMoniker.md)|调用控件的方法标记为。  ATL实现返回 **E\_NOTIMPL**。|  
|[IOleObjectImpl::Unadvise](../Topic/IOleObjectImpl::Unadvise.md)|删除与控件的建议使用性连接。|  
|[IOleObjectImpl::Update](../Topic/IOleObjectImpl::Update.md)|更新的控件。  ATL实现返回 `S_OK`。|  
  
## 备注  
 [IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709) 接口是容器与控件进行通信的主体接口。  选件类 `IOleObjectImpl` 提供此接口的默认实现并将信息发送实现 **IUnknown** 到转储计算机进行编译。  
  
 **相关文章** [ATL教程](../../atl/active-template-library-atl-tutorial.md)，[创建ATL项目](../../atl/reference/creating-an-atl-project.md)  
  
## 继承层次结构  
 `IOleObject`  
  
 `IOleObjectImpl`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX Controls Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Class Overview](../../atl/atl-class-overview.md)