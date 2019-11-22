---
title: .vcxproj 和 .props 文件结构
ms.date: 05/16/2019
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: a24349980e9395257f20fcfcc0987883060a7c1d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303132"
---
# <a name="vcxproj-and-props-file-structure"></a>.vcxproj 和 .props 文件结构

[MSBuild](../msbuild-visual-cpp.md) 是 Visual Studio 中默认的项目系统；在 Visual C++ 中选择“文件” > “新建项目”会创建一个 MSBuild 项目，其设置存储于扩展名为 `.vcxproj` 的 XML 项目文件中。 项目文件还可以导入 .props 文件和 .targets 文件，这两种文件能存储设置。 在大多数情况下，从不需要手动编辑项目文件，而且其实也不应手动编辑它，除非你对 MSBuild 非常了解。 应尽可能地使用 Visual Studio 属性页来修改项目设置（请参阅请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。）。 但在某些情况下，可能需要手动修改项目文件或属性表。 针对这类情况，本文包含与文件结构相关的基本信息。

**重要提示：**

如果选择手动编辑 .vcxproj 文件，请注意以下事项：

1. 文件结构必须遵循本文中所述的规定形式。

1. Visual Studio C++ 项目系统目前不支持在项目项中使用通配符。 例如，不支持此内容：

   ```xml
   <ClCompile Include="*.cpp"/>
   ```

1. Visual Studio C++ 项目系统目前不支持在项目项路径中使用宏。 例如，不支持此内容：

   ```xml
   <ClCompile Include="$(IntDir)\generated.cpp"/>
   ```

   “不支持”表示不能保证宏适用于 IDE 中的所有操作。 不会更改其在不同配置中的值的宏应该可以正常工作，但如果将项移动到不同的筛选器或项目，则可能不会保留这些宏。 为不同配置更改其值的宏会引起问题，因为 IDE 不希望不同的项目配置有不同的项目项路径。

1. 为了确保能在“项目属性”对话框中正确地添加、删除或修改项目属性，该文件必须包含每个项目配置各自的组，且条件必须为这种形式：

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

1. 分组中指定的每个属性必须带有正确的标签，就像项目规则文件中所指定的那样。 有关详细信息，请参阅[属性页 XML 规则文件](property-page-xml-files.md)。

## <a name="vcxproj-file-elements"></a>.vcxproj 文件元素

可以通过使用任何文本或 XML 编辑器来检查.vcxproj 文件的内容。 若要在 Visual Studio 中进行查看，请在解决方案资源管理器中右键单击项目，选择“卸载项目”，再选择“编辑 Foo.vcxproj”。

要注意的第一点是顶级元素按特定顺序显示。 例如:

- 大多数的属性组和项定义组都在导入 Microsoft.Cpp.Default.props 后出现。

- 所有目标都在文件末尾导入。

- 存在多个属性组，每个都带有唯一标签并按特定顺序显示。

由于 MSBuild 基于按顺序的计算模型，所以项目文件中的元素顺序非常重要。  如果项目文件（包括导入的所有 .props 和 .targets 文件）包含多个属性定义，则最新的定义会覆盖前面的定义。 在下面的示例中，将在编译过程中设置值 "xyz"，因为 MSBUild 引擎最后在其计算过程中遇到它。

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

下面的代码片段演示了一个最小型的 .vcxproj 文件。 Visual Studio 生成的所有 .vcxproj 文件都将包含这些顶级 MSBuild 元素，并且这些元素会按此顺序出现（不过可能包含每个顶级元素的多个副本）。 请注意，`Label` 特性只是 Visual Studio 用作编辑标志的任意标记；它们不具备其他功能。

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003'>
  <ItemGroup Label="ProjectConfigurations" />
  <PropertyGroup Label="Globals" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
  <PropertyGroup Label="Configuration" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ImportGroup Label="ExtensionSettings" />
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
  <ImportGroup Label="ExtensionTargets" />
</Project>
```

以下各节描述这些元素各自的用途以及它们如此排序的原因：

### <a name="project-element"></a>Project 元素

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project` 为根节点。 它表明要使用的 MSBuild 版本以及将文件向 MSBuild.exe 传递时要执行的默认目标。

### <a name="projectconfigurations-itemgroup-element"></a>ProjectConfigurations ItemGroup 元素

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations` 包含项目配置描述。 例如“Debug|Win32”、“Release|Win32”和“Debug|ARM”等等。 很多项目设置都特定于给定的配置。 例如，可为发布生成而不是调试生成设置优化属性。

在生成时不使用 `ProjectConfigurations` 项组。 Visual Studio IDE 需要将其用于加载项目。 可将这个项组移至 .props 文件并导入至 .vcxproj 文件。 但是在这种情况下，如果需要添加或删除配置，则需要手动编辑 .props 文件而无法使用 IDE。

### <a name="projectconfiguration-elements"></a>ProjectConfiguration 元素

下面的代码片段演示一个项目配置。 此示例中的配置名称为“Debug|x64”。 项目配置名称的格式必须为 $(Configuration)|$(Platform)。 项目配置节点可以具有两个属性：配置和平台。 在配置处于活动状态时，将自动采用此处指定的值来自动设置这些属性。

```xml
<ProjectConfiguration Include="Debug|x64">
  <Configuration>Debug</Configuration>
  <Platform>x64</Platform>
</ProjectConfiguration>
```

IDE 会查找一个项目配置，此配置可以是由所有 ProjectConfiguration 项中使用的配置值和平台值构成的任意组合。 这通常意味着项目可能具有无意义的项目配置以满足此要求。 例如，如果项目具有这些配置：

- Debug|Win32

- Retail|Win32

- Special 32-bit Optimization|Win32

那么即使“Special 32-bit Optimization”对于 x64 是没有意义的，项目还是需要这些配置：

- 调试|x64

- Retail|x64

- Special 32-bit Optimization|x64

可以在“解决方案配置管理器”中禁用任何配置的生成和部署命令。

### <a name="globals-propertygroup-element"></a>Globals PropertyGroup 元素

```xml
<PropertyGroup Label="Globals" />
```

`Globals` 包含项目级别设置，例如 ProjectGuid、RootNamespace 和 ApplicationType/ApplicationTypeRevision。 最后两项通常定义目标操作系统。 由于引用和项目项当前无法具备条件，所以一个项目只能面向一个操作系统。 通常不会在项目文件中的其他位置重写这些属性。 此组不依赖于配置，所以通常在项目文件中只存在一个 Globals 组。

### <a name="microsoftcppdefaultprops-import-element"></a>Microsoft.Cpp.default.props Import 元素

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

Microsoft.Cpp.default.props 属性表是 Visual Studio 附带的，且无法修改。 它包含项目的默认设置。 根据 ApplicationType，可能默认值会有所不同。

### <a name="configuration-propertygroup-elements"></a>Configuration PropertyGroup 元素

```xml
<PropertyGroup Label="Configuration" />
```

`Configuration` 属性组具备附加的配置条件（例如 `Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"`），并在多个副本中出现（每个配置各一个）。 此属性组承载着为特定配置设置的属性。 配置属性包括 PlatformToolset，并控制 Microsoft.Cpp.props 中的系统属性表所包含的内容。 例如，如果定义 `<CharacterSet>Unicode</CharacterSet>` 属性，则会包含系统属性表 microsoft.Cpp.unicodesupport.props。 如果检查 Microsoft.Cpp.props，会看到该行：`<Import Condition="'$(CharacterSet)' == 'Unicode'" Project="$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props" />`。

### <a name="microsoftcppprops-import-element"></a>Microsoft.Cpp.props Import 元素

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

Microsoft.Cpp.props 属性表直接或通过导入操作为很多特定于工具的属性（例如编译器的优化和警告等级属性、MIDL 工具的 TypeLibraryName 属性以及其他属性）定义默认值。 它还导入各种系统属性表，基于这些属性表在上述属性组中定义配置属性。

### <a name="extensionsettings-importgroup-element"></a>ExtensionSettings ImportGroup 元素

```xml
<ImportGroup Label="ExtensionSettings" />
```

`ExtensionSettings` 组包含属于生成自定义项的属性表的导入。 一个生成自定义项由至多三个文件定义：.targets 文件、.props 文件和 .xml 文件。 此导入组包含 .props 文件的导入。

### <a name="propertysheets-importgroup-elements"></a>PropertySheets ImportGroup 元素

```xml
<ImportGroup Label="PropertySheets" />
```

`PropertySheets` 组包含用户属性表的导入。 这些是在 Visual Studio 中通过属性管理器视图添加的属性表。 这些导入的列出顺序很重要，且会反映在属性管理器中。 项目文件通常包含此类导入组的多个实例，每个项目配置各一个。

### <a name="usermacros-propertygroup-element"></a>UserMacros PropertyGroup 元素

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros` 包含创建为变量的属性，这些属性用于自定义生成过程。 例径定如，可定义将自定义输出路义为 $(CustomOutputPath) 的用户宏，并用它来定义其他变量。 此属性组包含这类属性。 请注意，在 Visual Studio 中不会将此组填充到项目文件，因为 Visual C++ 不支持在配置中使用用户宏。 属性表支持用户宏。

### <a name="per-configuration-propertygroup-elements"></a>按配置 PropertyGroup 元素

```xml
<PropertyGroup />
```

此属性组有多个实例，所有项目配置都各有一个。 每个属性组必须具备一个附加的配置条件。 如果漏掉了任何配置，“项目属性”对话框将不会正常工作。 与上述属性组不同，此属性组没有标签。 此组包含项目配置级别的设置。 这些设置适用于所有属于该特定项组的文件。 在此处初始化生成自定义项定义元数据。

此 PropertyGroup 必须 `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` 之后，并且必须没有任何其他 PropertyGroup （否则，项目属性编辑将无法正常工作）。

### <a name="per-configuration-itemdefinitiongroup-elements"></a>按配置 ItemDefinitionGroup 元素

```xml
<ItemDefinitionGroup />
```

包含项定义。 它们必须和无标签的按配置 PropertyGroup 元素遵循同样的条件规则。

### <a name="itemgroup-elements"></a>ItemGroup 元素

```xml
<ItemGroup />
```

包含项目中的项（源文件等）。 不支持对项目项（也就是根据规则定义被视为项目项的项类型）使用条件。

元数据应具备每个配置的配置条件，即使它们都是一样的。 例如:

```xml
<ItemGroup>
  <ClCompile Include="stdafx.cpp">
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">true</TreatWarningAsError>
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">true</TreatWarningAsError>
  </ClCompile>
</ItemGroup>
```

Visual Studio C++ 项目系统目前不支持在项目项中使用通配符。

```xml
<ItemGroup>
  <ClCompile Include="*.cpp"> <!--Error-->
</ItemGroup>
```

Visual Studio C++ 项目系统目前不支持在项目项中使用宏。

```xml
<ItemGroup>
  <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
</ItemGroup>
```

ItemGroup 中指定了引用，且这些引用具有以下限制：

- 引用不支持条件。

- 引用元数据不支持条件。

### <a name="microsoftcpptargets-import-element"></a>Microsoft.Cpp.targets Import 元素

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

直接或通过导入定义 Visual C++ 目标，例如生成和清除等。

### <a name="extensiontargets-importgroup-element"></a>ExtensionTargets ImportGroup 元素

```xml
<ImportGroup Label="ExtensionTargets" />
```

此组包含生成自定义项目标文件的导入。

## <a name="impact-of-incorrect-ordering"></a>排序错误的影响

Visual Studio IDE 依赖于按上述顺序排列的项目文件。 例如，当你在属性页中定义属性值时，IDE 通常会将属性定义放置在带有空标签的属性组中。 这样确保用户定义的值可以覆盖系统属性表中的默认值。 同样，在末尾导入目标文件，因为它们使用上面定义的属性而通常不会自己定义属性。 类似地，在系统属性表之后导入用户属性表（通过 Microsoft.Cpp.props 纳入）。 这样确保用户可以重写系统属性表中的默认值。

如果 .vcxproj 文件未遵循此布局，可能会生成与预期不同的结果。 例如，如果系统属性表错误地导入在用户定义的属性表之后，那么用户设置会被系统属性表覆盖。

即使是 IDE 设计时体验，也在一定程度上依赖于元素的正确排序。 例如，如果 .vcxproj 文件没有 `PropertySheets` 导入组，IDE 可能无法确定放置用户在属性管理器中创建的新属性表的位置。 这可能会导致系统表覆盖用户表。 虽然 IDE 所使用的启发式方法可以容忍 .vcxproj 文件布局中细微的不一致，但强烈建议不要偏离本文前面部分所述的结构。

## <a name="how-the-ide-uses-element-labels"></a>IDE 如何使用元素标签

在 IDE 中，设置常规属性页中的 UseOfAtl 属性时，会将其写入项目文件中的 Configuration 属性组，但是同一属性页中的 TargetName 属性会写入无标签的按配置属性组。 Visual Studio 会在属性页的 xml 文件中查找关于属性写入位置的信息。 对于常规属性页（假设你有英文版的 Visual Studio 2019 Enterprise Edition），该文件则为`%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml`。 属性页 XML 规则文件定义关于 Rule 及其所有属性的静态信息。 这类信息之一就是 Rule 属性在目标文件（也就是将要写入值的文件）中的首选位置。 首选位置由项目文件元素上的 Label 特性指定。

## <a name="property-sheet-layout"></a>属性表布局

以下 XML 代码片段是属性表 (.props) 文件的最简布局。 这与 .vcxproj 文件类似，并且可以从前面的讨论推断出 .props 元素的功能。

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

若要制作自己的属性表，请复制 VCTargets 文件夹中的某个 .props 文件，并根据需要对它进行修改。 对于 Visual Studio 2019 Enterprise Edition，默认的 VCTargets 路径为 `%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets`。

## <a name="see-also"></a>另请参阅

[在 Visual Studio 中设置 C++ 编译器并生成属性](../working-with-project-properties.md)<br/>
[属性页 XML 文件](property-page-xml-files.md)
