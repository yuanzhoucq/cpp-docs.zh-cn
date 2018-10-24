---
title: 在 Visual Studio 中配置 Linux CMake 项目 | Microsoft Docs
description: 如何在 Visual Studio 中配置 Linux CMake 项目
ms.custom: ''
ms.date: 07/20/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 20291e1f824704ee94cb45f14c16d6f0e4960348
ms.sourcegitcommit: db6b2ad3195e71abfb60b62f3f015f08b0a719d0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410832"
---
# <a name="configure-a-linux-cmake-project"></a>配置 Linux CMake 项目

**Visual Studio 2017 版本 15.4 及更高版本**<br/>
为 Visual Studio 安装 Linux C++ 工作负载时，会默认选中对 Linux 的 CMake 支持。 现在即可处理使用 CMake 的现有基本代码，无需将其转换为 Visual Studio 项目。 如果基本代码为跨平台代码，则从 Visual Studio 中可同时面向 Windows 和 Linux。

本主题假定你基本了解 Visual Studio 中的 CMake 支持。 有关详细信息，请参阅 [Visual C++ 的 CMake 工具](../ide/cmake-tools-for-visual-cpp.md)。 有关 CMake 本身的详细信息，请参阅[使用 CMake 生成、测试并打包软件](https://cmake.org/)。

> [!NOTE]  
> 使用 Visual Studio 中的 CMake 支持需要 CMake 3.8 中引入的服务器模式支持。 对于 Microsoft 提供的 CMake 变体，请在 [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) 中下载最新的预生成二进制文件。 

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
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>选择 Linux 目标

只要打开文件夹，Visual Studio 就会分析 CMakeLists.txt 文件，并指定“x86 调试”以定目标到 Windows。 若要定目标到 Linux，请将项目设置更改为“Linux 调试”或“Linux 发布”。

默认情况下，Visual Studio 会选择“工具” > “选项” > “跨平台” > “连接管理器”下列表中的第一个远程系统。 如果未找到任何远程连接，那么系统会提示你进行创建。

指定 Linux 目标后，会将源复制到你的 Linux 计算机。 然后，CMake 在 Linux 计算机上运行，为项目生成 CMake 缓存。

![在 Linux 上生成 CMake 缓存](media/cmake-linux-1.png "Generate the CMake cache on Linux")

**Visual Studio 2017 版本 15.7 及更高版本：**<br/>
为了向远程头提供 IntelliSense 支持，Visual Studio 会自动将远程头复制到本地 Windows 计算机上的目录中。 有关详细信息，请参阅[远程标头的 IntelliSense](configure-a-linux-project.md#remote_intellisense)。

## <a name="debug-the-project"></a>调试项目

若要在远程系统上调试代码，请设置断点，并在项目设置旁边的工具栏菜单中选择“CMake 目标”作为启动项，再选择工具栏中的“&#x23f5; 开始”，或按 F5。

若要自定义程序的命令行参数，请右键单击解决方案资源管理器中的可执行文件，并选择“调试和启动设置”。 这会打开或创建 launch.vs.json 配置文件，其中包含程序信息。 若要指定其他参数，请以 `args` JSON 数组形式添加它们。 有关详细信息，请参阅 [Visual C++ 中的“打开文件夹”项目](../ide/non-msbuild-projects.md)。

## <a name="configure-cmake-settings-for-linux"></a>配置适用于 Linux 的 CMake 设置

若要更改默认的 CMake 设置，请从主菜单依次选择“CMake”|“更改 CMake 设置”|“CMakeLists.txt”，或右键单击“解决方案资源管理器”中的“CMakeSettings.txt”，然后选择“更改 CMake 设置”。 然后，Visual Studio 在名为 `CMakeSettings.json` 的文件夹中创建一个新文件，并使用项目设置菜单项中列出的默认配置进行填充。 以下示例显示了基于上述代码示例的 Linux 调试的默认配置：

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

可按需设置 `name` 值。 `remoteMachineName` 值指定了目标远程系统（以防存在多个系统）。 此字段启用了 IntelliSense，可帮助你选择正确的系统。 字段 `remoteCMakeListsRoot` 指定将项目源复制到远程系统上的何处。 字段 `remoteBuildRoot` 是远程系统上生成“生成输出”的位置。 还会在本地将该输出复制到由 `buildRoot` 指定的位置。 `remoteInstallRoot` 和 `installRoot` 字段与 `remoteBuildRoot` 和 `buildRoot` 类似，只不过在执行 cmake 安装时应用它们。 `remoteCopySources` 项控制是否将本地源复制到远程计算机。 如果具有大量文件且已自行同步源，则可能要将其设置为 false。 `remoteCopyOutputVerbosity` 值控制复制步骤的详细级别，以防需要诊断错误。 `remoteCopySourcesConcurrentCopies` 项控制要生成多少进程来执行复制。 `remoteCopySourcesMethod` 值可以是任一 rsync 或 sftp。 `remoteCopySourcesExclusionList` 字段可用于控制复制到远程计算机上的内容。 `rsyncCommandArgs` 值可用于控制复制的 rsync 方法。 `remoteCopyBuildOutput` 字段控制是否要将远程生成输出复制到本地生成文件夹。

还有一些可选设置，可用于其他控制：

```json
{
      "remotePreBuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostBuildCommand": "",
}
```

这些选项可用于生成前后以及 CMake 生成前在远程框中运行命令。 它们可以是远程框上的任何有效命令。 输出通过管道传递回 Visual Studio。

## <a name="download-prebuilt-cmake-binaries"></a>下载预生成的 CMake 二进制文件

你的 Linux 发行版可能具有更早版本的 CMake。 使用 Visual Studio 中的 CMake 支持需要 CMake 3.8 中引入的服务器模式支持。 对于 Microsoft 提供的 CMake 变体，请在 [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) 中下载最新的预生成二进制文件。 


## <a name="see-also"></a>请参阅

[使用项目属性](../ide/working-with-project-properties.md)<br/>
[Visual C++ 的 CMake 工具](../ide/cmake-tools-for-visual-cpp.md)  
