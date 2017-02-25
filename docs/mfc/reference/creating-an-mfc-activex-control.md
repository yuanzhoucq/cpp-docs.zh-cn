---
title: "创建 MFC ActiveX 控件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.activex.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], 创建"
  - "MFC ActiveX 控件 [C++], 创建"
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 创建 MFC ActiveX 控件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ActiveX 控件程序是旨在为父应用程序提供特定功能类型的模块化程序。  例如，可以创建诸如在对话框中使用的按钮或在网页中使用的工具栏这样的控件。  
  
 创建 MFC ActiveX 控件的最容易方法是使用 [MFC ActiveX 控件向导](../../mfc/reference/mfc-activex-control-wizard.md)。  
  
### 使用 MFC ActiveX 控件向导创建 MFC ActiveX 控件  
  
1.  按照帮助主题[用 Visual C\+\+ 应用程序向导创建项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)中的说明进行操作。  
  
2.  在**“新建项目”**对话框中，选择“模板”窗格中的**“MFC ActiveX 控件”**图标以打开 MFC ActiveX 控件向导。  
  
3.  使用 MFC ActiveX 控件向导定义[应用程序设置](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)、[控件名称](../../mfc/reference/control-names-mfc-activex-control-wizard.md)和[控件设置](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)。  
  
    > [!NOTE]
    >  跳过此步骤可保留向导的默认设置。  
  
4.  单击“完成”关闭向导并在开发环境中打开新项目。  
  
 创建项目后，可以在**解决方案资源管理器**中查看所创建的文件。  有关向导为项目创建的文件的更多信息，请参见项目生成的文件 ReadMe.txt。  有关文件类型的更多信息，请参见[为 Visual C\+\+ 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
 创建了项目后，可以使用代码向导添加[函数](../../ide/add-member-function-wizard.md)、[变量](../../ide/add-member-variable-wizard.md)、[事件](../../ide/add-event-wizard.md)、[属性](../../ide/names-add-property-wizard.md)和[方法](../../ide/add-method-wizard.md)。  有关自定义 ActiveX 控件的更多信息，请参见 [MFC ActiveX 控件](../../mfc/mfc-activex-controls.md)。  
  
## 请参阅  
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [属性页](../../ide/property-pages-visual-cpp.md)   
 [Deploying Applications](http://msdn.microsoft.com/zh-cn/4ff8881d-0daf-47e7-bfe7-774c625031b4)