---
title: "向导和资源编辑器 | Microsoft Docs"
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
  - "应用程序向导 [C++], 和 MFC"
  - "类视图工具, 管理 Windows 消息"
  - "编辑器, 资源"
  - "MFC [C++], 资源编辑器"
  - "MFC [C++], 向导"
  - "MFC 应用程序向导"
  - "资源编辑器, MFC"
  - "向导 [C++], MFC 编程"
  - "向导 [MFC]"
ms.assetid: f5dd4d13-9dc1-4a49-b6bf-5b3cb45fa8ba
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 向导和资源编辑器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 在编程，以及许多集成资源编辑器。的 MFC 包含一些向导使用。  对于编写 ActiveX 控件，[ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md) 一个用途与非常相似 MFC 应用程序向导。  当您可以将 MFC 应用程序，这无需大多数这些工具时，工具极大地简化和加速工作。  
  
##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a> 使用 MFC 应用程序向导创建 MFC 应用程序  
 使用 [MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md) 为 Visual C\+\+ 的 MFC 项目，可以由 OLE 和数据库支持。  在项目文件中包含应用程序，显示文档，以及框架窗口类；标准资源，包括菜单和工具栏；其他必需文件的窗口；和选项 .rtf 文件包含可以修改和扩充创建程序的帮助文件的标准 Windows 帮助主题。  
  
##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a> 使用类视图"中管理类和 Windows 消息  
 类视图帮助您创建 Windows 消息和命令处理程序函数，创建并管理的类，创建该类成员变量，创建自动化方法，并创建属性，数据库类。  
  
> [!NOTE]
>  类也重写视图用于 MFC 中的虚函数以及类。  选择类并重写虚函数。  过程的其余部分类似于处理消息，如下面段落所述。  
  
 在 Windows 下运行的应用程序 [驱动的消息](../mfc/message-handling-and-mapping.md)是。  在运行程序导致窗口发生发送到程序窗口的用户操作和其他事件。  例如，在中，如果用户单击该窗口设置鼠标，窗口将 `WM_LBUTTONDOWN` 信息，当按鼠标左键和 `WM_LBUTTONUP` 消息时，按钮时。  当用户选择从菜单栏时，该命令窗口还发送 **WM\_COMMAND** 信息。  
  
 在 MFC 框架，各个对象，如文档，查看，框架窗口，文档模板和应用程序对象，可以“处理”。  此类对象提供“函数处理程序”作为其成员函数之一，即，而框架传入消息映射到该处理程序。  
  
 映射的消息为哪些对象然后实现映射编程任务的一个主要部分选择。  为此，可使用类视图和"属性"窗口。  
  
 属性窗口将创建空的消息处理程序成员函数，因此，使用源代码编辑器实现处理程序的主体。  还可以创建或编辑类 \(从 MFC 类拥有，派生的类\) 不包含及其使用类视图的成员。  有关使用类视图的更多信息以及有关向项目添加代码的向导，请参见 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)。  
  
##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a> 使用资源编辑器创建和编辑资源  
 使用 [资源编辑器](../mfc/resource-editors.md) Visual C\+\+ 创建和编辑菜单、对话框、自定义控件、快捷、位图、图标、光标、字符串和版本资源。  自 Visual C\+\+ 4.0 版起，则工具栏编辑器使创建工具栏更容易。  
  
 若要帮助，则 Microsoft 基础类 \(MFC\) 库提供调用 COMMON.RES 的文件，包含“剪贴画”资源可以从 COMMON.RES 复制并粘贴到您自己的资源文件。  COMMON.RES 包含工具栏按钮、公用光标图标，等等。  在应用程序中使用，修改并重新指派这些资源。  有关 COMMON.RES 的更多信息，请参见 [CLIPART 示例](../top/visual-cpp-samples.md)。  
  
 MFC 应用程序向导、Visual C\+\+ 向导、资源编辑器和 MFC 框架完成您进行大量工作并使代码易于管理。  特定于的代码。大多数文档和视图类。  
  
## 请参阅  
 [使用类编写 Windows 应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)