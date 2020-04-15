---
title: Vcxproj.过滤器文件
ms.date: 09/25/2019
description: 使用 Visual Studio 中的筛选器文件C++项目为解决方案资源管理器中的文件定义自定义逻辑文件夹
helpviewer_keywords:
- vcxproj.filters
- filters file [C++]
ms.openlocfilehash: 57735246b543680243994b99b8c05c9ad1211f38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335932"
---
# <a name="vcxprojfilters-files"></a>vcxproj.过滤器文件

*筛选器*文件 （.vcxproj.filters）\*是位于根项目文件夹中的 MSBuild 格式的 XML 文件。 它指定解决方案**资源管理器**中的逻辑文件夹中进入哪些文件类型。 在下图中 *，.cpp*文件位于**源文件**节点下。 *.h*文件位于 **"标题文件"** 节点下 *，.ico*和 *.rc*文件位于**资源文件**下。 此放置由筛选器文件控制。

![解决方案资源管理器中的逻辑文件夹](media/solution-explorer-filters.png)

## <a name="creating-a-custom-filters-file"></a>创建自定义筛选器文件

可视化工作室会自动创建此文件。 对于桌面应用程序，预定义的逻辑文件夹（筛选器）是：**源文件**、**标题**文件**和资源文件**。 其他项目类型（如 UWP）可能具有一组不同的默认文件夹。 Visual Studio 会自动为每个文件夹分配已知的文件类型。 如果要使用自定义名称或包含自定义文件类型的筛选器创建筛选器，则可以在项目的根文件夹中或现有筛选器下创建自己的筛选器文件。 （**引用**和**外部依赖项**是不参与筛选的特殊文件夹。

## <a name="example"></a>示例

下面的示例显示示例之前显示的筛选器文件。 它有一个平面层次结构;换句话说，没有嵌套的逻辑文件夹。 `UniqueIdentifier` 节点是可选的。 它使 Visual Studio 自动化界面能够找到筛选器。 `Extensions`也是可选的。 将新文件添加到项目时，该文件将添加到具有匹配文件扩展名的最顶层筛选器中。 要将文件添加到特定筛选器，请右键单击筛选器并选择"**添加新项目**"。

在`ItemGroup`首次启动项目时`ClInclude`创建包含节点的 。 如果要生成自己的 vcxproj 文件，请确保所有项目项在筛选器文件中也有条目。 节点中`ClInclude`的值将覆盖基于文件扩展名的默认筛选。 当您使用 Visual Studio 向项目添加新项时，IDE 将在筛选器文件中添加单个文件条目。 如果更改文件的扩展名，则不会自动重新分配筛选器。

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

要创建嵌套逻辑文件夹，请声明筛选器中的所有节点`ItemGroup`，如下所示。 每个子节点必须将完整的逻辑路径声明为最上面的父节点。 在下面的示例中，必须声明空`ParentFilter`，因为它在后面的节点中引用。

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
