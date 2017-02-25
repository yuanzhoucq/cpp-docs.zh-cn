---
title: "MFC 应用程序向导的应用程序类型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.exe.apptype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "静态库，MFC"
ms.assetid: c3f62b0e-3f13-42c5-9859-d3890d0c3e1d
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# MFC 应用程序向导的应用程序类型
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)的此页设计新的 MFC 应用程序并为其添加基本功能。  
  
 **应用程序类型**  
 指定希望在应用程序中创建的文档支持类型。  您选择的应用程序类型决定了应用程序中可用的用户界面选项。  有关更多信息，请参见[MFC 应用程序向导的用户界面功能](../../mfc/reference/user-interface-features-mfc-application-wizard.md)。  
  
 有关文档类型的更多信息，请参见：  
  
-   [SDI 和 MDI](../../mfc/sdi-and-mdi.md)  
  
-   [框架窗口](../../mfc/frame-windows.md)  
  
-   [框架窗口类](../../mfc/frame-window-classes.md)  
  
-   [文档、视图和框架](../../mfc/documents-views-and-the-framework.md)  
  
-   [对话框](../../mfc/dialog-boxes.md)  
  
|选项|说明|  
|--------|--------|  
|**单文档**|为应用程序创建一个单文档界面 \(SDI\) 结构，其中的视图类基于 [CView Class](../../mfc/reference/cview-class.md)。  可以在向导的[MFC 应用程序向导的生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)页中更改视图的基类。  例如，若要创建基于窗体的应用程序，请使用 [CFormView Class](../../mfc/reference/cformview-class.md)作为视图类。<br /><br /> 在此类应用程序中，文档的框架窗口只能容纳一个文档。|  
|**多文档**|为应用程序创建一个多文档界面 \(MDI\) 结构，其中的视图类基于 `CView`。  可以在向导的**生成的类**页中更改视图的基类。  例如，若要创建基于窗体的应用程序，请使用 `CFormView` 作为视图类。<br /><br /> 在此类应用程序中，文档的框架窗口可以容纳多个子文档。|  
|**选项卡式文档**|将每个文档放置到单独的选项卡上。|  
|**基于对话框**|为应用程序创建一个基于对话框的结构，其中的对话框类基于 `CDialog`。（若要创建 HTML 对话框，请选中**“使用 HTML 对话框”**框。）|  
|**使用 HTML 对话框**|只适用于对话框应用程序。  从 [CDHtmlDialog Class](../../mfc/reference/cdhtmldialog-class.md)（而不是 [CDialog Class](../../mfc/reference/cdialog-class.md)）派生对话框类。  如果选中此框，则 `CDHtmlDialog` 会在向导的[MFC 应用程序向导的生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)页中的**“基类”**框中列出。<br /><br /> `CDHtmlDialog` 派生的对话框显示基于 HTML 的对话框、与 HTML 控件交换数据并处理 HTML 事件。|  
|**多顶级文档**|为应用程序创建一个多顶级结构，其中的类视图基于 `CView`。<br /><br /> 在此类应用程序中，当用户单击**“文件”**菜单上的**“新建”**（或**“新建框架”**）时，应用程序会创建一个其父窗口隐式为桌面的窗口。  新的文档框架会显示在任务栏中，并且不局限于应用程序窗口的工作区。|  
  
 **文档\/视图结构支持**  
 通过使用 [CDocument Class](../../mfc/reference/cdocument-class.md)和 [CView Class](../../mfc/reference/cview-class.md)（默认值）指定应用程序中是否包含文档\/视图结构。  如果要移植非 MFC 应用程序或者希望减小编译生成的可执行文件的大小，则清除此复选框。  默认情况下，无文档\/视图结构的应用程序派生自 [CWinApp Class](../../mfc/reference/cwinapp-class.md)，并且不包含从磁盘文件打开文档的 MFC 支持。  
  
 **资源语言**  
 设置资源的语言。  列表显示系统上由 Visual Studio 安装的可用语言。  如果要选择系统语言以外的语言，则必须已经安装了该语言的适当模板文件夹。  有关安装**“资源语言”**列表中默认可用语言资源以外的语言资源的更多信息，请参见[其他语言的向导支持](../../ide/wizard-support-for-other-languages.md)。  
  
 您选择的语言反映在向导的[MFC 应用程序向导的文档模板字符串](../../mfc/reference/document-template-strings-mfc-application-wizard.md)页中**“本地化字符串”**选项中。  
  
 **使用 Unicode 库**  
 指定是使用 Unicode 版 MFC 库还是使用非 Unicode 版 MFC 库。  
  
 **项目样式**  
 指示应用程序是否具有标准 MFC 资源管理器、文件、Visual Studio 或 Office 结构和显示。  有关详细信息，请参阅[创建文件资源管理器样式的 MFC 应用程序](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)。  
  
|选项|说明|  
|--------|--------|  
|**MFC 标准**|提供标准 MFC 应用程序结构。|  
|**文件资源管理器**|实现文件。Explorer 的应用程序使用左窗格为 [CTreeView Class](../../mfc/reference/ctreeview-class.md) 的拆分窗口，然后右窗格是 [CListView Class](../../mfc/reference/clistview-class.md)。|  
|**Visual Studio**|实现一个 Visual Studio 样式的应用程序，其中包含四个派生自 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 的可停靠窗格（**“文件视图”**、**“类视图”**、**“属性”**和**“输出”**）和一个派生自 [CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)（默认值）的主框架窗口。|  
|**Office**|实现一个 Office 样式的应用程序，其中包含一个派生自 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)的工作区、一个派生自 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)的 Outlook 栏、一个派生自 [CMFCCaptionBar 类](../../mfc/reference/cmfccaptionbar-class.md)的标题栏和一个派生自 [CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)的主框架。|  
  
 **视觉样式和颜色**  
 确定应用程序的视觉样式。  下列选项可用：  
  
-   **Windows 本机\/默认设置**  
  
-   **Office 2003**  
  
-   **Visual Studio 2005**  
  
-   **Office 2007 \(蓝色主题\)**  
  
-   **Office 2007 \(黑色主题\)**  
  
-   **Office 2007 \(银色主题\)**  
  
-   **Office 2007 \(水绿色主题\)**  
  
 **启用视觉样式切换**  
 指定在运行时，用户通常是否可以通过从菜单或工作区中选择适当的视觉样式来更改应用程序的视觉样式。  
  
 **MFC 的使用**  
 指定如何链接到 MFC 库。  默认情况下，MFC 作为共享 DLL 链接。  
  
|选项|说明|  
|--------|--------|  
|**使用共享 DLL 中的 MFC**|将 MFC 库作为共享 DLL 链接到应用程序。  应用程序在运行时调用 MFC 库。  如果应用程序由多个使用 MFC 库的可执行文件组成，则此选项可降低应用程序的磁盘和内存需求。  Win32 和 MFC 应用程序都可以调用 DLL 中的函数（默认值）。|  
|**使用静态库中的 MFC**|生成时将应用程序链接到静态 MFC 库。|  
  
## 请参阅  
 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)   
 [为 Visual C\+\+ 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)