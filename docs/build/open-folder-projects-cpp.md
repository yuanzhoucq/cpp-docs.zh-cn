---
title: 在 Visual Studio 中打开 c + + 生成系统的文件夹支持
ms.date: 01/21/2019
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: a7e352d7978ba5c973d779224639006fa984e4f0
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824993"
---
# <a name="open-folder-projects-for-c"></a>C + + 的打开文件夹项目

Visual Studio 2017 及更高版本中提供了“打开文件夹”功能，可通过它打开源文件的文件夹并借助 IntelliSense、浏览、重构、调试及更多方面的支持立即开始进行编码。 不加载 .sln 或 .vcxproj 文件；如有需要，可以通过简单的 .json 文件指定自定义任务和生成及启动参数。 有关打开的文件夹的常规信息，请参阅[开发 Visual Studio 中的代码，而无需项目或解决方案](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions)。

CMake 被集成在 Visual Studio IDE 中的 CMake 工具作为 Visual Studio 中，c + + 桌面工作负载的一个组件。 有关详细信息，请参阅[Visual Studio 中的 CMake 项目](cmake-projects-in-visual-studio.md)。 对于任何其他生成系统，可以使用打开文件夹功能。 打开文件夹有效地将分离的代码编辑器、 调试器和分析器生成系统和编译器工具集。 您可以使用其丰富的 IntelliSense 功能、 代码分析器和几乎任何生成系统，包括 CMake、 Ninja、 QMake （对于 Qt 项目）、 gyp、 SCons、 Gradle、 Buck、 品牌和的详细信息的 Visual Studio 调试器中使用 c + + 代码编辑器。 它甚至适用于单个文件或松散文件与任何生成系统的集合。

若要使用“打开文件夹”，请从主菜单选择“文件 | 打开 | 文件夹”或按 Ctrl+Shift+Alt+O。解决方案资源管理器会立即显示该文件夹中的所有文件。 可以单击任何文件开始编辑。 在后台，Visual Studio 开始对文件编制索引，以启用 IntelliSense、导航和重构功能。 在编辑、创建、移动或删除文件时，Visual Studio 会自动跟踪更改，并不断更新其 IntelliSense 索引。 

## <a name="qmake-projects-that-target-the-qt-framework"></a>面向 Qt 框架的 QMake 项目

可以使用 Visual Studio 的 CMake 工具以面向 Qt 生成 Qt 项目，也可以使用[Qt Visual Studio 扩展](https://download.qt.io/development_releases/vsaddin/)Visual Studio 2015 或 Visual Studio 2017。

## <a name="gyp-cons-scons-buck-etc"></a>gyp、Cons、SCons、Buck 等等

可以使用 Visual Studio 中的任何生成系统，并仍喜欢 c + + IDE 和调试器的优势。 打开你的项目的根文件夹时，c + + 代码编辑器使用试探法源文件编制索引的 IntelliSense 和浏览。 可以通过编辑 CppProperties.json 文件提供关于代码结构的提示。 以类似的方式，可以配置和调用通过编辑 launch.vs.json 文件生成程序。

## <a name="configuring-open-folder-projects"></a>配置“打开文件夹”项目

可以通过三个 JSON 文件来自定义“打开文件夹”项目：

| | |
|-|-|
|CppProperties.json|指定用于浏览的自定义配置信息。 如有需要，请在根项目文件夹中创建此文件。 （不使用 CMake 项目中。）|
|tasks.vs.json|指定自定义生成命令和编译器开关。 通过“解决方案资源管理器”上下文菜单项“配置任务”进行访问。|
|launch.vs.json|指定调试器命令行的参数。 通过“解决方案资源管理器”上下文菜单项“调试和启动设置”进行访问。|

### <a name="configure-intellisense-and-browsing-hints-with-cpppropertiesjson"></a>配置 IntelliSense 和浏览使用 CppProperties.json 提示

IntelliSense 和浏览行为在一定程序上取决于活动的生成配置，该配置定义 #include 路径、编译器开关和其他参数。 Visual Studio 默认提供“调试”和“发布”配置。 CMake 项目使用的 CMakeSettings.json 文件提供和 CMakeLists.txt 文件实现此目的。 对于其他类型的打开文件夹项目，可能需要在为了让 IntelliSense 和浏览功能完全理解您的代码中创建自定义配置。 若要定义新的配置，请在根文件夹中创建名为 CppProperties.json 的文件。 下面是一个示例：

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
有关详细信息，请参阅[CppProperties 架构参考](cppproperties-schema-reference.md)。

### <a name="define-build-tasks-with-tasksvsjson"></a>定义使用 tasks.vs.json 生成任务

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

有关详细信息，请参阅[Tasks.vs.json 架构参考](tasks-vs-json-schema-reference-cpp.md)。

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


