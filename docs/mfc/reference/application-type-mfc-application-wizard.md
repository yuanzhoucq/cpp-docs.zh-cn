---
title: "应用程序类型、 MFC 应用程序向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.exe.apptype
dev_langs: C++
helpviewer_keywords: static libraries, MFC
ms.assetid: c3f62b0e-3f13-42c5-9859-d3890d0c3e1d
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 45253eed40e9a79dbcb372f63cc44aaeb99edbe0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="application-type-mfc-application-wizard"></a>MFC 应用程序向导的应用程序类型
使用此页的[MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)设计并将基本功能添加到新的 MFC 应用程序。  
  
 **应用程序类型**  
 指定你想要在你的应用程序中创建的文档支持的类型。 你选择的应用程序的类型确定可用于你的应用程序的用户界面选项。 请参阅[用户界面功能，MFC 应用程序向导](../../mfc/reference/user-interface-features-mfc-application-wizard.md)有关详细信息。  
  
 有关类型的文档的详细信息，请参阅：  
  
-   [SDI 和 MDI](../../mfc/sdi-and-mdi.md)  
  
-   [框架窗口](../../mfc/frame-windows.md)  
  
-   [框架窗口类](../../mfc/frame-window-classes.md)  
  
-   [文档、视图和框架](../../mfc/documents-views-and-the-framework.md)  
  
-   [对话框](../../mfc/dialog-boxes.md)  
  
|选项|描述|  
|------------|-----------------|  
|**单个文档**|创建你的应用程序，视图类基于一个单文档界面 (SDI) 结构[CView 类](../../mfc/reference/cview-class.md)。 你可以更改中的视图的基类[生成的类，MFC 应用程序向导](../../mfc/reference/generated-classes-mfc-application-wizard.md)向导页。 若要创建基于窗体的应用程序，例如，使用[CFormView 类](../../mfc/reference/cformview-class.md)视图类。<br /><br /> 在此类型的应用程序，该文档的框架窗口可以容纳只有一个文档。|  
|**多个文档**|创建你的应用程序，其中基于视图类的多文档界面 (MDI) 结构`CView`。 你可以更改中的视图的基类**生成的类**向导页。 若要创建基于窗体的应用程序，例如，使用`CFormView`视图类。<br /><br /> 在此类型的应用程序，该文档的框架窗口可以容纳多个子 windows。|  
|**选项卡式的文档**|将每个文档置于单独的选项卡。|  
|**基于对话框**|创建对话框类取决于你的应用程序的基于对话框的体系结构`CDialog`。 (若要创建一个 HTML 对话框，请选中框**使用 HTML 对话框**。)|  
|**使用 HTML 对话框**|对话框框仅限于应用程序。 派生对话框类从[CDHtmlDialog 类](../../mfc/reference/cdhtmldialog-class.md)而不是[CDialog 类](../../mfc/reference/cdialog-class.md)。 如果勾选此框中，`CDHtmlDialog`被列入**基类**框中[生成的类，MFC 应用程序向导](../../mfc/reference/generated-classes-mfc-application-wizard.md)向导页。<br /><br /> A `CDHtmlDialog`-派生的对话框中显示的基于 HTML 的对话框时，交换数据与 HTML 控件和处理 HTML 事件。|  
|**多个顶级文档**|创建你的应用程序，其中基于视图类的多个顶级结构`CView`。<br /><br /> 在这种类型的应用程序，当用户单击**新建**(或**新帧**) 上**文件**菜单上，应用程序创建一个其父窗口隐式桌面的窗口。 新的文档框架将显示在任务栏，并且不局限于应用程序窗口的工作区。|  
  
 **文档/视图体系结构支持**  
 指定是否要包含在你的应用程序中使用的文档/视图体系结构[CDocument 类](../../mfc/reference/cdocument-class.md)和[CView 类](../../mfc/reference/cview-class.md)（默认值）。 如果要移植非 MFC 应用程序，或者如果你想要减少编译可执行文件的大小，请清除此复选框。 默认情况下，应用程序，而文档/视图体系结构不派生自[CWinApp 类](../../mfc/reference/cwinapp-class.md)，并且它不包括用于从磁盘文件打开的文档的 MFC 支持。  
  
 **资源语言**  
 设置你的资源的语言。 为已安装 Visual studio，该列表显示你系统上可用的语言。 如果你想要选择你的系统语言以外的语言，必须已安装该语言的适当的模板文件夹。 有关安装不同于默认安装中可用的语言资源的详细信息**资源语言**列表中，请参阅[其他语言的向导支持](../../ide/wizard-support-for-other-languages.md)。  
  
 你选择的语言反映在**本地化字符串**选项[文档模板字符串，MFC 应用程序向导](../../mfc/reference/document-template-strings-mfc-application-wizard.md)向导页。  
  
 **使用 Unicode 库**  
 指定是否使用 MFC 库的 Unicode 或非 Unicode 版本。  
  
 **项目样式**  
 指示你的应用程序是否具有标准 MFC、 文件资源管理器、 Visual Studio 中，或 Office 体系结构和显示。 有关详细信息，请参阅[创建文件资源管理器样式的 MFC 应用程序](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)。  
  
|选项|描述|  
|------------|-----------------|  
|**MFC 标准**|提供标准的 MFC 应用程序体系结构。|  
|**文件资源管理器**|实现使用拆分器窗口的左窗格中的工作所在的文件资源管理器样式的应用程序[CTreeView 类](../../mfc/reference/ctreeview-class.md)和右窗格中是[CListView 类](../../mfc/reference/clistview-class.md)。|  
|**Visual Studio**|实现包含四个可停靠窗格的 Visual Studio 类似应用程序 (**文件视图**，**类视图**，**属性**，和**输出**) 派生自[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)和派生自的主框架窗口[CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)（默认值）。|  
|**Office**|实现类似于 Office 的应用程序包含派生自的功能区[CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md)，派生自一个 Outlook 栏[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)，派生自的标题栏[CMFCCaptionBar 类](../../mfc/reference/cmfccaptionbar-class.md)，和派生自的主框架[CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)。|  
  
 **视觉样式和颜色**  
 确定应用程序的视觉样式。 可用选项如下：  
  
-   **Windows 本机/默认**  
  
-   **Office 2003**  
  
-   **Visual Studio 2005**  
  
-   **Office 2007 （蓝色主题）**  
  
-   **Office 2007 （黑色主题）**  
  
-   **Office 2007 （银级主题）**  
  
-   **Office 2007 （浅绿色主题）**  
  
 **启用视觉样式切换**  
 指定用户是否可以更改在运行时，应用程序的视觉样式通常通过从菜单或工作区中选择适当的视觉样式。  
  
 **MFC 的使用**  
 指定如何将链接到 MFC 库。 默认情况下，MFC 将作为共享 DLL 链接。  
  
|选项|描述|  
|------------|-----------------|  
|**在共享 DLL 中使用 MFC**|链接 MFC 库作为共享 DLL 的应用程序。 应用程序在运行时调用的 MFC 库。 此选项可减少应用程序包含多个可执行文件，使用 MFC 库的磁盘和内存要求。 Win32 和 MFC 应用程序可以在 DLL （默认值） 中调用函数|  
|**使用静态库中的 MFC**|链接到静态 MFC 库应用程序，在生成时。|  
  
## <a name="see-also"></a>请参阅  
 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)   
 [为 Visual C++ 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)

