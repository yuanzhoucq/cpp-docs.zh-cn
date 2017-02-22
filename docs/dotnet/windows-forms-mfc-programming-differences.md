---
title: "Windows 窗体/MFC 编程差异 | Microsoft Docs"
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
  - "MFC [C++], Windows 窗体支持"
  - "Windows 窗体 [C++], 与 MFC 比较"
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# Windows 窗体/MFC 编程差异
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md) 中的主题描述 MFC 对 Windows 窗体的支持。  如果您不熟悉 .NET Framework 或 MFC 编程，可以从本主题了解两者之间编程差异的相关背景信息。  
  
 Windows 窗体用于在 .NET Framework 上创建 Microsoft Windows 应用程序。  此框架提供一个现代的、面向对象的、可扩展的类集，它使您得以开发丰富的基于 Windows 的应用程序。  使用 Windows 窗体，您可以创建胖客户端应用程序，这种应用程序可使用 Windows 窗体控件访问多种数据源，同时提供数据显示和数据编辑功能。  
  
 但是，如果您已习惯使用 MFC，您可能会习惯于创建某些在 Windows 窗体中尚未受到显式支持的应用程序。  Windows 窗体应用程序等效于 MFC 对话应用程序。  但是，它们并不提供基础结构以直接支持其他 MFC 应用程序类型，如 OLE 文档服务器\/容器、ActiveX 文档或用于单文档界面 \(SDI\)、多文档界面 \(MDI\) 和多个顶级界面 \(MTI\) 的文档\/视图支持。  可以编写自己的逻辑以创建这些应用程序。  
  
 有关 Windows 窗体应用程序的更多信息，请参见 [Windows 窗体介绍](../Topic/Windows%20Forms%20Overview.md)。  
  
 有关能够显示与 MFC 一起使用的 Windows 窗体的示例应用程序信息，请参阅 [MFC 与 Windows 窗体集成](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
 Windows 窗体中并没有提供与下列 MFC 视图或文档以及命令传送相似的功能：  
  
-   shell 集成  
  
     当右击文档并选择如“打开”、“编辑”或“打印”之类的谓词时，MFC 将处理 shell 使用的动态数据交换 \(DDE\) 命令和命令行参数。  Windows 窗体则没有 shell 集成，不对 shell 谓词作出响应。  
  
-   文档模板  
  
     在 MFC 中，文档模板将包含在框架窗口（在 MDI、SDI 或 MTI 模式中）中的视图与打开的文档相关联。  Windows 窗体中则不存在文档模板这样的功能。  
  
-   文档  
  
     当从 shell 打开一个文档时，MFC 将注册这些文档文件类型并处理此文档类型。  Windows 窗体则不支持文档。  
  
-   文档状态  
  
     MFC 会维持文档的已更新状态。  因此，当关闭应用程序、关闭包含应用程序的最后一个视图或退出 Windows 时，MFC 将提示您保存文档。  Windows 窗体则不具有这样的支持。  
  
-   命令  
  
     MFC 有命令的概念。  菜单栏、工具栏和上下文菜单都可以调用相同的命令，例如，“剪切”和“复制”。  在 Windows 窗体中，命令是特定 UI 元素（如菜单项）上的紧绑定事件；因此，必须将所有命令事件显式挂钩。  在 Windows 窗体中也可以用单个处理程序处理多个事件。  有关更多信息，请参见[将多个事件连接到 Windows 窗体中的单个事件处理程序](../Topic/How%20to:%20Connect%20Multiple%20Events%20to%20a%20Single%20Event%20Handler%20in%20Windows%20Forms.md)。  
  
-   命令传送  
  
     MFC 命令传送使活动视图或文档能够处理命令。  由于相同的命令通常对不同的视图有不同的意义（例如，“复制”在文本编辑视图和在图形编辑器中的行为就不同），因此需要由活动视图来处理命令。  由于 Windows 窗体菜单和工具栏对活动视图没有固有理解，因此在未编写额外内部代码的情况下，对于 **MenuItem.Click** 事件，每个视图类型只能有唯一的处理程序。  
  
-   命令更新机制  
  
     MFC 具有命令更新机制。  因此，活动视图或文档负责 UI 元素的状态（例如，启用或禁用菜单项或工具按钮、选中状态等）。  Windows 窗体中则不存在命令更新这样的机制。  
  
## 请参阅  
 [在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Windows Forms Walkthroughs](http://msdn.microsoft.com/zh-cn/fd44d13d-4733-416f-aefc-32592e59e5d9)