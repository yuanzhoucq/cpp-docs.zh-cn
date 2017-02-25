---
title: "IAxWinAmbientDispatch Interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IAxWinAmbientDispatch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAxWinAmbientDispatch interface"
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# IAxWinAmbientDispatch Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此接口指定承载的控件或容器的属性的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
interface IAxWinAmbientDispatch : IDispatch  
  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[get\_AllowContextMenu](../Topic/IAxWinAmbientDispatch::get_AllowContextMenu.md)|**AllowContextMenu** 属性指定所承载的控件是否允许显示其自己的上下文菜单。|  
|[get\_AllowShowUI](../Topic/IAxWinAmbientDispatch::get_AllowShowUI.md)|**AllowShowUI** 属性指定所承载的控件是否允许显示其自己的用户界面。|  
|[get\_AllowWindowlessActivation](../Topic/IAxWinAmbientDispatch::get_AllowWindowlessActivation.md)|**AllowWindowlessActivation** 属性指定容器是将允许无窗口的激活。|  
|[get\_BackColor](../Topic/IAxWinAmbientDispatch::get_BackColor.md)|`BackColor` 属性指定容器的单个背景色。|  
|[get\_DisplayAsDefault](../Topic/IAxWinAmbientDispatch::get_DisplayAsDefault.md)|**DisplayAsDefault** 是允许查看控件的一个环境属性，如果它是默认控件。|  
|[get\_DocHostDoubleClickFlags](../Topic/IAxWinAmbientDispatch::get_DocHostDoubleClickFlags.md)|**DocHostDoubleClickFlags** 属性指定应在响应双击的操作。|  
|[get\_DocHostFlags](../Topic/IAxWinAmbientDispatch::get_DocHostFlags.md)|**DocHostFlags** 属性指定宿主对象的用户界面功能。|  
|[get\_Font](../Topic/IAxWinAmbientDispatch::get_Font.md)|**Font** 属性指定容器的单个字体。|  
|[get\_ForeColor](../Topic/IAxWinAmbientDispatch::get_ForeColor.md)|`ForeColor` 属性指定容器的单个前景色。|  
|[get\_LocaleID](../Topic/IAxWinAmbientDispatch::get_LocaleID.md)|**LocaleID** 属性指定容器的单个区域设置ID。|  
|[get\_MessageReflect](../Topic/IAxWinAmbientDispatch::get_MessageReflect.md)|**MessageReflect** 环境属性指定容器是将反映消息传递给承载控件。|  
|[get\_OptionKeyPath](../Topic/IAxWinAmbientDispatch::get_OptionKeyPath.md)|**OptionKeyPath** 属性指定注册表项路径用户设置。|  
|[get\_ShowGrabHandles](../Topic/IAxWinAmbientDispatch::get_ShowGrabHandles.md)|则应使用自行绘制抓取手柄，**ShowGrabHandles** 环境属性允许控件发现。|  
|[get\_ShowHatching](../Topic/IAxWinAmbientDispatch::get_ShowHatching.md)|则应自行绘制阴影的，**ShowHatching** 环境属性允许控件发现。|  
|[get\_UserMode](../Topic/IAxWinAmbientDispatch::get_UserMode.md)|**UserMode** 属性指定容器的单个用户模式。|  
|[put\_AllowContextMenu](../Topic/IAxWinAmbientDispatch::put_AllowContextMenu.md)|**AllowContextMenu** 属性指定所承载的控件是否允许显示其自己的上下文菜单。|  
|[put\_AllowShowUI](../Topic/IAxWinAmbientDispatch::put_AllowShowUI.md)|**AllowShowUI** 属性指定所承载的控件是否允许显示其自己的用户界面。|  
|[put\_AllowWindowlessActivation](../Topic/IAxWinAmbientDispatch::put_AllowWindowlessActivation.md)|**AllowWindowlessActivation** 属性指定容器是将允许无窗口的激活。|  
|[put\_BackColor](../Topic/IAxWinAmbientDispatch::put_BackColor.md)|`BackColor` 属性指定容器的单个背景色。|  
|[put\_DisplayAsDefault](../Topic/IAxWinAmbientDispatch::put_DisplayAsDefault.md)|**DisplayAsDefault** 是允许查看控件的一个环境属性，如果它是默认控件。|  
|[put\_DocHostDoubleClickFlags](../Topic/IAxWinAmbientDispatch::put_DocHostDoubleClickFlags.md)|**DocHostDoubleClickFlags** 属性指定应在响应双击的操作。|  
|[put\_DocHostFlags](../Topic/IAxWinAmbientDispatch::put_DocHostFlags.md)|**DocHostFlags** 属性指定宿主对象的用户界面功能。|  
|[put\_Font](../Topic/IAxWinAmbientDispatch::put_Font.md)|**Font** 属性指定容器的单个字体。|  
|[put\_ForeColor](../Topic/IAxWinAmbientDispatch::put_ForeColor.md)|`ForeColor` 属性指定容器的单个前景色。|  
|[put\_LocaleID](../Topic/IAxWinAmbientDispatch::put_LocaleID.md)|**LocaleID** 属性指定容器的单个区域设置ID。|  
|[put\_MessageReflect](../Topic/IAxWinAmbientDispatch::put_MessageReflect.md)|**MessageReflect** 环境属性指定容器是将反映消息传递给承载控件。|  
|[put\_OptionKeyPath](../Topic/IAxWinAmbientDispatch::put_OptionKeyPath.md)|**OptionKeyPath** 属性指定注册表项路径用户设置。|  
|[put\_UserMode](../Topic/IAxWinAmbientDispatch::put_UserMode.md)|**UserMode** 属性指定容器的单个用户模式。|  
  
## 备注  
 此接口由ATL的承载对象的ActiveX控件显示。  调用此接口的方法设置环境属性可为承载的控件或指定容器的行为的其他方面。  若要添加属性。`IAxWinAmbientDispatch`提供了，使用 [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)。  
  
 [AXHost](https://msdn.microsoft.com/en-us/library/system.windows.forms.axhost.aspx) 将尝试从包含代码的类型库加载有关 `IAxWinAmbientDispatch` 和 `IAxWinAmbientDispatchEx` 的类型信息。  
  
 如果使用ATL90.dll链接，**AXHost** 从类型库将加载该类型信息在DLL。  
  
 有关详细信息 [承载使用ATL AXHost的ActiveX控件](../../atl/hosting-activex-controls-using-atl-axhost.md) 参见。  
  
## 要求  
 此接口的定义的多种形式，如下表所示。  
  
|定义类型|文件|  
|----------|--------|  
|IDL|atliface.idl|  
|类型库|ATL.dll|  
|C\+\+|atliface.h \(也包括在ATLBase.h\)|  
  
## 请参阅  
 [IAxWinAmbientDispatchEx Interface](../../atl/reference/iaxwinambientdispatchex-interface.md)   
 [IAxWinHostWindow Interface](../../atl/reference/iaxwinhostwindow-interface.md)   
 [CAxWindow::QueryHost](../Topic/CAxWindow::QueryHost.md)   
 [AtlAxGetHost](../Topic/AtlAxGetHost.md)