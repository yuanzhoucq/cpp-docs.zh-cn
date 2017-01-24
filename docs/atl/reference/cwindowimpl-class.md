---
title: "CWindowImpl Class | Microsoft Docs"
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
  - "ATL::CWindowImpl"
  - "ATL.CWindowImpl"
  - "CWindowImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWindowImpl class"
  - "subclassing windows, ATL"
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWindowImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于创建或 subclassing 窗口的方法。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## 语法  
  
```  
  
      template <  
class T,  
class TBase= CWindow,  
class TWinTraits= CControlWinTraits   
>  
class ATL_NO_VTABLE CWindowImpl :  
public CWindowImplBaseT< TBase, TWinTraits>  
```  
  
#### 参数  
 `T`  
 您的新类从 `CWindowImpl` 派生  
  
 *TBase*  
 您的选件类基类。  默认情况下，基类为 [CWnd](../../atl/reference/cwindow-class.md)。  
  
 `TWinTraits`  
 定义了窗口的样式的 [特征选件类](../../atl/understanding-window-traits.md)。  默认值为 `CControlWinTraits`。  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CWindowImpl::Create](../Topic/CWindowImpl::Create.md)|创建一个窗口。|  
  
### CWindowImplBaseT 方法  
  
|||  
|-|-|  
|[DefWindowProc](../Topic/CWindowImpl::DefWindowProc.md)|提供一个默认值处理消息。|  
|[GetCurrentMessage](../Topic/CWindowImpl::GetCurrentMessage.md)|返回当前消息。|  
|[GetWindowProc](../Topic/CWindowImpl::GetWindowProc.md)|返回当前窗口过程。|  
|[OnFinalMessage](../Topic/CWindowImpl::OnFinalMessage.md)|调用最后一条消息后接收 \(通常 `WM_NCDESTROY`\)。|  
|[SubclassWindow](../Topic/CWindowImpl::SubclassWindow.md)|对窗口进行子分类。|  
|[UnsubclassWindow](../Topic/CWindowImpl::UnsubclassWindow.md)|恢复一个先前派生子类窗口|  
  
### 静态方法  
  
|||  
|-|-|  
|[GetWndClassInfo](../Topic/CWindowImpl::GetWndClassInfo.md)|返回 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)静态实例，管理窗口选件类信息。|  
|[窗口进程](../Topic/CWindowImpl::WindowProc.md)|处理发送到窗口。|  
  
### 数据成员  
  
|||  
|-|-|  
|[m\_pfnSuperWindowProc](../Topic/CWindowImpl::m_pfnSuperWindowProc.md)|指向窗口选件类的原始窗口过程。|  
  
## 备注  
 可以使用 `CWindowImpl` 创建窗口或子类现有的窗口。`CWindowImpl` 窗口过程使用消息映射处理消息的适当处理程序。  
  
 `CWindowImpl::Create` 创建根据 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)托管 windows 选件类信息的窗口。  `CWindowImpl` 包含 [DECLARE\_WND\_CLASS](../Topic/DECLARE_WND_CLASS.md) 宏，这意味着 `CWndClassInfo` 注册新的 windows 选件类。  如果要创建超类时现有窗口选件类，从 `CWindowImpl` 派生您的选件类并包含 [DECLARE\_WND\_SUPERCLASS](../Topic/DECLARE_WND_SUPERCLASS.md) 宏。  在这种情况下，`CWndClassInfo` 注册基于现有选件类，但在窗口选件类使用 `CWindowImpl::WindowProc`。  例如：  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/CPP/cwindowimpl-class_1.h)]  
  
> [!NOTE]
>  由于 `CWndClassInfo` 管理 windows 选件类的信息，通过 `CWindowImpl` 创建实例的每个窗口都根据同一窗口选件类。  
  
 `CWindowImpl` 还支持 subclassing 的窗口。  `SubclassWindow` 方法附加现有的窗口。`CWindowImpl` 对象和更改 windows 程序。`CWindowImpl::WindowProc`。  `CWindowImpl` 每个实例可以子类访问其他窗口。  
  
> [!NOTE]
>  对于任何给定 `CWindowImpl` 对象，请调用 **创建** 或 `SubclassWindow`。  不要对同一对象的两种方法。  
  
 除了 `CWindowImpl`外，ATL 提供 [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 创建在另一个对象包含的窗口。  
  
 基类析构函数 \(&#124;\)**CWindowImplRoot**确保窗口转到，在销毁之前对象。  
  
 `CWindowImpl` 从 **CWindowImplBaseT**派生，从 **CWindowImplRoot**派生，从 **TBase** 和 [CMessageMap](../../atl/reference/cmessagemap-class.md)派生。  
  
|有关以下内容的更多信息|请参见|  
|-----------------|---------|  
|创建控件|[ATL教程](../../atl/active-template-library-atl-tutorial.md)|  
|使用 ATL的窗口|[ATL 窗口类](../../atl/atl-window-classes.md)|  
|ATL 项目向导|[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)|  
  
## 继承层次结构  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CWindowImplBaseT`  
  
 `CWindowImpl`  
  
## 要求  
 **标头:** atlwin.h  
  
## 请参阅  
 [BEGIN\_MSG\_MAP](../Topic/BEGIN_MSG_MAP.md)   
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)