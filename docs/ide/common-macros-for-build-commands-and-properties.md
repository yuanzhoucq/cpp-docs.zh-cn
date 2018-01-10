---
title: "用于生成命令和属性的公共宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs: C++
helpviewer_keywords:
- $(FrameworkSDKDir) macro
- ProjectName macro $(ProjectName)
- DevEnvDir macro $(DevEnvDir)
- $(DevEnvDir) macro
- TargetPath macro $(TargetPath)
- VSInstallDir macro $(VSInstallDir)
- $(InputFileName) macro
- $(SolutionFileName) macro
- macros [C++], build macros
- InputFileName macro $(InputFileName)
- $(VCInstallDir) macro
- $(IntDir) macro
- $(ConfigurationName) macro
- SolutionDir macro $(SolutionDir)
- $(TargetPath) macro
- $(Inherit) macro
- $(SolutionPath) macro
- WebDeployRoot macro $(WebDeployRoot)
- WebDeployPath macro $(WebDeployPath)
- StopEvaluating macro $(StopEvaluating)
- $(RootNamespace) macro
- $(WebDeployRoot) macro
- ProjectPath macro $(ProjectPath)
- $(ProjectPath) macro
- $(InputDir) macro
- SolutionName macro $(SolutionName)
- ProjectExt macro $(ProjectExt)
- $(TargetExt) macro
- $(ProjectFileName) macro
- TargetName macro $(TargetName)
- $(References) macro
- References macro $(References)
- TargetExt macro $(TargetExt)
- ProjectDir macro $(ProjectDir)
- $(TargetDir) macro
- SolutionExt macro $(SolutionExt)
- $(SolutionDir) macro
- ProjectFileName macro $(ProjectFileName)
- VCInstallDir macro $(VCInstallDir)
- $(InputExt) macro
- $(TargetFileName) macro
- $(SolutionExt) macro
- PlatformName macro $(PlatformName)
- IntDir macro $(IntDir)
- $(FrameworkVersion) macro
- $(ProjectDir) macro
- build macros [C++]
- InputPath macro $(InputPath)
- $(VSInstallDir) macro
- $(WebDeployPath) macro
- TargetFileName macro $(TargetFileName)
- NoInherit macro $(NoInherit)
- ConfigurationName macro $(ConfigurationName)
- $(ProjectExt) macro
- TargetDir macro $(TargetDir)
- InputName macro $(InputName)
- $(ProjectName) macro
- FrameworkSDKDir macro $(FrameworkSDKDir)
- $(ParentName) macro
- InputExt macro $(InputExt)
- $(SafeRootNamespace) macro
- InputDir macro $(InputDir)
- $(FxCopDir) macro
- $(RemoteMachine) macro
- Inherit macro $(Inherit)
- FrameworkVersion macro $(FrameworkVersion)
- $(StopEvaluating) macro
- $(OutDir) macro
- FrameworkDir macro $(FrameworkDir)
- SolutionFileName macro $(SolutionFileName)
- $(NoInherit) macro
- RemoteMachine macro $(RemoteMachine)
- properties [C++], build property macros
- $(TargetName) macro
- $(SolutionName) macro
- $(InputPath) macro
- ParentName macro $(ParentName)
- OutDir macro $(OutDir)
- SafeRootNamespace macro $(SafeRootNamespace)
- FxCopDir macro $(FxCopDir)
- $(InputName) macro
- RootNamespace macro $(RootNamespace)
- builds [C++], macros
- $(FrameworkDir) macro
- $(PlatformName) macro
- SolutionPath macro $(SolutionPath)
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f96e403516d6f85804fa798d7a0c28575482ff43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="common-macros-for-build-commands-and-properties"></a>用于生成命令和属性的公共宏
具体取决于您的安装选项，Visual Studio 可以提供数百个宏给您。 这些方法对应于默认情况下，或在.props 或.targets 文件中或在项目设置中设置的 MSBuild 属性。 你可以在项目“属性页”  对话框中接受字符串的任意位置使用这些宏。 这些宏不区分大小写。  
  
 若要显示当前可用的宏，请在属性名称右侧列中单击下拉箭头。 如果“编辑”  可用，请单击它，然后在“编辑”对话框中单击“宏” 。 有关详细信息，请参阅**Specifying User-Defined 值**部分[属性页](../ide/property-pages-visual-cpp.md)。  
  
 标记为“已弃用”的宏不再使用，或已由等效的 [项元数据宏](/visualstudio/msbuild/itemmetadata-element-msbuild) （**%(***名称***)**）所替代。 标记为“已弃用；已迁移”的宏也已弃用。 此外，如果包含宏的项目迁移自 Visual Studio 2008，则 Visual Studio 会将宏转换为等效的当前宏。  
  
 下表介绍常用可用宏的子集。 此列表并不详尽。 有关如何创建和用作.props、.targets 和.vcxproj 文件中的宏 MSBuild 属性定义的详细信息，请参阅[MSBuild 属性](/visualstudio/msbuild/msbuild-properties)。  
  
|宏|描述|  
|-----------|-----------------|  
|**$ （remotemachine)**|设置为“调试”属性页上 **Remote Machine** 属性的值。 有关详细信息，请参阅 [更改 C/C++ 调试配置的项目设置](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) 。|  
|**$(Configuration)**|当前项目配置的名称，例如，“调试”。|  
|**$(Platform)**|当前项目平台，例如，"Win32"的名称。|  
|**$ （parentname)**|（已弃用。）包含此项目项的项的名称。 这将是父文件夹的名称或项目名称。|  
|**$ （rootnamespace)**|包含应用程序的命名空间（如果存在）。|  
|**$(IntDir)**|为中间文件指定的目录路径。 如果这是一个相对路径，中间文件将转到追加到项目目录的此路径。 此路径应具有尾随斜杠。 这将解析为 **Intermediate Directory** 属性的值。 请勿使用 **$(OutDir)** 定义此属性。|  
|**$(OutDir)**|输出文件目录的路径。 如果这是一个相对路径，则输出文件将转到追加到项目目录中的此路径。 此路径应具有尾随斜杠。 这将解析为 **Output Directory** 属性的值。 请勿使用 **$(IntDir)** 定义此属性。|  
|**$ （devenvdir)**|（定义为驱动器 + 路径）; 的 Visual Studio 安装目录包括尾随反斜杠\\。|  
|**$ （inputdir)**|（已弃用；已迁移。）输入文件 （定义为驱动器 + 路径）; 的目录包括尾随反斜杠\\。 如果项目即输入，则此宏等同于 **$(ProjectDir)**。|  
|**$ （inputpath)**|（已弃用；已迁移。）输入文件的绝对路径名称（定义为驱动器 + 路径 + 基名称 + 文件扩展名）。 如果项目即输入，则此宏等同于 **$(ProjectPath)**。|  
|**$ （inputname)**|（已弃用；已迁移。）输入文件的基名称。 如果项目即输入，则此宏等同于 **$(ProjectName)**。|  
|**$ （inputfilename)**|（已弃用；已迁移。）输入文件的文件名称（定义为基名称 + 文件扩展名）。 如果项目即输入，则此宏等同于 **$(ProjectFileName)**。|  
|**$ （inputext)**|（已弃用；已迁移。）输入文件的文件扩展名。 文件扩展名之前包括“.”。 如果项目即输入，则此宏等同于 **$(ProjectExt)**。|  
|**$(ProjectDir)**|（定义为驱动器 + 路径）; 项目的目录包括尾随反斜杠\\。|  
|**$(ProjectPath)**|项目的绝对路径名称（定义为驱动器 + 路径 + 基名称 + 文件扩展名）。|  
|**$(ProjectName)**|项目的基名称。|  
|**$(ProjectFileName)**|项目的文件名称（定义为基名称 + 文件扩展名）。|  
|**$(ProjectExt)**|项目的文件扩展名。 文件扩展名之前包括“.”。|  
|**$ （solutiondir)**|（定义为驱动器 + 路径）; 解决方案的目录包括尾随反斜杠\\。 定义仅在 IDE 中生成解决方案时。|  
|**$ （solutionpath)**|解决方案的绝对路径名称（定义为驱动器 + 路径 + 基名称 + 文件扩展名）。 定义仅在 IDE 中生成解决方案时。|  
|**$ （solutionname)**|解决方案的基名称。 定义仅在 IDE 中生成解决方案时。|  
|**$ （solutionfilename)**|解决方案的文件名称（定义为基名称 + 文件扩展名）。 定义仅在 IDE 中生成解决方案时。|  
|**$ （solutionext)**|解决方案的文件扩展名。 文件扩展名之前包括“.”。 定义仅在 IDE 中生成解决方案时。|  
|**$ （targetdir)**|（定义为驱动器 + 路径）; 生成的主输出文件的目录包括尾随反斜杠\\。|  
|**$ （targetpath)**|生成的主输出文件的绝对路径名称（定义为驱动器 + 路径 + 基名称 + 文件扩展名）。|  
|**$ （targetname)**|生成的主输出文件的基名称。|  
|**$ （targetfilename)**|生成的主输出文件的文件名称（定义为基名称 + 文件扩展名）。|  
|**$ （targetext)**|生成的主输出文件的文件扩展名。 文件扩展名之前包括“.”。|  
|**$(VSInstallDir)**|在其中安装了 Visual Studio 的目录。<br /><br /> 此属性包含目标 Visual Studio 版本，它可能与主机 Visual Studio 不同。 例如，当使用 `$(PlatformToolset) = v110`进行生成时， **$(VSInstallDir)** 包含 Visual Studio 2012 安装的路径。|  
|**$(VCInstallDir)**|在其中安装了 Visual C++ 的目录。<br /><br /> 此属性包含目标 Visual C++ 版本，它可能与主机 Visual Studio 不同。 例如，当生成`$(PlatformToolset) = v140`， **$ （vcinstalldir)**包含 Visual c + + 2015年安装的路径。|  
|**$(FrameworkDir)**|在其中安装了 .NET Framework 的目录。|  
|**$ （frameworkversion)**|Visual Studio 使用的.NET framework 版本。 结合 **$(FrameworkDir)**，Visual Studio 使用的.NET Framework 版本的完整路径。|  
|**$ （frameworksdkdir)**|在其中安装了 .NET Framework 的目录。 .NET Framework 可能已作为 Visual Studio 的一部分安装或单独安装。|  
|**$ （webdeploypath)**|从 Web 部署根到项目输出位置的相对路径。 返回与 <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A>相同的值。|  
|**$ （webdeployroot)**|位置的绝对路径 **\<localhost >**。 例如，c:\inetpub\wwwroot。|  
|**$(SafeParentName)**|（已弃用。）有效名称格式中直接父级的名称。 例如，窗体是 .resx 文件的父级。|  
|**$(SafeInputName)**|（已弃用。）作为有效类名称的文件名，去掉文件扩展名。|  
|**$ （saferootnamespace)**|（已弃用。）项目向导将在其中添加代码的命名空间名。 此命名空间名将仅包含有效的 C++ 标识符中允许的字符。|  
|**$ （fxcopdir)**|fxcop.cmd 文件的路径。 fxcop.cmd 文件不随所有 Visual C++ 版本安装。|  
  
## <a name="see-also"></a>请参阅  
 [在 Visual Studio 中生成 C++ 项目](../ide/building-cpp-projects-in-visual-studio.md)