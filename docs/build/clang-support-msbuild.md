---
title: Visual Studio 中的 Clang/LLVM 支持 Visual Studio 项目
ms.date: 08/30/2019
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: f0142c2583eeef10f159cd83451e1f3866990b75
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222626"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>Visual Studio 项目中的 Clang/LLVM 支持

::: moniker range="<=vs-2017"

Visual Studio 2019 中提供了对 CMake 和 MSBuild 项目的 Clang 支持。

::: moniker-end

::: moniker range="vs-2019"

可以将 Visual Studio 2019 版本16.2 与 Clang 配合使用, 以编辑、生成和C++调试面向 Windows 或 Linux 的 visual studio 项目 (MSBuild)。

## <a name="install"></a>安装

若要在 Visual Studio 中获得最佳 IDE 支持, 建议使用适用于 Windows 的最新 Clang 编译器工具。 如果尚未安装这些文件, 可以通过打开 Visual Studio 安装程序并在 "使用可选组件**进行C++桌面开发**" 下选择 **C++ "Clang tools for Windows** " 来安装它们。 如果希望在计算机上使用现有的 Clang 安装, 请选择 **C++ Clang-cl for v142 生成工具。** 可选组件。 Microsoft C++标准库当前至少需要 Clang 8.0.0;Clang 的捆绑版本将自动更新, 以使标准库的 Microsoft 实现中的更新保持最新。 

![Clang 组件安装](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>配置 Windows 项目以使用 Clang 工具

若要将 Visual Studio 项目配置为使用 clang, 请在**解决方案资源管理器**中右键单击项目节点, 然后选择 "**属性**"。 通常, 您应该首先选择对话框顶部的 "**所有配置**"。 然后, 在 "**常规** > **平台工具集**" 下选择 " **LLVM" (clang)** , 然后选择 **"确定"** 。

![Clang 组件安装](media/clang-msbuild-prop-page.png)

如果你使用的是与 Visual Studio 捆绑的 Clang 工具, 则无需执行其他步骤。 对于 Windows 项目, Visual Studio 默认情况下会在[Clang](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf)模式下调用 Clang, 并使用标准库的 Microsoft 实现的链接。 默认情况下, **clang-cl**位于中`C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`。

如果你使用的是自定义 Clang 安装, 则可以修改**项目** > **属性** > "**VC + + 目录** > " "**配置属性** > "**可执行文件目录**, 方法是将自定义 Clang 安装根目录添加为其中的第一个目录, 或更改`LLVMInstallDir`属性的值。 有关详细信息, 请参阅[设置自定义 LLVM 位置](#custom_llvm_location)。

## <a name="configure-a-linux-project-to-use-clang-tools"></a>配置 Linux 项目以使用 Clang 工具

对于 Linux 项目, Visual Studio 使用 Clang GCC 兼容前端。 项目属性和几乎所有编译器标志完全相同

若要将 Visual Studio Linux 项目配置为使用 Clang:

1. 右键单击 "**解决方案资源管理器**中的项目节点, 然后选择"**属性**"。 
1. 通常, 您应该首先选择对话框顶部的 "**所有配置**"。 
1. 如果使用的是适用于 Linux 的 Windows 子系统, 则选择 "**常规** > **平台工具集**", 如果使用的是远程计算机或 VM, 请选择 " **WSL_Clang_1_0** "。
1. 按“确定”。

![Clang 组件安装](media/clang-msbuild-prop-page.png)

在 Linux 上, Visual Studio 默认使用在 PATH 环境属性中遇到的第一个 Clang 位置。 如果你使用的是自定义 Clang 安装, `LLVMInstallDir`则必须更改属性的值, 或者替换**项目** > **属性** > "**VC + + 目录** >   **" 下的路径配置属性** > **可执行目录**。 有关详细信息, 请参阅[设置自定义 LLVM 位置](#custom_llvm_location)。

## <a name="custom_llvm_location"></a>设置自定义 LLVM 位置

可以通过创建*属性*文件并将该文件添加到任何项目的根文件夹中, 为一个或多个项目设置 LLVM 的自定义路径。 可以将其添加到根解决方案文件夹, 将其应用于解决方案中的所有项目。 文件应如下所示 (但替换为实际路径):

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>设置其他属性、编辑、生成和调试

设置 Clang 配置后, 再次右键单击项目节点, 然后选择 "**重新加载项目**"。 现在可以使用 Clang 工具生成和调试项目。 Visual Studio 检测到你正在使用 Clang 编译器, 并提供 IntelliSense、突出显示、导航和其他编辑功能。 错误和警告将显示在**输出窗口**中。 Clang 配置的项目属性页与 MSVC 的项目属性页非常相似, 尽管某些依赖于编译器的功能 (如 "编辑并继续") 不适用于 Clang 配置。 若要设置属性页中不可用的 Clang 编译器或链接器选项, 可以在**配置属性** > **C/C++ (或链接器)**  > **命令行**下的属性页中手动添加它。**其他选项**。  > 

调试时, 可以使用断点、内存和数据可视化, 以及大多数其他调试功能。  

![Clang 调试](media/clang-debug-msbuild.png)

::: moniker-end
