---
title: "CContainedWindowT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CContainedWindow"
  - "CContainedWindowT"
  - "ATL.CContainedWindowT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CContainedWindow class"
  - "CContainedWindowT class"
  - "contained windows"
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CContainedWindowT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现在其他对象中包含的窗口。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
class TBase= CWindow,  
class TWinTraits= CControlWinTraits   
>  
class CContainedWindowT :  
public TBase  
```  
  
#### 参数  
 *TBase*  
 将新选件类基类。  默认基类是 `CWindow`。  
  
 `TWinTraits`  
 特征的类定义了窗口的样式。  默认值为 `CControlWinTraits`。  
  
> [!NOTE]
>  [CContainedWindow](../Topic/CContainedWindow.md) 是 `CContainedWindowT`的专用化。  如果要更改基类或特征，请直接使用 `CContainedWindowT`。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CContainedWindowT::CContainedWindowT](../Topic/CContainedWindowT::CContainedWindowT.md)|构造函数。  初始化数据成员指定消息映射将处理包含窗口的消息。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CContainedWindowT::Create](../Topic/CContainedWindowT::Create.md)|创建一个窗口。|  
|[CContainedWindowT::DefWindowProc](../Topic/CContainedWindowT::DefWindowProc.md)|提供默认处理消息。|  
|[CContainedWindowT::GetCurrentMessage](../Topic/CContainedWindowT::GetCurrentMessage.md)|返回当前消息。|  
|[CContainedWindowT::RegisterWndSuperclass](../Topic/CContainedWindowT::RegisterWndSuperclass.md)|注册包含的窗口的窗口选件类。|  
|[CContainedWindowT::SubclassWindow](../Topic/CContainedWindowT::SubclassWindow.md)|子类窗口。|  
|[CContainedWindowT::SwitchMessageMap](../Topic/CContainedWindowT::SwitchMessageMap.md)|更改消息映射来处理包含窗口的消息。|  
|[CContainedWindowT::UnsubclassWindow](../Topic/CContainedWindowT::UnsubclassWindow.md)|还原以前子类窗口。|  
|[CContainedWindowT::WindowProc](../Topic/CContainedWindowT::WindowProc.md)|（静态）处理发送到包含窗口。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CContainedWindowT::m\_dwMsgMapID](../Topic/CContainedWindowT::m_dwMsgMapID.md)|标识消息映射将处理包含窗口的消息。|  
|[CContainedWindowT::m\_lpszClassName](../Topic/CContainedWindowT::m_lpszClassName.md)|指定新窗口选件类现有窗口选件类的名称。|  
|[CContainedWindowT::m\_pfnSuperWindowProc](../Topic/CContainedWindowT::m_pfnSuperWindowProc.md)|指向窗口选件类的原始窗口过程。|  
|[CContainedWindowT::m\_pObject](../Topic/CContainedWindowT::m_pObject.md)|指向包含的对象。|  
  
## 备注  
 `CContainedWindowT` 实现在其他对象中包含的窗口。  `CContainedWindowT`的窗口过程在对直接消息包含的对象使用消息映射到相应的处理程序。  当构造 `CContainedWindowT` 对象时，指定应使用哪消息映射。  
  
 `CContainedWindowT` 允许您通过创建超类现有窗口选件类创建一个新窗口。  **Create** 方法的第一个注册基于现有选件类，但在窗口选件类使用 `CContainedWindowT::WindowProc`。  **Create** 然后创建基于此新窗口选件类的窗口。  `CContainedWindowT` 每个实例可以创建超类时应用程序中采用不同的windows选件类。  
  
 `CContainedWindowT` 还支持subclassing的窗口。  `SubclassWindow` 方法附加现有的窗口。`CContainedWindowT` 对象和更改windows程序。`CContainedWindowT::WindowProc`。  `CContainedWindowT` 每个实例可以子类访问其他窗口。  
  
> [!NOTE]
>  对于任何给定 `CContainedWindowT` 对象，请调用 **Create** 或 `SubclassWindow`。  您不应调用在同一对象的两种方法。  
  
 当您在ATL项目向导使用 **Add control based on** 选项，向导会自动添加一个 `CContainedWindowT` 数据成员添加到实现控件的选件类。  下面的示例演示包含窗口如何声明:  
  
 [!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/CPP/ccontainedwindowt-class_1.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/CPP/ccontainedwindowt-class_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/CPP/ccontainedwindowt-class_3.h)]  
  
|有关以下内容的更多信息|请参见|  
|-----------------|---------|  
|创建控件|[ATL教程](../../atl/active-template-library-atl-tutorial.md)|  
|使用在ATL的窗口|[ATL窗口选件类](../../atl/atl-window-classes.md)|  
|ATL项目向导|[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)|  
|窗口|[Windows](http://msdn.microsoft.com/library/windows/desktop/ms632595) 及随后的主题。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]|  
  
## 继承层次结构  
 `TBase`  
  
 `CContainedWindowT`  
  
## 要求  
 **Header:** atlwin.h  
  
## 请参阅  
 [CWindow Class](../../atl/reference/cwindow-class.md)   
 [CWindowImpl Class](../../atl/reference/cwindowimpl-class.md)   
 [CMessageMap Class](../../atl/reference/cmessagemap-class.md)   
 [BEGIN\_MSG\_MAP](../Topic/BEGIN_MSG_MAP.md)   
 [ALT\_MSG\_MAP](../Topic/ALT_MSG_MAP.md)   
 [Class Overview](../../atl/atl-class-overview.md)