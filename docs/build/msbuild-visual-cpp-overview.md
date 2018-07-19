---
title: MSBuild （Visual c + +） 概述 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe3499cdd8f9a9a1cfb91a45e9f039e1b8be2e76
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039084"
---
# <a name="msbuild-visual-c-overview"></a>MSBuild (Visual C++) 概述  
  
MSBuild 是标准生成 Visual c + + 项目系统。 在 Visual Studio 集成的开发环境 (IDE) 中的项目生成时，它使用 msbuild.exe 工具、 一个基于 XML 的项目文件和可选的设置文件。 你可以使用 msbuild.exe 和命令行上的项目文件，但 IDE 将提供一个用户界面，以便可以更轻松地配置设置和生成项目。 本概述介绍 Visual c + + 如何使用 MSBuild 系统。  
  
## <a name="prerequisites"></a>系统必备  
  
阅读有关 MSBuild 的以下文档。  
  
- [MSBuild](/visualstudio/msbuild/msbuild)  
 MSBuild 概念概述。  
  
- [MSBuild 参考](/visualstudio/msbuild/msbuild-reference)  
 有关 MSBuild 系统的参考信息。  
  
- [项目文件架构参考](/visualstudio/msbuild/msbuild-project-file-schema-reference)  
 列出的 MSBuild XML 架构元素，以及其属性和父和子元素。 请特别注意[ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild)， [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild)，[目标](/visualstudio/msbuild/target-element-msbuild)，和[任务](/visualstudio/msbuild/task-element-msbuild)元素。  
  
- [命令行参考](/visualstudio/msbuild/msbuild-command-line-reference)  
 描述的命令行参数和选项，可以将用 msbuild.exe。  
  
- [任务参考](/visualstudio/msbuild/msbuild-task-reference)  
 介绍 MSBuild 任务。 尤其是请注意这些任务，特定于 Visual c + +: [BscMake 任务](/visualstudio/msbuild/bscmake-task)， [CL 任务](/visualstudio/msbuild/cl-task)， [CPPClean 任务](/visualstudio/msbuild/cppclean-task)， [LIB 任务](/visualstudio/msbuild/lib-task)， [链接任务](/visualstudio/msbuild/link-task)， [MIDL 任务](/visualstudio/msbuild/midl-task)， [MT 任务](/visualstudio/msbuild/mt-task)， [RC 任务](/visualstudio/msbuild/rc-task)， [SetEnv 任务](/visualstudio/msbuild/setenv-task)， [VCMessage 任务](/visualstudio/msbuild/vcmessage-task)， [XDCMake 任务](/visualstudio/msbuild/xdcmake-task)， [XSD 任务](/visualstudio/msbuild/xsd-task)。  
  
## <a name="msbuild-on-the-command-line"></a>MSBuild 命令行上  
  
中的以下语句[MSBuild 命令行参考](/visualstudio/msbuild/msbuild-command-line-reference)演示 msbuild.exe 工具，使用隐式或显式*project_file*自变量 （对于 Visual c + + 项目.vcxproj 文件）零个或更多命令行*选项*自变量。  
  
> **msbuild.exe** [ *project_file* ] [*选项*]  
  
使用**target** (或 **/t**) 和 **/property** (或 **/p**) 用于重写特定属性和目标的命令行选项项目文件中指定。  
  
项目文件的基本功能是指定*目标*，即应用于你的项目，并输入和执行该操作所需的输出的特定操作。 项目文件可以指定一个或多个目标，可以包括默认目标。  
  
每个目标包含的一个或多个序列*任务*。 每个任务由包含一个可执行命令的.NET Framework 类表示。 例如， [CL 任务](/visualstudio/msbuild/cl-task)包含[cl.exe](../build/reference/compiling-a-c-cpp-program.md)命令。  
  
A*任务参数*是类任务的属性，通常表示可执行命令的命令行选项。 例如，`FavorSizeOrSpeed`参数`CL`任务对应于 **/Os**和 **/Ot**编译器选项。  
  
其他任务参数支持 MSBuild 基础结构。 例如，`Sources`任务参数指定一组可供其他任务的任务。 有关 MSBuild 任务的详细信息，请参阅[任务参考](/visualstudio/msbuild/msbuild-task-reference)。  
  
大多数任务要求输入和输出，如文件名、 路径和字符串，数字或布尔参数。 例如，常见的输入是要编译的.cpp 源文件的名称。 重要的输入的参数是一个字符串，指定生成配置和平台，例如，"调试\|Win32"。 通过一个或多个用户定义的 XML 指定输入和输出`Item`中所含元素`ItemGroup`元素。  
  
项目文件还可以指定用户定义*属性*和`ItemDefinitionGroup`*项*。 属性和项形成可以用作在生成中的变量的名称/值对。 对的名称组件定义*宏*，并声明的值组件*宏值*。 使用 $ 访问属性宏 (*名称*) 表示法和的项宏可通过 %(*名称*) 表示法。  
  
项目文件中的其他 XML 元素可以测试宏，然后有条件地设置的任何宏的值或控制生成的执行。 宏名称和文字字符串可以串联生成的结构，如的路径和文件名称。 在命令行中， **/property**选项设置或重写项目属性。 项不能引用在命令行上。  
  
之前或之后另一个目标，MSBuild 系统可以有条件地执行一个目标。 此外，系统可以生成基于目标使用的文件是否比它发出的文件较新的目标。  
  
## <a name="msbuild-in-the-ide"></a>在 IDE 的 MSBuild  
  
当你在 IDE 中设置项目属性，，然后保存该项目，Visual c + + 项目设置写入项目文件。 项目文件包含到你的项目，唯一的设置，但它不包含生成你的项目所需的所有设置。 项目文件包含`Import`包括的其他网络元素*支持文件。* 支持文件包含剩余的属性、 目标和生成项目所需的设置。  
  
大多数目标和支持文件中的属性存在只是为了实现生成系统。 以下部分讨论一些有用的目标和可以在 MSBuild 命令行指定的属性。 若要了解更多目标和属性，请浏览支持文件目录中的文件。  
  
### <a name="support-file-directories"></a>支持文件目录  
  
默认情况下，主 Visual c + + 支持文件位于以下目录中。 Microsoft Visual Studio 下的目录使用 Visual Studio 2017 和更高版本，MSBuild 下的目录使用的 Visual Studio 2015 及更早版本。  
  
|目录|描述|  
|---------------|-----------------|  
|*驱动器*: \Program Files *(x86)* \Microsoft Visual Studio\\*年*\\*版本*\Common7\IDE\VC\VCTargets\ <br /><br />*驱动器*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp (x86) \v4.0\\*版本*\ |包含主目标文件 (.targets) 和目标使用的属性文件 (.props)。 默认情况下，$(VCTargetsPath) 宏引用此目录。|  
|*驱动器*: \Program Files *(x86)* \Microsoft Visual Studio\\*年*\\*版本*\Common7\IDE\VC\VCTargets\平台\\*平台*\ <br /><br />*驱动器*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*版本*\Platforms\\*平台*\ |包含重写目标和在其父目录中的属性的特定于平台的目标和属性文件。 此目录还包含一个 DLL，它定义在此目录中的目标使用的任务。<br /><br /> *平台*占位符表示 ARM、 Win32、 或 x64 子目录。|  
|*驱动器*: \Program Files *(x86)* \Microsoft Visual Studio\\*年*\\*版本*\Common7\IDE\VC\VCTargets\平台\\*平台*\PlatformToolsets\\*工具集*\ <br /><br />*驱动器*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*版本*\Platforms\\*平台*\PlatformToolsets\\*工具集*\ <br /><br />*驱动器*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*平台*\PlatformToolsets\\*工具集*\ |包含启用生成要通过使用指定生成 Visual c + + 应用程序的目录*工具集*。<br /><br /> *年*和*版本*占位符由 Visual Studio 2017 和更高版本。 *版本*占位符为 Visual Studio 2012 的 V110、 V120 对于 Visual Studio 2013 或 Visual Studio 2015 的 V140。 *平台*占位符表示 ARM、 Win32、 或 x64 子目录。 *工具集*占位符表示的工具集子目录，例如，v140 构建 Windows 应用程序通过使用 Visual Studio 2015 工具集，v120_xp 生成适用于使用 Visual Studio 2013 工具集或到 v110_wp80 的 Windows XP通过使用 Visual Studio 2012 工具集生成 Windows Phone 8.0 应用。<br /><br />包含启用生成以生成 Visual c + + 2008年或 Visual c + + 2010年应用程序的目录的路径不包括*版本*，和*平台*占位符表示Itanium、 Win32、 或 x64 子目录。 *工具集*占位符表示 v90 或 v100 工具集子目录。|  
  
### <a name="support-files"></a>支持文件  
  
支持文件目录包含具有这些扩展名的文件：  
  
|扩展名|描述|  
|---------------|-----------------|  
|.targets|包含`Target`指定目标执行的任务的 XML 元素。 可能还包含`PropertyGroup`， `ItemGroup`， `ItemDefinitionGroup`，以及用户定义`Item`用于将文件和命令行选项分配给任务参数的元素。<br /><br /> 有关详细信息，请参阅[Target 元素 (MSBuild)](/visualstudio/msbuild/target-element-msbuild)。|  
|.props|包含`Property Group`和用户定义`Property`指定在生成期间使用的文件和参数设置的 XML 元素。<br /><br /> 可能还包含`ItemDefinitionGroup`和用户定义`Item`指定其他设置的 XML 元素。 项定义组中定义的项类似于属性，但不能从命令行访问。 Visual c + + 项目文件频繁地使用项而不是属性表示设置。<br /><br /> 有关详细信息，请参阅[ItemGroup 元素 (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild)， [ItemDefinitionGroup 元素 (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild)，和[Item 元素 (MSBuild)](/visualstudio/msbuild/item-element-msbuild)。|  
|.xml|包含声明和初始化 IDE 用户界面元素 （例如属性表和属性页和文本和列表框控件的 XML 元素。<br /><br /> .Xml 文件直接支持 IDE，不 MSBuild。 但是，分配的 IDE 属性的值生成属性和项。<br /><br /> 大多数的.xml 文件是特定于区域设置子目录中。 例如，英语-美国区域的文件位于 $(VCTargetsPath) \1033\\。|  
  
## <a name="user-targets-and-properties"></a>用户目标和属性  
  
若要在命令行上最有效地使用 MSBuild，它有助于了解哪些属性和目标是有用且相关。 大多数属性和目标帮助实施 Visual c + + 生成系统，并因此不与用户相关。 本部分介绍一些值得面向用户的属性和目标。  

### <a name="platformtoolset-property"></a>PlatformToolset 属性  
  
`PlatformToolset`属性确定在生成中使用的 Visual c + + 工具集。 默认情况下，使用当前的工具集。 当设置此属性时，与字符串组合成包含生成用于特定平台的项目所需的属性和目标文件的目录的路径连接属性的值。 必须安装的平台工具集为使用该平台工具集版本生成。  
  
例如，设置`PlatformToolset`属性`v140`若要使用 Visual c + + 2015年工具和库构建你的应用程序：  
  
`msbuild myProject.vcxproj /p:PlatformToolset=v140`  
  
### <a name="preferredtoolarchitecture-property"></a>PreferredToolArchitecture 属性  
  
`PreferredToolArchitecture`属性确定是否在生成中使用的 32 位或 64 位编译器和工具。 此属性不影响输出平台体系结构或配置。 默认情况下，MSBuild 使用 x86 版本的编译器和工具，如果未设置此属性。  
  
例如，设置`PreferredToolArchitecture`属性`x64`以使用 64 位编译器和工具来生成应用程序：  
  
`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### <a name="useenv-property"></a>UseEnv 属性  
  
默认情况下，当前项目的特定于平台的设置重写路径、 INCLUDE、 LIB、 LIBPATH、 配置和平台环境变量。 设置`UseEnv`属性`true`若要确保环境变量不重写。  
  
`msbuild myProject.vcxproj /p:UseEnv=true`  
  
### <a name="targets"></a>目标  
  
有成百上千的 Visual c + + 支持文件中的目标。 但是，大多数是用户可以忽略的面向系统的目标。 大多数系统目标前缀是下划线 (_)，或具有以"PrepareFor"，"计算"、"之前"，"After"，"前"或"发布"开头的名称。  
  
下表列出了多个有用的面向用户的目标。  
  
|目标|描述|  
|------------|-----------------|  
|BscMake|执行 Microsoft 浏览信息维护实用工具的工具，bscmake.exe。|  
|生成|生成项目。<br /><br /> 这是项目的默认目标。|  
|ClCompile|执行 Visual c + + 编译器工具，cl.exe。|  
|清理|删除临时和中间生成文件。|  
|Lib|执行 Microsoft 32 位库管理器工具中，lib.exe。|  
|链接|执行 Visual c + + 链接器工具，link.exe。|  
|ManifestResourceCompile|从清单提取资源的列表，然后执行 Microsoft Windows 资源编译器工具，rc.exe。|  
|Midl|执行 Microsoft 接口定义语言 (MIDL) 编译器工具，midl.exe。|  
|重新生成|清理，然后生成你的项目。|  
|ResourceCompile|执行 Microsoft Windows 资源编译器工具 rc.exe。|  
|XdcMake|执行 XML 文档工具 xdcmake.exe。|  
|Xsd|执行 XML 架构定义工具中，xsd.exe。 *请参阅下面的说明。*|  

> [!NOTE] 
> 在 Visual Studio 2017，c + + 项目支持**xsd**文件已弃用。 你仍然可以使用**Microsoft.VisualC.CppCodeProvider**通过添加**CppCodeProvider.dll**手动到 GAC。
  
## <a name="see-also"></a>请参阅  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
