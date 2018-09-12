---
title: 使用项目属性 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- project properties [C++], modifying
- properties [C++]
- Visual C++ projects, properties
- projects [C++], properties
ms.assetid: 9b0d6f8b-7d4e-4e61-aa75-7d14944816cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9961eaa6529773e8d21d9c953242d1656a6a443
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211658"
---
# <a name="working-with-project-properties"></a>使用项目属性

在 IDE 中，生成项目的需要的全部信息都公开为属性。 此信息包括应用程序名称、扩展名（如 DLL、LIB、EXE）、编译器选项、链接器选项、调试器设置、自定义生成步骤和许多其他操作。 通常情况下，使用属性页（“项目”&#124;“属性”）来查看和修改这些属性。

创建项目时，系统分配各种属性的值。 根据项目类型和在应用向导中所选的选项类型，默认值会有所不同。 例如，ATL 项目具有与 MIDL 文件相关的属性，但这些属性在基本控制台应用程序中都不存在。 默认属性在属性页的“常规”窗格中显示：

![Visual C&#43;&#43;项目默认值](../ide/media/visual-c---project-defaults.png "Visual C++ 项目默认值")

某些属性（例如应用程序名称）适用于所有生成变量，而不考虑目标平台或其为调试版本还是发布版本。 但是大多数属性都依赖于配置。 这是由于编译器必须知道程序将在哪个特定平台上运行，以及使用哪个特定编译器选项以便生成正确的代码。 因此，设置属性时，请务必注意新值应适用于哪个配置和平台。 它应该仅适用于调试 Win32 版本还是也适用于调试 ARM 和调试 x64 版本？ 例如，默认情况下，“优化”属性在版本配置中设为“最大化速度(/O2)”，但在调试配置中禁用。

这样设置属性页是便于随时可以查看并在必要时修改属性值应适用于哪个配置和平台。 下图显示了属性页，该页的顶部列表框中包含配置和平台信息。 在此处设置“优化”属性时，它将仅适用于调试 Win32 版本，这正好是活动配置，如红色箭头所示。

![显示活动配置的 Visual C&#43;&#43;属性页](../ide/media/visual-c---property-pages-showing-active-configuration.png "显示活动配置的 Visual C++ 属性页")

下图显示相同的项目属性页，但该配置已更改为发布。 请注意“优化”属性的不同值。 另请注意，活动配置仍是调试。 可以在此处设置任何配置的属性；它不必处于活动状态。

![显示版本配置的 Visual C&#43;&#43; 属性页](../ide/media/visual-c---property-pages-showing-release-config.png "显示版本配置的 Visual C++ 属性页")

此项目系统本身基于 MSBuild，它定义了任何类型的生成项目的文件格式和规则。 MSBuild 承应生成多个配置和平台的复杂性，但你需要了解一些 MSBuild 的工作原理。 如果想要定义自定义配置，或者创建可共享和导入多个项目的可重用的属性集，这一点尤为重要。

项目属性直接存储在项目文件 (*.vcxproj) 中或项目文件导入的其他 .xml 或 .props 文件（提供有默认值）中。 如前面所示，相同配置的同一属性在不同文件中可能分配有不同值。 生成项目时，MSBuild 引擎以明确定义的顺序评估项目文件和所有导入的文件（如下所述）。 在评估每个文件时，该文件中定义的任何属性值都将覆盖现有值。 未指定的任何值都从之前已评估的文件继承。 因此，使用属性页设置属性时，也请务必注意设置它的位置。 如果在 .props 文件中将属性设置为“X”，但该属性在项目文件中已设为“Y”，然后将在属性设为“Y”的情况下生成项目。 如果在项目项（例如 .cpp 文件）上，相同的属性已设为“Z”，然后 MSBuild 引擎将使用“Z”值。 有关更多信息，请参见本文后面的[属性继承](#bkmkPropertyInheritance)。

## <a name="build-configurations"></a>生成配置

配置只是给定名称的任意一组属性。 Visual Studio 提供“调试”和“发布”配置，并且每个配置都相应地为调试版本和发布版本设置各种属性。 可以使用 Configuration Manager 来定义自定义配置，提供一种简单的方法来组合属性获得特定风格的版本。 属性管理器用于处理属性的高级事项，但我们在此处介绍是因为其有助于属性配置可视化。 可以从“视图”&#124;“属性管理器”或“视图”&#124“其他窗口”&#124;“属性管理器”访问属性管理器，具体取决于设置。 它具有项目中每个配置/平台对的节点。 这些节点的每个节点下都是属性表（.props 文件）的节点，为该配置设置某些特定属性。

![属性管理器](../ide/media/property-manager.png "属性管理器")

如果转到属性页中的“常规”窗格（请参阅以上图示），并将字符集属性设为“未设置”而不是“使用 Unicode”，并单击“确定”，属性管理器将不对当前配置显示“Unicode 支持”属性表，但该表对其他配置仍然存在。

有关属性管理器和属性表的详细信息，请参阅本文后面的[创建可重用的属性配置](#bkmkPropertySheets)。

> [!TIP]
> .user 文件是一项旧功能，我们建议将其删除以便根据配置/平台正确地对属性分组。

## <a name="target-platforms"></a>目标平台

目标平台是指可执行文件将在此之上运行的各种设备和/或操作系统。 可以生成多个平台的项目。 C++ 项目的可用目标平台取决于各种项目；包括但不限于 Win32、x64、ARM、Android 和 iOS。     可能在 Configuration Manager 中看到的 x86 目标平台等同于本机 C++ 项目中的 Win32。 Win32 意味着 32 位的 Windows，而 x64 意味着 64 位的 Windows。 有关这两个平台的详细信息，请参阅[运行 32 位的应用程序](/windows/desktop/WinProg64/running-32-bit-applications)。

可能在 Configuration Manager 中看到的任意 CPU 目标平台值对本机 C++ 项目无影响；而是与 C++/CLI 和其他 .NET 项目类型相关。 有关详细信息，请参阅 [/CLRIMAGETYPE（指定 CLR 映像的类型）](../build/reference/clrimagetype-specify-type-of-clr-image.md)。

## <a name="property-pages"></a>属性页

如上文所述，Visual C++ 项目系统基于 [MSBuild](/visualstudio/msbuild/msbuild-properties)，并且值存储在 XML 项目文件、默认 .props 和 .targets 文件中。 对于 Visual Studio 2015，这些文件位于\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140。 对于 Visual Studio 2017，这些文件位于 \\Program Files (x86)\\Microsoft Visual Studio\\2017\\edition\\Common7\\IDE\\VC\\VCTargets，其中“edition”是已安装的 Visual Studio 版本。 属性也存储在可能想要添加到自己项目的任何自定义 .props 文件中。 我们强烈建议不要手动编辑这些文件，而是使用 IDE 中的属性页来更改所有属性，特别是参与继承的属性，除非你非常了解 MSBuild。

下图显示了 Visual C++ 项目的属性页。 在左窗格中，选中“VC++ 目录”规则，右窗格中即会列出与该规则关联的属性。 遗憾的是，`$(...)` 值称为宏。 这些不是 C/C++ 宏，而是简单的编译时常量。 本文后面的[属性页宏](#bkmkPropertiesVersusMacros)部分中讨论了宏。

![项目属性页](../ide/media/project_property_pages_vc.png "Project_Property_Pages_VC")

> [!WARNING]
> 已删除 Visual Studio 的早期版本中的“通用属性”配置。 若要添加对项目的引用，现在以用于托管语言的相同方式使用“添加引用”对话框。 请参阅[管理项目中的引用](/visualstudio/ide/managing-references-in-a-project)。

#### <a name="to-set-a-property-for-a-project"></a>设置项目属性

1. 大多数情况下，可以在项目级别设置属性无需创建自定义属性表。 在主菜单上选择“项目”&#124;“属性”或右键单击解决方案资源管理器中的项目节点，并选择“属性”。

2. 使用对话框顶部的“配置”和“平台”列表框，指定哪些属性组应该应用更改。 在许多情况下，“所有平台”和“所有配置”是正确的选择。 若要只为某些配置设置属性，请在“属性管理器”中选择多个配置，然后打开快捷菜单并选择“属性”。

“属性页”对话框仅显示适用于当前项目的属性页。 例如，如果该项目没有 .idl 文件则不会显示 MIDL 属性页。

在属性页中突出显示某一属性时，可以按 F1，转到参考主题，详细了解相应编译器或链接器开关。

可以在这些主题中找到有关每个属性页的详细信息：

- [常规属性页（项目）](../ide/general-property-page-project.md)

- [“常规”属性页（文件）](../ide/general-property-page-file.md)

- [“命令行”属性页](../ide/command-line-property-pages.md)

- [C++ 调试配置的项目设置](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)

- [“Nmake”属性页](../ide/nmake-property-page.md)

- [“链接器”属性页](../ide/linker-property-pages.md)

- [“资源”属性页](../ide/resources-property-pages.md)

- [“MIDL”属性页](../ide/midl-property-pages.md)

- [“Web 引用”属性页](../ide/web-references-property-page.md)

- [“XML 数据生成器工具”属性页](../ide/xml-data-generator-tool-property-page.md)

## <a name="to-quickly-browse-and-search-all-properties"></a>快速浏览和搜索所有属性

“所有选项”属性页（在“属性页”对话框中“配置属性”&#124;“C/C++”节点下）可实现快速浏览和搜索当前上下文中可用的属性。 它具有特殊的搜索框和简单的语法，能够帮助你筛选结果：

无前缀：<br/>
仅在属性名称中搜索（不区分大小写的子字符串）。

'/' 或 '-'：<br/>
仅在编译器开关中搜索（不区分大小写的前缀）

v:<br/>
仅在值中搜索（不区分大小写的子字符串）。

##  <a name="bkmkPropertiesVersusMacros"></a> 属性页宏

宏是编译时常量，是指由 Visual Studio 或 MSBuild 系统定义的值，或是由用户定义的值。 通过使用宏（而不是硬编码值，例如目录路径），你可更轻松地在计算机之间以及 Visual Studio 的版本之间共享属性设置，并且可更好地确保项目设置正确地参与属性继承。 可以使用属性编辑器来查看所有可用宏的值。

### <a name="predefined-macros"></a>预定义宏

全局宏<br/>
应用于项目配置的所有项目。 具有语法 `$(name)`。 全局宏的示例是 `$(VCInstallDir)`，它存储 Visual Studio 安装的根目录。 全局宏与 MSBuild 中的 `PropertyGroup` 相对应。

项宏<br/>
具有语法 `%(name)`。 对于文件来说，仅适用于该文件的项宏，例如可以使用 `%(AdditionalIncludeDirectories)` 来指定仅适用于特定文件的包含目录。 这种项宏与 MSBuild 中的 `ItemGroup` 元数据相对应。 在项目配置中使用时，项宏适用于特定类型的所有文件。 例如，C/C++“预处理器定义”配置属性可以采用适用于项目中所有 .cpp 文件的 `%(PreprocessorDefinitions)` 项宏。 这种项宏与 MSBuild 中的 `ItemDefinitionGroup` 元数据相对应。 有关详细信息，请参阅[项定义](/visualstudio/msbuild/item-definitions)。

### <a name="user-defined-macros"></a>用户定义的宏

你可以创建用户定义的宏，以便在项目生成中将宏用作变量。 例如，可以创建一个用户定义的宏来提供自定义生成步骤或自定义生成工具的值。 用户定义的宏是名称/值对。 在项目文件中，使用 $(<em>name</em>) 表示法访问该值。

用户定义的宏存储在属性表中。 如果你的项目尚未包含属性表，可以按照[创建可重用属性配置](#bkmkPropertySheets)中的步骤创建一个。

##### <a name="to-create-a-user-defined-macro"></a>创建用户定义的宏

1.  在“属性管理器”窗口中（在菜单栏上，依次选择“视图”、“属性管理器”），打开属性表的快捷菜单（名称以 .user 结尾），然后选择“属性”。 此时将打开该属性表的“属性页”对话框。

2.  在对话框的左窗格中，选择“用户宏”。 在右窗格中，选择“添加宏”按钮，打开“添加用户宏”对话框。

3.  在对话框中，指定宏的名称和值。 根据需要，选中“将此宏设置为生成环境中的环境变量”复选框。

## <a name="property-editor"></a>属性编辑器

你可以使用属性编辑器来修改特定字符串属性，选择宏作为值。 若要访问“属性编辑器”，在属性页中选择属性，然后选择右侧的向下箭头按钮。 如果下拉列表包含“\<编辑>”，那么你可以选择它来显示该属性的属性编辑器。

![属性&#95;编辑器&#95;下拉列表](../ide/media/property_editor_dropdown.png "Property_Editor_Dropdown")

在属性编辑器中，可以选择“宏”按钮查看可用宏及这些宏的当前值。 下图显示选中“宏”按钮后，“附加包含目录”属性的属性编辑器。 如果选中“从父级或项目默认设置继承”复选框并添加了新值，则该值会附加到当前被继承的任意值。 如果清除复选框，则新值会替换继承值。 在大多数情况下，选中复选框。

![属性编辑器，Visual C&#43;&#43;](../ide/media/propertyeditorvc.png "PropertyEditorVC")

##  <a name="bkmkPropertySheets"></a> 创建可重用的属性配置

虽然可以根据每个用户和每台计算机设置“全局”属性，但我们不建议这样做。 相反，建议你使用“属性管理器”创建属性表，来存储你希望能够重新使用或与其他人共享的每一类项目的设置。 属性表还使无意中更改其他项目类型的属性设置的可能性变小。 在[创建可重用的属性配置](#bkmkPropertySheets)中详细讨论了属性表。

> [!IMPORTANT]
> **.user 文件以及它们存在问题的原因**
>
> 过去的 Visual Studio 版本使用了全局属性表，此表包含 .user 文件名扩展，并且位于\<userprofile>\AppData\Local\Microsoft\MSBuild\v4.0\ folder。 我们不再推荐这些文件，因为它们是针对每个用户、每台计算机来设置项目配置属性的。 特别是如果你在生成计算机上面向多个平台，此类“全局”设置会影响生成。 例如，如果你同时拥有一个 MFC 项目和 Windows Phone 项目，则其中一个项目的 .user 属性将会无效。 可重用的属性表更为灵活，而且更加可靠。
>
> 尽管 Visual Studio 仍安装 .user 文件并参与属性继承，但默认情况下，这些文件为空。 最佳做法是删除项目在“属性管理器”中的引用，以确保项目按每个计算机设置和每个用户独立运行。这对确保 SCC（源代码管理）环境中的正确行为来说非常重要。

若要显示“属性管理器”，请在菜单栏上依次选择“视图”、“其他窗口”、“属性管理器”。

如果你想将经常使用的属性集应用于多个项目，则可以使用“属性管理器”在可重用的属性表文件中捕获，按照惯例，文件的扩展名为 .props。 你可以将一张或多张表应用于新项目，这样就不必从零开始设置属性。 若要访问“属性管理器”，在菜单栏中选择“视图”、“属性管理器”。

![“属性管理器”快捷方式菜单](../ide/media/sharingnew.png "SharingNew")

在每个配置节点下，将看到适用于该配置的每个属性表的节点。 创建项目时，此系统添加了属性表，该表基于在应用向导中所选的选项来设置值。 右键单击任何节点并选择“属性”来查看适用于该节点的属性。 所有属性表都自动导入到项目的“主”属性表 (ms.cpp.props) 中并进行评估，以便在属性管理器中显示。 可以移动它们来更改评估顺序。 稍后评估的属性表将覆盖之前已评估表中的值。

如果选择“添加新项目属性表”，然后进行选择（例如 MyProps.props 属性表），将显示属性页对话框。 请注意，适用于 MyProps 属性表；你所做的任何更改都将写入表中，而非属性文件 (.vcxproj) 中。

如果直接在 .vcxproj 文件中设置同一属性，属性表中的属性将被重写。

你可以按所需的频率导入属性表。 一个解决方案中的多个项目可从同一个属性表继承设置，一个项目可有多个表。 属性表自身可以从另一个属性表继承设置。

你还可以为多个配置创建一个属性表。 为此，请为每个配置创建属性表，打开其中一个配置的快捷菜单，选择“添加现有属性表”，然后添加其他表。 但是，如果使用一个常用属性表，请注意在设置属性时，它会获取该表适用的所有配置设置，而且 IDE 不会显示从给定属性表继承的项目或其他属性表。

在具有多个项目的大型解决方案中，创建解决方案级别的属性表非常有用。 在将项目添加到解决方案时，请使用“属性管理器”将该属性表添加到项目中。 如果项目级别为必填字段，则可以添加一个新属性表以设置指定的项目值。

> [!IMPORTANT]
> 由于 .props 文件不作为项目项创建，因此该文件默认不参与源代码管理。 如果你希望将文件加入源代码管理，则可以手动添加文件作为解决方案项。

#### <a name="to-create-a-property-sheet"></a>创建属性表

1. 在菜单栏上，依次选择“查看”、“属性管理器”。 此时将打开“属性管理器”。

2. 若要定义属性表的范围，请选择属性表适用的项。 这可能是一个特殊配置，或另一个属性表。 打开该项的快捷菜单，然后选择“添加新项目属性表”。 指定一个名称和位置。

3. 在“属性管理器”中，打开新的属性表然后设置要包括的属性。

##  <a name="bkmkPropertyInheritance"></a> 属性继承

项目属性已分层。 每层继承前一层的值，但是继承的值可以通过设置属性显式重写。 这是基本的继承树：

1. 来自 MSBuild CPP 工具集的默认设置（..\Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props，由 .vcxproj 文件导入。）

2. 属性表

3. .vcxproj 文件。 （可能重写默认设置和属性页设置。）

4. 项元数据

> [!TIP]
> 在属性页中，`bold` 的属性在当前上下文中定义。 普通字体的属性将被继承。

项目文件 (.vcxproj) 在生成时导入其他属性表。 在导入所有属性表后，对项目文件进行计算，然后所有属性值都使用最后一个定义。 有时，通过查看展开的文件来确定给定的属性值如何继承非常有用。 若要查看扩展版本，请在 Visual Studio 命令提示中输入以下命令。 （将占位符文件名称更改为要使用的名称。）

**msbuild /pp:** *temp* **.txt** *myapp* **.vcxproj**

除非你十分熟悉 MSBuild，否则展开的项目文件可能会很大并且难以理解。 这是项目文件的基本结构：

1. 基本项目属性，不在 IDE 中显示。

2. 导入 Microsoft.cpp.default.props，该文件定义了一些基本的、不依赖于工具集的属性。

3. 全局配置属性在“常规配置”页面上显示为“PlatformToolset”和“项目”默认属性。 这些属性决定下一步将哪个工具集和内部属性表导入 Microsoft.cpp.props 中。

4. 导入 Microsoft.cpp.props，该文件设置大多数项目默认值。

5. 导入所有属性表，包括 .user 文件。 这些属性表可以重写内容，但“PlatformToolset”和“项目”默认属性除外。

6. 项目配置属性的其余部分。 这些值可以重写属性表中设置的内容。

7. 项（文件）及其元数据。 这些始终是 MSBuild 评估规则的最后一项，即使它们出现在其他属性和导入之前仍是如此。

有关详细信息，请参阅 [MSBuild 属性](/visualstudio/msbuild/msbuild-properties)。

## <a name="adding-an-include-directory-to-the-set-of-default-directories"></a>添加包含目录到默认目录集

在将包含目录添加到项目中时，请勿重写所有默认目录，这点非常重要。 添加目录的正确方法是追加新路径，例如"C:\MyNewIncludeDir\\"，然后追加“$(IncludePath)”宏为属性值。

## <a name="setting-environment-variables-for-a-build"></a>设置生成的环境变量

Visual C++ 编译器 (cl.exe) 可识别某些环境变量，尤其是 LIB、LIBPATH、PATH 和 INCLUDE。 使用 IDE 生成时，[VC++ Directories Property Page](../ide/vcpp-directories-property-page.md) 属性页中设置的属性用于设置那些环境变量。 如果已设置了 LIB、LIBPATH 和 INCLUDE 值（例如通过开发人员命令提示设置），则这些值将被相应的 MSBuild 属性的值替换。 然后生成在 PATH 前预置 VC++ 目录可执行目录属性的值。 你可以通过创建用户定义的宏然后选中显示“在生成环境中将此宏设置为环境变量”的框来设置用户定义的环境变量。

## <a name="setting-environment-variables-for-a-debugging-session"></a>设置调试会话的环境变量

在项目“属性页”对话框的左窗格中，展开“配置属性”，然后选择“调试”。

在右窗格中，修改“环境”或“合并环境”项目设置，然后选择“确定”按钮。

## <a name="modifying-properties-and-targets-without-changing-the-project-file"></a>修改属性和目标无需更改项目文件

可以从 MSBuild 命令提示符处重写项目属性和目标而无需更改项目文件。 当你想要暂时或偶尔应用某些属性时，这非常有用。 它假定你对 MSBuild 有一定了解。 有关详细信息，请参阅 [MSBUild](https://docs.microsoft.com/en-us/visualstudio/msbuild/msbuild)。

> [!IMPORTANT]
> 可以使用 Visual Studio 中的 XML 编辑器或任何文本编辑器来创建 .props 或 .targets 文件。 不要在此情况下使用“属性管理器”，因为它会将属性添加到项目文件中。

重写项目属性：

1. 创键指定要重写的属性的 .props 文件。

1. 从命令提示符处设置 ForceImportBeforeCppTargets="C:\sources\my_props.props"

重写项目目标：

1. 创建具有其实现或特定目标的 .targets 文件

2. 从命令提示符处设置 ForceImportAfterCppTargets ="C:\sources\my_target.targets"

还可以使用/p: 选项在 msbuild 命令行上设置任一选项：

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props"
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets"
```

以这种方法重写属性和目标等同于将以下导入添加到该解决方案的所有 .vcxproj 文件：

```cmd
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```

## <a name="see-also"></a>请参阅

[创建和管理 Visual C++ 项目](../ide/creating-and-managing-visual-cpp-projects.md)<br/>
[.vcxproj 和 .props 文件结构](vcxproj-file-structure.md)<br/>
[属性页 XML 文件](property-page-xml-files.md)<br/>
