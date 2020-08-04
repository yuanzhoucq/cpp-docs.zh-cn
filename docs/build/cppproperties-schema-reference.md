---
title: CppProperties.json 参考
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: 2409c1d93d4e9d814407dbd4334daa73ae630775
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224053"
---
# <a name="cpppropertiesjson-reference"></a>CppProperties.json 参考

不使用 CMake 的“打开文件夹”项目可以将 IntelliSense 的项目配置设置存储在 CppProperties.json  文件中。 （CMake 项目使用 [CMakeSettings.json](customize-cmake-settings.md) 文件。）配置包含名称/值对，定义了 #include 路径、编译器开关和其他参数组成。 有关如何在“打开文件夹”项目中添加配置的详细信息，请参阅 [C++ 的“打开文件夹”项目](open-folder-projects-cpp.md)。 以下各节总结了各种设置。 有关架构的完整说明，请导航到 CppProperties_schema.json  ，其完整路径会在 CppProperties.json  打开时在代码编辑器顶部提供。

## <a name="configuration-properties"></a>配置属性

一个配置可能会有以下列出的其中几个属性：

|||
|-|-|
|`inheritEnvironments`| 指定哪些环境适用于此配置。|
|`name`|将出现在 C++ 配置下拉菜单中的配置名称|
|`includePath`|应在包含路径（对于大多数编译器，映射到 /I）中指定的文件夹的逗号分隔列表|
|`defines`|应定义的宏的列表（对于大多数编译器，映射到 /D）|
|`compilerSwitches`|可以影响 IntelliSense 行为的一个或多个附加开关|
|`forcedInclude`|会自动包含在每个编译单元的标头（对于 MSVC，映射到 /FI；对于 clang，映射到 -include）|
|`undefines`|未定义的宏的列表（对于 MSVC，映射到 /U）|
|`intelliSenseMode`|要使用的 IntelliSense 引擎。 你可以为 MSVC、gcc 或 Clang 指定预定义体系结构特定的变量之一。|
|`environments`|用户定义的变量集，其行为类似于命令提示符中的环境变量，可以使用 ${env.\<VARIABLE>} 宏访问。|

### <a name="intellisensemode-values"></a>intelliSenseMode 值

开始键入内容时代码编辑器会显示可用选项：

![“打开文件夹”IntelliSense](media/open-folder-intellisense-mode.png "“打开文件夹”IntelliSense")

以下是支持的值：

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
- linux-gcc-arm

注意：仅出于遗留原因支持 `msvc-x86` 和 `msvc-x64` 值。 改用 `windows-msvc-*` 变量。

## <a name="pre-defined-environments"></a>预定义环境

Visual Studio 为 Microsoft C++ 提供了以下预定义环境，它们会映射到相应的开发人员命令提示。 继承其中一个环境时，可以将全局属性 `env` 与以下宏语法一起使用，从而引用任何环境变量：${env.\<VARIABLE>}。

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

|变量名|描述|
|-----------|-----------------|
|linux_x86|远程将 x86 Linux 设为目标|
|linux_x64|远程将 x64 Linux 设为目标|
|linux_arm|远程将 ARM Linux 设为目标|

## <a name="user-defined-environments"></a><a name="user_defined_environments"></a> 用户定义的环境

可以选择在 CppProperties.json  中以全局形式或按配置使用 `environments` 属性定义变量集。 这些变量的行为类似于“打开文件夹”项目上下文中的环境变量，可以使用在此处定义的 tasks.vs.json 和 launch.vs.json 中的 ${env.\<VARIABLE>}  语法进行访问。 但是，不一定要在 Visual Studio 内部使用的任何命令提示符中将它们设置为实际环境变量。

Visual Studio 2019 版本 16.4 及更高版本  ：CppProperties.json  中定义的特定于配置的变量由调试目标和任务自动选取，无需设置 `inheritEnvironments`。 调试目标会使用在 CppProperties.json  中指定的环境自动启动。

Visual Studio 2019 版本 16.3 及更早版本  ：使用环境时，必须在 `inheritsEnvironments` 属性中指定它，即使环境定义为相同配置的一部分也是如此；`environment` 属性指定环境的名称。 下面的示例演示在 MSYS2 安装中为 GCC 启用 IntelliSense 的示例配置。 请注意配置如何定义和继承 `mingw_64` 环境，以及 `includePath` 属性如何访问 `INCLUDE` 变量。

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

在配置中定义环境  属性时，它将替代任何同名的全局变量。

## <a name="built-in-macros"></a>内置宏

可访问 CppProperties.json  中的下列内置宏：

|||
|-|-|
|`${workspaceRoot}`| 工作区文件夹的完整路径|
|`${projectRoot}`| CppProperties.json  所在文件夹的完整路径|
|`${env.vsInstallDir}`| 安装 Visual Studio 的运行示例的文件夹的完整路径|

### <a name="example"></a>示例

如果项目具备包含文件夹并包含 windows.h  和 Windows SDK 中的其他通用标头，可能需要更新 CppProperties.json  配置文件，使其带有以下包含内容：

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
> `%WindowsSdkDir%` 和 `%VCToolsInstallDir%` 并不是作为全局环境变量设置的，请确保从定义这些变量的开发人员命令提示启动 devenv.exe。 （在 Windows“开始”菜单中键入“developer”。）

## <a name="troubleshoot-intellisense-errors"></a>对 IntelliSense 错误进行故障排除

如果没有按预期看到 IntelliSense，可以进行故障排除，具体方法为依次转到“工具” > “选项” > “文本编辑器” > “C/C++” > “高级”，然后将“启用日志记录”设置为 `true`。 若要开始，请尝试将“日志记录级别”设置为 5，“日志记录筛选器”设置为 8   。

![诊断日志记录](media/diagnostic-logging.png)

输出会传递给“输出窗口”，并在选择“显示输出来源  ：  Visual C++ 日志”时显示。 除了其他内容之外，输出还包含 IntelliSense 尝试使用的实际包含路径的列表。 如果路径与 CppProperties.json  中的路径不匹配，请尝试关闭文件夹并删除包含缓存浏览数据的 .vs  子文件夹。

若要对缺少包含路径引起的 IntelliSense 错误进行故障排除，请打开“错误列表”，筛选出“仅限 IntelliSense”和错误代码 E1696“无法打开源文件...”的结果  。
