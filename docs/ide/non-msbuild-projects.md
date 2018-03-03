---
title: "在 Visual c + + 中打开文件夹项目 |Microsoft 文档"
ms.custom: 
ms.date: 08/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 721dd39cf8cda6277eb129f259b7ede2d9f0da28
ms.sourcegitcommit: ef2a263e193410782c6dfe47d00764263439537c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="open-folder-projects-in-visual-c"></a>在 Visual c + + 中打开文件夹项目
Visual Studio 2017 引入了"打开文件夹"功能，可用于打开源文件的文件夹立即开头编码支持 IntelliSense，浏览、 重构、 调试，依次类推。 不加载任何.sln 或.vcxproj 文件;如果需要可以指定自定义任务以及生成和启动参数通过简单的.json 文件。 供电打开文件夹时，Visual c + + 现在可以支持的文件，松散集合不仅还几乎是任何生成系统，包括 CMake、 忍者、 QMake （对于 Qt 项目）、 gyp、 SCons、 Gradle、 Buck、 生成和的详细信息。 

若要使用打开的文件夹，请从主菜单选择*文件 |打开 |文件夹*或按*Ctrl + Shift + Alt + O*。解决方案资源管理器立即显示文件夹中的所有文件。 你可以单击任何文件以开始编辑它。 在后台，Visual Studio 启动文件后，若要启用智能感知、 导航和重构功能编制索引。 如编辑、 创建、 移动或删除文件，Visual Studio 将自动跟踪所做的更改，并不断更新其 IntelliSense 的索引。 
  
## <a name="cmake-projects"></a>CMake 项目
CMake 中集成 Visual Studio IDE CMake 工具和 Visual c + +，c + + 桌面工作负荷的一个组件。 有关详细信息，请参阅 [Visual C++ 的 CMake 工具](cmake-tools-for-visual-cpp.md)。
 
## <a name="qmake-projects-that-target-the-qt-framework"></a>QMake Qt 框架为目标的项目
你可以使用 CMake 工具 Visual c + + 到目标 Qt 生成 Qt 项目，或者你可以使用 Qt Visual Studio 扩展。 注意： 截至年 8 月 2017年[Qt Visual Studio 扩展 Visual Studio 2017 支持](https://download.qt.io/development_releases/vsaddin/)用作 beta 版本。

## <a name="gyp-cons-scons-buck-etc"></a>gyp，Cons、 SCons、 Buck，等等
你可以在 Visual c + + 中使用任何生成系统，仍同时享受 Visual c + + IDE 和调试器的优势。 打开你的项目的根文件夹时，Visual c + + 使用试探法来为 IntelliSense 和浏览索引的源文件。 你可以通过编辑 CppProperties.json 文件提供有关代码的结构的提示。 以类似的方式，可以通过编辑 launch.vs.json 文件来配置生成程序。 

## <a name="configuring-open-folder-projects"></a>打开文件夹对项目进行配置
你可以通过三个 JSON 文件来自定义打开文件夹项目：
|||
|-|-|
|CppProperties.json|指定用于浏览的自定义配置信息。 如果需要可在根项目文件夹，请创建此文件。|
|launch.vs.json|指定命令行参数。 通过访问**解决方案资源管理器**上下文菜单项**调试和启动设置**。|
|tasks.vs.json|指定自定义生成命令和编译器开关。 通过访问**解决方案资源管理器**上下文菜单项**配置任务**。|

### <a name="configure-intellisense-with-cpppropertiesjson"></a>使用 CppProperties.json 配置 IntelliSense
IntelliSense 和浏览行为部分取决于活动的生成配置，它定义 #include 路径、 编译器开关和其他参数。 默认情况下，Visual Studio 提供调试和发布配置。 对于某些项目，你可能需要在为了让 IntelliSense 和浏览功能完全理解你的代码中创建自定义配置。 若要定义新的配置，创建名为 CppProperties.json 的根文件夹中的文件。 下面是一个示例：

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
一个配置可能会有任何以下属性：

|||  
|-|-| 
|`name`|在 c + + 配置下拉列表中显示的配置名称|
|`includePath`|应包含路径 （映射到 /I 为大多数编译器） 中指定的文件夹的列表|
|`defines`|应为宏的列表定义 （映射到 /D 为大多数编译器）|
|`compilerSwitches`|可以影响 IntelliSense 行为的一个或多个附加开关|
|`forcedInclude`|标头，以便将自动包含在每个编译单元 （映射到 /FI 为 MSVC; 或-包括用于 clang）|
|`undefines`|宏是未定义 （映射到 MSVC 的 /U） 的列表|
|`intelliSenseMode`|要使用 IntelliSense 引擎。 你可以为 MSVC gcc 和 Clang 指定体系结构的特定变体：
- msvc x86 （默认值）
- msvc-x64
- msvc-arm
- windows-clang-x86
- windows-clang-x64
- windows-clang-arm
- Linux-x64
- Linux-x86
- Linux arm
- gccarm

#### <a name="environment-variables"></a>环境变量
CppProperties.json 支持系统环境变量扩展为包括路径和其他属性的值。 语法是`${env.FOODIR}`以展开环境变量`%FOODIR%`。 此外支持以下系统定义变量：

|变量名称|描述|  
|-----------|-----------------|
|vsdev|默认 Visual Studio 环境|
|msvc_x86|编译为 x86 使用 x86 工具|
|msvc_arm|编译 arm 使用 x86 工具|
|msvc_arm64|针对 ARM64 编译使用 x86 工具|
|msvc_x86_x64|针对 AMD64 编译使用 x86 工具|
|msvc_x64_x64|针对 AMD64 编译使用 64 位工具|
|msvc_arm_x64|为 ARM 使用 64 位工具编译|
|msvc_arm64_x64|针对 ARM64 编译使用 64 位工具|

安装 Linux 工作负荷时，以下环境是可用于远程指向 Linux 和 WSL:

|变量名称|描述|  
|-----------|-----------------|
|linux_x86|面向 x86 Linux 远程|
|linux_x64|面向 x64 Linux 远程|
|linux_arm|远程面向 ARM Linux|

你可以定义自定义环境变量中 CppProperties.json 或者全局或每个配置。 下面的示例演示如何可以声明并使用默认和自定义环境变量。 全局**环境**属性声明一个名为变量**包括**，可以由任何配置：

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
你还可以定义**环境**内配置，以便它仅适用于该配置，并将覆盖具有相同名称的任何全局变量的属性。 在下面的示例中，x64 配置定义本地**包括**将重写全局值的变量：

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

所有自定义和默认环境变量也会出现在 tasks.vs.json 和 launch.vs.json。

#### <a name="macros"></a>宏
你有权在 CppProperties.json 内的以下内置宏：
|||
|-|-|
|`${workspaceRoot}`| 工作区文件夹的完整路径|
|`${projectRoot}`| CppProperties.json 所在文件夹的完整路径|
|`${vsInstallDir}`| 为安装 VS 2017 正在运行的实例的文件夹的完整路径|

例如，如果你的项目已包含文件夹，并且还包括 windows.h 和 Windows SDK 中的其他常见标头，你可能想要更新使用这些配置文件包括你 CppProperties.json:

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

**注意：** `%WindowsSdkDir%`和`%VCToolsInstallDir%`未按照全局环境变量因此请确保你启动 devenv.exe 针对，从"开发人员命令提示符 VS 自 2017 年 1"定义这些变量进行设置。

若要解决 IntelliSense 由缺少引起的错误包括路径，打开**错误列表**、 筛选"仅智能感知"到其输出和错误代码 E1696"无法打开源文件..."。 

你可以在 CppProperties.json 创建任意数量的配置。 每个会在配置下拉列表中显示：

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
### <a name="define-tasks-with-tasksvsjson"></a>定义使用 tasks.vs.json 任务
你可以自动执行生成脚本或通过直接在 IDE 中的任务中运行的你当前的工作区中没有的文件的任何其他外部操作。 你可以通过右键单击文件或文件夹并选择配置新任务**配置任务**。 

![打开文件夹配置任务](media/open-folder-config-tasks.png)

这创建 （或打开） `tasks.vs.json` .vs 文件夹将在根项目文件夹中创建 Visual Studio 中的文件。 你可以在此文件中定义任意的任何任务，然后调用从**解决方案资源管理器**上下文菜单。 下面的示例演示定义单个任务的 tasks.vs.json 文件。 `taskName`定义在上下文菜单中显示的名称。 `appliesTo`定义可以对执行命令的文件。 `command`属性是指 COMSPEC 环境变量，它标识控制台 (在 Windows 上的 cmd.exe) 的路径。 你还可以引用 CppProperties.json 或 CMakeSettings.json 中声明的环境变量。 `args`属性指定要调用的命令行。 `${file}`宏检索中的所选的文件**解决方案资源管理器**。 下面的示例将显示当前所选的.cpp 文件的文件名。

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
在保存后 tasks.vs.json，右键单击该文件夹中的任何.cpp 文件，选择**Echo filename**从上下文菜单中，并显示在输出窗口中的文件名称，请参阅。



#### <a name="appliesto"></a>appliesTo
您可以通过指定其名称中的创建的任何文件或文件夹的任务`appliesTo`字段，例如`"appliesTo" : "hello.cpp"`。 以下文件掩码可以用作值：
|||
|-|-|
|`"*"`| 任务可供所有文件和工作区中的文件夹|
|`"*/"`| 任务可供在工作区中的所有文件夹|
|`"*.cpp"`| 任务可供具有扩展名.cpp 工作区中的所有文件|
|`"/*.cpp"`| 任务可供具有扩展名.cpp 工作区的根目录中的所有文件|
|`"src/*/"`| 任务可供所有子文件夹的"src"文件夹|
|`"makefile"`| 任务可供在工作区中的所有生成文件文件|
|`"/makefile"`| 任务是仅供工作区的根目录中生成文件|

#### <a name="output"></a>输出
使用`output`属性来指定按下时，将启动的可执行文件**F5**。 例如:

```json
      "output": "${workspaceRoot}\\bin\\hellomake.exe" 
```

#### <a name="macros-for-tasksvsjson"></a>用于 tasks.vs.json 宏

|||
|-|-|
|`${env.<VARIABLE>}`| 指定任何环境变量 （例如，${env。路径}，${env.COMSPEC} 等) 的设置的开发人员命令提示符。 有关详细信息，请参阅[Visual Studio 的开发人员命令提示](/dotnet/framework/tools/developer-command-prompt-for-vs)。|
|`${workspaceRoot}`| 工作区文件夹 (例如，"C:\sources\hello") 的完整路径|
|`${file}`| 文件或选择要运行此任务针对 (例如，"C:\sources\hello\src\hello.cpp") 的文件夹的完整路径|
|`${relativeFile}`| 文件或文件夹 (例如，"src\hello.cpp") 的相对路径|
|`${fileBasename}`| 无路径或扩展名 （例如，"你好"） 文件的名称|
|`${fileDirname}`| 文件，不包括文件名 (例如，"C:\sources\hello\src") 的完整路径|
|`${fileExtname}`| 所选的文件 (例如，".cpp") 的扩展|

#### <a name="custom-macros"></a>自定义的宏
若要在 tasks.vs.json 中定义自定义宏，添加任务块之前的名称： 值对。 下面的示例定义一个名为宏`outDir`这在中使用`args`属性：

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
若要自定义程序的命令行自变量，请右键单击中可执行文件**解决方案资源管理器**和选择**调试和启动设置**。 这将打开一个现有`launch.vs.json`文件，或者如果不存在，它将创建一个新的文件，预填充了所选的程序有关的信息。 

若要指定其他参数，只需添加在`args`JSON 数组，如下面的示例中所示：

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

保存此文件时，新的配置出现在调试目标下拉列表中，你可以选择它以启动调试器。 您可以创建许多调试配置，根据需要任意数量的可执行文件。 如果按**F5**现在，则调试器将启动并命中已设置任何断点。 所有熟悉的调试器窗口和其功能现已提供。

## <a name="see-also"></a>请参阅
[用于 Visual C++ 开发的 IDE 和工具](ide-and-tools-for-visual-cpp-development.md)

