---
title: 在 Visual Studio 中创建和配置 Linux CMake 项目
description: 如何在 Visual Studio 中创建、配置、编辑和编译 Linux CMake 项目
ms.date: 10/04/2019
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 128b8dac297398ffbfadfaade5b36c843d55e163
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625953"
---
# <a name="create-and-configure-a-linux-cmake-project"></a>创建和配置 Linux CMake 项目

::: moniker range="vs-2015"

Linux 支持在 Visual Studio 2017 及更高版本中提供。

::: moniker-end

::: moniker range="vs-2019"

若要在 Visual Studio 2019 中创建新的 Linux CMake 项目，请执行以下操作：

1. 在 Visual Studio 中选择“**文件 > 新建项目**”，或按 **Ctrl + Shift + N**。
1. 将“语言”设置为“C++”，然后搜索“CMake”。 然后，选择“下一步”。 输入“名称”和“位置”，然后选择“创建”。

Visual Studio 创建一个最小的 CMakeLists.txt 文件，其中只包含可执行文件的名称和所需的最小 CMake 版本。 可以按自己喜欢的方式手动编辑此文件；Visual Studio 永远不会覆盖所做的更改。 通过右键单击“解决方案资源管理器”中的根目录 CMakeLists.txt 文件，并选择“CMake 项目设置”，指定 CMake 命令行参数和环境变量。 若要指定调试选项，请右键单击项目节点，然后选择“调试并启动设置”。

::: moniker-end

打开包含现有 CMake 项目的文件夹时，Visual Studio 会使用 CMake 缓存中的变量来自动配置 IntelliSense 和生成。 本地配置和调试设置存储在 JSON 文件中，可选择与使用 Visual Studio 的其他人共享这些文件。

Visual Studio 不会修改 CMakeLists.txt 文件，因此处理同一个项目的其他人可继续使用他们已在使用的任何工具。 在保存对 CMakeLists.txt 的编辑或在某些情况下保存对 CMakeSettings.json 的编辑时，Visual Studio 会重新生成缓存。 但是，如果使用的是“现有缓存”配置，则 Visual Studio 不会修改缓存。

有关 Visual Studio 中的 CMake 支持的常规信息，请参阅 [Visual Studio 中的 CMake 项目](../build/cmake-projects-in-visual-studio.md)。 在继续此处的操作前，请先阅读相关内容。

## <a name="before-you-begin"></a>在开始之前

首先，请确保已安装“使用 C++ 的 Linux 开发”工作负载，包括 CMake 组件。 请参阅[在 Visual Studio 中安装 C++ Linux 工作负载](download-install-and-setup-the-linux-development-workload.md)。 

在 Linux 系统上，请确保已安装以下项： 

- gcc
- gdb
- rsync
- zip 

::: moniker range="vs-2019"

Linux 对 CMake 项目的支持要求在目标计算机上安装最新版本的 CMake。 发行版的默认包管理器提供的版本通常不够新，不足以支持 Visual Studio 所需的所有功能。 Visual Studio 2019 会检测 Linux 系统上是否安装了最新版本的 CMake。 如果未找到，Visual Studio 将在编辑器窗格顶部显示一个信息栏，用于从 [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) 安装此最新版本。

使用 Visual Studio 中的 CMake 支持需要 CMake 3.8 中引入的服务器模式支持。 在 Visual Studio 2019 中，建议采用版本 3.14 或更高版本。

::: moniker-end

::: moniker range="vs-2017"

使用 Visual Studio 中的 CMake 支持需要 CMake 3.8 中引入的服务器模式支持。 对于 Microsoft 提供的 CMake 变体，请在 [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) 中下载最新的预生成二进制文件。

二进制文件将安装到 `~/.vs/cmake`。 部署二进制文件后，项目将自动再生成。 请注意，如果由 `CMakeSettings.json` 中的 `cmakeExecutable` 字段指定的 CMake 无效（不存在或是不受支持的版本）且预生成二进制文件存在，则 Visual Studio 将忽略 `cmakeExecutable` 并使用预生成二进制文件。

:::moniker-end

## <a name="open-a-folder"></a>打开文件夹

首先，依次选择主菜单中的“文件” > “打开” > “文件夹”，或在命令行中键入“`devenv.exe <foldername>`”。 打开的文件夹中应该有一个 CMakeLists.txt 文件，以及你的源代码。
以下示例显示了一个简单的 CMakeLists.txt 文件和 .cpp 文件：

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

CMakeLists.txt：

```cmd
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>选择 Linux 目标

只要打开文件夹，Visual Studio 就会分析 CMakeLists.txt 文件，并指定 Windows 目标“x86 调试”。 要以远程 Linux 系统为目标，请将项目设置更改为“Linux 调试”或“Linux 发布”。 （请参阅下面的[配置适用于 Linux 的 CMake 设置](#configure_cmake_linux)。）

::: moniker range="vs-2019"

若要以适用于 Linux 的 Windows 子系统为目标，请单击主工具栏配置下拉列表中的“管理配置”。 如果使用 GCC，请按“添加配置”按钮，选择“WSL 调试” 或“WSL 发布” ；如果使用 Clang/LLVM 工具集，则选择 Clang 变体。 

Visual Studio 2019 版本 16.1：在以 WSL 为目标时，无需复制源或标头，因为 Linux 上的编译器可以直接访问源文件所在的 Windows 文件系统。 （在 Windows 版本 1903 或更高版本中，Windows 应用程序同样可以直接访问 Linux 头文件，但 Visual Studio 还不能利用此功能）。

::: moniker-end

对于远程目标，Visual Studio 默认选择“工具” > “选项” > “跨平台” > “连接管理器”下列表中的第一个远程系统。 如果未找到任何远程连接，那么系统会提示你进行创建。 有关详细信息，请参阅[连接到远程 Linux 计算机](connect-to-your-remote-linux-computer.md)。

如果指定远程 Linux 目标，则会将源复制到远程系统。

选择目标后，CMake 会在 Linux 系统上自动运行，以便为项目生成 CMake 缓存。 

![在 Linux 上生成 CMake 缓存](media/cmake-linux-1.png "在 Linux 上生成 CMake 缓存")

为了向远程 Linux 系统上的标头提供 IntelliSense 支持，Visual Studio 会自动将这些标头从 Linux 计算机复制到本地 Windows 计算机上的目录中。 有关详细信息，请参阅[远程标头的 IntelliSense](configure-a-linux-project.md#remote_intellisense)。

## <a name="debug_cmake_project"></a> 调试 CMake 项目

若要在指定调试目标系统上调试代码，请设置断点，并在项目设置旁边的工具栏菜单中选择“CMake 目标”作为启动项，再选择工具栏中的“&#x23f5; 开始”，或按 F5。

若要自定义程序的命令行参数，请按“解决方案资源管理器”顶部的“切换目标”按钮，然后选择“目标视图”。 然后右键单击一个目标并选择“调试和启动设置”。 这会打开或创建 launch.vs.json 配置文件，其中包含程序信息。 要指定源文件的位置，请将 sourceFileMap 属性添加到该文件中，如以下示例中所示：

```json
"MIMode": "gdb",
"externalConsole": true,
"sourceFileMap": {
"c/Users/USER/source/repos/CMAKEPROJECTNAME": "C:\\Users\\USER\\source\\repos\\CMAKEPROJECTNAME"
},
"remoteMachineName": "${debugInfo.remoteMachineName}",
```

若要指定其他参数，请以 `args` JSON 数组形式添加它们。 有关详细信息，请参阅 [C++ 的“打开文件夹”项目](../build/configure-cmake-debugging-sessions.md)和[配置 CMake 调试会话](../build/open-folder-projects-cpp.md)。

## <a name="configure_cmake_linux"></a> 配置适用于 Linux 的 CMake 设置

CMake Linux 项目中的 CMakeSettings.json 文件可指定在[自定义 CMake 设置](../build/customize-cmake-settings.md)中列出的所有属性，以及控制远程 Linux 计算机上的生成设置的其他属性。 

::: moniker range="vs-2019"

若要在 Visual Studio 2019 中更改默认 CMake 设置，请在主工具栏中打开“配置”下拉列表，然后选择“管理配置”。 

![CMake 管理配置](../build/media/vs2019-cmake-manage-configurations.png "CMake 配置下拉列表")

此操作将打开“CMake 设置编辑器”，可使用它来编辑根项目文件夹中的 `CMakeSettings.json` 文件。 也可以通过单击编辑器中的“编辑 JSON”按钮来直接打开文件。 有关详细信息，请参阅[自定义 CMake 设置](../build/customize-cmake-settings.md)。

::: moniker-end

::: moniker range="vs-2017"

若要在 Visual Studio 2017 中更改默认 CMake 设置，请从主菜单依次选择“CMake”|“更改 CMake 设置”|“CMakeLists.txt”，或右键单击“解决方案资源管理器”中的“CMakeSettings.txt”，然后选择“更改 CMake 设置”。 然后，visual Studio 会在根项目文件夹中创建一个新的 `CMakeSettings.json` 文件。 可使用“CMake 设置”编辑器打开文件或直接修改该文件。 有关详细信息，请参阅[自定义 CMake 设置](../build/customize-cmake-settings.md)。

以下示例显示了基于上述代码示例的 Visual Studio 2017（以及 Visual Studio 2019 版本 16.0）中 Linux 调试的默认配置：

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "remoteMachineName": "${defaultRemoteMachineName}",
      "configurationType": "Debug",
      "remoteCMakeListsRoot": "/var/tmp/src/${workspaceHash}/${name}",
      "cmakeExecutable": "/usr/local/bin/cmake",
      "buildRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteInstallRoot": "/var/tmp/build/${workspaceHash}/install/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "remoteCopySourcesMethod": "rsync",
      "remoteCopySourcesExclusionList": [".vs", ".git"],
      "rsyncCommandArgs" : "-t --delete --delete-excluded",
      "remoteCopyBuildOutput" : "false",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```

::: moniker-end

::: moniker range="vs-2019"

 Visual Studio 2019 版本 16.1 中的默认 Linux 调试配置如下所示：

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "configurationType": "Debug",
      "cmakeExecutable": "/usr/bin/cmake",
      "remoteCopySourcesExclusionList": [ ".vs", ".git", "out" ],
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux_x64" ],
      "remoteMachineName": "${defaultRemoteMachineName}",
      "remoteCMakeListsRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/src",
      "remoteBuildRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/build/${name}",
      "remoteInstallRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/install/${name}",
      "remoteCopySources": true,
      "rsyncCommandArgs": "-t --delete --delete-excluded",
      "remoteCopyBuildOutput": false,
      "remoteCopySourcesMethod": "rsync",
      "addressSanitizerRuntimeFlags": "detect_leaks=0",
      "variables": []
    }
  ]
}
```
::: moniker-end

有关这些设置的详细信息，请参阅 [CMakeSettings.json 引用](../build/cmakesettings-reference.md)。


## <a name="optional-settings"></a>可选设置

可使用以下可选设置进行更多控制：

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

这些选项可用于生成前后以及 CMake 生成前在 Linux 系统中运行命令。 值可以是远程系统上的任何有效命令。 输出通过管道传递回 Visual Studio。



## <a name="see-also"></a>请参阅

[使用项目属性](../build/working-with-project-properties.md)<br/>
[Visual Studio 中的 CMake 项目](../build/cmake-projects-in-visual-studio.md)<br/>
[连接到远程 Linux 计算机](connect-to-your-remote-linux-computer.md)<br/>
[自定义 CMake 设置](../build/customize-cmake-settings.md)<br/>
[配置 CMake 调试会话](../build/configure-cmake-debugging-sessions.md)<br/>
[部署、运行和调试 Linux 项目](deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 预定义配置引用](../build/cmake-predefined-configuration-reference.md)<br/>
