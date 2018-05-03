---
title: 在 Visual Studio 中配置 Linux CMake 项目 | Microsoft Docs
ms.custom: ''
ms.date: 10/25/2107
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-linux
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 961419e9ffcd5dede0db01f81e1b1eedc3290436
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="configure-a-linux-cmake-project"></a>配置 Linux CMake 项目
  
**Visual Studio 2017 版本 15.4** 安装 Linux C++ 工作负载时，会默认选中对 Linux 的 CMake 支持。 现在即可处理使用 CMake 的现有基本代码，无需将其转换为 Visual Studio 项目。 如果基本代码为跨平台代码，则从 Visual Studio 中可同时面向 Windows 和 Linux。 

本主题假定你基本了解 Visual Studio 中的 CMake 支持。 有关详细信息，请参阅 [Visual C++ 的 CMake 工具](../ide/cmake-tools-for-visual-cpp.md)。 有关 CMake 本身的详细信息，请参阅[使用 CMake 生成、测试并打包软件](https://cmake.org/)。

> [!NOTE] 
> 使用 Visual Studio 中的 CMake 支持需要 CMake 3.8 中引入的服务器模式支持。 如果包管理器提供的 CMake 版本较旧，你可从源构建 CMake 3.8 来解决此问题。



## <a name="open-a-folder"></a>打开文件夹
若要开始，请从主菜单依次选择“文件”|“打开”|“文件件”，或者在命令行上键入 `devenv.exe <foldername>`。 打开的文件夹中应该有一个 CMakeLists.txt 文件，以及你的源代码。
以下示例显示了一个简单的 CMakeLists.txt 文件和 .cpp 文件：

```cpp
// Hello.cpp

#include <iostream>;
 
int main(int argc, char* argv[])
{
    std::cout << "Hello" << std::endl;
}
```

CMakeLists.txt： 
```cmd
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>选择 Linux 目标
只要打开文件夹，Visual Studio 就会分析 CMakeLists.txt 文件，并指定 Windows 目标使用 x86 调试。 若要以 Linux 为目标，请将项目设置更改为 Linux 调试或 Linux 版本。

默认情况下，Visual Studio 会选择列表中的第一个远程系统（位于“工具”|“选项”|“跨平台”|“连接管理器”下）。 如果未找到任何远程连接，那么系统会提示你进行创建。

指定 Linux 目标后，会将源复制到你的 Linux 计算机。 然后，CMake 在 Linux 计算机上运行，为项目生成 CMake 缓存。  

![在 Linux 上生成 CMake 缓存](media/cmake-linux-1.png "Generate the CMake cache on Linux")  

## <a name="debug-the-project"></a>调试项目  
若要在远程系统上调试代码，设置一个断点，并在项目设置旁的工具栏菜单中选择 CMake 目标作为启动项，然后单击“运行”（或按 F5）。

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
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```
可按需设置 `name` 值。 `remoteMachineName` 值指定了目标远程系统（以防存在多个系统）。 此字段启用了 IntelliSense，可帮助你选择正确的系统。 字段 `remoteCMakeListsRoot` 指定将项目源复制到远程系统上的何处。 字段 `remoteBuildRoot` 是远程系统上生成“生成输出”的位置。 还会在本地将该输出复制到由 `buildRoot` 指定的位置。

## <a name="building-a-supported-cmake-release-from-source"></a>从源生成受支持的 CMake 版本
Linux 计算机所需的最低 CMake 版本是 3.8，并它还必须支持服务器模式。 若要进行验证，请运行此命令：

```cmd
cmake --version
```

若要验证是否启用了该服务器模式，请运行：

```cmd
cmake -E capabilities
```

在输出中，查找 “serverMode”:true。 请注意，即使按如下所述从源编译 CMake，也应该在完成后检查各项功能。 Linux 系统可能存在限制，会阻止启用服务器模式。

若要在 Linux 系统的 shell 中开始从源进行生成，请确保包管理器为最新版，且可使用 git 和 cmake。 首先，从我们用于 Visual Studio 的 CMake 支持的存储库中克隆 CMake 源：

```cmd
sudo apt-get update
sudo apt-get install -y git cmake
git clone https://github.com/Microsoft/CMake.git
cd CMake
```

然后运行以下命令：

```cmd
mkdir out
cd out
cmake ../
make
sudo make install
```

上面的命令生成当前版本的 CMake，并将其安装到 /usr/local/bin。 运行以下命令验证该版本是否为 3.8 或更高版本，以及是否启用了服务器模式：

```cmd
/usr/local/bin/cmake –version
cmake -E capabilities
```

## <a name="see-also"></a>请参阅
[使用项目属性](../ide/working-with-project-properties.md)  
[Visual C++ 的 CMake 工具](../ide/cmake-tools-for-visual-cpp.md)
