---
title: 用于生成命令和属性的常用宏 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b94347e48a7b8b134915456c92aea3397f97a1b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339626"
---
# <a name="common-macros-for-build-commands-and-properties"></a>用于生成命令和属性的常用宏
根据你的安装选项，Visual Studio 可以为你提供数百个宏。 这些宏对应于默认设置的，或者在 .props 或 .targets 文件中，或者在项目设置中设置的 MSBuild 属性。 你可以在项目“属性页”  对话框中接受字符串的任意位置使用这些宏。 这些宏不区分大小写。  
  
 若要显示当前可用的宏，请在属性名称右侧列中单击下拉箭头。 如果“编辑”  可用，请单击它，然后在“编辑”对话框中单击“宏” 。 有关详细信息，请参阅[属性页](../ide/property-pages-visual-cpp.md)中“指定用户定义的值”部分。  
  
 标记为“已弃用”的宏不再使用，或已由等效的[项元数据宏](/visualstudio/msbuild/itemmetadata-element-msbuild)（%(name)）所替代****。 标记为“已弃用；已迁移”的宏也已弃用。 此外，如果包含宏的项目迁移自 Visual Studio 2008，则 Visual Studio 会将宏转换为等效的当前宏。  
  
 下表介绍了可用宏的常用子集。 此列表并不详尽。 有关如何创建 MSBuild 属性定义以及如何在 .props、.targets 和 .vcxproj 文件中将其用作宏的详细信息，请参阅 [MSBuild 属性](/visualstudio/msbuild/msbuild-properties)。  
  
|宏|描述|  
|-----------|-----------------|  
|**$(RemoteMachine)**|设置为“调试”属性页上 **Remote Machine** 属性的值。 有关详细信息，请参阅 [更改 C/C++ 调试配置的项目设置](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) 。|  
|**$(Configuration)**|当前项目配置的名称，例如，“调试”。|  
|**$(Platform)**|当前项目平台的名称（例如“Win32”）。|  
|**$(ParentName)**|（已弃用。）包含此项目项的项的名称。 这将是父文件夹的名称或项目名称。|  
|**$(RootNameSpace)**|包含应用程序的命名空间（如果存在）。|  
|**$(IntDir)**|为中间文件指定的目录路径。 如果这是一个相对路径，则中间文件将转到追加到项目目录的此路径。 此路径应具有尾随斜杠。 这将解析为 **Intermediate Directory** 属性的值。 请勿使用 **$(OutDir)** 定义此属性。|  
|**$(OutDir)**|输出文件目录的路径。 如果这是一个相对路径，则输出文件将转到追加到项目目录中的此路径。 此路径应具有尾随斜杠。 这将解析为 **Output Directory** 属性的值。 请勿使用 **$(IntDir)** 定义此属性。|  
|**$(DevEnvDir)**|Visual Studio 的安装目录（定义为驱动器 + 路径）；包括尾随反斜杠“\\”。|  
|**$(InputDir)**|（已弃用；已迁移。）输入文件的目录（定义为驱动器 + 路径）；包括尾随反斜杠“\\”。 如果项目即输入，则此宏等同于 **$(ProjectDir)**。|  
|**$(InputPath)**|（已弃用；已迁移。）输入文件的绝对路径名称（定义为驱动器 + 路径 + 基名称 + 文件扩展名）。 如果项目即输入，则此宏等同于 **$(ProjectPath)**。|  
|**$(InputName)**|（已弃用；已迁移。）输入文件的基名称。 如果项目即输入，则此宏等同于 **$(ProjectName)**。|  
|**$(InputFileName)**|（已弃用；已迁移。）输入文件的文件名称（定义为基名称 + 文件扩展名）。 如果项目即输入，则此宏等同于 **$(ProjectFileName)**。|  
|**$(InputExt)**|（已弃用；已迁移。）输入文件的文件扩展名。 文件扩展名之前包括“.”。 如果项目即输入，则此宏等同于 **$(ProjectExt)**。|  
|**$(ProjectDir)**|项目的目录（定义为驱动器 + 路径）；包括尾随反斜杠“\\”。|  
|**$(ProjectPath)**|项目的绝对路径名称（定义为驱动器 + 路径 + 基名称 + 文件扩展名）。|  
|**$(ProjectName)**|项目的基名称。|  
|**$(ProjectFileName)**|项目的文件名称（定义为基名称 + 文件扩展名）。|  
|**$(ProjectExt)**|项目的文件扩展名。 文件扩展名之前包括“.”。|  
|**$(SolutionDir)**|解决方案的目录（定义为驱动器 + 路径）；包括尾随反斜杠“\\”。 仅当在 IDE 中生成解决方案时定义。|  
|**$(SolutionPath)**|解决方案的绝对路径名称（定义为驱动器 + 路径 + 基名称 + 文件扩展名）。 仅当在 IDE 中生成解决方案时定义。|  
|**$(SolutionName)**|解决方案的基名称。 仅当在 IDE 中生成解决方案时定义。|  
|**$(SolutionFileName)**|解决方案的文件名称（定义为基名称 + 文件扩展名）。 仅当在 IDE 中生成解决方案时定义。|  
|**$(SolutionExt)**|解决方案的文件扩展名。 文件扩展名之前包括“.”。 仅当在 IDE 中生成解决方案时定义。|  
|**$(TargetDir)**|生成的主输出文件的目录（定义为驱动器 + 路径）；包括尾随反斜杠 “\\”。|  
|**$(TargetPath)**|生成的主输出文件的绝对路径名称（定义为驱动器 + 路径 + 基名称 + 文件扩展名）。|  
|**$(TargetName)**|生成的主输出文件的基名称。|  
|**$(TargetFileName)**|生成的主输出文件的文件名称（定义为基名称 + 文件扩展名）。|  
|**$(TargetExt)**|生成的主输出文件的文件扩展名。 文件扩展名之前包括“.”。|  
|**$(VSInstallDir)**|在其中安装了 Visual Studio 的目录。<br /><br /> 此属性包含目标 Visual Studio 版本，它可能与主机 Visual Studio 不同。 例如，当使用 `$(PlatformToolset) = v110`进行生成时， **$(VSInstallDir)** 包含 Visual Studio 2012 安装的路径。|  
|**$(VCInstallDir)**|在其中安装了 Visual C++ 的目录。<br /><br /> 此属性包含目标 Visual C++ 版本，它可能与主机 Visual Studio 不同。 例如，当使用 `$(PlatformToolset) = v140` 进行生成时，$(VCInstallDir) 包含 Visual C++ 2015 安装的路径。|  
|**$(FrameworkDir)**|在其中安装了 .NET Framework 的目录。|  
|**$(FrameworkVersion)**|Visual Studio 使用的.NET framework 版本。 结合 **$(FrameworkDir)**，Visual Studio 使用的.NET Framework 版本的完整路径。|  
|**$(FrameworkSDKDir)**|在其中安装了 .NET Framework 的目录。 .NET Framework 可能已作为 Visual Studio 的一部分安装或单独安装。|  
|**$(WebDeployPath)**|从 Web 部署根到项目输出位置的相对路径。 返回与 <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A>相同的值。|  
|**$(WebDeployRoot)**|\<localhost> 的位置的绝对路径。 例如，c:\inetpub\wwwroot。|  
|**$(SafeParentName)**|（已弃用。）有效名称格式中直接父级的名称。 例如，窗体是 .resx 文件的父级。|  
|**$(SafeInputName)**|（已弃用。）作为有效类名称的文件名，去掉文件扩展名。|  
|**$(SafeRootNamespace)**|（已弃用。）项目向导将在其中添加代码的命名空间名。 此命名空间名将仅包含有效的 C++ 标识符中允许的字符。|  
|**$(FxCopDir)**|fxcop.cmd 文件的路径。 fxcop.cmd 文件不随所有 Visual C++ 版本安装。|  
  
## <a name="see-also"></a>请参阅  
 [在 Visual Studio 中生成 C++ 项目](../ide/building-cpp-projects-in-visual-studio.md)