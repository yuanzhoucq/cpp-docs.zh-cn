---
title: "Which ATL Classes Facilitate ActiveX Control Containment? | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件容器 [C++], ATL control hosting"
  - "hosting controls using ATL"
ms.assetid: 803a4605-7f4c-4139-8638-49d8783d31b0
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Which ATL Classes Facilitate ActiveX Control Containment?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL的控件承载代码不需要使用任何ATL选件类;可以创建 **"AtlAxWin80"** 窗口并根据需要，使用控件承载API \(有关更多信息，请参见 [什么是控件承载API ATL?](../atl/what-is-the-atl-control-hosting-api-q.md)）。  但是，下面选件类使包容功能更易于使用。  
  
|类|说明|  
|-------|--------|  
|[CAxWindow](../atl/reference/caxwindow-class.md)|包装一 **"AtlAxWin80"** 窗口中，提供创建窗口中，创建控制和\/或控件附加到窗口和检索接口指针在宿主对象。|  
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|包装一 **"AtlAxWinLic80"** 窗口中，提供创建窗口中，创建控件并\/或附加一个授权控件到窗口和检索接口指针在宿主对象。|  
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|作为ActiveX基于对话框资源的控件选件类的基类。  此类控件可以包含其他ActiveX控件。|  
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|作为基于对话框资源的对话框选件类的基类。  此对话框可以包含ActiveX控件。|  
|[CWindow](../atl/reference/cwindow-class.md)|提供方法，[GetDlgControl](../Topic/CWindow::GetDlgControl.md)，将返回在控件的接口指针将承载它的窗口的ID。  此外，`CWindow` 显示的Windows API包装通常使窗口管理更加轻松。|  
  
## 请参阅  
 [控件包含常见问题](../atl/atl-control-containment-faq.md)