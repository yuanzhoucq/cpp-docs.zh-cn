---
title: 在 Visual Studio 中创建 C++ 跨平台项目
description: 本教程介绍如何在同时面向 Linux 和 Windows 的 Visual Studio 中设置、编译和调试 C++ 开源 CMake 项目。
author: mikeblome
ms.topic: tutorial
ms.date: 03/05/2019
ms.openlocfilehash: cd01d5e389bda46fbb05d297ece8e68ef2265725
ms.sourcegitcommit: c53a3efcc5d51fc55fa57ac83cca796b33ae888f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71960730"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>教程：在 Visual Studio 中创建 C++ 跨平台项目 

Visual Studio C 和 C++ 开发不再仅适用于 Windows。 本教程介绍如何使用基于 CMake 的 Visual Studio for C++ 跨平台开发，而无需创建或生成 Visual Studio 项目。 当打开包含 CMakeLists.txt 文件的文件夹时，Visual Studio 会自动配置 IntelliSense 并生成设置。 可以在 Windows 上快速编辑、生成和调试代码，然后在 Visual Studio 中切换配置以在 Linux 上执行相同的操作。

在本教程中，你将了解：

> [!div class="checklist"]
> * 从 GitHub 克隆一个开源 CMake 项目
> * 在 Visual Studio 中打开项目 
> * 在 Windows 上生成和调试可执行目标
> * 添加与 Linux 计算机的连接
> * 在 Linux 上生成和调试相同的目标

## <a name="prerequisites"></a>先决条件

- 设置适用于跨平台 C++ 开发的 Visual Studio
    - 首先你需要[安装 Visual Studio](https://visualstudio.microsoft.com/vs/)。 接下来，确认安装了“使用 C++ 的桌面开发”和“使用 C++ 的 Linux 开发”工作负载。 此最小安装仅有 3 GB，根据下载速度安装不应超过 10 分钟。
- 设置适用于跨平台 C++ 开发的 Linux 计算机
    - Visual Studio 不需要任何特定的 Linux 发行版。 OS 可以在物理计算机、VM 种、云或 Linux Windows 子系统 (WSL) 上运行。 但是，本教程需要一个图形环境；因此不推荐 WSL，因为它主要用于命令行操作。
    - Visual Studio 在 Linux 计算机上需要的工具是：C++编译器、GDB、ssh、rsync 和 zip。 在基于 Debian 的系统上，可以按如下方式安装这些依赖项。
    
    ```cmd
        sudo apt install -y openssh-server build-essential gdb rsync zip
    ```
    - Visual Studio 要求 Linux 计算机具有启用服务器模式的最新版 CMake（至少为 3.8 版）。 Microsoft 生成可以在任何 Linux 发行版上安装的通用 CMake 版本。 建议使用此版本以确保拥有最新功能。 可从 GitHub 上的 [CMake 存储库 Microsoft 分支](https://github.com/Microsoft/CMake/releases)获得 CMake 二进制文件。 转到该页面并下载与 Linux 计算机上的系统架构匹配的版本，然后将其标记为可执行文件：
    
    ```cmd
        wget <path to binary>
        chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```
    - 可以使用 `-–help` 查看运行脚本的选项。 建议使用 `–prefix` 选项在“/usr/local”路径中指定安装，因为这是 Visual Studio 查找 CMake 的默认位置。 以下示例显示了 Linux-x86_64 脚本。 如果使用其他目标平台，请根据需要进行更改。 
    
    ```cmd
        sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr/local
    ```
- 在 Windows 计算机上安装的适用于 Windows 的 Git。
- 一个 GitHub 帐户。

## <a name="clone-an-open-source-cmake-project-from-github"></a>从 GitHub 克隆一个开源 CMake 项目

本教程使用 GitHub 上的 Bullet Physics SDK，为各种不同的应用程序提供冲突检测和物理模拟。 它包括示例可执行程序，这些程序无需编写额外代码即可编译和运行。 本教程未修改任何源代码或生成脚本。 首先，从安装了 Visual Studio 的计算机上的 GitHub 克隆 bullet3 存储库。 

```cmd

git clone https://github.com/bulletphysics/bullet3.git

```

1. 从 Visual Studio 主菜单中，选择“文件”>“打开”>“CMake”，然后导航到刚刚下载的 bullet3 存储库的根目录中的 CMakeLists.txt 文件。

    ![“文件”>“打开”>“CMake”的 Visual Studio 菜单](media/cmake-open-cmake.png)

    打开文件夹后，文件夹结构将显示在“解决方案资源管理器”中。

    ![Visual Studio 解决方案资源管理器文件夹视图](media/cmake-bullet3-solution-explorer.png)

    此视图可以准确显示磁盘上的内容，而不是逻辑或筛选视图。 默认情况下，该视图不显示隐藏文件。 

2. 按“显示所有文件”按钮以查看文件夹中的所有文件。

    ![Visual Studio 解决方案资源管理器中“显示所有文件”按钮](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>切换到目标视图

打开使用 CMake 的文件夹时，Visual Studio 会自动生成 CMake 缓存。 此操作可能需要一些时间，具体取决于项目的大小。 

1. 在“输出窗口”中，选择“显示输出源”，然后选择“CMake”以监控缓存生成过程的状态。 操作完成后，会显示“目标信息提取已完成”。

    ![显示 CMake 的输出的 Visual Studio 输出窗口](media/cmake-bullet3-output-window.png)

    完成此操作后，将配置 IntelliSense，可以生成项目，你可以调试应用程序。 Visual Studio 现在可以根据 CMakeLists 文件中指定的目标提供解决方案的逻辑视图。 

2. 使用“解决方案资源管理器”中的“解决方案和文件夹”按钮切换到 CMake 目标视图。

    ![显示 CMake 目标视图的解决方案资源管理器中的“解决方案和文件夹”按钮](media/cmake-bullet3-show-targets.png)

    以下是 Bullet SDK 的视图：

    ![解决方案资源管理器 CMake 目标视图](media/cmake-bullet3-targets-view.png)

    目标视图提供了此源基础内容更直观的视图。 你可以看到一些目标是库，其他目标是可执行文件。 

3. 在 CMake 目标视图中展开节点以查看其源代码文件，无论这些文件位于磁盘上的哪个位置。

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>添加显式的 Windows x64-Debug 配置

Visual Studio 将为 Windows 创建默认的**x64-调试**配置。 Visual Studio 可借助配置了解将在 CMake 中使用的平台目标。 磁盘上未显示默认配置。 显式添加配置时，Visual Studio 会创建一个名为 CMakeSettings.json 的文件，该文件将填充指定的所有配置的设置。 

1. 单击工具栏中的“配置”下拉列表，然后选择“管理配置...”，添加新配置

    ![“管理配置”下拉列表](media/cmake-bullet3-manage-configurations.png)

    这将打开 " [CMake 设置编辑器](customize-cmake-settings.md)"。 选择编辑器左侧的绿色加号，以添加新配置。 随即将出现“将配置添加到 CMakeSettings”对话框。

    ![将配置添加到 CMakeSettings 对话框](media/cmake-bullet3-add-configuration-x64-debug.png)

    此对话框显示 Visual Studio 附带的所有配置，以及可能创建的任何自定义配置。 如果要继续使用**x64-调试**配置，则应为添加的第一个配置。 选择“x64-Debug”，然后单击“选择”。 这会创建 CMakeSettings 文件，其中包含**X64 调试**的配置，并将配置保存到磁盘。 可通过直接在 CMakeSettings.json 中更改名称参数来使用你喜欢的任何名称。

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>设置断点，在 Windows 上生成和运行 

在此步骤中，我们将调试一个演示 Bullet Physics 库的示例程序。
  
1. 在“解决方案资源管理器”中，选择 AppBasicExampleGui 并展开它。 
1. 打开文件 `BasicExample.cpp`。 
1. 设置在单击正在运行的应用程序时将触发的断点。 单击事件在 helper 类中的方法中进行处理。 快速转至此处：

    1. 选择结构 `BasicExample` 派生自第 30 行的 `CommonRigidBodyBase`。
    1. 右键单击并选择“转到定义”。 现在已在标头 CommonRigidBodyBase.h 中。 
    1. 在上面的浏览器视图中，应看到自己位于 `CommonRigidBodyBase`。 转到右侧，可以选择要检查的成员。 单击下拉列表并选择 `mouseButtonCallback` 以转到标头中该函数的定义。

        ![Visual Studio 成员列表工具栏](media/cmake-bullet3-member-list-toolbar.png)

1. 在此函数的第一行设置一个断点。 在 Visual Studio 调试器下启动时，在应用程序窗口中单击鼠标按钮时会触发此断点。

1. 若要启动应用程序，请使用工具栏中显示“选择启动项”的播放图标选择启动下拉列表。 在下拉列表中选择 AppBasicExampleGui.exe。 可执行文件名现在显示在启动按钮上：

    ![“选择启动项”的 Visual Studio 工具栏启动下拉列表](media/cmake-bullet3-launch-button.png)

5.  按“启动”按钮生成应用程序和必要的依赖项，然后使用附加的 Visual Studio 调试器启动它。 几分钟后将显示正在运行的应用程序：

    ![调试 Windows 应用程序的 Visual Studio](media/cmake-bullet3-launched.png)

6. 将鼠标移动到应用程序窗口，然后单击按钮以触发断点。 此操作会将 Visual Studio 带回到前台，其中编辑器显示执行暂停的行。 你将能够检查应用程序变量、对象、线程和内存。 可以以交互方式单步执行代码。 可以单击“继续”，让应用程序恢复并正常退出或使用“停止”按钮停止在 Visual Studio 中执行。

##  <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>添加 Linux 配置并连接到远程计算机

1. 现在，添加 Linux 配置。 右键单击“解决方案资源管理器”视图中的 CMakeSettings.json 文件，然后选择“添加配置”。 此时将出现与之前相同的“将配置添加到 CMakeSettings”对话框。 选择 " **Linux-调试**时间"，然后保存 CMakeSettings 文件（ctrl + s）。 
2. 现在在配置下拉列表中选择“Linux-Debug”。

    ![使用“X64-Debug”和“Linux-Debug”选项启动配置下拉列表](media/cmake-bullet3-linux-configuration-item.png)

    如果这是首次连接到 Linux 系统，则会出现“连接到远程系统”对话框。

    ![Visual Studio 中“连接到远程系统”对话框](media/cmake-bullet3-connection-manager.png)

    如果已添加远程连接，则可以通过导航到“工具”>“选项”>“跨平台”>“连接管理器”来打开此窗口。
 
3. 向 Linux 计算机提供 [连接信息] （连接到 computer.md），然后单击 "**连接**"。 Visual Studio 会将该计算机作为 CMakeSettings 的默认连接添加到**Linux-调试**的默认连接。 它还将从远程计算机中请求标头，以便获取[特定于该远程连接的 IntelliSense](https://docs.microsoft.com/en-us/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense)。 现在，Visual Studio 会将文件发送到远程计算机，并在远程系统上生成 CMake 缓存。 这些步骤可能需要一些时间，具体取决于网络速度和远程计算机的功率。 当 CMake 输出窗口中出现“目标信息提取完成”消息时，你将知道这已完成。

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>在 Linux 上设置断点、生成和运行

由于这是桌面应用程序，因此你需要为调试配置提供一些其他配置信息。 

1. 在“CMake 目标”视图中，右键单击“AppBasicExampleGui”并选择“调试并启动设置”以打开隐藏的“.vs”子文件夹中的 launch.vs.json 文件。 此文件是开发环境的本地文件。 如果希望签入该文件并将其保存到团队中，则可以将该文件移动到项目的根目录中。 在此文件中，已为 AppBasicExampleGui 添加了一个配置。 这些默认设置在大多数情况下都有效，但由于这是一个桌面应用程序，你需要提供一些额外的信息来启动程序，以便在 Linux 计算机上看到它。 
2. 你需要知道 Linux 计算机上环境变量 `DISPLAY` 的值，运行此命令才能获得它。

    ```cmd
    echo $DISPLAY
    ```

    在 AppBasicExampleGui 的配置中，有一个参数数组“pipeArgs”。 其中有一行“${debuggerCommand}”。 这是在远程计算机上启动 gdb 的命令。 Visual Studio 需要在该命令运行之前将显示内容导出到此上下文中。 例如，如果显示值为 1，请修改该行，如下所示：

    ```cmd
    "export DISPLAY=:1;${debuggerCommand}",
    ```
3. 现在，若要启动和调试应用程序，请选择工具栏中的“选择启动项”下拉列表，然后选择 AppBasicExampleGui。 现在按下该按钮或按 F5。 这将在远程 Linux 计算机上生成应用程序及其依赖项，然后使用附加的 Visual Studio 调试器启动它。 在远程 Linux 计算机上，你应看到一个应用程序窗口。

4. 将鼠标移动到应用程序窗口，单击按钮，将触发断点。 程序执行暂停，Visual Studio 回到前台，你将位于该断点位置。 你还应看到 Visual Studio 中出现了一个 Linux 控制台窗口。 此窗口提供远程 Linux 计算机的输出，它还可接受 `stdin` 的输入。 与任何 Visual Studio 窗口一样，它可以停靠在你希望看到它的位置，并且它的位置将在将来的会话中保留。

    ![Visual Studio Linux 控制台窗口](media/cmake-bullet3-linux-console.png)

5. 可以使用 Visual Studio 以交互方式检查应用程序变量、对象、线程、内存和步骤。 但是这次是在远程 Linux 计算机而不是本地 Windows 环境中完成所有这些工作。 可以单击“继续”，让应用程序恢复并正常退出，或者也可以按“停止”按钮，就像本地执行一样。

6. 查看“调用堆栈”窗口，并查看自 Visual Studio 在 Linux 上启动应用程序后对 `x11OpenGLWindow` 的调用。

    ![显示 Linux 调用堆栈的“调用堆栈”窗口](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>已了解的内容 

在本教程中，已了解直接从 GitHub 克隆的代码库，并在 Windows 上生成、运行和调试，且无需修改。 在远程 Linux 计算机上生成、运行和调试了代码库，并进行了少量配置更改。 

## <a name="next-steps"></a>后续步骤

了解有关在 Visual Studio 中配置和调试 CMake 项目的更多信息：

> [!div class="nextstepaction"]
> [Visual Studio 中的 CMake 项目](cmake-projects-in-visual-studio.md)<br/><br/>
> [配置 Linux CMake 项目](../linux/cmake-linux-project.md)<br/><br/>
> [连接到远程 Linux 计算机](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [自定义 CMake 生成设置](customize-cmake-settings.md)<br/><br/>
> [配置 CMake 调试会话](configure-cmake-debugging-sessions.md)<br/><br/>
> [部署、运行和调试 Linux 项目](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [CMake 预定义配置引用](cmake-predefined-configuration-reference.md)
> 
