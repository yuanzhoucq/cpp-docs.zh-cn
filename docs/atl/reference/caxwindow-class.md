---
title: "CAxWindow Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAxWindowT"
  - "CAxWindow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 承载 ActiveX 控件"
  - "CAxWindow class"
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CAxWindow Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供用于承载ActiveX控件的选件此类用于操作窗口。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CAxWindow : public CWindow  
  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[AttachControl](../Topic/CAxWindow::AttachControl.md)|附加现有的ActiveX控件绑定到 `CAxWindow` 对象。|  
|[CAxWindow](../Topic/CAxWindow::CAxWindow.md)|构造 `CAxWindow` 对象。|  
|[CreateControl](../Topic/CAxWindow::CreateControl.md)|创建一个ActiveX控件，将其初始化，并将其在 `CAxWindow` 窗口。|  
|[CreateControlEx](../Topic/CAxWindow::CreateControlEx.md)|创建一个ActiveX控件并从控件中检索接口指针\(或指针）。|  
|[GetWndClassName](../Topic/CAxWindow::GetWndClassName.md)|（静态）来检索 `CAxWindow` 对象的预定义的类名。|  
|[QueryControl](../Topic/CAxWindow::QueryControl.md)|检索承载ActiveX控件的 **IUnknown**。|  
|[QueryHost](../Topic/CAxWindow::QueryHost.md)|检索 `CAxWindow` 对象的 **IUnknown** 指针。|  
|[SetExternalDispatch](../Topic/CAxWindow::SetExternalDispatch.md)|设置 `CAxWindow` 对象的范围之外使用调度接口。|  
|[SetExternalUIHandler](../Topic/CAxWindow::SetExternalUIHandler.md)|设置 `CAxWindow` 对象使用的外部 **IDocHostUIHandler** 接口。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符\=](../Topic/CAxWindow::operator%20=.md)|分配 **HWND** 到现有的**CAxWindow** 对象。|  
  
## 备注  
 此选件类用于操作承载一个ActiveX控件的窗口的方法。  “**AtlAxWin80"**提供承载，由 `CAxWindow`包装。  
  
 选件类 `CAxWindow` 实现为 `CAxWindowT` 选件类的专用化。  此专用化声明如下所示:  
  
 `typedef CAxWindowT<CWindow> CAxWindow;`  
  
 如果需要更改基类，可以使用 `CAxWindowT` 并指定新的基类用作模板参数。  
  
## 要求  
 **Header:** atlwin.h  
  
## 请参阅  
 [ATLCON示例](../../top/visual-cpp-samples.md)   
 [CWindow Class](../../atl/reference/cwindow-class.md)   
 [复合控件基础知识](../../atl/atl-composite-control-fundamentals.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [控件包含常见问题](../../atl/atl-control-containment-faq.md)