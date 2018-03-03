---
title: "属性页 XML 规则文件 |Microsoft 文档"
ms.custom: 
ms.date: 04/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- property page XML files
ms.assetid: dd9d9734-4387-4098-8ba6-85b93507731d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b81e8965773c64144059fa433b54484c786159a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="property-page-xml-rule-files"></a>属性页 XML 规则文件
通过 VCTargets 文件夹中的 XML 文件，配置在 IDE 中的项目属性页。 确切的路径取决于安装了 Visual Studio 的 edition(s)，和产品语言。 对于 Visual Studio 自 2017 年 1 Enterprise Edition 中，在英语中，路径是`%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`。 XML 文件描述的规则、 类别中，和的各个属性，其数据类型、 默认值的名称和它们将如何显示。 当你在 IDE 中设置属性时，在项目文件中存储的新值。

你需要了解这些文件和 Visual Studio IDE 的内部工作原理是您 （a） 的唯一方案想要创建自定义属性页中，或者 （b） 想要自定义项目属性中通过 Visual Studio IDE 以外的其他一些。 

首先，让我们打开项目的属性页 (右键单击中的项目节点**解决方案资源管理器**，然后选择属性):
   
![Visual c + + 项目属性](media/cpp-property-page-2017.png)

在每个节点**配置属性**称为规则。 一个规则有时表示编译器，之类的单一工具，但一般而言术语是指拥有的属性、 执行和，可能会产生一些输出的内容的。 每个规则将填充从 xml 文件 VCTargets 文件夹中。 例如，由 cl.xml 填充上面所示的 C/c + + 规则。

如上所示，每个规则具有一组组织为类别的属性。 每个规则下的子节点表示类别。 例如，C/c + + 下的优化节点包含编译器工具的所有优化相关的属性。 在右窗格中的网格格式呈现的属性和其值本身。

你可以在记事本或 （请参阅下面快照） 的任何 XML 编辑器中打开 cl.xml。 你将看到具有相同的定义其下显示在 UI 中，以及其他元数据的属性列表的规则的根节点。

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

没有对应于在配置属性下 UI 中的属性页中的每个节点的一个 XML 文件。 你可以添加或删除在 UI 中的规则通过包括或项目中删除相应的 XML 文件的位置。 例如，这是如何 Microsoft.CppBuild.targets （向上提升一级 1033年文件夹中） 包括 cl.xml:

```xml  
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>

``` 
条带 cl.xml 的所有数据时，如果你最终将得到以下框架：
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

以下部分描述每个主要元素和一些可以附加到它们的元数据。

1. **规则：**规则通常是 xml 文件中的根节点; 它可以具有多个属性：

```xml    
<Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
          xmlns="http://schemas.microsoft.com/build/2009/properties"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.DisplayName>
    <sys:String>C/C++</sys:String>
  </Rule.DisplayName>
```  

   a. **名称：**名称属性是规则的 id。 它必须是唯一的而项目的所有属性页 xml 文件。

   b. **PageTemplate:** UI 使用此属性的值从 UI 模板集合中进行选择。 "工具"模板呈现标准网格格式中的属性。 此属性的其他内置值是"调试器"和"泛型"。 请参阅调试节点和常规节点，分别，请参阅导致指定这些值的 UI 格式。 "调试器"页模板的 UI 使用一个下拉列表框来切换不同的调试器的属性，而"泛型"模板显示所有中而不是具有多个类别子节点下的规则的一页的不同属性类别节点。 此属性是只是一项建议 UI;xml 文件被旨在作为独立的 UI。 不同 UI 可能用于不同目的使用此属性。

  c. **SwitchPrefix:**这是用于交换机命令行中使用的前缀。 值为"/"将导致如下所示 /ZI、 /nologo、 /W3 等的开关。

  d. **顺序：**这是向与所有其他规则比较，在系统中此规则的相对位置上的潜在 UI 客户端的建议。

  e. **xmlns:**这是一个标准的 XAML 元素。 你可以看到列出的三个命名空间。 这些方法对应于 XAML 反序列化的命名空间类，XAML 架构和系统命名空间，分别。

  f. **DisplayName:**这是在规则节点的属性页 UI 上显示的名称。 此值进行了本地化。 我们创建 DisplayName 规则的子元素，而不是属性 （如名称或 SwitchPrefix） 由于内部本地化工具要求。 从 XAML 的角度来看，两个等效值。 因此，你可以只需将其属性以减少混乱，或将它保留原样。

  g. **数据源：**这是一个非常重要的属性，指示项目系统的属性值应从该位置从读取和写入和其分组 （如下所述）。 有关 cl.xml，这些值如下：

```xml  
       <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
```  
   - `Persistence="ProjectFile`通知规则的所有属性应都写入项目文件的项目系统或属性表使用的文件 （具体取决于节点已生成的属性页）。 其他可能的值是将值写入.user 文件的"UserFile"。

   - `ItemType="ClCompile"`显示属性，将存储为 ItemDefinition 元数据或 （后者仅当属性页已生成从解决方案资源管理器中的文件节点） 的项元数据的此项类型。 如果未设置此字段，然后会将此属性写 PropertyGroup 中的常见属性。

   - `Label=""`指示当属性都被编写为`ItemDefinition`元数据，父 ItemDefinitionGroup 的标签将为空 （每个 MSBuild 元素可以有标签）。 Visual Studio 2017 使用标记的组来导航.vcxproj 项目文件。 请注意，包含大多数规则属性的组具有一个空字符串作为标签。

   - `HasConfigurationCondition="true"`告知项目系统以粘贴配置条件与值，以便它会仅对当前项目配置 （条件无法附加到父组或值本身） 生效。 例如，打开项目节点关闭属性页并设置属性的值**将警告作为错误**下**配置属性 > C/c + + 常规**为"是"。 下面的值写入项目文件。 请注意配置条件附加到父 ItemDefinitionGroup。

```xml  
     <ItemDefinitionGroup Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">
        <ClCompile>
           <TreatWarningAsError>true</TreatWarningAsError>
        </ClCompile>
     </ItemDefinitionGroup>
 ```
   如果在特定的文件，例如 stdafx.cpp，属性页中设置此值然后将在中的项目文件，如下所示的 stdafx.cpp 项下写入属性值。 请注意如何配置条件直接连接到的元数据本身。

 ```xml  
<ItemGroup>
   <ClCompile Include="stdafx.cpp">
      <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
   </ClCompile>
</ItemGroup>
 ```
   另一个属性**数据源**上面未列出是**PersistedName**。 可以使用此属性来表示使用的不同名称的项目文件中的属性。 默认情况下，此属性设置为该属性的**名称**。 

   单个属性可以重写其父级规则的数据源。 在这种情况下，该属性的值的位置将不同于其他规则中的属性。

   h. 有未在此处显示的一个规则，如说明、 SupportsFileBatching 等其他特性。 可以通过浏览这些类型的文档获取完整的适用的规则或任何其他元素的属性集。 或者，可以检查中的类型上的公共属性`Microsoft.Build.Framework.XamlTypes`中的命名空间`Microsoft.Build.Framework .dll`程序集。

   i. **DisplayName**， **PageTemplate**，和**顺序**不与 UI 相关的属性都存在于这独立于 UI 的数据模型。 这些属性是几乎可以肯定地用于用来显示属性页的任何 UI。 **DisplayName**和**说明**均存在于 xml 文件中的几乎所有元素的两个属性。 这些是已本地化的仅有两个属性和 （本地化这些字符串将更高版本的文章中所述）。

2.  **类别：**规则可以具有多个类别。 在 xml 文件中列出的类别的顺序是到 UI 的建议的相同顺序显示的类别。 例如，在 UI 中所示的 C/c + + 节点下的类别的顺序 – 常规、 优化、 预处理器，...  – 与该在 cl.xml 相同。 示例类别如下所示：

```xml  
 <Category Name="Optimization">
    <Category.DisplayName>
        <sys:String>Optimization</sys:String>
    </Category.DisplayName>
 </Category>
```
上面的代码段显示**名称**和**DisplayName**已之前描述的属性。 同样，有其他特性**类别**可以具有的上面未使用。 通过阅读的文档或通过检查使用 ildasm.exe 的程序集，可以知道有关它们的信息。

3. **属性：**这是 xml 文件的核心内容，其中包含此规则中的所有属性的列表。 每个属性可以是一个在 XAML 上面的主干中所示的五个可能类型。 当然，你可以在你的文件有只有几个这些类型。 属性具有多个允许应用程序具有丰富所述的特性。 我将仅介绍**StringProperty**此处。 其余都非常类似。

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
之前描述了大多数代码段中的属性。 新的是子类型、 类别和交换机。

   a. **子类型**是一个属性仅适用于**StringProperty**和**StringListProperty**; 它提供的上下文信息。 例如，"文件"的值指示该属性表示的文件路径。 此类的上下文信息用于通过提供作为允许用户直观地选择的文件的属性的编辑器的 Windows 资源管理器增强编辑体验。

   b. **类别：**这会将声明在其下此属性所属的类别。 尝试查找此属性在**输出文件**在 UI 中的类别。

   c. **交换机：**当规则表示一个工具 – 例如编译器工具在此情况下 – 大多数规则属性作为交换机期间传递给该工具可执行生成时。 此属性的值指示文本要使用交换机。 上述属性指定应为其交换机**Fo**。 结合**SwitchPrefix**父规则，此属性的属性传递到可执行文件作为**/Fo"调试\"** （在 C/c + + 中的属性页 UI 的命令行中可见）。

   其他属性特性包括：

   d. **可见性：**如果由于某种原因，您不希望属性显示在属性页中 （但在生成期间可能仍然可用），将此属性设置为 false。

   e. **ReadOnly:**如果你想要提供的属性页中的此属性的值的只读视图，则将此属性设置为 true。

   f. **IncludeInCommandLine:**某些属性可能不需要在生成期间要传递给工具。 将此属性设置为 false 将阻止其传递。


