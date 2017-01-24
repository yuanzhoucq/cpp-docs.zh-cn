---
title: "创建 COM 接口 (Visual C++) | Microsoft Docs"
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
  - "vc.codewiz.com.creating.interfaces"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM 接口, 创建"
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建 COM 接口 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 提供用于创建项目的向导和模板，而这些项目使用为 COM 对象和自动化类定义接口和调度接口的 COM。  
  
 可以使用这些向导执行下列三项常规任务：  
  
-   [向 MFC 项目添加 ATL 支持](../mfc/reference/adding-atl-support-to-your-mfc-project.md)  
  
     使用 [MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)创建 MFC 项目后，将 ATL 支持添加到 MFC 应用程序，然后运行“向 MFC 添加 ATL 支持”代码向导。  该支持仅应用到添加到 MFC 可执行文件或 DLL 项目的简单 COM 对象。  这些 ATL 对象可能有多个接口。  
  
-   [创建 MFC ActiveX 控件](../mfc/reference/creating-an-mfc-activex-control.md)  
  
     打开 [MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)创建在 .idl 文件和控件类中分别定义调度接口和事件映射的 ActiveX 控件。  
  
-   [添加 ATL 控件](../atl/reference/adding-an-atl-control.md)  
  
     使用 [ATL 项目向导](../atl/reference/atl-project-wizard.md)和 [ATL 控件向导](../atl/reference/atl-control-wizard.md)的组合创建 ATL ActiveX 控件。  
  
     也可以将 ATL 控件添加到已经添加了 ATL 支持的 MFC 项目，详见上文。  另外，如果在“添加类”对话框中选择**“ATL 控件”**，并且尚未为 MFC 项目添加 ATL 支持，Visual Studio 将显示一个确认是否为 MFC 项目添加 ATL 支持的对话框。  
  
     该向导在项目类中生成 IDL 源和 COM 映射。  
  
 打开了 ATL 项目后，[添加类](../ide/add-class-dialog-box.md)对话框将为您提供向项目添加 COM 接口的附加向导和模板。  下列向导允许为对象建立一个或多个接口：  
  
-   [ATL COM\+ 1.0 组件向导](../atl/reference/atl-com-plus-1-0-component-wizard.md)  
  
-   [ATL 简单对象向导](../atl/reference/atl-simple-object-wizard.md)  
  
-   [ATL Active Server Page 组件向导](../atl/reference/atl-active-server-page-component-wizard.md)  
  
-   [ATL 控件向导](../atl/reference/atl-control-wizard.md)  
  
 另外，还可通过在类视图中右击对象的控件类然后单击[实现接口](../ide/implement-interface-wizard.md)，在 COM 控件上实现新接口。  
  
> [!NOTE]
>  Visual Studio 不提供向项目添加接口的向导。  通过使用 [ATL 简单对象向导](../atl/reference/atl-simple-object-wizard.md)添加简单对象，可向 ATL 项目或向[“向 MFC 项目添加 ATL 支持”](../mfc/reference/adding-atl-support-to-your-mfc-project.md)添加接口。  或者，可打开项目的 .idl 文件并通过键入以下内容创建接口：  
  
```  
interface IMyInterface {  
};  
  
```  
  
 有关更多信息，请参见[实现接口](../ide/implementing-an-interface-visual-cpp.md)和[向 ATL 项目添加对象和控件](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。  
  
 Visual C\+\+ 提供多种查看和[编辑 COM 接口](../ide/editing-a-com-interface.md)（为项目而定义）的方法。  [“类视图”](http://msdn.microsoft.com/zh-cn/8d7430a9-3e33-454c-a9e1-a85e3d2db925)为 C\+\+ 项目的 .idl 文件中定义的任何接口或调度接口显示图标。  
  
 对基于 ATL 的 COM 对象类，类视图读取 ATL 类中的 COM 映射以显示 ATL 类和它实现的任何接口间的关系。  
  
 在类视图及其快捷菜单中，可以如下方式使用接口：  
  
-   将 ATL 对象添加到基于 MFC 的应用程序。  
  
-   添加方法、属性和事件。  
  
-   双击某项，直接跳转到它的接口代码。  
  
## 请参阅  
 [使用应用程序向导创建桌面项目](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)