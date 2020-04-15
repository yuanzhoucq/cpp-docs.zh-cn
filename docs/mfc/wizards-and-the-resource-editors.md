---
title: 向导和资源编辑器
ms.date: 11/04/2016
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
ms.openlocfilehash: 04d9f2cf615636b151af93a3c3880f7357496048
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365267"
---
# <a name="wizards-and-the-resource-editors"></a>向导和资源编辑器

可视化C++包括用于 MFC 编程的几种向导，以及许多集成资源编辑器。 对于 ActiveX 控件编程[，ActiveX 控制向导](../mfc/reference/mfc-activex-control-wizard.md)的作用与 MFC 应用程序向导的用途非常类似。 虽然无需大多数这些工具即可编写 MFC 应用程序，但这些工具大大简化了您的工作并加快了速度。

## <a name="use-the-mfc-application-wizard-to-create-an-mfc-application"></a><a name="_core_use_appwizard_to_create_an_mfc_application"></a>使用 MFC 应用程序向导创建 MFC 应用程序

使用[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)在 Visual C++中创建 MFC 项目，该项目可以包括 OLE 和数据库支持。 项目中的文件包含应用程序、文档、视图和框架窗口类;标准资源，包括菜单和可选工具栏;其他必需的 Windows 文件;和可选的 .rtf 文件包含标准 Windows 帮助主题，您可以修改和增强这些主题以创建程序的帮助文件。

## <a name="use-class-view-to-manage-classes-and-windows-messages"></a><a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a>使用类视图管理类和 Windows 消息

Class View 可帮助您为 Windows 消息和命令创建处理程序函数、创建和管理类、创建类成员变量、创建自动化方法和属性、创建数据库类等。

> [!NOTE]
> 类视图还可以帮助您覆盖 MFC 类中的虚拟函数。 选择要重写的类和虚拟函数。 该过程的其余部分类似于消息处理，如以下段落所述。

在 Windows 下运行的应用程序是[消息驱动的](../mfc/message-handling-and-mapping.md)。 运行程序中发生的用户操作和其他事件会导致 Windows 向程序中的窗口发送消息。 例如，如果用户单击窗口中的鼠标，则当按下鼠标左键时，Windows 会发送WM_LBUTTONDOWN消息，并在释放该按钮时发送WM_LBUTTONUP消息。 当用户从菜单栏中选择命令时，Windows 还会发送WM_COMMAND消息。

在 MFC 框架中，各种对象（如文档、视图、框架窗口、文档模板和应用程序对象）可以"处理"消息。 此类对象提供"处理程序函数"作为其成员函数之一，并且框架将传入消息映射到其处理程序。

编程任务的很大一部分是选择要映射到哪些对象的消息，然后实现该映射。 为此，请使用类视图和[类向导](reference/mfc-class-wizard.md)。

[类向导](reference/mfc-class-wizard.md)将创建空消息处理程序成员函数，并且您可以使用源代码编辑器来实现处理程序的正文。 您还可以使用类视图创建或编辑类（包括您自己的类，而不是从 MFC 类派生的类） 及其成员。 有关使用类视图和向项目添加代码的向导的详细信息，请参阅[使用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)。

## <a name="use-the-resource-editors-to-create-and-edit-resources"></a><a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a>使用资源编辑器创建和编辑资源

使用 VisualC++[资源编辑器](../windows/resource-editors.md)创建和编辑菜单、对话框、自定义控件、快捷键、位图、图标、游标、字符串和版本资源。 从 Visual C++ 版本 4.0 起，工具栏编辑器使创建工具栏变得更加容易。

为了帮助您更多，Microsoft 基础类库提供了一个名为 COMMON 的文件。RES，其中包含可以从 COMMON 复制的"剪贴画"资源。RES 并粘贴到您自己的资源文件中。 常见。RES 包括工具栏按钮、常用光标、图标等。 您可以在应用程序中使用、修改和重新分发这些资源。 有关 COMMON 的详细信息。RES，请参阅[剪贴图示例](../overview/visual-cpp-samples.md)。

MFC 应用程序向导、可视C++向导、资源编辑器和 MFC 框架为您做了大量工作，使管理代码变得更加容易。 应用程序特定代码的大部分位于文档和视图类中。

## <a name="see-also"></a>另请参阅

[使用类为 Windows 编写应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)
