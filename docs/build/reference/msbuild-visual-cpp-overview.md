---
title: Visual Studio 中的 C++ 项目的 MSBuild 内部项
ms.date: 05/16/2019
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
ms.openlocfilehash: b3348320a1468fea03f39e43cc847f1085f3d319
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837230"
---
# <a name="msbuild-internals-for-c-projects"></a>C++ 项目的 MSBuild 内部项

如果在 IDE 中设置项目属性并保存项目，则 Visual Studio 会将项目设置写入项目文件。 项目文件包含项目独有的设置，但是不包含生成项目所需的所有设置。 项目文件包含 `Import` 元素，该元素包括由其他支持文件形成的网络。 这些支持文件包含生成项目所需的其余属性、目标和设置。

支持文件中的大部分目标和属性只用于实现生成系统。 以下部分讨论一些有用的目标和属性，可在 MSBuild 命令行上指定。 若要了解更多目标和属性，请浏览支持文件目录中的文件。

## <a name="support-file-directories"></a>支持文件目录

默认情况下，主要的 Visual Studio 支持文件位于以下目录中。 Visual Studio 2017 和更高版本使用 Microsoft Visual Studio 下的目录，而 Visual Studio 2015 和更早的版本则使用 MSBuild 下的目录。

|目录|说明|
|---------------|-----------------|
|*drive*:\Program Files *(x86)* \Microsoft Visual Studio\\*year*\\*edition*\Common7\IDE\VC\VCTargets\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp (x86)\v4.0\\*version*\ |包含目标使用的主要目标文件 (.targets) 和属性文件 (.props)。 默认情况下，$(VCTargetsPath) 宏引用此目录。|
|*drive*:\Program Files *(x86)* \Microsoft Visual Studio\\*year*\\*edition*\Common7\IDE\VC\VCTargets\Platforms\\*platform*\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*version*\Platforms\\*platform*\ |包含特定于平台的目标文件和属性文件，这些文件会覆盖其父目录中的目标和属性。 此目录还包含定义此目录中的目标所使用的任务的 DLL。<br /><br /> “platform”占位符表示 ARM、Win32 或 x64 子目录。|
|*drive*:\Program Files *(x86)* \Microsoft Visual Studio\\*year*\\*edition*\Common7\IDE\VC\VCTargets\Platforms\\*platform*\PlatformToolsets\\*toolset*\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*version*\Platforms\\*platform*\PlatformToolsets\\*toolset*\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*platform*\PlatformToolsets\\*toolset*\ |包含让生成可通过使用指定工具集生成 C++ 应用程序的目录。<br /><br /> “year”和“edition”占位符由 Visual Studio 2017 和更高版本使用。 “version”占位符对于 Visual Studio 2012 是 V110，对于 Visual Studio 2013 是 V120，对于 Visual Studio 2015 是 V140，对于 Visual Studio 2017 是 V141，对于 Visual Studio 2019 是 V142。 “platform”占位符表示 ARM、Win32 或 x64 子目录。 “toolset”占位符表示工具集子目录，例如，对于使用 Visual Studio 2015 工具集的 Windows 应用生成是 v140，对于使用 Visual Studio 2013 工具集的 Windows XP 生成则为 v120_xp。<br /><br />包含用于生成 Visual Studio 2008 或 Visual Studio 2010 应用程序的目录的路径不包括表示 Itanium、Win32 或 x64 子目录的“version”和“platform”占位符。 “toolset”占位符表示 v90 或 v100 工具集子目录。|

## <a name="support-files"></a>支持文件

支持文件目录包含带有以下扩展名的文件：

|扩展名|说明|
|---------------|-----------------|
|.targets|包含指定由目标执行的任务的 `Target` XML 元素。 可能还包含 `PropertyGroup`、`ItemGroup`、`ItemDefinitionGroup` 和用户定义的 `Item` 元素，这些元素用于将文件和命令行选项分配给任务参数。<br /><br /> 有关详细信息，请参阅 [Target 元素 (MSBuild)](/visualstudio/msbuild/target-element-msbuild)。|
|.props|包含 `Property Group` 和用户定义的 `Property` XML 元素，这些元素指定在生成过程中使用的文件和参数设置。<br /><br /> 还可能包含 `ItemDefinitionGroup` 和用户定义的 `Item` XML 元素，这些元素指定其他设置。 在项定义组中定义的项类似于属性，但是无法从命令行访问。 Visual Studio 项目文件经常使用项（而不是属性）来表示设置。<br /><br /> 有关详细信息，请参阅 [ItemGroup 元素 (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild)、 
[ItemDefinitionGroup 元素 (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild) 和 [Item 元素 (MSBuild)](/visualstudio/msbuild/item-element-msbuild)。|
|.xml|包含声明和初始化 IDE 用户界面元素的 XML 元素，例如属性表和属性页以及文本框和列表框控件。<br /><br /> .xml 文件直接支持 IDE，而不是 MSBuild。 不过 IDE 属性的值分配给生成属性和项。<br /><br /> 大多数 .xml 文件都位于特定于区域设置的子目录中。 例如 English-US 区域的文件就位于 $(VCTargetsPath)\1033\\。|

## <a name="user-targets-and-properties"></a>用户目标和属性

若要在命令行上最有效地使用 MSBuild，最好了解哪些属性和目标是有用且相关的。 大多数属性和目标在实现 Visual Studio 生成系统方面都有所帮助，所以与用户不相关。 本部分介绍一些有价值的、面向用户的属性和目标。

### <a name="platformtoolset-property"></a>PlatformToolset 属性

`PlatformToolset` 属性确定生成中使用的 MSVC 工具集。 默认使用当前工具集。 如果设置此属性，此属性的值会与文本字符串连接，构成包含针对特定平台生成项目所需的属性和目标文件的目录的路径。 若要使用某个平台工具集版本进行生成，则必须安装该平台工具集。

例如，将 `PlatformToolset` 属性设为 `v140`，以使用 Visual Studio 2015 工具和库来生成应用程序：

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>PreferredToolArchitecture 属性

`PreferredToolArchitecture` 属性确定在生成中是使用 32 位还是 64 位编译器和工具。 此属性不会影响输出平台体系结构或配置。 默认情况下，MSBuild 使用 x86 版本的编译器和工具（如果未设置此属性）。

例如，将 `PreferredToolArchitecture` 属性设为 `x64`，以使用 64 位编译器和工具来生成应用程序：

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>UseEnv 属性

默认情况下，当前项目的特定于平台的设置会覆盖 PATH、INCLUDE、LIB、LIBPATH、CONFIGURATION 和 PLATFORM 环境变量。 将 `UseEnv` 属性设为“true”，可以保证这些环境变量不被覆盖。

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>目标

Visual Studio 支持文件中有数百个目标。 但是大多数目标都是面向系统的，用户可以忽略。 大多数系统目标都带有下划线 (_) 前缀，或者名称以“PrepareFor”、“Compute”、“Before”、“After”、“Pre”或“Post”开头。

下表列出了一些有用的面向用户的目标。

|Target|说明|
|------------|-----------------|
|BscMake|执行 Microsoft 浏览信息维护实用工具 (bscmake.exe)。|
|生成|生成项目。<br /><br /> 这是项目的默认目标。|
|ClCompile|执行 MSVC 编译器工具 (cl.exe)。|
|清理|删除临时生成文件和中间生成文件。|
|Lib|执行 Microsoft 32 位库管理器工具 (lib.exe)。|
|链接|执行 MSVC 链接器工具 (link.exe)。|
|ManifestResourceCompile|从清单中提取资源列表，然后执行 Microsoft Windows 资源编译器工具 (rc.exe)。|
|Midl|执行 Microsoft 接口定义语言 (MIDL) 编译器工具 (midl.exe)。|
|重新生成|清理然后生成项目。|
|ResourceCompile|执行 Microsoft Windows 资源编译器工具 (rc.exe)。|
|XdcMake|执行 XML 文档工具 (xdcmake.exe)。|
|Xsd|执行 XML 架构定义工具 (Xsd.exe)。 请参见下面的注释。|

> [!NOTE]
> 在 Visual Studio 2017 和更高版本中，已弃用对 xsd 文件的 C++ 项目支持。 仍可通过向 GAC 手动添加 CppCodeProvider.dll 来使用 Microsoft.VisualC.CppCodeProvider。

## <a name="see-also"></a>请参阅

[MSBuild 任务参考](/visualstudio/msbuild/msbuild-task-reference)<br/>
[BscMake 任务](/visualstudio/msbuild/bscmake-task)<br/>
[CL 任务](/visualstudio/msbuild/cl-task)<br/>
[CPPClean 任务](/visualstudio/msbuild/cppclean-task)<br/>
[LIB 任务](/visualstudio/msbuild/lib-task)<br/>
[Link 任务](/visualstudio/msbuild/link-task)<br/>
[MIDL 任务](/visualstudio/msbuild/midl-task)<br/>
[MT 任务](/visualstudio/msbuild/mt-task)<br/>
[RC 任务](/visualstudio/msbuild/rc-task)<br/>
[SetEnv 任务](/visualstudio/msbuild/setenv-task)<br/>
[VCMessage 任务](/visualstudio/msbuild/vcmessage-task)<br/>
[XDCMake 任务](/visualstudio/msbuild/xdcmake-task)<br/>
