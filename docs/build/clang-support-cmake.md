---
title: 可视化工作室 CMake 项目中的 Clang/LLVM 支持
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: 46bfe788c13df3a37dd9cba654d16cfe4c3fe177
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323179"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>可视化工作室 CMake 项目中的 Clang/LLVM 支持

::: moniker range="<=vs-2017"

Clang 支持可在 Visual Studio 2019 中提供。

::: moniker-end

::: moniker range="vs-2019"

您可以将 Visual Studio 与 Clang 一起编辑和调试C++面向 Windows 或 Linux 的 CMake 项目。

**Windows**： Visual Studio 2019 版本 16.1 包括在面向 Windows 的 CMake 项目中使用 Clang/LLVM 进行编辑、构建和调试的支持。

**Linux**：对于 Linux CMake 项目，不需要特殊的视觉工作室支持。 您可以使用发行版的包管理器安装 Clang，并在 CMakelists.txt 文件中添加相应的命令。

## <a name="install"></a>安装

为了在 Visual Studio 中获得最佳 IDE 支持，我们建议使用 Windows 的最新 Clang 编译器工具。 如果还没有这些，则可以通过打开 Visual Studio 安装程序和选择桌面开发下的 Windows **C++ Clang 编译器**来安装它们 **，C++** 可选组件。 使用自定义 Clang 安装时，请检查**C++ Clang-cl 中的 v142 生成工具**组件。

![Clang 组件安装](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>创建新配置

要向 CMake 项目添加新的 Clang 配置，：

1. 右键单击**解决方案资源管理器**中的 CMakelists.txt，然后选择**项目的"CMake"设置**。

1. 在 **"配置"** 下，按 **"添加配置**"按钮：

   ![添加配置](media/cmake-add-config-icon.png)

1. 选择所需的 Clang 配置（请注意，为 Windows 和 Linux 提供了单独的 Clang 配置），然后按 **"选择**" ：

   ![CMake Clang 配置](media/cmake-clang-configuration.png)

1. 要修改此配置，请使用 **"CMake 设置编辑器**"。 有关详细信息，请参阅[在可视化工作室中自定义 CMake 生成设置](customize-cmake-settings.md)。

## <a name="modify-an-existing-configuration-to-use-clang"></a>修改现有配置以使用 Clang

要修改现有配置以使用 Clang，请按照以下步骤操作：

1. 右键单击**解决方案资源管理器**中的 CMakelists.txt，然后选择**项目的"CMake"设置**。

1. 在 **"常规"** 下选择 **"工具集**下拉"并选择所需的 Clang 工具集：

   ![CMake Clang 工具集](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>自定义 Clang 位置

默认情况下，Visual Studio 在两个位置查找 Clang：

- （视窗）视觉工作室安装程序附带的 Clang/LLVM 的内部安装副本。
- （视窗和Linux）PATH 环境变量。

您可以通过在 **"制作设置**"中设置**CMAKE_C_COMPILER**和**CMAKE_CXX_COMPILER** CMake 变量来指定其他位置：

![CMake Clang 工具集](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Clang 兼容性模式

对于 Windows 配置，CMake 默认情况下以[clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf)模式调用 Clang，并与标准库的 Microsoft 实现链接。 默认情况下 **，clang-cl.exe**位于`C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`中。

您可以在 **"CMake"变量和缓存**下的 **"CMake 设置"** 中修改这些值。 单击 **"显示高级变量**"。 向下滚动以查找**CMAKE_CXX_COMPILER**，然后单击 **"浏览"** 按钮以指定其他编译器路径。

## <a name="edit-build-and-debug"></a>编辑、生成和调试

设置 Clang 配置后，可以生成和调试项目。 Visual Studio 检测到您正在使用 Clang 编译器，并提供 IntelliSense、突出显示、导航和其他编辑功能。 错误和警告显示在**输出窗口中**。

调试时，可以使用断点、内存和数据可视化以及大多数其他调试功能。 某些与编译器相关的功能（如"编辑"和"继续"）不适用于 Clang 配置。

![CMake Clang 调试](media/clang-debug-visualize.png)

::: moniker-end
