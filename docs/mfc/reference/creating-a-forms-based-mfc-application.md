---
title: "创建基于窗体的 MFC 应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfcforms.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序 [MFC], 基于窗体"
  - "基于窗体的应用程序"
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 创建基于窗体的 MFC 应用程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

窗体是一个对话框，包含允许用户访问数据（可能还允许更改数据）的控件。  可能需要开发一个用户可从窗体选项中进行选择的应用程序。  通常，基于应用程序的窗体允许用户通过单击 **文件**菜单中的“新建”来访问。  基于对话框的应用程序不允许用户访问**“文件”**菜单中的**“新建”**选项，但也视为是基于窗体的应用程序。  
  
 单文档界面 \(SDI\) 基于窗体的应用程序一次只允许具体某个窗体的一个实例运行。  通过从**“文件”**菜单的**“新建”**选项中选择一个新窗体，可以同时从基于 SDI 窗体的应用程序运行其他窗体。  
  
 如果创建多文档界面 \(MDI\) 基于窗体的应用程序，该应用程序将能够支持同一窗体的多个实例。  
  
 如果创建具有多顶级文档支持的应用程序，则桌面是文档的隐式父级，而且文档的框架不局限为该应用程序的工作区。  可以打开文档的多个实例，每个实例有自己的框架、菜单和任务栏图标。  可以逐个关闭文档的后续实例，但是如果从初始实例的**文件**菜单中选择`Exit`选项，则应用程序将关闭所有实例。  
  
 SDI、MDI 和多顶级文档应用程序都基于窗体并且使用文档\/视图结构。  
  
 根据定义，任何基于对话框的应用程序都基于窗体。  基于对话框的应用程序不使用文档\/视图结构，因此您必须为自己的附加窗体管理创建和访问方法。  
  
 基于窗体的应用程序的基类是 [CFormView](../../mfc/reference/cformview-class.md)。  如果应用程序具有数据库支持，则也可以选择任何从 `CFormView` 导出的类。  窗体是任何从 `CFormView` 导出或从继承自 `CFormView` 的任何类导出的窗口。  
  
 即使使用基类（如 [CView](../../mfc/reference/cview-class.md)），也可以在以后通过[添加 MFC 类](../../mfc/reference/adding-an-mfc-class.md)（从 `CFormView` 导出）并在 [MFC 类向导](../../mfc/reference/document-template-strings-mfc-add-class-wizard.md)中选中“生成 DocTemplate 资源”复选项，使应用程序基于窗体。  
  
 完成了向导后，项目打开，如果选择了 `CFormView`（或从 `CFormView` 继承的类）作为基类或者如果创建了基于对话框的应用程序，Visual C\+\+ 将打开对话框编辑器。  这时，准备设计第一个窗体。  
  
### 开始创建基于窗体的 MFC 可执行文件  
  
1.  按照[创建 MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)中的指导操作。  
  
2.  在 MFC 应用程序向导的[应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)页中，选择“文档\/视图结构支持”复选框。  
  
3.  选择“单文档”、“多文档”或“多顶级文档”。  
  
    > [!NOTE]
    >  如果选择了 SDI、MDI 或多顶级文档界面应用程序，则默认情况下，`CView` 在向导的 [生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md) 页中被设置成应用程序视图的基类。  若要创建基于窗体的应用程序，必须选择 `CFormView` 作为应用程序视图的基类。  注意向导对基于窗体的应用程序不提供打印支持。  
  
4.  在其他向导页中设置所需的任何其他项目选项。  
  
5.  单击“完成”生成主干应用程序。  
  
 有关详细信息，请参阅：  
  
-   [派生的视图类](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [文档\/视图结构的替换选项](../../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [应用程序设计选择](../../mfc/application-design-choices.md)  
  
## 请参阅  
 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)   
 [窗体视图](../../mfc/form-views-mfc.md)   
 [创建文件资源管理器样式的 MFC 应用程序](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)   
 [创建 Web 浏览器样式的 MFC 应用程序](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)