---
title: "CComControl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComControl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ambient properties"
  - "CComControl class"
  - "CComControlBase class, CComControl class"
  - "control flags"
  - "控件 [ATL], control helper functions"
  - "控件 [ATL], 属性"
  - "常用属性, ATL"
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComControl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类为创建和管理ATL控件的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
class T,  
class WinBase= CWindowImpl< T>   
>  
class ATL_NO_VTABLE CComControl :  
public CComControlBase, public WinBase;  
```  
  
#### 参数  
 `T`  
 实现控件的选件类。  
  
 *WinBase*  
 基类实现多窗口功能。  为 [CWindowImpl](../../atl/reference/cwindowimpl-class.md)的默认值。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComControl::CComControl](../Topic/CComControl::CComControl.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComControl::ControlQueryInterface](../Topic/CComControl::ControlQueryInterface.md)|检索指向请求的接口。|  
|[CComControl::CreateControlWindow](../Topic/CComControl::CreateControlWindow.md)|创建控件的窗口。|  
|[CComControl::FireOnChanged](../Topic/CComControl::FireOnChanged.md)|通知容器接收器的控件属性已更改。|  
|[CComControl::FireOnRequestEdit](../Topic/CComControl::FireOnRequestEdit.md)|通知容器接收器的控件属性将更改，并且对象是询问该接收器如何执行。|  
|[CComControl::MessageBox](../Topic/CComControl::MessageBox.md)|调用此方法创建，显示和运行消息框。|  
  
## 备注  
 `CComControl` 是设置有用的控件helper函数和关键数据成员ATL控件的。  使用ATL控件向导，当您创建标准控件或一个DHTML控件，该向导从 `CComControl`将自动派生您的选件类。  `CComControl` 从 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)派生其大多数方法。  
  
 有关创建控件的更多信息，请参见 [ATL教程](../../atl/active-template-library-atl-tutorial.md)。  有关ATL项目向导的更多信息，请参见文章 [创建ATL项目](../../atl/reference/creating-an-atl-project.md)。  
  
 有关 `CComControl` 方法和数据成员的演示，请参见 [CIRC](../../top/visual-cpp-samples.md) 示例。  
  
## 继承层次结构  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 `CComControl`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [CWindowImpl Class](../../atl/reference/cwindowimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComControlBase Class](../../atl/reference/ccomcontrolbase-class.md)   
 [CComCompositeControl Class](../../atl/reference/ccomcompositecontrol-class.md)