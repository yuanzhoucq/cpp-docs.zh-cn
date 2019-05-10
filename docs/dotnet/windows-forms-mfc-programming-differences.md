---
title: Windows 窗体-MFC 编程差异
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
ms.openlocfilehash: 998485a3384512f57cf35fc264e2321fa0996728
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384447"
---
# <a name="windows-formsmfc-programming-differences"></a>Windows 窗体/MFC 编程差异

中的主题[在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)描述 Windows 窗体的 MFC 支持。 如果您不熟悉.NET Framework 或 MFC 编程，本主题提供有关编程方面的这两个不同的背景信息。

Windows 窗体是用于在.NET Framework 上创建 Microsoft Windows 应用程序。 此框架提供现代的、 面向对象的、 可扩展套使您能够开发丰富的基于 Windows 的应用程序的类。 使用 Windows 窗体，您就能够创建丰富的客户端应用程序，可以访问各种数据源和提供数据显示和使用 Windows 窗体控件的数据编辑功能。

但是，如果您习惯于 MFC，则可能创建某些类型的应用程序尚不显式支持在 Windows 窗体中使用。 Windows 窗体应用程序是等效于 MFC 对话框应用程序。 但是，它们不提供直接支持 OLE 文档服务器/容器、 ActiveX 文档、 文档/视图支持等其他 MFC 应用程序类型，对于单文档界面 (SDI)，多文档界面 (MDI) 的基础结构和多个顶级接口 (MTI)。 可以编写您自己创建这些应用程序的逻辑。

Windows 窗体应用程序的详细信息，请参阅[Windows 窗体介绍](/dotnet/framework/winforms/windows-forms-overview)。

显示与 MFC 一起使用的 Windows 窗体的示例应用程序，请参阅[MFC 和 Windows 窗体集成](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。

以下的 MFC 视图或文档和路由功能的命令具有在 Windows 窗体中没有等效项：

- Shell 集成

   MFC 处理动态数据交换 (DDE) 命令和在右键单击文档和选择这种谓词作为打开、 编辑或打印时使用 shell 的命令行参数。 Windows 窗体没有 shell 集成并不响应外壳动词。

- 文档模板

   在 MFC 中，文档模板将视图，它包含在框架窗口 （在 MDI、 SDI 或 MTI 模式下），与打开的文档相关联。 Windows 窗体具有到文档模板没有等效项。

- 文档

   MFC 注册文档文件类型，并从命令行程序中打开文档时处理的文档类型。 Windows 窗体的任何文档支持。

- 文档状态

   MFC 维护文档的已更新状态。 因此，当关闭应用程序、 关闭上一个视图包含的应用程序，或从 Windows 中退出，MFC 会提示你保存文档。 Windows 窗体具有没有等效的支持。

- 命令

   MFC 提供的命令的概念。 菜单栏、 工具栏和上下文菜单所有可以调用相同的命令，例如，剪切和复制。 在 Windows 窗体中的命令是从特定的 UI 元素 （如菜单项）; 紧密绑定的事件因此，您必须显式挂接命令的所有事件。 此外可以处理多个事件与 Windows 窗体中的单个处理程序。 有关详细信息，请参阅[将多个事件连接到单个事件处理程序在 Windows 窗体中](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms)。

- 命令传送

   MFC 命令路由，该活动视图或处理命令的文档。 因为在同一命令通常具有不同的视图的不同的含义 （例如，副本的行为以不同的方式比在图形编辑器中的文本编辑视图中），需要由活动视图处理命令。 Windows 窗体菜单和工具栏已活动视图没有固有了解，因为不能具有不同的处理程序的每个视图类型的应用**MenuItem.Click**而无需编写额外的内部代码的事件。

- 命令更新机制

   MFC 提供的命令更新机制。 因此，活动视图或文档是负责 UI 元素 （例如，启用或禁用菜单项或工具按钮，以及选中状态） 的状态。 Windows 窗体具有命令更新机制没有等效项。

## <a name="see-also"></a>请参阅

[在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)
