---
title: "MFC 应用程序向导 | Microsoft Docs"
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
  - "vc.appwiz.mfc.exe.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "可执行文件, 创建"
  - "MFC 应用程序向导"
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 应用程序向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC 应用程序向导生成这样一个应用程序：编译后可实现 Windows 可执行 \(.exe\) 应用程序的基本功能。  MFC 起始应用程序包括 C\+\+ 源文件 \(.cpp\)、资源文件 \(.rc\)、头文件 \(.h\) 和一个项目文件 \(.vcxproj\)。  这些起始文件中生成的代码基于 MFC。  
  
> [!NOTE]
>  根据您选择的选项，向导会在项目中创建附加文件。  例如，如果选中[高级功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)页中的**“区分上下文的帮助”**，向导会创建编译项目的帮助文件所需的文件。  有关向导创建的文件的更多信息，请参见[为 Visual C\+\+ 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)以及项目中的 Readme.txt 文件。  
  
## 概述  
 此向导页描述正在创建的 MFC 应用程序的当前应用程序设置。  默认情况下，该向导按如下方式创建项目：  
  
-   [MFC 应用程序向导的应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)  
  
    -   创建项目，并使其支持选项卡式多文档界面 \(MDI\)。  有关详细信息，请参阅[SDI 和 MDI](../../mfc/sdi-and-mdi.md)。  
  
    -   项目使用 [文档\/视图体系结构](../../mfc/document-view-architecture.md)。  
  
    -   项目使用 Unicode 库。  
  
    -   使用 Visual Studio 项目样式创建项目，并对项目启用视觉样式切换。  
  
    -   项目使用共享 DLL 中的 MFC。  有关详细信息，请参阅[Visual C\+\+ 中的 DLL](../../build/dlls-in-visual-cpp.md)。  
  
-   [MFC 应用程序向导的复合文档支持](../../mfc/reference/compound-document-support-mfc-application-wizard.md)  
  
    -   项目不提供复合文档支持。  
  
-   [MFC 应用程序向导的文档模板字符串](../../mfc/reference/document-template-strings-mfc-application-wizard.md)  
  
    -   项目使用默认文档模板字符串的项目名称。  
  
-   [MFC 应用程序向导的数据库支持](../../mfc/reference/database-support-mfc-application-wizard.md)  
  
    -   项目不提供数据库支持。  
  
-   [MFC 应用程序向导的用户界面功能](../../mfc/reference/user-interface-features-mfc-application-wizard.md)  
  
    -   项目实现标准 Windows 用户界面功能，如系统菜单、状态栏、最大化和最小化框、**“关于”**框、标准菜单栏和停靠工具栏以及子框架。  
  
-   [MFC 应用程序向导的高级功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)  
  
    -   项目支持打印和打印预览。  
  
    -   项目支持 ActiveX 控件。  有关详细信息，请参阅[用于创建 ActiveX 控件的操作顺序](../../mfc/sequence-of-operations-for-creating-activex-controls.md)。  
  
    -   项目不支持[自动化](../../mfc/automation.md)、[MAPI](../../mfc/mapi-support-in-mfc.md)、[Windows 套接字](../../mfc/windows-sockets-in-mfc.md)或 Active Accessibility。  
  
    -   项目支持**“资源管理器”**停靠窗格、**“输出”**停靠窗格和**“属性”**停靠窗格。  
  
-   [MFC 应用程序向导的生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)  
  
    -   项目的视图类派生自 [CView Class](../../mfc/reference/cview-class.md)。  
  
    -   项目的应用程序类派生自 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)。  
  
    -   项目的文档类派生自 [CDocument Class](../../mfc/reference/cdocument-class.md)。  
  
    -   项目的主框架类派生自 [CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)。  
  
    -   项目的子框架类派生自 [CMDIChildWndEx 类](../../mfc/reference/cmdichildwndex-class.md)。  
  
 若要更改这些默认设置，请在向导的左侧栏中单击相应的选项卡标题，然后在显示的页中进行更改。  
  
 创建 MFC 应用程序项目后，可以使用 Visual C\+\+  [代码向导](../../ide/adding-functionality-with-code-wizards-cpp.md)向项目中添加对象或者控件。  
  
## 请参阅  
 [创建 MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)   
 [MFC 桌面应用程序](../../mfc/mfc-desktop-applications.md)   
 [使用类编写 Windows 应用程序](../../mfc/using-the-classes-to-write-applications-for-windows.md)