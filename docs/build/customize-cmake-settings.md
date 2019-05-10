---
title: 在 Visual Studio 中自定义 CMake 生成设置
ms.date: 04/25/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: 20ed066f71a5c8c3acb00ef5923fa5c9f16ac229
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877161"
---
# <a name="customize-cmake-build-settings"></a>自定义 CMake 生成设置

::: moniker range="vs-2019"

在 Visual Studio 2019 及更高版本，可以添加配置和使用自定义其设置**CMake 设置编辑器**。 编辑器用于更简单的替代手动编辑 CMakeSettings.json 文件中，但如果你喜欢直接编辑文件，你可以单击**编辑 JSON**右上方的编辑器中的链接。 

若要打开编辑器中，单击**配置**在主工具栏中的下拉列表中，选择**管理配置**。

![CMake 配置下拉列表](media/vs2019-cmake-manage-configurations.png)

现在，会看到**设置编辑器**在左侧的已安装配置。 

![CMake 设置编辑器](media/cmake-settings-editor.png)

Visual Studio 提供两个配置了默认情况下：`x64-Debug`和`x86-Debug`。 通过单击绿色加号，可以添加其他配置。在编辑器中看到的设置可能有所不同，具体取决于选择配置。

在编辑器中选择的选项将写入一个名为 CMakeSettings.json 文件。 此文件提供了命令行自变量和生成项目时传递给 CMake 的环境变量。 Visual Studio 永远不会修改 CMakeLists.txt 自动保存功能。使用 CMakeSettings.json 可以自通过 Visual Studio 的生成定义时，使你的团队中的其他人可以使用它们与正在使用任何工具，CMake 项目文件保持不变。

## <a name="cmake-general-settings"></a>CMake 常规设置

以下设置下有**常规**标题：

### <a name="configuration-name"></a>配置名称

对应于**名称**设置。 这是在显示的名称C++配置下拉列表。 可以使用`${name}`宏编写其他属性值，例如路径。


### <a name="configuration-type"></a>配置类型

对应于**配置类型**设置。 定义生成配置类型为选定的生成器。 当前支持的值为“Debug”、“MinSizeRel”、“Release”和“RelWithDebInfo”。

### <a name="toolset"></a>工具集

对应于**inheritedEnvironments**设置。 用于定义将用于生成所选的配置的编译器环境。 支持的值取决于配置的类型。 若要创建自定义环境，请单击**编辑 JSON**设置编辑器的右上角中的链接并直接编辑 CMakeSettings.json 文件。

### <a name="cmake-toolchain-file"></a>CMake 工具链文件

CMake 工具链文件的路径。 将传递给 CMake 作为"-DCMAKE_TOOLCHAIN_FILE =\<文件路径 >"。

### <a name="build-root"></a>生成根

对应于**buildRoot**。 映射到 **-DCMAKE_BINARY_DIR**切换并指定将在其中创建 CMake 缓存。 如果文件夹不存在，则会创建一个。

## <a name="command-arguments"></a>命令参数

以下设置下有**命令参数**标题：

### <a name="cmake-command-arguments"></a>CMake 命令参数

对应于**cmakeCommandArgs**。 指定你想要传递给 CMake.exe 任何其他开关。

### <a name="build-command-arguments"></a>生成命令参数

对应于**buildCommandArgs**： 指定其他交换机，以传递给基础生成系统。 例如，使用 Ninja 生成器强制输出命令行使用 Ninja 时，传递 -v。


### <a name="ctest-command-arguments"></a>CTest 命令参数

对应于**ctestCommandArgs**： 指定要运行测试时传递给 CTest 的其他开关。

## <a name="general-settings-for-remote-builds"></a>远程生成的常规设置

对于使用远程生成的配置，如 Linux，以下设置也是可用的：

### <a name="rsync-command-arguments"></a>rsync 命令参数

提供要传递给 rsync 的任何命令参数。 

## <a name="cmake-variables-and-cache"></a>CMake 变量和缓存

这些设置，可设置 CMake 变量并将其保存在 CMakeSettings.json 中。 它们将在生成时传递给 CMake，并且将重写任何值可能会在 CMakeLists.txt 文件中。 在可能使用 CMakeGUI 若要查看所有可编辑的 CMake 变量列表的相同方式，可以使用此部分。 单击**保存并生成缓存**按钮以查看所有 CMake 变量可用于编辑的列表包括高级的变量 （每个 CMakeGUI)。 可以按变量名称来筛选列表。 

对应于**变量**： 包含将为传入的 CMake 变量的名称-值对 **-D** *_名称_= _值_* 给 CMake。 如果 CMake 项目生成指令指定将任何变量直接添加到 CMake 缓存文件，那么建议改为在这里添加它们。

## <a name="advanced-settings"></a>高级设置

### <a name="cmake-generator"></a>CMake 生成器

对应于**生成器**： 将映射到 CMake **-G**切换并指定要使用的生成器。 编写其他属性时，此属性也可用作宏 `${generator}`。 Visual Studio 当前支持下列 CMake 生成器：

  - "Ninja"
  - "Unix 生成文件"
  - "Visual Studio 16 2019年"
  - "Visual Studio 16 2019 Win64"
  - - "Visual Studio 16 2019 ARM"
  - "Visual Studio 15 2017"
  - "Visual Studio 15 2017 Win64"
  - "Visual Studio 15 2017 ARM"
  - "Visual Studio 14 2015"
  - "Visual Studio 14 2015 Win64"
  - "Visual Studio 14 2015 ARM"
  
  由于 Ninja 旨在加快生成速度，而不是为了提高灵活性和功能，因此它被设为默认生成器。 但是，某些 CMake 项目可能无法使用 Ninja 正确地进行生成。 如果发生这种情况，可以指示 CMake 改为生成 Visual Studio 项目。

### <a name="intellisense-mode"></a>IntelliSense 模式

对于准确 IntelliSense、 其设置为适当的值为你的项目。

### <a name="install-directory"></a>安装目录

CMake 在其中安装生成的目标目录。

### <a name="cmake-executable"></a>CMake 可执行文件

为 CMake 可执行文件，其中包括文件名和扩展名的完整路径。 对于远程生成，在远程计算机上指定的 CMake 位置。

对于使用远程生成的配置，如 Linux，以下设置也是可用的：

### <a name="remote-cmakeliststxt-root"></a>远程 CMakeLists.txt 根

包含根 CMakeLists.txt 文件的远程计算机上的目录。

### <a name="remote-install-root"></a>远程安装根

CMake 在其中安装目标的远程计算机上的目录。

### <a name="remote-copy-sources"></a>远程复制源

指定是否将源文件复制到远程计算机并使您能够指定是否选择 rsync 或 sftp。 

## <a name="directly-edit-cmakesettingsjson"></a>直接编辑 CMakeSettings.json

您可以直接编辑`CMakeSettings.json`若要创建自定义配置。 **设置编辑器**已**编辑 JSON**打开文件进行编辑的右上角的按钮。 

下面的示例演示可以用作起始点的示例配置：

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

JSON IntelliSense 可帮助你编辑`CMakeSettings.json`文件：

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

JSON 编辑器还将提示您选择不兼容的设置。

有关每个文件中的属性的详细信息，请参阅[CMakeSettings.json 架构参考](cmakesettings-reference.md)。

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 提供了多个 CMake 配置用于定义如何调用 CMake.exe 创建给定项目的 CMake 缓存。 若要添加新的配置，请单击工具栏的下拉列表中的配置，然后选择“管理配置”：

   ![CMake 管理配置](media/cmake-manage-configurations.png)

可从预定义配置列表中进行选择：

   ![CMake 预定义配置](media/cmake-configurations.png)

第一次选择配置时，Visual Studio 会在项目的根文件夹里创建一个 `CMakeSettings.json` 文件。 此文件用于重新创建 CMake 缓存文件，例如，在“清除”操作后重新创建。 

要添加其他配置，请右键单击 `CMakeSettings.json`，然后选择“添加配置”。 

   ![CMake 添加配置](media/cmake-add-configuration.png "CMake Add Configuration")

也可使用“CMake 设置编辑器”来编辑文件。 右键单击“解决方案资源管理器”中的 `CMakeSettings.json`，然后选择“编辑 CMake 设置”。 或者，从顶部的编辑器窗口的配置下拉列表中选择“管理配置”。 

您可以直接编辑`CMakeSettings.json`若要创建自定义配置下面的示例显示了一个示例配置，可以使用作为起始点：

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

有关每个文件中的属性的详细信息，请参阅[CMakeSettings.json 架构参考](cmakesettings-reference.md)。

::: moniker-end

## <a name="see-also"></a>请参阅

[Visual Studio 中的 CMake 项目](cmake-projects-in-visual-studio.md)<br/>
[配置 Linux CMake 项目](../linux/cmake-linux-project.md)<br/>
[连接到远程 Linux 计算机](../linux/connect-to-your-remote-linux-computer.md)<br/>
[配置 CMake 调试会话](configure-cmake-debugging-sessions.md)<br/>
[部署、运行和调试 Linux 项目](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 预定义配置引用](cmake-predefined-configuration-reference.md)<br/>
