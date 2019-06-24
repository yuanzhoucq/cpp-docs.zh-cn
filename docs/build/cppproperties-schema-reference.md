---
title: CppProperties.json 架构引用
ms.date: 05/16/2019
helpviewer_keywords:
- CMake in Visual Studio
ms.openlocfilehash: 8432b72deaef99ee20147505030cbc8a9a270869
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344405"
---
# <a name="cpppropertiesjson-schema-reference"></a>CppProperties.json 架构引用

不使用 CMake 的“打开文件夹”项目可以将项目配置设定存储在 `CppProperties.json` 文件中。 （CMake 项目使用 [CMakeSettings.json](customize-cmake-settings.md) 文件。）Visual Studio IDE 对 IntelliSense 和代码导航使用 `CppProperties.json`。 配置包含名称/值对，定义了 #include 路径、编译器开关和其他参数组成。 


## <a name="default-configurations"></a>默认配置

Visual Studio 预定义的配置为 x86 和 x64 的 Debug 和 Release。 默认情况下，项目在 `CppProperties.json` 中为 x86-Debug 配置。 若要添加新的配置，请右键单击`CppProperties.json`文件中**解决方案资源管理器**，然后选择**添加配置**:

![打开文件夹-添加新的配置](media/open-folder-add-config.png "打开文件夹添加新的配置")

默认配置如下所示：

```json
{
  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86-Release",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "NDEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    },
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Release",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "NDEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```
对于具有一系列允许值的属性，开始键入内容时代码编辑器会显示可用选项：

![“打开文件夹”的 IntelliSense](media/open-folder-intellisense-mode.png "Open Folder IntelliSense")



## <a name="configuration-properties"></a>配置属性

一个配置可能会有以下列出的其中几个属性：

|||
|-|-|
|`name`|显示在“C++ 配置”下拉列表中的配置名称|
|`includePath`|应在包含路径中指定的文件夹的列表（对于大多数编译器，映射到 /I）|
|`defines`|应定义的宏的列表（对于大多数编译器，映射到 /D）|
|`compilerSwitches`|可以影响 IntelliSense 行为的一个或多个附加开关|
|`forcedInclude`|会自动包含在每个编译单元的标头（对于 MSVC，映射到 /FI；对于 clang，映射到 -include）|
|`undefines`|未定义的宏的列表（对于 MSVC，映射到 /U）|
|`intelliSenseMode`|要使用的 IntelliSense 引擎。 MSVC、 gcc 高级版，或 Clang，可以指定特定于体系结构的变体：<br/><br/>- windows-msvc-x86 (default)<br/>- windows-msvc-x64<br/>- msvc-arm<br/>- windows-clang-x86<br/>- windows-clang-x64<br/>- windows-clang-arm<br/>- Linux-x64<br/>- Linux-x86<br/>- Linux-arm<br/>- gccarm|

注意:仅出于遗留原因支持 `msvc-x86` 和 `msvc-x64` 值。 使用`windows-msvc-*`变体相反。

## <a name="custom-configurations"></a>自定义配置


可自定义 `CppProperties.json` 中的任何默认配置，或创建新配置。 每个配置都会显示在配置下拉列表中：

```json
{
  "configurations": [
    {
      "name": "Windows",
      ...
    },
    {
      "name": "with EXTERNAL_CODECS",
      ...
    }
  ]
}
```

## <a name="system-environment-variables"></a>系统环境变量 

 `CppProperties.json` 支持用于包含路径和其他属性值的系统环境变量扩展。 语法为 `${env.FOODIR}`，用于扩展环境变量 `%FOODIR%`。 还支持下列系统定义的变量：

|变量名|描述|
|-----------|-----------------|
|vsdev|默认的 Visual Studio 环境|
|msvc_x86|使用 x86 工具为 x86 编译|
|msvc_arm|使用 x86 工具为 ARM 编译|
|msvc_arm64|使用 x86 工具为 ARM64 编译|
|msvc_x86_x64|使用 x86 工具为 AMD64 编译|
|msvc_x64_x64|使用 64 位工具为 AMD64 编译|
|msvc_arm_x64|使用 64 位工具为 ARM 编译|
|msvc_arm64_x64|使用 64 位工具为 ARM64 编译|

安装 Linux 工作负载后，可使用以下环境变量远程定向到 Linux 和 WSL：

|变量名|描述|
|-----------|-----------------|
|linux_x86|远程将 x86 Linux 设为目标|
|linux_x64|远程将 x64 Linux 设为目标|
|linux_arm|远程将 ARM Linux 设为目标|

## <a name="custom-environment-variables"></a>自定义环境变量

可在 `CppProperties.json` 中以全局形式或按配置定义自定义环境变量。 下面的示例演示如何声明并使用默认和自定义的环境变量。 全局 environments 属性声明名为 INCLUDE 的变量，此变量可用于任何配置   ：

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\src\includes"
    }
  ],

  "configurations": [
    {
      "inheritEnvironments": [
        // Inherit the MSVC 32-bit environment and toolchain.
        "msvc_x86"
      ],
      "name": "x86",
      "includePath": [
        // Use the include path defined above.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        // Inherit the MSVC 64-bit environment and toolchain.
        "msvc_x64"
      ],
      "name": "x64",
      "includePath": [
        // Use the include path defined above.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```
## <a name="per-configuration-environment-variables"></a>预配置环境变量

您还可以定义**环境**在配置的属性。 它仅适用于该配置，并将覆盖具有相同名称的任何全局变量。 在下面的示例中，x64 配置定义了一个会覆盖全局值的本地 INCLUDE 变量  ：

```json
{
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\src\includes"
    }
  ],

  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86",
      "includePath": [
        // Use the include path defined in the global environments property.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "environments": [
        {
          // Append 64-bit specific include path to env.INCLUDE.
          "INCLUDE": "${env.INCLUDE};${workspaceRoot}\src\includes64"
        }
      ],

      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64",
      "includePath": [
        // Use the include path defined in the local environments property.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```

所有自定义和默认环境变量也能用于 `tasks.vs.json` 和 `launch.vs.json`。

#### <a name="build-in-macros"></a>内置宏

可访问 `CppProperties.json` 中的下列内置宏：

|||
|-|-|
|`${workspaceRoot}`| 工作区文件夹的完整路径|
|`${projectRoot}`| `CppProperties.json` 所在文件夹的完整路径|
|`${vsInstallDir}`| 安装 Visual Studio 的运行示例的文件夹的完整路径|

例如，如果你的项目具有的包含文件夹，并且还包括 windows.h 和 Windows SDK 中的其他常见标头，您可能想要更新你`CppProperties.json`以下配置文件包括：

```json
{
  "configurations": [
    {
      "name": "Windows",
      "includePath": [
        // local include folder
        "${workspaceRoot}\include",
        // Windows SDK and CRT headers
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\ucrt",
        "${env.NETFXSDKDir}\include\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\shared",
        "${env.VCToolsInstallDir}\include"
      ]
    }
  ]
}
```

> [!Note]
> `%WindowsSdkDir%` 和 `%VCToolsInstallDir%` 并不是作为全局环境变量设置的，请确保从定义这些变量的开发人员命令提示符启动 devenv.exe。 （在 Windows“开始”菜单中键入“developer”。）

## <a name="troubleshoot-intellisense-errors"></a>对 IntelliSense 错误进行故障排除

若要对缺少包含路径引起的 IntelliSense 错误进行故障排除，请打开“错误列表”，筛选出“仅限 IntelliSense”和错误代码 E1696“无法打开源文件...”的结果  。
