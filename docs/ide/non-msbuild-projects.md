---
title: Visual C++ 中的“打开文件夹”项目 | Microsoft Docs
ms.custom: ''
ms.date: 06/01/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4444e70ec158d7afa35c3955bbef9af4bfa12f2
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131318"
---
# <a name="open-folder-projects-in-visual-c"></a>Visual C++ 中的“打开文件夹”项目

Visual Studio 2017 及更高版本中提供了“打开文件夹”功能，可通过它打开源文件的文件夹并借助 IntelliSense、浏览、重构、调试及更多方面的支持立即开始进行编码。 不加载 .sln 或 .vcxproj 文件；如有需要，可以通过简单的 .json 文件指定自定义任务和生成及启动参数。 借助“打开文件夹”的支持，Visual C++ 现在不仅支持文件的松散集合，还几乎支持所有的生成系统，包括 CMake、Ninja、QMake（用于 Qt 项目）、gyp、SCons、Gradle、Buck 及更多其他系统。 

若要使用“打开文件夹”，请从主菜单选择“文件 | 打开 | 文件夹”或按 Ctrl+Shift+Alt+O。解决方案资源管理器会立即显示该文件夹中的所有文件。 可以单击任何文件开始编辑。 在后台，Visual Studio 开始对文件编制索引，以启用 IntelliSense、导航和重构功能。 在编辑、创建、移动或删除文件时，Visual Studio 会自动跟踪更改，并不断更新其 IntelliSense 索引。 
  
## <a name="cmake-projects"></a>CMake 项目
CMake 作为 Visual C++ 的 CMake 工具集成在 Visual Studio IDE 中，是 C++ 桌面工作负载的一个组件。 有关详细信息，请参阅 [Visual C++ 的 CMake 工具](cmake-tools-for-visual-cpp.md)。
 
## <a name="qmake-projects-that-target-the-qt-framework"></a>面向 Qt 框架的 QMake 项目
可以使用 Visual C++ 的 CMake 工具面向 Qt 生成 Qt 项目，或者可以使用适用于 Visual Studio 2015 或 Visual Studio 2017 的 [Qt Visual Studio 扩展](https://download.qt.io/development_releases/vsaddin/)。

## <a name="gyp-cons-scons-buck-etc"></a>gyp、Cons、SCons、Buck 等等
可使用以 Visual C++ 进行编写的任何生成系统，并依然能享受 Visual C++ IDE 和调试程序的优势。 打开项目的根文件夹时，Visual C++ 使用试探法将源文件编入索引用于 IntelliSense 和浏览。 可以通过编辑 CppProperties.json 文件提供关于代码结构的提示。 还可以用同样的方式，通过编辑 launch.vs.json 文件配置生成程序。 

## <a name="configuring-open-folder-projects"></a>配置“打开文件夹”项目
可以通过三个 JSON 文件来自定义“打开文件夹”项目：
|||
|-|-|
|CppProperties.json|指定用于浏览的自定义配置信息。 如有需要，请在根项目文件夹中创建此文件。|
|launch.vs.json|指定命令行参数。 通过“解决方案资源管理器”上下文菜单项“调试和启动设置”进行访问。|
|tasks.vs.json|指定自定义生成命令和编译器开关。 通过“解决方案资源管理器”上下文菜单项“配置任务”进行访问。|

### <a name="configure-intellisense-with-cpppropertiesjson"></a>使用 CppProperties.json 配置 IntelliSense
IntelliSense 和浏览行为在一定程序上取决于活动的生成配置，该配置定义 #include 路径、编译器开关和其他参数。 Visual Studio 默认提供“调试”和“发布”配置。 对于某些项目，可能需要创建自定义配置，从而让 IntelliSense 和浏览功能完全理解你的代码。 若要定义新的配置，请在根文件夹中创建名为 CppProperties.json 的文件。 下面是一个示例：

```json
{
  "configurations": [
    {
      "name": "Windows x64",
      "includePath": [ "include" ],
      "defines": [ "_DEBUG" ],
      "compilerSwitches": "/std:c++17",
      "intelliSenseMode": "msvc-x64",
      "forcedInclude": [ "pch.h" ],
      "undefines": []
    }
  ]
}
```
一个配置可能会有以下列出的其中几个属性：

|||  
|-|-| 
|`name`|显示在 C++ 配置下拉列表中的配置名称|
|`includePath`|应在包含路径中指定的文件夹的列表（对于大多数编译器，映射到 /I）|
|`defines`|应定义的宏的列表（对于大多数编译器，映射到 /D）|
|`compilerSwitches`|可以影响 IntelliSense 行为的一个或多个附加开关|
|`forcedInclude`|会自动包含在每个编译单元的标头（对于 MSVC，映射到 /FI；对于 clang，映射到 -include）|
|`undefines`|未定义的宏的列表（对于 MSVC，映射到 /U）|
|`intelliSenseMode`|要使用的 IntelliSense 引擎。 你可以为 MSVC、gcc 或 Clang 指定体系结构特定的变量：
- msvc-x86（默认）
- msvc-x64
- msvc-arm
- windows-clang-x86
- windows-clang-x64
- windows-clang-arm
- Linux-x64
- Linux-x86
- Linux-arm
- gccarm

#### <a name="environment-variables"></a>环境变量
CppProperties.json 支持用于包含路径和其他属性值的系统环境变量扩展。 语法为 `${env.FOODIR}`，用于扩展环境变量 `%FOODIR%`。 还支持下列系统定义的变量：

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

可以在 CppProperties.json 中以全局形式或按配置定义自定义环境变量。 下面的示例演示如何声明并使用默认和自定义的环境变量。 全局 environments 属性声明名为 INCLUDE 的变量，此变量可用于任何配置：

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\\src\\includes"
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
还可在某个配置内定义 environments 属性，让它只应用于该配置，并覆盖所有同名的全局变量。 在下面的示例中，x64 配置定义了一个会覆盖全局值的本地 INCLUDE 变量：

```json
{
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\\src\\includes"
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
          "INCLUDE": "${env.INCLUDE};${workspaceRoot}\\src\\includes64"
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

所有自定义和默认环境变量也能用于 tasks.vs.json 和 launch.vs.json。

#### <a name="macros"></a>宏
可访问 CppProperties.json 中的下列内置宏：
|||
|-|-|
|`${workspaceRoot}`| 工作区文件夹的完整路径|
|`${projectRoot}`| CppProperties.json 所在文件夹的完整路径|
|`${vsInstallDir}`| 安装 VS 2017 的运行示例的文件夹的完整路径|

例如，如果项目具备包含文件夹并包含 windows.h 和 Windows SDK 中的其他通用标头，可能需要更新 CppProperties.json 配置文件，使其带有这些包含内容：

```json
{
  "configurations": [
    {
      "name": "Windows",
      "includePath": [
        // local include folder
        "${workspaceRoot}\\include",
        // Windows SDK and CRT headers
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\ucrt",
        "${env.NETFXSDKDir}\\include\\um",
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\um",
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\shared",
        "${env.VCToolsInstallDir}include"
      ]
    }
  ]
}
```

**Note：**`%WindowsSdkDir%` 和 `%VCToolsInstallDir%` 并不是作为全局环境变量设置的，所以请确保从定义这些变量的“适用于 VS 2017 的开发人员命令提示”启动 devenv.exe。

若要对缺少包含路径引起的 IntelliSense 错误进行故障排除，请打开“错误列表”，筛选出“仅限 IntelliSense”和错误代码 E1696“无法打开源文件...”的结果。 

可以在 CppProperties.json 中创建任意数量的配置。 每个配置都会显示在配置下拉列表中：

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
### <a name="define-tasks-with-tasksvsjson"></a>使用 tasks.vs.json 定义任务
可以通过直接在 IDE 中作为任务运行来自动执行生成脚本，或者对当前工作区中的现有文件自动执行任何其他外部操作。 可以通过右键单击文件或文件夹并选择“配置任务”来配置新任务。 

![“打开文件夹”配置任务](media/open-folder-config-tasks.png)

此任务会在 .vs 文件夹中创建（或打开）`tasks.vs.json` 文件，该文件夹由 Visual Studio 在根项目文件夹中创建。 可以在此文件中定义任意任务，然后使用从“解决方案资源管理器”上下文菜单调用它。 以下示例显示定义单个任务的 tasks.vs.json 文件。 `taskName` 定义上下文菜单中显示的名称。 `appliesTo` 定义可在其中执行命令的文件。 `command` 属性指 COMSPEC 环境变量，该变量定义控制台的路径（Windows 上的 cmd.exe）。 你还可以引用 CppProperties.json 或 CMakeSettings.json 中声明的环境变量。 `args` 属性指定要调用的命令行。 `${file}` 宏检索“解决方案资源管理器”中选定的文件。 下面的示例将显示当前所选 .cpp 文件的文件名。

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```
保存 tasks.vs.json 后，可以在文件夹中右键单击任一 .cpp 文件，选择上下文菜单中的“Echo 文件名”，并查看输出窗口中显示的文件名。



#### <a name="appliesto"></a>appliesTo
可通过在 `appliesTo` 字段中指定其名称来创建任何文件或文件夹任务，例如 `"appliesTo" : "hello.cpp"`。 以下文件掩码可用作值：
|||
|-|-|
|`"*"`| 任务适用于工作区中的所有文件和文件夹|
|`"*/"`| 任务适用于工作区中的所有文件夹|
|`"*.cpp"`| 任务适用于工作区中带 .cpp 扩展名的所有文件|
|`"/*.cpp"`| 任务适用于工作区根目录中带 .cpp 扩展名的所有文件|
|`"src/*/"`| 任务适用于“src”文件夹的所有子文件夹|
|`"makefile"`| 任务适用于工作区中的所有生成文件文件|
|`"/makefile"`| 任务仅适用于工作区根目录中的生成文件|

#### <a name="output"></a>输出
使用 `output` 属性来指定按 F5 时启动的可执行文件。 例如:

```json
      "output": "${workspaceRoot}\\bin\\hellomake.exe" 
```

#### <a name="macros-for-tasksvsjson"></a>tasks.vs.json 宏

|||
|-|-|
|`${env.<VARIABLE>}`| 指定为开发人员命令提示符设置的任何环境变量（例如，${env.PATH}、${env.COMSPEC} 等）。 有关详细信息，请参阅 [Visual Studio 开发人员命令提示符](/dotnet/framework/tools/developer-command-prompt-for-vs)。|
|`${workspaceRoot}`| 工作区文件夹的完整路径（例如“C:\sources\hello”）|
|`${file}`| 为再次运行该任务而选择的文件或文件夹的完整路径（例如“C:\sources\hello\src\hello.cpp”）|
|`${relativeFile}`| 文件或文件夹的相对路径（例如“src\hello.cpp”）|
|`${fileBasename}`| 没有路径或扩展名的文件的名称（例如“hello”）|
|`${fileDirname}`| 文件的完整路径，不包括文件名（例如“C:\sources\hello\src”）|
|`${fileExtname}`| 所选文件的扩展名（例如“.cpp”）|

#### <a name="custom-macros"></a>自定义宏
若要在 tasks.vs.json 中定义自定义宏，请将名称/值对添加到任务块之前。 以下示例定义了在 `args` 属性中使用的名为 `outDir` 的宏：

```json
{
"version": "0.2.1",
  "outDir": "${workspaceRoot}\\bin",
  "tasks": [
    {
      "taskName": "List outputs",
      "*",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": [
        "dir ${outDir}"
      ]
    }
  ]
```

### <a name="configure-debugging-parameters-with-launchvsjson"></a>使用 launch.vs.json 配置调试参数
若要自定义程序的命令行参数，请右键单击解决方案资源管理器中的可执行文件，并选择“调试和启动设置”。 这将打开现有的 `launch.vs.json` 文件，如果该文件不存在，则新建由所选程序相关信息填充的文件。 

若要指定其他参数，将它们添加到 `args` JSON 数组即可，如下面的代码所示：

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CPP\\7zip\\Bundles\\Alone\\O\\7za.exe",
      "name": "7za.exe list content of helloworld.zip",
      "args": [ "l", "d:\\sources\\helloworld.zip" ]
    }
  ]
}
```

保存该文件时，新配置将出现在“调试目标”下拉列表中，且可以选择该配置来启动调试程序。 可以根据需要创建任意数量的调试配置，用于任意数量的可执行文件。 如果现在按 F5，调试程序将启动并命中可能已设置的任何断点。 现可使用所有熟悉的调试程序窗口及其功能。

## <a name="see-also"></a>请参阅
[用于 Visual C++ 开发的 IDE 和工具](ide-and-tools-for-visual-cpp-development.md)

