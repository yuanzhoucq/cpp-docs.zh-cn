---
title: 演练：使用 MSBuild 创建 Visual c + + 项目
ms.date: 09/24/2018
f1_keywords:
- msbuild.cpp.walkthrough.createproject
helpviewer_keywords:
- 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
ms.openlocfilehash: c7b038ede8c03f7016c5e9f81a9db785c49da448
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2019
ms.locfileid: "57813911"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>演练：使用 MSBuild 创建 Visual c + + 项目

本演练演示如何使用 MSBuild 生成 Visual c + + 项目的命令提示符处。 您将了解如何创建 c + + 源代码文件和 Visual c + + 控制台应用程序的基于 XML 的项目文件。 后生成项目时，将了解如何自定义生成过程。

本演练阐释了以下任务：

- 正在创建你的项目的 c + + 源代码文件。

- 创建 XML MSBuild 项目文件。

- 使用 MSBuild 生成项目。

- 使用 MSBuild 自定义你的项目。

## <a name="prerequisites"></a>系统必备

若要完成本演练，你需要具备以下条件：

- Visual Studio 中使用一份**使用 c + + 的桌面开发**安装工作负载。

- 大致了解 MSBuild 系统。

> [!NOTE]
> 如果你想要更高版本通过使用 Visual Studio IDE 中编辑项目文件，则不使用此方法。 如果手动创建.vcxproj 文件，Visual Studio IDE 可能不能编辑或加载它，尤其是如果该项目在项目项中使用通配符。

> [!NOTE]
> 大多数低级别构建说明包含在 **.targets**并 **.props**属性中存储的 VCTargets 目录中定义的文件`$(VCTargetsPath)`。 这些文件在 Visual Studio 2017 Enterprise Edition 中的默认路径为 c:\\Program Files (x86)\\Microsoft Visual Studio\\2017年\\企业\\Common7\\IDE\\VC\\VCTargets\\。

## <a name="creating-the-c-source-files"></a>创建 c + + 源文件

在本演练中，将创建具有源文件和头文件的项目。 源文件 main.cpp 包含控制台应用程序的主函数。 标头文件 main.h 包含代码以包括 iostream 标头文件。 可以通过使用 Visual Studio 或文本编辑器 （如 Visual Studio Code） 创建这些 c + + 文件。

### <a name="to-create-the-c-source-files-for-your-project"></a>若要创建你的项目的 c + + 源代码文件

1. 创建你的项目的目录。

1. 创建名为 main.cpp 的文件并将以下代码添加到此文件：

    ```cpp
    // main.cpp : the application source code.
    #include <iostream>
    #include "main.h"
    int main()
    {
       std::cout << "Hello, from MSBuild!\n";
       return 0;
    }
    ```

1. 创建名为 main.h 的文件并将以下代码添加到此文件：

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>创建 XML MSBuild 项目文件

MSBuild 项目文件是一个包含项目根元素的 XML 文件 (`<Project>`)。 在下面的示例项目中，`<Project>`元素包含七个子元素：

- 三个项组标记 (`<ItemGroup>`)，用于指定项目配置和平台、 源文件名和头文件的名称。

- 三个导入标记 (`<Import>`)，用于指定 Microsoft Visual c + + 设置的位置。

- 属性组标记 (`<PropertyGroup>`)，指定项目设置。

### <a name="to-create-the-msbuild-project-file"></a>若要创建 MSBuild 项目文件

1. 使用文本编辑器创建名为的项目文件`myproject.vcxproj`，然后添加以下根`<Project>`元素。 在以下过程步骤根目录之间中插入元素`<Project>`标记：

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

1. 添加以下两个`<ProjectConfiguration>`中的子元素`<ItemGroup>`元素。 子元素指定调试和发布适用于 32 位 Windows 操作系统的配置：

    ```xml
    <ItemGroup>
      <ProjectConfiguration Include="Debug|Win32">
        <Configuration>Debug</Configuration>
        <Platform>Win32</Platform>
      </ProjectConfiguration>
      <ProjectConfiguration Include="Release|Win32">
        <Configuration>Release</Configuration>
        <Platform>Win32</Platform>
      </ProjectConfiguration>
    </ItemGroup>
    ```

1. 以下代码添加到`<Import>`元素，它指定此项目的默认 c + + 设置的路径：

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

1. 添加以下属性组元素 (`<PropertyGroup>`)，它指定两个项目属性：

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v141</PlatformToolset>
    </PropertyGroup>
    ```

1. 以下代码添加到`<Import>`元素，用于指定此项目的当前 c + + 设置的路径：

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

1. 添加以下`<ClCompile>`中的子元素`<ItemGroup>`元素。 子元素指定要编译的 C/c + + 源文件的名称：

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > `<ClCompile>` 是*构建面向*中定义， **VCTargets**目录。

1. 添加以下`<ClInclude>`中的子元素`<ItemGroup>`元素。 子元素指定 C/c + + 源代码文件的标头文件的名称：

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

1. 以下代码添加到`<Import>`元素，它指定定义此项目的目标的文件的路径：

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>完整的项目文件

下面的代码演示在上一过程中创建完整的项目文件。

```xml
<Project DefaultTargets="Build" ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <ProjectConfiguration Include="Debug|Win32">
      <Configuration>Debug</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|Win32">
      <Configuration>Release</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
  <PropertyGroup>
    <ConfigurationType>Application</ConfigurationType>
    <PlatformToolset>v141</PlatformToolset>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ItemGroup>
    <ClCompile Include="main.cpp" />
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="main.h" />
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
</Project>
```

## <a name="using-msbuild-to-build-your-project"></a>使用 MSBuild 生成项目

若要生成控制台应用程序的命令提示符处键入以下命令：

`msbuild myproject.vcxproj /p:configuration=debug`

MSBuild 创建目录的输出文件，然后编译并链接项目以生成 Myproject.exe 程序。 生成过程完成后，使用以下命令从 debug 文件夹中运行应用程序：

`myproject`

应用程序应显示"Hello，from MSBuild ！" 显示文本字符串“Hello World!”。

## <a name="customizing-your-project"></a>自定义项目

MSBuild，可执行预定义的生成的目标、 应用用户定义的属性，并使用自定义的工具、 事件和生成步骤。 本部分阐释了以下任务：

- 将 MSBuild 用于生成目标。

- 与生成属性结合使用 MSBuild。

- 使用 MSBuild 的 64 位编译器和工具。

- 将 MSBuild 用于不同的工具集。

- 添加 MSBuild 自定义项。

### <a name="using-msbuild-with-build-targets"></a>将 MSBuild 用于生成目标

一个*构建目标*是一组命名的预定义或用户定义可以在生成期间执行的命令。 使用目标命令行选项 (`/t`) 指定了生成目标。 有关`myproject`示例项目，在预定义**干净**目标删除调试文件夹中的所有文件并创建新的日志文件。

在命令提示符下键入以下命令以清理`myproject`。

`msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>将 MSBuild 用于生成属性

属性命令行选项 (`/p`) 使你可以覆盖在项目生成文件中的属性。 在中`myproject`示例项目、 发布或调试生成配置指定由`Configuration`属性。 指定用于运行生成的应用程序的操作系统和`Platform`属性。

在命令提示符下键入以下命令创建的调试版本`myproject`只应在 32 位 Windows 上运行的应用程序。

`msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

假定`myproject`示例项目还定义了配置的 64 位 Windows 和另一个名为自定义操作系统配置`myplatform`。

在命令提示符下，在 64 位 Windows 上运行以下命令以创建版本生成的类型。

`msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

在命令提示符下键入以下命令以创建版本生成的`myplatform`。

`msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>使用 MSBuild 的 64 位编译器和工具

如果已在 64 位 Windows 上安装 Visual c + +，默认情况下，将安装 64 位 x64 本机和跨工具。 您可以将 MSBuild 配置为使用 64 位编译器和工具来生成应用程序通过设置`PreferredToolArchitecture`属性。 此属性不会影响项目配置或平台属性。 默认情况下，使用这些工具的 32 位版本。 若要指定的编译器和工具的 64 位版本，请将以下属性组元素添加到后的 Myproject.vcxproj 项目文件`Microsoft.Cpp.default.props`\<导入 / > 元素：

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

在命令提示符下键入以下命令以使用 64 位工具生成应用程序。

`msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>将 MSBuild 用于不同的工具集

如果你具有的工具集和其他版本的 Visual c + + 安装的库，MSBuild 可以生成有关最新 Visual c + + 版本或其他已安装版本的应用程序。 例如，如果你已安装 Visual Studio 2012 Visual c + + 11.0 工具集指定为 Windows XP 中，将以下属性组元素添加到后的 Myproject.vcxproj 项目文件`Microsoft.Cpp.props`\<导入 / > 元素：

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

若要重新生成你的项目的 Visual c + + 11.0 Windows XP 工具集，请键入以下命令：

`msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

### <a name="adding-msbuild-customizations"></a>添加 MSBuild 自定义项

MSBuild 提供了多种自定义生成过程。 以下主题说明如何向 MSBuild 项目中添加自定义生成步骤、 工具和事件：

- [如何：向 MSBuild 项目添加自定义生成步骤](how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [如何：向 MSBuild 项目添加自定义生成工具](how-to-add-custom-build-tools-to-msbuild-projects.md)

- [如何：在 MSBuild 项目中使用生成事件](how-to-use-build-events-in-msbuild-projects.md)
