---
title: "MSBuild (Visual C++) 概述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "MSBuild 概述"
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# MSBuild (Visual C++) 概述
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MSBuild 是标准生成 Visual c + + 项目系统。 在 Visual Studio 集成的开发环境 (IDE) 中的项目生成时，它使用 msbuild.exe 工具、 基于 XML 的项目文件标识符和可选的设置文件。 虽然您可以使用 msbuild.exe 和命令行上的项目文件，IDE 提供了一个用户界面，以便可以更轻松地配置设置和生成项目。 本概述介绍 Visual c + + 如何使用 MSBuild 系统。  
  
## <a name="prerequisites"></a>先决条件  
 阅读有关 MSBuild 下列文档。  
  
 [MSBuild](MSBuild1.md)  
 MSBuild 概念概述。  
  
 [MSBuild 参考](../Topic/MSBuild%20Reference.md)  
 有关 MSBuild 系统的参考信息。  
  
 [项目文件架构参考](../Topic/MSBuild%20Project%20File%20Schema%20Reference.md)  
 列出的 MSBuild XML 架构元素，以及它们的属性和父元素和子元素。 请特别注意 [ItemGroup](../Topic/ItemGroup%20Element%20\(MSBuild\).md), ，[PropertyGroup](../Topic/PropertyGroup%20Element%20\(MSBuild\).md), ，[目标](../Topic/Target%20Element%20\(MSBuild\).md), ，和 [任务](../Topic/Task%20Element%20\(MSBuild\).md) 元素。  
  
 [命令行参考](../Topic/MSBuild%20Command-Line%20Reference.md)  
 描述的命令行参数和选项，您可以使用 msbuild.exe。  
  
 [任务参考](../Topic/MSBuild%20Task%20Reference.md)  
 介绍 MSBuild 任务。 特别注意这些任务，特定于 Visual c + +: [BscMake 任务](../Topic/BscMake%20Task.md), ，[CL 任务](../Topic/CL%20Task.md), ，[CPPClean 任务](../Topic/CPPClean%20Task.md), ，[LIB 任务](../Topic/LIB%20Task.md), ，[将任务链接](../Topic/Link%20Task.md), ，[MIDL 任务](../Topic/MIDL%20Task.md), ，[MT 任务](../Topic/MT%20Task.md), ，[RC 任务](../Topic/RC%20Task.md), ，[SetEnv 任务](../Topic/SetEnv%20Task.md), ，[VCMessage 任务](../Topic/VCMessage%20Task.md), ，[XDCMake 任务](../Topic/XDCMake%20Task.md), ，[XSD 任务](../Topic/XSD%20Task.md)。  
  
## <a name="msbuild-on-the-command-line"></a>MSBuild 命令行上  
 中的以下语句 [命令行参考](../Topic/MSBuild%20Command-Line%20Reference.md) 文档说明了 msbuild.exe 工具采用隐式或显式 `project file` 参数 （对于 Visual c + + 项目.vcxproj 文件） 和零个或更多命令行 `options`。  
  
 **msbuild.exe [** `project file` **] [** `options` **]**  
  
 使用 **target** (或 **/t**) 和 **/property** (或 **/p**) 命令行选项用于重写属性和项目文件中指定的目标。  
  
 项目文件的基本功能是指定 *目标*, ，即应用于您的项目，并输入和执行该操作所需的输出的特定操作。 项目文件可指定一个或多个目标，它可以包括一个默认目标。  
  
 每个目标包含的一个或多个序列 *任务*。 每个任务由包含一个可执行命令的.NET Framework 类表示。 例如， [CL 任务](../Topic/CL%20Task.md) 包含 [cl.exe](../build/reference/compiling-a-c-cpp-program.md) 命令。  
  
 一个 *任务参数* 是类任务的属性，并且通常表示可执行命令的命令行选项。 例如， `FavorSizeOrSpeed` 参数 `CL` 任务对应于 **/Os** 和 **/Ot** 编译器选项。  
  
 其他任务参数支持的 MSBuild 基础结构。 例如， `Sources` 任务参数指定的一组可供其他任务的任务。 有关 MSBuild 任务的详细信息，请参阅 [任务参考](../Topic/MSBuild%20Task%20Reference.md)。  
  
 大多数任务要求输入和输出，如文件名、 路径和字符串、 数值或布尔参数。 例如，常见的输入是要编译的.cpp 源文件的名称。 重要的输入的参数是一个字符串，指定生成配置和平台，例如，"调试 &#124;Win32"。 输入和输出指定一个或多个用户定义的 xml `Item` 中所含元素 `ItemGroup` 元素。  
  
 项目文件还可以指定用户定义 *属性* 和 *项定义组**项*。 属性和项窗体可以用作在生成中的变量的名称/值对。 一对的名称部分定义 *宏*, ，和值部分声明 *宏值*。 通过使用 $ 访问属性宏 (*名称*) 表示法和项宏可通过 %(*名称*) 表示法。  
  
 项目文件中的其他 XML 元素然后，可以测试宏，并有条件地将任何宏的值设置或控制生成的执行。 宏名称和文字字符串可以是连接起来以生成构造，如路径和文件名的名称。 在命令行 **/property** 选项设置或重写项目属性。 项不能引用在命令行上。  
  
 MSBuild 系统可以有条件地执行目标之前, 或之后另一个目标。 此外，系统可以生成基于目标使用的文件是否比它发出的文件的目标。  
  
## <a name="msbuild-in-the-ide"></a>在 IDE 中的 MSBuild  
 当你在 IDE 中设置项目属性，然后保存该项目时，Visual c + + 会将项目设置写入你的项目文件。 项目文件包含到项目中，唯一的设置，但它不包含生成您的项目所需的所有设置。 项目文件包含 `Import` 包含的其他网络元素， *支持文件。* 这些支持文件包含其余的属性、 目标和生成该项目所需的设置。  
  
 大多数目标和支持文件中的属性存在只是为了实现生成系统。 下面几节讨论一些有用的目标和可以在 MSBuild 命令行指定的属性。 若要发现多个目标和属性，了解支持的文件目录中的文件。  
  
### <a name="support-file-directories"></a>支持文件目录  
 默认情况下，主 Visual c + + 支持文件位于以下目录中。  
  
|目录|描述|  
|---------------|-----------------|  
|*驱动器*: \Program Files\MSBuild\Microsoft.Cpp\v4.0\\*版本*\|包含主目标文件 (.targets) 和由目标使用的属性文件 (.props)。 默认情况下，$(VCTargetsPath) 宏引用此目录。|  
|*驱动器*: \Program Files\MSBuild\Microsoft.Cpp\v4.0\\*版本*\Platforms\\*平台*\|包含重写其父目录中的属性和目标的特定于平台的目标和属性文件。 此目录还包含.dll 文件中定义此目录中的目标使用的任务。<br /><br />  *平台* 占位符表示 `ARM`, ，`Win32`, ，或 `x64` 子目录。|  
|*驱动器*: \Program Files\MSBuild\Microsoft.Cpp\v4.0\\*版本*\Platforms\\*平台*\PlatformToolsets\\*工具集*\|包含启用生成以生成具有指定的 Visual c + + 应用程序的目录 *版本* 的工具集。<br /><br />  *平台* 占位符表示 `ARM`, ，`Win32`, ，或 `x64` 子目录。  *工具集* 占位符表示用于构建 Windows、 Windows XP 或 Windows Phone 应用程序的工具集的子目录。|  
|*驱动器*: \Program Files\MSBuild\Microsoft.Cpp\v4.0\Platforms\\*平台*\PlatformToolsets\\*工具集*\|包含启用生成以生成 9.0 或 Visual c + + 10.0 的应用程序的目录。<br /><br />  *平台* 占位符表示 `Itanium`, ，`Win32`, ，或 `x64` 子目录。  *工具集* 占位符表示 `v90` 或 `v100` 工具集子目录。|  
  
### <a name="support-files"></a>支持文件  
 支持文件目录包含具有以下扩展名的文件。  
  
|扩展名|描述|  
|---------------|-----------------|  
|.targets|包含 `Target` 指定由目标执行的任务的 XML 元素。 此外可能包含 `Property Group`, ，`Item Group`, ，`Item Definition Group`, ，和用户定义 `Item` 用于将文件和命令行选项分配给任务参数的元素。<br /><br /> 有关详细信息，请参阅 [Target 元素 (MSBuild)](../Topic/Target%20Element%20\(MSBuild\).md)。|  
|由于.props|包含 `Property Group` 和用户定义 `Property` 指定在生成期间使用的文件和参数设置的 XML 元素。<br /><br /> 此外可能包含 `Item Definition Group` 和用户定义 `Item` 指定其他设置的 XML 元素。 项定义组中定义的项类似于属性，但不能从命令行访问。 Visual c + + 项目文件经常使用的项而不是属性表示设置。<br /><br /> 有关详细信息，请参阅 [ItemGroup 元素 (MSBuild)](../Topic/ItemGroup%20Element%20\(MSBuild\).md), ，[ItemDefinitionGroup 元素 (MSBuild)](../Topic/ItemDefinitionGroup%20Element%20\(MSBuild\).md), ，和 [Item 元素 (MSBuild)](../Topic/Item%20Element%20\(MSBuild\).md)。|  
|.xml|包含声明和初始化 IDE 例如属性表和属性页中，以及文本和列表框控件的用户界面元素的 XML 元素。<br /><br /> .Xml 文件直接支持 IDE，不 MSBuild。 但是，分配的 IDE 属性的值以生成属性和项。<br /><br /> 大多数的.xml 文件是特定于区域设置子目录中。 例如，英语-美国地区的文件位于 $(VCTargetsPath) \1033\\。|  
  
## <a name="user-targets-and-properties"></a>用户目标和属性  
 若要在命令行上最有效地使用 MSBuild，最好先了解哪些属性和目标是有用且相关。 大多数属性和目标可以帮助实施 Visual c + + 生成系统，并因此不与用户相关。 本部分介绍一些值得面向用户的属性和目标。  
  
### <a name="platformtoolset-property"></a>PlatformToolset 属性  
  `PlatformToolset` 属性确定在生成中使用的 Visual c + + 工具集。 属性的值与字符串组合成包含生成用于特定平台的项目所需的属性和目标文件的目录路径串联。  
  
 设置 `PlatformToolset` 属性设置为 `v110` 使用 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 工具和库来构建您的应用程序。  
  
 `msbuild myProject.vcxproj /p:PlatformToolset=v110`  
  
 设置 `PlatformToolset` 属性设置为 `v100` 使用 [!INCLUDE[cpp_dev10_long](../build/includes/cpp_dev10_long_md.md)] 工具和库来构建您的应用程序。  
  
 `msbuild myProject.vcxproj /p:PlatformToolset=v100`  
  
 设置 `PlatformToolset` 属性设置为 `v90` 使用 Visual c + + 2008年工具和库来生成你的应用程序。 此属性才有效在计算机上必须已安装的 Visual c + + 2008年工具集。  
  
 `msbuild myProject.vcxproj /p:PlatformToolset=v90`  
  
### <a name="preferredtoolarchitecture-property"></a>PreferredToolArchitecture 属性  
  `PreferredToolArchitecture` 属性确定是否在生成中使用 32 位或 64 位编译器和工具。 此属性不影响输出的平台体系结构或配置。 默认情况下，MSBuild 使用 x86 版本的编译器和工具，如果此属性未设置，或为设置为任何值以外 `x64`。  
  
 设置 `PreferredToolArchitecture` 属性设置为 `x64` 以使用 64 位编译器和工具来生成应用程序。  
  
 `msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### <a name="useenv-property"></a>UseEnv 属性  
 默认情况下，当前项目的特定于平台的设置重写路径、 INCLUDE、 LIB、 LIBPATH、 配置和平台环境变量。 设置 `UseEnv` 属性设置为 `true` 若要确保环境变量不重写。  
  
 `msbuild myProject.vcxproj /p:UseEnv=true`  
  
### <a name="targets"></a>目标  
 有数百个 Visual c + + 支持文件中的目标。 但是，大多数都是用户可忽略的面向系统的目标。 大多数系统目标前缀是下划线 (_)，或具有"PrepareFor"，"计算"，以"Before"，"After"，"之前"或"Post"开头的名称。  
  
 下表列出了几个值得面向用户的目标。  
  
|目标|描述|  
|------------|-----------------|  
|BscMake|执行 Microsoft 浏览信息维护实用工具工具 bscmake.exe。|  
|生成|生成项目。<br /><br /> 这是一个项目的默认目标。|  
|ClCompile|执行 Visual c + + 编译器工具，cl.exe。|  
|清理|删除临时和中间生成文件。|  
|Lib|执行 Microsoft 32 位库管理器工具 lib.exe。|  
|Link|执行 Visual c + + 链接器工具，link.exe。|  
|ManifestResourceCompile|从清单提取资源的列表，然后执行 Microsoft Windows 资源编译器工具 rc.exe。|  
|Midl|执行 Microsoft 接口定义语言 (MIDL) 编译器工具，midl.exe。|  
|重新生成|清理，然后生成您的项目。|  
|ResourceCompile|执行 Microsoft Windows 资源编译器工具 rc.exe。|  
|XdcMake|执行 XML 文档工具 xdcmake.exe。|  
|Xsd|执行 XML 架构定义工具中，xsd.exe。|  
  
## <a name="see-also"></a>另请参阅  
 [MSBuild （Visual c + +）](../build/msbuild-visual-cpp.md)