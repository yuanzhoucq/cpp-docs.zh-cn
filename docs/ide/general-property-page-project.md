---
title: "常规属性页 （项目） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.ManagedExtensions
- VC.Project.VCConfiguration.BuildBrowserInformation
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.ATLMinimizesCRunTimeLibraryUsage
- VC.Project.VCConfiguration.ReferencesPath
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.useOfMfc
- VC.Project.VCConfiguration.CharacterSet
- VC.Project.VCGeneralMakefileSettings.ConfigurationType
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.AppSupport
- VC.Project.VCConfiguration.ToolFiles
- VC.Project.VCConfiguration.useOfATL
dev_langs:
- C++
helpviewer_keywords:
- Clean Build option
- output files, setting directory
- Unicode, creating C++ build configuration
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 772192a4b367760e85bb1631f1ef7b50650af0c1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="general-property-page-project"></a>“常规”属性页（项目）

在中的项目节点，在解决方案资源管理器，右键单击并选中**属性**、**常规**下的属性页**配置属性**中的节点左窗格中显示属性的两个的部分：

- 常规

- 项目默认值

对于非 Windows 项目，请参阅[Linux c + + 属性页引用](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->。

## <a name="general"></a>常规

常规部分中的属性影响在生成过程创建和删除时的文件的文件的位置**清理**选项 (**生成**菜单) 选择。

**目标平台**  
指定项目将在其中运行的平台。 例如，Windows、Android 或 iOS。 值**Windows 10**表示通用 Windows 平台的项目目标。 如果你面向的早期版本的 Windows，则版本未列出且此字段中的值将仅显示为**Windows**。 这是当你创建项目时将设置的一个只读字段。

**Windows SDK 版本**  
对于 Windows 目标平台上，它指定你的项目需要的 Windows sdk 的版本。 在使用 Visual Studio 安装程序安装 c + + 工作负荷，也会安装 Windows SDK 的必需的部分。 如果你的计算机上有其他 Windows SDK 版本，每个版本的已安装的 SDK 工具会出现的下拉列表中。

若要针对 Windows 7 或 Windows Vista，使用值**8.1**，因为 Windows SDK 8.1 对那些平台向后的兼容。 此外，你应在其中定义的相应值**_WIN32_WINNT**在 targetver.h 中。 对于 Windows 7，即 0x0601。 请参阅[修改 WINVER 和 _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md)。

你可以安装 Visual Studio，若要使用当前版本的库构建 Windows XP 和 Windows 2003 Server 项目中包含的 Windows XP 平台工具集。 有关如何获取和使用此平台工具集的信息，请参阅[适用于 Windows XP 配置程序](../build/configuring-programs-for-windows-xp.md)。 有关更改平台工具集的其他信息，请参阅[如何：修改目标框架和平台工具集](../build/how-to-modify-the-target-framework-and-platform-toolset.md)。

**目标平台最小版本**  
指定项目可以在其中运行的最低版本平台。 仅当项目类型支持时，此属性才（在例如 Windows 通用项目中）显示。 如果你的应用可以利用较新 Windows SDK 版本中的功能，但仍可以在不包含这些功能的早期版本上运行（可能有一些功能丢失），则这两个属性的值可能不同。 如果这样，你的代码应检查在运行时它所运行的平台的版本，并且不尝试使用在较旧的平台版本中不可用的功能。

请注意，Visual C++ 不强制实施此选项。 包含它是为了与其他语言（如 C# 和 JavaScript）保持一致，并为使用你的项目的任何人提供指南。 如果你使用在最低版本中不可用的一个功能，则 Visual C++ 不会生成错误。

**输出目录**  
指定链接器等工具将放置在生成过程中创建的所有最终输出文件的目录。 通常，这包括链接器、库管理器或 BSCMake 等工具的输出。 默认情况下，此属性是指定宏 $(SolutionDir) $（配置） 的目录 \。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>。

**中间目录**  
指定编译器等工具将放置在生成过程中创建的所有中间文件的目录。 通常，这包括 C/C++ 编译器、MIDL 和资源编译器等工具的输出。 默认情况下，此属性是指定宏 $（配置） 的目录 \。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>。

**目标名称**  
指定此项目生成的文件名称。 默认情况下，此属性是由宏 $(ProjectName) 指定的文件名。

**目标文件扩展名**  
指定此项目生成的文件扩展名；例如，.exe 或 .dll。

**删除的干净扩展名**  
**清理**选项 (**生成**菜单) 从在其中生成项目的配置的中间目录中删除文件。 将具有使用此属性指定的扩展名的文件时删除**清理**运行或当你执行重新生成。 除了中间目录中具有这些扩展名的文件以外，生成系统也将删除任何已知的生成输出，而无论它所在的位置（包括中间输出，如 .obj 文件）。 请注意，你可以指定通配符。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>。

**生成日志文件**  
允许你指定生成项目时创建的日志文件的非默认位置。 默认位置是由宏 $(IntDir) $(MSBuildProjectName).log 指定的。

可使用项目宏来更改目录位置。 请参阅[用于生成命令和属性的公共宏](../ide/common-macros-for-build-commands-and-properties.md)。

**平台工具集**  
允许项目面向不同版本的 Visual C++ 库和编译器。 Visual c + + 项目可面向任一默认工具集安装的 Visual Studio 中，或多个以前版本的 Visual Studio 中，包括创建可以 Windowx XP 运行的可执行文件的工具集安装的工具集之一。 有关更改平台工具集的信息，请参阅[如何： 修改目标框架和平台工具集](../build/how-to-modify-the-target-framework-and-platform-toolset.md)。

**启用托管增量生成**  
对于托管项目，使生成的程序集外部可见性的检测。 如果更改为托管项目不可见的其他项目，然后不重新生成依赖项目。 这可以显著提高包括托管的项目的解决方案中的生成时间。

## <a name="project-defaults"></a>项目默认值

“项目默认设置”部分中的属性表示你可以修改的默认属性。 可以在中的.props 文件中找到的这些属性定义*安装目录*\VC\VCProjectDefaults。

**配置类型**  
有几种配置类型可供选择：

- **应用程序 (.exe)**，显示链接器工具集 （C/c + + 编译器、 MIDL、 资源编译器、 链接器、 BSCMake、 XML Web 服务代理生成器、 自定义生成、 预生成、 链接前、 生成后事件）。

- **动态库 (.dll)**显示链接器工具集，指定 /DLL 链接器选项，以及将 _WINDLL 定义到 CL。

- **生成文件**，显示生成文件工具集 (NMake)。

- **静态库 (.lib)**，显示库管理器工具集 （除了链接器替代库管理器并且省略了 XML Web 服务代理生成器的链接器工具集相同）。

- **实用工具**，显示实用程序工具集 (MIDL、 自定义生成、 预生成、 生成后事件)。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>。

**MFC 的使用**  
指定 MFC 项目将静态还是动态链接到 MFC DLL。 非 MFC 项目可以选择**使用标准 Windows 库**以链接到使用 MFC 时将包括在内的各种 Win32 库。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>。

**ATL 的使用**  
指定 ATL 项目将静态还是动态链接到 ATL .DLL。 如果不指定任何其他**不使用 ATL**，定义将被添加到编译器的**命令行**属性页。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfATL%2A>。

**字符集**  
定义应设置 _UNICODE 还是 _MBCS。 在适当的情况下，还会影响链接器入口点。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>。

**公共语言运行时支持**  
导致[/clr](../build/reference/clr-common-language-runtime-compilation.md)编译器选项来使用。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>。

**.NET 目标框架版本**  
在托管项目中，指定为目标的.NET framework 版本。

**全程序优化**  
指定[/GL](../build/reference/gl-whole-program-optimization.md)编译器选项和[/LTCG](../build/reference/ltcg-link-time-code-generation.md)链接器选项。 默认情况下，这对于调试配置，禁用和启用零售配置。

**Windows 应用商店应用支持**  
指定此项目是否支持 Windows 运行时 （通用 Windows 平台） 应用。 有关详细信息，请参阅[/ZW （Windows 运行时编译）](../build/reference/zw-windows-runtime-compilation.md)，和 Windows 开发人员中心。

## <a name="see-also"></a>请参阅

[属性页](../ide/property-pages-visual-cpp.md)  