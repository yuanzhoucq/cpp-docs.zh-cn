---
title: 在 Visual Studio 中创建 C++ 跨平台项目
description: 如何在 Visual Studio 中设置、编译和调试面向 Linux 和 Windows 的C++开源 CMake 项目。
ms.topic: tutorial
ms.date: 01/08/2020
ms.openlocfilehash: aac536f488cf22adf5aa835c9fe5b884fc5d7298
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328744"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>教程：在可视化工作室创建C++跨平台项目

Visual Studio C 和 C++ 开发不再仅适用于 Windows。 本教程演示如何使用 Visual Studio 在 Windows 和 Linux 上C++跨平台开发。 它基于 CMake，因此您不必创建或生成 Visual Studio 项目。 当您打开包含 CMakelists.txt 文件的文件夹时，Visual Studio 会自动配置 IntelliSense 并生成设置。 您可以在 Windows 上快速开始编辑、构建和调试代码。 然后，切换配置，在 Linux 上执行相同的操作，所有这些都来自 Visual Studio 中。

在本教程中，你将了解如何执行以下操作：

> [!div class="checklist"]
>
> * 从 GitHub 克隆一个开源 CMake 项目
> * 在 Visual Studio 中打开项目
> * 在 Windows 上生成和调试可执行目标
> * 添加与 Linux 计算机的连接
> * 在 Linux 上生成和调试相同的目标

## <a name="prerequisites"></a>先决条件

* 设置适用于跨平台 C++ 开发的 Visual Studio
  * 首先，[安装 Visual Studio，](https://visualstudio.microsoft.com/vs/)选择**具有C++工作负载的C++** 和**Linux 开发。** 此最小安装仅为 3 GB。 根据您的下载速度，安装时间不应超过 10 分钟。

* 设置适用于跨平台 C++ 开发的 Linux 计算机
  * Visual Studio 不需要任何特定的 Linux 发行版。 操作系统可以在物理计算机、VM 或云中运行。 您也可以将 Windows 子系统用于 Linux （WSL）。 但是，对于本教程，需要图形环境。 此处不建议使用 WSL，因为它主要用于命令行操作。
  * Visual Studio 需要在 Linux 计算机上使用这些工具：C++编译器、gdb、ssh、rsync、忍者和 zip。 在基于 Debian 的系统上，您可以使用此命令安装以下依赖项：

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync ninja-build zip
    ```

  * Visual Studio 要求在 Linux 计算机上启用服务器模式（至少 3.8）的最新版本的 CMake。 Microsoft 生成可以在任何 Linux 发行版上安装的通用 CMake 版本。 我们建议您使用此版本来确保您具有最新的功能。 可从 GitHub 上的 [CMake 存储库 Microsoft 分支](https://github.com/Microsoft/CMake/releases)获得 CMake 二进制文件。 转到该页面并下载与 Linux 计算机上的系统体系结构匹配的版本，然后将其标记为可执行文件：

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * 可以使用 `-–help` 查看运行脚本的选项。 我们建议您使用`–prefix`选项指定在 **/usr**路径中的安装，因为 **/usr/bin**是 Visual Studio 查找 CMake 的默认位置。 以下示例显示了 Linux-x86_64 脚本。 如果您使用的是其他目标平台，则根据需要进行更改。

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr
    ```

* 在 Windows 计算机上安装的适用于 Windows 的 Git。
* 一个 GitHub 帐户。

## <a name="clone-an-open-source-cmake-project-from-github"></a>从 GitHub 克隆一个开源 CMake 项目

本教程在 GitHub 上使用项目符号物理 SDK。 它为许多应用提供碰撞检测和物理模拟。 SDK 包括无需编写其他代码即可编译和运行的示例可执行程序。 本教程不修改任何源代码或生成脚本。 要开始，请从安装了 Visual Studio 的计算机上的 GitHub 克隆*项目符号3*存储库。

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. 在可视化工作室主菜单上，选择**文件>打开>制作**。 导航到您刚刚下载的 cmakelists.txt 的 cmakelists.txt 文件。

    ![“文件”>“打开”>“CMake”的 Visual Studio 菜单](media/cmake-open-cmake.png)

    一旦打开文件夹，您的文件夹结构就会在**解决方案资源管理器**中可见。

    ![Visual Studio 解决方案资源管理器文件夹视图](media/cmake-bullet3-solution-explorer.png)

    此视图可以准确显示磁盘上的内容，而不是逻辑或筛选视图。 默认情况下，该视图不显示隐藏文件。

1. 选择"**显示所有文件**"按钮以查看文件夹中的所有文件。

    ![Visual Studio 解决方案资源管理器中“显示所有文件”按钮](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>切换到目标视图

打开使用 CMake 的文件夹时，Visual Studio 会自动生成 CMake 缓存。 此操作可能需要一些时间，具体取决于项目的大小。

1. 在“输出窗口”中，选择“显示输出源”，然后选择“CMake”以监控缓存生成过程的状态************。 操作完成后，会显示“目标信息提取已完成”。

   ![显示 CMake 的输出的 Visual Studio 输出窗口](media/cmake-bullet3-output-window.png)

   此操作完成后，将配置 IntelliSense。 您可以生成项目并调试应用程序。 Visual Studio 现在根据 CMakelists 文件中指定的目标显示解决方案的逻辑视图。

1. 使用“解决方案资源管理器”中的“解决方案和文件夹”按钮切换到 CMake 目标视图********。

   ![显示 CMake 目标视图的解决方案资源管理器中的“解决方案和文件夹”按钮](media/cmake-bullet3-show-targets.png)

   以下是 Bullet SDK 的视图：

   ![解决方案资源管理器 CMake 目标视图](media/cmake-bullet3-targets-view.png)

   目标视图提供了此源基础内容更直观的视图。 你可以看到一些目标是库，其他目标是可执行文件。

1. 在 CMake 目标视图中展开节点以查看其源代码文件，无论这些文件位于磁盘上的哪个位置。

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>添加显式的 Windows x64-Debug 配置

Visual Studio 为 Windows 创建默认**x64 调试**配置。 Visual Studio 可借助配置了解将在 CMake 中使用的平台目标。 磁盘上未显示默认配置。 当您显式添加配置时，Visual Studio 将创建一个名为 *"CMakeSettings.json"* 的文件。 它填充了您指定的所有配置的设置。

1. 添加新配置。 打开工具栏中的 **"配置**"下拉列表，然后选择 **"管理配置**"。

   ![“管理配置”下拉列表](media/cmake-bullet3-manage-configurations.png)

   将打开["制作设置编辑器](customize-cmake-settings.md)"。 选择编辑器左侧的绿色加号以添加新配置。 将显示"**将配置添加到"设置"对话框**。

   ![将配置添加到 CMakeSettings 对话框](media/cmake-bullet3-add-configuration-x64-debug.png)

   此对话框显示 Visual Studio 中包含的所有配置，以及您创建的任何自定义配置。 如果要继续使用**x64 调试**配置，则应是添加的第一个配置。 选择**x64-调试**，然后选择 **"选择**"按钮。 Visual Studio 创建具有**x64 调试**配置的 CMakeSettings.json 文件，并将其保存到磁盘。 可通过直接在 CMakeSettings.json 中更改名称参数来使用你喜欢的任何名称。

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>设置断点、生成并在 Windows 上运行

在此步骤中，我们将调试一个演示 Bullet Physics 库的示例程序。
  
1. 在“解决方案资源管理器”中，选择 AppBasicExampleGui 并展开它****。

1. 打开 `BasicExample.cpp` 文件。

1. 设置在正在运行的应用程序中单击时命中的断点。 单击事件在 helper 类中的方法中进行处理。 快速转至此处：

   1. 选择`CommonRigidBodyBase`结构派生自该结构`BasicExample`。 在30号线附近

   1. 右键单击并选择“转到定义”****。 现在，您位于"共同刚性博基础.h"的标头中。

   1. 在源上方的浏览器视图中，您应该看到您位于 中`CommonRigidBodyBase`。 转到右侧，可以选择要检查的成员。 打开下拉列表并选择`mouseButtonCallback`转到标头中该函数的定义。

      ![Visual Studio 成员列表工具栏](media/cmake-bullet3-member-list-toolbar.png)

1. 在此函数的第一行设置一个断点。 当您单击应用程序窗口中的鼠标按钮时，在 Visual Studio 调试器下运行时，它会被命中。

1. 要启动应用程序，请在工具栏中选择启动下拉列表。 它是一个绿色播放图标，显示"选择启动项目"。 在下拉列表中，选择 AppBasicExampleGui.exe。 可执行文件名现在显示在启动按钮上：

   ![“选择启动项”的 Visual Studio 工具栏启动下拉列表](media/cmake-bullet3-launch-button.png)

1. 选择启动按钮以生成应用程序和必要的依赖项，然后在附加 Visual Studio 调试器后启动它。 几分钟后将显示正在运行的应用程序：

   ![调试 Windows 应用程序的 Visual Studio](media/cmake-bullet3-launched.png)

1. 将鼠标移动到应用程序窗口，然后单击按钮以触发断点。 断点将 Visual Studio 带回前台，编辑器显示暂停执行的行。 您可以检查应用程序变量、对象、线程和内存，也可以以交互方式单步执行代码。 选择 **"继续**"以让应用程序继续，然后正常退出。 或者，通过使用停止按钮停止 Visual Studio 中的执行。

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>添加 Linux 配置并连接到远程计算机

1. 添加 Linux 配置。 右键单击“解决方案资源管理器”视图中的 CMakeSettings.json 文件，然后选择“添加配置”********。 此时将出现与之前相同的“将配置添加到 CMakeSettings”对话框。 选择**Linux调试**这一次，然后保存CMakeSettings.json文件（ctrl +s）。

1. 在配置下拉列表中选择**Linux 调试**。

   ![使用“X64-Debug”和“Linux-Debug”选项启动配置下拉列表](media/cmake-bullet3-linux-configuration-item.png)

   如果这是您第一次连接到 Linux 系统，则会出现 **"连接到远程系统"** 对话框。

   ![Visual Studio 中“连接到远程系统”对话框](media/cmake-bullet3-connection-manager.png)

   如果已添加远程连接，则可以通过导航到**工具>选项>跨平台>连接管理器**来打开此窗口。

1. 向[Linux 计算机提供连接信息](/cpp/linux/connect-to-your-remote-linux-computer)，然后选择 **"连接**"。 Visual Studio 将该计算机添加为 CMakeSettings.json 作为**Linux 调试的**默认连接。 它还从远程计算机下拉头，因此您将获得[特定于该远程连接的 IntelliSense。](/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense) 接下来，Visual Studio 会将文件发送到远程计算机，并在远程系统上生成 CMake 缓存。 这些步骤可能需要一些时间，具体取决于网络速度和远程计算机的电源。 当"目标信息提取完成"消息出现在 CMake 输出窗口中时，您会知道它已完成。

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>设置断点、构建和在 Linux 上运行

因为它是桌面应用程序，因此您需要向调试配置提供一些其他配置信息。

1. 在"CMake 目标"视图中，右键单击 AppBasicExampleGui 并选择 **"调试和启动设置"** 以打开隐藏 **.vs**子文件夹中的启动.vs.json 文件。 此文件是开发环境的本地文件。 如果希望签入该文件并将其保存到团队中，则可以将该文件移动到项目的根目录中。 在此文件中，已为 AppBasicExampleGui 添加了配置。 在大多数情况下，这些默认设置工作，但此处不工作。 因为它是桌面应用程序，您需要提供一些附加信息来启动程序，以便您可以在 Linux 计算机上看到它。

1. 要查找 Linux 计算机上的环境变量`DISPLAY`的值，请运行以下命令：

   ```cmd
   echo $DISPLAY
   ```

   在 AppBasicExampleGui 的配置中，有一个参数数组"pipeArgs"。 它包含一行："$[调试器命令]"。 它是在远程计算机上启动 gdb 的命令。 可视化工作室必须在该命令运行之前将显示器导出到此上下文中。 例如，如果显示的值为`:1`，请修改该行，如下所示：

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. 启动和调试应用程序。 在工具栏中打开 **"选择启动项目**"下拉列表，然后选择**AppBasicExampleGui**。 接下来，选择工具栏中的绿色播放图标，或按**F5**。 应用程序及其依赖项构建在远程 Linux 计算机上，然后随附加 Visual Studio 调试器一起启动。 在远程 Linux 计算机上，你应看到一个应用程序窗口。

1. 将鼠标移到应用程序窗口中，然后单击按钮。 断点被命中。 程序执行暂停，Visual Studio 回到前台，您将看到断点。 你还应看到 Visual Studio 中出现了一个 Linux 控制台窗口。 该窗口提供来自远程 Linux 计算机的输出，并且它还可以接受`stdin`的输入。 与任何 Visual Studio 窗口一样，您可以将其停靠在您喜欢查看的位置。 它的立场在未来的届会中保持不变。

   ![Visual Studio Linux 控制台窗口](media/cmake-bullet3-linux-console.png)

1. 可以使用 Visual Studio 以交互方式检查应用程序变量、对象、线程、内存和步骤。 但是这一次，你所做的都是在远程 Linux 计算机上，而不是本地的 Windows 环境中。 您可以选择 **"继续**"以让应用程序正常恢复和退出，也可以选择停止按钮，就像本地执行一样。

1. 查看“调用堆栈”窗口，并查看自 Visual Studio 在 Linux 上启动应用程序后对 `x11OpenGLWindow` 的调用。

   ![显示 Linux 调用堆栈的“调用堆栈”窗口](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>已了解的内容

在本教程中，您直接从 GitHub 克隆了一个代码库。 您无需修改即可在 Windows 上生成、运行和调试它。 然后，使用相同的代码库（具有次要的配置更改）在远程 Linux 计算机上生成、运行和调试。

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
