---
title: 演练：使用 MSBuild 创建 Visual C++ 项目
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
ms.openlocfilehash: c93867f3be3b17f703c549aa5c05f3d327934c26
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422714"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>演练：使用 MSBuild 创建 Visual C++ 项目

此演练演示如何使用 MSBuild 在命令提示符中生成 Visual Studio C++ 项目。 你将了解如何为 Visual C++ 控制台应用程序创建 C++ 源文件和基于 XML 的项目文件。 生成该项目后，你将了解如何对生成过程进行自定义。

本演练阐释了以下任务：

- 为项目创建 C++ 源文件。

- 创建 XML MSBuild 项目文件。

- 使用 MSBuild 生成项目。

- 使用 MSBuild 自定义项目。

## <a name="prerequisites"></a>先决条件

若要完成本演练，你需要具备以下条件：

- 需安装 Visual Studio 的副本，并安装“使用 C++ 的桌面开发”工作负载  。

- 对 MSBuild 系统有大致的了解。

> [!NOTE]
> 如果以后想通过使用 Visual Studio IDE 编辑项目文件，请勿采用此方法。 如果手动创建 .vcxproj 文件，Visual Studio IDE 可能无法编辑或加载该文件，尤其是在项目在项目项中使用通配符时。

> [!NOTE]
> 大多数低级别的生成说明都包含在 .targets 和 .props 文件中，这些文件是在 VCTargets 目录中定义的，存储在属性 `$(VCTargetsPath)` 中   。 这些文件在 Visual Studio 2019 Enterprise Edition 中的默认路径为 C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\MSBuild\Microsoft\VC\v160\Microsoft.Cpp.Common.props。

## <a name="creating-the-c-source-files"></a>创建 C++ 源文件

在本演练中，将创建具有源文件和头文件的项目。 源文件 main.cpp 包含控制台应用程序的主函数。 头文件 main.h 包含代码以包括 iostream 头文件。 可以通过使用 Visual Studio 或类似 Visual Studio Code 的文本编辑器来创建这些 C++ 文件。

### <a name="to-create-the-c-source-files-for-your-project"></a>为项目创建 C++ 源文件

1. 为项目创建目录。

1. 创建一个名为 main.cpp 的文件，并将以下代码添加到此文件：

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

1. 创建一个名为 main.h 的文件，并将以下代码添加到此文件：

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>创建 XML MSBuild 项目文件

MSBuild 项目文件是一个包含项目根元素 (`<Project>`) 的 XML 文件。 在下面的示例项目中，`<Project>` 元素包含七个子元素：

- 三个项组标记 (`<ItemGroup>`)，用于指定项目配置和平台、源文件名和头文件名。

- 三个导入标记 (`<Import>`)，用于指定 Microsoft Visual C++ 设置的位置。

- 一个属性组标记 (`<PropertyGroup>`)，用于指定项目设置。

### <a name="to-create-the-msbuild-project-file"></a>创建 MSBuild 项目文件

1. 使用文本编辑器创建名为 `myproject.vcxproj` 的项目文件，然后添加以下根 `<Project>` 元素。 在以下过程步骤中，将这些元素插入根 `<Project>` 标记之间。 （如果使用 Visual Studio 2017，请采用 ToolsVersion="15.0"；如果使用 Visual Studio 2019，请采用 ToolsVersion="16.0"。）

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

1. 在 `<ItemGroup>` 元素中添加以下两个 `<ProjectConfiguration>` 子元素。 该子元素指定 32 位 Windows 操作系统的调试和发布配置：

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

1. 添加以下 `<Import>` 元素，该元素指定此项目的默认 C++ 设置的路径：

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

1. 添加以下属性组元素 (`<PropertyGroup>`)，该元素指定两个项目属性。 （如果使用 Visual Studio 2017，请采用 v141；如果使请 Visual Studio 2019，则采用 v142。）

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v142</PlatformToolset>
    </PropertyGroup>
    ```

1. 添加以下 `<Import>` 元素，该元素指定此项目的当前 C++ 设置的路径：

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

1. 在 `<ItemGroup>` 元素中添加以下 `<ClCompile>` 子元素。 该子元素指定要编译的 C/C++ 源文件的名称：

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > `<ClCompile>` 是生成目标，且在 VCTargets 目录中进行定义   。

1. 在 `<ItemGroup>` 元素中添加以下 `<ClInclude>` 子元素。 该子元素指定 C/C++ 源文件的头文件的名称：

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

1. 添加以下 `<Import>` 元素，该元素指定定义此项目的目标的文件的路径：

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>完整的项目文件

以下代码演示在上一过程中创建的完整项目文件。 （如果使用 Visual Studio 2017，请采用 ToolsVersion="15.0"。）

```xml
<Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
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
    <PlatformToolset>v142</PlatformToolset>
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

在命令提示符处键入以下命令以生成控制台应用程序：

`msbuild myproject.vcxproj /p:configuration=debug`

MSBuild 创建输出文件的命令，然后编译并链接项目以生成 Myproject.exe 程序。 完成生成过程后，请使用以下命令从 debug 文件夹中运行应用程序：

`myproject`

该应用程序应在控制台窗口中 显示文本字符串“Hello World!”。

## <a name="customizing-your-project"></a>对项目进行自定义

使用 MSBuild，可以执行预定义的生成目标、应用用户定义的属性并使用自定义工具、事件和生成步骤。 本部分阐释了以下任务：

- 将 MSBuild 和生成目标配合使用。

- 将 MSBuild 和生成属性配合使用。

- 将 MSBuild 和 64 位编译器和工具配合使用。

- 将 MSBuild 和不同的工具集配合使用。

- 添加 MSBuild 自定义项。

### <a name="using-msbuild-with-build-targets"></a>将 MSBuild 和生成目标配合使用

“生成目标”是一组命名的预定义或用户定义的命令，可以在生成期间执行这些命令  。 使用目标命令行选项 (`/t`) 以指定生成目标。 对于 `myproject` 示例项目，预定义的清理目标删除调试文件夹中的所有文件，并创建新的日志文件  。

在命令提示符处，键入下列命令以清理 `myproject`。

`msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>将 MSBuild 和生成属性配合使用

使用属性命令行选项 (`/p`)，可以覆盖项目生成文件中的属性。 在 `myproject` 示例项目中，发布或调试生成配置是由 `Configuration` 属性指定的。 而要运行生成的应用程序的操作系统是由 `Platform` 属性指定的。

在命令提示符处键入以下命令，创建要在 32 位 Windows 上运行的 `myproject` 应用程序的调试版本。

`msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

假设 `myproject` 示例项目还定义了 64 位 Windows 的配置，以及另外一个用于自定义操作系统 `myplatform` 的配置。

在命令提示符处键入以下命令，创建在 64 位 Windows 上运行的发布版本。

`msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

在命令提示符处键入以下命令，为 `myplatform` 创建发布版本。

`msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>将 MSBuild 和 64 位编译器和工具配合使用

在默认情况下，如果在 64 位 Windows 上安装了 Visual Studio，则会安装 64 位 x64 本机和兼容工具。 可以配置 MSBuild，通过设置 `PreferredToolArchitecture` 属性以使用 64 位编译器和工具来生成自己的应用程序。 此属性不会影响项目配置或平台属性。 默认采用 32 位版本的工具。 要指定 64 位版本的编译器和工具，请将以下属性组元素添加到 Myproject.vcxproj 文件，添加在 `Microsoft.Cpp.default.props` \<Import /> 元素之后：

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

在命令提示符处键入以下命令，使用 64 位工具生成应用程序。

`msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>将 MSBuild 和不同的工具集配合使用

如果安装了其他版本的 Visual C++ 的工具集和库，则 MSBuild 可以针对当前 Visual C++ 版本或已安装的其他版本生成应用程序。 例如，如果已安装 Visual Studio 2012 且要指定 Windows XP 的 Visual C++ 11.0 工具集，请将以下属性组元素添加到 Myproject.vcxproj 文件，添加在 `Microsoft.Cpp.props` \<Import /> 元素之后：

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

若要使用 Visual C++ 11.0 Windows XP 工具集重新生成项目，请键入以下命令：

`msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

### <a name="adding-msbuild-customizations"></a>添加 MSBuild 自定义项

MSBuild 提供了多种自定义生成过程的方式。 以下主题介绍如何向 MSBuild 项目添加自定义生成步骤、工具和事件：

- [如何：向 MSBuild 项目添加自定义生成步骤](how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [如何：向 MSBuild 项目添加自定义生成工具](how-to-add-custom-build-tools-to-msbuild-projects.md)

- [如何：在 MSBuild 项目中使用生成事件](how-to-use-build-events-in-msbuild-projects.md)
