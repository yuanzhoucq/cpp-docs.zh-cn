---
title: MSBuild 命令和属性的常见宏
ms.date: 08/02/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
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
- $(PlatformShortName) macro
- SolutionPath macro $(SolutionPath)
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
ms.openlocfilehash: e2c7fe6f2ea63f2cbd259e4114843fcfc28fcd84
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988324"
---
# <a name="common-macros-for-msbuild-commands-and-properties"></a>MSBuild 命令和属性的常见宏

根据您的安装选项，Visual Studio 可以在 Visual Studio 项目中提供数以百计的宏（基于 MSBuild）。 它们分别对应于默认设置的 MSBuild 属性，或在属性或 .targets 文件中，或者在项目设置中。 你可以在项目“属性页” 对话框中接受字符串的任意位置使用这些宏。 这些宏不区分大小写。

## <a name="view-the-current-properties-and-macros"></a>查看当前属性和宏

若要显示所有当前可用的宏，请在 "**属性页**" 对话框的 " **VC + + 目录**" 下，选择属性行末尾的下拉箭头。 单击 "**编辑**"，然后在 "编辑" 对话框中，选择 "**宏**" 按钮。 对 Visual Studio 可见的当前属性和宏集，连同每个属性和宏的当前值一起列出。 有关详细信息，请参阅[ C++项目属性页引用](property-pages-visual-cpp.md)的**指定用户定义的值**部分。

!["VC + + 宏" 按钮](../media/vcppdir_libdir_macros.png "宏菜单")

## <a name="list-of-common-macros"></a>常见宏列表

下表介绍了可用宏的常用子集;这里有很多未列出的内容。 请访问 "**宏**" 对话框，查看项目中的所有属性及其当前值。 有关如何创建 MSBuild 属性定义以及如何在 .props、.targets 和 .vcxproj 文件中将其用作宏的详细信息，请参阅 [MSBuild 属性](/visualstudio/msbuild/msbuild-properties)。

|宏|描述|
|-----------|-----------------|
|**$(Configuration)**|当前项目配置的名称，例如，“调试”。|
|**$(DevEnvDir)**|Visual Studio 的安装目录（定义为驱动器 + 路径）；包括尾随反斜杠“\\”。|
|**$(FrameworkDir)**|在其中安装了 .NET Framework 的目录。|
|**$(FrameworkSDKDir)**|在其中安装了 .NET Framework 的目录。 .NET Framework 可能已作为 Visual Studio 的一部分安装或单独安装。|
|**$(FrameworkVersion)**|Visual Studio 使用的.NET framework 版本。 结合 **$(FrameworkDir)** ，Visual Studio 使用的.NET Framework 版本的完整路径。|
|**$(FxCopDir)**|fxcop.cmd 文件的路径。 Fxcop .cmd 文件未随所有 Visual Studio 版本一起安装。|
|**$(IntDir)**|为中间文件指定的目录路径。 如果它是相对路径，则中间文件会将此路径追加到项目目录。 此路径应具有尾随斜杠。 它解析为**中间目录**属性的值。 请勿使用 **$ （OutDir）** 定义此属性。|
|**$(OutDir)**|输出文件目录的路径。 如果它是相对路径，则输出文件将跳到该路径追加到项目目录。 此路径应具有尾随斜杠。 它解析为 "**输出目录**" 属性的值。 请勿使用 **$ （IntDir）** 定义此属性。|
|**$(Platform)**|当前项目平台的名称（例如“Win32”）。|
|**$ （PlatformShortName）**|当前体系结构的短名称，例如 "x86" 或 "x64"。|
|**$(ProjectDir)**|项目的目录（定义为驱动器 + 路径）；包括尾随反斜杠“\\”。|
|**$(ProjectExt)**|项目的文件扩展名。 文件扩展名之前包括“.”。|
|**$(ProjectFileName)**|项目的文件名称（定义为基名称 + 文件扩展名）。|
|**$(ProjectName)**|项目的基名称。|
|**$(ProjectPath)**|项目的绝对路径名称（定义为驱动器 + 路径 + 基名称 + 文件扩展名）。|
|**$ （PublishDir）**|发布目标的输出位置;包括尾随反斜杠 "\\"。 默认为 **$ （OutDir）应用。发布\\** 文件夹。|
|**$(RemoteMachine)**|设置为“调试”属性页上 **Remote Machine** 属性的值。 有关详细信息，请参阅 [更改 C/C++ 调试配置的项目设置](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) 。|
|**$(RootNameSpace)**|包含应用程序的命名空间（如果存在）。|
|**$(SolutionDir)**|解决方案的目录（定义为驱动器 + 路径）；包括尾随反斜杠“\\”。 仅当在 IDE 中生成解决方案时定义。|
|**$(SolutionExt)**|解决方案的文件扩展名。 文件扩展名之前包括“.”。 仅当在 IDE 中生成解决方案时定义。|
|**$(SolutionFileName)**|解决方案的文件名称（定义为基名称 + 文件扩展名）。 仅当在 IDE 中生成解决方案时定义。|
|**$(SolutionName)**|解决方案的基名称。 仅当在 IDE 中生成解决方案时定义。|
|**$(SolutionPath)**|解决方案的绝对路径名称（定义为驱动器 + 路径 + 基名称 + 文件扩展名）。 仅当在 IDE 中生成解决方案时定义。|
|**$(TargetDir)**|生成的主输出文件的目录（定义为驱动器 + 路径）；包括尾随反斜杠 “\\”。|
|**$(TargetExt)**|生成的主输出文件的文件扩展名。 文件扩展名之前包括“.”。|
|**$(TargetFileName)**|生成的主输出文件的文件名称（定义为基名称 + 文件扩展名）。|
|**$(TargetName)**|生成的主输出文件的基名称。|
|**$(TargetPath)**|生成的主输出文件的绝对路径名称（定义为驱动器 + 路径 + 基名称 + 文件扩展名）。|
|**$(VCInstallDir)**|包含 Visual Studio 安装的 C++ 内容的目录。 此属性包含目标 Microsoft C++ （MSVC）工具集的版本，它可能与主机 Visual Studio 不同。 例如，在 `$(PlatformToolset) = v140`生成时， **$ （VCInstallDir）** 包含 Visual Studio 2015 安装的路径。|
|**$(VSInstallDir)**|在其中安装了 Visual Studio 的目录。 此属性包含目标 Visual Studio 工具集的版本，它可能与主机 Visual Studio 不同。 例如，当使用 `$(PlatformToolset) = v110`进行生成时， **$(VSInstallDir)** 包含 Visual Studio 2012 安装的路径。|
|**$(WebDeployPath)**|从 Web 部署根到项目输出位置的相对路径。|
|**$(WebDeployRoot)**|\<localhost> 的位置的绝对路径。 例如，c:\inetpub\wwwroot。|

## <a name="obsolete-macros"></a>弃用的宏

Visual Studio 2008 和 Visual Studio 2010 之间的 C++ 生成系统已显著更改。 早期项目类型中使用的许多宏已更改为新的宏。 这些宏已不再使用，或者被一个或多个等效属性或[项目元数据宏](/visualstudio/msbuild/itemmetadata-element-msbuild) (%(name)) 值替换。 项目迁移工具可以更新标记为“已迁移”的宏。 如果包含宏的项目从 Visual Studio 2008 或更旧版本迁移到了 Visual Studio 2010，则 Visual Studio 会将宏转换为等效的当前宏。 更高版本的 Visual Studio 无法将 Visual Studio 2008 和更低版本中的项目转换为新的项目类型。 转换这些项目必须执行两步操作；首先将这些项目转换为 Visual Studio 2010，然后将结果转换为更新版本的 Visual Studio。 有关详细信息，请参阅[潜在的升级问题概述](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md)。

|宏|描述|
|-----------|-----------------|
|**$(InputDir)**|（已迁移。）输入文件的目录（定义为驱动器 + 路径）;包括尾随反斜杠 "\\"。 如果项目即输入，则此宏等同于 **$(ProjectDir)** 。|
|**$(InputExt)**|（已迁移。）输入文件的文件扩展名。 文件扩展名之前包括“.”。 如果项目即输入，则此宏等同于 **$(ProjectExt)** 。 对于源文件，此为“%(Extension)”。|
|**$(InputFileName)**|（已迁移。）输入文件的文件名（定义为基名称 + 文件扩展名）。 如果项目即输入，则此宏等同于 **$(ProjectFileName)** 。 对于源文件，此为“%(Identity)”。|
|**$(InputName)**|（已迁移。）输入文件的基名称。 如果项目即输入，则此宏等同于 **$(ProjectName)** 。 对于源文件，此为“%(Filename)”。|
|**$(InputPath)**|（已迁移。）输入文件的绝对路径名称（定义为驱动器 + 路径 + 基名称 + 文件扩展名）。 如果项目即输入，则此宏等同于 **$(ProjectPath)** 。 对于源文件，此为“%(FullPath)”。|
|**$(ParentName)**|包含此项目项的项的名称。 这将是父文件夹的名称或项目名称。|
|**$(SafeInputName)**|作为有效类名称的文件名，去掉文件扩展名。 此属性没有确切的等效项。|
|**$(SafeParentName)**|有效名称格式中直接父级的名称。 例如，窗体是 .resx 文件的父级。 此属性没有确切的等效项。|
|**$(SafeRootNamespace)**|项目向导将在其中添加代码的命名空间名。 此命名空间名将仅包含有效的 C++ 标识符中允许的字符。 此属性没有确切的等效项。|

## <a name="see-also"></a>另请参阅

[Visual Studio 项目- C++ ](../creating-and-managing-visual-cpp-projects.md)\
[Visual C++移植和升级指南](../../porting/visual-cpp-porting-and-upgrading-guide.md)\
[潜在的升级问题概述](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md)
