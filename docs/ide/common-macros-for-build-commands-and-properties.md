---
title: "用于生成命令和属性的宏 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles"
  - "VC.Project.VCCLCompilerTool.XMLDocumentationFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "$(ConfigurationName) 宏"
  - "$(DevEnvDir) 宏"
  - "$(FrameworkDir) 宏"
  - "$(FrameworkSDKDir) 宏"
  - "$(FrameworkVersion) 宏"
  - "$(FxCopDir) 宏"
  - "$(Inherit) 宏"
  - "$(InputDir) 宏"
  - "$(InputExt) 宏"
  - "$(InputFileName) 宏"
  - "$(InputName) 宏"
  - "$(InputPath) 宏"
  - "$(IntDir) 宏"
  - "$(NoInherit) 宏"
  - "$(OutDir) 宏"
  - "$(ParentName) 宏"
  - "$(PlatformName) 宏"
  - "$(ProjectDir) 宏"
  - "$(ProjectExt) 宏"
  - "$(ProjectFileName) 宏"
  - "$(ProjectName) 宏"
  - "$(ProjectPath) 宏"
  - "$(References) 宏"
  - "$(RemoteMachine) 宏"
  - "$(RootNamespace) 宏"
  - "$(SafeRootNamespace) 宏"
  - "$(SolutionDir) 宏"
  - "$(SolutionExt) 宏"
  - "$(SolutionFileName) 宏"
  - "$(SolutionName) 宏"
  - "$(SolutionPath) 宏"
  - "$(StopEvaluating) 宏"
  - "$(TargetDir) 宏"
  - "$(TargetExt) 宏"
  - "$(TargetFileName) 宏"
  - "$(TargetName) 宏"
  - "$(TargetPath) 宏"
  - "$(VCInstallDir) 宏"
  - "$(VSInstallDir) 宏"
  - "$(WebDeployPath) 宏"
  - "$(WebDeployRoot) 宏"
  - "生成宏 [C++]"
  - "builds [C++], 宏"
  - "ConfigurationName 宏 $(ConfigurationName)"
  - "DevEnvDir 宏 $(DevEnvDir)"
  - "FrameworkDir 宏 $(FrameworkDir)"
  - "FrameworkSDKDir 宏 $(FrameworkSDKDir)"
  - "FrameworkVersion 宏 $(FrameworkVersion)"
  - "FxCopDir 宏 $(FxCopDir)"
  - "Inherit 宏 $(Inherit)"
  - "InputDir 宏 $(InputDir)"
  - "InputExt 宏 $(InputExt)"
  - "InputFileName 宏 $(InputFileName)"
  - "InputName 宏 $(InputName)"
  - "InputPath 宏 $(InputPath)"
  - "IntDir 宏 $(IntDir)"
  - "宏 [C++], 生成宏"
  - "NoInherit 宏 $(NoInherit)"
  - "OutDir 宏 $(OutDir)"
  - "ParentName 宏 $(ParentName)"
  - "PlatformName 宏 $(PlatformName)"
  - "ProjectDir 宏 $(ProjectDir)"
  - "ProjectExt 宏 $(ProjectExt)"
  - "ProjectFileName 宏 $(ProjectFileName)"
  - "ProjectName 宏 $(ProjectName)"
  - "ProjectPath 宏 $(ProjectPath)"
  - "属性 [C++], 生成属性宏"
  - "References 宏 $(References)"
  - "RemoteMachine 宏 $(RemoteMachine)"
  - "RootNamespace 宏 $(RootNamespace)"
  - "SafeRootNamespace 宏 $(SafeRootNamespace)"
  - "SolutionDir 宏 $(SolutionDir)"
  - "SolutionExt 宏 $(SolutionExt)"
  - "SolutionFileName 宏 $(SolutionFileName)"
  - "SolutionName 宏 $(SolutionName)"
  - "SolutionPath 宏 $(SolutionPath)"
  - "StopEvaluating 宏 $(StopEvaluating)"
  - "TargetDir 宏 $(TargetDir)"
  - "TargetExt 宏 $(TargetExt)"
  - "TargetFileName 宏 $(TargetFileName)"
  - "TargetName 宏 $(TargetName)"
  - "TargetPath 宏 $(TargetPath)"
  - "VCInstallDir 宏 $(VCInstallDir)"
  - "VSInstallDir 宏 $(VSInstallDir)"
  - "WebDeployPath 宏 $(WebDeployPath)"
  - "WebDeployRoot 宏 $(WebDeployRoot)"
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
caps.latest.revision: 22
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 用于生成命令和属性的宏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

你可以在项目“属性页”对话框中接受字符串的任意位置使用这些宏。 这些宏不区分大小写。  
  
 若要显示当前可用的宏，请在属性名称右侧列中单击下拉箭头。 如果“编辑”可用，请单击它，然后在“编辑”对话框中单击“宏”。 有关详细信息，请参阅 [属性页](../ide/property-pages-visual-cpp.md) 的 **Specifying User\-Defined Values** 部分。  
  
 标记为“已弃用”的宏不再使用，或已由等效的[项元数据宏](../Topic/ItemMetadata%20Element%20\(MSBuild\).md)（**%\(***名称***\)**）所替代。 标记为“已弃用；已迁移”的宏也已弃用。 此外，如果包含宏的项目迁移自 Visual Studio 2008，则 Visual Studio 会将宏转换为等效的当前宏。  
  
|宏|说明|  
|-------|--------|  
|**$\(RemoteMachine\)**|设置为“调试”属性页上 **Remote Machine**  属性的值。 有关详细信息，请参阅[更改 C\/C\+\+ 调试配置的项目设置](../Topic/Project%20Settings%20for%20a%20C++%20Debug%20Configuration.md)。|  
|**$\(Configuration\)**|当前项目配置的名称（例如“调试”）。|  
|**$\(Platform\)**|当前项目平台的名称（例如“Win32”）。|  
|**$\(ParentName\)**|（已弃用。） 包含此项目项的项的名称。 这将是父文件夹的名称或项目名称。|  
|**$\(RootNameSpace\)**|包含应用程序的命名空间（如果存在）。|  
|**$\(IntDir\)**|为中间文件指定的目录路径。 如果这是一个相对路径，则中间文件将转到追加到项目目录的此路径。 此路径应具有尾随斜杠。 这将解析为 **Intermediate Directory** 属性的值。 请勿使用 **$\(OutDir\)** 定义此属性。|  
|**$\(OutDir\)**|输出文件目录的路径。 如果这是一个相对路径，则输出文件将转到追加到项目目录中的此路径。 此路径应具有尾随斜杠。 这将解析为 **Output Directory** 属性的值。 请勿使用 **$\(IntDir\)** 定义此属性。|  
|**$\(DevEnvDir\)**|Visual Studio 的安装目录（定义为驱动器 \+ 路径）；包括尾随反斜杠“\\”。|  
|**$\(InputDir\)**|（已弃用；已迁移。） 输入文件的目录（定义为驱动器 \+ 路径）；包括尾随反斜杠“\\”。 如果项目即输入，则此宏等同于 **$\(ProjectDir\)**。|  
|**$\(InputPath\)**|（已弃用；已迁移。） 输入文件的绝对路径名称（定义为驱动器 \+ 路径 \+ 基名称 \+ 文件扩展名）。 如果项目即输入，则此宏等同于 **$\(ProjectPath\)**。|  
|**$\(InputName\)**|（已弃用；已迁移。） 输入文件的基名称。 如果项目即输入，则此宏等同于 **$\(ProjectName\)**。|  
|**$\(InputFileName\)**|（已弃用；已迁移。） 输入文件的文件名称（定义为基名称 \+ 文件扩展名）。 如果项目即输入，则此宏等同于 **$\(ProjectFileName\)**。|  
|**$\(InputExt\)**|（已弃用；已迁移。） 输入文件的文件扩展名。 文件扩展名之前包括“.”。 如果项目即输入，则此宏等同于 **$\(ProjectExt\)**。|  
|**$\(ProjectDir\)**|项目的目录（定义为驱动器 \+ 路径）；包括尾随反斜杠“\\”。|  
|**$\(ProjectPath\)**|项目的绝对路径名称（定义为驱动器 \+ 路径 \+ 基名称 \+ 文件扩展名）。|  
|**$\(ProjectName\)**|项目的基名称。|  
|**$\(ProjectFileName\)**|项目的文件名称（定义为基名称 \+ 文件扩展名）。|  
|**$\(ProjectExt\)**|项目的文件扩展名。 文件扩展名之前包括“.”。|  
|**$\(SolutionDir\)**|解决方案的目录（定义为驱动器 \+ 路径）；包括尾随反斜杠“\\”。|  
|**$\(SolutionPath\)**|解决方案的绝对路径名称（定义为驱动器 \+ 路径 \+ 基名称 \+ 文件扩展名）。|  
|**$\(SolutionName\)**|解决方案的基名称。|  
|**$\(SolutionFileName\)**|解决方案的文件名称（定义为基名称 \+ 文件扩展名）。|  
|**$\(SolutionExt\)**|解决方案的文件扩展名。 文件扩展名之前包括“.”。|  
|**$\(TargetDir\)**|生成的主输出文件的目录（定义为驱动器 \+ 路径）；包括尾随反斜杠 “\\”。|  
|**$\(TargetPath\)**|生成的主输出文件的绝对路径名称（定义为驱动器 \+ 路径 \+ 基名称 \+ 文件扩展名）。|  
|**$\(TargetName\)**|生成的主输出文件的基名称。|  
|**$\(TargetFileName\)**|生成的主输出文件的文件名称（定义为基名称 \+ 文件扩展名）。|  
|**$\(TargetExt\)**|生成的主输出文件的文件扩展名。 文件扩展名之前包括“.”。|  
|**$\(VSInstallDir\)**|在其中安装了 Visual Studio 的目录。<br /><br /> 此属性包含目标 Visual Studio 版本，它可能与主机 Visual Studio 不同。 例如，当使用 `$(PlatformToolset) = v110` 进行生成时，**$\(VSInstallDir\)** 包含 Visual Studio 2012 安装的路径。|  
|**$\(VCInstallDir\)**|在其中安装了 Visual C\+\+ 的目录。<br /><br /> 此属性包含目标 Visual C\+\+ 版本，它可能与主机 Visual Studio 不同。 例如，当使用 `$(PlatformToolset) = v90` 进行生成时，**$\(VCInstallDir\)** 包含 Visual C\+\+ 2008 安装的路径。|  
|**$\(FrameworkDir\)**|在其中安装了 .NET Framework 的目录。|  
|**$\(FrameworkVersion\)**|Visual Studio 使用的.NET framework 版本。 结合 **$\(FrameworkDir\)**，Visual Studio 使用的.NET Framework 版本的完整路径。|  
|**$\(FrameworkSDKDir\)**|在其中安装了 .NET Framework 的目录。 .NET Framework 可能已作为 Visual Studio 的一部分安装或单独安装。|  
|**$\(WebDeployPath\)**|从 Web 部署根到项目输出位置的相对路径。 返回与 <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A> 相同的值。|  
|**$\(WebDeployRoot\)**|**\<localhost\>** 的位置的绝对路径。 例如，c:\\inetpub\\wwwroot。|  
|**$\(SafeParentName\)**|（已弃用。） 有效名称格式中直接父级的名称。 例如，窗体是 .resx 文件的父级。|  
|**$\(SafeInputName\)**|（已弃用。） 作为有效类名称的文件名，去掉文件扩展名。|  
|**$\(SafeRootNamespace\)**|（已弃用。） 项目向导将在其中添加代码的命名空间名。 此命名空间名将仅包含有效的 C\+\+ 标识符中允许的字符。|  
|**$\(FxCopDir\)**|fxcop.cmd 文件的路径。 fxcop.cmd 文件不随所有 Visual C\+\+ 版本安装。|  
  
## 请参阅  
 [在 Visual Studio 中生成 C\+\+ 项目](../ide/building-cpp-projects-in-visual-studio.md)