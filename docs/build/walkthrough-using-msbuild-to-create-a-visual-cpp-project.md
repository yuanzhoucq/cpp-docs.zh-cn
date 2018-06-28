---
title: 演练： 使用 MSBuild 创建 Visual c + + 项目 |Microsoft 文档
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.walkthrough.createproject
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b2c5c3f7001a98572129baaf3ee35bb02b6458fd
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041206"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>演练：使用 MSBuild 创建 Visual C++ 项目

本演练演示如何使用 MSBuild 生成 Visual c + + 项目，在命令提示符。 您将学习如何创建 c + + 源代码文件和 Visual c + + 控制台应用程序的基于 XML 的项目文件。 后生成项目时，您将学习如何自定义生成过程。

本演练阐释了以下任务：

- 创建你的项目的 c + + 源文件。

- 创建 XML MSBuild 项目文件。

- 使用 MSBuild 来生成你的项目。

- 使用 MSBuild 以自定义你的项目。

## <a name="prerequisites"></a>系统必备

若要完成本演练，你需要具备以下条件：

- 一份装有 Visual Studio**使用 c + + 桌面开发**安装的工作负荷。

- MSBuild 系统大致了解。

> [!NOTE]
> 如果你想要通过使用 Visual Studio IDE 更高版本编辑项目文件，则不使用此方法。 如果手动创建.vcxproj 文件，Visual Studio IDE 可能不能编辑或加载它，尤其是如果项目在项目项中使用通配符。

> [!NOTE]
> 低级别的生成的指令的大多数都包含在 **.targets**和 **.props**在 VCTargets 目录中，存储在属性中定义的文件`$(VCTargetsPath)`。 在 Visual Studio 自 2017 年 1 Enterprise Edition 中的这些文件的默认路径为 c:\\Program Files (x86)\\Microsoft Visual Studio\\2017年\\企业\\Common7\\IDE\\VC\\VCTargets\\。

## <a name="creating-the-c-source-files"></a>创建 c + + 源文件

在本演练将创建具有源文件和头文件的项目。 源文件 main.cpp 包含控制台应用程序的主函数。 标头文件 main.h 包含代码以包括 iostream 标头文件。 可以通过使用 Visual Studio 或文本如 Visual Studio 代码编辑器创建这些 c + + 文件。

### <a name="to-create-the-c-source-files-for-your-project"></a>若要创建你的项目的 c + + 源文件

1. 创建你的项目的目录。

2. 创建名为 main.cpp 文件并将下面的代码添加到此文件：

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

3. 创建名为 main.h 的文件并将下面的代码添加到此文件：

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>创建 XML MSBuild 项目文件

MSBuild 项目文件是一个包含项目根元素的 XML 文件 (\<项目 >)。 在下面的示例项目中，\<项目 > 元素包含七个子元素：

- 三个项组标记 (\<o u p >)，用于指定项目配置和平台、 源文件名和头文件的名称。

- 三个导入标记 (\<导入 >)，用于指定 Microsoft Visual c + + 设置的位置。

- 属性组标记 (\<PropertyGroup >)，指定项目设置。

### <a name="to-create-the-msbuild-project-file"></a>若要创建 MSBuild 项目文件

1. 使用文本编辑器创建名为的项目文件`myproject.vcxproj`，然后添加以下根\<项目 > 元素。 在根之间以下过程中的步骤中插入元素\<项目 > 标记：

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. 添加以下两个\<ProjectConfiguration > 中的子元素\<o u p > 元素。 子元素指定调试和发布适用于 32 位 Windows 操作系统的配置：

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

3. 添加以下\<导入 / > 元素，用于指定此项目的默认 c + + 设置的路径：

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

4. 添加以下属性组元素 (\<PropertyGroup >)，它指定两个项目属性：

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v141</PlatformToolset>
    </PropertyGroup>
    ```

5. 添加以下\<导入 / > 元素，用于指定此项目的当前 c + + 设置的路径：

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

6. 添加以下\<ClCompile > 中的子元素\<o u p > 元素。 子元素指定要编译的 C/c + + 源文件的名称：

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > \<ClCompile > 是*生成目标*中定义，在**VCTargets**目录。

7. 添加以下\<ClInclude > 中的子元素\<o u p > 元素。 子元素指定的标头文件的 C/c + + 源文件的名称：

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

8. 添加以下\<导入 > 元素，它指定定义此项目的目标的文件的路径：

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>完成项目文件

下面的代码演示了你在前面的过程中创建的完整项目文件。

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

## <a name="using-msbuild-to-build-your-project"></a>使用 MSBuild 生成你的项目

生成控制台应用程序的命令提示符处键入以下命令：

`msbuild myproject.vcxproj /p:configuration=debug`

MSBuild 为输出文件中，创建目录然后编译并链接你的项目以生成 Myproject.exe 程序。 生成过程完成后，使用以下命令运行该应用程序：

`myproject`

应用程序应显示"Hello，从 MSBuild ！" 显示文本字符串“Hello World!”。

## <a name="customizing-your-project"></a>自定义项目

MSBuild，可执行预定义的生成目标、 应用用户定义的属性，并使用自定义工具，事件，或生成步骤。 本部分阐释了以下任务：

- MSBuild 使用生成目标。

- 生成属性中使用 MSBuild。

- 使用 MSBuild 使用 64 位编译器和工具。

- MSBuild 使用不同的工具集。

- 将添加 MSBuild 自定义项。

### <a name="using-msbuild-with-build-targets"></a>MSBuild 使用生成目标

A*生成目标*是一组命名的预定义的或用户定义可以在生成期间执行的命令。 使用目标命令行选项 (**/t**) 指定了生成目标。 情况下`myproject`示例项目的预定义**干净**目标删除的调试文件夹中的所有文件并创建一个新的日志文件。

在命令提示符下键入以下命令以清除`myproject`。

`msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>MSBuild 使用生成属性

属性的命令行选项 (**/p**) 使你可以覆盖项目生成文件中的属性。 在`myproject`示例项目、 版本或调试生成配置指定通过`Configuration`属性。 指定用于运行生成的应用程序的操作系统和`Platform`属性。

在命令提示符下键入以下命令以创建的调试版本`myproject`旨在在 32 位 Windows 上运行的应用程序。

`msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

假定`myproject`项目还为 64 位 Windows，以及另一个名为自定义操作系统配置中定义的配置示例`myplatform`。

在命令提示符下，在 64 位 Windows 上运行以下命令以创建版本生成的类型。

`msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

在命令提示符下键入以下命令以创建发行版本的`myplatform`。

`msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>使用 64 位编译器和工具使用 MSBuild

如果你已在 64 位 Windows 上安装 Visual c + +，默认情况下，会安装 64 位 x64 本机编译和跨平台工具。 你可以配置使用 64 位编译器和工具来生成应用程序通过设置 MSBuild`PreferredToolArchitecture`属性。 此属性不会影响的项目配置或平台属性。 默认情况下，使用这些工具的 32 位版本。 若要指定的编译器和工具的 64 位版本，请将以下属性组元素添加到 Myproject.vcxproj 项目文件后`Microsoft.Cpp.default.props`\<导入 / > 元素：

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

在命令提示符下键入以下命令以使用 64 位工具来生成应用程序。

`msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>MSBuild 使用不同的工具集

如果你有的工具集和其他版本的 Visual c + + 安装的库，MSBuild 可以生成有关最新 Visual c + + 版本或其他已安装版本的应用程序。 例如，如果你已安装[!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)]，若要为 Windows XP 中指定的 Visual c + + 11.0 工具集，添加以下属性组元素 Myproject.vcxproj 项目文件后 Microsoft.Cpp.props`<Import />`元素：

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

若要重新生成你的项目与 Visual c + + 11.0 Windows XP 工具集，请键入以下命令之一：

`msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

`msbuild myproject.vcxproj /t:rebuild`

### <a name="adding-msbuild-customizations"></a>将添加 MSBuild 自定义项

MSBuild 提供自定义生成过程的各种方法。 以下主题演示如何向 MSBuild 项目中添加自定义生成步骤、 工具和事件：

- [如何：向 MSBuild 项目添加自定义生成步骤](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [如何：向 MSBuild 项目添加自定义生成工具](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)

- [如何：在 MSBuild 项目中使用生成事件](../build/how-to-use-build-events-in-msbuild-projects.md)
