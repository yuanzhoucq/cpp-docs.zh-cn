---
title: "用于 Visual C++ 开发的 IDE 和工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Visual C++, 开发工具"
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 用于 Visual C++ 开发的 IDE 和工具
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

作为 Visual Studio 集成开发环境 (IDE) 的一部分，Visual C++ 共享许多与其他语言相同的窗口和工具。 其中许多窗口和工具（包括“解决方案资源管理器” 、“代码编辑器”和“调试器”）都记录在 MSDN 库中的 [Visual Studio IDE](../Topic/Visual%20Studio%20IDE.md)之下。 通常，共享的工具或窗口为 C++ 提供的功能集与为 .NET 语言或 Javascript 提供的功能集略有不同。 某些窗口或工具仅在 Visual Studio Pro 或 Visual Studio Enterprise 中可用。 本主题从 Visual C++ 的角度来介绍 Visual Studio IDE，并提供指向与 Visual C++ 相关的其他主题的链接。  
  
 除了 Visual Studio IDE 中的共享工具之外，Visual C++ 还有几种专门用于本机代码开发的工具。 这些工具也会在本文中列出。 有关每个版本的 Visual Studio 中可用的工具列表，请参阅 [Visual C++ Tools and Templates in Visual Studio Editions](../ide/visual-cpp-tools-and-templates-in-visual-studio-editions.md)。  
  
## <a name="creating-a-solution-and-projects"></a>创建解决方案和项目  
 在所有版本的 Visual C++ 中，都可将可执行文件（例如 .exe、.dll 或 .lib）的源代码和相关文件组织为一个项目。 一个项目具有一个 XML 格式的项目文件 (.vcxproj)，指定了编译程序所需的所有文件和资源，以及其他配置设置（例如目标平台（x 86、x64 或 ARM）以及生成的是程序的发行版本还是调试版本）。 一个项目（或多个项目）包含在一个 *解决方案*中；例如，一个解决方案可能包含多个 Win32 DLL 项目和一个使用这些 DLL 的 Win32 控制台应用程序。 生成项目时，MSBuild 引擎将使用项目文件并生成可执行文件和/或你指定的任何其他自定义输出。  
  
 **项目模板**  
  
 Visual C++ 附带了几个项目模板，其中包含起始代码和多种基本程序类型所需的设置。 您通常通过选择启动 **文件 &#124;新项目** 若要从项目模板创建一个项目，然后将新的源代码文件添加到该项目中，或在开始编码中提供的文件。 有关特定于 C++ 项目和项目向导的信息，请参阅 [Creating and Managing Visual C++ Projects](../ide/creating-and-managing-visual-cpp-projects.md)。  
  
 **应用程序向导**  
  
 Visual C++ 为某些项目类型提供了向导。 向导将指导你逐步完成创建一个新项目的过程。 这对于具有许多选项和设置的项目类型很有用。 有关详细信息，请参阅 [Creating Desktop Projects By Using Application Wizards](../ide/creating-desktop-projects-by-using-application-wizards.md)。  
  
## <a name="creating-user-interfaces-with-designers"></a>使用设计器创建用户界面  
 如果你的程序包含用户界面，则首要任务之一是使用控件（如按钮和列表框等）对其进行填充。 Visual Studio 包括一个可视化设计图面和工具箱，可创建各种风格的 C++ 应用程序。 无论正在创建哪种类型的应用，基本理念都是相同的：从工具箱窗口拖动控件，将其放置到设计图面上的所需位置。 Visual Studio 将在后台生成使所有应用都正常运行所需的资源和代码。  
  
 有关设计用于通用 Windows 平台应用程序的用户界面的详细信息，请参阅  [设计和用户界面](https://developer.microsoft.com/en-us/windows/design)。  
  
 有关为 MFC 应用程序创建用户界面的详细信息，请参阅 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)。 Win32 Windows 程序的相关信息，请参阅 [Windows 桌面应用程序](../windows/windows-desktop-applications-cpp.md)。  
  
 有关使用 C++/CLI 的 Windows 窗体应用程序的信息，请参阅 [使用 .NET Framework 创建 Windows 窗体应用程序 (C++)](http://msdn.microsoft.com/zh-cn/8e007885-6c8b-4fb2-a41d-91febd114a9b)。  
  
## <a name="writing-and-editing-code"></a>编写和编辑代码  
 **语义颜色设置**  
  
 创建项目后，所有项目文件将都显示在“解决方案资源管理器”窗口中。 当你单击解决方案资源管理器中的 .h 或 .cpp 文件时，该文件将在代码编辑器中打开。 代码编辑器是专用于 C++ 源代码的字处理器。 它会以不同的颜色标记语言关键字、方法和变量名以及代码的其他元素，使代码更具可读性且更易于理解。  
  
 **Intellisense**  
  
 代码编辑器还支持几个功能，这些功能组合在一起被称为 Intellisense。 可以将鼠标悬停在某种方法上，并查看该方法的一些相关基本文档。 键入类变量名称以及 . 或 -> 后，将显示该类的实例成员列表。 如果键入一个类名，然后键入 ::，则将显示静态成员列表。 当开始键入类名或方法名时，代码编辑器中将提供完成语句的建议。 有关详细信息，请参阅 [Using IntelliSense](../Topic/Using%20IntelliSense.md)。  
  
 **代码段**  
  
 可以使用 Intellisense 代码片段，通过快捷方式击键生成常用的或复杂的代码构造。 有关详细信息，请参阅 [Code Snippets](../Topic/Code%20Snippets.md)。  
  
## <a name="navigating-code"></a>导航代码  
 “视图”菜单提供对多个窗口和工具的访问，这些窗口和工具用于在代码文件中导航。 有关这些窗口的详细信息，请参阅 [Viewing the Structure of Code](../Topic/Viewing%20the%20Structure%20of%20Code.md)。  
  
 **解决方案资源管理器**  
  
 在所有版本的 Visual Studio 中，使用“解决方案资源管理器”窗格在项目中的文件之间导航。 展开 .h 或 .cpp 文件图标，查看文件中的类。 展开某个类，以查看其成员。 双击某个成员，以导航到其在文件中的定义或实现。  
  
 **类视图和代码定义窗口**  
  
 使用“类视图”窗格，可查看所有文件中的命名空间和类（包括分部类）。 展开每个命名空间或类可查看其成员，而双击成员可导航到源文件中的该位置。 如果打开“代码定义”窗口，则当在类视图中选择类型时，可以查看该类型的定义或实现。  
  
 **对象浏览器**  
  
 使用对象浏览器浏览 Windows 运行时组件（.winmd 文件）、.NET 程序集和 COM 类型库中的类型信息。 它不与 Win32 DLL 一起使用。  
  
 **转到定义/声明**  
  
 在任何 API 名称或成员变量上按 F12，以转到其定义。 如果定义位于 .winmd 文件（对于 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用）中，则将在对象浏览器中显示类型信息。 还可右键单击变量名或类型名称，并从上下文菜单中选择相应选项，以“转到定义”或“转到声明”。  
  
 **查找所有引用**  
  
 在源代码文件中，将鼠标光标置于类型、方法或变量的名称上，右键单击，并选择“查找所有引用”，以返回文件、项目或解决方案中使用该类型的每个位置的列表。 “查找所有引用”十分智能，仅返回同一变量的实例，即使其他作用域中的其他变量具有相同的名称。  
  
 **体系结构资源管理器和依赖项关系图 (Ultimate)**  
  
 使用体系结构资源管理器可查看代码中各个元素之间的关系。 有关详细信息，请参阅 [使用体系结构资源管理器查找代码](http://msdn.microsoft.com/zh-cn/b1707926-ef73-47f9-92cd-e00d0fac7e76)。 使用依赖项关系图可查看依赖关系。 有关详细信息，请参阅 [How to: Generate Dependency Graphs for C and C++ Code](http://msdn.microsoft.com/zh-cn/3bd5cf9f-62f6-41d0-9f35-d4b2637cba3c)。  
  
## <a name="adding-and-editing-resources"></a>添加和编辑资源  
 Visual Studio 桌面项目的上下文中的术语“资源”包括许多内容，例如对话框、图标、可本地化的字符串、初始屏幕、数据库连接字符串或想要包含在可执行文件中的任意数据。  
  
 有关在本机桌面 C++ 项目中添加资源以及编辑其中资源的详细信息，请参阅 [Working with Resource Files](../mfc/working-with-resource-files.md)。  
  
## <a name="building-compiling-and-linking"></a>生成（编译和链接）  
 按 **Ctrl + Shift + B** ，编译并链接一个项目。 Visual Studio 使用 [MSBuild](MSBuild1.md) 来创建可执行代码。 您可以设置下的常规生成选项 **工具和 #124;选项 &#124;项目和解决方案** 还可以设置下的特定项目的属性 **项目 &#124;属性**。 生成错误和警告报告在错误列表 (**Ctrl +\\, ，E**)。 其他信息有时会显示在输出窗口中 (**Alt + 2**)。 有关详细信息，请参阅  [使用项目属性](../ide/working-with-project-properties.md) 和 [Visual Studio 中生成 c + + 项目](../ide/building-cpp-projects-in-visual-studio.md)。  
  
 还可以直接从命令行使用 Visual C++ 编译器 (cl.exe) 和许多其他与生成相关的独立工具（如 NMAKE 和 LIB）。 有关详细信息，请参阅 [Building on the Command Line](../build/building-on-the-command-line.md) 和 [C/C++ Building Reference](../build/reference/c-cpp-building-reference.md)。  
  
## <a name="testing"></a>测试  
 Visual Studio 包含一个用于本机 C++ 和 C++/CLI 的单元测试框架。 有关详细信息，请参阅 [使用单元测试验证代码](../Topic/Unit%20Test%20Your%20Code.md) 和 [用适用于 C++ 的 Microsoft 单元测试框架编写 C/C++ 单元测试](../Topic/Writing%20Unit%20tests%20for%20C-C++%20with%20the%20Microsoft%20Unit%20Testing%20Framework%20for%20C++.md)  
  
## <a name="debugging"></a>调试  
 将项目配置设置为“调试”时，按 F5 即可调试程序。 在调试期间，可通过按 F9 设置断点、按 F10 逐步执行代码、查看指定变量或寄存器的值，甚至还可在某些情况下在代码中进行更改并继续调试，而无需重新编译。 有关详细信息，请参阅 [Debugging in Visual Studio](../Topic/Debugging%20in%20Visual%20Studio.md)。  
  
## <a name="deploying-completed-applications"></a>部署已完成的应用程序  
 在部署 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 通过 Windows 应用商店通过向客户 **项目 &#124;应用商店** 菜单选项。 将在后台自动处理 CRT 的部署。 有关更多信息，请参阅 [将你的应用投入市场](http://go.microsoft.com/fwlink/p/?LinkId=262280)。  
  
 将本机 C++ 桌面应用程序部署到另一台计算机时，必须安装该应用程序及其依赖的任何库文件。 为应用程序部署 Visual C++ 运行时有 3 种方法：集中部署、本地部署或静态链接。 有关详细信息，请参阅 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)。  
  
 有关部署的 C + + /CLI 程序，请参阅 [开发人员部署指南](../Topic/.NET%20Framework%20Deployment%20Guide%20for%20Developers.md),，  
  
## <a name="other-tools"></a>其他工具  
  
## <a name="related-articles"></a>相关文章  
  
|||  
|-|-|  
|[Visual c + + 工具和 Visual Studio 版本中的模板](../ide/visual-cpp-tools-and-templates-in-visual-studio-editions.md)|显示各种版本的 Visual Studio 中提供的功能。|  
|[Visual c + + 指导教程](http://msdn.microsoft.com/zh-cn/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)|提供 Visual Studio 开发环境和可创建的 C++ 应用类型的概述。|  
|[创建和管理 Visual c + + 项目](../ide/creating-and-managing-visual-cpp-projects.md)|对 Visual Studio 中的 C++ 项目和指向其他介绍如何创建和管理它们的文章的链接进行了概述。|  
|[生成 C/c + + 程序](../build/building-c-cpp-programs.md)|介绍如何生成 C++ 项目。|  
|[部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)|对 C++ 应用的部署和指向其他详细介绍部署的文章的链接进行了概述。|  
|[移植和升级程序](http://msdn.microsoft.com/zh-cn/c36c44b3-5a9b-4bb4-9b7a-469aa770ed00)|指向文章的链接，这些文章介绍如何打开在早期版本的 Visual Studio 中创建的 C++ 应用，以及如何打开使用工具而非 Visual Studio 创建的应用。|  
|||  
|[Visual C++](../top/visual-cpp-in-visual-studio-2015.md)|描述 Visual C++ 在 Visual Studio 中的主要功能，并链接到 Visual C++ 文档的剩余部分。|