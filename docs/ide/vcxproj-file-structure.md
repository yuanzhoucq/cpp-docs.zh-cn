---
title: ".vcxproj 和.props 文件结构 |Microsoft 文档"
ms.custom: 
ms.date: 04/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
caps.latest.revision: "1"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d48b16d9a4250de8c8c3dfef62fdcfb5c1434960
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2018
---
# <a name="vcxproj-and-props-file-structure"></a>.vcxproj 和.props 文件结构

MSBuild 是 Visual Studio; 中的默认项目系统当你选择**文件 |新项目**在 Visual c + + 中，您将创建具有扩展名的 XML 项目文件中存储其设置 MSBuild 项目`.vcxproj`。 .Props 文件和.targets 文件设置可以存储，还可以导入的项目文件。 在大多数情况下，从不需要以手动编辑项目文件中，而实际上你应不能编辑它手动除非你有 MSBuild 更好地理解。 只要有可能应使用 Visual Studio 属性页来修改项目设置 (请参阅[使用项目属性](working-with-project-properties.md)。 但是，在某些情况下，你可能需要手动修改项目文件或属性表。 对于这些方案中，这篇文章包含有关文件的结构的基本信息。

**重要提示：**

如果你选择手动编辑.vcxproj 文件，请注意以下事项：

1. 文件的结构必须遵循本文中所述的规定窗体。

1. Visual c + + 项目系统当前不支持通配符在项目项中。 例如，不支持此：

   ```xml
   <ClCompile Include="*.cpp"/>
   ```

1. Visual c + + 项目系统当前不支持宏项目项路径中。 例如，不支持此：

   ```xml
   <ClCompile Include="$(IntDir)\generated.cpp"/>
   ```

1. 以便具有正确添加、 删除或修改时在中编辑项目属性**项目属性**对话框中，该文件必须包含每个项目配置，不同的组和条件必须是此窗体中：

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

1. 每个属性必须指定正确的标签，在属性规则文件指定的组中。 有关详细信息，请参阅[属性页 xml 规则文件](property-page-xml-files.md)。

## <a name="vcxproj-file-elements"></a>.vcxproj 文件元素

你可以通过使用任何文本或 XML 编辑器来检查.vcxproj 文件的内容。 可以通过右键单击项目在解决方案资源管理器，查看它在 Visual Studio 中选择**卸载项目**，然后选择**编辑 Foo.vcxproj**。

需要注意的第一个操作是顶级元素出现在特定的顺序。 例如:

- 属性组和项定义组的最晚 Microsoft.Cpp.Default.props 的导入。
- 在文件末尾导入所有目标。
- 有多个属性组，每个都有唯一标签，并且它们将按特定顺序发生。

项目文件中的元素的顺序是非常重要，因为 MSBuild 基于顺序计算模型。  如果你的项目文件，包括所有导入的.props 和.targets 文件包含多个定义的属性，最后一个定义将覆盖前面的。 在下面的示例中，"xyz"的值将设置在编译期间因为 MSBUild 引擎的遇到它上次其求值期间。

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

下面的代码段演示的最小.vcxproj 文件。 由 Visual Studio 生成任何.vcxproj 文件将包含这些顶级 MSBuild 元素，它们将 （但可能包含多个副本的每个此类顶级元素） 按以下顺序出现。 请注意，`Label`特性是仅由 Visual Studio 用作 signposts 以进行编辑的任意标记; 它们具有任何其他功能。

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

以下各节描述了上述每个元素的用途以及它们为何排序这种方式：

### <a name="project-element"></a>Project 元素

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project`是根节点。 它指定要使用的 MSBuild 版本以及此文件将传递到 MSBuild.exe 时要执行的默认目标。

### <a name="projectconfigurations-itemgroup-element"></a>ProjectConfigurations ItemGroup 元素

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations`包含项目配置说明。 示例包括调试 |Win32，版本 |Win32，调试 |ARM 和等等。 许多项目设置是特定于给定的配置。 例如，你可能会想要设置的发布版本，但不是调试版本中的优化属性。

`ProjectConfigurations`项组不在生成期间使用。 Visual Studio IDE 将需要它才能加载项目。 此项组可以移动到.props 文件和导入到.vcxproj 文件。 但是，在这种情况下，如果你需要添加或删除配置，你必须手动编辑.props 文件;不能使用 IDE。

### <a name="projectconfiguration-elements"></a>ProjectConfiguration 元素

下面的代码段显示的项目配置。 在此示例中调试 | x 64 is 的配置名称。 项目配置名称必须采用格式 $(Configuration)|$(Platform). 项目配置节点可以具有两个属性： 配置和平台。 将配置处于活动状态时在此处指定的值自动设置这些属性。

   ```xml
   <ProjectConfiguration Include="Debug|x64">
     <Configuration>Debug</Configuration>
     <Platform>x64</Platform>
   </ProjectConfiguration>
   ```

IDE 预期查找所有 ProjectConfiguration 项中使用的配置和平台值的任意组合的项目配置。 这通常意味着一个项目可能有意义的项目配置，以满足此要求。 例如，如果一个项目具有这些配置：

- Debug|Win32
- 零售 |Win32
- 特殊的 32 位优化 |Win32

然后它必须还具有这些配置，即使"特殊 32 位优化"是没有意义 x64 也是如此：

- 调试|x64
- 零售 | x64
- 特殊的 32 位优化 | x64

你可以禁用生成和部署中的任何配置的命令**解决方案 Configuration Manager**。

### <a name="globals-propertygroup-element"></a>Globals PropertyGroup 元素

```xml
 <PropertyGroup Label="Globals" />
```

`Globals`包含项目级别设置，例如 ProjectGuid、 根命名空间和 ApplicationType / ApplicationTypeRevision。 最后两个通常定义目标操作系统。 因为，引用和项目项不能有条件当前，项目仅可具有单个 OS。 这些属性通常不会被替代其他位置在项目文件中。 此组不依赖于配置的因此通常只有一个全局组存在于项目文件时才。

### <a name="microsoftcppdefaultprops-import-element"></a>Microsoft.Cpp.default.props 导入元素

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

**Microsoft.Cpp.default.props**属性表附带了 Visual Studio，并且不能修改。 它包含项目的默认设置。 默认值可能会有所不同，具体取决于 ApplicationType。

### <a name="configuration-propertygroup-elements"></a>配置 PropertyGroup 元素

```xml
<PropertyGroup Label="Configuration" />
```

A`Configuration`属性组具有一个附加的配置条件 (如`Condition=”'$(Configuration)|$(Platform)'=='Debug|Win32'”`)，它会在多个副本，每个配置的其中一个。 此属性组主持的特定配置的设置的属性。 配置的属性包括 PlatformToolset 和还控制系统中的属性表包含**Microsoft.Cpp.props**。 例如，如果定义了属性`<CharacterSet>Unicode</CharacterSet>`，然后系统属性表**microsoft。Cpp.unicodesupport.props**将不包括在内。 如果您检查**Microsoft.Cpp.props**，你将看到行： `<Import Condition=”'$(CharacterSet)' == 'Unicode'”   Project=”$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props”/>`。

### <a name="microsoftcppprops-import-element"></a>Microsoft.Cpp.props 导入元素

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

**Microsoft.Cpp.props**属性表 （直接或通过导入） 定义例如编译器的优化和警告级别属性，MIDL 工具 TypeLibraryName 的许多工具特定属性的默认值属性，依次类推。 它还导入基于立即上述属性组中定义的配置属性的各种系统属性表。

### <a name="extensionsettings-importgroup-element"></a>ExtensionSettings ImportGroup 元素

```xml
<ImportGroup Label="ExtensionSettings" />
```

`ExtensionSettings`组包含属于生成自定义项的属性表的导入。 生成的自定义项定义由最多三个文件： 一个.targets 文件、.props 文件和一个.xml 文件。 此导入组包含.props 文件导的入。

### <a name="propertysheets-importgroup-elements"></a>PropertySheets ImportGroup 元素

```xml
<ImportGroup Label="PropertySheets" />
```

`PropertySheets`组包含用户属性表的导入。 这些是通过 Visual Studio 中的属性管理器视图添加属性表。 这些导入的列出的顺序很重要，并且会反映在属性管理器中。 项目文件通常包含这种类型的导入组中，一个用于每个项目配置的多个实例。

### <a name="usermacros-propertygroup-element"></a>UserMacros PropertyGroup 元素

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros`包含属性创建作为用于自定义生成过程的变量。 例如，你可以定义用户宏来定义你的自定义输出的路径为 $(CustomOutputPath) 并使用它来定义其他变量。 此属性组可容纳此类属性。 请注意，在 Visual Studio 中，将填充此组不在项目文件中因为 Visual c + + 不支持配置的用户宏。 属性表中支持用户宏。

### <a name="per-configuration-propertygroup-elements"></a>每个配置 PropertyGroup 元素

```xml
<PropertyGroup />
```

有多个实例的此属性组中，每个配置的所有项目配置的其中一个。 每个属性组必须具有一个附加的配置条件。 如果任何配置缺少，**项目属性**对话框不会正常工作。 与上面的属性组中，此一个没有标签。 此组包含项目配置级别设置。 这些设置适用于属于指定的项组的所有文件。 生成自定义项定义元数据初始化此处。

此 PropertyGroup 必须后`<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />`，且必须具有不带标签之前它的任何其他 PropertyGroup （否则编辑项目属性将不能正常工作）。

### <a name="per-configuration-itemdefinitiongroup-elements"></a>每个配置 ItemDefinitionGroup 元素

```xml
 <ItemDefinitionGroup />
```

包含项定义。 这些必须遵循的标签的每个配置 PropertyGroup 元素相同的条件规则。

### <a name="itemgroup-elements"></a>ItemGroup 元素

```xml
<ItemGroup />
```

包含项目中的项 （源文件等）。 项目项 （即，它们视为项目项规则定义的项类型） 不支持条件。

元数据应具有配置条件的每个配置，即使它们是所有相同。 例如:

   ```xml
   <ItemGroup>
     <ClCompile Include="stdafx.cpp">
       <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
       <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|x64’">true</TreatWarningAsError>
     </ClCompile>
   </ItemGroup>
   ```

Visual c + + 项目系统当前不支持通配符在项目项中。

   ```xml
   <ItemGroup>
     <ClCompile Include="*.cpp"> <!--Error-->
   </ItemGroup>
   ```

Visual c + + 项目系统当前不支持宏在项目项中。

   ```xml
   <ItemGroup>
     <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
   </ItemGroup>
   ```

ItemGroup 中指定的引用，并且它们具有以下这些限制：

- 引用不支持条件。
- 引用元数据不支持条件。

### <a name="microsoftcpptargets-import-element"></a>Microsoft.Cpp.targets 导入元素

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

定义 （直接或通过导入） Visual c + + 目标，例如生成、 清除等。

### <a name="extensiontargets-importgroup-element"></a>ExtensionTargets ImportGroup 元素

```xml
<ImportGroup Label="ExtensionTargets" />
```

此组包含生成自定义目标文件的导入。

## <a name="impact-of-incorrect-ordering"></a>不正确排序的影响

Visual Studio IDE 依赖于项目文件的顺序上面所述。 例如，在定义的属性值的属性页中时，IDE 将通常会空标签的属性组中将属性定义。 这可确保用户定义的值会重写使系统属性表中的默认值。 同样，目标文件导入末尾由于它们使用上面定义的属性，因为它们通常不定义属性本身。 在系统属性表后同样，导入用户属性表 (包括通过**Microsoft.Cpp.props**)。 这可确保用户可以重写任何被系统属性表的默认设置。

如果.vcxproj 文件未遵循此布局，生成结果可能不是你的预期。 例如，如果你错误地导入后由用户定义的属性表的系统属性表，将覆盖用户设置系统属性表。

即使 IDE 设计时体验在某种程度上依赖于正确排序的元素。 例如，如果你.vcxproj 文件没有`PropertySheets`导入组中，IDE 可能不能确定 where to place 新的属性表中创建该用户具有**属性管理器**。 这可能会导致正在由系统表的重写用户表中。 虽然 IDE 使用启发式方法可以容忍细微.vcxproj 文件布局中的不一致，强烈建议不偏离本文前面所示的结构。

## <a name="how-the-ide-uses-element-labels"></a>IDE 如何使用元素标签

在 IDE 中，当你设置**UseOfAtl**它写入到在项目文件中，配置属性组的常规属性页中的属性，而**TargetName**相同的属性页中的属性写入到标签的每个配置属性组。 Visual Studio 会查找在何处写入每个属性的信息的属性页的 xml 文件。 有关**常规**属性页 （假设你有英语版本的 Visual Studio Enterprise 版），该文件是`%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml`。 属性页 XML 规则文件定义有关规则和所有其属性的静态信息。 此类一条信息是目标文件 （将在其中写入其值的文件） 中的规则属性的首选的位置。 首选的位置是由项目文件元素的标签特性指定的。

## <a name="property-sheet-layout"></a>属性表布局

以下 XML 代码片段是属性表 (.props) 文件的最小布局。 类似于.vcxproj 文件，并且可以从前面的讨论推断.props 元素的功能。

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

若要使你自己的属性表，复制 VCTargets 文件夹中的.props 文件之一，并对其进行修改您的要求。 对于 Visual Studio 自 2017 年 1 Enterprise edition 中，默认 VCTargets 路径是`%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets`。

## <a name="see-also"></a>请参阅

[使用项目属性](working-with-project-properties.md)  
[属性页 XML 文件](property-page-xml-files.md)  
