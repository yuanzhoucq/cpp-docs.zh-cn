---
title: "“常规”属性页（项目） | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCConfiguration.IntermediateDirectory"
  - "VC.Project.VCConfiguration.ConfigurationType"
  - "VC.Project.VCConfiguration.ManagedExtensions"
  - "VC.Project.VCConfiguration.BuildBrowserInformation"
  - "VC.Project.VCConfiguration.BuildLogFile"
  - "VC.Project.VCConfiguration.PlatformToolset"
  - "VC.Project.VCConfiguration.TargetName"
  - "VC.Project.VCConfiguration."
  - "VC.Project.VCConfiguration.TargetExt"
  - "VC.Project.VCConfiguration.ATLMinimizesCRunTimeLibraryUsage"
  - "VC.Project.VCConfiguration.ReferencesPath"
  - "VC.Project.VCConfiguration.DeleteExtensionsOnClean"
  - "VC.Project.VCConfiguration.useOfMfc"
  - "VC.Project.VCConfiguration.CharacterSet"
  - "VC.Project.VCGeneralMakefileSettings.ConfigurationType"
  - "VC.Project.VCConfiguration.OutputDirectory"
  - "VC.Project.VCConfiguration.AppSupport"
  - "VC.Project.VCConfiguration.ToolFiles"
  - "VC.Project.VCConfiguration.useOfATL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "“Clean Build”选项"
  - "输出文件，设置目录"
  - "Unicode，创建 C++ 生成配置"
ms.assetid: 593b383c-cd0f-4dcd-ad65-9ec9b4b19c45
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# “常规”属性页（项目）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在解决方案资源管理器中右键单击项目节点并选择“属性”时，左窗格中“配置属性”节点下的“常规”属性页将显示属性的两个部分：  
  
-   常规  
  
-   项目默认值  
  
## 常规  
 “常规”部分中的属性影响在生成过程中创建的文件的位置，并影响当已选中“清理”选项（“生成”菜单）时要删除哪些文件。  
  
 **目标平台**  
 指定项目将在其中运行的平台。 例如，Windows、Android 或 iOS。 值 **Windows 10** 表示面向通用 Windows 平台的项目。 如果你面向的是 Windows 的早期版本，则版本未被列出且此字段中的值将仅显示为 **Windows**。 这是当你创建项目时将设置的一个只读字段。  
  
 **目标平台版本**  
 对于 Windows 平台，指定生成项目所使用的 Windows SDK 的版本。 对于 Windows，这就是 Windows SDK 版本。[!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 附带了Windows SDK 8.1。 如果已安装了[Windows 10 工具](http://go.microsoft.com/fwlink/p/?LinkId=617631)，则已安装的那些工具的每个版本将出现在下拉列表中。  
  
 若要面向 Windows 7 或 Windows Vista，请使用值 **8.1**，因为 Windows SDK 8.1 对那些平台向后兼容。 此外，你应在 targetver.h 中为 \_WIN32\_WINNT 定义适当的值。 对于 Windows 7，即 0x0601。 请参阅 [修改 WINVER 和 \_WIN32\_WINNT](../porting/modifying-winver-and-win32-winnt.md)。  
  
 可以安装 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] 中内附的 v110\_xp 平台工具集，以便使用当前版本的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 来构建 Windows XP 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 项目。 有关如何获取和使用此平台工具集的信息，请参阅 [配置适用于 Windows XP 的 C\+\+ 11 程序](../build/configuring-programs-for-windows-xp.md)。 有关更改平台工具集的其他信息，请参阅 [如何：修改目标框架和平台工具集](../build/how-to-modify-the-target-framework-and-platform-toolset.md)。  
  
 **目标平台最低 版本**  
 指定项目可以在其中运行的最低版本平台。 仅当项目类型支持时，此属性才（在例如 Windows 通用项目中）显示。 如果你的应用可以利用较新 Windows SDK 版本中的功能，但仍可以在不包含这些功能的早期版本上运行（可能有一些功能丢失），则这两个属性的值可能不同。 如果这样，你的代码应检查在运行时它所运行的平台的版本，并且不尝试使用在较旧的平台版本中不可用的功能。  
  
 请注意，Visual C\+\+ 不强制实施此选项。 包含它是为了与其他语言（如 C\# 和 JavaScript）保持一致，并为使用你的项目的任何人提供指南。 如果你使用在最低版本中不可用的一个功能，则 Visual C\+\+ 不会生成错误。  
  
 **输出目录**  
 指定链接器等工具将放置在生成过程中创建的所有最终输出文件的目录。 通常，这包括链接器、库管理器或 BSCMake 等工具的输出。  
  
 若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>。  
  
 **中间目录**  
 指定编译器等工具将放置在生成过程中创建的所有中间文件的目录。 通常，这包括 C\/C\+\+ 编译器、MIDL 和资源编译器等工具的输出。  
  
 若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>。  
  
 **目标文件名**  
 指定此项目生成的文件名称。  
  
 **目标文件扩展名**  
 指定此项目生成的文件扩展名；例如，.exe 或 .dll。  
  
 **清除时要删除的扩展名**  
 “清理”选项（“生成”菜单）从生成项目的配置的中间目录中删除文件。 具有使用此属性指定的扩展名的文件将在运行“清理”或当你执行重新生成时被删除。 除了中间目录中具有这些扩展名的文件以外，生成系统也将删除任何已知的生成输出，而无论它所在的位置（包括中间输出，如 .obj 文件）。 请注意，你可以指定通配符。  
  
 若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>。  
  
 **生成日志文件**  
 允许你指定生成项目时创建的日志文件的非默认位置。  
  
 可使用项目宏来更改目录位置。 请参阅 [用于生成命令和属性的宏](../ide/common-macros-for-build-commands-and-properties.md)。  
  
 **平台工具集**  
 允许项目面向不同版本的 Visual C\+\+ 库和编译器。[!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 项目既可以 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] \(**v100**\) 中的默认工具集为目标，也可以创建能够在 Windows XP 上运行的可执行文件的工具集为目标。  
  
## 项目默认值  
 “项目默认设置”部分中的属性表示你可以修改的默认属性。 可以在*安装目录*\\VC\\VCProjectDefaults 中的 .props 文件中找到这些属性的定义。  
  
 **配置类型**  
 有几种配置类型可供选择：  
  
-   **“应用程序 \(.exe\)”** 显示链接器工具集（C\/C\+\+ 编译器、MIDL、资源编译器、链接器、BSCMake、XML Web 服务代理生成器、自定义生成、预生成、链接前、生成后事件）。  
  
-   **“动态库 \(.dll\)”** 显示链接器工具集，指定 \/DLL 链接器选项以及将 \_WINDLL 定义添加到 CL。  
  
-   **“生成文件”** 显示生成文件工具集 \(NMake\)。  
  
-   **“静态库 \(.lib\)”** 显示库管理器工具集（除了链接器的替代库管理器外，其他与链接器工具集相同并且省略了 XML Web 服务代理生成器）。  
  
-   **“实用程序”** 显示实用程序工具集（MIDL、自定义生成、预生成、生成后事件）。  
  
 若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>。  
  
 **MFC 的使用**  
 指定 MFC 项目将静态还是动态链接到 MFC DLL。 非 MFC 项目可以选择**“使用标准 Windows 库”**以链接到使用 MFC 时将包括在内的各种 Win32 库。  
  
 若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>。  
  
 **ATL 的使用**  
 指定 ATL 项目将静态还是动态链接到 ATL .DLL。 如果指定**“不使用 ATL”**以外的任何内容，定义将被添加到编译器的**“命令行”**属性页。  
  
 若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfATL%2A>。  
  
 **字符集**  
 定义应设置 \_UNICODE 还是 \_MBCS。 在适当的情况下，还会影响链接器入口点。  
  
 若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>。  
  
 **公共语言运行时支持**  
 导致要使用 [\/clr](../build/reference/clr-common-language-runtime-compilation.md) 编译器选项。  
  
 若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>。  
  
 **全程序优化**  
 指定 [\/GL](../build/reference/gl-whole-program-optimization.md) 编译器选项和 [\/LTCG](../build/reference/ltcg-link-time-code-generation.md) 链接器选项。  
  
 **Windows 应用商店应用支持**  
 指定该项目是否支持 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]应用。 有关详细信息，请参阅 [\/ZW（Windows 运行时编译）](../build/reference/zw-windows-runtime-compilation.md) 和 Windows 开发人员中心。  
  
## 请参阅  
 [属性页](../ide/property-pages-visual-cpp.md)