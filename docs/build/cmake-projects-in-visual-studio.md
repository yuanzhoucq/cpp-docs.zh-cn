---
title: Visual Studio 中的 CMake 项目
ms.date: 03/27/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 22a8ecc34e6413c32628381241d45d3d76b39ecc
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342231"
---
# <a name="cmake-projects-in-visual-studio"></a>Visual Studio 中的 CMake 项目

CMake 是一种跨平台开源工具，用于定义在多个平台上运行的生成过程。 本文假定你熟悉 CMake。 可在[使用 CMake 生成、测试和打包软件](https://cmake.org/)时了解更多关于它的信息。

在 Visual Studio 2015 中，Visual Studio 用户可使用 [CMake 生成器](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html)生成 MSBuild 项目文件，IDE 之后可将该项目文件用于 IntelliSense、浏览和编译。

Visual Studio 2017 引入了对 CMake 的丰富支持，包括[跨平台 CMake 项目](../linux/cmake-linux-project.md)。 “Visual C++ Tools for CMake”组件使用“打开文件夹”功能，让 IDE 能够直接将 CMake 项目文件（例如 CMakeLists.txt）用于 IntelliSense 和浏览。 支持 Ninja 和 Visual Studio 生成器。 如果使用 Visual Studio 生成器，则会生成一个临时项目文件并将该文件传递给 msbuild.exe，但是绝不会出于 IntelliSense 或浏览目的加载它。 您可以导入现有 CMake 缓存;Visual Studio 会自动将提取自定义的变量，并创建预填充**CMakeSettings.json**文件。 

## <a name="installation"></a>安装

默认情况下，“Visual C++ Tools for CMake”作为“使用 C++ 的桌面开发”工作负载的一部分安装，并作为“使用 C++ 的 Linux 开发”工作负载的一部分。

![C++ 桌面工作负载中的 CMake 组件](media/cmake-install.png)

有关详细信息，请参阅[在 Visual Studio 中安装 C++ Linux 工作负载](../linux/download-install-and-setup-the-linux-development-workload.md)。

## <a name="ide-integration"></a>IDE 集成

选择“文件”|“打开”|“文件夹”，打开一个包含 CMakeLists.txt 文件的文件夹时，将发生以下情况：

- Visual Studio 将“CMake”菜单项添加到主菜单，其中包含用于查看和编辑 CMake 脚本的命令。

- 解决方案资源管理器显示文件夹结构和文件。

- Visual Studio 运行 CMake.exe 并根据需要生成默认配置（即 x86 Debug）的 CMake 缓存。 输出窗口中显示 CMake 命令行以及 CMake 的其他输出。

- 在后台，Visual Studio 开始对源文件编制索引，以启用 IntelliSense、浏览信息和重构等等。 随着工作进行，Visual Studio 监视器在编辑器和磁盘中随之发生变化，以保持其索引与源同步。

可以打开包含任意数量 CMake 项目的文件夹。 Visual Studio 检测并配置工作区中的所有“根”CMakeLists.txt 文件。 CMake 操作（配置、生成、调试）以及 C++ IntelliSense 和浏览可用于工作区中的所有 CMake 项目。

![包含多个根的 CMake 项目](media/cmake-multiple-roots.png)

还可按目标查看经过逻辑组织的项目。 在“解决方案资源管理器”工具栏中，从下拉列表中选择“目标视图”：

![CMake“目标视图”按钮](media/cmake-targets-view.png)

Visual Studio 使用名为的文件**CMakeSettings.json**存储环境变量或 Cmake.exe 的命令行选项。 **CMakeSettings.json**还可以让您来定义和存储多个 CMake 生成配置，并方便地在 IDE 中它们之间进行切换。 

否则，请使用**CMakeLists.txt**就像你会在任何 CMake 项目指定源代码文件，发现库、 设置编译器和链接器选项，并指定其他生成系统中的相关信息。

如果你需要在调试时将参数传递到可执行文件，可以使用另一个名为的文件**launch.vs.json**。 在某些情况中，Visual Studio 会自动生成这些文件；你可以手动编辑它们。 也可自己创建文件。

> [!NOTE]
> 对于其他类型的打开文件夹项目，可使用两个其他的 JSON 文件：**CppProperties.json**并**tasks.vs.json**。 这些都与 CMake 项目无关。

## <a name="import-an-existing-cache"></a>导入现有缓存

导入现有 CMakeCache.txt 文件时，Visual Studio 自动提取自定义的变量，并基于这些变量创建一个预填充的 **CMakeSettings.json** 文件。 不会以任何方式修改原始缓存，并且仍可从命令行或者借助用于生成原始缓存的工具或 IDE 使用该原始缓存。 新**CMakeSettings.json**文件将位于与项目的根 CMakeLists.txt 一起。 Visual Studio 基于设置文件生成新的缓存。 可在“工具”|“选项”|“CMake”|“常规”对话框中替代自动缓存生成。

并非缓存中的所有内容都会被导入。  生成器和编译器的位置等属性替换为已知适合用于 IDE 的默认值。

### <a name="to-import-an-existing-cache"></a>导入现有缓存

1. 从主菜单中选择“文件”|“打开”|“CMake”：

   ![打开 CMake](media/cmake-file-open.png "“文件”>“打开”>“CMake”")

   “从缓存导入 CMake”向导随即显示。

2. 导航到要导入的 CMakeCache.txt 文件，然后单击“确定”。 “从缓存导入 CMake 项目”向导随即显示：

   ![导入 CMake 缓存](media/cmake-import-wizard.png "打开 CMake 导入缓存向导")

   在向导完成时，可在解决方案资源管理器中看到新的 CMakeCache.txt 文件，位于项目中的根 CMakeLists.txt 文件旁边。

## <a name="building-cmake-projects"></a>生成 CMake 项目

要生成 CMake 项目，可选择执行以下操作：

1. 在常规的工具栏中，找到**配置**下拉列表中; 它可能默认显示"Linux-调试"或"x64-Debug"。 选择所需的配置，然后按**F5**，或单击**运行**（绿色三角形） 按钮在工具栏上的。 项目首先自动生成，就像 Visual Studio 解决方案一样。

1. 右键单击 CMakeLists.txt，并从上下文菜单中选择“生成”。 如果在文件夹结构中有多个目标，可以选择生成所有目标或仅生成某个特定目标。

1. 从主菜单中选择“生成”|“生成解决方案”（F7 或 Ctrl+Shift+B）。 请确保已在“常规”工具栏的“启动项”下拉列表中选择了 CMake 目标。

![CMake 生成菜单命令](media/cmake-build-menu.png "CMake 生成命令菜单")

可以自生成配置、 环境变量、 命令行参数和其他设置定义不修改 CMakeLists.txt 文件的使用情况**CMakeSettings.json**文件。 有关详细信息，请参阅[自定义 CMake 设置](customize-cmake-settings.md)。

生成结果按预期显示在“输出窗口”和“错误列表”中。

![CMake 生成错误](media/cmake-build-errors.png "CMake 生成错误")

在包含多个生成目标的文件夹中，可以在“CMake”菜单或“CMakeLists.txt”上下文菜单上选择“生成”项，指定要生成的 CMake 目标。 在 CMake 项目中按 Ctrl+Shift+B 可生成当前活动文档。

## <a name="debugging-cmake-projects"></a>调试 CMake 项目

要调试 CMake 项目，请选择所需配置并按 F5，或按工具栏中的“运行”按钮。 如果“运行”按钮提示“选择启动项”，请选择向下箭头并选择要运行的目标。 （在 CMake 项目中，“当前文档”选项只对 .cpp 文件有效。）

![CMake“运行”按钮](media/cmake-run-button.png "CMake“运行”按钮")

如果在上次生成后进行了更改，则“运行”或“F5”命令会先生成项目。

你可以自定义调试会话中设置属性 CMake **launch.vs.json**文件。 有关更多信息，请参阅[配置 CMake 调试会话](configure-cmake-debugging-sessions.md)。


## <a name="editing-cmakeliststxt-files"></a>编辑 CMakeLists.txt 文件

要编辑 CMakeLists.txt 文件，请右键单击“解决方案资源管理器”中的文件，并选择“打开”。 如果对文件进行更改，会显示一个黄色的状态栏，通知用户 IntelliSense 将更新，并且用户可以选择取消该更新操作。 有关 CMakeLists.txt 的详细信息，请参阅 [CMake 文档](https://cmake.org/documentation/)。

   ![CMakeLists.txt 文件编辑](media/cmake-cmakelists.png "CMakeLists.txt 文件编辑")

保存文件后，配置步骤立即自动再次运行，并在“输出”窗口中显示信息。 错误和警告显示在“错误列表”或“输出”窗口中。 双击“错误列表”中的错误可导航到 CMakeLists.txt 中出现问题的行。

   ![CMakeLists.txt 文件错误](media/cmake-cmakelists-error.png "CMakeLists.txt 文件错误")


## <a name="cmake-configure-step"></a>CMake 配置步骤

当对进行重大更改**CMakeSettings.json**或 CMakeLists.txt 文件，Visual Studio 会自动重新运行 CMake 配置步骤。 如果配置步骤正确完成，则可在 C++ IntelliSense 和语言服务以及生成和调试操作中使用所收集的信息。

如果多个 CMake 项目使用相同的 CMake 配置名称（例如 x86-Debug），那么在选择该配置时会配置并生成所有这些项目（在其自己的生成根文件夹中）。 可以调试参与该 CMake 配置的所有 CMake 项目中的目标。

   ![CMake“仅生成”菜单项](media/cmake-build-only.png "CMake“仅生成”菜单项")

若要限制生成和调试会话保存到工作区中项目的子集，创建新的配置中的唯一名称**CMakeSettings.json**文件，并将其应用于仅限这些项目。 如果选择了该配置，则仅为这些特定项目启用 IntelliSense 以及生成和调试命令。

## <a name="troubleshooting-cmake-cache-errors"></a>排查 CMake 缓存错误

如果需要有关 CMake 缓存状态的详细信息来诊断问题，请打开“CMake”主菜单或“解决方案资源管理器”中的“CMakeLists.txt”上下文菜单，运行下面的某个命令：

- **查看缓存**：从编辑器中的生成根文件夹打开 CMakeCache.txt 文件。 （如果清除缓存，则将擦除在此处对 CMakeCache.txt 进行的任何编辑。 若要清除缓存后保留的更改，请参阅[的自定义的 CMake 设置](customize-cmake-settings.md)。)

- **打开缓存文件夹**：打开生成根文件夹的资源管理器窗口。

- **清理缓存**：删除生成根文件夹，使下一个 CMake 配置步骤从清理缓存开始。

- **生成缓存**：即使 Visual Studio 认为环境是最新的，也强制运行生成步骤。

可在“工具”|“选项”|“CMake”|“常规”对话框中禁用自动缓存生成。

## <a name="single-file-compilation"></a>单个文件编译

要在 CMake 项目中编译单个文件，可在解决方案资源管理器中右键单击该文件，然后选择“编译”。 通过使用 CMake 主菜单，还可编译当前在编辑器中打开的文件：

![CMake 单个文件编译](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>从命令行运行 CMake

如果已从 Visual Studio 安装程序安装 CMake，可以通过执行以下步骤从命令行运行它：

1. 运行适当的 vsdevcmd.bat (x86/x64)。 有关详细信息，请参阅[基于命令行生成](building-on-the-command-line.md)。

1. 切换到输出文件夹。

1. 运行 CMake 以生成/配置应用程序。
  
## <a name="see-also"></a>请参阅

[教程：在 Visual Studio 中创建 C++ 跨平台项目](get-started-linux-cmake.md)<br/>
[配置 Linux CMake 项目](../linux/cmake-linux-project.md)<br/>
[连接到远程 Linux 计算机](../linux/connect-to-your-remote-linux-computer.md)<br/>
[自定义 CMake 生成设置](customize-cmake-settings.md)<br/>
[CMakeSettings.json 引用](cmakesettings-reference.md)<br/>
[配置 CMake 调试会话](configure-cmake-debugging-sessions.md)<br/>
[部署、运行和调试 Linux 项目](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 预定义配置引用](cmake-predefined-configuration-reference.md)<br/>
