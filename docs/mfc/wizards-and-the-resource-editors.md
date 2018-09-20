---
title: 向导和资源编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a02a6e1f2b40f777cef0f82f92d0c41ff40595b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436529"
---
# <a name="wizards-and-the-resource-editors"></a>向导和资源编辑器

Visual c + + MFC 编程，以及许多集成的资源编辑器中包括用于多个向导。 对于 ActiveX 控件编程中， [ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)非常相似的 MFC 应用程序向导的用途。 虽然可以编写 MFC 应用程序而无需大多数这些工具，这些工具将极大地简化并加速你的工作。

##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a> 使用 MFC 应用程序向导创建 MFC 应用程序

使用[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)创建 Visual c + +，这可以包括 OLE 和数据库支持的 MFC 项目。 项目中的文件包含你的应用程序、 文档、 视图和框架窗口类;标准资源，包括菜单和可选的工具栏;其他所需的 Windows 文件;和可选的.rtf 文件包含标准 Windows 帮助主题，可以修改和创建程序的帮助文件中增加。

##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a> 使用类视图，管理类和 Windows 消息

类视图可帮助您创建的 Windows 消息和命令的处理程序函数、 创建和管理类，创建类成员变量、 创建自动化方法和属性、 创建数据库的类，和的详细信息。

> [!NOTE]
>  类视图还可帮助你重写虚函数中的 MFC 类。 选择类和重写的虚函数。 以下各段中所述，余下是过程的类似于消息处理。

在 Windows 下运行的应用程序都[消息驱动](../mfc/message-handling-and-mapping.md)。 用户操作和其他正在运行的程序中发生的事件会导致将消息发送到的窗口中查看该程序的 Windows。 例如，如果用户单击鼠标在窗口中的，Windows 会发送 WM_LBUTTONDOWN 消息时按下鼠标左键和 WM_LBUTTONUP 消息释放按钮时。 当用户从菜单栏中选择命令时，Windows 还会发送 WM_COMMAND 消息。

在 MFC 框架中，各种对象，如文档、 视图、 框架窗口、 文档模板和应用程序对象，可以"处理"消息。 此类对象提供了一个"处理程序函数"作为其成员之一的函数，和框架将传入消息映射到其处理程序。

您的编程任务，很大一部分是选择将哪些消息将映射到哪些对象，然后实现该映射。 为此，请使用类视图和属性窗口。

属性窗口将创建空的消息处理程序成员函数，并在源代码编辑器用于实现处理程序的正文。 您还可以创建或编辑 （包括你自己的类不派生自 MFC 类） 的类和类视图具有其成员。 有关如何使用类视图以及有关将代码添加到项目的向导的详细信息，请参阅[用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)。

##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a> 使用资源编辑器来创建和编辑资源

使用 Visual c + +[资源编辑器](../windows/resource-editors.md)来创建和编辑菜单、 对话框、 自定义控件、 快捷键、 位图、 图标、 游标、 字符串和版本资源。 截至 Visual c + + 4.0 版，工具栏编辑器创建工具栏大大简化。

为了帮助您更多，Microsoft 基础类库提供了一个名为常见文件。RES，其中包含你可以从常见复制的"剪贴画"资源。RES 并粘贴到您自己的资源文件。 常见。RES 包括工具栏按钮、 常见游标、 图标和的详细信息。 可以使用、 修改和重新分发应用程序中的这些资源。 有关常见的详细信息。RES，请参阅[剪贴画示例](../visual-cpp-samples.md)。

MFC 应用程序向导、 Visual c + + 向导、 资源编辑器和 MFC 框架为您做了大量工作，并使管理你的代码容易得多。 特定于应用程序大部分是代码的在文档和视图的类中。

## <a name="see-also"></a>请参阅

[使用类编写 Windows 应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)
