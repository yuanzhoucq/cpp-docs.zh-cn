---
title: 属性页 XML 规则文件
ms.date: 05/06/2019
helpviewer_keywords:
- property page XML files
ms.assetid: dd9d9734-4387-4098-8ba6-85b93507731d
ms.openlocfilehash: 610dc7341a35845b35d8ed80f52b421d1c2fb5d1
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65217722"
---
# <a name="property-page-xml-rule-files"></a>属性页 XML 规则文件

IDE 中的项目属性页是由 VCTargets 文件夹中的 XML 文件配置的。 确切的路径取决于安装的 Visual Studio 版本和产品语言。 对于英语版 Visual Studio 2017 Enterprise Edition，路径为 `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`。 XML 文件描述规则名称、类别以及各个属性、其数据类型、默认值和显示方式。 在 IDE 中设置属性时，新值存储在项目文件中。

只有在以下情况下，才需要了解这些文件和 Visual Studio IDE 的内部工作：(a) 想要创建自定义属性页，或 (b) 想要通过除 Visual Studio IDE 之外的某些方式自定义项目属性。

首先，打开项目的属性页（右键单击“解决方案资源管理器”中的项目节点，并选择“属性”）：

![Visual StudioC++项目属性](../media/cpp-property-page-2017.png)

“配置属性”下的每个节点都称为一个“规则”。 规则有时表示编译器之类的单个工具，但该术语通常是指具有属性的事物，可执行和生成某些输出。 每个规则都使用 VCTargets 文件夹中的 xml 文件填充。 例如，上面显示的 C/C++ 规则由“cl.xml”填充。

如上所示，每个规则都具有一组属性，这些属性按类别整理。 规则下的每个子节点代表一个类别。 例如，C/C++ 下的“优化”节点包含编译器工具的所有优化相关属性。 这些属性及其值本身在右窗格上以网格形式呈现。

可以在记事本或任何 XML 编辑器中打开 cl.xml（请参阅以下快照）。 可看到名为“规则”的根节点下包含定义的属性列表（与 UI 中显示的属性列表相同）以及其他元数据。

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--Copyright, Microsoft Corporation, All rights reserved.-->
<Rule Name="CL" PageTemplate="tool" DisplayName="C/C++" SwitchPrefix="/" Order="10" xmlns="http://schemas.microsoft.com/build/2009/properties" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.Categories>
    <Category Name="General" DisplayName="General" />
    <Category Name="Optimization" DisplayName="Optimization" />
    <Category Name="Preprocessor" DisplayName="Preprocessor" />
    <Category Name="Code Generation" DisplayName="Code Generation" />
    <Category Name="Language" DisplayName="Language" />
    <Category Name="Precompiled Headers" DisplayName="Precompiled Headers" />
    <Category Name="Output Files" DisplayName="Output Files" />
    <Category Name="Browse Information" DisplayName="Browse Information" />
    <Category Name="Advanced" DisplayName="Advanced" />
    <Category Name="All Options" DisplayName="All Options" Subtype="Search" />
    <Category Name="Command Line" DisplayName="Command Line" Subtype="CommandLine" />
  </Rule.Categories>
...
```

属性页 UI 中配置属性下的每个节点对应一个 XML 文件。 可以通过在项目中包含或删除对应 XML 文件的位置来添加或删除 UI 中的规则。 例如，以下是 Microsoft.CppBuild.targets（1033 文件夹的上一级）包含 cl.xml 的方式：

```xml
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>
```

如果剥离所有数据的 cl.xml，最终将得到以下主干：

```xml
<?xml version="1.0" encoding="utf-8"?>
<Rule>
  <Rule.DataSource />
  <Rule.Categories>
    <Category />
        ...
  </Rule.Categories>
  <BoolProperty />
  <EnumProperty />
  <IntProperty />
  <StringProperty />
  <StringListProperty />
</Rule>
```

下一部分介绍每个主要元素以及可以附加到主要元素的一些元数据。

1. **规则：** 规则通常是 xml 文件中; 中的根节点它可以具有多个属性：

    ```xml
    <Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
              xmlns="http://schemas.microsoft.com/build/2009/properties"
              xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
              xmlns:sys="clr-namespace:System;assembly=mscorlib">
      <Rule.DisplayName>
        <sys:String>C/C++</sys:String>
      </Rule.DisplayName>
    ```

   a. **名称：** Name 属性是该规则的 id。 在项目的所有属性页 xml 文件中，它必须是唯一的。

   b. **PageTemplate:** UI 使用此属性的值可供选择的 UI 模板集合。 “工具”模板以标准网格形式呈现属性。 此特性的其他内置值为“调试程序”和“通用”。 请分别查看“调试”节点和“常规”节点，以查看指定这些值所产生的 UI 格式。 “调试程序”页模板的 UI 使用下拉框在不同调试程序的属性之间进行切换，而“通用”模板在一个页面中显示所有不同属性类别，而不是在“规则”节点下包含多个类别子节点。 此特性只是针对 UI 的一项建议，xml 文件本质上独立于 UI。 不同的 UI 可能出于不同目的使用此特性。

   c. **SwitchPrefix:** 这是针对开关在命令行中使用的前缀。 “/”的值将产生类似于 /ZI、/nologo 和 /W3 的开关。

   d. **部署顺序：** 这是向预期 UI 客户端上与所有其他规则比较系统中此规则的相对位置的建议。

   e. **xmlns:** 这是标准的 XAML 元素。 可以看到三个列出的命名空间。 这三个命名空间分别对应于 XAML 反序列化类命名空间、XAML 架构命名空间和系统命名空间。

   f. **DisplayName:** 这是规则节点的属性页用户界面显示的名称。 此值已本地化。 由于内部本地化工具的要求，我们将 DisplayName 创建为规则的子元素，而不是特性（如 Name 或 SwitchPrefix）。 从 XAML 的角度来看，二者都是一样的。 因此，可以仅将其用作用于减少混乱或保持原样的特性。

   g. **数据源：** 这是一个非常重要的属性，它会告知项目系统属性值应从该位置读取和写入，以及其分组 （如下所述）。 对于 cl.xml，这些值为：

      ```xml
      <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
      ```

   - `Persistence="ProjectFile` 指示项目系统应写入项目文件或属性表文件（取决于用于生成属性页的节点）的规则的所有属性。 其他可能的值为“UserFile”，用于将值写入 .user 文件。

   - `ItemType="ClCompile"` 表示属性将存储为 ItemDefinition 元数据或此项类型的项元数据（后者仅在属性页从解决方案资源管理器中的文件节点生成的情况下适用）。 如果未设置此字段，则属性写入为 PropertyGroup 中的常见属性。

   - `Label=""` 指示在属性写入为 `ItemDefinition` 元数据时，父级 ItemDefinitionGroup 的标签将为空（每个 MSBuild 元素都可以有一个标签）。 Visual Studio 2017 使用已标记的组来导航 vcxproj 项目文件。 请注意，包含大多数规则属性的组都具有空字符串作为标签。

   - `HasConfigurationCondition="true"` 指示项目系统为值附加配置条件，以便其仅对当前项目配置生效（该条件可以附加到父组或值本身）。 例如，打开项目节点的属性页，并将“配置属性”>“C/C++ 常规”下的“将警报视为错误”属性值设为“是”。 以下值将写入项目文件中。 请注意附加到父级 ItemDefinitionGroup 的配置条件。

      ```xml
      <ItemDefinitionGroup Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">
        <ClCompile>
          <TreatWarningAsError>true</TreatWarningAsError>
        </ClCompile>
      </ItemDefinitionGroup>
      ```

      如果在特定文件（例如 stdafx.cpp）的属性页中设置此值，则该属性值将在项目文件中的 stdafx.cpp 项下写入，如下所示。 请注意将配置条件直接附加到元数据本身的方式。

      ```xml
      <ItemGroup>
        <ClCompile Include="stdafx.cpp">
          <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
        </ClCompile>
      </ItemGroup>
      ```

   上文未列出的另一个 DataSource 特性为 PersistedName。 通过此特性，可以使用不同的名称表示项目文件中的属性。 默认情况下，此特性设置为属性的 Name。

   单个属性可以重写其父级规则的 DataSource。 在这种情况下，此属性值的位置将不同于规则中其他属性的位置。

   h. 还有一些其他规则特性（例如 Description、SupportsFileBatching 等）未在此处显示。 通过浏览这些类型的文档，可以获得适用于规则或任何其他元素的完整特性集。 或者，可以检查 `Microsoft.Build.Framework .dll` 程序集中 `Microsoft.Build.Framework.XamlTypes` 命名空间中的类型的公共属性。

   i. DisplayName、PageTemplate 和 Order 是独立于 UI 的数据模型中存在的 UI 相关属性。 用于显示属性页的任何 UI 几乎肯定会使用这些属性。 DisplayName 和 Description 这两个属性几乎存在于 xml 文件中的所有元素上。 并且只有这两个属性经过了本地化（这些字符串的本地化将在后面的文章中进行讲解）。

1. **类别：** 规则可以有多个类别。 xml 文件中列出类别的顺序是让 UI 以相同顺序显示类别的建议。 例如，在 UI（“常规”、“优化”、“预处理器”...）中看到的 C/C++ 节点下的类别顺序  与在 cl.xml 中相同。 示例类别如下所示：

    ```xml
    <Category Name="Optimization">
      <Category.DisplayName>
        <sys:String>Optimization</sys:String>
      </Category.DisplayName>
    </Category>
    ```

   以上代码片段显示了之前介绍过的 Name 和 DisplayName 特性。 再次强调，“类别”还可能包含上文未使用的其他特性。 可以通过阅读文档或使用 ildasm.exe 检查程序集来了解相关信息。

1. **属性：** 这是 xml 文件的主要内容，其中包含此规则中的所有属性的列表。 每个属性都可以是在上述 XAML 主干中显示的五种可能类型之一。 当然，文件中可能只有一些这些类型。 一个熟悉包含多个特性，可对属性进行详尽描述。 在此仅介绍 StringProperty。 其余的属性都非常相似。

    ```xml
    <StringProperty Subtype="file" Name="ObjectFileName" Category="Output Files" Switch="Fo">
      <StringProperty.DisplayName>
        <sys:String>Object File Name</sys:String>
      </StringProperty.DisplayName>
      <StringProperty.Description>
        <sys:String>Specifies a name to override the default object file name; can be file or directory name.(/Fo[name])</sys:String>
      </StringProperty.Description>
    </StringProperty>
    ```

   此代码片段中的大部分特性上文前都已介绍过。 新的特性为 Subtype、Category 和 Switch。

   a. Subtype 是仅适用于 StringProperty 和 StringListProperty 的特性；提供了上下文信息。 例如，“文件”的值指示该属性表示文件路径。 此类上下文信息通过提供 Windows 资源管理器作为属性的编辑器，允许用户直观地选择文件来提升编辑体验。

   b. **类别：** 这会将声明在其下此属性所属的类别。 尝试在 UI 的“输出文件”类别下查找此属性。

   c. **开关：** 当规则表示工具-如编译器工具 – 这种规则的大多数属性作为开关期间传递给该工具可执行文件生成时。 此特性的值指示要使用的开关文本。 以上属性指定其开关应为“Fo”。 结合父规则上的 SwitchPrefix 特性，此属性作为 /Fo"Debug\" 传递给可执行文件（在属性页 UI 的 C/C++ 命令行中可见）。

   其他属性特性包括：

   d. **可见：** 如果由于某种原因，您不希望使属性显示在属性页中 （但可能仍可在生成期间），将此属性设置为 false。

   e. **只读：** 如果你想要提供的属性页中的此属性的值的只读视图，请将此属性设置为 true。

   f. **IncludeInCommandLine:** 某些属性可能不需要在生成时要传递给工具。 将此特性设为 false 可阻止传递。
