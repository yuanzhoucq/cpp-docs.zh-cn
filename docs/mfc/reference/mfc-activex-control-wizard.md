---
title: "MFC ActiveX 控件向导 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.ctl.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], MFC"
  - "MFC ActiveX 控件向导"
  - "MFC ActiveX 控件 [C++], 向导"
  - "OLE 控件 [C++]"
  - "OLE 控件 [C++], 创建"
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ActiveX 控件是特定的[自动化服务器](../../mfc/automation-servers.md)类型；它是可重用的组件。  承载 ActiveX 控件的应用程序是该控件的[自动化客户端](../../mfc/automation-clients.md)。  如果目标是创建这种可重用的组件，则使用该向导创建控件。  有关更多信息，请参见 [MFC ActiveX 控件](../../mfc/mfc-activex-controls.md)。  
  
 或者，可以使用 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)创建自动化服务器 MFC 应用程序。  
  
 用该向导创建的 ActiveX 控件可以有用户界面或是不可见的。  可以在向导的[控件设置](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)页中指示此选项。  计时器 \(Timer\) 控件是希望其不可见的 ActiveX 控件的示例。  
  
 ActiveX 控件可以有复杂的用户界面。  一些控件可以像封装窗体：一个控件包含许多字段，而每个字段本身就是一个 Windows 控件。  例如，作为 MFC ActiveX 控件实现的自动部件对象可能呈现类似窗体的用户界面，通过该界面用户可以读取和编辑部件编号、部件名称和其他信息。  有关更多信息，请参见 [MFC ActiveX 控件](../../mfc/mfc-activex-controls.md)。  
  
 如果需要创建 ActiveX 对象容器，请参见[创建 ActiveX 控件容器](../../mfc/reference/creating-an-mfc-activex-control-container.md)。  
  
 MFC 起始程序包括 C\+\+ 源文件 \(.cpp\)、资源文件 \(.rc\) 和一个项目文件 \(.vcxproj\)。  这些起始文件中生成的代码基于 MFC。  
  
 下面的示例列表显示 ActiveX 控件的增强任务和类型：  
  
-   [优化 ActiveX 控件](../../mfc/mfc-activex-controls-optimization.md)  
  
-   [向 ActiveX 控件添加常用事件](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [添加自定义事件](../../mfc/mfc-activex-controls-adding-custom-events.md)  
  
-   [添加常用方法](../../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [添加自定义方法](../../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [添加常用属性](../../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [添加自定义属性](../../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [ActiveX 控件容器中的 ActiveX 控件编程](../../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
## 概述  
 此向导页描述正在创建的 MFC ActiveX 控件项目的当前应用程序设置。  默认情况下，该向导按如下方式创建项目：  
  
-   默认项目不生成运行时许可证和帮助文件。  可以在[应用程序设置](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)页中更改这些默认设置。  只有在该 ActiveX 控件向导页中所做的选择才反映在“概述”页中。  
  
-   项目包括基于项目名称的控件类和属性页类。  可以在[控件名称](../../mfc/reference/control-names-mfc-activex-control-wizard.md)页中编辑项目名称和文件名。  
  
-   控件不基于现有的 Windows 控件，当变为可见时激活，有用户界面并且包括**“关于”**对话框。  可以在[控件设置](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)页中更改这些默认设置。  
  
## 请参阅  
 [创建和管理 Visual C\+\+ 项目](../../ide/creating-and-managing-visual-cpp-projects.md)   
 [Visual C\+\+ 项目类型](../../ide/visual-cpp-project-types.md)   
 [概念](../../atl/active-template-library-atl-concepts.md)