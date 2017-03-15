---
title: "用于生成 MFC 应用程序的操作顺序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序 [MFC], 开发"
ms.assetid: 6973c714-fe20-48c6-926b-de88356b3a3d
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 用于生成 MFC 应用程序的操作顺序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表解释可能通常遵循的一般序列，当您开发 MFC 应用程序。  
  
### 用于生成与 Framework 的应用顺序  
  
|任务|You do|框架|  
|--------|------------|--------|  
|创建一个应用程序框架|运行[MFC Application Wizard](../mfc/reference/mfc-application-wizard.md)。  指定可以在选项页需选项。  包含进行应用程序空闲 COM 组件，容器或两个选项；添加自动化；并使应用数据库支持。|MFC 应用程序向导创建应用程序的主干文件，包括源文件应用程序、文档、视图和框架窗口；一个资源文件；一个项目文件；另，所有类型定制的规范。|  
|参见框架和 MFC 应用程序向导提供，而无需添加自己的代码行。|生成主干应用程序并运行在 Visual C\+\+。|连续主干应用程序框架从派生许多标准 **文件**、**编辑**、**视图**和 **帮助** 菜单命令。  在 MDI 应用程序中，您还将获取一个完整功能窗口菜单，并且，框架管理创建、MDI 子窗口上排列和析构。|  
|构造应用程序的用户界面。|使用 [资源编辑器](../mfc/resource-editors.md) 可视化 Visual C\+\+ 编辑应用程序的用户界面：<br /><br /> -   创建菜单<br />-   定义快捷键。<br />-   创建对话框。<br />-   创建并编辑位图、图标和光标。<br />-   编辑可用于您创建的工具栏由 MFC 应用程序向导。<br />-   创建并编辑其他资源。<br /><br /> 还可以测试在对话框编辑器中的对话框。|MFC 应用程序向导"创建的默认资源文件提供所需的多个资源。  Visual C\+\+ 允许您编辑现有资源并轻松和视觉上添加新的资源。|  
|给处理程序函数的映射菜单。|使用 **事件** 按钮。[属性窗口](../Topic/Properties%20Window.md) 连接菜单和快捷键为代码中处理函数。|属性窗口、消息映射项并将函数模板为指定并管理手动许多编码任务的源文件。|  
|编写处理程序代码。|使用类视图直接跳转到在源代码编辑器中的代码。  填写处理程序函数的代码。  有关使用Class View向项目中添加代码的向导的更多信息，请参见[用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)。|打开类视图编辑器中，滚动到空函数模板并确定您的光标。|  
|映射到命令的工具栏按钮。|映射工具栏上的每个按钮设置为菜单或快捷键命令通过将按钮适当的命令 ID.|框架控制绘图，启用，禁用，检查和工具栏按钮的其他可视方面。|  
|测试处理程序函数。|重新生成程序并使用内置工具测试调试处理程序正常工作。|可以单步执行代码或跟踪查看如何处理程序调用。  如果完成处理程序代码，处理程序执行命令。  框架将自动禁用未处理的菜单项和工具栏按钮。|  
|增加[dialog boxes](../mfc/dialog-boxes.md)。|设计使用对话框编辑器中的对话框模板资源。  然后创建对话框类和对话框的代码。|框架和实现对话框管理检索用户输入的信息。|  
|初始化，验证，以及检索对话框数据。|还可以定义的对话框控件将如何初始化和验证。  使用 Visual Studio 将成员变量添加到类和对话框\) 映射它们向对话框控件。  指定验证规则应用到每个控件，用户输入数据。  如果希望，提供自己的自定义验证。|框架管理此对话框的初始化和验证。  如果用户输入无效框架的信息，显示消息框并允许用户重新输入数据。|  
|创建其他的类。|使用"类视图"创建附加文档、视图和框架窗口类超出 MFC 应用程序向导自动创建的参数以外。  可以创建其他的数据库记录集类，对话框类，依此类推。\(使用类视图，可以创建未从 MFC 类派生的类。\)|您定义它们为所有命令的连接它们处理的类视图"添加类。这些源文件和帮助。|  
|为应用程序添加直接使用的组件。|使用 `New Item dialog box` 添加各种项。|这些项是轻松集成应用程序并保存您的工作。|  
|实现类文档。|实现具有特定的记录类或类。  添加成员变量存储数据结构。  添加成员函数提供接口。数据。|框架还会使用文档数据文件进行交互。  可以打开和关闭文件，读取和写入文档的数据处理，并且其他用户界面。  您可以关注文档的数据如何进行操作。|  
|实现保存和打开，"另存为"命令。|编写文档的 `Serialize` 成员函数中的代码。|框架显示了 **打开**、**保存**和 **另存为** 命令在对话框的 **文件** 菜单。  编写它并且回读取文档使用 `Serialize` 成员函数中指定的数据格式。|  
|实现视图类。|实现一个或多个类视图与文档相对应。  实现视图的成员函数映射要将使用类视图的用户界面。  多种的 [CView](../mfc/reference/cview-class.md)派生类可用，包括 [CListView](../mfc/reference/clistview-class.md) 和 [CTreeView](../mfc/reference/ctreeview-class.md)。|框架的大多数管理文档及其视图之间的关系。  视图的成员函数访问的文档视图呈现它在屏幕或打印的页面更新文档的数据响应图像和结构编辑命令的用户。|  
|引发默认打印。|如果需要多页支持打印，请重写视图成员函数。|框架支持 **打印**、**页面设置**和 **打印预览** 命令。**文件** 菜单。  必须通知它如何将文档多个页。|  
|添加滚动。|如果需要支持滚动，请从 [CScrollView](../mfc/reference/cscrollview-class.md)视图派生的一个或多个类。|当窗口变得太小时，视图将自动添加滚动条。|  
|创建窗体视图。|如果您希望基于视图对话框模板资源，请从 [CFormView](../mfc/reference/cformview-class.md)视图派生的一个或多个类。|视图使用对话框模板资源。显示控件。  用户可以从控件切换到视图的控件。|  
|创建数据库窗体。|如果需要基于窗体的数据访问应用程序，请从 [CRecordView](../mfc/reference/crecordview-class.md) 视图派生类 \(ODBC 的编程\)。|视图可像窗体视图，但其控件连接到表示数据库表的 [CRecordset](../mfc/reference/crecordset-class.md) 对象的字段。  MFC 将数据在控件和记录集之间您的。|  
|创建简单的文本编辑器。|如果希望视图是一个简单的文本编辑器，或从 [CEditView](../mfc/reference/ceditview-class.md) [CRichEditView](../mfc/reference/cricheditview-class.md)视图派生的一个或多个类。|视图提供编辑函数、剪贴板和支持文件输入\/输出。  `CRichEditView` 提供了设置的文本。|  
|增加拆分窗口|如果希望支持拆分窗口，将 [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) 对象到 SDI 框架窗口或 MDI 子窗口和功能在窗口中 [OnCreateClient](../Topic/CFrameWnd::OnCreateClient.md) 成员函数。|框架在滚动条旁边提供拆分框控件和管理的"拆分到多个窗格。  如果拆分窗口框架创建用户，并附加到文档的其他视图对象。|  
|生成，测试，然后调试应用程序。|使用 Visual C\+\+ 的功能生成，将测试和调试应用程序。|Visual C\+\+ 允许您调整编译，LINK 和其他选项。  它还让您浏览源代码并自己层结构。|  
  
## 请参阅  
 [用于创建 OLE 应用程序的操作顺序](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [用于创建 ActiveX 控件的操作顺序](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [用于创建数据库应用程序的操作顺序](../mfc/sequence-of-operations-for-creating-database-applications.md)   
 [基于框架生成](../mfc/building-on-the-framework.md)