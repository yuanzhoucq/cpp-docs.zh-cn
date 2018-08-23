---
title: Windows 窗体 MFC 编程差异 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9ad9e47ba2bb3d9a5e5b21620a4bf4b50177d63b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172666"
---
# <a name="windows-formsmfc-programming-differences"></a>Windows 窗体/MFC 编程差异
中的主题[在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)描述 Windows 窗体的 MFC 支持。 如果你不熟悉.NET Framework 或 MFC 编程，本主题提供有关编程两者之间的差异的背景信息。  
  
 Windows 窗体是用于创建在.NET Framework 上的 Microsoft Windows 应用程序。 此框架提供现代的、 面向对象的、 可扩展的一组允许你开发丰富的基于 Windows 的应用程序的类。 Windows 窗体，你就能够创建的丰富的客户端应用程序可以访问各种数据源，并提供数据显示和使用 Windows 窗体控件的数据编辑功能。  
  
 但是，如果你习惯于 MFC，你可能创建特定类型的应用程序尚不显式支持 Windows 窗体中使用。 Windows 窗体应用程序是等效于 MFC 对话框应用程序。 但是，它们不提供直接对于单文档界面 (SDI)，多文档界面 (MDI)，支持其他 MFC 应用程序类型，如 OLE 文档服务器/容器、 ActiveX 文档、 文档/视图支持的基础结构和多个顶级接口 (MTI)。 你可以编写自己的逻辑来创建这些应用程序。  
  
 有关 Windows 窗体应用程序的详细信息，请参阅[简介 Windows 窗体](/dotnet/framework/winforms/windows-forms-overview)。  
  
 显示与 MFC 一起使用的 Windows 窗体的示例应用，请参阅[MFC 和 Windows 窗体集成](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
 以下的 MFC 视图或文档和路由功能的命令具有 Windows 窗体中没有等效项：  
  
-   命令行程序集成  
  
     MFC 处理的动态数据交换 (DDE) 命令和在用鼠标右键单击文档和选择这些谓词作为打开、 编辑或打印时使用命令行界面的命令行自变量。 Windows 窗体程序没有命令行程序集成，并不响应 shell 谓词。  
  
-   文档模板  
  
     在 MFC 中，文档模板将视图，它包含在框架窗口 （在 MDI、 SDI 或 MTI 模式下），与打开的文档相关联。 Windows 窗体具有到文档模板无等效项。  
  
-   文档  
  
     MFC 注册文档文件类型，并从命令行界面中打开文档时处理此文档类型。 Windows 窗体具有任何文档支持。  
  
-   文档状态  
  
     MFC 维护文档的已更新状态。 因此，当你关闭应用程序、 关闭最后一个视图包含的应用程序，或从 Windows 退出，则 MFC 会提示你保存文档。 Windows 窗体具有没有等效的支持。  
  
-   命令  
  
     MFC 提供的命令的概念。 菜单栏、 工具栏和上下文菜单所有可以调用相同的命令，例如，剪切和复制。 Windows 窗体中的命令是从特定的 UI 元素 （如菜单项）; 紧密绑定的事件因此，必须显式挂钩所有命令事件。 你还可以处理与 Windows 窗体中的单个处理程序的多个事件。 有关详细信息，请参阅[将多个事件连接到 Windows 窗体中的单个事件处理程序](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms)。  
  
-   命令传送  
  
     MFC 命令路由允许的活动视图或文档的处理命令。 因为同一命令通常具有不同的含义，为不同的视图 （例如，副本的行为以不同的方式比在图形编辑器中的文本编辑视图中），需要由活动视图处理命令。 由于 Windows 窗体菜单和工具栏的活动视图没有固有了解，不能具有不同类型的处理程序每个视图为你**MenuItem.Click**而无需编写额外的内部代码的事件。  
  
-   命令更新机制  
  
     MFC 具有更新机制的命令。 因此，活动视图或文档是负责的 UI 元素 （例如，启用或禁用菜单项或工具按钮，以及选中状态） 的状态。 Windows 窗体具有一个命令更新机制无等效项。  
  
## <a name="see-also"></a>请参阅  
 [在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Windows 窗体演练](http://msdn.microsoft.com/en-us/fd44d13d-4733-416f-aefc-32592e59e5d9)