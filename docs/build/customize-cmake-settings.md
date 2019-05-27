---
title: 在 Visual Studio 中自定义 CMake 生成设置
ms.date: 05/16/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: d8102250fa59dc787cc48fc293ac740b81b4446c
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837112"
---
# <a name="customize-cmake-build-settings"></a>自定义 CMake 生成设置

::: moniker range="vs-2019"

在 Visual Studio 2019 及更高版本中，可以使用“CMake 设置编辑器”添加配置并自定义其设置。 编辑器是手动编辑 CMakeSettings.json 文件的更简单的替代方法，但是如果你希望直接编辑文件，可以单击编辑器右上角的“编辑 JSON”链接。 

若要添加编辑器，请单击主工具栏的“配置”下拉列表，然后选择“管理配置”。

![CMake 配置下拉列表](media/vs2019-cmake-manage-configurations.png)

现在可以看到“设置编辑器”左侧显示了已安装的配置。 

![CMake 设置编辑器](media/cmake-settings-editor.png)

Visual Studio 默认提供两种配置：`x64-Debug` 和 `x86-Debug`。 可以单击绿色加号添加其他配置。在编辑器中看到的设置可能会因所选的配置而有所不同。

在编辑器中选择的选项会写入名为 CMakeSettings.json 的文件中。 此文件提供生成项目时传递到 CMake 的命令行参数和环境变量。 Visual Studio 不会自动修改 CMakeLists.txt；使用 CMakeSettings.json，可通过 Visual Studio 自定义生成，同时保持 CMake 项目文件不变，确保团队中的其他人可以使用当前工具进行处理。

## <a name="cmake-general-settings"></a>CMake 常规设置

“常规”标题下提供了以下设置：

### <a name="configuration-name"></a>配置名称

对应于“名称”设置。 这是显示在 C++ 配置下拉列表中的名称。 可以使用 `${name}` 宏编写其他属性值（如路径）。


### <a name="configuration-type"></a>配置类型

对应于“configurationType”设置。 定义所选生成器的生成配置类型。 当前支持的值为“Debug”、“MinSizeRel”、“Release”和“RelWithDebInfo”。

### <a name="toolset"></a>工具集

对应于“inheritedEnvironments”设置。 定义将用于生成所选配置的编译器环境。 支持的值取决于配置类型。 若要创建自定义环境，请单击“设置”编辑器右上角中的“编辑 JSON”链接，然后直接编辑 CMakeSettings.json 文件。

### <a name="cmake-toolchain-file"></a>CMake 工具链文件

CMake 工具链文件的路径。 将作为“-DCMAKE_TOOLCHAIN_FILE = \<filepath>”传递给 CMake。

### <a name="build-root"></a>生成根目录

对应于“buildRoot”。 映射到“-DCMAKE_BINARY_DIR”开关，并指定要创建 CMake 缓存的位置。 如果文件夹不存在，则会创建一个。

## <a name="command-arguments"></a>命令参数

“命令参数”标题下提供了以下设置：

### <a name="cmake-command-arguments"></a>CMake 命令参数

对应于“cmakeCommandArgs”。 指定要传递给 CMake.exe 的任何其他开关。

### <a name="build-command-arguments"></a>生成命令参数

对应于“buildCommandArgs”：指定传递给基础生成系统的其他开关。 例如，使用 Ninja 生成器强制输出命令行使用 Ninja 时，传递 -v。


### <a name="ctest-command-arguments"></a>CTest 命令参数

对应于“ctestCommandArgs”：指定运行测试时传递给 CTest 的其他开关。

## <a name="general-settings-for-remote-builds"></a>远程生成的常规设置

对于使用远程生成的配置（如 Linux），还提供以下设置：

### <a name="rsync-command-arguments"></a>rsync 命令参数

提供要传递给 rsync 的任何命令参数。 

## <a name="cmake-variables-and-cache"></a>CMake 变量和缓存

通过这些设置，可设置 CMake 变量并将其保存在 CMakeSettings.json 中。 它们将在生成时传递给 CMake，并将替代 CMakeLists.txt 文件中的任何值。 你可以按照此部分所述使用 CMakeGUI 来查看可编辑的所有 CMake 变量列表相同。 单击“保存并生成缓存”按钮以查看所有可编辑的 CMake 变量列表，包括高级变量（根据 CMakeGUI）。 可以按变量名称筛选列表。 

对应于“变量”：包含将作为“-D name=value”传递给 CMake 的 CMake 变量的名称/值对。 如果 CMake 项目生成指令指定将任何变量直接添加到 CMake 缓存文件，那么建议改为在这里添加它们。

## <a name="advanced-settings"></a>高级设置

### <a name="cmake-generator"></a>CMake 生成器

对应于“生成器”：映射到 CMake“-G”开关并指定要使用的生成器。 编写其他属性时，此属性也可用作宏 `${generator}`。 Visual Studio 当前支持下列 CMake 生成器：

  - "Ninja"
  - “Unix 生成文件”
  - “Visual Studio 16 2019”
  - “Visual Studio 16 2019 Win64”
  - - “Visual Studio 16 2019 ARM”
  - "Visual Studio 15 2017"
  - "Visual Studio 15 2017 Win64"
  - "Visual Studio 15 2017 ARM"
  - "Visual Studio 14 2015"
  - "Visual Studio 14 2015 Win64"
  - "Visual Studio 14 2015 ARM"
  
  由于 Ninja 旨在加快生成速度，而不是为了提高灵活性和功能，因此它被设为默认生成器。 但是，某些 CMake 项目可能无法使用 Ninja 正确地进行生成。 如果发生这种情况，可以指示 CMake 改为生成 Visual Studio 项目。

### <a name="intellisense-mode"></a>IntelliSense 模式

为获得准确的 IntelliSense，请将其设置为适合项目的值。

### <a name="install-directory"></a>安装目录

CMake 在其中安装生成目标的目录。

### <a name="cmake-executable"></a>CMake 可执行文件

CMake 可执行文件的完整路径，包括文件名和扩展名。 对于远程生成，请在远程计算机上指定 CMake 位置。

对于使用远程生成的配置（如 Linux），还提供以下设置：

### <a name="remote-cmakeliststxt-root"></a>远程 CMakeLists.txt 根目录

远程计算机上包含根文件 CMakeLists.txt 的目录。

### <a name="remote-install-root"></a>远程安装根目录

远程计算机上 CMake 在其中安装目标的目录。

### <a name="remote-copy-sources"></a>远程复制源

指定是否将源文件复制到远程计算机，并允许你指定是使用 rsync 还是 sftp。 

## <a name="directly-edit-cmakesettingsjson"></a>直接编辑 CMakeSettings.json

还可以直接编辑 `CMakeSettings.json` 以创建自定义配置。 “设置编辑器”的右上角有一个“编辑 JSON”按钮，单击该按钮可打开文件进行编辑。 

下面的示例演示了一个示例配置，可将该配置用作起点：

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },

```

可借助 JSON IntelliSense 编辑 `CMakeSettings.json` 文件：

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

当你选择的设置不兼容时，JSON 编辑器还会进行提示。

有关文件中每个属性的详细信息，请参阅 [CMakeSettings.json 架构引用](cmakesettings-reference.md)。

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 提供多个 CMake 配置，这些配置定义如何调用 CMake.exe 来创建给定项目的 CMake 缓存。 若要添加新的配置，请单击工具栏的下拉列表中的配置，然后选择“管理配置”：

   ![CMake 管理配置](media/cmake-manage-configurations.png)

可从预定义配置列表中进行选择：

   ![CMake 预定义配置](media/cmake-configurations.png)

第一次选择配置时，Visual Studio 会在项目的根文件夹里创建一个 `CMakeSettings.json` 文件。 此文件用于重新创建 CMake 缓存文件，例如，在“清除”操作后重新创建。 

要添加其他配置，请右键单击 `CMakeSettings.json`，然后选择“添加配置”。 

   ![CMake 添加配置](media/cmake-add-configuration.png "CMake Add Configuration")

也可使用“CMake 设置编辑器”来编辑文件。 右键单击“解决方案资源管理器”中的 `CMakeSettings.json`，然后选择“编辑 CMake 设置”。 或者，从顶部的编辑器窗口的配置下拉列表中选择“管理配置”。 

还可直接编辑 `CMakeSettings.json` 以创建自定义配置。以下示例显示了一个示例配置，可将该配置用作起点：

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },

```

可借助 JSON IntelliSense 编辑 `CMakeSettings.json` 文件：

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

有关文件中每个属性的详细信息，请参阅 [CMakeSettings.json 架构引用](cmakesettings-reference.md)。

::: moniker-end

## <a name="see-also"></a>请参阅

[Visual Studio 中的 CMake 项目](cmake-projects-in-visual-studio.md)<br/>
[配置 Linux CMake 项目](../linux/cmake-linux-project.md)<br/>
[连接到远程 Linux 计算机](../linux/connect-to-your-remote-linux-computer.md)<br/>
[配置 CMake 调试会话](configure-cmake-debugging-sessions.md)<br/>
[部署、运行和调试 Linux 项目](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 预定义配置引用](cmake-predefined-configuration-reference.md)<br/>
