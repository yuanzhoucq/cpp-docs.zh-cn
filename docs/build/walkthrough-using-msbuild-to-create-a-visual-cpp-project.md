---
title: "演练：使用 MSBuild 创建 Visual C++ 项目 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msbuild.cpp.walkthrough.createproject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (c++), 演练：创建项目"
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
caps.latest.revision: 27
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 演练：使用 MSBuild 创建 Visual C++ 项目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此演练演示如何在命令提示符处使用 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 生成 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 项目。  您将学习如何为 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 控制台应用程序创建 C\+\+ 源文件和基于 XML 的项目文件。  生成项目后，您将学习如何自定义生成过程。  
  
 本演练阐释了以下任务：  
  
-   为项目创建 C\+\+ 源文件。  
  
-   创建 XML [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 项目文件。  
  
-   使用 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 生成项目。  
  
-   使用 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 自定义项目。  
  
## 系统必备  
 要完成本演练，您需要：  
  
-   [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]  
  
-   大概了解 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 系统。  
  
## 创建 C\+\+ 源文件  
 在本演练中，您将创建一个具有源文件和头文件的项目。  源文件 main.cpp 包含控制台应用程序的主要功能。  头文件 main.h 包含用于纳入 iostream 头文件的代码。  您可以使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 或文本编辑器创建这些 C\+\+ 文件。  
  
#### 为项目创建 C\+\+ 源文件  
  
1.  为项目创建目录。  
  
2.  创建一个名为 main.cpp 的文件并将以下代码添加到该文件中：  
  
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
  
3.  创建一个名为 main.h 的文件并将以下代码添加到该文件中：  
  
    ```hlsl  
    // main.h: the application header code.  
    /* Additional source code to include. */  
    ```  
  
## 创建 XML MSBuild 项目文件  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 项目文件是一个包含项目根元素 \(\<Project\>\) 的 XML 文件。  在以下示例项目中，\<Project\> 元素包含七个子元素：  
  
-   三个项组标记 \(\<ItemGroup\>\)，用于指定项目配置和平台、源文件名以及头文件名。  
  
-   三个导入标记 \(\<Import\>\)，用于指定 Microsoft [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 设置的位置。  
  
-   一个属性组标记 \(\<PropertyGroup\>\)，用于指定项目设置。  
  
#### 创建 MSBuild 项目文件  
  
1.  使用文本编辑器创建名为 `myproject.vcxproj` 的项目文件，然后添加以下根 \<Project\> 元素。  在根 \<Project\> 标记之间插入以下过程步骤中的元素：  
  
    ```xml  
    <Project DefaultTargets="Build" ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    </Project>  
    ```  
  
2.  在 \<ItemGroup\> 元素中添加以下两个 \<ProjectConfiguration\> 子元素。  子元素为 32 位 Windows 操作系统指定调试配置和发布配置：  
  
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
  
3.  添加以下 \<Import\/\> 元素，该元素为此项目指定默认 C\+\+ 设置的路径：  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />  
  
    ```  
  
4.  添加以下属性组元素 \(\<PropertyGroup\>\)，该元素指定两个项目属性：  
  
    ```xml  
    <PropertyGroup>  
      <ConfigurationType>Application</ConfigurationType>  
      <PlatformToolset>v120</PlatformToolset>  
    </PropertyGroup>  
    ```  
  
5.  添加以下 \<Import\/\> 元素，该元素为此项目指定当前 C\+\+ 设置的路径：  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />  
    ```  
  
6.  在 \<ItemGroup\> 元素中添加以下 \<ClCompile\> 子元素。  该子元素指定要编译的 C\/C\+\+ 源文件的名称：  
  
    ```xml  
    <ItemGroup>  
      <ClCompile Include="main.cpp" />  
    </ItemGroup>  
    ```  
  
7.  在 \<ItemGroup\> 元素中添加以下 \<ClInclude\> 子元素。  该子元素为 C\/C\+\+ 源文件指定头文件的名称：  
  
    ```xml  
    <ItemGroup>  
      <ClInclude Include="main.h" />  
    </ItemGroup>  
    ```  
  
8.  添加以下 \<Import\> 元素，该元素指定为此项目定义目标的文件的路径：  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />  
  
    ```  
  
### 完整的项目文件  
 以下代码显示了在上一个过程中创建的完整的项目文件。  
  
```xml  
<Project DefaultTargets="Build" ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
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
    <PlatformToolset>v120</PlatformToolset>  
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
  
## 使用 MSBuild 生成项目  
 在命令提示符处键入以下命令以生成控制台应用程序：  
  
```  
msbuild myproject.vcxproj /p:configuration=debug  
```  
  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 将为输出文件创建目录，然后编译并链接项目以生成 Myproject.exe 程序。  生成过程完成之后，请使用以下命令运行该应用程序：  
  
```  
myproject  
```  
  
 该应用程序在控制台窗口中应该显示“Hello, from MSBuild\!”。  
  
## 自定义您的项目  
 通过 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]，您可以执行预定义的生成目标，应用用户定义的属性，以及使用自定义的工具、事件和生成步骤。  本节阐释了以下任务：  
  
-   将 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 与生成目标结合使用。  
  
-   将 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 与生成属性结合使用。  
  
-   使用带有 64 位编译器和工具的 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]。  
  
-   将 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 与不同的工具集结合使用。  
  
-   添加 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 自定义项。  
  
### 将 MSBuild 与生成目标结合使用  
 生成目标是指定的一组预定义命令或用户定义的命令，这组命令可在生成期间执行。  使用目标命令行选项 \(**\/t**\) 可以指定生成目标。  对于 `myproject` 示例项目，预定义的 **clean** 目标将删除调试文件夹中的所有文件并创建新日志文件。  
  
 在命令提示符处，键入以下命令以清理 `myproject`。  
  
 `msbuild myproject.vcxproj /t:clean`  
  
### 将 MSBuild 与生成属性结合使用  
 通过使用属性命令行选项 \(**\/p**\)，您可以在项目生成文件中重写属性。  在 `myproject` 示例项目中，发布版本配置或调试版本配置是由 `Configuration` 属性指定的。  用来运行生成的应用程序的操作系统是由 `Platform` 属性指定的。  
  
 在命令提示符处，键入以下命令，以创建打算在 32 位 Windows 上运行的 `myproject` 应用程序的调试版本。  
  
 `msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`  
  
 假设 `myproject` 示例项目也为 64 位 Windows 定义了配置，并为名为 `myplatform` 的自定义操作系统定义了另一个配置。  
  
 在命令提示符处，键入以下命令，以创建在 64 位 Windows 上运行的发布版本。  
  
 `msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`  
  
 在命令提示符处，键入以下命令以为 `myplatform` 创建发布版本。  
  
 `msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`  
  
### 使用带有 64 位编译器和工具的 MSBuild  
 如果已在 64 位 Windows 上安装了 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)]，默认情况下，将安装 64 位 x64 本机和兼容工具。  可配置 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]，使用 64 位编译器和工具以通过设置 `PreferredToolArchitecture` 属性来生成应用程序。  此属性不影响项目配置或平台属性。  默认情况下使用该工具的 32 位版本。  如要指定编辑器和工具的 64 位版本，请将以下属性组元素添加到 `Microsoft.Cpp.default.props` \<导入\/\>元素之后的 Myproject.vcxproj 项目文件中：  
  
```xml  
<PropertyGroup>  
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>  
</PropertyGroup>  
```  
  
 在命令提示符处，键入以下命令以使用 64 位工具生成应用程序。  
  
 `msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### 将 MSBuild 与不同的工具集结合使用  
 如果您已安装适用于 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 的其他版本的工具集和库，[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 则可以生成适用于当前 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 版本或其他已安装版本的应用程序。  例如，如果您已安装了 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)]，为对 Windows XP 指定 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 11.0 工具集，请将以下属性组元素添加到位于 Microsoft.Cpp.props `<Import />` 元素后的 Myproject.vcxproj 项目文件中：  
  
```xml  
<PropertyGroup>  
    <PlatformToolset>v110_xp</PlatformToolset>  
</PropertyGroup>  
```  
  
 若要使用 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 11.0 Windows XP 工具集重新生成您的项目，请键入以下任何一条命令：  
  
 `msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`  
  
 `msbuild myproject.vcxproj /t:rebuild`  
  
### 添加 MSBuild 自定义项  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 提供了自定义生成过程的不同方式。  以下主题演示如何向 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 项目添加自定义的生成步骤、工具和事件。  
  
-   [如何：向 MSBuild 项目添加自定义生成步骤](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)  
  
-   [如何：向 MSBuild 项目添加自定义生成工具](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)  
  
-   [如何：在 MSBuild 项目中使用生成事件](../build/how-to-use-build-events-in-msbuild-projects.md)