---
title: "CComCompositeControl Class | Microsoft Docs"
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
  - "CComCompositeControl"
  - "ATL::CComCompositeControl"
  - "ATL.CComCompositeControl<T>"
  - "ATL.CComCompositeControl"
  - "ATL::CComCompositeControl<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComCompositeControl class"
  - "复合控件, CComCompositeControl class"
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComCompositeControl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供需要的方法实现复合控件。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
class T   
>  
class CComCompositeControl :  
public CComControl< T, CAxDialogImpl< T > >  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，以及从任何其他接口要用于复合控件支持。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CComCompositeControl::CComCompositeControl](../Topic/CComCompositeControl::CComCompositeControl.md)|构造函数。|  
|[CComCompositeControl::~CComCompositeControl](../Topic/CComCompositeControl::~CComCompositeControl.md)|该析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CComCompositeControl::AdviseSinkMap](../Topic/CComCompositeControl::AdviseSinkMap.md)|调用此方法建议或unadvise该复合控件中承载的所有控件。|  
|[CComCompositeControl::CalcExtent](../Topic/CComCompositeControl::CalcExtent.md)|调用此方法计算在所使用的对话框资源的 **HIMETRIC** 单元的大小承载复合控件。|  
|[CComCompositeControl::Create](../Topic/CComCompositeControl::Create.md)|此方法调用创建复合控件的控件的窗口。|  
|[CComCompositeControl::CreateControlWindow](../Topic/CComCompositeControl::CreateControlWindow.md)|调用此方法创建控件的窗口和建议所有承载控件。|  
|[CComCompositeControl::SetBackgroundColorFromAmbient](../Topic/CComCompositeControl::SetBackgroundColorFromAmbient.md)|使用容器的背景色，调用此方法将复合控件的背景色。|  
  
### 公共数据成员  
  
|名称|描述|  
|--------|--------|  
|[CComCompositeControl::m\_hbrBackground](../Topic/CComCompositeControl::m_hbrBackground.md)|背景画笔。|  
|[CComCompositeControl::m\_hWndFocus](../Topic/CComCompositeControl::m_hWndFocus.md)|当前具有焦点的窗口的句柄。|  
  
## 备注  
 从选件类派生的选件类 `CComCompositeControl` 继承ActiveX复合控件的功能。  从 `CComCompositeControl` 派生的ActiveX控件由标准对话框承载。  以下类型的控件调用复合控件，因为它们可以承载其他控件\(本机Windows控件和ActiveX控件\)。  
  
 `CComCompositeControl` 在创建标识对话框资源使用该复合控件通过查找一个计数值成员在子选件类。  此子选件类的成员IDD设置为将用作控件windows对话框资源的资源ID。  下面是从 `CComCompositeControl` 派生的选件类应包含标识用于控制windows将使用的对话框资源数据成员的示例:  
  
 [!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/CPP/ccomcompositecontrol-class_1.h)]  
  
> [!NOTE]
>  复合控件始终有窗口的控件，不过，它们可能包含无窗口控件。  
  
 `CComCompositeControl`实现的控件\-具有默认tab键行为安装的派生类。  当控件通过选项卡式接收焦点到包含组件的应用程序，串行按tab键将导致焦点通过所有复合控件所包含的控件中循环，然后从该复合控件和到下一个项目选项按容器的序列。  对话框资源取决于承载的控件的tab键顺序并确定选定将发生的顺序。  
  
> [!NOTE]
>  为了快捷键可以用于 `CComCompositeControl`时，加载快捷键对应表，因为控件创建有必要，通过快捷键的句柄和数量回 [IOleControlImpl::GetControlInfo](../Topic/IOleControlImpl::GetControlInfo.md)最后销毁表，释放该控件。  
  
## 示例  
 [!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/CPP/ccomcompositecontrol-class_2.h)]  
  
## 继承层次结构  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 [CComControl](../../atl/reference/ccomcontrol-class.md)  
  
 `CComCompositeControl`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [复合控件基础知识](../../atl/atl-composite-control-fundamentals.md)   
 [Class Overview](../../atl/atl-class-overview.md)