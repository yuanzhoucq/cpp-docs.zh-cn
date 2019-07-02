---
title: Clang/LLVM 支持在 Visual Studio 的 CMake 项目
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++
ms.openlocfilehash: 6773d9cdb076ef305ba635306f3bc9c6575d2203
ms.sourcegitcommit: b233f05adae607f75815111006a771c432df5a9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67517102"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Clang/LLVM 支持在 Visual Studio 的 CMake 项目

::: moniker range="<=vs-2017"

Clang 支持现已推出 Visual Studio 2019。

::: moniker-end

::: moniker range="vs-2019"

您可以使用 Visual Studio 使用 Clang 编辑和调试C++CMake 项目的目标 Windows 或 Linux。

**Windows**：Visual Studio 2019 版本 16.1 包括编辑、 生成和使用 Clang/LLVM 在面向 Windows 的 CMake 项目中进行调试的支持。 

Linux  ：对于 Linux CMake 项目，没有特殊的 Visual Studio 支持是必需的。 你可以安装使用发行版的包管理器、 Clang 和 CMakeLists.txt 文件中添加适当的命令。

## <a name="install"></a>安装

有关在 Visual Studio 中的最佳 IDE 支持，我们建议使用最新的 Clang 编译器 tools for Windows。 如果您没有这些，则可以通过打开 Visual Studio 安装程序并选择安装它们**Windows 的 Clang 编译器**下**使用的桌面开发C++** 可选组件。

![Clang 组件安装](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>创建新的配置

若要将新的 Clang 配置添加到 CMake 项目：

1. 右键单击中 CMakeLists.txt**解决方案资源管理器**，然后选择**项目的 CMake 设置**。

1. 下**配置**，按**添加配置**按钮：

   ![添加配置](media/cmake-add-config-icon.png)

1. 选择所需的 Clang 配置 （请注意，适用于 Windows 和 Linux 提供独立的 Clang 配置），然后按**选择**:

   ![CMake Clang 配置](media/cmake-clang-configuration.png)

1. 若要修改此配置，请使用**CMake 设置编辑器**。 有关详细信息，请参阅[自定义 CMake 生成 Visual Studio 中的设置](customize-cmake-settings.md)。

## <a name="modify-an-existing-configuration-to-use-clang"></a>修改现有配置为使用 Clang

若要修改现有配置为使用 Clang，执行以下步骤：

1. 右键单击中 CMakeLists.txt**解决方案资源管理器**，然后选择**项目的 CMake 设置**。

1. 下**常规**选择**工具集**下拉列表中选择所需的 Clang 工具集：

   ![CMake Clang 工具集](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>自定义 Clang 位置

默认情况下，Visual Studio 查找 Clang 在两个位置：

- (Windows)在内部安装的 Clang/LLVM 随附在 Visual Studio 安装程序的副本。
- （Windows 和 Linux）PATH 环境变量。

可以通过设置指定另一个位置**CMAKE_C_COMPILER**并**CMAKE_CXX_COMPILER**中的 CMake 变量**CMake 设置**:

![CMake Clang 工具集](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Clang 兼容性模式

对于 Windows 配置，默认情况下的 CMake 调用在 Clang [clang cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf)模式和使用的 Microsoft 实现的标准库的链接。 默认情况下**clang cl.exe**位于`C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`。

 您可以修改这些值在**CMake 设置**下**CMake 变量和缓存**。 单击**显示高级变量**。 向下滚动找到**CMAKE_CXX_COMPILER**，然后单击**浏览**按钮以指定不同的编译器路径。

## <a name="edit-build-and-debug"></a>编辑、 生成和调试

在设立 Clang 配置后，可以生成和调试项目。 Visual Studio 检测到你正在使用 Clang 编译器，提供 IntelliSense，突出显示、 导航和其他编辑功能。 中显示错误和警告**输出窗口**。

在调试时，可以使用断点、 内存和数据可视化效果和其他大多数调试功能。 不可用的 Clang 配置某些依赖于编译器的功能，例如编辑并继续。

![CMake Clang 调试](media/clang-debug-visualize.png)

::: moniker-end
