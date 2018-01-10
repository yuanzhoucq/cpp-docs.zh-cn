---
title: "向导和资源编辑器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- application wizards [MFC], and MFC
- MFC, resource editors
- resource editors, MFC
- MFC Application Wizard
- editors [MFC], resource
- wizards [MFC]
- wizards [MFC], MFC programming
- MFC, wizards
- Class View tool, managing Windows messages
ms.assetid: f5dd4d13-9dc1-4a49-b6bf-5b3cb45fa8ba
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1fd81a8548dbb746da4afa5b89bc49ee801cbaeb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="wizards-and-the-resource-editors"></a>向导和资源编辑器
Visual c + + 包括多个向导用于在 MFC 编程中，以及许多集成的资源编辑器。 对于 ActiveX 控件编程中， [ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)非常类似于 MFC 应用程序向导的起作用。 虽然可以编写没有其中大多数工具的 MFC 应用程序，则工具将极大地简化并加速你的工作。  
  
##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a>使用 MFC 应用程序向导创建 MFC 应用程序  
 使用[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)在 Visual c + +，其中可能包括 OLE 和数据库支持中创建的 MFC 项目。 项目中的文件包含你的应用程序、 文档、 视图和框架窗口类;标准资源，包括菜单和可选的工具栏中;其他所需的 Windows 文件;和可选的.rtf 文件包含标准 Windows 帮助主题，您可以修改和增加来创建程序的帮助文件。  
  
##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a>使用类视图来管理类和 Windows 消息  
 类视图可帮助你创建的 Windows 消息和命令的处理程序函数、 创建和管理类，创建变量的类成员、 创建自动化方法和属性、 创建数据库的类，和的详细信息。  
  
> [!NOTE]
>  类视图还可帮助你重写虚函数中的 MFC 类。 选择类和重写虚函数。 以下各段中所述，该过程的其余部分是类似于消息处理。  
  
 在 Windows 下运行的应用程序是[驱动的消息](../mfc/message-handling-and-mapping.md)。 用户操作和其他运行的程序中发生的事件导致 Windows 将消息发送到程序中的窗口。 例如，如果用户单击鼠标在窗口中的，则 Windows 将发送`WM_LBUTTONDOWN`消息时按下鼠标左键和`WM_LBUTTONUP`消息时释放按钮。 Windows 还会发送**WM_COMMAND**邮件时对用户从菜单栏中选择命令。  
  
 在 MFC 框架中中, 各种对象，如文档、 视图、 框架窗口、 文档模板和应用程序对象中，可以"处理"消息。 此类对象"处理程序函数"作为其成员之一和提供函数，框架将传入的消息映射到其处理程序。  
  
 你的编程任务的大部分内容是选择要映射到的对象的哪些消息，然后实现该映射。 为此，请使用类视图和属性窗口。  
  
 属性窗口将创建空的消息处理程序成员函数，并使用源代码编辑器来实现处理程序的主体。 你还可以创建或编辑 （包括你自己的类不派生自 MFC 类） 的类和类视图具有其成员。 有关如何使用类视图以及向项目添加代码的向导的详细信息，请参阅[用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)。  
  
##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a>使用资源编辑器来创建和编辑资源  
 使用 Visual c + +[资源编辑器](../windows/resource-editors.md)创建和编辑菜单、 对话框、 自定义控件、 快捷键、 位图、 图标、 光标、 字符串和版本资源。 从 Visual c + + 4.0 版，开始工具栏编辑器可以创建工具栏容易得多。  
  
 为了帮助你更多，Microsoft 基础类库提供了名为常见的文件。RES，其中包含你可以从公共复制的"剪贴画"资源。RES 然后将粘贴到你自己的资源文件。 常见。RES 包括工具栏按钮、 常见游标、 图标和的详细信息。 你可以使用、 修改和重新分发应用程序中的这些资源。 有关常见的详细信息。RES，请参阅[剪贴画示例](../visual-cpp-samples.md)。  
  
 MFC 应用程序向导、 Visual c + + 向导、 资源编辑器和 MFC 框架为你执行大量工作，并使管理你的代码容易得多。 你的应用程序特定代码大部分是您的文档和视图类中。  
  
## <a name="see-also"></a>请参阅  
 [使用类编写 Windows 应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)
