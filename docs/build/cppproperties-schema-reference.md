---
title: CppProperties.json 架构参考
ms.date: 03/05/2019
helpviewer_keywords:
- CMake in Visual C++
ms.openlocfilehash: fd655de3313dd95eb3fcefaeba21e703d32e860a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824894"
---
# <a name="cpppropertiesjson-schema-reference"></a>CppProperties.json 架构参考

不使用 CMake 打开文件夹项目可以存储中的项目配置设置`CppProperties.json`文件。 (CMake 项目使用[CMakeSettings.json](customize-cmake-settings.md)文件。)Visual Studio IDE 使用`CppProperties.json`IntelliSense 和代码导航。 配置包含名称/值对，并定义 #include 路径、 编译器开关和其他参数。 


## <a name="default-configurations"></a>默认配置

Visual Studio 提供了预定义的配置的 x86 和 x64 调试和发布。 默认情况下，你的项目具有 x86 调试配置`CppProperties.json`。 若要添加新的配置，请右键单击`CppProperties.json`文件中**解决方案资源管理器**，然后选择**添加配置**:

![打开文件夹添加配置](media/open-folder-add-config.png "打开文件夹添加新的配置")

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
对于具有一系列允许的值的属性，代码编辑器中显示可用的选项，当您开始键入：

![打开文件夹 IntelliSense](media/open-folder-intellisense-mode.png "打开文件夹 IntelliSense")



## <a name="configuration-properties"></a>配置属性

一个配置可能会有以下列出的其中几个属性：

|||
|-|-|
|`name`|在 c + + 配置下拉列表中显示的配置名称|
|`includePath`|应在包含路径 （映射到 /I 为大多数编译器） 中指定的文件夹的列表|
|`defines`|应为的宏的列表定义 （映射到 /D 为大多数编译器）|
|`compilerSwitches`|可能会影响 IntelliSense 的行为的一个或多个其他开关|
|`forcedInclude`|要自动包含在每个编译单元中的标头 （MSVC 为映射到 /FI; 或-包括用于 clang）|
|`undefines`|宏是未定义 （映射到 /U 表示 MSVC） 的列表|
|`intelliSenseMode`|要使用 IntelliSense 引擎。 你可以为 MSVC、gcc 或 Clang 指定体系结构特定的变量：<br/><br/>- msvc-x86（默认）<br/>- msvc-x64<br/>- msvc-arm<br/>- windows-clang-x86<br/>- windows-clang-x64<br/>- windows-clang-arm<br/>- Linux-x64<br/>- Linux-x86<br/>- Linux-arm<br/>- gccarm|

## <a name="custom-configurations"></a>自定义配置


您可以自定义任何中默认 configuations `CppProperties.json`，或创建新的配置。 每个配置都会显示在配置下拉列表中：

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

 `CppProperties.json` 支持系统环境变量扩展为包括路径和其他属性值。 语法为 `${env.FOODIR}`，用于扩展环境变量 `%FOODIR%`。 还支持下列系统定义的变量：

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

可以定义中的自定义环境变量`CppProperties.json`是全局或每个配置。 下面的示例演示如何声明并使用默认和自定义的环境变量。 全局 environments 属性声明名为 INCLUDE 的变量，此变量可用于任何配置：

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
      "intelliSenseMode": "msvc-x86"
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
      "intelliSenseMode": "msvc-x64"
    }
  ]
}
```
## <a name="per-configuration-environment-variables"></a>每个配置环境变量

还可在某个配置内定义 environments 属性，让它只应用于该配置，并覆盖所有同名的全局变量。 在下面的示例中，x64 配置定义了一个会覆盖全局值的本地 INCLUDE 变量：

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
      "intelliSenseMode": "msvc-x86"
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
      "intelliSenseMode": "msvc-x64"
    }
  ]
}
```

所有自定义和默认环境变量也会出现在`tasks.vs.json`和`launch.vs.json`。

#### <a name="build-in-macros"></a>生成中的宏

有权访问中的以下内置宏`CppProperties.json`:

|||
|-|-|
|`${workspaceRoot}`| 工作区文件夹的完整路径|
|`${projectRoot}`| 文件夹的完整路径其中`CppProperties.json`放置|
|`${vsInstallDir}`| 安装 VS 2017 的运行示例的文件夹的完整路径|

例如，如果你的项目具有的包含文件夹，并且还包括 windows.h 和 Windows SDK 中的其他常见标头，您可能想要更新你`CppProperties.json`与这些配置文件包括：

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
> `%WindowsSdkDir%` 和 `%VCToolsInstallDir%` 并不是作为全局环境变量设置的，所以请确保从定义这些变量的“适用于 VS 2017 的开发人员命令提示”启动 devenv.exe。

## <a name="troubleshoot-intellisense-errors"></a>对 IntelliSense 错误进行故障排除

若要对缺少包含路径引起的 IntelliSense 错误进行故障排除，请打开“错误列表”，筛选出“仅限 IntelliSense”和错误代码 E1696“无法打开源文件...”的结果。



