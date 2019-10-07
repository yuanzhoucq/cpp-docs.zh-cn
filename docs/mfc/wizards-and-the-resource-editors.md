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
ms.openlocfilehash: fb1a523ca82cd8e1a4256da657efe9702517beda
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907352"
---
# <a name="wizards-and-the-resource-editors"></a>向导和资源编辑器

Visual C++包含多个用于 MFC 编程的向导，以及许多集成的资源编辑器。 对于 ActiveX 控件编程， [Activex 控件向导](../mfc/reference/mfc-activex-control-wizard.md)的作用与 MFC 应用程序向导的作用非常类似。 虽然你可以在不使用这些工具的情况下编写 MFC 应用程序，但这些工具可以极大地简化和加速你的工作。

##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a>使用 MFC 应用程序向导创建 MFC 应用程序

使用[Mfc 应用程序向导](../mfc/reference/mfc-application-wizard.md)可在 Visual C++中创建 MFC 项目，该项目可包含 OLE 和数据库支持。 项目中的文件包含应用程序、文档、视图和框架窗口类;标准资源，包括菜单和可选工具栏;其他必需的 Windows 文件;和可选的 .rtf 文件，其中包含可修订和增强以创建程序的帮助文件的标准 Windows 帮助主题。

##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a>使用类视图管理类和 Windows 消息

类视图帮助您为 Windows 消息和命令创建处理程序函数，创建和管理类，创建类成员变量，创建自动化方法和属性，创建数据库类等。

> [!NOTE]
>  类视图还有助于替代 MFC 类中的虚函数。 选择要重写的类和虚函数。 此过程的其余部分类似于消息处理，如以下各部分所述。

在 Windows 下运行的应用程序由[消息驱动](../mfc/message-handling-and-mapping.md)。 在正在运行的程序中发生的用户操作和其他事件会导致 Windows 将消息发送到程序中的窗口。 例如，如果用户在窗口中单击鼠标，则在按下鼠标左键时，Windows 将发送一条 WM_LBUTTONDOWN 消息，并在按钮释放时发送 WM_LBUTTONUP 消息。 当用户从菜单栏中选择命令时，Windows 也会发送 WM_COMMAND 消息。

在 MFC 框架中，各种对象（如文档、视图、框架窗口、文档模板和应用程序对象）都可以 "处理" 消息。 此类对象提供 "处理程序函数" 作为其成员函数之一，并且框架将传入消息映射到其处理程序。

编程任务的一大部分是选择哪些消息要映射到哪些对象，然后再实现该映射。 为此，请使用类视图和[类向导](reference/mfc-class-wizard.md)。

[类向导](reference/mfc-class-wizard.md)将创建空消息处理程序成员函数，并使用源代码编辑器来实现处理程序的主体。 你还可以创建或编辑类（包括你自己的类，而不是从 MFC 类派生的类）及其具有类视图的成员。 有关使用类视图和向项目添加代码的向导的详细信息，请参阅[使用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)。

##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a>使用资源编辑器创建和编辑资源

使用可视化C++ [资源编辑器](../windows/resource-editors.md)可以创建和编辑菜单、对话框、自定义控件、快捷键、位图、图标、光标、字符串和版本资源。 从 Visual C++版本4.0，工具栏编辑器可以更轻松地创建工具栏。

为了更好地帮助你，Microsoft 基础类库提供了一个称为 "通用" 的文件。RES，其中包含可从 COMMON 复制的 "剪贴画" 资源。RES 并粘贴到你自己的资源文件中。 常见问题解答.RES 包含工具栏按钮、常见光标、图标等。 可以在应用程序中使用、修改和重新分发这些资源。 有关常见情况的详细信息。RES，请参阅 "[剪贴画" 示例](../overview/visual-cpp-samples.md)。

MFC 应用程序向导、可视化C++向导、资源编辑器和 mfc 框架为您执行了大量工作，并使您的代码管理变得更加容易。 应用程序特定的代码在文档和视图类中。

## <a name="see-also"></a>请参阅

[使用类编写 Windows 应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)
