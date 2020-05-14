---
title: Visual Studio CMake 项目中的 Clang/LLVM 支持
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: 46bfe788c13df3a37dd9cba654d16cfe4c3fe177
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323179"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Visual Studio CMake 项目中的 Clang/LLVM 支持

::: moniker range="<=vs-2017"

Visual Studio 2019 中已提供 Clang 支持。

::: moniker-end

::: moniker range="vs-2019"

可以将 Clang 和 Visual Studio 配合使用来编辑和调试以 Windows 或 Linux 为目标的 C++ CMake 项目。

**Windows**：Visual Studio 2019 版本 16.1 支持在 CMake 项目中以 Windows 为目标使用 Clang/LLVM 进行编辑、生成和调试。

Linux  ：对于 Linux CMake 项目，不需要特殊的 Visual Studio 支持。 可以使用发行版的包管理器安装 Clang，并在 CMakeLists.txt 文件中添加适当的命令。

## <a name="install"></a>安装

若要在 Visual Studio 中获得最佳 IDE 支持，建议使用适用于 Windows 的最新 Clang 编译器工具。 如果尚未安装这些工具，可以通过打开 Visual Studio 安装程序并在“使用 C++ 的桌面开发”可选组件下选择“适用于 Windows 的 C++ Clang 编译器”来安装它们   。 使用自定义 Clang 安装时，请选中“适用于 v142 生成工具的 C++ Clang-cl”组件  。

![Clang 组件安装](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>创建新配置

向 CMake 项目添加新的 Clang 配置：

1. 右键单击“解决方案资源管理器”中的 CMakeLists.txt，然后选择“项目的 CMake 设置”   。

1. 在“配置”下，按“添加配置”按钮   ：

   ![添加配置](media/cmake-add-config-icon.png)

1. 选择所需的 Clang 配置（请注意，Windows 和 Linux 具有单独的 Clang 配置），然后按“选择”  ：

   ![CMake Clang 配置](media/cmake-clang-configuration.png)

1. 若要对此配置进行修改，请使用“CMake 设置编辑器”  。 有关详细信息，请参阅[在 Visual Studio 中自定义 CMake 生成设置](customize-cmake-settings.md)。

## <a name="modify-an-existing-configuration-to-use-clang"></a>修改现有配置以使用 Clang

若要修改现有配置以使用 Clang，请执行以下步骤：

1. 右键单击“解决方案资源管理器”中的 CMakeLists.txt，然后选择“项目的 CMake 设置”   。

1. 在“常规”下，选择“工具集”下拉列表并选择所需的 Clang 工具集   ：

   ![CMake Clang 工具集](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>自定义 Clang 位置

默认情况下，Visual Studio 在两个位置查找 Clang：

- (Windows) Visual Studio 安装程序随附的 Clang/LLVM 的内部安装副本。
- （Windows 和 Linux）PATH 环境变量。

可通过在“CMAKE 设置”中设置“CMAKE_C_COMPILER”和“CMAKE_CXX_COMPILER”CMAKE 变量，来指定其他位置    ：

![CMake Clang 工具集](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Clang 兼容性模式

对于 Windows 配置，CMake 默认情况下会在 [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) 模式下调用 Clang，并与标准库的 Microsoft 实现链接。 默认情况下，clang-cl.exe  位于 `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin` 中。

可以在“CMake 设置”的“CMake 变量和缓存”下修改这些值   。 单击“显示高级变量”  。 向下滚动找到“CMAKE_CXX_COMPILER”编译器，然后单击“浏览”按钮以指定其他编译器路径   。

## <a name="edit-build-and-debug"></a>编辑、生成和调试

设置 Clang 配置后，可以生成和调试项目。 Visual Studio 会检测到在使用 Clang 编译器，并提供 IntelliSense、突出显示、导航和其他编辑功能。 错误和警告会显示在“输出窗口”  中。

调试时，可以使用断点、内存和数据可视化以及大多数其他调试功能。 某些依赖于编译器的功能（如“编辑”和“继续”）不可用于 Clang 配置。

![CMake Clang 调试](media/clang-debug-visualize.png)

::: moniker-end
