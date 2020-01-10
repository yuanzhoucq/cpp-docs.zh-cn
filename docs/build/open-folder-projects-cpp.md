---
title: 对 Visual Studio 中 C++ 生成系统的“打开文件夹”支持
ms.date: 12/02/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 8342060e7286c1089312874199bf341ec36bed62
ms.sourcegitcommit: 6c1960089b92d007fc28c32af1e4bef0f85fdf0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556680"
---
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>对 Visual Studio 中 C++ 生成系统的“打开文件夹”支持

::: moniker range="vs-2015"

Visual Studio 2017 和更高版本中提供了 "打开文件夹" 功能。

::: moniker-end

::: moniker range=">=vs-2017"

Visual Studio 2017 及更高版本中提供了“打开文件夹”功能，可通过它打开源文件的文件夹并借助 IntelliSense、浏览、重构、调试及更多方面的支持立即开始进行编码。 在编辑、创建、移动或删除文件时，Visual Studio 会自动跟踪更改，并不断更新其 IntelliSense 索引。 不加载 .sln 或 .vcxproj 文件；如有需要，可以通过简单的 .json 文件指定自定义任务和生成及启动参数。 此功能使你能够将任何第三方生成系统集成到 Visual Studio 中。 有关“打开文件夹”的常规信息，请参阅[在 Visual Studio 中开发代码而无需创建项目或解决方案](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions)。

## <a name="cmake-and-qt"></a>CMake 和 Qt

CMake 作为C++桌面工作负荷的组件集成到 VISUAL Studio IDE 中。 CMake 的工作流与本文中所述的工作流不完全相同。 如果使用的是 CMake，请参阅[Visual Studio 中的 CMake 项目](cmake-projects-in-visual-studio.md)。 还可以使用 CMake 生成 Qt 项目，也可以使用 Visual Studio 2015 或 Visual Studio 2017 的[Qt Visual Studio 扩展](https://download.qt.io/development_releases/vsaddin/)。

## <a name="other-build-systems"></a>其他生成系统

若要将 Visual Studio IDE 与不直接支持的生成系统或编译器工具集一起使用，请选择 "**文件" |打开 |文件夹**，或按**Ctrl + Shift + Alt + O**。导航到包含源代码文件的文件夹。 若要生成项目，请配置 IntelliSense 并设置调试参数，添加三个 JSON 文件：

| | |
|-|-|
|CppProperties.json|指定用于浏览的自定义配置信息。 如有需要，请在根项目文件夹中创建此文件。 （不用于 CMake 项目。）|
|tasks.vs.json|指定自定义生成命令。 通过“解决方案资源管理器”上下文菜单项“配置任务”进行访问。|
|launch.vs.json|指定调试程序的命令行参数。 通过“解决方案资源管理器”上下文菜单项“调试和启动设置”进行访问。|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>用 Cppproperties.json 配置代码导航

为了使 IntelliSense 和浏览行为（如 "**转到定义**" 正常工作），Visual Studio 需要知道所使用的编译器、系统标头的位置以及任何其他包含文件的位置（如果这些文件不直接位于打开的文件夹中）（工作区文件夹）。 若要指定配置，可以从主工具栏的下拉列表中选择 "**管理配置**"：

![管理配置下拉列表](media/manage-configurations-dropdown.png)

Visual Studio 提供以下默认配置：

![默认配置](media/default-configurations.png)

例如，如果选择**x64-调试**，则 Visual Studio 会在根项目文件夹中创建一个名为*cppproperties.json*的文件：

```json
{
  "configurations": [
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
    }
  ]
}
```

此配置继承 Visual Studio [x64 开发人员命令提示](building-on-the-command-line.md)的环境变量。 其中一个变量是 `INCLUDE` 的，你可以通过使用 `${env.INCLUDE}` 宏在此处进行引用。 `includePath` 属性告诉 Visual Studio 在何处查找 IntelliSense 所需的所有源。 在这种情况下，它会显示 "在 INCLUDE 环境变量指定的所有目录中，同时还显示当前工作文件夹树中的所有目录"。 `name` 属性是将在下拉列表中显示的名称，可以是你喜欢的任何内容。 `defines` 属性在遇到条件编译块时向 IntelliSense 提供提示。 `intelliSenseMode` 属性基于编译器类型提供一些其他提示。 MSVC、GCC 和 Clang 提供了几个选项。

> [!NOTE]
> 如果 Visual Studio 似乎忽略*cppproperties.json*中的设置，请尝试将异常添加到 *.gitignore*文件，如下所示： `!/CppProperties.json`。

## <a name="default-configuration-for-mingw-w64"></a>MinGW 的默认配置-mingw-w64

如果添加 MinGW-Mingw-w64 配置，则 JSON 会将其显示为：

```json
{
  {
      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.BIN_ROOT};${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR}",
          "environment": "mingw_64"
        }
      ]
    }
}
```

请注意 `environments` 块。 它定义了行为类似于环境变量的属性，并且这些属性不仅可在*cppproperties.json*文件中提供，还在其他配置文件*任务*中*提供。* `Mingw64` 配置继承 `mingw_w64` 环境，并使用其 `INCLUDE` 属性为 `includePath`指定值。 您可以根据需要向此数组属性添加其他路径。

`intelliSenseMode` 属性设置为适用于 GCC 的值。 有关所有这些属性的详细信息，请参阅[cppproperties.json 架构参考](cppproperties-schema-reference.md)。

当所有内容都正常工作时，当你将鼠标悬停在某个类型上时，你将看到来自 GCC 标头的 IntelliSense：

![GCC IntelliSense](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>启用 IntelliSense 诊断

如果看不到预期的 IntelliSense，可以通过转到 "**工具**" > **选项**" > **文本编辑器**" > **C/C++**  > **高级**"，并将"**启用日志记录**"设置为**true**，进行故障排除。 首先，尝试将**日志记录级别**设置为5，将**筛选器的日志记录**设置为8。

![诊断日志记录](media/diagnostic-logging.png)

输出将输送到**输出窗口**，并在选择 "*显示输出来源：视觉C++对象日志*" 时显示。 输出中包含 IntelliSense 尝试使用的实际包含路径的列表。 如果路径与*cppproperties.json*中的路径不匹配，请尝试关闭该文件夹，然后删除包含缓存浏览数据的 *. vs*子文件夹。

### <a name="define-build-tasks-with-tasksvsjson"></a>使用 tasks.vs.json 定义生成任务

可以通过直接在 IDE 中作为任务运行来自动执行生成脚本，或者对当前工作区中的现有文件自动执行任何其他外部操作。 可以通过右键单击文件或文件夹并选择“配置任务”来配置新任务。

![“打开文件夹”配置任务](media/configure-tasks.png)

这会在与你的根项目文件夹中创建的 vs 文件夹中创建（或打开） "vs *" 文件。* 可以在此文件中定义任意任务，然后使用从“解决方案资源管理器”上下文菜单调用它。 若要继续使用 GCC 示例，以下代码片段显示了一个完整的*任务. 与 json*文件，其中包含一个调用*g + + .exe*来生成项目的单个任务。 假定项目包含一个名为 "*你好*" 的文件。

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "build hello",
      "appliesTo": "/",
      "type": "default",
      "command": "g++",
      "args": [
        "-g",
        "-o",
        "hello",
        "hello.cpp"
      ]
    }
  ]
}

```

JSON 文件位于 *. vs*子文件夹中。 若要查看该文件夹，请单击**解决方案资源管理器**顶部的 "**显示所有文件**" 按钮。 若要运行此任务，请在**解决方案资源管理器**中右键单击根节点，然后选择 "**生成 hello**"。 任务完成后，应会在**解决方案资源管理器**中看到一个新的文件 " *hello* "。

您可以定义许多类型的任务。 下面的示例演示了一个用于定义单个任务的*任务。* `taskLabel` 定义上下文菜单中显示的名称。 `appliesTo` 定义可在其中执行命令的文件。 `command` 属性指的是 COMSPEC 环境变量，该变量标识控制台（Windows 上的*cmd.exe* ）的路径。 你还可以引用 CppProperties.json 或 CMakeSettings.json 中声明的环境变量。 `args` 属性指定要调用的命令行。 `${file}` 宏检索“解决方案资源管理器”中选定的文件。 下面的示例将显示当前所选 .cpp 文件的文件名。

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```

保存*任务*后，您可以右键单击该文件夹中的任何 *.cpp*文件，从上下文菜单中选择 "**回显文件名**"，然后查看 "输出" 窗口中显示的文件名。

有关详细信息，请参阅 [Tasks.vs.json 架构参考](tasks-vs-json-schema-reference-cpp.md)。

### <a name="configure-debugging-parameters-with-launchvsjson"></a>使用 launch.vs.json 配置调试参数

若要自定义程序的命令行参数和调试说明，请在**解决方案资源管理器**中右键单击可执行文件，然后选择 "**调试和启动设置**"。 这会打开一个现有的*启动*文件，或者，如果不存在，它将创建一个新文件，其中包含一组最小启动设置。 首先，你可以选择想要配置的调试会话类型。 对于调试 MinGw mingw-w64 项目，我们选择**MinGw/Cygwin （C++ gdb）的 C/启动**。 这将创建一个用于使用*gdb*的启动配置，并对默认值进行一些有一定推测的推测。 其中一个默认值为 `MINGW_PREFIX`。 可以用文本路径替换（如下所示），也可以在*cppproperties.json*中定义 `MINGW_PREFIX` 属性：

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "cppdbg",
      "name": "hello.exe",
      "project": "hello.exe",
      "cwd": "${workspaceRoot}",
      "program": "${debugInfo.target}",
      "MIMode": "gdb",
      "miDebuggerPath": "c:\\msys64\\usr\\bin\\gdb.exe",
      "externalConsole": true
    }
  ]
}

```

若要开始调试，请在 "调试" 下拉列表中选择可执行文件，然后单击绿色箭头：

![启动调试器](media/launch-debugger-gdb.png)

应该会看到 "**初始化调试器**" 对话框，然后是运行程序的外部控制台窗口。

有关详细信息，请参阅[启动. 与 json 架构引用](launch-vs-schema-reference-cpp.md)。

## <a name="launching-other-executables"></a>启动其他可执行文件

你可以为计算机上的任何可执行文件定义启动设置。 下面的示例通过将7za 添加到 `args` JSON 数组中，启动并指定其他参数：

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

::: moniker-end
