---
title: "What Is the ATL Control-Hosting API? | Microsoft Docs"
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
  - "API [C++], hosting"
  - "control-hosting API"
  - "控件 [ATL], 承载 API"
ms.assetid: 75b27e45-cfba-4950-aa35-96cc7d8da753
caps.latest.revision: 15
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# What Is the ATL Control-Hosting API?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控件承载API ATL的是允许所有窗口作为ActiveX控件容器的功能。  这些函数可以静态或动态链接到您的项目，因为它们可用作为源代码并由ATL90.dll显示。  控件承载函数在下表中列出。  
  
|功能|说明|  
|--------|--------|  
|[AtlAxAttachControl](../Topic/AtlAxAttachControl.md)|创建一个宿主对象，将其连接到所提供的窗口，然后附加现有控件。|  
|[AtlAxCreateControl](../Topic/AtlAxCreateControl.md)|创建一个宿主对象，将其连接到所提供的窗口，然后填充控件。|  
|[AtlAxCreateControlLic](../Topic/AtlAxCreateControlLic.md)|创建一个授权的ActiveX控件，将其初始化，并将其承载于指定的窗口，与 [AtlAxCreateControl](../Topic/AtlAxCreateControl.md)。|  
|[AtlAxCreateControlEx](../Topic/AtlAxCreateControlEx.md)|创建一个宿主对象，将其连接到所提供的窗口，然后加载控件\(也允许事件接收器设置为）。|  
|[AtlAxCreateControlLicEx](../Topic/AtlAxCreateControlLicEx.md)|创建一个授权的ActiveX控件，将其初始化，并将其承载于指定的窗口，与 [AtlAxCreateControlLic](../Topic/AtlAxCreateControlLic.md)。|  
|[AtlAxCreateDialog](../Topic/AtlAxCreateDialog.md)|创建从对话框资源的无模式对话框并返回窗口句柄。|  
|[AtlAxDialogBox](../Topic/AtlAxDialogBox.md)|创建从对话框资源的模式对话框。|  
|[AtlAxGetControl](../Topic/AtlAxGetControl.md)|返回在窗口中承载的控件的 **IUnknown** 接口指针。|  
|[AtlAxGetHost](../Topic/AtlAxGetHost.md)|返回宿主对象的 **IUnknown** 接口指针连接到窗口。|  
|[AtlAxWinInit](../Topic/AtlAxWinInit.md)|初始化控件承载代码。|  
|[AtlAxWinTerm](../Topic/AtlAxWinTerm.md)|Uninitializes控件承载代码。|  
  
 前三个功能的 `HWND` 参数必须是现有的窗口\(几乎任何类型。）  如果显式调用这三个函数中的任何一个\(通常，您就不必\)，请不要通过处理已为宿主的窗口\(如果您，现有的宿主对象不会释放）。  
  
 前七隐式函数调用 [AtlAxWinInit](../Topic/AtlAxWinInit.md)。  
  
> [!NOTE]
>  控件承载API窗体ATL的基础。ActiveX控件包容支持。  但是，因此，如果利用或充分利用ATL的包装选件类，通常有一点需要直接调用这些函数。  有关更多信息，请参见 [要ATL分类ActiveX控件包容?](../atl/which-atl-classes-facilitate-activex-control-containment-q.md)。  
  
## 请参阅  
 [控件包含常见问题](../atl/atl-control-containment-faq.md)