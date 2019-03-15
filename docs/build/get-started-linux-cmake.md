---
title: 在 Visual Studio 中创建 c + + 跨平台项目
description: 本教程演示如何设置、 编译和调试 c + + 的开源 CMake 项目面向 Linux 和 Windows 的 Visual Studio 中。
author: mikeblome
ms.topic: tutorial
ms.date: 03/05/2019
ms.openlocfilehash: deb2c91d6d09d8945e5eb57a7ac742c5b1705e83
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824468"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>教程：在 Visual Studio 中创建 c + + 跨平台项目 

Visual Studio C 和 c + + 开发不再仅用于 Windows。 本教程演示如何使用 Visual Studio for c + + 跨平台开发基于 CMake 而无需创建或生成 Visual Studio 项目。 当打开包含 CMakeLists.txt 文件的文件夹时，Visual Studio 配置智能感知和生成设置自动。 快速可以进行编辑、 构建和调试本地 Windows，你的代码，然后切换您的配置以在 Visual Studio 中执行在 Linux 上，相同操作中的所有内容。

在本教程中，你将了解：

> [!div class="checklist"]
> * 克隆 GitHub 中的开放源代码 CMake 项目
> * 在 Visual Studio 中打开项目 
> * 生成和调试在 Windows 上的可执行文件目标
> * 添加到 Linux 计算机的连接
> * 生成和调试在 Linux 上相同的目标

## <a name="prerequisites"></a>系统必备

- 跨平台 c + + 开发设置 Visual Studio
    - 首先您需要具有[安装 Visual Studio](https://visualstudio.microsoft.com/vs/)。 接下来，确认你具有**使用 c + + 的桌面开发**并**使用 c + + 工作负荷的 Linux 开发**安装。 此最小安装仅为 3 GB，具体取决于您的下载速度安装不应超过 10 分钟。
- 跨平台 c + + 开发设置 Linux 计算机
    - Visual Studio 不需要任何特定 Linux 分发版。 用于 Linux (WSL) 可以在虚拟机、 云或 Windows 子系统物理机上运行操作系统。 但是，本教程中的图形环境是必需的;因此，因为它是主要用于命令行操作，不建议 WSL。
    - Visual Studio 需要 Linux 计算机的工具有：C + + 编译器，GDB，ssh，和 zip。 在 Debian 基于系统中，可以按如下所示安装这些依赖项。
    
    ```cmd
        sudo apt install -y openssh-server build-essential gdb zip
    ```
    - Visual Studio 需要的 Linux 计算机具有最新版本的 CMake 服务器启用了模式 (至少 3.8)。 Microsoft 生成 CMake 可以在任何 Linux 发行版上安装一个通用版本。 我们建议使用此生成以确保拥有最新功能。 你可以获取从 CMake 的二进制文件[CMake 存储库的 Microsoft 分叉](https://github.com/Microsoft/CMake/releases)GitHub 上。 转到该页面并下载匹配您系统的体系结构在 Linux 上，然后将其标记为可执行文件的版本：
    
    ```cmd
        wget <path to binary>
        chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```
    - 可以查看有关运行该脚本的选项`-–help`。 我们建议你使用`–prefix`选项以指定在安装 **/usr/local**路径因为这是 Visual Studio 在何处查找针对 CMake 的默认位置。 下面的示例显示了 Linux x86_64 脚本。 如果你正在使用不同的目标平台根据需要更改的。 
    
    ```cmd
        sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr/local
    ```
- 在 Windows 计算机上安装适用于 windows 的 Git。
- 一个 GitHub 帐户。

## <a name="clone-an-open-source-cmake-project-from-github"></a>克隆 GitHub 中的开放源代码 CMake 项目

本教程，它提供各种不同的应用程序用于冲突检测和物理模拟在 GitHub 上使用项目符号的物理 SDK。 它包括示例可执行程序，编译并运行，而无需编写其他代码。 本教程不会修改任何源代码或生成脚本。 若要开始，bullet3 存储库克隆 GitHub 中在计算机上必须安装 Visual Studio。 

```cmd

git clone https://github.com/bulletphysics/bullet3.git

```

1. 从 Visual Studio 主菜单中，选择**文件 > 打开 > CMake**并导航到刚下载的 bullet3 存储库的根目录中 CMakeLists.txt 文件。

    ![Visual Studio 菜单中的文件 > 打开 > CMake](media/cmake-open-cmake.png)

    只要打开文件夹时，会显示在您的文件夹结构**解决方案资源管理器**。

    ![Visual Studio 解决方案资源管理器文件夹视图](media/cmake-bullet3-solution-explorer.png)

    此视图显示究竟什么是磁盘，不是逻辑或已筛选视图上。 默认情况下，它不显示隐藏的文件。 

2. 按**显示所有文件**按钮以查看文件夹中的所有文件。

    ![Visual Studio 解决方案资源管理器中显示所有文件按钮](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>切换到目标视图

当您打开使用 CMake 的文件夹时，Visual Studio 会自动生成 CMake 缓存。 此操作可能需要一些时间，具体取决于你的项目的大小。 

1. 在中**输出窗口**，选择**显示输出来源**，然后选择**CMake**来监视缓存生成过程的状态。 该操作完成后，状态显示"目标信息提取完成"。

    ![显示输出从 CMake 的 visual Studio 输出窗口](media/cmake-bullet3-output-window.png)

    此操作完成后，配置 IntelliSense，可以生成项目，并可以调试应用程序。 Visual Studio 现在可以提供基于 CMakeLists 文件中指定的目标的解决方案的逻辑视图。 

2. 使用**解决方案和文件夹**按钮**解决方案资源管理器**切换到 CMake 目标视图。

    ![解决方案和文件夹按钮，在解决方案资源管理器以显示 CMake 目标视图](media/cmake-bullet3-show-targets.png)

    下面是哪些视图如下所示的项目符号 SDK:

    ![解决方案资源管理器 CMake 目标视图](media/cmake-bullet3-targets-view.png)

    目标视图提供了此源库中的内容更直观的视图。 您可以看到某些目标是库和其他一些则是可执行文件。 

3. 展开 CMake 目标视图以查看其源代码文件中的节点，只要这些文件可能位于磁盘上。

## <a name="set-a-breakpoint-build-and-run"></a>设置断点、 生成和运行

在此步骤中，我们将调试演示项目符号的物理库的示例程序。
  
1. 在中**解决方案资源管理器**、 选择 AppBasicExampleGui 并将其展开。 
1. 打开文件`BasicExample.cpp`。 
1. 设置在运行的应用程序中单击时将命中断点。 中的帮助器类的一个方法中处理单击事件。 若要快速转至此处：

    1. 选择`CommonRigidBodyBase`，该结构`BasicExample`围绕第 30 行派生自。
    1. 右键单击并选择**转到定义**。 现在，已在标头 CommonRigidBodyBase.h 中。 
    1. 在浏览器视图中更高版本，您的源应看到处于`CommonRigidBodyBase`。 右侧，可以选择要检查的成员。 单击下拉列表，然后选择`mouseButtonCallback`以转到标头中该函数的定义。

        ![Visual Studio 成员列表工具栏](media/cmake-bullet3-member-list-toolbar.png)

1. 此函数中的第一行上放置一个断点。 这将被命中时单击鼠标按钮时在 Visual Studio 调试器中启动的应用程序的窗口中。

1. 若要启动该应用程序，请选择启动有 play 图标的工具栏中显示"选择启动项"下拉列表。 在下拉列表选择 AppBasicExampleGui.exe。 可执行文件的名称现在显示启动按钮：

    ![Visual Studio 工具栏中启动下拉列表选择启动项](media/cmake-bullet3-launch-button.png)

5.  按启动按钮以生成应用程序和所需的依赖关系，然后启动带有附加 Visual Studio 调试程序。 几分钟后将显示运行的应用程序：

    ![Visual Studio 调试 Windows 应用程序](media/cmake-bullet3-launched.png)

6. 将鼠标移到应用程序窗口中，然后单击一个按钮以触发断点。 这将返回到前台显示一行执行会暂停编辑器与 Visual Studio。 你将能够检查应用程序变量、 对象、 线程和内存。 可以以交互方式逐句通过代码。 可以单击**继续**让恢复和正常退出或停止在 Visual Studio 中使用停止按钮执行的应用程序。

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>添加显式 Windows x64 调试配置

到目前为止，一直在使用默认值**x64 调试**的 Windows 配置。 Visual Studio 如何了解哪些平台配置是它要使用 CMake 的目标。 在磁盘上表示不是默认配置。 时显式添加配置，Visual Studio 将创建使用指定的所有配置设置的调用 CMakeSettings.json 中已填充的文件。 

1. 通过单击来添加新的配置配置工具栏中的下拉列表中，选择**管理配置...**

    ![管理配置下拉列表](media/cmake-bullet3-manage-configurations.png)

    **将配置添加到出现 CMakeSettings**对话框将出现。

    ![将配置添加到出现 CMakeSettings 对话框](media/cmake-bullet3-add-configuration-x64-debug.png)

    此对话框显示包含在 Visual Studio 的所有配置，以及可能会创建任何自定义配置。 如果你想要继续使用默认值**x64 调试**配置中，应添加的第一个。 通过添加该配置，你将能够来回切换 Windows 和 Linux 之间配置。 选择**x64 调试**然后单击**选择**。 这将创建具有配置的 CMakeSettings.json 文件**x64 调试**和切换 Visual Studio 以使用该配置，而不是默认值。 你将看到配置下拉列表不会再显示"(default)"作为名称的一部分。 可以使用您喜欢通过更改直接在 CMakeSettings.json 中的 name 参数配置的任何名称。

##  <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>添加 Linux 配置并连接到远程计算机

1. 现在，添加 Linux 配置。 右键单击中的 CMakeSettings.json 文件**解决方案资源管理器**视图，然后选择**添加配置**。 请参阅到出现 CMakeSettings 对话框作为之前相同的添加配置。 选择**Linux 调试**这一次，然后保存 CMakeSettings.json 文件。 
2. 现在，选择**Linux 调试**配置下拉列表中。

    ![启动配置 X64 调试和 Linux 调试选项的下拉列表](media/cmake-bullet3-linux-configuration-item.png)

    如果这是要连接到 Linux 系统，第一次**连接到远程系统**对话框将出现。

    ![Visual Studio 连接到远程系统对话框](media/cmake-bullet3-connection-manager.png)

    如果你已添加的远程连接可以通过导航到打开此窗口**工具 > 选项 > 跨平台 > 连接管理器**。
 
3. 提供在 Linux 计算机的连接信息，然后单击**Connect**。 Visual Studio 将 CMakeSettings.json 关于该计算机添加作为默认设置**Linux 调试**。 它还会拉取在远程计算机中的标头，以便获取 IntelliSense 特定于该计算机时使用它。 现在 Visual Studio 会将文件发送到远程计算机，然后生成 CMake 缓存，并创建完成后将为该远程 Linux 计算机中使用相同的源基配置 Visual Studio。 这些步骤可能需要一些时间，具体取决于网络速度和远程计算机的电源。 您将知道 CMake 输出窗口中显示消息"目标信息提取完成"时，这是完整。

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>设置断点、 生成和运行在 Linux 上

由于这是一个桌面应用程序，你需要提供到调试配置一些其他配置信息。 

1. 在 CMake 目标视图中，右键单击 AppBasicExampleGui 并选择**调试和启动设置**以打开 launch.vs.json 文件中隐藏 **.vs**子文件夹。 此文件是本地的开发环境。 您可以将其移动到在项目的根目录如果你想要其签入并将其保存与你的团队。 在此文件中配置已添加对 AppBasicExampleGui。 在大多数情况下，这些默认设置工作，但由于这是你需要提供一些其他信息来启动程序的方式的桌面应用程序可以看到它在我们的 Linux 计算机上。 
2. 您需要了解的环境变量的值`DISPLAY`在 Linux 上运行此命令可获取它。

    ```cmd
    echo $DISPLAY
    ```

    在配置中为 AppBasicExampleGui 是参数数组"pipeArgs"。 在这里是一个行"${debuggerCommand}"。 这是启动远程计算机上的 gdb 命令。 Visual Studio 需要先运行该命令将导出到此上下文中显示。 例如，如果您的显示的值： 1，相应行修改，如下所示：

    ```cmd
    "export DISPLAY=:1;${debuggerCommand}",
    ```
3. 现在为了启动并调试我们的应用程序，选择**选择启动项**工具栏中的下拉列表中，选择 AppBasicExampleGui。 现在按下该按钮或命中**F5**。 这将生成应用程序，在远程 Linux 计算机上的其依赖项然后附带 Visual Studio 调试器启动它。 在远程 Linux 计算机，你会看到显示的应用程序窗口。

4. 将鼠标移到应用程序窗口中，单击一个按钮，并将命中断点。 程序执行暂停，Visual Studio 返回转入前台，并且将在断点处。 您应看到 Linux 控制台窗口在 Visual Studio 中显示。 此窗口提供输出从远程 Linux 计算机，并还可以接受的输入`stdin`。 它可以像任何 Visual Studio 窗口中，停靠其中想要查看它，它的位置将保留在将来的会话。

    ![Visual Studio Linux 控制台窗口](media/cmake-bullet3-linux-console.png)

5. 可以通过使用 Visual Studio 以交互方式在代码中检查应用程序变量、 对象、 线程、 内存和步骤。 但这次实现所有这在远程 Linux 计算机上而不本地 Windows 环境。 可以单击**继续**让应用程序恢复并退出通常情况下，或者您可以按停止按钮，就像使用本地执行一样。

6. 查看调用堆栈窗口，并查看对调用`x11OpenGLWindow`由于 Visual Studio 启动 Linux 上的应用程序。

    ![调用堆栈窗口显示 Linux 调用堆栈](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>已了解的内容 

在本教程中，已了解基于直接从 GitHub 克隆和生成、 运行，并调试 Windows 不作任何修改的代码。 这是代码库，与配置做出细微更改，已生成、 运行和调试远程 Linux 计算机上。 

## <a name="next-steps"></a>后续步骤

了解有关配置和调试 Visual Studio 中的 CMake 项目的详细信息：

> [!div class="nextstepaction"]
> [在 Visual Studio 中的 CMake 项目](cmake-projects-in-visual-studio.md)<br/><br/>
> [配置 Linux CMake 项目](../linux/cmake-linux-project.md)<br/><br/>
> [连接到远程 Linux 计算机](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [自定义 CMake 生成设置](customize-cmake-settings.md)<br/><br/>
> [配置 CMake 调试会话](configure-cmake-debugging-sessions.md)<br/><br/>
> [部署、运行和调试 Linux 项目](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [CMake 预定义的配置参考](cmake-predefined-configuration-reference.md)
> 
