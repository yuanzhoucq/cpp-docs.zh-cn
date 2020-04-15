---
title: CppProperties.json 参考
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: be6db52e1e62244e9f44db8ac86238242ab50ca0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328721"
---
# <a name="cpppropertiesjson-reference"></a>CppProperties.json 参考

不使用 CMake 的"打开文件夹"项目可以在*CppProperties.json*文件中存储 IntelliSense 的项目配置设置。 （CMake 项目使用["CMakeSettings.json"](customize-cmake-settings.md)文件。配置由名称/值对组成，并定义#include路径、编译器开关和其他参数。 有关如何在打开文件夹项目中添加配置的详细信息，请参阅[打开文件夹项目C++。](open-folder-projects-cpp.md) 以下各节总结了各种设置。 有关架构的完整说明，请导航到*CppProperties_schema.json*，当*CppProperties.json*处于打开时，其完整路径位于代码编辑器的顶部。

## <a name="configuration-properties"></a>配置属性

一个配置可能会有以下列出的其中几个属性：

|||
|-|-|
|`inheritEnvironments`| 指定适用于此配置的环境。|
|`name`|将在C++配置下拉列表中显示的配置名称|
|`includePath`|应在包含路径中指定的文件夹的逗号分隔列表（对于大多数编译器映射到 /I）|
|`defines`|应定义的宏的列表（对于大多数编译器，映射到 /D）|
|`compilerSwitches`|可以影响 IntelliSense 行为的一个或多个附加开关|
|`forcedInclude`|会自动包含在每个编译单元的标头（对于 MSVC，映射到 /FI；对于 clang，映射到 -include）|
|`undefines`|未定义的宏的列表（对于 MSVC，映射到 /U）|
|`intelliSenseMode`|要使用的 IntelliSense 引擎。 您可以为 MSVC、gcc 或 Clang 指定预定义的体系结构特定变体之一。|
|`environments`|用户定义的变量集，它们在命令提示符中类似于环境变量，并且使用 $_env 进行访问。\<变量>] 宏。|

### <a name="intellisensemode-values"></a>内泰利感知模式值

开始键入时，代码编辑器显示可用选项：

![打开文件夹智能感知](media/open-folder-intellisense-mode.png "打开文件夹智能感知")

这些是支持的值：

- windows-msvc-x86
- windows-msvc-x64
- windows-msvc-arm
- windows-msvc-arm64
- android-clang-x86
- android-clang-x64
- android-clang-arm
- android-clang-arm64
- ios-clang-x86
- ios-clang-x64
- ios-clang-arm
- ios-clang-arm64
- windows-clang-x86
- windows-clang-x64
- windows-clang-arm
- windows-clang-arm64
- linux-gcc-x86
- linux-gcc-x64
- linux-gcc 臂

注意： 值`msvc-x86`和`msvc-x64`仅出于遗留原因受支持。 改用`windows-msvc-*`变体。

## <a name="pre-defined-environments"></a>预定义环境

Visual Studio 为 Microsoft 提供了以下预定义环境C++这些环境映射到相应的开发人员命令提示。 继承这些环境之一时，可以通过使用此宏语法的全局属性`env`来引用任何环境变量：$_env。\<可变>]。

|变量名|说明|
|-----------|-----------------|
|vsdev|默认的 Visual Studio 环境|
|msvc_x86|使用 x86 工具为 x86 编译|
|msvc_x64|使用 64 位工具为 AMD64 编译|
|msvc_arm|使用 x86 工具为 ARM 编译|
|msvc_arm64|使用 x86 工具为 ARM64 编译|
|msvc_x86_x64|使用 x86 工具为 AMD64 编译|
|msvc_arm_x64|使用 64 位工具为 ARM 编译|
|msvc_arm64_x64|使用 64 位工具为 ARM64 编译|

安装 Linux 工作负载后，可使用以下环境变量远程定向到 Linux 和 WSL：

|变量名|说明|
|-----------|-----------------|
|linux_x86|远程将 x86 Linux 设为目标|
|linux_x64|远程将 x64 Linux 设为目标|
|linux_arm|远程将 ARM Linux 设为目标|

## <a name="user-defined-environments"></a><a name="user_defined_environments"></a>用户定义的环境

您可以选择使用 属性`environments`在*CppProperties.json*中定义全局或每个配置中的变量集。 这些变量在打开文件夹项目的上下文中类似于环境变量，可以使用 $_env 进行访问。\<变量>]语法从*任务.vs.json*和*启动.vs.json*定义他们在这里。 但是，在 Visual Studio 内部使用的任何命令提示中，它们不一定设置为实际环境变量。

**Visual Studio 2019 版本 16.4 及更高版本：***在 CppProperties.json*中定义的特定于配置的变量由调试目标和任务自动选取，而无需设置`inheritEnvironments`。 调试目标使用您在*CppProperties.json*中指定的环境自动启动。

**Visual Studio 2019 版本 16.3 及更早版本：** 使用环境时，即使环境定义为同一配置的一部分，`inheritsEnvironments`也必须在 属性中指定它;属性`environment`指定环境的名称。 下面的示例显示了用于在 MSYS2 安装中为 GCC 启用 IntelliSense 的示例配置。 请注意配置如何定义和继承`mingw_64`环境，以及`includePath`属性如何访问`INCLUDE`变量。

```json
"configurations": [
    {

      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath ,": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**",
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.MINGW64_ROOT}\\bin;${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR};",
          "environment": "mingw_64"
        }
      ]
    }
  ]
```

在配置中定义**环境**属性时，它将覆盖任何同名的全局变量。

## <a name="built-in-macros"></a>内置宏

您可以访问*CppProperties.json*中的以下内置宏：

|||
|-|-|
|`${workspaceRoot}`| 工作区文件夹的完整路径|
|`${projectRoot}`| 放置*CppProperties.json*的文件夹的完整路径|
|`${env.vsInstallDir}`| 安装 Visual Studio 正在运行的实例的文件夹的完整路径|

### <a name="example"></a>示例

如果项目具有包含文件夹，并且还包括 Windows SDK 中的*windows.h*和其他常见标头，则可能需要更新*您的 CppProperties.json*配置文件，其中包括：

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

如果您没有看到预期中的 IntelliSense，则可以通过访问**工具** > **选项** > **文本编辑器** > **C/C++** > **高级**和将**启用日志记录**设置为**true**来进行故障排除。 首先，请尝试将**日志记录级别**设置为 5，**并将筛选器**设置为 8。

![诊断日志记录](media/diagnostic-logging.png)

输出通过管道到**输出窗口**，当您选择 **"显示输出从：可视C++日志**"时，输出可见。 输出包含 IntelliSense 尝试使用的实际路径列表。 如果路径与*CppProperties.json*中的路径不匹配，请尝试关闭文件夹并删除包含缓存浏览数据的 *.vs*子文件夹。

若要对缺少包含路径引起的 IntelliSense 错误进行故障排除，请打开“错误列表”，筛选出“仅限 IntelliSense”和错误代码 E1696“无法打开源文件...”的结果****。
