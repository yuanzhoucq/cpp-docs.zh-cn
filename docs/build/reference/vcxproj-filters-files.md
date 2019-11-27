---
title: .vcxproj 文件
ms.date: 09/25/2019
description: 使用 Visual Studio C++项目中的筛选器文件为中的文件定义自定义逻辑文件夹解决方案资源管理器
helpviewer_keywords:
- vcxproj.filters
- filters file [C++]
ms.openlocfilehash: ee44bf3d1cbe06d6c007ed8976ec384a456efca5
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686922"
---
# <a name="vcxprojfilters-files"></a>.vcxproj 文件

*筛选器*文件（\*.vcxproj）是一个采用 MSBuild 格式的 XML 文件，位于根项目文件夹中。 它指定哪些文件类型将进入**解决方案资源管理器**的逻辑文件夹。 在下图中， *.cpp*文件位于 "**源文件**" 节点下。 *.h*文件位于 "**头文件**" 节点下， *.ico*和 *.rc*文件位于 "**资源文件**" 下。 此位置由筛选器文件控制。

![解决方案资源管理器中的逻辑文件夹](media/solution-explorer-filters.png)

## <a name="creating-a-custom-filters-file"></a>创建自定义筛选器文件

Visual Studio 会自动创建此文件。 对于桌面应用程序，预定义的逻辑文件夹（筛选器）为：**源文件**、**头文件**和**资源文件**。 其他项目类型（例如 UWP）可能具有一组不同的默认文件夹。 Visual Studio 会自动将已知的文件类型分配给每个文件夹。 如果要使用自定义名称或包含自定义文件类型的筛选器创建筛选器，则可以在项目的根文件夹中或在现有筛选器下创建自己的筛选器文件。 （**引用**和**外部依赖项**是不参与筛选的特殊文件夹。）

## <a name="example"></a>示例

下面的示例演示前面的示例显示的筛选器文件。 它具有平面层次结构;换句话说，没有嵌套的逻辑文件夹。 `UniqueIdentifier` 节点是可选的。 它使 Visual Studio 自动化接口能够查找筛选器。 `Extensions` 也是可选的。 将新文件添加到项目时，会将其添加到具有匹配文件扩展名的最顶层筛选器中。 若要将文件添加到特定筛选器，请右键单击该筛选器，然后选择 "**添加新项**"。

首次启动项目时，将创建包含 `ClInclude` 节点的 `ItemGroup`。 如果要生成自己的 .vcxproj 文件，请确保所有项目项在筛选器文件中也有一个条目。 `ClInclude` 节点中的值将基于文件扩展名覆盖默认筛选。 使用 Visual Studio 向项目添加新项时，IDE 将在筛选器文件中添加单个文件项。 如果更改文件扩展名，则不会自动重新分配筛选器。 

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Filter Include="Source Files">
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier>
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions>
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
    <Filter Include="Resource Files">
      <UniqueIdentifier>{67DA6AB6-F800-4c08-8B7A-83BB121AAD01}</UniqueIdentifier>
      <Extensions>rc;ico;cur;bmp;dlg;rc2;rct;bin;rgs;gif;jpg;jpeg;jpe;resx;tiff;tif;png;wav;mfcribbon-ms</Extensions>
    </Filter>
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="MFCApplication1.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="MFCApplication1Dlg.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="stdafx.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="targetver.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="Resource.h">
      <Filter>Header Files</Filter>
    </ClInclude>
  </ItemGroup>
  <ItemGroup>
    <ClCompile Include="MFCApplication1.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="MFCApplication1Dlg.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="stdafx.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
  </ItemGroup>
  <ItemGroup>
    <ResourceCompile Include="MFCApplication1.rc">
      <Filter>Resource Files</Filter>
    </ResourceCompile>
  </ItemGroup>
  <ItemGroup>
    <None Include="res\MFCApplication1.rc2">
      <Filter>Resource Files</Filter>
    </None>
  </ItemGroup>
  <ItemGroup>
    <Image Include="res\MFCApplication1.ico">
      <Filter>Resource Files</Filter>
    </Image>
  </ItemGroup>
</Project>
```

若要创建嵌套逻辑文件夹，请在筛选器中声明所有节点 `ItemGroup` 如下所示。 每个子节点必须声明最顶层父节点的完整逻辑路径。 在下面的示例中，必须声明空的 `ParentFilter`，因为在以后的节点中引用了该。

```xml
  <ItemGroup>
    <Filter Include="ParentFilter">
    </Filter>
    <Filter Include="ParentFilter\Source Files"> <!-- Full path to topmost parent.-->  
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier> <!--  Optional-->
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions> <!-- Optional -->
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
  </ItemGroup>
```

