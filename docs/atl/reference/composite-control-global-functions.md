---
title: "Composite Control Global Functions | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "复合控件, 全局函数"
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
caps.latest.revision: 20
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Composite Control Global Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些功能提供支持创建对话框以及创建，承载和授权ActiveX控件。  
  
> [!IMPORTANT]
>  下表中列出的函数不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
|||  
|-|-|  
|[AtlAxDialogBox](../Topic/AtlAxDialogBox.md)|创建从用户提供的对话框模板的模式对话框。  随后出现的对话框中可以包含ActiveX控件。|  
|[AtlAxCreateDialog](../Topic/AtlAxCreateDialog.md)|创建从用户提供的对话框模板的无模式对话框。  随后出现的对话框中可以包含ActiveX控件。|  
|[AtlAxCreateControl](../Topic/AtlAxCreateControl.md)|创建一个ActiveX控件，将其初始化，并将其承载于指定的窗口。|  
|[AtlAxCreateControlEx](../Topic/AtlAxCreateControlEx.md)|创建一个ActiveX控件，将其初始化，承载它在指定的窗口，然后从控件检索接口指针\(或指针）。|  
|[AtlAxCreateControlLic](../Topic/AtlAxCreateControlLic.md)|创建一个授权的ActiveX控件，将其初始化，并将其承载于指定的窗口。|  
|[AtlAxCreateControlLicEx](../Topic/AtlAxCreateControlLicEx.md)|创建一个授权的ActiveX控件，将其初始化，承载它在指定的窗口，然后从控件检索接口指针\(或指针）。|  
|[AtlAxAttachControl](../Topic/AtlAxAttachControl.md)|附加以前创建的控件添加到指定的窗口。|  
|[AtlAxGetHost](../Topic/AtlAxGetHost.md)|用于获取一个直接接口指针到指定的窗口的容器（如果有）将其处理。|  
|[AtlAxGetControl](../Topic/AtlAxGetControl.md)|用于获取一个直接接口指针到控件中包含的于指定的窗口（如果有）将其处理。|  
|[AtlSetChildSite](../Topic/AtlSetChildSite.md)|初始化子站点的 **IUnknown**。|  
|[AtlAxWinInit](../Topic/AtlAxWinInit.md)|初始化AxWin对象的承载代码。|  
|[AtlAxWinTerm](../Topic/AtlAxWinTerm.md)|Uninitializes AxWin对象的承载代码。|  
|[AtlGetObjectSourceInterface](../Topic/AtlGetObjectSourceInterface.md)|返回有关对象的默认源接口的信息。|  
  
## 请参阅  
 [函数](../../atl/reference/atl-functions.md)   
 [Composite Control Macros](../../atl/reference/composite-control-macros.md)