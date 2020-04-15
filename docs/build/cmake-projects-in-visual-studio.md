---
title: Visual Studio 中的 CMake 项目
description: 如何在可视化工作室中使用"CMake"创建和构建C++项目。
ms.date: 01/08/2020
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 49ba53eaa8ac075ab6d3b2a66f33160c5c3ec410
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329160"
---
# <a name="cmake-projects-in-visual-studio"></a>Visual Studio 中的 CMake 项目

CMake 是一种跨平台开源工具，用于定义在多个平台上运行的生成过程。 本文假定您熟悉 CMake。 可在[使用 CMake 生成、测试和打包软件](https://cmake.org/)时了解更多关于它的信息。

> [!NOTE]
> 在过去几个版本中，CMake 与 Visual Studio 的集成性越来越大。 要查看您首选版本的 Visual Studio 的文档，请使用**版本**选择器控件。 它位于此页面的目录顶部。

::: moniker range="vs-2019"

用于 Windows 组件**的C++ CMake 工具**使用["打开文件夹"](open-folder-projects-cpp.md)功能直接用于用于 IntelliSense 和浏览目的的"CMakeLists.txt"项目文件（如*CMakelists.txt）。* 支持 Ninja 和 Visual Studio 生成器。 如果使用 Visual Studio 生成器，它将生成一个临时项目文件并将其传递给 msbuild.exe。 但是，该项目永远不会加载用于 IntelliSense 或浏览目的。 您还可以导入现有的 CMake 缓存。

## <a name="installation"></a>安装

**C++ Windows 的 CMake 工具**是桌面开发中的一部分 **，具有C++工作负载C++** 和**Linux 开发**。 有关详细信息，请参阅[跨平台"造单项目](../linux/cmake-linux-project.md)"。

![C++ 桌面工作负载中的 CMake 组件](media/cmake-install-2019.png)

有关详细信息，请参阅[在 Visual Studio 中安装 C++ Linux 工作负载](../linux/download-install-and-setup-the-linux-development-workload.md)。

## <a name="ide-integration"></a>IDE 集成

当您选择 **"打开>文件夹>打开**包含*CMakelists.txt*文件的文件夹时，会发生以下情况：

- Visual Studio 将 **"CMake"** 项目添加到 **"项目"** 菜单中，并带有用于查看和编辑 CMake 脚本的命令。

- 解决方案资源管理器显示文件夹结构和文件****。

- Visual Studio 运行 cmake.exe 并生成默认 （x64 调试） 配置的 CMake 缓存文件 （*CMakeCache.txt*）。 输出窗口中显示 CMake 命令行以及 CMake 的其他输出****。

- 在后台，Visual Studio 开始对源文件编制索引，以启用 IntelliSense、浏览信息和重构等等。 随着工作进行，Visual Studio 监视器在编辑器和磁盘中随之发生变化，以保持其索引与源同步。

可以打开包含任意数量 CMake 项目的文件夹。 Visual Studio 检测并配置工作区中的所有"根 *"CMakelists.txt*文件。 CMake 操作（配置、生成、调试）、C++ IntelliSense 和浏览都可用于工作区中的所有 CMake 项目。

![包含多个根的 CMake 项目](media/cmake-multiple-roots.png)

还可按目标查看经过逻辑组织的项目。 在“解决方案资源管理器”工具栏中，从下拉列表中选择“目标视图”********：

![CMake“目标视图”按钮](media/cmake-targets-view.png)

单击**解决方案资源管理器**顶部的 **"显示所有文件**"按钮，查看*出/生成/\<配置>* 文件夹中的所有 CMake 生成的输出。

可视化工作室使用名为 **"CMakeSettings.json"的**配置文件。 此文件允许您定义和存储多个生成配置，并在 IDE 中方便地在它们之间进行切换。 *配置*是可视化工作室构造，用于封装特定于给定生成类型的设置。 这些设置用于配置 Visual Studio 传递给 cmake.exe 的默认命令行选项。 您还可以在此处指定其他 CMake 选项，并定义您喜欢的任何其他变量。 所有选项都作为内部变量或外部变量写入 CMake 缓存。 在 Visual Studio 2019 中 **，CMake 设置编辑器**提供了一种编辑设置的便捷方式。 有关详细信息，请参阅[自定义 CMake 设置](customize-cmake-settings.md)。

一个设置`intelliSenseMode`不会传递到"单行"，但仅由 Visual Studio 使用。

在每个项目文件夹中使用**CMakelists.txt**文件，就像在任何 CMake 项目中一样。 您可以指定源文件、查找库、设置编译器和链接器选项以及指定其他生成系统相关信息。

要在调试时将参数传递给可执行文件，可以使用另一个称为**launch.vs.json**的文件。 在某些情况下，Visual Studio 会自动生成这些文件。 您可以手动编辑它们，甚至可以自己创建文件。

> [!NOTE]
> 对于其他类型的打开文件夹项目，使用另外两个 JSON 文件 **：CppProperties.json**和**任务.vs.json**。 这些都与 CMake 项目无关。

## <a name="open-an-existing-cache"></a>打开现有缓存

当您打开现有的 CMake 缓存文件 （*CMakeCache.txt*） 时，Visual Studio 不会尝试管理缓存并为您构建树。 您的自定义或首选工具可以完全控制 CMake 如何配置项目。 要在可视化工作室中打开现有缓存，请选择 **"文件>打开>"制作**"。 然后，导航到现有的*CMakeCache.txt*文件。

您可以将现有的 CMake 缓存添加到打开的项目。 它所做的方式与添加新配置的方式相同。 有关详细信息，请参阅我们在 Visual Studio[中打开现有缓存的](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/)博客文章。

## <a name="building-cmake-projects"></a>生成 CMake 项目

要生成 CMake 项目，可选择执行以下操作：

1. 在"常规"工具栏中，查找 **"配置"** 下拉列表。 默认情况下，它可能显示"x64 调试"。 选择首选配置并按**F5**，或单击工具栏上的 **"运行**（绿色三角形）"按钮。 项目首先自动生成，就像 Visual Studio 解决方案一样。

1. 右键单击*CMakelists.txt，* 然后从上下文菜单中选择 **"生成**"。 如果在文件夹结构中有多个目标，可以选择生成所有目标或仅生成某个特定目标。

1. 从主菜单中，选择 **"生成>全部构建****（F7**或**Ctrl_Shift_B**）。 请确保已在“常规”工具栏的“启动项”下拉列表中选择了 CMake 目标********。

![CMake 生成菜单命令](media/cmake-build-menu.png "CMake 生成命令菜单")

生成结果按预期显示在“输出窗口”和“错误列表”中********。

![CMake 生成错误](media/cmake-build-errors.png "CMake 生成错误")

在具有多个生成目标的文件夹中，可以指定要构建的 CMake 目标：在 **"CMake"** 菜单或*CMakelists.txt*上下文菜单中选择**生成**项以指定目标。 如果在 CMake 项目中输入**Ctrl_Shift_B，** 它将生成当前活动文档。

## <a name="debugging-cmake-projects"></a>调试 CMake 项目

要调试 CMake 项目，请选择首选配置并按**F5**，或按工具栏中的 **"运行"** 按钮。 如果 **"运行"** 按钮显示"选择启动项目"，请选择下拉箭头。 选择要运行的目标。 （在 CMake 项目中，“当前文档”选项只对 .cpp 文件有效。）

![CMake 运行按钮](media/cmake-run-button.png "CMake 运行按钮")

如果在上次生成后进行了更改，则“运行”或“F5”命令会先生成项目********。 对 *"CMakeSettings.json"的*更改会导致重新生成 CMake 缓存。

您可以通过在**启动.vs.json**文件中设置属性来自定义 CMake 调试会话。 有关更多信息，请参阅[配置 CMake 调试会话](configure-cmake-debugging-sessions.md)。

## <a name="just-my-code-for-cmake-projects"></a>只为我的代码为 CMake 项目

当您使用 MSVC 编译器为 Windows 生成时，CMake 项目支持仅使用"我的代码"调试。 要更改"仅我的代码"设置，请转到**工具** > **选项** > **调试** > **常规**。

## <a name="vcpkg-integration"></a>Vcpkg 集成

如果您安装了[vcpkg，](vcpkg.md)在 Visual Studio 中打开的 CMake 项目会自动集成 vcpkg 工具链文件。 这意味着无需额外配置即可将 vcpkg 用于您的 CMake 项目。 此支持适用于您定位的远程系统上的本地 vcpkg 安装和 vcpkg 安装。 当您在"CMake 设置"配置中指定任何其他工具链时，将自动禁用此行为。

## <a name="customize-configuration-feedback"></a>自定义配置反馈

默认情况下，除非出现错误，否则将禁止大多数配置消息。 通过在**工具** > **选项** > **CMake**中启用此功能，可以查看所有消息。

   ![配置 CMake 诊断选项](media/vs2019-cmake-configure-options.png "CMake 诊断选项")

## <a name="editing-cmakeliststxt-files"></a>编辑 CMakeLists.txt 文件

要编辑*CMakelists.txt*文件，请右键单击**解决方案资源管理器**中的文件并选择 **"打开**"。 如果对文件进行更改，将显示一个黄色状态栏，并通知您 IntelliSense 将更新。 它为您提供了取消更新操作的机会。 有关*CMakelists.txt*的信息，请参阅[CMake 文档](https://cmake.org/documentation/)。

   ![CMakelists.txt 文件编辑](media/cmake-cmakelists.png "CMakelists.txt 文件编辑")

保存文件后，配置步骤立即自动再次运行，并在“输出”窗口中显示信息****。 错误和警告显示在“错误列表”或“输出”窗口中********。 双击**错误列表中**的错误，以导航到*CMakelist.txt*中的违规行。

   ![CMakelists.txt 文件错误](media/cmake-cmakelists-error.png "CMakelists.txt 文件错误")

## <a name="cmake-configure-step"></a>CMake 配置步骤

当您对*CMakeSettings.json*或*CMakelists.txt*文件进行重大更改时，Visual Studio 会自动重新运行"CMake 配置"步骤。 如果配置步骤完成且没有错误，则收集的信息可在 C++ IntelliSense 和语言服务中提供。 它还用于生成和调试操作。

## <a name="troubleshooting-cmake-cache-errors"></a>排查 CMake 缓存错误

如果您需要有关 CMake 缓存状态的详细信息来诊断问题，在**解决方案资源管理器**中打开**项目**主菜单或*CMakelists.txt*上下文菜单以运行以下命令之一：

- **视图缓存**从编辑器中的生成根文件夹中打开*CMakeCache.txt*文件。 （如果您清理缓存，您在此处对*CMakeCache.txt*进行的任何编辑都会被擦除。 要进行在清理缓存后仍然存在的更改，请参阅自定义[CMake 设置](customize-cmake-settings.md)。

- **打开缓存文件夹**：打开生成根文件夹的资源管理器窗口。

- **清理缓存**：删除生成根文件夹，使下一个 CMake 配置步骤从清理缓存开始。

- 即使 Visual Studio 认为环境是最新的，**生成缓存**也会强制生成步骤运行。

可以在 **"工具>选项>常规**对话框中禁用自动缓存生成>常规对话框。

## <a name="run-cmake-from-the-command-line"></a>从命令行运行 CMake

如果已从 Visual Studio 安装程序安装 CMake，可以通过执行以下步骤从命令行运行它：

1. 运行适当的 vsdevcmd.bat (x86/x64)。 有关详细信息，请参阅[在命令行上构建](building-on-the-command-line.md)。

1. 切换到输出文件夹。

1. 运行 CMake 以生成/配置应用程序。

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 对 CMake 有丰富的支持，包括[跨平台的 CMake 项目](../linux/cmake-linux-project.md)。 用于**CMake 组件的可视化C++工具**使用 **"打开文件夹"** 功能，使 IDE 能够直接使用 CMake 项目文件（如*CMakelists.txt），* 用于智能感知和浏览。 支持 Ninja 和 Visual Studio 生成器。 如果使用 Visual Studio 生成器，它将生成一个临时项目文件并将其传递给 msbuild.exe。 但是，该项目永远不会加载用于 IntelliSense 或浏览目的。 您还可以导入现有的 CMake 缓存。

## <a name="installation"></a>安装

**用于 CMake 的可视化C++工具**作为桌面开发的一部分安装 **，具有C++工作负载C++** 和**Linux 开发**。

![C++ 桌面工作负载中的 CMake 组件](media/cmake-install.png)

有关详细信息，请参阅[在 Visual Studio 中安装 C++ Linux 工作负载](../linux/download-install-and-setup-the-linux-development-workload.md)。

## <a name="ide-integration"></a>IDE 集成

当您选择 **"打开>文件夹>打开**包含*CMakelists.txt*文件的文件夹时，会发生以下情况：

- Visual Studio 将“CMake”菜单项添加到主菜单，其中包含用于查看和编辑 CMake 脚本的命令****。

- 解决方案资源管理器显示文件夹结构和文件****。

- Visual Studio 运行 CMake.exe 并根据需要生成默认配置（即 x86 Debug）的 CMake 缓存**。 输出窗口中显示 CMake 命令行以及 CMake 的其他输出****。

- 在后台，Visual Studio 开始对源文件编制索引，以启用 IntelliSense、浏览信息和重构等等。 随着工作进行，Visual Studio 监视器在编辑器和磁盘中随之发生变化，以保持其索引与源同步。

可以打开包含任意数量 CMake 项目的文件夹。 Visual Studio 检测并配置工作区中的所有"根 *"CMakelists.txt*文件。 CMake 操作（配置、生成、调试）、C++ IntelliSense 和浏览都可用于工作区中的所有 CMake 项目。

![包含多个根的 CMake 项目](media/cmake-multiple-roots.png)

还可按目标查看经过逻辑组织的项目。 在“解决方案资源管理器”工具栏中，从下拉列表中选择“目标视图”********：

![CMake“目标视图”按钮](media/cmake-targets-view.png)

Visual Studio 使用名为*CMakeSettings.json*的文件来存储 Cmake.exe 的环境变量或命令行选项。 *CMakeSettings.json*还使您能够定义和存储多个 CMake 生成配置。 您可以在 IDE 中方便地在它们之间进行切换。

否则，使用*CMakelists.txt，* 就像在任何 CMake 项目中一样，指定源文件、查找库、设置编译器和链接器选项以及指定其他与生成系统相关的信息。

如果需要在调试时将参数传递给可执行文件，则可以使用另一个称为 **"启动.vs.json"** 的文件。 在某些情况下，Visual Studio 会自动生成这些文件。 您可以手动编辑它们，甚至可以自己创建文件。

> [!NOTE]
> 对于其他类型的打开文件夹项目，使用另外两个 JSON 文件 **：CppProperties.json**和**任务.vs.json**。 这些都与 CMake 项目无关。

## <a name="import-an-existing-cache"></a>导入现有缓存

导入现有*CMakeCache.txt*文件时，Visual Studio 会自动提取自定义变量，并根据这些变量创建预填充的*CMakeSettings.json*文件。 原始缓存不会以任何方式修改。 它仍然可以从命令行使用，也可以与用于生成它的任何工具或 IDE 一起使用。 新的*CMakeSettings.json*文件与项目的根*CdMakelists.txt*放在一起。 Visual Studio 基于设置文件生成新的缓存。 您可以在 **"工具>选项>常规对话框中**覆盖自动缓存生成>常规对话框。

并非缓存中的所有内容都会被导入。  生成器和编译器的位置等属性替换为已知适合用于 IDE 的默认值。

### <a name="to-import-an-existing-cache"></a>导入现有缓存

1. 从主菜单中选择 **"文件>打开>"：：**

   ![打开 CMake](media/cmake-file-open.png "文件， 打开， 制作")

   此命令将启动 **"从缓存导入 CMake"** 向导。

2. 导航到要导入的*CMakeCache.txt*文件，然后单击 **"确定**"。 “从缓存导入 CMake 项目”向导随即显示****：

   ![导入 CMake 缓存](media/cmake-import-wizard.png "打开 CMake 导入缓存向导")

   向导完成后，您可以在**解决方案资源管理器**中看到项目中根*CMakelists.txt*文件旁边的新的*CMakeCache.txt*文件。

## <a name="building-cmake-projects"></a>生成 CMake 项目

要生成 CMake 项目，可选择执行以下操作：

1. 在"常规"工具栏中，查找 **"配置"** 下拉列表。 默认情况下，它可能显示"Linux 调试"或"x64 调试"。 选择首选配置并按**F5**，或单击工具栏上的 **"运行**（绿色三角形）"按钮。 项目首先自动生成，就像 Visual Studio 解决方案一样。

1. 右键单击 *"CMakelists.txt"* 并从上下文菜单中选择 **"生成**"。 如果在文件夹结构中有多个目标，可以选择生成所有目标或仅生成某个特定目标。

1. 从主菜单中，选择 **"构建>构建解决方案****（F7**或**Ctrl_Shift_B**）。 请确保已在“常规”工具栏的“启动项”下拉列表中选择了 CMake 目标********。

![CMake 生成菜单命令](media/cmake-build-menu.png "CMake 生成命令菜单")

您可以在*CMakeSettings.json*文件中自定义生成配置、环境变量、命令行参数和其他设置。 它允许您在不修改*CMakelists.txt*文件的情况下进行更改。 有关详细信息，请参阅[自定义 CMake 设置](customize-cmake-settings.md)。

生成结果按预期显示在“输出窗口”和“错误列表”中********。

![CMake 生成错误](media/cmake-build-errors.png "CMake 生成错误")

在具有多个生成目标的文件夹中，可以指定要构建的 CMake 目标：在 **"CMake"** 菜单或*CMakelists.txt*上下文菜单中选择**生成**项以指定目标。 如果在 CMake 项目中输入**Ctrl_Shift_B，** 它将生成当前活动文档。

## <a name="debugging-cmake-projects"></a>调试 CMake 项目

要调试 CMake 项目，请选择首选配置，然后按**F5**。 或者，按工具栏中的 **"运行"** 按钮。 如果“运行”按钮提示“选择启动项”，请选择向下箭头并选择要运行的目标****。 （在 CMake 项目中，“当前文档”选项只对 .cpp 文件有效。）

![CMake 运行按钮](media/cmake-run-button.png "CMake 运行按钮")

如果在上次生成后进行了更改，则“运行”或“F5”命令会先生成项目********。

您可以通过在**启动.vs.json**文件中设置属性来自定义 CMake 调试会话。 有关更多信息，请参阅[配置 CMake 调试会话](configure-cmake-debugging-sessions.md)。

## <a name="editing-cmakeliststxt-files"></a>编辑 CMakeLists.txt 文件

要编辑*CMakelists.txt*文件，请右键单击**解决方案资源管理器**中的文件并选择 **"打开**"。 如果对文件进行更改，将显示一个黄色状态栏，并通知您 IntelliSense 将更新。 它为您提供了取消更新操作的机会。 有关*CMakelists.txt*的信息，请参阅[CMake 文档](https://cmake.org/documentation/)。

   ![CMakelists.txt 文件编辑](media/cmake-cmakelists.png "CMakelists.txt 文件编辑")

保存文件后，配置步骤立即自动再次运行，并在“输出”窗口中显示信息****。 错误和警告显示在“错误列表”或“输出”窗口中********。 双击**错误列表中**的错误，以导航到*CMakelist.txt*中的违规行。

   ![CMakelists.txt 文件错误](media/cmake-cmakelists-error.png "CMakelists.txt 文件错误")

## <a name="cmake-configure-step"></a>CMake 配置步骤

当对*CMakeSettings.json*或*CMakelists.txt*文件进行重大更改时，Visual Studio 会自动重新运行"CMake 配置"步骤。 如果配置步骤完成且没有错误，则收集的信息可在 C++ IntelliSense 和语言服务中提供。 它还用于生成和调试操作。

多个 CMake 项目可能使用相同的 CMake 配置名称（例如，x86-Debug）。 选择配置时，将配置和生成所有这些配置（在自己的生成根文件夹中）。 可以调试参与该 CMake 配置的所有 CMake 项目中的目标。

   ![仅制作"仅生成"菜单项](media/cmake-build-only.png "仅制作"仅生成"菜单项")

您可以将生成和调试会话限制为工作区中项目的子集。 在*CMakeSettings.json*文件中创建具有唯一名称的新配置。 然后，仅将配置应用于这些项目。 选择该配置后，IntelliSense 和生成和调试命令仅适用于这些指定的项目。

## <a name="troubleshooting-cmake-cache-errors"></a>排查 CMake 缓存错误

如果需要有关 CMake 缓存状态的详细信息来诊断问题，请打开“CMake”主菜单或“解决方案资源管理器”中的“CMakeLists.txt”上下文菜单，运行下面的某个命令**********：

- **视图缓存**从编辑器中的生成根文件夹中打开*CMakeCache.txt*文件。 （如果您清理缓存，您在此处对*CMakeCache.txt*进行的任何编辑都会被擦除。 要进行在清理缓存后仍然存在的更改，请参阅自定义[CMake 设置](customize-cmake-settings.md)。

- **打开缓存文件夹**：打开生成根文件夹的资源管理器窗口。

- **清理缓存**：删除生成根文件夹，使下一个 CMake 配置步骤从清理缓存开始。

- 即使 Visual Studio 认为环境是最新的，**生成缓存**也会强制生成步骤运行。

可以在 **"工具>选项>常规**对话框中禁用自动缓存生成>常规对话框。

## <a name="single-file-compilation"></a>单个文件编译

要在 CMake 项目中生成单个文件，请右键单击**解决方案资源管理器**中的文件。 从弹出式菜单中选择 **"编译**"。 您还可以使用主**CMake**菜单在编辑器中生成当前打开的文件：

![CMake 单个文件编译](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>从命令行运行 CMake

如果已从 Visual Studio 安装程序安装 CMake，可以通过执行以下步骤从命令行运行它：

1. 运行适当的 vsdevcmd.bat (x86/x64)。 有关详细信息，请参阅[在命令行上构建](building-on-the-command-line.md)。

1. 切换到输出文件夹。

1. 运行 CMake 以生成/配置应用程序。

::: moniker-end

::: moniker range="vs-2015"

在 Visual Studio 2015 中，Visual Studio 用户可使用 [CMake 生成器](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html)生成 MSBuild 项目文件，IDE 之后可将该项目文件用于 IntelliSense、浏览和编译。

::: moniker-end

## <a name="see-also"></a>另请参阅

[教程：在可视化工作室创建C++跨平台项目](get-started-linux-cmake.md)\
[配置 Linux CMake 项目](../linux/cmake-linux-project.md)\
[连接到远程 Linux 计算机](../linux/connect-to-your-remote-linux-computer.md)\
[自定义"制作"构建设置](customize-cmake-settings.md)\
[CMakeSettings.json 架构引用](cmakesettings-reference.md)\
[配置"制作"调试会话](configure-cmake-debugging-sessions.md)\
[部署、运行和调试 Linux 项目](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake 预定义配置引用](cmake-predefined-configuration-reference.md)
