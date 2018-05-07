---
title: 项目文件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .vcproj files
- Visual C++ projects, project file format
- VCPROJ (Visual C++ project file) format
- project files [C++], .vcproj file format
ms.assetid: 5261cf45-3136-40a6-899e-dc1339551401
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e66d6e94e4938c72adc5aea1a478ce6c0658e56e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="project-files"></a>项目文件
Visual c + + 项目文件是一个基于 XML 的文件具有.vcxproj 文件扩展名，并且包含生成的 Visual c + + 项目所需的信息。  
  
## <a name="example"></a>示例  
 下面的示例.vcxproj 文件由指定生成**Win32 控制台应用程序**中**新项目**对话框。 若要处理一个项目文件使用 msbuild.exe 工具在命令行中，或**生成**命令[!INCLUDE[TLA2#tla_ide](../build/includes/tla2sharptla_ide_md.md)]。 （因为未提供所需的源文件和头文件，无法处理此示例。）有关项目文件中的 XML 元素的详细信息，请参阅[项目文件架构引用](/visualstudio/msbuild/msbuild-project-file-schema-reference)。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <ItemGroup Label="ProjectConfigurations">  
    <ProjectConfiguration Include="Debug|Win32">  
      <Configuration>Debug</Configuration>  
      <Platform>Win32</Platform>  
    </ProjectConfiguration>  
    <ProjectConfiguration Include="Release|Win32">  
      <Configuration>Release</Configuration>  
      <Platform>Win32</Platform>  
    </ProjectConfiguration>  
  </ItemGroup>  
  <PropertyGroup Label="Globals">  
    <ProjectGuid>{96F21549-A7BF-4695-A1B1-B43625B91A14}</ProjectGuid>  
    <Keyword>Win32Proj</Keyword>  
    <RootNamespace>SomeProjName</RootNamespace>  
  </PropertyGroup>  
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />  
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'" Label="Configuration">  
    <ConfigurationType>Application</ConfigurationType>  
    <CharacterSet>Unicode</CharacterSet>  
  </PropertyGroup>  
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">  
    <ConfigurationType>Application</ConfigurationType>  
    <WholeProgramOptimization>true</WholeProgramOptimization>  
    <CharacterSet>Unicode</CharacterSet>  
  </PropertyGroup>  
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />  
  <ImportGroup Label="ExtensionSettings">  
  </ImportGroup>  
  <ImportGroup Label="PropertySheets" Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">  
    <Import Project="$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props" Condition="exists('$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props')" Label="LocalAppDataPlatform" />  
  </ImportGroup>  
  <ImportGroup Label="PropertySheets" Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">  
    <Import Project="$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props" Condition="exists('$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props')" Label="LocalAppDataPlatform" />  
  </ImportGroup>  
  <PropertyGroup Label="UserMacros" />  
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">  
    <LinkIncremental>true</LinkIncremental>  
  </PropertyGroup>  
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">  
    <LinkIncremental>false</LinkIncremental>  
  </PropertyGroup>  
  <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">  
    <ClCompile>  
      <PrecompiledHeader>Use</PrecompiledHeader>  
      <WarningLevel>Level3</WarningLevel>  
      <MinimalRebuild>true</MinimalRebuild>  
      <DebugInformationFormat>EditAndContinue</DebugInformationFormat>  
      <Optimization>Disabled</Optimization>  
      <BasicRuntimeChecks>EnableFastChecks</BasicRuntimeChecks>  
      <RuntimeLibrary>MultiThreadedDebugDLL</RuntimeLibrary>  
      <PreprocessorDefinitions>WIN32;_DEBUG;_CONSOLE;%(PreprocessorDefinitions)</PreprocessorDefinitions>  
    </ClCompile>  
    <Link>  
      <SubSystem>Console</SubSystem>  
      <GenerateDebugInformation>true</GenerateDebugInformation>  
    </Link>  
  </ItemDefinitionGroup>  
  <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">  
    <ClCompile>  
      <WarningLevel>Level3</WarningLevel>  
      <PrecompiledHeader>Use</PrecompiledHeader>  
      <DebugInformationFormat>ProgramDatabase</DebugInformationFormat>  
      <Optimization>MaxSpeed</Optimization>  
      <RuntimeLibrary>MultiThreadedDLL</RuntimeLibrary>  
      <FunctionLevelLinking>true</FunctionLevelLinking>  
      <IntrinsicFunctions>true</IntrinsicFunctions>  
      <PreprocessorDefinitions>WIN32;NDEBUG;_CONSOLE;%(PreprocessorDefinitions)</PreprocessorDefinitions>  
    </ClCompile>  
    <Link>  
      <SubSystem>Console</SubSystem>  
      <GenerateDebugInformation>true</GenerateDebugInformation>  
      <EnableCOMDATFolding>true</EnableCOMDATFolding>  
      <OptimizeReferences>true</OptimizeReferences>  
    </Link>  
  </ItemDefinitionGroup>  
  <ItemGroup>  
    <None Include="ReadMe.txt" />  
  </ItemGroup>  
  <ItemGroup>  
    <ClInclude Include="stdafx.h" />  
    <ClInclude Include="targetver.h" />  
  </ItemGroup>  
  <ItemGroup>  
    <ClCompile Include="SomeProjName.cpp" />  
    <ClCompile Include="stdafx.cpp">  
      <PrecompiledHeader Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">Create</PrecompiledHeader>  
      <PrecompiledHeader Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">Create</PrecompiledHeader>  
    </ClCompile>  
  </ItemGroup>  
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />  
  <ImportGroup Label="ExtensionTargets">  
  </ImportGroup>  
</Project>  
```  
  
## <a name="see-also"></a>请参阅  
 [生成 Visual Studio 中的 c + + 项目](../ide/building-cpp-projects-in-visual-studio.md)   
 [使用项目属性](../ide/working-with-project-properties.md)