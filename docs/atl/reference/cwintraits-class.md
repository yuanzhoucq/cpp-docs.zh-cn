---
title: "CWinTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinTraits"
  - "CMDIChildWinTraits"
  - "ATL.CWinTraits"
  - "CFrameWinTraits"
  - "ATL::CWinTraits"
  - "CControlWinTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CControlWinTraits class"
  - "CFrameWinTraits class"
  - "CMDIChildWinTraits class"
  - "CWinTraits class"
  - "window styles, default values for ATL"
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CWinTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在创建windows对象时，此选件类出于标准化使用的样式提供方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
DWORD t_dwStyle= 0,  
DWORD t_dwExStyle= 0  
>  
class CWinTraits  
```  
  
#### 参数  
 `t_dwStyle`  
 默认标准窗口样式。  
  
 `t_dwExStyle`  
 默认扩展窗口样式。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CWinTraits::GetWndExStyle](../Topic/CWinTraits::GetWndExStyle.md)|（静态）来检索 `CWinTraits` 对象的扩展样式。|  
|[CWinTraits::GetWndStyle](../Topic/CWinTraits::GetWndStyle.md)|（静态）来检索 `CWinTraits` 对象的标准样式。|  
  
## 备注  
 此 [窗口特征](../../atl/understanding-window-traits.md) 选件类出于标准化用于ATL窗口创建该对象的样式提供简单的方法。  使用此选件类的专用化作为模板参数传递到 [CWindowImpl](../../atl/reference/cwindowimpl-class.md) 或其他ATL的窗口选件类指定标准该的默认和该窗口选件类实例的扩展样式。  
  
 请使用此模板，当您希望提供默认值将使用的windows样式时，只有当其他样式到 [CWindowImpl::Create](../Topic/CWindowImpl::Create.md)时的调用中指定。  
  
 ATL为windows样式的常用的组合提供此模板的三个预定义的专用化:  
  
 `CControlWinTraits`  
 设计用于标准控件的窗口。  使用以下标准样式: **WS\_CHILD**、 **WS\_VISIBLE**、 **WS\_CLIPCHILDREN**和 **WS\_CLIPSIBLINGS**。  不扩展样式。  
  
 `CFrameWinTraits`  
 用于标准帧窗口。  使用的标准样式包括: **WS\_OVERLAPPEDWINDOW**、 **WS\_CLIPCHILDREN**和 **WS\_CLIPSIBLINGS**。  使用的扩展样式包括: **WS\_EX\_APPWINDOW** 和 **WS\_EX\_WINDOWEDGE**。  
  
 `CMDIChildWinTraits`  
 用于标准MDI子窗口。  使用的标准样式包括: **WS\_OVERLAPPEDWINDOW**、 **WS\_CHILD**、 **WS\_VISIBLE**、 **WS\_CLIPCHILDREN**和 **WS\_CLIPSIBLINGS**。  使用的扩展样式包括: **WS\_EX\_MDICHILD**。  
  
 如果要确保特定样式为windows选件类的所有实例设置，并允许其他样式设置基于每个实例的基类型，使用 [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) 时。  
  
## 要求  
 **Header:** atlwin.h  
  
## 请参阅  
 [Class Members](http://msdn.microsoft.com/zh-cn/dbe6a147-3f01-4aea-a3fb-fe6ebadc31f8)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Understanding Window Traits](../../atl/understanding-window-traits.md)